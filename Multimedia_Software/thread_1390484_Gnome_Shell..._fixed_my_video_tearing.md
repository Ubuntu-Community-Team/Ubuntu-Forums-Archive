---
title: "Gnome Shell... fixed my video tearing???"
date: 2010-01-25
forum: Multimedia Software
---

### Post by Roasted on 2010-01-25
I have a high definition live concert here on my system. I fire it up and oh my gosh does it look great. Oh, except that massive tear across everybody's face. It makes playing movies and whatnot on Linux just unbearable because it's constantly there. 

I've been tinkering with the Ricotz PPA of Gnome Shell recently. Out of curiosity I was like, well, let's see how DVD/multimedia video playback is.

System is as follows:

Quad Core 2.33ghz, 4gb DDR2 800 RAM, Nvidia 9600 GT 256bit 512mb RAM PCIEx16 2.0, 19" 1440x900 24" 1920x1080 twinview, Nvidia 185 drivers.

Ever since I began on Ubuntu (6.06) I have used Nvidia.
Ever since I've been on Ubuntu, I've had video tearing.
Different systems. Different Nvidia cards. Always tearing.

Fired up this live concert (Oasis @ 2008 Wembley. Amazing) and fast forwarded to where a guitar solo was going on. Lots of lights, quick movements, basically an area I would ALWAYS see high amounts of tearing.

As expected, tons of tearing.

Ran gnome-shell --replace, fired up the same video, fast forwarded to the same part...

No tearing...

WHAT! Really? Wow. Seriously? Tons of different hardware configs. Tons of different Nvidia drivers. Always had tearing. And Gnome Shell solved it? And Gnome Shell is in... what... alpha stage? Beta stage? 

Note - I will say this. I get little to no tearing on my 19". I've only ever used 22" or larger for my primary monitor, which is where I've had the tearing. Smaller the video box, less likely it is to see video tearing. But I've always had it on my 22" and 24" main monitors. But like I said, it looks like using GS I don't have it.

Note to self - when playing a movie, use GS if you're not already using it.

---

### Post by sys32592 on 2010-01-25
I have been lurking for quite some time (been an Ubuntu user for years now) and *finally* decided to register since I read your dilemna. I have the same Nvidia card, and the tearing was getting to me for the longest time. I swapped cards with an ATI Radeon 4600 series model and the tearing was STILL there.

Well, I went back to my trusty Nvidia card determined to find the solution. It has a lot to do with the desktop visual effects in Ubuntu (even set to normal), so turn them to "none". Also, run your nvidia-settings and turn the OpenGL all the way up to "High Quality". 

After adjusting these two settings I have absolutely zero video tearing. Hope that helps!

---

### Post by Roasted on 2010-01-26
> **sys32592 said:**
> I have been lurking for quite some time (been an Ubuntu user for years now) and *finally* decided to register since I read your dilemna. I have the same Nvidia card, and the tearing was getting to me for the longest time. I swapped cards with an ATI Radeon 4600 series model and the tearing was STILL there.

Well, I went back to my trusty Nvidia card determined to find the solution. It has a lot to do with the desktop visual effects in Ubuntu (even set to normal), so turn them to "none". Also, run your nvidia-settings and turn the OpenGL all the way up to "High Quality". 

After adjusting these two settings I have absolutely zero video tearing. Hope that helps!

Well I certainly appreciate you registering just to respond to my post! However, I already have compiz effects completely disabled and I still had tearing. I did not try the high quality settings with OpenGL though... I'll give that a shot when I get home.

Can anybody who knows what's "under the hood" of the current Gnome versus Gnome Shell help me understand why they're so different to give me different (and positive) results?

---

### Post by Roasted on 2010-01-27
Desktop Effects - None.
OpenGL Settings - High.
Video Tearing? Yes. :(

The one positive thing to say about this is I don't have tearing in Dragon Player in Kubuntu and I also don't have tearing in Gnome Shell. So regardless, whatever I upgrade to from Ubuntu 9.10 in the near future, I'll have a fix (FINALLY) at that point.

---

### Post by k64 on 2010-01-27
It's probably Clutter, the toolkit that GNOME Shell is based on, that is helping. GTK+ does a pretty bad job at video playback.

---

### Post by Roasted on 2010-01-27
> **k64 said:**
> It's probably Clutter, the toolkit that GNOME Shell is based on, that is helping. GTK+ does a pretty bad job at video playback.

That's what I was thinking too. It's a shame GS isn't further along in development. I wouldn't mind running it full time if more features were implemented and it was a bit more stable.

Can't knock alpha/beta software for lack of stability though. :P

---

### Post by sports.car.guy on 2010-01-28
This has nothing to do with Gnome. It has everything to do with the setup of the video driver. With nVidia, unlike AMD at this time if you go into the configuration app, you can enable vertical syncing for video. Well AMD has it sorta but still a work in progress at this point.

Enable that, and it should solve the problem because by default it is not enabled on nVidia.

---

### Post by Roasted on 2010-01-28
> **sports.car.guy said:**
> This has nothing to do with Gnome. It has everything to do with the setup of the video driver. With nVidia, unlike AMD at this time if you go into the configuration app, you can enable vertical syncing for video. Well AMD has it sorta but still a work in progress at this point.

Enable that, and it should solve the problem because by default it is not enabled on nVidia.

I'm quite certain it has more to do with Gnome. I've heard countless times the way GTKT applied video feedback was very poor, and I'm seeing proof of it now.

BTW - I did not see "vertical syncing" in the nvidia-settings control panel, however I do have sync to vblank enabled already.

Not sure what else I can do, but there's one thing I know.

Gnome Shell fixed my video tearing. This is a good sign, at least for future usage of Gnome. It'll be nice to actually play a DVD on here and not want to punch my computer in the face.

---

### Post by turbodellmini on 2010-01-31
Just thought I'd pop in and confirm that I too noticed this phenomenon.  I've been struggling with video tearing since day one on my macbook pro (8400M GT).  I eventually gave up.

After hearing about gnome shell I decided to give it a go and I was dumbfounded.  All video tearing gone.  If only gnome shell were more functional at the moment I would be a full time user!

---

### Post by sports.car.guy on 2010-01-31
This tread should be a definite read then for a lot of Ubuntu users with AMD graphics, like that Mac Book does (Well I believe it does).  Most of the complaints about AMD GPU's with Ubuntu is tearing and not to the extent I have ever seen on Kubuntu before doing a couple graphics tweeks that get rid of it.

That is why I said what I said about the tearing. It is because that is usually how you go about trying to get it straight with AMD. Some after still complain about major tearing and this could very well be why.

---

### Post by Roasted on 2010-01-31
Although Gnome Shell seems to fix video tearing, I'm not so sure I'd recommend it to users yet. I am using Gnome Shell because I find it interesting and I'm trying to learn more about it while it's still in testing.

But it should be known, Gnome Shell isn't even in alpha yet, it's that young. It seems VERY stable for not being in alpha stage yet, but it's still in the infancy stage of testing. I run it full time on my work laptop full well understanding that it might give me issues along the way.

You can bet though, once more updates and patches come down I'll be very happy to run this full time on my desktop at home. But for now, it's fine sitting on my work laptop. :)

---

### Post by sports.car.guy on 2010-02-01
> **Roasted said:**
> Although Gnome Shell seems to fix video tearing, I'm not so sure I'd recommend it to users yet. I am using Gnome Shell because I find it interesting and I'm trying to learn more about it while it's still in testing.

But it should be known, Gnome Shell isn't even in alpha yet, it's that young. It seems VERY stable for not being in alpha stage yet, but it's still in the infancy stage of testing. I run it full time on my work laptop full well understanding that it might give me issues along the way.

You can bet though, once more updates and patches come down I'll be very happy to run this full time on my desktop at home. But for now, it's fine sitting on my work laptop. :)

Um wouldn't you want a more stable work machine? I mean to me when I am looking at the possibility of making my work life harder I would have gone the other way round and let my fun machine be the one to possibly be a PITA

---

### Post by Roasted on 2010-02-01
> **sports.car.guy said:**
> Um wouldn't you want a more stable work machine? I mean to me when I am looking at the possibility of making my work life harder I would have gone the other way round and let my fun machine be the one to possibly be a PITA

Just because I have GS on my work laptop doesn't mean I run it 247. I often run my work laptop at home getting caught up on minor stuff and I'll run GS there to get more acquianted with it. Ironically, at the moment I'm at work with GS running on the laptop. It runs pretty good, especially considering it's pre alpha state.

---

### Post by Roasted on 2010-02-03
For the time being since I'm not going to touch gnome shell with my desktop, since GS seems to have some issues with dual screen setups yet, I'm STILL, after 4 years, looking for a way to eliminate video tearing on my nvidia desktop.

Is there anything I can do, anything at all?

---

### Post by Roasted on 2010-02-04
So, I'm having a hard time trying to figure this out. I went into the Gnome Shell chat and asked exactly what was different between the way metacity renders video and mutter, and their answer was sync to vblank is already done so there's no checkboxes to worry about - something that nvidia seems to fail at by default. But even STILL, when I sync to vblank, I still have tearing.

I set all of my settings in compiz to sync to vblank, along with sync to vblank in nvidia-settings, set opengl settings to the best they can be, unchecked auto detect refresh rate and forced 60hz, etc.

---

### Post by turbodellmini on 2010-02-05
> **Roasted said:**
> For the time being since I'm not going to touch gnome shell with my desktop, since GS seems to have some issues with dual screen setups yet, I'm STILL, after 4 years, looking for a way to eliminate video tearing on my nvidia desktop.

Is there anything I can do, anything at all?


Not sure about dual screens, but switching to KDE+Kwin (I hear it might be possible to use kwin in gnome?)  worked perfectly in clearing up my video tearing issues on my NVIDIA 8600M GT.

---

### Post by Roasted on 2010-02-05
> **turbodellmini said:**
> Not sure about dual screens, but switching to KDE+Kwin (I hear it might be possible to use kwin in gnome?)  worked perfectly in clearing up my video tearing issues on my NVIDIA 8600M GT.

I ran Kubuntu 9.10 and also had video tearing.

---

### Post by Roasted on 2010-02-06
up.....

---

### Post by Roasted on 2010-02-08
After hearing more users tell me they've fixed their video tearing, yet I still can't get mine to work right, I'm growing a little frustrated to fix this 4 year old problem.

Bumping again...

---

### Post by petvet2 on 2010-04-03
(For years now) I have used separate x-screens together with xinerama and video tearing has not been an issue.

---

### Post by Roasted on 2010-04-03
> **petvet2 said:**
> (For years now) I have used separate x-screens together with xinerama and video tearing has not been an issue.

How would one accomplish this?

---

### Post by petvet2 on 2010-04-04
With Nvidia cards: 

In the console: sudo nvidia-settings . In the opened configuration utility choose 'X Server Display Configuration' -> click 'Configure' choose 'Separate X screen' and finally tick 'Enable Xinerama' and 'Save to X Configuration File'. Exit nvidia-settings, log out and back in (or restart the computer).

In the file /etc/X11/xorg.conf i guess that the following options should be present:

Section "ServerLayout"
    Option         "Xinerama" "1"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

and:

Section "Screen"
    Option         "TwinView" "0"
EndSection

However, I am certainly not a xorg.conf-expert.
Nvidia vdpau and xrandr does not work with xinerama. This probably causes problems with e.g. 3d-desktop effects.

---

### Post by Roasted on 2010-04-04
Not sure what I did wrong, but let's just say I'm glad I backed up my xorg.conf before I made those changes. Compositing didn't work (docky failed to start) and my secondary monitor ended up becoming my primary. Couldn't add my panel to be on my primary or anything.

Any idea??

---

### Post by petvet2 on 2010-04-04
Compositing will probably not work with xinerama. Roasted, what kind of configuration do you have? Video card, monitors, tv etc.?

---

### Post by renkinjutsu on 2010-04-04
If you're an nvidia user, you should try the nouveau drivers.. they're already amazing in their current state..

I'm playing a video file in HD that has a higher resolution than my monitor (1680x1050) and there's no video tearing at all!

I would like to try gnome-shell with nouveau/gallium, but it crashes X (it could be because i use xinit instead of gdm) .. oh! i think i'll just have to delete "exec pekwm" from my xinitrc

---

### Post by Roasted on 2010-04-05
Intel Q8200
ASUS P5QL Pro
Nvidia 9600GT 512mb 256bit PCIEx16 2.0
4gb DDR2 800
Ubuntu 9.10 64 bit
Latest Nvidia drivers from restricted hardware manager

---

### Post by petvet2 on 2010-04-05
Roasted, no reason to edit xorg.conf manually - use 'sudo nvidia-settings' and you will easily get your desired monitor orientation. Renkinjutsu, I have the Nvidia 195.36.15 driver on 64 bit Ubuntu 9.10, and video tearing is still a serious problem except when using 'separate x-screens' + 'xinerama'.

(Nvidia GF GTS8600, Core Q6600 @ 3.6GHz, 4GB Ram / SMPlayer and VLC media player)

---

### Post by Roasted on 2010-04-05
> **petvet2 said:**
> Roasted, no reason to edit xorg.conf manually - use 'sudo nvidia-settings' and you will easily get your desired monitor orientation. Renkinjutsu, I have the Nvidia 195.36.15 driver on 64 bit Ubuntu 9.10, and video tearing is still a serious problem except when using 'separate x-screens' + 'xinerama'.

(Nvidia GF GTS8600, Core Q6600 @ 3.6GHz, 4GB Ram / SMPlayer and VLC media player)

I never was editing the xorg file manually...?

---

### Post by northrat on 2010-08-30
Hey, sorry for resurrecting this thread but it seems that I had the same problem.
I have an Nvidia 9600 GT gpu as well and I couldn't get decent quality playback from most video files. 1080p files are choppy depending on their bitrate and all media was tearing up all over the place, especially in action scenes, which is incredibly irritating. It seems only Dragon Player let me have an improved video watching experience but it still wasn't perfect. XBMC kept choking too, I tried finding advice on how to Vsync and I turned my video card's quality options to the max.

I found this thread and it helped me fix it by using Gnome-shell.
What I noticed was that in a normal Gnome session under XBMC when using the diagnostic screen, which you reach by pressing 'o' during video playback, to check how many frames I was dropping, there was no reference to VDPAU and while running XBMC under Gnome-Shell it mentioned VDPAU and video playback was almost perfect, only dropping frames when I resumed a paused video before stabilizing playback.

I don't know how relevant it is, but is it something wrong with the video card, the setup or window manager? Obviously the card is capable of displaying video just fine, but for some reason it doesn't under the normal Gnome or KDE for that matter. Perhaps it's got something to do with Gnome-Shell using Mutter as opposed to Metacity.

I don't know, anyway that's what I noticed, maybe it's useful to someone, somehow. If anyone wants more info I'll be happy to give it to you if you tell me where to get it and how.

---

