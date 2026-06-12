---
title: "How to Share/Mount Hardrives over a Local Area Network?"
date: 2011-03-19
forum: Networking &amp; Wireless
---

### Post by christosophia on 2011-03-19
Greetings,
I have a computer, the one I am on now, with Ubuntu 10.10, it should be completely updated... and I can network with other computers, I can access Windows XP and 7 shared locations on other computers, and I can also get Ubuntu on other computers to access this computer's shared files.
What I can't do, however, is share my hardrives that are on this computer, I have tried sharing them in /media/ and etc, but it is not working, apparently you have to mount them in some mystical way.
Another problem is getting Windows machines to access Ubuntu computers on the network - which I believe is a Windows problem, so I can figure that out some other time, but importantly, I want to be able to share my hardrives over the network.
If someone can give me some instructions to mounting and sharing hardrives(internal), and even my DVD-Drives, and portable USB devices, would also be fantastic - since, in Windows you can just right click, "share", and it's done.. It is a very useful thing to have, and I don't want to use Windows on this computer anymore, but I have no choice, really, if I can't share my storage to the other computers.

Cheerio!

---

### Post by mikewhatever on 2011-03-19
Portable USB devices should automount, as for internal hard drives, it's slightly more complicated. Could you post the output of 
**sudo fdisk -l** 
from a terminal window. That should show what file systems you have to deal with.

---

### Post by garvinrick4 on 2011-03-19
Install samba
```
sudo apt-get install samba 
```Open Samba and make shares.
Just browse and add:

---

### Post by garvinrick4 on 2011-03-19
In windows 7 you have to delete Windows live essentials from your machine not Windows Live but Windows Live essentials and will work. Was in other threads earlier and this stopped linux box's from repeating asking for password. (worked for me) Windows workgroup (ubuntu to Windows 7)

---

### Post by Morbius1 on 2011-03-19
> If someone can give me some instructions to mounting and sharing  hardrives(internal), and even my DVD-Drives, and portable USB devices,  would also be fantastic - [COLOR=Blue]since, in Windows you can just right click,  "share", and it's done.[/COLOR]Oddly enough in Ubuntu it's done exactly the same way:
Open Nautilus
Right click on a folder you own ( or open nautilus as gksu and select anything)
Select "Sharing Options"
[COLOR=Blue]* It will prompt for a Samba install if it's not there.*[/COLOR]
Select all three boxes
Select "Create Share"
It will ask you if you want it to modify permissions - you do.
You just created a samba guest share.

But:
> I can also get Ubuntu on other computers to access this computer's shared files.It sounds like you already have sharing working.

When you say the share of these other "drives" are not working do you mean you created the share and it won't allow access. Or the share is not visible.

Why not post the output of the following commands so we can see how your samba shares are set up:
```
net usershare info --long
``````
testparm -s
```

---

