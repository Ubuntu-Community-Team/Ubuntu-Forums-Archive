---
title: "Why I hate linux"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by Fidelity on 2007-04-29
Ok so after installing my graphics card drivers, they partially function. I can change the resolution and set up dualscreen, but the dualscreen is retarded because it forces me to use both of my monitors as 1 big one, with 1 wallpaper.

So I get it all set up to be  somewhat functional, and then it decides not to save to the Xorg.conf file, ever. Every time I log in and out or restart, it discards all my changes, and defaults back to no dual screen and my 24" monitor running at 1280x786.

So ok, I think to myself, obviously the GUI for editing the xorg config file was made by a 3rd grader with downs syndrome, I open up the xorg file and make edits to it manually using the nano text editor.

Guess what happens next, yeah I messed something up and it renders my ubuntu install a black screen with a blinking white line.

I posted on these boards for help yesterday in a very cool and composed manner and got no answer.

So lets recap: Linux forces a user whos been using the OS for a matter of hours to edit a crucial system file because the GUI for it is broken, which ends up breaking the installation. I post on here for help and no one responds. User friendly? I love it, thanks Ubuntu! Because of you im back on Windows XP.

---

### Post by Swab on 2007-04-29
> **Fidelity said:**
> Ok so after installing my graphics card drivers, they partially function. I can change the resolution and set up dualscreen, but the dualscreen is retarded because it forces me to use both of my monitors as 1 big one, with 1 wallpaper.

So I get it all set up to be  somewhat functional, and then it decides not to save to the Xorg.conf file, ever. Every time I log in and out or restart, it discards all my changes, and defaults back to no dual screen and my 24" monitor running at 1280x786.

So ok, I think to myself, obviously the GUI for editing the xorg config file was made by a 3rd grader with downs syndrome, I open up the xorg file and make edits to it manually using the nano text editor.

Guess what happens next, yeah I messed something up and it renders my ubuntu install a black screen with a blinking white line.

I posted on these boards for help yesterday in a very cool and composed manner and got no answer.

So lets recap: Linux forces a user whos been using the OS for a matter of hours to edit a crucial system file because the GUI for it is broken, which ends up breaking the installation. I post on here for help and no one responds. User friendly? I love it, thanks Ubuntu! Because of you im back on Windows XP.

Get what you pay for I guess.

---

### Post by collieman on 2007-04-29
> **Fidelity said:**
> Ok so after installing my graphics card drivers, they partially function. I can change the resolution and set up dualscreen, but the dualscreen is retarded because it forces me to use both of my monitors as 1 big one, with 1 wallpaper.

So I get it all set up to be  somewhat functional, and then it decides not to save to the Xorg.conf file, ever. Every time I log in and out or restart, it discards all my changes, and defaults back to no dual screen and my 24" monitor running at 1280x786.

So ok, I think to myself, obviously the GUI for editing the xorg config file was made by a 3rd grader with downs syndrome, I open up the xorg file and make edits to it manually using the nano text editor.

Guess what happens next, yeah I messed something up and it renders my ubuntu install a black screen with a blinking white line.

I posted on these boards for help yesterday in a very cool and composed manner and got no answer.

So lets recap: Linux forces a user whos been using the OS for a matter of hours to edit a crucial system file because the GUI for it is broken, which ends up breaking the installation. I post on here for help and no one responds. User friendly? I love it, thanks Ubuntu! Because of you im back on Windows XP.

That's where I'm at right now too......back on XP.   Had to take a nerve pill after hours of fighting Linux.

---

### Post by Uriel2006 on 2007-04-29
> **collieman said:**
> That's where I'm at right now too......back on XP.   Had to take a nerve pill after hours of fighting Linux.

Think i don't understand is why people leaving something is so much interested to make aware people remaining.....

Anyway, good luck with your XP....

Uriel

---

### Post by jondecker76 on 2007-04-29
It took me a while to figure out, but if you are using the NVidia panel with an NVidia card, in order for changes to be saved to xorg.conf, it must be opened with as root

I.e. at the terminal, gksudo nvidia-settings

Also, dual monitors can be set up as a single screen, or even as separate x sessions. I run dualscreen with NVidia twinview. To have different wallpapers on both screens, you just need to make a wider image out of 2 separate images.

I was frustrated by the same things when I first started, but if you look around a bit, the answers are out there

---

### Post by floke on 2007-04-29
Your first post was hardly 'composed':
--
Ok first off, I'm running Kubuntu (feisty fawn) with an 8800GTX.

I got the driver and x server installed fine.

However, dualscreen refuses to work. Twinview will work, but it sees my 2 monitors as one large one, and wont let me set things like wallpaper independently.

When I try setting them to "separate x display", it only displays an image on my secondary monitor. So pretty much there is no way for me to get a practical dualscreen setup in linux. It works fine under XP using dualview.

The second problem is that "Nvidia X Server settings" REFUSES to save my display settings, so whenever I log out or restart, my 1920x1200 screen goes back to 1280x768

I'm about to go back to XP, this is ridiculous.
--

Maybe you should have looked around - try the Google or there's a rather useful search facility in the top right hand corner of the ubuntu forum screen. Maybe it was designed by a 'retard' and you missed it. Maybe it should be 6 feet tall in bright flashing neon for you. Maybe waiting a whole 20 hours without a reply to a post is simply unacceptable, 

Maybe Linux is just too hard for you. 

Enjoy XP :)

---

### Post by hosk on 2007-04-29
So, in answer to his problem for future reference....

His settings saved problem was that he didn't sudo edit the file?

---

### Post by the8thstar on 2007-04-29
You must admit that it's hard to find answers when you're a newbie, because you often don't know what the problem is.

---

### Post by silkstone on 2007-04-29
I configured my graphics card with nvidia-settings (no gksudo) and they were lost on reboot, UNTIL I called up nvidia-settings again from the terminal and then the previous settings were applied again without me resetting them.

So I went System>Preferences>Sessions>Startup tab and added nvidia-settings to the start-up list with the line nvidia-settings --load-config-only, and that does the job. I'm not sure if it works in all cases.

---

### Post by floke on 2007-04-29
True. But don't rant about it in an infantile manner.
There's plenty of stuff that I can't get working properly, but hey that's life!
Get over it.

---

### Post by WinterWeaver on 2007-04-29
Patience is a virtue.....

If I had such a short attention span, I would be off ubuntu months ago. However, perseverance, eventually taught me much more than I ever knew.

I started out as  a complete Linux newbie, but after about 1 year, I now know a lot more that when I started, was able to help 2 friends set up ubuntu successfully, and I have the freedom in using my PC the way I want to use it, without being bound by commercial products (even though I still use a couple of preferred commercial apps).

But I guess that some people prefer being spoon fed, while others enjoy to grow from challenges presented to them.

Good Luck and have fun with your XP.

WW

---

### Post by Fidelity on 2007-04-29
Ok, I got dual monitors working and I got it to save my settings.

One more problem, my primary and secondary monitors are switched.

the icons and taskbar appear on my secondary monitor, not my primary. How can I switch them?

---

### Post by floke on 2007-04-29
You still here?

---

### Post by Fidelity on 2007-04-29
Yes i'm still here. Help. Please.

---

### Post by WinterWeaver on 2007-04-29
Open up the xorg.conf file with a text editor and paste the contents for us here pls ^_^

the file is located here:
/etc/X11/xorg.conf

thx

EDIT: PS - I'm going home from work now... will only be back online in about 1 hr

---

### Post by floke on 2007-04-29
Fidelity, I have no idea how to help on this problem.
There are plenty of people here who I'm sure will do their best to help you out.
I'm sure you'll get it fixed.

Hope it all works for you so you can dump that XP pile of crap and stop ranting about how you want to run back to it when really we all know you don't :) 

Good luck

---

### Post by Fidelity on 2007-04-29
> # nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:39:38 PST 2007

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTX"
    Option         "AddARGBLXVisuals" "True"
    Option         "RenderAccel" "True" 
    Option         "AllowGLXWithComposite" "True"
    Option         "backingstore" "True"
    Option         "TripleBuffer" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: 1440x900 +1920+300, DFP-1: 1920x1200 +0+0; DFP-0: nvidia-auto-select +800+0, DFP-1: 800x600 +0+0; DFP-0: nvidia-auto-select +640+0, DFP-1: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

______________________________

I added the lines 
>     Option         "AddARGBLXVisuals" "True"
    Option         "RenderAccel" "True" 
    Option         "AllowGLXWithComposite" "True"
    Option         "backingstore" "True"
    Option         "TripleBuffer" "True"

in an attempt to get Beryl working. Whenever I start beryl, there are no window borders. I cant resize or minimize or maximize windows :(
Edit: Got beryl working :D But my primary and secondary monitors still are not switched :(

---

### Post by floke on 2007-04-29
Option "AddARGBLXVisuals" "True"

Should be "AddARGBGLXVisuals" "True"

For the window borders you might need to open up emerald (right click the beryl icon in the system tray) and make sure that the window decorator is set to Beryl

---

### Post by WinterWeaver on 2007-04-29
OK... I'm home

here's what you need to do...

in your device section of the xorg.conf
(this section)
```
Section "Device"
Identifier "Videocard0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GeForce 8800 GTX"
Option "AddARGBLXVisuals" "True"
Option "RenderAccel" "True"
Option "AllowGLXWithComposite" "True"
Option "backingstore" "True"
Option "TripleBuffer" "True"
EndSection
```

Add the following line

```
Option "TwinViewOrientation" "RightOf"
```

This can change to any of the following, to have your secondary monitor in different places
```
"RightOf"  (the default)
    "LeftOf"
    "Above"
    "Below"
    "Clone"
```

hope it helps

---

### Post by Fidelity on 2007-04-29
This didnt help :(

The orientation is correct, it is displaying the one monitor right of the other, its just that the wrong monitor is set to primary.

My 24" should be the primary, not the 19".

My icons are currently all on the wrong monitor.

---

### Post by WinterWeaver on 2007-04-29
ok... easiest thing to do ... which is quite funny lol

easiest way is to the monitor cables around.

the primary monitor is usually the normal plug, while the secondary is the funny adaptor type plug.

so if you just swap the two around, you should have it display on the correct one.

lemme know... ^_^

---

### Post by Fidelity on 2007-04-29
Im hesitant to do this because the primary and secondary was correct until I screwed up my xorg and had to reset it. There must be some way to switch them without physically switching them. This would mess up my windows dualscreens too.

---

### Post by WinterWeaver on 2007-04-29
hmm... I understand what you mean....

Lets see if there is anyone else that can answer that one.... cause this is a problem which I've not come across with myself.

I'll have a wee poke around quick, and see if I can dig up anything else.

---

### Post by WinterWeaver on 2007-04-29
Ok, I think you can have a look here for a solution, as I'm out of ideas. 

[http://ubuntuforums.org/showthread.php?t=301946&highlight=twinview](http://ubuntuforums.org/showthread.php?t=301946&highlight=twinview)

I reccomend you make a post on that thread explaining the problem, and to see if anyone can help you out. People are probably only reading the first couple of posts in this thread, and then moving, on, because they think it's another rant (the way it started out).

A New thread may also do the job, but remember to be patient.

you can also do a search for Twinview, Xorg, Nvidia etc.

I hope that you find the solution, and dont give up to soon.

WW

---

### Post by Fidelity on 2007-04-30
Still have not found a solution :(

---

### Post by misconfiguration on 2007-04-30
Linux doesn't work well with people that have no patients and a defeatist attitude. You shouldn't EXPECT anything out of the community in the first place, it was your choice to give it a whirl, blame yourself.

---

### Post by PhatStreet on 2007-04-30
> **Steve.K said:**
> True. But don't rant about it in an infantile manner.
There's plenty of stuff that I can't get working properly, but hey that's life!
Get over it.
I recently installed Kubuntu on a laptop of mine, and nearly everything works perfectly out-of-the-box. But multimedia keys and suspend don't work at all. Its ATI video card also required a small fix. But after a few hours of research, its usability is amazing.

To expect a free OS to have no hardware problems at all is just as retarded as blaming MS for the driver problems in Vista. Yeah, I know most people here hate MS, but they aren't the ones supposed to be writing the drivers. The companies are. Likewise, you can't rant off on the OSS community because the drivers/modules they've written don't work perfectly with closed hardware.

---

### Post by dante.regis on 2007-05-01
> **the8thstar said:**
> You must admit that it's hard to find answers when you're a newbie, because you often don't know what the problem is.

sure, but even then, there's no reason to call the volunteers that develop gui version of complex configurations (and even the builders of everything else) retards or with "down symptoms" just because you were not patient enough to look for the answers. 20 hours the friend told us he waited. Well, what can I say

---

### Post by stchman on 2007-05-01
> **Fidelity said:**
> Ok so after installing my graphics card drivers, they partially function. I can change the resolution and set up dualscreen, but the dualscreen is retarded because it forces me to use both of my monitors as 1 big one, with 1 wallpaper.

So I get it all set up to be  somewhat functional, and then it decides not to save to the Xorg.conf file, ever. Every time I log in and out or restart, it discards all my changes, and defaults back to no dual screen and my 24" monitor running at 1280x786.

So ok, I think to myself, obviously the GUI for editing the xorg config file was made by a 3rd grader with downs syndrome, I open up the xorg file and make edits to it manually using the nano text editor.

Guess what happens next, yeah I messed something up and it renders my ubuntu install a black screen with a blinking white line.

I posted on these boards for help yesterday in a very cool and composed manner and got no answer.

So lets recap: Linux forces a user whos been using the OS for a matter of hours to edit a crucial system file because the GUI for it is broken, which ends up breaking the installation. I post on here for help and no one responds. User friendly? I love it, thanks Ubuntu! Because of you im back on Windows XP.

You are free to NOT use Linux ever again.  Patience is a virtue.  You will find that Linux has a great deal of flexibility and no one telling you that you have to use the OS ina  certain manner.  With Windows M$ tells you what to do, how to do it, etc.

---

### Post by amaroKer on 2007-05-01
> **Steve.K said:**
> 
Maybe Linux is just too hard for you. 


:lolflag:

---

### Post by emil10001 on 2007-05-03
I have a dual head setup at home (not here at work) and I understand that getting the orientation correct can be a bit frustrating. If I were you, I'd get used to looking at the pseudo term screen until you can get this thing figured out properly. Start by backing up your xorg.conf file (very important). Then start tinkering with it until you get it where you want it. 

The first couple of times that you do this, and just sit there and pound away at it, will be cumbersome and tiring, but after that you should have a pretty good idea of what to expect in the future if you need a specialized setup (as currently dual-head is not the norm). 

I also noticed that you only had one device section, one screen section, and one monitor section. You should try splitting them up into different sections to make it more managable, and to get different x sessions on your two screens (not xinerama). 

I'd also google "ubuntu dual head xorg.conf" to get an idea of what other people's xorg.conf files look like. I'll post mine to give you an example of what a dual head config file should look like, with multiple sections for each screen, device and monitor. Then you can take examples from that config file (don't just drop it in there because i likely have different settings for my setup than what you want).

Also, get used to the command line, because while it may not be necessary to get things done, it is one of the things that makes linux so powerful. It also makes fixing things much easier and quicker. And be patient, I know that getting some of these hardware things to work can be frustrating, the display being at the top, but the payoff, a good sense of accomplishment and the knowledge gained, is generally well worth the trouble.

---

