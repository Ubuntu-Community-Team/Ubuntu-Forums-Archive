---
title: "players can't play .avi"
date: 2010-03-17
forum: Multimedia Software
---

### Post by goustaroubunta on 2010-03-17
neither Mplayer, VLC or SMPlayer can play an .avi i have. and they won't download the codecs needed.
look> [http://img2.imageshack.us/img2/144/wtfffl.png](http://img2.imageshack.us/img2/144/wtfffl.png)

should i manually download codecs from somewhere?
or shift to a new player maybe?

---

### Post by hazelnut on 2010-03-17
The AVI container format is obsolete and should be pitched out with your next sewerage flush.  

If VLC can't play it, there is something bizaar inside the container or it is DRM and you won't be able to play it without WinBlows Media PLayer.

---

### Post by goustaroubunta on 2010-03-17
(sorry, i'm not from an English-speaking country)

so you said i shouldn't use the avi format? 
and what format should i choose my downloads to be?

it's from axxo. it can't be with DRM.

it says:
permissions:
owner: stef - Stef [me]
access: read and write
video:
codec: Microsoft Windows Media 9
type: AVI video (video/x-msvideo)

i'm guessing it has to do with this> [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

note: i have installed the "Ubuntu restricted extras" software.

---

### Post by hansdown on 2010-03-17
Hi goustaroubunta.

I found a few instances, where WMP won't play aXXo.avi files.

[http://www.google.ca/search?aq=f&sourceid=chrome&ie=UTF-8&q=aXXo.avi](http://www.google.ca/search?aq=f&sourceid=chrome&ie=UTF-8&q=aXXo.avi)

---

### Post by hxcobd on 2010-03-17
Gousta, I'm pretty sure you're trying to play a virused video file that you downloaded from a torrent, lol.

When users upload fake video files, they're generally 10-20 second "intro" clips with a huge fake error message on the screen, like the one you're displaying.

And when you actually DO play the fake video file in Windows Media Player, it opens a warez website in Internet Explorer.

Solution: Download another torrent of that movie.

hahaha

(I have pretty extensive experience with downloading torrented movies myself, and have found fake videos like this all over the place.)

Think about it logically: if you didn't have the right codec, why would the video be playing in the background? lol

---

### Post by mc4man on 2010-03-17
Maybe try to produce some info from a terminal
Ex.
mplayer /path/to/filename
or
vlc -vv /path/to/filename

or just open vlc with vlc -vv and then try to play file

---

### Post by hxcobd on 2010-03-17
I'm 99.9% sure my answer is correct.

---

### Post by goustaroubunta on 2010-03-17
i mentioned "it's an axxo" as an argument about the file not being with
*Digital rights management*, since it's created by a known uploader.

i dunno.
it's a torrent downloaded many times. (not many tbh though)
 so logically it must be my operating system or my codecs' fault.

i'll check out some stuff and see what's going on..

---

### Post by goustaroubunta on 2010-03-17
> **hxcobd said:**
> I'm 99.9% sure my answer is correct.

omfg you _are_ right. i can't believe i'm such a noob. f$&k.

though it is my first time i see those idiotic videos> [http://img2.imageshack.us/img2/144/wtfffl.png](http://img2.imageshack.us/img2/144/wtfffl.png)

i uploaded the pic so that people with experience like you could see it and say whether they've seen something like that.

how the hell do they make it be 700mb  ?
lolz.

](*,)

note for dumbass (me): i should have noticed the complete absence of comments about[ that ]("http://*******.com/torrent_details/158018085/hangover+axxo?tab=summary")torrent x]
*facepalm*

---

### Post by hxcobd on 2010-03-17
Check the ratings on the torrent, if there are any.

Trust me, it's a fake upload. I've downloaded 3-4 movies in the past week that displayed that exact same "intro clip" with "PLAY IN WINDOWS MEDIA PLAYER" right on the screen.

It would make absolutely no sense if it were a codec issue. What, did the guy who ripped the DVD use one codec for the opening credits and a completely different one for the movie itself?

On top of that, look at the duration of the video file. 19 seconds.

---

### Post by hxcobd on 2010-03-17
> **goustaroubunta said:**
> omfg you _are_ right. i can't believe i'm such a noob. f$&k.

though it is my first time i see those idiotic videos> [http://img2.imageshack.us/img2/144/wtfffl.png](http://img2.imageshack.us/img2/144/wtfffl.png)

i uploaded the pic so that people with experience like you could see it and say whether they've seen something like that.

how the hell do they make it be 700mb  ?
lolz.

](*,)

note for dumbass (me): i should have noticed the complete absence of comments about[ that ]("http://*******.com/torrent_details/158018085/hangover+axxo?tab=summary")torrent x]
*facepalm*

haha, yup.

:)

Fake video uploads have plagued torrent sites recently. I have no idea why. It's almost impossible to keep up with them.

There are literally dozens of torrents for a 2010 movie called Frozen online right now, and EVERY SINGLE ONE I've tried has been fake. EVERY. ONE.

So irritating.

---

### Post by mc4man on 2010-03-17
> I'm 99.9% sure my answer is correct.
That sounds pretty right, have never seen that displayed message before from any linux player - (not big on dl'ed video

---

### Post by Baneblade on 2010-03-17
If you look at that video its only 19 secs long. That is a fake bud. You may also notice that the size is very small for what is supposed to be a full movie. I think you need to look into better sources.

---

### Post by hxcobd on 2010-03-17
> **Baneblade said:**
> If you look at that video its only 19 secs long. That is a fake bud. You may also notice that the size is very small for what is supposed to be a full movie. I think you need to look into better sources.

Nah, a lot of the new warez videos are actually 700 meg, which fools people even more easily.

There are a lot of techniques one can use to make a video file 700 meg; encoding the audio or video at an appallingly high bitrate and limiting the filesize to exactly 700 megs will do it.

---

### Post by goustaroubunta on 2010-03-17
> **hxcobd said:**
> Check the ratings on the torrent, if there are any.
[...]
Trust me, it's a fake upload..

absolutely mate. is this a new trend? i haven't downloaded torrents for 2 weeks and there are new dumb shite going on in the "industry"..

(btw is it "there are new dumb shite" or "there is new dumb shite"?)

---

### Post by hxcobd on 2010-03-17
> **goustaroubunta said:**
> absolutely mate. is this a new trend? i haven't downloaded torrents for 2 weeks and there are new dumb shite going on in the "industry"..

(btw is it "there are new dumb shite" or "there is new dumb shite"?)

("there is new dumb ****" would be correct.)

Yeah, it seems to be a new trend. There's a theory that it's a new way to combat piracy; by uploading dozens of fake videos, people just get discouraged and stop trying to download the movie in question at all.

Saves time on trying to come up with copyright protection/DRM. It'd actually be kind of brilliant if that's what they were doing.

---

### Post by goustaroubunta on 2010-03-17
> **hxcobd said:**
> haha, yup.

:)

Fake video uploads have plagued torrent sites recently. I have no idea why. It's almost impossible to keep up with them.

There are literally dozens of torrents for a 2010 movie called Frozen online right now, and EVERY SINGLE ONE I've tried has been fake. EVERY. ONE.

So irritating.

that's a relief. i used to make fun of my friends not recognizing fakes. and now i got the bait and i felt like a r#t@rd.
wtf we should make a blacklist for this rubbish.

---

### Post by hxcobd on 2010-03-17
> **goustaroubunta said:**
> that's a relief. i used to make fun of my friends not recognizing fakes. and now i got the bait and i felt like a r#t@rd.
wtf we should make a blacklist for this rubbish.

I considered doing such a thing, but after seeing the sheer NUMBER of fake torrents for any given movie, it'd be futile.

The best thing to do is just make an account on your favorite torrent site, and if you download a fake movie, make sure you click the site's "downrank" button so other people know it's fake too.

---

### Post by goustaroubunta on 2010-03-17
> **hxcobd said:**
> ("there is new dumb ****" would be correct.)

Yeah, it seems to be a new trend. There's a theory that it's a new way to combat piracy; by uploading dozens of fake videos, people just get discouraged and stop trying to download the movie in question at all.

Saves time on trying to come up with copyright protection/DRM. It'd actually be kind of brilliant if that's what they were doing.

if they are investing on that new defence, they should make many fake profiles on torrent sites and comment "**dharmasdad: **great copy thanks", "**AmEzAR: **Badasss moviee", "**Trindade: **Great quality thanks" and such.
i am downloading that movie from a new torrent. i sure hope those aren't fake comments !

oh and thanx for the help bro, keep it up. *thumb up*

---

### Post by hxcobd on 2010-03-17
Don't give them any ideas!

---

### Post by goustaroubunta on 2010-03-17
> **hxcobd said:**
> Don't give them any ideas!

heh :D  i'm sure they have thought about that, whoever creates those fakes.

anyway. goodnight from Greece mate.

---

### Post by goustaroubunta on 2010-03-17
oh and i downloaded a _real_ torrent for that movie and MPlayer _does_ play .avi 
so **this thread is officially resolved** (not to mention dumb -from my side).

---

### Post by hxcobd on 2010-03-17
In linux, any media player is limited to playing filetypes currently installed on your system via Gstreamer codecs.

So if you have a specific Gstreamer codec installed, then in theory, all of your media players (MPlayer, Totem, VLC) should be able to play it.

---

### Post by hazelnut on 2010-03-18
In my understanding VLC is independent of other installed codecs.  All video decoding is statically compiled into the binary.

---

