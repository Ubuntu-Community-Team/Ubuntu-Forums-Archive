---
title: "Nvidia drivers makes screen blue/purple"
date: 2008-12-27
forum: Multimedia Software
---

### Post by hougSTAR on 2008-12-27
Yo.

So this is my first time with Linux, and I'm not getting anywhere far as of yet. 

My video card is a GeForce 6200 AGP, when I install the drivers it causes the Ubuntu desktop and everything else to be bluish and purple-ish tinted.  I can't change it, even adjusting the Hue in the Nvidia Server settings doesn't do anything. 

I installed it via the Hardware Drivers selection, in fact I installed ALL 3 of the drivers in hopes that one would work.  Am I needing to adjust anything to make this bugger display properly?

Nvidia Linux Driver- 177.82

---

### Post by hougSTAR on 2008-12-28
Update-

Uninstalled Nvidia drivers, and installed the Envy program.  I selected the Compatible and Recommended Nvidia driver (173 I believe) and it does the same thing.

Thought- Could the funk color be due to me running a S-Video cable from the video card, to a Composite converter to my HDTV be the cause?

---

### Post by wackston on 2009-01-03
Very likely.  Mostly likely you've got a TV expecting PAL and your card producing NTSC (or vice-versa).   Aside: picture quality will be loads better attaching S-Video directly.

---

### Post by hougSTAR on 2009-01-03
Thanks.

How is it that Windows is displaying it just fine though?

---

### Post by hougSTAR on 2009-01-03
Well now I have another issue.

S-Video now works

But, I want to run it in Component.  When I change over to component, it is all blue again.  I was told I can change the Xorg.conf file to recognize it, but I cannot save the changes I make on the bugger.

Secondly, now Windows XP Pro will not display, after the loading screen.  Its just a bunch of lines flickering upward- any ideas?


FYI: I am using a breakout adapter that has Component, S-Video and a composite connection.

---

### Post by wackston on 2009-01-04
If you can't save your xorg.conf changes you probably forgot to edit
with root priviledges (the file is owned by root).

sudo "your editor command " 

to edit using root priviledges.

Aside: it is usually impossible to use 60Hz Component outputs for 50Hz HDTV.  This is a PAIN ff you're trying to 50Hz SDTV/HDTV content as you *really* *really* want to use a 50Hz output (the judder watching 50Hz with a 60Hz display refresh is hideous).

---

### Post by hougSTAR on 2009-01-04
Thanks for your help, I finally got the Xorg.conf file altered and it now sees my Component connection perfectly (wow, that's a major quality improvement).  Windows also sees the component connection, I just didnt set the bugger to use it.

---

### Post by usafaviator on 2009-01-04
I've seen quite a few different Xorg.conf modifications on the bulletins, many of which appear to be no longer valid thanks to 177.  Can you tell me what specific changes you made to your file to fix this problem?  Much appreciated...

---

### Post by dornelas on 2009-08-03
I've been having the same issue for a few years now.  When I connect my Nvidia 6200 AGP card up to multiple TVs via component and use the nvdia driver (v73 - 180) the screen has a blue hue as soon as X starts.  

While the system is booting up, including the graphical boot screen, the display is fine.  If I use the nv driver the display is also fine, so that's what I've been using all this time.  The problem with that is all of the TV screen isn't used, and boxee won't work without 3d acceleration.  

The following thread seems to have a plausible explanation:

[http://ubuntuforums.org/showthread.php?p=7607743](http://ubuntuforums.org/showthread.php?p=7607743)

> It's not the cable. I have had the same issue on a number of "HDTV-enabled" nvidia boards with the 7-pin S-video connection on them. I have the same "s-video-to-component" cable you mention. In my experience the blue tint issues are Linux-specific.

I believe it happens because the TVs we're using are expecting YPrPb (also known as YCrCb, and/or component HDTV) color coding.

The problem is that once under Linux driver control, the boards are being put into RGB mode for that connection. Some televisions are capable of receiving RGB video over component cables, but as far as my research goes these are few and far between. The vast majority of HDTVs with component video expect YPrPb, so we need to find a way to tell our nvidia drivers (likely by way of a modeline in xorg.conf) to switch back to that mode.

Under windows, the last few revisions of the Nvidia ForceWare drivers have a software switch in the Nvidia Control Panel applet that allows you to switch between RGB and YPrPb modes for the svideo-to-component connection (a setting you wouldn't have unless the board detects this special cable as being connected to the board and terminated on the other end by component cables on a TV, same as with older s-video- or component-only boards that wouldn't show settings for those connection unless you had a corresponding cable attached to a device. My old TNT2 with s-vid in & out comes to mind.)

As I don't use Ubuntu on a machine connected to a TV, I can't test the latest drivers for this software switch in the Nvidia settings panel, but I fear this is likely the only way forward, save for the modeline shenanigans.

but so far no solution.  Does anyone have any ideas?

---

