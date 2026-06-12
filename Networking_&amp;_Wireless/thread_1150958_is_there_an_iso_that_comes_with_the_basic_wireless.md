---
title: "is there an iso that comes with the basic wireless componets"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by rhendrix9 on 2009-05-06
I have a linksys 54gs router and a windows box using a wusb11 v4 wireless adapter. I just installed 9.04 but evidently there is NO wireless support, or am I missing something?

Is there another distro (any brand or version) that will let me utilize the wireless right out of the "box" , with a lot of trouble?

---

### Post by pastalavista on 2009-05-06
You might give [Crunchbang Linux]("http://crunchbanglinux.org/") a try. It comes with lots more drivers but fewer applications. You still might need to connect via wired to install the wireless. Have you tried that with Ubuntu?

---

### Post by jml on 2009-05-06
Actually compared to distros just a few years ago, 9.04 has very good wireless support.  However if you are new to Ubuntu its not obvious where to find it.  Assuming that you did a standard install with the USB adaptor plugged in, you have a very good chance of having wireless.

The key is the NetworkManager applet.  You won't find it in the menus.  If you look in the top right hand corner of the screen, you should see something that looks like a miniature computer terminal.  If you right click on it you will see two "radio buttons"  One is labled wired networking, the other wireless networking.  Make sure that the wireless networking option is selected.  Then left click on the same icon and you should see a list od all networks that your computer can "see."  Select the one you want to connect to.  Enter the pass phrase if it is encrypted and then click on the highlighted button to close the dialog box.  The icon should change to two very small circles "orbiting" each other.  When both turn green, a process that may take up to a minute, you will see a dialog box announcing that you are connected to the network.  You should then be able to surf the net, check e-mail etc.  Hope this is of help.

Joe

---

### Post by rhendrix9 on 2009-05-06
Well I set up "network connections" which i found in system but I could not find a way to make it try to connect I suspect it does not see the usb adapter.

I do not have a tiny terminal but i do have bars (like the at&t ad) but no mention of wireless there.

It doe not make sense that to use wireless you have to be wired!

---

### Post by pastalavista on 2009-05-06
> 
It doe not make sense that to use wireless you have to be wired!

Your wireless only worked when you got it because the Windows drivers for that card were installed by the manufacturer. My son added a wireless card to his Windows. The card came with a Windows install disk. Linux doesn't have that luxury since the wireless card makers don't support Linux as well because there's no money in it. The only way to download the wireless drivers is to connect to a wired network. It would be very hard to include drivers for every brand of wireless card out there. Is it such a huge problem for you to connect directly to your modem or router? Don't be such a cry-baby...

---

### Post by acimmarusti on 2009-05-06
Open up a terminal and type:

```

lspci -v | grep Network

```

Post the output. This will tell us what kind of PCI wireless device you are using.

If you are using a usb device then use: *lsusb*

---

### Post by rhendrix9 on 2009-05-06
Got it.
Since i was told it should have what it needs already.  I gotto thinkin.

so i pulled out another wireless adapter (diff brand) and plugged it in. ubuntu saw it and i got connected.

of course when i went to windows, then it was broken.  After downloading drivers everything seems to work now.

just a few hours, lol

Thanks

---

### Post by rhendrix9 on 2009-05-07
> **pastalavista said:**
> Your wireless only worked when you got it because the Windows drivers for that card were installed by the manufacturer. My son added a wireless card to his Windows. The card came with a Windows install disk. Linux doesn't have that luxury since the wireless card makers don't support Linux as well because there's no money in it. The only way to download the wireless drivers is to connect to a wired network. It would be very hard to include drivers for every brand of wireless card out there. Is it such a huge problem for you to connect directly to your modem or router? Don't be such a cry-baby...

Thanks for the constructive criticism

Sorry to hear about your son.

---

### Post by pastalavista on 2009-05-07
I forgot to mention that my son installed Crunchbang Linux on his box. His wireless didn't work with Linux either. He carried his big old tower downstairs, hooked it up directly to the router and downloaded and installed the correct driver for wireless in about 15 minutes. He still uses XP sometimes but only when he wants to play games. Sorry to be so condescending. I've learned that with a little patience and research you can do almost anything with Linux. And when it breaks you can fix it yourself without having to dowload and install special software to do it. I don't even use Windows any more at all. I'm not a gamer.

---

