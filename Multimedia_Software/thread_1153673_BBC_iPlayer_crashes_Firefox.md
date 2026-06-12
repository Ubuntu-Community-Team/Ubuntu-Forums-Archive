---
title: "BBC iPlayer crashes Firefox"
date: 2009-05-09
forum: Multimedia Software
---

### Post by rogerdean on 2009-05-09
Hello all

I find that iPlayer radio pages such as this one...

[http://www.bbc.co.uk/iplayer/episode/b00k4g55/4_Stands_Up_Series_3_Episode_6/?src=a_syn30]("http://www.bbc.co.uk/iplayer/episode/b00k4g55/4_Stands_Up_Series_3_Episode_6/?src=a_syn30")

...crash and close Firefox every time. I'm running Jaunty with mozilla-mplayer, and flash from ubuntu-restricted-extras. Funny thing is everything works perfectly in Mint 7 RC. Out of the box, too...

Anyone got any ideas? If you'd like the output code just let me know how to get it and I'll post

Many thanks indeed!
Roger

---

### Post by xc3RnbFO8P on 2009-05-09
Start Firefox in Terminal:
> firefox
and show output of error message if any.

---

### Post by rogerdean on 2009-05-09
Thanks! Here it is...

```
roger@roger-laptop:~$ firefox
Segmentation fault
roger@roger-laptop:~$ 

```

---

### Post by evanrmurphy on 2009-05-09
I had a very similar issue on Hardy every time I went to [www.colbertnation.com]("http://www.colbertnation.com"). I filed a [bug report]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/351379") on it, but was informed that my version of Firefox was outdated, so you might want to check that. The problem disappeared when I upgraded Ubuntu, first to Intrepid and then later to Jaunty.

---

### Post by kay-man on 2009-05-09
Well, I can confirm this exact behaviour Kubuntu Jaunty with firefox 3.0.10. I tried firefox safe mode as well - no difference.

Konqueror crashes as well, with an error in nspluginviewer.

The only thing I found that does work is opening the link directly in VLC, which will play it.

---

### Post by kay-man on 2009-05-09
It sort of works with the MediaPlayerConnectivity plugin, which you can instruct to open real media in an external player, e.g. vlc.

The error seems to be in the flash plugin. Not sure what that means and where to go with your bug report. Have you tried a completely different browser, for example opera?

---

### Post by rogerdean on 2009-05-09
Thanks for the input. Opera gets a bit further, at least sometimes showing the program picture. But there's no sound and no player controls. Flash again?

Will have a go with MediaPlayerConnectivity...

Cheers
Roger

---

### Post by iamboredr on 2009-05-09
That a drag of coming from firefox wow it really needs fixing

---

### Post by rogerdean on 2009-05-09
MediaPlayerConnectivity works a treat, thanks paulklos!

---

### Post by Knacker_Ned on 2009-05-09
I was having problems watching BBC iplayer videos from within Firefox. Discovered that Firefox was trying to play videos using the swfdec decoder/renderer instead of Flash. So I uninstalled swfdec and now Firefox and Flash handle iplayer videos with no problems whatsoever.

---

### Post by andy17 on 2009-05-13
Hi mates,

I got the same problem: opening BBC iplayer crashes FF.
I'm running KUBUNTU Jaunty AMD64 and I tried to install:

FLASH
JAVA
MediaPlayerConnectivity
MPlayer
RealPlayer (from .deb)

I guess I tried every combination of these but without results!

Any suggestions?

ps: opening radio streams with VLC via MediaPlayerConnectivity works, but after 1'21'' it always stop, no metter what stream I try to play!

---

### Post by Stenico on 2009-05-14
Updating flash from version 9 to 10 solved this for me:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

I installed the deb for Ubuntu 8.04+

s.

---

### Post by neolnxist on 2009-06-07
I'm also having problems listening to the BBC radio with iPlayer. The screen flashes up for a second and as soon as any content arrives FF crashes.  I upgraded to 9.04 recently but it was working fine in 8.10.

I've tried all the suggestions on the forum boards but with no luck.  Is this a problem with FF or the BBC end of things?  I would appreciate any advice.  Thanks very much.

---

### Post by candtalan on 2009-06-12
> **neolnxist said:**
> I'm also having problems listening to the BBC radio with iPlayer. The screen flashes up for a second and as soon as any content arrives FF crashes.  I upgraded to 9.04 recently but it was working fine in 8.10.

I've tried all the suggestions on the forum boards but with no luck.  Is this a problem with FF or the BBC end of things?  I would appreciate any advice.  Thanks very much.

same problem here although I have two machines and one crashes any time I try ff with bbc radio playing live, the other is ok. Trying to sort something out here. 
I am using the flash plugin from the repos

---

### Post by candtalan on 2009-06-12
> **kay-man said:**
> The only thing I found that does work is opening the link directly in VLC, which will play it.

I have tried but cannot get any success with trying to find the url in th ebbc pages (source)

---

### Post by candtalan on 2009-06-12
Maybe a related problem:
I can play bbc live radio using firefox (flash based), however, it looks as if *all* bbc 'listen again' broadcasts are now coming up with a notice that realplayer has to be installed first!

for example
[http://www.bbc.co.uk/iplayer/console/b007k4kd](http://www.bbc.co.uk/iplayer/console/b007k4kd)

fwiw, I went as far as actually installing Realplayer (!)
guess what? It did not work, so that is not the problem.

This is bad news. 
Help!?

---

### Post by ajgreeny on 2009-06-12
For those who have had problems with **mozilla-mplayer** plugin crashing on BBC Radio I suggest you uninstall the mozilla-mplayer and install the **gecko-mediaplayer**.  I had exactly this problem with 9.04 and it was so frustrating not being able to use the feeds in firefox, and having to use mplayer or gnome-mplayer as stand-alone apps.  Apple trailers for quicktime movies also crashed the plugin and both the BBC and trailers gave no useful terminal output other than Segmentation fault.

I now understand that this is a known bug of the mozilla-mplayer plugin in 9.04, so try gecko-mediaplayer, as I did.  I've now got my BBC Radio back where it should be, thank goodness!

---

### Post by rogerdean on 2009-06-12
Magnificent. Thank you so very much for that!

---

### Post by candtalan on 2009-06-13
> **ajgreeny said:**
> For those who have had problems with **mozilla-mplayer** plugin crashing on BBC Radio I suggest you uninstall the mozilla-mplayer and install the **gecko-mediaplayer**.  I had exactly this problem with 9.04 and it was so frustrating not being able to use the feeds in firefox, and having to use mplayer or gnome-mplayer as stand-alone apps.  Apple trailers for quicktime movies also crashed the plugin and both the BBC and trailers gave no useful terminal output other than Segmentation fault.

I now understand that this is a known bug of the mozilla-mplayer plugin in 9.04, so try gecko-mediaplayer, as I did.  I've now got my BBC Radio back where it should be, thank goodness!

It works great!
Thank you!!

---

### Post by joejk2 on 2009-06-25
Wonderful - thanks!

---

