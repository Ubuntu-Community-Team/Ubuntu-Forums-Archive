---
title: "need help badly ubuntu 8.10 pppoe"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by jimmy.iceman on 2008-12-18
2 weeks ago i made the switch from windows(after using it forever) to ubuntu 8.10 and i feel in love with ubuntu and in past couple of weeks i have worked my way through it.
i have understood most of the basics and its gr8

theres only 1 little thing that iam not able to do and that is driving me crazy and back to windows.

i have a wireless connection at home ubuntu connects to it just fine and runs like a dream wen it is set to "always on"(pppoe setting in the modem) but when i change the modem setting to "bridge" i m not able to connect to it.this is what happens

1.using "pppoeconf" in terminal i found 3 ethernet devices ath0,eth0,pan0 and configured it entering all the details and choosing not to connect now
then wen i typed "pon" in the terminal i get this

@ubuntu:~$ pon
/usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem'

so please any1 help me out this thing is really drivin me crazy
and also if there is any other way maybe GUI to setup a pppoe do tell

---

### Post by anubhavrocks on 2008-12-18
After you have done pppoeconf you should be able to see the settings in
 /etc/ppp/peers.

Normally its called  "dsl-provider".So the command you should give is
 pon dsl-provider

---

### Post by jimmy.iceman on 2008-12-18
dude this sucks i started ubuntu after couple of hrs now the network manager in the top right corner is gone.............

and how do i get into " /etc/ppp/peers"

---

### Post by anubhavrocks on 2008-12-21
You can see the various files using 
```
ls /etc/ppp/peers

```

You should get something like this
```

anubhav@anubhav-laptop:~$ ls /etc/ppp/peers
airtel  dsl-provider  kppp-options  ppp0  provider  wvdial  wvdial-pipe
```

Now to enable the dsl-provider connection,use the following command
```
anubhav@anubhav-laptop:~$ pon dsl-provider
```

---

