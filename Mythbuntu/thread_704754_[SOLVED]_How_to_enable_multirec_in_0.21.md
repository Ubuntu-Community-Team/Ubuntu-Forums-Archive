---
title: "[SOLVED] How to enable multirec in 0.21?"
date: 2008-02-22
forum: Mythbuntu
---

### Post by Archmage on 2008-02-22
I'm using the weekly builds of MythTV 0.21.

If I understand it correctly, with this I should be able to record more than one channel with only one turner. But it seems that I'm missing the option to enable this.

Does someone have a clue how I can turn this on? I would love to receive all the back to back episodes with a little overlap.

---

### Post by Nikas on 2008-02-22
Enter mythtv-setup.

Edit your tv-card/s and you should have a setting regarding "Recording" there. Don't know the right name in english.

---

### Post by Archmage on 2008-02-26
Thanks. This did help me finding it. I can record up to five recordings with one turner. Great.

---

### Post by volkswagner on 2008-02-26
Wow!  How does it work?  Does it work for any Mythtv supported tuner?  Anyone have it working?  Is there any PQ loss?

---

### Post by Nikas on 2008-02-26
> **volkswagner said:**
> Wow!  How does it work?  Does it work for any Mythtv supported tuner?  Anyone have it working?  Is there any PQ loss?

Sure. Works great. I know it works for DVB-T as long as the channels are on the same mux. Here in Sweden we have 6 muxes that broadcast all our channels both open and encrypted. I have 4 DVB-T tuners and i allow 2 simultaneous recordings on each tuner = 8 recorders. You can only record from two or more channels with the same tuner if they are on the same mux as said before. :) 
This can not be done with analog tuners.

Read more here:
[http://www.mythtv.org/wiki/index.php/Record_multiple_channels_from_one_multiplex](http://www.mythtv.org/wiki/index.php/Record_multiple_channels_from_one_multiplex)

---

### Post by Archmage on 2008-02-27
I did try to record 5 different recordings (the maximum) with one turner - it works, but of course it was stressing my harddrive a little. (I did change the setting to allow only one job (commercial flagging/trancode) on the machine to reduce the harddrive stress.

But this works. If the channels are on the same mux or if you are recording back-to-back episodes you only need a turner for them.

---

