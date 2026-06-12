---
title: "&quot;Failed to Mount Windows Share&quot; from USB Hard Drive"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by mikethehard on 2009-02-01
Hi, firstly I have performed the upgrade in [post #81 of this thread marked solved]("http://ubuntuforums.org/showthread.php?t=964564&highlight=failed+mount+windows+share") but I'm still having trouble. It seems that some others are still too having difficulty despite that solved status. 

I am trying to share music across my home wireless network (2 computers running Ubuntu 8.10  and a Windows XP machine) from a USB HD which is split into 4 Fat32 partitions.

The rest of my shares from the seperate computer's main hard drives are all working fine. As soon as I try to open any of the shared folders or partitions on the USB drive via the Network I get the message "Unable to mount location, failed to mount window share".

This problem is the same if the USB drive is connected to either the Ubuntu machines or the XP machine. (note that XP reports that it "cannot map the network drive" when i try to open the drive across the network when the USB HD is connected to an Ubuntu computer).

Any ideas?

---

### Post by mikethehard on 2009-02-01
additional information:

in Smb4K an attempt to mount a drive on the USB connection reports

Mount error 12=cannot allocate memory

---

### Post by dmatthys on 2009-02-01
bump 

same issue and it used to work up untill about a week ago except i get it both in ubuntu and windows and the drive is connected to a ubuntu computer 

im not exactly sure why it wont share with another ubuntu computer but it wont share with my wifes laptop either which is xp

---

### Post by mikethehard on 2009-02-01
yes, it should also be noted that when the HD is connected to Ubuntu machine X  via USB I can open the folders with no problem by navigating direct from the Places menu to the drive's volumes, or from the desktop.

However, on the same computer if i navigate through Places>Network>Windows Network>Workgroup>Ubuntu Machine X>USB drive volume
I get the mount failure error.

---

### Post by dmatthys on 2009-02-01
confirmed did the same thing for me have yet to find anything to correct the issue though

---

### Post by mikethehard on 2009-02-02
bump. 

No ideas at all on this??

---

### Post by dmatthys on 2009-02-02
>still nothing hopefully someone gets some ideas it worked just fine in 8.04 and for a >while after i upgraded it just recently stopped i have almost a hundred gigs of media that >my wife cant access unless im not on my computer when she wants to shes going crazy which >in turn is driving me nuts lol

ok i think i might have found a workaround by edditing /etc/fstab add an entry that looks like the entry below the values will probably be different as the drive names i highly doubt are the same but this will at least give a general idea and this automounts my drive on boot with me as the owner not root

```
/dev/sdd1       /media/HOMENET  vfat    rw,nouser,auto,exec,utf8,umask=0000,uid=1000,gid=1000 0       0
```

anyway hope this helps you one more thing the part with the umask=0000,uid=1000,gid=1000 was the part that i added to get that to show up

---

### Post by mikethehard on 2009-02-03
lol, my situation is the same.... girlfriend wants access to the drive so she can play music on her XP machine too.

Does the above solution work then?

Do you think you could talk me through how to find the right values and add that line in to the start up? I'm pretty new to Ubuntu still and a little walk through would be awesome if you have time.

---

### Post by dmatthys on 2009-02-04
actually i dont know how to find the values lol i copied and pasted that and just changed the drive path and mount points i listed some examples of what i know below for you im still kind of a noob too but this worked for me if it doesnt let me know ill be more than happy to try and be more helpful untill you get it straightened out i spend alot of time on the computer becuase i am in school online although i dont check the forums all the time so dont be to alarmed if i dont respond right away i will anyway hopefully the below info will be helpful the sooner the better lol

ex. /dev/sdc1 if you have two drives the first one is sda and the second with be sdb although it could be hda and hdb the number is the partition number if you have two drives split in two partitions each ex. would be /dev/sda1 /dev/sda2 /dev/sdb1 /dev/sdb2

sudo fdisk -l 

thats an L probably knew that but i see alot of confusion with people typing i instead it does have to be lowercase though

the above command will give you the /dev path

the /media/HOMENET in my example is the mount point associated with the drive path this value is whatever you set up as the mount point 

the vfat part is the type of file system the drive uses if its a fat32 fat 16 ntfs whatever it is mine actually are all set to auto now and work so dont worry about that try auto first

the rest i copied and pasted from an fstab file i found posted somewhere i would give you the adress except i dont remember what it was but you should be able to do the same from my previous post or actually i will post a new one in a second

---

### Post by dmatthys on 2009-02-04
```
<your drive path here>       <your mount point here>  auto    rw,nouser,auto,exec,utf8,umask=0000,uid=1000,gid=1000 0       0

```

just replace the stuff inside the < > with the appropriate info inside your /etc/fstab file

also you might find this helpful i found a few minutes ago explains how to mount a drive and explains the fstab file

[http://ubuntuforums.org/showthread.php?t=283131&highlight=creating+mount+point](http://ubuntuforums.org/showthread.php?t=283131&highlight=creating+mount+point)

---

### Post by posterlion on 2009-02-04
I've been going through this problem for the last week myself.  I've read many of the posts on this forum and have not found any post that addresses the problem directly.

Many posts recommend changing samba settings.  Samba is used to present Linux shares to Windows not the other way around.  Other posts recommend turning off password protection, but this is not a solution, it is merely a work-around.

Ubuntu should be able to recognize a Windows share immediately after it has been installed with zero modifications.  

I've done quite a bit of research and have determined that this problem was introduced in version 8.04 and has carried through into 8.10 as well, but not in exactly the same way.

I would like to point out that this problem is not specific to USB shares.  It is a problem with all WINDOWS shares.  In my test lab I am using work group networks, not domains.  I have four machines involved in my testing:

poster0 - 	Windows XP Professional
poster1 - 	Windows Vista Home Premium
poster2 -	 Ubuntu 7.10, 8.04, and 8.10
Barb -		Windows XP Home.

The network is a wireless access point using DHCP. 		

Ubuntu 7.10 works perfectly with XP and Vista.  If the share is a public share (USB or otherwise) you can get to it.  If the share is password protected, then Ubuntu prompts the user user for credentials.  If the credentials can be authenticated the share will be presented.

Ubuntu 8.04 will prompt for a password on a public XP share (which is an invalid response).  The credentials are not authenticated (at least I don't think so) because if the user simply hits the cancel button at the credentials prompt, the share will be displayed.  Windows Vista shares cannot be displayed period.

Ubuntu 8.10 fixes the invalid credentials prompt for XP shares and XP shares are displayed, but Vista shares (public or protected) can not be displayed.

Therefore, I conclude there is indeed a bug in the Ubuntu code.  My apologies in advance to the Ubuntu team if I am proven incorrect on this issue.

poster . . .

---

### Post by posterlion on 2009-02-04
I found a way to connect to my Vista shares, although it is not ideal.  I think I am on the right track to resoving this issue.

After you select NETWORK from PLACES, click on the button that has an illustration of a paper and pencil (toggle between button and text-based location bar).

Then you can type in the path to your share.  Mine is smb://poster1/public

I pressed enter after typing in the path and I was presented with a credentials box.  Knowing that the share was public I decided to click cancel and then the share was presented.

I did this test with 8.04 which as I already reported, should not display a credentials box for a public share.

Give this a try and report back on your results.

I am investigating another avenue that may resolve this issue.

poster . . .

---

### Post by posterlion on 2009-02-04
Apologies to the samba guys as well.  There is one valid reason that I have found for editing the /etc/samba/smb.conf file.

The default workgroup parameter in Ubuntu 7.10 is MSHOME.  However, beginning with Ubuntu 8.04 the default value changed from MSHOME to WORKGROUP.  I assume this change was made because the default value in Windows Vista was changed from the XP default of MSHOME to WORKGROUP.

I changed my smb.conf file from WORKGROUP to MSHOME which is my networks workgroup name.

After restarting, the credentials box displays MSHOME instead of WORKGROUP when I connect to my Vista shares.

To edit this file you must open a terminal window from APPLICATIONS => ACCESSORIES => TERMINAL

once inside the terminal window type:

sudo gedit /etc/samba/smb.conf

Change the workgroup parameter to the workgroup of your network.  For example, my workgroup is MSHOME so I changed my smb.conf file to look like:

workgroup = MSHOME

Don't forget to save your changes then either reboot your machine or recycle your samba service.  Afterwards, any time a credentials box is displayed the workgroup field will contain the workgroup of your network.

I have decided to investigate the remaining smb.conf entries to see if the resolution for this problem can indeed be solved with additional changes to this file.

poster out . . .

---

### Post by mikethehard on 2009-02-06
Cheers for all your help guys. Finally got this working properly.


I formatted the external HD into one ext3 partition and put all the media back on. 


Then I changed ownership of the drive from root to my login name, as suggested by dmatthys - this seems to be the key.

I used slightly different input. method = login name..

> sudo chown -R method:method /media/sdb1
ls -la /media

(note that /media/sdb1 may vary depending on the drive's mount location - I found it by right clicking>properties>volume

Now the external hard drive shares fine when it's connected to the main Ubuntu machine across all Windows & Linux computers! It has been an interesting learning curve.  Thanks to both you guys.

---

### Post by retsin2000 on 2009-06-07
I had the same problem as the OP. I eventually realized that I coudn't connect to any of the shares on the USB drive (connected to an XP machine) through another XP machine either. These shares used to work. Then I came across this:

[http://www.tmsnetwork.org/blog/windows-share-error-not-enough-server-storage-available-process-command](http://www.tmsnetwork.org/blog/windows-share-error-not-enough-server-storage-available-process-command)

This solved my problem. Good luck.

---

