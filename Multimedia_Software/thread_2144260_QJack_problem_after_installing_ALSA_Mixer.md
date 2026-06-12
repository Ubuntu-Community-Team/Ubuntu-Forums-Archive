---
title: "QJack problem after installing ALSA Mixer"
date: 2013-05-11
forum: Multimedia Software
---

### Post by Atitudes on 2013-05-11
Hi everyone!

First of all I would like to say that I am an Ubuntu enthusiast, my knowledge is basic as a simple user but I do like to experiment and try different functionalities and software.

_Overview:_
As a musician, I use QJack along with Guitarix and other programs such as Audacity, Ardour, Hydrogen, Reason... Until yesterday everything was working fine although I had the "brilliant" idea to try to get sound output from my speakers and headphone set at the same time. After some forum and google searches, it seemed that ALSA Mixer could be the solution but I was not able to achieve my goal  :sad: (If anyone could help me with this issue I would appreciate!). I sometimes use my sound card for audio input (Line-in or Mic entry), and other times an USB device when I do not have a Mixing table at hand. After having installed ALSA Mixer, my idea of having 2 sound output at the same time did not work, thus I removed it from my system.

_The problem:_
What happens now is that I have a sort of "*by-pass*" using my Line-in and QJack has no effect on it -> I disconnect everything and the sound continues to play. Even with all the connections properly connected it makes no input at all. I also noted that even without QJack, my line-in plays sound but do not make any input to any software, e.g. Audacity (Using ALSA and configuring the entry to Line-in).

_Note:_
None of the above applies when I use my mic entry as everything works as it should, the problem only affects the Line-in.


Everything happened after I installed and un-installed ALSA Mixer so I presume it to be the source of the problem, unfortunately with my poor knowledge I am unable to revert the situation now. I searched forums and googled about this but I was not able to find a solution to my problem. I really appreciate some help about this as I really want to make it work again as it was!!!

Thank you very much in advance.

---

### Post by Atitudes on 2013-05-14
Any tips please?

---

### Post by stevem531 on 2013-05-15
[FONT=arial]Hello Atitudes

I too use audio related software (on Ubuntu 12.04) including Audacity and QjackCtl with Jack.

I am not an expert, but I offer the following comments in the hope that it might help resolve your problem.

If I have understood the symptoms correctly, having had ALSA Mixer (package gnome-alsamixer) installed and then removed there now appears to be a permanent through-route between the Line-in and the sound card output (speakers/headphones).

Something that you might consider is whether your sound card hardware has any provision for through-routing of input signals to the outputs ?

For examining and changing sound card settings I use the program alsamixer, part of the the alsa-utils package, which is run from a terminal window but has a basic (ncurses) graphical iinterface.

The alsa-utils package includes other command line utilities that are useful for debugging the ALSA configuration, but they need to be used with care and I do not have sufficient experience to advise you further - you will need help from one of the 'real experts'. With a bit of luck one will turn up very soon !!

Regards

Stephen[/FONT]

---

### Post by Atitudes on 2013-05-15
Hi stevem531, thank you very much for your feed back![FONT=arial]

[/FONT]> **stevem531 said:**
> [FONT=arial]
If I have understood the symptoms correctly, having had ALSA Mixer (package gnome-alsamixer) installed and then removed there now appears to be a permanent through-route between the Line-in and the sound card output (speakers/headphones).[/FONT]


You understood it all, that's completely what happened! And my goal is to revert the situation since it would be lovely to use mic and Line-in inputs at the same time again (of course, without the referred through-route in my Line-in...).
[FONT=arial]
[/FONT]> **stevem531 said:**
> [FONT=arial]
[/FONT][FONT=arial]Something that you might consider is whether your sound card hardware has any provision for through-routing of input signals to the outputs ?

For examining and changing sound card settings I use the program alsamixer, part of the the alsa-utils package, which is run from a terminal window but has a basic (ncurses) graphical iinterface.[/FONT]
[FONT=arial]
The alsa-utils package includes other command line utilities that are useful for debugging the ALSA configuration, but they need to be used with care and I do not have sufficient experience to advise you further - you will need help from one of the 'real experts'. With a bit of luck one will turn up very soon !![/FONT]
[FONT=arial] [/FONT][FONT=arial] 

My sound card is on-board and it doesn't seems I can do anything to configure input/output signals "outside" of ALSA resources (If it is possible, please guide me I would really appreciate, maybe it is the source of this problem).

I did installed ALSA mixer but didn't changed anything in its configuration as I only tried some volume options aiming for having two simultaneous outputs (speakers and headphones). Some posts stated that if I could enable the "[/FONT]Headphone Jack Sense" option it would work but the latter did not appeared in the ALSA mixer utility. Furthermore, I did ran ALSA mixer you referred (the ncurses graphical interface) but everything seems ok, perhaps I am missing something in the middle... I really don't know and thus requiring help!

I will keep on trying different solutions, step by step but I agree with you, I think I really need some "real experts'" help at the moment.

Once again, thank you for your feedback!
Cheers.

---

### Post by stevem531 on 2013-05-16
Hi Atitudes

Just a couple more thoughts.

You could perhaps  just check again the sound card settings by running alsamixer (ncurses  version), and look especially at the Capture Options (F4 key) to make  sure that the Line-in capture channel has not been muted (dotted lines  being shown). Normal (unmuted) operation should show CAPTURE highlighted  in Red. The keyboard Spacebar toggles the mute/unmute state.

Also  check at the same time to look for perhaps an Input Selector Switch  that allows the capture channel normally used by the Line-in input to be  switched to any other input sources.


Some sound cards (even  just the normal built-in ones) allow mixing of one or more inputs  signals directly to the output. You might look in the alsamixer Playback  (F3) settings to see if there is a slider for the Playback Volume level  for the Line-in.

(I have never tried the GNOME Alsamixer but I  understand that apart from a few enhancements and the nicer GUI  interface it does much the same job as the ncurses alsamixer. I would  expect that any sound card settings that GNOME Alsamixer changed can be  changed back again using the ncurses version alsamixer).

Apart from the above though I am now running out of ideas.

You  mentioned that you were planning just to try things out step by step  and that seems to be the best way forward, and what I also try to do  when faced with a problem to solve.

Hope that you get it sorted soon, and let us know how you get on.

Regards

Stephen

---

### Post by Atitudes on 2013-05-19
Thank you very much stevem531 for another excellent input. I still haven't managed to solve the situation, I will have more time to experiment during the upcoming week. 

The alsamixer is a bit "tricky", I really have no idea about some of the options. Trying them one by one did not performed any desired change, I will try some combinations from now on registering the steps in order to be able to revert.

One thing I was thinking, but as I stated my knowledge is rather basic and this could be ridiculous but I will ask it anyway (I also found [this post]("http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/")). I know that some users disables the PulseAudio driver and use only the Alsa-mixer configurations to configure their sound settings. My thoughts were to remove PulseAudio, re-boot and re-install it. Do you think it could make any difference? (just a thought...)

Thank you very much for your kind help and inputs.

---

### Post by stevem531 on 2013-05-19
Hi Atitudes

I understand what you meant when you say that  alsamixer is a bit "tricky". Even for just a normal built-in sound card  there can be quite a large number of sliders and switches to control  which can be a bit confusing.

As your system has PulseAudio you  might consider installing the PulseAudio Volume Control (pavucontrol).  This has a proper GUI and would allow you to more easily control many of  the sound card settings, and it also features a 'bar' type level meter.  I have pavucontrol on my system and I find it very useful at times.

If  you leave the alsamixer terminal window open while running pavucontrol  you should see the associated alsamixer settings change in response to any changes  made in the pavucontrol settings. Also take care, (I expect that you  already are), when experimenting with the sound settings and leave  speakers & headphones unplugged until sure that the levels have been  set correctly.

I would be inclined to leave the PulseAudio  installation as it is though. I do not think that the process of  de-installing and re-installing would necessarily fix the sound card  issue, and it brings with it at least some risk of introducing other  problems.

I will leave you to try out a few more options over the  next few days. Please let us know how it is going and if there are any  other questions that arise.


Regards

Stephen

---

### Post by Atitudes on 2013-05-21
Hi stevem531!

I performed some more experiences today without getting any luck... I did not mess with the PulseAudio installation but did installed the pavucontrol as per your suggestion. It did not provided any help with regards to my issue unfortunately but thank you for the suggestion, I did not knew about its existence. In fact, I managed somehow to be able to record through the Line-in but now I detected another problem I wasn't aware: the Line-in can't be muted while recording, it plays through even if I check/uncheck the mute options either in pavucontrol or in the normal sound managing options from the system settings. As you can imagine, it can be a bit annoying while recording voices/instruments while having a playback track and an amp screaming by my side...

For now, I think I will resign myself for the Mic input but I am quite unhappy as my Line-in seemed to have a nice dB cut (around 6/8 dB) that was perfect for some recording e.g. guitar through Guitarix (Line-in), with voice (Mic)... Unfortunately, I am back to the old days now ](*,) 

From my experience, it is better to try again in a few days since I sometimes solve issues without even knowing how I did it! It seems stupid but it is true! I fought as a mad man to get QJack, Guitarix, Hydrogen and Ardour or Audacity to work all together with a USB mixer for a long time without any success. I left it alone and forgot about it for some weeks and when I got back on it, surprise! Managed to put everything working perfectly, QJack wasn't bugging or crashing without knowing why, Ardour and Guitarix recognized everything and I could finally have some fun with the connection settings. Even working with Reason was a real pleasure!!

Anyway, that was just an outburst; I really hope some expert could solve my issue with some magical powder, it would be a treat to my ears :guitar:


Once again, thank you very much for your help and do not hesitate to drop more useful tips, I most appreciate and I will give updates to the situation if any changes arise.

Cheers!

---

### Post by Atitudes on 2013-05-27
And after some more experiments, nothing good happened so far :(

As I've seen many queries for the [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo) output, here is mine in case it may provide some gentle help [http://www.alsa-project.org/db/?f=e9044fca643b00f74c7dc79b8936222b9e416492](http://www.alsa-project.org/db/?f=e9044fca643b00f74c7dc79b8936222b9e416492)

Thanks in advance, I'll keep posting my new findings.

Cheers!

---

### Post by stevem531 on 2013-05-28
Hi Atitudes

I have had a look at the Alsainfo output and from my understanding of the mixer controls there is a fader and mute switches for 'Line Playback Volume'. It seems that this is unmuted, and the fader turned up. If you are still hearing the sound from the Line Input continuously, I think this could be the cause.

You should be able to see the fader and mute controls in the PLAYBACK (F3) option in alsamixer, but it might need use of the left/right arrow keys to scroll them into the window.

I note that there are also similar controls listed for front and rear mic but they are muted and/or the levels turned down which would explain why the Mic input is not heard at the output, only the Line input.

Something to try anyway. Let us know how you get on. In any case it was a really good idea to post the Alsainfo as it will contain much of the info the 'Sound Gurus' might need.

Regards

Stephen

---

### Post by Atitudes on 2013-05-28
Hi stevem531! Once again, thank you very much for your kind support!

And magic has happened!!!

For my Line-in issue, I simply turned down the fader from the Alsamixer (F3 menu) as per your suggestion, and everything went back to normal it seems! Means I have no by-pass any more now from the Line-in! Thank you so so much!! (no idea why I didn't figured this out before)

But still something catches my attention as in the Alsamixer (F3 menu), the Mic-input fader is all the way up and the Line-in fader is all the way down and they are working exaclty the same. Is this a normal behaviour? 

I was expecting them to behave the same way, for example I can now plug a CD player to the Line-input (not to the Mic-input), turn up the Line-in fader (in Alsamixer F3 menu) and listen to it from my output but the same does not apply for my Mic-input (there are two faders for it, I tried them both). Sorry for my words but am I missing something stupid again?!?

Once again, thank you very much for your patience with such a "*noob*" like me, specially when the solution was quite obvious!! But I still find it strange why my two inputs (Mic and Line) aren't behaving the same way with regards to the Alsamixer configuration...

I will mark the thread as solved although I would really appreciate to continue the conversation until I solve this alleged second problem!!

Cheers!

---

### Post by stevem531 on 2013-05-28
Hi Atitudes

I am really pleased that you now seem to have the Mic and Line inputs working the way they used to !!.

The  apparent difference in behaviour between the Mic and Line Playback  Volume settings in the alsamixer F3 menu is I think because Mic has been  muted. You will probably notice 'MM' just below the volume slider. If  you want to unmute both left and right channels you just press the 'm'  (or 'M' ) key and you can toggle between muted 'MM' and unmuted '00' by  pressing 'm' (or 'M') as required. The '<' and '>' keys do the  same as the 'm' key but for left and right channels independently.

The  second Mic fader that you see (without a mute status indicator) will be  'Mic Boost' and just to confuse matterts this same control will I  expect also appear in the Capture (F4) menu !!

The final thing to  mention is that as many PCs have separate Front Mic jack and Rear Mic  jack inputs, provision has been made for these to have separate sets of  volume controls, both for Playback and Capture.

I hope that helps clarify the situation but I will of couse try to provide more details if you are still unsure.

Hopefully though you will now be able to spend a bit more time actually making music !!

Regards

Stephen

---

### Post by Atitudes on 2013-05-28
Hi stevem531!

Once again you just screwed the nail on the head!! Awesome, better than an instruction manual, I can't be more grateful to you as it's working perfectly!!

So if I understand, the second Mic fader should be all the way down then in order to keep the Mic-input "clean" from any on-board/system amplification which will help to get a "pure" sound from the Mic-input right? 
In other way, I should only use it in case I plug some "crappy" microphone to it and need some kind of boost to get some audible sound, else I will leave them alone while recording. 

Maybe the lack of this option for the Line-in is why I always preferred that input to record instead of the Mic entry although I was always preoccupied to have the sound level below the amplified one in the pavucontrol/sound system settings (and I was thinking it had some kind of dB cut...). Am I correct?

So, summarizing, both my Mic entries (Front and Rear) are provided with a boost option in the F3 menu and they also appear in the F4 menu (only for the boost option). The Line-in does not have a visual boost in Alsamixer although it looks like it is an option provided in the pavucontrol/sound options settings...Weird but ok ;) 

Without wanting to abuse your patience, I am still unsure about the F4 menu 'Capture' options, respectively 'capture' and 'capture 1'. From my "little experiences" it is controlling the volume input from any plugged entry when using a software for recording. It doesn't seem to change any speakers output but while recording, the 'capture 1' option seems to have a very small "booster" action on the 'capture' option...Could you please clarify their use?

Thanks to your instructions I think I will be using the Alsamixer a lot more from now on! Despite its "tricky" first impression, it's really a very good and wonderful tool and you made me change my mind about it!! (The '<' and '>' in the Mic-line in the F3 menu are really great and useful options!!)

You said you were not an expert but for me you've been more than a teacher! I really appreciate and thank you again for all your patience!

Cheers!

---

### Post by stevem531 on 2013-05-29
[FONT=arial][SIZE=2]Hi Atitudes

I'll try to clarify some of the issues from your previous post.

I have 12.04 on a PC with a Realtek ALC883 audio codec, similar to the ALC887 on your system, so that has been useful when trying to answer your questions.

The 'second Mic fader' or Mic Boost, one each for the Front Mic and Rear Mic, provides up to +30dB amplification in 10dB steps (0, +10, +20 & +30 dB). Mic Boost is applied to the Mic input signal before it is fed to anything else. Just as you say, these controls are only provided for the Mic Inputs, not for the Line Input.

I noticed that the PulseAudio input volume settings for the Mic inputs (either System Sound settings or pavucontrol) operate the Mic Boost and Capture Level controls together, such that at the '100%' or '0dB' point on the PulseAudio slider both the Boost and Capture levels shown in alsamixer are set to maximum. (The Line Input also has an input level slider in pavucontrol/sound settings but only adjusts the Capture Level shown in alsamixer.)

The PulseAudio level controls also seem to provide for a further +11 dB of software amplification !!

Whether it would be better instead to do as you suggest and manually set the levels to use the full range of the Capture Level control before applying the next stage of Mic Boost I am not at all sure. I think the main concern in any case, which you touched upon, is that if the Mic signal level is quite low, and it needs a lot of boost to provide an adequate signal level for recording, then system noise could be a problem.

There are two Capture Level controls shown in alsamixer (F4 settings). The ALC887 audio codec has two stereo analogue to digital converters (ADCs). Each Capture Level control (labelled Capture and Capture 1) is assigned to just one of the two ADCs. Each ADC also has an Input Source selector switch (either Line, Front Mic, Rear Mic, CD..), and an input mute control (operated in alsamixer using the spacebar).

My built-in sound card (and perhaps your's also) was originally set up for PulseAaudio use, either in Stereo Duplex configuration or maybe using one of the Surround Sound options. So just one of my Capture devices is being used at the moment, the one marked Capture.

You are correct that the Capture Level controls only affect the recording level, but I am surprised though if the Capture 1 Level control seems to be having an affect on if using PulseAudio.

Anyway, I hope that the above has been of some further help, but I suppose we should (mainly to keep the Forum Moderators happy !!) be thinking about bringing things to a close on this now solved thread...

Best Wishes

Stephen
[/SIZE][/FONT]

---

### Post by Atitudes on 2013-05-29
> **stevem531 said:**
> [FONT=arial][SIZE=2]
Anyway, I hope that the above has been of some further help, but I suppose we should (mainly to keep the Forum Moderators happy !!) be thinking about bringing things to a close on this now solved thread...

Best Wishes

Stephen
[/SIZE][/FONT]

Hi stevem531,

I could not agree more!! 

> **stevem531 said:**
> [FONT=arial][SIZE=2]H(The  Line Input also has an input level slider in pavucontrol/sound settings  but only adjusts the Capture Level shown in alsamixer.)[/SIZE][/FONT]

And THAT was the solution to my problem, you can call me dumb but it was really hard for me to get there despite all the options being in front of me, and believe-me I did tried a lot of different solutions!! And finally got though thanks to you!

> **stevem531 said:**
> [FONT=arial][SIZE=2]
There are two Capture Level controls shown in alsamixer (F4 settings).  The ALC887 audio codec has two stereo analogue to digital converters  (ADCs). Each Capture Level control (labelled Capture and Capture 1) is  assigned to just one of the two ADCs. Each ADC also has an Input Source  selector switch (either Line, Front Mic, Rear Mic, CD..), and an input  mute control (operated in alsamixer using the spacebar).[/SIZE][/FONT]

That's one of my next steps to analyse, which one does what!!

> **stevem531 said:**
> [FONT=arial][SIZE=2]
My built-in sound card (and perhaps your's also) was originally set up  for PulseAaudio use, either in Stereo Duplex configuration or maybe  using one of the Surround Sound options. So just one of my Capture  devices is being used at the moment, the one marked Capture.[/SIZE][/FONT][FONT=arial]

I don't know if it was from Alsa mixer (from the software center) or not that *messed*[/FONT] with those options. When I first started Alsamixer from a terminal after having uninstalled Alsa mixer (GUI), 'capture 1' was set at about 40dB and 'capture' around 12dB...it wasn't that great for recording and I noticed the difference the moment I installed Alsa mixer (GUI).

> **stevem531 said:**
> [FONT=arial][SIZE=2]
You are correct that the Capture Level controls only affect the  recording level, but I am surprised though if the Capture 1 Level  control seems to be having an affect on if using PulseAudio.[/SIZE][/FONT]

I can say that with an guitar muted and plugged to Line-in or Mic-in, with 'capture' at 100dB it had some residual acceptable noise. When I slide 'capture 1' up, the residual noise went up significantly (about 5dB and could be more depending on the residual noise *coming in*). I experimented this without anything plugged in and every "knob" from the Alsamixer down (inputs & boosts). Recording through Audacity with 100dB in 'capture' gives me some tiny insignificant residual sound and when I scroll up 'capture 1' it doubles (or more) and is much more noticeable. I am still a bit confused about its function...

I need some more time to assimilate all that information and make some more testing on my own and once again I say thank you very much for your inputs and all the help provided!!
I will give you a feedback through private message and really hope you don't mind!!

Thank you for pointing the need to *close* this thread as I'm really getting more and more curious!! **Thanks also to the moderators that didn't closed this thread, feel free to do so now if required!!**

[SIZE=1]Just a spoiler, I was going to ask you if it is possible to split our inputs in order to be able to record them separately. With my noobish experiences I achieved it by using Jack and 2 different software, e.g: audacity and ardour. With your inputs I am also trying to record from both Mic-inputs (Rear and Front), setting one to left and the other to right channel respectively.  Obviously I do this while recording in Stereo and then I just *extract* each side to different mono channels and* voilá!* Two mono tracks created!! But if I could easily use each input separately for recording, like an "on-board mixer" while using Jack and the same recording software it would be awesome!! (perhaps some more experiences and knowledge can make me find the solution but as you've been so helpful perhaps you have some quick answer that could save me a lot of time!! I am sure you understand. Thank you very much).
[/SIZE]

---

