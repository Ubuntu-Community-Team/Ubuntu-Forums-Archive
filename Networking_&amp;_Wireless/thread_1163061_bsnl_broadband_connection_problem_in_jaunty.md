---
title: "bsnl broadband connection problem in jaunty"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by ganeshredcobra on 2009-05-18
ganesh@ganesh-desktop:~$ sudo pppoeconf
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
ganesh@ganesh-desktop:~$ plog
May 16 02:25:11 ganesh-desktop pppd[4070]: Unable to complete PPPoE Discovery
May 16 02:26:16 ganesh-desktop pppd[4070]: Timeout waiting for PADS packets
May 16 02:26:16 ganesh-desktop pppd[3418]: Timeout waiting for PADS packets
May 16 02:26:16 ganesh-desktop pppd[3418]: Unable to complete PPPoE Discovery
May 16 02:26:16 ganesh-desktop pppd[4070]: Unable to complete PPPoE Discovery
May 16 02:26:52 ganesh-desktop pppd[4358]: Plugin rp-pppoe.so loaded.
May 16 02:26:52 ganesh-desktop pppd[4358]: RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
May 16 02:26:52 ganesh-desktop pppd[4360]: pppd 2.4.5 started by root, uid 0
ganesh@ganesh-desktop:~$ 



i cannot connect to internet bcoz of this problem does somebody have a solution for me

---

### Post by superprash2003 on 2009-05-18
post output of **ifconfig** from the terminal

---

### Post by Arup on 2009-05-18
For BSNL use an MTU of 1452.

---

### Post by aditya.phanindra on 2009-05-20
Hey,
I'm facing the same problem.
I used MTU = 1452 (default) while configuring using pppoeconf.

I get:
[B]
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5[/B]

after I try "pon dsl-provider" but I am not able to connect to the internet.

This problem is bugging me for the last 2 days. Can someone please help me out here?

---

### Post by eewo on 2009-05-24
Same here. Just happened few days ago

---

### Post by rohitfeb14 on 2009-07-10
Same problem with me...
network manager DSL also unable to connect to broadband

---

### Post by superprash2003 on 2009-07-10
what error do you face? are you able to access [http://192.168.1.1?](http://192.168.1.1?)

---

### Post by authentik on 2009-07-12
any update? I've got the same problem.

---

### Post by ubu-lemon on 2009-07-21
same problem here (I'm posting from an 8.10 computer, but the problem occurs with a jaunty jackalope machine)
(pppoe dsl connection)

strange thing is Skype does function but Firefox doesn't
same error message with 'pon dsl-provider'

---

### Post by rahulsingh.nitrkl on 2009-07-29
I am so relieved to see these posts. Atleast i am not alone. I have been trying to get a solution for weeks. I would be much happier if someone could post the solution though.

---

