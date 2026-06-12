---
title: "Weird issue with Novation Launchpad Pro MK3"
date: 2020-04-01
forum: Multimedia Software
---

### Post by muranyia2 on 2020-04-01
Hi All! First forum post after 27 years on Linux and who knows how many on Ubuntu... :D

I have the Novation Launchpad Pro MK3 external MIDI controller, which is also a standalone hardware sequencer (MK1 was not, MK2 only with custom firmware).

On one of my Ubuntu PCs (but not on the other, nor with Windows), when the Launchpad is connected (via USB), _its internal sequencer becomes sensitive to pushing function keys_ on the unit and whenever I do, other _hardware which is synced to the Launchpad falls out of sync_. (Just to make it clear, the issue doesn't ever occur when the device is not connected to the PC.)

I've reported this to Novation but they don't officially support Linux and my problem is hard to reproduce anyway, therefore I'm asking for your guidance.

Weirdness in the weirdness is that when I connect the MIDI **input** coming from the Launchpad (using the Connect feature of QJackCtl - N.B. jack is not running) to QMidiRoute, the problem goes away. This makes no sense to me, especially that connecting to other software (Sequencer64, the successor of Seq24) makes no such difference.

I'm particularly curious whether anything is being "secretly" sent to the Launchpad (even though there is nothing explicitly routed), so [I asked on askubuntu]("https://askubuntu.com/questions/1223229/how-to-monitor-midi-output") for specific tips on monitoring MIDI **output**.

Before you suggest that the Launchpad might need more power from USB, it is connected via a powered USB HUB, and when it's not (and not misbehaving either) it is still powered from the same HUB which claims to supply max 1.5A per port. It still might be a power issue, but then not a trivial one...

---

