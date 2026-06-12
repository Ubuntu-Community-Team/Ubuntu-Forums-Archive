---
title: "Fragment Image Viewer"
date: 2020-06-22
forum: Multimedia Software
---

### Post by EdRaket on 2020-06-22
Since yesterday I have a complete new installation of Ubuntu Studio 20.04.

In the past, I have loved to work with image viewer Fragment, <https://www.fragmentapp.info/download-fragment-linux.html>. So I wanted to install it again.

I have downloaded the deb file fragment_1.8.1_amd64.deb. Installing with Software Install resulted in an error: 'Unable to install fragment: The following packages have unmet dependencies:'   .... and than nothing ........

In Terminal I went to my Downloads-folder, and tried: ```sudo dpkg -i fragment_1.8.1_amd64.deb```. 

Unfortunately this error: 

```Selecting previously unselected package fragment.
(Reading database ... 425980 files and directories currently installed.)
Preparing to unpack fragment_1.8.1_amd64.deb ...
Unpacking fragment (1.8.1) ...
dpkg: dependency problems prevent configuration of fragment:
 fragment depends on libwebkit2gtk-3.0-25 (>= 2.0.2); however:
  Package libwebkit2gtk-3.0-25 is not installed.

dpkg: error processing package fragment (--install):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.31-0ubuntu9) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Errors were encountered while processing:
 fragment
```

If I do a right-click on an image, Ubuntu offers me to open with Fragment, but nothing happens when I try.

I have tried to do ```sudo apt-get install -f```, but terminal wants to uninstall Fragment:

```Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  fragment
0 upgraded, 0 newly installed, 1 to remove and 18 not upgraded.
1 not fully installed or removed.
After this operation, 47,9 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 426105 files and directories currently installed.)
Removing fragment (1.8.1) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for libc-bin (2.31-0ubuntu9) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...
```

I had similar problems with Ubuntu 18.04, but now Fragment doesn't want to work at all.

Has someone an idea what I am doing wrong? Is it something that I have to do with the binaries-only file fragment_1.8.1.tar.xz?

---

### Post by Holger_Gehrke on 2020-06-25
If the package relies on libwebkit2gtk-3.0-25 then it's meant for 16.04. All newer versions of Ubuntu come with libwebkit2gtk-4.0-37.  So you probably have to unpack the fragment_1.8.1.tar.xz into a directory of your choice and make your own .desktop file for it, unless you're okay with running it from the CLI. That binary archive carries two warnings by the author(s), for one it won't set up file-type associations and unless you have webkitgtk installed direct upload to Facebook won't work.

Holger

---

### Post by EdRaket on 2020-06-26
Many thanks Holger!

I have unpacked the tar.xz file to my home directory. In this new folder, I see 2 executable files: 'fragment' and 'fragAssoc'. 

If I execute 'fragAssoc', I get an error saying that Fragment needs to be installed. So I install fragment (again) with sudo dpkg --install fragment_1.8.1_amd64.deb

Now I can open 'fragAssoc' with just a double-click and can set the file associations.

Double-click on fragment: nothing happens. So I tried: 'sudo chmod +x fragment', and after 'sudo ./fragment'. Now I get this error:

libGL error: MESA-LOADER: failed to open radeonsi (search paths /usr/lib/x86_64-linux-gnu/dri:\$${ORIGIN}/dri:/usr/lib/dri)
libGL error: failed to load driver: radeonsi
libGL error: MESA-LOADER: failed to open radeonsi (search paths /usr/lib/x86_64-linux-gnu/dri:\$${ORIGIN}/dri:/usr/lib/dri)
libGL error: failed to load driver: radeonsi
libGL error: MESA-LOADER: failed to open swrast (search paths /usr/lib/x86_64-linux-gnu/dri:\$${ORIGIN}/dri:/usr/lib/dri)
libGL error: failed to load driver: swrast
QOpenGLWidget: Failed to create context
virtual bool SceneView::event(QEvent*) false false
"SceneView::showEvent  23:08:51.176"
"SceneView::initBackgroundAndImage  23:08:51.176"
Segmentation fault (core dumped)



Btw: Fragment worked on Ubuntu Studio 18.04. Only thing was that I had to reinstall it after every update/ installation of a new program.

---

### Post by Holger_Gehrke on 2020-06-27
The libGL errors seem to point at direct rendering drivers either missing or changed so much that fragment can't use them. Is the package 'libgl1-mesa-dri' installed ? IIRC it should be part of a standard install, but check anyway. Use 'dpkg -l libgl1-mesa-dri' to find out; if the status line printed begins with 'ii' its correctly installed.

Holger

---

### Post by EdRaket on 2020-06-27
Hi Holger,

great and very unexpected to get help from a former professional German football player. Danke schön!

The 'ii' is printed in the status line.


Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                  Version         Architecture Description
+++-=====================-===============-============-====================================================
ii  libgl1-mesa-dri:amd64 20.0.4-2ubuntu1 amd64        free implementation of the OpenGL API -- DRI modules

---

### Post by Holger_Gehrke on 2020-06-27
Sorry, but the only thing I have in common with that "Holger Gehrke" is the name. The closest I come to professional football is watching a game on TV.

So, if libgl1-mesa-dri is correctly installed there should be a radeonsi_dri.so and a radeonsi_drv_video.so in /usr/lib/x86_64-linux-gnu/dri. 

Looks like the only thing left to do is complain to the author. That's the trouble with closed source software: beyond a certain point you have to rely on the author to keep the software useable. Since the author hasn't posted anything on the app's site since the middle of 2019 I wouldn't get my hopes up. That's the main reason I usually go for Open Source; if worst comes to worst I can just try to compile it myself and (at least try to) fix the problem. 

Image viewers I can recommend are geeqie (rather traditional GUI program), feh (keyboard and command line oriented) and 'display' from the ImageMagick suite (takes a long while to get used to; can use all the many image manipulation options available in ImageMagick, so most useful if you're trying to figure out a long(-ish) set of options to use with 'convert' or 'mogrify' to (batch-) transform images). And for organizing images there's always Digikam. And GiMP for doing any serious work with them.

Holger

---

### Post by EdRaket on 2020-06-28
I already wrote the author last week, no answer till now. Anyway: many thanks for your help. I appreciate it very much, even now I know that you are not a former football player :-) If there comes a solution, I will write it in this topic. For now I will try your suggestions, some of them I did not know till now.

---

