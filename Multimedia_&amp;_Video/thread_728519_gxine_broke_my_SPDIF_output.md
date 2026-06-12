---
title: "gxine broke my S/PDIF output"
date: 2008-03-18
forum: Multimedia &amp; Video
---

### Post by unitek on 2008-03-18
Hi!

I hope you all feel good!  As the subject of this post tells, I have a sound problem.  First, here is my configuration:

OS: Ubuntu 7.10 (32-bit)
CPU: AMD AthlonXP
MB: Asus A7N8X 2.0 (nForce2, on-board sound disabled)
SC: Creative Labs Soundblaster Audigy LS
SS: Cambridge Soundworks DTT3500 Digital (using S/PDIF jack)

All of this has to do with DVD playback.  The first thing I did was installing all the necessary gstreamer plug-ins suggested by Totem Movie Player, plus libdvdread3 and libdvdcss2, to be able to watch encrypted DVD's.  It worked, but it was only able to read DVD's at autoplay (when I first inserted the disc in the tray).  It also couldn't seek and couldn't play certain DVD's.  So I installed Totem Movie Player with xine backend (uninstalling Totem Movie Player with gstreamer backend).  Now I could seek and play a disc after I had closed Totem.  Fine!  But certain DVD's still couldn't play.  That's when I installed gxine.  It could play DVD's that wouldn't work with Totem!  Oh great!

But that's where trouble begins.  I shut gxine and realized I had lost S/PDIF digital output.  Nothing would play at all.  So I uninstalled everything xine.  Sound came back!  All right!  A couple of days later...  Oh man!  I don't want to go back to Windows XP just because of DVD playback!  There must be a way.  DELL has DVD playback pre-installed on some machines without broken sound, doesn't it?  Went back to xine to be able to play all my DVD's with seek, etc.  Closing gxine broke digital out again!  But the passthrough still works for DVD's.

I need to get digital out running again.  Please take note that I am new to the Linux/Ubuntu world.

Thanks for all your feedback!

Steve

---

### Post by erginemr on 2008-03-19
OK. I also favor totem-xine and gxine and have been using them exclusively for video playback, but if you are having problems with sound only when xine is installed, I suggest you to return to totem-gstreamer, uninstall gxine and try one of the two big boys of the Linux world when it comes to video playback: **mplayer** or **vlc**. Both players are available in the repositories.

Try mplayer and vlc both for playing DVD movies, I am sure you will like either one.

---

### Post by unitek on 2008-03-19
Thanks!

But it seems that xine (or gxine) may not be THE problem, precisely.  I uninstalled everything xine, but sound didn't come back.  There was totem-xine remaining, so I installed totem-grstreamer (that allowed me to uninstall totem-xine at the same time).  Still no sound.

Finally, I uninstalled totem-gstreamer in an attempt to remove any sticky setting.  Still there's no S/PDIF output available from the sound card, even though IEC958 is checked in the "Contrôleur de volume" (GNOME volume controller?).

Is there any way to set the card (or ALSA) back up, a reset or something?  AC3 Passthrough seems to be sticked in somewhere...  I'm not sure it is related to ALSA, as my sound preferences are set to Automatic detection, but it did work that way before and I just tested specific devices to no avail.  The only error I get is when testing ESD (server not found).

Thank you for any feedback!

Steve

---

### Post by erginemr on 2008-03-20
Even though you have disabled the onboard sound card, I am suspecting that it may still be interfering with the SB Audigy card. So, in an effort to identify the problem, could you please cost the outcome of the following commands from the terminal:
```
aplay -l
```
```
lspci | grep -i audio
```
```
cat /proc/asound/cards
```

---

### Post by unitek on 2008-03-20
There it is:

```
aplay -l
```

**** Liste des PLAYBACK périphériques ****
carte  0: CA0106 [CA0106], périphérique 0 : ca0106 [CA0106]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: CA0106 [CA0106], périphérique 1 : ca0106 [CA0106]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: CA0106 [CA0106], périphérique 2 : ca0106 [CA0106]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: CA0106 [CA0106], périphérique 3 : ca0106 [CA0106]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

```
lspci | grep -i audio
```

01:0a.0 Multimedia audio controller: Creative Labs SB Audigy LS

```
cat /proc/asound/cards
```

 0 [CA0106         ]: CA0106 - CA0106
                      AudigyLS [SB0310] at 0xc800 irq 20
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10

---

### Post by erginemr on 2008-03-20
Based on these results, it turned out that I was wrong. It is clear that your onboard sound card is not interfering with Audigy...

---

### Post by unitek on 2008-03-20
Hi!

That's all right, then!
But now, any idea how to turn AC3 Passthrough off and digital out (S/PDIF) on?

Maybe I would be able to watch a DVD with AC3 Passthrough, as it was the case before I uninstalled everything movie-related, but what's for sure now it that I can't get any sound / music out of the sound card.

When on DOLBY DIGITAL / PCM AUDIO (passthrough / movie mode), the receiver is all right.  When on MULTI-CHANNEL, DIGITAL DIN's green light keeps flashing.

Any feedback would be much appreciated! :)

Thanks!

Steve

---

