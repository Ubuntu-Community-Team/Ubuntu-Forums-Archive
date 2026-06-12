---
title: "i cant play dvd's please help"
date: 2009-02-17
forum: Multimedia Software
---

### Post by Billbrasky7718 on 2009-02-17
i have been reading through forum's but cant seem to find my problem...

I cant play dvd's, I can read from my dvd drive, write to it but i cant play dvd movies. When i try and run regionset i get this 

regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.

there is a video dvd in the drive

I am running ubuntu 8.04 on a new m-series gateway, off of an external hard drive. Can anyone help me?

---

### Post by SunnyRabbiera on 2009-02-17
you need libdvdcss probably, by default ubuntu cant provide it because in some nations its not considered legal.
I personally dont care and install it anyway, another package to try is totem xine.
If you need help installing these things just ask.
To begin I suggest using medibuntu:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Billbrasky7718 on 2009-02-18
i have installed totem with the xine backend and it freezes on me when i try and load a dvd, I have also messed around with gxine

It seem's to me that ubuntu is having trouble even reading the content of a dvd when i have it in the drive... I had an old scenery dvd that came with an old computer that i got to play one of the video file's on... after having that dvd in the drive every other dvd that i put in with that file name has the same video thumbnail pictures..

thank you very much i really appreciate your time.

Colin kraus

---

### Post by Billbrasky7718 on 2009-02-25
ok i am getting there but now i keep getting this funky error message

: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: You may want to run apt-get update to correct these problems

i might be able to do this myself but im not sure what im apt-getting

---

### Post by cariboo on 2009-02-25
If you follow SunnyRabbiera's advice and enable the Medibuntu repositories for your version, then scroll down and get the gpg Key. ALl you have to do is opn System->Administration-->Synaptic Package Manager and search for libdvdcss2, mark it for installation and install it, you'll be playing dvd's in about 5 minutes.

Jim

---

### Post by Billbrasky7718 on 2009-02-25
Hey guy's thank you for putting up with me this is pretty cool i got video now but it's all chopped up into diffrent scenes but if your busy im sure i will sort this out too.

Thank's a million... ubuntu rock's... you guy's are great

---

