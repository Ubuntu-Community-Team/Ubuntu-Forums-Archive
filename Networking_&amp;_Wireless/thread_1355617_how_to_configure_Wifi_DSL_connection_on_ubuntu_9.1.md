---
title: "how to configure Wifi DSL connection on ubuntu 9.10??"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by bhupinderjitbawa on 2009-12-15
Hi i have working DSL wired BSNL broadband connection.Its working well.But how can i configure wireless DSL connection.By default it shows a "default" connection in network manager.But this default connection does not start my internet connection.

IN window 7,i first connect thru a default wireless connection and then used to dial DSL connection,
in Ubuntu
Same there is option for connecting thru default wireless connection but there is no option to dial my BSNL DSL dialup connection,

How to dial DSL connection after connecting thru default wireless connection?????

---

### Post by shredder12 on 2009-12-20
I have never actually used a wireless DSL modem but I think this might help you out..
[http://www.ehow.com/how_2212487_install-wireless-dsl-modem.html](http://www.ehow.com/how_2212487_install-wireless-dsl-modem.html)

---

### Post by kshtjsnghl on 2009-12-24
I am facing the same problem.
I can get connected to BSNL Broadband when i dial through my windows system but when I try to connect through my Ubuntu system either through wireless network or the direct wired one, it shows connected but i am not connected to internet as probably I am too unable to use the dial up for this connection.

PS : I am using 9.04

---

### Post by dineshs on 2009-12-24
> **kshtjsnghl said:**
> I am facing the same problem.
I can get connected to BSNL Broadband when i dial through my windows system but when I try to connect through my Ubuntu system either through wireless network or the direct wired one, it shows connected but i am not connected to internet as probably I am too unable to use the dial up for this connection.

PS : I am using 9.04

Did you run the following command ?
```
sudo pppoeconf
```
and follow instructions 
Then to connect use the command
```
pon dsl-provider
```
and to disconnect
```
poff dsl-provider
```

---

### Post by swapnilps on 2010-06-05
:popcorn:Thanks a lot buddy...
it worked for me.. but same thing i tried from the network icon present at upper right corner. but that didnt worked.
would like to know: how to do it from GUI mode.
anyways thanks a lottttt.
Cheers!

---

### Post by dineshs on 2010-06-05
Pl try this link
[http://ubuntuforums.org/showthread.php?t=1501756](http://ubuntuforums.org/showthread.php?t=1501756)
BTW most of the modems are configurable in PPPoE mode.
[http://ubuntuforums.org/showthread.php?t=1497648&page=2](http://ubuntuforums.org/showthread.php?t=1497648&page=2)
If you do so you need not run pppoeconf/pon dsl-provider everytime.(you can directly use your web browser)To configure your modem in PPPoE mode examples are available here
[http://ernakulam.sancharnet.in/ernakulam/bbservice.html](http://ernakulam.sancharnet.in/ernakulam/bbservice.html)

---

