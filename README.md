# 🖥️Form Tag 데이터 처리 프로젝트


## 📋 프로젝트 개요
JSP 기반 웹 애플리케이션에서 HTML `<form>` 태그를 활용해 사용자 입력 데이터를 받고, 파일 업로드 및 다양한 입력값을 처리해 결과를 출력하는 프로젝트입니다.

---

## ✨ 주요 기능
- 파일 업로드 및 서버 저장 (중복 파일명 자동 처리)  
- 학번, 이름, 전화번호, 이메일, 성별, 수강 과목(복수 선택), 학년, 소개글 입력  
- MultipartRequest를 통한 파라미터 수집 및 처리  
- DTO 객체(`ccc`)를 통한 데이터 관리  
- 입력 데이터 테이블 형식 출력 및 업로드 이미지 출력  
- 입력폼으로 다시 돌아가는 링크 제공  

---

## 🛠 사용 기술
- Java, JSP  
- Apache Tomcat 서버  
- cos.jar (com.oreilly.servlet 패키지)  
- HTML, CSS  

---

## 📂 프로젝트 구조
/webapp  
│  
├── form.jsp # 입력 폼  
├── result.jsp # 입력 데이터 처리 및 출력  
├── upload/ # 업로드 파일 저장 폴더  
│  
/src/aaa/bbb  
└── ccc.java # 사용자 정보 DTO 클래스


---

## 🖼️ 실행 화면
- 입력폼: 학번, 이름, 전화번호, 이메일 등 다양한 필드 입력 가능  
- 결과화면: 입력된 데이터 테이블 출력, 업로드한 사진 표시

---

## 💻 주요 코드 예시

### form.jsp (입력 폼 일부)
```jsp
<form action="result.jsp" method="post" enctype="multipart/form-data">
    파일 : <input type="file" name="filename"><br>
    학번: <input type="text" name="studentId"><br>
    이름: <input type="text" name="name"><br>
    전화번호: 
    <select name="phone1">
        <option value="010">010</option>
        <option value="011">011</option>
        <option value="02">02</option>
    </select> - 
    <input type="text" maxlength="4" name="phone2"> - 
    <input type="text" maxlength="4" name="phone3"><br>
    <!-- 기타 필드 생략 -->
    <input type="submit" value="제출">
</form>
```

### form.jsp (입력 폼 일부)
```jsp
String uploadPath = application.getRealPath("/upload");
MultipartRequest multi = new MultipartRequest(request, uploadPath, 5 * 1024 * 1024, "utf-8", new DefaultFileRenamePolicy());

String filename = multi.getFilesystemName("filename");
String studentId = multi.getParameter("studentId");
// 기타 파라미터 처리

ccc student1 = new ccc();
student1.setStudentId(studentId);
// DTO에 값 세팅
```

---


## 🖼️예시사진


<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/64f24ac5-cc28-4091-8d41-ed8c34dbcd78" width="200"/></td>
    <td><img src="https://github.com/user-attachments/assets/0fd06b2d-8967-422b-9067-b7de78f64719" width="200"/></td>
  </tr>
</table>

---


## 📝배운점
JSP에서 MultipartRequest를 활용한 파일 업로드 처리 경험  
다양한 폼 데이터(텍스트, 체크박스, 라디오 버튼 등) 처리 방법 습득  
DTO 객체 활용으로 데이터 관리 효율성 향상  
사용자 친화적인 결과 화면 출력 구현  

