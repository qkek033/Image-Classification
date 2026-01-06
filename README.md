# Image-Classification
EfficientNet과 Vision Transformer모델을 활용한 이미지 분석을 통해 강아지와 고양이 사진을 판별, 분류

# 프로젝트 개요
Kaggle의 Dogs vs Cats 이미지 데이터를 활용하여 개와 고양이를 분률하는 이진 이미지 분류 모델을 구축하고,
서로 다른 딥러닝 모델의 성능 차이와 일반화 성능을 비교, 분석한 프로젝트입니다.
다나순히 Validation Accuracy만 비교하는 것이 아니라,
Kaggle Private Score(Log Loss)를 기준으로 실제 데이터에 더 강한 모델을 선별하는 것을 목표로 하였습니다.

# 프로젝트 목표
- 이미지 데이터 기반 이진 분류 모델 구현
- 데이터 증강 및 전처리를 통한 일반화 성능 향상
- 서로 다른 딥러닝 아키텍처 성능 비교
- 실험 결과를 기반으로 최적의 모델 선정

# 데이터 소개
- 출처: Kaggle Dogs vs Cats Dataset
- 학습 데이터: 25,000장
- 테스트 데이터: 12,500장
- 분류 기준: Dog -> 1, Cat -> 0

# 사용 기술
- 언어: Python
- 프레임워크: PyTorh
- 모델: EfficientNet-B7, Vision Transformer(ViT)
- 라이브러리: Numpy, Pandas, Matplotlib, timm
- 실행 환경: Google Colab

# 프로젝트 수행 과정
- 데이터 로드 및 Train / Validation 분리
- 이미지 전처리 및 데이터 증강(Augmentation) 적용
- 사전 학습된 모델 기반 Transfer Learning 적용
- 모델 학습 및 Validation 성능 모니터린
- Kaggle Private Score 기반 성능 비교
- 최종 모델 선정 및 결과 분석

# 모델 성능 비교 결과
| 사용 모델 | Scheduler | Epoch | Validation Accuracy | Kaggle Private Score (Log Loss) |
|-----------|-----------|-------|---------------------|--------------------------------|
| ViT (vit_base_patch32_224) | 사용 | 10 | 99.52% | 0.05439 |
| ViT (vit_base_patch32_224) | 미사용 | 10 | 99.61% | 0.05162 |
| ViT (vit_base_patch32_224) | 미사용 | 30 | 99.16% | 0.05842 |
| EfficientNet-B7 | 미사용 | 20 | **99.64%** | **0.03901** |
| ViT + EfficientNet-B7 | 미사용 | 30 | 99.16% | 0.04014 |

# 최종 모델 선정
여러 실험 결과를 비교한 결과,
EfficientNet-B7 단일 모델이 Validation Accuracy와 Kaggle Private Score 모두에서 가장 우수한 성능을 보였습니다.
이를 통해 본 프로젝트에서는 EfficientNet-B7을 최종 모델로 선정하였습니다.

# 프로젝트를 통해 얻은 인사이트
- Validation Accuracy만으로는 모델의 일반화 성능을 완전히 판단하기 어렵다는 점
- 실제 평가 지표(Kaggle Private Score)의 중요성
- 데이터 특성에 따라 CNN 기반 모델이 Transformer 기반 모델보다 더 효과적일 수 있음
- 실험과 비교를 통한 합리적인 모델 선택의 중요
