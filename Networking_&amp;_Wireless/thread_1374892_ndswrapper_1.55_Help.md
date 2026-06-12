---
title: "ndswrapper 1.55 Help"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by Timbot2000 on 2010-01-07
OK Downloaded NDSwrapper from sourceforge, now and unpacked it onto my desktop. 


Now the questions begin. 

Where is the executable? I see nothing but flat files!
Also, until I can get my CDROM off of /root, or find out how to log on as /root, I cannot install the windows drivers from the CD anyway!

Please help

---

### Post by bkratz on 2010-01-07
> **Timbot2000 said:**
> OK Downloaded NDSwrapper from sourceforge, now and unpacked it onto my desktop. 


Now the questions begin. 

Where is the executable? I see nothing but flat files!
Also, until I can get my CDROM off of /root, or find out how to log on as /root, I cannot install the windows drivers from the CD anyway!

Please help

You are kind of doing it the hard way. If you have a wired connection available you could simply go to System>>Administration>Synaptic and search for and download ndisgtk this will also tick and download the two ndis...files.
Ndisgtk is a gui that appears in System>>Administration>Windows wireless Drivers which makes the use of ndiswrapper really easy. It is pretty straightforward.

---

### Post by Timbot2000 on 2010-01-07
> **bkratz said:**
> You are kind of doing it the hard way. If you have a wired connection available you could simply go to System>>Administration>Synaptic and search for and download ndisgtk this will also tick and download the two ndis...files.
Ndisgtk is a gui that appears in System>>Administration>Windows wireless Drivers which makes the use of ndiswrapper really easy. It is pretty straightforward.
Thanks a lot! thats very useful. I'll do that right away!

---

### Post by Timbot2000 on 2010-01-07
By "Driver" do you mean the windows *.ini file? Problem is the Belkin disk has no *.ini file, it seems to be packaged inside an *.exe. Should I load the driver onto my Windows box, and manually copy the ini to a floppy?

---

### Post by bkratz on 2010-01-07
> **Timbot2000 said:**
> By "Driver" do you mean the windows *.ini file? Problem is the Belkin disk has no *.ini file, it seems to be packaged inside an *.exe. Should I load the driver onto my Windows box, and manually copy the ini to a floppy?

Boy, if you could do that it would be the easiest way.  You are supposed to have the .inf file and the .sys file somewhere on your system (I put mine in home). You should be able to scan your Windows system for the files by the date added. I think they end up in xxxx/32 or something like that, that is why I would scan by date added. I don't recall where they really end up. I will look though.
Good Luck

---

### Post by bkratz on 2010-01-07
I just did it to my Windows system and they both ended up in

C: windows\usb devices   ( In XP don't know about other versions)

One also seemed to end up in 
windows\systems32\drivers but I forget which one (I think it was the .inf)
Anyway Ndisgtk seems to only ask for the .inf but, I think I remember seeing that they both should be there.

---

### Post by Timbot2000 on 2010-01-07
Well, I ran it. and long story short, not only did it not see the device, or improve performance, but it killed the Linux rt2870usb driver, so now I have not even vestigial networking. I'll have to download the driver from RealTek and reinstall it.

---

### Post by bkratz on 2010-01-07
You might want to look through this thread

[http://ubuntuforums.org/showthread.php?t=766850&highlight=rt2870usb](http://ubuntuforums.org/showthread.php?t=766850&highlight=rt2870usb)

---

### Post by Timbot2000 on 2010-01-07
This is bad, long story short, native linux driver is dead, where there was hope, now there is none. Downloaded very recent driver from chipset manufacutrer, but I have to actually compile the drive. The instructions are...obscure to say the very least. Is there any way I can download and reinstall fresh drivers for my kernel just ot get back to square one?

---

### Post by bkratz on 2010-01-07
> **Timbot2000 said:**
> This is bad, long story short, native linux driver is dead, where there was hope, now there is none. Downloaded very recent driver from chipset manufacutrer, but I have to actually compile the drive. The instructions are...obscure to say the very least. Is there any way I can download and reinstall fresh drivers for my kernel just ot get back to square one?

I just posted this but something went wrong, so if duplicate ignore one or the other!

This looks recent and helpful

[http://art.ubuntuforums.org/showthread.php?t=1342593](http://art.ubuntuforums.org/showthread.php?t=1342593)

---

### Post by Timbot2000 on 2010-01-07
> **bkratz said:**
> I just posted this but something went wrong, so if duplicate ignore one or the other!

This looks recent and helpful

[http://art.ubuntuforums.org/showthread.php?t=1342593](http://art.ubuntuforums.org/showthread.php?t=1342593)

Very good, wish I had this before I went on my Ndswrapper fiasco. Problem is, I don't think I have the rs8070usb drivers anymore, I think installing the Windows driver wiped them. What's the best way to get them back? Kernel re-install?

Thanks in advance

Tim

---

### Post by bkratz on 2010-01-07
> **Timbot2000 said:**
> Very good, wish I had this before I went on my Ndswrapper fiasco. Problem is, I don't think I have the rs8070usb drivers anymore, I think installing the Windows driver wiped them. What's the best way to get them back? Kernel re-install?

Thanks in advance

Tim

There is an active link in that thread ( I will repeat it here for you)

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

---

### Post by Timbot2000 on 2010-01-07
> **bkratz said:**
> There is an active link in that thread ( I will repeat it here for you)

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)


Thanks, I have that link, and downloaded the driver earlier today. But as a newbie I was hoping for something that did not involve extensive research (or, to be honest, work) on my part (It would be nice if drive package *.deb were available from the package store for easy download and installation) (sigh)

---

### Post by Timbot2000 on 2010-01-07
OK first Issue
	sudo gedit /etc/modprobe.d/blacklist.conf  Returns 
	gedit: command not found 
Is there a variant of this under Xubuntu? (I know some commands do vary)

---

### Post by bkratz on 2010-01-07
> **Timbot2000 said:**
> OK first Issue
	sudo gedit /etc/modprobe.d/blacklist.conf  Returns 
	gedit: command not found 
Is there a variant of this under Xubuntu? (I know some commands do vary)

first I have never used Xubuntu so take this for what it is worth (maybe nothing) but I bet you have to use something other than gedit perhaps it is nano.

Found this thread it looks like I was right

[http://ubuntuforums.org/showthread.php?t=299819](http://ubuntuforums.org/showthread.php?t=299819)

---

