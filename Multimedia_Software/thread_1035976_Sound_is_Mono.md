---
title: "Sound is Mono"
date: 2009-01-10
forum: Multimedia Software
---

### Post by Cheemag on 2009-01-10
After an epic struggle I've managed to get Sound Recorder to work
in Heron, however stereo sound recorded from streamed radio
or from Firefox is mono (left channel only). Or at least
only the left is available in Audacity and it although there is
sound from both speakers, I'm fairly sure it's mono.   :(

They're saved as .WAV - no means of saving as .MP3. Is .WAV mono
only?

---

### Post by namdung on 2009-01-10
In *Audacity==>Edit==>Preferences==>Audio IO==>Recording==>Channels*, select **2 Stereo.**

Audacity needs the file libmp3lame.so.0 to create mp3 which is proprietary format. This file can be downloaded and set in *Preferences==>Import/Export*.

WAV can have both mono and stereo channels.

BTW-I'm using Ubuntu 8.04.1 with Audacity 1.3.5b.

---

### Post by Cheemag on 2009-01-10
> **namdung said:**
> In *Audacity==>Edit==>Preferences==>Audio IO==>Recording==>Channels*, select **2 Stereo.**

Audacity needs the file libmp3lame.so.0 to create mp3 which is proprietary format. This file can be downloaded and set in *Preferences==>Import/Export*.

WAV can have both mono and stereo channels.

BTW-I'm using Ubuntu 8.04.1 with Audacity 1.3.5b.

I downloaded the Lame file yesterday but even so, Audacity
couldn't find it. I don't yet know how to copy/move/delete
files in Linux. Assuming I can find it, where does it go and
how can I move it?


I rather feel that, even if I get .MP3 working I'll still be
in mono.   :(

---

### Post by namdung on 2009-01-10
Did u follow my earlier instructions?

_Install LAME_
[http://audacityteam.org/wiki/index.php?title=Lame_Installation#Setting_Audacity_up_to_use_LAME](http://audacityteam.org/wiki/index.php?title=Lame_Installation#Setting_Audacity_up_to_use_LAME)

_Record in stereo_
[http://audacity.sourceforge.net/help/faq?s=recording&i=stereo](http://audacity.sourceforge.net/help/faq?s=recording&i=stereo)

---

### Post by Cheemag on 2009-01-11
> **namdung said:**
> In *Audacity==>Edit==>Preferences==>Audio IO==>Recording==>Channels*, select **2 Stereo.**

Audacity needs the file libmp3lame.so.0 to create mp3 which is proprietary format. This file can be downloaded and set in *Preferences==>Import/Export*.

WAV can have both mono and stereo channels.

BTW-I'm using Ubuntu 8.04.1 with Audacity 1.3.5b.

In Audacity's preferences (2) Stereo was already selected.

There's no Preferences|Import/Export in my copy of Audacity.

It's completely knackered now, the [X] at top right won't
kill the programme, only File|Exit gets me out of it.


"Couldn't find package libmp3lame.so.0"

---

### Post by Cheemag on 2009-01-11
> **namdung said:**
> Did u follow my earlier instructions?

_Install LAME_
[http://audacityteam.org/wiki/index.php?title=Lame_Installation#Setting_Audacity_up_to_use_LAME](http://audacityteam.org/wiki/index.php?title=Lame_Installation#Setting_Audacity_up_to_use_LAME)

_Record in stereo_
[http://audacity.sourceforge.net/help/faq?s=recording&i=stereo](http://audacity.sourceforge.net/help/faq?s=recording&i=stereo)

Later.

Synaptic tells me Lame is installed, Audacity seems to expect
it to be in /usr/lib/

I can't find /usr/lib either.

Audacity can load and play .MP3s but cannot export them.

---

### Post by goltoof on 2010-03-16
Did you ever find a solution to this?  I'm having the exact same issue, fresh install of linux.

Sound output works fine but Sound Recorder and Audacity only record left channel.  I tried everything discussed so far.

---

### Post by Cheemag on 2010-03-16
> **goltoof said:**
> Did you ever find a solution to this?  I'm having the exact same issue, fresh install of linux.

Sound output works fine but Sound Recorder and Audacity only record left channel.  I tried everything discussed so far.

In Audacity itself Edit>Preferences>Audio-In/Out>Channels> select Stereo. Other than that I don't know.

I gave up on Ubuntu and am now looking at Linux Mint-8 KDE.

---

