---
title: "firefox crash on some html5 video while chrome does not"
date: 2015-05-18
forum: Multimedia Software
---

### Post by cosy2 on 2015-05-18
for example ff 38 crashed  when try to play html5 videos even in safemode 

any idea how to fix this ?

edit

the videos play perfectly on chrome 


example of videos that crash [http://clips.vorwaerts-gmbh.de/big_buck_bunny.ogv](http://clips.vorwaerts-gmbh.de/big_buck_bunny.ogv)

---

### Post by ajgreeny on 2015-05-18
Works fine here with FF 38 and flash v 11.2.202.460, though in my FF flash is not being used to view the videos on that site; I think it uses HTML-5.

Check you are HTML5 enabled at [https://www.youtube.com/html5](https://www.youtube.com/html5), which seems to work on other sites as well as youtube.

What hardware have you got?

---

### Post by cosy2 on 2015-05-18
are you sure is not flash related because looks strange hehe 
youtube works fine

if i go to [https://www.youtube.com/html5](https://www.youtube.com/html5)
i got red ! on 
> Media Source Extensions
MSE & H.264
MSE & WebM VP9

---

### Post by sammiev on 2015-05-18
> **ajgreeny said:**
> Works fine here with FF 38 and flash v 11.2.202.460, though in my FF flash is not being used to view the videos on that site; I think it uses HTML-5.

Check you are HTML5 enabled at [https://www.youtube.com/html5](https://www.youtube.com/html5), which seems to work on other sites as well as youtube.

What hardware have you got?

+1 on HTML5

---

### Post by cosy2 on 2015-05-18
[https://crash-stats.mozilla.com/report/index/cf2fb017-5db4-457d-bc6f-501002150518](https://crash-stats.mozilla.com/report/index/cf2fb017-5db4-457d-bc6f-501002150518) here the report

---

### Post by ajgreeny on 2015-05-19
> **cosy2 said:**
> [https://crash-stats.mozilla.com/report/index/cf2fb017-5db4-457d-bc6f-501002150518](https://crash-stats.mozilla.com/report/index/cf2fb017-5db4-457d-bc6f-501002150518) here the report
That does not tell us what hardware you have, I'm afraid.

How much RAM; what CPU; which graphic card and driver (probably nvidia from the report)?

---

### Post by cosy2 on 2015-05-19
why should be hardware a problem ??

i mean the video should run easily on firefox since it runs perfectly on chrome  
geforce 970 8gbram quadcore

---

### Post by monkeybrain20122 on 2015-05-20
Works here.

Start a new profile to see if it works. Close Firefox, then open your home directory, press ctrl+h to show hidden files, find the hidden folder .mozilla and rename it to something like .mozilla-bk and then start firefox and go to to the link again. To revert back, close FF, go to home directory and show hidden files and delete .mozilla and rename .mozilla-bk back to .mozilla.


Edited: the video is in html5, not sure what flash has to do with it..

---

### Post by Bucky Ball on 2015-05-20
Just another confirmation. Faultless here. Xubuntu 14.04 LTS new install (last Friday) and minimal. Firefox 38.

---

### Post by mc4man on 2015-05-20
What's enabled for youtube doesn't quite matter elsewhere (you should be able to get everything green on that youtube page except the last one which doesn't really matter one way or the other  (MSE & WebM VP9

Seems you are playing from this page - [http://camendesign.com/code/video_for_everybody/test.html](http://camendesign.com/code/video_for_everybody/test.html)
What happens if you r. click on the OGG link > Save link as  & then open the downloaded vid, (big_buck_bunny.ogv),  in firefox from wherever you downloaded to, typically your Downloads folder

---

### Post by Naposk on 2015-05-27
I can confirm cosy2 is **not** hallucinating (and neither is their FF crash reporter). I've been having the same problem - Firefox crashing on HTML5 videos - for a couple of months now.

The status page for YouTube's HTML5 check also looks identical (bottom 3 are red). I also doubt this is a (purely) hardware problem, since, again similarly to cosy2's situation, all videos run fine in Chrome.

Here's a crash dump resulting from opening the URL mc4man linked, with a fresh profile, and **all **extensions **and **plugins disabled:
[https://crash-stats.mozilla.com/report/index/bbcf5ca3-56f5-4f61-af2b-f99db2150527](https://crash-stats.mozilla.com/report/index/bbcf5ca3-56f5-4f61-af2b-f99db2150527)

(Note the different thread stack - then again, I have a different graphics driver, and I'm on KDE)

---

### Post by mcduck on 2015-05-28
The link in the first post is not to HTML video (which isn't a format anyway ;)), but a direct link to Ogg Theora video file. (The page where the link is located does use HTML5 video tag to display the same clip in-page, so if you want to test HTML5 video then go to the page, not to the video clip itself).

Youtube uses different video format, WebM, and as mentioned any settings in Youtube won't have anything to do with the playback of the video file in the original post (In fact the Youtube's HTML5 test doesn't even test for the Ogg format since Youtube doesn't use it, making the test completely irrelevant for this thread). Playing back that file is exactly the same as downloading the video clip and opening it on your browser instead of the video player.

...And that is pretty much the pitfall of "HTML5" video, there actually isn't such thing. There's a HTML5 tag for embedding video files on web ages, but the video format (and other related features) supported depends on which browser you happen to be using. 

Anyway, the video clip in question plays fine for me, as it should since support for Ogg Theora video format is built in to Firefox. Problems playing back the video sound more likely a hardware/video driver issue, but of course trying a fresh Firefox profile might be worth doing.

---

### Post by Naposk on 2015-05-28
mcduck: true on the video format front ("HTML5 video" is used as a shorthand, and not only by the OP but also by e.g. YouTube itself), but as already noted:

- the crash **is triggered every time, even with a fresh profile** (at least in my case),
- the problem **does not occur in other browsers** (in both OP's case and mine) so it's **highly unlikely** that a (purely) hardware/driver issue is at play.

---

### Post by VMC on 2015-05-28
"OGV" extension:
[http://www.online-convert.com/file-format/ogv](http://www.online-convert.com/file-format/ogv)

With the following info:
On Webpages, OGV files _are often used to play videos using the HTML5_  < video > tag. Generally, these videos are referenced as being OGG  files in the HTML source even though the underlying file format is OGV.

---

### Post by mcduck on 2015-05-28
the crash report seems to be related to a gstreamer library, and there seems to be some issues with gstreamer and ffmpeg/libav built with certain options.

Have you tried downloading the video clip and playing it from your desktop (using any gstreamer-based media player, for example the default video player on Unity/Gnome)? Or you could try disabling gstreamer in Firefox settings (enter "about:config" in the address bar, search for "media.gstreamer.enabled" and toggle it to "false")

(I'm not using Chrome myself, but it wouldn't surprise me at all if it just brings it's own video codecs with it instead of using gstreamer, which would explain why it can play the video even if Firefox and desktop players crash)

---

### Post by gil-delahousse on 2015-05-29
Bonjour, j'ai le même problème depuis quelques temps avec Firefox, plantage complet ou erreur de script sur les pages html5, pour Youtube il faut savoir qu'il y a eu une mise à niveau vers html5 ce qui rend en plus le navigateur Youtube smplayer complètement osbolète??
Merci pour votre aide si quelqu'un à une solution. Mais il est évident que depuis 1 semaine Firefox n'arrête pas de planter.
Je suis sous Ubuntu 15.04 voilà ma config:

---

### Post by gil-delahousse on 2015-05-29
Voilà en écrivant replantage de Firefox donc ma config** gil-Compaq-CQ58-Notebook-PC , mémoire **3,5 Gio, AMD E1-1500 APU with Radeon(tm) HD Graphics × 2, carte graphique Gallium 0.4 on AMD PALM, OS 64 bits. Merci pour votre aide. Sachant que j'ai essayé avec une version antérieure de Firefox: même problème avec une wifi stable.
Cordialement

---

### Post by Elfy on 2015-05-29
@ gil-delahousse - this forum is English speaking, for support option in French please see [http://loco.ubuntu.com/teams/ubuntu-fr/](http://loco.ubuntu.com/teams/ubuntu-fr/)

ce forum est anglophone, pour l'option de support en français s'il vous plaît voir [http://loco.ubuntu.com/teams/ubuntu-fr/](http://loco.ubuntu.com/teams/ubuntu-fr/)

---

### Post by Naposk on 2015-06-10
> **mcduck said:**
> the crash report seems to be related to a gstreamer library, and there seems to be some issues with gstreamer and ffmpeg/libav built with certain options.

Have you tried downloading the video clip and playing it from your desktop (using any gstreamer-based media player, for example the default video player on Unity/Gnome)? Or you could try disabling gstreamer in Firefox settings (enter "about:config" in the address bar, search for "media.gstreamer.enabled" and toggle it to "false")

[...]

Heh, I wasn't even aware of such an option, **toggling "media.gstreamer.enabled" off has indeed stopped the crashes!** All videos tested so far load and play fine as well. Thank you very much, mcduck!

By the way, I've tried opening the test video in all video players (including Totem), and that played fine - still indicating a Firefox-specific issue. In fairness, I suspect a reason for the problem might be a presence of some legacy AV libs required to run the Spotify client.

Nevertheless, thanks again!

PS. Note that I have unintentionally hijacked this thread, as the OP's (cosy2) crash report does not indicate an immediate problem with gstreamer.

---

