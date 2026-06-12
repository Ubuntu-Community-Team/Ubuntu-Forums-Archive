---
title: "HP LaserJet M1522n - scanner doesn't work"
date: 2008-06-30
forum: Multimedia Software
---

### Post by qaws on 2008-06-30
Hello,

I've bought new All-in-One device HP LaserJet M1522n and scanner doesn't work.

It's connected to my router with 100Mbit network cable. I am able to access its web-settings and to print, but my computer is not able to find scanner there.

I tried ```
hp-makeuri 192.168.1.61
```
and it returns only CUPS URI, that is only for printing.
When I try: ```
hp-makeuri --sane 192.168.1.61
``` it returns *error: Device does not support scan.*


I read "man sane-net" and there was written that a sane-port had to be defined in /etc/services. It is defined, but I tried to change its port to fit a printer's port (I tried only 8289/tcp), but if I change it and run xsane, xsane freezes.

Hpoj does not work, it does not detect the scanner.

Finally, these ports on my LaserJet are open
```
PORT      STATE SERVICE
7/tcp     open  echo
80/tcp    open  http
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
515/tcp   open  printer
8289/tcp  open  unknown
8888/tcp  open  sun-answerbook
9100/tcp  open  jetdirect
9999/tcp  open  abyss
10002/tcp open  unknown
23000/tcp open  unknown
```

If you don't know exact solution for my problem, try to ask me more questions, please -> that questions can help me to make it work.

Thanks in advance.

---

### Post by xc3RnbFO8P on 2008-06-30
Scannig is not supported:
[http://hplip.sourceforge.net/models/laserjet/hp_laserjet_m1522n_mfp.html]("http://hplip.sourceforge.net/models/laserjet/hp_laserjet_m1522n_mfp.html")

---

### Post by qaws on 2008-07-01
> **Ringi said:**
> Scannig is not supported:
[http://hplip.sourceforge.net/models/laserjet/hp_laserjet_m1522n_mfp.html]("http://hplip.sourceforge.net/models/laserjet/hp_laserjet_m1522n_mfp.html")

Thanks, but isn't there any unofficial solution?

---

### Post by Berduchwal on 2008-09-20
any news on the subject I have just got mine and wanted to use scanner. Did you get anywhere?

---

### Post by qaws on 2008-09-20
> **Berduchwal said:**
> any news on the subject I have just got mine and wanted to use scanner. Did you get anywhere?
I didn't get any news. The only thing I know is, that it is getting better: Sane URI is generated now, but scanner returns IO error and advices from Google doesn't work.

---

### Post by qaws on 2008-10-11
Scanner works now, but you need to follow these steps.

I will describe it here.
[LIST=1]
[*]You need hplip version 2.8.6 (not newer or older, **2.8.6b also doesn't work**). If you haven't this version, you should remove hplip package and execute file from [http://www.mirrorservice.org/sites/download.sourceforge.net/pub/sourceforge/h/hp/hplip/hplip-2.8.6.run]("http://www.mirrorservice.org/sites/download.sourceforge.net/pub/sourceforge/h/hp/hplip/hplip-2.8.6.run")
[*]Install your device with *hp-setup -i* or via GUI (you have to do it only if scanner hadn't been installed before).
[*]Try scanning. When it says there is no such device, it probably won't work or you haven't followed step 1.
[/LIST]

These steps are from page [https://bugs.launchpad.net/hplip/+bug/243940]("https://bugs.launchpad.net/hplip/+bug/243940")

---

