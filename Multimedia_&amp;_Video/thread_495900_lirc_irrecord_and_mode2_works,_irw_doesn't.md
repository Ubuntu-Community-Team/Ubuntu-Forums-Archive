---
title: "lirc: irrecord and mode2 works, irw doesn't"
date: 2007-07-08
forum: Multimedia &amp; Video
---

### Post by noof on 2007-07-08
Hey, I've been trying to get lirc to work for some time now and I've almost succeeded. I've followed the guide at [https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty), and after some struggling with /dev/lirc0, mode2 outputs things when I press buttons on the remote and I've configured a remote using irrecord. I copied the config file to "/etc/lirc/lircd.conf" and restarted lircd. But when I run irw it doesn't output anything no matter how much I press the remote control buttons. Any ideas? I'm using the serial driver with feisty.

---

### Post by eeanm on 2007-08-26
I have the same problem, using an ATI Remote Wonder II. irw doesn't work, but mode2 does. My lircd.conf does have my remote control listed. 

But it seems like I'm missing something... lircd.conf can have multiple cards in it (though mine only has one) how is irw supposed to know which to use?

---

### Post by Mohonri on 2008-03-30
Thread necromancy here, but OP didn't get a reply, and I'm having the same issue (albeit with a different remote, and on Gutsy).

Everything up to this point went fine.  I recorded the buttons with irrecord, and copied the .conf file to /etc/lirc/lircd.conf and /etc/lircd.conf.  The button recording ended up using raw mode, which is fine with me.   I restarted lirc, and mode2 shows everything the way it should be, but irw doesn't show anything.

I checked dmesg and lsmod and even /var/log/daemon.log (where lircd does its logging), and everything appears to be normal.  My first inclination is to think that somehow lircd.conf is wrong, or lirc is looking at the wrong conf file.  So far, though, I see little to no difference between the output of mode2 and the contents of lircd.conf--all the pulses are about 500, and all the spaces are either around 1000 or 2000.

Any lirc gurus around here?

EDIT:  I was able to solve the problem--it looks like I was just too far away from the irreceiver when I ran irrecord.  This makes sense, because this same remote has been variously identified by irrecord as RC-5, RC-6, pulse encoding, and just plain raw, so I should have clued into the inconsistencies.  I just did irrecord once more, this time with the lights out, and everything appears to be kosher.

---

