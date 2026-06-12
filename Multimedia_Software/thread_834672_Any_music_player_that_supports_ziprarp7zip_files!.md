---
title: "Any music player that supports zip/rar/p7zip files?!"
date: 2008-06-19
forum: Multimedia Software
---

### Post by kung fu buntu on 2008-06-19
Is there anything on GNU/Linux world like Foobar2000? :(

I have lots of mp3 albuns in RAR or ZIP archives... It SUCKS having to unarchive them every time... just for Linux :-/

---

### Post by mc4man on 2008-06-19
I would think if anything amarok. I could only try a .rar, none of the 6 methods available here were successful 
(engage, open with, drag and drop, my r. click actions - enqueue, append, load)
Maybe there's a script - ck. amarok website

---

### Post by cozmicharlie on 2008-06-19
I would think you could write some type of script to do this.  If you can't find a way with a native Linux package then you could install foobar via wine.  I love the "live show tagger" in foobar and their is nothing comparable in Linux so I use foobar through wine and it works fine.  Their is a method for installing foobar in wine on the foobar forums.

---

### Post by jrusso2 on 2008-06-19
I don't think its a good idea to compress your music. Don't you lose quality doing that?

Most of the formats are already compressed.

---

### Post by Chrysalis on 2008-06-20
same as zipping any other file... you dont loose anything and you dont gain much of anything since music files are already compressed.

the most common use that i know of is for file sharing. people share/seed archived files so being able to play it out of the archive saves them from having 2 copes on the computer (one archived for sharing and another to listen to), theres probably more uses that i cant think of at the minute like maybe data corruption or password protection etc. . you get the idea ;p

---

### Post by padrecovsky on 2009-06-09
Hello,
so is there anything like foobar for linux? 
Since i have more than 200Gb of music in .rar files it's a great nuisance to always be decompressing them to be able to listen to them.


Cheers from a noob

---

### Post by andrew.46 on 2009-06-10
Hi padrecovsky,

> **padrecovsky said:**
> Since i have more than 200Gb of music in .rar files it's a great nuisance to always be decompressing them to be able to listen to them.

You have resurrected a reasonably old post here :-). However you may be interested to know that the commandline MPlayer *can* play rar files without having to manually decompress them:

```
unrar p -inul *myarchive.rar* | mplayer -cache 2048 -
```

I have taken the liberty of quoting from my own guide:

Top 10 Tricks and Tips for the svn MPlayer
[http://ubuntuforums.org/showthread.php?t=1154431](http://ubuntuforums.org/showthread.php?t=1154431)

where you will see similar syntax demonstrated for .zip and .gz files.

All the best,

Andrew

---

### Post by padrecovsky on 2009-06-10
> **andrew.46 said:**
> Hi padrecovsky,

You have resurrected a reasonably old post here :-). However you may be interested to know that the commandline MPlayer *can* play rar files without having to manually decompress them:

```
unrar p -inul *myarchive.rar* | mplayer -cache 2048 -
```I have taken the liberty of quoting from my own guide:

Top 10 Tricks and Tips for the svn MPlayer
[http://ubuntuforums.org/showthread.php?t=1154431](http://ubuntuforums.org/showthread.php?t=1154431)

where you will see similar syntax demonstrated for .zip and .gz files.

All the best,

Andrew

Yes i have ressurrected a very old thread, while searching for answers i found this thread and thought it would be better to ask here than to open another thread.
I'll be looking into the post you pointed me to. Thanks a lot.


Cheers

---

### Post by padrecovsky on 2009-06-10
> **andrew.46 said:**
> Hi padrecovsky,



You have resurrected a reasonably old post here :-). However you may be interested to know that the commandline MPlayer *can* play rar files without having to manually decompress them:

```
unrar p -inul *myarchive.rar* | mplayer -cache 2048 -
```I have taken the liberty of quoting from my own guide:

Top 10 Tricks and Tips for the svn MPlayer
[http://ubuntuforums.org/showthread.php?t=1154431](http://ubuntuforums.org/showthread.php?t=1154431)

where you will see similar syntax demonstrated for .zip and .gz files.

All the best,

Andrew

Hi there,
i've tried to do that and it doesn't seems to work :(
The message i get is this one:```
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.06GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing -.
Reading from stdin...
Cache fill:  0.00% (0 bytes)   
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll

```

Does this makes any sense to you? 
I feel i must point out that i'm one of the noobs. Been using ubuntu for a day now.
Thanks for any help.


Cheers

---

### Post by logos34 on 2009-06-10
> **Chrysalis said:**
> same as zipping any other file... you dont loose anything and you dont gain much of anything since music files are already compressed.

the most common use that i know of is for file sharing. people share/seed archived files so being able to play it out of the archive saves them from having 2 copes on the computer (one archived for sharing and another to listen to),

exactly. Which is why I don't understand why people use .rar for music--it doesn't compress the file any more (unless they're, like, wavs!)...luckily I see them only rarely on torrents.  You can also play music as it's being shared from your torrent folder--just don't edit the tags!

> **padrecovsky said:**
> Hello,
so is there anything like foobar for linux? 
Since i have more than 200Gb of music in .rar files it's a great nuisance to always be decompressing them to be able to listen to them.


foobar runs great on wine in linux

what format is the music in?  Because you could probably save a lot of space by converting it to another format

---

### Post by padrecovsky on 2009-06-10
> **logos34 said:**
> exactly. Which is why I don't understand why people use .rar for music--it doesn't compress the file any more (unless they're, like, wavs!)...luckily I see them only rarely on torrents.  You can also play music as it's being shared from your torrent folder--just don't edit the tags!



foobar runs great on wine in linux

what format is the music in?  Because you could probably save a lot of space by converting it to another format

I store the music files in a .rar mostly for filesharing, still an emule user :)
I'd say that 98% of the music is in mp3, and the rest in .mpc and some other formats.
I already tried to run foobar with wine, but it doesn't seem to be working, probably i'm the cause of it not working, but after spending 3/4 hours reading this tutorial --> [http://www.hydrogenaudio.org/forums/index.php?showtopic=54933](http://www.hydrogenaudio.org/forums/index.php?showtopic=54933) and not getting anything from it, i kinda got frustrated and tried to find other options.
You're of great help, thanks a lot again. People here are very supporting.

Cheers

---

### Post by andrew.46 on 2009-06-10
Hi padrecovsky,

> **padrecovsky said:**
> 

```
Playing -.
Reading from stdin...
Cache fill:  0.00% (0 bytes)   
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll

```

Does this makes any sense to you? 
I feel i must point out that i'm one of the noobs. Been using ubuntu for a day now.

I did not realise that you have only been using Ubuntu for a day, so my apologies for dragging you into a comparatively advanced usage of my favourite media player :-). This error message probably indicates that the rar archive contains some sort of playlist and I am not sure if MPlayer can actually read this from an *archive*. But if you are keen you could try a slight variation:

```
unrar p -inul *myarchive.rar* | mplayer -cache 2048 -playlist -
```

but I should mention that I have not tested this syntax. Some discussion of this error message [here]("http://www.mail-archive.com/debian-user@lists.debian.org/msg500740.html").

BTW welcome to Ubuntu!!

Andrew

---

### Post by logos34 on 2009-06-10
> **padrecovsky said:**
> I store the music files in a .rar mostly for filesharing, still an emule user :) I'd say that 98% of the music is in mp3, and the rest in .mpc and some other formats.

ok, I see...if it's already in lossy format, nothing to do there

> I already tried to run foobar with wine, but it doesn't seem to be working, probably i'm the cause of it not working, but after spending 3/4 hours reading this tutorial --> [http://www.hydrogenaudio.org/forums/index.php?showtopic=54933](http://www.hydrogenaudio.org/forums/index.php?showtopic=54933) and not getting anything from it, i kinda got frustrated and tried to find other options.

I had a look at that tut...looks really good--can't see where you might have gone wrong...except maybe try "standard" instead of "portable" installation.

.rar playback on my foobar is fine (shows I have "RAR reader" vers. 1.2 foo_unpack)...it might have changed though to **foo_unpack_7z**

where exactly is the problem?

---

### Post by padrecovsky on 2009-06-10
> **andrew.46 said:**
> Hi padrecovsky,
I did not realise that you have only been using Ubuntu for a day, so my apologies for dragging you into a comparatively advanced usage of my favourite media player :-). This error message probably indicates that the rar archive contains some sort of playlist and I am not sure if MPlayer can actually read this from an *archive*. But if you are keen you could try a slight variation:

```
unrar p -inul *myarchive.rar* | mplayer -cache 2048 -playlist -
```but I should mention that I have not tested this syntax. Some discussion of this error message [here]("http://www.mail-archive.com/debian-user@lists.debian.org/msg500740.html").

BTW welcome to Ubuntu!!

Andrew

First of all, there's no need for apologies, there's the need for me to thank the help.
And that syntax actually worked, so as far as i understood this line i should use when there's a playlist inside the .rar the previous one is for use when there's not a playlist, right?
Actually i'm feeling very welcomed into this world, people are always trying to help and find solutions for the problems.
So thanks again for the help.

Cheers

---

### Post by padrecovsky on 2009-06-10
> **logos34 said:**
> ok, I see...if it's already in lossy format, nothing to do there

I had a look at that tut...looks really good--can't see where you might have gone wrong...except maybe try "standard" instead of "portable" installation.

.rar playback on my foobar is fine (shows I have "RAR reader" vers. 1.2 foo_unpack)...it might have changed though to **foo_unpack_7z**

where exactly is the problem?

Thanks again for being so helpful firstly.
The problem is that actually foobar never got to work, open (i do miss it)
I followed the howto step by step until **IV. *Application Package ***and i've actually used the "portable" instalation and did everything according to the howto and it never worked.
The foobar icon actually appears under the "sound and video" tab, i click on it and nothing happens. i didn't continue to the components part, as i almost never use any of them anyway. I'm being a noob that's for sure, but where exactly am I ruining everything, i don't know. I hope you can understand what i've written.
So thanks again.

Cheers

---

### Post by yoasif on 2009-06-10
I'm fairly sure VLC will play rar files, give that a shot.

---

### Post by andrew.46 on 2009-06-10
Hi padrecovsky,

> **padrecovsky said:**
> First of all, there's no need for apologies, there's the need for me to thank the help.
And that syntax actually worked, so as far as i understood this line i should use when there's a playlist inside the .rar the previous one is for use when there's not a playlist, right?

That is certainly my understanding of the requirement and I guess this makes it all a bit clumsier. You could simply test this with either syntax or if you have developed a taste for the commandline you can list the contents of the rar archive as follows:

```
unrar l *myarchive.rar*
```

and decide from there. My apologies were for the most part because it is often a mistake to confront new Ubuntu users with the commandline as the gui is usually more welcoming. Hard for me sometimes as I am something of a commandline junkie :-).

> Actually i'm feeling very welcomed into this world, people are always trying to help and find solutions for the problems.
So thanks again for the help.

It is my pleasure :-). It is the Ubuntu community that keeps drawing me personally back to Ubuntu.

Andrew

---

### Post by padrecovsky on 2009-06-10
> **yoasif said:**
> I'm fairly sure VLC will play rar files, give that a shot.

You're absolutely right, it does play them.
There's only one problem, it plays an album as if it was one song only.
I'll keep trying to get foobar working.

Thanks

Cheers

---

### Post by padrecovsky on 2009-06-10
> **andrew.46 said:**
> Hi padrecovsky,


```
unrar l *myarchive.rar*
```and decide from there. My apologies were for the most part because it is often a mistake to confront new Ubuntu users with the commandline as the gui is usually more welcoming. Hard for me sometimes as I am something of a commandline junkie :-).

It is my pleasure :-). It is the Ubuntu community that keeps drawing me personally back to Ubuntu.

Andrew

For now i'm still a bit afraid of the command line :) , but with time i'll get used to it.
I'm really enjoying ubuntu so far, but let me get used to all those command lines, as it's still very frightening.
So far i'm positively impressed with all the help i've been getting. People are actually nice and helpful.
Again thanks for the help and tips.

Cheers

---

### Post by logos34 on 2009-06-10
> **andrew.46 said:**
> ```
unrar p -inul *myarchive.rar* | mplayer -cache 2048 -playlist -
```


It seems a variation of that works on vlc (sort of):
> 
unrar p -inul *myarchive.rar* | vlc -

but there's pops and glitches in playback and odd error messages, so I'm not sure what the deal is...

---

### Post by logos34 on 2009-06-10
> **padrecovsky said:**
> The problem is that actually foobar never got to work, open (i do miss it)
I followed the howto step by step until **IV. *Application Package ***and i've actually used the "portable" instalation and did everything according to the howto and it never worked.
The foobar icon actually appears under the "sound and video" tab, [COLOR="Red"]i click on it and nothing happens[/COLOR]. 

Did you run this command at the end of step III. (shell script):
> 
sudo chmod +x /usr/bin/foobar2000

?

---

### Post by padrecovsky on 2009-06-10
> **logos34 said:**
> Did you run this command at the end of step III. (shell script):


?

Yes i did. I also ran "gksudo gedit /usr/share/applications/foobar2000.desktop".
I just didn't do anything for the components. I stopped there.
But it shoul still work, shouldn't it?

thanks

Cheers

---

### Post by logos34 on 2009-06-10
what about running this in terminal:
> 
foobar2000

?

check foobar2000.exe in your portable foobar folder--does it have execute permission?  If not, run sudo chmod +x on it too

other than that you might check wine config

> winecfg

maybe add foobar in applications tab

But I doubt that's it--sounds like it may be a bug with 9.04 Jaunty and latest version of wine (assuming that's what you're using)

that's about all I can think of

good luck

---

### Post by lukeiamyourfather on 2009-06-10
Maybe I'm missing something but why don't you just decompress the archives in another location if you need to keep the original archives? I'm sure there are other issues that will come up like built in music libraries not working since they are usually based on folder structures (that are not compressed). Seems like a Rube Goldberg setup to be decompressing archives on the fly just to play music that's already compressed. Cheers!

---

### Post by padrecovsky on 2009-06-11
I must have done something wrong, so I guess i'll try going through all the steps from the beginning to see if i can get it working this time around.
Thanks for all the help still.
I'll be back with some news, hopefully good.

CHeers

---

### Post by padrecovsky on 2009-06-13
Finally i got it working :D
I'm not sure if this is the correct way, but it's working.
To open foobar i have to click on the foobar2000.exe and tell it to open with Wine Windows Program Loader, since when i click on the icon that's on the icon thats on the sound and video tab it doesn't open. Just glad its working. Hip hip hurray.
Just another question, how do i get it to scrobble to lastfm?
What do i have to do to get it to do that?

Cheers

---

### Post by padrecovsky on 2009-06-15
I installed the audioscrobbler plugin through Wine.
Now how do i get it to scrobble to lastfm?
Suggestions are needed, an are surely appreciated :D
Thanks.


Cheers

---

### Post by padrecovsky on 2009-06-21
Problem solved.
Just installed the windows version of lastfm through wine and it scrobbles perfectly.



:cool:

---

