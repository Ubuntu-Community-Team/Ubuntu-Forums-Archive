---
title: "Upgrade to 10.04 lirc problem with USB"
date: 2010-07-04
forum: Mythbuntu
---

### Post by Tim L on 2010-07-04
Just Updated from Ubuntu 09.10 to 10.04 and the USB MCE IR Blaster has stopped working using Microsoft Windows Media Center V2 (usb) : Sky Satellite Receiver with a scrip and an external satellite box.

Before the upgrade everything worked no problem. After upgrade cannot change channels on the Sky Box. The channel will change no problem with the original Sky Remote.

On the front of the satellite box there is a small LED labeled “ir received” when a correct code is received this flashes. The IR blaster has two LED's, one viable and one inferred. When the code is being sent to the LED it flashes as it should but it seems to be sending the incorrect code because the LED on the satellite box does not flash to show it was receiving the code. 

Everything is set up as I have done a number of times before

I have made sure that /usr/local/bin/change-channel-lirc.sh is correct and working using:
1.sudo -u mythtv /usr/local/bin/change-channel-lirc.sh 
2.sudo chmod 755 /usr/local/bin/change-channel-lirc.sh

I have also checked that the “/usr/share/lirc/transmitters/sky/general.conf” file is correct.

I also have tried:
irsend -d /dev/lircd SEND_ONCE sky 1 
/usr/local/bin/change-channel-lirc.sh 01

Both of these send a command to the IR blaster connected to the USB box, but they are not recognised by the Sky Box.

One thought was that the IR transistor was blown. I checked it by using an IR extender and it picks up the IR signal correctly.

 
I have used cat /etc/lirc/hardware.conf and cannot see a problem with the hardware.

I have stopped and started Lirc.

No matter what I try all seems correct – but the “ir received” LED on the Sky box does not flash as it does when using the original Sky Remote Directly.

I think the lirc is sending the incorrect information. I have seen that a number of people have had problems since upgrading. There is a number of suggestions but none seem to fit my situation. I am thinking of going back to Ubuntu 09.10 as I can not find an answer.

Any suggestions?

---

### Post by azmyth on 2010-07-05
I had the same issue with a Scientific Atlanta box. Had to set the proper frequency in the lircd.conf that the blaster accesses. Could also try to build a test lircd.conf for the remote using irrecord to see if the remote codes match. I figure you'd have the same issue with 9.10 that you're not seeing though. Also, could try turning on lircd logging to see if it gives you any hints.

---

### Post by Tim L on 2010-07-07
Solved:

Although I have now been running mythbuntu for about 2 years I consider myself a very newcomer to it and Linux.

When originally setting up the IR Blaster I followed in instructions in:

[https://help.ubuntu.com/community/MythTV_External_Channel_Changer](https://help.ubuntu.com/community/MythTV_External_Channel_Changer)

As part of that I installed the “general.config” in /usr/share/lirc/transmitters/sky/general.conf

I had assumed when upgrading from mythbuntu 9.10 to 10.04 as with previous upgrades that things would stay the same. But of course hardware.conf and lircd.conf changed and no longer pointed to where the “general.conf” file was placed. As a result the incorrect code was being transmitted to the IR Blaster.

To correct the situation:

1.I put the “general.conf” in:   “/usr/share/lirc/extras/transmitters/sky/general.conf”

2.suso nano /etc/lirc/hardware.conf - so it pointed to the “general.conf”:

TRANSMITTER_LIRC_CONF=”/usr/share/lirc/extras/transmitters/sky/general.conf”

3.sudo nano /etc/lirc/lircd.conf - so it pointed to the “general.conf”:

include “usr/share/lirc/extras/transmitters/sky/general.conf”

Such a simple thing took me probably 8 hours to figure out, because the IR Blaster seemed to be working I just did not consider this as the problem!

---

