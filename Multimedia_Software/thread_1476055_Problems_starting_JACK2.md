---
title: "Problems starting JACK2"
date: 2010-05-07
forum: Multimedia Software
---

### Post by Abu_Dayya on 2010-05-07
ok, so:

- I added this PPA "http://ppa.launchpad.net/falk-t-j/lucid/ubuntu"
- Installed jack2 version 1.9.5
- Installed qjackctl
- Used these settings in qjackctl
- I get the error" Could not connect to JACK server as client", no such file or folder" when I try to start JACK
- I ran the command ```
yousef@YousefLaptop:~/Downloads/qjackctl-0.3.6$ which jackd
/usr/local/bin/jackd

```
- Used it in qjackctl. Still the same error

I don't have rt kernel installed
Any help

---

### Post by Abu_Dayya on 2010-05-11
Any help guys

---

### Post by Abu_Dayya on 2010-05-15
Ok it looks like a miss-read the error message. The error message says "Unknown driver alsa". I have alsa-tools, alsa-utils, alsa-base installed. is there anything I should do? I googled it and found someone who has the same problem and his solution was to install alsa-devel package and compile jack2 from source. I can't see that package in KPackageKit.

---

### Post by cchhrriiss121212 on 2010-05-15
Could you post the full output of the error message in jack?

---

