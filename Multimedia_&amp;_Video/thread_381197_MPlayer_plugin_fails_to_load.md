---
title: "MPlayer plugin fails to load"
date: 2007-03-10
forum: Multimedia &amp; Video
---

### Post by jswhite on 2007-03-10
When I navigate to any page that has media on it (where I would expect the MPlayer plugin to load), I get nothing but an empty box. I haven't seen or heard anything that would lead me to believe that the plugin is loading at all.

So far, I've done:

1. Installed MPlayer plugin through Synaptic, restarted Firefox, and restarted the computer. Nothing.
2. Uninstalled that, then tried again through Automatix. Still nothing.
3. Done a complete removal of the MPlayer plugin, restarted the computer, and tried to install it again through Synaptic. Nothing again.

Any other ideas?

---

### Post by r4ik on 2007-03-10
Reinstall with automatix and make sure you install the codecs.
Right click the empty screen set video to xv and sound to alsa and
you should be oke.

---

### Post by ssavelan on 2007-03-10
I really like totem-xine.

If you get totem-xine, libxine-extracodecs, the totem plugin + flash-nonfree + realplayer, I believe you will have found the easiest way to access all (or very nearly all) media formats.

You will have to remove the mplayer plugin.

Not exactly the advice you are looking for, but I had a similar issue a while back and just  went with:

totem-xine/Flash/Realplayer

Hope that helps.

---

### Post by jswhite on 2007-03-10
r4ik: Tried that, didn't help. The problem wasn't with MPlayer itself being faulty, since the standalone player works just fine. It's just that the plugin is not loading properly within Firefox to play embedded media like it should.

ssavelan: Tried that also, still didn't help. With or without the mplayer plugin, it's just giving me a blank white box where the embedded media player should be.

I also tried deleting my profile to see if that would help. Unfortunately, it did the same thing even with a completely clean profile.

---

### Post by ssavelan on 2007-03-10
Take away all media plugins.... &

sudo apt-get install

totem-xine
libxine-extracodecs
totem-mozilla

If that does not work and you get tired of searching, reinstall ubuntu and do it.  with Flash and RealPlayer, all common media formats will be available streaming and otherwise.

---

### Post by jswhite on 2007-03-10
Upon further inspection, I doubt it's either an MPlayer issue or a codec issue. I've got every codec known to man installed (and reinstalled several times), and I've tried the Totem plugin, Kaffeine plugin, and MPlayer plugin. Still, I've got websites that load NONE of them for embedded media, and instead display only a white box.

I had this working properly with this exact profile on my MEPIS install before I reformatted, so I know it at least CAN work. Sites like YouTube work, and Realplayer comes up just fine for embedded .ra files. The two specifically that I've noticed are embedded .mp3's and embedded .wmv's. Both give me white boxes.

Two examples:

[http://www.sherdog.com/news/radio.asp?id=140](http://www.sherdog.com/news/radio.asp?id=140) (embedded .mp3)

[http://www.wrestlinggonewrong.com/video/angle_mcmahon_glass.html](http://www.wrestlinggonewrong.com/video/angle_mcmahon_glass.html) (embedded .wmv)

On both sites previously, the MPlayer plugin launched upon loading the page and displayed the embedded media. Now, either with my backed-up old profile from my MEPIS install or with a brand-spanking new profile, I just get a white box where the plugin should be appearing.

Someone wanna click a couple links and see if it works for you?

---

### Post by RomeReactor on 2007-03-10
Hi. Just tried the links and they both work here. Make sure you **only** have one video plugin for Firefox installed; my system's had the symptoms you describe when multiple video plugins for Firefox were installed. So i recommend searching for **mozilla** on Synaptic, and uninstalling kaffeine-mozilla, mozilla-plugin-vlc, mozilla-helix-player, and totem-mozilla, leaving only mozilla-mplayer.

---

### Post by jswhite on 2007-03-10
I thought that might be a problem, so I checked. Unfortunately, I'm already down to just one media player plugin (totem-mozilla, which can't be removed without removing ubuntu-desktop).

*grumble*

---

### Post by RomeReactor on 2007-03-11
That's odd; i don't recall Totem-Mozilla telling me it was going to remove the Ubuntu-Desktop package when i uninstalled it. However, you should still be able to view .WMV files with it if you installed the w32codecs package from the PLF repositories, if you have them in your **sources.list** file. If you don't have it, then open a terminal and type:

```
gksudo gedit /etc/apt/sources.list
```

and add at the end

```
## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
```

Save and close the file, and, still in the terminal:

```
sudo apt-get update
```

Then search for the w32codecs in Synaptic, or install them from the command line:

```
sudo apt-get install w32codecs
```

I also recommend you install

```
sudo apt-get install libxine1 libxine-extracodecs
```

Totem should then play those files in Firefox.

---

### Post by jswhite on 2007-03-11
The problem isn't in being able to view .wmv files, or any other file type. I've already got all the codecs installed, and if I download the videos to my computer I can view them just fine. I can also just copy the URL into Totem and view it that way. The only problem is that, if it's embedded in the page, I just get a white box where the Totem/MPlayer/Kaffeine plugin window should be. No plugin starts, and I don't get any unplayable/unviewable/missing codecs/etc error messages. It's just blank, like Firefox doesn't even know that it's supposed to be starting something.

---

### Post by tommcd on 2007-03-11
This is not an ideal solution, but try the firefox addon "media player connectivity". This will let you select any media player you have to play embedded media, which will open in a new window. It's a bit clunky, but it works:
[https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/)
I had the same problem, which in my case was due to the mplayer plugins being broken, and I never managed to fix it.

---

### Post by jswhite on 2007-03-11
I hadn't even thought about that. I used to use that extension a while back, but I think I switched profiles at one point and forgot to reinstall it. I'll give it a whirl and see if that does the trick.

---

### Post by ssavelan on 2007-03-12
Wow, when I click the above links, I get no indication that anything supposed to be happening: no sound, no video.  However, in my own little world, I run into no unavailable media.

But, when I click on "get the podcast" my set-up can not handle .itm, firefox has no association with it.  And, I thought I had all available formats!

I don't get a white box... (I am also on xubuntu [which actually seems a bit less buggy than gnome-ubuntu])  I get an error message.  Let me reproduce exactly..


Click Here to check out the podcast on iTunes.

Firefox doesn't know how to open this address, because the protocol (itms) isn't associated with any program.

I'll be interested to see where this thread goes.

---

### Post by novice1 on 2007-03-15
> **RomeReactor said:**
> Hi. Just tried the links and they both work here. Make sure you **only** have one video plugin for Firefox installed; my system's had the symptoms you describe when multiple video plugins for Firefox were installed. So i recommend searching for **mozilla** on Synaptic, and uninstalling kaffeine-mozilla, mozilla-plugin-vlc, mozilla-helix-player, and totem-mozilla, leaving only mozilla-mplayer.

I have the identical problem mozilla-mplayer will NOT run in Firefox. In attempting to follow your advice I found that totem-mozilla can NOT be removed without forcing the removal of the ubuntu-desktop!!  In the Synaptic Package Manager there is a strongly worded caution that removal of the ubuntu-desktop is not recommended. 

I use Edgy and in the file browser -- I look in the /usr/mozilla-firefox/plugins I find the following two files listed as "link (broken)" and their Icons displaying a white X in a red box.  I check this directory each time after , reinstalling, removing and reinstalling, complete removal and then reinstall and I always get these files listed as "link (broken)" and yes they are not there after I do a removal /complete removal:

mplayerplug-in-gmp.so
mplayerplug-in-gmp.xpt

So it would seem to me that at least in Edgy the mozilla-mplayer plug in does not get installed correctly or the above files are corrupted in some way.

Any advice you may have to get me up and running would be greatly appreciated.

---

### Post by tommcd on 2007-03-16
novice1,
This is exactly the problem I had, and I never found a solution. This is what led me to media player connectivity. If you ever find a solution, please add it to this thread.

---

### Post by ssavelan on 2007-03-16
> **novice1 said:**
> 
Any advice you may have to get me up and running would be greatly appreciated.


What advantages are there to mplayer over totem-xine?

---

### Post by tommcd on 2007-03-17
> **ssavelan said:**
> What advantages are there to mplayer over totem-xine?

For just playing media, I don't think mplayer has any advantage over totem or totem-xine. Those programs have a better user interface also. Mplayer has mencoder, the video encoding app. This is available in synaptic as a seperate package. If you get mencoder, then get devede also. Devede is an idiot-proof GUI fron end for mencoder that makes it real easy to make DVD isos out of video files that you can then burn to disc and watch on a DVD player.

---

### Post by ssavelan on 2007-03-17
> **tommcd said:**
> For just playing media, I don't mplayer has any advantage over totem or totem-xine. Those programs have a better user interface also. Mplayer has mencoder, the video encoding app. This is available in synaptic as a seperate package. If you get mencoder, then get devede also. Devede is an idiot-proof GUI fron end for mencoder that makes it real easy to make DVD isos out of video files that you can then burn to disc and watch on a DVD player.

Thanks for the tip.  I was wondering how I could perform such a task.  i haven't put any time into it; but, I had a vague hope of doing just that.  Sounds like a simple enough way to go.

---

### Post by ssavelan on 2007-03-17
and, for those who are interested, you can just

sudo apt-get install devede

and mplayer, mencoder and the rest are dependent.  one stop shopping.

---

### Post by silkstone on 2007-03-17
It seems that many people have had a problem with video from the BBC website (and maybe other places). This has affected people using Real Player for the clips - the Beeb site Preferences let you choose between using Real Player or Windows Media Player, and of course the latter is not available for Linux.

Some people say they've solved this by installing RP manually rather than from the repos, but this didn't work for me. Every time I tried to open a video clip, the new window opened, RP started and then crashed, and the player window went grey. You could then choose to 'Play in stand-alone media player' and the clip would play in RP with no problem. But it was a flippin' nuisance having to go through the open/crash routine to get there.

Anyway, I've solved it, but I'm not sure exactly how. I'll tell you what I did in case it works for anyone else.

1. Uninstall Real Player. You may have to do this from Synaptic rather than Add/Remove. When this is done, go back into Synaptic, click on Status and see of there are any residual components of RP left behind. If so, get rid of them too.

2. From Synaptic, install the VLC media player, plus every single one of the codec plugins that are listed under it. When you choose some of these, Synaptic will tell you that you also need to install some lib* library files, and it will automatically check those for installation too. That's fine. Let it install everything.

3. Start Firefox and go to the BBC Sports page where there are usually quite a few video clips. Click on one of them. It will try to open, but probably you'll get an error message saying that some component of Real Player cannot be found. Not surprising 'cos you've binned it all.

4. In the Beeb Player Window, click on Preferences at the top right. Choose Windows Media Player (really) and also set the connection speed to fast, assuming you're on Broadband.

5. Now close that window and try again with a video clip. It should work, although be patient because it does take a little while to download and buffer the data stream.

I'm not sure if the Beeb player is using one of the VLC codecs for Windows or quite what, but it doesn't really matter as long as it works.

BTW you can use either VLC or Totem (which comes with Ubuntu) for playing other media files and DVDs - it's up to you. I think Totem is OK, so I've left that as default.

P.S. Apologies - I know this relates to Real Player rather than MPlayer, but perhaps replacing MPlayer with VLC would work here too.

---

### Post by ssavelan on 2007-03-17
> **silkstone said:**
> 

BTW you can use either VLC or Totem (which comes with Ubuntu) for playing other media files and DVDs - it's up to you. I think Totem is OK, so I've left that as default.



How, pray tell, do you set media defaults in Firefox?

---

### Post by wearekosh on 2007-03-24
Hi - Im a newbe to Ubuntu 

I get the same white box when trying to play video at [www.evilchili.com](www.evilchili.com) - and have installed mplayer, totem, w32codec 
- (thats totem, totem-gstreamer & totem-mozilla but not totem-xine)


but also gstreamer? and it seem i have the "good" the "bad" and the "ugly" plugins installed? is this a problem?

may be a clue???

---

### Post by wearekosh on 2007-03-24
look here 

[http://www.ubuntuforums.org/showthread.php?t=337825](http://www.ubuntuforums.org/showthread.php?t=337825)

---

### Post by ssavelan on 2007-03-24
> **wearekosh said:**
> Hi - Im a newbe to Ubuntu 

I get the same white box when trying to play video at [www.evilchili.com](www.evilchili.com) - and have installed mplayer, totem, w32codec 
- (thats totem, totem-gstreamer & totem-mozilla but not totem-xine)


but also gstreamer? and it seem i have the "good" the "bad" and the "ugly" plugins installed? is this a problem?

may be a clue???

Having multiple plugins for the same job is often a problem.

I would personally go with totem-xine with all the codecs (libxine-etracodecs is crucial) and totem-mozilla.  I would try to remove all other plugins.  I have never gotten gstreamer-based to work as well as xine-based; but, there has to be people out there that prefer gstreamer.

---

