---
title: "Audacious won't play"
date: 2008-12-18
forum: Multimedia Software
---

### Post by ftmichael on 2008-12-18
A few days ago, Audacious stopped playing for me; pressing the Play button gives me an elapsed time of 00:00 and nothing else happens.  It won't play either streaming live audio or plain audio files on my hard drive.  I uninstalled it and deleted **~/.config/audacious**, then reinstalled it. Same exact problem.

When I run it from a terminal, pressing play gives me this error:

```
** (audacious:15696): WARNING **: Failed to connect to server: Connection refused
```

That could be understandable when I'm trying to play a live stream (although vlc plays the same stream with no problems), but why is it trying to connect to a server when I'm trying to play an ordinary music file on my hard drive?  It gives the same exact error no matter what I try to play with it.

Ordinarily I'd happily just use vlc, but I use Audacious's Alarm plugin to get up in the morning, and vlc doesn't seem to have such a plugin.  I prefer lightweight, unobtrusive media players, and I have no need for an application that indexes my stuff, so I'm not really interested in something like Rhythmbox.  I'd like Audacious to just work!

---

### Post by rjpilla on 2008-12-18
I just had the same thing happen to me hope somebody has figured this out.

---

### Post by rjpilla on 2008-12-18
Solved use the following command in the terminal

rm -rf ~/.config/audacious

---

### Post by ftmichael on 2008-12-18
I already removed all of ~/.config/audacious and that didn't help.

---

### Post by Bootsy Collins on 2008-12-19
The "server" in question is almost certainly the PulseAudio server -- it's not some network-based server machine, but rather a server application assumed to be running on your machine.  It "serves" sound to your computer's sound hardware.  It's normally started as part of GNOME upon login, and its main purpose (among other purposes) is to handle mixing of simultaneous sound from multiple sources together before passing the combined sound to the soundcard.  The reason for this is because some (mostly older) soundcards can't do such mixing in the hardware -- when a sound arrives at such a card while another sound is playing, the second sound (and the application trying to play that sound) will hang until the soundcard becomes free.

Assuming I'm right, try this:

1.  Open Audacious, and bring up your preferences (ctrl-p)
2.  Click on Audio
3.  At the top, there'll be a pulldown called "Current output plugin".  Change that from "PulseAudio Output Plugin" to "ALSA Output Plugin".  That causes Audacious to communicate directly with the drivers for the soundcard.
4.  Close Preferences.  You may need to restart Audacious, but I don't think you do.
5.  Verify that you can play stuff OK.

If it doesn't work, then I'm wrong, and I don't know what your problem is.

If it does work, you're not yet done.  You've fixed the immediate problem -- you have sound from Audacity -- but you still have some questions to ask yourself (and answer):

a)  Why did the pulseaudio server not process the sound?  Is it not running?  Presumably it'll restart the next time I log in under GNOME.

b)  Can my soundcard do hardware mixing?  (you can test this by sending two sounds directly to ALSA from different apps at the same time)  If it can, then I probably don't need the pulseaudio server to run -- it just increases sound playback latency and introduces one more thing that can go wrong.  If it can't, then having Audacious output directly to ALSA means it'll hang onto the soundcard whenever it's playing something, allowing no other sounds to play until Audacious exits (and often forcing the other aps that want to play sounds to hang until then).  In that case, you'll need to get pulseaudio or something like it working.

As an aside, in that pulldown menu for output plugin, you may have seen some other things that looked like "aRts output plugin," "ESD output plugin," and "JACK output plugin."  Those are other sound server applications that function similarly to pulseaudio.  I'm new to ubuntu and don't know why it uses pulseaudio over ESD, which is what GNOME used to use.  aRts is used by KDE.  JACK is a special case -- it's a sound server designed for use in pro-audio environments.  In general, if you don't know anything about these, it's probably not worth your while to mess with them (and definitely Audacious shouldn't be pointing at them if they're not running).

Hope this helps.

-c

---

### Post by ftmichael on 2008-12-19
I swear I tried that earlier and it didn't work, but probably that was just Audacious sucking in other ways.  This time it worked.  Thanks!

New question, then: How do I get Audacious to not randomly reset my preferences to whatever it feels like from time to time?  I don't want to have to keep reminding it to use ALSA, or that I need an alarm at a given time, etc.  The alarm plugin in particular likes to lose my settings and just make up random stuff every now and then.

---

### Post by markbuntu on 2008-12-19
> **Bootsy Collins said:**
> The "server" in question is almost certainly the PulseAudio server -- it's not some network-based server machine, but rather a server application assumed to be running on your machine.  It "serves" sound to your computer's sound hardware.  It's normally started as part of GNOME upon login, and its main purpose (among other purposes) is to handle mixing of simultaneous sound from multiple sources together before passing the combined sound to the soundcard.  The reason for this is because some (mostly older) soundcards can't do such mixing in the hardware -- when a sound arrives at such a card while another sound is playing, the second sound (and the application trying to play that sound) will hang until the soundcard becomes free.

Assuming I'm right, try this:

1.  Open Audacious, and bring up your preferences (ctrl-p)
2.  Click on Audio
3.  At the top, there'll be a pulldown called "Current output plugin".  Change that from "PulseAudio Output Plugin" to "ALSA Output Plugin".  That causes Audacious to communicate directly with the drivers for the soundcard.
4.  Close Preferences.  You may need to restart Audacious, but I don't think you do.
5.  Verify that you can play stuff OK.

If it doesn't work, then I'm wrong, and I don't know what your problem is.

If it does work, you're not yet done.  You've fixed the immediate problem -- you have sound from Audacity -- but you still have some questions to ask yourself (and answer):

a)  Why did the pulseaudio server not process the sound?  Is it not running?  Presumably it'll restart the next time I log in under GNOME.

b)  Can my soundcard do hardware mixing?  (you can test this by sending two sounds directly to ALSA from different apps at the same time)  If it can, then I probably don't need the pulseaudio server to run -- it just increases sound playback latency and introduces one more thing that can go wrong.  If it can't, then having Audacious output directly to ALSA means it'll hang onto the soundcard whenever it's playing something, allowing no other sounds to play until Audacious exits (and often forcing the other aps that want to play sounds to hang until then).  In that case, you'll need to get pulseaudio or something like it working.

As an aside, in that pulldown menu for output plugin, you may have seen some other things that looked like "aRts output plugin," "ESD output plugin," and "JACK output plugin."  Those are other sound server applications that function similarly to pulseaudio.  I'm new to ubuntu and don't know why it uses pulseaudio over ESD, which is what GNOME used to use.  aRts is used by KDE.  JACK is a special case -- it's a sound server designed for use in pro-audio environments.  In general, if you don't know anything about these, it's probably not worth your while to mess with them (and definitely Audacious shouldn't be pointing at them if they're not running).

Hope this helps.

-c

If you don't know something, you should find out. Like you could find out that pulseaudio has zero latency and resolves problems that ESD cannot. You will also find that if you have libasound2 and libasound2-plugins then audacious will play through the pulseaudio sound server wether it is set to pulseaudio or alsa or oss and other applications can share the sound card.

If you really want to learn about sound in Ubuntu you can go here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

If that is too much for you and you just want a quick solution to getting your sound set up properly in Intrepid or Hardy you can go here

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by Ze MoreiRa on 2009-06-17
> **Bootsy Collins said:**
> The "server" in question is almost certainly the PulseAudio server -- it's not some network-based server machine, but rather a server application assumed to be running on your machine.  It "serves" sound to your computer's sound hardware.  It's normally started as part of GNOME upon login, and its main purpose (among other purposes) is to handle mixing of simultaneous sound from multiple sources together before passing the combined sound to the soundcard.  The reason for this is because some (mostly older) soundcards can't do such mixing in the hardware -- when a sound arrives at such a card while another sound is playing, the second sound (and the application trying to play that sound) will hang until the soundcard becomes free.

Assuming I'm right, try this:

1.  Open Audacious, and bring up your preferences (ctrl-p)
2.  Click on Audio
3.  At the top, there'll be a pulldown called "Current output plugin".  Change that from "PulseAudio Output Plugin" to "ALSA Output Plugin".  That causes Audacious to communicate directly with the drivers for the soundcard.
4.  Close Preferences.  You may need to restart Audacious, but I don't think you do.
5.  Verify that you can play stuff OK.

If it doesn't work, then I'm wrong, and I don't know what your problem is.

If it does work, you're not yet done.  You've fixed the immediate problem -- you have sound from Audacity -- but you still have some questions to ask yourself (and answer):

a)  Why did the pulseaudio server not process the sound?  Is it not running?  Presumably it'll restart the next time I log in under GNOME.

b)  Can my soundcard do hardware mixing?  (you can test this by sending two sounds directly to ALSA from different apps at the same time)  If it can, then I probably don't need the pulseaudio server to run -- it just increases sound playback latency and introduces one more thing that can go wrong.  If it can't, then having Audacious output directly to ALSA means it'll hang onto the soundcard whenever it's playing something, allowing no other sounds to play until Audacious exits (and often forcing the other aps that want to play sounds to hang until then).  In that case, you'll need to get pulseaudio or something like it working.

As an aside, in that pulldown menu for output plugin, you may have seen some other things that looked like "aRts output plugin," "ESD output plugin," and "JACK output plugin."  Those are other sound server applications that function similarly to pulseaudio.  I'm new to ubuntu and don't know why it uses pulseaudio over ESD, which is what GNOME used to use.  aRts is used by KDE.  JACK is a special case -- it's a sound server designed for use in pro-audio environments.  In general, if you don't know anything about these, it's probably not worth your while to mess with them (and definitely Audacious shouldn't be pointing at them if they're not running).

Hope this helps.

-c

You Rock
thanks

---

### Post by Huzudra on 2009-06-18
same problem as OP, audicious just up and stopped working after a reboot ad i don't know why. i tried some of the above stuff and nothing. aqualung works but is laggy to respond to song changes and runs like poo in general.

---

### Post by JamesSmith on 2009-08-26
(Jaunty)

Changing the audio output plugin to ALSA didn't work for me.  I don't know exactly when audacious stopped working but I can only assume it was after an update that happened recently.

I was about to try deleting the audacious config file in ¬/.config/audacious, but did wonder whether anyone had investigated exactly what setting in this config file is causing a/the problem? I don't like just deleting something and forcing a solution this way.

James

---

### Post by JamesSmith on 2009-08-26
Well, having made a backup of the config file and deleted the original, audacious did play my music.

I went back into preferences to have a poke around.  Firstly, the default output driver is PulseAudio - so I've left that as is.  Secondly, apparently setting the output bit depth to 24 causes audacious to not play my files and stick at 00:00 - for me anyway.

btw my machine is an Acer Aspire One (AOA150Ab) netbook.

J

---

### Post by Vasile on 2009-09-05
> **ftmichael said:**
> 
New question, then: How do I get Audacious to not randomly reset my preferences to whatever it feels like from time to time?  I don't want to have to keep reminding it to use ALSA, or that I need an alarm at a given time, etc.  The alarm plugin in particular likes to lose my settings and just make up random stuff every now and then.


I also have this problem. How can I stop audacious to randomly change my audio driver or my mixer?

---

### Post by Bondy_uk on 2009-10-09
> **JamesSmith said:**
> apparently setting the output bit depth to 24 causes audacious to not play my files and stick at 00:00 - for me anyway.

Thank you!

I tried changing to Alsa Mixer before reading this, then the other things here and it just wasn't working at all for me. It happened when updating to 9.04.

However, I put everything back to default (even PulseAudio), then changed the bit depth from 24 to 16 and its working perfectly now!!!!!!

:guitar:

---

### Post by kickula on 2010-01-07
I'm having the same problem, except changing to the ALSA mixer didn't help me. Any other tips? It's not even pretending to be playing, just stuck on 00:00. 

Thanks in advance,
-linux n00b

---

### Post by elitenoobboy on 2010-01-07
> **kickula said:**
> I'm having the same problem, except changing to the ALSA mixer didn't help me. Any other tips? It's not even pretending to be playing, just stuck on 00:00. 

Thanks in advance,
-linux n00b

What version of audacious are you using? The latest version is 2.2, while the version in the repos is still 2.1 IIRC. Try upgrading to the latest version and see if that helps.

---

### Post by kickula on 2010-01-12
> **elitenoobboy said:**
> What version of audacious are you using? The latest version is 2.2, while the version in the repos is still 2.1 IIRC. Try upgrading to the latest version and see if that helps.

I got mine from the Synaptic stuff, which says the latest version is "1.5.1-4ubuntu3". How do I update it? 
*n00b*

PS: I downloaded the package that's just called "audacious", nothing fancy.

---

### Post by elitenoobboy on 2010-01-12
> **kickula said:**
> I got mine from the Synaptic stuff, which says the latest version is "1.5.1-4ubuntu3". How do I update it? 
*n00b*

PS: I downloaded the package that's just called "audacious", nothing fancy.

Your best bet is to download from a ppa, as the debs may have other dependencies. Go to [https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra)  There are instructions on how to install it there, and after that upgrading should be easy through updatemanager.

---

