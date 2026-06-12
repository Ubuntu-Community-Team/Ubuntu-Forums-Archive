---
title: "AWUS036H and Airmon-ng"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by geminidpr on 2010-05-09
I'm trying to run airmon-ng and below is what I get. I'm using ubuntu 9.1 and it does recognize that card (awus036h) in fact I'm using it to right now to write this post. I installed "Root" thinking thats what I needed but I still can't run that program. I'm a newbie at this so please don't get pissed and lecture me like other forums do to newbies sometimes. Remember,we were all newbies at one time.

geminidpr@geminidpr-laptop:~$ airmon-ng
Run it as root
geminidpr@geminidpr-laptop:~$ root
  *******************************************
  *                                         *
  *        W E L C O M E  to  R O O T       *
  *                                         *
  *   Version  5.18/00b     10 March 2008   *
  *                                         *
  *  You are welcome to visit our Web site  *
  *          [http://root.cern.ch](http://root.cern.ch)            *
  *                                         *
  *******************************************

ROOT 5.18/00b (branches/v5-18-00-patches@22563, Nov 13 2009, 08:35:00 on linux)

CINT/ROOT C/C++ Interpreter version 5.16.29, Jan 08, 2008
Type ? for help. Commands must be C++ statements.
Enclose multiple statements between { }.
root [0] airmon-ng
Error: Symbol airmon is not defined in current scope  (tmpfile):1:
Error: Symbol ng is not defined in current scope  (tmpfile):1:
(const int)0
*** Interpreter error recovered ***
root [1]

---

### Post by geminidpr on 2010-05-10
I found out all I needed to do is type gksu B4 the command to run the program as root. This will benefit other newbies in the future. Below is an example:

geminidpr@geminidpr-laptop:~$ gksu airmon-ng

---

