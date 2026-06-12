---
title: "Let's talk about Nvidia black windows for a minute"
date: 2011-05-26
forum: Multimedia Software
---

### Post by lshurr on 2011-05-26
Apparently this is a problem that has come and gone multiple times.  Without trying too hard, I found posts about this problem from back in 2007.  In fact, it started with an announcement that the problem was fixed in the latest Nvidia driver with some followups that basically said, "Not necessarily". To avoid unnecessary suspense, let me tell you now that I have (apparently) gotten around Nvidia black window syndrome.

I scored a great E-bay deal on a Presario F500 notebook, a model which dates back to 2007 or so.  It looks the next best thing to new and it works well.  It's equipped with an Nvidia Go 6150, not a particularly fabulous device to be sure, but with Kubuntu 11.04 installed, the display is bright and sharp and desktop effects work well and are very responsive.  As I said, though, I first had to deal with black windows.

I tried the experimental free driver and several versions of the non-free Nvidia drivers, which, in case you don't know, Ubuntu has been taught to handle and they can be obtained using apt-get or KPackageKit (since we're talking Kubuntu here).  The latest drivers may be obtained by following the procedure found at "http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html".  I installed and enabled V270.41.19, but the black window problem persisted.

I found that turning off Desktop Effects from Systems Settings seemed to make black window go away, but of course I want Desktop Effects, so I started looking for any individual settings which might affect black window and found what I was looking for under System Settings -> Desktop Effects -> Advance Tab, specifically the OpenGL Options. After unchecking the box for "Enable direct rendering", Nvidia black window syndrome seems to have disappeared.

Giving up direct rendering has surely cost something.  The only obvious difference I've seen so far is that the "Magic Lantern" effect isn't quite as smooth and snappy as before, but generally it looks just about as good as ever and (so far, anyway) no black windows.  This may suggest something to developers of OpenGL, desktop effects and other, related pieces of code which ultimately leads to a fix.  I hope so, anyway.

Let me warn you that I've seen a few KWin failure/restart cycles, both before and after disabling direct rendering which seem to be related to Desktop Effects, more specifically, while changing Desktop Effect settings.  On the bright side, black window syndrome was accompanied by the occasional unexpected reboot, which also appears to have gone away with direct rendering turned off.

Hope that helps!

Larry

---

### Post by sanette on 2011-08-21
same problem here... thanks for the tip !

---

### Post by fatbuttlarry on 2011-11-02
Thanks for this.

I experienced this same issue in Ubuntu 11.04, 32-bit, except it was a white screen.

The black screen symptom shows up on KDE after I open a few windows.  Disabling direct rendering seems to fix it for sure.

I even went as far as filing a bug report with Ubuntu, but it must not have gotten anywhere as this issue is still persistent with 11.10.

Thanks for the help.

-Tres

---

### Post by wildmanne39 on 2011-11-02
Hi, I have had that problem with the same card since 11.04 and all I had to do is activate the 173 driver in additional drivers and make sure no other nvidia drivers are installed in synaptic because if you installed more then one driver it will have them all installed even though only one shows up in additional drivers.
Thank you

---

### Post by nimrodwebdesign on 2011-12-01
I fixed this problem thanks to _[manzano]("https://launchpad.net/~manzano-vocamen")_ on _[this launchpad page]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/96473")_.

I upped the video memory in the bios from 64MB to 256MB, and the black windows went away. Separate X screen still doesn't work, but at least I have Twinview!

What changed between Ubuntu 11.04 and 11.10 that broke this? I got the same problem in Linux Mint 12 which uses Gnome 3, so it isn't a Unity thing. Odd. :S

Oh well, it's resolved now, and I'm using Linux Mint instead thanks to that glitch (the LXDE version works flawlessly on my ancient laptop!!! Wooo!! Ubuntu was unusable, or flaky at best!). :(

---

### Post by watcheroftheskies on 2011-12-13
Hi,

Great to find this thread. I also read a post about using the 173 driver instead of the 260 (is that 'current'?) here:
[http://www.linuxquestions.org/questions/slackware-14/window-contents-turn-black-when-maximized-in-kde-889917/](http://www.linuxquestions.org/questions/slackware-14/window-contents-turn-black-when-maximized-in-kde-889917/) 

which seems to be suppported by:

[http://wiki.compiz.org/Troubleshooting](http://wiki.compiz.org/Troubleshooting)

I reallly would like to try a stable KDE distro. I have been using Gnome up until now (Mint implementation), but with Gnome3/Unity still in turmoil KDE now seems a haven of stability and very beautiful...

Thanks for the BIOS video mem tip by the way...

---

### Post by jmate24 on 2011-12-13
why don't you file this bug on launchpad and help to make opengl drivers and nvidia drivers better just go to [https://bugs.launchpad.net/]("https://bugs.launchpad.net/")

and enter a discription of the problem in the field if there is both white and black apps or screen please be specific and whether it is opengl or opengl2.

---

