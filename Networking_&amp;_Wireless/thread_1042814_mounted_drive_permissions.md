---
title: "mounted drive permissions"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by ffoeg on 2009-01-17
Hello. I managed to mount a windows share (off an XP Home) computer to an Ubuntu 10.1 workstation. I mounted the drive to a subdirectory on the /mnt directory.
After that happened, I realized that I couldn't do anything with the files and folders inside the mounted drive. I don't have the permissions necessary. I tried changing the permissions from the terminal, I tried changing my user group to root, nothing straightened it out.

I even mounted it to a different directory, to one within my Home folder. That didn't help.

Can someone help my mount the drive so that someone within the user group on the ubuntu system can read/write the data?

The mount command I ran is:
mount -t cifs //192.168.xxx.xxx/sharename -o username=username,password=userpassword /mnt/subdirectory

Thank you for your help

---

### Post by skern03 on 2009-01-17
> **ffoeg said:**
> Hello. I managed to mount a windows share (off an XP Home) computer to an Ubuntu 10.1 workstation. I mounted the drive to a subdirectory on the /mnt directory.
After that happened, I realized that I couldn't do anything with the files and folders inside the mounted drive. I don't have the permissions necessary. I tried changing the permissions from the terminal, I tried changing my user group to root, nothing straightened it out.

I even mounted it to a different directory, to one within my Home folder. That didn't help.

Can someone help my mount the drive so that someone within the user group on the ubuntu system can read/write the data?

The mount command I ran is:
mount -t cifs //192.168.xxx.xxx/sharename -o username=username,password=userpassword /mnt/subdirectory

Thank you for your help

If you're trying to mount a Windows share on another box on your network, then you have to set the share up on that machine first. You can locate it on Linux from Places, Network, Windows Network, <machine>, <share>. If you want it to be permanently visible, you can bookmark it in Nautilus.

If you're trying to make a windows instance on the SAME machine shareable to the rest of your Windows network (or Linux), then what you can try is Samba. Go to Synaptic (System, Administration, Synaptic Package Manager) and search for and install system-config-samba. Once installed, you can find it under System Administration, Samba. Then you just set up the shares you want. alternatively, you can run 
```
sudo apt-get install system-config-samba
```

Hope this helps... If I've misunderstood, apologies..,

---

### Post by ffoeg on 2009-01-18
Hi Skern.

Thanks for the reply. But I've already got that Windows folder shared out (with the appropriate permissions), and I've got Samba installed.
I'm able to successfully mount that Windows share. When I go  to the mount point on the file system I see the files and folders. But I can't create new folders within or modify the files. Is there anything missing in my mount command, that would allow members of the user group to have  the necessary permissions (r/w)?
Thanks.

---

### Post by ffoeg on 2009-01-18
Although I had already tried chmod, it worked this time. I used:
 chmod  -R  777  /mnt/mount-point

Now I have read/write access. Can I modify etc/fstab to allow me these permissions every time I boot?

Thanks

---

### Post by skern03 on 2009-01-18
> **ffoeg said:**
> Although I had already tried chmod, it worked this time. I used:
 chmod  -R  777  /mnt/mount-point

Now I have read/write access. Can I modify etc/fstab to allow me these permissions every time I boot?

Thanks

I'm confused... where is this physically located? Are you dual-booting, and are you trying to access a windows folder on the windows installation on the same physical machine on which you have Ubuntu installed? 

If so, you don't need to chmod. Here's what my smb.conf looks like for my windows installation documents\all users\my music folder:
```
[StevesMusic]
	comment = Steve's Music
	path = /media/Beast_drv/Documents and Settings/All Users/Documents/My Music
	writeable = yes
;	browseable = yes
	guest ok = yes
```

The "writeable = yes" takes care of read/write access. This is why you don't need chmod.

And if you're having trouble mounting the windows partition permanently, here's a link that describes how you do it:

[http://ubuntuforums.org/showthread.php?t=836061](http://ubuntuforums.org/showthread.php?t=836061)

---

### Post by ffoeg on 2009-01-18
Hi Skern,

The Windows share is on a different computer that's part of my local network.

---

### Post by skern03 on 2009-01-18
> **ffoeg said:**
> Hi Skern,

The Windows share is on a different computer that's part of my local network.

Ah... The reason chmod didn't work permanently is that the Windows box is controlling permissions, not Ubuntu. The read/write permissions need to be set on the Windows machine. From the Windows box, right-click on the folder, and select the Sharing tab (which you've probably already done). Make sure the settings permit the user logged into the Ubuntu machine the appropriate access rights. I usually do this on the Shared Folders for the machine only.

Are you running any sort of firewall software, like Symantec (Norton)? It gets pretty crabby about access. That MAY be part of your problem.

Sounds like you also want to set up this shared object similar to a permanently mapped drive in Windows.

Try this:
1) open Networks, in the file browser, then navigate to the machine and to the shared folder. Right-click the folder, and click Mount Volume. It will appear in your Places list.

2) As mentioned before, you can bookmark the folder from the menu. It appears in the File Browser, underneath the places listings.

I'm going to log out, and back in to make sure these settings are "sticky." 

BRB...

---

### Post by skern03 on 2009-01-18
> **skern03 said:**
> 

Try this:
1) ...Right-click the folder, and click Mount Volume. It will appear in your Places list.

2) ...bookmark the folder...


Results: bookmarking the folder is permanent, so I suggest using this technique. 

Can you edit files via the Networks link? You said earlier that you had the permissions set up correctly. This is how I edit windows shares from a machine running Ubuntu. Works fine for me - no need to mount, no need for chmod or anything.

---

### Post by dmizer on 2009-01-18
Have a look at the second link in my sig which includes troubleshooting tips for permissions problems. Also, I highly suggest that you mount with fstab rather than manually via mount command, as the latter can often cause permissions problems.

---

### Post by ffoeg on 2009-01-18
Hi Skern,

Thank you for your info. But I'm sure it's not a Windows security settings issue. If it was CHMOD would never help. I'm leaning towards the advise of dmizer, of using fstab instead. I do have to learn more about that. So I'm going to read up on the details.
I'll let you know what happens.
I thank you both.

---

### Post by theozzlives on 2009-01-18
maybe your Windows end isn't setup right

---

### Post by ffoeg on 2009-01-18
Hi theozzlives. If the Windows machine was the problem, then how can it be possible that I can manually run the mount command? That worked a long time ago. I just had to tweak the mounted drive permissions within Ubuntu.

At this point, I'm trying to enter the mount request in the fstab file.

Can anyone see what I'm doing wrong? I tried using cifs as the file type, but that wasn't working. I got a " wrong fs type, bad option, bad superblock on //192.168..." error. I changed it to ntfs-3g, and the error switched to " Failed to access volume".

The entry in fstab is:
//192.168.xxx.xxx/qb$	/mnt/qb	ntfs-3g	user,auto,credentials=/home/user/credentials,exec,rw	0	0

Also, since this is being entered on a laptop, that's wirelessly connected to the network, I'm not sure how fstab can be used if it's not connected to the network until after bootup finishes. To test the syntax, I enter: sudo mount -a 

Thank you

---

### Post by dmizer on 2009-01-19
> **ffoeg said:**
> Hi theozzlives. If the Windows machine was the problem, then how can it be possible that I can manually run the mount command? That worked a long time ago. I just had to tweak the mounted drive permissions within Ubuntu.

At this point, I'm trying to enter the mount request in the fstab file.

Can anyone see what I'm doing wrong? I tried using cifs as the file type, but that wasn't working. I got a " wrong fs type, bad option, bad superblock on //192.168..." error. I changed it to ntfs-3g, and the error switched to " Failed to access volume".

The entry in fstab is:
//192.168.xxx.xxx/qb$	/mnt/qb	ntfs-3g	user,auto,credentials=/home/user/credentials,exec,rw	0	0

Also, since this is being entered on a laptop, that's wirelessly connected to the network, I'm not sure how fstab can be used if it's not connected to the network until after bootup finishes. To test the syntax, I enter: sudo mount -a 

Thank you
Wait ...

In your first post you indicated CIFS, why are you using NTFS now? ntfs-3g is for mounting an NTFS drive that's physically attached to the same computer as Ubuntu.

If you have two computers (one Windows, and one Ubuntu), you will need to use CIFS to mount the Windows computer's shared folders. Please follow the second link in my sig for mounting Windows shares in Ubuntu.

---

### Post by ffoeg on 2009-01-19
DMizer, you rock! Thank you for being so patient with me. I have years and years of experience as a Windows admin. I still have so much to learn about Linux, and I have to remember to not overlook the fine details.
In regard to this work being done on a laptop, that doesn't connect to the wireless network until after bootup, will that prevent this entry in /etc/fstab from working? If so, is there a work around?

Thanks

---

### Post by dmizer on 2009-01-19
> **ffoeg said:**
> In regard to this work being done on a laptop, that doesn't connect to the wireless network until after bootup, will that prevent this entry in /etc/fstab from working? If so, is there a work around?
There will be a tiny message during boot that says it couldn't find the server, but it will not prevent /etc/fstab from working properly. The mounted drive will become available automatically once you connect to your wireless network.

I have several lines in my fstab. Some are configured to connect to my servers at home, and some are configured to connect to my servers at work. I don't use a different fstab for work and home.

---

