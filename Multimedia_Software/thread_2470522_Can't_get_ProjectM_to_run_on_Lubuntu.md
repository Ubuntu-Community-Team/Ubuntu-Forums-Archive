---
title: "Can't get ProjectM to run on Lubuntu"
date: 2022-01-02
forum: Multimedia Software
---

### Post by Seamless in Northampton on 2022-01-02
I've loaded Lubuntu 18.04 on an otherwise useless laptop. This laptop is for only one very limited purpose: running ProjectM with audio routed from my stereo. But ProjectM gets a segmentation fault. Only solution I've seen anywhere directs you to just turn off frame buffering with cmake. Which is great, if you know what that means and how to do it! But I don't. 

ProjectM-pulseaudio in terminal gets this:

(projectM-pulseaudio:6198): dbind-WARNING **:16:31:32:948: Error retrieving 
accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name 
org.ally.Bus was not provided by any .service files
Qapplication: invalid style override passed, ignoring it.
Default config: /usr/local/share/projectM/config.inp
reading /home/[username]/.config/projectM/config.inp
[projectM] config file: /home/[username]/.config/projectM/config.inp
unconnected: connecting...
connectHelper: "also_output.pci-0000_00_1f.5.analog-stereo.monitor"
CREATED
READY
Segmentation fault (core dumped)


Any help is appreciated. Ironically, this laptop used to run projectM just fine when it had Windows XP! This may be the first time I've ever regretted an Ubuntu switchover.
Any chance another flavor of Linux would help? (Seems unlikely, but I was considering Bodhi Linux.)

---

### Post by schragge on 2022-01-04
> **Seamless in Northampton said:**
> Only solution I've seen anywhere directs you to just turn off frame  buffering with cmake. Which is great, if you know what that means and  how to do it! But I don't.
The latest release tarball 3.1.12 doesn't include [CMakeLists.txt]("https://github.com/projectM-visualizer/projectm/blob/master/CMakeLists.txt"): it was released in February 2021, but the project was converted to use CMake after that, in Juni 2021. To build with CMake, you'll have to clone from git. Besides, it requires at least CMake 3.14, and Bionic only provides 3.10.

> **Seamless in Northampton said:**
> /usr/local/share/projectM/config.inp
**/usr/local/** in the path suggests you installed from source. Have you tried the **projectm-pulseaudio** 2.1.0 DEB package from universe?

A couple of Kodi PPAs provide ProjectM 3.x packages for Bionic. E.g. ProjectM 3.1.1 in [ppa:nkvoronov/kodi-leia]("https://launchpad.net/~nkvoronov/+archive/ubuntu/kodi-leia").

> **Seamless in Northampton said:**
> Any chance another flavor of Linux would help?
Ubuntu 20.04 LTS would definitely help. [ppa:dtl131/mediahacks2]("https://launchpad.net/~dtl131/+archive/ubuntu/mediahacks2") has the latest ProjectM release (3.1.12) packaged for Focal.

---

### Post by Seamless in Northampton on 2022-01-04
Thank you for that info! I'm a little out of my depth, but I think I followed. 

Using 20.04 LTS brings up another question: can I run it on this laptop? It's an IBM T42, with a Pentium M. I was under the impression 18.04 was the best I could do.

---

### Post by schragge on 2022-01-04
[Search](https://distrowatch.com/search.php?ostype=Linux&category=Old+Computers&basedon=Debian&architecture=i686&status=Active) @DistroWatch.com with **ostype=Linux&category=Old+Computers&basedon=Debian&architecture=i686&status=Active** gives me three hits:
[list]
[*]antiX
[*]Q4OS
[*]Emmabuntüs
[/list]

**antiX** looks like a reasonable choice for hardware released in 2005.

Retaining **architecture=i686**, but omitting **category=Old+Computers** gives much more (although Ubuntu is not there).

---

### Post by Seamless in Northampton on 2022-01-04
Cool! Thank you. Considering just giving Kodi a try in 18.04 and seeing if that add-on ProjectM will work. Was gonna try Kodi anyhow.

---

### Post by Seamless in Northampton on 2022-01-04
And... wow, is Kodi too much for this old machine! It's not really usable. I want to play music and/or route it through the system, and have a screen with ProjectM, and that's it. I'm surprised how hard that is to come by!

---

