---
title: "Devede, Mplayer, Totem and online video woes"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by Steve H on 2007-04-25
Since upgrading to Feisty i found that i was having trouble with Devede producing static on the audio track of the files it produced. I have been using Devede to turn my .avi's into DVD compatible files for quite a while. However, like I say, once I burned the files I found that the audio was rubbish (just static). After much trawling of the Ubuntu forums and the net I found [_this thread _]("http://ubuntuforums.org/showthread.php?t=416707")and that it was down to the Mplayer/Mencoder that is packaged with Feisty. When I went to [_this_]("http://www.rastersoft.com/programas/devede.html") site, I found a new version of Devede and Mplayer/Mencoder. 

So I uninstalled the old version of Mplayer/Mencoder and installed the new package supplied by Devede, as well as installing the newer Devede. BINGO! This worked a treat, I can now turn avi's into DVD compatible files with no problem what so ever. The static has gone.

However, I noticed that this new package disabled the Mplayer-Mozilla plug-in, and any attempt to reinstall, just forced Synaptic to uninstall the Devede-Mplayer/Mencoder package. So I left it with the new Devede version.

Then I found that I was having problems watching DVD's using VLC (as mplayer had stopped working). So ,again, after much searching I found a thread that suggested altering the Gstreamer-properties page, so that the video output was No Xv. Which I did. Another problem solved......or so I thought.

So now Firefox is using Totem to play online streaming videos, which works fine on Youtube, but is very hit and miss on the BBC. For some reason I either get a black screen with audio (unless i restart X) or i get about half a second of play and then it stops. I presume this is down to the Gstreamer video output module change that i did.

Is there any way to get ALL of these things working at once? 
Is there a new Mencoder being releasen that still allows Devede to do good quality DVD files??
And how the hell do i get the BBC online video streaming working again???

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

I have done a clean reinstall of Feisty and it seems to have sorted all my multimedia problems.

---

