---
title: "Music players"
date: 2011-09-08
forum: Multimedia Software
---

### Post by 3lud13 on 2011-09-08
Have been trying out alot of music players lately to find what one I like and one thing I have found them to be lacking is when listing my music none of them seem to group compilations together. this was one feature of itunes i really liked but now that i have moved over to the linux camp I find my search continueing for something suitable. Any suggestions

---

### Post by ajgreeny on 2011-09-08
What exactly are "group compilations"?  Are you talking of music groups eg The Beatles, the Rolling Stones, etc, or are they some grouping of your own, eg as ID3 tags to the files?  What about making playlists of all the music files in your groups;  that should do it.

---

### Post by 3lud13 on 2011-09-08
> **ajgreeny said:**
> What exactly are "group compilations"?  Are you talking of music groups eg The Beatles, the Rolling Stones, etc, or are they some grouping of your own, eg as ID3 tags to the files?  What about making playlists of all the music files in your groups;  that should do it.

I am talking about compilation albums like movie soundtracks and whatnot with multiple artists on one album.
Currently when I look at my artist list I have all these artists with 1 or 2 songs from compilations and its just very annoying would like to have them all moved into there own section

---

### Post by haqking on 2011-09-08
> **3lud13 said:**
> I am talking about compilation albums like movie soundtracks and whatnot with multiple artists on one album.
Currently when I look at my artist list I have all these artists with 1 or 2 songs from compilations and its just very annoying would like to have them all moved into there own section


i have lots of compilations, and a playlist for each one.

like ajgreeny said, its easy to do

---

### Post by dniMretsaM on 2011-09-08
I don't think there are any Music players available on Linux that have iTunes-like compilation handling. Playlists are your best bet.

---

### Post by haqking on 2011-09-08
> **dniMretsaM said:**
> I don't think there are any Music players available on Linux that have iTunes-like compilation handling. Playlists are your best bet.


I think [clementine]("http://www.clementine-player.org/") and [amarok]("http://amarok.kde.org/") might ?

i think i remember reading about it before somewhere ?

and [gmusicbrowser]("http://gmusicbrowser.org/") possibly

may be wrong, you will need to dig into them

---

### Post by dniMretsaM on 2011-09-08
> **haqking said:**
> I think [clementine]("http://www.clementine-player.org/") and [amarok]("http://amarok.kde.org/") might ?

i think i remember reading about it before somewhere ?

and [gmusicbrowser]("http://gmusicbrowser.org/") possibly

may be wrong, you will need to dig into them

I stand possibly corrected. I was unaware of this. Is Amarok's "Collections" feature what you're looking for? On an off-note, I really should try Amarok again. I haven't used it in a while. I didn't really like it the first time (I only used it for like a day, though), but as I was looking at the website just now I really like what I see in the features list. I think I'll take a look at Clementine also.

---

### Post by haqking on 2011-09-08
> **dniMretsaM said:**
> I stand possibly corrected. I was unaware of this. Is Amarok's "Collections" feature what you're looking for? On an off-note, I really should try Amarok again. I haven't used it in a while. I didn't really like it the first time (I only used it for like a day, though), but as I was looking at the website just now I really like what I see in the features list. I think I'll take a look at Clementine also.


you will need to dig abit, i am just remembering from reading a comparison somewhere.

I personally use rythymbox and playlists for compilations to be honest, it suits me fine ;-)

---

### Post by dniMretsaM on 2011-09-08
> **haqking said:**
> you will need to dig abit, i am just remembering from reading a comparison somewhere.

I personally use rythymbox and playlists for comilations to be honest, it suits me fine :wink:

After some searching I can confirm that you can use compilations on Amarok and it is very similar to iTunes. Amarok has always been touted as one of the most iTunes-like free players, I guess it's living up to it's name (except in the area of resource consumption ;-)). Anyway, 3lud13, give Amarok a try. You might find it has what you're looking for. Good luck!

---

### Post by 3lud13 on 2011-09-08
> **dniMretsaM said:**
> After some searching I can confirm that you can use compilations on Amarok and it is very similar to iTunes. Amarok has always been touted as one of the most iTunes-like free players, I guess it's living up to it's name (except in the area of resource consumption ;-)). Anyway, 3lud13, give Amarok a try. You might find it has what you're looking for. Good luck!

Looking at amarok its saying it is for the kde platform hence the reason I havent actually tried it yet would I be able to use this with gnome without issues

---

### Post by SeijiSensei on 2011-09-08
Installing amarok will automatically install the Qt libraries and other things that a KDE application requires.  There will be quite a few of these "dependencies."

I would suggest trying Clementine as well.  I used Amarok through the 1.x series, but didn't like the 2.0 version that was released with KDE4.  Clementine is a well-maintained fork of Amarok 1.4, but I don't know if it has the compilation features you're looking for.

The most up-to-date Clementine version is in this PPA:
[https://launchpad.net/~me-davidsansome/+archive/clementine-dev](https://launchpad.net/~me-davidsansome/+archive/clementine-dev)

---

### Post by SlugSlug on 2011-09-09
takes a little setting up but i think its the best music player I've tried.

you install the daemon 'mpd' and the gui gmpc

did I mention its by far the best I've used :)

---

### Post by nothingspecial on 2011-09-09
I know of one player that will do what you require but it's supposed to be for specific hardware, anyway

Squeezeboxserver

[http://www.mysqueezebox.com/download](http://www.mysqueezebox.com/download)

You don't actually need the hardware to use it. You can control it from a web interface. It's a music streaming server so you need a client to play the music, any one that will play a stream or you can install it's own cli player, squeezeslave (that involves building it yourself, I can show you how though if you are unsure).

Another nice thing about it is that you can connect to that stream from any other networked device, so if you have an internet radio, fancy phone or other computers you can play the same stream in different rooms which is great for parties and things.

It has a setting that will group compilations (tagged with the itunes complilation tag) together. Like I said, it's not a player but a server (like mpd), if you want to try it and need any help, post back.

---

### Post by davdo2004 on 2011-09-09
Have you had a look at Guayadeque.In the browser view you just click on the album cover and it will play the tracks in your compilation album or in the library view you can sort out your music any way you can think of. It is also lightning quick, I can find any song over 3 different hard drives in an instant. It is in the repos.  Here is a couple of screenshots.

[www.davdo.pwp.blueyonder.co.uk/guayadeque-1.png](www.davdo.pwp.blueyonder.co.uk/guayadeque-1.png)
[www.davdo.pwp.blueyonder.co.uk/guayadeque-2.png](www.davdo.pwp.blueyonder.co.uk/guayadeque-2.png)

---

### Post by nothingspecial on 2011-09-09
> **davdo2004 said:**
> Have you had a look at Guayadeque.In the browser view you just click on the album cover and it will play the tracks in your compilation album or in the library view you can sort out your music any way you can think of. It is also lightning quick, I can find any song over 3 different hard drives in an instant. It is in the repos.  Here is a couple of screenshots.

[www.davdo.pwp.blueyonder.co.uk/guayadeque-1.png](www.davdo.pwp.blueyonder.co.uk/guayadeque-1.png)
[www.davdo.pwp.blueyonder.co.uk/guayadeque-2.png](www.davdo.pwp.blueyonder.co.uk/guayadeque-2.png)

I love guayadeque and would recommend it as a full featured music player for linux over any other, however it doesn't do what the op wants, which is this

[ATTACH]201792[/ATTACH]

[ATTACH]201793[/ATTACH]

That is group all compilations together so you don't have to scroll through ten hundred bazillion artist that you just have one track of that came on a free cd on a magazine.

The browser feature in guayadeque does group all albums together but puts the compilations under one of artists on it, unless you know of a setting I don't.

**EDIT**: I would like to stress so that there is absolutely no confusion, that the album "Love Songs From Hollywood" in the screenshot belongs to and was purchased by my wife and has absolutely nothing to do with me. Thankyou

---

### Post by dniMretsaM on 2011-09-09
> **3lud13 said:**
> Looking at amarok its saying it is for the kde platform hence the reason I havent actually tried it yet would I be able to use this with gnome without issues

Yes, it will run perfectly fine on any DE. It will just install a few extra files that are installed with KDE by default. Same with a GNOME program, it would run just fine on KDE.

> **nothingspecial said:**
> **EDIT**: I would like to stress so  that there is absolutely no confusion, that the album "Love Songs From  Hollywood" in the screenshot belongs to and was purchased by my wife and  has absolutely nothing to do with me. Thankyou

:lolflag: :lolflag: :lolflag:

---

