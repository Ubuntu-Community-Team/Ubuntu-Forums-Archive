---
title: "Upgraded and now videos won't play"
date: 2009-04-02
forum: Mythbuntu
---

### Post by Weidbrewer on 2009-04-02
I really need to learn to leave well enough alone.  I just upgraded the OS on one of my frontends to Mythbuntu 8.10, and now nothing will play.  When I click play on any videos or recordings, Myth crashes to the desktop.  Any suggestions on where to start?  Everything had been working fine up until now.

---

### Post by nasha on 2009-04-02
Start mythfrontend from a terminal, and when it crashes paste the last 10 lines from the terminal window here. This should tell us whats going wrong. I suspect mythvideo didnt upgrade smoothly

---

### Post by Weidbrewer on 2009-04-02
Okay...from the command line, it won't even full start up.  The Myth menu flashes and then goes back to the desktop.   Starting from the standard shortcut, it will start and doesn't crash until I try to play something.  Because of this, I am not able to get a commandline capture of the error that brought me here...hopefully what I have below is similar and will help.  It is what i get when run from the commandline.

```
2009-04-02 21:02:44.845 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-04-02 21:02:44.857 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-04-02 21:02:44.857 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-04-02 21:02:44.858 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-04-02 21:02:44.981 Trying 640x480 60 Hz
2009-04-02 21:02:45.250 SwitchToGUI: Switched to 640 x 480
2009-04-02 21:02:45.490 TV: StopStuff() -- end
2009-04-02 21:02:45.490 TV Error: LiveTV not successfully started
2009-04-02 21:02:45.568 DPMS Reactivated.
Segmentation fault

```


That is just the last ten lines you requested.  I have attached the full output.

Another issue that I've run in to:  The resolution comes up wonky when it boots.  If I exit out of Myth and then restart it, it recalibrates, but it resets the next time I boot the machine.

---

### Post by Weidbrewer on 2009-04-03
Update:  I fixed the resolution problem by clicking the "save session for future logins" option on the restart menu.   Still can't figure out how to fix the segmentation fault error above.

---

### Post by nickrout on 2009-04-03
> 2009-04-02 21:02:26.061 VideoOutputXv Error: Could not find suitable XVideo surface.
2009-04-02 21:02:26.064 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2009-04-02 21:02:26.095 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x879bc30) visual(0x8790598) 
                        XJ_depth(24) WxH(800x600) bpl(2400)

doesn't look good, what does xvinfo tell you?

> 2009-04-02 21:02:34.549 GLCtx: OpenGL vendor  : ATI Technologies Inc.
2009-04-02 21:02:34.553 GLCtx: OpenGL renderer: RADEON 9800 PRO

ATI, not usually a good choice I'm afraid.

---

### Post by Weidbrewer on 2009-04-03
Yes, yes - let the ATI bashing begin.  ;)  I'll say at this juncture what I always say - this box is the only one of my 5 myth machines that is running ATI, and it's also the one with the oldest equipment....yet up until this "upgrade," it's been running flawlessly for months.  Might just be that 8.10 has finally just said "screw it" to older ATI completely.  Might have to revert back to 8.04.

I'll give xvinfo after dinner when I'm accessible to that machine.

---

### Post by dtoronto on 2009-04-03
Did you try reinstalling the drivers?

---

### Post by Weidbrewer on 2009-04-03
I haven't tried uninstalling them yet...I installed the default restricted driver when the OS upgraded.

---

### Post by Weidbrewer on 2009-04-03
Okay, xvinfo yields:

```
******@Saint: ~$ xvinfo
X-Video Extention version 2.2
screen#0
  no adaptors present.

```

Doesn't sound good.  Also, not sure what changed aside from the screen resolution fix I did last night, but not it no longer crashes to the desktop - it now goes to a black screen and freezes.


What parts of my mythfrontend.log could I post that would help?  (Too large to post the whole thing.)


Other notes:  I made sure my codecs are all up-to-date, and also got my repos updated.   Like I said above, playing a video now hangs the system, and I figured out part of the reason.   Most of the work I have been doing the last few hours have been over VNC...when I actually turned on the TV, I saw that the Myth menu that displays just fine remotely is pixalated all over the place on the TV...that's obviously a problem with the graphics card/driver.

I know that ATI is not the most popular of cards, but as previously mentioned, this one worked just fine under 8.04.  Does anyone have any ideas how to get it up and running again.

---

### Post by nickrout on 2009-04-03
> **Weidbrewer said:**
> Yes, yes - let the ATI bashing begin.  

Appreciate what you say, but you will get breakages more often with ati. the drivers appear to be crap for mythtv. nVidia is usually a known good choice.

But anyway ati should still be able to use Xv, so xvinfo is the next step.

---

### Post by Weidbrewer on 2009-04-03
See my xvinfo output above.

---

### Post by Weidbrewer on 2009-04-03
Got it.  ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

That seems to have done the trick...I'm back in business.

---

