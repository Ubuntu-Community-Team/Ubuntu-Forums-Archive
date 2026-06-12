---
title: "audio problems using webcam and skype"
date: 2011-05-07
forum: Multimedia Software
---

### Post by petefan12 on 2011-05-07
I'm running Natty Narwhal and really like it. Today I bought a Digitech c160m webcam for video calls with my wife since she travels 75% of the time. I gave her the microphone to plug into her netbook. She runs Windows XP on her netbook and her netbook has a built in webcam (im rambling). The webcam I bought for my laptop has an microphone built into it. Both of us have Skype accounts and we are able to call each other with no problem. I can see and hear her and she can see me, but cant hear me. I know the microphone in my webcam works because I can do a test call with skype and it is fine and I can record a video with the Cheese application and it plays back with sound.

Why do you think my wife cant hear me on her netbook. What setting in Natty can I check. I looked at the sound preferences and changed the Input to 0824 analog mono. Also, when we tried it with the microphone and earpiece plugged into my computer instead of the webcam built in microphone, she could her me, but then I couldn't hear her. Dunno if her netbook has a built in micrphone or not. 

I hope my question makes sense. Do i need to buy another microphone and ignore the one built into the webcam?

---

### Post by b0b138 on 2011-05-07
Ok this mount sound really silly, but, if her netbook has a built in webcam, it should have its own mic.  And if shes plugging in a separate mic, might she be plugging it into a headphone jack, thus disabling her speakers?  what netbook is it?

---

### Post by petefan12 on 2011-05-07
It is an EEE PC. She is still here with me tonight and leaves tomorrow morning. The microphone has two plugs, one for microphone and one for speakers. Initially, she had both plugged into her netbook, but has now unplugged the speaker plug from the netbook. I checked my sound preferences and and went into alsamixer but wasnt sure what to do, since im still new to ubuntu.

thanks

---

### Post by b0b138 on 2011-05-07
well if your fine in cheese and the test call, it shouldn't be on your end.

Try without the extra stuff plugged into the netbook.

Also, it sounds like you're using a headset?  Make sure the volume for the headphones is turned up and not muted in windows.

---

### Post by xmfclick on 2011-06-20
Sorry if this is covered in another thread but I just spent half an hour searching here and on the Skype forums and couldn't find it ...

I just loaded Skype 2.2.0.25 on my Acer Aspire One 150 running Ubuntu 11.04(?) Natty Narwhal (the latest version, anyway). It's a new Ubuntu installation, not tweaked, fresh out of the (download) box. Skype is not seeing the built-in microphone.

There's stuff in the Skype release notes on their website about configuring Pulseaudio, and I have followed those instructions (i.e. obtain the Pulseaudio Volume Control app and make sure the input side is configured correctly) but to no avail. Skype Call Test connects but there is silence when it comes to playing back the message I spoke.

Thing is, the mic does work because the Ubuntu sound recorder app works fine. (Also, and much to my surprise, Skype sees the built-in web cam -- it's just the mic it can't find.)

I am loath to go through the procedure of disabling Pulseaudio and reverting to ALSA only (as described in the Skype release notes as an "if all else fails you could try this" option) because the main reason for installing Ubuntu is that I screwed up the audio on the original Linpus installation on the Acer by messing around with ALSA. I'm a Linux newbie, so everything I'm doing is seat-of-the-pants stuff and the last thing I want is to start trying to install and uninstall various bits and pieces of Ubuntu/Linux on the off chance that something might work. That's what broke Linpus in the first place. I ended up with Skype not working and none of the other audio stuff working either.

So, what can I do? I assume the Skype/Pulseaudio thing is a known problem by now -- does it have a fix? Or, I have seen elsewhere that Skype 2.0 worked OK with Ubuntu 11 -- any idea if that is true, and if so, where I can get hold of 2.0 and how to install it?

Thanks in anticipation.

---

