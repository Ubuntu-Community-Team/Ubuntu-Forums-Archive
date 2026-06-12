---
title: "xdtv sound problem"
date: 2010-05-11
forum: Multimedia Software
---

### Post by vlajkoral on 2010-05-11
Installed Ubuntu lucid (after 9.04), everything work fine. Setup my Winfast 2000xp rm tv card, and installed (dpkg -i) [xdtv]("http://xawdecode.sourceforge.net/"), by downloading from [http://nicolas.estre.free.fr/ubuntu/dists/edgy/main/binary-i386/xdtv_2.4.0-2_i386.deb]("http://nicolas.estre.free.fr/ubuntu/dists/edgy/main/binary-i386/xdtv_2.4.0-2_i386.deb") got the other requirments with $sudo apt-get install xaw3dg libzvbi0 tv-fonts ...

xdtv now work fine except sound, can't control volume, or record any sound... every time when start xdtv it say 
```
You should launch XdTV with the -mixer_tvchan parameter.
Goto the man page to get more informations about that switch.
Your Alsa mixer doesn't propose any of those channels:

Line, PCM, Capture, Aux, Wave Surround
SB Live Analog/Digital Output Jack or Master

Select the good one for your own audio card.
Or use OSS with the -noalsa parameter. 
```

i know that it need -mixer_tvchan parameter bat dont't know the right syntax...
any help?

P.S."Sorry for my bad english"

---

