---
title: "Jaunty and Skype = Major Sound Delay"
date: 2009-05-01
forum: Multimedia Software
---

### Post by Geekkit on 2009-05-01
I've noticed that using Skype now with Jaunty I have a really bad lag/delay between sound and video. It wasn't like this at all with Skype and 8.04. I was just curious if anyone knows about this and if there are any fixes.

---

### Post by Geekkit on 2009-05-01
*bump*

... Anyone?

---

### Post by atmartin50 on 2009-05-02
I'm having the exact same problem, and it's pretty frustrating seeing as I rely on Skype to stay in touch with family back home. Anyone have any ideas?

---

### Post by Arup on 2009-05-02
Go to sound options in Skype, deselect Pulse and set it to ALSA or any hardware you can see, I have set mine to Intel and it works fine with no delays and minimal CPU usage.

---

### Post by atmartin50 on 2009-05-02
Thanks, Arup! Talk about synchronicity at work! I tried the very thing you suggested right before I saw your reply and it solved the problem (at least with a test call---I'll find out for sure when I talk to family back home later today). Geekkit, try going into the Skype 'Sound Devices' options to change from Pulse to HDA or something applicable to your system and maybe it'll work for you, too. Good luck.

---

### Post by Arup on 2009-05-02
> **atmartin50 said:**
> Thanks, Arup! Talk about synchronicity at work! I tried the very thing you suggested right before I saw your reply and it solved the problem (at least with a test call---I'll find out for sure when I talk to family back home later today). Geekkit, try going into the Skype 'Sound Devices' options to change from Pulse to HDA or something applicable to your system and maybe it'll work for you, too. Good luck.

It should work, I have talked for hours without any issue and the clarity is excellent, I don't use USB mic though and use a regular line in mic. Also no issues with video either. I actually open up vlc to brighten up the camera and then use it in Skype.

---

### Post by bhaskar on 2009-05-02
The problem is that even though the sound quality is good, there is an unacceptable time lag of seconds.  This of course does not show up in the Skype test call.  Skype and Jaunty are quite unusable for me for this reason.

The choices I have for Sound Devices are:
  Default device (Default)
  HDA Intel (hw:Intel,0)
  HDA Intel (plughw:Intel,0)
  HDA Intel (hw:Intel,6)
  HDA Intel (plughw:Intel,6)
  hdmi
  headset
  pulse

The only option that works for both the Test Sound and Test Call is pulse.  The test call works great, but real conversations experience unacceptable time lags, as if I were making a phone call to space and was seeing limits imposed by the speed of light.

-- Bhaskar

---

### Post by Arup on 2009-05-02
I have no delays here whatsoever, have you tried out Skype OSS build?

---

### Post by FewClues on 2009-05-02
> **Arup said:**
> It should work, I have talked for hours without any issue and the clarity is excellent, I don't use USB mic though and use a regular line in mic. Also no issues with video either. I actually open up vlc to brighten up the camera and then use it in Skype.

Arup you might turn out to be my hero.  I cannot get the video to work with Jaunty on Skype.  Please explain a bit about using VLC.

---

### Post by cfogelberg on 2009-05-05
> **atmartin50 said:**
> Thanks, Arup! Talk about synchronicity at work! I tried the very thing you suggested right before I saw your reply and it solved the problem (at least with a test call---I'll find out for sure when I talk to family back home later today). Geekkit, try going into the Skype 'Sound Devices' options to change from Pulse to HDA or something applicable to your system and maybe it'll work for you, too. Good luck.

Drat, I don't know what's happened. I'm using Jaunty and I used to have Skype working fine with pulse. Sound out is set to HDA intel (hw:Intel,0) but unless I set sound in to pulse it's too quiet. I just tried a test call again though before ringing a friend and it's got the enormous delay you talk about here.

Does anyone know of a good solution to this problem in my situation? I seem to be stuck between a rock (mic volume too low) and a hard place (sound delay making it unusable) :/

Christo

---

### Post by cfogelberg on 2009-05-05
> **cfogelberg said:**
> Drat, I don't know what's happened. I'm using Jaunty and I used to have Skype working fine with pulse. Sound out is set to HDA intel (hw:Intel,0) but unless I set sound in to pulse it's too quiet. I just tried a test call again though before ringing a friend and it's got the enormous delay you talk about here.

Does anyone know of a good solution to this problem in my situation? I seem to be stuck between a rock (mic volume too low) and a hard place (sound delay making it unusable) :/

Christo

Update: Restarting the laptop seems to have fixed the problem, I don't know what could have caused it. I have just tried starting and playing some music on Amarok, and found that this doesn't interfere with it, although I can't use Skype and Amarok at the same time - I have to stop (not just pause - the music in Amarok, then use Skype. Any solutions to this possibly general problem of several things using the sound system at the same time?

Best,
Christo

---

### Post by justken on 2009-05-10
I have a problem with using exaile and skype but have managed to solve the time delay problem by re-setting the sound options in skype (and without uninstalling pulse, as suggested in some other threads).

My current settings are:

Sound in:  HDA NVidia (hw:Nvidia,2)
Sound out: HDA NVidia (hw:Nvidia,0) 
Ringing:   HDA NVidia (hw:Nvidia,0) 

Obviously will depend on what sound card you are using - and other combinations might work.  Interestingly, my brother has pretty much the same rig as me and has:

Sound in:  HDA NVidia (hw:Nvidia,0)
Sound out: pulse 
Ringing:   pulse

We are currently speaking with clear sound and no delay - perhaps it is just the 'sound in' that has a problem in skype - or if both users are using pulse?

In fact, I have just duplicated my brother's settings, restarted skype and everything is ok - which suggests that it is the 'sound in' bit that's the problem.

Still a workaround rather than a fix but I'm happy.

Regards,

Ken

---

### Post by techfun on 2009-05-16
I had this problem on multiple Jaunty installs.

Following the steps in this post completely and utterly solved them.  The steps disable PulseAudio and make ALSA your first choice / default sound system.

Ubuntu 9.04 Jaunty – Keeping the beast Pulseaudio at bay - [http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/")

---

### Post by GNUbee40 on 2009-05-17
Hello there!

My sound card is Intel 82801H (ICH8 Family) HD Audio Controller

**My expriences with this problem:**

[LIST]
With Audio set to Default settings neither Audio IN or OUT works.
[*]With Audio IN set to Pulse there is the enormous lag (ca. 5 seconds) earlier described in this thread.
[*]With Audio IN set to HDA Intel (Intel:HW,4) and Audio OUT set to Pulse there is no major lag (ca. half a second).
[*]Additionally with Audio OUT set to HDA Intel (Intel:HW,0) there is no detectable lag. However - with this setting it is not possible to use other applications who use the Audio OUT (notably Music players) at the same time, which is quite unpractical. [/LIST]
I prefer the third setting.

**How to measure Sound Delay with the Skype test call:**
Simply start counting loud into the MIC (preferably 1 count/second) after the beep signal and until the second beep. Remember the last number you managed to say before the second beep (usually 10 if you count seconds). If you hear yourself counting all the way to that number (with no considerable pause between second beep and your recorded voice) than everything is fine. If there is a pause of several seconds between second beep and your recorded voice and if the counting stops before that last number - then this means as many seconds delay as numbers missing. 

Cheers

---

### Post by chocobanana on 2009-05-18
I had the same problem on one of my laptops running Jaunty 9.04.

All sound settings were set to Pulse. I left the outputs on Pulse and only changed the input to one of the Alsa inputs [in my case the very first, Intel ICH6 (hw:ICH6, 0)] - You may have to use another one, though.

Problem was solved immediately.

Hope this is inspiring. :)

Thanks for this thread.

---

### Post by psyke83 on 2009-05-18
For all versions of Ubuntu which use PulseAudio, Skype needs to be manually configured in a specific way. Failure to do this will cause mixing errors, or delays in audio (as the original poster has experienced).

See my PulseAudio guide for the precise details (Appendix C).

---

### Post by Man Eating Duck on 2009-07-24
I got big delays with Skype and an Logitech Clearchat Comfort usb headset. This was because pulseaudio uses all available cpu, causing a delay. I've had great luck doing the following in Skype and pasuspender:

Skype:
Sound In = Logitech USB Headset (plughw:Headset,0)
Sound Out = Logitech USB Headset (hw:Headset,0)
Ringing: pulse

It seems that plughw will be the mic in most cases. The problem is that pulse is hogging the headset, preventing Skype from accessing it. I created a launcher in the panel with these settings:

Type: Application
Name: Skype Pasuspender
Command: gnome-terminal -t "Skype Pasuspender" -x pasuspender -- sleep 10000

This opens pasuspender in a terminal, disabling pulse. When I make a call I launch it prior to calling. When someone calls me Skype will ring via pulseaudio, and I hit the launcher prior to answering. Skype will then use the usb headset without problems and delays. Very occasionally Skype will croak when pasuspender activates and it can't play its ringing sound, then I'll relaunch it and call back with pasuspender still active.

When I'm finished I close this terminal, and pulseaudio will get back to normal within about ten seconds.

An ugly workaround, but I hope it helps someone :)

---

### Post by igorzwx on 2009-07-24
Friends!

I have a solutions for old boxes.
This soulution is OSS4.
USB audio devices are not supported by OSS4
and something else too.

I have Ubuntu 9.04 (with OSS4) installed on IBM
notebook (of 2003) and old box (of 2001).

Skype and Ekiga work perfectly.
No noise, no latency, no delay.
Fantastic quality.
I can call now to my friends around the world.

more info you may find here:
[Howto: OSS4 with Ubuntu Lite (Beta, netboot)]("http://www.4front-tech.com/forum/viewtopic.php?t=3237")
[http://www.4front-tech.com/forum/viewtopic.php?t=3237](http://www.4front-tech.com/forum/viewtopic.php?t=3237)

---

### Post by juaninse on 2009-07-30
I have the same problem, however pulse seems to be the only option that skype will accept.  Any sound input device selection other than "pulse" causes a "Problem with Audio Capture" error.

Is there not some pulse setting that can be adjusted for this?

---

### Post by igorzwx on 2009-07-30
If you do not have a quadro core,
you may not manage to fix Skype and PulseAudio.
If you have an old box, the only solution is OSS4.

---

### Post by igorzwx on 2009-08-03
This works my old box of 2001 (Pentium 4, 1.6GHz, 500MB RAM)

[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[How to remove PulseAudio and fix sound with ALSA and ESound]("http://ubuntuforums.org/showthread.php?t=1230561")
[http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)

[B]Audacity works (playback and recording).
VLC works.
Skype works too.[/B]

---

### Post by Riffster on 2009-08-12
I've got a very similar problem - using Jaunty and all other sounds work great except Skype. I'm running a dual core Athlon on a relatively new board so do I need to run OSS? I won't get rid of Pulse, I've had plenty of other sound probems and all the other stuff is working nice.

If I do, how do I get it and how do I remove Skype from my system?

---

