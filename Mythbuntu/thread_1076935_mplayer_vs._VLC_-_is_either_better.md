---
title: "mplayer vs. VLC - is either better?"
date: 2009-02-21
forum: Mythbuntu
---

### Post by gungfujoe on 2009-02-21
This may be a naive question, but is there any advantage to mplayer over VLC?  I've generally heard good things about VLC (across all platforms), but even though Mythbuntu installs VLC by default, the standard setup plays videos within MythTV using mplayer instead.

Basically, I'm having trouble getting mplayer to do something that VLC does [pretty much automatically]("http://ubuntuforums.org/showthread.php?p=6776708"), and I'm wondering if I'd lose anything by changing my default player to VLC.

---

### Post by joho500 on 2009-02-23
I'm using VLC to my satisfaction a couple of months now. I prefer it because I find VLC more complete when setting it up using the GUI. I can't say that vlc is better than mplayer.

Cheers,
Joost

---

### Post by august495 on 2009-02-23
I use VLC to, only because I couldn't get rid of the screensaver kicking in while useing MPLAYER. I like it and have no problems with it.

---

### Post by dgray_from_dc on 2009-02-23
I use VLC because I don't have to worry about which codecs I have installed.  I do think that mplayer is more polished.

---

### Post by bobbob1016 on 2009-02-23
I use both.  Mplayer on my Mythbox since Mplayer can use CoreAVC which allows for multi-core video decoding, great for 1080p.  I use VLC to play videos on my desktop.  Mplayer seems to be like a swiss army knife, as in can do almost anything if you know how, and VLC is a normal knife, it is simple to use, but doesn't come with a toothpick.

---

### Post by Archmage on 2009-02-23
I'm using Mplayer, because you get install it without GUI and I think that I can change more setting with a keystroke.

---

### Post by simtaalo on 2009-02-23
mplayer is cool, but vlc is near perfect.i cant actually think of anything wrong with it. just works perfectly, always plays the files that other players might not sync up quite right.

vlc every time :)

---

### Post by SuperSonic4 on 2009-02-23
SMPlayer is the best front-end to mplayer imo. It basically does what mplayer does with vlc's options and it remembers where you left off. Plus for some reason vlc does not work on my setup

---

### Post by gungfujoe on 2009-02-24
> **bobbob1016 said:**
> I use both.  Mplayer on my Mythbox since Mplayer can use CoreAVC which allows for multi-core video decoding, great for 1080p.
Thanks, this may be a key point for me, since I'm using a relatively low-end system for an HD HTPC.  Being able to use both of its relatively slow cores for HD video decoding might be important, since I'm finding that neither Mplayer nor VLC can play my 720p MKV files without introducing video artifacts (horizontal lines periodically, especially in fast-moving scenes) that I don't get on my faster Windows system.  I'll have to look into CoreAVC and see how I can go about setting it u (I see a couple threads that cover it).

And since I'm primarily using this as an HTPC, the GUI interface doesn't matter much except for setup, as I'll be playing videos full-screen 99% of the time.

---

### Post by hirak99 on 2009-10-14
I use mPlayer, VLC, Winamp with CCCP, Media Player Classic - Home Cinema - though I am gradually phasing out mPlayer and will probably soon delete it.

I haven't found much problem with mPlayer or VLC. With VLC though, a significant advantage is that you can increase the volume well above 100% - upto 400%.

I play the HD movies with MPC-HomeCinema - it does so without breaking sweat in my AMD Athlon 64 X2 4000+, since it uses my graphics card's H264 decoding chip directly. I have NVidia 8600 GTS card.

Winamp's advantage is that it can almost magically identify any song by looking at the mp3 - and suggests proper ID3 tags from the Gracenote database.

---

### Post by pederj on 2009-10-15
> **hirak99 said:**
>  With VLC though, a significant advantage is that you can increase the volume well above 100% - upto 400%.

Mplayer does this too with a software mixer. Edit the configuration file, adding the following:
```

softvol=yes
softvol-max=400

```

---

### Post by ravi.xolve on 2010-04-06
> **pederj said:**
> Mplayer does this too with a software mixer. Edit the configuration file, adding the following:
```

softvol=yes
softvol-max=400

```


Your tip is really great!!! Now I don't need vlc at all!

Hey any way to show up the volume in numeric.

---

### Post by sajdude on 2010-04-06
VLC all the way, its the best on all platforms... Has tons on features....

---

### Post by ravi.xolve on 2010-04-07
MPlayer is not supposed to be the actual player but to be wrapped up by some GUI (at the time SMplayer seems to be the best). It has a really good codebase and has variety of options, even allows to play in console (I think VLC too supports this).

With raw MPlayer you need to configure the options yourself and I feel that it will be hard to find a feature in any of them which can't be found in another (thogh how you set and use it differs)

I like MPlayer because it allows you tons of ways to use - command line, warapped up in another GUI, you can use it with some nice scripts as a console audio player and so many things. The keyboard shortcuts to seek 10s, 1 min and 10 min are great and its pretty straighforward to use.

---

### Post by ravi.xolve on 2010-04-07
MPlayer is not supposed to be the actual player but to be wrapped up by some GUI (at the time SMplayer seems to be the best). It has a really good codebase and has variety of options, even allows to play in console (I think VLC too supports this).

With raw MPlayer you need to configure the options yourself and I feel that it will be hard to find a feature in any of them which can't be found in another (thogh how you set and use it differs)

I like MPlayer because it allows you tons of ways to use - command line, warapped up in another GUI, you can use it with some nice scripts as a console audio player and so many things. The keyboard shortcuts to seek 10s, 1 min and 10 min are great and its pretty straighforward to use.

---

### Post by ben2talk on 2010-11-03
I just set up my TV with Twinview (nVidia) - so now I launch video's and put the player off the PC monitor.

VLC shouldn't be compared directly to mplayer, rather to SMplayer which gives you some extras.

Mostly for me it's the ability to sit and watch the TV with just my keyboard.

Currently SMPlayer wins out - video is excellent, hitting the 'a' to set aspect ration cycles more options and gets it right (good if you have an old tube 4.3 monitor and wanna compress to 16.9 - so need the anamorphic output)

With SMPlayer there are the same controls as VLC - but more accessible are the contrast, brightness, hue/saturation settings.

It's also easier to adjust audio delay (ahead/behind video) and subtitles (for my Thai gf I like to set them about half a second ahead so she can read and then listen) - the subtitles also look nicer to me (maybe I could set up vlc to look as good...).

Annoyances - F11 doesn't work - it's 'F' for fullscreen
ctrl H doesn't 'hide' the interface, you have to use ctrl C for 'compact' - but the keyboard and mouse settings are very accessible and incredibly comprehensive (way ahead of VLC here guys)

SMplayer has a nicer interface than VLC when you put it on the screen.

Awesome - game over, use Mplayer with the SMplayer interface.

---

### Post by geekyhawkes on 2010-11-04
I have had problems with mplayer since upgrading to 10.10 (it doesnt play files but does allow me to skip forward through them, wierd) and was thinking of going to VLC.  I guess my question is 2 fold, firstly anyone know how i might fix mplayer post upgrade and if not, how do i run vlc without the gui displayed from myth? (the mrs doesnt want a keyboard out everytime we want to watch a ripped film etc). 

Thanks guys

---

### Post by nickrout on 2010-11-04
You really should switch to the Internal player. Access to external players is going away fairly soon. Internal has developed enormously.

---

### Post by dakota34 on 2010-11-04
Nick, is it really going away? The last mention I saw was a [this thread]("http://www.gossamer-threads.com/lists/mythtv/users/436989?search_string=external%20players;#436989") on the myth users list (actually I think you were a part of that thread) -- has a decision been made to withdraw the supportfor external player mentioned in that thread?

---

### Post by nickrout on 2010-11-04
> **dakota34 said:**
> Nick, is it really going away? The last mention I saw was a [this thread]("http://www.gossamer-threads.com/lists/mythtv/users/436989?search_string=external%20players;#436989") on the myth users list (actually I think you were a part of that thread) -- has a decision been made to withdraw the supportfor external player mentioned in that thread?

Seems to be a bit up in the air, seer this mythbuntu thread, which is more recent:

[http://ubuntuforums.org/showthread.php?p=10045706](http://ubuntuforums.org/showthread.php?p=10045706)

---

### Post by luisito on 2010-11-04
Sorry if it is not really your question, but if you want to play 720p or even 1080p smoothly, what works really well is to use the vdpau driver from NVIDIA.

I have a HP z555 with a Pentium 4 (much slower than yours). I bought an NVIDIA 8500GS video card (which is probably the best choice for video alone) and I can see smooth 1080p using either XBMC or mplayer with the NVIDIA drivers. I don't know if vlc uses vdpau.

---

### Post by ravi.xolve on 2010-11-05
I am using plain mplayer and its great!!! I don't need any wrapper. The keyboard shortcuts are the big plus with mplayer.

---

### Post by waynerod on 2011-06-27
> **august495 said:**
> I use VLC to, only because I couldn't get rid of the screensaver kicking in while useing MPLAYER. I like it and have no problems with it.

Have you tried Caffeine ([https://launchpad.net/caffeine]("https://launchpad.net/caffeine"))?

It prevents screensaver (and dimming, etc). I use it when I'm watching videos. :popcorn:

---

### Post by Rasa1111 on 2011-06-27
yeah, VLC is better.

but lately Ive been using "UMPlayer", and it's awesome!
very cool, check it out!

---

### Post by thatguruguy on 2011-06-30
I'm pretty sure that the correct answer to this and any Linux-related question is, "Try them both. Whichever one you like more is the best one for you."

---

### Post by staropram on 2011-07-06
> **thatguruguy said:**
> I'm pretty sure that the correct answer to this and any Linux-related question is, "Try them both. Whichever one you like more is the best one for you."

There is no correct answer.

It's always useful to get recommendations and opinions off other users, especially those who are more knowledgeable and experienced that oneself.  Besides, it is fun to discuss these things anyway. You learn about others, and it helps build a sense of community.

Furthermore, sometimes the sheer quantity of options makes the "find out for yourself" option untenable or at least prohibitively time consuming. For example, if someone asked me "what unix-like OS should I use, I'm a total newbie and I don't know ls from rm" I don't think they would be helped by me saying something like:

"Oh, go away and try out MiLAX, have a quick look at Debian, try out a Dragonfly BSD while you're at it, and you might want to roll your own LFS too. Don't ask me what you want, go away and find out for yourself!".

No, I'd say "start with ubuntu and move on when you get itchy feet".

I don't think you've acted in a manner concordant with the former, so I'm not having a go. But I just happened to see your response when searching for something on google, and felt compelled to hug a longstanding personal bugbear.

Of course in the case of VLC vs mplayer, we are only talking two options, so the problem isn't so dire, and it is trivial to try both. But in summary:

Getting recommendations from others that one can trust can save one a lot of time and ballache.

staro

---

### Post by runny6play on 2013-01-03
> **gungfujoe said:**
> Thanks, this may be a key point for me, since I'm using a relatively low-end system for an HD HTPC.  Being able to use both of its relatively slow cores for HD video decoding might be important, since I'm finding that neither Mplayer nor VLC can play my 720p MKV files without introducing video artifacts (horizontal lines periodically, especially in fast-moving scenes) that I don't get on my faster Windows system.  I'll have to look into CoreAVC and see how I can go about setting it u (I see a couple threads that cover it).

And since I'm primarily using this as an HTPC, the GUI interface doesn't matter much except for setup, as I'll be playing videos full-screen 99% of the time.

You might also want to look into vdpau or VA-api for unloading some of the work to the graphics card.

---

### Post by sudodus on 2013-01-03
I use them both and I like them both, but in different ways.

I usually run mplayer directly from a terminal window. I have aging computers, and was very happy with the improved graphics performance with 12.04 Lubuntu compared to what I used before, vanilla Ubuntu 10.04. I have an nVidia GeForce GT 430 card. VDPAU started to work really well with 12.04 (to play 1280x720-50p and 1920x1080-50p from my camera).

VLC is very good on most platforms, and I find it easier to use (so I also recommend it for beginners).

---

### Post by howefield on 2013-01-03
Old thread closed.

---

