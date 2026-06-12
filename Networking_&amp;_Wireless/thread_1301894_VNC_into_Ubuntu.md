---
title: "VNC into Ubuntu"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by Mandrew on 2009-10-26
I am sort of a Linux noob.

I would like to VNC into ubuntu from my crappy old laptop running Puppy Linux. Does anyone know how I would do this? Am I even posting in the right forum? If not, I'm sorry. Thanks for your help.

---

### Post by linorics on 2009-10-26
Well there are tons a ways to do this. But the most simple is to use ubuntu built-in vnc server. 

First login to the computer you want to view(the Server)

open the terminal ans type ifconfig and copy down the ipadress. It should look like 192.168.x.x or 10.0.x.x. 

Go under System > Preferences > "Remote Desktop" 

Click on Allow other users to to control your desktop
Require users to enter a password (type in a password)

then on the "crappy computer" download a vnc client.

Ubuntu: sudo apt-get install xtightvncviewer

Windows: google tightvnc viewer

type in your Ip you wrote down earlier, enter password and tada!

---

### Post by Mandrew on 2009-10-26
Thank you very much! This worked wonderfully.

But... my Ubuntu computer uses a 19" monitor and the "crappy computer" uses a 12". So, to view my Ubuntu screen, I have to constantly scroll around. Is there a way to view my the entire screen over VNC on the smaller monitor? I am using tight VNC viewer.

---

### Post by linorics on 2009-10-27
Basically what your wanting is called scaling. So if your client PC is 

Ubuntu: you can use Aplications>Internet>"Remote Desktop Viewer". when you connect to a pc you can enable scaling.

Windows: I don't remember exactly if tightvnc viewer has scaling or not but I know UltraVNC viewer does. 

I can give you more details if you want. So just let me know.

---

