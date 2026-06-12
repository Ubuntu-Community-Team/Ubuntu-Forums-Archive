---
title: "sampler questions"
date: 2006-04-02
forum: Multimedia &amp; Video
---

### Post by cleentrax on 2006-04-02
I hope to record my next album with Dapper. It's running great on my laptop, but to this point I haven't installed it in my studio, which has two Windows PCs -- one running Gigastudio, and one running SONAR 5. A few questions:  

1. I see many attempts have been made to use VST in Linux. Is this mature yet? Or are there mature OSS equivalents to synths like Native Instruments' B4 and Absynth, or effects like Waves' dither, reverb and multiband compressors?
2. LinuxSampler/QSampler seems to be the only Linux equivalent to Gigastudio, but it seemsto be in alpha. Is it usable yet? Does it sync with and run on the same machine with something like Ardour or Rosegarden?
3. I work with lots of MIDI and audio loops. Does Ardour or Rosegarden support this? (as you would find in SONAR or Acid).
4. Has anyone attempted Linux drivers for the Frontier Design Dakota and WaveCenter PCI?

Thanks for any input!

---

### Post by dolson on 2006-04-04
[QUOTE=cleentrax]I hope to record my next album with Dapper. It's running great on my laptop, but to this point I haven't installed it in my studio, which has two Windows PCs -- one running Gigastudio, and one running SONAR 5. A few questions:  

1. I see many attempts have been made to use VST in Linux. Is this mature yet? Or are there mature OSS equivalents to synths like Native Instruments' B4 and Absynth, or effects like Waves' dither, reverb and multiband compressors?
2. LinuxSampler/QSampler seems to be the only Linux equivalent to Gigastudio, but it seemsto be in alpha. Is it usable yet? Does it sync with and run on the same machine with something like Ardour or Rosegarden?
3. I work with lots of MIDI and audio loops. Does Ardour or Rosegarden support this? (as you would find in SONAR or Acid).
4. Has anyone attempted Linux drivers for the Frontier Design Dakota and WaveCenter PCI?

Thanks for any input![/QUOTE]

1. VST is equalled in Linux by LADSPA and DSSI. The fact is that there aren't as many developers of Linux-based plugins, and certainly no one is being paid to do it. VSTis are also equalled by DSSI, but there are not many of those instruments yet either. You can always try running your VSTs or VSTis in Linux using dssi-vst or fst or whathaveyou, but they will only run as well as Wine works (IMHO, not well). If your music relies heavily on Windows-only software, and you cannot find any alternatives, perhaps Windows is your better option at this time. Or pay someone to develop the equivalent of what you require for Linux.

2. I have no idea what Gigastudio is or how it works. LinuxSampler/Qsampler is usable. A majority of Linux software is "alpha" including Wine, but that didn't stop several companies from [at least attempting to] making money off of it (Corel, Transgaming, Codeweavers, etc). There are other samplers, but maybe not ones that are as complete, stable, featureful, etc. Specimen was good, but it isn't going to be developed any longer. There are also more ambitious apps that try to take on the whole world, like Wired and LMMS. I think Wired can load Akai sample banks. Another option is to make your own SoundFonts with Swami and load them into FluidSynth/Qsynth.

3. I don't run Windows, so I don't run Windows apps. I've got no idea about MIDI and audio loops as it pertains to your listed Windows apps. But Ardour definitely has no MIDI support currently, although it is planned for the future. Rosegarden does not look to me like it is a loop-based sequencer, but it can repeat stuff. You record it, cut it how you want, and then set the number of repeats.. Probably Seq24 is closer to what you are looking for, if you want a loop-based MIDI sequencer. For audio loops, I have no idea what you need... You could load a loop into Ardour and have it repeat, maybe only by copy-paste, I don't know. But I am not sure it's what you're looking for. If you can describe what those Windows apps do, exactly, I might be able to help you more.

4. No idea. Did you check the ALSA project website? It lists pretty much every supported device there. And if this is something you do not yet own and want to run on Linux, I would recommend you read up on what is recommended for use under Linux prior to purchasing.

Hope that helps in some small way, even if only to point out that Linux might not fill your needs.

---

### Post by philipacamaniac on 2006-04-04
I don't think pro audio in Linux is at the level you need. Sorta like the much-needed CMYK support in Linux graphics applications.

1. Linux audio apps have their own plugin architecture (LADSPA), and I haven't seen an app yet that can run VSTs. LADSPA and DSSi are nowhere near the professional caliber and quality of commercial VSTs.

2. I've been searching for over a year now for a synth/sampler/sequencer to replace my Reason. Nothing so far, except on disconnected low levels. LinuxSampler can run audio samples, Hydrogen is a great drum sampler, Seq24 is MIDI samples. But again, nowhere near the caliber and quality of Reason, Live, Sonar, Cubase, etc.

3. Loops. Same deal, mostly. And worst of all, I can't find an equivalent to ReWire so that all these various Linux audio apps can work together as a synched workstation.

Ardour is great at multi-tracking (and hopefully Wired will be too); Rosegarden is great at MIDI sequencing. But if you're looking to do serious studio recording work, don't bet money (or waste time) in Linux. Eventually I think I'll be able to wane myself off of my Windows dual-boot partition, but that will only be when I can afford a dedicated Mac for my studio work.

---

### Post by dolson on 2006-04-04
I'm pretty sure Ardour can use VSTs if you compile it with VST support. But don't expect this sort of thing to ever make it into a Linux distro without Steinberg changing their license terms.

Rosegarden, with DSSI support enabled, can use dssi-vst as well.

LMMS also has VST[i] support, when you compile it in.

I don't know what ReWire is, but uh, everything works together with JACK..

And I wouldn't go so far as to say that you can't do serious recording work with Linux. Quite the contrary. However it's a different way of thinking, and different tools.

A good engineer can do miracles with the crappiest of tools. If someone has to hide behind some proprietary-only feature, then perhaps they're just not that good?

---

### Post by cleentrax on 2006-04-04
> A good engineer can do miracles with the crappiest of tools. If someone has to hide behind some proprietary-only feature, then perhaps they're just not that good?

Well, that's not very friendly. While I am interested in using all types of tools, I no longer find it necessary to "prove" myself as legit by using crappy tools. 

Of course, I will consider Linux compatibility when I purchase future audio hardware, but when I purchased my Frontier Design hardware seven years ago, Linux audio was not really an option.

It sounds like Linux audio apps are not ready to take center stage in my studio. I will perhaps experiment with some of them on a dual boot in my spare time. 

Loop-based editing allows you to create measure-length audio snippets that sync and follow changes to key and tempo -- a crucial tool for remixing and sound design. 

Gigastudio is a streaming sampler that allows you to load huge sound banks because only the header of the sample is loaded into RAM -- the rest of the sample is streamed from the disk. This is necessary for creating complex orchestrations.

---

### Post by dolson on 2006-04-04
I didn't say that Linux only has crappy tools to offer. On the contrary, I think it is rapidly approaching what it is you require.

Even if SONAR or Pro-Tools or Fruity Loops were available for Linux, I don't think I would use them because I don't have the money for this stuff. When it comes down to it, I think that JACK and the assortment of compatible applications are a good enough replacement.

Sorta how I wouldn't bother buying Photoshop, because Gimp is all I need and more, and only gets better with each release. CMYK is missing to a large degree, but with a lot of printing shops accepting Microsoft Word .doc files now, I don't think it's that big of an issue.

Sorta how Blender is my 3D modeller/renderer of choice now, and even if 3DSMax was ported, I wouldn't buy it, and Maya is here already but too expensive. Blender's main problem was always the UI, which didn't bother me, but it has come leaps and bounds since going open source.

If Microsoft Office came to Linux, I wouldn't buy it either. OpenOffice.org does lack some features that even I used once upon a time, but that doesn't mean I would turn my back the minute Microsoft tries to get every last penny out of every PC user.

So too, I will continue to use JACK and friends, no matter what apps come to Linux, until such a time as these apps are obsolete, unsupported, and undeveloped - if that ever happens.

This isn't to say that EVERY person out there could do as I do, and that's fine. Traditionally, Linux users have had to lose out on some features, and music apps are no different.

In time, I hope this is remedied, at which point we can welcome everyone with open arms. But this won't happen until a lot of time goes on, and improvements are made slowly, or someone with a lot of cash puts some into the hands of those who can make things happen.

I can't afford all the groceries I need this month, nevermind bounties for features. But if I ever get a really good job and have some extra cash, for sure I will try and get something improved with monetary assistance. Lord knows I can't code worth a damn! Heh.

Anyhow, I hope you do try out what Linux has to offer. If you are using Breezy still, then you might wanna wait for Dapper. Check it out, and see what can and cannot be done for yourself, because I am not as familiar with this stuff and the Windows side of things as you are. If you make some notes of missing features of apps, feel free to submit them to the software authors. I know that Rob who develops Seq24 is friendly to feature requests, and he will implement them based on demand and as time permits.

Also, part of my goal with Ubuntu Studio was, had I received any donations, was to implement a feature-request system, where we can vote on features for apps and put part of the donations towards those features. But the details have not yet been worked out, and there is no rush to get it done, as no donations have come in yet anyhow.

Seven years ago, I was using Linux on floppy disks, heh. :D It wasn't ready for me to even use as a main desktop at that time, so I hear ya.

I never used loop-based stuff yet, other than MIDI, so I definitely can't answer your question about that.

I don't know about RAM usage for any Linux-based samplers.

Sorry that I ramble a lot. I'm lonely. :\

---

### Post by udanton67 on 2006-04-18
I'm trying out LMMS, and it looks pretty good for looping, etc. Comments?

---

### Post by GameGod on 2006-04-21
Is it wrong that I use [Buzz]("http://buzzwiki.wipe-records.org/index.php/Main_Page") in Linux, and it does everything I need pretty much?
It basically runs flawlessly... (It's a Windows app, but runs perfectly in WINE.)

Also, Buzz can load VST instruments and effects, and I've pretty much had excellent compatibility with that... (Which leads me to believe that VSTs work well with any version of WINE within the last year...)

---

### Post by dolson on 2006-04-21
I never used Buzz, but it looks a bit like:
[IMG]http://www.buzztard.org/images/c/cb/Bt-edit-0.0.1-03.png[/IMG]

---

