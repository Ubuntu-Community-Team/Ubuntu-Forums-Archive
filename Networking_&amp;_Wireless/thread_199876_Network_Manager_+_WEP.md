---
title: "Network Manager + WEP"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by jrattner on 2006-06-19
Afternoon,

Currently I'm using my broadcom43xx card + ndiswrappers to utilize my wireless network. 

I then use Network Manager (the version found in the repos) to manage my wireless networks.  Everything works flawlessly, I can switch from one wireless network to another using network manager quite easily.

**The problem occurs when I attempt to join a network that has a WEP key.**  I choose the network from the network manager applet, and when I choose to connect it prompts me for the key.   I then enter the key and wait while network manager does its spinning thing to connect.  It never does connect even though im proving the proper WEP key.

This is weird because unless its a secure wireless network, everything is fine.

---

### Post by Doughsay on 2006-06-19
Hi,  I think I'm having a similar problem, but would like more information.  Can you connect to WPA networks, or have you tried?  And how many different WEP encrypted networks have you tried?

My other post is [here]("http://www.ubuntuforums.org/showthread.php?t=199863").  My problem, if you read, is that I can connect to SOME wep networks but others.  But I guess I forgot to mention that it's also happening with the unencrypted networks.  Some work some don't.  Regardless of encryption.

---

### Post by vivedekananda on 2006-09-07
try changing the authentication method in network manager to open/restricted (if thats possible)
the equivalent commmands are:
iwconfig wlan0 key open XXX
or
iwconfig wlan0 key restricted XXX

where XXX is your wep key

---

### Post by dangermouse28 on 2006-09-08
I have exactly the same problem only I have 2 laptops - network manager on both - one works, the other doesn't - I wonder if it's actually a hardware / driver issue?:-k

---

### Post by christophe123 on 2006-09-14
I was unable to connect to my WPE network while I was able to connect to my neigborh unprotected network.

With "iwconfig eth1", I found out that network manager was trying an invalid key (don't know where it got it but not from me).

lspci tells me that I have a:
Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)

I installed gnome-keyring-manager and found that the wpe key stored in gnome-keyring was the wrong one (the one I saw with iwconfig). After editing it to the correct value, I was able to connect to my network.

Last thing to do was to remove the gconf entry for the unprotected network I tried earlier otherwise NM always tried to connect to this one.

rm -rf .gconf/system/networking/wireless/networks/belkin54g

Is there a good place to discuss network-manager issues with its authors?

Hope this help somebody else,
Christophe

---

### Post by randomnote1 on 2006-10-04
I have the same issue.  I can only connect to a 128 bit encrypted wep network.  (I think it's wep anyway)  I haven't had any success in connecting to open networks or networks of any other encryption or encryption level.  I've been able to try it with 4 different wireless routers.  2 linksys, 1 netgear, and 1 belkin.  So, I'm really unsure what the deal really is.  I don't have time at the moment to post the commands listed in the previous posts, but I will do that in the near future.  Thanks!](*,)

---

### Post by radium226 on 2006-10-14
I was having a similar problem--open networks worked fine, but WEP networks would not connect.  I can now verify thad vivedekananda's advice to use:

iwconfig wlan0 key open XXX

worked (thanks viv!).  I'm using a Dell D620 with the Broadcom-based wireless (running off of ndiswrapper driver with bcmwl5.inf).  

Also related, the ndiswrapper that can be gotten via automatix did not work for me; I had to download the source and compile it myself.  Finally, I also had to disable the ethernet device (wasn't enough to just change the Default Gateway Device).

---

### Post by Chaos5lw on 2006-10-15
> **vivedekananda said:**
> try changing the authentication method in network manager to open/restricted (if thats possible)
the equivalent commmands are:
iwconfig wlan0 key open XXX
or
iwconfig wlan0 key restricted XXX

where XXX is your wep keyI have the same problem.

Using Kubuntu 6.06, a Linksys WMP54G PCI network adapter and a Linksys WAP54G Access Point with 128-bit WEP encryption with SSID turned off.

If i turn off WEP, the network connects fine. With it on neither using Wirless Assistant or iwconfig to change the settings will get the network to connect (depsite both showing the correct info). If i use the Network Settings option under System Settings, the network still doesnt work and but even worse the system will hang on boot at the Configuring Network Devices stage and i have to reinstall Kubuntu.

Anyone got any ideas at all?

---

### Post by Chaos5lw on 2006-10-15
Ive even tried using SuSE with ndiswrapper, and still it wont connect with WEP.

---

### Post by Chaos5lw on 2006-10-15
I am now using the Live Kubuntu CD on my laptop (Dell Inspiron 6000) and to my supprise the network configured using Wireless Assistant and WEP first time with no problems.

What the hells going on with my desktop computer?

---

### Post by jshein on 2006-10-15
Give my solution from this thread a try

[http://ubuntuforums.org/showthread.php?p=1622085](http://ubuntuforums.org/showthread.php?p=1622085)

---

### Post by Chaos5lw on 2006-10-16
> **jshein said:**
> Give my solution from this thread a try

[http://ubuntuforums.org/showthread.php?p=1622085](http://ubuntuforums.org/showthread.php?p=1622085)
Still no good.

I bought this card because reviews said it worked with Linux (namely Kubuntu) See [here]("http://www.dabs.com/productview.aspx?Quicklinx=2D13&SearchType=1&SearchTerms=linksys+wmp54g&PageMode=3&SearchKey=All&SearchMode=All&NavigationKey=0&v=3#infoarea") the review called "Works with Linux" by "Howard Connellan" on the "24/04/2006"

---

### Post by Chaos5lw on 2006-10-17
No one?

---

### Post by Chaos5lw on 2006-10-17
UPDATE
I downloaded the Ubuntu 6.06 ISO and ran it as a live CD. After following [this guide]("https://help.ubuntu.com/community/Rt61WirelessCardsHowTo") i finally have the network card working. Im installing Ubuntu now and hopefully it will continue to work and i can just install KDE instead of Gnome.

---

### Post by Chaos5lw on 2006-10-18
Ok, i have the system installed and the wireless is working however i still have one slight problem because i have to run "dhclient" in a shell everytime i boot the computer and because the interface is configured manually via the drivers conf file, network manager shows it as unconfigured.

Any suggestions?

---

### Post by Chaos5lw on 2006-10-20
The system is running very well now with the Kubuntu desktop. However there is still the problem of the network not auto-connecting on boot.

---

### Post by blackfede on 2006-10-22
> **radium226 said:**
> I was having a similar problem--open networks worked fine, but WEP networks would not connect.  I can now verify thad vivedekananda's advice to use:

iwconfig wlan0 key open XXX

worked (thanks viv!).

This also worked for me! I've got an Airport Express Base Station with WEP 128 bit network. An USB canyon wireless adapter (Model CN-WF518). Worker fine after recompile driver (driver name: zd1211), becose the one present by default in 6.04 doesn't work at all.
Thanks!

---

