---
title: "Using Two Sound Cards"
date: 2009-07-06
forum: Multimedia Software
---

### Post by meschaefer on 2009-07-06
I would like to be able to use two sound cards simultaneously. (actually want to use one soundcard and onboard audio) Is there a way in .asoundrc to force Ubuntu to do this?

---

### Post by kostkon on 2009-07-06
What version of Ubuntu do you have?

---

### Post by fh_scott on 2009-07-06
in principal, Ubuntu can use multiple sound cards.

I currently have the onboard audio + a USB sound adapter that I use for Skype.

Sometimes the system gets a little confused where it's supposed to send sounds.  About half the time the startup sound comes out of my Skype headset and the other half it comes out the main speakers.

I didn't really have to mess with .asoundrc, just the PulseAudio manager.

I'm running 9.04 btw...

-scott

---

### Post by meschaefer on 2009-07-06
At the moment, this system is sitting in parts on my workbench.  I intend to install Jaunty Jackalope, and the system will be used as an HTPC with XBMC. (I have been using Hardy Heron on my desk top, where I have been testing media software)
 
The motherboard is a [GIGABYTE GA-E7AUM-DS2H LGA 775 ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128363&Tpk=GIGABYTE%20GA-E7AUM-DS2H"), and this will handle digtial audio out for 5.1 
 
The Audio Card will most likely be [M-AUDIO Audiophile 2496 ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16829121120")to handle analog audio out (I havn't purchased this yet, because it will be a waste if this doesn't work, actually the whole system is a waste if this doesn't work)
 
If I can't do this through ALSA and .asoundrc, it looks like I should be able to send sound out to an audio server such as [JACK]("http://alsa.opensrc.org/index.php/Jack_%28plugin%29"), and have jack then send the audio to the two cards.  My receiver will decide wich stream to use.  The only thing that concerns me with this, is audio sycing in movies.
 
Thanks for any help.

---

### Post by meschaefer on 2009-07-06
> **fh_scott said:**
> in principal, Ubuntu can use multiple sound cards.
 
I currently have the onboard audio + a USB sound adapter that I use for Skype.
 
Sometimes the system gets a little confused where it's supposed to send sounds. About half the time the startup sound comes out of my Skype headset and the other half it comes out the main speakers.
 
I didn't really have to mess with .asoundrc, just the PulseAudio manager.
 
I'm running 9.04 btw...
 
-scott
 
 
From my research using two cards does not seem to be a problem, but using them simultaneously seems to be a little trickier. I am trying to avoid having to have choose between one or the other and have both of them working at all times. i.e. system sound should come out of both devices. 
 
Everything I have read so far, leads me to beleive that I will need to remove PulseAudio.

---

### Post by markbuntu on 2009-07-06
No, you do not need to remove pulseaudio. In fact it is the easiest way to control multiple sound hardware. I have 4 hardware sound devices on my machine and they all work simultaneously with pulseaudio.

You can set up alsa and jack to use multiple hardware devices but you will need to build the libasound2 library from source since ubuntu has stipped out the libraries necessary to play alsa and oss apps through jack though they left in the libs for jack to play through alsa so there is some confusion over this. You will also need to make some devices in asoundconf to use multiple hardware devices with jack or use netjack, which if you want to do you will need to build jack from source since ubuntu has left that out too.

If you just want audio out, the 2496 is sort of overkill for that but will work OOB.

The Pulseaudio version used in Jaunty (0.9.14) was not recomended for distribution by the pulse developers so it is somewhat broken and ALSA is also pretty kludged in Jaunty. 

You would be better off with pulseaudio 0.9.15 and alsa 1.0.20 and a 2.6.29 kernel and jack 1.9.2 and ardour2.8. or maybe just waiting for Karmic Koala in October.

---

### Post by malrost on 2009-07-07
I am currently using my gigabyte mobo's onboard sound (snd-intel-hda) for movies/music/media/games and a Hammerfall HDSP sound card for low-latency recording. I think you're right that you can accomplish what you need w/out pulseaudio.

I strongly disagree that pulseaudio is the easiest way to handle multiple sound hardware. It works well enough w/ my onboard sound but is *useless* for the HDSP card (not to mention the latency hit it would add).

Currently I use ALSA & jack for low-latency recording and monitoring with the HDSP, and pulseaudio for the onboard card. I did not have to build libasound2 from source to get ALSA to work, either (I'm running jaunty amd64).

If you just want to be able to send one or two streams to one or two sound cards I think ALSA & jack will both work and make sense. Installing the ubuntustudio-audio and ubuntustudio-audio-plugins packages should give you everything you'll need.

---

### Post by tariely on 2009-07-07
I have Audidgy2 old card and it's work perfect :)
















[&#1079;&#1077;&#1083;&#1105;&#1085;&#1099;&#1081; &#1083;&#1072;&#1079;&#1077;&#1088; &#1076;&#1083;&#1103; &#1087;&#1086;&#1076;&#1072;&#1088;&#1082;&#1072;](http://www.shocksale.ru/shop/laser/)

---

### Post by markbuntu on 2009-07-07
> **malrost said:**
> I am currently using my gigabyte mobo's onboard sound (snd-intel-hda) for movies/music/media/games and a Hammerfall HDSP sound card for low-latency recording. I think you're right that you can accomplish what you need w/out pulseaudio.

I strongly disagree that pulseaudio is the easiest way to handle multiple sound hardware. It works well enough w/ my onboard sound but is *useless* for the HDSP card (not to mention the latency hit it would add).

Currently I use ALSA & jack for low-latency recording and monitoring with the HDSP, and pulseaudio for the onboard card. I did not have to build libasound2 from source to get ALSA to work, either (I'm running jaunty amd64).

If you just want to be able to send one or two streams to one or two sound cards I think ALSA & jack will both work and make sense. Installing the ubuntustudio-audio and ubuntustudio-audio-plugins packages should give you everything you'll need.

As I said, there is some confusion over this alsa jack thing. Try playing a native ALSA application through jack, you cannot unless it has a jack plugin.

In a recording environment you would not use pulseaudio anyway. In fact the pulse devs recomend against it. Anyway, you are not trying to use your cards simultaneously which is what the OP asked.

There is another significant problem with using multiple cards together, their clocks drift apart and can cause significant discrepancies in timing. Unless you are using pairs of high end sound production cards like Hammerfall or M-Audio cards designed for clock sharing you will have this problem with jack and alsa since they have no way to synchronize the clocks other than physically wiring the clock circuits together.

The reason I use pulseaudio with my multiple sound hardware devices is because pulseaudio is the only way to keep them in sync. It works fine for playback which is what I use it for.

For live recording etc I use jack and one card only. I can also feed jack with any app playing in pulseaudio through the pulse-jack module which, btw, is also not included in ubuntu and must be built from the source code. I can also use one card for jack and another for pulseaudio and run them both at the same time without any problems. I have been doing these things for a long time in Hardy but with Jaunty there are some problems between the kernel and the pulseaudio version causing it to not work so well so, while I have Jaunty installed, I still use Hardy as my main OS.

I will probably wait for jack2.0 before moving my production away from hardy.

---

### Post by malrost on 2009-07-07
> **markbuntu said:**
> As I said, there is some confusion over this alsa jack thing. Try playing a native ALSA application through jack, you cannot unless it has a jack plugin. . . .

Anyway, you are not trying to use your cards simultaneously which is what the OP asked.

The reason I use pulseaudio with my multiple sound hardware devices is because pulseaudio is the only way to keep them in sync. It works fine for playback which is what I use it for.

For live recording etc I use jack and one card only. I can also feed jack with any app playing in pulseaudio through the pulse-jack module which, btw, is also not included in ubuntu and must be built from the source code. I can also use one card for jack and another for pulseaudio and run them both at the same time without any problems. I have been doing these things for a long time in Hardy but with Jaunty there are some problems between the kernel and the pulseaudio version causing it to not work so well so, while I have Jaunty installed, I still use Hardy as my main OS.

I will probably wait for jack2.0 before moving my production away from hardy.

Would you mind attaching a screenshot of the pulse-jack module in action, and/or it's config window? I had no idea.

I'm more musician than hacker so some of your critique is lost on me.  What is an example of a native ALSA app that won't run in jack? There are distinctions between native ALSA apps, apps with a jack plugin, alsa/oss apps etc.?

Since pulse was included in Hardy, everything I have so far been able to accomplish with pulseaudio I had been able to accomplish previously w/ ALSA, including networked audio via remote access.

Admittedly I have a difficult time conceptually w/ pulseaudio. I *enjoy* audio functionality apps and I've tried to understand the pulse approach, but have yet to find any worth to my efforts, particularly when the jack model seems so logical. In jack, anything that has an audio in/out can be connected w/ anything else that does. Also you have ready access to tweak settings for all available hardware.

Perhaps that's my main problem w/ pulseaudio: it does not seem to recognize my HDSP card, while jack recognizes both. Maybe you'd have some insight as to why: attached are screenshot comparisons of pulse and jack. You can see that my HDSP card in inaccessible via pulseaudio, whereas both appear in jack connections (the HDSP HW:1,0 and the onboard NVidia is HW:0).

While I hadn't yet needed to try using both cards simultaneously, I've since tested my dual card setup for concurrent use. The two card outs go to different amp/speaker hardware, for obvious reasons. Jack/ALSA for recording/monitoring works simultaneously with pulseaudio entertainment playback. While both recording and monitoring through the HDSP w/ jack & ardour, I am able to get sound from Amarok, Flash (Daily Show on Firefox), and I stopped at four additional audible instances of VLC.

---

### Post by markbuntu on 2009-07-08
There are directions for using pulse-jack and a lot of other stuff here 

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

The pulse-jack info is near the bottom of the OP in the Ubuntu Studio section.

If jack is running and using the HDSP then it is unavailable to pulseaudio and so will not show up. It should show up if jack is closed and some other app has not already grabbed it while pulse was sleeping

If you are happy with your setup I can not really recomend you changing it and pulse in Jaunty is not really working as it should so I have not fooled around too much with the pulse-jack stuff there but others have and it seems to work well for them.

But, if you want to add a little functionality like applications playing through pulse being available to connect through jack then the pulse-jack modules are pretty easy to get working as you will see in the link above. What it does is creat a jack-sink and jack-source in pulseaudio and create pulse input and output clients in jack. The jack and pulse devs have been talking with each other lately so hopefully we can get some more from this in future versions. There are a few things you need to be careful with but they are explained.

Sometimes I use the pulse-jack sink to add effects to streams playing in Amarok, or record you tube with ardour, or play along, things like that and to get record-my-desktop working. It can all be done on the fly without having to restart jack or any of the apps to change devices so it is very handy in that regard. The alsa/pulse apps stay in pulseaudio and the jack apps stay with jack and the pulse-jack sink lets you connect them without losing anything from either one.

Pulseaudio is going through some big changes lately. Pulse0.9.15 has a much better volume control with a lot of added functionality and they expect to add even more with future versions along with playing better with jack. They have not jumped to version 1.0 so I suspect the devs feel pulseaudio is still somewhat incomplete.

But, things are looking up soundwise, FFADO is working better, Jack2.0 is very close. When jack gets back into the /main repo a lot of these issues will go away.

A little history so maybe you can understand why all of a sudden so many distros moved to pulseaudio and why everything has become so confusing. The alsa drivers have been moved into the kernel. Due to kernel security concerns this move brought about a big change in the way the alsa drivers should be communicated with. It is no longer acceptable for applications to be able to directly manipulate the drivers since they are in user space and the drivers are now in the kernel. Since the ALSA sound server (not the drivers) architecture (esound, demix, et al) was such a mess and so many changes were needed to conform to this new paradigm, it was easier to just abandon it and institute a new sound server that would sit between the drivers and the applications and prevent user applications from intruding on the kernel space. Pulseaudio, unready as it was, was about the only thing that fit the bill and so was adopted by ubuntu and fedora and suse and mandriva etc. 

Meanwhile, KDE, as they are wont to do, started developing their own new sound server, Phonon, which has replaced aRTS in KDE4 and is very similar to pulseaudio but is still very much a work in progress. 

And OSS has jumped back in the game but nobody is taking that too seriously since their previous abandonment of the Open Source community generated a lot of resentment and mistrust. (The devs took OSS private and started charging for it.)

Meanwhile jack stands apart from all of this and continues on its dedicated but limited mission. To provide a low latency controller for professional quality sound production. Jack will never be a sound server but the jack devs are working to get jack better integrated into the sound server scheme without compromising the mission.

Soo, the linux sound scheme is in what can be charitably called a brief period of flux. Hopefully it will all settle out in another year or 2 and these new sound servers will have their act together. Meanwhile you can still fall back to the old ALSA server stuff but I think much of the server side API will become deprecated over the next few years due to security concerns.

That was probably way more than anyone needs to know.

---

### Post by malrost on 2009-07-09
Thanks for the help on the pulse-jack modules. (BTW, I've often referred to your 10,000 page audio guide thread for a while now; the info is helpful and appreciated.) Looks like using the pulse-jack modules requires updating to jack2 AND updating pulseaudio, and neither of those updates are yet packaged for Ubuntu.

I'm torn between my currently functional setup and my curiosity, particularly by jack2's ability to better use a multicore cpu. Does that translate to even lower latency? The jackdmp paper ([http://lac.zkm.de/2005/proceedings.shtml#letz_et_al]("http://lac.zkm.de/2005/proceedings.shtml#letz_et_al")) indicates that the jackdmp model actually adds one buffer more latency (Page 3, section 3.4.2), which if I understand correctly, unfortunately means slightly higher latency.

---

### Post by wayward4now on 2009-07-19
As long as you are not running Karmic, just use synaptic to find "asoundconf-gtk" and that will install a teeny tiny little application that puts up a simple little graphical box that allows you to switch audio sources. Karmic broke mine as it has no /usr/bin/asoundcon file any more. BUT when it was working with Hardy and Intrepid, it presented either my main sound card or my USB headset. SWEET!! Worked like a charm. If I wanted to change volume or turn on the headset boom mike, then 'alsamixer' would do the job. Magic! Best little handy application in the whole distro. I kept it's icon parked in my bar for quick switching. Now, I cannot use it with Jaunty :( That sux. X[ Ric

---

### Post by markbuntu on 2009-07-19
> **malrost said:**
> Thanks for the help on the pulse-jack modules. (BTW, I've often referred to your 10,000 page audio guide thread for a while now; the info is helpful and appreciated.) Looks like using the pulse-jack modules requires updating to jack2 AND updating pulseaudio, and neither of those updates are yet packaged for Ubuntu.

I'm torn between my currently functional setup and my curiosity, particularly by jack2's ability to better use a multicore cpu. Does that translate to even lower latency? The jackdmp paper ([http://lac.zkm.de/2005/proceedings.shtml#letz_et_al]("http://lac.zkm.de/2005/proceedings.shtml#letz_et_al")) indicates that the jackdmp model actually adds one buffer more latency (Page 3, section 3.4.2), which if I understand correctly, unfortunately means slightly higher latency.

If you really are still using 7.10 as your sig suggests then you should just wait for the next release, karmic koala in October. jack2 will be in there and ardour3 etc, etc, along with the 2.6.30 kernel which, from what I understand has incorporated the rt patch so will be rt capable OOB. 

One more buffer vs multicore, I am not sure that latency will actually increase in any significant manner since before that jack was using a slice of one cpu and can now use slices from multiple cpus. Unless this buffer for multi cpus is quite large, which I doubt, there will be no increased latency.

---

### Post by Stochastic on 2009-09-01
> **markbuntu said:**
> If you really are still using 7.10 as your sig suggests then you should just wait for the next release, karmic koala in October. jack2 will be in there and ardour3 etc, etc, along with the 2.6.30 kernel which, from what I understand has incorporated the rt patch so will be rt capable OOB.

I just stumbled on this thread, I know it's old, but I have to scratch my head.  Karmic won't have any of those features.

We're past feature freeze so here is the official package versions for Karmic:
Jackd is 0.116.1
Ardour is 2.8.2 (Ardour3 hasn't even been released yet)
Kernel is 2.6.31 (there is a SEPARATE 2.6.31-rt because the Realtime patch is still a patch and is not incorporated in the mainline kernel yet)

It'd be nice to have jack2 packaged soon, and people are working toward that; but promising it for any version until it is packaged is just silly.

---

### Post by Eliasvan on 2012-09-22
Hi,

I recently made a tool called 'p2jaudio' (screenshots: [http://code.google.com/p/p2jaudio/wiki/ScreenshotsAndVideos](http://code.google.com/p/p2jaudio/wiki/ScreenshotsAndVideos)).
I think this tool does the opposite of what you are trying to do.
If Skype audio is sent via PulseAudio JACK Sink, and if I manage to create the opposite of 'p2jaudio' (something like 'j2paudio'), you could connect 'PulseAudio JACK Sink' with the resulting 'Headset' input jack, and connect audio from non-'PulseAudio JACK Sink' ports to a resulting 'Speakers' input jack.

But optimal would be that you could configure in Pavucontrol the following: the audio coming from 'Skype' to go only through the headsets and the audio coming from all the other applications to go through the speakers.
But I don't know this is possible.

---

### Post by howefield on 2012-09-22
Old thread closed.

---

