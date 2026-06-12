---
title: "sharing troubles"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by Hagar55 on 2009-12-09
I have a desktop and a laptop, both have Karmic installed.
The desktop is a dual boot with XP, the laptop one with Vista.

When the desktop boots into XP I can acces the drives on the computer with my Ubuntu, print, do anything I want.

When I boot into Karmic on the desktop I cannot see the window drives nor the files wich I shared on my home.

Is there a way to see the drives on the desktop from my laptop on the desktop if both computers are running Ubuntu ?

---

### Post by Iowan on 2009-12-09
From Ubuntu to Ubuntu gives you more options than Ubuntu to Windows - including Samba, NFS, SSHFS, and FTP. Links available if you wish. If you want to keep Windows in the mix, Samba will be the primary option. [Here]("http://ubuntuforums.org/showthread.php?t=1169149") is a How-To that might help with some of the Windows sharing problems.

---

### Post by Hagar55 on 2009-12-13
Do I need to congigure samba or will it just work ?

---

### Post by Iowan on 2009-12-13
It'll need some configuration - mostly via */etc/samba/smb.conf*. [This]("http://ubuntuforums.org/showthread.php?t=202605") is a good starting point. [Here]("https://help.ubuntu.com/8.10/internet/C/networking-shares.html") is another method.

---

### Post by Hagar55 on 2009-12-13
Ok, let's be honest if Ubuntu wants to be a really mainstream option like windows this part is going to have to be A LOT MORE SIMPLE.....beginning with a GUI to configure the options.

---

### Post by deathbyswiftwind on 2009-12-13
There is a gui option if you would have looked in the repos you would have seen that. So dont blast something before you even look everytime I find a need for something Ive always found it in a repo. To see these gui options(yes surprise more than just 1) open up synaptics and search samba there are a few in there.

To make the whole thing work you need to only edit 1 line in the entire smb.conf file. All you need to do to get your windows to see the shared files is change the workgroup name from workgroup to MSHOME. Not so hard you can do it in the gui or by sudo gedit /etc/samba/smb.conf and manually change the one line. Pretty easy to do I just did it last night for the first time ever. Everything works great between my linux laptop my linux desktop my wifes windows desktop and my wifes windows/linux laptop.

---

### Post by Iowan on 2009-12-13
With **freedom** comes complexity. Yes, it would me much simpler if the OS decided what you want - then it could set things up for you.
[This]("http://ubuntuforums.org/showpost.php?p=8466082&postcount=6") post has some options for Samba configuration GUI's.

---

### Post by Hagar55 on 2009-12-14
This isn't about looking in the repo's to find something.
The documentation about networking in Ubuntu is scarse to say the least.
So it's hard to search for something if you don't know what you're looking for.

And I'm glad you got it to work right away, I haven't been so lucky, and admit it or not changing a config file and having to do it from Terminal isn't a small obstacle for most people.

---

