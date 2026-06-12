---
title: "Absolute Beginner - Ubunto 10.04.2 - Zoom Wireless-G USB 4410B Help"
date: 2011-05-20
forum: Networking &amp; Wireless
---

### Post by JamieH93 on 2011-05-20
Hi All;
 
Im very new to Ubuntu and i am having trouble setting up my wireless device:
 
Zoom Wireless-G USB 4410B
 
So far i have .inf files which got extracted from windows drivers (Searched around for solutions first).
 
I dont have any internet connection on ubuntu however i do on my Windows 7.
 
I need an absolute beginner help; I'll ive done on Ubuntu is start it up and logged in. Nothing else.
 
Any help;
 
Thanks, Jamie. btw its 5:26am here O.O
 
EDIT:
 
I typed lsusb and got a list; this one said zoom..
 
Bus 001 Device 006 ID 0803:4410

---

### Post by chili555 on 2011-05-20
You need to install ndiswrapper before we can proceed. I don't know how you installed Ubuntu. If you have the install CD, it's on there. Browse the contents of the CD and browse to pool/main/n/ndiswrapper and drag and drop the two ndiswrapper .deb files to your desktop. Open Applications > Accessories > Terminal and do:```
cd Desktop
sudo dpkg -i ndis*.deb
```The wildcard * will install all the .deb files that are named ndis-something; namely all of them.

Next we need to make sure you have the correct .inf file. ndiswrapper uses the Windows ***XP*** .inf file. Vista, 7 or 95 simply won't work! Here is a guide that will help identify the one you want:  [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Zoom_4410b](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Zoom_4410b)

Notice the usb.id is the same: 0803:4410 

It explains the process very well.

Post back if you get stuck. Uncle Chili is here for you.

---

### Post by JamieH93 on 2011-05-20
Yes i have now installed ndiswrapper and i also have the files for the wireless.
 
I also followed that little tutorial however got stuck on one part(i also did get a successful readout):
 
```

If you did get a successful readout, saying your drivers are installed, then you can now do:
ndiswrapper -m
```I did this however the file it made dosesnt have .conf on it.Anything i should try?Thanks, Jamie.

---

### Post by chili555 on 2011-05-21
> I did this however the file it made dosesnt have .conf on it.We can fix it quite easily if you can tell is what it was. It shouldn't affect the operation of the wireless. Is it working?

---

### Post by JamieH93 on 2011-05-21
> **chili555 said:**
> We can fix it quite easily if you can tell is what it was. It shouldn't affect the operation of the wireless. Is it working?

No its not working; Infact when i try to do the next bit in the tutorial it does nothing then freezes up; If i restart the OS wont boot after.

---

### Post by chili555 on 2011-05-22
> **JamieH93 said:**
> No its not working; Infact when i try to do the next bit in the tutorial it does nothing then freezes up; If i restart the OS wont boot after.Ouch! If it won't boot, all I can suggest is a reinstall.

---

### Post by JamieH93 on 2011-05-22
> **chili555 said:**
> Ouch! If it won't boot, all I can suggest is a reinstall.

I have done this; Several Times :(

---

