---
title: "mythbuntu setup problems"
date: 2008-02-29
forum: Mythbuntu
---

### Post by tehbeermang on 2008-02-29
I can't setup Mythbuntu. I've tried two different motherboards and two different video cards.

Here's what happens in all four combinations:

I insert the CD and boot to it. I get the splash screen and options. I have chosen several different vga options.

Next, I get the purple "knight rider" moving image and the mythbuntu logo.

I get a blinking cursor, the CD Rom goes ballistic.

Then I get a garbled line across the screen that reacts to the mouse. Then I get six Mythbuntu logos and what appears to be six columns of icons and six sets of instructions.

I tried Ubuntu 7.04 alternate, and I have the same problem after installation is complete.

The motherboards are both 4 years old. Both are running AMD Athlon chips. One was pulled from a Compaq Presario 4020. The other is an older Biostar.

The video cards are an Nvidia mx-400 (has the yellow "video out") and an ATI Radeon 9250. I installed the Radeon to test, assuming the mobo AGP was bad. My research tells me the 9250s S-Video out won't work with current drivers.

The only constant in the chain that might present a problem is the 14 year old Packard Bell VGA monitor (my newer CRT has been recycled). I have a Viewsonic LCD I could try if needed.

Should I try the LCD? It worked with Knoppix in the past.

If the monitor is not going to make a difference, what mobo/cpu/vid card should I consider?

---

### Post by laga on 2008-02-29
Yes, I'd definitely try the LCD first.

That's easier than changing hardware :)

---

### Post by tehbeermang on 2008-02-29
If I start in safe graphics mode, can I use the TV-out on my NVidia card and a CRT style television? That's where we're going to end up anyways.

---

### Post by mcgyver42 on 2008-03-27
I am having a similar problem.  Using a Biostar P4M900 motherboard with a 2.8GHz 478 Intel chip, VIA P4M900 / VT8237A chipsets.  The built in video is VIA Chrome9 HC IGP.

I'm building this system for a MythTV server, and have successfully installed Mythdora 4.0 previously.  (Didn't finish setting that up, though.)

Then I was lured away by Ubuntu, and tried Mythbuntu 8.04.  Got the "Knightrider" screen, then this:
[IMG]http://members.cox.net/mcgyver42/RS_IMG_0003.JPG[/IMG]

Hmmm.  Mythbuntu 7.10 does a nearly identical thing.  However, Ubuntu 7.10 installs just fine.

Obviously some kind of video driver shortcoming.  How would one approach this?

Can I install Mythdora on top of generic Ubuntu?

---

### Post by nasha on 2008-03-28
mcgyver42:
Every onboard video ive tried with MythBuntu procudes similar graphics issues. I suggest purchasing an aftermarket video card.
MythDora is another operating system, just like Ubuntu, so if by saying over the top you mean, removing the old OS, yes.

tehbeermang:
I dont know 100%, but theres a good chance TV-Out wont work in Safe Graphics mode, 

In regards to the video issue, ATI has known compatibility problems with linux. Steer clear of any ATI cards wherever possible, or expect issues.

I find it strange that your having issues with the mx400 as its a known working video card for mythbuntu.

By all means try changing the monitor, but i dont know how effective it will be

---

### Post by mcgyver42 on 2008-03-28
nasha:
My mistake.  I meant to say Mythbuntu, not Mythdora.  I'd like to add whatever is unique about Mythbuntu to the successful Ubuntu 7.10 installation that I accomplished last night.  Note that Ubuntu had no problems with the built-in video card.  That still implies that Mythbuntu is missing some video driver that Ubuntu includes, IMHO.

So, since Ubuntu is up and running, what does one do to convert it to Mythbuntu?

---

### Post by nasha on 2008-03-28
Install MythTV...
All MythBuntu is, is a cut down ubuntu with mythtv preinstalled

```
sudo apt-get install mythtv
```

---

### Post by mcgyver42 on 2008-03-28
Ah, yes, and I found a nice step-by-step here:

[www.mythbuntu.org/existing-ubuntu]("http://www.mythbuntu.org/existing-ubuntu")

---

### Post by laga on 2008-03-28
> **nasha said:**
> Install MythTV...
All MythBuntu is, is a cut down ubuntu with mythtv preinstalled

```
sudo apt-get install mythtv
```

No! Just installing 'mythtv' is not enough and not the smartest choice. 

But mcgyver42 already found the correct thing:

> Ah, yes, and I found a nice step-by-step here:

[www.mythbuntu.org/existing-ubuntu](www.mythbuntu.org/existing-ubuntu)

---

### Post by zmerch on 2008-03-28
> **tehbeermang said:**
> 
The only constant in the chain that might present a problem is the 14 year old Packard Bell VGA monitor (my newer CRT has been recycled). I have a Viewsonic LCD I could try if needed.

Should I try the LCD? It worked with Knoppix in the past.

If the monitor is not going to make a difference, what mobo/cpu/vid card should I consider?

I'd try the LCD, or if you want to try a fully TV-compatible install, try KnoppMyth.

The "6 copies of night rider" is caused by the video card driving the old monitor "too fast" -- at a refresh frequency that the monitor can't handle; a common occurance with very old 14" monitors that aren't Plug -n- Pray.

My MythTV box is running older hardware (1333Mhz Sempron, Nvidia GeForce 5200) and Mythbuntu didn't support a TV/SVideo install at all - once X started booting the TV would go black. However, if you're paring some newer hardware (brand new MCE2 remote in my case) in the mix, Mythbuntu is the way to go because it' s based on the 2.6.x kernel.  KnoppMyth supports older hardware a little better because it's based on the 2.4.x series kernel but doesn't support newer hardware well at all; and the X system on KnoppMyth is "archaic" to put mildly - if you're used to a KDE- or Gnome-based X experience, you'll find Knoppmyth's GUI... a bit daunting. ;-)

Using Synaptic as a package manager is much more "polished" for getting updates and/or installing new software than what's available with KnoppMyth.

Hope this helps!
Roger "Merch" Merchberger

---

### Post by laga on 2008-03-28
> **zmerch said:**
> 
 KnoppMyth supports older hardware a little better because it's based on the 2.4.x series kernel

Knoppmyth was using a 2.6 series kernel last time I tried it.. and that was almost 2 years ago :)

---

