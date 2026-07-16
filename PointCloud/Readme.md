#PointCloud

3D LiDAR Data를 받아서 Point 구체 형태로 표현하는 프로젝트


대용량 그래픽 데이터 최적화: GPU 자원을 효율적으로 쓰기 위해 대용량 정점 데이터를 런타임에 직접 동적 생성하지 않고 THREE.DynamicDrawUsage 옵션의 고정 버퍼 메모리(maxPoints: 2,000,000)를 재사용(VRAM Pooling)했습니다.

Non-blocking UI 아키텍처: 수백만 개의 좌표를 일시에 로드할 때 자바스크립트의 싱글 스레드 특성상 발생하는 화면 멈춤(Freeze)을 막기 위해 50,000개 단위의 청크(Chunk) 스케줄링 기법을 적용하여 60FPS의 안정적인 UI 반응성을 보장했습니다.

하이브리드 모바일 연동 인프라: 네이티브 기기 통신용 Web Message Bridge를 설계하여 하드웨어 센서 데이터를 실시간 디코딩하고, 짐벌락(Gimbal Lock) 방지를 위해 오일러각을 쿼터니언 변환 연산하여 완벽하게 기기 동적 회전을 트래킹했습니다.
