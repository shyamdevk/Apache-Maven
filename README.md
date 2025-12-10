# 🚀 Apache Maven

![Apache maven](maven.png)

Apache Maven is a **build automation** and **project management tool** used mainly for **Java projects**.  
It helps developers **compile, test, package, and manage dependencies** easily using one configuration file: `pom.xml`.

---

## 🧱 What is Apache Maven?
Apache Maven is a tool that **automates the entire build process**.  
It removes the need to manually download libraries or write long build scripts.

**In simple words:**  
➡️ *Maven builds your Java project and downloads everything your project needs automatically.*

---

## 🎯 Why Do We Use Maven?
- ✔ **Manages dependencies** (libraries downloaded automatically)  
- ✔ **Standard project structure** → easy for teams  
- ✔ **Automates build** (compile → test → package)  
- ✔ **Uses `pom.xml` for configuration**  
- ✔ **Works the same everywhere** (CI/CD friendly)  

---

## 📄 POM (Project Object Model)
`pom.xml` is the **heart of Maven**.  
It contains:
- Project name, version  
- Required dependencies  
- Build plugins  
- Repositories  
- Packaging type (JAR/WAR)

### ✔ Example Dependency Block
```xml
<dependency>
  <groupId>org.springframework</groupId>
  <artifactId>spring-core</artifactId>
  <version>5.3.20</version>
</dependency>
````

➡️ Maven reads this and **automatically downloads** the correct library.

---

## 📦 Dependencies

These are **external libraries** that your project needs.
Example: Spring Boot, MySQL Connector, Gson, etc.

Maven downloads dependencies from:

* **Local Repository** → on your computer
* **Maven Central** → global public repo
* **Remote Repositories** → (optional, company repos)

---

## 🔄 Maven Build Lifecycle (Simple Explanation)

Maven follows a fixed sequence called the **build lifecycle**:

| Phase      | Simple Meaning              |
| ---------- | --------------------------- |
| `validate` | Check project correctness   |
| `compile`  | Compile Java code           |
| `test`     | Run test cases              |
| `package`  | Create JAR/WAR file         |
| `verify`   | Extra checks                |
| `install`  | Add build to local repo     |
| `deploy`   | Upload build to remote repo |

Most commonly used:

```
mvn clean package
```

---

## 🧰 Common Maven Commands

| Command       | Description                   |
| ------------- | ----------------------------- |
| `mvn compile` | Compiles Java code            |
| `mvn test`    | Runs tests                    |
| `mvn package` | Builds JAR/WAR                |
| `mvn clean`   | Deletes old build files       |
| `mvn install` | Installs output to local repo |
| `mvn deploy`  | Pushes build to remote repo   |

---

## 📁 Standard Maven Project Structure

```
project/
 ├── src/
 │    ├── main/
 │    │     ├── java/        # Java source files
 │    │     └── resources/   # Config files
 │    └── test/
 │          ├── java/        # Test code
 │          └── resources/
 └── pom.xml
```

➡️ This structure is the **same** in all Maven projects → makes things easy to understand.

---

## 🔌 Maven Plugins

Plugins add additional features.

Common plugins:

* **Compiler Plugin** → controls Java version for compiling
* **Surefire Plugin** → runs test cases
* **Shade Plugin** → create fat JAR (single runnable JAR)

Example plugin:

```xml
<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-compiler-plugin</artifactId>
  <version>3.8.1</version>
  <configuration>
    <source>17</source>
    <target>17</target>
  </configuration>
</plugin>
```

---

## ⭐ Summary (Super Simple)

| Concept          | Meaning                                   |
| ---------------- | ----------------------------------------- |
| **Maven**        | Tool to build/manage Java projects        |
| **POM**          | XML file with project info & dependencies |
| **Dependencies** | External libraries                        |
| **Lifecycle**    | Steps Maven follows to build              |
| **Commands**     | compile, test, package, clean             |

---

# 🏗️ Maven Architecture 

![Maven GIF](archi.png)
---

## 🧱 1. Local Repository
The **local repository** is a folder on your computer where Maven stores all downloaded libraries.

➡️ When you build a project, Maven **first checks the local repo** to see if the required dependency already exists.

If found → Maven uses it directly (faster builds).

---

## 🌐 2. Remote Repository
If a dependency is **not found** locally, Maven downloads it from a **remote repository** like Maven Central using **HTTP**.

➡️ Remote repo = Internet storage for Java libraries.

---

## ⚙️ 3. Maven Build System
Maven uses configuration files such as:

- `pom.xml` (main file used today)
- Older formats like `project.xml` or `maven.xml` (shown in diagrams)

These files tell Maven:
- What dependencies the project needs  
- How to build, test, and package the project  

➡️ Maven reads this file and controls the entire build process.

---

## 🗂️ 4. Communication Flow
- **Maven ↔ Local Repository** → Quickly checks local storage first  
- **Maven ↔ Remote Repository** → Downloads required dependencies if missing  

---

## 📄 5. Maven Site (Optional)
Maven can generate a **project website** that includes documentation, reports, and project details.

➡️ This is optional but useful for large projects.

---

## ⭐ Summary (Very Simple)
- **Local Repo** → First place Maven checks for libraries  
- **Remote Repo** → Downloads missing libraries  
- **Maven Build System** → Reads `pom.xml` and builds your project  
- **Site** → Optional documentation output  

Maven mainly acts as a bridge between your project and these repositories to make building easier and automatic.

---
# 📦 Maven Example Code with Simple Explanation

## 🧩 Sample `pom.xml`

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
         http://maven.apache.org/xsd/maven-4.0.0.xsd">

    <!-- 1. Model Version -->
    <modelVersion>4.0.0</modelVersion>

    <!-- 2. Basic Project Information -->
    <groupId>com.example</groupId>
    <artifactId>maven-demo</artifactId>
    <version>1.0.0</version>
    <packaging>jar</packaging>

    <!-- 3. Project Name -->
    <name>Maven Demo Project</name>

    <!-- 4. Dependencies Section -->
    <dependencies>
        <!-- Example dependency: Gson library -->
        <dependency>
            <groupId>com.google.code.gson</groupId>
            <artifactId>gson</artifactId>
            <version>2.10.1</version>
        </dependency>
    </dependencies>

    <!-- 5. Build Section with Plugins -->
    <build>
        <plugins>

            <!-- Compiler Plugin -->
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <source>17</source>
                    <target>17</target>
                </configuration>
            </plugin>

        </plugins>
    </build>

</project>
````

---

# 📝 Explanation of the Code (Simple & Beginner Friendly)

## 1️⃣ Model Version

```xml
<modelVersion>4.0.0</modelVersion>
```

* This is always **4.0.0** for modern Maven projects.
* It tells Maven which POM structure to follow.

---

## 2️⃣ Basic Project Details

```xml
<groupId>com.example</groupId>
<artifactId>maven-demo</artifactId>
<version>1.0.0</version>
<packaging>jar</packaging>
```

* **groupId** → Your organization/project base name
* **artifactId** → Your application or module name
* **version** → Version number of your build
* **packaging** → Output format (`jar`, `war`, etc.)

➡️ This is how Maven identifies and names your project output.

---

## 3️⃣ Project Name

```xml
<name>Maven Demo Project</name>
```

A readable name for your project (used in reports and logs).

---

## 4️⃣ Dependencies

```xml
<dependencies>
    <dependency>
        <groupId>com.google.code.gson</groupId>
        <artifactId>gson</artifactId>
        <version>2.10.1</version>
    </dependency>
</dependencies>
```

* Dependencies are **external libraries** your project needs.
* Example here: **Gson**, used to work with JSON.
* Maven automatically downloads this library for you.

➡️ You don’t need to manually download JAR files — Maven handles it!

---

## 5️⃣ Build Section + Plugins

```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-compiler-plugin</artifactId>
            <version>3.8.1</version>
            <configuration>
                <source>17</source>
                <target>17</target>
            </configuration>
        </plugin>
    </plugins>
</build>
```

### ✔ What this plugin does:

* Tells Maven to use **Java 17** for compiling code.
* Ensures your code follows the correct Java version.

➡️ Without this, Maven might use an older Java version.

---

## ⭐ Summary (Super Simple)

| Section          | Purpose                              |
| ---------------- | ------------------------------------ |
| **Project Info** | Identifies the project               |
| **Dependencies** | Libraries to download automatically  |
| **Plugins**      | Tools that modify the build behavior |
| **Build Config** | Controls compilation settings        |

Maven uses this file to completely automate your project's build process.

---



