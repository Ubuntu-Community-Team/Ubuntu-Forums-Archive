---
title: "Slackware HELP!"
date: 2006-05-16
forum: Networking &amp; Wireless
---

### Post by kickstar on 2006-05-16
Hello,

Ok don’t scream at me but this question isn’t really about Ubuntu, its about a problem I have in slackware 10.2. I have Ubuntu breezy on my desktop but my laptops too old to run it smoothly so a friend of mine from college (rado_london) told me that I might get better performance if I use Slackware and he gave me the disk. Installation went fine and it booted into KDE fine. The system is a lot faster that Ubuntu and its perfect for the laptop. Now, during setup you are asked to setup your network (netconfig) during which you have to supply a hostname and a domain name. then I told it I was using DHCP and it asked me to set a DHCP Hostname (havnt a clue what this is!) which I think is the serial number printed in my modems manual that I got from NTL. Does this look right “ntl-ct8-cj486” anyway I entered it and I thought it would just work. To cut a long story short, it didn’t work. This is where I get angry. I know slackware is made for uber geeks that want To configure every single part of their setup but how comes, and this is where Ubuntu comes into it, how comes the Ubuntu installation sets up my NIC automatically and with no hassle. Couldn’t slackware just incorporate whatever technology is used to do this into their distro and save newbies like me the hassle. So here I am writing this post on my desktop while I stare like a maniac at my lappy as sits there with its beautiful, and it is beautiful, KDE looking straight back at me as if to say “TWEAK ME! TWEAK ME!”. Well I cant do much tweaking until I get the internet up and running so if you want to save this laptop please answer my question PLEASE!.

Basically I need help with the following:

•	getting the internet to work in slackware

END

Information you may require:

•	My NIC is a SIS 900 Based PCI Fast Ethernet adapter. The module for which I have uncommented in /etc/rc.d/rc.modules so that should be getting loaded at boot. The module is called sis900.
•	The modem connected to the NIC is an Ambit cable modem that was supplied by NTL. You can connect it via Ethernet or USB. I'm trying to use Ethernet for my lappy cos I thought it would be easier for the system to detect (apparently not!) should I try to use the USB option? Oh and again on the Ubuntu install it recognizes both!
•	When I ping [www.google.com](www.google.com) it returns ping: unknown host [www.google.com](www.google.com) (WTF!).
•	 There are three lights on my modem none of which are showing any signs of activity.

Please seriously can someone help me I just want to get it working. What do I need to do please!!!!!!](*,) 

thanx

---

### Post by s|k on 2006-05-16
> **kickstar]Hello,

Ok don&#8217 said:**
> www.google.com[/url] it returns ping: unknown host [www.google.com](www.google.com) (WTF!).
&#8226;	 There are three lights on my modem none of which are showing any signs of activity.

Please seriously can someone help me I just want to get it working. What do I need to do please!!!!!!](*,) 

thanx
I just put 'localhost' for the host and 'localDomain' for domain on my slackware machine with DHCP and that worked for me.

EDIT: If your modem isn't showing any lights, you may not be connected to the internet at all. That's when you call your ISP.

---

### Post by kickstar on 2006-05-16
thanx s|k i know my modems ok though cos it works fine in windows and linux (ubuntu) i will try what u said and see if it works

cheers mate!:D

---

### Post by kickstar on 2006-05-16
no luck! arrrr!!!!!!

i cant seem to get it to work. i have got to get some sleep:evil:  though so i think i will leave it till the morning. things like this bug me though and i wont just give up on slackware because imo its a good distro. i think it teaches you more about the workings of you box and i like that. i know its difficult and probably stupid for a newb like me to jump straight in at the deep end with a distro like slackware but at the moment its the fastest distro on my laptop (compared to ubuntu, kubuntu and xubuntu) and so i wanna just set it up. the internet is the only problem apart from that the OS is running perfectly fine.

PS: thankyou for the help s|k, much appreciated.

thankyou people and goodnight!!!!!!!!!!!!!!!!!!!!!

---

### Post by dmizer on 2006-05-16
you said ubuntu was too heavy to run on your laptop ... what's your specs.

i would reccomend trying one of the mini ubuntu distros.  like instead of using gnome for your windows manager, use icewm.

i have a 600mhz pIII pc with 64meg of ram that runs ubuntu mini with enough left over to play dvds without skips.

only reason i suggest ubuntu over slackware is that laptops are fairly quirky about drivers ... especially older laptops.  i tried slackware on several of my older laptops and got nothing but frustrated.

try this.  [http://www.ubuntuforums.org/showthread.php?t=98233](http://www.ubuntuforums.org/showthread.php?t=98233)
works awesome for me. on all of my older laptops, and hardware support should be less painful.  then, if you want to play with slackware, i suggest using a desktop where you have more control over the hardware.

---

### Post by kickstar on 2006-05-17
thanx dmizer

My scecs:

1GHz PIII 256L2
128Mb RAM - alternate between 8 and 16Mb for my shared G's

speaking of shared graphics is it best to use the minimum 8Mb to free up some ram or doesnt it really matter?

i do agree with you about dodgy drivers but the question is how comes ubuntu recognized my cable modem when it was connected through both USB and Ethernet?

Would dapper run any faster than breezy on my laptop?

thanx people!

---

### Post by dmizer on 2006-05-17
you are having speed issues with that laptop?

my current work machine is a 1ghz pIII with 256m of ram, and she runs a moderately tricked out ubuntu gnome just fine.  i can also run a vm win2000 inside qemu without too much lag once the swap catches up.

i did have to do alot of tweaking to get it pared down far enough to make it viable, but since you said you wanted to play anyway ...

i'd say the more ram you have free the better.  but it's a tradeoff because the more vram you have, the faster your machine will be too.  i would suggest staying with factory default settings on that.

haven't looked at daper yet though so i have no idea.  some say it's faster, and from what i've been reading, laptop and wireless support is better.

if you're dead set on using slackware, take a look at what your ubuntu machine uses to drive your modem, and see if you can cary it over to slackware.

not sure i fully understand your question about ubuntu recongnizing both usb and network, but i would strongly suggest you stay away from usb for a cable modem.  first of all, because your usb is probably just 1.1 at that vintage.  and second of all, usb is always more flaky than ethernet when working with network connections.

---

### Post by craigmac on 2006-05-17
I sense a pattern in my posts of late, but anyway...

Download and install the Xubuntu flavour of Ubuntu. It will run exceptionally well on the laptop you have. Setup of network during install is just like Ubuntu so no worries there. 

Get it [here]("http://cdimage.ubuntu.com/xubuntu/releases/dapper/beta-2/xubuntu-6.06-beta2-live-i386.iso") 8)

---

### Post by kickstar on 2006-05-17
first off thankyou for all your comments much appreciated.

i think im gonna just stick it out with no net on my slackbox cos i hav it on my DT anyway.

iv tried xfce but i dont like the feel of it if you know what i mean? is it customizable? can you disable that right click menu thingy cos i hate it (dont know why)?

maybe there is a problem with the laptop, its been dropped more times than the vista release LOL.

once again thanx for all your comments. 
:mrgreen: :mrgreen: :mrgreen: :mrgreen:

---

### Post by mips on 2006-05-17
kickstar,

Can you ping your modem/router's IP address ??
Can you ping 198.133.219.25 ??

If you can ping the above then your problem is DNS related and you will have to manually specify your dns/nameservers.

---

### Post by dmizer on 2006-05-18
[QUOTE=kickstar]The modem connected to the NIC is an Ambit cable modem that was supplied by NTL. You can connect it via Ethernet or USB. I'm trying to use Ethernet for my lappy cos I thought it would be easier for the system to detect (apparently not!) should I try to use the USB option? Oh and again on the Ubuntu install it recognizes both![/QUOTE]
when you are trying to connect to the modem via your laptop, do you still have your desktop connected to the modem (say ... by usb?).

if so, it may just be a simple case of ... your modem is not a router.  what ip is the working desktop getting?

---

### Post by Sef on 2006-05-18
> My scecs:

1GHz PIII 256L2
128Mb RAM - alternate between 8 and 16Mb for my shared G's

Get more ram and Ubuntu will do fine.  I have a 1.3 GHz Celeron with 512 memory, and it works great.

---

