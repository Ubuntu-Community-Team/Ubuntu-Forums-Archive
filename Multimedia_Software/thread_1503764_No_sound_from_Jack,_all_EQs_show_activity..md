---
title: "No sound from Jack, all EQs show activity."
date: 2010-06-07
forum: Multimedia Software
---

### Post by dchurch24 on 2010-06-07
Hi all,

I haven't recorded for a while (about a month), and I turned on my DAW machine yesterday as I had a few ideas floating around in my head (which have since gone!), started up Hydrogen and Ardour which all started ok (Jack must have been running), the EQ goes up and down when I click a drum or load on old song into Ardour, but I have no sound out at all.

The result of dmesg shows:

```

    dave@ubuntustudio:~$ dmesg |grep ICE
    [   19.409352] ICE1712 0000:03:00.0: PCI INT A -> Link[LNEC] -> GSI 17 (level, low) -> IRQ 17

```


The card is a M-Audio Delta 66 - which was working fine (thanks to you fine people here!) until yesterday.

I've played around with the settings in Jack - all to no avail. The output amp is all wired fine, as if I pull out the output from the breakout box and touch it with my finger, I can hear the static through the speakers. All connections have been screwed in tight etc.... so I think it's a software issue.

EDIT: This is the 64 bit version of Ubuntu Studio 9.10 (rt), if that makes any difference.

---

### Post by cchhrriiss121212 on 2010-06-07
Check your analog (DAC 0-5) levels using alsamixer, they sometimes get reset after updates.

---

### Post by dchurch24 on 2010-06-07
Hi, thanks for that - although I'd already checked these (I've had that issue before), and they are fine.

It's a strange one - working one day, then not the next!

I wonder if reinstall of Jack might sort it out, or at least return it to default perhaps?

---

### Post by cchhrriiss121212 on 2010-06-07
So do you have playback with straight alsa apps? Firefox etc.
A reinstall of jack might help, but it may remove your desktop as it is part of the studio meta-package. Have you tried all the outputs and checked everything is connected right in patchage/jack connections?

---

### Post by dchurch24 on 2010-06-07
Hi,

I haven't tried Firefox, but did try Audacity - that showed as though it was working, but I still had no sound output.

> checked everything is connected right in patchage/jack connections?

I did check these, and they seemed to be ok - e.g. In the Jack connections window, Ardour was connected to System Out etc...

It was working a few weeks ago - and I do remember messing about with the settings to get something new working - I can't for the life of me remember what it was, and I ended up uninstalling it, as I was only playing with it out of curiousity.

I have checked all the cables, they are in quite correctly - I tested the lead to the amp as well - I can hear the static noise when I press my finger on it, so I know it's all connected right.

I am stumped.

I could post a screenshot of my Jack settings etc... when I get home; perhaps someone with more knowledge than me might see it and see the error straight away.

---

### Post by dchurch24 on 2010-06-08
Odd - the Envy24 outputs were set to SPDIF.

Changed these, and voila! I have sound!

Thanks very much guys for your time and effort, much appreciated.

---

