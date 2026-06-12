---
title: "Is DTS Connect on the RealTek ALC889A supported on Ubuntu 8.04?"
date: 2008-04-14
forum: Multimedia &amp; Video
---

### Post by F for Fragging on 2008-04-14
I already [searched]("http://www.google.nl/search?q=site%3Ahttp%3A%2F%2Fubuntuforums.org%2F+%22dts+connect%22&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a") for DTS Connect, but it didn't give any useful results.

Currently I'm considering which motherboard I'm going to buy for my new PC. Currently my choice is the [Gigabyte GA-P35-DS3]("http://www.giga-byte.com/Products/Motherboard/Products_Overview.aspx?ProductID=2748"), but I've seen that the Gigabyte [GA-P35-DS4]("http://http://www.giga-byte.com/Products/Motherboard/Products_Overview.aspx?ProductID=2745") features [DTS Connect]("http://en.wikipedia.org/wiki/Digital_Theater_System#Others").

My current PC is connected with those three analog cables to my Logitech Z-5500 5.1 speakerset. AFAIK the problem with analog cables is that they can't give you 5.1 audio on DVD's, they only give 5.1 audio on games. And if I used a digital connection, the problem would be the other way around, no 5.1 audio for games but only for DVD's.

If I understand correctly, with the DS4 I could use a TOSLINK cable to connect to the the S/PDIF (digital optical) connector on the motherboard and hook it up to the digital optical connector of my [Logitech Z-5500 Digital]("http://www.logitech.com/index.cfm/speakers_audio/home_pc_speakers/devices/224&cl=GB,en") 5.1 speakerset, and get both games (because the analog 5.1 signal is then encoded as DTS AFAIK) and DVD audio in 5.1 audio. Also, just one TOSLINK cable is less clutter than those three analog cables.

Before I'm going to buy the slightly more expensive DS4 just for DTS Connect, I'd like to be sure that DTS Connect works on Ubuntu 8.04. I have a suspicion that the drivers for the RealTek ALC 889A codec, which provides the DTS Connect feature on the motherboard, don't support DTS Connect in Linux. That would mean that I'll have to play some Linux games like Quake 4 and Enemy Territory: Quake Wars on Windows to get 5.1 audio. Of course I want 5.1 audio on Linux, so I'd like to know if my suspicion is correct?

I also asked Gigabyte's helpdesk via e-mail if DTS Connect is supported on Linux, but they said that isn't tested. So my question is, is there anyone here who could tell me if DTS Connect will work on Ubuntu 8.04, or maybe even anyone who owns the GA-P35-DS4 motherboard?

---

### Post by Elif on 2008-04-27
Greetings.

I am using the GIGABYTE GA-MA69GM-S2H which features the Realtek ALC889A chipset. I am running Hardy on it and have been trying to get SPDIF working to no avail for about three hours. 

I am by no means an ubuntu expert but it does not seem to me like SPDIF will work on this motherboard in ubuntu out of the box. 

If anyone can help me hack it, please let me know :)

---

### Post by DuncanG on 2008-06-15
> **Elif said:**
> I am using the GIGABYTE GA-MA69GM-S2H which features the Realtek ALC889A chipset. I am running Hardy on it and have been trying to get SPDIF working to no avail for about three hours. 

Me too. Anyone got this combination working ?

---

### Post by Janusz11 on 2008-06-30
Just for your info: DTS Connect as well as Dolby Digital Live will not work on Linux. This is simply due to the reason that neither DTS, nor Dolby have (and most probably never will) released any proper drivers for Linux. 

Only for the nVidia nForce2 based motherboards (which come along with the MCP2-T chip) a nVidia driver exists that enables Dolby Digital encoding on the fly. However, it only provides stereo sound and the possibility to duplicate the stereo output to the rear speakers. No surround sound whatsoever (i.e. nothing what you're used to from the Windows drivers).   

That said, you can of course connect your computer via the optical S/PDIF output of your soundcard to any external decoder as long as the ALSA or OSS driver supports it. But the signal will be only plain stereo. You will never be able to experience true surround sound due to the lack of proper encoding of the stream. 

If you want to experience surround sound in games you either have to use the separate analog outputs of your soundcard- or simply use Windows (which in my eyes is still the only serious gaming platform besides all those uncountable consoles <-- just my 2 cent).

Concerning the Realtek ALC889A chip, its a relatively new chip exclusively produced for Gigabyte. Its the "light" version of the upcoming ALC889 chip, Realtek's new flagship. Therefore, don't expect any fully working drivers just yet. 	 

Hope that helps.

---

### Post by DuncanG on 2008-06-30
> **Janusz11 said:**
> ... use the separate analog outputs of your soundcard ...
Thanks for that, it's quite a revelation!
But are you saying that the four separate analogue outputs (front pair, rear pair, centre, sub) will output a decoded signal OK ?

---

### Post by Janusz11 on 2008-07-01
If you have a AC-3 decoder software and a properly setup media player then yes, the analogue outputs will give out a already decoded surround sound signal just fine. In other words you will be able to watch DVDs over such a setup. 

But I'd recommend hardware decoding and hooking up the computer via the S/PDIF with an external decoder when it comes to DVDs (saves the hassle with all the cables). And music is mostly in stereo anyway.  

For games of course the situation looks a little different. For a 5.1 system the three separate analogue outputs will give out three stereo signals: front stereo, rear stereo and a stereo signal combining the stream for the center and subwoofer.

---

### Post by DuncanG on 2008-07-01
I was a little confused by the "Connect" bit of DTS Connect. It's just digital output I want, normal Dolby or DTS, and it isn't working at the moment on my Ubuntu setup. That would be better than using my analogue outputs, I'd hope my $1K Yamaha can decode better than a $5 motherboard circuit. I'll have a play and see if I can persuade it.

---

### Post by Janusz11 on 2008-07-02
> **DuncanG said:**
> I was a little confused by the "Connect" bit of DTS Connect. 

DTS Connect just like Dolby Digital Live is rather a product name for a encoding technology. It means that the chip of the sound card or motherboard is able to encode an audio signal into a multi channel (like 5.1) format "on the fly" (in real time). The signal can then be send via a single cable over the S/PDIF to an external decoder. This technology is most (if not only) useful for interactive media like games and only for the reason that you can have very precise surround sound and everything only via a single cable. 

Mind you, there is no such thing like Dolby Digital *in* games. Its technically impossible. Only a soundtrack of a game could be in Dolby Digital/DTS. Its the chip (either hardware based like the MCP2-T of the nForce boards, or software based like most chips available nowadays on the market, like the CMedia CMI8788) which is doing the job.

DTS Connect and Dolby Digital Live are pretty useless for music or DVDs though, because music is mostly in stereo (keep in mind, Dolby Digital is a lossy audio codec) and DVDs come with an already mixed audio signal in either Dolby Digital or DTS, which is best send to an external decoder (passthrough) anyway. 

That said, you can still hook up your computer via the S/PDIF with any external decoder and listen to music or watch DVDs just fine. The signal is in stereo and for DVDs you pass the Dolby Digital/DTS signal through the S/PDIF on to the external decoder. Only the driver for the sound card has to work of course and support output through the S/PDIF

---

