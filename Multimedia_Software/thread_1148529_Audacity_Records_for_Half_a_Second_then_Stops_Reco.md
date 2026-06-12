---
title: "Audacity Records for Half a Second then Stops Recording"
date: 2009-05-04
forum: Multimedia Software
---

### Post by sobrien on 2009-05-04
I recently upgraded to Jaunty 9.04, and Audacity records for a bit less than one half of a second and then the recording of sound stops although the cursor in the recording window continues to move normally.  The bars in the Input Level Meter continue to bounce with my voice the entire time, but I only get the one half second of waveform graph in the recording window.

When I listen to the playback, the half a second audio is just fine, and then it just stops, although the playback of nothing continues for the duration of the file.

Audacity is version 1.3.7, I completely un-installed it and re-installed it.  I totally deleted the .audacity-mylogin and .audacity-data files in my home directory and started over.  Audacity reports that "Disk space remains for recording 193 hours."

My machine is a Dell Optiplex GX620 with which I have used Audacity with older versions of Ubuntu in the past.  My microphone is a USB WebCam; I tried a different USB microphone and had the same problem.

Totem plays audio and video just fine, VLC works perfectly, and I use the microphone with Skype and it works great.  (Of course, I kill ALL applications that use the microphone or audio BEFORE I start Audacity.)

If you have any ideas, I would be most grateful.

---

### Post by davidsmind on 2009-05-11
I'm getting this same problem.

[http://www.linuxquestions.org/questions/ubuntu-63/audacity-records-for-a-half-second-then-stops.-723221/](http://www.linuxquestions.org/questions/ubuntu-63/audacity-records-for-a-half-second-then-stops.-723221/)

The above link claims setting the defualt bit rate to 48000 Hz has solved the problem. I've tried doing so, with no effect. Anyone here using ALSA+Audacity with jaunty?

---

### Post by umaxtu on 2009-05-13
> **davidsmind said:**
> I'm getting this same problem.

[http://www.linuxquestions.org/questions/ubuntu-63/audacity-records-for-a-half-second-then-stops.-723221/](http://www.linuxquestions.org/questions/ubuntu-63/audacity-records-for-a-half-second-then-stops.-723221/)

The above link claims setting the defualt bit rate to 48000 Hz has solved the problem. I've tried doing so, with no effect. Anyone here using ALSA+Audacity with jaunty?

I am it worked fine with my Quickcam pro 9000 on 8.10 but no ton 9.04

---

### Post by sobrien on 2009-05-14
Setting the Default Sample Rate to 48000 did not help me, but setting it to 16000 made it work just fine.  None of the other Rates work, ONLY 16000.

Very odd; Audacity worked fine on this machine on previous versions of Ubuntu.

---

### Post by dld on 2009-05-16
I have the same problem on one of two machines.  48000 works for me on the problem machine.

---

### Post by johnleonard on 2009-05-19
I had this problem on Xubuntu 9.04 and fiddled around with the Audio I/O settings. A have an Intel chipset for sound and I found it worked when, by trial and error, I set Device: ALSA: Intel 82801DB-ICH4 and then selected mic:0 from the dropdown on the main interface.

These options will be different for other systems but my experience suggests that trying all different combinations of recording device settings may help.

I am happy now as I never managed to get it to work on 8.04.

---

### Post by johnleonard on 2009-05-21
.. and it failed again next time I rebooted. I did find that deleting audacity.cfg in the .audacity folder then restarting audacity sorted the problem though. A drag if you have to do this every time though.

---

### Post by johnleonard on 2009-06-09
Me again. After repeated failures I purged audacity 1.37
```
sudo apt-get purge audacity
```
and installed version 1.35 from [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/) which works fine.):P

---

### Post by keithpeter on 2009-07-01
> **johnleonard said:**
> Me again. After repeated failures I purged audacity 1.37
```
sudo apt-get purge audacity
```
and installed version 1.35 from [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/) which works fine.):P

I'm resurrecting this thread to ask how to compile Audacity 1.2.6 from the sources on the audacity page? 

I'm on Jaunty and get *exactly* the behaviour described by the OP. I like and trust 1.2.6 and I use it on my Windows staff laptop and on the significant other's iBook.

Ta

---

### Post by tmckellar on 2009-08-11
I believe the issue actually has to do with Software Playthrough. I get this when I am trying to record with my M-audio Delta 44 but not my RME Digi 96/8 for some reason. Pulse Audio is completely unusable when with the Software Playthrough option enabled either. It does record however but is extremely messed up. Disabling Software Playthrough (while it is extremely annoying having to do so) fixes the problem. Hopefully somebody is on this problem and a fix will be available soon.

---

### Post by FOffMicrosoft on 2009-08-23
this just happened to me, i had to change mine from 44100 to 48000, which happens to match the "Actual Rate" Box in lower right, then it worked.  Could it be related?  Jaunty 9.04 & Audacity 1.3.7

---

### Post by cpeachey on 2009-10-26
quote...I believe the issue actually has to do with Software Playthrough.... unquote.
My recordings were stopping, I have unchecked both playthrough boxes and recording is now OK. Thanks for the tip.
Chris

---

### Post by jsedwards on 2010-01-22
I have used Audacity occasionally on this machine for a couple of years and never had a bit of trouble until now.  It has always just worked without my doing anything.  Yesterday I started it up and it was just recording silence.

I went into the Preferences and changed the Recording device from "default" (which I assume it has always been set to) to "SB Audigy 1 [SB0092]: Mike Capture (hw:0,1)" and now it records for half a second and then stops capturing data.  And when I play that half a second back it sounds like a chipmunk.  It says I have enough disk space to record for 5 hours and 38 minutes (there is 7 GB free).

I have tried the suggestions in this thread and tried changing the sample rate to 48000, 16000, etc. all with the same result.

Earlier this week when I booted it up, it popped up a dialog that said the Sound Blaster Audigy card had been removed (I haven't made any hardware changes to this machine).  I have never seen that before.

I tried uninstalling and reinstalling Audacity and that didn't change anything.  Since I had switched from Gnome to KDE and did a distupgrade to 9.10, I decided to just do a clean install of Kubuntu and see if that helped.  It didn't.

And I am still getting the dialog boxes about the Sound Card being removed when I start up.  I am wondering if the Audigy card has gone bad?

---

### Post by king dumb on 2010-02-12
I had the same problem [ recording for 1/2 sec. then stopping] I changed the rate to 48000 and it work now, but it is still unable to to do playthrough

Audicity 1.3.9 + ubunto 9.10

.k

---

### Post by PuraVida on 2011-06-06
> **FOffMicrosoft said:**
> this just happened to me, i had to change mine from 44100 to 48000, which happens to match the "Actual Rate" Box in lower right, then it worked.  Could it be related?  Jaunty 9.04 & Audacity 1.3.7

I came to this forum via searching Google to solve this problem although I am actually using openSUSE 11.2.  Like another person here, I used Audacity before on this same machine, with the same OS, and without any problem but this time, it would record for a fraction of a second and quit.  

I just wanted to say that doing what I quoted above worked.  And also, if anyone knows the true reason this happens, they should still provide that info if you can.

---

