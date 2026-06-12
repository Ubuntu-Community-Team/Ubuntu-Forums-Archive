---
title: "Audacious?Xmms?Crossfade???"
date: 2008-08-29
forum: Multimedia Software
---

### Post by Seti on 2008-08-29
I dunno what it is exactly about this whole xmms vs. audacious thing, but its really getting on my nerves. OK. Today tried to install xmms like always, INCLUDING xmms-crossfade, and find that apt no-can-do. OK. So I guess it's this whole "we're all using Audacious now, Xmms is old and no longer maintained" business. So I install Audacious and audacious-crossfade. Where is the plugin? How do you enable it in Audacious? Why is this 10 times more difficult than it used to be with Xmms, the "no longer maintained" package?
Someone please enlighten me.

---

### Post by markbuntu on 2008-08-29
Did you try getting xmms from here:

i386:

[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)

amd64:

[https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2) 

Beware of dependency problems with libglib1.2 and libglib1.2dbl on the amd64 build, i386 is no problem. You can read about that here:

[http://ubuntuforums.org/showthread.php?t=774461](http://ubuntuforums.org/showthread.php?t=774461)

Change the output plugin to alsa and you should be good to go.

---

### Post by Seti on 2008-08-29
What a frigging nightmare. Why is nobody in these forums addressing the issue that many of us are having with Audacious sucking the CPU cycles like crazy? I did a search and found a thread where it was sort of being discussed, and when I go to post a reply in that thread it says I don't have permission to post????? but I digress.

Why is it that after 5 years of using linux, I am finding myself next to impossible to install the decent media player that I like with the crossfade plugin???

/edit

I installed the audacious-crossfade plugin and OK now that works. It still doesn't resolve the issue that Audacious is really using WAY too much CPU cycles. 'top' is showing audacious using upwards of 42% CPU. For a 2.0 GHz P4 this is unnaceptable in my opinion. 

any ideas would be greatly appreciated.

---

### Post by Seti on 2008-08-29
So now I've installed xmms, except xmms-crossfade wont' install:mad:
when I go ```
./configure
```
I get:

"configure: error: *** xmms-config not found - please install first (comes with XMMS > 1.0.0) ***"
Soo... here are my choices. Use Audacious and have the functionality of the crossfade plugin AND just accept that its using about 42% of my CPU's time... OR...
Use Xmms but not have the xmms-crossfade plugin. 

WTF

---

### Post by Seti on 2008-08-31
So in other words nobody knows anything about this at all, right?

/BUMP

---

### Post by emshains on 2008-09-02
Maybe you must compile the xmms and xmms-crosfade together to make 'em work, hmm? Like copy the code in a single folder and then try to ./configure make sudo make install. I'm no expert and I think I won't be wright this time.

---

### Post by Seti on 2008-09-02
Found a binary for it [here]("https://launchpad.net/ubuntu/hardy/i386/xmms-crossfade/0.3.12-2build1").

At least now I can listen to mp3 sets where each track has to cut right into the next one. I love the 'gapless' feature in the crossfade plugin.

I don't know why its so hard for other media-players to adopt this kind of functionality.

---

### Post by peter-xf on 2008-12-04
{XMMS,Audacious}-crossfade does not do any guessing as to what player to compile for, so you have to use: 

```
./configure --enable-player=audacious
```

Hope this works for you...

---

### Post by gychang on 2008-12-09
> **peter-xf said:**
> {XMMS,Audacious}-crossfade does not do any guessing as to what player to compile for, so you have to use: 

```
./configure --enable-player=audacious
```

Hope this works for you...

I am relatively new and interested in installing crossfade to audicious player I have been using.  Is the command above will install "crossfade" function?

gychang

---

