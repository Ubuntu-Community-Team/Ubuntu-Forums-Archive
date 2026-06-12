---
title: "Newbie Needs Help with wireless Belkin f5d7050"
date: 2006-07-06
forum: Networking &amp; Wireless
---

### Post by kingsmm on 2006-07-06
I have just bought a Belkin Wiresless G USB Network Adapter. 
I have spent about 3 hours online searching for a way to make it work. 
I am new to ubuntu and have no idea about all the complex stuff. 
Is there a very easy way to get me hooked up to wireless or should i buy a differnt USB network wireless adapter? 

Thanks,
kip:confused:

---

### Post by jonboy99 on 2006-07-07
This works fine in ubuntu, and is the one I use.  Follow these instructions, copied from somewhere on these forums:

	

1. First, go into Synaptic Package Manager, and search for "ndiswrapper-utils"

2. Install it.

3. Go into Terminal and go to the directory where the .inf file and .sys file(s) are for the driver. (I had the CD for mine, but if you don't have one, research how to find your driver.)

4. Type in "sudo ndiswrapper -i driver.inf", where "driver" is the name of the .inf file.
(example: My .inf file was called "netwg111.inf". Yours will probably be different unless you have a Netgear WG111 usb or laptop card.)

5. Type in "sudo modprobe ndiswrapper"

6. Type in "sudo ndiswrapper -m"

7. Go into Networking (System > Administration > Networking

8. There should be a choice that says "Wireless Connection". It should also say that it is inactive.

9. Click "Wireless Connection" and then click properties.

10. Click "Enable this connection" and fill out the information accordingly. Make sure that you have the correct network name filled out. The Key type will normally be Hexadecimal. I don't know what the WEP key is, but I left it blank and it works fine. My network is configured with DHCP, so I chose DHCP as mine. If your network is not configured with DHCP, select "Static IP Address" and fill out the information accordingly.

11. Internet should work at this point. If it doesn't, you probably don't have something configured right. Go back and check everything.

12. To make this enable itself every time you boot up, open a terminal and type in "sudo gedit /etc/modules".

13. Add "ndiswrapper" to the bottom of all the text. There! Wireless should be configured an ready to go!




To get the appropriate driver files, I would recommend downloading the file  from the belkin website, install the driver on a windows machine, find the directory where they installed by right clicking on the start menu entry and selecting "find target", then copying all the files in that directory over to a temporary directory on your ubuntu desktop.
The drivers on the CD that came with it may work, but they never worked for me in windows so might not work in ubuntu.

hope this helps.

---

### Post by jonboy99 on 2006-07-07
Hmm, well having said that i'm having problems with dapper now.  Worth a try though.

---

### Post by p0intman on 2007-01-15
Well this is my first post so forgive me any errors is protocol I have the Belkin usb g f5d7050 v 4000. I tried using the windows drivers with ndiswrapper it worked very spotty were it worked for a little while and then froze my computer I couldn't even Ctrl+Alt+Del to restart my computer.

The only successfully drivers I used can be found at [http://zd1211.ath.cx/wiki#ZyDASZD1211802.11b/gUSBWLANchipsetLinuxdrivers](http://zd1211.ath.cx/wiki#ZyDASZD1211802.11b/gUSBWLANchipsetLinuxdrivers) 

There instruction seem to be pretty on I have not suffered from a system freeze in a while, hope this is useful to you.

---

### Post by aberry5555 on 2007-01-15
I have this problem with a different wifi card, it would simply not work at all if I tried to use the internet, but I found a way around it. unfortunately (and very unhelpfully) Im not at my ubuntu pc right now, I'm at work, so I cant remember the exact command but I know how to find out what it is. If you go to a terminal and type in sudo ndiswrapper it will give you a list of commands (e.g. ndiswrapper -i or -m) now if you find the command that sets up the wifi alias (as I say I can't remember the exact command) and then, once you've found it, do the next two down. They both have the same starting letters but each has a different ending, I believe they are basically the same thing but the aliases are written in a more complex way, resulting in your computer not managing to trip over itself :p I checked on the ndiswrapper website but couldnt see any list of commands so I can't tell you the exact one at the moment :S I will try and tell you the command later when I get back home.

---

### Post by teaker1s on 2007-01-15
in terminal to see your connected devices

[COLOR="Red"]lspci[/COLOR]

or for usb

[COLOR="Red"]lsusb[/COLOR]

if its a broadcom chipset then look here

[COLOR="Red"]https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show[/COLOR]

---

### Post by NothingtoGein on 2007-11-15
Sorry for my ignorance - but what is the terminal?  Also what is the gO5 equivalent assuming there is one.

---

### Post by NothingtoGein on 2007-11-15
Nvm I found a terminal in g0S.  However, I ran your steps through run command instead of gnome-terminal.  It says the .inf file was already installed.  But there is no networking - that I can see - button in gOS.  Is there another way to get into networking on Ubuntu because I have a feeling I could do the same on gOS.


BTW, the gOS forum crashed for about 5 hours now.  So this is really the only place I can get help from.  Please respond!

---

### Post by sop408 on 2008-07-11
I suppose it is bit too late to respond, but this thread helped me. Try it.
[http://ubuntuforums.org/showpost.php?p=3609183&postcount=1](http://ubuntuforums.org/showpost.php?p=3609183&postcount=1)

---

