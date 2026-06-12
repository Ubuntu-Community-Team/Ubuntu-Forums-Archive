---
title: "[SOLVED] no theme dir?"
date: 2008-09-04
forum: Mythbuntu
---

### Post by stevanbt on 2008-09-04
Hi,
I've just applied the latest updates and broken mythtv.  I had a bit of trouble getting mythbackend to speak to mysql, but that's fixed.  In a rush to get things sorted I removed my existing tuner card in mythtv-setup - stupid of me I know.

I'm trying to add them back in through mythtv-setup, but when I select Capture Cards --> New Capture Card I get a blank screen and the terminal output is as attached (sorry can't capture text output in the terminal window).

From the messages I assume the error is with the themes (no theme dir).

Thanks, Steve

---

### Post by oobe-feisty on 2008-09-04
go to mythbuntu-control-centre and check you have themes installed 

but if were you i would consider purging your myth install and starting from scratch since you dont have very much done yet

---

### Post by se99paj on 2008-09-04
I've got exatly the same problem, this isn't on a new install this is only after installing the latest updates.

Could you let me know how you managed to get the backend speaking to MYSQL. I can't get my front end to connect to the backend and this could be related.

---

### Post by oobe-feisty on 2008-09-04
this is strange im using the mythbuntu Automated Weekly MythTV 0.21-fixes Builds repos and nothing has gone wrong for me

---

### Post by stevanbt on 2008-09-04
Ok I think I'm sorted now:-

frontend/backend connection, I opened a terminal and did (taking all the defaults):-
```
sudo dpkg-reconfigure mythtv-common
```

missing theme directory, I just linked to the real theme directory (I don't think this is needed as it didn't sort out the blank screen in mythtv-setup, but it stopped the messages being displayed - which is nice.)
```
ln -s /usr/share/mythtv/themes/ themes

```

To get rid of the blank screen in mythv-setup I recompiled the v4l source:-
```
cd v4l-dvb/
make
sudo make install
sudo reboot now

```
Reboot was just to make sure :)

Hope this helps someone.

Thanks, Steve.

---

### Post by se99paj on 2008-09-04
I was just about to get back to you on that, a shutdown then reboot seemed to resolve most of my issues, I'm just recompiling v4l-dvb to see if it resolves my card problems.

---

### Post by mosabua on 2008-09-07
> **se99paj said:**
> 
Could you let me know how you managed to get the backend speaking to MYSQL. I can't get my front end to connect to the backend and this could be related.

I am in the same trouble and would love to know as well. I guess I will be turning off the hardy backports repo again. Although I needed to get subversion 1.5 from there.. oh well

---

### Post by stevanbt on 2008-09-07
> **mosabua said:**
> I am in the same trouble and would love to know as well. I guess I will be turning off the hardy backports repo again. Although I needed to get subversion 1.5 from there.. oh well

Mine is a combined FE/BE, but to get them talking to MySQL I opened a terminal and did (taking all the defaults):-

```
sudo dpkg-reconfigure mythtv-common
```

Thanks, Steve.

---

### Post by mosabua on 2008-09-12
The defaults where all empty for me but I added the right info and that did the trick for me. Thanks.

---

