---
title: "Radeon 5830 video card"
date: 2010-06-03
forum: Multimedia Software
---

### Post by sumigo on 2010-06-03
Hello Forum,

I am slowly and steadily learning linux, I love ubuntu, its a great platform and I cannot recommend it to enough people.

I have a small not so serious issue with my ATI card.

After I install the FGLXR driver I get a small message in the bottom right hand corner of the desk top, it has the AMD logo and it says "unsupported hardware".

I have tried reinstalling the OS and have reinstalled the drivers but every time I do it comes back, it is not there on 10.04's stock drivers however.

Anyone know what I can do to get rid of it?  As I said it isnt the end of the world, everything is running great, I installed NeverWinter Nights and it looks great except for the small AMD logo I mentioned.

I am getting used to it but i would like to get rid of it if possible.

I am running:

AMD Phenom 2 X4 945 Black
4 gigs of A data ddr 2
Gigabyte Radeon 5830
Gigabyte mobo (cannot remember the model # right now as I am at work)
Lucid Lynx 64 bit.
Any help would be appreciated.

---

### Post by xzero1 on 2010-06-03
I've had a similar issue. It is likely your card is not yet supported in linux with the current driver. For fglrx you will have to wait for the next release or try a beta version. Its also possible it could be supported in an earlier Ubuntu release.

---

### Post by Yellow Pasque on 2010-06-03
Another thing to try is using ATI's control file from another Catalyst release. Here is the control file from Catalyst 10.5 (released last week). Download it to your home directory and:
```
cd ~/
tar xzf control.tar.gz
sudo cp /etc/ati/control ~/control.bak
sudo cp control /etc/ati
```
Log out and back in to restart the X server.

If it doesn't work or breaks something, restore your old one:
```
sudo cp ~/control.bak /etc/ati
```

---

### Post by drreed on 2010-06-04
> **Temüjin said:**
> Another thing to try is using ATI's control file from another Catalyst release. Here is the control file from Catalyst 10.5 (released last week). Download it to your home directory and:
```
cd ~/
tar xzf control.tar.gz
sudo cp /etc/ati/control ~/control.bak
sudo cp control /etc/ati
```Log out and back in to restart the X server.

If it doesn't work or breaks something, restore your old one:
```
sudo cp ~/control.bak /etc/ati
```


Thanks, I had the same problem with my new 5830 that arrived today. Now I don't. Now to check the HDMI cable and see if it works yet

---

### Post by justindisgustin on 2010-09-12
These instructions worked flawlessly for me as far as I can tell.  Exact same functionality as before (the driver seemed to be working fine already) but no annoying watermark.  This is with the 5830 and 10.04 x86
Reposted on my blog and gave credit/linked back here.  Thank you!  [http://mypcchronicles.blogspot.com/](http://mypcchronicles.blogspot.com/)

---

### Post by senormoll on 2010-10-01
Thanks a lot man... I unfortunately had to search too hard through all the threads about this subject to find yours.  The problem with using ATI's drivers is they don't work lol...they made video and stuff very choppy.  This let's me use the fully functional fglrx but without the watermark...thanks!

---

