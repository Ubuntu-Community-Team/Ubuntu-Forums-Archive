---
title: "[SOLVED] Xvidcap crashes"
date: 2008-03-27
forum: Multimedia &amp; Video
---

### Post by spiderbatdad on 2008-03-27
Hi,
Trying to use Xvidcap to capture youtube video from my desktop.
When I start the capture utility, it crashes immediately. Terminal output says Segmentation Fault Core Dumped. Any help appreciated. Thanks.

---

### Post by spych102 on 2008-03-28
I had that problem with xvidcap so I started to use Istanbul instead.

---

### Post by mathew.chacko on 2008-03-29
It also crashed on 64bit Hardy beta. But when I disabled the audio it stoped crashing on start, but freezes randomly time to time. Also it records like fast forward... :(

---

### Post by spiderbatdad on 2008-03-29
Istanbul is what I started with. It crashed everytime I ran it, so I tried Xvidcap. 
Gtk Recordmydesktop works fine for this particular application.

---

### Post by spych102 on 2008-03-31
> **spiderbatdad said:**
> Istanbul is what I started with. It crashed everytime I ran it, so I tried Xvidcap. 
Gtk Recordmydesktop works fine for this particular application.

Actually I think Istanbul used to crash before I upgraded my RAM from .5G to 1.5G, how much RAM do you have? BTW you can set the post to [Solved] on the Thread Tools menu at the top of the thread.  :)

---

### Post by spiderbatdad on 2008-04-02
1g

---

### Post by spych102 on 2008-04-02
Okay, that doesn't prove anything yet. I must disable Ram on my system to test my thesis. A quick google search unearthed this for grub on a debian system:

```
/boot/vmlinuz-2.6.18-4-686 root=/dev/hda5 ro mem=2G
```

I know that I need to replace the kernel version with the version I have and the reference to hda5 needs to change to my root partition but should the mem=2g  be changed to 0.5G or to 512M?

---

### Post by eGlyph on 2008-05-15
A quick investigation in Hardy Heron shows that the xvidcap works fine without sound capture. Settings for sound capture for multiframe capture show that /dev/dsp is used. By default only root has an access to /dev/dsp.
So ```
sudo chmod a+rw /dev/dsp
``` should solve the issue. And it does.

---

### Post by mlivio on 2008-05-18
Hi eGlyph,

I tried your solution for fixing "xvidcap" crashing under Ubuntu Hardy (8.04) but after changing the permission of /dev/dsp file, the application "xvidcap" still crashes under Ubuntu Hardy.
When I disable the audio in multi-frame options "xvidcap" doesn't crash but I can't record any sound.
Do you know where this bug could come from as I tried debugging with "strace" and "lsof" but I can't find where the problem is.
By the way, I also tried to compile "xvidcap" but it still carshes and other applications like "recordmydesktop" and "istanbul" don't work either under Ubuntu Hardy (they freeze).

Thanks for your help,

Livio

---

### Post by eGlyph on 2008-05-21
> **mlivio said:**
> Hi eGlyph,

I tried your solution for fixing "xvidcap" crashing under Ubuntu Hardy (8.04) but after changing the permission of /dev/dsp file, the application "xvidcap" still crashes under Ubuntu Hardy.
When I disable the audio in multi-frame options "xvidcap" doesn't crash but I can't record any sound.


It seems you're right. I was playing with the xvidcap and once has been able to record with the sound. Black magic involved probably, but now it crashes again.
However I found it easier to record the silent video first, then narrate the text and add the background music, etc. Just a quick workaround.

> 
Do you know where this bug could come from as I tried debugging with "strace" and "lsof" but I can't find where the problem is.
By the way, I also tried to compile "xvidcap" but it still carshes and other applications like "recordmydesktop" and "istanbul" don't work either under Ubuntu Hardy (they freeze).

I keep investigating this issue. One thing to note is that in my Hardy installation recordmydesktop works fine, though I'd like to have ye ol' good xvidcap.

---

### Post by eGlyph on 2008-05-27
> **mlivio said:**
> 
By the way, I also tried to compile "xvidcap" but it still carshes and other applications like "recordmydesktop" and "istanbul" don't work either under Ubuntu Hardy (they freeze).

Thanks for your help,

Livio

The real problem on my computer was in trying to record two channels audio. 
The solution is quite simple. Look at the picture: [IMG]https://wiki.ubuntu.com/ScreencastTeam/RecordingScreencasts?action=AttachFile&do=get&target=xvidcap3.png[/IMG]
The sound is disabled but parameters are clearly visible.

---

### Post by nixtux on 2008-06-07
> **spiderbatdad said:**
> Hi,
Trying to use Xvidcap to capture youtube video from my desktop.
When I start the capture utility, it crashes immediately. Terminal output says Segmentation Fault Core Dumped. Any help appreciated. Thanks.

I came across this while trying to resolve a hanging issue with xvidcap.    

This may be a bit late to post, but you don't need to use xvidcap to capture youtube and the likes.  Just look in /tmp dir and the flv file will be in there.  I find it best to play with movie player.  

Hope that helps and saves you some time.

---

### Post by mlivio on 2008-06-17
Hi,

sorry for the late answer but after trying your prposed solutions I still have a segmentation fault with "xvidcap".
The only way to make it work on Hardy is to disable the audio capture, there must be a bug when setting "/dev/dsp....".
I searched everywhere to find a solution but nobody have yet found a fix for this problem so I went back to Gutsy which is much more stable then Hardy which looks more like a beta so far.


Livio

---

### Post by leonsmith on 2008-06-26
So why the heck is this thread marked "SOLVED" when it is still very much unsolved ?

Is there any way to escalate this problem ? I am two weeks behind on a project right now because I can no longer use xvidcap, istanbul or gtk-recordmydesktop after upgrading to Heron. Is anyone looing at these issues ? How can I tell ?

---

### Post by dbarbour on 2008-07-02
I'm also interested in resolving this issue with xvidcap Anyone?

---

### Post by dynacrylic on 2008-07-03
I've been trying to get this working as well.

Using:
sudo chmod a+rw /dev/dsp
stopped the crashing in 7.04 but still no audio. Haven't tried it on my 8.04 yet.

---

### Post by nixtux on 2008-07-08
I think the audio capture uses your line in, so if you run PCM to line in perhaps it'll capture?

> **dynacrylic said:**
> I've been trying to get this working as well.

Using:
sudo chmod a+rw /dev/dsp
stopped the crashing in 7.04 but still no audio. Haven't tried it on my 8.04 yet.

---

### Post by nixtux on 2008-07-08
I reverted back to 7.10 because it simply wouldn't work otherwise.

In 7.10 it goes over without a hiccup.  There has to be something in 8.10 that's messed up. 

I also noticed issues with multi-display and compiz, whereas, in 7.10 it runs flawless, albeit, an occasional WM crash but that's easy enough to resolve.

> **leonsmith said:**
> So why the heck is this thread marked "SOLVED" when it is still very much unsolved ?

Is there any way to escalate this problem ? I am two weeks behind on a project right now because I can no longer use xvidcap, istanbul or gtk-recordmydesktop after upgrading to Heron. Is anyone looing at these issues ? How can I tell ?

---

