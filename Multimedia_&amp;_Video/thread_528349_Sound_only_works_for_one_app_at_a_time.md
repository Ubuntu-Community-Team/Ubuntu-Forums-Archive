---
title: "Sound only works for one app at a time"
date: 2007-08-17
forum: Multimedia &amp; Video
---

### Post by Scooter7 on 2007-08-17
Hi, I know you've seen this asked many times, and I've checked other threads regarding this subject, and have tried the various solutions I could find.

None have worked for me.

I use XMMS to play music, pidgin for chatting, and SMplayer for video.

I use ALSA for everything.

Here is my sound card information:

Vendor: Intel Corporation
Device: 82801G (ICH7 Family) High Definition Audio Controller
Bus Type: PCI

Pidgin's sound doesn't work when I'm listening to music in XMMS.   While XMMS is running, I can't hear anything in SMplayer.   And as long as XMMS is running, I can't use either VisualBoyAdvance, or zsnes.

I have installed alsa-oss, but this didn't help.

Is there any way to fix this without starting each app with 'aoss'?

Thanks,

---

### Post by Haz13r on 2007-08-17
Well, i got used to only using 1 app for sound.  I never knew you could use 2 apps with sound at the same time although you can on Windows.  I need help as well if you CAN do this.  Anyway, hope you get it all figured out!

---

### Post by Scooter7 on 2007-08-19
Well, I'm actually getting used to it to, but I'm pretty sure it can be done - in fact, I'm 99.9% sure worked before for me, on a different computer, with Ubuntu Edgy.

So if anyone can help, it'd be much appreciated.

---

### Post by highgeere on 2007-08-20
I was planning on starting a thread about this, so I'll just bump this one. I've gotten used to only one audio source at a time, but my wife starting bugging me about it. Now I have to at least try to find a solution. Any help is appreciated.

---

### Post by Scooter7 on 2007-08-20
Wow, a lot of people seem to want help on this one.

That said, if I find a solution, I'll post it here. ;)

---

### Post by sjv on 2007-10-04
Anyone have anything on this? I've been having this problem for some time. I know that Ubuntu can play multiple sounds at once, since my wife's laptop does it just fine. I recently tried installing pulseaudio, and I was able to get multiple sounds at once(totem), except I couldn't get audio through firefox, opera, or xmms. 

In fact similar to above, I'm almost positive this worked fine for me before, except I think I lost it between my dapper/edgy upgrade. This has got to be some stupid configuration hiccup somewhere. Anyone have any idea what setting I should look for?

Thanks,
Steve

---

### Post by pay on 2007-10-04
sjv,
     You will have to configure those apps to use pulse audio i.e. for pulseaudio site. 
** Firefox/Flash **

 Firefox uses OSS audio by default and can be configured to use a wrapper that redirects audio to ALSA (aoss), NASD (audiooss), ESD (esddsp), aRts (artsdsp), or PulseAudio (padsp).  Simply edit /etc/firefox/firefoxrc or ~/.mozilla/firefox/rc and set the following variable. 
 FIREFOX_DSP="padsp"

Audacious has a plugin for pulseaudio (a fork of xmms). Theres might be aplugin for XMMS aswell but I don't know. Besides xmms 1 has ceased development whereas audacious still has development. 

For soundcards that don't have hardware audio mixing, then you will need to use software mixing. With alsa I believe you can use dmix (I tried setting it up with little sucess in gentoo) or you can use pulseaudio as a replacement for Esd. I believe either oneday pulseaudio will be the default for gnome. Fedora already has pulseaudio as the default sound server.

---

### Post by Scooter7 on 2007-10-04
Well, I just reinstalled Ubuntu Feisty, and sound works fine for me now, oddly enough.

---

### Post by sjv on 2007-10-05
On a suggestion from a friend I tried creating a different user account on the system, and seeing if the audio worked. I logged in, and everything worked fine. So it's something specific to my account. The question is what? Any ideas or suggestions on which files I should compare?

Thanks

---

