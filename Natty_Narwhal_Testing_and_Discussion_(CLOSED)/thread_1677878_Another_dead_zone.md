---
title: "Another dead zone?"
date: 2011-01-29
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-01-29
I appear to have another dead zone. Right in the middle of my screen. It seems to be roughly rectangular shaped - it's about 6 inches by 3, I would say. I can't right-click on the desktop or in any file, until I move the file a bit, then it's ok.
Left click is no better in the same area. It makes it difficult to click on a thread. The scroll wheel has no effect either if the pointer is in the dead zone.
I am fully updated and I didn't notice this yesterday, but that doesn't necessarily mean it wasn't there then :wink:
Anybody else noticed anything?

---

### Post by Harry33 on 2011-01-29
Could it be because you have upgraded today the package
xserver-xorg-input-evdev (2.6.0)?
It will break xserver 1.9 series for sure.
Try downgrading to previous 2.3.2 version.

---

### Post by coffeecat on 2011-01-29
> **Harry33 said:**
> Could it be because you have upgraded today the package
xserver-xorg-input-evdev (2.6.0)?
It will break xserver 1.9 series for sure.
Try downgrading to previous 2.3.2 version.

Yes, I'm getting the same as Quackers and I have the 1:2.6.0-1ubuntu1 version of xserver-xorg-input-evdev. But I don't have any other xorg breakage (that I've detected so far) so I think I'll just hang in there until the next update.

---

### Post by Harry33 on 2011-01-29
> **coffeecat said:**
> Yes, I'm getting the same as Quackers and I have the 1:2.6.0-1ubuntu1 version of xserver-xorg-input-evdev. But I don't have any other xorg breakage (that I've detected so far) so I think I'll just hang in there until the next update.

Coffeecat, do you have xserver 1.9.* series or 1.10rc1 installed?

---

### Post by coffeecat on 2011-01-29
> **Harry33 said:**
> Coffeecat, do you have xserver 1.9.* series or 1.10rc1 installed?

Opened Synaptic to check and the Properties window opened smack within the dead zone. :sigh:

Anyway... Good point. I have 2:1.9.0.902-1ubuntu4 for xserver-xorg-core and I think the same for xserver-common but I seem to be having problems with my Synaptic properties window for some reason! :lol:

---

### Post by Quackers on 2011-01-29
I too have the 2:1.9.0.902-1ubuntu4 for xserver-xorg-core and I have the new evdev so I will follow your link Harry33 and downgrade and see if the dead zone bugs off :-)

EDIT  Harry33, I've lost the link that you posted earlier. I forgot where it was :-(
How do I downgrade evdev? I presume the package - force option is no good, as it's greyed out :-)  Thanks!

---

### Post by mc4man on 2011-01-29
If finding a 'dead zone' (invisible window) did you happen to do any of these - 
maximize synaptic
have any window open w/ the top buried and pull the window down

Have you tried switching workspaces to see if the invisible window is only on 1 workspace

Ex.
newly created invis... on workspace 1

> xwininfo: Window id: 0xe00683 (has no name)

  Absolute upper-left X:  167
  Absolute upper-left Y:  453
  Relative upper-left X:  167
  Relative upper-left Y:  453
  Width: 595
  Height: 499
  Depth: 24
  Visual: 0x21
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: ForgetGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +167+453  -1158+453  -1158-128  +167-128
  -geometry 595x499+167+453


Moving to workspace 2, clicking in same area
> xwininfo: Window id: 0x1200024 "x-nautilus-desktop"

  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1920
  Height: 1080
  Depth: 24
  Visual: 0x21
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+0  -0+0  -0-0  +0-0
  -geometry 1920x1080+0+0


---

### Post by tghe-retford on 2011-01-29
> **Quackers said:**
> 
How do I downgrade evdev? I presume the package - force option is no good, as it's greyed out :-)  Thanks!
Do you have xserver-xorg-input-evdev version 2.3.2 in /var/cache/apt/archives/? If so, you can use that package to downgrade with dpkg:

This is for the 64-bit version that I have. If you're using Natty 32-bit, replace 'amd64' with 'i386':

```
sudo dpkg -i /var/cache/apt/archives/xserver-xorg-input-evdev_1%3a2.3.2-6ubuntu3b1_amd64.deb
```

I had to downgrade my xserver-xorg-input-evdev because in my case, the KDE desktop wouldn't even load.

---

### Post by Quackers on 2011-01-29
> **tghe-retford said:**
> Do you have xserver-xorg-input-evdev version 2.3.2 in /var/cache/apt/archives/? If so, you can use that package to downgrade with dpkg:

This is for the 64-bit version that I have. If you're using Natty 32-bit, replace 'amd64' with 'i386':

```
sudo dpkg -i /var/cache/apt/archives/xserver-xorg-input-evdev_1%3a2.3.2-6ubuntu3b1_amd64.deb
```

I had to downgrade my xserver-xorg-input-evdev because in my case, the KDE desktop wouldn't even load.

Thanks, but no :-) I only have xserver-xorg-input-evdev_1%3a2.6.0-1ubuntu1_amd64.deb in var/cache/apt/archives  :-(

---

### Post by tghe-retford on 2011-01-29
> **Quackers said:**
> Thanks, but no :-) I only have xserver-xorg-input-evdev_1%3a2.6.0-1ubuntu1_amd64.deb in var/cache/apt/archives  :-(
Launchpad to the rescue! :D

[https://launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/1:2.3.2-6ubuntu3b1](https://launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/1:2.3.2-6ubuntu3b1)

The builds are on the right hand side. Just be sure you don't select the dev or the udeb built files.

---

### Post by Quackers on 2011-01-29
Do I need to remove xserver-xorg-input-evdev_1%3a2.6.0-1ubuntu1_amd64.deb in var/cache/apt/archives  first, or the 2:1.9.0.902-1ubuntu4 for xserver-xorg-core from synaptic?
Thanks

---

### Post by tghe-retford on 2011-01-29
> **Quackers said:**
> Do I need to remove xserver-xorg-input-evdev_1%3a2.6.0-1ubuntu1_amd64.deb in var/cache/apt/archives  first, or the 2:1.9.0.902-1ubuntu4 for xserver-xorg-core from synaptic?
Thanks
No, you don't need to do either.

I just installed the deb file using dpkg on the command line (I didn't have a terminal, KDE wasn't working) and dpkg will downgrade it in due course.

I also use aptitude to hold the package (sudo aptitude hold xserver-xorg-input-evdev) to ensure it and dependencies don't upgrade whilst it is broken. If you do this, don't forget to unhold it (sudo aptitude unhold xserver-xorg-input-evdev) when the bug is fixed and a new version is uploaded. I use aptitude to upgrade. This procedure is different if you use apt-get to upgrade.

---

### Post by coffeecat on 2011-01-29
Well, this is curious. On my desktop I have:

xserver-xorg-input-evdev - 1:2.6.0-1ubuntu1
xserver-xorg-core - 2:1.9.0.902-1ubuntu4
xserver-common - 2:1.9.0.902-1ubuntu4

... and I'm getting the dead zone.

Whereas, on a laptop I have the same three versions of those packages and no dead zone (that I can find). Both the desktop and the laptop are using the open-source ATI driver if that has anything to do with it. Radeon HD4200 on laptop and Radeon HD4350 on desktop.

---

### Post by Quackers on 2011-01-29
Thanks to Harry33 and Retford, I've downgraded, as suggested, and my dead zone appears to have disappeared :-) Which is good, because it appeared to grow in size with use!
Unlike coffeecat's it seems :-(

---

### Post by coffeecat on 2011-01-29
> **Quackers said:**
> 
Unlike coffeecat's it seems :-(

You'll just have to get yourself a new laptop with an ATI card. :p Think about it: compiz and gee-whiz effects without having to install a proprietary blob. Uncorrupted Plymouth splash. The pleasure of using a make of card that most on this forum tell others to avoid. (I like being ornery.) Bliss! :)

---

### Post by Quackers on 2011-01-29
> **coffeecat said:**
> You'll just have to get yourself a new laptop with an ATI card. :p Think about it: compiz and gee-whiz effects without having to install a proprietary blob. Uncorrupted Plymouth splash. The pleasure of using a make of card that most on this forum tell others to avoid. (I like being ornery.) Bliss! :)

Been there, done that! (I've still got the scars :-) )

---

### Post by mc4man on 2011-01-29
> my dead zone appears to have disappeared
May return at some point, likely nothing to do w/ xserver, more so w/ compiz
(I have a new install, fully updated (nvidia-current ) and can create this almost at will.

---

### Post by Quackers on 2011-01-29
> **mc4man said:**
> May return at some point, likely nothing to do w/ xserver, more so w/ compiz
(I have a new install, fully updated (nvidia-current ) and can create this almost at will.

How do you do that? I'm not in the habit of moving screens around, or even unmaximising them, so that wasn't the problem with mine.
And compiz has been fine on here for weeks now.

---

### Post by coffeecat on 2011-01-29
> **mc4man said:**
> If finding a 'dead zone' (invisible window) did you happen to do any of these - 
maximize synaptic
have any window open w/ the top buried and pull the window down

Have you tried switching workspaces to see if the invisible window is only on 1 workspace

> **mc4man said:**
> May return at some point, likely nothing to do w/ xserver, more so w/ compiz
(I have a new install, fully updated (nvidia-current ) and can create this almost at will.

Interesting points. I'm back on my desktop now - the one that did have the dead zone - freshly rebooted, and no dead zone now. I'll watch out for those window glitches you mention to see if any are causing this. I did have  to pull a window down with alt+left-click before I noticed the dead zone, but I can't remember the details.

By the way, and I know this is OT, but does anyone know if there any way of stopping Firefox opening full screen? It only started happening a few days ago in Natty. It makes sense on a laptop but looks absurd on my 24" monitor.

---

### Post by Quackers on 2011-01-29
Doesn't FF open in the state that you closed it in? ie if it's unmaximised when you close it, it's unmaximised when you open it again?

---

### Post by coffeecat on 2011-01-29
> **Quackers said:**
> Doesn't FF open in the state that you closed it in? ie if it's unmaximised when you close it, it's unmaximised when you open it again?


I'm fairly sure I've tried that, but I'll try it again. Back in a mo'.


**EDIT**: Nope. Closed it with a sensible unmaximised size. Waited a few seconds, clicked on the Firefox icon in the dock and it opened maximised.

---

### Post by mc4man on 2011-01-29
>  I did have to pull a window down with alt+left-click before I noticed the dead zone,
It's by nature a very random occurrence.
As I mentioned in another thread one way to increase the likelihood of having a window 'buried' is to open synaptic > maximize and then close synaptic.

After that there are several good candidates to become 'buried', update manager is one. (may take a few tries.
Once you have to pull a window, an invisible window is created. (only a restart will fix, it's only on 1 workspace but there are other things going on once this happens.
open bug on (I may have not titled well, not one of my strong points
[https://bugs.launchpad.net/unity/+bug/709461](https://bugs.launchpad.net/unity/+bug/709461)

Edit: pretty much any utility type window can open buried - archive manager, gparted, software sources, logout,  ect. If you don't pull the window back nothing happens, once you do the in. window is created

> Doesn't FF open in the state that you closed it in? 

To a degree - currently unity has a 60% cutoff, all windows at 60% or more of available screen area are automaximized, those at 59% or less will open to size closed.

Personally think that 60% is too small, have asked for a larger cutoff (75%), we'll see
(I use 80% here

---

### Post by Quackers on 2011-01-29
Hmm, what about manually resizing the window to a size of your choosing. Then closing FF and re-opening. Any difference?

---

### Post by andrek on 2011-01-29
> **coffeecat said:**
> You'll just have to get yourself a new laptop with an ATI card. :p Think about it: compiz and gee-whiz effects without having to install a proprietary blob. Uncorrupted Plymouth splash. The pleasure of using a make of card that most on this forum tell others to avoid. (I like being ornery.) Bliss! :)

...except for proper power management support. Meh, I'll stay with the "proprietrary blob", that is fglrx. :)

---

### Post by mc4man on 2011-01-29
> Hmm, what about manually resizing the window to a size of your choosing. Then closing FF and re-opening. Any difference? 

No, other than the values mentioned. (below cutoff you'll get the resize, over it will be maxed
Just saw that a test of the higher value should be in next unity update (3.4), assuming the suggested 75%

[https://bugs.launchpad.net/unity/+bug/708809](https://bugs.launchpad.net/unity/+bug/708809)

---

### Post by Quackers on 2011-01-29
I see. Thanks for the input mc4man :-)

---

### Post by mc4man on 2011-01-29
Quackers - 
one thing to also keep in mind - the restore button will return your app to the chosen size in most cases (if that chosen size  was opening maximized due to being on or over the value, currently 60%

---

### Post by Quackers on 2011-01-29
Ah ok, thanks. Tbh, I am maximised most of the time, except for synaptic and a few others, which I have manually resized to about 40% of the screen. I'm quite happy for FF to open full screen. But I'm on a 17" laptop, not a 24" monster, like coffeecat :-)

---

### Post by mc4man on 2011-01-29
I myself, for various reasons, like to have contact with the desktop most of the time on both a small laptop and large desktop.
In the context of this thread i think you should watch out for any window that opens in the top left corner with the window deco missing (what I call buried)

If that happens - if you can use and or close the window without moving it then no 'dead zone' should happen
If you pull any such window down into the desktop I'm 99% sure you'll get a dead zone on that workspace.

What's also interesting is the windows most likely to open this way will never open maximized by default, like update manager, gparted, software sources ect. ect. (utility type windows
if they did open maximized then they may not lose the border (be buried), in the first place.

---

### Post by Quackers on 2011-01-29
I've seen what you describe, but just now and again. The first sign for me seems to be when I click on the top panel and select restart or shutdown. Most of the time the pop up box for confirmation will be in the middle of the screen, and have borders on it. Occasionally though, it will be top left of the screen, and partially buried in the top panel. This is usually fixed on rebooting. If that happens again I will search about for a dead zone :-)

---

### Post by coffeecat on 2011-01-30
> **mc4man said:**
> To a degree - currently unity has a 60% cutoff, all windows at 60% or more of available screen area are automaximized, those at 59% or less will open to size closed.

Personally think that 60% is too small, have asked for a larger cutoff (75%), we'll see
(I use 80% here

Thanks for the explanation, mc4man. I'll look forward to the Unity 3.4 with the 75% cutoff. I agree that 60% is far too small. 

> **mc4man said:**
> In the context of this thread i think you should watch out for any window that opens in the top left corner with the window deco missing (what I call buried)

After I posted last night I got a dead zone again, but this time nearer the top left of the screen. As you suggested earlier, I tried switching to another workspace and no dead zone, which is useful.

**EDIT**: Just to add - I tried opening the various utilities that mc4man suggested, which all behaved themselves until I tried gconf-editor which opened so far to the top left that the top window bar wasn't so much buried as spilling off the top of the screen. It wouldn't respond to alt+left-click so I had to kill it from workspace 2 which, of course, left a dead zone top left. Which makes me wonder how Quackers and I managed to get a dead zone in the centre of the screen. Whatever... So I've set window placement in ccsm from "Smart" to "Centered" to see if that helps.

---

