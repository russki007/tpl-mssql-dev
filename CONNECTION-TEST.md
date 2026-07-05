# MSSQL Connection Test Commands

## 1. From inside the devcontainer (VS Code terminal)

```bash
sqlcmd -S localhost,1433 -U sa -P 'Admin123!' -Q "SELECT @@VERSION"
```

## 2. From Windows host

**sqlcmd:**

```cmd
sqlcmd -S localhost,1434 -U sa -P "Admin123!" -Q "SELECT @@VERSION"
```

**SQL Server Management Studio:**

- Server name: `localhost,1434`
- Authentication: SQL Server Authentication
- Login: `sa`
- Password: `Admin123!`

## 3. From WSL2 (outside the container)

The IP of the WSL may change. You need to look it up as follows:

```bash
# Find your WSL IP address
ip addr show eth0 | grep inet
```

```bash
sqlcmd -S 172.29.174.233,1434 -U sa -P 'Admin123!' -Q "SELECT @@VERSION"
```

> **Note:** WSL2 and Windows share the same network for localhost, so both use port **1434** (the forwarded host port). Only inside the devcontainer do you use **1433** directly.
