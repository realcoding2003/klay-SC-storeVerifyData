# 클레이튼(Klaytn) 메시지 저장/검증 스마트 컨트랙트 개발 예제 프로젝트

이 프로젝트는 Klaytn 블록체인에서 메시지를 저장하고 검증할 수 있는 스마트 계약을 포함하고 있습니다.

샘플 프로젝트를 통해 클레이튼 스마트 계약을 좀 더 쉽고 빠르게 개발하기위한 목적으로 시작한 프로젝트 입니다.

실용적으로 데이터를 저장하고 반환해 주는 스마트 계약을 배포하고 이를 테스트 해보는 방식의 간단한 프로젝트 입니다.

- 스마트 계약 배포는 편의상 Remix IDE를 사용합니다.
- 배포된 계약에 대한 테스트는 node.js를 통해 수행합니다.

## 목차

- [사전 준비](#사전-준비)
- [시작하기](#시작하기)
- [배포](#배포)
- [테스트](#테스트)
   - [스트레스 테스트](#스트레스-테스트)
   - [검증](#검증)
- [이슈 및 피드백](#이슈-및-피드백)
- [포크와 스타](#포크와-스타)
- [라이선스](#라이선스)

## 사전 준비

시작하기 전에 다음 요구 사항을 충족하는지 확인하십시오:

- 로컬 머신에 Node.js와 npm이 설치되어 있어야 합니다.
- Klaytn 계정과 Klaytn 엔드포인트에 접근할 수 있어야 합니다.
- 스마트 계약 배포를 위해 [Remix IDE](https://remix.ethereum.org/)를 사용하십시오.

## 시작하기

1. 레포지토리를 클론합니다:
    ```sh
    git clone https://github.com/realcoding2003/klay-SC-storeVerifyData.git
    cd klay-SC-storeVerifyData
    ```

2. 의존성을 설치합니다:
    ```sh
    npm install
    ```

3. 루트 디렉토리에 `.env` 파일을 생성하고, Klaytn 엔드포인트, 개인 키, 주소를 추가합니다:
    ```env
    RPC_URL=YOUR_KLAYTN_ENDPOINT
    PRIVATE_KEY=YOUR_PRIVATE_KEY
    ADDRESS=YOUR_ADDRESS
    ```

## 스마트 계약 배포

1. [Remix IDE](https://remix.ethereum.org/)에서 [MessageStoreAndVerify.sol](contracts/MessageStoreAndVerify.sol) 파일을 엽니다.
2. Solidity 컴파일러를 사용하여 계약을 컴파일합니다.
3. Remix에서 적절한 환경(예: MetaMask를 통한 Injected Web3 사용)을 설정하여 Klaytn 네트워크에 계약을 배포합니다.
4. 배포된 계약 주소와 ABI를 저장합니다:
   - 계약 주소를 복사하여 `deployed` 디렉토리에 `Address.txt` 파일에 붙여넣습니다. (없으면 생성)
   - Remix에서 계약 ABI를 복사하여 `deployed` 디렉토리에 `ABI.json` 파일에 붙여넣습니다. (없으면 생성)

## 테스트

### 스트레스 테스트

해시를 연속적으로 저장하여 스트레스 테스트를 수행하려면:

1. `deployed` 디렉토리에 `Address.txt`와 `ABI.json` 파일이 올바르게 채워져 있는지 확인합니다.
2. 스트레스 테스트 스크립트를 실행합니다:
    ```sh
    npm run stress test
    ```

### 검증

저장된 해시를 검증하려면:

1. `deployed` 디렉토리에 `Address.txt`와 `ABI.json` 파일이 올바르게 채워져 있는지 확인합니다.
2. 검증 스크립트를 실행합니다:
    ```sh
    npm run verify
    ```

이 스크립트는 다음을 수행합니다:
- 샘플 메시지와 키에 대한 해시를 저장합니다.
- 블록체인에서 해시를 가져와서 검증합니다.

## 이슈 및 피드백

질문이 있거나 코드 수정이 필요한 경우 [이슈 페이지](https://github.com/realcoding2003/klay-SC-storeVerifyData/issues)를 통해 이슈를 등록해 주세요. 피드백은 언제나 환영합니다!

## 포크와 스타

이 프로젝트가 유용하다고 생각되시면, GitHub 레포지토리에 스타를 주시고, 프로젝트를 포크하여 자신만의 버전을 만들어 보세요. 여러분의 기여와 관심이 프로젝트를 더욱 발전시키는 데 큰 도움이 됩니다.


## 라이선스

이 프로젝트는 MIT 라이선스에 따라 라이선스가 부여됩니다. 자세한 내용은 [LICENSE](LICENSE) 파일을 참조하십시오.
