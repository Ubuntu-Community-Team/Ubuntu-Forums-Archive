---
title: "Very odd problem. My wifi not finding any networks, when it used to. Please read."
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by iamcims on 2009-07-06
I am really confused by how this is even possible. It's really strange. 

A few days ago I formatted and installed Ubuntu 9.04. I was connected to my LAN, I did the updates and then rebooted. I checked to see if my wifi was working and it was finding a lot of networks, some that I didn't even see on windows. It was working well. A friend talked me into using fedora so I installed that (Clean format) Fedora out of the box worked with my wifi with no issues. After using Fedora, I decided that Ubuntu is better for me and had less issues from the start out of the box. So I did another format and installed Ubuntu, just like the first time. Everything was fine, my wifi worked after system update. But this time I kept getting prompted for a password every bootup for a network keyring. I did many searches and got a lot of answers that didn't really fix my problem, I found it odd that it didn't do this for me the first time around. Since it was a new install anyway..

I formatted again lol. But this time around my wifi is not working! Nothing is showing up for wireless networks. I just don't understand how it would be possible to get a different result from a fresh format, when everything else is the same. I tried pressing my wifi button, etc. I even was so confused I formatted again, no luck. Nothing has changed. I installed ubuntu, ran updates with my lan like before and rebooted. The networks should pop up after that but not anymore.

What would make my wifi all of a sudden not work besides a hardware failure?

It's been awhile since I have used ubuntu, I can provide you with any information you need if you give me the commands. I'm just stumped as to how this is possible.

---

### Post by peterkim04 on 2009-07-06
Sorry to jump on your wagon like this but I had, and still have a similar problem. I have a Vaio NR10 with Ubuntu 8.10. When I had the Vista, the wireless was working ok, and the first ubuntu I had was 8.04 and it was finding lots of networks without having to configure anything. I upgraded to 8.10, still no problem working fine as before. But I had to format and install the ubuntu again after a problem, now the wireless isn't finding any networks. Even in places with wifi network, and i know that it is there because i used to use it but no detection. I have read some threads that I might have to find the networks physically, and having to set the network unsecure to set up properly, is that right? Would it help if I go up to 9.04? Many thanks!

---

### Post by iamcims on 2009-07-06
> **peterkim04 said:**
> Sorry to jump on your wagon like this but I had, and still have a similar problem. I have a Vaio NR10 with Ubuntu 8.10. When I had the Vista, the wireless was working ok, and the first ubuntu I had was 8.04 and it was finding lots of networks without having to configure anything. I upgraded to 8.10, still no problem working fine as before. But I had to format and install the ubuntu again after a problem, now the wireless isn't finding any networks. Even in places with wifi network, and i know that it is there because i used to use it but no detection. I have read some threads that I might have to find the networks physically, and having to set the network unsecure to set up properly, is that right? Would it help if I go up to 9.04? Many thanks!

Yeah, what would make it be different when ALL of the variables are the same? 

If I were you, since you just reformatted again why not just install 9.04 anyway, maybe you'll be lucky, if not, at least you have the newest version available.

---

### Post by diablo75 on 2009-07-06
Do you happen to know what wireless adapter (chipset) you have?  You might find it by running "lspci" in a terminal.  Paste the output of that command back in here.  Also, what is the model number of your system?

---

### Post by iamcims on 2009-07-06
> **diablo75 said:**
> Do you happen to know what wireless adapter (chipset) you have?  You might find it by running "lspci" in a terminal.  Paste the output of that command back in here.  Also, what is the model number of your system?

Compaq Presario c700

```
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
**01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)**
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

---

### Post by iamcims on 2009-07-06
SOLVED?

Well, after basically giving up on it for tonight. My battery was down to 8% and I turned off the machine. I go to my bedroom and plug it in the wall, decide to turn it on. Magically.. **my wifi is now working** like before. I did not do anything but post this thread on the forum and restart 5+ times or so (with my LAN plugged in/out, etc) I did try the other drivers in the hardware profile but that one made it so my wireless didn't even exist, then I deactivated it to go back to the old one, rebooted, no luck still. It also can't be the location, I live in a small apartment and before I was right next to the router where it worked fine before. Odd huh?

I rebooted a few times before so I'm not sure why it works now. I don't want to mark this thread as solved just yet just because it's still a question as to how this can happen. I did not install/update anything since the problem started. If no one knows why, I'll just mark it as solved to end it I suppose.

Who knows :-k

---

### Post by peterkim04 on 2009-07-23
Solved? 

Well, yes. I didn't really want to upgrade to 9.04, just waiting for the next one not because I loved 8.10 so much. I did to see if this problem will solve itself, and yes it did. As soon as it was upgraded (surprisingly maintaining a lot of settings from the previous version), flick the wi-fi switch and it's finding so many that it was stupid. Still having a little problem with wi-fi when using the battery power, but overall, it is solved. Thanks to everyone who suggested everything.

---

