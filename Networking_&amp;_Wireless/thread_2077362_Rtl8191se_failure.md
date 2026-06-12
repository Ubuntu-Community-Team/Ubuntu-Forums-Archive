---
title: "Rtl8191se failure"
date: 2012-10-28
forum: Networking &amp; Wireless
---

### Post by windowsfree on 2012-10-28
I installed LM13 (64 bit) on a generic laptop. (i5 processor, 8 gigs memory)
It detected my wireless network, when I tried to connect it connected and in about 20 seconds disconnected and could not reconnect.
I can see two wireless access points but cannot stay connected to either. If I reboot the laptop it attempts to connect and then disconnects and cannot reconnect. The wireless card is an RTL8191se. 

I see that Realtek has a driver for later kernels, but an unsure on how to install it. 
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE)

bob@laptop ~ $ inxi -SNx
System: Host: laptop Kernel: 3.2.0-23-generic x86_64 (64 bit, gcc: 4.6.3) Desktop: Gnome Distro: Linux Mint 13 Maya
Network: Card-1: Realtek RTL8191SEvB Wireless LAN Controller driver: rtl8192se port: 5000 bus-ID: 05:00.0
Card-2: JMicron JMC250 PCI Express Gigabit Ethernet Controller 
driver: jme ver: 1.0.8 ports: 4400 4000 bus-ID: 04:00.5

Any suggestions would be helpful.

Thank you,

---

### Post by ahallubuntu on 2012-10-28
To install the Realtek drivers, unzip the file you downloaded, then open a terminal window and read the "readme" file or one of the other documents.  This should tell you how to proceed, in a terminal though by typing commands.

Sometimes Realtek includes an "install.sh" script you run as sudo; sometimes they tell you to run "make" directly.

You may have to cd into the directory just created from the zip file and then:

```
chmod 755 ./install.sh 
```

then

```
sudo ./install.sh
```

to make that install.sh file executable, if your driver has that file.  Otherwise, follow the instructions they provide in the readme file or other documents.

You may have to blacklist the existing drier files.  Here's a similar case (not your exact card):

[http://ubuntuforums.org/showthread.php?t=2076315](http://ubuntuforums.org/showthread.php?t=2076315)

---

### Post by windowsfree on 2012-10-28
Thanks, I will attempt those steps.  Wish it was less complicated.  Was thinking of changing card in laptop.

I will post results

---

### Post by ahallubuntu on 2012-10-28
I have upgraded many laptop wireless cards successfully.  But HP and Lenovo laptops are not good choices for this, because they "whitelist" wireless cards so that you can use only specific approved cards!  Dell, Acer, Toshiba, etc. I've had no problem with.  Not sure what kind of "generic laptop" you have so I can't say what kind of luck you would have or what other card would work in there.  If it's an Intel chipset, one of the Intel cards would probably work better (Intel 5100, etc.).

---

### Post by windowsfree on 2012-10-28
it is a clevo b5100 with an Intel i5 processor.  
I dont know if it is pci type of adaptor or not, I removed the cover and saw some devices with wires going to them and they were screwed on to the laptop.  Thanks for the quick reply.  I tried a USB wifi device and it works but the built in turns on right away.  I was thinking of trying the blacklisting of the rtl8191se driver so the OS only sees the USB device that works.  Thanks again!

---

### Post by ahallubuntu on 2012-10-28
Clevo lists a driver for your laptop for an Intel PROSet WLAN driver.  That means one of the Intel cards will likely work just fine.  If your card happens to have bluetooth built in as well you'll want to get the Intel card that also does; if not, you can probably get an Intel 5100 or 6200.  If the card has three antenna wires attached to it, get the Intel 5300 or 6300 instead.

You can get used versions of these cards cheaply on eBay, but watch out for "new" cards from Asia.  I've had poor luck with those either being marked wrong or just not working.  I prefer used cards that came out of existing laptops.

---

### Post by windowsfree on 2012-10-28
Thank you, I think I am going to try that route as I have no luck with driver listed from Realtek.  I don't know if it is because of 64 bit or not, but it would not compile.

---

