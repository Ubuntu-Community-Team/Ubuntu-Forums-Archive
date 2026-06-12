---
title: "exaile rc 3.2 - again no sorting by album artist!"
date: 2010-06-16
forum: Multimedia Software
---

### Post by piedro on 2010-06-16
Hi everybody! 


I was glad to see another release of exaile. I'm always happy to see improving mainstream desktop apps, especially when they start being much superior to their commercial counterparts in both, quality and quantity, of features. 

But as if developers are ignoring the simple usability problems - again - exaile like all other gnome music players (apart from amarok, but that's kde!) can't browse your library by album artist! 

Got some samplers in your library? 
Yeehaa! - you then find thousands of unknown artists with just one song each in your library... easy to browse and easy to find!
Yeah! - you find that any artist who was featuring other artists will get dozens of entries also like "xy feat. A", "xy feat. B", "xy feat. C" ... beautiful and great usability! 

It's obviously completely ridiculous to do the sorting of audio libraries in a similar manner like those huge billion dollar companies that spend lots of money researching the ways people like to browse music. 
What do they know!? - They're just idiots that invest money to make even more money!

Yes I know: I should have learned programming instead of complaining ... maybe true, but I haven't. But still: 
What's so complicated about adding another library browser view in "exaile", "rhythmbox", "banshee" ... you name the others ... that sorts not only per "artist" but additionally, per choice, just for convenience also per "albumartist". Why can you tag it when it's ignored afterwards anyway? 

The handling of compilation and mixed-artist-albums with gnome mainstream music organizers is still a mess and this hasn't changed since I first installed linux 5 years ago ... for me this is really annoying. 

just my few cents. 

But whatever, 
thx for reading, 
piedro

---

### Post by Edu Camargo on 2010-08-23
Hi people, my first post. Hope you guys are fine out there. Greetings from Brazil.

@Piedro:

You see, the most supported format, MP3, even with an extensible  metadata  called ID3V2.3 (currently the most supported) has no  implementation for such item, making some sort of mess. Yes, Micro$oft  and Apple decided that TPE2 (band/orchestra/accompanyment) should be  used by default for storing album artist info, but as you see above, was  a trick, since there's no frame in ID3 that defines album artist info.  Some other developers have tried to push the concept of storing the  album artist into a TXXX frame. TXXX is a frame for custom fields, so  any modern player could put any info it feels comfortable. The problem  with that is that it breaks compatibility with limited players, devices,  blah and yadda. So the second option becomes useless.

The only audio formats I know of that have native support for Album  Artist natively are Micro$oft's WMA and Apple's MP4 Atoms. Probably some  other proprietary formats have such implementation as well, but since  we're talking about formats that are widely supported, the rest doesn't  matter.

Most music in my library is in FLAC format. Now get the picture. Things  can get massier than you can expect. There are three variants for Album  Artist pushed by some software and hardware developers supporters of the  format. ALBUMARTIST, ALBUM ARTIST and ENSEMBLE. Some players use all,  some use just one of them, and some use none. Which one do you think I  prefer? None of them!

The lack of standardisation in certain formats turns everything related  to metadata in a big fat head-ache. And I've read in several places  around the WEB, that even some devices from Apple that came after iPod,  does not support Album Artist propperly. Even the iPods seem to give  partial support for this field... This makes me think that this won't  change. After installing Ubuntu 10.04 and discovering this issue, and  also after further reading about this behavior in diferent softwares for  diferent operating systems, I decided to go for what everybody  understands.

So in a VA album, I'd put VA in the artist field, and then I'd put 'Song  Title - Artist' in the title field. Optionally I could use the comment  field for the purpose of storing the artist(s) performing the song,  since the comment field is ment for storing any text You and I might  think that is relevant for the listener or for ourselves.

Well, in the real world of physical media, the artist is the name that  appears on the CD right? If is there any aditional artist performing in a  song other than the main artist it appears in parenthesis after the  song title, ok? (Like on Christina Aguilera's album 'Stripped' - 'Dirrty  (feat. Redman)'.) Or if it's a VA album, song title and track artist  are separated with a dash, right? Sometimes the track artist appears in  brackets. Well, in the digital area the story goes on. I've purchased a  VA album from HDTracks and I found exactly this situation.

I use exaile in my linux box, and although I think they'd enhance it in  the future, I gave up, not for them directly, but for the  incompatibility that might occur amongst players. At least, they give  support for multiple discrete values. I'd go for the idea of letting the  user decide what collums should be displaied. For example, in classical  music you could browse or view composer information, conductor,  performer and so on.

Took me some amount of time to realise it, since my library is always  album-based, but in the end you have to face it. Less is more. But I  understand your point.

Thanks for sharing.

Peace,

Edu Camargo.

---

### Post by piedro on 2010-09-09
Thx Edu! 


I got some insight in this now. I do understand the problem to a little deeper level now. But ... 

I don't think less is more at this point. 
The handling of your music collection is for most private users one of the most important issues for their valueing of the dektop environment , even the whole operating system. 

In that respect Itunes has reached a standard status and is the trendsetter for look & feel (coverflow, library browser, cover download ...). I'm not saying I need all this stuff and I certainly don't want to be restricted by their closed license and feature list, but I have to admit, I expect (like most other users) I know at least the same functionality and at least the possibility of organizing my music with the same systematic approach to have a collection that is somewhat compatible to my friend's not using linux for example. I want to open up my music collection on my computer when giving a party and tell my freinds: just create a playlist, you'll be the DJ for the next hour. 

I'm trying to make the following point: There are conventions from a users point of view and they don't care about the technical difficulties to implement these conventions. It's hard to give up conventions like the method of organizing your music collection, so there should be a similar way - at least as a choosable option. 

Why can't we have a brwoser view in rhythmbox: genre - albumartist - album ? I understand it won't be perfect and it will not work for some files but it'll work on many. 
And can be done by the way: 
banshee has an albumartist based  collection support, just no browser view for it 
rhythmbox developers just ignore the constant bug reports and requests on this topic - so I don't know 
guayadeque is working hard towards solving the issue, it's working with most of the files 
some frontends for mpd support it more or less but most of them feel clumsy or buggy to use
gejengel can do it, but has no browser use at all 
deadbeef, clementine as very simple players work on it (as I understand) but are not really useful for huge collection management 
exaile fails like amarok, they have a kind of compilation support, but you can't search for albumartist, there's no browser or library view with it and if you use the compilation flag it won't work with other programs ... in my experience 

As you see, Edu, it can be done, people are working on workaround and in the end what counts is usability. We have to stop thinking that technical purity and conceptional difficulties should dictate the user experience. 

Anyways, thx for reading, 
piedro

---

### Post by Yellow Pasque on 2010-09-09
Maybe you should link to where you've reported this to exaile devs as a bug/feature request (because ranting about it on ubuntuforums.org might not be the most effective way to get it resolved ;) ).

---

### Post by Edu Camargo on 2010-09-09
As I've mentioned, I understand your point. But nothing is more painful than spending a big amount of time organizing your collection of music using for example, Foobar2000 for Windows, and getting convicted for a long time that the method used is what really counts, only to find some years later, like I did, that the criterias you've been applying are broken in most players, even for Windows. And although iTunes has gained a good reputation for setting standards on music organization, it's not even close to perfection. One of the most important things for me, for example, is support for multiple discrete values. Nothing is more irritating than browsing by artists, for example and finding something like this:
Beyoncé
Beyoncé/Jay-Z
Beyoncé/Bun B/Slin Thug
When all you need is:
Beyoncé
Jay-Z
Bun B
Slin Thug.
Users ask for it from time to time but the story is the same, even iTunes being in its 9th incarnation. Guayadeque is in an early stage, seems to be a new option for GTK users, but I can't say much about it, since I haven't tested the software to its fullest due to issues of interaction between it and Orca. (I'm blind).

But as someone suggested, it is always a great idea to submit a request to Exaile developers. Who knows they answer you better than the Rhythmbox team, and wins off Amarok in this department?

Peace,

Edu.

---

### Post by piedro on 2010-09-10
Hi Edu! 

I guess your right about nonexeistent perfection in iTunes. 
I think most of the players mentioned above have way more potential to be really good than itunes ever will. 

For your problem with the multiartist tracks and by the way the same applies to tracks you want to put into multiple labels, for all that there's probably only a database based soltuion suitable with a database holding all the information you're using and simply ignoring or at least extending the very limited id-tags of the various formats. I think amarok is a databased solution but doesn't really use it for the purposes discussed. 

But Temüjin and you are right, I will report my issues as bug to the exaile developers again. 

cya, 
piedro

---

### Post by Carroll Vance on 2010-10-29
Hi Edu, this feature is in the latest version of exaile in bzr, as well as support for m4a album artist tags. Its sad that we have to use a different field to support this, but it seems that id3 is broken and we have no choice to support this if we are to properly support mp3.

Carroll

---

### Post by Edu Camargo on 2010-10-29
Have to check out, thanks for posting, Carrol. Is it possible to obtain the latest beta from a repository?

Again, thanks. At least Exaile will come around and will play a more fair game in this senario, alongside Amarok.

The only thing that I think that needs some fix is proper gapless playback support in all albums. I've plaied with some things I have here, 'SMiLe' by Brian Wilson and 'The Turn of a Friendly Card (Expanded Edition)' by The Arlan Parsons Project, both albums in flac format. The latter still produces some milliseconds of gaps. This was also tested in Rhythmbox and everything works fine in Rhythmbox. But I've heard that this gap problem is something to do with Playbin2 which Exaile is using now for atempting gapless.

Again, thanks for keep me posted.

Peace,

Edu.

---

### Post by piedro on 2011-01-03
Hi there again! 


... maybe we get lucky after all these years (this is banshee):
[https://bugzilla.gnome.org/show_bug.cgi?id=540873](https://bugzilla.gnome.org/show_bug.cgi?id=540873)

cya, piedro

---

