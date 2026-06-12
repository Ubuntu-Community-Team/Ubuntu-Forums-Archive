---
title: "Sprint Merlin S620 *after* Dapper"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by malacandra on 2006-06-13
OK. I had a nice script to set up my Novatel Merlin S620 under Breezy. Ubuntu did NOT recognize the card, so I ran a small script to set up the hardware. Then I used wvdial to connect.

Now, in Dapper, the card is recognized automatically. I use the connect conf. file from Breezy and the modem will only stay connected for 2.5 minutes then it disconnects, (error 15). Any ideas on how to troubleshoot this? Here's my **wvdial.conf** file:

[Dialer Defaults]
Stupid Mode = on
Modem = /dev/ttyUSB0
Baud = 460800
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Phone = #777
Username = [email]XXXXXXX@sprintpcs.com[/email]
Password = XXXXXXX
# [Dialer phone2] =
# Phone = 555-4242
Init1 = ATZ
ISDN = 0
Modem Type = Analog Modem
Auto Reconnect = on
Carrier Check = no

[Dialer shh]
Init3 = ATM0

[Dialer pulse]
Dial Command = ATDP

------------------------------

Any ideas? 

Thanks,
Mark

---

### Post by malacandra on 2006-06-14
Found this solution here:

[http://groups.google.com/group/alt.cellular.cingular/browse_thread/thread/277fe225be14d77b/57c33dfff29f68b0%2357c33dfff29f68b0](http://groups.google.com/group/alt.cellular.cingular/browse_thread/thread/277fe225be14d77b/57c33dfff29f68b0%2357c33dfff29f68b0)

Short version: in **/etc/ppp/options**, modify the **lcp-echo-failure** value to 0 or comment it out.

---

