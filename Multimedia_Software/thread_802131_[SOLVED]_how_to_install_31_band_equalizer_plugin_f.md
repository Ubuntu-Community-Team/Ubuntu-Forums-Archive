---
title: "[SOLVED] how to install 31 band equalizer plugin for Audacious in hardy?"
date: 2008-05-21
forum: Multimedia Software
---

### Post by ramkumail on 2008-05-21
Hi,
 I would love to have 31 band equalizer plugin (listed on audacious page in effects plugins section) installed. [http://audacious-media-player.org/index.php?title=Plugins](http://audacious-media-player.org/index.php?title=Plugins). the audacious plugins extra package in repos does not seem to have this plugin. Can anyone tell me how to install this plugin for audacious 1.5 that is shipped with ubuntu. The guides out there say that it does not work with recent versions though they point to a plugin file that works with older versions.

---

### Post by ramkumail on 2008-05-22
bump

---

### Post by vprasaj on 2008-05-23
I was looking for this too... I realy miss it, couse buildin won't do the job for my sound system.

Older versions of eq-audacious are [HERE]("http://packages.gentoo.org/package/media-plugins/eq-audacious"). But i couldn't get it work. Compiled libeq.so (i think so) file is not recognized by audacious. 

From developers page: [HERE]("http://www.nenolod.net/audacious#effectplugins")
> eq-audacious-ng: eq-audacious-ng is a new version of the eq-audacious plugin. It has been rewritten not to use skins, as this simplifies the codebase and allows for concentration on the important part, which is the EQ. No public releases yet, look back around Audacious 1.4.0 beta1.

---

### Post by ramkumail on 2008-05-25
Thanks for the reply vprasaj. I have requested the developer for plugin for audacious 1.5. lets see how it goes. Hope he upgrades the plugin and help us hear some good quality sound.

---

### Post by vprasaj on 2008-05-27
That would be nice.

In the mid time you can use 2 equalizers from LADSPA plugins. Install packages tap-plugins and fil-plugins. Then you enable LADSPA host (properies->plugins->effects) in audacious. Then hit configure. You will find two equalizers and one 4-band parametric filter(i use this one). Add one or more and than you can adjust it to your needs. It is not hard to do it. Just be careful with gain to awoid clipping.

Good luck.

---

### Post by ramkumail on 2008-05-27
Thanks vpsraj. I have successfully installed. I just need to play with them now but the installation gives large number of options. Is there some kind of help available somewhere which ones are for what. If it is there please provide them so that I as well as others who follow this thread later have ease in configuring them.

I have attached scrrenshot of what i get after installing the plugins just to ensure i have done my installation correctly.
[[IMG]http://img91.imageshack.us/img91/3690/ladpsagk5.th.jpg[/IMG]](http://img91.imageshack.us/my.php?image=ladpsagk5.jpg)

---

### Post by vprasaj on 2008-05-28
You have the all the right things. Now you can add any of those plugins to the right side and then config them.

I will describe my case. You must know, that your speakers are different then mine, so the configuration will not be the same at all. I have those genius home theater speakers with 2 added 20 cm woofers parallel connected to woofer (this are wires). I did this because i like kick drum in rock or any other music. Amp is only 50W for woofer, but it keeps living... (just... amp is a little hot... hehe). My 2 added woofers have self frequency at 120Hz and strange resonance at 170Hz. This was my problem. I had to lower sound at those frequencies because it was thumpy. (Sometimes strong bass is not a clear bass) I had to gain really low frequency (20-60Hz) because speakers are not meant for this system.

OK, why and what i did...

I have always this in mind.

[IMG]http://www.duke.edu/~jak21/range.jpg[/IMG]

What the heck is this? Well it is just a response of our ears to sound. So what does it mean? Lower curve is a limit to hear anything at all (like from no sound to whisper). Higher curve represents where we feel pain in our ears (standing near jet engine or pneumatic hammer). Horizontally is the frequency(logarithm scale), vertically is sound level(log. too). You can see that we can hear in range between 20Hz to 16500Hz (16,5kHz). Over 16,5kHz most of us don't hear (this is getting lower by aging process). We don't hear anything below 20 Hz eather, but sometimes we can fell those vibrations with some strong sound system.
My speakers go down to 30Hz and up over 16,5kHz.

But we hear best around 2kHz to 5kHz.(according to graph.. someone can correct me if i'm wrong... )

So what we try to do?

We try to get maximum bass, the right mid tones and not too much high frequency.
The sound must be clear.

First you have to find out what should be corrected.
You can play with the equalizer and filter to make it sound like you want it.

If you want more science approach, then get some tone sinus generator.
I use this one: [LINK to Tone Generator]("http://www.nch.com.au/tonegen/index.html")
It's shareware.
Use wine to install. 
When it is installed correct shortcut command (add padsp) if you use pulseaudio.
```
env WINEPREFIX="/home/yourusername/.wine" **padsp** wine "C:\Program Files\NCH Swift Sound\ToneGen\tone.exe"
```
In this program you can generate sinus sounds. You must have heard one of this sounds before (car shows, audiophile tests). You can generate really low-fi like 20Hz to 20kHz(hi-fi).
This can help you find the frequency bands where the sinus sound is too loud or too quiet. When you find that out you simply adjust your equalizer or filter. There are some devices for this too, but we won't talk about those.

This is just a short description how sound works in "my way".

When you add a plugin in LADSPA like 4 band parametric filter (sometimes you have to click "add" and "configure" twice for some reason...), you can see, that you can adjust frequency, gain, and band. That's all you need.

You remember "too loud and too quiet bla, bla...". Change to that frequency then play a little with gain (amp) and bandwidth(how wide it works-it goes up and down from that frequency). Don't forget to press the button "press" for filter and the bands you use. You can hear change instantly. Practically it is 4 band eq, but far more advanced then any other in linux (i couldn't find one better yet).

Remember: 1st freq have range from 20-2000Hz, 2nd has 40-4000, 3rd...
Use 1st and 2nd for bass, 3rd for midtones and 4th for hi-fi.
It's almost the same for TAP equalizer. I didn't need it (try it, its great). But i use buildin eq for easy access when bass is too loud in some songs and simply fits at 170 +- Hz for my woofers. You can add as many filters as you want and use buildin eq at the same time. It works.
You can see my settings below. 
[[img]http://shrani.si/t/1m/kS/4PCyfVpw/audacious.jpg[/img]](http://shrani.si/?1m/kS/4PCyfVpw/audacious.png)

But again, my sound system is different then yours. The best result is when you are happy with your sound. You just have to find your right settings by yourself. That means play a little with options. But don't use too much gain. If you do, you will hear clipping sound (cuts away peaks, sound is horrible). When clipping appears lower gain or main gain in filter or in buildin eq. Improvise.

*I hope this have some sense what i wrote...*:-({|=

And sorry for my english...:-\" i don't use it every day.

Good luck and enjoy the music.[[img]http://www.freesmileys.org/smileys/music028.gif[/img]](http://www.freesmileys.org) [[img]http://www.freesmileys.org/smileys/music022.gif[/img]](http://www.freesmileys.org)  [[img]http://www.freesmileys.org/smileys/music021.gif[/img]](http://www.freesmileys.org)

---

### Post by ramkumail on 2008-05-28
Thanks Vpsraj. You have made this thread a really useful guide. It sounds great with the modifications. I am very happy now. This is something I was longing to have right from the time i switched to linux. Thanks for your time and effort. We as well have a common taste, both of our conky look the same.

---

### Post by vprasaj on 2008-05-28
I'm happy if you find my post useful. It's great that you opened this thread. I simply didn't remember to do so.
BTW I find out this when I switched from audacious 1.4 to 1.5. Before that eq-audacious worked.
I have to dig for some time to find out solution for my music sound and it was in front of my nose all the time.:^o#-o
Now I'm \\:D/[-o< !!!

Oh, yes... Conky is that one little thing that I really like.

Cheers.[[img]http://www.freesmileys.org/smileys/eatdrink004.gif[/img]](http://www.freesmileys.org) [[img]http://www.freesmileys.org/smileys/eatdrink003.gif[/img]](http://www.freesmileys.org) [[img]http://www.freesmileys.org/smileys/eatdrink001.gif[/img]](http://www.freesmileys.org) [[img]http://www.freesmileys.org/smileys/eatdrink007.gif[/img]](http://www.freesmileys.org)

---

