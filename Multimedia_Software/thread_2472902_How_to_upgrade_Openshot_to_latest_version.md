---
title: "How to upgrade Openshot to latest version"
date: 2022-03-16
forum: Multimedia Software
---

### Post by satimis on 2022-03-16
Hi all,

I haven't used OpenShot for prolonged time.

The version of my installed OpenShot is 2.4.3.  I supposed it was installed on downloading the package from its website.

Please advise.
1) How to upgrade it to version 2.6.0, the latest version ?
2) How to add a text editor ?

Thanks in advance.

Regards

---

### Post by Dennis N on 2022-03-16
> Please advise.
1) How to upgrade it to version 2.6.0, the latest version ?
2) How to add a text editor ?

I use the Flatpak of Openshot. The current stable version is actually **2.6.1**  

```
[dmn@Sydney ~]$ flatpak info org.openshot.OpenShot

OpenShot Video Editor - An easy to use, quick to learn, and surprisingly
powerful video editor

          ID: org.openshot.OpenShot
         Ref: app/org.openshot.OpenShot/x86_64/stable
        Arch: x86_64
      Branch: stable
     Version: 2.6.1
     License: GPL-3.0-or-later
      Origin: flathub
  Collection: org.flathub.Stable
Installation: system
   Installed: 252.9*MB
     Runtime: org.kde.Platform/x86_64/5.15-21.08
         Sdk: org.kde.Sdk/x86_64/5.15-21.08

```

Remove the Ubuntu repository package and install with Flatpak. Visit: [https://flathub.org/home](https://flathub.org/home) to learn how (click on Quick Setup).

---

### Post by satimis on 2022-03-16
> **Dennis N said:**
> I use the Flatpak of Openshot. The current stable version is actually **2.6.1**  

```
[dmn@Sydney ~]$ flatpak info org.openshot.OpenShot

OpenShot Video Editor - An easy to use, quick to learn, and surprisingly
powerful video editor

          ID: org.openshot.OpenShot
         Ref: app/org.openshot.OpenShot/x86_64/stable
        Arch: x86_64
      Branch: stable
     Version: 2.6.1
     License: GPL-3.0-or-later
      Origin: flathub
  Collection: org.flathub.Stable
Installation: system
   Installed: 252.9*MB
     Runtime: org.kde.Platform/x86_64/5.15-21.08
         Sdk: org.kde.Sdk/x86_64/5.15-21.08

```

Remove the Ubuntu repository package and install with Flatpak. Visit: [https://flathub.org/home](https://flathub.org/home) to learn how (click on Quick Setup).

Hi,

Thanks for your advice.

Performed following steps:-

$ sudo apt-get purge --auto-remove openshot
(to delete the current OpenShot package)

$ sudo apt install flatpak
$ sudo apt install gnome-software-plugin-flatpak
 
$ flatpak remote-add --if-not-exists flathub [https://flathub.org/repo/flathub.flatpakrepo](https://flathub.org/repo/flathub.flatpakrepo)
```

Note that the directories 

'/var/lib/flatpak/exports/share'
'/home/satimis/.local/share/flatpak/exports/share'

are not in the search path set by the XDG_DATA_DIRS environment variable, so
applications installed by Flatpak may not appear on your desktop until the
session is restarted.

```

$ reboot

$ flatpak install flathub org.openshot.OpenShot```

Looking for matches…
Required runtime for org.openshot.OpenShot/x86_64/stable (runtime/org.kde.Platform/x86_64/5.15-21.08) found in remote flathub
Do you want to install it? [Y/n]: Y

again Y

1. [&#10003;] org.freedesktop.Platform.GL.default                         21.08      i  flathub 130.9*MB / 131.2*MB
 2. [&#10003;] org.freedesktop.Platform.openh264                           2.0        i  flathub   1.5*MB / 1.5*MB
 3. [&#10003;] org.gtk.Gtk3theme.Yaru                                      3.22       i  flathub 151.8*kB / 210.3*kB
 4. [&#10003;] org.kde.Platform.Locale                                     5.15-21.08 i  flathub  16.9*kB / 345.2*MB
 5. [&#10003;] org.kde.PlatformTheme.QGnomePlatform.Sources                5.15-21.08 i  flathub   1.6*MB / 1.6*MB
 6. [&#10003;] org.kde.PlatformTheme.QGnomePlatform                        5.15-21.08 i  flathub  10.0*MB / 10.0*MB
 7. [&#10003;] org.kde.PlatformTheme.QtSNI.Sources                         5.15-21.08 i  flathub  47.4*kB / 41.5*kB
 8. [&#10003;] org.kde.PlatformTheme.QtSNI                                 5.15-21.08 i  flathub   1.3*MB / 1.3*MB
 9. [&#10003;] org.kde.WaylandDecoration.QGnomePlatform-decoration         5.15-21.08 i  flathub   6.1*MB / 10.5*MB
10. [&#10003;] org.kde.WaylandDecoration.QGnomePlatform_decoration.Sources 5.15-21.08 i  flathub   2.0*kB / 1.6*MB
11. [&#10003;] org.kde.Platform                                            5.15-21.08 i  flathub 242.9*MB / 305.3*MB
12. [&#10003;] org.openshot.OpenShot                                       stable     i  flathub 104.7*MB / 111.9*MB

Installation complete.

```

**[COLOR="#FF0000"]Run[/COLOR]**

$ flatpak run org.openshot.OpenShot

Done

OpenShot installed with shortcut added to Favorite.

I haven't run OpenShot for prolonged time.  How to add a text editor to it?

Can you help ?  Thanks

Regards

---

### Post by Dennis N on 2022-03-16
> How to add a text editor to it?

I'm guessing you want to add text (or "titles") to videos? Openshot has built in support for adding titles to a video through the "Title" option on it's menu bar. You get some templates. You can edit the text with the built-in editor.. Or if you need to create something different, Openshot uses Inkscape as a helper application to do custom work (which I haven't so far needed to do). You need to spend some time learning Openshot.  When I first started, I watched the developer's videos on YouTube:

[https://www.youtube.com/c/JonathanThomasOSS](https://www.youtube.com/c/JonathanThomasOSS)

Click the "Videos" tabs to see all tutorials that have been made.

Note that the titles can be transparent over your video!

Good luck, and have fun!

---

### Post by satimis on 2022-03-16
> **Dennis N said:**
> I'm guessing you want to add text (or "titles") to videos? Openshot has built in support for adding titles to a video through the "Title" option on it's menu bar. You get some templates. You can edit the text with the built-in editor.. Or if you need to create something different, Openshot uses Inkscape as a helper application to do custom work (which I haven't so far needed to do). You need to spend some time learning Openshot.  When I first started, I watched the developer's videos on YouTube:

[https://www.youtube.com/c/JonathanThomasOSS](https://www.youtube.com/c/JonathanThomasOSS)

Click the "Videos" tabs to see all tutorials that have been made.

Note that the titles can be transparent over your video!

Good luck, and have fun!
I have been running OpenShot editing videos in the past, about 10 years ago.  Later I used Avidemux/ShotCut/AviSynth/Davicin Resolve etc.  Now I'm coming back.  It is possible to add inkscape or other text editors for editing text on Title.

OK I'll search for the solution.  Thanks again for your advice.

Regards

---

### Post by Dennis N on 2022-03-16
> **satimis said:**
> I have been running OpenShot editing videos in the past, about 10 years ago.  Later I used Avidemux/ShotCut/AviSynth/Davicin Resolve etc.  Now I'm coming back.  It is possible to add inkscape or other text editors for editing text on Title.

OK I'll search for the solution.  Thanks again for your advice.

Regards

Inkscape would be used to design your own custom title frames with your own graphics. It can add text, so you wouldn't need another editor. To edit one of the default templates that OpenShot provides, OpenShot has built in editing for doing that.  OpenShot's editing is good enough to serve my purposes, and so far I haven't had a need for using Inkscape with OpenShot. 

As for my video tools, I have Avidemux for grabbing video clips, SimpleScreenRecorder for recording the Desktop, and Openshot for the assembling a final video with an optional audio track. These meet all my needs.

---

### Post by satimis on 2022-03-17
> **Dennis N said:**
> - snip -
As for my video tools, I have Avidemux for grabbing video clips, SimpleScreenRecorder for recording the Desktop, and Openshot for the assembling a final video with an optional audio track. These meet all my needs.
I have been spending sometime in retrofit my old video on VHS tape ripped by profession shop on DVD.  The old videos were captured in different environment, not only one video editing software able to do the job.  First I have to running ffmpeg to trim the video into sections.  Afterwards I run Avidemux/AviSynth/ShotCut/VirtualDub2 etc on either Linux or Windows OS. to retreat each section with different parameter/setting.

Now I'm prepared to assemble them with titles, background music and narration added.  I haven't used OpenShot for long time.  I may spend time to recapture its operation.

---

### Post by mIk3_08 on 2022-03-17
> **satimis said:**
> Hi all,

I haven't used OpenShot for prolonged time.

The version of my installed OpenShot is 2.4.3.  I supposed it was installed on downloading the package from its website.

Please advise.
1) How to upgrade it to version 2.6.0, the latest version ?
2) How to add a text editor ?

Thanks in advance.

Regards

Its either you download a latest deb or go to the package manager. There are some package manager that has already updated their packages. so, Good Luck and Regards

---

### Post by satimis on 2022-03-17
> **mIk3_08 said:**
> Its either you download a latest deb or go to the package manager. There are some package manager that has already updated their packages. so, Good Luck and Regards
Noted and thanks

Regards

---

### Post by satimis on 2022-03-17
Hi Dennis,

If I run Flatpak to install Inkscape;

$ sudo flatpak install flathub org.Inkscape.Inkscape

To Run Inkscape;
$ sudo flatpak run org.Inkscape.Inkscape

Would Inkscape be automatically linked to OpenShot ?

OR still I have to go through;

OpenShot
Edit -> Preference -> Advanced Title Editor (path) -> Browse .. etc.

Pls advise.  Thanks

Regards

Edit
====
Blender can also be installed via flatpak

$ flatpak install flathub org.blender.Blender

Run Blender

$ flatpak run org.blender.Blender

---

### Post by satimis on 2022-03-17
Hi Dennis,

If I run Flatpak to install Inkscape;

$ sudo flatpak install flathub org.Inkscape.Inkscape

To Run Inkscape;
$ sudo flatpak run org.Inkscape.Inkscape

Would Inkscape be automatically linked to OpenShot ?

OR still I have to go through;

OpenShot
Edit -> Preference -> Advanced Title Editor (path) -> Browse .. etc.

Pls advise.  Thanks

Regards

---

### Post by Dennis N on 2022-03-17
```
Would Inkscape be automatically linked to OpenShot ?

OR still I have to go through;

OpenShot
Edit -> Preference -> Advanced Title Editor (path) -> Browse .. etc.

Pls advise. Thanks

```
Inkscape is already shown as the "advanced editor" in my Openshot preferences. In my Openshot, It opens when I choose "Use Advanced Editor" in Titles > (text) Title.

Note: you don't need to use sudo to install a Flatpak application or run it, and you don't need to use Terminal to run. They should be started like any other applications: from menu, dock, or applications overview. Using sudo probably would install the program files with root as owner?

That said, I think I would just make my title as a .png image in Inkscape, then inport it into Openshot. Seems like that would work too.

---

### Post by satimis on 2022-03-17
> **Dennis N said:**
> ```
Would Inkscape be automatically linked to OpenShot ?

OR still I have to go through;

OpenShot
Edit -> Preference -> Advanced Title Editor (path) -> Browse .. etc.

Pls advise. Thanks

```
Inkscape is already shown as the "advanced editor" in my Openshot preferences. In my Openshot, It opens when I choose "Use Advanced Editor" in Titles > (text) Title.
.......
That said, I think I would just make my title as a .png image in Inkscape, then inport it into Openshot. Seems like that would work too.
No
Inksacpe not installed

Perform following steps

Start OpenShot
-> Import Files

drag the file to [Track 1]
-> Title > Bar 1 -> Use Advanced Editor

Error
Inksacpe not installed
-> OK

Pls refer to attached screenshot

> 
Note: you don't need to use sudo to install a Flatpak application or run it, and you don't need to use Terminal to run. They should be started like any other applications: from menu, dock, or applications overview. Using sudo probably would install the program files with root as owner?

I can't find Flatpak on menu bar.  Nor I can find it on [Activities]

Regards

[B][COLOR="#FF0000"]Edit-1
====[/COLOR][/B]
On Terminal

$ which inkscape
/usr/bin/inkscape

Also I found Inkscape on "Activities"

But I couldn't make Inkscape to work on OpenShot

$ which blender
no output

Blender not installed

[B][COLOR="#FF0000"]Edit-2
====[/COLOR][/B]
**I have tried several hours unable to make Inkscape to connect OpenShot**

OpenShot is installed running Flatpak
Inkscape is installed on repo of Ubuntu20.04

[COLOR="#FF0000"]**Would it be a problem?**[/COLOR]

---

### Post by satimis on 2022-03-18
Hi Dennis,
[B][COLOR="#FF0000"]
Inkscape can't connect Openshot installed running Flatpak[/COLOR][/B]

Problem solved as follows;

$ flatpak uninstall openshot```

Found installed ref &#8216;app/org.openshot.OpenShot/x86_64/stable&#8217; (system). Is this correct? [Y/n]: y

        ID                           Branch        Op
 1. [-] org.openshot.OpenShot        stable        r

Uninstall complete.

```

Download OpenShot-v2.6.1-x86_64.AppImage
[https://www.openshot.org/download/](https://www.openshot.org/download/)

On Terminal;
$ sudo chmod +x OpenShot-v2.6.1-x86_64.AppImage

Right-click OpenShot-v2.6.1-x86_64.AppImage -> Run
Start OpenShot

Title -> Use Advanced Editor
start Inkscape window

Done

Regards

---

### Post by Dennis N on 2022-03-18
I can only say that my system has both Inkscape and Openshot installed as a Flatpak and it all works as I described. Maybe using sudo to install these made a difference? [U]

Comment on AppImages[/U]:
I try to keep my AppImages to a minumum (use only if no other option) because of their design. I have just two installed now. On AppImage packages, each contains all the needed support libraries, except for some basic libraries that are assumed to be on any Linux OS. Flatpak applications can share common libraries thus avoiding duplication and reduce the space required. There also is a package management system for Flatpak that keeps them updated through a gnome software plugin. Snaps share libraries and automatically keep updated too, but I have my reasons to prefer Flatpak over Snap when seeking newer versions of applications.

---

### Post by satimis on 2022-03-18
> **Dennis N said:**
> I can only say that my system has both Inkscape and Openshot installed as a Flatpak and it all works as I described. Maybe using sudo to install these made a difference?

I only ran sudo on following command lines;

1)
$ sudo apt install flatpak
2)
$ sudo apt install gnome-software-plugin-flatpak

To install OpenShot is without sudo
3)
$ flatpak install flathub org.openshot.OpenShot

Inkscape was installed on Ubuntu 20.04 repo.  I can't install it without "sudo"
4)
$ sudo apt install inkscape

Whether you meant I should run command lines 1) and 2) without sudo?

> 
Comment on AppImages[/U]:
I try to keep my AppImages to a minumum (use only if no other option) because of their design. I have just two installed now. On AppImage packages, each contains all the needed support libraries, except for some basic libraries that are assumed to be on any Linux OS. Flatpak applications can share common libraries thus avoiding duplication and reduce the space required. There also is a package management system for Flatpak that keeps them updated through a gnome software plugin. Snaps share libraries and automatically keep updated too, but I have my reasons to prefer Flatpak over Snap when seeking newer versions of applications.

Just found following YouTube video.

How to install Openshot video editor 3.0 on Ubuntu 20.04 ?
[https://www.youtube.com/watch?v=9t4VcQhUwzA](https://www.youtube.com/watch?v=9t4VcQhUwzA)

I'll test it later.

Regards

---

### Post by Dennis N on 2022-03-18
>     Edit-2 - I have tried several hours unable to make Inkscape to connect OpenShot
    OpenShot is installed running Flatpak
    Inkscape is installed on repo of Ubuntu20.04
    Would it be a problem? 


OK I stand corrected on the commands to install. As to the above problem, it's possible that because of the mixed package types, the OpenShot Flatpak may not have permission to access the /usr/bin directory to start the Inkscape binary. It's fixable (see below) but the easy path forward for you is to just use the AppImage which has no such restrictions. You already said it worked. 

To fix a Flatpak permissions, you can grant the permission to access a desired folder. It can be done with a terminal command, but the neat way is a utility called Flatseal (which is another Flatpak). I would consider Flatseal indispensable for Flatpak users.

Note that snaps share such permission problems!

---

### Post by satimis on 2022-03-18
> **Dennis N said:**
> OK I stand corrected on the commands to install. As to the above problem, it's possible that because of the mixed package types, the OpenShot Flatpak may not have permission to access the /usr/bin directory to start the Inkscape binary. It's fixable (see below) but the easy path forward for you is to just use the AppImage which has no such restrictions. You already said it worked. 

**[COLOR="#FF0000"]Performed following test:-[/COLOR]**

**[COLOR="#FF0000"]1)[/COLOR]** Clone a new Ubuntu 20.04 VM (Orale VirtualBox)

**[COLOR="#FF0000"]2)[/COLOR]** Run Flatpak to install OpenShot
$ sudo apt install flatpak

$ sudo apt install gnome-software-plugin-flatpak

$ flatpak remote-add --if-not-exists flathub [https://flathub.org/repo/flathub.flatpakrepo](https://flathub.org/repo/flathub.flatpakrepo)

$ flatpak install flathub org.openshot.OpenShot

$ flatpak run org.openshot.OpenShot

Now OpenShot starts.  Exit OpenShot

**[COLOR="#FF0000"]3)[/COLOR]** Run Flatpak to install Inkscape

$ flatpak remote-add --user --if-not-exists flathub [https://flathub.org/repo/flathub.flatpakrepo](https://flathub.org/repo/flathub.flatpakrepo)

$ flatpak install --user flathub org.inkscape.Inkscape```

Looking for matches&#8230;

org.inkscape.Inkscape permissions:
    ipc      network      wayland      x11      file access [1]      dbus access [2]

    [1] host, xdg-run/gvfs, xdg-run/gvfsd
    [2] org.gtk.vfs.*

        ID                                     Branch           Op          Remote           Download
 1. [&#10003;] org.inkscape.Inkscape.Locale           stable           i           flathub           7.0*kB / 13.6*MB
 2. [&#10003;] org.inkscape.Inkscape                  stable           i           flathub          68.0*MB / 87.5*MB

Installation complete.

```

$ flatpak run org.inkscape.Inkscape

Start Inkscape
Version 1.1

What will be the path to be added to ????
Edit -> Preferences
Advanced Title Editor (path) [                       ]

I have tried;
1. adding [flatpak run org.inkscape.Inkscape    ]
2. -> Browse -> /run/user/1000/doc/5784ba42/inkscape

Both can't work.

> 
To fix a Flatpak permissions, you can grant the permission to access a desired folder. It can be done with a terminal command, but the neat way is a utility called Flatseal (which is another Flatpak). I would consider Flatseal indispensable for Flatpak users.

Whether on Terminal run;
$ sudo chown flatseal:flatseal -R /user/bin/inkscape
???

Other advice noted and thanks

Regards

---

### Post by Dennis N on 2022-03-19
```
 flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```
You don't have to repeat this **[SIZE=3]&#8593;[/SIZE]** with every application install. Adding the flathub repository is permanent.
I see you now have both OpenShot and Inkscape as flatpaks. Everything now looks good.
> What will be the path to be added to ????
Edit -> Preferences
Advanced Title Editor (path) [ ]
I didn't need to enter a path. Mine had 'inkscape' for that entry and I didn't change it. (see screenshot attached). Note that it has to be 'inkscape', not 'Inkscape'.
Sometimes you may need to restart your computer after changes to be sure they are recognized.

---

### Post by satimis on 2022-03-19
> **Dennis N said:**
> ```
 flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```
You don't have to repeat this **[SIZE=3]&#8593;[/SIZE]** with every application install. Adding the flathub repository is permanent.
I see you now have both OpenShot and Inkscape as flatpaks. Everything now looks good.

I didn't need to enter a path. Mine had 'inkscape' for that entry and I didn't change it. (see screenshot attached). Note that it has to be 'inkscape', not 'Inkscape'.
Sometimes you may need to restart your computer after changes to be sure they are recognized.
I got it fixed.  Thanks.

What about blender.  Do I need running Flatpak to install it?  Can I install it on repo of Ubuntu 20.04?

Regards

---

### Post by Dennis N on 2022-03-19
> What about blender. Do I need running Flatpak to install it? Can I install it on repo of Ubuntu 20.04?
I did confirm that OpenShot flatpak cannot open Inkscape from repo .deb package. If it's possible to permit this, I couldn't find a way.
So, based on that, I doubt it can open Blender installed from repo .deb package.

That said, as far as making custom titles to use in Openshot, you can create your title in any Inkscape, export it as a .png file, and then import it into OpenShot. This is easy to do, so I don't see this as a hindrance to using OpenShot flatpak.

---

### Post by satimis on 2022-03-20
> **Dennis N said:**
> I did confirm that OpenShot flatpak cannot open Inkscape from repo .deb package. If it's possible to permit this, I couldn't find a way.
So, based on that, I doubt it can open Blender installed from repo .deb package.

That said, as far as making custom titles to use in Openshot, you can create your title in any Inkscape, export it as a .png file, and then import it into OpenShot. This is easy to do, so I don't see this as a hindrance to using OpenShot flatpak.
Your advice noted and thanks

I don't need Inkscape.  I found alternative ways creating wonderful titles

1) With Libre Office as working table
1a) Copy&Paste an image on it as background
1b) Creating title wordings with selected fonts, color and sizes
1c) Take a screenshot of the title wordings and save it as .png file
1d) Creating the .png file with transparent background
1e) Import the .png file (transparent background) to Libre Office and dragging it on the image
1f) Take anther screenshot on the resultant title and save it as .png file
1g) Import the final .png file to OpenShot as title.

OR

2) Create title on GIMP, save it as .png file and import the .png file to OpenShot as Title.

I used those methods about 10 years ago.  I almost forgot them.  Also I haven't run GIMP for prolonged time.

Regards

---

