---
title: "after every restart I have to mount same NAS?"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by attilab on 2009-03-28
untill now had to concentrate for initial setup, getting more relaxed and just noticing:
- after every restart I have to re mount one of the NAS HDD, it is IP connected to the router. no problem with mounting just doesn't look good to repeat every time
- the other NAS HDD is a USB connected to the router, no problem, allways on desktop=mounted, and BTW has an FTP server on it with several different levels of permissions
- wireless router Linksys WRT350N, 
- standard windows network, all set in XP, working well for years

---

### Post by sreeyeshns on 2009-03-29
Which is the filesystem?

---

### Post by fmw on 2009-03-29
You're ahead of me.  Please tell me how you mount your NAS.  I can connect but not access.

---

### Post by attilab on 2009-03-29
> **sreeyeshns said:**
> Which is the filesystem?
1.) the one NAS (80Gb) what comes automatically (USB connected to router) has NTFS, there I setup the FTP from XP (thru Linksys router software) as a share on WORKGROUP
2.) the second NAS is a RAID (500Gb)what doesn't come automaticaly, (IP connected to router) has a setup disk with some portable linux format (?? I don't know YET which one)what I setup from XP as a STORAGE shared on WORKGROUP.  
not a big problem, all working fine from a)2xXP's; b)Vista and c)Mac, only ubuntu restart can't see it (the #2) automatically, I have to mount it manually
my question is an educational project, what and how to do to make the automation?
thanks

---

### Post by attilab on 2009-03-29
> **fmw said:**
> You're ahead of me.  Please tell me how you mount your NAS.  I can connect but not access.
I could help you from XP :!: to mount a NAS, byt in ubuntu I have no idea :redface: YET, willing to learn, but just way to many :?: things to take care of, so one by one question, bothering ppl](*,),

---

### Post by onecuwldood on 2009-12-09
I've searched and searched Ubuntu forums and this thread is as close to the what I'm trying to find out as I can find. I have an existing Windows network, I'm still new to Linux/Ubuntu, I have a NAS on my network which I keep my MP3 files on. With Windows (& Windows Media Center) I have no problems. Windows has no problem automatically connecting to this drive as another driver letter. So I'm able to point Media Center to it for my library. I would like to try to do the same with something like Banshee in Ubuntu. But I have no idea how to get Ubuntu to automatically connect to the NAS share and it doesn't look like Banshee has anyway to import but from local directories.

---

### Post by zaphod777 on 2009-12-10
i have done this before but lost my documentation I will see if I can't digg it up.

---

### Post by onecuwldood on 2009-12-10
Any help would be great!  I really want to learn Linux but I'm starting to wonder if you can teach an old dog new tricks! ;-)

Also to clarify, I should not have said Media Center but rather Windows Media Player. I like that it libraries my music and from what I can tell, Banshee does too. It would just be nice to be able to import into the Banshee library without having to copy music to my notebook. Besides it really doesn't have the hard drive space to do it.

---

### Post by attilab on 2009-12-26
interestingly, this my question still after several months didn't received a value respons.
During these months I've gave up several times and ended up installing the Samsung media server on top of XP on one of my old PCs in the basement. So I am feeding my Samsung LCD TV thru LAN with its own software, its very limited but at least works.

---

### Post by zaphod777 on 2009-12-26
I think this is what you are looking for
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

> Automagically mount SMB shares
In order to have a share mounted automatically every time you reboot, you need to do the following:

With any editor, create a file containing your Windows/Samba user account details:


gksu gedit /etc/samba/user
KDE users must use kdesu rather than gksu and instead of Gedit they can use Kwrite as editor.

... it should contain two lines as follows:


username=samba_user
password=samba_user_password
Note: "samba_user" = the user name on the samba server (may be different from your log-in name on the client). "samba_user_password" is the password you assigned to the samba_user on the samba server.

Save the file and exit gedit.

Change the permissions on the file for security:


sudo chmod 0400 /etc/samba/user # permissions of 0400 = read only
Now create a directory where you want to mount your share (e.g. /media/samba_share):


sudo mkdir /media/samba_share
Now, using any editor, and add a line to /etc/fstab for your SMB share as follows:


sudo cp /etc/fstab /etc/fstab.bak
gksu gedit /etc/fstab
Add a line for your SMB share:


//myserver_ip_address/myshare  /media/samba_share  cifs  credentials=/etc/samba/user,noexec  0 0
The share will mount automatically when you boot. The "noexec" option prevents executable scripts running from the SMB share.

To mount the share now, without rebooting,


sudo mount /media/samba_share
You can unmount the share with :


sudo umount /media/samba_share
If you wish to increase security at the expense of convenience, use this line in /etc/fstab


//myserver_ip_address/myshare  /media/samba_share  cifs  noauto,credentials=/etc/samba/user,noexec  0 0
The noexec" option prevents executable scripts running from the SMB share.

Edit /etc/samba/user, remove the password (leave just the samba user).

Now the share will NOT automatically mount when you boot and you will be asked for your samba password.

Mount the share with :


sudo mount /media/samba_share
CIFS may cause a shutdown error.

CIFS VFS: Server not responding.

---

### Post by CharlesA on 2009-12-26
Samba would be the way to go.

---

### Post by zaphod777 on 2009-12-26
> **CharlesA said:**
> Samba would be the way to go.

He already is the NAS he is trying to connect to is already running Samba.

His issue is that after he reboots ubuntu he needs to remount the shares on his ubuntu machine.

The documentation I provided him should do the trick.

---

