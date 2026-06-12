---
title: "Syncing iPod touch via iTunes"
date: 2012-04-02
forum: Multimedia Software
---

### Post by JawsThemeSwimming428 on 2012-04-02
I'm running Ubuntu 11.10 on my laptop. I have a 3rd generation iPod touch that I use religiously (not too much of an Apple advocate but the iPod is wonderful). Anyway, my issue is I dualboot and would like to be able to sync my iPod regardless of what OS I'm using (Windows 7, Ubuntu, or Chakra). The iPod get's mad when you try to sync it via multiple ways so I'd like to stay away from that. My thought is this:

1. Install Virtualbox or another virtualization client on each OS.
2. Install Windows 7 on that virtual machine. 
3. The virtual machine disk and files would be stored on a separate DATA partition that I share between all OS's
4. Boot the virtual machine to sync my ipod (regardless of OS).
5. The Music folder that currently holds all of my music and my iTunes library is pointed to (that lives on that shared DATA partition) would still sit there.
6. Set up a folder share to that music partition in the VM so that iTunes, in the Win 7 VM, can use that as the library folder.
7. This way, I can still make changes to my Music folder on the DATA partition and iTunes in the VM would have access to it as well.


I haven't tried this yet cause I'm not too sure of whether it will work or not. Any thoughts? I welcome all feedback as I don't claim to be any type of expert on this

Thanks!

---

### Post by 2F4U on 2012-04-02
It should be possible to use the same VM from either Windows or Linux. I have copied VM's between different Linux systems without much problems, but I haven't tried it with Windows. However, the internal format of the VM should be the same whether it is used from Windows or Linux.

---

### Post by leclerc65 on 2012-04-02
It's exactly what I am doing.
I run Windows XP inside VirtualBox. All the data is kept on a NTFS partition which is shared between Ubuntu and Win XP.
No problem and/or headache with virus (XP) or driver (Linux). Talking with Garmin 60Csx , TomTom 730, iPod Touch ... is a breeze, while not worrying too much about malwares. 
The other day I could not keep myself from laughing while a rogue site tempted upload an exe file while I searched for the Linux driver for my Brother printer. I clicked on the CANCEL button when seeing it's a Windows driver, it insisted on uploading it anyway.
The advantage of virtual XP is you don't have to re-install all the drivers if you upgrade the host, just export it then re-import later.

---

### Post by JawsThemeSwimming428 on 2012-04-03
So you just pointed your Virtualbox install at the virtual disk/files on the shared partition and it worked without any special configurations? I'm trying to figure out if there's any settings or tweaks to make since the same VM will be running off two different host OS's. If not, this sounds like a piece of cake. I just can't believe that you can pass the iPod touch USB connection through an Ubuntu host to a Win 7 VM and everything works (syncing, etc.).

That's awesome.

---

### Post by leclerc65 on 2012-05-07
Of course I have to install drivers on the virtual XP, no miracle there. But you know that every new device, when you open the box, the XP driver CD is there - or you search for them on the net easily.

---

### Post by iMurshaq on 2012-05-08
Is it possible to install iTunes on Ubuntu via Wine? If so, try that because I believe that an iPod can be synced with up to 5 computers.

---

### Post by cyberphrog on 2012-06-10
What driver(s) do you need to get an XP Vbox to recognize an iPod when I plug it onto the usb cable?  The device list doesn't capture the iPod when I plug it in and I haven't found a way yet...

---

