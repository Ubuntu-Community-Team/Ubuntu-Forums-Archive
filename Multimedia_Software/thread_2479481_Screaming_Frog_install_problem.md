---
title: "Screaming Frog install problem"
date: 2022-09-26
forum: Multimedia Software
---

### Post by keansargent on 2022-09-26
Guys, need your help, please! I was trying to install a Screaming Frog SEO Spider Website Crawler. 
And had a problem [https://drive.google.com/file/d/1UymwMTg1zBjPDKL2czCoYJS3ka8cqQi6/view?usp=sharing](https://drive.google.com/file/d/1UymwMTg1zBjPDKL2czCoYJS3ka8cqQi6/view?usp=sharing)

Did anybody meet such kind of problem? If yes, what did you do?

Thanks, Kean

---

### Post by westie457 on 2022-09-26
Welcome to the Forums.
Apt needs to be told where the downloaded package is. Assuming it is in your Downloads folder.
Try install this way ```
sudo apt update
sudo apt install -s ~/Downloads/screamingfrogseospider_17.2_all.deb #This is a simulation. If it looks okay run again leaving out the **-s**&#8203;
```

---

### Post by Holger_Gehrke on 2022-09-26
@westie457: He downloaded the file with wget into the current working directory and tried to install with 'apt install **./**screamingfrogseospider_17_2_all.deb', so there was a path to the file ...

@keansargent: can't help much, since I can't actually understand the error message. Since you posted them as an image I can't even send it through google translate. You could have copied and pasted the message from the terminal (since ctrl-c already has a special meaning in the shell, copying is ctrl-shift-c in most terminals) and you could have prefaced the commands with 'LANG=C' to get English error messages ('LANG=C sudo apt install **./**screamingfrogseospider_17_2_all.deb').

For what it's worth, I tried the installation and it ran through without any problems on my XUbuntu 22.04. I don't understand why this thing brings along a complete JRE instead of simply depending on one ... somebody seems to not quite understand the way .deb packages are supposed to work.

Holger

---

### Post by keansargent on 2022-09-26
Thank you westue457. I wiil try to do the way you adviced.

---

### Post by keansargent on 2022-09-26
Sorry. I tried to do as you say with [COLOR=#000000]LANG=C sudo apt install [/COLOR][B]./screamingfrogseospider_17_2_all.deb in terminal. 
That is what  I get 
[/B]Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is heWaiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is heWaiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is heWaiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is heWaiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is heWaiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is heWaiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is heWaiting for cache lock: Could not get lock /var/l^Citing for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 20857 (apt)... 95s20857 (apt)... 10sock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by processloboda@sloboda-Lenovo-IdeaPad-S145-15API:~$

---

### Post by keansargent on 2022-09-29
Giys, it is me again ) Can enybody help me with this problem. 
Matter of life and death! (

Thanks.

---

### Post by westie457 on 2022-09-29
This should be the terminal response to the commands in your screenshot.
```
graham@graham-IdeaCentre-AIO-3-24ALC6:~$ sudo apt install ./screamingfrogseospider_13.2_all.debReading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'screamingfrogseospider' instead of './screamingfrogseospider_13.2_all.deb'
Suggested packages:
  xvfb
The following NEW packages will be installed
  screamingfrogseospider
0 to upgrade, 1 to newly install, 0 to remove and 2 not to upgrade.
Need to get 0 B/533 MB of archives.
After this operation, 593 MB of additional disk space will be used.
Get:1 /home/graham/screamingfrogseospider_13.2_all.deb screamingfrogseospider amd64 17.2 [533 MB]
Selecting previously unselected package screamingfrogseospider.
(Reading database ... 236064 files and directories currently installed.)
Preparing to unpack .../screamingfrogseospider_13.2_all.deb ...
Unpacking screamingfrogseospider (17.2) ...
Setting up screamingfrogseospider (17.2) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for shared-mime-info (1.15-1) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...

```
Suggest you try again, if you do not get output similar to the above please post your output here in [code] tags.
Even if you keep it to your language we can work on this.

---

