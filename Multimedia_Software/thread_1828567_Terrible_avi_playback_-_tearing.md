---
title: "Terrible avi playback - tearing"
date: 2011-08-19
forum: Multimedia Software
---

### Post by hartz on 2011-08-19
I am using an Acer netbook connected to my TV as a media station.  I have a bunch of AVI movies for the kids and also some TV series, also in AVI format, which I play through this computer.

The kids also play all their games, quite a variety, actually, with everything from OpenArena to Crayons to Osmos to SuperTuxCart, on this computer (using a wireless mouse and keyboard), and the games performance is quite acceptable.

The AVI playback performance is not particularly great, but generally watchable with a little tearing and blocky artifacts, and audio which does shift a little relative to the video over time, but this is what I have come to accept.  (Note: The same files play perfectly on my primary laptop, so I am sure this is just a CPU power issue.)  

mkv and mp4 files are however unwatchable, though these are also playing fine on my much more capable laptop.

As of about 2 days ago I notice that when an AVI video starts playing in VLC or any of the other players I tried, it shows a set of on-screen controls (play, pause, forward, backward buttons).  The tearing / blocky artifacts have also now increased to a point where the videos are simply unwatchable.

I am looking for a solution to all of this.  Ideally I'd like to be able to watch any files, AVI and MKV, but if that is unrealistic given the hardware then if I can at least get the AVI playback back to normal then I would be happy.  

I have to mention that about two years ago when I started using the netbook as a dedicated media station, there used to be less tearing and blocky artifacts.  I have however tried various Linux distros and returned to Ubuntu (Xfce).  I feel though that with time and software updates, playback have degraded significantly, from almost perfect to rather second rate, and as of the last 2 days, unwatchable.

Any ideas / suggestions?

Thanx,
  _hartz

---

### Post by nomko on 2011-08-19
Did you installed the Ubuntu restricted packages? And did you installed the additional packages from Medibuntu? Go to my English site and check the page of how to add multimedia. It migth help you solving your problem.
 
Quick question: Which player are you using? I use Vlc and have no problems what so ever with media files.

---

### Post by kerry_s on 2011-08-19
you need to stick to around 480p, 720p+ videos are a crap shoot with these atoms & intel vids.

---

### Post by hartz on 2011-08-19
@nomko - I've installed and re-installed numerous times (though not in the last 5 months) ... I am going to re-install one more time and take note of what I do.  I must be getting older because I can't remember any more, but I'm fairly sure that I did install lots of probably conflicting codec and media player packages.  For what it is worth, I use mostly VLC, but sometimes fall back to any of the other players to see whether these act any differently.

@kerry_s - Thank you, I am sure that most of my videos are low quality, but I will keep this in mind.  Is there a way to quickly identify what quality a video file is?

I've found a few recommendations on how to set up a media station machine.  Any more recommendations would be great, particularly RAM saving tips!

---

### Post by kerry_s on 2011-08-19
If your going to do a fresh install, give lubuntu a try. 
Just install lubuntu-restricted-extras & you'll be all set for media codecs

---

### Post by drawkcab on 2011-08-19
Xubuntu is great if you have 1-2 gb of ram.  Anything less than that and you should be running lxde/openbox.

Follow this guide to improve performance with 720p mkv:

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Even so, it may not be enough.  I've only gotten 720p to work well on my atom 330 setup that comes with the nvidia ion graphics card.  On my atom 270 netbook with intel graphics, forget it.  standard def .avi only for the netbook.

---

### Post by kerry_s on 2011-08-19
> **drawkcab said:**
> Xubuntu is great if you have 1-2 gb of ram.  Anything less than that and you should be running lxde/openbox.

Follow this guide to improve performance with 720p mkv:

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Even so, it may not be enough.  I've only gotten 720p to work well on my atom 330 setup that comes with the nvidia ion graphics card.  On my atom 270 netbook with intel graphics, forget it.  standard def .avi only for the netbook.


lol, i got a atom 330 & 270 as well, but my vid cards are intel 950
i'm using the atom 270 with 2gb ram, the kids use the atom 330 for gaming.
you can tweak gnome-mplayer for slow cpu & it will do 720p.

> 
Hi, My cpu is too slow, help!
for mpeg1/2 or mpeg4 try adding -nodouble or mplayer -lavdopts lowres=1 -vfm ffmpeg will use half-res decoding to speed things up as well.
for H264 try mplayer -lavdopts skiploopfilter=all file.mkv
might cause artefacts like sudden color changes, in this case try e.g. "nonref" instead of "all"
Your computer is still too slow?
Try -lavdopts skipframe=nonref:skiploopfilter=all
This will skip many frames, but saves 50% CPU performance
if using -vo gl use -vo gl:yuv=2 or similar. For high FPS video (> 50 Hz) also try -vo gl:swapinterval=0 since the default limits FPS to well below monitor refresh.


[http://wiki.multimedia.cx/index.php?title=MPlayer_FAQ#Questions_from_.23mplayer_channel:](http://wiki.multimedia.cx/index.php?title=MPlayer_FAQ#Questions_from_.23mplayer_channel:)

---

### Post by hartz on 2011-08-20
For a short while today I had perfect playback.  And I mean perfect.  Not a single block, streak, tear.

And then it just went back to bad.  I'm convinced it is one of the "Updates".

What I did is:
1. Backed up /var/cache/apt and /etc/apt/sources.list (I got rid of /etc/apt/sources.list.d because I use a sources list generated by the generator here: [http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php))

2. Installed Ubuntu Natty 11.04 with "Extras" but without updates.  I performed a clean install, wiping the entire disk.

3. Restored the apt sources list, the cached packages, and re-added the keys, then performed apt-get update.

4. Installed VLC, restricted-extras and restricted-addons, grandr, as well as a few games from the apt-cache (supertuxcart, junior-math, junior-typing)

5. Used apt-get upgrade to update the packages.  Almost everything was updated from the cache.  I noticed though that the list of updates seemed short.

6. Tested playback.  AVI file playback is perfect.

7. Checked "Mark all available updates" in Synaptic.  Strangely it found a lot of files still to be updated.  I allowed this to run through, and noticed that again most files were used out of the cache with very little needing to be downloaded.

8. AVI files still played fine, but there was a message about some updates not being done. (Partial update?)

9. I rebooted to complete the updates and performed another update.  Again I got even more updates, though it was just a small list (about 6 files if memory serves).

10. Rebooted again.  After this AVI playback became terrible again.

Is there a log where I can see what was updated when exactly, particularly the last set so that I can try to undo the last few bits until playback recovers?

Thanx,
  _hartz

---

### Post by kerry_s on 2011-08-20
/var/log/apt/history.log

should be the place.

---

### Post by drawkcab on 2011-08-20
> **hartz said:**
> For a short while today I had perfect playback.  And I mean perfect.  Not a single block, streak, tear.

And then it just went back to bad. ** I'm convinced it is one of the "Updates".**



I think you're right.  I had excellent playback after reinstalling ubuntu 11.04, only to lose it after that last kernel update.

On the bright side I noticed that if, after the update, I purge and then reinstall ffmpeg then I can substantially restore high def video playback.  I'm not sure what all I would have to reinstall in order to restore standard def .avi playback.

At any rate, I think the key here is to recognize that something is going on to the effect that kernel updates are leading to tearing/artifacting.

Any further ideas?

---

### Post by kerry_s on 2011-08-20
You should still have the old kernel, hold the shift key while booting & select it. Then you can see if it's just a kernel problem.

---

