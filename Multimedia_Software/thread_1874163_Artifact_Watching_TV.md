---
title: "Artifact Watching TV"
date: 2011-11-02
forum: Multimedia Software
---

### Post by MiniVanMan on 2011-11-02
I'm Mythbuntu and I'm getting an artifact that I can describe but don't know what it is while watching TV.  First the hardware.

Dual core Intel processor (I think 2.8ghz x 2)
ATI 5450 passive video card (using HDMI out)
Hauppauge HVR-1600 Tuner Card (ATSC) for OTA transmission

57" 1080p capable LCD

The artifact is a horizontal blurry line that floats down the screen.  It looks like a deinterlacing problem.  

I threw a more powerful ATI card in the box (I had a 3870 lying around).  Didn't help.  

I get the artifact on both HD and SD transmissions.

It's an annoyance, but doesn't completely and the viewing is still completely watchable.  It is set off my motion and the football game I recorded last Sunday it was almost always there, just this thin blurry horizontal line that floated down the screen.

So, my question revolves around hardware.  It looks like MythTV supports Nvidia a lot more than ATI, but before I go out and spend the money on a capable Nvidia card (has to have HDMI out with audio) I want to make sure it's not something I should be trying to tweak in the settings.  

Any troubleshooting advice?

---

### Post by underquark on 2011-11-02
Check that the refresh rate of your output matches that which your TV can display.  Try a different refresh rate and/or resolution.

Check that both the TV and the PC are properly earthed (grounded).

Try a different HDMI cable (could be a screening/interference issue).

All this assumes, of course, that your TV works using its own tuner, the menus display OK on the TV etc. and it isn't just a TV fault.

---

### Post by MiniVanMan on 2011-11-02
> **underquark said:**
> Check that the refresh rate of your output matches that which your TV can display.  Try a different refresh rate and/or resolution.

Check that both the TV and the PC are properly earthed (grounded).

Try a different HDMI cable (could be a screening/interference issue).

All this assumes, of course, that your TV works using its own tuner, the menus display OK on the TV etc. and it isn't just a TV fault.

Brand new HDMI cable, and tried a swap.

Everything is grounded.  

TV is perfect with it's own tuner, and the same RG6 that's currently feeding the PC.

The refresh rate matches, but that's where I found my solution.  So, thank you for at least leading me to the menu that would fix the problem.  

The problem was the "Tear Free" setting was off which limits the vertical refresh rate.  With tear free on, the vertical refresh rate is set to "always on" and that eliminated my problem.  Added a new problem, but I know exactly what that issue is.  The 5450 is a dog of a card and isn't able to keep up with vertical refresh rate set that way, so I get some lag.  A little less annoying than the tear, but I can go get a better card and eliminate it all together.

Thanks!

---

### Post by MiniVanMan on 2011-12-12
Thought I would jump on and post my solution.  My solution was an Nvidia 9800 with VDPAU enabled.  It turns out the problem was with video acceleration and the ATI cards just don't have any with MythTV.  

A shame as I have a stack of ATI cards sitting in my parts bin.

---

### Post by BicyclerBoy on 2011-12-12
Believe that MythTV-0.25 will have native VAAPI support.
There is AMD XvBA support in VAAPI (with the right packages) so you will be able to get better video decode/post-proc with your HD5000.

I guess you made use of what you had at hand but the 9800GT is not the best HTPC card (feature set A & no HDA audio). The GT430/440 are much better.

---

