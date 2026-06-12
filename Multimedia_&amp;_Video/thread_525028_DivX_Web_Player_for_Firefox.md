---
title: "DivX Web Player for Firefox"
date: 2007-08-13
forum: Multimedia &amp; Video
---

### Post by Aslanov on 2007-08-13
how and where do i install from?
help appreciated
thanx.

---

### Post by Arthur Archnix on 2007-08-13
Edit: Didn't see that the title was part of the question.

Check out the [ubuntuguide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty"), and install vlc, its mozilla plugin, and all other plugins. If the divx is streamed you'll need to also install avahi, but the guide goes into detail.

---

### Post by Aslanov on 2007-08-13
umm....well..okay, i installed the MPlayer, and chose to open DivX with the MPlayer under configuration, but i still get this error:

Failed to open : (insert video link here)

PLZZ help, i need to watch SCRUBS!

---

### Post by Arthur Archnix on 2007-08-13
Sorry, I meant that you should use VLC for you viewiing needs. I've apt-gone and removed mplayer and use vlc for all viewing needs.

---

### Post by bjarneh on 2007-08-13
there is a multimedia plugin which is quite helpful if you want to use Mplayer (as one should) :-) for mm., its called MediaPlayerConnectivity and lets you assosiate filetypes with programs alot simpler then about:config stuff, then choose mplayer and off you go. it can be installed from firefox.com webpages i think...

---

### Post by Gremlinzzz on 2007-08-13
this is for the mplayer plugin 
 add divxs plugins to watch divxs online
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so

---

### Post by Aslanov on 2007-08-13
i still get the same error.

---

### Post by Gremlinzzz on 2007-08-13
if your going to use the mplayer mozilla plugin you have to uninstall the totem mozilla  plugin they bump heads
also set the configure right click on the video screen choose X11 for video and alsa for audio click ok

---

### Post by Gremlinzzz on 2007-08-13
> **Gremlinzzz said:**
> if your going to use the mplayer mozilla plugin you have to uninstall the totem mozilla  plugin they bump heads
also set the configure right click on the video screen choose X11 for video and alsa for audio click ok

you might need codecs too 
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)

---

### Post by Gremlinzzz on 2007-08-13
> **Gremlinzzz said:**
> you might need codecs too 
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)

put these commands in the terminal one at a time and press enter
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so

---

### Post by Aslanov on 2007-08-14
k i tried those stuff, but when i press play with Mplayer it tried connecting and all that, but then it just says "Stopped"

---

### Post by Arthur Archnix on 2007-08-14
I had the same problems man. I'm not sure why people recommend mplayer so strongly. Never had as smooth as time as I've had since I removed totem, and mplayer, and used vlc for ALL my viewing needs. 

But hey... I'm still in the n00b classification myself, so what do I know.

---

### Post by misfitpierce on 2007-08-14
Google Divx linux codecs.. download them into your home folder then type this in terminal

sudo sh FILENAME.sh

It will give you some info hit Q then type yes

It will install then restart firefox and it should work fine.

---

### Post by Aslanov on 2007-08-14
still same error.....oh my god!

@Arthur, can u please tell me what u did, seeing as how im a n00b hopefully its n00b-proof

---

### Post by Arthur Archnix on 2007-08-14
Well, like I said, I seem to be in the minority here. But after installing various linuxes and ubuntus over the past two years, and fiddling with getting stuff to play, I've never had as much effortless fun since I did this (from a clean install):

```
sudo apt-get remove mplayer
sudo apt-get remove totem
```

Then I used the ubuntuguide at [www.ubuntuguide.org](www.ubuntuguide.org) to do the following:
```
sudo apt-get install ubuntu-restricted-extras
```
keep the terminal open, because you'll need to say yes to some license stuff. Then enable mediabuntu repo by adding this line:
```
deb http://packages.medibuntu.org/ feisty free non-free
```
to you sources in
```
sudo gedit /etc/apt/sources.list
```
then do:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get upgrade
```
then do:
```
sudo apt-get install w32codecs
```
Now you're ready for VLC and all its plugins. Do:
```
sudo apt-get install vlc vlc-plugin-* mozilla-plugin-vlc
```
then add these two so that you can use it to stream:
```
sudo apt-get install avahi-daemon
sudo apt-get install avahi-utils
```
That's it. Everything should "just work". If it doesn't, it may be because of all the stuff you've done with mplayer and such. In which case, all I can suggest is:
```
sudo apt-get purge mozilla-firefox
```
which will do a lot. Then start over at the top (ignoring the stuff about adding repos), so that any packages automatically removed are reinstalled and all the links restored.  oh but first you'll have to reinstall firefox:
```
sudo apt-get install mozilla-firefox
```

Don't worry about losing ubuntu-desktop. You only need that to do a dist-upgrade, but if you choose to do that you can just install it first then do a dist-upgrade.

---

### Post by Terry of Astoria on 2007-08-15
Hi. I'm following the suggestions above and when I do 
```
sudo apt-get update
```
after adding the medibuntu source, I get
```
W: GPG error: http://packages.medibuntu.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

```
 Hm ...I'll try to forge ahead and look for info.
(goes away on another tab)
(comes back later) 
OK. I found out that after I do 
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
..recommended at the medibuntu site for adding feisty medibuntu repository then my apt-get update does not throw that error. So I continue to follow the directions now. THANKS for posting these suggestions here. I've always liked vlc and did not know about the FF plugin, so want to try this.

---

### Post by Arthur Archnix on 2007-08-15
Sorry, didn't realize the key was necessary. I was just copying from the ubuntuguide and may have missed a step.

I'll add that line to my instructions.

Post back if you have any problems.

Best

---

### Post by Terry of Astoria on 2007-08-15
Actually all the steps went through OK but FF still cannot play divx files which have the extension .divx . I haven't tried avi fiiles yet where is one? I'm trying to play this cool grateful dead video at tv-links.co.uk 
[http://tv-links.co.uk/video/5/4685/7102/47404/69475]("http://tv-links.co.uk/video/5/4685/7102/47404/69475")
--it plays on my Desktop running Dapper w/Mplayer plugin installed by Automatix, but the Automatix method did not work for this Inspirno 1300 laptop w/Feisty, so I tried the VLC trick . . .alas, so luck yet.

---

### Post by Arthur Archnix on 2007-08-15
Your link doesn't work. I play all sorts of videos from that site though, perhaps you could describe how to get there?

---

### Post by Terry of Astoria on 2007-08-15
That link is in Music Videos under Grateful Dead.
I got it to work excellently with Mplayer, and the above-suggested MediaPlayerConnectivity. Actually this is just what I've wanted. The streaming video has finally escaped from the firefox window! True Fullscreen City at tv-links!
I installed Mplayer with the plugin using Automatix and then configured MediaPlayerConnectivity to use mplayer WITHOUT the GUI - it didn't work right with it -- just learn a few key strokes - F for fullscreen is my favorite. spacebar pauses. I still kept VLC and I can use it anytime! I like this MediaPlayerConnectivity plugin. Install it from Firefox by clicking tools-addons-get extensions then search for it and install.

---

### Post by Arthur Archnix on 2007-08-15
Glad to hear your problems are solved.

I was able to watch the live grateful dead show without mplayer installed, which is not to say I told you so, only that in Linux, the answer is always at hand if you are willing to try.

Happy ubuntuing!

---

