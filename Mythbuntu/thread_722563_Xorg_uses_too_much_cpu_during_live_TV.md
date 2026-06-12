---
title: "Xorg uses too much cpu during live TV"
date: 2008-03-12
forum: Mythbuntu
---

### Post by murbanci on 2008-03-12
I have just updated to MythTV 0.21 and noticed that while watching live tv, xorg jumps to around 80 to 90 % according to top.  Theres no problem however when im watching a movie or recording, its only about 2 or 3% then.  Is there any way to fix this?  It makes my computer run hot and loud since the fans are working harder.  Any help would be appreciated.  Thanks.

---

### Post by Nikas on 2008-03-12
I have the same problem. 0.21 here.

---

### Post by murbanci on 2008-03-12
Update: I have figured out that the main cause for the problem is the pop-ups that appear when I change the channel, adjust the volume, or scroll through the TV guide.  Whenever I do this, the cpu usage for xorg spikes to upwards of 100% and then will hang there for a while, returning to normal after about 10 or 15 minutes.  There are also random spikes for no apparent reason.  Is this normal or it there a way to fix this?

---

### Post by Phydeaux on 2008-03-13
Mine stays just at or under 100% while watching livetv and doing nothing else, no popups, OSD, etc.  It actually starts a bit lower, around 60% then gradually gets higher and higher.  I'm not really sure if this existed prior to 0.21, though I think I would have noticed this.  My proc fan is controlled by a knob on the front as opposed to the mobo, so it isn't dynamic.  I have a temp lcd on the front and it doesn't appear to be any higher than normal usage.  This is a brand new amd quad-core or core 2 duo or whatever amd calls it.  It doesn't effect playback.  Possibly a problem with alpha blending?

---

### Post by p$y on 2008-03-14
> **Phydeaux said:**
> Mine stays just at or under 100% while watching livetv and doing nothing else, no popups, OSD, etc.

same here, even while watching recordings...

---

### Post by fercactus on 2008-05-07
Hey everyone,

I believe I got this solved for me.

I have the nVdia GeForce 7100 G video card.  I also noticed that Xorg would jump to 100 percent when entering Program Guide, adjusting volume, etc... in Live TV.

In order to fix this problem I found the following article on wiki.mythtv.org when searching for XvMC:  [http://www.mythtv.org/wiki/index.php/XvMC](http://www.mythtv.org/wiki/index.php/XvMC)

Per the article I modified my xorg.conf file with:

add to section "device"
  Option "UseEvents" "true"
  Option "XvmcUsesTextures" "false"  # necessary for color Chromakey OSD)
  Option "NVAGP" "1"               # some users report 2 or 3 works better

add:
Section "Extensions"
      Option "Composite" "Disabled"
EndSection

Went to /etc/X11/XvMCConfig and changed to:
libXvMCNVIDIA_dynamic.so.1

Now Xorg does not go above 10% -- still think this is high.  It also still remains around 10% cpu after leaving OSD for about 10 - 15 minutes.

Still have an issue -- when in Program Guide under Live TV it hangs (freezes) for a few seconds when scrolling through the channels.

Hope this helps.

---

### Post by gr8nash on 2008-05-14
on my forth frontend i had this problem last night after a fresh install of 8.04  my hardware is this:

amd 3500+
1 gig ram
Nvidia 7100GS GPU

It also had the OSD causing 100% processor usage. I also noticed that we have the same graphics card.  I will try the xvmc fix tonight and see if it fixes it for me.

---

### Post by gr8nash on 2008-05-14
hmm well my 3500+ that used to be able to play HD cant play it on 8.04.. maybe its the OPENGL stuff myth committed.. no idea.  i did the XORG stuff above and it didnt help.

---

### Post by WilDCarD418 on 2008-05-15
Has anyone figured this out yet? I'm having the exact same issue described here. It makes for a rather unpleasant TV watching experience.

---

### Post by ruger01 on 2010-10-07
Same issue here Xorg running at 60% and Kaffeine 30% + according to TOP have an ATI Radeon HD4250 integrated card is this a driver issue?

---

### Post by LowSky on 2010-10-08
> **ruger01 said:**
> Same issue here Xorg running at 60% and Kaffeine 30% + according to TOP have an ATI Radeon HD4250 integrated card is this a driver issue?

Are you running compiz or any desktop effects? If yes turn them off.

---

### Post by ruger01 on 2010-10-10
Hi,

All effects are set at none, and not running compiz either.

---

