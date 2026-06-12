---
title: "old Toshiba laptop audio setup problems in Xubuntu"
date: 2007-01-06
forum: Multimedia &amp; Video
---

### Post by cookevillain on 2007-01-06
Hi everybody!

I know this information is out there but I have been looking for several hours now and just cannot take this anymore. I have an old Toshiba Satellite 2530 CDS laptop. I put Xubuntu 6.10 on it (because that was the only thing that fit) and am trying to bring it to the level of functionality it had under XP. After fixing the X problems, I am ready to tackle the audio setup. Here is the problem. I had an old version of Ubuntu on it (5.10) before I finally gave up on the wireless and switched to XP and the audio and irda worked fine. I spent several hours setting it up then and all I have is a modules.conf file left from that era. Basically I need to reproduce this in the current init scheme:

alias usb-controller usb-ohci
alias sound-slot-0 opl3sa2
post-install sound-slot-0 /bin/aumix-minimal -f /etc/.aumixrc -L >/dev/null 2>&1 || :
pre-remove sound-slot-0 /bin/aumix-minimal -f /etc/.aumixrc -S >/dev/null 2>&1 || :
options sound dmabuf=1
alias synth0 opl3
options opl3 io=0x388
options opl3sa2 mss_io=0x530 irq=5 dma=1 dma2=1 mpu_io=0x330 io=0x370
alias irda0 toshoboe
#options toshoboe max_baud=9600
alias char-major-161 ircomm-tty
alias tty-ldisk-11 irtty
alias char-major-10-187 irnet
alias char-major-10-188 irnet

alias eth0 toshoboe

 As far as I remember, the options for opl3* drivers mattered the most, as well as pre-install/post-install lines.
So far I have done the following: I removed opl3* lines from the blacklist-oss file and stuck the options lines into the options file. I can sort of play sound files but the sound is interrupted several times (an irq problem?) and some portions do not play at all. How do I fix this? Any ideas. And one more stupid question: how do I restart alsa without rebooting (sorry, I am used to Fedora with its `system' command)? 

Thanks in advance

---

