---
title: "Need help withHelp with Hauppauge WinTV NOVA-T USB2"
date: 2010-03-19
forum: Mythbuntu
---

### Post by sinkyboy2000 on 2010-03-19
I'm pretty new to Ubuntu and Mythbuntu.  I've installed Mythbuntu 9.10 on my Acer Revo and have been trying to get the above USB capture card to work.  I'm in the UK.

From this link, I've established that there's two versions of the card.  I have the older one.  

[http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_USB2](http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_USB2)

I've downloaded both dvb-dibusb-nova-t-1.fw and dvb-usb-nova-t-usb2-02.fw from this page:-

[http://exploit.l-n.org.uk/mythtvdump/](http://exploit.l-n.org.uk/mythtvdump/)

I've put them both in  /lib/firmware/ - The reason for this is that I actually misread the mythtv wiki page and downloaded dvb-usb-nova-t-usb2-02.fw first.  This apperead to get the card working to some extent.  The red light came on and I could run w_scan.  However, I couldn't get any of the TV applications to work.  I tried a few such as totem and me-tv.  

I'm not sure what I've done exactly, but now I can't even get w_scan to run.  When I try, I get this error message:-

```
w_scan version 20091230 (compiled for DVB API 5.0)
using settings for UNITED KINGDOM
DVB aerial
DVB-T GB
frontend_type DVB-T, channellist 6
output format vdr-1.6
Info: using DVB adapter auto detection.
main:2911: FATAL: ***** NO USEABLE DVB CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.
```

This caused me to look at the wiki page again and I noticed I'd put the wrong firmware (according to that page) in to lib/firmware/.  That was why I then put dvb-dibusb-nova-t-1.fw in there as well.  

lsusb produces this:-
```
Bus 001 Device 004: ID 2040:9301 Hauppauge WinTV NOVA-T USB2 (warm)
```

dmesg produces these entries amongst others (I just searched for all containing the text dvb).

```
[   10.326165] dvb-usb: found a 'Hauppauge WinTV-NOVA-T usb2' in warm state.
[   10.326397] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   10.330989] DVB: registering new adapter (Hauppauge WinTV-NOVA-T usb2)
[   10.333277] dvb-usb: MAC address: 00:0d:fe:04:5e:64
[   10.340413] DVB: registering adapter 0 frontend 0 (DiBcom 3000MC/P)...

..................

[   10.960198] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:04.1/usb1/1-5/input/input6
[   10.960313] dvb-usb: schedule remote query interval to 100 msecs.
[   10.960324] dvb-usb: Hauppauge WinTV-NOVA-T usb2 successfully initialized and connected.
[   10.960402] usbcore: registered new interface driver dvb_usb_nova_t_usb2
```

Any help would be greatly appreciated!

---

### Post by sinkyboy2000 on 2010-03-22
Shameless Bump!

Sorry - I know bumping annoys some people, but I'd really like to get an answer to this.  I've searched extensively and haven't been able to work out what's going on.

---

### Post by utar on 2010-03-22
Did you try renaming the newer firmware file as the wiki suggests?  Make sure you do a cold reboot rather then a warm one if you change the firmware files.

What happens when you try and add the card in mythbackend? It may be useful to look at the mythbackend.log.

---

