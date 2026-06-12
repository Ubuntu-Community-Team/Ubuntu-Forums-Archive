---
title: "No video player working in Gutsy. :-("
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by mmcmonster on 2007-11-14
I have a bunch of videos in various formats: .avi files downloaded off the internet, .iso files I created myself, and commercial DVDs.

None of them are playing with vlc, mplayer, or totem.  All of them play the audio perfectly.  All of them show the same garbage for the video (some thin verticle yellow and black lines with some interlacing artifacts.

All the videos worked well under Ubuntu 7.04 before I did a clean installation.

I installed w32codecs already.

Any ideas?

---

### Post by djrobthaman on 2007-11-14
Install vlc.

Just go to add/remove applications and install it from there.

That should give you playback for pretty much any format conceivable.

But, if you also want to watch dvds, then BEFORE you install vlc you have to install one special file.  To do this you just open up the terminal and type the following

```

sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

Then open synaptic package manager, refresh, and install libdvdcss2.  Once you're done with this go ahead and install vlc and you'll have video playback for files and dvds.

---

### Post by soaro77 on 2007-11-14
I am having this exact same problem. Before I upgraded to Gutsy I could play any video file. Now when I play many of them, especially avi, I get sound but the video is just a bunch of pink lines and garbage. There is no picture at all. How can I fix this so I can see videos again?

---

### Post by mmcmonster on 2007-11-15
> **djrobthaman said:**
> Install vlc.

Just go to add/remove applications and install it from there.

That should give you playback for pretty much any format conceivable.

But, if you also want to watch dvds, then BEFORE you install vlc you have to install one special file.  To do this you just open up the terminal and type the following

```

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

```Then open synaptic package manager, refresh, and install libdvdcss2.  Once you're done with this go ahead and install vlc and you'll have video playback for files and dvds.

In my second line I mentioned that vlc is showing the same garbage as mplayer and totem.

This is obviously a lower level problem.  Maybe a codec problem.  The thing is, the same problem exists for **.iso** files of **unencrypted DVDs**, **physical DVDs**, **.avi files**, and even **quicktime files** viewed over the internet using mplayer's firefox plugin.

I can't imagine a single codec being the problem, but maybe an interaction between them?  I have all the usual suspects installed, including **w32codecs** and **libdvdcss2**.

Again, there is **identical** garbage video with **mplayer** and **vlc**.

By the way, the same video files work perfectly when I copy them to a different PC.

---

### Post by moodog on 2007-11-15
I too am having this problem. It only started for me about 5 days ago - not sure what updates I installed then. I have an nvidia 7700 card, and noticed that new restricted drivers were installed the other day. Will try updating graphics driver with envy tonight and see if that fixes the problem.

---

### Post by mmcmonster on 2007-11-15
It's not due to the batch of updates from 3-4 days ago.  I had the problem before that and was holding back on the updates for a couple days.

I installed the updates last night and that didn't fix matters, either. :-(

---

### Post by ukripper on 2007-11-15
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by chiefbearclaw on 2007-11-15
For me its only MPlayer that completely  gags, chokes and vomits all over my xorg.conf. I try to play a video in MPlayer and boom.. back to tty1. I'd much rather have a few weird lines and atrifacts.. (at least that is entertaining). tty1 isn't all that entertaining when you just lost everything you were working on. VLC works fine. I should mention this just recently started happening for me as well and I'm in LinuxMint XFCE Beta (7.10 Gutsy). However don't listen to my post because I have so many problems with my video as it is... I may just be adding more confusion. It did *feel* like a recent update did it. :lol:

---

### Post by djrobthaman on 2007-11-15
> **mmcmonster said:**
> In my second line I mentioned that vlc is showing the same garbage as mplayer and totem.

This is obviously a lower level problem.  Maybe a codec problem.  The thing is, the same problem exists for **.iso** files of **unencrypted DVDs**, **physical DVDs**, **.avi files**, and even **quicktime files** viewed over the internet using mplayer's firefox plugin.

I can't imagine a single codec being the problem, but maybe an interaction between them?  I have all the usual suspects installed, including **w32codecs** and **libdvdcss2**.

Again, there is **identical** garbage video with **mplayer** and **vlc**.

By the way, the same video files work perfectly when I copy them to a different PC.

Woops... silly me.  Actually sometimes I have a similar problem with some videos.  If you use vlc you can go to the preferences dialogue and click the advanced settings box in the bottom right corner.  Then go to the left drop down menu and go to Video>Output Modules.  Now I'm at a windows machine now so I can't guarantee this is the right sequence, but you should see a "Video Output Module" drop down box on the right.

Keep changing the module til the video looks good.  I find that the X11 option tends to do the trick.

---

### Post by mmcmonster on 2007-11-15
> **ukripper said:**
> [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Okay.  As I mentioned earlier, I've got **w32codecs** and **libdvdcss2** installed.  I've got **Medibuntu** in my repositories as well (that's where those come from, right?).


The problem is, **vlc**, **mplayer**, and **totem** all give **the same garbled video**.

I don't think vlc is the problem.  It's the same problem with any video player, **regardless of what codec** the video is encoded with.  (It happens with css-encrypted DVDs, unencrypted DVD .iso files, it happens with divx-encoded .avi files, it happens with quicktime encoded files on the internet.)




P.S. Sorry for all the bold-face.  It's just that I seem to be repeating myself a bit. :-(

---

### Post by ukripper on 2007-11-15
> **mmcmonster said:**
> Okay.  As I mentioned earlier, I've got **w32codecs** and **libdvdcss2** installed.  I've got **Medibuntu** in my repositories as well (that's where those come from, right?).


(

Good for you!

---

### Post by JasonF on 2007-11-15
> **djrobthaman said:**
> Woops... silly me.  Actually sometimes I have a similar problem with some videos.  If you use vlc you can go to the preferences dialogue and click the advanced settings box in the bottom right corner.  Then go to the left drop down menu and go to Video>Output Modules.  Now I'm at a windows machine now so I can't guarantee this is the right sequence, but you should see a "Video Output Module" drop down box on the right.

Keep changing the module til the video looks good.  I find that the X11 option tends to do the trick.

THIS is the correct answer.  Set video output to opengl for the best output. Avoid XVideo, though it should be the best solution, current nvidia drivers are broken and will display garbage with an XVideo output.  In mplayer you can use the switch -vo gl. I'm not sure about totem but it would probably be set somewhere in a global place for gstreamer.

---

### Post by mmcmonster on 2007-11-15
> **JasonF said:**
> THIS is the correct answer.  Set video output to opengl for the best output. Avoid XVideo, though it should be the best solution, current nvidia drivers are broken and will display garbage with an XVideo output.  In mplayer you can use the switch -vo gl. I'm not sure about totem but it would probably be set somewhere in a global place for gstreamer.


Okay.  I'll give it a shot tonight.  Is this is a temporary (known) problem with the nvidia drivers?

---

### Post by JasonF on 2007-11-15
> **mmcmonster said:**
> Okay.  I'll give it a shot tonight.  Is this is a temporary (known) problem with the nvidia drivers?

It's a very common problem, many of the posts on this very forum are about the same issue. Most of the posts go unanswered, however, as few people seem to be able to make the connection between the garbage output and the XVideo implementation in nvidia's current drivers.

Also, some people have reported success in fixing it by rolling back the nvidia driver a couple of versions.

---

### Post by mmcmonster on 2007-11-15
> **JasonF said:**
> It's a very common problem, many of the posts on this very forum are about the same issue. Most of the posts go unanswered, however, as few people seem to be able to make the connection between the garbage output and the XVideo implementation in nvidia's current drivers.

Also, some people have reported success in fixing it by rolling back the nvidia driver a couple of versions.


Well, in that case I'll let you guys know how things turn out.  :-)  Thanks for all the help.

---

### Post by Phurious on 2007-11-15
I had the same problems and switching the output module in VLC to X11 solved my issues!  Many thanks!

---

### Post by ubuntu-freak on 2007-11-15
Due to the desktop effects now default in Ubuntu, some of you will need to use the x11 driver in MPlayer's video preferences. Or just disable the effects and use the superior xv driver (good idea for DVD's). Add zoom=1 to the conf file in /home/you/.mplayer if your gonna use x11. If you are having trouble viewing streaming wmv, mp4, real etc or just want to improve mplayerplug-in's performance, I have posted a howto in the Debian User Forum's:
[http://forums.debian.net/viewtopic.php?t=21315](http://forums.debian.net/viewtopic.php?t=21315)
 It's worked fantastic for me that's why I'm sharing it. Make sure you don't have any # in the conf file. Enjoy.

---

### Post by moodog on 2007-11-16
FYI, I installed some more updates last night. Nothing obvious that would solve this problem, but after that video was all playing well again. No pink lines. I also updated the nvidia driver with envy, but the video was working before I did this. Was also still working afterwards too.

---

### Post by mmcmonster on 2007-11-19
> **JasonF said:**
> THIS is the correct answer.  Set video output to opengl for the best output. Avoid XVideo, though it should be the best solution, current nvidia drivers are broken and will display garbage with an XVideo output.  In mplayer you can use the switch -vo gl. I'm not sure about totem but it would probably be set somewhere in a global place for gstreamer.


It works great.  This issue is resolved for me.  Except that I notice slight audio skips when watching certain videos, and pauses during (supposedly) CPU-intensive tasks (such as the pop-up box from firefox's gmail-notifier extension coming up).

I noticed some updates in graphics components over the last few days.  I guess I'll try going back to the xv mode, since it doesn't have any audio skips on my system.

---

### Post by Mblackwell on 2007-11-28
I have this issue actually, and restarting X fixes it (although of course it means I have to kill all work). I haven't tried switching to X11.

---

### Post by eye208 on 2007-11-28
> **Phurious said:**
> I had the same problems and switching the output module in VLC to X11 solved my issues!  Many thanks!
Of all the available workarounds, X11 is the worst option because it results in high CPU load and the video will be all blocky when scaled to fullscreen.

VLC and MPlayer support OpenGL output which is much better quality.

If for some reason you have to use a player that does not support OpenGL (e.g. Totem), there is another workaround: Go to System --> Preferences --> Screen Resolution, select a different resolution, then click "Use previous resolution" to set it back again. This will make XVideo work.

I'd love to see an Nvidia driver update in the backports repository. If there has ever been a good reason for a backport, this is certainly one.

---

### Post by akparker on 2007-11-28
I followed the procedure on page 1 of this thread.

Then, when I tried to install VLC, it gives me the message below.
Can anyone help, or point me to a thread that addresses this?

Thanks,
AKP

[I]Cannot install 'vlc'

This application conflicts with other installed software. To install 'vlc' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.[/I]

---

