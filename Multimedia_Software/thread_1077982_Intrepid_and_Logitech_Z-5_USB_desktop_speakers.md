---
title: "Intrepid and Logitech Z-5 USB desktop speakers"
date: 2009-02-22
forum: Multimedia Software
---

### Post by raymondvillain on 2009-02-22
Using 8.10 Intrepid.  Noob.  Needed basic speakers for my desktop, so I went to Best Buy and picked up a scratch & dent box of Logitech Z-5 USB speakers.  I forgot all about system requirements etc.  So I get home and hook up the speakers, and THEN I see that "Windows Vista or Windows XP" are the only supported OS's.  Went to these forums and searched on "Logitech Z-5" but nothing at all turned up.  I'm on the verge of taking them back, but I tried them out, just for kicks.  No sound.  Went to system>preferences>sound and on the devices tab they appeared as one of the choices on the drop-down list!  So I selected them and I have sound on Rythmbox.  Even the remote control works.  And I never installed any software!  Linux gets better and better.

There is a glitch, though, and I'm hoping somebody knows how to get around this.

Rythmbox works with them and their remote control, but Amarok doesn't seem to see them.  Any suggestions?

---

### Post by Master Siege on 2009-02-23
I also have these speakers in ubuntu.

I couldn't get them completely working with just the USB.
Rythym box would work but not youtube via firefox etc.

So I just used the auxilary port on the back straight from my sound card.
The USB is basically just for the power in this case.

I'm debating if I should take them back because only the volume and power works on the remote not the next/previous track and play/pause buttons.

I wish logitech would support linux.

Let me know if anyone else has better luck.

---

### Post by kostkon on 2009-02-23
> **raymondvillain said:**
> Using 8.10 Intrepid.  Noob.  Needed basic speakers for my desktop, so I went to Best Buy and picked up a scratch & dent box of Logitech Z-5 USB speakers.  I forgot all about system requirements etc.  So I get home and hook up the speakers, and THEN I see that "Windows Vista or Windows XP" are the only supported OS's.  Went to these forums and searched on "Logitech Z-5" but nothing at all turned up.  I'm on the verge of taking them back, but I tried them out, just for kicks.  No sound.  Went to system>preferences>sound and on the devices tab they appeared as one of the choices on the drop-down list!  So I selected them and I have sound on Rythmbox.  Even the remote control works.  And I never installed any software!  Linux gets better and better.

There is a glitch, though, and I'm hoping somebody knows how to get around this.

Rythmbox works with them and their remote control, but Amarok doesn't seem to see them.  Any suggestions?
No you did it the wrong way.

And, of course, there is an explanation why only *Rhythmbox* works. The sound preferences work only for *Gstreamer* based applications like *Rhythmbox* is.

The thing you need to do is to install the *PulseAudio Device Chooser* utility (it will have a menu entry in *Applications &#8594; Sound & Video*). Run it, left-click on its icon in your system tray and select *Volume Control*.

From there you will be able to send the audio stream of one application from one device to another in real time. In the *Playback* tab you should see the audio streams of your running applications (the ones that produce audio only, of course). Right-click on one and select Move Stream... to move its audio to the device you want.

In the *Input Devices* and *Output Devices* tabs you can set the default input and output device to be used by your applications. Right-click on the device you want and enable the *Default* option. Thus, I assume you'll want to set here your speakers as the default output device. Afterwards, all your applications will send their audio there by default.

For this to work, you should set all your sound playbacks in *System &#8594; Preferences &#8594; Sound* to **Autodetect** (and if you want your inputs to *PulseAudio*), because you have changed them.

You can set *PulseAudio Device Chooser* to start every time you login from its preferences.

Hope that helps...

---

### Post by raymondvillain on 2009-02-23
Thanks, Kostkon, glad to know somebody out there has figured this out.

Are there any tricks to setting up Pulseaudio device chooser?

I have Amarok ( or Rythmbox, result is the same) playing a CD track, and under "Volume Control" on Pulseaudio device chooser (Playback tab) there are no entries, just an empty box with "No application is currently playing audio".

If I use Rythmbox, the Output Devices tab (of pulseaudio volume control) shows my USB speakers.  If I run Amarok, the same tab sort of reflects a choice I make in the "Configure Amarok) box (under settings).

If you have any more insight, please share.  Thanks,
raymondvillain

---

### Post by raymondvillain on 2009-02-23
> **Master Siege said:**
> I also have these speakers in ubuntu.

I couldn't get them completely working with just the USB.
Rythym box would work but not youtube via firefox etc.

So I just used the auxilary port on the back straight from my sound card.
The USB is basically just for the power in this case.

I'm debating if I should take them back because only the volume and power works on the remote not the next/previous track and play/pause buttons.

I wish logitech would support linux.

Let me know if anyone else has better luck.

I can get the remote to cause Rythmbox or Amarok to jump to the next track and also to a previous track, but nothing else.  If I try to use the remote to change the volume, a window appears with a symbol of a speaker and (I guess) sound waves, and a box that is partially filled to indicate the percentage of volume selected, but the sound volume coming out of my speakers does not change.  Same for the on-off button on the remote.

The pause-play button on the remote works in Rythmbox but not Amarok.

If you learn any more, please post same.

---

### Post by raymondvillain on 2009-02-24
I learned a little bit more.  If I go to system>preferences>sound and change the "default mixer tracks" selection to "Logitech Z-5 speakers (Alsa mixer)" then the remote control that comes with the Logitech speakers will increase and decrease the volume in Amarok.

A good article to read is

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

Hope this helps.

---

### Post by Marcus_Ophiuchus on 2009-03-14
Man, I can't even get the option to show up in my Devices tab.

Taking my speakers back is less of an option, considering they're the only pair I have.  Any help on this?

---

### Post by Smashing Pumpkin on 2009-03-26
Same here.... got some Logitech Z-5 speakers but I'm really struggling to get them to work in Xubuntu Intrepid. At the moment, I have some wireless headphones plugged in to my soundcard socket so I'm using that, but I'd love to work out how to get the sound coming from the USB socket and through the Z-5 speakers.

I've installed PulseAudio as it's recommended in some threads and although it seems to be working (I can connect to it) I've not got a clue what it's actually used for and what needs to be changed to get the sound through the Z-5's.

Has anyone managed to actually get these to work? I'd love to get some advice on what needs to be done.

---

### Post by markbuntu on 2009-03-26
The problem with the Z5 is that it does not use standard usb protocols and logitech will not release the info so the driver writers can fix it. You guys should complain loudly to logitech about this.

---

### Post by nikarul on 2009-06-16
FYI, I was able to get my Z-5 speakers working through USB in Kubuntu 9.04 by following the instructions for setting up PulseAudio here:  [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

KDE is able to play through them fine and after I set up Pulse Audio I was able to play Pandora through them from Firefox.

  -Michael

---

### Post by hedgom on 2009-08-06
Hi you all!

I had the same problem and kostkon's tip worked just fine for me! (pulse audio applet!) thanks!

---

### Post by erikthedrink on 2009-09-08
I've got logitech usb speakers too.  In Xubuntu, go to Applications, then Accessories, then Terminal.  In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:P
Note, if you unplug your usb speakers, your laptop speakers will take over.  In order to re-establish contact with the usb speakers, you will need to (plug them back in) restart the system.

---

### Post by iGeorgie on 2009-10-03
Just installed Ubuntu 9.10 Beta.

1. Plug in the Logitech Z-5.
2. Go to Sound Preferences, Output and select Z-5.
3. Done!

Everything else works out of the box, even the remote!:KS

---

### Post by sentinel23 on 2010-01-14
Anyone know if the infrared receiver in the speakers could be used (presumably with lirc) with another remote - to control more than just the speakers?

If so, these would be perfect for my MythTV (Mythbuntu 9.10) frontend machine! No separate IR receiver to clutter up my setup!!

(Though I'm a bit worried that the "omnidirectional" aspect of them would cause sound to be blasted into the wall I share with the neighboring apartment, instead of just to me...)

---

### Post by RiddleRose on 2010-02-05
So I got the z-5 speakers as a gift, and thus really don't want to get rid of them.  After fooling around for a while I managed to get them to play music from RhythmBox, but the remote control doesn't work at all.  It won't even turn them on or off.  Changing the volume on the computer or in RhythmBox also does nothing.  This is really annoying, because I live in a dorm room and my neighbours will certainly not appreciate me playing music extremely loudly.  Not to mention the fact that the default volume setting is far too loud for my tiny box of a room.  Any tips?

Less important but still annoying is the fact that they won't play sound from youtube, pandora,  etc.  I can deal with that, but it is a little bothersome.

Thanks!

---

### Post by newyorkcityjay on 2010-07-31
The speakers work fine for me out of the box on Lucid-AMD-64, but the volume is screwy - it can only be at 100% or higher so I have to keep the applications volume set very low and cannot use keyboard controls... I tried messing with the alsa-base.conf file as describe here <http://kubuntuforums.net/forums/index.php?topic=3112023.0> but that killed the speakers all together... so.... they work, just with poor control over volume.  Any ideas?

---

