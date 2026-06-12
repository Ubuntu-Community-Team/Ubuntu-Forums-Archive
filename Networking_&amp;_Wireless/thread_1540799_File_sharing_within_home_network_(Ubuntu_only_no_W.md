---
title: "File sharing within home network (Ubuntu only no Windows/OSX)"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by PendragonUK on 2010-07-28
For the first time networking my home computers I'm not interested in getting Ubuntu boxes to to talk to Windows and we now have Ubuntu on all machines.

I'm trying to use the "Personal Files Sharing Preferences" but there is a message telling me I require some packages. Most unlike Ubuntu but it doesn't tell me what packages I do need.

[[IMG]http://a.imageshack.us/img237/7669/screenshotpersonalfiles.png[/IMG]]("http://img237.imageshack.us/i/screenshotpersonalfiles.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

What I would really like to do is have access to sertain directory's on other computers and have full access to read/write within the home directory.

---

### Post by Morbius1 on 2010-07-28
"Personal File Sharing" uses a baby apache server and broadcasts it's share using avahi. SO you need to install the following packages:
> Apache2.2.bin
libapache2-mod-dnssdBTW, you will have no control over what is shared. By default only one directory is shared: /home/your_user_name/Public

---

### Post by PendragonUK on 2010-07-28
I'll give your suggestion a go, although I don't think it's the solution I'm after.

I sort of had a few points to make with my post. Firstly that answer to the question. Also the bit about the dialogue box, telling me something was missing but not what or how to fix it, most un-Ubuntu like.

Not to mention how come ubuntu doesn't talk to other ubuntu computers on the same network. Well not out of the box...

---

### Post by endotherm on 2010-07-28
I rather recomend samba over the personal filesharing, but the drop-dead easiest to get remote file access working in 2 mintes, is to install openssh-server from the repos. then on the client machine, open nautilus, hit Ctrl + L to enter location mode, and enter:
```
ssh://<serverbox>
or 

ssh://username@serverbox
```

this will open a nautilus window to the remote machines / partition.

---

### Post by Morbius1 on 2010-07-28
> **PendragonUK said:**
> I sort of had a few points to make with my post. Firstly that answer to the question. Also the bit about the dialogue box, telling me something was missing but not what or how to fix it, most un-Ubuntu like.

Yep, you're right. I've played with it a bit and my very personal feeling is that it was shipped disabled because it doesn't work very well. With Linux - Linux a share will appear on the client and then disappear. On Windows - Linux it doesn't seem to work at all even after one installs avahi ( on windows it's called bonjour ). I think the only reason it's there is because it's part of a package that also contains the Bluetooth parts.

>  Not to mention how come ubuntu doesn't talk to other ubuntu computers on the same network. Well not out of the box...     It sort of kind of does but you have to use samba - and one particular method of samba called usershares or Nautilus-shares. 

Open your home folder and right click on say ... Documents
Select "Sharing Options"

[COLOR=Blue]*Unlike Personal File Sharing, if you don't have Samba installed it will ask you if you want to install it.*[/COLOR]

Select "Share this folder", "Allow others to create and delete..." and "Guest access"
Select "Create Share"
It will ask you if you want it to modify permissions - you do

You just created a samba public share.

Just remember this is samba. For 70% of the users who use it and have [COLOR=Blue]resisted the temptation [/COLOR]to use the 5 million howto's out there that describe how it should be done, it works out of the box.

For the remaining 30% it's a living hell.

---

### Post by drdos2006 on 2010-07-28
Maybe this HOWTO will offer some alternatives.
[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)

regards

---

### Post by PendragonUK on 2010-07-29
Thanks for everyone's help, what got me going on this is I have ftp accsess to a remote server. Ubuntu does this so seamlessly, the server appears as a location in places. Nautilus handles files just like they were on my own computer. I was hoping to be able to do this with the three computers in my home network. To discover that it wasn't as strait forward was more than a little surprising. I had hoped to avoid Samba as I too have had my issues with it when I had a mixed network. Now every computer is running Ubuntu I had thought it might be easer...

---

