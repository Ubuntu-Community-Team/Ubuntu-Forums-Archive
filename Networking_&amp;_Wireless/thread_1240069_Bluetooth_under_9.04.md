---
title: "Bluetooth under 9.04"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by user256 on 2009-08-14
Firstly let me just say i've been using some form of debian/ubuntu as my main os for nearly 2 years, and 'm sorry if this has been answered before, i hate starting threads and i can almost always avoid it by searching carefully. Unfortunately i'm making no progress here despite vast quantities of free time (i broke my foot and can't work). So after over a week of no bluetooth i'm calling uncle.

I have a usb thumbnail dongle shows up as  
Bus 007 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode).

However i can't connect to either my phone or my headset (ihifi handsfree kit) More accurately i can't find either, and yes both are set to visible, my headset 180 seconds, my phone 120 seconds. Few outputs i found in my searching:

user256@01:/var/lib/bluetooth$ hcitool dev
Devices:
        hci0    00:1F:81:00:02:50
user256@01:/var/lib/bluetooth$ hidd --search
Searching ...
ser256@01:/var/lib/bluetooth$ hcitool scan
Scanning ...
Inquiry failed: Connection timed out
sudo hciconfig hci0 inqmode 0
Can't set inquiry mode on hci0: Connection timed out (110)
user256@01:/var/lib/bluetooth$ sudo hciconfig hci0 reset
Can't init device hci0: Connection timed out (110)

I bought the dongle on ebay because the seller listed it as supported by ubuntu, which it doesn't seem to be, i tried blueman but i'm having no luck there. Can anyone help me get this working.

At very least can someone direct me to the list of ubuntu supported dongles, i can't seem to find now - if anyone has that handy i'm happy enough to buy another. My girlfriends in the US for a couple of months and it's costing a fortune to call her so i'd like to get my headset working as i have no landline! If anyone can even recommend a dongle that works out of the box in 9.04 that'd be amazing, i'm not too worried about the price, it'll be slight by comparison to the phone costs!

---

### Post by user256 on 2009-08-17
bump. anyone?

---

### Post by Merovius on 2009-08-17
I use the same dongle on Ubuntu 9.04 , so I know it works. Gave me a hastle to get my mouse set up but eventually it worked. I found it needs to be on before I boot and be shut off after shutting down. Not sure about headsets though..

---

### Post by Horomancer on 2009-08-18
I'm having my own headaches with bluetooth and Ubuntu. I'm trying to get a headset to work with very little luck.
One thing that helped was setting my headset into pairing mode then running

hcitool scan

in command console. This seemed to tbe the only way for me to get the headset and Ubuntu to see each other.
good luck. loooks like we'll both need it to get Ubuntu working with bluetooth items

---

### Post by user256 on 2009-08-19
Thanks for replying guys! Firstly Merovius do you mean pairing, the device you wish to pair with mus be on before you boot? I've had no luck with that myself.

Horomancer, have you changed your system at all? I've actually done a clean install so as to start again with bluetooth. I'm still having no luck with hcitool scan

user256@01:~/Desktop/Downloads$ hcitool scan
Scanning ...
Inquiry failed: Connection timed out

I've bought another usb dongle i'm hoping will work, i'll update my progress when it arrives.

---

### Post by Horomancer on 2009-08-19
Hmmmm... I don't get a time out message when i use hcitool scan. Either I pick up the headset, or i go back to the command line with no message if the headset is not in pairing mode. I've gone through sooooo many walkthroughs that i have no clue what the hell I've done to my computer by now.
I have a thread going on this board somewhere following my own troubles in case it gives you any help-
[http://ubuntuforums.org/showthread.php?t=1243480](http://ubuntuforums.org/showthread.php?t=1243480)
i'm thinking of starting a new thread in Beginner Talk to see if anyone there can help since i'm getting little feed back aswell
good luck

---

### Post by Merovius on 2009-08-22
Sorry so slow. I mean the mouse has to be on before I boot and I shut it off after I shut down the laptop. (It has a power button on the bottom.) Just turning it on after the laptop starts gets me no where fast. Not sure why.

Forgot to  mention I also do not get a time out with the hcitool scan command.

---

### Post by chrisme52 on 2009-08-24
My usb bluetooth is listed the same as yours and i've had no problems.
My mouse reconnects at boot and i can tranfer files etc.

I am using 64bit 9.04(clean install) was yours an upgrade or a new install?

---

### Post by The Foz on 2009-08-24
It might be an idea to check that you have all the relevant updates to your system. When I first installed 9.04 (as a new install in a new partition), bluetooth didn't work at all. After various software updates, it started working recently.

Another thing to try is to disconnect (wait 10 seconds) and then reconnect the bluetooth adapter. I have found that, if it is left on for a long period (weeks, not hours), it simply stops working. Rebooting the PC will not fix this, as the USB ports are not usually powered down on reboot.

Just to depress you, I bought a bluetooth headset specifically for use with my Ubuntu PC, and never got it to work. There is a very old post in the forums about this. The headset works fine with my mobile phone. The bluetooth also works fine to connect my PC with my mobile phone. Every attempt to get the headset working with the PC failed. I did all the pairing, and would see the message that the device was connected, but it would never work; I think what happened is that the connection timed out too quickly. You cannot trust the time it takes for the bluetooth manager to tell you the device has disconnected, as that typically includes a retry period.

My personal recommendation would be to find someone who has a bluetooth headset which works with Ubuntu, and then borrow it to see if it works with your PC. It might also be worth seeing if that person can get your headset working with their PC. If their headset works with your PC, buy one exactly the same.

---

### Post by user256 on 2009-08-24
Hey guys, thanks to everyone for your support, the problem must have been with the dongle my belkin arrived this morning and out the box autodetects both my headset and my phone. I've not tried setting either up as i'm pretty busy but just thought i'd advise!

All hail ubuntu!

---

