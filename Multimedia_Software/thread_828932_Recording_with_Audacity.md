---
title: "Recording with Audacity"
date: 2008-06-14
forum: Multimedia Software
---

### Post by Gina on 2008-06-14
I've now tried several versions of Ubuntu and can't get Audacity to record from my audio Line input.  I've checked all the settings and everything seems to be set up correctly.  It correctly recognises my sound system and the sound system takes line input and plays it through the line out to the speakers.  Audacity plays pre-recorded music files fine.  I have also tried Sound Recorder and that's the same - so there is a common factor.  I've searched the forums and web etc. for a solution but not found anything so far that works.

Has anyone any suggestions, please?

---

### Post by logos34 on 2008-06-14
check if 'capture' is enabled in sound settings (if it doesn't appear check Prefs)

---

### Post by Gina on 2008-06-14
Thank you for your reply.  Yes, I enabled capture.

---

### Post by VanillaMozilla on 2008-06-15
I have the same problem.  It records a blank signal.  I can hear the sound fine, but can't record.

"check if 'capture' is enabled in sound settings"

I'm looking for a check box somewhere.  Alternatively, I'm trying to figure out which sound device to choose and where to choose it.  Can you be more explicit?


You're not referring to the alsamixer, are you?  That's a complicated device, and I've done a lot of monkeying with it without effect on recording.

---

### Post by VanillaMozilla on 2008-06-16
EDIT:  I guess I don't have quite the identical problem.  The original poster is using Line input.  I am trying to do a sound card capture.  Hope you don't mind my posting here.  Will post elsewhere if you think it's too confusing.



OK, going down the list in the Welcome page:

**1. Recording Device**
ALSA: default[/b].  Changing device to
card 0: I82801BAICH2 [Intel 82801BA-ICH2], device 0: Intel ICH [Intel 82801BA-ICH2]
doesn't work either.  That's what I get from the aplay -l command.

After flipping back and forth a couple of times alternatively with the Device Toolbar and the menu I get

"Error while opening sound device. Please check the input device settings and the project sample rate."  Sample rate is correct:  44100 (default).

Closing window and opening a new one gets rid of error message but not the problem.


**2. Input source**
There are instructions for Windows and Mac, but not Linux.  **The Mixer Tool has no dropdown selector.  I think that's a clue**  It has an input volume control.  Turning that up has no effect with either input device.

**3. Input volume**
(Side note: all the blue links are inactive.  The Linux version needs some work here.)
EDIT:  I think the following paragraph on monitoring is irrelevant.

A. Enabled monitoring.  Double-clicked to right of meters and/or clicked on drop down menu.  Usual result:  Two red bars, followed by the above error message.  Clicked on the little monitor drop-down selector.  I get one of two results.  Either I get the error message above or **Audacity CRASHES.  And I can duplicate the crash.**

B. Working through the Wiki troubleshooting guide, the last step describes the problem but not the solution:

Linux-specific issues, #6:  "The recording device you currently have selected on the Audio I/O tab of the Preferences only has one input source, and so there is no choice that can be made. Many USB and Firewire Input/Output devices fall into this category."  This is sound card capture, not USB or Firewire.


It works in Windows, so the hardware is fine.  What am I doing wrong?

---

### Post by logos34 on 2008-06-16
> **VanillaMozilla said:**
> I have the same problem.  It records a blank signal.  I can hear the sound fine, but can't record.

You're not referring to the alsamixer, are you?  That's a complicated device, and I've done a lot of monkeying with it without effect on recording.

Yes, alsamixer.

vanillamozilla just reminded of something:

the reason you're getting blank signal/static volume level bars is the 'mix' setting may not be enabled (i.e. audio from soundcard).  You can hear it, but audacity can't

gnome-volume-control

>edit>prefs>check mix and capture

>swtiches tab>check/enable 'mix'
>recording tab>toggle 'capture', set volume

back in audcatiy, click on the microphone icon>'start monitoring'.  If there's audio playing on soundcard, the bars should light up and move

That's what works for me, at least

---

### Post by VanillaMozilla on 2008-06-18
OK, I made a discovery.  You have to RIGHT CLICK to get the volume control, AKA Alsa mixer.

You really have to be explicit with this stuff.  They've hidden a lot of stuff, and it's not really well documented.  Also, what is "PCM"?  I keep seeing that on audio devices.

I don't have time to try the suggestions just yet, but I also found this:
[http://audacityteam.org/forum/viewtopic.php?f=36&t=4826](http://audacityteam.org/forum/viewtopic.php?f=36&t=4826)

---

### Post by Gina on 2008-06-18
> **logos34 said:**
> Yes, alsamixer.

vanillamozilla just reminded of something:

the reason you're getting blank signal/static volume level bars is the 'mix' setting may not be enabled (i.e. audio from soundcard).  You can hear it, but audacity can't

gnome-volume-control

>edit>prefs>check mix and capture

>swtiches tab>check/enable 'mix'
>recording tab>toggle 'capture', set volume

back in audcatiy, click on the microphone icon>'start monitoring'.  If there's audio playing on soundcard, the bars should light up and move

That's what works for me, at leastYep, tried all that - no joy.  Except that I don't have a "mix" option.

I have got a form of Audacity working on my P4 desktop - the Windoze version in WINE!  Sound recording works as does playback - you need Software Playthrough enabled to hear what you're recording.  There is no monitoring without actually recording though.  Tried the same thing on my AMD64 desktop (using both 64bit and 32bit systems) and Audacity doesn't show the control buttons.  Why there's and difference using 32bit Hardy on both machines I really don't know.  Could be the NVidia display driver I guess.  I have ATI open source driver on the P4.

---

### Post by Gina on 2008-06-18
Just been fiddling around again - don't know what I did but the Linux version of Audacity (on my P4) is recording!  Only trouble is I can't seem to control the speaker volume - it's stuck at full volume (or off)

Later...  Just had another go with my AMD64 machine but no joy with that - just the same.

---

### Post by VanillaMozilla on 2008-06-18
There are so many mixers and volume controls everywhere.  Is there documentation that lists them all and describes what they do?

Anybody?

---

### Post by rayce on 2008-07-24
Hi all, I'm just a newbie to LINUX and am using Mint with Gnome and KDE; (I think).Sorry if I've come in the wrong way.
Audacity poses a problem for me that I can't find a thread to.
Recording is fine once I worked it out, saving is fine, playback is skipping as in speeding up then normal then speeding up, etc.
It plays back on all platforms the same way.
When recording the playthrough sounds great.
My only thought is that when the input spectrum jumps at the end of the window to accept the recording in real time, it somehow changes the recording. 
All settings look all right and I am using a NVidia card as it is the only one that works. My Realtek doesn't respond to the system.
Can anyone help with this please as I don't want to use windows anymore.

Thanks Rayce

---

### Post by coleyman on 2008-07-25
After much fiddling around with different settings, I finally got Audacity to record and the level meters showing. I am recording from the headphone out on my home stereo into the front mic on my PC. After getting a song from an album recorded, when I try to play it back I get the error message: "Error while opening sound device. Please check the output device settings and the project sample rate." I read a different post where the user got the same message on trying to playback something they had recorded in Audacity, but said that pre-recorded songs played back fine. So I imported a pre-recorded MP3 and tried and got the same error message. Any ideas on this?
Jeff

---

### Post by coleyman on 2008-07-25
ARRRGGGHHH! After last posting, I went back and tried to play an MP3 with the regular media player (which had been working) and, alas, no sound. So, I tried a movie that had had sound and, again, no sound. And I don't remember all the moves I made trying to get Audacity to work. Any way to go back to default sound settings? Help, pleeeeeeeze!
Jeff

---

### Post by coleyman on 2008-07-25
Never mind, I found what I had changed. I need to stay off of here and quit bothering people until I experiment around some more. Although I still can't play anything back in Audacity. I still keep getting that error message.

---

### Post by coleyman on 2008-07-28
> **VanillaMozilla said:**
> EDIT:  I guess I don't have quite the identical problem.  The original poster is using Line input.  I am trying to do a sound card capture.  Hope you don't mind my posting here.  Will post elsewhere if you think it's too confusing.



OK, going down the list in the Welcome page:

**1. Recording Device**
ALSA: default[/b].  Changing device to
card 0: I82801BAICH2 [Intel 82801BA-ICH2], device 0: Intel ICH [Intel 82801BA-ICH2]
doesn't work either.  That's what I get from the aplay -l command.

After flipping back and forth a couple of times alternatively with the Device Toolbar and the menu I get

"Error while opening sound device. Please check the input device settings and the project sample rate."  Sample rate is correct:  44100 (default).

Closing window and opening a new one gets rid of error message but not the problem.


**2. Input source**
There are instructions for Windows and Mac, but not Linux.  **The Mixer Tool has no dropdown selector.  I think that's a clue**  It has an input volume control.  Turning that up has no effect with either input device.

**3. Input volume**
(Side note: all the blue links are inactive.  The Linux version needs some work here.)
EDIT:  I think the following paragraph on monitoring is irrelevant.

A. Enabled monitoring.  Double-clicked to right of meters and/or clicked on drop down menu.  Usual result:  Two red bars, followed by the above error message.  Clicked on the little monitor drop-down selector.  I get one of two results.  Either I get the error message above or **Audacity CRASHES.  And I can duplicate the crash.**

B. Working through the Wiki troubleshooting guide, the last step describes the problem but not the solution:

Linux-specific issues, #6:  "The recording device you currently have selected on the Audio I/O tab of the Preferences only has one input source, and so there is no choice that can be made. Many USB and Firewire Input/Output devices fall into this category."  This is sound card capture, not USB or Firewire.


It works in Windows, so the hardware is fine.  What am I doing wrong?
Audacity is the only program I've got that I can't get sound on playback. I kept getting that same error message. Then a friend asked if I was using any other apps that might be keeping the sound at a certain sample rate like Firefox or anything. I had been keeping Firefox up while trying to figure my problem out, so I could check the forums and all, so I closed it and tried Audacity again, just playing back an mp3 that I had opened with it. Still no sound but the error message didn't come up. Hope this helps.
Jeff

---

### Post by cotcot on 2008-07-28
I recently got my line-in working :

---> right click Volume applet  (that is the loadspeaker icon where you change the volume)
---> Open Volume Control
---> Edit
---> Preferences
See if line-in and microphone are checked.
Thick Input Source. That gives a new tab (Option) in the Open Volume window where you can define the capture device for the Input Source.

---

