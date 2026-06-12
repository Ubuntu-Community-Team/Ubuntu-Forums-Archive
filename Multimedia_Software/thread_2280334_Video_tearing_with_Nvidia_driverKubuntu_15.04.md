---
title: "Video tearing with Nvidia driver/Kubuntu 15.04"
date: 2015-05-29
forum: Multimedia Software
---

### Post by imrazor on 2015-05-29
I have an NVidia GTX 670. In the past (ie, with previous versions of Ubuntu and Mint) I've had an aneurysm inducing problem with tearing, both in video playback and with desktop effects. In the past, I've been able to workaround the issue by 1) disabling compositing and 2) using the VDPAU plugin for whatever video player I'm using (currently VLC.) However, these fixes did NOT remedy the problem with Kubuntu 15.04, for whatever reason. Since I'm really pleased with the KDE 5 Plasma desktop, I decided to go the extra mile and dug out an old ATI Radeon 5750. I turned on the very effective "Tear Free Desktop" feature in the Catalyst control center, and presto! no more tearing. 

Now the problem with this solution is that I still have my old GTX 670 taking up space and power in my rig for Windows gaming, I have a really weird monitor config, and the performance of the 5750 is not even close to the GTX 670. 

TL; DR Does anyone know how to fix video tearing with the NVidia driver and the KDE 5 desktop?

---

### Post by kryten35 on 2015-05-30
I tried plasma 5 for a short while and decided against it.But i remember i was getting tearing with the nvidia driver. GT640 card.  Theres different options for V-sync in the compositor and one of them fixed it.I think it was called  complete screen repaint or something like that.I had to play around with the settings for a while before i worked out how to fix it.

---

### Post by imrazor on 2015-05-30
OK, I'll reload Kubuntu and try that option. Any other suggestions?

---

### Post by kryten35 on 2015-05-30
System settings >hardware>display and monitor>compositor

Tearing prevention :  fullscreen repaints

OpenGL interface: GLX

Rendering backend : OpenGL 2

These are the selections that worked for my nvidia card .But you can try other option/combinations as well.

VLC media player  for nvidia card/driver   Tools >preferences>Video  under display

Turn off accelerated video output - best quality and stability is to use your processor.Only use it for old/weak  hardware.
Output:select  Open GLX video output(XCB)   think its the fourth one down.

I was using  346.59 nvidia driver with my GT640 card.

---

### Post by imrazor on 2015-06-02
No joy. Even though I duplicated those settings to a T, I still get bad tearing in videos. Odd thing is if I mess around with different settings for a while, the problem will go away. However, as soon as I reboot, the problem reappears.

---

### Post by kryten35 on 2015-06-02
Have you tried creating a  Tearing.sh file in  /etc/profile.d  folder as administrator?
Some people have found that either
```
export KWIN_TRIPLE_BUFFER=1
```
or
```
export __GL_YIELD="USLEEP"
```
Then make it executable in terminal  with:
```
chmod +x /etc/profile.d/Tearing.sh
```
REBOOT
Fixes it.Dont use both.

What about  upgrading your nvidia driver to the latest for your card?

Netrunner 16 just been released ,its Plasma 5/15.04.There involved with kde development.
Mabye that might work better?.Or at least rule out a kubuntu problem with your card.

The only desktop that ive had tearing with nvidia is Xfce.All the rest, including mint 17.1 cinnamon have been fine.

---

### Post by imrazor on 2015-06-05
This seems to have done the trick!
```
export KWIN_TRIPLE_BUFFER=1
```

After testing for a few days, I can confirm that I no longer see tearing in video playback or desktop effect. There appears to be one fly in the ointment, though. My display goes crazy with video artifacts if I try to change resolution. So far it's only been necessary once, so I hope it won't be an issue going forward.

Thanks! I Googled for what seemed like hours and not once did I see that fix.

---

### Post by P.a.w.e.l on 2016-01-06
This has worked for me too on Manjaro KDE. I'm surprised they don't turn the triple buffer on by default, or at least allow it in the KDE options.
Anyway, thanks! You've made my day!

---

### Post by victoriseup on 2016-08-10
@kryten35 : Thanks a lot, that's work great  for me too !

---

