# 3.7.0

Release Date: 2020-01-29

### 버그 수정

- 카메라의 영역을 제한하고 영역 바깥쪽에서 제스처로 지도를 스크롤하면 카메라가 잘못된 위치로 이동하는 현상 수정 
- 코드로 `NMFNaverMapView` 생성 시 최초 로딩이 안되는 현상 수정
- 두 개 이상의 맵뷰 생성 시 첫 번째 맵뷰 제외하고 최초 로딩이 안되는 현상 수정

### 새로운 기능

- 지도의 줌 레벨과 오버레이의 최소/최대 줌 레벨이 동일할 때 오버레이를 보일지 여부를 지정하는 기능 추가
  - `NMFOverlay.isMinZoomInclusive` / `NMFOverlay.isMaxZoomInclusive`
- 특정 영역이 화면에 온전히 보이는 최대 줌 레벨을 반환하는 유틸리티 메서드 추가
  - `NMFCameraUtils.getFittableZoomLevelWith`

### 개선

- 경로선 진척률을 음수로 지정할 수 있도록 개선
  - `NMFPath.progress` / `NMFMultipartPath.progress`

# 3.6.1

Release Date: 2019-12-11

### 버그 수정

- 정보 창을 마커에 열 경우 간헐적으로 지도와 마커 간의 싱크가 맞지 않는 현상 수정
- 경로선이 간헐적으로 심벌 위에 나타나는 현상 수정
- 일부 도로 번호가 비뚤게 나타나는 현상 수정

# 3.6.0

Release Date: 2019-10-07

### 새로운 기능

- 마커 캡션의 최소/최대 줌 레벨을 아이콘과 별도로 지정할 수 있는 기능 추가
  - `NMFMarker.captionMaxZoom`, `captionMinZoom`
- 마커 캡션이 다른 요소와 겹칠 경우 동적으로 다른 곳에 배치하는 옵션 추가
  - `NMFMarker.captionAligns`
  - `NMFAlign` 열거형 대신 `NMFAlignType` 클래스 속성 사용
- 마커가 충돌되어 사라지더라도 자신의 영역을 유지하도록 하는 옵션 추가
  - `NMFMarker.occupySpaceOnCollision`
- 경로선과 겹치는 마커, 캡션, 지도 심벌을 숨기는 기능 추가
  - `NMFPath.isHideCollidedSymbols` / `isHideCollidedMarkers` / `isHideCollidedCaptions`
  - `NMFMultipartPath.isHideCollidedSymbols` / `isHideCollidedMarkers` / `isHideCollidedCaptions`
- 카메라 이동 트랜지션 취소 시 원인을 전달할 수 있도록 `reason` 파라메터 추가
  - `NMFMapView.cancelTransitions(NSInteger)`

### 개선

- `NMFGroundOverlay`, `NMFInfoWindow`에서 더 큰 이미지를 사용할 수 있도록 지원
- 메모리 사용량 개선

### 버그 수정

- `NMFPolylineOverlay`의 `capType`, `joinType`이 적용되지 않는 오류 수정
- `NMFPolylineOverlay`에 일부 크랙이 발생하는 현상 수정
- `extent`를 지정하고 지도를 빠르게 패닝하면 지도가 잘못된 방향으로 이동하는 현상 수정
- 마커가 충돌되어 사라지는 중에 충돌하지 않는 곳으로 위치를 변경하면 하면 페이드인이 일어나는 현상 수정
- 지도 회전시 일부 심벌이 번쩍이는 현상 수정
- 지도 뷰의 높이가 작을 때 경로선 패턴이 나타나지 않는 현상 수정
- 높이가 너비보다 큰 이미지를 경로선 패턴으로 사용하면 패턴이 부자연스럽게 나타나는 현상 수정

# 3.5.0

Release Date: 2019-08-12

### 새로운 기능

- 배경 지도를 그리지 않는 지도 유형 추가
  - `NMFMapTypeNone`
- 밝은/어두운 기본 배경색을 각각 상수로 제공
  - `NMFDefaultBackgroundLightColor`, `NMFDefaultBackgroundDarkColor`

### 개선

- `NMFPolygonOverlay`의 외곽선 퀄리티 개선
- 성능 및 데이터 사용량 개선

### 버그 수정

- `NMFPolygonOverlay`사용중 `NMGPolygon`객체의 `interiorRings`가 존재할 경우 일부 영역이 비정상적으로 렌더링되는 오류 수정
- 경로의 길이가 매우 긴 경우 `- NMFGeometryUtils.progressWithLatLngs`, `- NMFGeometryUtils.progressWithLineStrings`의 오차가 큰 오류 수정
- 일부 지도 심벌이 경로선 아래에 나타나는 현상 수정
- 남/북극을 초과하는 영역에 배경색이 적용되지 않는 현상 수정
- 일부 아랍 문자가 노출되지 않는 현상 수정

# 3.4.0

Release Date: 2019-06-07

### 새로운 기능

- Path 및 Polygon 오버레이에서 속성 및 생성자 추가
  - `NMFPath.pathWithLineString`
  - `NMFMultipartPath.multipartPath`
  - `NMFPolygonOverlay.polygonOverlayWith`
- Projection, InfoWindow 데모 추가

### 개선

- Path 및 Polygon 오버레이의 속성 및 메서드 변경
  - `NMFPath.points` -> `NMFPath.path`
  - `NMFPath.pathWithPoints` 매개변수로 `NMGLatLng` 배열 받음
  - `NMFMultipartPath.coordParts` -> `NMFMultipartPath.lineParts`
  - `NMFMultipartPath.multipartPathWithCoordParts` -> `NMFMultipartPath.multipartPathWith`
  - `NMFPolygonOverlay.updatePolygon` -> `NMFPolygonOverlay.polygon`
- 실내지도 층 컨트롤 연결층 텍스트 추가
- 앱 사용중에만 위치 권한을 받도록 수정

# 3.3.0

Release Date: 2019-04-08

### 새로운 기능

- 유형이 다른 오버레이간의 겹침 우선순위를 지정하는 기능 추가
  - `NMFOverlay.globalZIndex`
- 마커 아이콘에 색상을 덧입히는 기능 추가
  - `NMFMarker.iconTintColor`
- 현재 화면을 커버하는 타일 ID를 가져오는 기능 추가
  - `NMFTileCoverHelper`

### 개선

- 심벌 렌더링 성능 개선
- bitcode 적용
  - 바이너리 용량 증대로 [git-lfs](https://git-lfs.github.com/)가 적용되었습니다. [git-lfs](https://git-lfs.github.com/)를 필수로 설치해야합니다.
- 내위치 버튼을 사용하지 않아도 positionMode 가 동작하도록 개선

### 버그 수정

- 빌딩 레이어 그룹(`NMF_LAYER_GROUP_BUILDING`)이 기본적으로 비활성화되어 있는 오류 수정
- 특정 심벌 피킹시 간혹 크래시가 발생하는 오류 수정
- 지도 SDK 사용시 `LocalizedString`이 동작하지않는 오류 수정

# 3.2.1

Release Date: 2019-02-22

### 개선

- 지도 로딩 속도 및 데이터 사용량 개선

### 버그 수정

- 마커 캡션에 이모지 사용시 간헐적으로 크래시가 발생하는 오류 수정

# 3.2.0

Release Date: 2019-02-14

### 새로운 기능

- 공공기관용 네이버 클라우드 플랫폼 지원
  - `NMFMAuthManager.govClientId`

### 개선

- 오버레이의 비트맵을 오버레이가 화면에 나타나는 순간에 백그라운드에서 디코딩하도록 개선
- 마커 캡션에 이모지를 넣을 수 있도록 개선

### 버그 수정

- `isHideCollidedSymbol`이 `true`인 마커를 추가/삭제할 때 심벌이 재배치되지 않는 현상 수정
- 줌 변경시 지도 심벌이 겹쳐나오는 현상 수정
- 지도 로딩시 검은 화면이 잠깐 나타났다 사라지는 현상 수정
- 앱이 백그라운드에 있을 때 지도 API를 호출하고 포그라운드로 전환하면 화면이 즉시 갱신되지 않는 오류 수정
- 시계방향으로 10도 미만 회전 된 경우 0도로 되돌아 가지 않는 오류 수정
- 지도에 contentInset을 지정 할 때 cameraPosition이 업데이트 되지 않는 오류 수정

# 3.1.0

Release Date: 2019-01-21

### 새로운 기능

- 마커 아이콘과 다른 마커 간 겹침시 숨김 옵션 추가
  - `NMFMarker.isHideCollidedMarkers`
  - `NMFMarker.isForceShowIcon`
- 네이버 로고 위치 변경 기능 제공
  - `NMFMapView.logoAlign`
  - `NMFMapView.logoMargin`

### 개선

- `NMFCircleOverlay`의 테두리 퀄리티 개선
- SDK 내에서 사용하는 문자열에 다국어 대응 추가
- SDK 사용 인증시 인터넷 연결이 되지 않을 경우 인증 실패로 간주하지 않고 연결을 기다리도록 개선

### 버그 수정

- `NMFInfoWindow`의 `-openWithMarker:`를 여러 마커에 대해 호출시 크래시가 발생하는 오류 수정
- `NMFMapType`이 `NMFMapTypeSatellite`일 때 지상, 폴리라인, 폴리곤, 경로선 오버레이가 나타나지 않는 오류 수정
- 간헐적으로 일부 심벌 캐릭터가 이상한 문자로 노출되는 현상 수정
- 줌 레벨 변경시 심벌 사이즈가 부자연스럽게 커졌다 작아지는 현상 수정
- 마커 추가시 페이드 인 애니메이션이 무조건 발생하는 현상 수정
- 제스처를 모두 막은 상태에서 Pinch 제스처로 지도 이동하는 오류 수정
- 오버레이 이미지가 간헐적으로 중복되는 오류 수정
- `NMFProjection.latlngBoundsFromViewBounds`사용시 크기가 0인 `NMGLatLngBounds`를 반환하는 오류 수정

# 3.0.0

Release Date: 2018-11-12

Initial Release
