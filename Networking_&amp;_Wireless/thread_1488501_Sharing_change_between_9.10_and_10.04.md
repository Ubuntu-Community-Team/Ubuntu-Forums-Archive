---
title: "Sharing change between 9.10 and 10.04"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by Hannes.nz on 2010-05-20
Hi all...

A bit of background...
I have a MediaGate MG35 which allows me to play movies and things via my network from my computer.

This worked fine with Vista, but when I upgraded to Windows 7 the samba sharing changed and my MediaGate was no longer able to gain access to my shares on 7.

My solution was using VirtualBox with Ubuntu.  This worked fine on 9.10.  I did this by creating a folder in my /media folder called windows-share, giving it a share called movies with Guest access. and then adding the following line in the rc.local file to mount the windows share though VirtualBox: 
mount -t vboxsf movies /media/windows-share/ 
(movies being the name I gave the shared folder in VirtualBox)
So I had to do was start the VirtualBox and everything was setup without me having to do anything.

This then allowed me to get to my movies saved in windows with my MediaGate.  This worked great.

I've now got Ubuntu 10.04 on a new VirtualBox.  I've set up everything the same, but when I try to access the shared folder, it doesn't work.  If I try to access it with windows, it says that the share is not accessible or I don't have access.
This ONLY happens to the folder that has been mounted to, any other folder I share works fine.

Does anyone know what has changed that I may need to fix?
I would prefer to use 10.04 as it starts up a lot quicker so I don't have to wait as long for it to start up to be able to get to my movies.

Thanks!

---

### Post by Hannes.nz on 2010-05-21
Can no one help with this issue?

Thanks.

---

