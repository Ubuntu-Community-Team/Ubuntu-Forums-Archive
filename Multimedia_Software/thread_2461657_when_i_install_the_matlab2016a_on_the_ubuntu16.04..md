---
title: "when i install the matlab2016a on the ubuntu16.04.7,when i type ./install on the term"
date: 2021-05-05
forum: Multimedia Software
---

### Post by yk0vpusdf85mz4tks on 2021-05-05
when i install the matlab2016a on the ubuntu16.04.7,when i type ./install on the terminal,it's display :
how can solve this ?

$./install
Preparing installation files ...
Installing ...
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f458cf86550, pid=3981, tid=139936649860864
#
# JRE version:  (7.0_60-b19) (build )
# Java VM: Java HotSpot(TM) 64-Bit Server VM (24.60-b09 mixed mode linux-amd64 compressed oops)
# Problematic frame:
# V  [libjvm.so+0x5f8550]  InterpreterRuntime::quicken_io_cc(JavaThread*)+0x10
#
# Core dump written. Default location: /home/jacob/Documents/matlab2016alinux64/core or core.3981
#
# An error report file with more information is saved as:
# /home/jacob/Documents/matlab2016alinux64/hs_err_pid3981.log
#
# If you would like to submit a bug report, please visit:
#   [http://bugreport.sun.com/bugreport/crash.jsp](http://bugreport.sun.com/bugreport/crash.jsp)
#
Finished

---

### Post by scorp123 on 2021-05-05
Did you check the log it tells you to check?

---

### Post by TheFu on 2021-05-05
Standard support for 16.04 Server ended in April.  If there are any issues, it hasn't been worth figuring those out on that release for about 6-12 months. 

New installs should be 20.04.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) has the support schedule.
[https://ubuntu.com/blog/what-is-an-ubuntu-lts-release](https://ubuntu.com/blog/what-is-an-ubuntu-lts-release) shows how to get paid support, which is what you need with 16.04.

---

