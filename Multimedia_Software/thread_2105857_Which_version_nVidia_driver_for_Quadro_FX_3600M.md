---
title: "Which version nVidia driver for Quadro FX 3600M?"
date: 2013-01-17
forum: Multimedia Software
---

### Post by aplonis on 2013-01-17
Which nVidia driver for 12.04 LTS best suits the Quadro FX 3600M installed in my Dell M6300?

This same laptop used to work fine on either of two 1920x1080, second monitors prior to my upgrade from 10.04 LTS to 12.04 LTS. Now I have the white-screen issue (from Nautilus) making any second monitor completely useless. It is causing me to have to boot that same laptop as Vista whenver I want to watch a video. Very annoying.

So my thought is that I have somehow saddled myself with a too-new nVidia driver on the upgrade. But I've failed to identify which prior driver I had ought to downgrade myself to, the Quadro FX 3600M being proprietary to Dell and not mentioned definitively in any docs that I've so-far obtained.

---

### Post by lukeiamyourfather on 2013-01-17
That's not a special chipset, other vendors use it too. Any driver from Nvidia for the last few years should support it. Have you installed the proprietary drivers from Nvidia using the Ubuntu hardware drivers utility?

---

### Post by BicyclerBoy on 2013-01-17
I suspect the OP is seeing "separate X screens" with unity desktop.
Last time I tried, it was disgraceful..

From terminal in screen 0 (<ctrl>+<alt<+<T>):
export DISPLAY=:0.1 gnome-terminal

Do you get another terminal on the white screen?

Option:
- don't use unity
- use "twinview" (not optimal for full screen video)
- try "mosaic" (this is enabled for quadro cards)

---

### Post by aplonis on 2013-01-17
> **BicyclerBoy said:**
> 
From terminal in screen 0 (<ctrl>+<alt<+<T>):
export DISPLAY=:0.1 gnome-terminal

Do you get another terminal on the white screen?

Yes, that's it exactly. When I boot to Ubuntu with an external monitor plugged in (supplementary to the to the laptop screen), what happens is first I get the artsy magenta background on both screens. One second later the external monitor turns white. I get a curser there which moves as expected (an arrow, not the X). 

Then, with the curser on that monitor, typing CTRL-ALT-T as you describe gives me a normal looking terminal.

The white is from Nautilus, I read. And sure enough, by killing Nautilus the white goes away. But doing without Nautilus is hardly an option.

Anyhow, I had no such problem at all before upgrading to 12.04 LTS from 10.04 LTS so my thought was that maybe my video card was too old for the new nVidia driver. If that were the case, I thought maybe backpedalling to an older nVidia driver might be the fix. Hence this particular thread. So that's not it then? I just have to wait and maybe later it will get fixed? Any idea how I'd know when that happened other than searching, searching, searching for a SOLVED tag on the topic?

---

### Post by BicyclerBoy on 2013-01-18
Can you please re-read my previous post..

FYI Your card supports VDPAU feature set A..

---

### Post by aplonis on 2013-01-19
> **BicyclerBoy said:**
> I suspect the OP is seeing "separate X screens" with unity desktop.
Last time I tried, it was disgraceful..

From terminal in screen 0 (<ctrl>+<alt<+<T>):
export DISPLAY=:0.1 gnome-terminal

Do you get another terminal on the white screen?

Option:
- don't use unity
- use "twinview" (not optimal for full screen video)
- try "mosaic" (this is enabled for quadro cards)

gus@m6300-laptop:~$ export DISPLAY=0.1 gnome-terminal
bash: export: `gnome-terminal': not a valid identifier
gus@m6300-laptop:~$ 

Above is what it says back at me, if that's what I was supposed to have reported. Don't know what "mosaic" is. Will have to look it up.

---

### Post by BicyclerBoy on 2013-01-19
Fair enough..

You made a typo with my cmd:
[COLOR="SeaGreen"]export DISPLAY=:0.1[/COLOR]

Your card is supported by the lastest nvidia drivers.
Anything from 275 - 313..

Do not attempt to download/install from nvidia website; it is a recipe for pain & heartache for zero gain..

You can try "twinview" or "mosaic" (possibly) from:
nvidia-settings

Only quadro (& gt440?) owners get the chance to try mosaic, so I have never seen/used it.

Seperate X screens is/was very badly supported by unity 12.04.

---

### Post by aplonis on 2013-01-20
Okay, got it to work, sort of. Mosaic does not show up as an option even though (all on its own) Ubuntu presented a series of updates to install, which I okay'd. Among them was one for "nvidia-current" and required a reboot at the end. So I'm up-to-date as of yesterday on the video driver. Or should I prevent it from doing that?

It was after then that I looked for Mosaic, and not finding it, chose Twin View from the nVidia driver's menu. That done, the white background on the Panasonic TV (my 2nd monitor) went away. An error message also splahed, momentarily across the screen saying something about settings not working. But the white was gone. 

So that's a definite improvement, although not quite all that I need as the vertical task bar is also repeated along the left and my desktop icons are duplicated on that 2nd monitor. I don't mind them being in the way, but the Panasonic is a plasma and they'll burn in over time. 

If now I could make them to go away, I could choose a black desktop background (just like I do for MS Vista) and the plasma screen would not burn in.

So this is good in that I can use the big screen for videos without having to boot to Vista when I've a project going on Linux and only want to be taking a little break. But I can't use the big screen for something like Blender with a tutorial on the little screen at the same time, which is also a goal. If the icon's and scrolling task bar weren't also there, I could have 90% window on the plasma for whatever and move it around from time to time like I had used to do before updating to 12.04 from 10.04.

If I had the funds I'd trade in the plasma for an LED and call it good.

---

### Post by BicyclerBoy on 2013-01-20
Unity has settings to control it's dock/taskbar.
Make sure you are not mirroring.

Unity is a compiz plugin.
There is config tool for compiz (ccsm), ignore the warnings at your peril.

Remember the command:
unity --reset

You could try a non-Unity window manager & separate X screens.
Unity just does not work properly..
IMO Separate X screens is best for full screen video playback because you have complete independent video modes & full VDPAU performance.

You can launch apps to either screen by launcher scripts & just be "clicking" on required screen.

Using separate X screens:
In a terminal or launcher script...
export DISPLAY=:0.1 blender

---

### Post by aplonis on 2013-01-20
Thank you, BicyclerBoy, for your helpful support. I used to have a lot more time and interest in tweaking my OS (back when I ran with NetBSD) but switched to Ubuntu some years ago when the ex-wife tossed my computer (and all backup HDs) out the back door onto hard bricks. Confronted with rebuilding everything from scratch I threw up my hands and went with Ubuntu. Having an OS that mostly took care of itself, I grew lazy. I'm now also at another job which consumes my at-home study time, leaving me even less inclined to dive into the minutia of fiddling with my tools.

I'm convinced now to abandon Unity at the very least. I was un-aware of the tie-in between the Unity Lens and Amazon whereby my searching for files on my PC is not truly private but opens me to being personality-profiled by Amazon (or anybody). That puts Unity at a full-stop as far as I am concerned, regardless of there being an opt-out feature. I didn't know it was there. If Ubuntu thinks they informed me, then it was buried in the small print somewhere. I'm done with Unity on that account alone, technical glitches aside. I don't trust it. Had that feature been opt-in versus opt-out, might be a different matter. Such a feature, once installed, I never trust to be completely removed. Grr, argh!

At minimum I'll have a look at Gnome. Or possibly KDE. I used both of those long ago in my NetBSD days. 

I've now stayed up past my bed-time, reading positive things about Linux Mint. As happens, my Dell M6300 has it's HD in an easy-to-swap drawer on the side (which is how I change between Ubuntu and Vista now). In my sleep-deprived paranoia I'm thinking that tomorrow I should search Ebay for a used 250GB HD on which to easily try out Linux Mint. It looks to be as maintenance-free as Ubuntu...or so they say. Guess I'll find out.

It's not a rant, I don't think, to simply state a firm distrust of any OS whatsoever that violates my privacy out-of-the-box, one where I have to delve into fine print to keep my private searches out of Amazon's (or anybody's) database. Alas and alack.

---

### Post by BicyclerBoy on 2013-01-21
install gnome-fallback-session
logout select gnome session, login...

You can remove all unity packages except unity-greeter..
You have to find an alternative greeter before removing unity-greeter else you have a X startup mess.

---

### Post by aplonis on 2013-02-03
Okay, not saying this is for everyone but my solution was easily found by an alternate route. For safety and convenience I purchased a used HD and spare (my 3rd) HD drawer caddy for the M6300. Then I DL'd and burned a live CD for Linux Mint 14. Last night I made the install on the new HD (every bit as easy as for Ubuntu). I next found a tutorial instructing me to...

sudo apt-get install nvidia-current

...followed by...

sudo nvidia-xconfig

...and it just worked. Further, all my several annoyances from Unity are gone. Although I'm on TwinView (haven't tried separate X-screens yet) all unnecessary crap on the 2nd screen is gone. And best of all, the windows are easy grab, re-size and scroll from the edge. No more hunting for that one-pixle thin line at the right side so as to make the scroll handle appear.

VLC came already installed and installing Handbrake worked exactly the same as on Ubunntu via the Stibbins PPA. Still saving my prior HD with Ubuntu 12.04 LTS just in case, but that's just me playing things safe. I expect I'll be sticking with Linux Mint. Thanks, Ubuntu, for a nice ride these past few years but I think I may have to bid you adieu. I tried, I really did, to get used to Unity. But it's just too annoying. Even were it not for that, the opt-out (versus opt-in) privacy invasion arrangement with Amazon very deeply offends. So, I'm thinking, this may be so long.

---

### Post by bogan on 2013-02-03
> **lukeiamyourfather said:**
> That's not a special chipset, other vendors use it too. Any driver from Nvidia for the last few years should support it. There is a similar Post by Bicycle-boy.  This is not strictly true.

Edit: this was Posted before reading **aplonis'**s Post #12.

According to the Nvidia.com>Download Drivers site, the Quadro FX series is not listed as supported by the latest drivers, 313.xx, and some other recent versions.

The Quadro FX 3600M is specifically listed as supported by v 310.90, and, amongst others, v 304.51, which is available in the Ubuntu version.

**BUT! ** make sure you do **not **get the: "304.51-actually-304.43" version which can give some nasty surprises when you come to remove it.

Chao!, **bogan**.

---

### Post by BicyclerBoy on 2013-02-04
I never said anything about driver releases from nVidia.
No one suggested going there..certainly not me.
Almost any driver release in 12.04 should be okay.

The salient point is/was: there is nothing special or new about quadro FX 3600M; any of the distro drivers should be okay inc nouveau.

Good warning for OP that newer driver releases, in the 12.04 pipeline, will not work.
But one of the legacy drivers should.

@OP have a look at kde, cinnamon & consort DEs.
Are you using cinnamon on mint already ?

---

### Post by bogan on 2013-02-04
Hi!, **Bicycler-Boy**,

You Posted:> I never said anything about driver releases from nVidia.
No one suggested going there..certainly not me.Nor did I suggest that route for driver installation by the OP.
Though there is always a chance the OP might have to utilize it.

I am well aware of the prejudice attached to any such suggestion, no longer - in my opinion - justified. Even the 295.40 disaster equally affected the Ubuntu versions.

I quoted from the nvidia.com drivers site as the only source I know of that lists which GPU's any driver version supports. I have seen nothing to suggest the Ubuntu proprietary versions, with the same version numbers, are any different in what they do or do not support.

Chao!,** bogan**

---

### Post by BicyclerBoy on 2013-02-05
nvidia-current in 12.04 is still 295.xx..
nvidia-updates pkg is 304..& experimental is 304/310.

The settings tool version 313 is in the 12.04 repos so may be a matter of time.

I don't have any issue with nVidia installer method & have used it in the past when VDPAU was in its infancy.

I just think it is madness to suggest this method to users who don't understand/realize the complications & can not fix their problems.
The user who knows how to solve the possible problems does not need to be told about nVidia installer method.

The OP should consider pinning the nVidia driver version (& settings tool) before it is too late.

---

