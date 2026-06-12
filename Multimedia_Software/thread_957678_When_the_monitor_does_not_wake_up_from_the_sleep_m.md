---
title: "When the monitor does not wake up from the sleep mode"
date: 2008-10-24
forum: Multimedia Software
---

### Post by Uikku on 2008-10-24
After certain amount of time of idleness the monitor goes into power-saving mode. That is, goes to sleep. Then pressing any key or moving the mouse should wake the display up. This is the normal behavior, something that one would expect to happen.

For some reason on my multiple user system the display woke up only occasionally. More often it did not. Then I had to turn off the monitor from the power switch and the back on again. That helped, but it was quite frustrating. Searching the net and forums consumed time but brought no help.

I figured out that with the users who had not changed the power-saving or screen saver settings the monitor acted normally. After some experimenting I found out that personal power-saving and monitor settings are stored in **.gconfd/saved_state** and **.nvidia-settings-rc**. So I renamed both of those files with **.old** extension to disable them.

For now it seems that the monitor is back to normal behavior. It wakes up as it should. But why does altering the time of inactivity after which the monitor goes to sleep or screen saver activation time would cause the monitor not waking up?

I'm running Ubuntu Hardy on Asus P5k se/epu motherboard, Asus nVidia en7300gt Silent graphics card and Acer x243w monitor.

---

### Post by xyphur on 2008-12-12
I have the same Acer X243w, and it's been doing this to me under Ubuntu 8.10, Vista Ultimate, and XP Pro SP3. No rhyme or reason to it. I personally think it has something to do with the monitor itself and not necessarily the power scheme set in the OS.

For comparison's sake, mine is currently connected via DVI to an nVidia 7300 PCI-E x16 low-profile card in a Dell GX280 Small form factor desktop (P4-HT 3.0GHz, 4GB DDR2 800, etc, etc) but has been tested on a few other machines, and the results were always the same. Intermittent failure to resume from suspend with mouse/keyboard activity.

---

### Post by jeperezd on 2009-01-24
I have the same problem in my desktop. I thought it was due to my special configuration. I have a Full HD TV connected wwith HDMI to my nvidia 8600 card. Recently I have changed (the old died) to a nvidia 9800GT card, but it didn't help at all.
I also have multiuser envinronment but I haven't seen any difference when I'm with one or more users logged at the same time.
The only solution is to rebot or to switch off completely the TV (disconnecting the power).
This problem I had it with my Ubuntu 8.04 and with a fresh install of 8.10. I usually kept the nVidia drivers up to date, so it seems it doesn't have any relation with it.

Any ideas?

---

### Post by JavaBeanHead on 2009-08-05
Hi Uikku . . . I see that you have an ASUS EN7300GT Silent card . . . I cannot for the life of me get it to work correctly.  I'm running in "low-graphics mode" (new install here).  Can you give me a walkthrough of installing the correct drivers for it?

Any advice would be trememdously appreciated.

Thanks.

---

### Post by xyphur on 2009-08-05
JavaBeanHead: As is the case with almost any nVidia card under Ubuntu these days, drivers for yours can be enabled (read: automatically detect correct version, then download & install it) under System > Administration > Hardware Drivers.

Enable the recommended one if given multiple choices, provide your password when prompted, it'll apply all changes, and then a reboot will be necessary. That's all there is to it.

---

### Post by JavaBeanHead on 2009-08-05
Xyphur,

Thanks for the reply.  Sadly, I've done this, and I'm not getting the resolutions I'm after.  Trying to figure a way to get a resolution higher than 1024x768. :(

---

### Post by xyphur on 2009-08-05
Make & model # of your monitor?

---

### Post by JavaBeanHead on 2009-08-05
My apologies (and geeeez you're quick!) KDS [K-22MDWB]("http://www.kdsusa.com/K22mdwb.asp").

---

### Post by xyphur on 2009-08-05
Forgot to ask, analog or digital connection?

And what version of Ubuntu also?

(When I notice someone I'm trying to help out is online, I lurk around and hit F5 until there's a new post ;) )

---

### Post by JavaBeanHead on 2009-08-05
Oh . . . analog, and 8.10.  But before I go any further . . . I am not quite sure what happened here, but I fixed it.  

First of all . . . relative n00b here . . . I have to learn NOT to use System >> Preferences >> Screen Resolution when using an NVIDIA card . . . gotta change screen resolution via System >> Administration >> NVIDIA X Server Settings.  

But that wasn't the core of the problem because even the NVIDIA X Server Settings wasn't giving me the resolution I wanted.  After creating about 5-6 different versions of my xorg.conf file . . . and even installing/uninstalling envyng-gtk . . . I resorted back to the xorg.conf.failsafe.  

```
cp xorg.conf.failsafe xorg.conf
```Reboot.

It finally came out of low graphics mode. *whew*

Anyway after reading a bajillion threads on the subject, I was convinced that it had to do with the HorizSync and VertRefresh issue but had not gotten it to work.  So after going back to the drawingboard with the failsafe xorg.conf, I simply added the HorizSync and VertRefresh values specific to my model of monitor an NOTHING ELSE. 

No 
```
Option          "UseEDID"                       "False"
```in the Device section.

And no
```

Section "Screen"
              Identifier      "Default Screen"
              DefaultDepth    24
              SubSection "Display"
                           Depth           24
                           Modes           "1680x1050"
              EndSubSection
EndSection
```either.

Lesson learned: Start with the xorg.conf.failsafe file to be at ground zero, work your way up.  No EnvyNG (just not specific enough, and it was enough to throw me off completely because I used that as a springboard to start editing a dirty xorg.conf file.

Threads that helped me out most:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Ubuntu%207.10](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Ubuntu%207.10)
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/91292](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/91292)
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Sir I am greatful for your attempt, and I'm sorry if I've wasted your time.  I can only redocument what I have not found yet, and hope that it makes things better. 

Now, off to fix a printer that won't connect.

---

### Post by xyphur on 2009-08-05
Glad you managed to get everything going. No worries about time, I have no qualms in lending a hand, anything to benefit the community. More information = less problems for everyone. :)

Also, I would really recommend you pick up a DVI cable... super cheap. The inter-device capabilities information exchange seems to work better than DDC ever did over analog (at least in my experience)... and, y'know, a better picture. ;)

---

### Post by JavaBeanHead on 2009-08-06
Thanks for the advice.  Running a  KVM Switch . . . no DVI possible a the moment . . . but . . . 

Ohhh man . . . I want so badly to be like you guys . . . I work in IT, and I feel pretty adept at normal geekery . . . but Linux is a relatively new world. 

Help a brother out (and I know you will).  Whenever I reboot, it goes back to a default resolution.

Why?

---

### Post by xyphur on 2009-08-06
I'm totally guessing here, but based on something I saw in another forum post (I think?) you may try running the nvidia-settings applet with sudo from the terminal (instead of launching it from the System submenu), as it may require inherited priviledges to write out the configuration file for use on next reboot... Again though, completely guessing here - albeit an educated one ;)

I imagine a quick googling should turn up a few related posts if that doesn't do the trick though... most nvidia stuff is quite well documented, even under Linux.

---

### Post by JavaBeanHead on 2009-08-09
That did it: sudo nvidia-settings

A gentleman, and a scholar.  Thanks again . . .

---

### Post by juliobahar on 2009-12-10
Hey Guess this thread started with a topic and ended with a very different one. 
The main topic should be "Monitor not waking up from sleep" not how do you install non-proprietory driver.

Please post new threads for different topics.

Thanks

---

