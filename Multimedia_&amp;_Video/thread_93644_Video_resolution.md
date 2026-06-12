---
title: "Video resolution"
date: 2005-11-22
forum: Multimedia &amp; Video
---

### Post by jmurr on 2005-11-22
Please excuse me if this question is really stupid but I am very new to Linux.  I have installed Ubunto 5.04 on my system with a Stealth II s220 v1.36 video card from Diamond Multimedia.  The trouble is I cannot change the screen resolution from 640x480 to any other resolution.  Do I need new drivers?  Is this a setting I need to change?  I searched the forums and could only find one post by Mbutterman “How to for installing new graphics card”
Any help would be appreciated.
Jim

---

### Post by jeffjanzen on 2005-11-22
[System menu > preferences >screen resolution] is where resolution settings are supposed to be.  have you tried that?

---

### Post by MButterman on 2005-12-20
Hi jmurr,

I am the person that requested the graphic card how to. The information I gather from different sources is that the Diamond Stealth is the S3/Savage line of video cards. While Breezy is supposed to support this card, there has been alot of technical issues with it, including not being able to change resolution. The problem has been solved for the next release of Ubuntu (Dapper Drake) that is scheduled for April. That isn't going to help you now though. I would replace the card with either an Nvidia or ATI based card (PCI or AGP).There is one temporary solution for you but the card won't operate in an excellerated mode. I'll list the steps here.

This is under the assumption the Stealth is installed and I highlighting parts in [COLOR="Red"]red[/COLOR] to indicate either commands used or make reference to key words to look for.

1 Goto Applications/ Accessories/ Terminal and select it with a left mouse click.

2.In the terminal window, type the following:
"[COLOR="Red"]sudo gedit /etc/X11/xorg.conf[/COLOR]" minus the quotation marks. press enter.

3.sudo requires your password, enter it at the "[COLOR="Red"]Password[/COLOR]" prompt and press enter.

4. A new window will open displaying the contents of /etc/X11/xorg.conf. Scroll down to the "[COLOR="Red"]Section "Device"[/COLOR]" and locate the "Driver" entry. If you have this card installed it should say something like "[COLOR="Red"]S3Savage[/COLOR]" remove this part of the entry and replace it with the word [COLOR="Red"]"vesa"[/COLOR]. Keep the quotation marks on this one. Select save, close the window and restart. 

This will allow you have the higher resolutions but, you will have no excelleration and the only thing that it seems to affect is playing games. While this is my set of instructions, there are more complete ones written by more experienced users. Make sure you cross referance these with other suggestions before you undertake it. It could cause issues if done improperly.

Hope This Helps and Good Luck.

MButterman

---

### Post by frodon on 2005-12-20
Jmurr, could you post your xorg.conf file and tell us the full name of your monitor ? : ```
sudo gedit /etc/X11/xorg.conf
```Your problem should be solved by putting in your xorg.conf the good horizontal and vertical refresh rates corresponding to your screen specification.

---

