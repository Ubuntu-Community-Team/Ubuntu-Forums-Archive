---
title: "Computer missing on my network.Help"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by taito on 2009-12-14
Hi all... I'm a newbie in Linux... so sorry if I'll say 'amenities'... I installed Ubuntu 9.10 on both my pcs... desktop and laptop as well... I have a wireless router connected by cable to my desktop, which provides a wireless internet access to laptop. Everything works perfectly... laptop found immediately the network connection and had access to internet in a few seconds... I had to do nothing but swich my laptop on !!!

Then I tried to create a network between my 2 pcs... and I had some kind of success.... after a long struggle anyway!! Unfortunately... it still doesn't work... that's what I achieved so far: my two pcs see each other... if I go in the network folder (network:///) I find both them... I can go into them and see the shared folders... exactly as I  set them.

Here's comes the trouble... when I try to open one of the shared folders, it returns the error message " Unable to mount location, failed to mount windows share ". 

What did I do wrong??? Please help me or I'll get mad!!!

Thank you all very much (sorry for my bad english)

Taito

---

### Post by Iowan on 2009-12-14
> **taito said:**
> Please help me or I'll get mad!!!There's motivation... ;)
Sounds like machines have decided to use Samba for sharing. There are other options for sharing between Ubuntu machines - all involve a little work setting up the server side.
 [This]("http://ubuntuforums.org/showthread.php?t=1169149") How-To might help with the Windows sharing problems. [Here]("https://help.ubuntu.com/8.10/internet/C/networking-shares.html") is a different method. This was written for 8.10 - so I don't know if something has changed in Karmic.
Some options: [NFS]("http://ubuntuforums.org/showthread.php?t=249889"), [FTP]("http://ubuntuforums.org/showthread.php?t=249889"), [SSH]("https://help.ubuntu.com/community/SSH"), [SSHFS]("http://https://help.ubuntu.com/community/SSHFS").

---

### Post by taito on 2009-12-15
Hi Iowan.. thank you very much for your hints... I'll check them out at home... now I'm writing on a windows-based pc. I warmly hope they'll work!!! I'll tell you.
 
Bye and thx again

---

### Post by taito on 2009-12-27
Dear Iowan and Linux users all... I'm so proud to announce that, after a long and painful struggle... 5 minutes ago I've finally won my war on home-networking!!!

Thank to your suggestion too Iowan, I managed to connect my two ubuntu pcs in a network... but I'll tell you more... I succeeded in two ways.... via SSH and samba as well!! Gorgeous isn't it?? 
That's the HowTo which helped me so much with samba settings:

 [http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)

I hope what's  above could be useful to somebody!!

Bye and see you soon with the next trouble !!

Taito.

---

