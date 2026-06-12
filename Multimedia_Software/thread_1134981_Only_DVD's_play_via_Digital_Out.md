---
title: "Only DVD's play via Digital Out"
date: 2009-04-24
forum: Multimedia Software
---

### Post by racerraul on 2009-04-24
I had the digital ouput working with all media.  Mp3, video files and internet radio.

But after playing a DVD, now only DVD can be heard from the digital output.
I noticed the problem began when I changed the audio preferences in xine for the digital passthrough.

I have since removed xine and settled for VLC.  But the problem persists... only DVD's work via Digital Out.

I'm hoping someone can tell me what changed... seems to me that some configuration file has changed to cause this.

I have a theory, based on some observations on my amp... before I made the changes in an effort to get 5.1 sound from the DVD the digital stream was ID as a PCM stream by the amp.  In this manner no matter what I played worked via the digital output.

After I set the Digital Passthrough in xine, the amp now ID the digital signal as DD 5.1, and in this mode only the DVD can be heard via digital out.

I have tried searching for what might have changed, but can't find it.

initially I was able to test the card outputs by doing this...
in a terminal window...
aplay -D hw:0,0 test.wav
and I hear the test tone via analog

aplay -D hw:0,1 test.wav
used play the test sound file via digital but not anymore.

---

### Post by racerraul on 2009-04-24
Been googling all night about this... and just tried searching for changing the digital audio stream in Linux.  And found this command...

in a terminal window run...
iecset audio on

if anyone knows what it does... let me know.  for now, happy to have my audio working again.

---

