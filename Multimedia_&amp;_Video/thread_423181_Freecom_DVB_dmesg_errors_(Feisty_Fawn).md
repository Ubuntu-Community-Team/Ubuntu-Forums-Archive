---
title: "Freecom DVB dmesg errors (Feisty Fawn)"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by Simon Richards on 2007-04-25
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=183297&amp;page=7&amp;highlight=Freecom+USB+DVB](http://ubuntuforums.org/showthread.php?t=183297&amp;page=7&amp;highlight=Freecom+USB+DVB) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I know that the topic of the Freecom USB DVB stick has had a great airing on this forum and others. I believe that I have been through all the relevant posts and have come to a dead end.

I get the following entries in dmesg:
dvb_usb_dtt200u: disagrees about version of symbol dvb_usb_nec_rc
_key_to_event
[   33.372620] dvb_usb_dtt200u: Unknown symbol dvb_usb_nec_rc_key_to_event
[   33.372689] dvb_usb_dtt200u: disagrees about version of symbol dvb_usb_generi
c_rw
[   33.372691] dvb_usb_dtt200u: Unknown symbol dvb_usb_generic_rw
[   33.372756] dvb_usb_dtt200u: disagrees about version of symbol dvb_usb_device
_init
[   33.372758] dvb_usb_dtt200u: Unknown symbol dvb_usb_device_init
[   33.372810] dvb_usb_dtt200u: disagrees about version of symbol dvb_usb_generi
c_write
[   33.372812] dvb_usb_dtt200u: Unknown symbol dvb_usb_generic_write

As far as I know the firmware files are up to date - the one at the linuxtv.org site is older than that in the firmware directory (but I've tried that one anyway).

make and make install both worked without errors in ~/v4l-dvb.

lsmod | grep dvb gives 
dvb_usb                20620  0 
dvb_core               79784  1 dvb_usb
dvb_pll                14596  1 dvb_usb
i2c_core               21776  10 i2c_ec,wm8775,cx25840,tuner,dvb_usb,nvidia,ivtv,i2c_algo_bit,tveeprom,dvb_pll
usbcore               131480  6 dvb_usb,xpad,usbhid,ehci_hcd,uhci_hcd

dvb_usb_dtt200u seems to be missing - presumably because of the errors in dmesg. Is this correct?

lsusb gives
Bus 004 Device 002: ID 14aa:022a AVerMedia (again) or C&E 

Like some other  people posting on this topic I just dont (seem to) have a /dev/dvb

Gerv said "The firmware file I have, which works for my stick, is called dvb-usb-dib0700-01.fw" - I am totally confused! There are all these postings on Freecom USB sticks. dvb_usb_dtt200u seems to be the firmware we should be interested in. Yes we are looking for AVerMedia in the lsusb listing and in Gerv's case it is a completely different firmware file that works for his stick.

Its great that so many people give their time to help others out and I'm really reluctant to ask yet another question on this topic, but I've simply run out of places to self help.

Any assistance would be hugely appreciated.

Simon

---

