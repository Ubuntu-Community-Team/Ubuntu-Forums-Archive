---
title: "python 2.6 is back...?"
date: 2011-02-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by zika on 2011-02-03
```
The following NEW packages will be installed:
  libpython2.6{a} python2.6{a} python2.6-minimal{a}
The following packages will be upgraded:
  libglew1.5 libglewmx1.5 python-cupshelpers python-gobject 
  python-gobject-cairo system-config-printer-common 
  system-config-printer-gnome system-config-printer-udev
```

---

### Post by Harry33 on 2011-02-03
> **zika said:**
> ```
The following NEW packages will be installed:
  libpython2.6{a} python2.6{a} python2.6-minimal{a}
The following packages will be upgraded:
  libglew1.5 libglewmx1.5 python-cupshelpers python-gobject 
  python-gobject-cairo system-config-printer-common 
  system-config-printer-gnome system-config-printer-udev
```

What the h...
What were you installing/upgrading, when you got that?

---

### Post by zika on 2011-02-03
> **Harry33 said:**
> What the h...
What were you installing/upgrading, when you got that?The only stuff that I was working on today is TeXLive...
Then, I wanted to do regular (before sleep) update/upgrade and voilà...

```
~$ sudo aptitude upgrade
Resolving dependencies...                
The following NEW packages will be installed:
  libpython2.6{a} python2.6{a} python2.6-minimal{a} 
The following packages will be upgraded:
  libglew1.5 libglewmx1.5 python-cupshelpers python-gobject 
  python-gobject-cairo system-config-printer-common 
  system-config-printer-gnome system-config-printer-udev 
8 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,128 kB of archives. After unpacking 18.0 MB will be used.
Do you want to continue? [Y/n/?] n
Abort.
```

I do have libpython2.7 python2.7 python2.7-minimal installed, they are dependencies that these system-config-printer packages need but they have >=2.5 or similar.

---

### Post by Harry33 on 2011-02-03
> **zika said:**
> The only stuff that I was working on today is TeXLive...
Then, I wanted to do regular (before sleep) update/upgrade and voilà...

```
~$ sudo aptitude upgrade
Resolving dependencies...                
The following NEW packages will be installed:
  libpython2.6{a} python2.6{a} python2.6-minimal{a} 
The following packages will be upgraded:
  libglew1.5 libglewmx1.5 python-cupshelpers python-gobject 
  python-gobject-cairo system-config-printer-common 
  system-config-printer-gnome system-config-printer-udev 
8 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,128 kB of archives. After unpacking 18.0 MB will be used.
Do you want to continue? [Y/n/?] n
Abort.
```

I do have libpython2.7 python2.7 python2.7-minimal installed, they are dependencies that these system-config-printer packages need but they have >=2.5 or similar.

Well this is interesting indeed.
You have done nothing wrong there.

The new pygobject_2.27.0+git20110131-0ubuntu2 (packages python-gobject and python-gobject-cairo)
[https://launchpad.net/ubuntu/natty/+source/pygobject/2.27.0+git20110131-0ubuntu2](https://launchpad.net/ubuntu/natty/+source/pygobject/2.27.0+git20110131-0ubuntu2)
depends on both libpython2.6 and libpython2.7.
There must be a mistake in those builds.
I would not upgrade those. The former pygobject_2.27.0+git20110108-0ubuntu1 was OK, without libpython dependencies.

I call that a regression.

---

### Post by mc4man on 2011-02-03
Those new package upgrades have a build-dep on python-all-dev which deps to both python2.6-dev and python2.7-dev, that can create an install dep of the 2.6
(possibly this was unintentional

---

### Post by Harry33 on 2011-02-03
Here is the bug report:
[https://bugs.launchpad.net/ubuntu/+source/pygobject/+bug/712734](https://bugs.launchpad.net/ubuntu/+source/pygobject/+bug/712734)

---

### Post by zika on 2011-02-03
> **Harry33 said:**
> Here is the bug report:
[https://bugs.launchpad.net/ubuntu/+source/pygobject/+bug/712734](https://bugs.launchpad.net/ubuntu/+source/pygobject/+bug/712734)Confirmed it.

---

### Post by Harry33 on 2011-02-04
Now there is a new update to the pygobject (= 2.27.0+git20110131-0ubuntu3) in repos, but that one cannot be installed, because of incorrect provided virtual packages.
The installation would remove python-gtk2 and thus several important applications
(like firefox, gedit, gnome-panel, update-manager ...).
Let's wait for the fix.

---

### Post by zika on 2011-02-04
At least no offer for python2.6```
Current status: 37 updates [+29], 148 new [+2].
Resolving dependencies...                
The following NEW packages will be installed:
  libfolks-telepathy20{a} libfolks20{a} 
The following packages will be upgraded:
  appmenu-gtk chromium-browser chromium-browser-inspector 
  chromium-codecs-ffmpeg empathy empathy-common google-chrome-unstable 
  gstreamer0.10-alsa gstreamer0.10-plugins-base 
  gstreamer0.10-plugins-base-apps gstreamer0.10-x indicator-applet 
  indicator-applet-session indicator-application indicator-appmenu 
  jockey-common jockey-gtk libdbusmenu-glib3 libdbusmenu-gtk3 libglew1.5 
  libglewmx1.5 libgstreamer-plugins-base0.10-0 libindicate-gtk2 
  libindicate5 libsqlite3-0 nautilus-sendto-empathy python-cupshelpers 
  python-gobject-cairo python-indicate system-config-printer-common 
  system-config-printer-gnome system-config-printer-udev 
  transmission-common transmission-gtk upstart xkb-data 
36 packages upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 44.3 MB of archives. After unpacking 1,024 kB will be used.
Do you want to continue? [Y/n/?] 
```... :)
(and a partial, as I can see...)
```
:~$ sudo aptitude dist-upgrade
The following NEW packages will be installed:
  libfolks-telepathy20{a} libfolks20{a} 
The following packages will be upgraded:
  appmenu-gtk chromium-browser chromium-browser-inspector chromium-codecs-ffmpeg empathy empathy-common google-chrome-unstable gstreamer0.10-alsa gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-x indicator-applet indicator-applet-session indicator-application 
  indicator-appmenu jockey-common jockey-gtk libdbusmenu-glib3 libdbusmenu-gtk3 libglew1.5 libglewmx1.5 libgstreamer-plugins-base0.10-0 libindicate-gtk2 libindicate5 libsqlite3-0 nautilus-sendto-empathy python-cupshelpers python-gobject python-gobject-cairo python-indicate 
  system-config-printer-common system-config-printer-gnome system-config-printer-udev transmission-common transmission-gtk upstart xkb-data 
37 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 44.6 MB of archives. After unpacking 229 kB will be used.
The following packages have unmet dependencies:
  python-gnome2: Depends: python2.6-gobject which is a virtual package.
  python-gtksourceview2: Depends: python2.6-gobject which is a virtual package.
  python-gtk2: Depends: python2.6-gobject which is a virtual package.
  python-gconf: Depends: python2.6-gobject which is a virtual package.
The following actions will resolve these dependencies:

       Remove the following packages:                                               
1)       alacarte                                                                   
2)       apturl                                                                     
3)       banshee-extension-ubuntuonemusicstore                                      
4)       checkbox-gtk                                                               
5)       computer-janitor-gtk                                                       
6)       driconf                                                                    
7)       firefox                                                                    
8)       firefox-branding                                                           
9)       firefox-gnome-support                                                      
10)      gdebi                                                                      
11)      gedit                                                                      
12)      gedit-latex-plugin                                                         
13)      gimp                                                                       
14)      gnome-about                                                                
15)      gnome-applets                                                              
16)      gnome-codec-install                                                        
17)      gnome-control-center                                                       
18)      gnome-menus                                                                
19)      gnome-orca                                                                 
20)      gnome-panel                                                                
21)      gnome-sudoku                                                               
22)      gwibber                                                                    
23)      gwibber-service                                                            
24)      gwibber-service-facebook                                                   
25)      gwibber-service-identica                                                   
26)      gwibber-service-twitter                                                    
27)      ibus                                                                       
28)      ibus-pinyin                                                                
29)      ibus-table                                                                 
30)      indicator-applet                                                           
31)      indicator-applet-session                                                   
32)      indicator-me                                                               
33)      libgwibber1                                                                
34)      libsyncdaemon-1.0-1                                                        
35)      libubuntuone-1.0-1                                                         
36)      libubuntuone1.0-cil                                                        
37)      onboard                                                                    
38)      pitivi                                                                     
39)      python-gconf                                                               
40)      python-glade2                                                              
41)      python-gmenu                                                               
42)      python-gnome2                                                              
43)      python-gnomekeyring                                                        
44)      python-gtk2                                                                
45)      python-gtksourceview2                                                      
46)      python-gtkspell                                                            
47)      python-ibus                                                                
48)      python-notify                                                              
49)      python-poppler                                                             
50)      python-pyatspi                                                             
51)      python-pygoocanvas                                                         
52)      python-ubuntuone-client                                                    
53)      python-vte                                                                 
54)      python-webkit                                                              
55)      python-wnck                                                                
56)      rhythmbox                                                                  
57)      rhythmbox-plugin-cdrecorder                                                
58)      rhythmbox-plugins                                                          
59)      software-center                                                            
60)      software-properties-gtk                                                    
61)      system-config-printer-gnome                                                
62)      totem-plugins                                                              
63)      ubufox                                                                     
64)      ubuntu-desktop                                                             
65)      ubuntu-sso-client                                                          
66)      ubuntuone-client                                                           
67)      ubuntuone-client-gnome                                                     
68)      update-manager                                                             
69)      update-notifier                                                            
70)      usb-creator-gtk                                                            
71)      xul-ext-ubufox                                                             

       Leave the following dependencies unresolved:                                 
72)      apport-gtk recommends update-notifier                                      
73)      banshee recommends banshee-extension-ubuntuonemusicstore (= 1.9.2-1ubuntu1)
74)      capplets-data recommends gnome-control-center (>= 1:2.32.1-0ubuntu3)       
75)      gedit-common recommends gedit                                              
76)      gimp-data recommends gimp                                                  
77)      gnome-panel recommends alacarte                                            
78)      gnome-panel recommends python-gconf                                        
79)      gnome-panel-data recommends gnome-panel                                    
80)      indicator-applet-session recommends indicator-me                           
81)      indicator-me recommends gwibber (>= 2.29.90)                               
82)      libappindicator1 recommends indicator-application (= 0.2.92-0ubuntu1)      
83)      libgimp2.0 recommends gimp                                                 
84)      mousetweaks recommends gnome-control-center                                
85)      rhythmbox-plugins recommends python-webkit                                 
86)      synaptic recommends software-properties-gtk                                
87)      totem recommends totem-plugins (>= 2.32.0-0ubuntu8)                        
88)      ubuntu-desktop recommends computer-janitor-gtk                             
89)      ubuntu-desktop recommends gnome-codec-install                              
90)      ubuntu-desktop recommends gnome-orca                                       
91)      ubuntu-desktop recommends gnome-sudoku                                     
92)      ubuntu-desktop recommends ibus                                             
93)      ubuntu-desktop recommends ibus-pinyin                                      
94)      ubuntu-desktop recommends ibus-table                                       
95)      ubuntu-desktop recommends onboard                                          
96)      ubuntu-desktop recommends pitivi                                           
97)      unity recommends indicator-me                                              
98)      update-manager recommends software-properties-gtk (>= 0.71.2)              
99)      update-notifier recommends software-properties-gtk                         
100)     xul-ext-ubufox recommends firefox (>= 4.0~b6) | abrowser (>= 4.0~b6)       


Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
```

---

### Post by Quackers on 2011-02-04
I noticed that last night so didn't update that package. That's another held package for me (that's 43 now! :-) )

---

### Post by zika on 2011-02-04
Hop! Again!
```
Current status: 42 updates [+3].
Resolving dependencies...                
The following NEW packages will be installed:
  libfolks-telepathy20{a} libfolks20{a} libpython2.6{a} python2.6{a} python2.6-minimal{a} 
The following packages will be upgraded:
  appmenu-gtk chromium-browser chromium-browser-inspector chromium-codecs-ffmpeg empathy empathy-common google-chrome-unstable gstreamer0.10-alsa gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-x indicator-applet indicator-applet-session indicator-application 
  indicator-appmenu jockey-common jockey-gtk libdbusmenu-glib3 libdbusmenu-gtk3 libglew1.5 libglewmx1.5 libgstreamer-plugins-base0.10-0 libindicate-gtk2 libindicate5 libsqlite3-0 nautilus-sendto-empathy popularity-contest ppp python-cupshelpers python-gobject python-gobject-cairo 
  python-indicate system-config-printer-common system-config-printer-gnome system-config-printer-udev transmission-common transmission-gtk ubuntu-sso-client upstart xkb-data xserver-common xserver-xorg-core 
42 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 52.1 MB of archives. After unpacking 19.1 MB will be used.
Do you want to continue? [Y/n/?] n
Abort.

:~$ sudo aptitude dist-upgrade
The following NEW packages will be installed:
  libfolks-telepathy20{a} libfolks20{a} libpython2.6{a} python2.6{a} python2.6-minimal{a} 
The following packages will be upgraded:
  appmenu-gtk chromium-browser chromium-browser-inspector chromium-codecs-ffmpeg empathy empathy-common google-chrome-unstable gstreamer0.10-alsa gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-x indicator-applet indicator-applet-session indicator-application 
  indicator-appmenu jockey-common jockey-gtk libdbusmenu-glib3 libdbusmenu-gtk3 libglew1.5 libglewmx1.5 libgstreamer-plugins-base0.10-0 libindicate-gtk2 libindicate5 libsqlite3-0 nautilus-sendto-empathy popularity-contest ppp python-cupshelpers python-gobject python-gobject-cairo 
  python-indicate system-config-printer-common system-config-printer-gnome system-config-printer-udev transmission-common transmission-gtk ubuntu-sso-client upstart xkb-data xserver-common xserver-xorg-core 
42 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 52.1 MB of archives. After unpacking 19.1 MB will be used.
Do you want to continue? [Y/n/?] n
Abort.
```

---

### Post by MadCow108 on 2011-02-04
it has been readded and dropped again:
[https://launchpad.net/ubuntu/+source/pygobject/+changelog](https://launchpad.net/ubuntu/+source/pygobject/+changelog)
the latter has not hit the repositories yet.

---

### Post by Harry33 on 2011-02-04
> **MadCow108 said:**
> it has been readded and dropped again:
[https://launchpad.net/ubuntu/+source/pygobject/+changelog](https://launchpad.net/ubuntu/+source/pygobject/+changelog)
the latter has not hit the repositories yet.

That is right.
Now the regression-bug has been really fixed.
No more unmet dependencies with the version 2.7.0+git20110131-0ubuntu5
Here:
[https://launchpad.net/ubuntu/natty/+source/pygobject/2.27.0+git20110131-0ubuntu5](https://launchpad.net/ubuntu/natty/+source/pygobject/2.27.0+git20110131-0ubuntu5)

This will soon be Natty repos.

---

### Post by zika on 2011-02-04
```
:~$ sudo aptitude dist-upgrade
[sudo] password for zika: 
The following NEW packages will be installed:
  libfolks-telepathy20{a} libfolks20{a} 
The following packages will be upgraded:
  appmenu-gtk chromium-browser chromium-browser-inspector chromium-codecs-ffmpeg empathy empathy-common google-chrome-unstable gstreamer0.10-alsa gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-x indicator-applet indicator-applet-session indicator-application 
  indicator-appmenu jockey-common jockey-gtk libdbusmenu-glib3 libdbusmenu-gtk3 libglew1.5 libglewmx1.5 libglibmm-2.4-1c2a libgstreamer-plugins-base0.10-0 libindicate-gtk2 libindicate5 libsqlite3-0 nautilus-sendto-empathy popularity-contest ppp python-cupshelpers python-gobject 
  python-gobject-cairo python-indicate system-config-printer-common system-config-printer-gnome system-config-printer-udev transmission-common transmission-gtk ubuntu-sso-client upstart xkb-data xserver-common xserver-xorg-core 
43 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 47.4 MB of archives. After unpacking 1,094 kB will be used.
Do you want to continue? [Y/n/?]
```
```
:~$ sudo aptitude safe-upgrade 
Resolving dependencies...                
The following NEW packages will be installed:
  libfolks-telepathy20{a} libfolks20{a} 
The following packages will be upgraded:
  appmenu-gtk chromium-browser chromium-browser-inspector chromium-codecs-ffmpeg empathy empathy-common google-chrome-unstable gstreamer0.10-alsa gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-x indicator-applet indicator-applet-session indicator-application 
  indicator-appmenu jockey-common jockey-gtk libdbusmenu-glib3 libdbusmenu-gtk3 libglew1.5 libglewmx1.5 libglibmm-2.4-1c2a libgstreamer-plugins-base0.10-0 libindicate-gtk2 libindicate5 libsqlite3-0 nautilus-sendto-empathy popularity-contest ppp python-cupshelpers python-gobject 
  python-gobject-cairo python-indicate system-config-printer-common system-config-printer-gnome system-config-printer-udev transmission-common transmission-gtk ubuntu-sso-client upstart xkb-data xserver-common xserver-xorg-core 
43 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 47.4 MB of archives. After unpacking 1,094 kB will be used.
Do you want to continue? [Y/n/?]
```

Thank You!
Case closed...

---

