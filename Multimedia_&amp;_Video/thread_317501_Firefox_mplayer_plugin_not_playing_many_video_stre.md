---
title: "Firefox mplayer plugin not playing many video streams"
date: 2006-12-12
forum: Multimedia &amp; Video
---

### Post by mauripop on 2006-12-12
Hi, my Edgy Eft Kubuntu installation is working very well except for the following glitch: video streams don't play on the mplayer plugin installed in Firefox. 

It seems to be windows based streams, since I can play those based on Quicktime like the ones on Apple's web site. But streams from cnn.com or netflix.com seem caught in an endless loop that displays messages like "Buffering... Playing... Connected... Playing mms://... Connecting... Buffering mmst://...Connecting to server 38.98...". No video ever gets shown nor any audio played. This loop can continue endlessly. 

I installed all necessary codecs from automatix2, and I tried the mplayer plugin on both Swiftfox and Firefox, installed from automatix2 and Adept respectively. Same results. 

While trying the Linspire vmware application on the same machine, I tried to play some of the same streams with the same results! However, I still have a Mandriva distro installed on the same computer, and when I boot up that one streams are played perfectly using its mplayer plugin. 

I have looked at this forum and googled around but I found no similar complains. I'm sure I'm not the only one with this problem! Am I?

---

### Post by khelidan on 2006-12-14
same problem for me.....

---

### Post by chocbar31 on 2006-12-14
Have you tried deleting the totem codecs from the plugins folder? Worked for me, as all codecs now default to mplayer.

Hope this helps!


> **mauripop said:**
> Hi, my Edgy Eft Kubuntu installation is working very well except for the following glitch: video streams don't play on the mplayer plugin installed in Firefox. 

It seems to be windows based streams, since I can play those based on Quicktime like the ones on Apple's web site. But streams from cnn.com or netflix.com seem caught in an endless loop that displays messages like "Buffering... Playing... Connected... Playing mms://... Connecting... Buffering mmst://...Connecting to server 38.98...". No video ever gets shown nor any audio played. This loop can continue endlessly. 

I installed all necessary codecs from automatix2, and I tried the mplayer plugin on both Swiftfox and Firefox, installed from automatix2 and Adept respectively. Same results. 

While trying the Linspire vmware application on the same machine, I tried to play some of the same streams with the same results! However, I still have a Mandriva distro installed on the same computer, and when I boot up that one streams are played perfectly using its mplayer plugin. 

I have looked at this forum and googled around but I found no similar complains. I'm sure I'm not the only one with this problem! Am I?

---

### Post by mauripop on 2006-12-14
Yes, I had read about it, and I made sure there were no totem plugins in my /opt/swiftfox/plugins folder. The only plugins there are:

file:///opt/swiftfox/plugins/libflashplayer.so
file:///opt/swiftfox/plugins/libjavaplugin_oji.so
file:///opt/swiftfox/plugins/libnullplugin.so
file:///opt/swiftfox/plugins/libunixprintplugin.so
file:///opt/swiftfox/plugins/mplayerplug-in-qt.so
file:///opt/swiftfox/plugins/mplayerplug-in-qt.xpt
file:///opt/swiftfox/plugins/mplayerplug-in-rm.so
file:///opt/swiftfox/plugins/mplayerplug-in-rm.xpt
file:///opt/swiftfox/plugins/mplayerplug-in.so
file:///opt/swiftfox/plugins/mplayerplug-in-wmp.so
file:///opt/swiftfox/plugins/mplayerplug-in-wmp.xpt
file:///opt/swiftfox/plugins/mplayerplug-in.xpt
file:///opt/swiftfox/plugins/nphelix.so
file:///opt/swiftfox/plugins/nphelix.xpt
file:///opt/swiftfox/plugins/nppdf.so

Any other ideas?

---

### Post by mauripop on 2006-12-14
I thought  had fixed it by enabling ipV6 support in Firefox, but after playing a couple of streams it's back to the same behavior... endless loop of mplayer plugin displaying messages connecting and playing, connecting and playing.

---

### Post by zilbere on 2006-12-19
I took me 5 hours to figure out - damn, why it is so hard to put this information on mplayerplug-in FAQ ?

Ok, you should choose X11 for your video output. Well, that is it.
Otherwise, to see the embedded movie you should click right mouse button, enter full screen mode and it will work as well.

There is one more solution :
add to (create if not exsts) ~/.mplayer/mplayerplug-in.conf
noembed=1

This way you will see a new mplayer window with movie, instead of embedded.

Enjoy !

---

### Post by mauripop on 2006-12-19
The x11 thing kinda helped... the fullscreen tip did not. 
I guess cnn streams are hard to see anyway... it sometimes works for me, sometimes not. Most other streams work well. 

Thanks for your help!

---

### Post by Affejunge on 2006-12-30
I cannot believe how simple that fix was.  X11 did the trick for me.  I never would have thought that was the cause of the issue.
Awesome job, Zilbere.

---

### Post by crispy_420 on 2006-12-30
For me it is hit and miss. Sometimes it plays and other times it buffers only to lead to failure. It depends on what website I'm at though. It has even frozen my browser.

But if I download the problem file and play it locally, it works. So leads me to believe it not the player but the plugin.

---

### Post by dnccnd on 2007-01-03
> **zilbere said:**
> Ok, you should choose X11 for your video output.

I am having kind of the same problem, though I laways get the massege (no picture) where there should be a video playing.

How do I choose X11 for my video output?

Is there maybe a way to choose another application instead of Mplayer to watch videos in FIrefox?

---

### Post by mauripop on 2007-01-03
To choose X11 for your video output, try to play a video and right click on MPlayer's video window. Choose Configure on the context menu that will appear. A configuration window will appear, the first option is Video and it has a drop down list. From that list choose X11. Then click OK on that window. You should probably close the MPlayer video and try it again for the changes to take effect. 

Mine is working very well now, only some CNN videos falter at times. Although it is finicky, of all the streaming media players I've tried, MPlayer is the best in x86 Linux for Windoze (mms and asf) and Quicktime videos. For Realplayer, go with Realplayer's own plugin video player for Linux, it works flawlessly with nfl.com videos.

---

### Post by dnccnd on 2007-01-05
Now it works! Great! Thanks!

My Mplayer was already set on X11, but I could see that there are different types of X11:

1) XV > X11/XV
2) X11 > X11(XImange/SHM)
3) gl > X11 (OpenGL)
4) gl2 > X11 (OpenGL) - multiple textures version
5) xvidix > X11 (vidix)

I tried nr. 5 and I could hear the sound, then I tried nr. 3 and now I can see and hear.

I guess I have a different version of Mplayer as I had to choose Preferences to get to the video settings.

---

### Post by sdowney717 on 2007-03-03
none of your suggestions are working for me.
I have this working in fedora.

All It does is play the audio, the video is a tan screen with the mms stream url displayed.

Any other ideas
thanks

---

### Post by sdowney717 on 2007-03-03
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)

install these win32 codecs and then it works ok.

---

