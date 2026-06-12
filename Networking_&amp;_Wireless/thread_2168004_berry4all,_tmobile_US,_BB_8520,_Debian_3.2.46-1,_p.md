---
title: "berry4all, tmobile US, BB 8520, Debian 3.2.46-1, pppd error connection time out"
date: 2013-08-16
forum: Networking &amp; Wireless
---

### Post by mochatime on 2013-08-16
UbuntuForums,

I'm attempting to use [berry4all]("http://www.berry4all.com/home") (01/27/2012, bbtether-0.3q.tgz, extracted to home/username directory, not root ) with Debian Wheezy connecting a BB Curve 8520 over USB to T Mobile and getting connection errors; syslog file says, 

**"pppd [pid#]: The remote system is required to authenticate itself, but I could not find any suitable secret (password) for it to use to do so."**

The berry4all python script I'm running as root is:  python bbtether.py tmobile -v .  The output from this statement is:

[B]Looking for USB devices:
    Bus 005 Device 002: ID 0483:2016
    Bus 005 Device 001: ID 1d6b:0001
    Bus 004 Device 001: ID 1d6b:0001
    Bus 003 Device 001: ID 1d6b:0001
    Bus 002 Device 001: ID 1d6b:0001
    Bus 001 Device 002: ID 0fca:8004
    Bus 001 Device 001: ID 1d6b:0002
USB Device lookup finished
Reading prefs from /root/.bbtether.conf
Using saved EP data: 0, 135, 9, 138, 11

Using Data Endpoint Pair:0x87/0x9
Using Modem pair: 0x8a/0xb

Claiming interface 0
    -> [0x0 0x0 0xc 0x0 0x5 0xff 0x0 0x0 0x0 0x0 0x4 0x0 ] [............][/B]

I'm just noticing 6 lines above "/root/.bbtether.conf" ... is a file that I do not have.  The only dot files I have in my root directory are .pulse and ..pulse-cookie.

More output just appears to me to be the time out:
[B]
Pin: 0x********
Description: RIM BlackBerry Device
System: Linux,3.2.0-4-686-pae,#1 SMP Debian 3.2.46-1,i686

Modem pty: /dev/pts/3
Initializing Modem
Writing data size: 12
    Modem -> [0x1 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x78 0x56 0x34 0x12 ] [........xV4.]
error: Connection timed out
#error: Connection timed out[/B]

I'm using the script defaults in the config file, which is " connect /usr/sbin/chat -f ./conf/tmobile-chat " and the wap.voicestream.com APN

Of note on my BB:  Settings->Options->Advanced Options->TCP/IP->APN Settings Enabled, APN: epc.tmobile.com

I've successfully tethered this BB to an Apple Macbook (10.6.8) using both wap.voicestream.com and epc.tmobile.com (both with blank user/pass, and gprs user/pass).

As per the [/help page]("http://www.berry4all.com/faqs"), I modified the config file to use an explicit path for tmobile-chat.  After doing so, no change in output either verbose from the script or in syslog.

A point in the right direction or assistance of any kind would be appreciated.

--mochatime

---

### Post by mochatime on 2013-08-21
Removed reply due to formatting

---

