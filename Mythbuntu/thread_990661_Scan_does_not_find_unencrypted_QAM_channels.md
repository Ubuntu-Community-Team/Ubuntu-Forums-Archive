---
title: "Scan does not find unencrypted QAM channels"
date: 2008-11-22
forum: Mythbuntu
---

### Post by The Odometer on 2008-11-22
I just installed a Hauppauge HVR-1600 dual tuner into my Mythbox. This tuner is capable of playing ClearQAM channels. My cable provider has begun to transmit all of their basic cable channels via QAM. I have the tuner working (at least the analog side) by using the instructions posted on here.

Here's the problem, when I go to scan for channels, I only seem to get encrypted channels. These channels are in the 50's as it scans. The unencrypted QAM channels are in the 20's and 30's (their frequencies). I do get a few unencrypted channels further up that I suspect are HD channels. However, I've been unable to tune onto them to see so.

I've also used DVB-utils to see that my computer is able to scan channels. I ended up getting over 180 channels using DVB-utils, so I know that there is something there. Any thoughts? I'm totally stumped...

Please help! (My wife would really appreciate it!)

I know I'm not giving a lot of information out--its late and been a long day. Please just ask what you need and I'll be happy to give it to you!

---

### Post by ian dobson on 2008-11-23
Hi,

Could you try installing w_scan (I think it's in the dvb-tools package), and try scanning for channels with that.

w_scan is a command line channel scanner that for me works alot better than the MythTV builtin scanner.

Edit: It doesn't look as if it's included in the ubuntu pakages. you'll need to compile it yourself. Have a look here [http://edafe.org/vdr/w_scan/](http://edafe.org/vdr/w_scan/)
Regards
Ian Dobson

---

