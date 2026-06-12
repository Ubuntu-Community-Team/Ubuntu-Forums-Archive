---
title: "USB wireless"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by James_M on 2006-06-04
I'm using Xubuntu on an iBook (soon on a Powerbook G4) and  even though I have an Airport Extreme card, none of my four tries to use it have worked.  I'm using a live CD because this machine isn't mine, but on the PB I can do a clean install.  I was just wondering if there is a USB Wi-Fi dongle I can use out of the box with Dapper.

On another note, I'd like to be able to install this to a firewire drive.  How do I do that?

---

### Post by bsell on 2006-06-04
I don't have a Mac, but I have a desktop and a cheap, generic notebook (Via CPU) using Netgear WG111v2 USB wireless adapters. Both worked out of the box with Dapper.

---

### Post by James_M on 2006-06-04
cool, thanks.  I'll try it out.  I'm assuming that by "out of the box" you mean no driver downloads, no hours in command line.  "Out of the box" as in plug-and-play, not "plug, mess around for three hours, and then play"?  If so then you have saved my job.

---

### Post by bsell on 2006-06-05
Configured it in Networking in less than 2 minutes while using LiveCD. Surfed the Ubuntu forums during install. No driver downloads. No ndiswrapper. No terminal.

---

### Post by James_M on 2006-06-05
I went out and bought the card, and when I plugged it in, Xubuntu saw it, but I can't get a connection.  What exactly do I need to configure, and how?
[EDIT]  Not sure if this means anything, but the little blue light blinks once when I put it in, but I still can't ping anything or open any web pages.

---

### Post by James_M on 2006-06-06
It shows up when I do a lsusb, and when I do an iwconfig, but I just can't seem to see my AP anywhere.  I set it to find the SSID of 2WIRE927 (my router), but that won't do anything.  I tried setting a static IP, but that won't work either.  WHat the heck am I doing wrong???

---

### Post by Jason_25 on 2006-06-06
Could you post the output of the command you used when you say setting an IP "doesn't work"?  Also , you say the graphical thing could not find your router.  Well that's typical.  Does 
```

iwlist scan

```
see it though?

---

### Post by James_M on 2006-06-06
[QUOTE=Jason_25]Could you post the output of the command you used when you say setting an IP "doesn't work"?  

[/QUOTE]
I didn't use a command, I just tried the network manager and turned off DHCP on my router.  I'm nowhere near a wireless network right now, so I'll post the "iwlist scan" results when I get home.  one bit of potentially hopeful information, though:
```
lo      Interface doesn't support scanning

eth0      Interface doesn't support scanning

sit0      Interface doesn't support scanning

wlan0      No scan results
```
I think this means that Ubuntu knows my card is there!

---

### Post by bsell on 2006-06-06
[QUOTE=James_M]I went out and bought the card, and when I plugged it in, Xubuntu saw it, but I can't get a connection.  What exactly do I need to configure, and how?
[EDIT]  Not sure if this means anything, but the little blue light blinks once when I put it in, but I still can't ping anything or open any web pages.[/QUOTE]

Your blue light is blinking because it is trying to find the network. That's good news. You need to set it to the network to get an access point.

Click on Applications. Go to System>Networking. This will open a dialog box. You should see the wireless connection and it should say it is active. Highlight the wireless connection. Click on Properties. Another dialog box will appear. You will see a  ***blank*** menu next to Network Name (ESSID). Click on the menu arrow. Your network should show up (mine says NETGEAR). Click on it to assign it as ESSID. 

In Connection Settings set the Configuration to DHCP. Click OK. An 'Activating interface wlan0' message will pop up. It will stop after your interface is activated. On the Default Gateway Device, click on the menu arrow and click to highlight wlan0. Click OK. 

Open Firefox and start surfing or ping a web address to see if it works. 

I used the Xubuntu Live CD and my NETGEAR USB wireless to surf here using the instructions I just gave you.

---

### Post by James_M on 2006-06-06
okay, no go on the iwlist scan.  Even with an AP about 2 feet away it won't work.  It still says no scan results.  Bsell, I tried your mini tutorial and I got as far as interface properites.  The network didn't show up in the drop down menu.  When I said it blinked, I meant just once, not a repeating blink.  Think of it more as a blip.

---

### Post by Jason_25 on 2006-06-06
Well for some reason scanning may not be working but hopefully it can still connect.    Enter your essid and monitor the connection with 
```

iwconfig

```
I noticed you mentioned the network manager.  It is not at all compatible with the graphical network tool.

---

### Post by James_M on 2006-06-07
I'm kind of confused, is the ESSID the same as the name my router has, or is it the name of my card?

---

### Post by Jason_25 on 2006-06-07
ESSID is your router's name.

---

### Post by bsell on 2006-06-07
ESSID is the network name. Usually, it's the same as your router.

Make sure your router supports g/b wireless. 

Ubuntu "sees" your wireless USB. It did read wireless connection is active in networking, didn't it?

---

### Post by James_M on 2006-06-08
[QUOTE=bsell]ESSID is the network name. Usually, it's the same as your router.

Make sure your router supports g/b wireless. 

Ubuntu "sees" your wireless USB. It did read wireless connection is active in networking, didn't it?[/QUOTE]
yes it tells me the connection is active.

---

### Post by mavioo7 on 2006-07-15
I am having similar problem with Linksys USB Wireless-b adaptor,

On device manager it looks like the system perfectly find the driver but i am unable to see the wireless card under System, Administration, Networking
only my Ethernet  and my modem connection are listed there. 

why i have to do or check to to display wireless adaptor under networking list?
Thank you,

---

