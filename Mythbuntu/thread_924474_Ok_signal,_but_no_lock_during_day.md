---
title: "Ok signal, but no lock during day"
date: 2008-09-19
forum: Mythbuntu
---

### Post by leeko on 2008-09-19
Hi all,

I'm in the process of setting up an ATI HDTV Wonder ATSC/NTSC tuner, and wanted to ask a quick question:

At night, I'm able to get a lock and watch a few channels. Many of the channels don't lock, but i put that down to my antenna not being great (Radioshack Delta non-amplified multidirectional). 

However, during the day I can't get a lock on a single channel. Not even one. I played with the positioning of the antenna today, but still no joy. 

The antenna is being fed into a signal splitter, and one cable goes to my ATI card. The other cable goes to my DTV set-top box, which reports a signal strength of 75% for certain channels. Tuning to the same channel with the ATI card, shows:

Signal strength: jumps rapidly between 60% and 99% (on some channels, it's stable somewhere between these numbers).
S/N ratio: 4-5dB
BE: 0
LAM - no lock (certain channels this flickers briefly, but goes back to "no lock"

I don't understand it. I understand that the signal is better at night, but surely I should be able to lock to something? Especially the channels which are showing decent signal strength on the settop box (from the same antenna)? 

If anyone can shed some light, I'd really appreciate it. I'd rather not lay down the expense of a fancy antenna if that's not the whole story!

Thanks,

Lee

---

### Post by chris_nava on 2008-09-19
Try removing the splitter from the equation.  They are notorious for degrading signal quality.

Potentially the signal could be bad only on one output line if it's defective. (try swapping the outputs)

---

### Post by leeko on 2008-09-20
Ahah! I figured it out - sort of :P

The PC had been in standby mode (S3 suspend) between last night and today. 

I ran a couple of tests, and it looks like the TV tuner doesn't lock to any channels after a standby.

Any idea how I would go about troubleshooting this? 

Thanks,

Lee

---

