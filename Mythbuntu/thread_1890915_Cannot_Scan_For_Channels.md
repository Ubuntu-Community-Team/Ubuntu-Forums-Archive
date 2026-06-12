---
title: "Cannot Scan For Channels"
date: 2011-12-04
forum: Mythbuntu
---

### Post by colonelpenguinx on 2011-12-04
I decided to give myhtbuntu a shot for the first time the other yesterday, and things have gone pretty well so far except one major problem.  I cannot seem to scan for any channels.  I am using two HVR-850 usb sticks.  I have tried using the built in scan function on MythTV, scan, and w_scan to look for over-the-air broadcasts with no success.  I am running 11.10 64-bit.  Can anyone help me get this sorted out?  Thanks in advance!

I have used these tuners for years on a 32-bit mythdora install without problems.  The drivers appear to be loading, but I am not certain of this.  I could use some help verifying what exactly is causing the problem.

---

### Post by jlp_engineer on 2011-12-19
Hello,

I too am having the same or similar problem.  I have three PVR-150's and a pcHDTV HD-5500 in the same backend.  When I go to scan for digital channels using the HD-5500, things work like I would expect.  It finds a bunch of encrypted QAM channels and a few unencrypted ones.  I then began going through the PVR-150's, and to my surprise, scanning for the analog channels did not work.  It just flew right through all the channels without locking onto anything.  

I did some reading (and there is not much), but found some old posts talking about the analog channel scanner function in MythTV and how it has been broken since version 0.21.  I read the bug report on it, and it has been opened, had its status changed from serious to trivial, and then closed.  It does not seem that there is a lot of concern about "not" having the ability to scan for analog channels.  Apparently we are all supposed to be digital and forget about analog channels.  Well...my local cable provider is still broadcasting 54 channels in analog, and only 5 stations in unencrypted digital.  Consequently, all my MythTV watching will be on the analog stations, so being able to scan them in is pretty important to me.:mad:   If I was a programmer, I would grab the source and fix it myself.  Unfortunately, my expertise extends only into computer storage hardware, and not a lot into programming.

I have also read that a user should be able just use the guide information and use the channel information there.  My only problem with that, is that this assumes (a big problem) the channel information is correct, and that none of the stations need fine tuning for frequency drift, etc.  I believe the analog channel scanner code should be fixed and re-inserted into the MythTV code.

Just my 2 cents.

):P

---

