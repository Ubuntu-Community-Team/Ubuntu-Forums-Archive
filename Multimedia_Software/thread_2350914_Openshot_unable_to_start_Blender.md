---
title: "Openshot unable to start Blender"
date: 2017-01-28
forum: Multimedia Software
---

### Post by satimis on 2017-01-28
Hi all,

Ubuntu 16.04 64bit
AMD 8-core
RAM 32G
Video RAM 2G
OpenShot 1.4.3
Blender 2.7.8
(Blender can be started running on terminal; 
blender 
or /usr/bin/blender)

On OpenShot -> Animated Title Editor
Selecting any Thumb Name starts following warning:

```

Blender, the free open source 3D content creation suite is required for this action (http://www.blender.org).

Please check the preferences in OpenShot and be sure the Blender executable is correct.  This setting should be the path of the 'blender' executable on your computer.  Also, please be sure that it is pointing to Blender version 2.62 or greater.

Blender Path:
/usr/bin/blender (also tried - blender)

Error Output:
No frame was found in the output from Blender

```

I have tried several versions of OpenShot such as; 
openshot-qt
openshot-edge

according to the suggestions found on Internet but without luck.

Whether Ubuntu 16.04 is not suitable for running OpenShot?

TIA

Regards
satimis

---

### Post by Bucky Ball on 2017-01-28
Uninstall Openshot and [go here and install the PPA]("http://www.openshot.org/ppa/"). You'll have better luck. The version in the repos is dated and dodgy.

16.04 is fine for running Openshot and Blender (at least, mine is). :)

I'm not that familiar with Openshot, though, but not sure why it's trying to open Blender to edit subtitles unless they were created there? :-k Were they? You could perhaps check preferences and, if there is the option, change the default app to edit subtitles to something other than Blender if it is set to that (like Openshot?).

Perhaps more details about your work flow and what you are doing would help. ;) You should be powering along with that setup. Which video card?

---

### Post by wildmanne39 on 2017-01-28
*Thread moved to **Multimedia Software for better support**.*

---

### Post by satimis on 2017-01-29
> **Bucky Ball said:**
> Uninstall Openshot and [go here and install the PPA]("http://www.openshot.org/ppa/"). You'll have better luck. The version in the repos is dated and dodgy.

16.04 is fine for running Openshot and Blender (at least, mine is). :)

I'm not that familiar with Openshot, though, but not sure why it's trying to open Blender to edit subtitles unless they were created there? :-k Were they? You could perhaps check preferences and see the default tool to edit subtitles is set to Blender and not something else (like Openshot?).

Perhaps more details about your work flow and what you are doing would help. ;) You should be powering along with that setup. Which video card?
Hi,

Thanks for your advice and link.

I have followed below link before installing openshot-qt but without luck;
How to Install OpenShot 2.1 Stable in Ubuntu 16.04, 14.04
[http://ubuntuhandbook.org/index.php/2016/08/install-openshot-2-1-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/08/install-openshot-2-1-ubuntu-16-04/)

I tried both blender and /usr/bin/blender on Preference -> Blender Executable;

I doubt whether it would be the problem of the graphic card.  Blender is running.  It can be started on terminal with;
blender
OR
/usr/bin/blender

Regards
satimis

---

