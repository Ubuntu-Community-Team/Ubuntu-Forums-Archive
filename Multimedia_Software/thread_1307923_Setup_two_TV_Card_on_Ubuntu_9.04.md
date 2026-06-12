---
title: "Setup two TV Card on Ubuntu 9.04"
date: 2009-10-31
forum: Multimedia Software
---

### Post by rc_chc_hk on 2009-10-31
I've two MSI TV@anywhere plus TV capture card(saa7134 chipset) installed on Ubuntu 9.04 and would like to use vlc to broadcast the video form those two tv card
 
I'd setup a config file saa7134.conf located at /etc/modprobe
 
alias char-major-81 videodev
alias char-major-81-1 saa7134
options saa7134 card=17
 
Ubuntu detected those two tv card existed on the system but only /dev/video0 is working properly, /dev/video1 is not working at all
 
Can anyone give me a help, thx a lots

---

### Post by rc_chc_hk on 2009-11-02
Oh, finally I found the solutions from VLC API Specification [http://v4l2spec.bytesex.org/spec/c174.htm](http://v4l2spec.bytesex.org/spec/c174.htm)

The config file saa7134.conf need a little bit change as below
 
alias char-major-81 videodev
 alias char-major-81-0 saa7134 
alias char-major-81-1 saa7134
options saa7134 card=17,17
 
Now both TV capture card works fine

---

