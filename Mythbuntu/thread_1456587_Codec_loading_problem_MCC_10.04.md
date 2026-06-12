---
title: "Codec loading problem MCC 10.04"
date: 2010-04-17
forum: Mythbuntu
---

### Post by williammanda on 2010-04-17
I'm in the process of installing MCC 10.04 on top of ubuntu lucid. I can't seem to load codecs as I usually do. I select Enable DVD Support and hit apply. It looks like to is processing then it comes back to the codec screen with Enable DVD Support unchecked. See codec screenshot.

---

### Post by williammanda on 2010-04-17
Same result on the second 64 bit machine. I installed the frontend only where as the 1st machine is the master backend / frontend.

---

### Post by williammanda on 2010-04-17
Same result on a 32 bit mythbunu install.

---

### Post by tgm4883 on 2010-04-17
Odd, works for me here. Can you check the following.

What version of mythbuntu-control-centre do you have installed?

Is libdvdread4 installed?

---

### Post by tgm4883 on 2010-04-17
Open up two command prompts. 

In the first one, run 

```
sudo /usr/share/mythbuntu/mcc-backend
```

In the second one, run 

```
mythbuntu-control-centre
```

Then try to enable the proprietary codecs. Post the output from both windows (although any errors should pop up in the mcc-backend window).

---

### Post by williammanda on 2010-04-17
> **tgm4883 said:**
> Open up two command prompts. 

In the first one, run 

```
sudo /usr/share/mythbuntu/mcc-backend
```

Here is the output of the 1st terminal:

```
william@C2Q:~$ sudo /usr/share/mythbuntu/mcc-backend
[sudo] password for william: 
--2010-04-17 15:47:16--  http://packages.medibuntu.org/dists/lucid/free/binary-amd64/Packages
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8080 (7.9K) [text/plain]
Saving to: `/tmp/dvdcss-bZWDxH/Packages'

100%[======================================>] 8,080       32.4K/s   in 0.2s    

2010-04-17 15:47:17 (32.4 KB/s) - `/tmp/dvdcss-bZWDxH/Packages' saved [8080/8080]

--2010-04-17 15:47:17--  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 38080 (37K) [application/x-debian-package]
Saving to: `/tmp/dvdcss-bZWDxH/libdvdcss.deb'

100%[======================================>] 38,080      98.8K/s   in 0.4s    

2010-04-17 15:47:18 (98.8 KB/s) - `/tmp/dvdcss-bZWDxH/libdvdcss.deb' saved [38080/38080]

Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service udev reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload udev
 * Stopping remote control daemon(s): LIRC
   ...done.



```

> In the second one, run 

```
mythbuntu-control-centre
```

Then try to enable the proprietary codecs. Post the output from both windows (although any errors should pop up in the mcc-backend window).

Output from 2nd terminal

```
william@C2Q:~$ mythbuntu-control-centre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
no crontab for william
Reading package lists... Done
Building dependency tree       
Reading state information... Done
no crontab for william


```

---

### Post by tgm4883 on 2010-04-17
Odd, I was able to reproduce the bug when mcc-backend was started on it's own, but not when I started it via the terminal. 

Please file a bug for this at launchpad.net/mythbuntu

---

### Post by williammanda on 2010-04-18
Submitted! [https://bugs.launchpad.net/mythbuntu/+bug/565769](https://bugs.launchpad.net/mythbuntu/+bug/565769)

---

### Post by williammanda on 2010-04-18
Its been so long since I had to install codecs manually. I used this site:

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

These commands:

sudo apt-get install libdvdcss2

sudo apt-get install w64codecs

---

### Post by tgm4883 on 2010-04-18
Actually you had already installed the dvd support. When you lauched the backend manually.

---

### Post by williammanda on 2010-04-18
> **tgm4883 said:**
> Actually you had already installed the dvd support. When you lauched the backend manually.

Your correct! But on the additional three computers I used the manual way. I just thought it would be helpful for anyone running into the same issue.

---

### Post by tgm4883 on 2010-04-18
Actually, just running the following command as sudo would do it

```
/usr/share/doc/libdvdread4/install-css.sh
```

---

