---
title: "Problems with sound"
date: 2008-09-22
forum: Multimedia Software
---

### Post by emu42 on 2008-09-22
I posted this topic earlier in the "Multimedia Production" section, but that forum is rather inactive and so I hope I will get more response here.

Anyways, I have two main problems. First, most sounds (sounds made by programs, system sounds, etc.) are played at full volume regardless of sound settings. Second, Rosegarden doesn't make a sound, whether I have the JACK server running or not.

The original thread is here:
[http://ubuntuforums.org/showthread.php?t=915453](http://ubuntuforums.org/showthread.php?t=915453)

---

### Post by markbuntu on 2008-09-22
Can you adjust the sound anywhere?
Volume Control, have you tried changing device? 
alsamixer?
Are you using pulseaudio?
If so, do you have the Pulse Audio Volume Control (pavucontrol)?
Have you tried using that?

What sound card are you using?
Do any applications play sound?
Are they playing through jack or alsa or pulse audio?
What are your System/Preferences/Sound settings?

We need information.

---

### Post by emu42 on 2008-09-22
"Can you adjust the sound anywhere?"
  Is there a place to adjust the sound other than the main volume control?

"Volume Control, have you tried changing device?"
  Yes, with same results.

"alsamixer?"
  Not sure what you mean, but I am using Alsa.

"Are you using pulseaudio?"
  In the first topic, one poster suggested I install esound and  uninstall PulseAudio. Nothing changed.

"Have you tried using that [pavucontrol]?"
  I don't see the point, because I am not using PulseAudio.

"What sound card are you using?"
  Creative sound blaster audigy

"Do any applications play sound?"
  As I said in my post, applications other than Rosegarden play sound full blast.

"Are they playing through jack or alsa or pulse audio?"
  Rosegarden plays through JACK, with no sound. Other applications are playing through Alsa, with sound.

"What are your System/Preferences/Sound settings?"
  Pretty much as is described in the tutorial to use esound (set everything to Alsa, disable system sounds).

---

### Post by markbuntu on 2008-09-23
There is a terminal sound mixer alsamixer that you can call from a terminal but I find it much easier to use

gnome-alsamixer

which you can get with synaptic. Once it is installed you can find it in Applications/Sound and Video. This mixer may reveal what your problem is, it has more options than the mixer in the Volume Control. I really suggest you get it. You can also look in my guide for more extensive help:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by emu42 on 2008-09-24
I fixed the volume control by simply changing the "visible tracks" (sound manager->preferences) to the one that my sound was running through. Silly me.

Anyways, Rosegarden is still not making a sound. I'm guessing that it has to do with the JACK server, since that's where the sound is put through. Have any idea what is wrong?

---

### Post by eye208 on 2008-09-25
> **emu42 said:**
> Anyways, Rosegarden is still not making a sound. I'm guessing that it has to do with the JACK server, since that's where the sound is put through. Have any idea what is wrong?
Please post a screenshot of the settings dialog of QJackCtl.

---

### Post by markbuntu on 2008-09-25
Try these for setting up jack:


[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://jackaudio.org/faq](http://jackaudio.org/faq)

---

### Post by emu42 on 2008-09-26
> Try these for setting up jack:


[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[http://www.ubustu.com/globe/2007/05/...ubuntu-studio/](http://www.ubustu.com/globe/2007/05/...ubuntu-studio/)

[http://jackaudio.org/faq](http://jackaudio.org/faq)

When I try to toggle options, I only get errors when trying to run Jack. When I just use the default settings, I get a successful connection, which, in the link you posted, looks like this:

[http://www.ubustu.com/globe/wp-content/uploads/2007/05/jackmsgs.png](http://www.ubustu.com/globe/wp-content/uploads/2007/05/jackmsgs.png)

---

### Post by markbuntu on 2008-09-26
Can you post a screenshot of your jack control setup/setting screen. Also what errors you are getting and what you are trying to change.

Make sure that Rosegarden is connected to system playback in the connections box and check in Configure Rosegarden that in General Configuration/Behavior/ Sequencer Status.= it says MIDI OK, audio OK.

Can you record or playback anything with ardour or hydrogen?

---

### Post by emu42 on 2008-10-11
> Can you post a screenshot of your jack control setup/setting screen.

[IMG]http://img91.imageshack.us/img91/1369/screenshotsetupjackaudifl1.png[/IMG]

>  Also what errors you are getting and what you are trying to change.

Unfortunately, I am getting no errors in JACK or Rosegarden. Just no sound in Rosegarden.

> Make sure that Rosegarden is connected to system playback in the connections box and check in Configure Rosegarden that in General Configuration/Behavior/ Sequencer Status.= it says MIDI OK, audio OK.

Rosegarden is connected to system playback under Audio. Also, the sequencer status seems to be fine as well.

[IMG]http://img373.imageshack.us/img373/5947/screenshotsetupjackaudiny4.png[/IMG]

> Can you record or playback anything with ardour or hydrogen? 

I don't have a recording device, but Hydrogen playback works great with or without JACK. However I haven't figured out how to use Ardour. It does say that it is connected to JACK though.

---

### Post by emu42 on 2008-11-10
bump

---

### Post by emu42 on 2009-01-02
I'm also still using 8.04, I don't feel the need to upgrade at the moment. However I still can't get Rosegarden to work.

---

