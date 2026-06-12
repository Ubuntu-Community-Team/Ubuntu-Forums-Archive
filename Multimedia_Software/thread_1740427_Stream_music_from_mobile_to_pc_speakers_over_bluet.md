---
title: "Stream music from mobile to pc speakers over bluetooth"
date: 2011-04-27
forum: Multimedia Software
---

### Post by krshna_r on 2011-04-27
Hi All,
 
I am trying to stream music from mobile phone (Samsung Galaxy S) to my laptop. I am using a bluetooth adapter of version 2.1
 
I have followed the steps given by Ric123 as given in one of the solved threads.
 
Everything goes fine until the last step.
 
After doing load-module module-loopback source=<name> sink=<name> successfully when i try to play audio from my mobile phone, the pulseaudio is getting disconnected and is not able to connect again.
 
When i check the log, i am seeing the following error
 
"pulseaudio[6694]: alsa-util.c: snd_pcm_avail_delay() returned strange values: delay 0 is less than avail 14.
 
pulseaudio[6694]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers."
 
Why does this occur. Someone please help me as i am a newbie to Linux
 
Whr am i going wrong.....

---

