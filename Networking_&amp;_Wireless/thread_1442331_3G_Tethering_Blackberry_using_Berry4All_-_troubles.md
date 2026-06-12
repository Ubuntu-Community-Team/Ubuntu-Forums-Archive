---
title: "3G Tethering Blackberry using Berry4All - troubleshooting"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by ironwolfe on 2010-03-29
My blackberry works tethered to my Windows Machine using the following parameters:

```
Disable IP Header Compression
Make sure TCP/IP Properties (Advanced) "Use IP Header Compression" checkbox is NOT checked. To verify this, do these steps:
Quote:
1. Start Menu->Network Connections->"BlackBerry Modem"
2. Click Properties Button
3. Click Networking Tab
4. Select "Internet Protocol (TCP/IP)"
5. Click Properties Button
6. Click Advanced... Button
7. Disable "Use IP header compression" checkbox
8. Click all OK buttons to close all dialogs
Also make sure you clear all these checkboxes, if you see any of these checked:
Turn off "Enable Hardware Flow Control"
Turn off "Enable Modem Error Control"
Turn off "Enable Modem Compression"
```


Using Karmic 9.10 I can tether it on 2G (EDGE) using the standard Berry4All (ppd scripts) 


```

ian@ian-minihp:~/bbtether/conf$ nano rogers
  GNU nano 2.0.9                   File: rogers

# Tested by Max Taranukha
115200
noipdefault
defaultroute
#nomultilink
ipcp-restart 7
ipcp-accept-local
ipcp-accept-remote
lcp-echo-interval 0
lcp-echo-failure 999
nopcomp
noaccomp
pap-timeout 20
pap-restart 20
lcp-restart 10
#noauth
crtscts
usepeerdns
nomagic
noccp
novj
user wapuser
password wap
name wapuser
#debug debug debug
# does not exist in all pppd versions (osx)
#replacedefaultroute

connect "/usr/sbin/chat -f conf/rogers-chat"

```

Normally it connects and PAP authorizes then just terminates connection giving the error
```
Could not determine local IP address
```

so I googled it [http://pptpclient.sourceforge.net/howto-diagnosis.phtml#cndlia]("http://pptpclient.sourceforge.net/howto-diagnosis.phtml#cndlia")

and it said that it is having trouble providing a local IP, so it suggested adding the following line:

```
10.0.0.1:
```

And it no longer terminates and successfully stays connected with a remote IP even.  But I cannot connect to it.

The chatscript is working great - it is the pppd script that has some issues.

I am trying to connect to Rogers in Canada (similar to ATT)

 are there any ppp guru's out there?  How do I get a local IP?

---

### Post by matt.parkes on 2010-04-06
Which version of berr4all are you using?  I could get tethering to work 2G/EDGE only with the newest version.  After trying the version people suggested in the comments it no longer works.  It is erroring out with your same error.  I'd suggest removing it completely and reinstalling the newest version. I'm wondering if anyone has had any luck on Rogers with the Berry4all on 3G/HSDPA.

Thanks

---

### Post by yusery on 2010-07-30
Hii..

Try switch back to 3G after the connection is established at your BB phone.

Its work for me.

---

### Post by at2it on 2010-09-24
Any update on this?

I've tried with a Bold 9000 and a Bold 9700 without success (on 3G).

I too am able to connect on EDGE, but 3G gives me the > "Could not determine local IP address" error.

Connecting on EDGE and switching to 3G does not work for me. It either stays on EDGE speeds or disconnects completely.

---

### Post by Brebs on 2011-01-04
> Could not determine local IP address
Remove the **novj** option.

---

