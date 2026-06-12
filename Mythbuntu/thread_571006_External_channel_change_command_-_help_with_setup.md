---
title: "External channel change command - help with setup"
date: 2007-10-08
forum: Mythbuntu
---

### Post by I Use Dial on 2007-10-08
I'm new to Linux/Ubuntu/MythTV and I'm setting up a MythTV backend server that will only be a backend server.

In the setup of MythTV it states to enter External channel change command, but I'm not sure what to put here.

The description states this command will be run to change the channel for inputs which have an external tuner device.  I have DirecTV so this sounds like something I need for my Hauppage PVR-150 IR Blaster.

I have found this explanation for Lirc Feisty, but it doesn't make things very clear to me on what I enter into this field or exactly what I need to do to get things to work within Mythbuntu.
[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

Thank you!

---

### Post by rusty0101 on 2007-10-09
As I understand it there should be a program or script you can 'send' infrared commands to the DirecTV receiver. 'irsend' looks like one possibility. In general you will need to configure this line something like 'irsend DirecTV $S [NUM]'

To build this configuration, you can use something like 'irsend LIST "" ""' to get a list of possible remote controls to use. (this is also listed in lircd from what I read in the man page) then 'irsend LIST REMOTE ""' to list the possible codes for that remote. Replace REMOTE with a remote selected from the 'irsend LIST "" ""' 

There's a lot of testing that you could end up going through. Mark over at blushingpenguin.com has posted abraindupm that might work out for you. Mythtv does not need to have the patches applied to lirc so far as I know, but I could be wrong. His blog entry is at [http://www.blushingpenguin.com/mark/blog/?p=24]("http://www.blushingpenguin.com/mark/blog/?p=24")

Good luck.

---

### Post by sica on 2007-11-12
This is what I have. 
I picked it up along the way..

Make a file /usr/local/bin/change_chan.sh

#!/bin/sh
REMOTE_NAME=TWC_UR4-P360
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend --device=/dev/lircd1 SEND_ONCE $REMOTE_NAME $digit
sleep 0.4 # note, you may have to tweak the interdigit delay up a bit
done
irsend --device=/dev/lircd1 SEND_ONCE $REMOTE_NAME SELECT


you will have to change remote_name to your remote.
SELECT may be different for you too. could be ENTER.
make sure to make it executable!

then all you have to enter in the external channel chage box is change_chan.sh

---

