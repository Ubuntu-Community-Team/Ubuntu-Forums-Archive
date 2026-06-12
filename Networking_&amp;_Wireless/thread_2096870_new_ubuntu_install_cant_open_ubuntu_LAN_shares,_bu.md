---
title: "new ubuntu install cant open ubuntu LAN shares, but others can"
date: 2012-12-21
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2012-12-21
I just setup a new Ubuntu PC.
I can see the shares, navigate folders, but when I try to open I cant, says permission denied.
Using the new Ubuntu pc, I can connect to a win7 box and open its shares.

Another Ubuntu install can open the shares that the new ubuntu install cant.
The shares are open to everyone on the ubuntu machine.


So what do you think is the problem?
The shares that wont open are on an Ubuntu PC

I shared a folder on the new ubuntu PC and other ubuntu PC can open it's shares.

pic of a view of the share dialog

---

### Post by sdowney717 on 2012-12-21
from the new ubuntu pc, here is what happens
shares are seen, but cant open

---

### Post by sdowney717 on 2012-12-21
strangely I just found out one of the folders will open the pictures.
it is very odd, some folders you can browse and see the file names but cant open them.
Others you cant browse, just says permission denied.
Some will open a picture, but a subfolder will say permission denied.
I just seems very random.

---

### Post by fdrake on 2012-12-21
ca you post the permissions of the main folder "ls -l" ans of the folder that you cannot open

---

### Post by sdowney717 on 2012-12-21
I see what you mean. 

Ok, here is for a folder I cant open pictures
```
scott@scott-P5QC:~$ ls -l Pscrapbookscan
total 2668
-rw-r----- 1 scott scott 770281 Nov 21 15:33 americangirl.jpeg
-rw------- 1 scott scott 135309 Nov 21 15:46 christmas2001fam.jpg
-rw------- 1 scott scott  36695 Nov 21 15:47 daddykriskayak.jpg
-rw------- 1 scott scott  38556 Nov 21 15:47 davesusewed2.jpg
-rw------- 1 scott scott  51380 Nov 21 15:48 davesusewedd.jpg
-rw------- 1 scott scott  78653 Nov 21 15:48 famext.jpg
-rw------- 1 scott scott  62081 Nov 21 15:48 granmomlandonbaby.jpg
-rw------- 1 scott scott  46064 Nov 21 15:48 jessballon.jpg
-rw------- 1 scott scott  36651 Nov 21 15:48 jesscheerleader.jpg
-rw------- 1 scott scott  58967 Nov 21 15:49 jesscreek.jpg
-rw------- 1 scott scott  10498 Nov 21 15:49 jessduckchristman.jpg
-rw------- 1 scott scott  69841 Nov 21 15:49 jesskrisseaworld.jpg
-rw------- 1 scott scott  48260 Nov 21 15:49 jessswing.jpg
-rw------- 1 scott scott  52575 Nov 21 15:49 jesstire2.jpg
-rw------- 1 scott scott  48992 Nov 21 15:49 jesstire.jpg
-rw------- 1 scott scott  29037 Nov 21 15:49 jesswithapple.jpg
-rw------- 1 scott scott  24721 Nov 21 15:50 kristinbabe2.jpg
-rw------- 1 scott scott  26911 Nov 21 15:50 kristinbabe.jpg
-rw------- 1 scott scott  44667 Nov 21 15:50 kristingpday.jpg
-rw------- 1 scott scott  40167 Nov 21 15:50 kristinhorse.jpg
-rw------- 1 scott scott  56272 Nov 21 15:50 krisunknown.jpg
-rw------- 1 scott scott  62887 Nov 21 15:50 Landon.jpg
-rw-rw-r-- 1 scott scott 458429 Dec  1 12:56 Receipt2.jpg
-rw------- 1 scott scott  41107 Nov 21 15:50 scottdavidyoung.jpg
-rw------- 1 scott scott  76268 Nov 21 15:50 scotttriciafirsthouse.jpg
-rw------- 1 scott scott  49511 Nov 21 15:51 scottwithbuickcabin.jpg
-rw------- 1 scott scott  40562 Nov 21 15:51 scottwithjesscouch.jpg
-rw------- 1 scott scott  39413 Nov 21 15:51 shawnjesskids.jpg
-rw------- 1 scott scott  53025 Nov 21 15:51 Shawn.jpg
-rw------- 1 scott scott  56486 Nov 21 15:51 trichscottcollege.jpg
-rw------- 1 scott scott  28070 Nov 21 15:51 triciajess.jpg

```

This one I can open pictures. I did a test and copied a picture 38.jpg that cant open into this folder and it still cant open yet the others can

```
scott@scott-P5QC:~$ ls -l Phospital
total 1560
-rw-r--r-- 1 scott scott  58928 Jan  5  2011 0714092039.jpg
-rw-r--r-- 1 scott scott  79133 Jan  5  2011 0714092040.jpg
-rw-r--r-- 1 scott scott  57426 Jan  5  2011 0723091459.jpg
-rw-r--r-- 1 scott scott  73191 Jan  5  2011 0727091428.jpg
-rw-r--r-- 1 scott scott  59278 Jan  5  2011 0727091429a.jpg
-rw-r--r-- 1 scott scott  70878 Jan  5  2011 0727091429b.jpg
-rw-r--r-- 1 scott scott  74438 Jan  5  2011 0727091429.jpg
-rw-r--r-- 1 scott scott  61744 Jan  5  2011 0727091430a.jpg
-rw-r--r-- 1 scott scott  66787 Jan  5  2011 0727091430.jpg
-rw-r--r-- 1 scott scott  73749 Jan  5  2011 0727091431.jpg
-rw-r--r-- 1 scott scott  64490 Jan  5  2011 0727091432.jpg
-rw-r--r-- 1 scott scott  85064 Jan  5  2011 0803091100.jpg
-rw-r--r-- 1 scott scott  62810 Jan  5  2011 0912091817a.jpg
-rw-r--r-- 1 scott scott  78983 Jan  5  2011 0912091817.jpg
-rw-r--r-- 1 scott scott  67894 Jan  5  2011 0912091818a.jpg
-rw-r--r-- 1 scott scott  75169 Jan  5  2011 0912091818.jpg
-rw------- 1 scott scott 442761 Oct  6  2008 38.JPG
scott@scott-P5QC:~$ 

```

---

### Post by fdrake on 2012-12-21
you are missing read permission for others
chmod o+r -R ~/mySgared_folder

---

### Post by sdowney717 on 2012-12-21
Ok will try it.

Before any changes, I just tested using a win7 pc on this LAN to view the shares and they open!
including the 38.jpg file. etc...

That fixed it, thanks.
Still I dont know how other PC could view these.

---

