---
title: "Help Getting remote frontend started"
date: 2011-09-28
forum: Mythbuntu
---

### Post by GooKing on 2011-09-28
Hi All, Having issues with a remote frontend. Starting using GUI gives lots of disk loading, and it shows as a process, but nothing on screen. Starting in command line gives the following:


```
2011-09-29 01:00:46.364 Using runtime prefix = /usr
2011-09-29 01:00:46.364 Using configuration directory = /home/gooking/.mythtv
2011-09-29 01:00:46.386 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-09-29 01:00:47.515 Empty LocalHostName.
2011-09-29 01:00:47.515 Using localhost value of diningroom1
2011-09-29 01:00:47.516 Testing network connectivity to '10.0.2.13'
2011-09-29 01:00:47.944 New DB connection, total: 1
```

And there it will hang until cancelled

Both systems are Mythbuntu. Backend is new hardware, and also runs a frontend with no issues. Remote front end is ancient dell hardware.

Steps so far - Backend:
Updated to 0.24
Updated IP address in GUI setup to real IP address
Entered 0000 as PIN code
Modified one mysql text file to allow remote connections
Reset DB user/password

Front End:
Updated to 0.24
Re-run setup
Tested SQL link with MySQL command line - connection was accepted, can list tables.


Any suggestions for test/fixes?

---

### Post by thatguruguy on 2011-09-28
> **GooKing said:**
> 
Updated IP address in GUI setup to real IP address
Did you do that in both places?

> **GooKing said:**
>  Entered 0000 as PIN code
No reason to even touch that setting, really.

> **GooKing said:**
> Modified one mysql text file to allow remote connections
Why?
> **GooKing said:**
> Reset DB user/password
Why?

---

### Post by GooKing on 2011-09-28
1) Yes, both field set to real external IP
2) Ok
3) Default MySQL was listening on localhost only. Changed to IP address. Works as I can now get a command line connection.
4) Just did! Definitely correct now, since I have worked out how to use command line SQL a bit.

---

### Post by azmyth on 2011-09-29
I'd look in your /var/log/auth.log and your mysql log that's listed in your /etc/mysql/my.cnf file on the back-end PC. If it's not turned on in your my.cnf I'd turn on logging. I have a feeling your having a permission problem.

---

### Post by thatguruguy on 2011-09-29
> **GooKing said:**
> 1) Yes, both field set to real external IP
2) Ok
3) Default MySQL was listening on localhost only. Changed to IP address. Works as I can now get a command line connection.
4) Just did! Definitely correct now, since I have worked out how to use command line SQL a bit.

If number 4 means that you've sorted out your problem, feel free to mark this thread as solved.

---

### Post by GooKing on 2011-09-29
> **azmyth said:**
> I'd look in your /var/log/auth.log and your mysql log that's listed in your /etc/mysql/my.cnf file on the back-end PC. If it's not turned on in your my.cnf I'd turn on logging. I have a feeling your having a permission problem.

Thanks, will do this weekend and update this thread.

---

