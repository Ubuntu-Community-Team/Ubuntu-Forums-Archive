---
title: "ardour ?"
date: 2007-07-06
forum: Multimedia Production
---

### Post by firedancer on 2007-07-06
i am able to start jack an them ardour, but the als driver won't load when using my soundcard ESS Technology ES 1969 
only some others and oss, but when i record nothing actually records

I was kind of happy so i can start recording again , but ....

so if anyone has an answer


i 'm going to purchase a penthium 4 cpu , cause this celeron thing is not it
i have 1 Gig ram  


:(

---

### Post by firedancer on 2007-07-07
i can only choose oss driver + ESI soundinput/ouputs 

i get some soft sound ,cant hear anything i record

and i get a audioengine error ardour is not able to connect rite


imme try ardour on the dyne now 


i'm finally have some time to sort out things about ardour




:(

---

### Post by firedancer on 2007-07-07
ok audacity on d:b is recording "sound on sound" just like i was trying before , but now it's going without skips an such, so i think with a m-audio it will be better (the sound)


ardour, understanding jack better now , but i have a questions

What actually causes the Xruns  (i reached a maximum of 25.424 msec), and  what is the way to prevent /eliminate this 


that's my only questions , kind a happy again, cause i really thought my "linuxrecordingproject" would be a very long one 

anybody can answer my question pls. 


[-o<

---

### Post by firedancer on 2007-07-08
I have a ESS 1969 

and a lexicon omega , also supported by alsa-project

but when i try alsa driver in jack , it just would not go , changed settings but still nothing,

only oss , butr then ardour can't connect to soundengine

how can i make alsa connect to server the client and let work with ardour


:confused:

---

### Post by firedancer on 2007-07-08
thank you alsa folks, ardour folks,     oss plp



finally , thought i wasn't going to make it but finally , ardour is a strong recorder indeed

just need to read some about panelling mono tracks, etc..

but i'm dear , well dyne i fought with , but 

ubuntu-studio folks love you alot , finally can do some soundonsound recording without a hassle , well hopefully i'll get the m-audio 66 for multitrack stuff , but for now i'm reeeeaaallly happy :popcorn: for everyone and some sodas  


it's a pity sound was not recording with the lexicon omega because the 4 tracks were detected but , i still checking if it will be possible 

strange that alsa had problems with the ESS soundcard it is supported, but not such a good quality either , so

and no response is good too, i like the challenge (lol) 

:)

---

### Post by fredj on 2007-07-11
Xruns are caused by some other process interrupting jack so that it can't play or record the sound stream
in time. To get really professional sound on ubuntu you need to install the real time kernel. Look at the sticky
at the top of this forum.

---

### Post by firedancer on 2007-07-14
I have it already , but i do need a pentium 4 processor , although now i.m recording already 

thnx to all who contributed 


yeah and when recording i shouldn't do other stuff , i know now 





saludos

---

### Post by fredj on 2007-07-15
Pentium 4 processors are to put it frankly crap and even Intel have abandoned them. Get an Intel core duo
processor if you want to upgrade. Xruns and latency are related to lots of things. Older computers with older
soundchips and conflicting interrupts may never be able to reach a low latency.
I have a Samsung Q35 notebook with a modest core duo 1.8Ghz processor and a build in Intel HDA audio 
system that can easily achieve a latency of less than 3ms without Xruns. Your processor is a bit underpowered
but it might be the soundcard that is limiting the latency you can achieve.

---

### Post by skipkent on 2007-07-15
Fun with Ardour:  record a basic song or ditty with your guitar and Hydrogen drum machine playing a simple 1-bar loop in the background.  Record the guitar, but don't record Hydrogen just yet.  Now go to Hydrogen and work out a full arrangement for the song.  This will force you to learn Hydrogen which is a good thing as that is a VERY well-crafted application.  With both apps linked to Jack, this works great.

Now, once your drum sequencing is done, go into the preferences menu for Hydrogen and enable multiple outs.  This is where the fun starts!  Assign these to tracks in Ardour and record them.  Now you've got lots of tracks to play with and work out groups, busses and so on.

You COULD just leave all the drum tracks in Hydrogen, but where's the fun in that?!

---

