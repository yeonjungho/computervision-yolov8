# 💊 의약품 객체 탐지 프로젝트 (yoloPillDetector)

본 프로젝트는 고령화 시대 및 다량의 의약품 복용 환경에서 발생할 수 있는 오투약 사고를 방지하기 위해, **YOLOv8 기반의 의약품 객체 탐지 모델**을 구축하고 최적화한 연구입니다.

## 1. 개요
- **목적:** 알약 4종(마그밀, 게보린, 뮤테란, 삐콤씨)을 실시간으로 식별하는 객체 탐지 모델 개발.
- **기술 스택:** Python, PyTorch, YOLOv8 (Ultralytics), AWS EC2(Tesla T4).
- **데이터:** AI Hub 의약품 이미지 데이터셋 (학습 667장, 검증/평가 167장).

## 2. 실험 및 성능 결과
| 실험 모델 | 하이퍼파라미터(Epochs/LR) | mAP50 | 추론 시간(Inference) |
| :--- | :--- | :---: | :---: |
| **Baseline (Nano)** | 30 / 0.01 | 99.3% | 1.9ms |
| **Tuned (Nano)** | 50 / 0.005 | **99.5%** | **2.0ms** |
| **Heavy (Small)** | 50 / 0.01 | 98.4% | 3.3ms |

## 3. 핵심 성과 및 고찰
1. **전이 학습(Transfer Learning):** 사전 학습된 가중치를 활용하여 데이터셋 한계를 극복하고 99.5%라는 높은 정밀도 달성.
2. **모델 최적화:** 무거운 모델(8s)보다 경량화 모델(8n)의 튜닝이 성능과 속도 면에서 더 효율적임을 입증.
3. **시스템 최적화:** AWS 인프라 환경에서 AutoBatch 및 하이퍼파라미터 튜닝을 통해 실시간 서비스 적용 가능성 확인.

## 4. 구조 및 실행
- `data.yaml`: 데이터셋 구성 파일.
- `results/`: 실험별 지표 및 예측 결과물.

## 5. 성능이미지

Baseline
<img width="2400" height="1200" alt="image" src="https://github.com/user-attachments/assets/b72538b3-0f41-408e-9dd5-633c1729c4cd" /> 
<img width="1464" height="1920" alt="image" src="https://github.com/user-attachments/assets/f317852b-a18a-4075-9053-54d0de08c861" />
<img width="1920" height="1920" alt="image" src="https://github.com/user-attachments/assets/20cfcff8-34f0-450d-abd6-1a321a0d439c" />



Tuned
<img width="2400" height="1200" alt="image" src="https://github.com/user-attachments/assets/05a9c47e-a0fb-4dcb-b744-42fcf54b478f" />
<img width="2400" height="1200" alt="image" src="https://github.com/user-attachments/assets/194d0890-6d5e-42ad-a112-04e99865bc66" />
<img width="2400" height="1200" alt="image" src="https://github.com/user-attachments/assets/fbfcf401-cda2-462f-82c3-6bd27b66cca7" />



Heavy
<img width="2400" height="1200" alt="image" src="https://github.com/user-attachments/assets/190887cf-4f37-4c23-ba59-ffb2853cd303" />
<img width="1464" height="1920" alt="image" src="https://github.com/user-attachments/assets/525d8487-68d0-4b60-815c-75fd20050714" />
<img width="1464" height="1920" alt="image" src="https://github.com/user-attachments/assets/07543396-d349-4164-944b-31a838897c13" />
