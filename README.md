# 특이사항 
없음

# 개요 
[[pipeline] ci/cd와 github actions의 기본 개념](https://sbi1024.github.io/devops/pipeline/1) 블로그의 게시글에서 sample로 제공되는 프로젝트 입니다.

# 사용법
위 블로그 글을 읽의면서 `deploy.yml` 파일의 코드를 주석처리 하면서 단계적으로 따라가보세요.

크게 3단계로 나누어 실습해 볼 수 있습니다.

## Step1. GitHub Actions 기본 이해하기

```  yml
name: GitHub Actions 실행시켜보기
on:
  push:
    branches:
      - main
jobs:
  My-Deploy-job:
    runs-on: ubuntu-latest
    steps:
      - name: Hello World 출력
        run: echo "Hello World"
```

## Step2. GitHub Actions 여러 명령어 한번에 실행해보기

```  yml
name: GitHub Actions 실행시켜보기
on:
  push:
    branches:
      - main
jobs:
  My-Deploy-job:
    runs-on: ubuntu-latest
    steps:
      - name: Hello World 출력
        run: echo "Hello World"
      - name: 여러 명령어 문장 출력하기
        run: |
          echo "Good"
          echo "Morning"
```

## Step3. GitHub Actions Secret 변수 사용해보기

``` yml
name: GitHub Actions 실행시켜보기
on:
  push:
    branches:
      - main
jobs:
  My-Deploy-job:
    runs-on: ubuntu-latest
    steps:
      - name: Hello World 출력
        run: echo "Hello World"
      - name: 여러 명령어 문장 출력하기
        run: |
          echo "Good"
          echo "Morning"
      - name: Github Actions 자체에 저장되어 있는 변수 사용해 보기
        run: |
          echo $GITHUB_SHA
          echo $GITHUB_REPOSITORY
      - name: 아무한테나 노출이 되면 안되는 값
        run: |
          echo ${{ secrets.API_KEY_PASSWORD }}
```

# 결과
### Step1. Result
![image5](https://github.com/user-attachments/assets/0846fb8b-d649-4edd-8fc9-d0917b644825)

### Step2. Result
![image11](https://github.com/user-attachments/assets/8cd0ba07-cbef-43f5-bc26-683a447c5123)

### Step3. Result
![image16](https://github.com/user-attachments/assets/fe031b59-322c-47fd-b37a-a775c7f29e51)

