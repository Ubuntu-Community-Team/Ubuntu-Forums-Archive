---
title: "Intel 945G Vsync Tearing on all apps"
date: 2008-10-06
forum: Multimedia Software
---

### Post by LiquidRain on 2008-10-06
Hello,

Everything on my Thinkpad X60s suffers from severe screen tearing.

I have tried googling, seeking help in the IRC channel, editing my xorg.conf, everything I can think of. (tried disabling GLX to no avail; something somewhere overwrites disabling it)

It occurs in X, showing itself prominently with Compiz, games and emulators, and movie playback regardless of the playback program, output driver, codec, movie resolution, etc. (tried gxine, totem, VLC with X11 rendering and OpenGL)

Nothing seems to be working and this is frustrating me to no end, coming from the pleasantly smooth nVidia drivers to this.

Anyone have any ideas?

Thanks.

---

### Post by LiquidRain on 2008-10-07
Found the answer.

Use a .drirc in your ~ and an /etc/drirc file that looks like this:
```
<driconf>
<device screen="0" driver="i915">
   <application name="all">
      <!-- Always synchronize with vertical refresh to avoid tearing -->
      <option name="vblank_mode" value="3"/>
   </application>
</device>
```
Then set applications to specifically use OpenGL.  It seems to have fixed it.  I also added "INTEL_BATCH=1" to my /etc/environments since it is supposed to improve performance by a good chunk. (as much as it can be on these chips, at any rate)

---

### Post by szale9001 on 2008-10-15
I tried this, however it had no effect. Is there really no way to vsync the intel 945s?? Rather, what causes this, this card supposedly works fine with Aero on Vista so why would there be such tearing with compiz??
BTW I am running Intrepid Beta, but the tearing has been consistent since Hardy Final. Any suggestions??

---

### Post by LiquidRain on 2008-10-15
I can't say I really tried it with Compiz, since I run a dual monitor setup off the laptop that requires me to disable DRI for X. (and subsequently disabling Compiz)  Adding the /etc/drirc and ~/.drirc files with the above fixed vsync on VLC for me.  I wonder if it's an upstream driver bug.

---

