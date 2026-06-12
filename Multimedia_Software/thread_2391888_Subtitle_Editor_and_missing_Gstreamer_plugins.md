---
title: "Subtitle Editor and missing Gstreamer plugins"
date: 2018-05-14
forum: Multimedia Software
---

### Post by viktor09 on 2018-05-14
I've installed Subtitle Editor but it won't play any videos because (depending on file format) it says it needs the following Gstreamer plugins:
[LIST]
[*]MPEG-4 Video (Simple Profile) decoder
[*]H.264 (High Profile) decoder
[*]Advanced Streaming Format (ASF) demuxer
[/LIST]

The good, the bad and the ugly sets are all installed, as is the base set. Also installed are plugins for X11 and Pango, ALSA, and GTK+3 (Subtitle Editor is a GTK+3 tool).

What the hell else can it need?? Well, obviously it needs the three plugins listed above ... but where do I get them and how do I install them?

For info, I'm on Lubuntu 18.04 and I'm a Linux newbie, so clear and simple instructions are appreciated--don't be afraid of treating me like the know-nothing that I am :D

Thanks in advance for any help :)

Viktor

---

### Post by TheFu on 2018-05-14
"Why" things are the way they are is a different question, full of history, internal politics, brilliance and stupidity.

How do I say this ... 18.04 has made some huge changes in the way many things work.  If there is an issue at this point, and there are lots of issues, it might be best to wipe and install 16.04 which will still get support until 2021.  16.04 also had huge internal changes that broke how the system worked. It took more than a few months to settle down back in 2016 before the big things were addressed.  And with 16.04, there are how-to guides which have been out for a few years, fully tested.

18.04 will get there, but they made some huge changes. With only a few thousand testers, it is easy for things to be missed. I don't have 18.04 installed anywhere now and will probably wait until July before I put it on a test virtual machine.  Doubt I'll make a desktop change to 18.04 until sometime in the fall, at the earliest. For me, something that works, predictably, is much more important than something "new."  BTW, I still have 2 systems running 14.04 which is supported until April 2019.   LTS is what you want. LTS is released in April of even-years.  So 14,16,18 are even years.  .04 is April.  Odd years don't have any LTS releases and October (.10) releases are never LTS. So 17.10 only has 6-9 months of support, which is a bad choice for you (and me).

Anyway ... the key part for your question is that you need to install **gstreamer plugins**.  I don't use gstreamer, but it has been included in Ubuntu for a fairly long time.  [https://gstreamer.freedesktop.org/documentation/plugins.html](https://gstreamer.freedesktop.org/documentation/plugins.html) is a list of many gstreamer plugins from "the source" .... "freedesktop.org" is the home for many Gnome projects. It is a reputable site for getting information directly from the Gnome project.

A little more guessing ... and I came up with these packages for installation:
**  gstreamer0.10-plugins-good gstreamer0.10-plugins-base**
So use whatever package manager tool you like to install those.  Hopefully it will work, but I don't know if 18.04 supports those packages or if those packages have the decoders you seek. I'm more confident for 16.04. If they don't, remove them.   You shouldn't need to reboot post-install. Just logout and login again.

BTW, the "0.10" in the package names is very odd.  For almost all packages, the version numbers aren't included.  I actually double-checked that because it is so odd.   During the install, I think there is an option to install non-Free media addons. Did you check that?

Hopefully, all the extra info isn't confusing even more.

---

