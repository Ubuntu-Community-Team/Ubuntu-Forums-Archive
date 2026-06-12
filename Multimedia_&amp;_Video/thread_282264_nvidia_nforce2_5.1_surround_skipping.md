---
title: "nvidia nforce2 5.1 surround skipping"
date: 2006-10-22
forum: Multimedia &amp; Video
---

### Post by key134 on 2006-10-22
Hi everyone.  I have been trying to search around the forums for my problem, but I have not been able to find any posts with my exact problem.  I think it is partially because the "skipping" keyword can mean too many things.

I have an ASUS A7N8X-E Deluxe motherboard with an nforce 2 chipset and, yes, it does have soundstorm.  The reason I have not followed the howto about this ([http://ubuntuforums.org/showthread.php?t=253725](http://ubuntuforums.org/showthread.php?t=253725)) is because my rear speakers DO sort-of work.  In vlc, when I change the audio device to 5.1, all of the speakers start skipping.  I have tried multiple dvds (retail and burned) so that is not the problem.  The 2 front 2 rear setting works in vlc, but then I am pretty sure I don't have my center channel and it is not surround anyway.  Has anyone had this problem?  Do I have to install nvidia's drivers?   It is so close to working.

Thanks in advance,  Keith

---

### Post by Icarosaurus on 2006-11-07
Hi Key,
well, I have a similar problem. I own an Abit AN7 MoBo with soundstorm and analog speakers.
I installed succesfully the Nvidia proprietary drivers, but when I play 5.1 streams with EVERY player, central/Subwoofer channel switches to Rear Right/Left channel (I hear central in the rear/left).

Note that under Windoz I have to switch the corresponding jacks on the MoBo (so, the black jack plugged into the orange port and vice-versa) to have a normal situation. I don't know if you have the same problem, but I had the same with an Abit N7F. Surround works fine in Windoz with this configuration.

So, under Ubuntu, with jacks inverted, I hear a normal 2D sound with Rear speakers cloning front ones, but I have to switch the jacks to hear 5.1 correctly (but Subwoofer doesn't seem to sound very loud).

Noone gave me a real solution, but I tried at least to make the question :
[http://ubuntuforums.org/showthread.php?t=253725&page=6]("http://ubuntuforums.org/showthread.php?t=253725&page=6")

As you see, I followed the HOWTO, but I had only a partial solution to my problems (oh well, hardware mixing works great!)

Maybe someone will solve our problem in the future :)

---

### Post by Genius16 on 2007-03-16
Greetings. I have the same problem with my soundcard. When I play a DVD in VLC it plays fine, but when I switch it to 5.1 the sound skips, constantly, to all channels. 2.0 sound works fine. My audio information as follows:

SiS SI7012 with AD1888 Codec
Motherboard is 761GX-M754 (V3.0A) 
North/South Chipsets 761GX & 964

Running Kubuntu 6.10
Not using a ~/.asoundrc file, I run the speaker-test without passing a var for -D but using -c 6 it attempts to play through each channel, though only front right/left will sound. Passing a var of -D surround40 -c4 it plays through front/rear fine. passing -D surround 51 -c6 it gives me an error. 

Any ideas as to why I would get an error? Prehaps there is no surround51 device specified? I'm rather new to how sound works in linux... Also, the main issue being trying to play a 5.1 source, skipping sucks!

Oh, the soundcard uses 3 shared jacks, which I have plugged in analog Logitech x-540 speakers to. 


Also, if the suggestion is to buy a real sound card, which one? Looking for something that is rather cheap (less than 80-100 USD) and would support my speakers (3 1/8" mini plugs, rather standard for low end 5.1 computer speakers) I'm looking at the m-audio revolution.

---

