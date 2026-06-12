---
title: "Problem Ripping My DVDs..."
date: 2011-09-08
forum: Multimedia Software
---

### Post by Valkyr333 on 2011-09-08
Hi, everyone...

So I'm trying to rip one of my DVDs with Kubuntu so I'll have a backup copy on my hard drive. Problem is, it doesn't seem like the computer can read it properly. I tried opening it with Movie Player, but it gives me the error message, "Could not open location; you might not have permission to open the file." 

I've tried opening it with AcidDVDRipper, dvd::rip and Thoggen DVD Ripper, but they all say they can't read any files from the disc. Thoggen suggests I "might not have libdvdcss2 installed" but my search for that in Synaptic doesn't turn up any exact results. Just Brasero and some Kubuntu Restricted Extras. I also tried this in my Windows XP computer, but my ripper there says "there are no DVD files in the source directory."

Is there something I can fix or tweak to get Kubuntu to recognize and capture the video from the disc? I'd really rather not have to buy another when this one gets old.

Thanks!

---

### Post by dniMretsaM on 2011-09-08
You might need to add the Medibuntu repository for libdvdcss2. Check out [this page]("http://medibuntu.org/repository.php") on how to add it. Then run:
```
sudo apt-get update
sudo apt-get install libdvdcss2
```EDIT: Removed second link. Was the wrong one, I'll see if I can find the correct one.

EDIT #2: Found it. You might be interested in [this]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") information too.

---

### Post by Valkyr333 on 2011-09-08
Hi,

Thanks for your response. I added the Medibuntu repositories, and followed the rest of your instructions. This didn't solve the problem, so I tried the second link you gave me for playing encrypted DVDs. I didn't notice at first that there was a section in that specifically for AMD64 users, (>.< D'oh!) so I followed the instructions at the top first. When I realized that was wrong, I used "apt-get remove" to undo it. I then followed the instructions for 64-bit users. The first one,
```

sudo apt-get install debhelper build-essential fakeroot
```

returned,

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
debhelper is already the newest version.
build-essential is already the newest version.
fakeroot is already the newest version.
```

I figured this meant that these were already installed, so I tried the next one,

```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

Which returned "command not found." Does this mean I have something else to install before this will work?

---

### Post by dniMretsaM on 2011-09-08
> **Valkyr333 said:**
> Hi,

Thanks for your response. I added the Medibuntu repositories, and followed the rest of your instructions. This didn't solve the problem, so I tried the second link you gave me for playing encrypted DVDs. I didn't notice at first that there was a section in that specifically for AMD64 users, (>.< D'oh!) so I followed the instructions at the top first. When I realized that was wrong, I used "apt-get remove" to undo it. I then followed the instructions for 64-bit users.

I'm not sure where the 64-bit-specific section is. Are you talking about the Medibuntu page or the encrypted DVD page?

> **Valkyr333 said:**
> The first one,
```

sudo apt-get install debhelper build-essential fakeroot
```returned,

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
debhelper is already the newest version.
build-essential is already the newest version.
fakeroot is already the newest version.
```I figured this meant that these were already installed, so I tried the next one,

Yes, that's what that means. Nice to see there are people around who can read between the lines...

> **Valkyr333 said:**
> ```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```Which returned "command not found." Does this mean I have something else to install before this will work?

Try these commands:
```
sudo apt-get update
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by Valkyr333 on 2011-09-08
Thanks. =)

That second code (after sudo apt-get update) returned the following error:
```

E: Couldn't find package libdvdread4sudo

```

---

### Post by dniMretsaM on 2011-09-08
> **Valkyr333 said:**
> Thanks. =)

That second code (after sudo apt-get update) returned the following error:
```

E: Couldn't find package libdvdread4sudo

```

You must have ran it before I edited my post. I accidentally typed:
```
sudo apt-get update
sudo apt-get install libdvdread4sudo /usr/share/doc/libdvdread4/install-css.sh
```Instead of this:
```
sudo apt-get update
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh
```Run that and see what happens. And sorry about that.

---

### Post by Valkyr333 on 2011-09-08
Okay, thanks for the correction.

That one returns,

```
libdvdread4 is already the newest version.
libdvdread4 set to manually installed.

```

---

### Post by dniMretsaM on 2011-09-08
> **Valkyr333 said:**
> Okay, thanks for the correction.

That one returns,

```
libdvdread4 is already the newest version.
libdvdread4 set to manually installed.

```

Ok, now try rebooting and playing or ripping a DVD. It should be working. If not, report any errors.

---

### Post by Valkyr333 on 2011-09-08
Movie Player still gives me the same error, "Could not open location; you might not have permission to open the file."

It won't let me rip it either. Thoggen says, "Failed to retrieve DVD titles for some reason. Maybe you do not have libdvdcss2 installed?"

---

### Post by dniMretsaM on 2011-09-08
> **Valkyr333 said:**
> Movie Player still gives me the same error, "Could not open location; you might not have permission to open the file."

It won't let me rip it either. Thoggen says, "Failed to retrieve DVD titles for some reason. Maybe you do not have libdvdcss2 installed?"

Hmm... Ok. You said Synaptic didn't give any results for libdvdcss2. Are the Multiverse repositories enabled? And I assume the out put of the following is "E: libdvdcss2 has no installation candidate."

```
sudo apt-get update
sudo apt-get install libdvdcss2
```

---

### Post by Valkyr333 on 2011-09-08
sudo apt-get install libdvdcss2 returns,

```
libdvdcss2 is already the newest version.
```

And Movie Player still returns the same error. My update manager poked me to install an update and a bug fix right before I started writing this post. The update was for "mplayer." Do you think I ought to try another reboot to see if it's got that all sorted out?

---

### Post by dniMretsaM on 2011-09-08
> **Valkyr333 said:**
> sudo apt-get install libdvdcss2 returns,

```
libdvdcss2 is already the newest version.
```And Movie Player still returns the same error. My update manager poked me to install an update and a bug fix right before I started writing this post. The update was for "mplayer." Do you think I ought to try another reboot to see if it's got that all sorted out?

Yeah go for it. A reboot might not be necessary, but I'd do it anyway. Since libdvdcss2 seems to be installed, I don't really know what the problem is. You could try:
```
sudo apt-get update
sudo apt-get install --reinstall libdvdcss2
``` I believe that's the command for reinstalling a package.

---

### Post by Valkyr333 on 2011-09-08
Actually, now Synaptic does show results for libdvdcss2. It actually shows it as being installed, now. I guess that's not the issue.

*Edit - Oops, sorry. You just said that. >.< Fail.

---

### Post by dniMretsaM on 2011-09-09
Ok since that's not the problem, I'm not really sure where to go from here. But I'll do my best. One thing to do is make sure you have your DVD drive set to a region. See the second link on my first post for information on that. Another thing would be to install libdvdnav4:
```
sudo apt-get update
sudo apt-get install libdvdnav4
```
This shouldn't have anything to do with the ability to rip a DVD, but I'm kind of grasping at straws here. Also, try a few different DVD's. It could just be an issue with the one your using. I'll keep digging and see if I can find anything more on this.

---

### Post by SeijiSensei on 2011-09-09
Have you tried using k3b for this?  Just make sure the kubuntu-restricted-extras and libk3b6-extracodecs packages are installed.

Can you play the DVDs with "mplayer dvd://1"?  Run this from a command prompt and you'll see a lot of details which might explain where the problems lay.

---

### Post by Valkyr333 on 2011-09-09
Yes, the universe and multiverse repositories are enabled. The result of that command is the same "libdvdcss2 is already the most recent version."

@[dniMretsaM]("http://ubuntuforums.org/member.php?u=1268161") - I've tried several DVDs this way, yeah. And the libdvdnav4 command returns the same "already the most recent version"

@[SeijiSensei]("http://ubuntuforums.org/member.php?u=698195") - I looked at the Restricted Extras package a bit before. Isn't it (or parts of it) made by Microsoft? I noticed it asked me to sign an EULA when I tried to install it, and I'd really rather not give MS any further legal authority over my computer. That's part of why I want to quit using Windows altogether. =/ If I've missed something there, please tell me. But I've seriously had it with MS, Apple, etc.

---

### Post by dniMretsaM on 2011-09-09
> **Valkyr333 said:**
> Yes, the universe and multiverse repositories are enabled. The result of that command is the same "libdvdcss2 is already the most recent version."

@[dniMretsaM]("http://ubuntuforums.org/member.php?u=1268161") - I've tried several DVDs this way, yeah. And the libdvdnav4 command returns the same "already the most recent version"

@[SeijiSensei]("http://ubuntuforums.org/member.php?u=698195") - I looked at the Restricted Extras package a bit before. Isn't it (or parts of it) made by Microsoft? I noticed it asked me to sign an EULA when I tried to install it, and I'd really rather not give MS any further legal authority over my computer. That's part of why I want to quit using Windows altogether. =/ If I've missed something there, please tell me. But I've seriously had it with MS, Apple, etc.

It asked you to sign something? I don't remember it doing that for me. Something to do would be to install the separate parts of the without the Microsoft font package. The package in question is [FONT=Courier New]ttf-mscorefonts-installer[/FONT] and is used for installing .ttf fonts (a Microsoft proprietary format). So if you want to install everything else, run this in terminal:
```
sudo apt-get update
sudo apt-get install flashplugin-installer gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-fluendo-mp3 libk3b6-extracodecs libtunepimp5-mp3 gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse libavcodec-extra-52 libmp3lame0 unrar lame
```

This code installs all of the packages installed [FONT=Courier New]kubuntu-restricted-extras[/FONT] except [FONT=Courier New]ttf-mscorefonts-installer[/FONT] and [FONT=Courier New]libdvdnav4[/FONT].You could substitute [FONT=Courier New]unrar-free[/FONT] for [FONT=Courier New]unrar[/FONT] if you want to use more free software. It's nice for the occasional .rar archive you find. It may have trouble with a few of them though, that's why the non-free, restricted version is installed. Also note that the Flash installed via [FONT=Courier New]flashplugin-installer[/FONT] is not very good. Your much better off using the Firefox add-on [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") (You may already do this, I don't know. Just though I'd mention it.). Anyway, I guess I should have asked if you had this installed in the first place. My bad.

---

### Post by Valkyr333 on 2011-09-09
Okay, well "sign" probably wasn't the best term. It asked me to agree to the terms, click the button, etc. I've become wary of EULA's, especially from MS, Apple, etc. They like to take away users' rights.

I notice you mention installing a Flash Plugin. I remember installing and configuring flash and other visual components on this computer being a -real- hassle in the beginning (working with AMD64 as a fullblown linux virgin, etc) - so my question here is, what's the likelihood that running 

```
sudo apt-get update
sudo apt-get install flashplugin-installer gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-fluendo-mp3 libk3b6-extracodecs libtunepimp5-mp3 gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse libavcodec-extra-52 libmp3lame0 unrar lame
```

might cause major screwups in the monitor, the internet, etc on this computer?

I've never looked into Flash-Aid, but I'll check it out to see if it might benefit me somehow. =)

---

### Post by dniMretsaM on 2011-09-09
The[FONT=Courier New] flashplugin-installer[/FONT] package doesn't actually install the plug-in, it's just a tool to install it (a little weird). But you could just not install it (remove it from the command) if you've already got it set up in a satisfactory manner and it would be fine. And if you've got a dual-monitor, I would recommend not messing with it (those are usually a royal pitb). So just remove it from the command and you'll be all set.

---

### Post by Valkyr333 on 2011-09-09
Okay, results of that...

```
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-ffmpeg is already the newest version.
E: Couldn't find package gstreamer0.10-pitfdll
```

---

### Post by dniMretsaM on 2011-09-09
But everything else installed installed without a problem? And [FONT=Courier New]gstreamer0.10-pitfdll[/FONT] must not be available on 10.04. It is on 11.04 though (not sure about 10.10). It shouldn't matter for what your trying to do anyway. If all the other packages installed correctly, try ripping again (with K3b and the other rippers you have) and see if it works.

---

### Post by Valkyr333 on 2011-09-09
k3b doesn't seem to want to do anything with this disc... I put it in, k3b recognizes it, but when I click "rip video dvd" nothing happens.

*Edit - Thoggen shows the same results now as well. That "Failed to find dvd title information for some reason. Perhapse you do not have libdvdcss2 installed?" message.

---

### Post by 4Orbs on 2011-09-09
Are you trying to rip a bluray disc? Have you tried any other dvd's to see if they will even play?

---

### Post by Valkyr333 on 2011-09-09
No, it's not a BluRay. And yes, I've tried several other DVD's to see if the problem would remain. It does.

---

### Post by 4Orbs on 2011-09-09
Have you gone to the [Comprehensive Multimedia how-to]("http://ubuntuforums.org/showthread.php?t=766683") on this forum and followed the steps under the dvd playback/ripping section? Probably a good idea to follow the entire how-to from top to bottom; but only follow the parts that apply to your specific installation.

You might need to add the xine stuff, although I think kubuntu already has those included.

---

### Post by Valkyr333 on 2011-09-30
Okay, so I've followed the steps in that comprehensive how-to. I still can't play DVD's straight from the disk-drive, but I can rip them to my hard drive and play them back just fine from there. Same goes for CD's, and I'm totally stoked about a lot of these programs. k3b, Kid3 and soundKonverter are a dream, and I haven't even tried the WinFF Video Converter yet. My problems are effectively solved. Thanks, guys. =)

---

