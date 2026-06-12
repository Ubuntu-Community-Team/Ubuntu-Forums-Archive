---
title: "Why Amarok Stinks"
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by unimatrix on 2008-01-07
Yes, that's right, I think Amarok is a really bad piece of software. Now let me explain why.

Every time I leave Amarok on for a few hours without playing anything, after I come back and it loads the next song, the entire system hangs with a pleasant high-pitched tone coming from the speakers. There is no AltGr+SysRq+REISUB... (Almost never works anyway), so I have to reset my computer and risk data loss.

The second thing that bothers me about Amarok is it's HUGE resource consumption. No matter what database I use (and I use MySQL which was supposed to be the fastest) it needs more than 50% of CPU usage for a moment just to load the next song! (Imagine Winamp doing that?? People would go mad). And yes, I have a decent PC (AMD64 2500+ if you must know).The memory consumption is also enormous. If I load my entire mp3 collection into XMMS's playlist, It still uses less memory than a simple 20-song random playlist in Amarok. That's just sick.

Another thing is the visualizations. They are just pathetic. At least they could've made all of the XMMS's ready-made ones work in Amarok. Also, who ever thought of a visualization that is locked to a resolution of 640x480... Well Amarok gives you that too.

Next thing are key shortcuts. You can have Global shortcuts and just Shortcuts. I'm not entirely sure what's the difference, but there are no useful shortcuts in either of those sections. Why can't I toggle 'repeat track' with a shortcut? Who in their right mind would need a 'burn CD' shortcut more than that? The only useful ones are Skip, Stop and Play (but not Skip Backwards - because it doesn't work in dynamic random playlists... try it yourself)

And of course playability of different media. Basically, Amarok can play Mp3, wave, and some other similar formats. But what about Midi files? Mod files? ... Dream on. Most audio software can play that (even on Linux), but hey, why should Amarok.

But what bothers me most is the way people praise Amarok like it was so good. It's simply not. Don't ever tell me XMMS and Audacious aren't better, because Amarok has A LOT of catching up to do before it could even compare to those.

---

### Post by meho_r on 2008-01-07
> **unimatrix said:**
> 
But what bothers me most is the way people praise Amarok like it was so good. It's simply not. Don't ever tell me XMMS and Audacious aren't better, because Amarok has A LOT of catching up to do before it could even compare to those.

Why does it bother you? If you don't like it - don't use it. It's simple as that. There're always XMMS, Audacious, Exaile... Many people love amaroK because it IS good for them. Leave them be...

---

### Post by unimatrix on 2008-01-07
Well of course I agree with you.
But deep down I feel like I want to support it. Maybe I was too rough with it in my first post. The thing is that the whole idea about Amarok is really good, but the implementation still needs a lot of work.
Btw. I use Amarok mainly because of the dynamic random playlists (can't have that in XMMS/Audacious .. or at least not that I know of any practical way).

Oh and by the way, my friends sort of wanted to force me to use it XD... I don't blame them.

Anyway, what I would really like to hear is somebody comment everything else I wrote, about the problems with Amarok. I can't simply ignore them, can you?

---

### Post by picpak on 2008-01-07
I suppose you could give Exaile a try. Be warned, though, that it can vary. For instance, it runs smoothly on my system but eats up all the CPU on my sister's. See if it works for you though.

---

### Post by unimatrix on 2008-01-07
Thank you for your reply picpak. I have tested Exaile and must say it has most of the functionality I need (not perefect, but better than Amarok), and it also feels lighter. However on my KDE system where I've tested it, it is constantly using around 7.5% of CPU (open or minimized or minimized to tray) which is unacceptable.

What I would like to se is a program capable of playing (and loading the next song) and sustaining **_less_ than 1%** of CPU usage at it. Actually XMMS can do that, but it's kinda old and getting abandoned by modern distros. Also Winamp can do it... why couldn't any other linux program do it too. That's like saying Windows is better... :/

---

### Post by picpak on 2008-01-07
If you're feeling up to it, maybe even cplay can do what you want. K.Mandla has a guide on it [here](http://kmandla.wordpress.com/2007/05/01/howto-use-cplay-like-a-pro/).

---

### Post by silverhammermba on 2008-01-08
I like Amarok (though I just started using it a few minutes ago).

I tried XMMS and Audacious. I liked the similarity to Winamp but I just can't live without robust music management tools. Amarok may be a bit slow loading tracks, which is annoying, but it does what I need it to do.

Also, I did try Exaile before Amarok and didn't like it. Most of it's the same but it was a bit lacking. The media library has a lot less navigation options than Amarok's and generally seems less customizable. Also, it was a pain in the *** to load my m3u playlists since Exaile didn't automatically import them along with my music. Furthermore, I had a lot of problems while editing file information - either it wouldn't let me at all or would max out my CPU and take 15-20 seconds to edit just a single song.

So basically, I like Amarok because it's an incredibly robust program - even if it's a bit of a hog and has some minor flaws.

---

### Post by jeffus_il on 2008-01-08
> **unimatrix said:**
> Well of course I agree with you.
But deep down I feel like I want to support it. Maybe I was too rough with it in my first post. The thing is that the whole idea about Amarok is really good, but the implementation still needs a lot of work.
Btw. I use Amarok mainly because of the dynamic random playlists (can't have that in XMMS/Audacious .. or at least not that I know of any practical way).

Oh and by the way, my friends sort of wanted to force me to use it XD... I don't blame them.

Anyway, what I would really like to hear is somebody comment everything else I wrote, about the problems with Amarok. I can't simply ignore them, can you?

OK, support is positive, it is different to "Amarok Stinks" Do some research, find out what is causing the problem, maybe its your setup, your hardware environment, the sound driver you are using, maybe some advice from the forum would help ...

---

### Post by unimatrix on 2008-01-08
You can't do any research when your computer freezes. It means there will be no log files. :S
Unless you got any better ideas i suppose. I did all the research I could, but found nothing.

A friend of mine suggested me that the problem may be within the xine engine. However I can only select xine as an engine, even after installing the amarok-engines package. Any idea why?

---

### Post by jeffus_il on 2008-01-08
You can do some things
Check out what you are running in your session, eliminate stuff that you don't need.
When you run programs , try to run it alone so that you have more of and idea what was running when it freezes.
Maybe run "top" in a console (Ctrl-Alt-F1)
When your machine freezes you may be able to Ctrl-Alt-F1 to the console and see what's happening

---

### Post by unimatrix on 2008-01-08
> **jeffus_il said:**
> You can do some things
Check out what you are running in your session, eliminate stuff that you don't need.
When you run programs , try to run it alone so that you have more of and idea what was running when it freezes.
Maybe run "top" in a console (Ctrl-Alt-F1)
When your machine freezes you may be able to Ctrl-Alt-F1 to the console and see what's happening

Thanks, but I really can't do anything after it freezes, because it's a full kernel freeze. I'll try 'top' though, but I already suspect I'll see mysql or amarokapp in the upper row.

---

### Post by unimatrix on 2008-01-08
Update:
Did what u said, and saw nothing. The system froze so fast none of the process managers could show anything.

---

### Post by jeffus_il on 2008-01-08
Try a different engine in Amarok
using 
Settings -> Configure Amarok... -> Engines

If the engine is causing the hang, this will work.

---

### Post by derouge on 2008-01-08
Jeffus, he can't select any different engines.

> **unimatrix said:**
> A friend of mine suggested me that the problem may be within the xine engine. However I can only select xine as an engine, even after installing the amarok-engines package. Any idea why?

---

### Post by unimatrix on 2008-01-08
Thanks derouge :)

Edit: I've also filed a bug... If someone with the same problem ever googles this thread, here's a link: [https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/181289](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/181289)

---

### Post by jeffus_il on 2008-01-08
Does xine work OK? I mean if you use the Xine-ui or Gxine?
Can you access the Amarok text setup file in your home directory, you could back it up and delete it, so it could start afresh with default values, you could try to find the driver line and change it there ...

---

### Post by unimatrix on 2008-01-11
OK, guys I didn't forget about this. I was testing some stuff (it took me quite some time too).
Amarok doesn't seem to be the direct cause for the system freeze problem. I noticed the freezes only happen when reading audio files from a mounted NTFS partition. That's right. It seems that ntfs-3g is not stable after all.

If someone wants to try and replicate this bug:
1. make a music collection consisting of mp3 files written on a mounted NTFS partition
2. make a dynamic random playlist in Amarok (don't know if this step is necessary)
3. play a song (preferably using xine engine)
4. stop/pause the song (dynamic playlist stays)
5. leave Amarok open for 30 minutes (maybe less, i haven't been able to find the minimum)
6. play/resume a song, if nothing happens, skip to next song
That should cause a system freeze. At least it does on my computer.

So the solution to solving this main Amarok annoyance would obviously be to have all partitions ext3. But then (no matter how rarely) I wouldn't be able to use those partitions in Windows. Luckily I only use windoze about 5 times a year, but this still shouldn't happen.

PS: Next Amarok annoyance... It is possible to set a global key shortcut to toggle repetition of current track?

---

