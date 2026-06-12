---
title: "Unable to listen to streaming audio"
date: 2007-07-04
forum: Multimedia &amp; Video
---

### Post by gibsonman on 2007-07-04
I love unbuntu..except that I can't listen to streaming audio...I've installed the codecs, software...but still cannot listen...


here is a site that I listen to : [www.kfi640.com/pages/streaming.html...can](www.kfi640.com/pages/streaming.html...can) some one check this out and help me...thanks

---

### Post by moore.bryan on 2007-07-04
*it worked for me.  what browser are you using?*

---

### Post by gibsonman on 2007-07-04
firefox.....how are you able to listen?

---

### Post by moore.bryan on 2007-07-05
*i just go to the page and listen.  have installed ALL the media codecs?*

---

### Post by Gremlinzzz on 2007-07-05
Which plugin are you using?
What i have too do to setup mplayer first i uninstall totem and its plugin.
then i get the deb package for smplayer [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/) plays my dvd movies.
Then i install mplayer plugin using synaptic package manager.
now for the codecs paste commands in terminal
[https://help.ubuntu.com/community/Re...t=%28codecs%29](https://help.ubuntu.com/community/Re...t=%28codecs%29)
now thxs to this forum i add divxs plugins to watch divxs online
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
last but not least i test mplayer plugin at [http://www.hogsbreath.com/hogcam/](http://www.hogsbreath.com/hogcam/)
if its gray i config the settings by right clicking the video window and choose X11 video &ALSA audio
Thats it and it works great i can watch dvd movie cds and divxs movies and streaming video.
these are the setup tweaks i learned for mplayer i could not find tweaks that match em for totem.

---

### Post by moore.bryan on 2007-07-05
*i only have flash and java plugins; mplayer isn't even installed.*

---

### Post by gibsonman on 2007-07-05
I have the mplayer plug-in for firefox, also VLC....I'll uninstall them and follow your instructions...thanks

---

### Post by gibsonman on 2007-07-07
Still doesn't work....can you give me a step by on how to make it work...windows XP works fine...I really want to quit using windows however linux seems to NOT be as user friendly unfortunately...it shouldn't be that hard to listen to streaming audio

---

### Post by sdowney717 on 2007-07-07
I am using mplayer plugin and it works. I hear the stream fine.
Do you have real player installed?
I do not.
I can also use mplayer plugin to play real audio. Which I was unable to do before.

---

### Post by sdowney717 on 2007-07-07
It comes over as an mp3 file. If you cant hear mp3 then might be the way to fix it.

---

### Post by sdowney717 on 2007-07-07
[http://www.kfi640.com/pages/KFInews1.MP3](http://www.kfi640.com/pages/KFInews1.MP3)

---

### Post by xc3RnbFO8P on 2007-07-07
this is the codec I have install and all works for me

---

### Post by gibsonman on 2007-07-07
I have the mplayer movie player.....is this the right one...if so how do you configure it?

---

### Post by gibsonman on 2007-07-07
also if its a live stream how are you listening it as a MP3 file.......

---

### Post by moore.bryan on 2007-07-08
*i have xine installed, with all the extra codecs, and the firefox [multimediaplayerconnectivity]("https://addons.mozilla.org/en-US/firefox/addon/446") extension to direct the stream to xine.  in theory, you could have it direct to any of your players.*

---

### Post by sdowney717 on 2007-07-08
Ok, I found the live streaming link.
It loads a smaller page 
Then the mplayer plugin starts loading the stream for about 30 seconds and then it starts talking

So you can use mplayer plug in for the broser which then loads mplayer to play the stream.
You can install these thru synaptic.

You may also have to set the about:config parameters, I dont know if this is an mms stream which firefox does not know how to handle. In which case you have to tell it in about:config

---

### Post by sdowney717 on 2007-07-08
Well, I just looked and I dont have it set in about:config
So maybe you dont anymore, but I used to have to do this for cnn video.

This does mention this for mms streaming

[http://ubuntuforums.org/showthread.php?t=378939&highlight=network.protocol-handler.external](http://ubuntuforums.org/showthread.php?t=378939&highlight=network.protocol-handler.external)

---

### Post by gibsonman on 2007-07-08
How do I configure mplayer?

---

### Post by xc3RnbFO8P on 2007-07-08
> **Ringi said:**
> this is the codec I have install and all works for me

I should have tried it first, nothing is working. I have taken screenshots of VLC player when I tried play stream from denmarks radio. Look at the info bar. At first it start conecting to
[http://wmsc.dr.dk/wmcontentbitrate=3000000](http://wmsc.dr.dk/wmcontentbitrate=3000000) after 5 sec. it change to
mms://192.168.16.8:80/e02ch01m?wmcontentbitrate=.asf
and its quits.
Firefox starts totem but nothing happens.
I have installed "mediaplayerconnectivity" in firefox, but it does not work.
I have check  all codec I can play mp3 files.
I have a router, I have not made no changes there.
I got a update to "Ktorrent"  if its means something.

---

### Post by sdowney717 on 2007-07-08
mplayer plugin installed thru synaptic is already configured

But you can configure it by right clicking the browser plugin

---

### Post by sdowney717 on 2007-07-08
here is synaptic showing mplayer and the codecs

---

### Post by gibsonman on 2007-07-09
did it still no sound...

---

### Post by moore.bryan on 2007-07-09
> **Ringi said:**
> I have installed "mediaplayerconnectivity" in firefox, but it does not work.
[i]check to make sure the mediaplayerconnectivity extension is being told to load the appropriate program.  you then have to actually click on the little black screen presented to you.
i do it this way: i've installed xine-ui, libxine1, libxine-extracodecs, and firefox's mediaplayerconnectivity extension.  in screenshot 1, it's the page in xmradio where you choose your station.  screenshot 2 show the change in the playing bar when you choose a station (i circled it red).  screenshot three shows xine loaded and playing the stream.  now, it took about 5 seconds for xine to figure-out how to handle the stream, but that's a short time to actually wait for this thing to work.  :-)[/i]

---

### Post by xc3RnbFO8P on 2007-07-09
I got all codec and libs, if you look at the screenshots, why is VLC player trying to connect 192.168.16.8:80

---

### Post by moore.bryan on 2007-07-09
[I]@ringi...
i may have found, somewhat, of an answer for you.  it seems after searching google a little bit, i came up with [this]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2005-January/050735.html").  it seems it's in wma9, but there is another [thread]("http://ubuntuforums.org/showthread.php?t=270066&highlight=wmv9&page=4") which seems to have gotten a similar site working; maybe that fits what you need it to?
[/I]

---

### Post by xc3RnbFO8P on 2007-07-10
> **moore.bryan said:**
> [I]@ringi...
i may have found, somewhat, of an answer for you.  it seems after searching google a little bit, i came up with [this]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2005-January/050735.html").  it seems it's in wma9, but there is another [thread]("http://ubuntuforums.org/showthread.php?t=270066&highlight=wmv9&page=4") which seems to have gotten a similar site working; maybe that fits what you need it to?
[/I]

I check it, here is screenshot mplayer error.

---

### Post by moore.bryan on 2007-07-10
[I]i don't know if you've seen [this post]("http://www.linuxquestions.org/questions/showthread.php?t=239176"), but it may lead to some answers as well.  i also don't know if vlc has the -playlist option.  i just visited wmsc.dr.dk now, swiftweasel detected the stream, and mediaplayerconnectivity extensions played the stream fine in xine.  this is a really strange error, but not one that seems to be all that uncommon when one googles the problem.
the AF_INET6 thing refers to something on the page (perhaps the stream itself) designed for ipv6 and according to the online docs.  it seems one work-around may be to add ```
prefer-ipv4=yes
``` to either your ~/.mplayer/config or /etc/mplayer/mplayer.conf file.  let me know if it works...
[/I]

---

### Post by xc3RnbFO8P on 2007-07-10
I found this in forum [URL="http://ubuntuforums.org/showthread.php?t=270718&highlight=remove+ipv6&page=2"]http://ubuntuforums
.org/showthread.php?t=270718&highlight=remove+ipv6&page=2[/URL]


Here is a very simple solution that worked for me, running AMD 64 Ubuntu 6.06 64, if you are on adsl pppoe and don't need ipv6. This does not remove but disables ipv6. Don't remember link where I found this, was just running through a bunch of things and writing down the solutions. In **Firefox type in "about:config" Push enter, add ipv6 in top blank, forget what they call it, then double click on results to change boolean from false to true. **I'm a real newbie but this has my internet booming, I mean booming! Good luck.

It works for me, still get error message from Mplayer tho. No problem with VLC.
Thanks for your help, it got me on a right trak :)

---

### Post by xc3RnbFO8P on 2007-07-10
> **moore.bryan said:**
> [I]i don't know if you've seen [this post]("http://www.linuxquestions.org/questions/showthread.php?t=239176"), but it may lead to some answers as well.  i also don't know if vlc has the -playlist option.  i just visited wmsc.dr.dk now, swiftweasel detected the stream, and mediaplayerconnectivity extensions played the stream fine in xine.  this is a really strange error, but not one that seems to be all that uncommon when one googles the problem.
the AF_INET6 thing refers to something on the page (perhaps the stream itself) designed for ipv6 and according to the online docs.  it seems one work-around may be to add ```
prefer-ipv4=yes
``` to either **your ~/.mplayer/config **or /etc/mplayer/mplayer.conf file.  let me know if it works...
[/I]

No error message in Mplayer:)

---

