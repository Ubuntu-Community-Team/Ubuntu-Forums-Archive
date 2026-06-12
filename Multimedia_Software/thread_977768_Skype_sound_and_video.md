---
title: "Skype sound and video"
date: 2008-11-10
forum: Multimedia Software
---

### Post by okkadiroglu on 2008-11-10
Hi,

On two notebooks (Compaq nx6110 and Toshiba Satellite A135) I use Ubuntu 8.10 and I do have sound and video problems. I can listen to internet radio and other sound and video files by using Amarok and other media players, but when I use Skype I get "Problem with Audio Playback" warning. I have reinstalled the most up-to-date version of Skype. Also, I have video problems with Skype while my webcam works fine with Cheese and Ekiga programs. I did not have these problems before I upgraded to 8.10 from 8.04.

Many thanks for the help,

Best Regards

---

### Post by GoLinux on 2008-11-10
8.10 Intrepid is the first Ubuntu version I'm using and I had problems with Skype as well on my Thinkpad T41.

I solved the audio output problem selecting "Pulse" as "Sound Out" and "Ringing" in Skype's audio options.

Fixing the sound input via the built-in microphone took a little more work. First I had to check "capture" and "microphone capture" in the "preferences" of the audio mixer. Make sure the sliders are up and unmuted.

Next select the name of your sound card in "sound In" from the drop-down list. You'll probably see it listed with several slightly different identifiers. In my case I got the microphone working selecting the one listed right after "pulse". If it doesn't work, try all the others until you get the one which does.

I used the "make a test call" function in Skype options to check wich selection of "sound in" worked.

Now Skype works fine, but I still can't record through "Sound Recorder". As all the remaining applications have sound out, at this time that is a secondary issue for me.

---

### Post by okkadiroglu on 2008-11-11
Thank you very much for your help. I did what you have told me. Now I can hear the Skype sound but my microphone doen not work. It is connected, "Sound in", "Sound Out" and "Ringing" are all pulse and I hear sound when I try "Make a test sound" and "Make a test call". My sound device is Intel ICH6 and mic is on at "Playback" list of "Volume Control".At "Recording" tab I keep changing "Capture" volume but after I leave the page the mic changes to close. I sense that I am very close to the solution and missing a small step. But what is it, I have no idea.

---

### Post by GoLinux on 2008-11-13
Selecting "Pulse" as "Sound in" didn't work for me either. Leave "Sound out" and "Ringing" set to "Pulse" and try to select a different device for "Sound In". In my case selecting the one listed right after "Pulse" worked.

It is a time consuming process as you have to select the device and then try a test call everytime, but it is worth trying.

In my case too the "capture" slide changes to what i looks like "mute" (the small red "X" on the microphone icon), but that doesn't seem to have effect as long as the right device is selected as "Sound in". Make sure the "microphone capture" shows and the slider is all up, not just "capture".

To check if the hardware is ok, you can also activate "microphone boost" and try to increase the volume on your notebook until you get the typical high pitch feedback sound. Very crude, but at least will tell you if the microphone is activated or not.

---

### Post by GoLinux on 2008-11-13
You may want to try this too:

[http://ubuntuforums.org/showthread.php?t=980929&highlight=webcam+skype](http://ubuntuforums.org/showthread.php?t=980929&highlight=webcam+skype)

I just found it searching information on how to get my Intel USB webcam to work with Skype. Now that I solved the audio, it is time to get video working....

---

