---
title: "We get signal!  Well, sort of..."
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by mr_pitchfork on 2009-06-23
Alright, interesting issue:  My machine recieves a perfect wireless signal, but no software can access the internet.  I've tried switching the wireless switch off and on, restarting the coputer, restarting the router, and, since I'm definitely not a computer magician, I'm completely out of ideas.  The help documentation says nothing about this, and I'm honestly not sure how to search for the issue on the board.

---

### Post by Metaljaz on 2009-06-23
When you left click on the network connections icon on the top right corner of the screen do you see the connection that you wish to connect to or are connected to?
If you right click on the same icon make sure you have wireless enabled. 

Tell us a little more about whats not accessing the internet. Software meaning, firefox and thunderbird?

---

### Post by mr_pitchfork on 2009-06-23
I can see all the available wireless connections when I click on the wireless icon, and wireless is enabled.
 
All software, like Firefox, Thunderbird, Pidgin, Skype, Transmission, Synaptic, none of it is able to send and recieve information across the network.
 
I'm using a different computer connected to the network and sending/getting info through it to post these messages.  It runs under XP.

---

### Post by Metaljaz on 2009-06-24
Lets take a look at your wireless device:
From the terminal window type lspci and list the results here. It should look something like this:
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Also post Ubuntu version and laptop or desktop. Maybe your card is having driver issues with Ubuntu.

---

### Post by mr_pitchfork on 2009-06-24
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
 
Running Jaunty under Sony VAIO NS, probably an old model since it's missing the built-in cam.
 
It seems many people are having issues with their connection after the latest update!  It seems these people are all having issues with the connection they used to update, but that may just be because they only use that connection.

---

### Post by Metaljaz on 2009-06-24
try installing linux-backports-modules-jaunty package by typing the below in a terminal window. Then restart computer and see if its working.

sudo apt-get install linux-backports-modules-jaunty

---

