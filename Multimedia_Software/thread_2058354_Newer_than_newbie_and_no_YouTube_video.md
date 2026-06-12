---
title: "Newer than newbie and no YouTube video"
date: 2012-09-15
forum: Multimedia Software
---

### Post by redsand on 2012-09-15
My first attempt w/Linux and so far I'm excited but frustrated with all the new terminology. I'm running  12.04 LTS on an older  Athlon 1800 and Radeon 9200 ATI AGP dual monitor board.  I don't use the VGA at all just the DVI output. From what I've read I get my old board is kinda wonky and doesn't play nice with Linux so please be kind.  Youtube I get a black box for video and that's it.  I plunked in a DVD and it won't play anything.  Sound  works fine and no audio problems. Screen Res is 1680x1050 and photos look good so everything but videos. 
Anyone have a clue what's up here?

RS

---

### Post by oldos2er on 2012-09-15
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) has information about installing flash and other codecs, etc.

---

### Post by redsand on 2012-09-15
Thank you for the link to more info but I have to admit I'm still lost here.  I've installed all the restricted software. DVD now works with VLC but still I have a black box where videos usually play on YouTube. I'm needing a step by step to narrow down if this a hardware or software thing.  I'm assuming it's software or driver as it all works fine using Win XP so? Now I noticed an error when I attempt to stream a radio station " shockwave crash" reported. This is getting complicated..

What to check next?
Thanks in advance.
RS

---

### Post by dniMretsaM on 2012-09-15
If you're using Firefox, check out [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/?src=ss). It will install the right flash player for your system. Also, you can join opt to join [URL=https://youtube.com/html5]YouTube's HTML5 program (which I like a lot, personally).

---

### Post by MrsUser on 2012-09-15
Google "things to do after installing ubuntu 12.04" and you get lots of good instructions.

---

### Post by redsand on 2012-09-15
Seems I'm missing something here.  Thanks to those that responded. Still no streaming audio or video.

---

### Post by dniMretsaM on 2012-09-15
> **redsand said:**
> Seems I'm missing something here.  Thanks to those that responded. Still no streaming audio or video.

What have you done so far?

---

### Post by oldos2er on 2012-09-15
> **redsand said:**
> Thank you for the link to more info but I have to admit I'm still lost here.  

What browser are you using? Also what video card do you have?

---

### Post by redsand on 2012-09-16
I have a AGP Radeon 9200 Pro using the DVI  output and the VGA is not used.  I've tried everything suggested in the responses  above.  It all looks like it's working but noaudio or video from a stream. I did manage to get the DVD to play using VLC so I accomplished something. 

I've been using Firefox for years with XP and know my way around pretty well there. I installed Chrome as well just to see if maybe the browser was a problem but the same results.

Got to be something simple I've missed but I'm not sure where to go next.

RS

---

### Post by oldos2er on 2012-09-16
Have you tried installing proprietary drivers for your video card? ```
jockey-gtk
```

In Chrome, open chrome:plugins, and check that it's using Pepper Flash (libpepflashplayer.so) and not libflashplayer.so

---

### Post by redsand on 2012-09-16
Yup. Pepper flash.  On YouTube it reports "Missing Plug-in" using Chrome.  It also asks for permission to which I respond "Always Run" and it ignores me :mad:

I'm now well over a day and a half just to test drive this Linux thing and I must admit this is way more trouble than I ever expected.  I'm leaning towards a hardware issue here or? My experience with Mint and Mageia about the same. 

Just venting a bit here and thanks for all that have contributed. 
Discouraged.
RS

---

### Post by oldos2er on 2012-09-16
Sorry you're having so many problems with this. Flash on Linux can be a pain, but usually it's not this bad.

---

### Post by redsand on 2012-09-16
Sometimes it's good to just stop and take a deep breath.  Maybe I'll look in the retired video board box and see if I can find one Flash likes better.  What flavor plays nice in the sand box with Ubuntu... anyone?

Thanks Ann
RS

---

### Post by redsand on 2012-09-16
Something is very fishy here. I plugged in an old Nvidia Gforce board and low and behold same deal. No flash video. In Chrome it just says missing plug-in.  I can't be the only Linux Dummy around having this problem can I?

:mad:

---

### Post by BicyclerBoy on 2012-09-16
The developer of flashvideoreplacer has withdrawn that plugin.

What did work:
adobe shockwave flash plugin still works (ubu 11.10 firefox) but it is history on linux (adobe).
flashvideoreplacer is on-hold/removed from firefox add-ons (still available in synaptic as gecko-mediaplayer).
It used to work..

Now it seems the flashvideoreplacer does not work with flv video & stops the other plugins working.

You might want to disable all plugins except shockwave & then try youtube..
The other plugins (vlc totem gecko) could all be the problem.

There are different video types avail from youtube; html5(webm) & flv.
You can opt-in to the html5 trial.
The html5 (webm) videos work well in firefox but unfortunately there are very few videos available in this format.
(add &webm=1 to search)

Alternative for flv:
- Don't bother.
- keep using shockwave until it fails.
- make google pepper api work in chrome browser
- use terminal program "quvi" & mplayer. (this works).

This may still work..
[http://ubuntuforums.org/showthread.php?t=1976503](http://ubuntuforums.org/showthread.php?t=1976503)

---

### Post by contributor on 2012-09-17
[FONT=Arial]You have already received a lot of good suggestions from the experts. But still, I want to add one more in this list. You can search it on google by using this keyword "[/FONT][FONT=Arial][SIZE=2]To Do List After installing Ubuntu 12.04"[/SIZE][/FONT][FONT=Arial]. I am not sure but may be it can help you. Good luck.[/FONT]

---

### Post by SeijiSensei on 2012-09-17
1) In Firefox go to Tools > Add-Ons > Plugins.  Is the "Shockwave Flash" plugin installed and not marked as disabled?  Is it 11.2 r202, the current version?

2) The easiest way to install Flash is to use the partner repository.  Try this:

a)  Use "sudo nano /etc/apt/sources.list" to edit the list of repositories.  Find this line: 
```
deb http://archive.canonical.com/ubuntu precise partner
```
and remove the hash mark ("#") at the beginning of the line if it is there.  Type Ctrl-X, then say Y when prompted to save the file. (If you are using an older version of Ubuntu, "precise" will be replaced with something like "oneiric" or "lucid".

b)  Now run 
```

sudo apt-get update
sudo apt-get install adobe-flashplugin

```

Any better?

---

### Post by redsand on 2012-09-17
I wish to thank everyone that responded and tell you all this was overwhelming (almost).  I watched my first YouTube video this morning and thanks to the help here I've had quite an education on Linux. How to run terminal, shortcuts, and like Edison found fifty or so things that didn't work at all.  The terminology more than anything was Gnawing at my pea brain but I've managed and now am only half lost.
The HTML5 that YouTube offered seems the only solution at this point but I'll continue to explore a fix that will work on other sites. I'm still without audio from streaming radio but I'll stay at it. I'm very impressed with easy of Ubuntu and if not for the flash glitches pretty painless but I'm not ready to give up XP just yet but I'm at least thinking about it. 
My compliments to the chefs and all the help.

RS

---

### Post by BicyclerBoy on 2012-09-18
This ain't pretty but it works..

[http://ppcluddite.blogspot.co.nz/2012/09/yet-another-flash-alternative.html](http://ppcluddite.blogspot.co.nz/2012/09/yet-another-flash-alternative.html)

Use it until you get a cleaner soln working..
You can wrap the cmd line up in a script to make it easier re-use..

---

