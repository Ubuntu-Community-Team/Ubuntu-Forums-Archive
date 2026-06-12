---
title: "nvidia 8400 GS driver question"
date: 2008-07-24
forum: Multimedia Software
---

### Post by stmartin on 2008-07-24
Hello! :)

Can you please tell me should I use the restricted drivers from System-->Administration-->Hardwire drivers or should I use the drivers from the download site of nvidia? I am using ubuntu 8.04.

Thank you.

---

### Post by overdrank on 2008-07-24
> **stmartin said:**
> Hello! :)

Can you please tell me should I use the restricted drivers from System-->Administration-->Hardwire drivers or should I use the drivers from the download site of nvidia? I am using ubuntu 8.04.

Thank you.

HI and some users have had success with both methods. I do not have that model but I have used both and had no issues. If you would like you may also look at Envy.

---

### Post by stmartin on 2008-07-24
Thanks for the reply. When I tried the first method in Hardware drivers, the restrictred driver shows: "Not in use", is this bad?

---

### Post by overdrank on 2008-07-24
> **stmartin said:**
> Thanks for the reply. When I tried the first method in Hardware drivers, the restrictred driver shows: "Not in use", is this bad?

Ok so you have enabled the device but it states not in use? Have you rebooted the system after enabling.

---

### Post by balaknair on 2008-07-24
Hi
I've got an nVidia 8400GS too, and I've been using the drivers from the Restricted Drivers Manager(I'm on Gutsy 7.10 though) with no issues. I don't think the 'not in use' message should be an issue. Maybe you just have to click the 'enable' option(see screenshot) and reboot. I've used the nVidia drivers on Feisty earlier, worked OK there too(though I did have some trouble at first, I tinkered too much with Xorg.conf and totally lost my graphic interface and had to do some command line acrobatics to fix it; but that was my fault, not the driver's).

---

### Post by jonelnz on 2008-07-24
Hi stmartin

I also have an 8400 GS which runs fine in Ubuntu 8.04 with the restricted drivers from System > Administration > Hardware Drivers. As *balaknair* has correctly pointed out just enable driver and restart your system. You shouldn't need to edit any files at all. (least I didn't)

---

### Post by stmartin on 2008-07-24
Thank you all. I installed it, and it works properly. I hope everything is gonna be alright.

---

### Post by rpbulls on 2008-08-04
I'm a noobie to this. I have a Dell inspiron 1720 with Nvidia 8400GS installed. I have not yet been able to enable my graphics card and am using a generic driver. 
I tried enabling my graphics card and i had a message from the Driver installation tools saying i had "xen kernel" installed and the graphics card wouldn't work with that. 
So, i reverted from that and never ventured into enabling my card again. 

Is there a comprehensive step-by-step process on how i can setup my graphics driver? I currently use Hardy Heron (8.04) and this is what i get when i do "uname -a" 
Linux ravilt 2.6.24-19-server #1 SMP Sat Jul 12 00:40:01 UTC 2008 i686 GNU/Linux

Any help is greatly appreciated. 

thx

---

### Post by krishnagudi on 2009-08-08
hi, i h've nvidia 8400GS graphics card, installed ubuntu  8.10 works fine with nvidia restricted driver version- 177

---

