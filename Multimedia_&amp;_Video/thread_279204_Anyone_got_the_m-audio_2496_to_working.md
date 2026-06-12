---
title: "Anyone got the m-audio 2496 to working?"
date: 2006-10-17
forum: Multimedia &amp; Video
---

### Post by idn on 2006-10-17
I am trying to get the maudio to work my system but have had no success so far, I cant even get sound out of it.

I am using Edgy - has anyone else got it to work out the box on any other distros or got it working somehow. Please :)

The card is actually detected:

idn@idn-server:~$ cat /proc/asound/cards 
 0 [ICH7           ]: ICH4 - Intel ICH7
                      Intel ICH7 with ALC655 at 0xfdffe000, irq 225
 1 [M2496          ]: ICE1712 - M Audio Audiophile 24/96
                      M Audio Audiophile 24/96 at 0xdf00, irq 169

But I am not sure how to set the default sound card under linux. 

Thanks!

---

### Post by blackcoatman on 2006-10-18
I have the 2496 and I got it working... and not working :P Basically, it was automatically recognised by Edgy, so I only had to choose it from the mixer devices list in the mixer to control it (though the mixer can end up a bit chaotic and buggy when adding all the available controls there) and, generally, I had to choose the card seperately in each software (xmms, audacity, ardour...)... At some point I installed the open-sound drivers ([www.opensound.com](www.opensound.com)) which are pointed by the m-audio website, but I was having trouble loging-in (?!), so I removed them and finally installed the latest ALSA drivers from [www.alsa-project.org](www.alsa-project.org) - Now it works almost as good as before (i can record and listen to sounds), except I have to use the "Jack" plugin in xmms instead of oss and alsa which give me an error and i can't test anything in the sound configuration dialog. What is stupidly disturbing though is that you can't monitor your input AND have audio-playback at the same time like in Windows. At least I, have to change the output from HW 0 and HW 1 to PCM out and vice versa. This card could use some more proper drivers :/

---

### Post by NyquistLimit on 2006-10-22
I also have the 2496 and after upgrading to Edgy from Dapper I've been having some sound problems. None of the sound tests in Sound Preferences seem to work. I get the following error whenever i try a test:

```
audiotestsrc wave=sine freq=512 !
audioconvert ! audioresample ! gconfaudiosink:
Could not open resource for writing.
```

I've managed to get some limited sound output by choosing oss in mplayer. Also, I get sound from the flash 9 plugin and amarok works too but only one at a time. If I try to watch something from youtube and play music at the same time amarok will popup an error.

I've also tried the installation instructions [here]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Midiman%2FMAudio&card=Delta+Audiophile+2496.&chip=ICE1712+(Envy24)&module=ice1712") but it didnt seem to make any difference. Most likely my limited linux skills failed to make much (if any) use of it :(

---

### Post by theslut on 2006-10-22
Edgy isn't working properly with my 24/96 either. And my USB Audio device will playback but not record. I don't seem to be able to use ALSA at all and OSS is working sometimes.

I really hope they fix this before the final release because the RC was not up to scratch for me and sound is an important department.

It's a great shame because the new sound control panel was looking great, being able to assign devices to different sound tasks.

---

### Post by arundo on 2006-10-25
Hi, 

I just dist-upgraded to Edgy and my M2496 didn't work either - same error as quoted above.

When I was about to compile the drivers from CVS, I noticed asoundconf which correctly listet the card. To my suprise **asoundconf set-default-card M2496** did the trick! Everything is working again, just as it did under Dapper.

Hope this is helpful to you!



cheers from Germany.

---

