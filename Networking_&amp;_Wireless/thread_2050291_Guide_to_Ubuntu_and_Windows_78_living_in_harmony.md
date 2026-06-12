---
title: "Guide to Ubuntu and Windows 7/8 living in harmony?"
date: 2012-08-30
forum: Networking &amp; Wireless
---

### Post by espo111 on 2012-08-30
Is there a DEFINITIVE guide to setting up a home network where Windows 7/8 boxes can live peacefully with Ubuntu systems?

I have to keep a windows machine because of adobe  programs but I have 4 other Ubuntu machines running. But I cannot decipher the way to make them all connect with each other (Ubuntu reads a Windows share, a windows 7 machine reads a Ubuntu share). so is there a really good guide out there instead of all these forum posts that never seem to address my situation?

I simply do not understand how they connect or how it works.

any help would be appreciated.

---

### Post by BrianBlaze on 2012-08-30
Windows has a lot of trouble seeing any file system that is not NTFS or FAT... and I would be willing to guess that you Ubuntu is an ext4 filesystem... To me the best idea is to have all of your pc's Ubuntu and have one with a virtual machine of Windows 7 or 8 or whatever. I am not an expert at this I just saw that you have no response and that alone can be really frustrating so just to pop some ideas in your head! I suppose it depends on what you are using Adobe for but you could always try it and test it out before officially setting up a new Ubuntu box. I am assuming you are not using photoshop since you are not using a MAC but of course I could be wrong and if your PC is powerful enough it could probably run photoshop in a vm anyways :) Just some suggestions and information! hope I helped a bit.

---

### Post by espo111 on 2012-08-30
> **BrianBlaze said:**
> ... photoshop since you are not using a MAC but of course I could be wrong and if your PC is powerful enough it could probably run photoshop in a vm anyways :) Just some suggestions and information! hope I helped a bit.


I am using photoshop, indesign illustrator and premiere, sometimes all at once because clients use them so i need strong access to the hardware. I tried a VM but it was too slow. Macs are also too slow for my taste (i build my own PCs).

thanks for the help!

---

### Post by BrianBlaze on 2012-08-30
> **espo111 said:**
> Macs are also too slow for my taste (i build my own PCs).

Unless you wanna pay 3 grand for an almost fast MAC lol... Are you using vmware or virtualbox? I know vmware has really good 3D Graphic support (although vmware is not free). You have to be the smartest Adobe user I have ever seen... I don't know anyone who uses the Adobe suite on anything but a MAC and I am not a fan of MAC and have always wondered why everyone uses them. Thank you for breaking the mold since clearly if you build a PC for 3 grand you will end up with a PC that is more powerful then a $10000 mac! :guitar:

---

### Post by redmk2 on 2012-08-30
> **espo111 said:**
> Is there a DEFINITIVE guide to setting up a home network where Windows 7/8 boxes can live peacefully with Ubuntu systems?

I have to keep a windows machine because of adobe  programs but I have 4 other Ubuntu machines running. But I cannot decipher the way to make them all connect with each other (Ubuntu reads a Windows share, a windows 7 machine reads a Ubuntu share). so is there a really good guide out there instead of all these forum posts that never seem to address my situation?

I simply do not understand how they connect or how it works.

any help would be appreciated.

There is no simple definitive guide as Samba is complex and adaptable to many situations.  Most forum posts are based on the writers experience without thought to other user needs or capabilities.  This in itself is not bad.  You should be aware of your needs and use  only the features you need. 

One of the best teaching guides would be Samba by example, available [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.samba.org/samba/docs/man/Samba-Guide/").  This takes the reader through the most basic to very complex set up.

---

### Post by espo111 on 2012-08-30
> **BrianBlaze said:**
> Thank you for breaking the mold since clearly if you build a PC for 3 grand you will end up with a PC that is more powerful then a $10000 mac! :guitar:


yeah! i don't like macs and always use CS on pcs...if Adobe ever ports them to Linux, i will never touch a windows machine again! Hopefully GIMP and Sribus and inkscape can get more used and then people will adanodn them too.


but i have to live in the M$ world right now so I need to figure out samba I guess.

---

### Post by zendob on 2012-10-09
Coming back to you a little late... but have you considered keeping your data somewhere central, like FreeNAS, that you can then access from any PC or device etc?

---

