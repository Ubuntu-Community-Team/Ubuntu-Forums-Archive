---
title: "[SOLVED] Gutsy DVB usb working .....BUT??"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by potnoodles on 2007-10-22
[SOLVED - see post #4] Using megasky 580 usb tv mini 

Tested this device on XP on a triple boot system...then
did a restart and booted to newly upgraded  Ubuntu.Gutsy
Installed Kaffeine.
USB DVB was detected and a scan found lots of channels -but couldnt play them.
Switched to synaptic and installed libxine1 dependencies and the Channels played okay.
Even did a few recording tests which worked.

Grrrrrrrrrreat I thought. this Gutsy version rocks (as much as windows).However...
After a shut-down the device was not detected and there was no option for Digital TV.

After several reinstalls of Kaffeine I was at a loss ....
until I did a restart in XP having used the tuner  and booted Ubuntu .
DTV was back and working in Kaffeine. It seems that the device gets turned on in XP and remains turned on after a restart to Ubuntu.

now I don't propose we all install XP in a dual boot system to get this working...So

Can anyone suggest how to start the USB device in Ubuntu ???

regards,

potnoodles



I

---

### Post by potnoodles on 2007-10-23
Found this thread on the Megasky - some people have this working - others not apparently.

[http://ubuntuforums.org/showthread.php?t=319727](http://ubuntuforums.org/showthread.php?t=319727)

not sure about the solution - I will need to experiment.

regards,

potnoodles

---

### Post by potnoodles on 2007-10-23
UPDATE - MSI Megasky 580 DVB USB

I only need to boot XP and do a restart, booting to ubuntu and kaffeine digital tv works.

There is no need to open the DVB software in XP. the device must become active when XP boots and remain active until a power down occurs such that when ubuntu boots by default after a restart the already activated device is ready to use and works perfectly using kaffeine.

Kaffeine recognises the device as "DVB device 0:0" 
and says the hardware is a "Zarlink MT352 DVB-T" and autoscan works as well.

The advice in the Megasky thread (link in previous post)  seems to be outdated, so I am still looking for help in getting ubuntu to initialise the device.

Any advice welcome

potnoodles

---

### Post by potnoodles on 2007-10-25
Followed advice in this thread(for a different usb dvb device)

[http://ubuntuforums.org/showthread.php?t=533528&highlight=dvb+usb](http://ubuntuforums.org/showthread.php?t=533528&highlight=dvb+usb)


Downloaded this file
[http://linuxtv.org/~mkrufky/firmware/dvb-usb-megasky-02.fw](http://linuxtv.org/~mkrufky/firmware/dvb-usb-megasky-02.fw)

and copied it using

sudo cp  dvb-usb-megasky-02.fw /lib/firmware/2.6.22-14-generic/dvb-usb-megasky-02.fw



 dmesg


6316.765649] dvb-usb: found a 'MSI Mega Sky 580 DVB-T USB2.0' in cold state, will try to load a firmware
[ 6316.769558] dvb-usb: downloading firmware from file 'dvb-usb-megasky-02.fw'
[ 6317.196376] usb 2-8: USB disconnect, address 4
[ 6317.471154] usb 2-8: new high speed USB device using ehci_hcd and address 5
[ 6317.610147] usb 2-8: configuration #1 chosen from 1 choice
[ 6317.610222] dvb-usb: found a 'MSI Mega Sky 580 DVB-T USB2.0' in warm state.
[ 6317.610245] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 6317.610327] DVB: registering new adapter (MSI Mega Sky 580 DVB-T USB2.0).
[ 6317.701213] DVB: registering frontend 0 (Zarlink MT352 DVB-T)...
[ 6317.716795] Quantek QT1010 successfully identified.
[ 6317.716849] input: IR-receiver inside an USB DVB receiver as /class/input/input6
[ 6317.716872] dvb-usb: schedule remote query interval to 100 msecs.
[ 6317.716876] dvb-usb: MSI Mega Sky 580 DVB-T USB2.0 successfully initialized and connected



Started kaffeine and the tuner is workind

RESULT!!!

regards,

POTNOODLES
.

---

### Post by brainstuff on 2008-04-24
just thought I'd pop by to say w00t, this works for Ubuntu Hardy Heron 8.04 too, getting Kaffeine through Synaptic with its dependencies for Gnome. My old megasky has been sat in a drawer ever since I moved from XP to Vista64 (no driver support at all). For the record, it's got to be done in the order stated - unplug the damn thing until you've copied the .fw over, then plug it in and DMESG - whammo! Lovely.

---

### Post by potnoodles on 2008-04-26
> **brainstuff said:**
> just thought I'd pop by to say w00t, this works for Ubuntu Hardy Heron 8.04 too, getting Kaffeine through Synaptic with its dependencies for Gnome. My old megasky has been sat in a drawer ever since I moved from XP to Vista64 (no driver support at all). For the record, it's got to be done in the order stated - unplug the damn thing until you've copied the .fw over, then plug it in and DMESG - whammo! Lovely.

Ive got this working on a new 8.04 64 bit fresh install.

Ironically I cant get it to work on 32bit 8.04 - a managed update from Gutsy (where it worked perfectly)
more here
[http://ubuntuforums.org/showthread.php?t=768751](http://ubuntuforums.org/showthread.php?t=768751)

regards,
potnoodles

---

