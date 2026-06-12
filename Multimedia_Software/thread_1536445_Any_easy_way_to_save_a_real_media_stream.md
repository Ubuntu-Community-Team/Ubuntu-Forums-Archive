---
title: "Any easy way to save a real media stream?"
date: 2010-07-22
forum: Multimedia Software
---

### Post by Anuovis on 2010-07-22
I know this is possible but I have already tried 5 threads about this topic and they have gotten me nowhere. It is always something like "download these 3 plugins, type a few miles of text in the terminal..." which I do not mind but every time something went wrong and I could not get the stream saved. 

The closest one to success was saving some 95% of the file which took a lot of time and then the procedure got stuck or froze. Sad thing is that I do not remember which of those thread has gotten me this far. In any case, I tried to follow the instructions letter by letter several times (to double check any typing errors and such) and still no luck.

Right now I am tired of browsing for countless plug-ins and typing things in the terminal that do not work. Is there a simple and reliable method (GUI preferable but not necessary) for 10.04 to accomplish this?

---

### Post by ron999 on 2010-07-22
[B]Any easy way to save a real media stream?
[/B]

It depends where you're trying to save it from.

---

### Post by Anuovis on 2010-07-22
From the net. I have the URL and I can download the .ram file.

---

### Post by hansdown on 2010-07-22
Hi Anuovis.

In firefox, click tools> addons> get addons.

Search for 

```
xine plugin

```


This will help stream from the web.


Also, in ubuntu, click system> administration> synaptic package manager.

Search for 

```
gxine
```

---

### Post by Anuovis on 2010-07-22
Hansdown, I installed both of them through Synaptic. But how can I save the actual stream to my HDD now?

---

### Post by hansdown on 2010-07-22
> **Anuovis said:**
> Hansdown, I installed both of them through Synaptic. But how can I save the actual stream to my HDD now?

In firefox, click tools> addons> get addons.

Search for downloadhelper.

---

### Post by Anuovis on 2010-07-22
You meant this one?
 [https://addons.mozilla.org/en-US/firefox/addon/3006/](https://addons.mozilla.org/en-US/firefox/addon/3006/)

I can't see anything named exactly as "downloadhelper", there are a few addons with that as part of their name.

In any case, what you mean is that one can save the real media stream by using a proper addon for Firefox? Is it possible?

---

### Post by hansdown on 2010-07-22
> **Anuovis said:**
> You meant this one?
 [https://addons.mozilla.org/en-US/firefox/addon/3006/](https://addons.mozilla.org/en-US/firefox/addon/3006/)

I can't see anything named exactly as "downloadhelper", there are a few addons with that as part of their name.

In any case, what you mean is that one can save the real media stream by using a proper addon for Firefox? Is it possible?

Yes, sorry about that.

When it is installed, it just says Downloadhelper.

When you search for it, you need to search for video downloadhelper.

It will save that media,** if**  you also install 

```
xine plugin
```

from firefox.

---

### Post by Anuovis on 2010-07-23
Thank you for the replies.

I have the download helper add-on but not sure about the xine. What I found and installed is called *gxine starter plugin*. Is that it?

Also I can associate it to some of the file types and it seems to work (tested mp3 stream). Some external(?) player is launched that then plays it. 
However, I have no option to associate it with real media in Firefox - no entry in the drop down menu for that file type (see the screenshot).

Am I going in the right direction?

And do you know why xine can not be set to play real streams? I have checked Mozilla documentation but it seems all the available plug ins should show there automatically. Do I  need to add it somehow?

---

### Post by andrew.46 on 2010-07-24
Hi Anuovis,

Can you give an address of one of the streams you are trying to capture?

All the best,

Andrew

---

### Post by Anuovis on 2010-07-24
Sure. Here it is:
[http://www.bbc.co.uk/radio4/reith/historic_audio/ram/russell_1948.ram](http://www.bbc.co.uk/radio4/reith/historic_audio/ram/russell_1948.ram)

---

### Post by mc4man on 2010-07-24
A rather basic/crude way (assuming your mplayer can play the stream - 
saving to blue in home folder (change name if desired

I'm sure others can refine greatly for you....

```
mplayer rtsp://rmv8.bbc.net.uk/radio4/reith/russell_1948.rm?BBC-UID=041cd4ab41e628e57037a398f1142502b3a101f62080220122c8d064930c2018_n -dumpstream -dumpfile [COLOR="Blue"]russell_1948.rm[/COLOR]
```

---

### Post by ron999 on 2010-07-24
Hi
To follow on from **mc4man**.
Download the ram file and inspect it in a text editor.
With this BBC file you only need the part before the question mark.
This is:- [B]rtsp://rmv8.bbc.net.uk/radio4/reith/russell_1948.rm
[/B]
To download it with mPlayer you can use this command:-
```
mplayer rtsp://rmv8.bbc.net.uk/radio4/reith/russell_1948.rm -dumpstream -dumpfile russel.ra -bandwidth 999999999999 -ao null

```
You'll end up with a 4.6MB file named **russel.ra** in RealAudio format.

---

### Post by mc4man on 2010-07-24
The bandwith option is a good idea ( had just tried it, used 1000000, don't know what the difference is, if any)

Anyway it greatly increases the 'record' speed

If you have any connection issues then add a -cache 2048 to command

---

### Post by Anuovis on 2010-07-24
Thank you very much. It worked.

I remember trying something very similar from another thread and I guess I gave up because it threw a bunch of errors at me and was taking quite a bit of time.  Thanks to anyone who contributed to this thread.

Anyway, just out of curiosity, are these important?

```

MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
```

---

### Post by mc4man on 2010-07-24
> Anyway, just out of curiosity, are these important?

Not at all

---

### Post by andrew.46 on 2010-07-24
Hi Anuovis,

As mc4man has mentioned this is not anything to worry about but it is annoying nevertheless. It refers to Linux Infrared Remote Control (hence LIRC) and details are here:

[http://www.mplayerhq.hu/DOCS/HTML/en/control.html](http://www.mplayerhq.hu/DOCS/HTML/en/control.html)

and of course you can spend some time setting it all up if you actually happen to have one of these devices. If you don't I believe you can turn off the message by adding either *nolirc = yes* or *lirc = no* in your $HOME/.mplayer/config file, I will admit that I cannot remember exactly which one is correct and perhaps both will work :).

All the best,

Andrew

---

### Post by Anuovis on 2010-07-24
I will keep that in mind. Thanks for all the help, I can finally listen to those streams with my mp3 player. Woot :)

---

### Post by mc4man on 2010-07-24
> perhaps both will work

mplayer will quite kindly accept either (if using. no spaces

---

### Post by Despot Despondency on 2010-07-25
Hi, 

How do you find the RAM files on bbc radio 4 website? I've been trying for ages but I can't find out how to get them.

cheers

---

### Post by Anuovis on 2010-07-25
> **Despot Despondency said:**
> Hi, 
How do you find the RAM files on bbc radio 4 website? I've been trying for ages but I can't find out how to get them.


It depends. Some of the broadcasts might not be available as ram files. Just look around the site for *Listen to* or buttons/links of that sort. You then will get the .rm file which you can use to stream the program or... you can open it with a text editor and look for the real source of the stream. This method was proposed in this thread, take a look.

If you can find a podcast, then you simply download that and get a full audio file.

---

### Post by Despot Despondency on 2010-07-25
Thanks for the quick response. I think it is not possible to get the RAM file of the program I want. Nevermind. Cheers.

---

