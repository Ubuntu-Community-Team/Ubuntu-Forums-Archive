---
title: "How to Tether Blackberry Bold with Ubuntu 9.04"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by mozilla2004 on 2009-12-08
I want to use my blackberry bold as a modem to connect my laptop with ubuntu 9.04 to the internet so that i can browse webpages.

Can someone give me step by step instructions on how to do this?  I am new to linux, so hopefully someone can recommend a manual that I can understand.

I installed Barry, but not sure if I missed a step or what to do next.

---

### Post by jbslaw on 2009-12-08
Try Berry4all.  [http://www.berry4all.com/home]("http://www.berry4all.com/home")  Be aware of the dependencies listed on the installation page.

You should read some of the comments there.  There are some issues with 3G connectivity, apparently, but if you're okay with 2G it is quite easy and reliable.

---

### Post by mozilla2004 on 2009-12-09
I have everythign installed.  When i tried to run berry4all using the conf/bellmobility setting, the gui ends with the following lines

PAP authentication succeeded
LCP terminated by peer
Connection Terminated

I looked at the comments in berry4all.com, but no one mentions this problems.  Also, no one seems to be responding to the others problems mentioned in the comments.

Any suggestions?

---

### Post by matt.parkes on 2010-01-26
> **jbslaw said:**
> Try Berry4all.  [http://www.berry4all.com/home]("http://www.berry4all.com/home")  Be aware of the dependencies listed on the installation page.

You should read some of the comments there.  There are some issues with 3G connectivity, apparently, but if you're okay with 2G it is quite easy and reliable.

Has anyone figured out how to get this to work on ROGERS with 3G speeds? It's working fine if I set my network connection to 2G/EDGE.

Ideas?  Is there an official forum for this application?

---

### Post by ironwolfe on 2010-03-29
Resurrecting this post

I am in the same boat - 2G works but not 3G.

i am using Rogers in Canada.  I have a feeling it is the either the chatscript or the pppd script.

here is the chat script.  Notice it says it needs the ~p at the end.  I will try later to see if I remove this if it works.  The author of the software admits he only has 2G so it isn't likely that he has tested it.

Ian

```
ian@ian-minihp:~/bbtether/conf$ ls
total 120K
-rw-r--r-- 1 ian ian 415 2009-03-09 10:05 att
-rw-r--r-- 1 ian ian 288 2009-03-10 10:18 att-chat
-rw-r--r-- 1 ian ian 447 2009-07-21 11:09 bellmobility
-rw-r--r-- 1 ian ian 288 2009-07-21 11:09 bellmobility-chat
-rw-r--r-- 1 ian ian 415 2009-09-10 12:00 fido
-rw-r--r-- 1 ian ian 304 2009-09-10 12:01 fido-chat
-rw-r--r-- 1 ian ian 433 2009-07-21 10:44 orange
-rw-r--r-- 1 ian ian 487 2009-11-05 10:29 orange-alt
-rw-r--r-- 1 ian ian 339 2009-11-05 10:29 orange-alt-chat
-rw-r--r-- 1 ian ian 291 2009-07-21 10:42 orange-chat
-rw-r--r-- 1 ian ian 425 2009-03-09 10:05 porta
-rw-r--r-- 1 ian ian 305 2009-03-10 10:18 porta-chat
-rw-r--r-- 1 ian ian 441 2009-03-09 10:05 rogers
-rw-r--r-- 1 ian ian 288 2009-03-10 10:18 rogers-chat
-rw-r--r-- 1 ian ian 702 2009-09-10 12:12 sfr
-rw-r--r-- 1 ian ian 254 2009-09-10 12:05 sfr-chat
-rw-r--r-- 1 ian ian 448 2009-03-12 16:57 sprint
-rw-r--r-- 1 ian ian 231 2009-03-10 11:20 sprint-chat
-rw-r--r-- 1 ian ian 965 2009-04-08 10:27 tmobile
-rw-r--r-- 1 ian ian 264 2009-03-10 10:18 tmobile-bb-chat
-rw-r--r-- 1 ian ian 267 2009-03-10 11:20 tmobile-chat
-rw-r--r-- 1 ian ian 228 2009-03-10 10:18 tmobile-data-chat
-rw-r--r-- 1 ian ian 219 2009-03-10 10:18 tmobile-epc-chat
-rw-r--r-- 1 ian ian 479 2009-07-21 11:12 tmobilehu
-rw-r--r-- 1 ian ian 267 2009-07-21 11:12 tmobilehu-chat
-rw-r--r-- 1 ian ian 228 2009-03-10 10:18 tmobile-vpn-chat
-rw-r--r-- 1 ian ian 276 2009-11-05 10:23 uscellular-chat.conf
-rw-r--r-- 1 ian ian 761 2009-11-05 10:23 uscellular.conf
-rw-r--r-- 1 ian ian 493 2009-04-08 10:28 verizon
-rw-r--r-- 1 ian ian 151 2009-04-08 10:59 verizon-chat

root@ian-minihp:/etc/chatscripts# nano rogers.chat
  GNU nano 2.0.9             File: rogers.chat

TIMEOUT 10
ABORT 'BUSY'
ABORT 'NO ANSWER'
ABORT 'ERROR'
SAY 'Starting GPRS connect script\n'

'' 'BBT_OS'
'' 'ATZ'
SAY 'Setting APN\n'
OK 'AT+CGDCONT=1,"IP","internet.com"'
ABORT 'NO CARRIER'

SAY 'Dialing...\n'
OK 'ATD*99#'
CONNECT
# Without ~p it does NOT continue passed Connect !!
~p
```

---

### Post by ironwolfe on 2010-03-29
My blackberry works tethered to my Windows Machine.  using the following parameters:

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

I wonder if there is someway to toggle these same commands in the ppp file:

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

I just don't know what to change.  are there any ppp guru's out there?

---

### Post by ironwolfe on 2010-03-29
I have started to document the commands in the pppd script comparing to the working windows commands:

**WINDOWS **Disable "Use IP header compression" checkbox

**pppd**

[INDENT]**novj**
    Disable Van Jacobson style TCP/IP header compression in both the transmit and the receive direction. 
**novjccomp**
    Disable the connection-ID compression option in Van Jacobson style TCP/IP header compression. With this option, pppd will not omit the connection-ID byte from Van Jacobson compressed TCP/IP headers, nor ask the peer to do so. [/INDENT]

**WINDOWS** Turn off "Enable Hardware Flow Control"

**pppd** 

[INDENT]**crtscts**
    Use hardware flow control (i.e. RTS/CTS) to control the flow of data on the serial port. If neither the crtscts, the nocrtscts, the cdtrcts nor the nocdtrcts option is given, the hardware flow control setting for the serial port is left unchanged. Some serial ports (such as Macintosh serial ports) lack a true RTS output. Such serial ports use this mode to implement unidirectional flow control. The serial port will suspend transmission when requested by the modem (via CTS) but will be unable to request the modem stop sending to the computer. This mode retains the ability to use DTR as a modem control line. 
[/INDENT]

**WINDOWS ** Turn off "Enable Modem Error Control"

**pppd** [COLOR="Red"]No Idea...[/COLOR]

**WINDOWS ** Turn off "Enable Modem Compression"

**pppd** 
[INDENT]**noaccomp**
    Disable Address/Control compression in both directions (send and receive). 
**noccp**
    Disable CCP (Compression Control Protocol) negotiation. This option should only be required if the peer is buggy and gets confused by requests from pppd for CCP negotiation.
**nocrtscts**
    Disable hardware flow control (i.e. RTS/CTS) on the serial port. If neither the crtscts nor the nocrtscts nor the cdtrcts nor the nocdtrcts option is given, the hardware flow control setting for the serial port is left unchanged.
[/INDENT]

---

