---
title: "Java stealing the whole soundcard?"
date: 2008-07-03
forum: Multimedia Software
---

### Post by UpSignal on 2008-07-03
Hello my friends. Well, first things first:
    I'm having an awesome experience with ubuntu. I have a laptop (HP dv6000) and a desktop pc. Both running ubuntu hardy heron. I have all my stuff working, audio...video...webcams...microphones, all the stuff, so i can say i'm a pretty happy user! Since i drop windows, i never looked back. BUT...however there's one small detail that really annoys the hell out of me. It's the damn Java. When i'm playing "runescape" (a java based game), all my soundcard goes for it. I mean, i can't listen music while i'm playing. It's like Java steals the whole sound!
    On the other way, Flash it's cool! i can play music whçy watching youtube, no problem. Or while i'm watching a movie on Mplayer!
    It seems the Java audio engine it's a crap, i don't know! i'm not a linux geek, i can get most things working, but this time i really need help! Someone told me it was possible to change the java sound engine, so it can play cool with other audio programs. Is that true? How?

Some details:

Using Java JRE version 6 and firefox version 3
I have the Gstreamer codecs installed, and my system is updated. I never changed my audio components ( i believe i'm using the pulse audio, the default). So, if i need to change to some other audio, like alsa or such, just tell me how. i just need my java working perfect! :)
    Thanks in advance for all the time you can spare with me

---

### Post by Nadab on 2008-07-03
The same thing happens with me, except that it happens when i'm trying to watch an youtube video...if there's a music player on, or just opened, the audio from the video in youtube simply doesn't work.

---

### Post by UpSignal on 2008-07-03
that's because you need to install a little plugin. Open synaptics and search this:

flashplugin-nonfree

     and

libflashsupport

Install both, and restart firefox. Now you should listen youtube and any music player :)
I wish java was so easy

---

### Post by UpSignal on 2008-07-04
bump! still waiting for some tips

---

### Post by Nadab on 2008-07-04
Thanks man, and don't worry, someone is gonna help like you helped me. That's the meaning of the forum right? 
I see you're from Portugal (I'm from Brazil), so maybe you should try to post your problem at the [[COLOR="Blue"]UBUNTU FORUM - PT[/COLOR]]("http://ubuntuforum-br.org/"). Give it a try.

---

### Post by UpSignal on 2008-07-18
bump...

---

### Post by MakotoTheKnight on 2008-07-19
Java just robs us of the sound card while we play RuneScape.  It's destined, unfortunately.  I *think* it's filed as a bug someplace, but for now, there's a neat little workaround that I've used.  It works faithfully for me, but your mileage may vary.

Pulseaudio has a neat little wrapper that you can add to most programs.  In this case, it'll wrap the sound output of Java out to Pulseaudio so it doesn't rob you of your sound card.

To use it:

padsp firefox

OR

padsp firefox %u

I have mine set up so that it 'wraps' my browsers on launch.

Good luck :)

---

### Post by UpSignal on 2008-07-19
awesome! i'll try that later :) thanks so much

---

### Post by UpSignal on 2008-08-02
> **MakotoTheKnight said:**
> Java just robs us of the sound card while we play RuneScape.  It's destined, unfortunately.  I *think* it's filed as a bug someplace, but for now, there's a neat little workaround that I've used.  It works faithfully for me, but your mileage may vary.

Pulseaudio has a neat little wrapper that you can add to most programs.  In this case, it'll wrap the sound output of Java out to Pulseaudio so it doesn't rob you of your sound card.

To use it:

padsp firefox

OR

padsp firefox %u

I have mine set up so that it 'wraps' my browsers on launch.

Good luck :)

Hi again dude. your fix worked like a charm. the problem is:
I can't set this to browser startup. I red all over the web, that i have to edit the Firefoxrc file, located in /etc/firefox , or, /etc/firefox-3.0/

The problem is.. the file it's not there. weird stuff, in firefox 2 i could edit that file with no problem. now, it's gonne. is there any other idea to add PADSP to firefox startup? 
Now that i googled for the word "padsp", i understood that this problem is a bug from pulse audio. And it's funny because nobody in several foruns, could simply tell me this:

"no dude, you're not doing anything wrong. that's a bug in pulse audio. Just follow this workaround". You're the only guy that really helped me. thanks man

---

