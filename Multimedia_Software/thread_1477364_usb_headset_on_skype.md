---
title: "usb headset on skype"
date: 2010-05-08
forum: Multimedia Software
---

### Post by james1415 on 2010-05-08
I'm having problems with the builtin mike on my laptop, so I want to use  my USB Logitech headset for Skype (the main reason I need a mike).  The  headset (with mike) works fine on Audacity, but I can't get skype to  recognize it.

Under Sound Devices in the options panel in Skype, I  only get  Pulse Audio Server. Should it also list Logitech USB headset (like in the  Devices option in Audacity and in the Kmix panel)?   Or am I looking in the wrong place? 

... help ... !!

James

ps I remember having a similar problem in Windows a while ago, and the solution there was to start skype after plugging in the headset - so I've tried that here but it makes no difference.

---

### Post by anivegmin on 2010-05-09
Go to Sound Preferences.
Your device should be listed in the Hardware tab.

Then on the Input tab select your device for mic input.

Then Output tab select for audio output.

When you have finished your call you will have to reset the output device in the Output tab to get sound back on your main speakers.

This is really annoying and I haven't found a cure for this yet.

---

### Post by anivegmin on 2010-05-09
That's Sound Preferences in Ubuntu not Skype

---

### Post by kostkon on 2010-05-09
Install the *PulseAudio Device Chooser* utility and use the pulseaudio volume control to set an input and output device for Skype. PulseAudio will remember your choice.

---

### Post by anivegmin on 2010-05-09
Yes I have tried that - 

Start padevchooser.

Few seconds later my sound card disappears from hardware list.

Then Skype starts automatically using my handset, presumably because that's all there is. (apart from my cam)

While this is happening I have no idea what I am supposed to set or adjust.

Then, to get my sound card back, I have to restart pulse audio and everything reverts to normal with sound coming from main speakers.

Any help appreciated.

---

### Post by james1415 on 2010-05-12
Thanks guys - that seems to work.  I have installed the PulsaAudio device chooser, and it has  remembered the settings for Skype (though in order to set the settings, it apears skype actually has to be using record/playback - so I set them while using the skype call testing service). And it still uses the external speakers for other programs.

James

ps
I must say it took me a while to find PulseAudio device chooser on KPackageKit.  I had it set to Find by Name (rather than by description), and entered pulseaudio (turns out to be case sensitive), and there are over 20 files listed, none of them saying anything about device chooser.  I then noticed anivegmin called it padevchooser, and that worked (so thanks, anivegmin). I suspect the database is probably quite a stumbling block to people  transferring to linux - surely there's a better way of presenting the list of files - eg with subheadings, such as basic usage, enhancements, and development.

---

### Post by Bucky Ball on 2010-05-13
Tip: Get Skype going on a test call, open Pulse Volume Control and in the Playback Stream window right click on the stream and 'Move Stream' to whichever audio device you like. This took me ages to figure out and there is no clear description of how to set up and get this happening. Ad hoc.

You can do this with any audio stream but you need to get it going first. In my opinion clumsy.

---

### Post by Barney on 2010-05-13
Bucky Ball's solution worked for me:

 Re: usb headset on skype
Tip: Get Skype going on a test call, open Pulse Volume Control and in the Playback Stream window right click on the stream and 'Move Stream' to whichever audio device you like. This took me ages to figure out and there is no clear description of how to set up and get this happening. Ad hoc.

---

### Post by Bucky Ball on 2010-05-14
> **Barney said:**
> Bucky Ball's solution worked for me:

 This took me ages to figure out and there is no clear description of how to set up and get this happening. Ad hoc.

Agreed. It took me ages too and this was a result of cobbling together various tips from various pages. There is no real comprehensive guide from start to finish. I only found one site with the 'right click-'move stream'' tip in all my searching.

This tip works with any audio playback stream incidentally. If you start your music player and check the stream in that window you can move it to any available device. Quite handy really but quite clumsy also as you have to get the stream going to then move it to where you want it seems.

---

### Post by LanceHaverkamp on 2011-02-11
What do you mean by "move stream"?  All I see after right-clicking is "terminate playback".

---

### Post by grashdur on 2011-05-21
Wow! Hey all of you, thanks for the useful info -- I've been tinkering with this off and on for years and couldn't get it to work since Jaunty Jack! You wouldn't believe how many separate threads are ongoing on this topic here and elsewhere online! Thanks especially to james1415 for making the crucial details extra clear. Without that I wouldn't have done it.

So glad to be finally able to use Skype with a newer version of Ubuntu! :D

---

### Post by Timothy Taylor on 2011-11-09
After ages banging my head against the wall from frustrated attempts to get my Yealink USB phone to work with Ubuntu, I have succeeded!  
At LAST!!
Yay!!!!
:)

Bucky Ball's solution worked for me too - thank-you very much!

Also key to this success was installing the Pulse Audio Manager, which enables the phone device properties to be tweaked to set the volumes to a useful level.

I can't believe what an absolute pain it has been to get such a commonly used device set up to work just as a simple mic and earpiece... 
:(

---

### Post by Timothy Taylor on 2011-11-10
Ah - looks like I spoke too soon: started my PC this morning and the USB phone is back to not working again.

This is really, really ****ing infuriating.

This rubbish needs sorting out while I'm still responsible for my actions...
:mad:

ETA:
after some partial success getting sound out of my USB phone, nothing works *at all* now.  
Absolutely ****ing useless.
:mad:

---

