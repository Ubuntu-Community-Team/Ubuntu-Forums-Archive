---
title: "Installing PCI DVB-T Drivers on Mythbuntu 10.04"
date: 2012-01-28
forum: Mythbuntu
---

### Post by Levo2012 on 2012-01-28
A few months ago my old PC had the BSOD since that day it hasn't been able to do a fresh install of Windows 7 or any of the later versions of Ubuntu other than Ubuntu 10.04.

I therefore wanted to do something with the computer instead of throwing it away so I opted to turn it into a Mythbuntu PC. I downloaded 10.04 version and bought the PEAK DVB-T 221544AGPK Dual Tuner and thought I'd have it as a backend PC sending up through the network to my Apple TV and laptop. I am pretty new to Ubuntu and Linux.

But now that I have installed Mythbuntu I am having problems with the drivers for the card.

I installed the drivers recommended from the in the restricted hardware drivers and although it in Mythbuntu it can see the card, I can't get a signal when I do a search and have tried it plugged into the roof aerial. 

I discovered [http://linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#KWorld](http://linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#KWorld) where it mentions that I can install the drivers for a KWorld card [DVB-T PC160-2T]("http://linuxtv.org/wiki/index.php/KWorld_DVB-T_PC160-2T") I click on the link on the wiki and I just don't know what to do to download or even install the drivers. 

This page [http://linuxtv.org/hg/~anttip/af9015-mxl500x-copy-fw/](http://linuxtv.org/hg/~anttip/af9015-mxl500x-copy-fw/) is a repositories index, but when I click on either of the links down the side (zip, gz, bz2) it basically just reloads the page.

So I am stuck in a loop and am not sure how to go about getting out of it. I hope you can help thanks in advance.

---

### Post by Levo2012 on 2012-01-28
I have come across this [http://www.gossamer-threads.com/lists/mythtv/users/453871](http://www.gossamer-threads.com/lists/mythtv/users/453871)

When I run [FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]'dmesg | grep -i dvb'

I get 

[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]```
levo@levo-desktop:~$ dmesg | grep -i dvb
[   14.281287] dvb-usb: found a 'KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T)' in cold state, will try to load a firmware
[   14.281297] usb 2-1: firmware: requesting dvb-usb-af9015.fw
[   14.354007] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
[   14.463204] dvb-usb: found a 'KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T)' in warm state.
[   14.463264] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   14.463634] DVB: registering new adapter (KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T))
[   15.203969] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...
[   15.521168] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   15.521596] DVB: registering new adapter (KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T))
[   16.237980] af9013: found a 'Afatech AF9013 DVB-T' in warm state.
[   16.251356] DVB: registering adapter 1 frontend 0 (Afatech AF9013 DVB-T)...
[   16.544802] dvb-usb: KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T) successfully initialized and connected.
[   16.555091] usbcore: registered new interface driver dvb_usb_af9015

```

Does this suggest successful installation of the drivers?


[FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]

[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by ecwanet on 2012-01-28
It looks encouraging. 

Have a look in /dev/dvb/ to see if the adapters are in there. If so try using 'scan' to look for channels in a terminal session. 

```
scan /usr/share/dvb/dvb-t/<your transmitter>
```Look in that directory for your local transmitter. They are organised by country and region. Put the file name in place of '<your transmitter>'.

With Mythbuntu, you probably have 'scan', it's in the dvb-apps package (pre-installed I believe). 

If you get some encouraging messages (there could be quite alot), run it again but add

```
| tee channels.conf
```to pipe the output to your user directory. With luck you should get a file of channel information including names, callsigns, frequencies and other transmission settings. You can use this file with the tuning utility, 'tzap', or in mythbackend-setup to scan for channels (copy the file to the .mythtv subdirectory of your userid). If you have 'mplayer', copy the file to the .mplayer subdirectory of your userid and try (using one of your channel names, of course)
```
mplayer dvb://"BBC ONE"
```If the adapters don't appear in dev/dvb you may need some udev rules to create them. I can post what I used if necessary.

Bear in mind that I'm far from being an expert. 
Bon chance.

---

### Post by Levo2012 on 2012-01-28
Thank you very much for your reply. 

It seems everything is working fine right now. I watching TV and recording TV. 

What I need to be able to do now is get the wireless network sorted so that I can stick the box out of the way and send it all to my Apple TV or other front ends.

---

