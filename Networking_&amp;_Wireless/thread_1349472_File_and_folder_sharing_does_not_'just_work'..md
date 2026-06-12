---
title: "File and folder sharing does not 'just work'."
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by mutex023 on 2009-12-08
Please please is there a GUI only way of making file and folder sharing just work. as of now i cant get it to work between ubuntu machines, forget getting it to work between ubuntu and windows.

I am using ubuntu 9.10, latest samba installed.
When i try to access the shared folder from another ubuntu machine, it takes a long long time and finally pops out some error message like - "unable to retrieve <some> list".

I've searched around , but everywhere i find that you need to edit the damned config file. Surely there is a gui only way?
As far as I can make out this problem has been around from 2005, 4 years have passed and still no fix ? Long way to go for ubuntu to catch up with windoze. Really frustrating problem, especially since this is a very important feature a modern OS must have.

---

### Post by DJonsson2008 on 2009-12-08
I hear you filesharing should be point and click but
its can be as knarly in windows expecially between NT,
W2K and Vista on the same peer to peer as it can be
with Linux. 

For starters what I found works with both windows
and ubuntu/linux

Logon with same username and same password 
on both machines.

Perhaps try staring with a folder on your 
desktop to be shared, and apply liberal
rights to it. 

Using Konqueror gave me considerable leverage 
in resolving this sort of issue. 

Mountconfig is another tool that has helped, especially
when local NTFS HDs are or partitions are connected.

mountconfig and konqueror can be easily found in
the synaptics installer. 

Most of all start simple, leverage with Konqueror, and
mountconfig while not fully GUI but do give more GUI 
support, use a desktop folder to get started and use 
the same username/password combination on the first 2
machines you link together.  

Validating that can be done -- branch out.

---

### Post by DJonsson2008 on 2009-12-08
While it may not be GUI, PRINTING this URL out below 
onto paper, carefully READING it and then taking 
its instructions/suggestions STEP by STEP was a
breakthrough in getting my Samba to communicate 
robustly to XP.

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch12_:_Samba_Security_and_Troubleshooting](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch12_:_Samba_Security_and_Troubleshooting)

---

### Post by mutex023 on 2009-12-08
Much appreciate your help, but does this mean that as of now there is no GUI or wizards that make changes to the smb.conf file?

---

### Post by carniola on 2009-12-08
**mutex**, I feel your pain. I've been struggling to get folder sharing working between two ubuntu machines; so far without any success whatsoever. It doesn't help that most guides seem to be about sharing between ubuntu/XP and are wicked complicated.

I certainly would love to see the process simplified. Sorry I can't offer anything other than moral support...

Best of luck.

---

### Post by Iowan on 2009-12-08
> **mutex023 said:**
> Much appreciate your help, but does this mean that as of now there is no GUI or wizards that make changes to the smb.conf file?
There's SWAT, ebox and a couple of new-to-me options: system-config-samba and a module called gadmin-samba. More discussion near the end of [this]("http://ubuntuforums.org/showthread.php?t=763445") thread.

[Here]("https://help.ubuntu.com/community/SettingUpSamba#Graphical%20Configuration") is another one that might be helpful.

---

### Post by mutex023 on 2009-12-08
> **Iowan said:**
> There's SWAT, ebox and a couple of new-to-me options: system-config-samba and a module called gadmin-samba. 



Thanks, I installed both system-config-samba and gadmin-samba, the latter seems to be more comprehensive, will try it out and let you know if it works.

---

### Post by sgosnell on 2009-12-09
All I've ever had to do is install samba on all the Linux boxes, then use Nautilus go show the folders I want to share, then right-click on each, select Properties, go the the Share tab and set things up how I want, and that's it.  You have to do this on each machine that you want to have shared directories.  It's the same process as in Windows.

---

### Post by mutex023 on 2009-12-09
dude, i did that, it doesnt work , in places->network, i see the names of the other machines, but double clicking any of them only gives an error msg like -'unable to mount location' or 'failed to retrieve list'.

And I also tried configuring shared folders using 'gadmin-samba' , but no luck, now places->network only shows 'Windows Network' and opening that throws up an error msg.

Guess I will now try with system-config-samba

---

### Post by frankhdz on 2009-12-18
sigh ... I am about to give up on Ubuntu, this is the one thing that I must say is a hell of a lot easier in windows. Like you I cannot get file sharing between multiple machines to work. I have followed every tutorial I can find and the only thing I am able to do is simply see the folder names but not able to access the contents of the shared folders, I also get the "Unable to mount" message. On the windows box I get access denied messages. I may have to go back to windows, I have a home office and need to work and I have spent 2 days now trying to solve this problem and I simply have not found a solution. As much as I like Ubuntu I need something that just works.

---

### Post by mutex023 on 2009-12-18
Ok, I found a workaround, DO NOT USE SAMBA !
Instead use ftp, install pure-ftpd from package manager.
You can then access the files from another machine in nautilus by typing-
ftp://<IP addr> in the address bar.
But make sure you use your username and pwd to login, anonymous login does not seem to work for me.
Hope this helps others who faced the same problem with samba.

---

