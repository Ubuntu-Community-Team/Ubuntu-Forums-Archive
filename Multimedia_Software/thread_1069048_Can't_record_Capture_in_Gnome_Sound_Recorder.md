---
title: "Can't record Capture in Gnome Sound Recorder"
date: 2009-02-13
forum: Multimedia Software
---

### Post by etienne@Rofti on 2009-02-13
Hi!

I have looked through the forums, but not yet managed to find a problem quite like mine, so I will attempt to explain it:

I am using Ubuntu Intrepid, but I cannot seem to get Sound Recorder to capture and record my computer's ALSA sound output. The only option in Sound Recorder's input drop-down menu is "Master".

I have also attempted to record while using Jack, but then the program hangs.

Any suggestions? Or any other info that I can give to make it easier?
Thanks!

---

### Post by gorg_karlo on 2009-02-15
I had the same frustration a few days ago after having a fresh install (forgot to note down the settings I had from before!).

Since you are recording using GNOME Sound Recoder, try doing this:

Click on System > Preferences > Sound

Under Audio Conferencing > Sound Capture - select your sound card under OSS (mine is HDA Intel ALC861 Analog (OSS). Click Close.

Now you need to select the switch which works for your recording. Double click on the speaker icon in your notification bar, then select Preferences.

Find the following switches:

Front
Front Mic
Front Mic Capture
Microphone Capture

Open your GNOME Sound Recorder and start recording. You should have the CAPTURE option immediately selected. Individually test the switches to see which one works for the recording. For my computer, the sure shot switch that works is the Front switch (the built-in microphone). I have yet to figure out how to make the external microphone work - for now, as long as I can use something, I'm good... :-)

If you still do not hear your recording, it could be that the Microphone under the OSS Mixer is muted. Under Volume Control (remember the speaker icon in your notification bar), select under Device > Your_Sound_Card (OSS Mixer), then go the Recording Tab. Unmute the microphone if it is muted. Repeat the testing of the switches above just to make sure you did not miss anything.

Just in case you have Skype recording problems, here's a tip:

Go to Options > Sound Devices

Sound In: HDA Intel (hw:Intel,0)
Sound Out: pulse
Ringing: pulse

You might want to install Skype Call Recorder to record conversations in Skype. Check out [http://atdot.ch/scr/](http://atdot.ch/scr/) to download the deb file.

Hope this helps!

---

### Post by keyboardslave on 2009-02-18
Every time i unmute my capture in ALSA Mixer when i close it and reopen its back to mute... 0_o

---

### Post by gorg_karlo on 2009-02-19
keyboardslave:

I been playing bit more on the settings - try doing this:

Go to System > Preferences > Sound

Under Audio Conferencing > Sound capture, select Your_Hardware_Name Analog (ALSA)

Click Close

Head to your Volume Control (double click on the speaker in your notification bar to adjust some settings)

Under Device > HDA Intel/Hardware_Name (Alsa Mixer), in the Recording Tab (if you checked Capture in your Volume Control Preferences), make sure CAPTURE IS IN FULL BLAST... (don't mind if it's muted/unmuted for now... mine is working even though it's muted... which I find strange...)

Then change to Device > Your_Hardware_Name (OSS Mixer), in the Recording Tab, make sure that the Microphone is NOT MUTED, and IS NOT FULL BLAST...

Go back to Device > HDA Intel/Hardware_Name (Alsa Mixer), click Preferences, then look for the microphone switches. 

Same with my first post - fire up GNOME Sound Recorder, and test your microphone switches one by one.

Let me know if you have some success.

---

### Post by etienne@Rofti on 2009-02-27
I think I have a general problem with sound capture.
When I go into Preferences > Sound , and then under Audio conferencing, choose Test Sound at the Sound Capture option box, it beeps for a moment, then the sound dies.
This does not happen whenever I test any other sound than the Capture.

Any ideas?

---

### Post by Pkadjipag on 2009-04-10
My built-in mic won't work even though I followed your suggestions. It's beginning to be a bit of a pain really... May it be a problem with my soundcard?

---

