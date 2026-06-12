---
title: "Problems with flash player stream."
date: 2009-03-19
forum: Multimedia Software
---

### Post by FreddieBambino on 2009-03-19
Ok, so I have downloaded Ubuntu and tossed out Windows. Everything works beautifully except streaming flash videos on some websites. Youtube works fine, I can watch it and fast forward after the buffer has loaded and so on.

But when I go to my local news websites(local being Iceland) I cant fast forward or backwards on streaming videos. I did get a suggestion for additional plugins first when I entered the sites and tried to stream so I downloaded those(think it was gstreamer plugin) after that I was able to play the videos but not able to fast forward and backwards.

Does anyone know of some plugins I can use?
Here are the websites:
[http://dagskra.ruv.is/sjonvarpid/4456554/2009/03/19/](http://dagskra.ruv.is/sjonvarpid/4456554/2009/03/19/)
and
[http://vefmidlar.visir.is/?channelID=&programID=d93d6ddc-f3df-4c27-90e2-28d49738f306&mediaSourceID=1c475314-8de6-408b-ba0c-d944290d3e44](http://vefmidlar.visir.is/?channelID=&programID=d93d6ddc-f3df-4c27-90e2-28d49738f306&mediaSourceID=1c475314-8de6-408b-ba0c-d944290d3e44)


The problems are two. 
1. The streaming is not good, that is it seems to jam all the time, for few milliseconds, then pick up speed(dont know how to say that in English:D).
2. The player can not fastforward or backwards even though I can see the streaming scale to do so. This is not a problem with Windows. If I try to fastforward it stops and begins from the beginning. Also, on both websites they split the news into news pieces, if I chose one news piece, it also stops and begins the whole news program from beginning.

Does anyone know of a fix for this.

---

### Post by gandaran on 2009-03-19
> **FreddieBambino said:**
> Ok, so I have downloaded Ubuntu and tossed out Windows. Everything works beautifully except streaming flash videos on some websites. Youtube works fine, I can watch it and fast forward after the buffer has loaded and so on.

But when I go to my local news websites(local being Iceland) I cant fast forward or backwards on streaming videos. I did get a suggestion for additional plugins first when I entered the sites and tried to stream so I downloaded those(think it was gstreamer plugin) after that I was able to play the videos but not able to fast forward and backwards.

Does anyone know of some plugins I can use?
Here are the websites:
[http://dagskra.ruv.is/sjonvarpid/4456554/2009/03/19/](http://dagskra.ruv.is/sjonvarpid/4456554/2009/03/19/)
and
[http://vefmidlar.visir.is/?channelID=&programID=d93d6ddc-f3df-4c27-90e2-28d49738f306&mediaSourceID=1c475314-8de6-408b-ba0c-d944290d3e44](http://vefmidlar.visir.is/?channelID=&programID=d93d6ddc-f3df-4c27-90e2-28d49738f306&mediaSourceID=1c475314-8de6-408b-ba0c-d944290d3e44)


The problems are two. 
1. The streaming is not good, that is it seems to jam all the time, for few milliseconds, then pick up speed(dont know how to say that in English:D).
2. The player can not fastforward or backwards even though I can see the streaming scale to do so. This is not a problem with Windows. If I try to fastforward it stops and begins from the beginning. Also, on both websites they split the news into news pieces, if I chose one news piece, it also stops and begins the whole news program from beginning.

Does anyone know of a fix for this.

those two links don't use flashplayer, you can play them with totem plugin or any other player plugin, for totem install the ubuntu-restricted-extras package (codecs), if you find totem-plugin is not good remove it and install mozilla-mplayer plugin or vlc plugin, I tried them with totem, plays fine but you cannot fastforward, some sites wont allow it.

---

### Post by FreddieBambino on 2009-03-19
Plenty thanks to you my friend. I did what you said, downloaded those extra plugins and restarted the computer but nothing changed. After that I downloaded every totem plugin I could find in the synaptic package manager but no luck. 
But dont I need to activate the plugin on the player somehow or does it come on automatically. When I right click on the totem movie it says: 
"Browser Plugin using GStreamer 0.10.21"

Should I perhaps remove Gstreamer? If I need to activate the plugin then how, can anyone tell me that please.

I also tried right clicking on the movie and play it with movie player, but it was the same, could not fast forward. 

So:
1. Should I somehow activate the plugin?
2. Should I remove the extras now and instead download the vlc plugin?
3. Should I remove the Gstreamer plugin?

---

### Post by FreddieBambino on 2009-03-19
Hi guys, I new development going on here. ;)

I went on and downloaded the vlc plugin, restarted. I did not remove the extra package.

Now the streaming of the player is better, and I can chose different news pieces and there for dont always need to start from beginning.

But there is still one new and big problem left to solve, now the scale bar for buffering is gone. That is to say I cant see that scale that one usually uses to fast forward on streaming videos. 
When I right click on the video nothing happens, no menu, no info, no options. Help please.

---

### Post by gandaran on 2009-03-20
> **FreddieBambino said:**
> Plenty thanks to you my friend. I did what you said, downloaded those extra plugins and restarted the computer but nothing changed. After that I downloaded every totem plugin I could find in the synaptic package manager but no luck. 
But dont I need to activate the plugin on the player somehow or does it come on automatically. When I right click on the totem movie it says: 
"Browser Plugin using GStreamer 0.10.21"

Should I perhaps remove Gstreamer? If I need to activate the plugin then how, can anyone tell me that please.

I also tried right clicking on the movie and play it with movie player, but it was the same, could not fast forward. 

So:
1. Should I somehow activate the plugin?
2. Should I remove the extras now and instead download the vlc plugin?
3. Should I remove the Gstreamer plugin?

firefox can only use one plugin at a time, it's best if you want vlc plugin or mplayer plugin to work you have to remove totem plugin, you can have more than one installed but then you have to set firefox to use it for a specific task like set vlc to play wmv files or mplayer for real video files, don't remove gstreamer plugins, other programs depend on them to work, you don't need to remove totem player, just remove totem plugin.

---

