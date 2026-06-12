---
title: "Switched ZTE MF626 still not connected"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by Cyberdragonfly on 2009-11-19
I have a t-mobile uk, ZTE MF626. With ubuntu 8.04 on a toshiba NB100.

I've managed to change the mode from usb storage to a modem. lsusb shows 19d2:0x0031 
... But I don't know what to do now. I've read that many posts and tryed several of the suggested ways to get it connected (udev + hal, subserial ...). I am very new to ubuntu and would appreciate some help with the next step.

I have the latest version of modeswitch on the desktop and I've altered its .conf file

The usb modem light goes blue/green (always a static light, never flashing) but its not showing t-mobile uk as an option in the network manager.

---

### Post by cavh on 2009-11-19
[I'm running Karmic Koala 9.10 so the command locations may be a little different]


1. Do you have Network Manager installed? You can check by opening Synaptic (System -> Administration -> Synaptic Package Manager) and searching for *network-manager*. 

2. If you don't have it installed, then connect to the Internet (using Ethernet/wireless) and reload the Synaptic package list (click on the blue reload symbol at the top left of the Synaptic screen), then search again for network-manager, right click the entry in the list and choose 'mark for installation', then click the green 'Apply' symbol. Synaptic will then download *network-manager* plus any dependencies, and install it for you.

3. Presuming you now have Network Manager, have you created a T-Mobile connection? You do this by going to:

System -> Preferences -> Network Connections -> Mobile Broadband tab -> Add

The T-Mobile (UK) settings will be inserted automagically by the network-manager after you run through the wizard that pops up.

---

### Post by Cyberdragonfly on 2009-11-19
The application list says I have network manager installed but its not there as an option from the system menu and I certainly don't get a wizard pop up. I'm going to instal it again and see if it comes up then.

---

### Post by Cyberdragonfly on 2009-11-20
I'm confused as to what the problem is with the network manager. I have the NM applet but I don't have an option anywhere to select a mobile broadband provider.

Do I need to remove the network manager and download another and do I need to initialize the usb modem on a windows system before it will work on ubuntu ?

---

### Post by pdc on 2009-11-20
RIGHT-CLICK on network manager;

select EDIT CONNECTIONS

third tab along: MOBILE BROADBAND

select ADD

choose COUNTRY;

choose PROVIDER

click to accept; CLOSE;

now left-click on network manager: any joy?

---

### Post by Cyberdragonfly on 2009-11-20
I may be in the wrong place altogether but when I right click on the NM applet link it says :

x Enable Neworking

x Enable Wireless

! Connection infornation (that option is greyed out and un-clickable)

 About

... they are the only options.

---

### Post by Cyberdragonfly on 2009-11-22
Which network manager app contains the mobile broadband setting option. I think I have the gnome network manager. Do I need to install the knetwork manager and the network selector ?

---

### Post by cavh on 2009-11-23
No need for knetwork manager, the Gnome version should be perfectly adequate. What version of the Gnome network manager are you running? Suggest checking via Synaptic and upgrading if there's a later version available (press the 'Reload' button in Synaptic to check the repositories for the latest packages).

---

### Post by coffeecat on 2009-11-23
> **cavh said:**
> What version of the Gnome network manager are you running?

The OP is running Hardy, which might explain why they don't see the mobile broadband option.

**Cyberdragonfly**, I realise that you may be running Hardy for a good reason and that you may not want to upgrade just yet, but why not download the ISO for the Karmic desktop CD? Run it live and you'll see the broadband option in the newer version of NM that comes with Karmic. Try connecting while still in live mode. If it works - and if everything else works - this may give you food for thought. You might want to run this later version. You won't damage or affect your Hardy install by running the live CD - so long as you don't write to the HD.

---

### Post by Cyberdragonfly on 2009-11-27
> **cavh said:**
> What version of the Gnome network manager are you running? Suggest checking via Synaptic and upgrading if there's a later version available (press the 'Reload' button in Synaptic to check the repositories for the latest packages).

It has 0.6.6-Oubuntu5 network manager. I've read that people have used the same network manager but I haven't read a post from anyone thats had it connected and was running ubuntu 8.04. 

So, maybe trying it with a later version of ubuntu, running live is the next logical step. 
I'm using 8.04 because thats what it came with and its only a few weeks old. I knew nothing about linux before this and I'm still way off knowing what I'm doing. So, thankyou for the replys every idea helps.

Edit: lsusb is now showing as ID 19d2:0076 ??? What on earth is that ?

---

### Post by cavh on 2009-12-10
> lsusb is now showing as ID 19d2:0076 ??? What on earth is that ?

'19d2' indicates the manufacturer of the modem chipset, '0076' indicates a model number.

Try running the LiveCD as suggested by Coffeecat, life will be a lot easier if you can use 9.04 (Jaunty) or 9.10 (Karmic). Of the two I would suggest Jaunty, there have been many issues with mobile broadband in Karmic.

---

