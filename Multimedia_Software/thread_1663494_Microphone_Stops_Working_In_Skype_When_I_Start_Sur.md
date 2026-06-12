---
title: "Microphone Stops Working In Skype When I Start Surfing The Web"
date: 2011-01-09
forum: Multimedia Software
---

### Post by bry72 on 2011-01-09
Hey Guys,

Info about my system:  I am using Ubuntu 10.04 on a Toshiba A100 Laptop.  I am using a headphone/microphone combo (Like a McDonald's drive thru employee uses) plugged into the front of the microphone and headset jacks.  This headset combo came with the Logitech C310H webcam.

I am running into a problem whenever I talk with someone on Skype and try to surf the web at the same time.  Once I start looking at websites, the microphone on my end stops working completely.  I can hear the other person but they cannot hear me.  The call is still connected but I have to end the call since they cannot hear me.

After this happens, I go over to the "Sound Preference" icon, choose the input tab, speak into the microphone and nothing registers in the Input Level.  I try messing around with the Input Volume but the microphone doesn't register at all.  I have tried shutting down Skype and restarting it, but the microphone still does not work.  I have tried shutting down everything, running BleachBit, restarting Skype and the microphone still does not work.  The only solution I have come up with is rebooting my computer, which sucks since it takes about 3-4 minutes to get back on Skype and reconnect with the person..

I have already unchecked the box "Allow Skype to automatically adjust my mixer levels" under Sound Devices in Options in Skype.  This was an issue before that was causing the mic to cut out, but unchecking that box helped...until I start surfing the web and using Skype at the same time.

Anyone else have this problem that they have found a solution for? The obvious answer would be to not surf the web while Skyping but since I sometimes research info on websites during a conversation, this is not an option.  Besides, I think using Skype and surfing the web at the same time should be something that is "doable" in Ubuntu.

---

### Post by bry72 on 2011-01-21
UPDATE:  I am still having problems with the mic cutting out using pulseaudio in Skype.

I tried switching everything over to Alsa using this technique: 
 [http://www.jeffsplace.net/node/12](http://www.jeffsplace.net/node/12)

  Doing that only brought on other problems.  I reversed everything back to pulseaudio.

I have installed the pulseaudio volume controller.  Under "Input Devices", I have pushed the front left to 0% and the front right to 100% based on what is written here:
[https://help.ubuntu.com/community/SkypeTroubleshooting](https://help.ubuntu.com/community/SkypeTroubleshooting)

I have gone into gconf-editor and under System->Gstreamer->0.10->Default, I have set audiosink, chataudiosink and musicaudiosink all to "pulsesink".

I have gone into gstreamer-properties to make sure both the Audio Default Output and Input Plugins are listed as "Pulse Audio Sound Server".

I have removed the Gnome Alsa Mixer.

I still have something labeled as "Mixer" under Applications->Sound and Video.  It is labelled as the "Audio Mixer for the Xfce Desktop Environment".  When I go into the Ubuntu Software Center and look at my installed software, it is not listed.

When I open up this mixer, it gives a label of "Mixer-HDA ATI SB (Alsa Mixer)".  Any ideas on how this can be removed?  I already have the Pulseaudio volume control and this one is not needed.

I have rebooted after each step and checked the microphone. I can still only get the microphone to work for about 4 minutes in Skype before it cuts off.  I have nothing else opened but Skype and I'm not surfing the web and it still cuts off.  

Under Options->Sound Devices in Skype, I have only one option of pulseaudio server(local) for Microphone, Speakers and Ringing.

The sound for movies as well as youtube.com works fine.  I don't use an online music player so I couldn't tell you if that works or not.

Pretty darn frustrated at this point as Skype worked fine when I use to use Windows.  From what I can gather looking through the ubuntu forums as well as the skype forums, the microphone issue in Skype has been ongoing for quite some time (over 2 years).  I've yet to come across a thread that had the solution...at least for my computer.

Anyone else have any suggestions?

---

### Post by gdea73 on 2012-03-22
This is extremely frustrating, I have the same problem, whenever Skype is opened the mic disables until a reboot.

---

### Post by geoffree on 2012-04-05
I see your post was awhile ago.  Have you found anything new to solve it?
I have same problem.

---

### Post by geoffree on 2012-04-05
I have similar problem except my mic doesnt work even when I'm only using Skype. Tried all the fixes that you all have tried.  Any newer ideas?

geo

---

