---
title: "HDMI audio broken again!"
date: 2015-06-11
forum: Multimedia Software
---

### Post by richie60 on 2015-06-11
Why oh why every time there's a new version of Ubuntu or any of it's derivatives does the audio over my HDMI connection fail to work?

I went through a few live CD's last night and these are the ones that work:

Debian 8
LinuxMint 17.1
Antergos
Manjaro
Xubuntu 14.04 LTS

The one's that currently don't work:

Ubuntu 14.04.1 LTS
Ubuntu 15.04
Xubuntu 15.04

I realize that LinuxMint have stuck with an older kernel and that's fine, but some of the other distro's have later kernels and they work so why not Ubuntu?

I have an NVidia card that's a few years old now and it has worked for years with various distro's so I know it's not my hardware.  I just want to know why Ubuntu fails everytime.  It's supposed to be the class-leading distro with the most widely supported hardware.

---

### Post by Bucky Ball on 2015-06-11
*Thread moved to **Multimedia**.*

Have you tried getting an audio stream going in Ubuntu> Opening Pulseaudio Volume Control and seeing where the audio stream is being routed to?

PS: If 14.04 LTS works, is there any reason you want to upgrade (or are continually upgrading to raise this issue)? 14.04 is an LTS which is supported for five years. 15.04, if that's what you're trying, is an interim release, not guaranteed to be as stable and runs out of support in nine months, well, actually about seven months from now, and then guess what? You'll have to upgrade to another interim release, 15.10, and that may break your HDMI audio again.

You could always start testing 15.10 now, I guess, specifically for this issue, and posting on the appropriate bug reports, forums and mailing lists. This would be of some help. Throwing mud isn't. Ubuntu has a limited numbers of devs, limited finances, and relies heavily on the volunteer community to test and tweak.

Let us know how you go with Pulseaudio Volume Control and if it gives you any joy. If you can see the audio stream bouncing in the level meter in 'Playback', then it is working. If you can't hear it it is not routed correctly. :)

---

### Post by richie60 on 2015-06-12
If sound works in Xubuntu 14.04 LTS why doesn't it work in Ubuntu 14.04 LTS?  Stupid isn't it?

It just gets routed to 'Dummy Output' Screenshot below:

[[IMG]http://i1083.photobucket.com/albums/j387/hifiman60/Forum%20pics/Screenshot%20from%202015-06-12%20155154_zpsuquu4ato.png[/IMG]](http://s1083.photobucket.com/user/hifiman60/media/Forum%20pics/Screenshot%20from%202015-06-12%20155154_zpsuquu4ato.png.html)

I am not continually upgrading to raise the issue, but occasionally like to try out other distros, as Mint 17.1 works perfectly, I would have thought Ubuntu would have as well.  I have no desire to start testing 15.10, but wanted to try 15.04, but it's not even recognised there!  It's seen in 14.04 but there's no way to get sound out of the PC!

I just don't understand why that it would work in previous versions and other distros but not stock Ubuntu!  Fairly standard stuff I would have thought.  Maybe I should forget Ubuntu and move on.

---

### Post by Bucky Ball on 2015-06-12
You should be looking in Pulseaudio Volume Control. If you haven't got it installed, install from Software Centre. Play an audio stream, check the Playback tab. Check the output tab. Which device is the stream using? No HDMI option? Go to the Configuration tab (I think it is) and choose the HDMI duplex. Go back and select in the other tabs.

Try PAVControl. I advised this in my first post, but you seem to have missed it. :)

Let us know of any progress and developments ...

---

