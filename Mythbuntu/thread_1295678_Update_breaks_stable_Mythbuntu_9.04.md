---
title: "Update breaks stable Mythbuntu 9.04"
date: 2009-10-19
forum: Mythbuntu
---

### Post by kazam on 2009-10-19
Hi,

Background:
Have had myth running for 4+ years. Started on Knoppmyth on VIA EPIA MII12000, then 1.5 years ago upgraded hardware to VIA EPIA EX15000 and mythbuntu 8.04. A few weeks ago I upgraded to 9.04.

My rule is that was stable, dont touch it. I.e. *no* updates, apt-get's etc. Hence I have had a very very stable system for many years (although it could take time to get it stable).

Since the upgrade a few weeks ago (to 9.04) its been solid as a rock. However Ubuntu's Update Manager has kept appearing behind mythfrontend, and (I suspect) stealing keypresses. So the keyboard wouldn't work till I closed the UpdateManager. However the remote worked and that's what we use 95% of the time. So no big deal.

I should have simply turned off Update Manager, but in the weekend I thought "what the hell", and I let it update. Darn!

Now TV doesn't play right:
- TV plays fast with jerky video and fast scratchy audio. 
- The mythfrontend.log is filling up with audio buffer overflow errors.

Videos (which I play using xine) are unchanged and play just fine. Xine uses xvmc.

I've changed the TV playback profile, switching between XVMC, VIA XVMC, and the other options. No go, probably because I need xvmc working to get good video on my low powered box.

Does anyone have any thoughts on this? Does anyone have a mythbuntu 9.04 running on an EPIA box that they have run "apt-get upgrade" recently? If so, what are your TV playback settings? Are you getting audio buffer issues?

Many thanks for your help.
Paul.

p.s. I can't use VIA (too common) or TV (too short) as tags. Darn.

---

### Post by kazam on 2009-10-20
Ok. I've resolved this, sort of.

The update deposited 2.6.28-15 on my system. That fails to work with XvMC.
Rolling back to 2.6.27-14. That also fails to work.
Rolling back to 2.6.24-19 - SUCCESS!!! Everything works smoothly, CPU utilization is < 30%, which means that Via XvMC is definately active.

So it seems there was a bug added to the kernel after 2.6.24 that somehow upsets timing with XvMC.

I've disabled Updates.
I've set 2.6.24-19 to be the default kernel.

No more updates for me :-)

---

### Post by kazam on 2009-10-30
Ok. This one gets curiouser and curiouser. And its not just me. A number of people on the web are noticing a problem with EPIA mobos and 2.6.26+.

The interesting new twist is summed up in the difference between the kernels.
[B]
Kernel 2.6.24:[/B]
- mythtv TV playback works fine. CPU is low (20%). 
- /dev/dri/card[0-9] does not exist.
- Xorg.0.log shows:
```

    drmOpenDevice: node name is /dev/dri/card0
    drmOpenByBusid: drmOpenMinor returns -1

```
    ... and so on through card9.
- XOrg.0.log also shows:
```

    (II) CHROME(0): direct rendering disabled

```
[B]
Kernels 2.6.26, 2.4.28:[/B]
- mythtv TV playback does not work.
    CPU load is 80%
    mythfrontend.log shows "audio buffering overflow"
    video appears to play fast and stop and fast and stop. 
- /dev/dri/card[0-9] *does* exist.
- Xorg.0.log shows:
```

    drmOpenDevice: node name is /dev/dri/card0
    drmOpenDevice: open result is 10, (OK)

```
- XOrg.0.log also shows:
```

    (II) CHROME(0): direct rendering enabled

```


So this is pretty confusing:
When DRI is enabled, XvMC doesn't seem to work.
When DRI is disabled, XvMC does seem to work.

And even stranger, xine works just fine on all kernels using XvMC. So this is a myth problem.

Some people have pointed to CPU throttling in later kernels. I've turned off throttling and it still happens.


Does anyone have any ideas?
Thx.
Paul

---

