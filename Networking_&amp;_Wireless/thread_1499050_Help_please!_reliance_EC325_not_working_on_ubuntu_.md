---
title: "Help please! reliance EC325 not working on ubuntu 10.04"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by satksri on 2010-06-01
I have a reliance usb modem card (EC325) which is not working with 10.04. It worked fine on 9.04. When I run wvdial I get following output:
-----------------------------------------
satyendra@satyendra-laptop:~$ wvdial cdma
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT 230400
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Jun  1 23:28:29 2010
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 2748
--> Using interface ppp0
--> pppd: Hi&#65533;[08]&#65533;i&#65533;[08]
--> pppd: Hi&#65533;[08]&#65533;i&#65533;[08]
--> pppd: Hi&#65533;[08]&#65533;i&#65533;[08]
--> pppd: Hi&#65533;[08]&#65533;i&#65533;[08]
--> Disconnecting at Tue Jun  1 23:28:33 2010
--> The PPP daemon has died: Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password? (exit code = 19)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 19)



can some one please help?

Thanks in advance!
sachin

---

### Post by satksri on 2010-06-02
Hey Guys- thanks a lot for not responding! It forced me to bash my head against "bash" and come up with solutions. And it works. It certainly makes me feel more confident with Ubuntu and Linux. 
Let me share. I am not pro- so watch out before you trust too much on my guidance though:confused:

1. From my own post, I picked up "/etc/ppp/chap-secrets: Permission denied" and did a google search.
2. Found this link- [http://linmodems.technion.ac.il/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/archive-sixth/msg04656.html)
3. ran this command once- # chmod a+rw /etc/ppp/pap-secrets
4. After that I used wvdial- and voila! It is working- after 48 hours of bashing around..
Thanks Marvin Stodolsky and the open source community!
:guitar:

---

### Post by pdc on 2010-06-02
as you have become so good on ppp secrets, here is some more reading for you

[http://www.pcurtis.com/ubuntu-mobile.htm#ppp_secrets](http://www.pcurtis.com/ubuntu-mobile.htm#ppp_secrets)

---

### Post by satksri on 2010-06-05
> **pdc said:**
> as you have become so good on ppp secrets, here is some more reading for you

[http://www.pcurtis.com/ubuntu-mobile.htm#ppp_secrets](http://www.pcurtis.com/ubuntu-mobile.htm#ppp_secrets)

Thanks a lot. This page taught me a few more things (at 52!).
Blessings!
sachin

---

