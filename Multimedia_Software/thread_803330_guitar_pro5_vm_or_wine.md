---
title: "guitar pro5 vm or wine"
date: 2008-05-22
forum: Multimedia Software
---

### Post by blackest_knight on 2008-05-22
first tuxguitar is great but it hasnt got the rse engine which makes midi guitars sound pretty good instead of the usual lousy midi effort. 

Theres two ways open either a vm or wine 

wine works to a degree but i am hoping someone can post proper settings.

vm 
well so far i got it working in vista as a guest in virtualbox but the sound was all over the place playing at random speeds the cpu maxed out so i guess vista may be too demanding, I will retry with 2000 as a guest and see how that performs. 

anyone done any better vmware maybe or xen perhaps.

it would be nice to get this working. :guitar:

---

### Post by blackest_knight on 2008-05-23
from

[http://appdb.winehq.org/commentview.php?iAppId=246&iVersionId=3782&iThreadId=12871](http://appdb.winehq.org/commentview.php?iAppId=246&iVersionId=3782&iThreadId=12871)


RSE is Realist Sound Engine, it makes GP5 sound like real guitars are playing

to fix this you need a fairly new computer

open terminal and type "winecfg"

the click the audio tab

make sure only OSS is checked

go do to hardware acceleration and choose standard or basic

change the Default Sample Rate to 48000

change Default Bits Per Sample to 16

Finally check the box that says Driver Emulation

"""if you choose standard under hardware acceleration and it doesnt work, change it to basic"""

""if basic dosent work choose emulated but sound may be scratchy"""

"""if all fails use MIDI"""

This kind of works the main problem seems to be system load 
the nt4 or 2000 emulations seem to be quite good.

speed of playback seems variable maybe with a fast enough system this is a working solution.

---

