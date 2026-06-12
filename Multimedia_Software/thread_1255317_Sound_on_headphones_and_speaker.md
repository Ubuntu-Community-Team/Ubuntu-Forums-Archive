---
title: "Sound on headphones and speaker"
date: 2009-09-01
forum: Multimedia Software
---

### Post by chloraldo on 2009-09-01
Hi all

I have a HP dv6 laptop. I have set the sound to Pulse.
It works, but I get sound over my headphones and my speakers.

How can I turn off the speakers when headphones are plugged in?

Thanks a lot

---

### Post by bootdoc on 2009-09-02
goto applications>sound and video>pulseaudio device chooser(pad)  this will put and icon on the panel.  left click icon and choose volume control.  goto the playback tab and right or left click on the stream and there should be a choice of headphones, front speakers or both.  Choose one.:)

---

### Post by chloraldo on 2009-09-03
> **bootdoc said:**
> goto applications>sound and video>pulseaudio device chooser(pad)  this will put and icon on the panel.  left click icon and choose volume control.  goto the playback tab and right or left click on the stream and there should be a choice of headphones, front speakers or both.  Choose one.:)

In the playback tab I only have System Sounds Mono, Output I have HDA Intel - STAC92xx Analog with Front Left and Right. Have I got something wrong there?

---

### Post by bootdoc on 2009-09-03
did you start the stream before going to PAD(pulseaudio device chooser)?  it will only display options when something is playing i.e. amarok, banshee, mplayer, etc. etc.

if you haven't read this [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449") I suggest you do so.  Pulse is a PITA.

I replaced pulse with esound [http://ubuntuforums.org/showthread.php?t=1230561&highlight=pulse+esound]("http://ubuntuforums.org/showthread.php?t=1230561&highlight=pulse+esound")

---

### Post by bootdoc on 2009-09-03
OK I just reinstalled Pulseaudio.  you have to make sure your sound settings are correct.  goto system>prefernces>sound.  set the first three items to Pulseaudio sound server.  Sound capture should be set also to pulse unless the mic you are using shows in the list.  If headphones have a mic then pulseaudio sound server should do it.  The 5th item (default mixer tracks should be set to your sound card alsa.  

If you goto preferences in PaDevChooser you can set it to start applet on session login.

Now open pulseaudio device chooser and choose configure local sound server.  check enable network access to local sound devices.  Not sure if this is needed but it doesn't hurt.  Next click on simultaneous output tab and check add virtual output device.  This enables streaming one playback device to speakers and another playback device to headphones.

start your favorite media player (start some music or video) and open padevchooser and click on volume control>playback tab.  Your media player should be listed there.  look closely you will see a pull down menu to the right of the playback which gives you the choice of output devices.  One problem I run into is that the headphones have to be plugged in before logging in.

---

