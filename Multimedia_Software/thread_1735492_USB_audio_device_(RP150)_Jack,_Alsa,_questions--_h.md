---
title: "USB audio device (RP150) Jack, Alsa, questions-- help!"
date: 2011-04-21
forum: Multimedia Software
---

### Post by sdkenned on 2011-04-21
Hi,  I am very new to ubuntu and linux and have problems with jack... I have had only minimal success with this audio controller and none with delivering audio input from the RP150 usb device (which is detected by ALSA) to ardour.  I have been able to get audio from the RP150 to Audacity, but the impetus for my inquiry into Linux is ardour and multimedia capacities...  I haven't studied Jack and have not found any resource to instruct me with Jack functionality... can anyone help with my specific problem or point me to Jack and ALSA literature?  Regards, S

---

### Post by sdkenned on 2011-04-22
No primer for JACK????

---

### Post by sdkenned on 2011-04-24
I know not why no replies have been posted.  Perhaps it is because you want me to search for posts on this topic... I have and have found a couple of threads... the problems of the persons posting threads concerning usb guitar processor to ardour are distinct from my own... hence this thread posting.

I would be content with audacity but have stability problems in windows and in ubuntu, audacity cannot record more than one track (I also searched for this problem on this forum but the problem was again dissimilar to my own, meaning the solutions suggested were ineffective or inapplicable to my problems).

---

### Post by sdkenned on 2011-04-24
If this post would be better placed in the ubuntu studio forum, will a moderator please relocate it?  Thanks!

---

### Post by cchhrriiss121212 on 2011-04-24
Hello,
Jack can be daunting on first try, simply due to all the options but it is simple once you get it running. Think of jack as a bunch of virtual cables that you can use to connect all your hardware and software together any way you please.

First open up the jack control setup window, then select your device from the "interface" dropdown list. Next select a buffer of 3, and frames setting of 512 which you can lower to give less latency. If you get xruns (audio dropouts) increase your latency via he frames setting. The other settings do not need changing. As this is a USB device I would not recommend anything higher than 48k for the sample rate. Check alsamixer from the terminal to adjust your volume levels.

Press start and jack should start running, now you can open up Ardour or what-have-you and connect things together with patchage (download this if you haven't already). If something is going wrong just post what the jack message window has to say, it usually will point you in the right direction.

Try not to be discouraged when you don't get a response, it won't be because the people here expect more from you, this is just a volunteer forum and it sometimes takes a few days for someone who knows the topic to see the thread.

---

### Post by sdkenned on 2011-05-02
Thanks for your reply.

I am, perhaps, not as familiar with computer (science) as I thought I was.  I had no idea I needed to select the usb device in the setup screen (under interface).

Now I can see the device in Patchage.

However, I do not know how the input/output connections should be setup.

Also, It appears Jack may detect my usb audio device as a midi device (at least, midi is in the name).

When I play a note on the guitar, I get visual input feedback in ardour (a partial victory?), as a blue signal intensity indicator at the edge of the primary track control panel (next to the visual data output area) but cannot get any audio signal from ardour.  When I export the recording to a .wav file and play it outside of ardour, I get no sound (thinking possibly ardour was not properly configured or connected to my system for audio playback).

Any direction from here?

Thanks for the reassurance and your attention (some boards are nasty out there).

S

---

### Post by cchhrriiss121212 on 2011-05-05
Good to see you have made some progress here.
> However, I do not know how the input/output connections should be setup.
For starters I would do a simple test to check the device works OK: just connect system capture 1 to system playback 1, then play your guitar. All you are doing here is sending the audio signal in to the computer, then straight out again.
If you can hear the unprocessed signal, then you know the device will work OK, and you can start recording or adding other things to the chain. If it does not work you may need to select a different playback port, or it could be that the device simply does not output audio. I have a USB device that can record but not playback.

To be honest I have not used Ardour in a while, so I am not sure about the export settings it has, but the fact that it registers a signal is good news.
I use Qtractor to record, which is simpler to use and I would recommend you try it out.

Regarding the wav file you have, what does it look like in Audacity? Is it empty or can you see an audible waveform?

---

### Post by sdkenned on 2011-05-07
Many gnarly thanks to you Ccchhris12!

I have live audio!  I am very impressed with the live capacity for my PC to arpeggate any audio I feed it (through the signal digitizer USB device)... my non-midi, non usb el cheapo keyboard with a 1/4 inch jack output (seemingly for headphones) plugs into the digitizer equally effectively as the guitar!  The tone generation is none too sophisticated, though... three cheers to you for expanding my digital music frontier infinitely!!!:guitar:

I think I like Qtractor just fine... seems less resource drawing than ardour???  Same or nearly so functionality???  I noted some looping functionality... I will need to explore this software... do you have any other suggestions for useful software for the digital music production initiate who is working with audio data?

Many thanks again!  Qtractor appears more responsive in patchage and I have no problem configuring the necessary connections at this point.

One more thanks for the help getting my foot in the door!

sd

---

### Post by cchhrriiss121212 on 2011-05-08
Excellent!

Qtractor is a bit lighter than Ardour but not by much. In terms of features: Qtractor has MIDI support and a mixer, but Ardour has more advanced audio tools (mostly automation stuff). Qtractor keeps things simple and functional, and that is why I like it.
> 
do you have any other suggestions for useful software for the digital music production initiate who is working with audio data?For software, you have the basics down: JACK and Qtractor. Audacity is a great tool for quick edits.
The rest depends on what you record, for guitars there is guitarix and rakarrack, for soft-synths there is phasex, bristol and yoshimi. For drums and sequencing there is hydrogen. For notation there is musescore. For soundfonts there is qsynth. For mastering there is JAMin. All of this is in the repositories, and of course free.
There are also a couple of proprietary DAWs that work nicely on Linux. Reaper works very well through WINE, and Renoise has a native Linux port. Useful if you like VSTs or want an alternative to FOSS offerings.

Software can only do so much though, the more you can learn about recording the better: mic-placement, mixing, mastering, where to place effects etc. Try searching through google for tips, there are thousands of guides and forums out there.

You could also take a look at system tuning (which is one of the advantages of Linux as a platform for audio). This link shows you everything there is on the subject:
[http://wiki.linuxmusicians.com/doku.php?id=system_configuration](http://wiki.linuxmusicians.com/doku.php?id=system_configuration)

That stuff is not essential however, the only tweaks I do are as follows:

[LIST]
[*]Use a lightweight DE like Openbox or XFCE (they are both great)
[*]Install a low latency kernel (PPA [here]("https://launchpad.net/%7Eabogani/+archive/ppa"))
[*]Set [swappiness]("https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?") to 1 and install preload (to make the most of RAM)
[/LIST]
Anyway, just take your time and have fun!

---

