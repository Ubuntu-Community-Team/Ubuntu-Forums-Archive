---
title: "USB headset &amp; Skype in Koala?"
date: 2009-11-15
forum: Multimedia Software
---

### Post by grashdur on 2009-11-15
Am I overlooking something here? I can't seem to use Skype with my (Skype-certified) USB headset any more now that I've upgrade to Karmic Koala. 

The situation before (Jaunty Jack & earlier): In System > Preferences > Sound > Devices, I set both input and output under "Audio Conferencing" to "C-Media USB Headphone Set...(ALSA)...". Then in Skype's own menu Options > Sound Devices I selected "ALSA" for ringing, and C-Media USB Headset for voice in and out. It worked all right: I used my headset for talking and listening, and when a call came in it rang on my speakers.

The situation now (Karmic Koala): In the Skype menu just mentioned, the options for "Microphone" and "Speakers" and "Ringing" have only one menu option, "PulseAudio server (local)". In Ubuntu's Sound Preferences I just can't figure out how to make it work with Skype. 

I hope this can be resolved, as I rely on Skype for almost all my phone calling--and I need it for work tomorrow morning (though I might switch to my laptop which still runs JJ).

---

### Post by VertexPusher on 2009-11-15
> **grashdur said:**
> The situation now (Karmic Koala): In the Skype menu just mentioned, the options for "Microphone" and "Speakers" and "Ringing" have only one menu option, "PulseAudio server (local)". In Ubuntu's Sound Preferences I just can't figure out how to make it work with Skype.
You can't use Skype with multiple devices if PulseAudio is installed. See here for an explanation: [http://share.skype.com/sites/linux/2009/09/some_explanations.html](http://share.skype.com/sites/linux/2009/09/some_explanations.html)

Also see this thread: [http://ubuntuforums.org/showthread.php?t=1319920](http://ubuntuforums.org/showthread.php?t=1319920)

The solution is to remove PulseAudio.

You might also want to vote for making PulseAudio an optional package in the next Ubuntu release: [http://brainstorm.ubuntu.com/idea/21827/](http://brainstorm.ubuntu.com/idea/21827/)

---

### Post by alicemoon on 2009-11-15
I had a similar problem - quick fix is to remove pulse audio through synaptic package manager and then configure your headset in skype - this worked for me -  see thread - [http://ubuntuforums.org/showthread.php?t=1319920&highlight=karmic+skype](http://ubuntuforums.org/showthread.php?t=1319920&highlight=karmic+skype)
however I then reinstalled pulse audio and found that my usb phone was now recognised in sound preferences as a microphone - so I can now use it with Pulse audio - I have no idea why!
I hope you get yours working

---

### Post by grashdur on 2009-11-15
Hi VertexPusher & Alicemoon, I read your ideas, your links, and links from those links on the subject. Spent the whole day trying all these different things:

**1. Fiddled with Pulse Audio’s sound preferences:** Lots of settings here, hard to understand what they really mean. At the beginning all audio just fine thru the computer speakers but not my Skype USB headset. After fiddling around: sound okay only thru the headset and not the computer speakers. Since I changed so many settings, how I got to that point was unclear.
[B]
2. System update since installing Skype:[/B] No updates available right now.
[B]
3. Installed Pulse Audio Device Chooser (padevchooser):[/B] Seemed a little complex, and hard to figure out what actual devices it was referring to. It couldn't give me Skype sound out/in to the USB headset while letting the rings, etc., go to the computer speakers. 

**4. Created file /.pulse/client.conf containing a line "autospawn = no":** no changes, even after rebooting, so I deleted this file.

**5. Removed Pulse Audio + installed Gnome ALSA Mixer & EarCandy:** That last program is designed to manage Pulse Audio, so I ignored it for now. Yes, Skype at this point was able to select specific devices. The ALSA Mixer applet had two tabs, one for USB audio and one for Realtek ALC880 (the sound card, I think). The USB audio tab was very simple and straightforward, and it allowed Skype to use the USB headset. The Realtek tab had a huge number of volume bars and checkboxes, but none of them seemed to do much of anything. Now I could use the headset very easily with Skype, and I could hear notification sounds on the computer speakers, but Totem kept playing sound files silently, with its speaker icon greyed out, and when I tried to close it, it froze up each time. Apparently Ubuntu doesn’t like going without Pulse Audio. No sound through the main computer speakers except for notifications, no Skype call ring thru the computer speakers.
[B]
6. Reinstalled Pulse Audio:[/B] since Ubuntu couldn’t play multimedia files without it. 

**7. Tried EyeCandy:** It didn’t seem to do anything, just seemed to quickly disappear when starting up. Doesn’t seem to have modified any preference menus. I tried reinstalling it, thinking maybe it got corrupted due to the absence of Pulse Audio the first time. Still nothing. The info online about this little program sounds wonderful, but it just isn’t up and running yet (version 0.50 now). 

**8. Reverted to Skype version 2.0.0.72 (running the non-Debian version in a folder):** The program started quickly, and remembered all my preferences from the (Debian) version 2.0.0.47 that I had just uninstalled. Still in my admin account, I looked at its Devices menu and was happy to see the many device options available again in spite of Pulse Audio’s presence. I started fiddling with it and it seemed like Skype was working just perfectly, with both the headset and call ringing thru the computer speakers. All sound was starting to work perfectly now, for all programs. So I switched over to my non-admin account to start doing the same settings there. Now I had perfect sound to my speakers from other programs, but no sound anywhere whatsoever for Skype. So I went back to my admin account to look at the settings again, and saw that now I had the same situation there as well. 
[B]
9. Rebooted:[/B] Now I have absolutely no sound, from any programs at all, through my computer speakers nor through my headset. What happened???

It looks like I won’t have any more time to work on this till Wednesday afternoon. At this point it looks like I have to just revert to Jaunty Jack—but what a shame, since Koala seems so outstanding in all areas other than sound!

---

### Post by alphacrucis2 on 2009-11-15
The Skype beta is working ok for me via pulseaudio and USB headset. I have to manually change the input and output under sound preferences to make it actually use the USB headset. It doesn't seem to automatically switch when the headset is plugged in. (I did try earcandy, which is supposed to help with that but it doesn't work). Removing pusleaudio is a non starter far as I am concerned as this is the way things are going.

---

### Post by VertexPusher on 2009-11-16
> **grashdur said:**
> The ALSA Mixer applet had two tabs, one for USB audio and one for Realtek ALC880 (the sound card, I think). The USB audio tab was very simple and straightforward, and it allowed Skype to use the USB headset. The Realtek tab had a huge number of volume bars and checkboxes, but none of them seemed to do much of anything.
I have the same type of sound card. First make sure that the ALSA mixer is showing all the controls for the Realtek card. Some may be hidden by default. Then turn the following sliders up: Master, PCM and Front. If you have a 5.1 setup, you might want to turn up Surround, Center and LFM as well. Also make sure that none of these channels is muted.

> but Totem kept playing sound files silently, with its speaker icon greyed out, and when I tried to close it, it froze up each time.
This is easy to fix. Make sure that gstreamer0.10-alsa is installed, then remove gstreamer0.10-pulseaudio. This will force Totem to use ALSA as well.

If you use VLC, you probably want to get rid of vlc-plugin-pulse, too.

---

### Post by VertexPusher on 2009-11-16
> **alphacrucis2 said:**
> The Skype beta is working ok for me via pulseaudio and USB headset.
Of course it is, but did you manage to make Skype use the headset for voice and the main sound card for ringing? That's the problem here.

> Removing pusleaudio is a non starter far as I am concerned as this is the way things are going.
That's up to you. As far as I am concerned, I'll give the finger to anyone telling me that I have to put up with a broken sound system because "that's the way things are going".

---

### Post by grashdur on 2009-11-18
Okay, following the latest suggestion I just tried this: 

**10. Removed Pulse Audio Again + Made Sure gstreamer0.10-alsa is installed + Removed gstreamer0.10-pulseaudio:** I checked the Gnome ALSA sliders: For my sound card, 15 sliders are visible. I looked at the soundcard preferences menu and confirmed that all available sliders are displayed. I made sure that Master, PCM and Front are all unmuted and up all the way. I checked the boxes for "IEC958" and "IEC958 Default PCM." Still no go. I rebooted. Still the same story. Skype this time makes its sounds on the computer speaker, but only after I go in and select the location of each sound file--the next time I open Skype, I have to do it again. Now I can play a .ogg file on Totem, but the sound is always muted by default so I have to turn it on every time. And the player still always freezes up for a while whenever I try to close it. I have to "Force Quit" every time. The first time I looked at the "USB Mixer" tab on the Gnome ALSA Mixer, the sliders took up the whole tab area and the options underneath were not visible. 

Strangely, I keep hearing a popping noise coming out of my computer speakers: usually when I open a sound devices menu, or when I try to play a sound and it doesn't play. Many times I hear the popping sound, and after some delay a sound does in fact work. 

This is all such a mess! I guess if I give my own vote in the big Pulse Audio vs. ALSA debate, I'd say they're both horrible and should be scrapped or totally reworked, at least their Koala versions. 

I'm now abandoning Karmic Koala, even though in all areas other than sound it's fantastic.

---

### Post by CalumSult on 2009-11-25
I have the same problem and this is what I did to 'fix' it (using 9.10, pulseaudio installed, and skype 2.1)- rather than trying to get skype to select a different audio output for the ringing I used their notification option to script the ringing.  It's janky but it actually works just fine and I can live with that.  I first used padevchooser to set skype to use the headset (both mic and speakers) for all input/output (had to turn the 'volume' on the mic way up too in Sound Prefrences).  Then installed sox and set the notification script for Incoming Call Ringing to [I]

play /usr/share/skype/sounds/CallRingingIn.wav

[/I]That gets you a single ring on an incoming call.  I think it should be easy to write a script to loop the ring, then have another script that kills the first one when the call is answered or ignored etc using the execute script on any event feature.Suggestions are welcome, my scriptfu is weak.  :)

---

### Post by grashdur on 2009-12-13
> **CalumSult said:**
> I first used padevchooser to set skype to use the headset (both mic and speakers) for all input/output (had to turn the 'volume' on the mic way up too in Sound Prefrences).

How did you use padevchooser to do that? This applet has gotten so complex and inscrutable that I just get lost in it now. And I'm still faced with the same fundamental problem as from the start: Karmic Koala does not allow the user to choose which programs use which outputs and inputs, at all. Which is why I can't use KK: I need to be able to use Skype on the headset, have it ring to the speakers, and listen to music or podcasts on the speakers. In JJ that's relatively easy. If I have to go in and try to change these extremely complex sound settings each time I want to answer an incoming call, it just won't work for me.

---

### Post by grashdur on 2010-05-07
This unsolved problem has persisted into Lucid Lynx -- I wanted to report this bug somewhere like Launchpad, but there's no category for it. I hope this will eventually get fixed, because I'd really like to upgrade at some point.

---

### Post by Andy.N.Z on 2010-05-27
> **CalumSult said:**
> I have the same problem and this is what I did to 'fix' it (using 9.10, pulseaudio installed, and skype 2.1)- rather than trying to get skype to select a different audio output for the ringing I used their notification option to script the ringing.  It's janky but it actually works just fine and I can live with that.  I first used padevchooser to set skype to use the headset (both mic and speakers) for all input/output (had to turn the 'volume' on the mic way up too in Sound Prefrences).  Then installed sox and set the notification script for Incoming Call Ringing to [I]

play /usr/share/skype/sounds/CallRingingIn.wav

[/I]That gets you a single ring on an incoming call.  I think it should be easy to write a script to loop the ring, then have another script that kills the first one when the call is answered or ignored etc using the execute script on any event feature.Suggestions are welcome, my scriptfu is weak.  :)

Hey that is a great work around & is what I am doing now. As feature full as sox is I could not find any command to stop it playing any audio. So I have edited CallRingIn.wav using Audacity to make the duration 10 seconds. That is about the usual length of time for the phone to ring before being answered. I´d really prefer to have another script cut off the ringing when I answer a call. Can any scripting experts help on that one?

---

