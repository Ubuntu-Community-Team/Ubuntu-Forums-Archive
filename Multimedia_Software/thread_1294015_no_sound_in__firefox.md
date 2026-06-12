---
title: "no sound in  firefox"
date: 2009-10-17
forum: Multimedia Software
---

### Post by karian021 on 2009-10-17
hi guys i have a problem when i try tu  watch a video on youtube or like linuxjournal,i get no sound, i ran firefox in terminal and i got this


 :~$ firefox
!!! [Hook] hook(): title not found
!!! [Hook] hook(): title not found

i tried to watch the video  when ruuning firefox in termianl and i think that's when i got  
           !!! [Hook] hook():           title not found the second time,i know know the settings are fine  because  when i try to watch a video or listen to a song on vlc player or smplayer y get sound and video can you guys help me out i'm running  ubuntu 8.10 the 64 version and i installed the 64 version of flash,and it had worked fine until today,i happened suddenly because i was watching  videos on youtube  and  i had sound and of all a sudden  it was gone,it happend to me before,but when i rebooted my computer my sound was back on again,help please

---

### Post by karian021 on 2009-10-18
dome on guys,any idea?

---

### Post by KIAaze on 2010-07-11
Happening to me too now.
Worked yesterday. Didn't change anything (no updates, no add-ons installed, no reboots, etc) and now it constantly crashes when trying to play any flash video.
Even in safe mode!

```
!!! [Hook] hook(): title not found
!!! [Hook] hook(): title not found
2.4+ kernel w/o ELF notes? -- report this
!!! [Hook] hook(): title not found
Segmentation fault

```

```
[^_^][11][~]$  lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04 LTS
Release:	10.04
Codename:	lucid
[^_^][12][~]$  uname -a
Linux my-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
[^_^][15][~]$  firefox --version
Mozilla Firefox 3.6.3, Copyright (c) 1998 - 2010 mozilla.org

```

```
Flash version: 10,1,53,64
```

edit: Interesting fact:
Flash stopped working in Google chrome too, but doesn't take down the browser with it. It says that the following plugin has crashed:
/usr/lib/flashplugin-installer/libflashplayer.so

re-edit:
Everything works again after reboot.

---

