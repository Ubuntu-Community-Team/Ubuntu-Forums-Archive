---
title: "Video, but no sound in TVTime"
date: 2009-06-09
forum: Multimedia Software
---

### Post by TheIdiotThatIsMe on 2009-06-09
Hi, I'm using a KWorld Global TV Terminator tv card that I recently put in the setup. I purchased it with an RF unit to play my PS2 under Linux using the TV card. I first tried to setup MythTV, but found it very complicated and unsuccesful. However, I was able to get it to work with MPlayer with the following code: 

```
mplayer tv://"insert channel" -tv driver=v4l2:device=/dev/video0:chanlist=us-cable:alsa:adevice=hw.1,0:amode=1:audiorate=32000:forceaudio:volume=100:immediatemode=0:norm=NTSC
```

It works, with sound and picture, but there is a lag, that when I press a button it doesn't appear on screen for about two to three seconds. I then decided to give TVTime a try, and voila! It works, and works *fast*, with good quality. The only bad part is there is no sound. I'm thinking it's a setting issue, but can't figure out anything about a sound device or anything like that in the settings, and I know it works in MPlayer with sound, so I know the hardware is working. Since it's an RF unit and goes through the cable box, I don't have any kind of extra composite audio or anything, and I'm figuring since it worked with MPlayer it's probably just a setting.

---

### Post by TheIdiotThatIsMe on 2009-06-09
I found that it is configured in an xml file, I looked for the xml file and this is what was inside: 

```
<?xml version="1.0"?>
<!DOCTYPE tvtime PUBLIC "-//tvtime//DTD tvtime 1.0//EN" "http://tvtime.sourceforge.net/DTD/tvtime1.dtd">
<tvtime xmlns="http://tvtime.sourceforge.net/DTD/">
  <option name="Channel" value="3"/>
  <option name="DefaultBrightness" value="-1"/>
  <option name="DefaultContrast" value="-1"/>
  <option name="DefaultSaturation" value="-1"/>
  <option name="DefaultHue" value="-1"/>
  <option name="PrevChannel" value="4"/>
  <option name="FramerateMode" value="0"/>
  <option name="OverScan" value="3.5"/>
  <option name="CheckForSignal" value="1"/>
  <option name="AudioBoost" value="90"/>
  <option name="AlwaysOnTop" value="0"/>
  <option name="QuietScreenshots" value="0"/>
  <option name="UnmuteVolume" value="23130"/>
  <option name="Muted" value="0"/>
  <option name="V4LInput" value="0"/>
  <option name="AudioMode" value="mono"/>
  <option name="PalDKMode" value="0"/>
<option name="ColourInvert" value="0"/><option name="MirrorInput" value="0"/><option name="DeinterlaceMethod" value="AdaptiveAdvanced"/><option name="FullScreen" value="0"/></tvtime>
```

I also checked all of my volume controlls, for ALL audio devices, including the one on my card that is Alsa-7134, and it's showing all as unmuted and volume turned up. The sound still works in MPlayer, but not TVTime :-(

---

### Post by TheIdiotThatIsMe on 2009-06-09
Ok I believe I found the problem, and that's linking the sound between the tuner and my sound card, as apparently the software assumes this and doesn't actually push the sound from the tuner card device to the sound card. I read this is done with a cord, but where can I find a cord that goes from the TV Tuner audio out to the sound card in?

---

### Post by Mrazek on 2009-08-30
I hope you will be able to use the same cord as for connecting audio out from CD/DVD-ROM to sound card. Also there are cords with more connectors on both sides.
I think any HW technician will give you some for free.

---

### Post by Jose Catre-Vandis on 2009-08-30
> **Mrazek said:**
> I hope you will be able to use the same cord as for connecting audio out from CD/DVD-ROM to sound card. Also there are cords with more connectors on both sides.
I think any HW technician will give you some for free.

Yep, that's what I had to do with my TV card (internal). There should be a connector on your card that is the same as the one you used to need to connect your CDrom to the motherboard for sound, and you should also have a similar point on your motherboard. This should give you sound under TVtime. There are two types of connector lead, some with three wires, some with four, I needed the three wire one.

---

