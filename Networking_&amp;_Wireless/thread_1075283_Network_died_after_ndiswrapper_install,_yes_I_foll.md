---
title: "Network died after ndiswrapper install, yes I followed the write-up..."
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by projectbronco on 2009-02-20
I have the netgear wg111v2 which works right when you plug it in, (Using Ubuntu 8.10) even though the light never came on. BUT, it kept dropping the connection and the only way I could get it back was to restart. 
So, I tried installing ndiswrapper as per the instructions. I then installed the newest netgear drivers for windows, using wine, which was the only way it would open. Then, I opened up ndis, installed the .inf file, but it said it was already installed. (this is version 3.4.0).
Then I turned off the computer, the next time I turned it on, the network wasn't working.
I type in ndiswrapper -l and it says
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile      install driver described by 'inffile'
-a devid driver use installed 'driver' for 'devid' (dangerous)
-r driver       remove 'driver'
-l              list installed drivers
-m              write configuration for modprobe
-ma             write module alias configuration for all devices
-mi             write module install configuration for all    
                devices
-v              report version information

where 'devid' is either PCIID or USBID  of the form XXXX:XXXX, as reported by 'lspci -n' or 'lsusb' for the card

The lsusb says:
ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)


What's annoying is that the network applet at the top won't list my network anymore. ndiswrapper says it can't find a network configuration tool when I try to configure the network. But, when I go to network configuration and choose wireless, it still has the settings...unless those are just saved from before?

I have been reading through posts now for a few hours and it has gotten me nowhere. If someone could help me I would really appreciate it. Thank you.

---

### Post by projectbronco on 2009-02-20
I will bump you!
Does anyone know what the problem is? I'm reduced to using my w2k laptop. lol

---

### Post by projectbronco on 2009-02-20
OK, well I tried ndiswrapper -i /path to my driver/
it said:

install/manage Windows drivers for ndiswrapper

Then I put in ndiswrapper -l
which gave me:

net111v2 : driver installed
       device (0846:6A00) present (alternate driver: rtl8187)

So, I know the driver is working, but it still won't find network tool...

I guess I should've been happy with my occational dropping connection...too late now. I'm in it for the long haul. 

If anyone knows a way to get the netgear driver working that would be cool, otherwise is there a way to get the old rtl8187 driver working again?

---

### Post by projectbronco on 2009-02-20
I thought perhaps the driver was the issue, from what I've been reading. So, I blacklisted rtl8187, uninstalled and through away the driver version 3.4.0, and tried 3.2.0. It is a vista only version, so it wouldn't even install.
Then I installed version 3.3.0, it installed, but I still got the "Could not find a network configuration tool" message. This is kind of annoying...
Does anyone even know how I get a network configuration tool, or how I lost the one I had, I was online only a day ago with my linux computer.

Oh, and this is the 64 bit version.

Thanks again in advance for any help.

---

### Post by projectbronco on 2009-02-21
Well, I found this site, [http://www.linuxquestions.org/questions/linux-wireless-networking-41/netgear-wg111v2-ndiswrapper-installation-problems-460124/]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/netgear-wg111v2-ndiswrapper-installation-problems-460124/") and it made sense, but didn't really help. I did everything he said, and even tried the Win98 driver that the dude in the last comment talked about. But still nothing happened.

I really don't want to do a fresh install, I just got everything how I wanted it, sans internet.

Also, I think I win for being the all-time thread killer. Everytime I post in this thread, no one else posts. :D

---

### Post by projectbronco on 2009-02-21
I guess since no one knows what to do, I'll just back up what I have and do a fresh boot. It kind of sucks, but oh well. I guess I learned to stay away from ndiswrapper, at least for the wg111v2.

---

### Post by scytheye on 2009-02-21
I am trying to get airmon to work, when I type **airmon-ng** into terminal, I get this: 
Interface	Chipset		Driver
wlan0		Unknown		ndiswrapper

I also looked up my card and its should support monitor mode? 
Modes : 	Managed, Ad-Hoc, Mesh
[I]Security : 	WEP, 802.1x, WPA
Scanning : 	Wireless Extensions
Monitor : 	Yes [/I]

I understand that ndiswrapper doesn't but maybe I don't need ndiswrapper.  Here's my **lscpi** output: 
[I]
01:01.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)[/I]

Please help!

---

### Post by sailthesea on 2009-02-21
I hope you didn't reinstall yet projectbronco!
I've got a very similar setup to you and have been the same problems Wireless in 2K optimal but really intermittent in Ubuntu LED sometimes on 50% of the time unplugging and replugging sometimes fixes this rtl8187 certainly helped but has not completely ndiswrapper didn't seem to help at all couldn't source drivers I thought it might be Firefox itself but doubtful now What else have you tried? I feel like I'm close to the solution Maybe we just need to join forces?
Cheers

---

### Post by projectbronco on 2009-02-22
Yeah, I've already reinstalled Ubuntu. My internet worked right away just like before I tried ndiswrapper. I have had it drop the connection...like before, but that is better than no connection at all. 
I'm actually using infrastructure as apposed to ad-hoc. I don't know if that could make any difference for you.  

I searched the ndiswrapper thread for Mavell Technology 88w8335.

You might want to try what they told this person to do? It didn't seem to work for him, but it may for you. I hope you get it working. I know that it can be *very* annoying. Here's the link:
[http://ubuntuforums.org/search.php?searchid=56002749]("http://ubuntuforums.org/search.php?searchid=56002749")

---

### Post by sailthesea on 2009-02-22
Thanks for the reply
  I looked at this one before and decided to try a terminal solution as there seem to be some issues with ndswrapper I can live with a sketchy connection Yes it can be very annoying But the way I see it 8.10 is still in evaluation and to foul up the kernel with windows code is a step in the wrong direction If I figure out a decent solution I'll be sure to get back to you 
 BTW Have you noticed how HOT the thing gets? Hmmmm....

 Thanks anyway

---

### Post by projectbronco on 2009-02-28
Sounds good.
I didn't notice until I felt it just now (I assume you're talking about the usb dangle). Also, I find it funny how it works without the light blinking. 
Oh well...

---

