---
title: "'Failed to Open Card'  NOVA-500"
date: 2012-02-15
forum: Mythbuntu
---

### Post by rbeer on 2012-02-15
I recently switched PCI cards to a NOVA-500 as I heard it had better support in Linux. Unfortunately in the mythtv setup it is listing as "failed to open card" and "could not get info for card".

I'm not sure if it's a cause or if it's normal but I can only run scan from the terminal with sudo:
```

rmbeer@mythtv:/usr/share/dvb/dvb-t$ scan uk-Hannington > ~/.tzap/channels.conf
scanning uk-Hannington
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2273: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 13 Permission denied

```

```

rmbeer@mythtv:/usr/share/dvb/dvb-t$ sudo scan uk-Hannington > ~/.tzap/channels.conf
[sudo] password for rmbeer: 
scanning uk-Hannington
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 706000000 0 3 9 1 0 0 0
initial transponder 650167000 0 2 9 3 0 0 0
initial transponder 626167000 0 2 9 3 0 0 0
initial transponder 674167000 0 3 9 1 0 0 0
...

```

Card seems to load ok:
```

rmbeer@mythtv:/usr/share/dvb/dvb-t$ dmesg | grep dvb
[   12.777896] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
[   12.777901] usb 2-1: firmware: requesting dvb-usb-dib0700-1.20.fw
[   12.812524] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   13.524455] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
[   13.524495] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.987581] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   14.384663] dvb-usb: schedule remote query interval to 50 msecs.
[   14.384668] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
[   14.384792] usbcore: registered new interface driver dvb_usb_dib0700

```

I can't find other people with a similar problem and most say the card works fine so suspect it probably has something to do with changing the cards. Is there a setting or something that might be messing this up? I have tried cold reboots including deleting all the tuners.

---

### Post by wyliecoyoteuk on 2012-02-15
It looks like a permissions problem, which would explain it requiring sudo.
In Mythbackend, is the card showing as a Dibcom 3000?
You may have a "diversity" model does it have twin antenna sockets?



My dmesg looks like this:
```
dmesg |grep dvb
[   12.687945] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   13.044072] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   13.820252] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   13.820340] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   14.418693] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   15.004693] dvb-usb: schedule remote query interval to 50 msecs.
[   15.004698] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   15.005327] usbcore: registered new interface driver dvb_usb_dib0700
lee@media1:~$ 


```

---

### Post by wyliecoyoteuk on 2012-02-15
Looks like this issue:

NOTE:if you get a "failed to open the card" error when you select the Scan For Channels button you're probably hitting the same issue I had. For some reason the tuner card is installed with the wrong permissions. To solve this problem you need to run the MythTV backend setup as root from a Terminal Session within gnome (Applications -> Accessories) by typing:

sudo mythtv-setup

and then go back into the Input Connections screen once more and try again.

[http://www.havetheknowhow.com/Install-the-software/MythTV-no-channels-found.html](http://www.havetheknowhow.com/Install-the-software/MythTV-no-channels-found.html)

---

### Post by rbeer on 2012-02-16
Thank you both. I have been sent a NOVA-TD-500 (diversity model) when I did order a NOVA-T-500 from amazon but from what I read on LinuxTV this should work out the box anyway (although the extra cabling and requirement for a splitter is annoying).

I ran the mythbackend with sudo and managed to run the channel scan successfully. Unfortunately running mythfrontend on my remote machine just shows partial lock for the channels and doesn't work for others. I will have to play around when I get home tonight. Not sure yet if the backend is recording correctly. I will try the import channels.conf method to see if that fixes things.

Not sure how the permissions got messed up. Is it as simple to resolve as using CHMOD on /DEV/DVB?

---

### Post by wyliecoyoteuk on 2012-02-16
You might need to enable the LNAs
see
[http://wyliecoyoteuk.wordpress.com/mythtv/](http://wyliecoyoteuk.wordpress.com/mythtv/)

---

