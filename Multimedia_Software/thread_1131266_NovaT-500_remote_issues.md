---
title: "NovaT-500 remote issues"
date: 2009-04-20
forum: Multimedia Software
---

### Post by jonathanhaddock on 2009-04-20
Hi All,

I'm running Ubuntu 8.10 and have installed Mythbuntu to it which seems to be working fine, mostly.

Unfortunately, the remote control doesn't seem to do anything.  I've followed various links, guides, instructions and I swear they're all useless!

From [http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI#Quick_test]("http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI#Quick_test") I see that running:
```
dmesg | grep -i dvb
```
should include a line like: 
```
input: IR-receiver inside an USB DVB receiver as /class/input/input4
```

Yet when I run the same command:
```

root@pvr:/home/fact# dmesg | grep -i dvb
[    9.900054] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
[    9.900060] firmware: requesting dvb-usb-dib0700-1.10.fw
[   10.773340] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[   11.480046] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
[   11.480381] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   11.480489] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   11.712976] DVB: registering frontend 0 (DiBcom 7000PC)...
[   11.897010] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   11.897184] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   12.049030] DVB: registering frontend 1 (DiBcom 7000PC)...
[   12.233440] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
[   12.233730] usbcore: registered new interface driver dvb_usb_dib0700

```

Which suggests to me that my IR input device isn't being found by the system.

According to the box, I'm using a **WinTV-NOVA-T500 model 289 SL-289-v2.1-UK**.  The 289 model is reported to work at version 2.0.

Any advice regarding this problem would be appreciated.  I've tried information from:
* [http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6440182]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6440182")
* [http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI]("http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI")

Amongst other places and now I'm out of ideas.

```

root@pvr:/home/fact# uname -ar
Linux pvr 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux

```

Thanks in advance,

Jonathan

---

