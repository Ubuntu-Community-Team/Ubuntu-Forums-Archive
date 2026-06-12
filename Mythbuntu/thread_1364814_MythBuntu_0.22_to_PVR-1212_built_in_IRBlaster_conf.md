---
title: "MythBuntu 0.22 to PVR-1212 built in IRBlaster configuration help needed"
date: 2009-12-26
forum: Mythbuntu
---

### Post by Jumping_jackas on 2009-12-26
**MythBuntu 0.22 to PVR-1212 built in IRBlaster configuration help needed** 			
 			 			 		   		 		 		My backend is a SFF HP DX5150 with 9.10 Mythbuntu and a PVR-1212 HDPVR receiving component signals from a Motorola 6200 STB. The frontend is a SFF HP DX5150 with 9.10 Mythbuntu.

_**I can not figure out how to change channels**_ USING THE IRBlaster. 

I do not have firewire so I need to use the IRBlaster that is built into the PVR-1212 to send IR remote control messages to my Motorola 6200 set top box. I can find lots of help setting this feature up on the PVR-150 internal card but only comments saying that the PVR-1212 IRBlaster works fine on their systems. 

Thanks in advance

Jeff

---

### Post by oliver.greg@gmail.com on 2009-12-27
I too just got a 1212, and am in the process of getting the IR receiver/blaster to work.

There are some kernel changes that are not in Ubuntu (hdpvr module changes and lirc module changes)..

They have to be compiled in manually for it to work.  If you search for Jared Wilson and hd-pvr lirc, there are email list threads about it with directions on where to pull the code from git and compile it.

You have to roll your own kernel currently.  I just downloaded the latest 2.6.33 from the mainline ppa and it is still not in there..  In fact, Jared says he has yet to even push the updates out to the respective maintainers for inclusion into the kernel..

I'll post my results as soon as I get some time to go through it all..

---

### Post by oliver.greg@gmail.com on 2010-01-01
Well, after I had to wait to get more ram for my video card, I decided that it is just not worth my time to get the lirc going, so I am just going to spend another $20 and use a USB receiver/blaster and be done with it :)

---

### Post by Jumping_jackas on 2010-01-15
i took a break during the holidays from all MythTV work on my system. Did the USB blaster solve your problem? if so can you post for me what you got and how you made it work?

It is a real pain in the @#$ to walk to the backend (equipment room in the garage) just to change the channel on the STB


Jeff

---

### Post by oliver.greg@gmail.com on 2010-01-16
I ended up buying this:

[http://www.amazon.com/gp/product/B000W5GK5C/ref=ox_ya_oh_product](http://www.amazon.com/gp/product/B000W5GK5C/ref=ox_ya_oh_product)

The receiver/blaster both work perfect on it.  I was a bit dismayed that there is no "generic mceusb" configuration available in the control-centre, and I have another post to see if there is a remote/blaster combo to select that will enable it.

There are thousands of examples for mceusb remotes online though.  The first one I followed just worked.  

The remote itself is kind of cheap feeling and the button presses do not always register on the receiver.  I am using my Harmony programmable remote though (I just needed the receiver/blaster), and it works great with the receiver.  If you are planning on using the remote, I would probably spend an extra few more dollars and get a better one.  For just the receiver/blaster it works well though.

BTW:  Here's another post on how to make the PVR1212 blaster work with minimal effort (it just will not survive upgrades, etc...)

[http://www.mythtv.org/wiki/Hauppauge_HD-PVR#Steps_to_Enable_IR_Transmitter](http://www.mythtv.org/wiki/Hauppauge_HD-PVR#Steps_to_Enable_IR_Transmitter)

-Greg

---

