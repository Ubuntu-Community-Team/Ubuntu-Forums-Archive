---
title: "Audio problems -- Onboard"
date: 2006-01-19
forum: Multimedia &amp; Video
---

### Post by foulplay on 2006-01-19
Audio
  Karajan audio module
    - Realtek ALC882 8-channel High Definition Audio CODEC
    - 6 audio jacks
    - 1 CD-in connector
    - 1 front audio connector

True stereo line level outputs

S/PDIF-in/out interface

That's the basic stuff from the motherboard's site.  When I try to load a site that has sound I get the following errors:

Can't init Audio Driver 'alsasink' - trying another one...

No usable audio-driver found! (alsasink)

Any help is appreciated.

---

### Post by FarEast on 2006-01-23
Hi,
Please paste the output of the command below.
$ cat /proc/asound/cards

---

### Post by ConfatSlim on 2006-03-25
cat /proc/asound/cards
0 [Snapper        ]: PMac Snapper - PowerMac Snapper
                     PowerMac Snapper (Dev 22) Sub-frame 0

---

### Post by FarEast on 2006-03-27
Are you an 'alias' of foulplay, ConfatSlim:) ?

Now I see that you have a Mac and your sound card seems to be properly configured.

> Can't init Audio Driver 'alsasink' - trying another one...
> No usable audio-driver found! (alsasink)

Select: System > Preferences > Multimedia System
Then change 'default sink' to ESD.  This may help.

---

