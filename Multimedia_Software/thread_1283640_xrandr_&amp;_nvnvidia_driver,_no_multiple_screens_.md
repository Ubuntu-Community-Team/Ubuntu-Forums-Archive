---
title: "xrandr &amp; nv/nvidia driver, no multiple screens possible?"
date: 2009-10-05
forum: Multimedia Software
---

### Post by kuadra on 2009-10-05
Hi,

I'm currently trying to hotplug an external monitor to my notebook, and have recently learned that since RandR 1.2 monitor hotplugging has reached one step closer to reality, and that hacking the xorg.conf file & restarting X is (or should be) not necessary any more.

Most of the howtos on the net seem to be about ATI or Intel graphic chips, and there, the output of xrandr always yields an entry for **LVDS**/**DVI** and **VGA** like in the [wiki]("https://wiki.ubuntu.com/X/Config/Resolution#Dynamically testing different resolutions").

Well, mine does not:

```
$ xrandr
Screen 0: minimum 640 x 480, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       60.0*
   1024x768       60.0
   800x600        60.0     56.0
   640x480        60.0
```

I've only a **default** entry, which is the internal notebook display. The consequence is that I'm not able to configure any external monitor/beamer.

Now for the specs: The notebook has an NVidia GeForce Go 7200, and I'm using the open source *nv* driver. I've also tried the binary *nvidia* driver, but the output is essentially the same (albeit of some additional modes in the table).

I've tested RandR also on a desktop computer, first with a Radeon 9250 and then with a spare GeForce 6200 (both times with a Kubuntu 9.04 Life CD).
The Radeon 9250 with the open source *ati* driver worked flawlessly just as in all the tutorials which I've found, and the only manual change I had to make in the xorg.conf was to add

```
SubSection "Display"
  Virtual 3600 1200
EndSubSection
```

in the "Screen" section to reserve enough memory to place the 2 screens next to each other.
The same experiment with the GeForce 6200 however returned exactly the same results as with my notebook. Only a **default** display is found, and the other monitor cannot be configured.

I've found a similar problem [here]("http://www.nvnews.net/vbulletin/showthread.php?t=134767"), but that concerns only the binary nvidia driver (which according to that post only supports RandR 1.1 yet).

I've found quite some nice [slides about RandR 1.2]("http://wiki.clug.org.za/images/2/29/Clug-talk-xrandr.pdf") and its new features as well as its requirements.
On slide 16 it states that the *nv* driver supports RandR 1.2 features as of version 2.1.6, and I've currently version 2.1.12 installed, so there should be no problem. Also, both GeForce cards are listed as supported in the Xorg.0.log file.
Last but not least, even [this article]("http://www.phoronix.com/scan.php?page=article&item=927&num=1"), which is almost 2 years old now, already states that the open source *nv* driver supports RandR 1.2 features.

Therefore at least the open source *nv* driver should support these features.
Has anyone here experienced similar problems, or an idea where to look next?

Thanks in advance!

P.S.: I _have_ already managed to configure both the internal LCD and an external VGA monitor using a modified xorg.conf which was created with *nvidia-settings*, and which I can use by switching the xorg.conf files and restarting the X-Server. This time, I want to accomplish real hotplugging.

---

### Post by kuadra on 2009-10-11
Well, I am pleased to announce that I've come to a conclusion.

Apparently, neither the *nv* nor the *nvidia* driver seem to (fully) support RandR 1.2. In particular, the open source *nv* driver only supports newer cards:

[QUOTE=openicc mailing list][According to nvidia the nv driver only has support for randr 1.2 for NV5 GPUs (8xxx and 9xxx cards)]("http://lists.freedesktop.org/archives/openicc/2008q3/001654.html")[/QUOTE]

So I've tried my luck with the open source *nouveau* driver, and bingo! It works out of the box, just like the ati or intel open source drivers. And the setup was [simpler than I had thought]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_904_nouveau"):
Just installing the package **xserver-xorg-video-nouveau** and setting **Driver "nouveau"** in the graphics' card device section in */etc/X11/xorg.conf*, restarting the X-Server, and viola.

As mentioned in my previous post, for RandR to achieve its full potential, a *Virtual* entry in the Display SubSection is necessary to unlock usable resolutions. E.g. the modes above 1280x1024 for my 1680x1050 TFT monitor were only available after that entry in */etc/X11/xorg.conf*.

If you want to confirm whether RandR 1.2 might work with your NVidia card, you can look at the [Feature Matrix]("http://nouveau.freedesktop.org/wiki/FeatureMatrix") of the nouveau wiki under the topic "Dual head (Randr 1.2)".

---

