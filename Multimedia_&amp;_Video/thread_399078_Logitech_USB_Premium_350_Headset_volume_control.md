---
title: "Logitech USB Premium 350 Headset volume control"
date: 2007-04-01
forum: Multimedia &amp; Video
---

### Post by Brayden on 2007-04-01
Hi!

I've just installed Ubuntu Edgy 6.10 yesterday - and love it! I'm sort of a novice when it comes to Linux, but I seem to have everything going, except a couple of things - one of them being this.

My headset is a Logitech USB Premium 350. Ubuntu detected and installed it appropriately and the sound works fine - however when I try and adjust the volume via the control on the headset, the meter comes up on the screen as if it is adjusting the volume, but it doesn't. 

I have all the latest updates for packages etc via Update Manager.

Any ideas? I think it is using the ALSA driver if that helps - if you need any more info, just ask. :)

Thanks in advance,

Brayden

---

### Post by Brayden on 2007-04-03
Anyone?

---

### Post by rockstar on 2007-04-04
[http://www.linuxforums.org/forum/suse-linux-help/63903-logitech-usb-headset-not-working.html](http://www.linuxforums.org/forum/suse-linux-help/63903-logitech-usb-headset-not-working.html)

---

### Post by Brayden on 2007-04-04
Hi,

Thanks for your reply. Unfortunately none of that is relevant to my issue - the headset works & is the default sound device - but I cannot get the in-line volume control to work.

---

### Post by anchor on 2007-05-09
I encountered the same problem you are having a couple of days ago.

I'm pretty sure the problem is related to the default alsamixer being used.

try this:

open a terminal and type "alsamixer" (without the quotes)

Try adjusting the volume via the headset's control.  If you notice the "master" volume changing as you do this, then it is most likely an issue with the default alsamixer.

To change the default alsamixer, you'll need to determine which card number ubuntu assigns to your headset.

run the following command:

```

cat /proc/asound/cards

```


Look for a line similar to this:

```

 1 [Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:1d.1-1, full

```

Where "1" is the card number assigned to the device by ubuntu.


Almost done.  In terminal run the following command:
```

sudo gedit /etc/asound.conf

```

Paste the following into the empty text document:  NOTE - replace the # with the card number you determined in the previous steps.  

```

pcm.!default {
    type hw
    card #
}
ctl.!default {
    type hw
    card #
}

```

Save the file and then reboot your PC.  You should now be able to control the volume via your headset control.

---

### Post by dir3wolf on 2007-05-11
> ```

pcm.!default {
    type hw
    card #
}
ctl.!default {
    type hw
    card #
}

```

Save the file and then reboot your PC.  You should now be able to control the volume via your headset control.

Now I can control mic volume with the remote, but still can't control speakers ;-)

---

### Post by Unix_Wizard on 2007-05-11
This problem persists! In feisty trying to change the volume using the volume control or keyboard shortcuts both result in the mic volume changing. 
So does anyone know how to change it so the headset volume is changed instead of the mic? I want to be able to change the global volume during my games. I'll take any solution that works for that.

Here's the output of cat /proc/asound/devices 

  2:        : timer
  3:        : sequencer
  4: [ 1- 0]: digital audio playback
  5: [ 1- 0]: digital audio capture
  6: [ 1]   : control

I want to control the volume for playback not capture!

---

### Post by anchor on 2007-05-11
> **dir3wolf said:**
> Now I can control mic volume with the remote, but still can't control speakers ;-)

Heh, at least we're getting close to a solution :)

Would you mind posting the output of

```

cat /proc/asound/cards

```

and

```

cat /proc/asound/devices 

```


I feel silly asking this but, you did remember to edit this:

```

pcm.!default {
    type hw
    card #
}
ctl.!default {
    type hw
    card #
}

```

to contain your card number?  In my case.

```

pcm.!default {
    type hw
    card 1
}
ctl.!default {
    type hw
    card 1
}

```


It should be noted that I had to create the following file

```

gedit ~/.asoundrc

```

with the following.

```

pcm.!default {
type plug
slave.pcm "combined"
}

pcm.combined {
type asym
playback.pcm "playback"
capture.pcm "hw:1,0"
}

pcm.playback {
type dmix
ipc_key 1024
slave {
pcm "hw:1,0"
period_time 0
period_size 1024
buffer_size 4096
rate 44100
}
bindings {
0 0
1 1
}
}

ctl.dmixer {
type hw
card 1
}

```


Just to  get ubuntu to use my logitech headset as the default sound device.  Prior to this it would only output sound from my internal laptop speakers.

---

### Post by Unix_Wizard on 2007-05-12
my .asoundrc is identical to yours. 

cat /proc/asound/cards
 1 [Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:0a.0-1, full speed

Just need to figure out how to link the keyboard shortcut and/or headset volume button to change the headset's volume instead of the mic. No such luck yet. Btw I never had to create an .asoundrc to get audio to work for the same setup for dapper, breezy or warty. The audio output problem is upstream alsa debian I'm not sure about the volume control problem. Someone should file a bug report for both.

---

### Post by Unix_Wizard on 2007-05-13
Looks like there's more to it. The microphone doesn't show up in sound recorder so I can't record anything at all with it. Yet in volume control the slider for microphone capture is there. Any ideas?

---

### Post by blazoner on 2007-06-12
I had the same problem, and the solution was simple.

After getting my USB headset to work as my default Alsa device, I went into system -> preferences -> sound, and under the Devices tab set "Default Mixer Tracks" to "Logitech USB Headset", and chose "Speaker" from the menu instead of "Microphone Capture". (This tells ALSA what to do when the keyboard shortcut keys are pressed.  The headset sends these same keystrokes when the + and - buttons are pressed.  It doesn't seem that the "Mute" button on the headset sends the "Mute" shortcut "0xa0", however.... )

Hope this helps! :)

---

### Post by udude on 2007-06-14
> **blazoner said:**
> I had the same problem, and the solution was simple.

After getting my USB headset to work as my default Alsa device, I went into system -> preferences -> sound, and under the Devices tab set "Default Mixer Tracks" to "Logitech USB Headset", and chose "Speaker" from the menu instead of "Microphone Capture". (This tells ALSA what to do when the keyboard shortcut keys are pressed.  The headset sends these same keystrokes when the + and - buttons are pressed.  It doesn't seem that the "Mute" button on the headset sends the "Mute" shortcut "0xa0", however.... )

Hope this helps! :)

Is there a way to set the headset controls working even if the default alsa device is not the headset? 
Its very convenient for me to have the default alsa device set to card 0 because its connected to a surround sys (all music and movies go there). Still I'd like the headset to control card 1 so I can control the headphones volume when doing voip calls

---

### Post by Unix_Wizard on 2007-09-20
I've tried everything mentioned in this thread and a few methods suggested in other sites but both my keyboard shortcuts and my headset buttons stubbornly change the mic volume. So I've reverted to onboard sound until I find a fix that works. Even alsamixer defaults to changing the mic volume. I've almost given up on this now.

---

### Post by anchor on 2007-09-21
> **Unix_Wizard said:**
> I've tried everything mentioned in this thread and a few methods suggested in other sites but both my keyboard shortcuts and my headset buttons stubbornly change the mic volume. So I've reverted to onboard sound until I find a fix that works. Even alsamixer defaults to changing the mic volume. I've almost given up on this now.

*edit:  Haha just noticed someone has already posted pretty much the same thing above. What's more they even pm'd me.  I must be getting old... :O.  Anyways, i can vouch for the method as I just tried it, and it did in fact work.


I think i finally have an answer for you. :D

Just recently i was struggling with my own method (ironic eh?), and like you i could only change the mic volume.  I finally got it to change the speaker volume by doing the following:

go to system > preferences > sound

Under "sound events"
ensure "usb audio" is chosen for sound playback

Under "Music and movies"
ensure "usb audio" is chosen for sound playback

Under "Audio Conferencing"
ensure "usb audio" is chosen for sound playback
ensure "silence" is chosen for sound capture

Under device select "Logitech USB headset (alsamixer)"
then ensure "speaker" is chosen in the box directly below.

after doing this i was able to make the headset controls control the headset speakers.

Hope this works.

---

### Post by Unix_Wizard on 2007-09-23
I did all of that and the headset controls are still changing the mic. Could you post your asoundrc?

---

### Post by anchor on 2007-09-23
> **Unix_Wizard said:**
> I did all of that and the headset controls are still changing the mic. Could you post your asoundrc?

Sure thing:

```

pcm.!default {
type plug
slave.pcm "combined"
}

pcm.combined {
type asym
playback.pcm "playback"
capture.pcm "hw:1,0"
}

pcm.playback {
type dmix
ipc_key 1024
slave {
pcm "hw:1,0"
period_time 0
period_size 1024
buffer_size 4096
rate 44100
}
bindings {
0 0
1 1
}
}

ctl.dmixer {
type hw
card 1
}

```

---

### Post by Unix_Wizard on 2007-09-27
EDIT: [RESOLVED]
All I did was delete asoundrc and all the backups in my home directory and create them again. Keyboard shortcut and buttons on the headset's volume control now correctly adjust the volume. Thanks everyone.
Like a previous user stated. The mute button on the headset doesn't work however the keyboard shortcut works fine :)

---

### Post by xbxopro on 2008-04-13
Hello, I have been having some of the same troubles, but differently. I'm trying to get my headset to work properly under Wine.
More importantly, what I'm here to ask for, is how to edit the asoundrc file (as given in the previous post(s), to be a separate device, rather than the default. 
I want to play audio from programs and games etc through my desktop speakers, but have audio for Wine applications go through my headset.
The above information allows my Microphone to work in Wine now, where it didn't before and the audio through the headset did, heh.
So i'm kinda in an opposite position of where I was before. I wanted my Mic to work, but now I also want the audio to work.
So I'm guessing I need to separate the device somehow in the asoundrc file.
Furthermore, the 'playback' device shows up in programs on Wine, but there is no sound through the headset and it plays audio very quickly. 
I know this because I have been using SAM Broadcaster 4.2.2, Mic works now, but trying to play audio through the headset results in it playing nothing through the headset and also with high speed.
Thank you for your help thusfar.

---

