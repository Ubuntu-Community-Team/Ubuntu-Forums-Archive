---
title: "How do disable ATI HDMI audio device?"
date: 2008-06-29
forum: Multimedia Software
---

### Post by darkpark on 2008-06-29
When I first started running Ubuntu 8.04, I had a soundblaster x-fi and onboard realtek sound.  Since there's no official support for the X-FI's in linux, I was using the oboard realtek sound device in linux.  Recently, I found an old Turtlebeach Santa Cruz sound card so I threw that in my system since I know linux (and alsa) has had support for the old cs46xx sound chips.  Since installing the santa cruz, I disabled the onboard realtek sound but now Ubuntu defaults to the ATI HMDI sound device (comes with the ati hd3870).  So my question is this: How do I either disable the driver for the HDMI sound device (I think it uses the intel_hda driver) or make sure that the santa cruz is always me default sound device.  I normally set this via the sound preferences applet, but it doesn't seem to retain this setting past the current session.

---

### Post by stabbyjones on 2008-07-28
the answer may be in /etc/ati somewhere i'm not at home to check but if anyone works this out it would be great.

8.4 drivers don't have hdmi support (only 8.5 and 8.6 have given me the ati hdmi device) so you can go back to those.

---

### Post by Melcar on 2008-07-28
```
asoundconf list  #lists all sound devices in the system

asoundconf set-default-card (parameter)  #sets "parameter" as the default device
```

I think they need to be run as root (sudo).

---

### Post by stabbyjones on 2008-07-28
is there a way to blacklist the hdmi completely or will setting a default do that for me? i don't have a default so that could fix everything.

intermittently  after logging in i don't get any soundcard except hdmi audio which seems really strange that it's locking out other cards but mostly both will show up. 

When this happens i've had to restart alsa to look for the correct card.

#When there is no sound
    /etc/init.d/alsasound restart

#alternative when above doesn't work 
   /etc/init.d/alsasound stop
   /etc/init.d/alsasound start

This will usually pick up a soundcard, if it fails i have to power down rather than restart then switch back on.

i'll try setting a default in asoundconf tonight.

---

### Post by kramthegram on 2008-08-04
Check the thread entitled: **Comprehensive Sound Problem Solutions Guide v0.5e**
it's a sticky in multimedia, here is the link:[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")
In the top post there is a section labeled: 
**Configuring default soundcards / stopping multiple soundcards from switching**
you can use that to set each device to diferent hw settings, making the card you want hw0 should fix this problem

---

### Post by jimmal on 2009-01-09
cat /proc/asound/modules

vi /etc/modprobe.d/blacklist -> blacklist snd_hda_intel

---

### Post by whisp71 on 2009-08-12
I want to use onboard sound card, and it seems that HDMI audio messes things up.
snd-hda-intel module is used for both hdmi and onboard cards. what to do in that case?

---

### Post by markbuntu on 2009-08-12
This is about multiple sound cards

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---

