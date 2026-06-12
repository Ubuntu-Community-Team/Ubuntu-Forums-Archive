---
title: "Added new usb tuner - got 2 extra encoders showing up??"
date: 2008-10-05
forum: Mythbuntu
---

### Post by ubnewbie2 on 2008-10-05
I recently added an ASUS my cinema U3100 usb tuner to my system (and had to upgrade from 7.10 to 8.04 - which may be relevent to this problem).

Previously I had 2 PCI DVB tuners, and the system showed I had 2 encoders (on the mythweb system status page).  After adding the usb tuner, mythweb system status shows 4 encoders ! Why the extra one?

Doing "ls /dev/dvb"  shows 3 adapters (0, 1 and 2).  The scheduler seems to be working with new tuner, as looking at the mythweb scheduled programs page shows it using the new tuner when 3 shows need to be recorded at once, but that page shows which tuner by "card" name, and I am not sure of the relationship between 'card' and 'encoder'.

When watching live TV, I can bring up the on-screen menu and switch to each of the three tuners.  However, the menu seems to confuse the names of the cards, sometimes showing one of them twice on the menu.

All very confusing...

---

### Post by ian dobson on 2008-10-05
Hi,

MythTV allows you to record several programs at the same time from one DVB tuner if the programs/channels are on the same multiplex. 

This is a nice feature to allow you to record back to back recordings.

If you go into mthtv-setup cards you'll see that the USB is setup as 2 tuners.

I think the feature is called multirec in MythTV.
Have a look here:- [http://www.mythtv.org/wiki/index.php/Record_multiple_channels_from_one_multiplex](http://www.mythtv.org/wiki/index.php/Record_multiple_channels_from_one_multiplex)


Regards
Ian Dobson

---

### Post by ubnewbie2 on 2008-10-06
Thank you for that.  You are quite correct.  Even better, I also set my other 2 internal DVB cards to allow 2 recordings at once, so now I have 6 encoders showing up!! :)

---

### Post by Nikas on 2008-10-06
Yes. Multirec is great.

Keep in mind that you only can record several programs at the same time with one tuner if the channels are on the same mux.

In Sweden, i can record from ALL channels at the same time with 6 tuners. I have 4 today. :)
Sweden has 6 multiplexes and around 30 channels.

---

