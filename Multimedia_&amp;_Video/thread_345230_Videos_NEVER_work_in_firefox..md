---
title: "Videos NEVER work in firefox."
date: 2007-01-24
forum: Multimedia &amp; Video
---

### Post by Peepsalot on 2007-01-24
*Please bear with me as I'm doing my absolute best to restrain my anger

I'm so tired of trying to view videos in firefox, does this actually work for anyone?

Here is an example video:
[http://eurekazone.com/albums/the-repeaters-in-action/ez_videos_009.mov](http://eurekazone.com/albums/the-repeaters-in-action/ez_videos_009.mov)

Can you play that?

Results for me:

First try:
totem gives some cryptic error message, I can't remember what it says exactly because I wiped totem off my system.   I honestly don't recall a single time it was capable of playing ANY file.  GOODBYE.
Second try:
After totem is removed, I restarted firefox and tried the page again.  I was hoping that without totem in the way, I would be able to try out the vlc-plugin.
Well, there is a black screen with the text "no video".  Is this a plugin?  If so, what plugin is this?  It has no interface.
ugh.
At this point I would like to try some other plugins, but I have no idea how to tell firefox which one to use.  I am aware of the about:plugins page in firefox, but what does it do when more than one plugin is assigned to a mime-type?  What does it give priority to?  How can these priorities be changed?
Third try:
So I hear many forum members touting mediaplayerconnectivity.  I try this with vlc and it seems to have issues.  It starts to play some files, then gets jerky or indefinitely pauses the video, like it isn't buffering the download or something.
Also, I find mediaplayerconnectivity annoying(besides the long winded name **) in that it must open the video players in a separate window.  Ideally I want to see videos embedded in the browser.

I generally like vlc, because it seems to play most of my files if I download them to my hard drive.  But as you can see playing them from my browser is a whole other matter. 

So far the only method that works is to find the url for the video, Save as, then go to the Desktop and click the file, then delete the file after viewing.
But this is a tremendous pain in the ...NECK.

** I tried to use mediaplayerconnectivity as one of the tags for this forum post.
Ubuntu forums gave me an error: 1. Please separate tags with commas. Each tag can only have a maximum of 3 words, and each word a maximum of 20 characters.

---

### Post by hscottyh on 2007-01-24
That video works great with the mozilla-mplayer plugin and the win32codecs. I just use automatix2 to install them. But for some reason it wants to install mozilla-totem plugin also. I just then remove that with synaptic. Or you could follow the howtos on this page and do it all by hand, which is just copy and paste in a terminal, so not that hard.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy) 

This has been a very useful guide for me. Search the page for *multimedia codecs* and *mozilla-mplayer* for a howto.

---

### Post by Peepsalot on 2007-01-24
OK I tried Automatix2, which I could have sworn I had done before, but it looks like I never installed the mplayer plugin through automatix.

I restarted firefox, and tried the link again.  I still get the black screen with "(no video)" text in the middle.  I still don't even know what plugin this is supposed to be, or how I would tell firefox which one to use.

---

### Post by hscottyh on 2007-01-24
If you haven't already done it, Install the 'Multimedia Codecs with automatix. Then with synaptic make sure mozilla-totem is not installed. If so, remove it.

If that doesn't work, I'm at a loss. Anyone else?

---

### Post by Peepsalot on 2007-01-30
Ok, I got rid of the vlc plugin, which apparently was the one making the black screen.  I already had the things you mentioned installed through automatix, but I decided to uninstall and reinstall and now things are working.
Thanks.

---

### Post by clean97gti on 2007-02-06
Just wanted to throw my 2 cents in.

The problem appeared to be the VLC plugin. It wouldn't play mpg, mov, or anything really.
I simply removed the VLC plugin from the folder (kept a copy in my home folder in case I ever want it back) and let the installed mplayer plugins handle the media. No issues at all. 
Here is how I did it.
open a terminal
change to the plugins dir.
```
cd /usr/lib/mozilla/plugins
```
make the copy of the VLC plugin file in your home dir. Obviously, replace mike with your dir.
```
sudo cp libvlcplugin.so /home/mike/libvlcplugin.so
```
Remove the VLC plugin from your plugins dir.
```
sudo rm libvlcplugin.so
```

You can open Nautilus to make sure its all done right or bounce around the directories to make sure.
Restart Firefox and browse to about:Plugins to make sure the pesky VLC plugin is gone. Please note, you'll need to have all the mplayer plugin installed. If you don't, you'll have to install it. No big deal and all the related info is in ubuntuguide.org

---

