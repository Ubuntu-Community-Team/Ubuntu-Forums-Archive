---
title: "Hearing myself through the speakers"
date: 2006-08-01
forum: Multimedia &amp; Video
---

### Post by PotatoPeeler on 2006-08-01
I'm somewhat of a Linux n00b so please forgive me for my ignorance.  I've done multiple searches to try and resolve this problem but nothing has helped.  

The problem is that everytime I speak through my microphone, I can hear myself through the speakers.  I've gone into alsa mixer and messes around with muting/unmuting the microphone, capture, and some other stuff but nothing seems to work.  I've tested the sound capture by using the Sound Recorder and that seems to work fine.  However, when I do this, I can still hear myself through the speakers when I'm recording.  

Anyone go any ideas?

I'm using and old SoundBlaster Live! 5.1 card.  AlsaMixer tells me my chipset is SigmaTel STAC9708,11

Thanks in advance for the help.

---

### Post by IYY on 2006-08-01
Are you sure the microphone is muted?

---

### Post by Washington Irving on 2006-08-01
> Are you sure the microphone is muted?
I'd guess that he'll probably want the mic on (while recording).
I'm pretty much a linux n00b aswell but I do have one suggestion which is that you mute the speakers when you are recording and then unmute them when you've finished. 

There probably is a better (and permanent) way to deal with this though and hopefully someone will provide it for you.

---

### Post by encompass on 2006-08-02
Unfortunately I have done it this way... rightclick on the panel and add to panel... then select volume control... from there:
you can right click on it and move it to when you want it... then goto preference and select the device part you wish to control... like the mic.  from there you can jsut scrol your mouse well to adjust the volume so when you use it it is on... and when you don't it is off.
It is nice to have if you use things like skype alot and want to adjust the volume.
Lastly, scrolling you mouse is nice to use as an adjuster.  Lets see windows do it.

---

### Post by PotatoPeeler on 2006-08-02
Alright, I continued to monkey with the settings and here's the resut.  All of this was done through the graphical AlsaMixer.

Also, let me state that I don't care about making recordings.  I'm just using the sound recorder to test the microphone since I want to use it with Skype and what not.

Setting #1:
Microphone: Unmuted and audio capture enabled.
Capture:   Unmuted and audio capture enabled.

Result: I can make recordings just fine but I can hear myself in through the speakers while doing so.

Setting #2: 
Microphone: Muted and audio capture disabled.
Capture:   Unmuted and audio capture enabled.

Result: I can make recordings just fine but I can hear myself in through the speakers while doing so.

Setting #3:
Microphone: Muted and audio capture enabled.
Capture:   Muted and audio capture enabled.

Result: I can make recordings just fine but I can hear myself in through the speakers while doing so.

Setting #4:
Microphone: Muted and audio capture disabled.
Capture:   Muted and audio capture enabled.

Result: I can make recordings just fine but I can hear myself in through the speakers while doing so.


Does this help narrow it down any?  I still can't figure out how to get it to work and I'm becoming somewhat frustrated.

Thanks.

---

### Post by PotatoPeeler on 2006-08-02
Here's another thing.  When I try to make a call through Skype, I can hear the other party on though my speakers just fine but they cannot hear me.  I'm sure that the microphone is not working properly but I still hear myself through my own speakers.  I know the microphone is not setup properly but I can't for the life of me figure out how to resolve the issue.

---

### Post by PotatoPeeler on 2006-08-03
Anyone?

---

### Post by BobSongs on 2006-08-03
Yeah; listen. I'm getting roughly the same problem. I'm not quite sure what's going on. But I'll keep you posted if I get a solution.

PC: Celeron
SoundCard: SoundBlaster Live 5.1
Mic: On, able to hear through the speakers
Skype: Unable to hear me

If I click Mic boost I get feedback through the speakers. So I know for sure the PC's getting feed from the Mic.

But I just tested both in Sound Recorder and in Audacity and I'm unable to record from the Mic. It's giving me a flat line. Let me tinker and I'll see what I can come up with, cool?

[INDENT]**Edit:** Just for the sake of adding it in for the curious. The Capture aspect of the Volume Control has the microphone at full and Capture at about 80%. Both Capture and Microphone are unmuted and the "toggle audio capture from" buttons have no red "X" in them.[/INDENT]

[INDENT]**Edit 2:** And to make matters more complex, I booted into XP and the Sound Recorder captures my mic sounds perfectly. ](*,) [/INDENT]

---

### Post by PotatoPeeler on 2006-08-03
That would be outstanding.  Thanks!

---

### Post by BobSongs on 2006-08-03
Listen: I've gotten nothing yet. I'm not giving up on you, dude.

But along with the mic not working there's also the problem with XSane not working either. Resorting to a full re-install is not a favorite option ... but I can easily back up my config files and re-install. It works but it's not a long term solution.

Still, I think I'll wait it out a bit and we'll see what turns up as far as answers.

---

### Post by PotatoPeeler on 2006-08-04
Thanks, man.  I appreciate it.  Hopefully we can get this figured out.  It'll be a little difficult because the computer that I have Ubuntu running on is for my brother.  He doesn't know jack about computers but only uses it for email and surfing so he should be fine.  I wanted to get the mic working properly because his wife uses it for talking with her parents in Latvia.  Hopefully when I do find a solution I will be able to walk him through it via email.  

In the mean time, I'll keep searching and I'll have an eye on this thread.  If I come across anything helpful, I'll post it here.

---

### Post by BobSongs on 2006-08-06
Well. I spoke to pros on the IRC. No success.

So: it meant re-installing. Now it works just fine. I think something happened in the kernel somewhere. It's not the best solution. But in this case it worked fine.

---

### Post by encompass on 2006-08-06
I got it to work!!! I can record and not hear myself... cool huh?
Hear is a screen shot... do you get what I did?

---

### Post by BobSongs on 2006-08-15
Hmm. Thought I'd revisit this thread. Actually, I'm not sure what you did. But the screenshots might help someone along.

I tried using the 'alsamixer' at the command prompt. No go. I think the problem was at a kernel level. Very frustrating.

All works well now. Sometimes something just hits a glitch while installing and the kernel isn't properly configured. It happens.

---

### Post by bogaerbr on 2006-08-16
Hallo,

Reading your posts, I start to wander whether the problem is not in the sound card.
I also use a SBLive 5.1 and I keep having problems when I want to use Skype.
Yesterday was typical : at 18h I could hear and record myself at echo123, at 20h no problem making a call, and at 20h30 Skype pretended that there was a problem with my audio device. Altough I had not changed anything on the settings in between...
This morning I tried again, first : Skype reported no problem with the audio device but I could not hear anything, I changed under 'tools','options','Head/handset' the audio device for calls and I could hear echo123 but not myself; finally I changed the settings of Alsa mixer, Capture, Capture, toggle audio capture from Capture and slide the markers to about 80%  and now I can hear echo123 and my own recording.
I have no idea why these settings change... I would hope that any configuration that works would still work half an hour later, a day later, or when I next reboot my system. But it doesn't..

Ah yes : I do hear myself through the speaker, but that doesn't bother me..

Bruno

---

### Post by haTem on 2006-08-25
I just figured out how to stop noise from my microphone from being played back over the speakers.

Here's what you need to do:

[LIST]
[*]Run alsamixer in a terminal (the same general process should apply to the graphical frontends)
[*]Go to "Mic". I have mine set to 100 (use the up and down arrows). The key part is to mute it (press m).
[*]You can toggle "Mic Boost" if you want (by pressing m), it just depends on how loud you want your microphone to record.
[*]Go to "AC97". This is another key part. Set it to 0.
[*]Press F4. You should see a list of new items.
[*]Head to "Mic" and make sure it's set to capture (press spacebar).
[*]Go to "Capture". Set desired volume and make sure it also is set to capture (press spacebar).
[*]Then go to "AC97". This appears to cause different results from the "AC97" in the previous section. It impacts your microphone's volume though, so play with the setting a bit.
[/LIST]

After following this procedure, I was able to use TeamSpeak and Sound Recorder without any problems with the added benefit of not hearing myself play back over the speakers. I haven't had a chance to try Skype yet, but it should work. I hope this helps.

Regards,
Hatem

Edit: Just tried Skype using their Echo123 bot, seems to be working fine.

---

### Post by mindless on 2006-09-24
> **haTem said:**
> I just figured out how to stop noise from my microphone from being played back over the speakers.

Here's what you need to do:

[LIST]
[*]Run alsamixer in a terminal (the same general process should apply to the graphical frontends)
[*]Go to "Mic". I have mine set to 100 (use the up and down arrows). The key part is to mute it (press m).
[*]You can toggle "Mic Boost" if you want (by pressing m), it just depends on how loud you want your microphone to record.
[*]Go to "AC97". This is another key part. Set it to 0.
[*]Press F4. You should see a list of new items.
[*]Head to "Mic" and make sure it's set to capture (press spacebar).
[*]Go to "Capture". Set desired volume and make sure it also is set to capture (press spacebar).
[*]Then go to "AC97". This appears to cause different results from the "AC97" in the previous section. It impacts your microphone's volume though, so play with the setting a bit.
[/LIST]

After following this procedure, I was able to use TeamSpeak and Sound Recorder without any problems with the added benefit of not hearing myself play back over the speakers. I haven't had a chance to try Skype yet, but it should work. I hope this helps.

Regards,
Hatem

Edit: Just tried Skype using their Echo123 bot, seems to be working fine.

Thanks man. You are a legend. I spent some time messing with alsamixer but I just couldn't find out which settings did what. This saved me. :)

---

### Post by kostkon on 2007-02-04
> **haTem said:**
> I just figured out how to stop noise from my microphone from being played back over the speakers.

Here's what you need to do:

[LIST]
[*]Run alsamixer in a terminal (the same general process should apply to the graphical frontends)
[*]Go to "Mic". I have mine set to 100 (use the up and down arrows). The key part is to mute it (press m).
[*]You can toggle "Mic Boost" if you want (by pressing m), it just depends on how loud you want your microphone to record.
[*]Go to "AC97". This is another key part. Set it to 0.
[*]Press F4. You should see a list of new items.
[*]Head to "Mic" and make sure it's set to capture (press spacebar).
[*]Go to "Capture". Set desired volume and make sure it also is set to capture (press spacebar).
[*]Then go to "AC97". This appears to cause different results from the "AC97" in the previous section. It impacts your microphone's volume though, so play with the setting a bit.
[/LIST]

After following this procedure, I was able to use TeamSpeak and Sound Recorder without any problems with the added benefit of not hearing myself play back over the speakers. I haven't had a chance to try Skype yet, but it should work. I hope this helps.

Regards,
Hatem

Edit: Just tried Skype using their Echo123 bot, seems to be working fine.


Thanks from me, also! With your instructions I managed to make my mic to work! Thanks alot!

---

### Post by Demogorge on 2007-02-19
I just spent about an hour trying to fix this and your instructions helped me out too!

I have a Soundblaster Live 5.1 and it's a normal sized PCI card. There's no AC97 involved... Without this forum I don't think I would ever have figured this out.

---

### Post by Morkhaar on 2007-03-19
hello, 
i had the exact same problem and through the forum I found this which worked as a charm. I'm using ubuntu 6.06, and basically need the mic for skype. don't know if it works on recordings:

(from the gentoo forums)
**Run alsamixer in console, and if you don't have it, emerge alsa-utils. Go into the playback "tab" and mute mic. Go into the capture tab, I think f4 and hit space on Mic and space on capture until L R Captur is red under both Mic and Capture. make sure you turn up the volume using the up arrows.**

If you've already found what to do, nevermind, if you're still experiencing problems good luck!

---

### Post by Morkhaar on 2007-03-19
well, sorry! that happens when you're a newbie at the forum and do not read both of the pages of the thread..  :biggrin:

---

### Post by Didge on 2007-08-23
Many many thanks. I now have my perfect setup in 7.04 thanks to this last glitch being solved. 

I spent more time with this than getting the infamous Dreamweaver CS3 and Photoshop CS3 to work!

---

### Post by Death Rider on 2007-09-03
> **haTem said:**
> I just figured out how to stop noise from my microphone from being played back over the speakers.

Here's what you need to do:

[LIST]
[*]Run alsamixer in a terminal (the same general process should apply to the graphical frontends)
[*]Go to "Mic". I have mine set to 100 (use the up and down arrows). The key part is to mute it (press m).
[*]You can toggle "Mic Boost" if you want (by pressing m), it just depends on how loud you want your microphone to record.
[*]Go to "AC97". This is another key part. Set it to 0.
[*]Press F4. You should see a list of new items.
[*]Head to "Mic" and make sure it's set to capture (press spacebar).
[*]Go to "Capture". Set desired volume and make sure it also is set to capture (press spacebar).
[*]Then go to "AC97". This appears to cause different results from the "AC97" in the previous section. It impacts your microphone's volume though, so play with the setting a bit.
[/LIST]

After following this procedure, I was able to use TeamSpeak and Sound Recorder without any problems with the added benefit of not hearing myself play back over the speakers. I haven't had a chance to try Skype yet, but it should work. I hope this helps.

Regards,
Hatem

Edit: Just tried Skype using their Echo123 bot, seems to be working fine.

Works fine :)

---

### Post by savethewabbit on 2008-01-04
I had the same problem: I could hear myself through the speakers but others could not hear me via Skype. 
It was actually very weird and I don't know if what I'm about to say makes any sense, but still: I fixed it opening Sound Recorder and selecting "Microphone" under "Record from input". 
I don't know why or how, but just after I did that Skype worked too. If you're having this problem it sure is worth a try.

---

### Post by Claus7 on 2008-03-04
Hello,

very nice indeed this thread! haTem it worked nicely. savethewabbit I did what you mention, yet every time I open the Sound Recorder (under Applications->Sound and Image) the option returns to default.
I have to say that I could be able to configure the sound so as not to hear myself from the speakers via menu bar, by clicking under the microphone the icons that it had, yet the configuration wasn't permanent. 

Regards!

---

