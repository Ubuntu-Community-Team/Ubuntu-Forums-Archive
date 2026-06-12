---
title: "Basic file access between Ubuntu boxes"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by jcoles on 2009-05-19
Is there a good FAQ somewhere about simple file browse/copy network access between Ubuntu boxes? I'm baffled. 

There is a Places menu, but I can never connect to anything! Places > Network shows network:/// in the Location bar, but if I add an IP address, the response is always that the location cannot be found. The same thing happens with Places > Computer and its computer:/// prefix. How are these menu items supposed to work?

SSH (command-line or using gFTP) works for connecting to some Linux machines at work. But my home machines always reject the connection. In both Hardy and Jaunty, there is nowhere in the Gnome Administration or Preferences menus to enable SSH access or file sharing. 

How is this done? All I should need to know is the IP address and user credentials of the other machine.

Thanks.

---

### Post by lisati on 2009-05-19
I use samba shares on my home network, partly because it's the first option I looked into, partly because I sometimes run Windows on one or two of my machines, and partly because I haven't looked too closely at ssh yet (perhaps I should!)

Have a look here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by Iowan on 2009-05-19
[Here]("https://help.ubuntu.com/8.10/internet/C/networking-shares.html") is one... seems to be Samba. I presume you've seen these on [SSH]("https://help.ubuntu.com/community/SSHHowto"), [SSHFS]("https://help.ubuntu.com/community/SSHFS"), and [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo").
I also tend to use Samba because of Windows machines on my network.

---

### Post by jcoles on 2009-05-19
Hi Lisati,

I have played with SMB a little, with varying results. Too many times I found that correct passwords would be rejected. I never really understood the configuration file well enough to know what I was doing. It's great that you got it working.

After posting, I kept searching and found another thread, [http://ubuntuforums.org/showthread.php?t=1014509]("http://ubuntuforums.org/showthread.php?t=1014509"), where lwsb advises using openssh-server. 

"install openssh-server on the system with the desired files (or on all systems). Then from other systems you can access the files by Main Menu/Places/Connect to Server, select SSH as server type, fill in host name or ip address of the target system & click Connect. You will be prompted for a user name & password and will then get a file browser window opened as if you were a user logged in on the target system."

It worked for me.

---

