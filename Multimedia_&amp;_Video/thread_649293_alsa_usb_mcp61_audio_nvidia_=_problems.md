---
title: "alsa usb mcp61 audio nvidia = problems ?"
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by dany3l on 2007-12-24
After trying with many diferent combinations of sound cards/motherboards  ,audigy  , generics , onboard ,etc...by miracle i found a crappy  external usb card that was working 100% in an old Pentium 3 with 256mbRam with 5ms latency (i couldnt believe it) , but the same , and believe me the same same configuration , and even the same hard drive with the same ubuntu and with another fresh ubuntu instalation DO NOT WORK AT ALL ..
i TRY DIFERENT kernels even realtime ones for use with jackd 
....and the only time i had a working combnination was NOT with fancy hardware.  ..and it was not mine .
SO trying to reproduce the experiment i keep the sound card and the hard drive with  the working installation and put it on my home pc (Sempron +3000/Nvidia MCP61 )but guess what..
It doesnt work!
So i'm guessing the combination of sound card + chipset +alsa +jack , etc , etc is essential .
The same "sound card/software"  (external usb ) in one systems works flawlessly and in the other not at all ,but if the software is the same (last alsa,last jack, same kernel ) the difference must be in what is in the middle ..so , the chipset and the usb..
and..so  what ? ..
NOTHING ! ,because there is no "drivers" for that matters..i'm I right? is everything handle by the kernel ..! 

the situation : 
HARDWARE :
OLD Pentium3 (dual processor) intel chipset 256MB ram bus + crappy "USB PCI VIA based " + crappy external "usb audio card"
SOFTWARE :
Ubuntu basic command line system + XFCE4 + realtime kernel + Jack and friends debs , etc, etc

RESULTS = 5ms latency 
AWESOME!!

#BUT , same software or same hard drive or other installation with standard kernel same packages  in a NVIDIA based motherboard with 1.5 GB RAM ---> and the initialization of the same usb audio card fail ..
alsa complain about no such device
USB is generally speaking working , 
I also try disabling EVRYTHING onboard except usb and VGA (nvidia) trying to free up IRQ

#progress . 
alsamixer: function snd_ctl_open failed for default: No such device

after trying user permision and triple checking /dev/snd/ and all that jazz , that was already ok. and after not finding alsaconf, and after finding asoundconf (not working) .
solved with asoundconf-gtk 
#BUT -> Jack refuse to connect , i will reboot and see what happens

#back_to_CERO
jack complains = ALSA lib confmisc.c:769:(parse_card) cannot find card ''
but alsamixer can see the card 
any clues ?

AFTER REBOOTINGS AND REBOOTINGS and google 
 asoundconf set-default-card 1
jAck is working !!!
time to check

---

