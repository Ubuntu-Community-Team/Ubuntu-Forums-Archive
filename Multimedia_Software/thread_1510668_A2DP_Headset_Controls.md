---
title: "A2DP Headset Controls"
date: 2010-06-15
forum: Multimedia Software
---

### Post by faustt on 2010-06-15
Not sure if this is a multimedia question per-say, but here goes.

I have a stereo bluetooth headset (Motorola HT820) that plays fine with 10.04 out of the box. For the life of me can't figure out how to get the controls on the headset to work though. Maybe I'm getting the lingo wrong for linux or something, but I can't find much with Google past just pairing the headset. As far as I know the A2DP profile handles stereo audio and controls. I would figure after selecting that in the sound properties window it would just work, no dice though.

The controls I'm talking about are on the right ear. Forward, Back and a pause/play toggle button. Is there a package I need to grab? Do I need a utility? Do I have to configure it somehow for every audio program or can it be global?

Thanks guys.

---

### Post by faustt on 2010-06-15
Well, my bad. AVRCP is the correct term. Still had to dig though. Found the solution here

[http://ubuntuforums.org/showpost.php?p=6497530&postcount=6](http://ubuntuforums.org/showpost.php?p=6497530&postcount=6)

Thank [Guillaume86]("http://ubuntuforums.org/member.php?u=119881") for this little tib bit

>  add uinput at the end of your /etc/modules file and enjoy AVRCP support...
just restart and its simple as that.

---

