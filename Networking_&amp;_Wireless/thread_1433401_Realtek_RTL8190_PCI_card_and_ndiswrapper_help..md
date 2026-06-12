---
title: "Realtek RTL8190 PCI card and ndiswrapper help."
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by The Lonely Toaster on 2010-03-19
I recently bought a Trendnet/Realtek wifi card for my computer. Stupid me, forgot to check to see if it works natively with Ubuntu...it doesn't. I'm still fairly new to ubuntu though I understand most of how and what things do, but I really need help with this one. 
What exactly is the process for getting this card to work in 9.10?
And how do I use 'ndiswrapper' to go about it?

If someone could breakdown how to do this that'd be awesome. It'll really help me with learning more about how to go about things in linux.

Thanks a bunch!


-tlt

---

### Post by silencej on 2010-03-19
You can go to realtek website:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=21&Level=4&Conn=3](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=21&Level=4&Conn=3)
There is no 8190 type. So you need to find out which one of the provided driver match your card.

---

### Post by Nauscar on 2010-03-19
hey i have the exact same card (RTL8190) and I was wondering how you managed to get it working in Ubuntu.  It would be nice to get Ubuntu fully functional on yet another one of my computers!

---

### Post by Mayfairy on 2010-03-25
For some reason the Linux drivers with this card don't work with Ubuntu Karmic and Lucid anymore, and none of the Windows drivers via Ndiswrapper won't work either. 

What I did was I scoured the internets for some drivers and eventually downloaded Realtek 819xP drivers (think I found them by searching 8192E drivers) and used their WinXP drivers with ndiswrapper to get it working. 

Someone somewhere told that Lucid kernel (2.6.32-) would bring back the 8192E drivers so I upgraded my Karmic to Lucid but I'm still using ndiswrapper drivers with it. The connection with these drivers is a bit flaky so I need to investigate whether I can find the kernel drivers for this card. 

The card I'm using is an A-Link Wireless-N 300 PCI card, but lspci lists it as Realtek RTL8190 card. 

Hope this helps someone. Too bad I can't remember exactly where I downloaded the working drivers. It might have been Realtek's own site but I'm not sure.

---

### Post by jlucio on 2010-10-08
I have used this tutorial here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

But, of course, I've changed the commands that depended on the driver. The one I used was exactly the one that came with the product, more precisely the WinXP x86 driver named "rtl8190p.sys" and "net8190.inf".

The commands, used on Ubuntu 9.10 were:

**[B][B]Step 1:- Install NDISWrapper and Blacklist Native Driver**[/B]
[/B]echo -e 'blacklist rtl8190\nblacklist wl' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/rtl8190; cd ~/rtl8190
[B][B][B]
Step 2: Copy [/B][/B]"rtl8190p.sys" and "net8190.inf" to ~/rtl8190
[/B]
[B]Step 3: Configure NDISWrapper (and WPA Supplicant)
[/B]sudo ndiswrapper -i net8190.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

---

