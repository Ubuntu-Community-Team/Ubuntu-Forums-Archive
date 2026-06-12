---
title: "question about drivers"
date: 2011-02-27
forum: Mythbuntu
---

### Post by MishMich on 2011-02-27
Hi, I moved to NZ from the UK, and brought an HP pavillion that I use MCE to watch and record TV to a 500GB USB disk.  In the UK I used a Hauppage Nova TD DVB-T stick (USB), which works in NZ (which is MPEG-4 rather than MPEG-2 in the UK - as Terrestrial Freeview is HD here).  Although it worked at one campsite, when we moved to a different site, there was not a usable terrestrial signal, so I bought an Avermedia AVerTV DVB-S USB Galaxy, which supports satellite, as well as analog and S-video etc.  Now we have a house, the two work together.  The logic behind the USB devices was that the HP pav is a low-profile case, and will not take a full-height PCI card, and there is only one spare bay which is not PCI-E.

I have used debian and ubuntu on low-spec PC's for a few years now - and a recent problem with Windows 7 (SP1 trashed my dual-boot laptop) has made me feel I need to get away from Windows altogether.  So, I'm looking at repartitioning the Windows 7 HP Pav, and putting Mythbuntu on it as a front and back end initially.

I have looked through the Wiki for Myth TV, and it looks like my Hauppage Nova TD may well work, but I can find no mention of the Avermedia Galaxy anywhere in this context.  So, I'm figuring there is no driver for it.

Before I start hacking at my HP Pav (which is our only source of TV - as the Freeview recorder & TV we bought don't - being MPEG-2 not MPEG-4) I was wondering what is involved in writing a driver for something like this.  I haven't written a driver for linux, and the last time I did write a driver was for a printer under SCO UNIX - over 15 years ago.

I apologise for the length of this, but if somebody could point me in the general direction of where I would start, that would be appreciated.  Would I need to get information from the manufacturer, or is there some other way of deriving the configuration settings I will need?

By the way, the Avermedia unit is extremely good, although the blue 'active' light is quite bright when watching TV in the dark.

Thanks,

Mish.

---

### Post by ian dobson on 2011-02-27
Hi,

Writing a driver for a card might be easy, it might be impossible. Firstly the easy part. It the card you have uses chips that are already supported by linux (Tuner chip & decoder chip) then it's "just" a matter of adding the PCI ID's to a driver that uses the same chips. The hard/impossible bit is if the card uses chips that aren't supported so you'll have to write your own driver and quite often you can't get access to the specifications for the chips.

A good example it took me about 2 days to hack support for a new chip into the w83627ehf hardware monitoring driver. Most of the time was spent understanding the code/getting the PDF specification and the actual changes were very small.

Edit: Why not just burn a liveCD, boot from it a see what linux finds (/dev/dvb) or dmesg.

Regards
Ian Dobson

---

### Post by MishMich on 2011-02-27
> **ian dobson said:**
> Hi,

Writing a driver for a card might be easy, it might be impossible. Firstly the easy part. It the card you have uses chips that are already supported by linux (Tuner chip & decoder chip) then it's "just" a matter of adding the PCI ID's to a driver that uses the same chips. The hard/impossible bit is if the card uses chips that aren't supported so you'll have to write your own driver and quite often you can't get access to the specifications for the chips.

A good example it took me about 2 days to hack support for a new chip into the w83627ehf hardware monitoring driver. Most of the time was spent understanding the code/getting the PDF specification and the actual changes were very small.

Edit: Why not just burn a liveCD, boot from it a see what linux finds (/dev/dvb) or dmesg.

Regards
Ian Dobson

Thanks, the simplest solutions are always the best - completely forgot it was available on live disk.

Mish.

---

### Post by MishMich on 2011-03-01
Thanks,

I tried the Ubuntu 6-pack live disk, and under Ubuntu it listed two devices.  I'll need to wait till I get a proper broadband connection to try installing on an older test PC first.

Mish.

---

### Post by MishMich on 2011-03-10
This is what I found.  Having tried using the liveCD, I installed Mythbuntu on an old PC, with the Hauppage DVB-T USB card.  This did work, although I lost the configuration trying to enable both channels - the signal was strong enough for one, but when split across two it played up.  It also worked with a cheap August USB I have - but again, the signal is too poor to run three tuners, even with a booster-splitter.

I had problems with the W7 MCE when it did an automatic update overnight (PC failed to come back up again, and couldn't access bios, etc.  I managed to get the system up with a liveCD, and complete the update.  I decided to install Mythbuntu beside W7, as a dual boot system (so I can still watch TV and getting this working when time allows).

The AverTV Galaxy USB DVB-S did not get picked up at all.  So, I am figuring that what was picked up by the liveCD was not the two devices, but the two tuners on the Hauppage USB DVB-T.

I want to get the AverTV DVB-S (which also has an analog tuner & FM radio) working because the satelite reception is much better than arial.  Then I could use the older box I set up to act as a back-end and Terrestrial Freeview recorder to avoid conflicts when watching TV on the DVB-S.  It would be in a different part of the house.

The HP Media Centre remote & IR receiver seems to work OK, which is nice.

Thanks,

Mish

---

### Post by MishMich on 2011-03-10
By the way, end of dmesg, following unpluf/replug of USB:

[ 6332.987593] usb 1-1: USB disconnect, address 2
[ 6339.776024] usb 1-1: new high speed USB device using ehci_hcd and address 5

It doesn't detail anything more than that.

$ ps -fe | grep udev

root       386     1  0 Mar10 ?        00:00:00 upstart-udev-bridge --daemon
root       392     1  0 Mar10 ?        00:00:00 udevd --daemon
root       544   392  0 Mar10 ?        00:00:00 udevd --daemon
root       549   392  0 Mar10 ?        00:00:00 udevd --daemon
user      4686  3688  0 00:47 pts/0    00:00:00 grep --color=auto udev

---

### Post by MishMich on 2011-03-10
I made some progress, reading around, I tried installing "linux-firmware-nonfree".  I then unplugged & replugged the card.

I now get

$ ls /dev/dvb
adapter0  adapter1  adapter2  adapter3

$ ls /dev/dvb/adapter0
audio0  ca0  demux0  dvr0  frontend0  net0  osd0  video0

and tail dmesg:

[ 8105.109604] usb 1-1: USB disconnect, address 5
[ 8110.092537] usb 1-1: new high speed USB device using ehci_hcd and address 6

but, I still cannot open the card.  The message I get is this:

$ sudo scan /usr/share/dvb/dvb-s/OptusD1-160E
scanning /usr/share/dvb/dvb-s/OptusD1-160E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 6 No such device or address

Any ideas?

---

### Post by ian dobson on 2011-03-10
Hi,

What else do you see in dmesg? Did the driver actually find/install the firmware?

Regards
Ian Dobson

---

### Post by MishMich on 2011-03-11
No, it didn't.

I contacted AverMedia about Linux drivers:

"For your information, the AverTV Galaxy is not compatible under Linux. Due that the device was originally designed to work under Windows only, we don't have any plannings on having the device supported under Linux."

Then in reply to a question about information to help construct a driver:

"Unfortunately, such information is considered classified according to company policy. Therefore, we are not allowed to provide detailed information out."

So, that is a bit of a problem really.

Mish.

---

