---
title: "Scanning problems"
date: 2018-04-09
forum: Multimedia Software
---

### Post by hakelm on 2018-04-09
I have an Epson PX830 WD connected over the LAN to my Ubuntu 16.04 that always has served me well.
Now it has suddenly stopped working and simple-scan can't find the scanner. Neither can any of the other scanning programs find the scanner.
Running another instance of Ubuntu direct out of the box on the same hardware enables me to scan. I can also scan from a virgin Ubuntu running in a VM. 
This shows that I don't have a hardware or network problem.
The simple-scan shows the scan source as EPSON PID 0879 in the Ubuntu running in a VM.
I have no idea of how to fix this and will appreciate any tip.
H

---

### Post by agemini68 on 2018-04-16
If this is an all in one thing with printer and scanner, I had the same problem. It picked up the printer part of the device but not the scanner. Run an upgrade and include the 18.04 beta release, that fixed my problem with a HP 2652 All In One.

---

### Post by hakelm on 2018-04-23
Thanks, sorry for my late response, I have been travelling.
Where did you find the 18.04 beta release?
H

---

### Post by sevendogsbsd on 2018-04-25
What is the output of ```
scanimage -L
```

Have any changes been made to ```
[FONT=monospace]/etc/sane.d/saned.conf[/FONT]
``` ?

---

### Post by hakelm on 2018-04-25
Thanks for your help, here is my answer

 root@nilx:~# scanimage -L  

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

On the VM that works running on top of my Ubuntu I get:

root@ubuntu:/home/he# scanimage -L
device `epson2:net:192.168.1.5' is a Epson PID 0879 flatbed scanner

cat [COLOR=#000000][FONT=monospace]/etc/sane.d/saned.conf gives the same output on both i.e. everything is commented out

nmap [/FONT][/COLOR] 192.168.1.5 gives identical outputs on both:

root@nilx:~# nmap 192.168.1.5


Starting Nmap 7.01 ( [https://nmap.org](https://nmap.org) ) at 2018-04-25 15:55 CEST
Nmap scan report for 192.168.1.5
Host is up (0.077s latency).
Not shown: 994 closed ports
PORT     STATE SERVICE
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
515/tcp  open  printer
631/tcp  open  ipp
9100/tcp open  jetdirect
MAC Address: A4:EE:57:5E:7E:80 (Seiko Epson)

On both systemctl gives the same output:

root@nilx:~# systemctl list-unit-files | grep sane
saned.service                              masked  
saned@.service                             indirect
saned.socket                               disabled



so I am at a total loss on how to proceed
H

---

### Post by sevendogsbsd on 2018-04-26
Interesting. This tells me the sane service is disabled:

```

[COLOR=#000000]saned.service masked [/COLOR]
[COLOR=#000000]saned@.service indirect[/COLOR]
[COLOR=#000000]saned.socket disabled[/COLOR]

```

I found this saned tutorial, see if it helps as it pertains to Ubuntu:

[https://help.ubuntu.com/community/SaneDaemonTutorial](https://help.ubuntu.com/community/SaneDaemonTutorial)

---

### Post by kenj69 on 2018-06-05
Maybe this topic can help -->

[https://ubuntuforums.org/showthread.php?t=2388273](https://ubuntuforums.org/showthread.php?t=2388273)

-=Ken=-

---

