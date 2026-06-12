---
title: "Microphone problem"
date: 2006-12-30
forum: Multimedia &amp; Video
---

### Post by Dekunuts on 2006-12-30
Hi, 

I am trying to use skype, but it tells me there is a problem with my audio device. When i change the skype setting to OSS it doesn't give an error and I can here myself very quietly on the test call. 

When i blow into the microphone while I'm on the desktop, not using skype or anything, i can hear the sound coming from my speakers. 

When I go to system->preferences->Sound, everything is listed as ALSA, which I think right, but when I use anything else than silence for the sound capture thing, the sound-recorder program refuses to start , telling me i have to change my sound settings. 

As you can see, this is a mess and I don't know what settings to use or how to fix all this. Also, when i run alsamixer, it doesn't work and gives : function snd_ctl_open failed for default : No such device.

the normal volume control does work and my mic is unmuted..

Please help

---

### Post by Dekunuts on 2006-12-31
please, someone, help me... do i have to pay in order for someone to really help me or how does this work ?

---

### Post by Handssolow on 2006-12-31
Sorry that nobody has replied but that's sometimes the way it goes. If you search this Forum section you should find lots of advise about setting up your microphone. Have you expanded up Alsamixer to enable the microphone boost? You might be able to get it working.

Now the bad news, I didn't get mine working. I had a lot of bother setting up my microphone for Skype because my Asus mobo has on-board sound chips. I kept hearing my microphone sounds in the speakers just like you. Either  I got feedback or my voice recorded by the Skype test call was too faint.

Incidentally I could also  only get Skype running under XP on my  other Asus PC by using the webcam microphone (Logitec Quickcam Pro 4000) and not with a separate microphone plugged into the rear mobo socket.

After several hours I finally fitted an Creative Audigy sound card that I'd used on an older PC which solved the problems of feedback and low volume plus the sound from the speakers is better. A Skype test call is now satisfactory.

---

### Post by Dekunuts on 2007-01-02
thank you, finally a reply :) 

One of the problems is that alsamixer won't run, it's broken and gives an error (see 1st post).
I am also using an asus motherboard but i installed a hercules sound cad in my pc and am using that one, but it doesn't work either (for the mic, all other things work). I have searched a lot but can't find a solution, I installed xp on a second drive and there it works, which is a shame :( 

I really like Ubuntu, but sometimes it's too hard to find good information...oh well...maybe i can buy an old pc or something and use skype on that through windows.

---

### Post by Handssolow on 2007-01-04
I'm bumping this thread because I feel others should offer you some other suggestions.

---

### Post by Dekunuts on 2007-01-04
that would be great:)  I'm really close to the perfect Ubuntu setup, just the mic and my other problem in another thread that I won't discuss here ofcourse;)  I really don't want to keep XP around for something silly as a microphone, I think everyone would agree with that.

---

### Post by Ambimom on 2007-01-04
Have you tried the comprehensive sound guide [http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

Does the microphone work when you use Sound Recorder? 
 
Have you enabled sound mixing in System /Preferences /Sound?

---

### Post by Dekunuts on 2007-01-04
Yes, I have tried that guide, and it helped me one time with a different problem, but not with this one. I can't find the option you are referring to under sound preferences. How could that be possible ?

---

### Post by Dekunuts on 2007-01-06
Maybe someone can help me with this error : 

gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.

I get it when i try to assign ALSA to the microphone in system->preferences->sound

---

### Post by Dekunuts on 2007-01-07
someone, please ](*,)

---

### Post by chartman on 2007-01-13
I am not sure whether this is going to be a lot of help... I couldn't get my mic to work either - it was one that you connect to the sound card. I even tried 2 different sound cards. Finally I bought a USD microphone from Logitec (AK 5370), plugged it in, booted, opened Skype.... the device was already detected and I could select as "Audio In". Worked PERFECTLY out-of-the box (LITERALLY).
That's no guarantee though.. but it only cost me £14 - maybe worth the risk?
Good luck.

---

### Post by Dekunuts on 2007-01-17
Thank you for the reply, it's a good suggestion.:)  But before I buy one, I'll try to use one from someone to make sure I can get it to work. 

In case there is someone who can tell me how to fix this error, i could keep the microphone I have now.

gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.

thanks

---

### Post by dcherryholmes on 2007-02-26
I'm getting the same error you are.  If I figure anything out I'll post it here.

---

### Post by HasratUSA on 2007-02-27
> **Dekunuts said:**
> Thank you for the reply, it's a good suggestion.:)  But before I buy one, I'll try to use one from someone to make sure I can get it to work. 

In case there is someone who can tell me how to fix this error, i could keep the microphone I have now.

gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.

thanks

in most cases you wouldn't need to buy another USB microphone.  at this point i really do understand that some of you guys haven't experimented enough with the settings. Believe it or not I was entirely unable to even record sound and make Linux detect a valid mic in my PC. the problem was almost killing me because my mom wants to talk to me often on yahoo messenger and to do that i had to switch to that boring useless Windows XP or whatever that came with dell and i hated to lose my precious linux uptime.

But no more, since just a few hours ago i fixed it all miraculously but simply (it was really a no-brainer). My dell dimension e521 has two ports for inserting a microphone. I believe the front one installed right under the dvd/rw is called front mic and the one at the very back and under the power cord is called 'mic'.  in windows XP both of these ports worked fine, the mic is usually attached to the front mic.

Now i opened alsamixer in terminal and saw that the mic wasn't active and there was no 'left right' thing or anything in there. so, i simply attached the mic to the 'mic' (the one at the back and under the power cord) and retried and walla! everything worked. Then i went to Yahoo chat rooms and to be fully sure, talked to some people and told them to tell me something about my voice quality and according to them it was really okay.

Let me tell you that it's 100 percent true that whenever you encounter problems such as this, it's not either ubuntu's or Linux's fault. And it is also true that by having been using Windows for more than 4-5 years, most of us who have been forced to adopt Windows has lost the patience, skill and interest to investigate and experiment.  Believe me, when you would solve a problem in linux, you yourself would realize how dumb you really have been forced to be turned into by M$. I'm not trying to look like i'm an expert linux user and i hate MS and blah blah blah. I just think M$ and its closed-source software don't let you grow within your self the interest to experiment and analyze the various facets of technology. No wonder why Eric Steven Raymond in his book How to Become a Hacker said, "Trying to learn to hack on a Microsoft Windows machine or under any other closed-source system is like trying to learn to dance while wearing a body cast".

Good luck everyone!

---

### Post by fakie_flip on 2007-03-03
> **Dekunuts said:**
> someone, please ](*,)

[http://www.google.com/search?hl=en&q=gconfaudiosrc+%21+audioconvert+%21+audioresample+%21+gconfaudiosink+profile%3Dchat&btnG=Google+Search](http://www.google.com/search?hl=en&q=gconfaudiosrc+%21+audioconvert+%21+audioresample+%21+gconfaudiosink+profile%3Dchat&btnG=Google+Search)

---

### Post by dbclinton on 2008-03-03
Hi,
I have exactly the same problem - there's no microphone input beyond a bit of static and alsamixer doesn't load, returning the error message: 
[INDENT]PULSEAUDIO: Unable to connect: Connection refused
alsamixer: function snd_ctl_open failed for default: Connection refused[/INDENT]

I wonder if it isn't a hardware conflict. I'm running a dual boot Winxp/Edubuntu 7.1.0 HP Vectra 420 MT with integrated audio (XP reports that there's an Intel BA/BAM 82801 AC'97 Audio controller along with a Creative Sound Blaster 16/AWE 32 card.

When I got the computer (used, from a corporate environment) the integrated audio was disabled in BIOS. the HP has an internal speaker which does process system audio (beyond simple system sounds) but plugging in external speakers, of course, didn't work. I enabled the audio in BIOS and got the external speakers working in both XP and Linus. However, the microphone jack isn't working (in either OS) and XP reports "this device cannot start - code 10" about the Sound Blaster.

I wonder if the HPs main board sound is conflicting with the mic function of the Sound Blaster card.

Does this sound familiar to anyone else with this problem?

David

---

### Post by dbclinton on 2008-03-03
It looks like I found a bit of a work-around. I still haven't got alsamixer working, but alienpilgrim in a post at 
[http://ubuntuforums.org/showthread.php?t=634290](http://ubuntuforums.org/showthread.php?t=634290)
wrote:
===========================
1) Right click the speaker on panel, choose "Open Volume Control"
2) Click "Options" tab. If you don't see the options tab, edit preferences and enable "Digital input source", this will make it appear.
3) Change the "Digital Input Source" to "Digital Mic 1" from "Analog Inputs".
To set the mic volume, edit the preferences and enable "digital". A "Recording" tab appears. Move the slider up for the Digital setting. Use the sound recorder to test your sound levels.
============================

Now it didn't work quite like that for me - there was no "digital input source" selection to toggle, but I simply clicked 
"File/Change device/Analog Devices AD 1885 (OSS mixer)"
hit the "record" tab and made sure that the two "microphone" settings were toggled.
The microphone now works in Audacity (though sound recorder still won't load and I haven't tested Skype yet).
It's progress, right?
David

---

### Post by roninbk on 2008-03-03
Similar situation here, attempting to set up sound for Audacity.

My message when attempting to set up Sound Capture in System - Preferences - Sound: 
> Failed to construct audio pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'
Incidentally, I get the message, no matter whether I assign ALSA or OSS to the Sound Capture setting.

(Ubuntu 7.10, AMD64, VIA 8237 chipset)

---

### Post by roninbk on 2008-03-03
OK, after mucking about with the Volume Control settings as suggested by dbclinton above, and swapping back and forth between forward and rear jacks, I was able to finally record successfully in Sound Recorder and Audacity. I was not able to correct the error I mentioned above, but since my initial problem was solved, I'll move along...

---

