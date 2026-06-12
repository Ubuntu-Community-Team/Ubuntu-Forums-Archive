---
title: "Mythtv mceusb frustration"
date: 2008-11-18
forum: Multimedia Software
---

### Post by beerguzzler on 2008-11-18
Wonder if anyone can give me some help with trying to get my remote working in Mythtv

I was using Hardy 8.04 and followed these [mythtv]("http://www.mythtv.org/wiki/index.php/MCE_Remote") [ubuntu specific]("http://www.mythtv.org/wiki/index.php/Ubuntu_lirc_install")tutorials and could get my remote working in irw but not in Mythtv.

I was thinking that perhaps there was a conflict with the 2 tutorials so decided on doing a fresh Intrepid install as the page says:

"Ubuntu 8.10

Ubuntu 8.10 ("Intrepid Ibex") has out of the box kernel modules for the MCE remotes. All that is required is to install lirc (as noted above), and follow the prompts." 

So with Intrepid installed, I ran "sudo apt-get install lirc" followed by "sudo /etc/init.d/lirc restart" as per the instructions. Again, my remote works in irw but not in Mythtv

000000037ff07be9 00 Play mceusb
000000037ff07be6 00 Stop mceusb
000000037ff07beb 00 Forward mceusb
000000037ff07bea 00 Rewind mceusb
000000037ff07be5 00 Skip mceusb
000000037ff07be5 01 Skip mceusb
000000037ff07be4 00 Replay mceusb
000000037ff07bde 00 Right mceusb
000000037ff07bdf 00 Left mceusb
000000037ff07be0 00 Down mceusb
000000037ff07be1 00 Up mceusb
000000037ff07bed 00 ChanUp mceusb
000000037ff07bed 01 ChanUp mceusb
000000037ff07bec 00 ChanDown mceusb
000000037ff07bee 00 VolDown mceusb
000000037ff07bef 00 VolUp mceusb
000000037ff07bf2 00 Home mceusb
000000037ff07bf1 00 Mute mceusb

lsusb shows "Bus 003 Device 002: ID 0471:0815 Philips eHome Infrared Receiver" and the back states it's an RC6 ir.

Is there no need in 8.10 to create hardware.conf, lircrc files and then give mythtv links to the lircrc as per earlier editions of Ubuntu? 

Thanks in advance for any help and tips offered.

---

