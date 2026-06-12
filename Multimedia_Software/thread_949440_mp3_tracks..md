---
title: "mp3 tracks."
date: 2008-10-16
forum: Multimedia Software
---

### Post by grillbert on 2008-10-16
Hi i have just recieved a new mp3 player samsung yp k5 but i noticed that there is a fade in at the beginning of each track and when listening to mixed dance music it ruins the mix. I do know you can split a single mp3 say 50 mins long into smaller mp3s. But is it possible to make one long mp3 with say 12 mp3 tracks?I would be very greatful for any help with this thank you:)

---

### Post by grillbert on 2008-10-16
Hi i forgot to mention that there is no option to turn the fade in off.

---

### Post by grillbert on 2008-10-16
Hi im sorry to keep posting but the edit won't load. Also as i take music from my cds and rip using wmp can i do the same thing with the tracks as i want to with the mp3 or would i have to convert the wmas to mp3.

---

### Post by DarkStarAeon on 2008-10-16
If your sound card is capable, you could in succession play each mp3 in a player (Mplayer, VLC, whatever you use) while using Audacity to record at the same time, and it wouldn't matter what format they were in as they played. A little odd, but it would work. 
You could even setup the 12 songs as a playlist in Rhythmbox so they play back to back, that way you don't have to keep clicking and launching songs manually.
If you don't have Audacity already installed, it will take a couple minutes of configuration once it is installed, but nothing difficult.
Once you are done recording, you could export the file to any format you want.

---

### Post by vanadium on 2008-10-16
If you want horrible quality and have a lot of time to spend, that is the way to go.

You should be aware that playing back tracks gaplessly with mp3 is not trivial, because the mp3 format unfortunately was not designed for that. Even if lossy audio files can be gapless (lame mp3's, ogg, mpc) then you still need a player that does effectively play them without interruption.

Also, you cannot combine different mp3's to one big mp3 without having little gaps between the tracks.

Your only solution unfortunately is to encode the entire CD as one single track. Again, unfortunately, Linux gui software rarely allows you to all tracks to a single one. There are some possibilities

1) The easiest one involves just using the command line

```

cdparanoia -v 1- image.wav
lame -V 2 --vbr-new image.wav

```
This will create a high quality file "image.mp3" containing the whole CD as a single track (you could pipe the commands to increase speed and avoid using the disk space taken by the wav).

2) With graphical tools, you could rip the individual tracks to wav or a lossless format like flac. Then you would need Audacity to import and combine the tracks. This will be far more time consuming than approach one.

---

### Post by DarkStarAeon on 2008-10-16
easy tiger, I was just offering a solution I could think of, trying to help. I said it was an odd one, no need to get all tense about it.

Besides, if his sound card is a good one, the "quality" wouldn't be any worse than the source or how it sounds to him already playing those songs on that computer.

You have a better solution, that's fine, I never said mine was perfect. Relax.

---

### Post by vanadium on 2008-10-17
No one is getting tense. I just discarded the option of recording with a one liner as being indefinitely inferior. Sorry if this has offended you.

You are right that it won't matter (except for  the time) when you listen through the PC speakers. However, the original poster was referring to a portable digital audio player and will be using headphones. It won't take an expert to hear the seriously degraded sound quality in these circumstances, even when using mediocre ear buds.

---

### Post by DarkStarAeon on 2008-10-17
I don't recall saying I was offended, but ok.

You continue to use speech that comes across as you being irritable, yet don't seem to realize it. If you don't mean it that way, great.

Again, I was presenting an option, and considering I have tried the suggestion I gave, and it sounded fine, perhaps my equipment is better than what you tried it on, perhaps you are a severe audiophile, I don't know.
It doesn't take an expert to know that with good equipment and even a minor amount of recording knowledge, you can get it to a decent quality. Considering how low quality mp3s are in the first place I think your point is irrelevant. Considering anything through earbuds and a portable player is going to sound less than great, again, I think your point is irrelevant.  Time seems to be a vital issue to you, sorry my suggestion didn't fit into your schedule.

Anyway, if you have a better solution, that is fine, I was merely presenting the person with an option that I knew of.

---

### Post by vanadium on 2008-10-17
> I don't recall saying I was offended, but ok.

and

> You continue to use speech that comes across as you being irritable, yet don't seem to realize it.

I perceived something you did not intend, and you perceived something I did not intent: that is inherent to communication between humans, and we have to be aware of it. Perhaps I am not the only one who needs to adapt.

> 
Again, I was presenting an option, and considering I have tried the suggestion I gave, and it sounded fine, perhaps my equipment is better than what you tried it on, perhaps you are a severe audiophile, I don't know.


To make sure, you would need to compare both versions -original and re-recorded - with headphones or decent speakers (not build-in computer speaker). I am pretty sure most people would readily hear the difference even if you carefully match the output levels. No need to be an audiophile or have expensive equipment.

> 
It doesn't take an expert to know that with good equipment and even a minor amount of recording knowledge, you can get it to a decent quality. 


What is 'decent'? It is quite likely that our original poster, wanting to listen to gapless music with headphones, will want to avoid the quality loss involved in re-recording the signal, even if the resulting quality can still be called "decent" (to what standards?).

> 
Considering how low quality mp3s are in the first place I think your point is irrelevant. 

Here you are making a serious glitch. Your statement about mp3 is plain wrong. So is consequently your conclusion on the relevance of my point. Audio quality of mp3s depends on the compression settings. You can easily create mp3's that essentially cannot be discerned from orginal CD audio, even when using expensive audiophile equipment.

> 
Considering anything through earbuds and a portable player is going to sound less than great, again, I think your point is irrelevant.
You might think so, but let the original poster decide for himself. Some portables and earbuds have pretty nice quality, and it will be easy to recognize your re-recording.

> 
Time seems to be a vital issue to you, sorry my suggestion didn't fit into your schedule.

Are you really sure you are not offended?

> 
Anyway, if you have a better solution, that is fine, I was merely presenting the person with an option that I knew of. 

Why then this heavy argument against my opinions above?

---

### Post by DarkStarAeon on 2008-10-17
Wow, you really need to be right that bad? 

I acknowledged repeatedly you have a much better solution, I just didn't think you needed to shoot down my idea in the manner in which you did, that's all.

I disgree on several of your statements regarding audio quality, but seeing as I can see where arguing anything with you will take this, I will gladly bow out of this one. I will say you defeated your own argument regarding the earbuds though, and stregnthened my point that equipment quality plays a factor.

Ok, fine Big Guy, you're the king, I personally don't have time for this, and seeing as how you seemed so time obsessed before, I'm surprised you have time for it now. Hope that helps you feel better about yourself.

I will thank you for reminding me why I usually don't post on forums.

---

### Post by vanadium on 2008-10-17
Don't take it so hard. I just gave my arguments why I consider it an unsuited approach. Hopefully we didn't scare grillbert away.

---

