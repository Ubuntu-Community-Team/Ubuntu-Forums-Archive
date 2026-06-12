---
title: "Can't view any youtube videos :("
date: 2014-02-07
forum: Multimedia Software
---

### Post by Camy on 2014-02-07
Dear All
I just installed Ubuntu 12.04LTS on a 13year old computer and am realy happy with it. The only snag is I can't watch any youtube videos thru firefox 26.0 for some reason. I also have a laptop with Ubuntu 12.04LTS that works fine.
I've compared the firefox plugins and they match and have been trying to solve this for a few days, and followed this [link]("http://www.techrepublic.com/blog/how-do-i/how-do-i-install-plugins-for-firefox-in-linux/"). Any help would be much appreciated.
Thanks


This is the plugin installed in firefox:
**Shockwave Flash**

File: libflashplayer.so
Path: /usr/lib/flashplugin-installer/libflashplayer.so
Version: 11,2,202,336
State: Enabled
Shockwave Flash 11.2 r202
[TABLE="class: contenttable"]
[TR]
[TH="class: type"]MIME Type[/TH]
[TH="class: desc"]Description[/TH]
[TH="class: suff"]Suffixes[/TH]
[/TR]
[TR]
[TD]application/x-shockwave-flash[/TD]
[TD]Shockwave Flash[/TD]
[TD]swf[/TD]
[/TR]
[TR]
[TD]application/futuresplash[/TD]
[TD]FutureSplash Player[/TD]
[TD]spl[/TD]
[/TR]
[/TABLE]

---

### Post by theDaveTheRave on 2014-02-07
Have you tried using the [flash-aid]("http://www.ubuntugeek.com/flash-aid-firefox-add-on.html") pluggin for firefox?

I recall having the same problem for a while untill I found it.

The link above has details for installing it in firefox.

Alternatively have you tried with another browser.

David

---

### Post by Camy on 2014-02-08
Hi David, the link you provided says 'This add-on has been removed by its author.' :( 
Haven't tried any other browser yet. I was kind of hoping it was something simple to fix.
Thanks

---

### Post by carl4926 on 2014-02-08
With such an old computer it's likely the current version of flash doesn't work with your CPU
People in a similar situation as you have looked for and installed version 10.3 of flash
Obviously there are security issues with that option
If flash is a must for you, it's time for a new machine

---

### Post by Dennis N on 2014-02-08
>  I can't watch any youtube videos thru firefox 26.0 for some reason

Its not clear what this means. Do the videos start and play? If so, what is wrong with them that makes them unwatchable? Are you watching full screen or what size? Could be your processor is too underpowered to handle the processing load - the video will skip frames and the audio becomes out of synch.

---

### Post by carl4926 on 2014-02-08
From a terminal run

```
cat /proc/cpuinfo
```

In the section near the end under flags
You will see something like this
```
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse **[COLOR=#800000]sse2[/COLOR]** ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm dtherm
```

You need to see at least sse2

---

### Post by Camy on 2014-02-08
Installed Epiphany and the related flash plugin and I can view Youtube videos using Epiphany.

---

### Post by Camy on 2014-02-08
Yes, sorry Dennis N.  The usual black area that comes up before the play button is available, is white and there is nothing there. No play button, nothing The processor is working pretty good as there is hardly any difference between this comp and my 4 year old laptop, and it is actually faster than a small windows laptop I bought 2 years ago.

---

### Post by Camy on 2014-02-08
[LEFT][COLOR=#000000][FONT=Ubuntu Mono]**cat /proc/cpuinfo**
[/FONT][/COLOR][/LEFT]
processor    : 0vendor_id    : AuthenticAMD
cpu family    : 6
model        : 10
model name    : AMD Athlon(tm) XP 3000+
stepping    : 0
cpu MHz        : 2168.439
cache size    : 512 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
bogomips    : 4336.87
clflush size    : 32
cache_alignment    : 32
address sizes    : 34 bits physical, 32 bits virtual
power management: ts
 
No sse2 :( but I've got it working in Epiphany now.

---

### Post by carl4926 on 2014-02-08
> [COLOR=#000000]No sse2 [/COLOR]:sad:[COLOR=#000000] but I've got it working in Epiphany now.[/COLOR]Remarkable, because that browser is so unreliable - I never even try it now. YMMV of course and I'm happy for you

---

### Post by Camy on 2014-02-08
Carl, I would prefer using firefox. One thing I noticed was when I tried to install the flash plugin from Epiphany from [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) I chose APT for Ubuntu 10.4 and the Ubuntu software centre was selected automatically, but when trying to do it like this in firefox I get a box saying 'this link needs to be opened with an application' so I chose the tar.gz file instead and installed it manually. I think this is my mistake.
How do I chose the Ubuntu software centre through the browse button?

---

### Post by Camy on 2014-02-08
I found the command to start the software-center which is '/usr/bin/software-center' and used it to install the 'Apt for Ubuntu flash-player' but still no luck.

---

### Post by carl4926 on 2014-02-08
Flash is part of the restricted extras

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by tony34 on 2014-02-09
Go to your Terminal (CTRL Alt t)
Type the following command:
*sudo apt-get install flashplugin-installer*

It will ask for your user password and then install the necessary flash plugin.
Even if you get an error stating that not all dependencies were installed check your videos. Your problem may have been solved.

---

### Post by monkeybrain20122 on 2014-02-09
Install greasemonkey addon for Firefox, then install Viewtube. [http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)
Install ubuntu-restricted-extras and optionally gecko-mediaplayer and [https://addons.mozilla.org/en-us/firefox/addon/toggle-mixed-active-content/](https://addons.mozilla.org/en-us/firefox/addon/toggle-mixed-active-content/) (see the little box with a green A in the bottom, click it to turn it to red) Then you don't need flash for Youtube. 

Do you have problems with other flash sites.

---

### Post by Camy on 2014-02-10
Thanks tony34, did as you said, then restarted firefox. It seems to have installed correctly but I still can't view youtubes. :(

Preconfiguring packages ...
(Reading database ... 260229 files and directories currently installed.)
Removing adobe-flash-properties-gtk ...
Removing adobe-flashplugin ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Selecting previously unselected package flashplugin-installer.
(Reading database ... 260203 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_11.2.202.336ubuntu0.12.04.1_i386.deb) ...
Processing triggers for update-notifier-common ...
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.336.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.336.orig.tar.gz)
Installing from local file /tmp/tmp7s6Vu9.gz
Flash Plugin installed.
Setting up flashplugin-installer (11.2.202.336ubuntu0.12.04.1) ...

---

### Post by Camy on 2014-02-10
Hey monkeybrain, thanks a lot. Followed you instructions and it's all good now.
Thanks a million.
:) Very happy with my old comp and Ubuntu :)

---

