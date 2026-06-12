---
title: "mythbunu setup - no signal"
date: 2009-10-18
forum: Multimedia Software
---

### Post by B34N on 2009-10-18
I just installed mythbuntu and I'm trying to get it working with my KWorld ATSC PCI-115. I found instructions at [http://www.mythtv.org/wiki/Kworld_ATSC_115](http://www.mythtv.org/wiki/Kworld_ATSC_115) but unfortunately I cannot get past the first step.  My guess is that the instructions are for older versions of mythbuntu.  I'm following the instruction on the Wiki because the card does not receive a signal and I'm confident I'm using the correct input and there is a signal (ran under XP).

My version is 2.6.28-11 and when I run "sudo apt-get install linux-doc-2.6.28" I get the message "Package linux-doc-2.6.28 is not available, but it is referred to by another package." I also tried "sudo apt-get install linux-doc" and that package could not be found. When I look in Synaptic Package Manager under documentation, all of the five listed packages are installed. There is no dvb directory is my "/usr/src/linux-headers-2.6.28-11/Documentation" directory. I do a "locate get_dvb_firmware.gz" and I get nothing back.

Does anyone have any suggestions?

---

### Post by B34N on 2009-10-18
I figured it out.  I didn't have one of the doc repository active.

I was able to get further on the instruction on the wiki.  I installed the docs.  I found "get_dvd_firmware.gz" in "/usr/share/doc/linux-doc-2.6.28/dvb".  I was able to edit it and change the URL and change the file permissions as specified.  However, when  i tried "sudo perl get_dvb_firmware nxt2004" I got the message "This firmware requires the unzip command - see ftp://ftp.info-zip.org/pub/infozip/UnZip.html" and the URL did not work for me.  Is it asking me to unzip one of the other files in the directory?  I have avermedia.txt.gz, cards.txt.gz, ci.txt.gz, faq.txt.gz, README.dvb-usb.gz and README.flexcop.gz in the same directory.  Then the next instruction is to "sudo cp dvb-fe-nxt2004.fw /lib/firmware/[kernel version]/" but my directory structure is different.  Should I be doing "sudo cp dvb-fe-nxt2004.fw /lib/firmware/2.6.28-15-generic/"

Thank you!

---

### Post by B34N on 2009-10-20
All I needed to do was install unzip....gzip was not enough.

---

### Post by B34N on 2009-11-06
Just in case someone searches this problem, here is how I got my ATSC to work with clear QAM:
I started over again (and again) with a fresh Mythbuntu 9.10

I used synaptic package manager to install linux-doc and unzip.

```
cd /usr/share/doc/linux-doc/dvb
sudo gzip -d get_dvb_firmware.gz
sudo chmod +x get_dvb_firmware
sudo perl get_dvb_firmware nxt2004
sudo cp dvb-fe-nxt2004.fw /lib/firmware
```

I edited /etc/modules to add both "saa7134" and "saa7134-dvb".  the only thing that was in there was "lp".  I don't know if this step was necessary but I did it anyway. (thoughts?)

Since I am only using the digital input (bottom on ATSC115 card) I setup only the device "DVB DTV capture card (v3.x)"

That's it and now everthing seems to be working.

---

