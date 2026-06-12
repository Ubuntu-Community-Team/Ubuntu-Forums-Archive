---
title: "Presonus Firepod Problem!!!"
date: 2010-04-15
forum: Multimedia Software
---

### Post by Torque313 on 2010-04-15
I make music for a living and have started to do some community work with some inner city kids here in Detroit and i would like to find a way to show them how to build functional home studios with as little money as possible. I have no problems using allot of the software for linux for recording but the one thing i'm having a hell of a time doing is getting it to work with my own setup here at home. If i can't get this working i'm going to have to abandon the idea and show them stuff in windows. I'm going to look like a tool telling them all about linux and then not being able to show them in my own setup.
anyhoo here's my problem.....
I use a Presonus Firepod and i've run across a ton of tutorials and none seem to even work for me. I can't even get the light on the front of the firepod to turn blue like it's even connected at all much less get a sound out of it. Now i'm nowhere even close to a programmer or any of that stuff so anything you tell me will have to be the simplest method you know of. My knowledge of linux in general is not very good but i can kick some *** in windows so i'm not totally illiterate but it is a complete foreign language to me so take it easy on me lol. 
I also don't mean to be a **** but time is of the essence

---

### Post by cchhrriiss121212 on 2010-04-15
Firstly, what have you tried out? Do you know how to use jack/ffado? A little more information would help
Here is a document for starters that should help you out:
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

### Post by Torque313 on 2010-04-15
Well the truth is i have an old laptop that i got going with ubuntu and fell in love with it. I had a couple of issues getting it to work on the computer with my wifi card but finally found something to help and it's been straight ever since. On there i've played with some of the multitracking programs and editors and find that most of them  are set up just like allot of pro ones. I've been teaching at a local community center the basics of synthesis and showing kids how to build small synths and noise makers to get them interested in electronics and one day i took my laptop in there and showed them how to multitrack on ardour with one synth i had them build and created a short track with the kids as an example. they all asked me what i was using to do it and i told them i was using ubuntu linux to do it and that all the software to get it done was free and i saw thier faces light up because i know that there is no way that thier parents can afford some of the windows/mac machines and software they need to do this and there is no way i'm going to teach these kids how to pirate software in order to get this done. In my own studio i use Cakewalk Sonar but i can't expect these kids to be able to get that kind of setup so in the mean time i need to find a way to give them a working example of a function application of linux in a real music studio. This is why i need to get this card working in my setup. I'm a recording engineer and music producer by trade not a programmer so i'm going to need to know how to get my setup working in particular.

I went to the link you supplied but still no luck, i'm going to need specific intruction from one of you guys.

---

### Post by cchhrriiss121212 on 2010-04-15
But where are you having problems? If you know how to use ardour, then you know how to set up jack. Have you installed jack? Have you installed an rt-kernel? (this is useful for low latency audio processing)
Firewire devices are only supported through jack with the ffado driver, so you will need to install that from synaptic or the terminal. You need audio and video permissions to use firewire devices, which you can change from users & groups in the system menu. You also need to give the video group access to the raw1394 file. Reboot.
All this is from that link I gave you under the "firewire" heading, and if you read and follow all the instructions there you are on your way to getting this working.

Then you can open qjackctl and select the firepod as the interface in the setup window. Press start and see if it works.

---

### Post by Torque313 on 2010-04-17
ok now i have it working with ardour but i'm having allot of dropouts
i'm also having no luck getting it to work with the rest of the other stuff like mp3 players and no luck getting it to play sound from the web
any suggestions on where to go to find that info?

---

### Post by cchhrriiss121212 on 2010-04-18
> ok now i have it working with ardour but i'm having allot of dropouts
Could you post what settings you are using? The content of ~/.jackdrc, or a screenshot.

> i'm also having no luck getting it to work with the rest of the other stuff like mp3 players and no luck getting it to play sound from the web
any suggestions on where to go to find that info?
Jack is designed for pro audio and so does not have support for every program. It does have support for vlc and audacious which covers audio and video. You can also try to get pulse audio, which is the default sound server, to run through jackd, but this seems difficult for most users. Here's a similar thread:
[http://ubuntuforums.org/showthread.php?t=1453751](http://ubuntuforums.org/showthread.php?t=1453751)

---

