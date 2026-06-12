---
title: "Home Network printer problem"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by NozSpark on 2009-08-15
Hi,, Noob with a question here...

I have just installed Ubuntu 9.03 (32bit) on my Acer Aspire 3680 laptop; I have got it working as a dual boot system.

It boots up perfecty and logs into my wireless router straight away

I did have a problem with my home network, but I have sorted that now.. it was the firewall!

The problem that I now have is that my laptop cannot find the printer that is attached to my desktop (windows XP) it's a Cannon Pixma MP460 (I understand that it will work with the MP160 driver) connected by USB. When I boot my laptop into Vista I have no problem with Networking or printer sharing..

When I try and install (find) the printer there is no smb printer option in the find network printers bit..

I have installed Samba and Samba4 & disabled the firewall, apart from that I am a complete Noob when it come to Linux.

Hope someone can help me!! TIA

---

### Post by SoftwareExplorer on 2009-08-16
When you are at the select device page, expand Nework Printer and Click windows printer via SAMBA.
Or are you saying you used to be able to find it but now it disappeared?

---

### Post by SoftwareExplorer on 2009-08-16
Welcome to the ubuntu forums by the way.

---

### Post by NozSpark on 2009-08-16
Thanks for the welcome..

Please bear with me, I am a complete noob to Linux,, but I am liking it alot.

When I go into System, Administration, Printer, New, Network printer.. there is no longer a selection that says "Windows printer via SAMBA" ... it was there before when I couldn't access my home network, but since I have sorted that it has now dissapeared.

Update..

I have just tried to access my desktop PC through the network and it says "unable to mount location", however when I access through my browser "smb://192.168.x.x" I can see the files no problem...

---

### Post by NozSpark on 2009-08-17
For some reason I can now access my desktop again...:confused:

And if I try and edit my* samba/smb.conf file*, it says that I don't have permission to change the file when I come to save the changes..

Can anyone help with this?????

---

### Post by SoftwareExplorer on 2009-08-17
> **NozSpark said:**
> For some reason I can now access my desktop again...:confused:

And if I try and edit my* samba/smb.conf file*, it says that I don't have permission to change the file when I come to save the changes..

Can anyone help with this?????
To change that file you have to run as root user. So do something like this ```
gksudo gedit
``` then open it and make your changes and then save.

---

### Post by NozSpark on 2009-08-17
Got that, cheers...

You mean

gksudo gedit /etc/samba/smb.conf ???

Did that and it gave me permission to save it..

Got the printer working in the end,,
In add/remove programs I added the printer configuration & printing programs... once added it found the printer straight away, I then installed the driver for the MP160 (mine is the MP460) and managed to print a test page straight away..:P:P

Thanks for the help everyone.... I'm sure that I'll have more questions...(infact I can think of a couple right now, but I'll have a search through the forum first)

---

### Post by SoftwareExplorer on 2009-08-17
> **NozSpark said:**
> Got that, cheers...

You mean

gksudo gedit /etc/samba/smb.conf ???

Did that and it gave me permission to save it..

Got the printer working in the end,,
In add/remove programs I added the printer configuration & printing programs... once added it found the printer straight away, I then installed the driver for the MP160 (mine is the MP460) and managed to print a test page straight away..:P:P

Thanks for the help everyone.... I'm sure that I'll have more questions...(infact I can think of a couple right now, but I'll have a search through the forum first)
Your welcome. Sometimes for me, gedit opens a blank file when I do what you said, so that's why I told you that way. Doesn't matter however if it worked!

---

