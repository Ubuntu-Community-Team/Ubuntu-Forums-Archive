---
title: "Cable Box IR Control Troubles"
date: 2010-03-16
forum: Mythbuntu
---

### Post by grygub on 2010-03-16
I am running mythbuntu 9.1. I have the vista version of the mce usb reciever/transmitter. The receiver worked out of the box after setup and it seems like the transmitter is close. The transmitter section of my infaraed setup is set for 

"microsoft windows media center v2 (usb): scientific atlanta cable box"

i have a scientific atlanta explorer 8300hdc. my lircd.conf is including an automatically generated config file for the explorer 8000 (sae8000).

when running irw in a terminal and using the remote for my cable box i see

grygub@htpc:~$ irw
0000000000377111 00 ch+ SAE8000

using irsend
grygub@htpc:~$ irsend send_once sae8000 ch+

i see the blaster flash but no response from the cable box

To verify the blaster location i set it up in windows media center and it changes the channel just fine. i have also verified that the cable box config file has the frequency set to 56000

any help would be appreciated

---

### Post by scottcrawford on 2010-03-17
I've got the same problem. I've got an IR02BK MCE receiver/transmitter. The receiver worked great out of the box. The transmitter blinks when I send a command, but my satellite box doesn't respond. I've also tried using the blaster on my DVD player just to test it out - no luck. I've recorded my remote commands (raw and regular) and I've downloaded config files. No luck either way.

---

### Post by azmyth on 2010-03-17
I was going to say the frequency wasn't set in the lircd.conf file but it sounds like you did this. The only thing it could be is you don't have the proper codes or placement of the blaster. You could write a very quick script to loop the irsend command so you can move the blaster around the front of the STB eye. I used a flashlight to find the location on the STB and I tacked mine slightly to the left of the eye. I'd also use irrecord to make sure your remote has the proper commands.

With all this said, I have a bit of a reliability issue on changing channels. I'm trying a different frequency.

---

