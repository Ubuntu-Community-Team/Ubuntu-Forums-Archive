---
title: "Startup hangs - 9.10 + HVR1300"
date: 2010-03-11
forum: Mythbuntu
---

### Post by djm-uk on 2010-03-11
I have an annoying problem that I don't seem to be able to get to the bottom of...

MB 9.10, on intel atom dual core board (G945CLF2 ?), with HVR 1300 PCI card, SATA HDD.

Every so often (say 1 in 4) the bootup process stops either just before or after the 'setting preliminary keymap' message. This is a hard hang - no keyboard LED response, no network response - the only thing to do is to power off & restart.

I have unplugged the IR Remote & there are no other USB devices.

I have put all updates on (up to kernel .20) & also tried with the original (.14?) kernel.

if I look in syslog then the last message is usually the (start of) loading firmware message for the hvr1300. I have compared the logs between a good and hung boot and cannot find a consistent difference.

I did find that it sometimes says 'TSC unreliable' & sometimes uses TSC. Also the load order of ALSA and Intel HDA (High def Audio) drivers varies. But in both cases when I checked a good vs hung boot the good boots had both TSC and no TSC and Alsa first and HDA first....

I was going to try a different card so got a DVICO fusion HDTV (Which was recognised immediately without any changes/problems), but the card seems a little 'deaf' and won't lock on the signal that the HVR has no problems with - if I take the splitter out then the DVICO has a very marginal lock but is unusable.  In any case it is another conexant based card so don't know if it is a valid check anyway...

Any suggestions to find the cause of this? (Edit: or suggestions for a cheapish non-conexant card to use as a test to eliminate the HVR 1300?)

David

---

### Post by djm-uk on 2010-07-14
Not sure if this is a fix or not...

I suspect a race condition - as ureadahead starts on STARTING mountall and not on it's completion I suspected an issue with disks not being mounted as ureadahead starts so..


on one machine I disabled ureadahead (by putting an exit 0 in the init script) and on the other I put a sleep 5 in there so the mount process has a chance to complete before ureadahead starts running.

This seems to make life much better - although I still have other issues with the sound...

David

---

