---
title: "AF9015 usb tv tunner stops locking channel after a while"
date: 2011-01-04
forum: Mythbuntu
---

### Post by jjrp78 on 2011-01-04
Hi All,

I have a usb tunner which works great except for the fact that after a couple of hours it stops locking the channels.

I know is not low signal problem because mythtv shows there is 87% signal.

The problem is solved by disconnecting the tunner, restarting the pc, then connecting the tunner again.

I have noticed that when the tunner works on /var/log/messages I have this line every 4 minutes:

Jan  2 01:34:40 MediaCenter kernel: [ 1125.279303] af9015_pid_filter_ctrl: onoff:0


..and when it stops working I dont get that line anymore

Any leads?

---

### Post by jjrp78 on 2011-01-06
bump!

---

### Post by jjrp78 on 2011-01-09
nobody?

---

### Post by size_XXM on 2011-01-11
Ah, good to know I'm not the only one having this problem. Unfortunately, I don't know how to fix this. At best, it's sufficient to unplug/re-plug the tuner in my case, *maybe* unload the modules. I've never had to reboot the machine. This however, was mostly on Kubuntu Karmic and Debian squeeze. I've migrated the Karmic to Maverick and haven't got around to testing it yet, and also migrated the Squeeze machine to Natty, where the tuner works OotB. The Natty machine seems not to have this problem, but I have yet to test it thoroughly.

Oh yeah - which version of the firmware are you using?

---

### Post by jjrp78 on 2011-01-30
True...no need to restart the machine..I have to restart myth-tv tough

by fm do you mean what is the module? dvb-usb-af9015

---

### Post by size_XXM on 2011-01-30
> **jjrp78 said:**
> by fm do you mean what is the module? dvb-usb-af9015
If you meant to ask about the firmware version, that is displayed in kernel messages when you insert the tuner:
> [181803.432142] usb 1-1: new high speed USB device using ehci_hcd and address 7
[181803.936544] dvb-usb: found a 'Afatech AF9015 DVB-T USB2.0 stick' in cold state, will try to load a firmware
[181803.963534] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
[181804.033699] dvb-usb: found a 'Afatech AF9015 DVB-T USB2.0 stick' in warm state.
[181804.033948] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[181804.034847] DVB: registering new adapter (Afatech AF9015 DVB-T USB2.0 stick)
[181804.047783] af9013: **firmware version:5.1.0.0**
...

On a separate note, the issue seems to have been fixed in natty's 2.6.37-12 (possibly earlier) kernel. I switched to 2.6.38-1 but that seems to bring up more issues than it solves.

---

### Post by mtbdescender on 2011-01-31
Exactly the same behavior with my Kworld 399U dual DVB-T usb 2.0 with AF9015 and Muthbuntu 10.10 amd 64.

Hopefully with natty final kernel problem is fixed.

---

### Post by teeedubb on 2011-06-24
Any word on how well the chipset works with the natty kernel?

---

### Post by size_XXM on 2011-06-25
> **teeedubb said:**
> Any word on how well the chipset works with the natty kernel?

Works for me OotB.

---

