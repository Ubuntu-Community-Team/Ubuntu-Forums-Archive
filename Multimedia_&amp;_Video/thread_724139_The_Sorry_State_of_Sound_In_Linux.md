---
title: "The Sorry State of Sound In Linux"
date: 2008-03-14
forum: Multimedia &amp; Video
---

### Post by SpookyET on 2008-03-14
[http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html](http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html)

I've only discovered this because of an ALSA [bug](http://tinyurl.com/2n848a) was making my life miserable.  That article was written about a month or two before OSS4 (Open Sound System v4) was released under GPL and CDDL. This past January, it was released under BSD as well. Unfortunately for the author, he does not understand open source very well. He is now reporting that his [revenue went significantly down.](http://4front-tech.com/hannublog/).

OSS4 does not equal to the crap OSS in Linux 2.4 kernels. Even OSS3 != OSS3 in former linux kernels. He was neglecting the open source version in favour of the commercial one. Instead of improving it, someone forked it. And, the fork became popular. Unfortunately, the original author had no interest in working on the fork. So, he only focused on the commercial version.  Now, many years later, the commercial version is fully open source. There is no more commercial version.

I've tried it,  and I really like it. Music sounds much better than on ALSA. For example, screaming in alternative rock is more legible.  It's like enabling enhanced voice on a phone. It supports higher PCM values without noise.

The mixer (vmix) is capable of 18 channels. It can also do per application volume control (like PulseAudio).

It totally makes sense that OSS gets back into the kernel because it works on almost every UNIX and UNIX-like system (except OS X). ALSA only works on Linux, and according to that article, developers still prefer the OSS API, even on ALSA. However, the ALSA OSS API is lacking according to an ALSA developer. I can confirm that the comment on ALSA OSS Emulation working better than the ALSA API. XMMS with ALSA enabled freezes my system. XMMS with OSS enabled on ALSA does not.

It worked without any configuration besides muting some channels to kill the noise.

**THE BAD**
ossmix and ossxmix are totally unusable because they do not name the channels properly. ossxmix uses 100% CPU if Compiz is enabled. Version 4.1 will fix this.
I had to figure out WTF **ossxmix.codec1.connector.jack14.jack 54:54** means. Sane names need to be added to the jacks.
It's best to use ossxmix (GTK+ mixer) and playing with all the jacks to figure out what each one does. 
One interesting control is how OSS4 should behave (Fast, Medium High, Professional, etc.). It's probably a latency control.  ossxmix is a demo app on how you can control the mixer from GTK. It needs to be made usable.

If you only use Media Player Daemon and MPlayer, OSS4 works beautifully. They use OSS directly. Others have problems.

Totem does not play sound. Totem-Xine uses 100% CPU (Xine-UI works with low CPU usage). 
In terminal I noticed some output from oss mixer control saying it received bad arguments. OSS4 is backwards compatible with OSS3, but xine-lib may be using the API badly.

The progress bar (seeker) in GStreamer based applications (Rhythmbox, Banshee) does not work if you use vmix. You have to enable softoss (the old mixer). vmix and gstreamer behave very badly. The gstreamer developer responsible for OSS claims that it does on his system. 

You have to apply this [patched gstreamer](http://4front-tech.com/forum/viewtopic.php?t=2357&highlight) to make volume control in GNOME work.
 
[DOWNLOAD IT (MOST SYTEMS)](http://www.opensound.com/download.cgi)
[Gentoo ebuild](http://bugs.gentoo.org/show_bug.cgi?id=184123)
[Arch Linux](http://aur.archlinux.org/packages.php?ID=14421) [(Read Wiki)](http://wiki.archlinux.org/index.php/OSS)

Check **[Configuring Applications for OSSv4](http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4)** after you install it.

Overall, I think it's a million times better than ALSA. It's cross platform, and it's stable. It was released a year ago on 15th of March 2007. Since he does not have a marketing department, no one has heard of it.

---

### Post by thirdspace on 2008-03-14
The OSS vs ALSA war is over. OSS lost. I hate the idea of restarting the OSS vs ALSA war even more than I hate ALSA. Anyway that was decided by the Linux kernel folks and it would be madness for Ubuntu or any other distribution to go their own way.

I think the best way to look at ALSA is as a low-level part and a high-level part. The low level part drives the hardware and provides maximum access to the unique features of each soundcard, with minimal latency (time delay). This part is pretty decent although everyone wishes the mixer interfaces were better documented. There is always some hardware out there that ALSA drives imperfectly or not at all, but the same is bound to be true of any set of soundcard drivers.

The trouble with ALSA is that it tries to provide a lot of additional functionality such that all kinds of sound and multimedia applications can use it directly, and these parts of ALSA are a huge disaster area. There has been a series of attempted solutions to the "audio device is busy" issue, all of them hard to understand and incomplete. Device naming is badly designed, There are crazy hoops you have to jump through to enable sample rate and other format conversions. There are configuration files that follow a unique syntax that no one seems to really understand. As a result there are multiple projects competing to become the standard way to protect application developers (and users) from the horror of the ALSA high-level API. JACK, Esound, aRTS, and PulseAudio come to mind, but there are a raft of others.

JACK seems to be well accepted for "professional" music production and related tasks. PulseAudio is new but looks like it has a good chance to eventually be the standard for all other desktop sound use-cases.

---

