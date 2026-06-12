---
title: "Trying to connect 2 ubuntu computers"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by Boneyard on 2009-01-21
Hi all, I have just discovered ubuntu, god knows why anyone uses windows, this software is amazing. Anyway I have solved most of my problems (wifi, sound etc) trawling the forums and help files but this one has got me stumped.

All the threads i have found is people having problems of linux seeing windows, thats not the case here!

I have 1 laptop running ubuntu 8.1 (dual boot with vista) 1 desktop running ubuntu 8.1 (fresh install) 1 desktop running Windows XP and a little netbook running Linpus (its an aspire one)

Heres the problem, from all of the Linux boxes, I can see the windows box just fine (windows wont look at linux but who cares, the windows box just has my files on it like a little server) BUT none of the Linux machines can see eachother, I can ping them but thats about the limit of my command line skill! I want to be able to see the drives/computers on my ubuntu desktop.

Am i missing somthing?

Thank you for any help

---

### Post by Coreigh on 2009-01-21
Are you wanting to share files between the Linux boxes? Or remote control/desktop? For the latter you need to enable remote (System >> Preferences >> Remote Desktop) or install ssh for remote command line.

To share files the quick and dirty is just to swap them through one of the Windows shares that everyone can see. To share directly you could use Samba ( I assume this is installed for Windows connections) but NFS is more efficient for Linux to Linux. I am not currently doing this but have in the past. Here's a link;
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by 2hot6ft2 on 2009-01-21
> **Coreigh said:**
> NFS is more efficient for Linux to Linux. I am not currently doing this but have in the past. Here's a link;
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
That's how I am doing mine right now since I don't use windows often enough to bother with setting it up. For 2 linux computers NFS is great I just created a share folder on the desktop of each pc and drop whatever I want to move or share into the folder.

If you plan on having windows pc's connected and sharing back and forth with them as well then this may be the way to go for a easy setup.
[http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

---

### Post by Boneyard on 2009-01-21
Thank you very much for the fast replies!

I would like to see the linux boxes as icons  (as the windows network is seen) so a click gives me hdd, and files i can click and either run from (streaming video that sort of thing) or copy from

Im a little unsure of the first method (currently re reading it) but the FTP doesnt seem to fit what i need to do

---

### Post by 2hot6ft2 on 2009-01-21
What you want may be samba or ssh. Here's the ubuntu networking documentation for networking and there are lots of people here that have done how to's that can help with those. But this lists the options here.
[https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking)

---

### Post by timcredible on 2009-01-21
> **Boneyard said:**
> 
I would like to see the linux boxes as icons  (as the windows network is seen) so a click gives me hdd, and files i can click and either run from (streaming video that sort of thing) or copy from


for that, just go to places->home folder, and then right-click on a folder, select 'sharing', and share it.  the system may prompt you to install samba, go ahead and install that, and then reboot.  your ubuntu box will show up under the Workgroup group now (standard group for windows).

---

### Post by Boneyard on 2009-01-21
Thanks Tim!

I am a COMPLETE IDIOT

Thats EXACTLY what I wanted, i feel sooo stupid

Thank you to all that helped me

---

### Post by jonobr on 2009-01-21
In the words of a great man

> Stupid is as stupid does

Your using ubuntu.... your not stupid.

---

### Post by Boneyard on 2009-01-21
Well, its thrown up another problem, I can see the computers/folders now, but I have no access to them. I am being asked for a password, but its always rejected. (i am using the password i used when i installed)

So i set the permissions to 'guest user, for those who have no account' and still nothing, i get a message that it wont mount the device

what else am i doing wrong?

Thanks for all the help

---

### Post by Iowan on 2009-01-21
For mounting, [this]("http://ubuntuforums.org/showthread.php?t=288534") is a must-read.  Probably also covers a few other questions you will eventually have.

It is also worth mentioning... Samba is not the only file system that can be used between two Ubuntu machines.  A couple of others:
[NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") and [SSHFS]("https://help.ubuntu.com/community/SSHFS")

---

### Post by detroit/zero on 2009-01-25
> **jonobr said:**
> **Your** using ubuntu.... **your** not stupid.
:lolflag:

---

