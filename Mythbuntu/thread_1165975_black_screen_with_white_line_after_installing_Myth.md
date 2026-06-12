---
title: "black screen with white line after installing Mythbuntu 9.04"
date: 2009-05-21
forum: Mythbuntu
---

### Post by Kheos on 2009-05-21
After installing Mythbuntu 9.04, I get the following funny screen:
a black screen with a white line 
I can escape this screen which lead to the question if I want to fill the myth-database(so the black screen should be the Myth wizard I guess.

The next issue is that when it needs to restart, the progress bar fills untill about 95% and stops so I have to reboot it manually.

hardware: 
D-LINK DWA-556 WIRELESS-N PCIE-DESKTOPADAPTER
AMD 5400+ X2 64BIT DUAL-CORE PROCESSOR AM2 BOXED
CORSAIR VX450W ROCK SOLID PERFORMANCE, INCREDIBLE VALUE (CMPSU-450VX) 
SAMSUNG HD103UJ 1000GB (1TB) 32MB SATA300 7200RPM
GIGABYTE GA-MA74GM-S2H AMD 740G SOCKET AM2
PREMIUM 2048MB DDR2 PC6400 800MHZ VALUE SERIES 
ANTEC FUSION REMOTE ZILVER MICRO ATX BEHUIZING NO PSU 
Hauppauge WinTV-PVR-150 Retail + remote
Hauppauge WinTV-PVR-150MCE (bulk, voor Mediacenter)

Any ideas?

---

### Post by jangia on 2009-05-21
Interesting .  I installed Mythbuntu 9.04 today as well and getting into same issue as well. There seems to be an issue with mythfrontend coz when this blank screen apprears I can goto terminal and change applications. Everything else seems to be working. I googled for last 3 hours and there have been some reported issues but none of the solutions are working (frontend restart etc). I have Radeon card and thought this might be video card issue as a bug were reported that fonts are not showing up etc. Now am tired of searching . I hope someone can help on this forum! 

Waiting!

~Jangia

---

### Post by jangia on 2009-05-21
OKay I found the solution! ... I assume you r using your onboard graphics chipset which, if am not mistaken, is ATI Radeon 21xx. Mythbuntu 9.04 has known bug for ATI cards and here is the solution;

[https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/341898](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/341898) 

I hope it helps.

~Jangia

---

### Post by Kheos on 2009-05-23
> **jangia said:**
> OKay I found the solution! ... I assume you r using your onboard graphics chipset which, if am not mistaken, is ATI Radeon 21xx. Mythbuntu 9.04 has known bug for ATI cards and here is the solution;

[https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/341898](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/341898) 

I hope it helps.

~Jangia

what exactly did you do?
-run Mario's patch at [https://launchpad.net/~superm1/+archive/ppa](https://launchpad.net/~superm1/+archive/ppa)
-set the "DRI off" option 
-...

---

### Post by Kheos on 2009-05-25
anyone else got this problem and a solution?

---

### Post by Kheos on 2009-05-30
bump

---

### Post by ohrock on 2009-06-01
bump again...

I have this problem as well, and I am curious about how exactly can we get this working.

Roberto

---

### Post by cederqvist on 2009-06-03
Hi' 
 
I have this problem as well, and I am curious about how exactly can we get this working. I have an old ATI 9600 GC.
 
Michael

---

### Post by beebad on 2009-06-03
New to LINUX, is this patch installed via dpkg ?

---

### Post by Kheos on 2009-06-07
seems like I'm not the only one with this problem

---

### Post by Kheos on 2009-06-09
Bump

---

### Post by nofear07 on 2009-06-10
Ok, here is how you can work around it.
edit /etc/X11/xorg.conf

```
sudo vi /etc/X11/xorg.conf
```
go down to the Section "Screen" and insert:
```
        Option  "DRI" "off"
```

Save your file, then do:
```
sudo /etc/init.d/gdm restart
```
or reboot and it should be fixed.

It's sad to see that Jaunty has this bug.  But it applies to all video cards that don't use NV proprietary drivers i.e. ATI, Intel etc...

---

### Post by Kheos on 2009-06-16
thanks, that indeed worked.
my resolution is still messed up, but atleast I can see what I'm doing.

---

### Post by mcmasterp on 2009-08-27
no one wants to help huh? 

well add me to the list I installed mythbuntu 9.04 on an amd64 with ati x550 pcie. I get the same screenand the same level of support. at least winblows works out of the box

---

### Post by mcmasterp on 2009-08-27
SOLUTION!

vote with my wallet and show ATI what happens when you discount linux users. I have purchased a Nvidia card that works

---

### Post by mpog on 2009-08-28
Hi all,
I'm really new with ubuntu/mythbuntu (installed yesterday, first time) and I have the same problem when the configuration for the backend starts (old Compaq notebook, ATI graphic card integrated). So have I only to set DRI to off?

---

