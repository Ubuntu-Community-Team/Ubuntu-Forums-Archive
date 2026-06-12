---
title: "skype on ubuntu 10.04 - only pulseaudio?"
date: 2010-05-22
forum: Multimedia Software
---

### Post by pythonscript on 2010-05-22
I just installed skype 2.1 beta 2 (the deb file) from the skype website, but the* only option* I see under Sound Devices -> Recording is "PulseAudio Server (local)" This doesn't work for me, as the skype test calls don't actually record anything I say. Any help here? I use skype a lot and FINALLY got it working under karmic, but I needed to upgrade to lucid and now it's broken. 

I've been around 8400 km away from home for the last 7 years, so I can't stress enough how important skype is to me. Thank you!

EDIT:  When I open Sound preferences and look at the Applications section, Skype shows up as recording when I run its test call... but no sound is recorded? How is it possible that my sound card picks up something recording but doesn't actually record it when I'm in skype?

---

### Post by cocolocko on 2010-05-22
I have the same Skype problem, with a HP Pavilion DV4-1414la Notebook.
Does someone have some experience with Skype and the following Audio Devices:

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller

With Pulseaudio and Alsa it is not possible to record audio in Skype.
Or there are some specials i can try?
Please give us some feedback.

Thanks

---

### Post by hyperAura on 2010-05-22
mine works fine with mic set to "PulseAudio Server (local)"

---

### Post by pythonscript on 2010-05-22
I just got mine to work. I rebooted my computer and it appears to be working fine now. That seems like a Windows-esque solution to the problem, so I doubt that was the actual solution, but I don't know nearly enough about Linux to track down the actual problem and/or the actual solution, so I leave it at that.

---

### Post by cocolocko on 2010-05-22
@ hyperAura:

Can you give us some Details? What Kind of Computer/Laptop do you have, and what Soundcard do you use?
Thanks

Greetings

---

### Post by lidex on 2010-05-23
> **cocolocko said:**
> @ hyperAura:
Can you give us some Details? What Kind of Computer/Laptop do you have, and what Soundcard do you use?
Thanks
Greetings
What exactly is your problem? Does everything work other than recording in skype? How about sound-recorder?

---

### Post by 42dorian on 2010-05-23
the solution I found to PulseAudio and Skype is from this website:

[http://blogs.skype.com/linux/2009/09/some_explanations.html]("http://blogs.skype.com/linux/2009/09/some_explanations.html")

When I went to ~/.pulse and created the file client.conf, opening it and adding the line "autospawn =no" (Without quotes of course), the next time I ran the program, any audio program really, I suddenly had access to all of the inputs and outputs of both my sound cards.

This means, when you go into Skype or wherever you need to define what input you want to use, you can select the exact mic and headphone jacks you're using, rather than the ones that PulseAudio detected and assumed you wanted.

I hope this helps everyone.

---

### Post by tech_girl on 2010-05-24
Or you may want to try by simply going to Preferences > Sound > Sound Effects, and uncheck "mute".

---

### Post by ka9qlq on 2010-09-06
> **tech_girl said:**
> Or you may want to try by simply going to Preferences > Sound > Sound Effects, and uncheck "mute".

In what???????

---

### Post by ashwinipn on 2010-10-06
> **42dorian said:**
> the solution I found to PulseAudio and Skype is from this website:

[http://blogs.skype.com/linux/2009/09/some_explanations.html]("http://blogs.skype.com/linux/2009/09/some_explanations.html")

When I went to ~/.pulse and created the file client.conf, opening it and adding the line "autospawn =no" (Without quotes of course), the next time I ran the program, any audio program really, I suddenly had access to all of the inputs and outputs of both my sound cards.

This means, when you go into Skype or wherever you need to define what input you want to use, you can select the exact mic and headphone jacks you're using, rather than the ones that PulseAudio detected and assumed you wanted.

I hope this helps everyone.

Hi,
I tried as suggested and disabled autospawn. Now, although Skype is able to display other audio devices as well, my pulseaudio is not working for the rest of the system. When I try opening System > Preferences > Sound, I get a notification saying "Waiting for sound system to respond".
Any take on this?

Regards,

Ashwini

---

### Post by lidex on 2010-10-06
> **ashwinipn said:**
> Hi,
I tried as suggested and disabled autospawn. Now, although Skype is able to display other audio devices as well, my pulseaudio is not working for the rest of the system. When I try opening System > Preferences > Sound, I get a notification saying "Waiting for sound system to respond".
Any take on this?

Regards,

Ashwini

You may need to restart pulseaudio. Try this command:
```
pulseaudio -D
```

---

### Post by ashwinipn on 2010-10-08
> **lidex said:**
> You may need to restart pulseaudio. Try this command:
```
pulseaudio -D
```

Thanks so much... It worked.... However, the purpose I "autospawn = no" it so that it enables me choose the device. Now I can't choose the device in Skype... since pulse audio has again taken over... In fact, both the options have their demerits.... With pulse audio, my voice services like Skype and Google mail chat do not work properly whereas when I disable pulse to choose other devices such as ALSA, it does not work simultaneously with different applications... For example, when I have played flash in Firefox, it would make sound problematic in VLC etc..... Pulse audio is a very good server... and able to take care of many different application playing simultaneously. But it needs improvement in routing so that different audio streams can play without any glitch, interference, delays, and screeches... At the same time, applications such as Skype and Google talk plugin should also be improved to support pulse audio. About Skype, there is no pulse audo support as well as 64 bit support, as suggested [here]("http://blogs.skype.com/linux/2009/09/some_explanations.html").

Ashwini

---

### Post by porlaizquierda on 2010-10-15
i tried everything that i found in forums and still could not get the mic to work. i ended up having to download an older version of skype. skype.com does not have it and i couldn't get to it on archive.org, but i found 2.0 on this blogger website. the mic works just fine now, even though i had to revert to an older version, but then skype for linux is terrible anyway.

[http://skype-old-version.blogspot.com/2010/03/skype-old-version.html](http://skype-old-version.blogspot.com/2010/03/skype-old-version.html)

---

### Post by ZekeGraal on 2010-11-16
[LEFT]Here is the solution I found that is quite easy to get my mic working:

1. Click on the speaker in the top bar, and choose sound preferences
2. Go to output and slide the balance all the way to the left or right
3. Open Applications>Sound & Video>PulseAudio Volume Control (if you dont have it, download it from the software center), and click the recording tab
4. Go to the settings on skype, and choose audio in the bar on the left.
5. Hit 'Test Call' and bring the PulseAudio Volume Control to the front, now while the nice lady with the accent is talking, it should show Skype and what hardware its using to record. Click the box, and choose your mic input instead of the monitor one.

It works! (yes you hear out of one speaker, oh well!) from now on it should work normally.
I had been looking for probably 2 months, and I found it.
(Skype for linux really needs to be updated, am I right?):lolflag:
[/LEFT]

---

### Post by ka9qlq on 2010-11-16
I just went back to ALSA and wish I stayed with 8.04
Yes Skype but we are the read headed step-child of software

---

### Post by ruslanasa on 2011-07-18
> **ZekeGraal said:**
> [LEFT]Here is the solution I found that is quite easy to get my mic working:

1. Click on the speaker in the top bar, and choose sound preferences
2. Go to output and slide the balance all the way to the left or right
3. Open Applications>Sound & Video>PulseAudio Volume Control (if you dont have it, download it from the software center), and click the recording tab
4. Go to the settings on skype, and choose audio in the bar on the left.
5. Hit 'Test Call' and bring the PulseAudio Volume Control to the front, now while the nice lady with the accent is talking, it should show Skype and what hardware its using to record. Click the box, and choose your mic input instead of the monitor one.

It works! (yes you hear out of one speaker, oh well!) from now on it should work normally.
I had been looking for probably 2 months, and I found it.
(Skype for linux really needs to be updated, am I right?):lolflag:
[/LEFT]


Thanks!!! 

This was the last step to success for me on Ubuntu Natty (11.04), had lots of struggle until Alsa mixer was setup correctly and microphone started to work for my Audigy2 under Ubuntu 11.04 desktop env. 

Also, I want to note, that you do not really need step [2], you should have setup for mono input, the essence here is that pulse audio volume control allows to review and update from where application gets capture stream. One post in forums was indicating that when capture is set to stereo you need to mute left or right channel, because otherwise both channels cancel each other out - don't really know if this is true, in any case better not to use stereo input when you have mono mic :). 

Use the same steps (except 2) for Voice Recorder, now it works too. :)

Cool! :popcorn:

---

### Post by SeijiSensei on 2011-07-20
> **ruslanasa said:**
> One post in forums was indicating that when capture is set to stereo you need to mute left or right channel, because otherwise both channels cancel each other out - don't really know if this is true, in any case better not to use stereo input when you have mono mic :).

Yes, that's how I got Skype to work on my daughter's ASUS 1201n.  I installed pavucontrol, then unlocked the microphone sliders, and turned one down to 0% and the other up to 100%.  That seemed to fix the problem.  I'm using PulseAudio.

---

