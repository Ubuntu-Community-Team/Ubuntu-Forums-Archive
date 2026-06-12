---
title: "Dial-up problems on Ubuntu 10.04  D-link dfm-560e serial modem"
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by amav.eram on 2010-05-22
Hi all.

I am new to ubuntu and to Linux in general and am having some problems with dialing

 up. Have tried to solve it myself thusfar, but I feel I need some assistance to go 

further.


My system specs are(please ask if you need more info):


Dell Dimension XPS D233 pentium 2, 256mb Ram.
Modem: D-Link dfm-560e Serial
Distro: Ubuntu 10.04, fresh install.
Internet Provider: Slingshot, 56k Dial Up (New Zealand)


So far I have run PPPConfig and entered in all relevant details, including my DNS 

servers, and I have selected the PAP setting as my ISP informed me that this setting is 

required for Linux. (My isp also informed me that I must disable the setting for 

'authentication in return', I am unsure of how to do this if anybody can help also). My 

modem is set to ttyS0, which seems to be okay.

After this I have run:


[FONT=Courier New]sudo adduser 'username' dip


[FONT=Times New Roman]and[FONT=Courier New] pon[FONT=Times New Roman]


[FONT=Arial]After this I get all of the dial-up noises, and seem to connect, but then i am disconnected after about 30 

seconds. I get no connectivity through firefox.[/FONT]


the output from [FONT=Courier New]plog [FONT=Times New Roman]gives me:


[FONT=Courier New]May 23 01:30:03 ubuntu chat[1861]: abort on (NO ANSWER)
May 23 01:30:03 ubuntu chat[1861]: abort on (DELAYED)
May 23 01:30:03 ubuntu chat[1861]: send (ATZ^M)
May 23 01:30:03 ubuntu chat[1861]: expect (OK)
May 23 01:30:03 ubuntu chat[1861]: ATZ^M^M
May 23 01:30:03 ubuntu chat[1861]: OK
May 23 01:30:03 ubuntu chat[1861]:  -- got it
May 23 01:30:03 ubuntu chat[1861]: send (ATDT087308880^M)
May 23 01:30:03 ubuntu chat[1861]: expect (CONNECT)
May 23 01:30:03 ubuntu chat[1861]: ^M
casey@ubuntu:~$ plog
May 23 01:30:33 ubuntu pppd[1858]: Using interface ppp0
May 23 01:30:33 ubuntu pppd[1858]: Connect: ppp0 <--> /dev/ttyS0
May 23 01:30:34 ubuntu pppd[1858]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x66bde2c8> <pcomp> <accomp>]
May 23 01:30:34 ubuntu pppd[1858]: rcvd [LCP ConfReq id=0x2f <asyncmap 0xa0000> <auth pap> <magic 0xcf907bbf> <pcomp> <accomp>]
May 23 01:30:34 ubuntu pppd[1858]: sent [LCP ConfAck id=0x2f <asyncmap 0xa0000> <auth pap> <magic 0xcf907bbf> <pcomp> <accomp>]
May 23 01:30:34 ubuntu pppd[1858]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x66bde2c8> <pcomp> <accomp>]
May 23 01:30:34 ubuntu pppd[1858]: sent [LCP EchoReq id=0x0 magic=0x66bde2c8]
May 23 01:30:34 ubuntu pppd[1858]: sent [PAP AuthReq id=0x1 user="cmbowden" password=<hidden>]
May 23 01:30:34 ubuntu pppd[1858]: rcvd [LCP EchoRep id=0x0 magic=0xcf907bbf]
casey@ubuntu:~$ plog
May 23 01:30:35 ubuntu pppd[1858]: sent [LCP ConfAck id=0x8f <mru 1460> <asyncmap 0xa0000> <auth pap> <magic 0xcf907bbf>]
May 23 01:30:35 ubuntu pppd[1858]: rcvd [LCP ConfRej id=0x2 <asyncmap 0x0> <pcomp> <accomp>]
May 23 01:30:35 ubuntu pppd[1858]: sent [LCP ConfReq id=0x3 <magic 0x20ef5b50>]
May 23 01:30:35 ubuntu pppd[1858]: rcvd [LCP ConfAck id=0x3 <magic 0x20ef5b50>]
May 23 01:30:35 ubuntu pppd[1858]: sent [LCP EchoReq id=0x0 magic=0x20ef5b50]
May 23 01:30:35 ubuntu pppd[1858]: sent [PAP AuthReq id=0x2 user="cmbowden" password=<hidden>]
May 23 01:30:38 ubuntu pppd[1858]: sent [PAP AuthReq id=0x3 user="cmbowden" password=<hidden>]
May 23 01:30:41 ubuntu pppd[1858]: sent [PAP AuthReq id=0x4 user="cmbowden" password=<hidden>]
May 23 01:30:44 ubuntu pppd[1858]: sent [PAP AuthReq id=0x5 user="cmbowden" password=<hidden>]
May 23 01:30:47 ubuntu pppd[1858]: sent [PAP AuthReq id=0x6 user="cmbowden" password=<hidden>]
casey@ubuntu:~$ plog
May 23 01:30:35 ubuntu pppd[1858]: rcvd [LCP ConfAck id=0x3 <magic 0x20ef5b50>]
May 23 01:30:35 ubuntu pppd[1858]: sent [LCP EchoReq id=0x0 magic=0x20ef5b50]
May 23 01:30:35 ubuntu pppd[1858]: sent [PAP AuthReq id=0x2 user="cmbowden" password=<hidden>]
May 23 01:30:38 ubuntu pppd[1858]: sent [PAP AuthReq id=0x3 user="cmbowden" password=<hidden>]
May 23 01:30:41 ubuntu pppd[1858]: sent [PAP AuthReq id=0x4 user="cmbowden" password=<hidden>]
May 23 01:30:44 ubuntu pppd[1858]: sent [PAP AuthReq id=0x5 user="cmbowden" password=<hidden>]
May 23 01:30:47 ubuntu pppd[1858]: sent [PAP AuthReq id=0x6 user="cmbowden" password=<hidden>]
May 23 01:30:50 ubuntu pppd[1858]: sent [PAP AuthReq id=0x7 user="cmbowden" password=<hidden>]
May 23 01:30:53 ubuntu pppd[1858]: sent [PAP AuthReq id=0x8 user="cmbowden" password=<hidden>]
May 23 01:30:56 ubuntu pppd[1858]: sent [PAP AuthReq id=0x9 user="cmbowden" password=<hidden>]
casey@ubuntu:~$ plog
May 23 01:30:44 ubuntu pppd[1858]: sent [PAP AuthReq id=0x5 user="cmbowden" password=<hidden>]
May 23 01:30:47 ubuntu pppd[1858]: sent [PAP AuthReq id=0x6 user="cmbowden" password=<hidden>]
May 23 01:30:50 ubuntu pppd[1858]: sent [PAP AuthReq id=0x7 user="cmbowden" password=<hidden>]
May 23 01:30:53 ubuntu pppd[1858]: sent [PAP AuthReq id=0x8 user="cmbowden" password=<hidden>]
May 23 01:30:56 ubuntu pppd[1858]: sent [PAP AuthReq id=0x9 user="cmbowden" password=<hidden>]
May 23 01:30:59 ubuntu pppd[1858]: sent [PAP AuthReq id=0xa user="cmbowden" password=<hidden>]
May 23 01:31:02 ubuntu pppd[1858]: sent [PAP AuthReq id=0xb user="cmbowden" password=<hidden>]
May 23 01:31:05 ubuntu pppd[1858]: sent [LCP EchoReq id=0x1 magic=0x20ef5b50]
May 23 01:31:05 ubuntu pppd[1858]: No response to PAP authenticate-requests
May 23 01:31:05 ubuntu pppd[1858]: sent [LCP TermReq id=0x4 "Failed to authenticate ourselves to peer"]
casey@ubuntu:~$ 


[FONT=Times New Roman]It seems to me that something is wrong with my name and password, although I have double checked and 

triple checked these...Do i need to somehow turn off the authentication requests?


I have installed WVDIAL and run [FONT=Courier New]sudo wvdialconf[/FONT] in the terminal. It seems to identify my modem and 

run smoothly. After this I entered all relevant information in the wvdialconf file, included turning stupid 

mode on.

When I run WVDIAL, again it connects and starts PPP, but disconnect after about 30 seconds.

The WVDIAL output is as follows:


[FONT=Courier New]--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT087308880
--> Waiting for carrier.
ATDT087308880
CONNECT 115200
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!"} }8}"}&} }*} } }#}$@#}%}&x]$i}'}"}(}"[07]2~
--> PPP negotiation detected.
--> Starting pppd at Sun May 23 01:35:40 2010
--> Pid of pppd: 1917
--> Using interface ppp0
--> pppd: ï¿½'ï¿½ H%ï¿½ 
--> pppd: ï¿½'ï¿½ H%ï¿½ 
--> pppd: ï¿½'ï¿½ H%ï¿½ 
--> pppd: ï¿½'ï¿½ H%ï¿½ 
--> pppd: ï¿½'ï¿½ H%ï¿½ 
--> Disconnecting at Sun May 23 01:36:16 2010
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.


I have also installed and run Gnome-PPP. Sets up and dials out fine, but 

same problems as I am having with WVDIAL.


Here is the output from /var/log/messages:

May 23 00:38:00 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="268" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
May 23 01:08:30 ubuntu pppd[1636]: pppd 2.4.5 started by casey, uid 1000
May 23 01:08:31 ubuntu pppd[1636]: Using interface ppp0
May 23 01:08:31 ubuntu pppd[1636]: Connect: ppp0 <--> /dev/ttyS0
May 23 01:09:01 ubuntu pppd[1636]: LCP: timeout sending Config-Requests
May 23 01:09:01 ubuntu pppd[1636]: Connection terminated.
May 23 01:09:01 ubuntu pppd[1636]: Modem hangup
May 23 01:09:01 ubuntu pppd[1636]: Exit.
May 23 01:20:59 ubuntu pppd[1727]: pppd 2.4.5 started by casey, uid 1000
May 23 01:20:59 ubuntu pppd[1727]: Using interface ppp0
May 23 01:20:59 ubuntu pppd[1727]: Connect: ppp0 <--> /dev/ttyS0
May 23 01:21:36 ubuntu pppd[1727]: Connection terminated.
May 23 01:21:36 ubuntu pppd[1727]: Modem hangup
May 23 01:21:36 ubuntu pppd[1727]: Exit.
May 23 01:22:14 ubuntu pppd[1758]: pppd 2.4.5 started by casey, uid 1000
May 23 01:22:14 ubuntu pppd[1758]: Using interface ppp0
May 23 01:22:14 ubuntu pppd[1758]: Connect: ppp0 <--> /dev/ttyS0
May 23 01:22:49 ubuntu pppd[1758]: Modem hangup
May 23 01:22:49 ubuntu pppd[1758]: Connection terminated.
May 23 01:22:49 ubuntu pppd[1758]: Exit.
May 23 01:30:02 ubuntu pppd[1858]: pppd 2.4.5 started by casey, uid 1000
May 23 01:30:03 ubuntu chat[1861]: abort on (BUSY)
May 23 01:30:03 ubuntu chat[1861]: abort on (NO CARRIER)
May 23 01:30:03 ubuntu chat[1861]: abort on (VOICE)
May 23 01:30:03 ubuntu chat[1861]: abort on (NO DIALTONE)
May 23 01:30:03 ubuntu chat[1861]: abort on (NO DIAL TONE)
May 23 01:30:03 ubuntu chat[1861]: abort on (NO ANSWER)
May 23 01:30:03 ubuntu chat[1861]: abort on (DELAYED)
May 23 01:30:03 ubuntu chat[1861]: send (ATZ^M)
May 23 01:30:03 ubuntu chat[1861]: expect (OK)
May 23 01:30:03 ubuntu chat[1861]: ATZ^M^M
May 23 01:30:03 ubuntu chat[1861]: OK
May 23 01:30:03 ubuntu chat[1861]:  -- got it
May 23 01:30:03 ubuntu chat[1861]: send (ATDT087308880^M)
May 23 01:30:03 ubuntu chat[1861]: expect (CONNECT)
May 23 01:30:03 ubuntu chat[1861]: ^M
May 23 01:30:32 ubuntu chat[1861]: ^M
May 23 01:30:32 ubuntu chat[1861]: CONNECT
May 23 01:30:32 ubuntu chat[1861]:  -- got it
May 23 01:30:32 ubuntu chat[1861]: send (\d)
May 23 01:30:33 ubuntu pppd[1858]: Serial connection established.
May 23 01:30:33 ubuntu pppd[1858]: Using interface ppp0
May 23 01:30:33 ubuntu pppd[1858]: Connect: ppp0 <--> /dev/ttyS0
May 23 01:31:09 ubuntu pppd[1858]: Hangup (SIGHUP)
May 23 01:31:09 ubuntu pppd[1858]: Modem hangup
May 23 01:31:09 ubuntu pppd[1858]: Connection terminated.
May 23 01:31:10 ubuntu pppd[1858]: Exit.
May 23 01:34:25 ubuntu pppd[1908]: pppd 2.4.5 started by root, uid 0
May 23 01:34:25 ubuntu pppd[1908]: Using interface ppp0
May 23 01:34:25 ubuntu pppd[1908]: Connect: ppp0 <--> /dev/ttyS0
May 23 01:35:01 ubuntu pppd[1908]: Modem hangup
May 23 01:35:01 ubuntu pppd[1908]: Connection terminated.
May 23 01:35:02 ubuntu pppd[1908]: Exit.
May 23 01:35:40 ubuntu pppd[1917]: pppd 2.4.5 started by root, uid 0
May 23 01:35:40 ubuntu pppd[1917]: Using interface ppp0
May 23 01:35:40 ubuntu pppd[1917]: Connect: ppp0 <--> /dev/ttyS0
May 23 01:36:16 ubuntu pppd[1917]: Modem hangup
May 23 01:36:16 ubuntu pppd[1917]: Connection terminated.
May 23 01:36:16 ubuntu pppd[1917]: Exit.


[FONT=Arial]Please help if you can...I am very keen to learn my way around ubuntu and move away from windows, 

but without an internet connection I can't do very much. 

Any links to resources that I could use to teach myself would be greatly appreciated also.


Amav.eram[/FONT]


[/FONT][/FONT]
[/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT]

---

### Post by boluele on 2010-05-22
try to cinfigure with kppp.

First you will need to download it, do that from-->Application---->Ubuntu Software Center.
on search type kppp, when appear apply to install, done that, follow the instruction.

Any doubt we are here to help each other.

cheers,

BL

---

### Post by klemes on 2010-05-22
Edit the /etc/ppp/peers/provider file and add the '_noauth_' pppd option if not already there.This might help.Also for good measure add usepeerdns,noipdefault,defaultroute and replacedefaultroute.(put them vertically one at the bottom of the other in a new line for each option).
Also take a look in the /etc/ppp/pap-secrets that your username and password are correctly entered there and if not edit them accordingly.
:popcorn:

---

### Post by amav.eram on 2010-05-23
Okay thanks. I will try that out and post my results soon. :-)

---

### Post by amav.eram on 2010-05-23
Boluele, thanks for the advice, i managed to find kppp in Ubuntu Software Centre, however there seems to be no option to install the file. I will see if I can find an archive file online on my other computer and install kppp manually.

hi klemes.

I had a look at my /etc/ppp/peers/provider file. The 'noauth' option was already there, as well as 'noipdefault' and 'defaultroute'. I tried to add 'usepeerdns' and 'replacedefaultroute', however usepeerdns seemed to cause problems with connecting via 'pon'. replacedefaultroute didnt seem to affect anything.

Here is the new output of plog, after adding usepeerdns:

casey@ubuntu:~$ plog
May 24 08:23:10 ubuntu chat[1793]: send (ATDT087308880^M)
May 24 08:23:10 ubuntu chat[1793]: expect (CONNECT)
May 24 08:23:10 ubuntu chat[1793]: ^M
May 24 08:23:48 ubuntu chat[1793]: ^M
May 24 08:23:48 ubuntu chat[1793]: NO CARRIER
May 24 08:23:48 ubuntu chat[1793]:  -- failed
May 24 08:23:48 ubuntu chat[1793]: Failed (NO CARRIER)
May 24 08:23:48 ubuntu pppd[1791]: Script /usr/sbin/chat -v -f /etc/chatscripts/provider finished (pid 1792), status = 0x5
May 24 08:23:48 ubuntu pppd[1791]: Connect script failed
May 24 08:23:49 ubuntu pppd[1791]: Exit.

My username and password in /etc/ppp/pap-secrets file was correct, however a part of this section was commented out, is this a problem? ('password' replaces my actual password)

#    *    password
"cmbowden" provider "password"

cmbowden    *    password

Also, here is the output of my /etc/ppp/peers/provider file if that helps:

# This optionfile was generated by pppconfig 2.3.18. 
# 
#
hide-password 
noauth
connect "/usr/sbin/chat -v -f /etc/chatscripts/provider"
debug
/dev/ttyS0
115200
defaultroute
noipdefault
user "cmbowden"
remotename provider
ipparam provider

Do you know what else I could try? 

I will try and contact my isp tomorrow and see if I can get any more information about connection settings from them, although they have already told me that they dont support linux :-(

Thanks guys

amav.eram

---

### Post by alexfish on 2010-05-23
hi

have a look here , read the parts about the LCP , also advise reading all

[http://www.pcurtis.com/ubuntu-mobile.htm](http://www.pcurtis.com/ubuntu-mobile.htm)

regards

alexfish

---

### Post by amav.eram on 2010-06-02
Hi all.
Thanks heaps for your help so far, and sorry i took so long to post. My old computer that I was using for linux has blown its power supply and i suspect also the mother board, so I will have to wait till i can buy another. Alexfish i checked out that article, was great and I definitely reccoment for any ubuntu noob, i tried out all of the tips that seemed applicable such as checking my permissions, and ensuring that i have write/read permissions for pap-secrets, however none of this seemed to have any effect.

Thanks heaps and you will hear from me again when I have a new box.

---

### Post by alexfish on 2010-06-02
hi

hope you get sorted

looking at the above log files ,looks as wvdial will work , may be only a couple of configs need to edited , 

regards

alexfish

---

