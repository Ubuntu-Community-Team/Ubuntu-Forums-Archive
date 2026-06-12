---
title: "Is anyone using FM on PVR-500?"
date: 2007-10-05
forum: Mythbuntu
---

### Post by tedder on 2007-10-05
Among other things, I'm using a PVR-500 for my Mythbuntu setup. I can't figure out how to get the damn FM tuner to work.

I've installed the extra header card, connected to 'header 2', jumpers are set correctly. If I plug the output of that into headphones or my receiver, I don't get anything.

I've tried connecting to header 1, I'm using fmtools to tune /dev/radio0 (and all the /dev/video devices, I think), but no luck.

---

### Post by tedder on 2007-10-05
So I'm trying ivtv-radio, which seems like it might be the right way to go, except for it not working.

```
# ivtv-radio -v  -f 101.1 -c "sox -t raw -r 48000 -w -s -c2 %s -t wav test.wav trim 0 10"
set to freq 101.10
signal strength: 45056
Running: sox -t raw -r 48000 -w -s -c2 /dev/video24 -t wav test.wav trim 0 10
Cleaning up

```

The file is completely silent. FWIW, I've tried recording /dev/video25, and it at least records my TV audio :-)

Do I need a loopback cable or anything? I've tried listening to the two sets of RF jacks on the pvr-500, plus my audio card output, while ivtv-radio is running, but I get nothing.

---

### Post by deffcon on 2007-10-06
Hi,

As far as i know there is not FM possiblilty in mythbuntu for FM radio,
what do you want to try, and what have you done already, i have 2x pvr500 mce, and really no problems.

Dave

---

### Post by superm1 on 2007-10-06
There used to be an old plugin way back when for FM stuff.  Thought it wasn't compatible w/ 0.20.2.

---

### Post by tedder on 2007-10-06
I could care less about using it through the Myth interface, I just want to get it to *work*.

---

### Post by axelsvag on 2007-10-07
I don´t have an answer to your problem, but. I have exactly the same question as you have. the ivtv tool seems to find the card, scan frequencies, find radio stations but where is the sound? And when I look at internet very few seems to bother. And I have not found any ideas to solve the problem. So  maybe can we find a solution together.

---

### Post by superm1 on 2007-10-07
I have a suspicion this may be caused by the old version of ivtv-utils in universe.

I'm going to attach a newer version of ivtv-utils (synced from debian).  If this resolves the issue, a universe upstream version freeze exception needs to be filed ASAP (The archives are in RC freeze right now).

Note, this attachment is for i386 machines only.

---

### Post by tedder on 2007-10-07
Installed that version ofivtv-utils, worked on the first try. Awesome!

So, what's next? What documentation can I give you to help with the bug filing?

---

### Post by superm1 on 2007-10-07
OK.  Well i've filed a bug:

[https://bugs.launchpad.net/ubuntu/+source/ivtv/+bug/150276](https://bugs.launchpad.net/ubuntu/+source/ivtv/+bug/150276)

Hopefully this can get in before release.  This is why we need people testing these sorts of things as early as possible :)

---

