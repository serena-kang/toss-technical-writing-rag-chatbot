# 토스 테크니컬 라이팅 가이드 RAG 챗봇

토스의 [개발자를 위한 글쓰기 기본기](https://github.com/toss/technical-writing) 
가이드 문서를 검색 가능한 챗봇으로 구현한 프로젝트입니다.

## 만든 이유

가이드를 "아는 것"과 "실천하는 것"의 차이를 보여주고 싶었습니다./n
RAG 챗봇을 구현하는 것에서 더 나아가, 코드를 작성할 때도 토스 가이드의
문장·구조 원칙을 직접 적용했습니다.

## 적용한 토스 원칙

| 원칙 | 적용 위치 |
|------|----------|
| 주체를 분명하게 하기 | 프롬프트 설계 (행동 주체를 챗봇으로 명확히) |
| 구체적으로 쓰기 | 함수 docstring (모호한 표현 대신 구체적 설명) |
| 예측 가능하게 하기 | 함수명·출력 형식 통일 (extract_, build_ 패턴) |
| 한 페이지에 하나만 다루기 | 노트북 셀 단위로 작업 분리 |
| 가치를 먼저 제공하기 | 코드보다 먼저 선택 이유 설명 |

## 기술 스택

- LangChain
- Chroma (벡터 데이터베이스)
- HuggingFace BGE-M3 (한국어 임베딩)
- GPT-4.1-mini (답변 생성)
- Gradio (챗봇 인터페이스)

## 구현 과정

1. 토스 가이드 mdx 문서 23개 로드 및 정제
2. 텍스트 청크 분할 (chunk_size=800)
3. 벡터 임베딩 후 Chroma 저장
4. MMR 검색으로 관련 문서 검색
5. RAG 체인으로 답변 생성
6. Gradio로 대화형 챗봇 구현

## 실행 방법

\`\`\`bash
pip install -r requirements.txt
\`\`\`

\`.env\` 파일에 OpenAI API 키를 추가한 뒤, 
\`toss_guide_chatbot_refactored.ipynb\`를 순서대로 실행하세요.

## 데이터 출처

\`technical_writing\` 폴더의 가이드 문서는 토스의 공개 저장소에서 
가져왔습니다. Copyright (c) 2024 Viva Republica, Inc.
원본: https://github.com/toss/technical-writing
