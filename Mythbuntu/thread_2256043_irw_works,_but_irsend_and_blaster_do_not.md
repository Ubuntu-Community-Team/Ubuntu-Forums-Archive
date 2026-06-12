---
title: "irw works, but irsend and blaster do not"
date: 2014-12-09
forum: Mythbuntu
---

### Post by kmallick on 2014-12-09
I just upgraded and installed a fresh Mythbuntu 14.04 on a system that worked perfectly with Mythbuntu 9 in the past. I have a genuine mceusb receiver with a transmitter attached to it to change channels on a Motorola DCH3200 cable box. I have configured MCC to handle the remotes and transmitter. Following that, I have gone in and edited the correct configuration files for the remote and transmitter in etc/lirc/hardware.conf. I have also ensured that the correct modules and options are defined in /etc/lirc/lircd.conf. The MCE remote works fine within MythTV. However, the IR blasting is not working and consequently I cannot get MythTV to change channels on my STB. 

As part of testing, when I type irw in terminal and click the remote button, I see the proper key presses showing up in terminal. But typing irsend command does not show any errors, nor does it produce any result when I am within MythTV frontend. For example I get:

$ irsend SEND_ONCE mceusb KEY_UP
$

and the focus on the MythTV menu button does not change. (It changes with the remote just fine).

I have tried irsend SEND_ONCE mceusb -d /dev/lirc KEY_UP, and I get the same result.

I have also tried irrecord and I can record the key presses successfully into a file.

Ultimately I want to test out the irsend command with the blaster to get to the channel change part. For example I want to test:

$irsend SEND_ONCE dch3200 POWER

to see the bug light up and turn off the power to STB. But it doesn't.

I know this exact same setup has worked in the past and I wish I could get it up and running again. Any help with troubleshooting will be highly appreciated.

---

### Post by one30nav on 2014-12-11
Perhaps your lircd is actually lircd1

Try:

irsend --device=/dev/lircd SEND_ONCE mceusb 1 2 3

or

irsend --device=/dev/lircd1 SEND_ONCE mceusb 1 2 3

Also, my previous post for reference: [http://ubuntuforums.org/showthread.php?t=2242413&p=13113049#post13113049](http://ubuntuforums.org/showthread.php?t=2242413&p=13113049#post13113049)

---

### Post by kmallick on 2014-12-11
> **one30nav said:**
> Perhaps your lircd is actually lircd1

Try:

irsend --device=/dev/lircd SEND_ONCE mceusb 1 2 3

or

irsend --device=/dev/lircd1 SEND_ONCE mceusb 1 2 3

Also, my previous post for reference: [http://ubuntuforums.org/showthread.php?t=2242413&p=13113049#post13113049](http://ubuntuforums.org/showthread.php?t=2242413&p=13113049#post13113049)

Thanks for the suggestion. I will try that and report back.

---

### Post by kmallick on 2014-12-11
Unfortunately neither of those options worked.

ls -l /dev/lirc*

shows

/dev/lirc0
/dev/lircd -> /run/lirc/lircd

irsend --device=/dev/lircd SEND_ONCE KEY_UP
from a terminal goes through without any error, but the focus button in myth doesn't change.

irsend --device=/dev/lircd1 SEND_ONCE KEY_UP
gives "irsend : could not connect to socket".

I had forgot to mention that 
irsend LIST "" ""
shows both mceusb and DCH3200.

---

### Post by one30nav on 2014-12-13
You need to isolate the error by getting away from the "KEY-UP" command. If you can successfully change to a known channel, you will at least know that irsend is working.

So, try:

irsend --device=/dev/lircd SEND_ONCE mceusb 1 2 3

and go from there.

---

### Post by neutron68 on 2014-12-20
Trying to understand the question/situation...  
Mythtv menus respond to your IR remote button presses just fine, but your IRSEND commands do not send out via your IRBLASTER device?

---

### Post by kmallick on 2014-12-20
Problem solved! All I did was change the usb port on the back of the mythtv box where the mceusb transceiver plugged in. And now irsend, ir blaster and channel change script all work.

---

