---
title: "itunes not working"
date: 2008-08-26
forum: Multimedia Software
---

### Post by methodtwo on 2008-08-26
Hi there.I'm running ubuntu 7.10.I've installed wine using the synaptic package manager.In the audio tab i selected ALSA and deselected OSS.I also selected windows XP in the applications tab.I then got itunes and did:
linux#wine iTunesSetup.exe
all seemed fairly normal
but when i do:
linux#wine ~/.wine/drive_c/Program\ Files/iTunes/iTunes.exe

the screen goes blank and i get this output:
matt@linux:~$ wine ~/.wine/drive_c/Program\ Files/iTunes/Itunes.exe
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:htmlhelp:HtmlHelpW HH case HH_INITIALIZE not handled.
fixme:heap:HeapSetInformation 0x1db0000 0 0x33f718 4
fixme:win:EnumDisplayDevicesW ((null),0,0x33ebd0,0x00000000), stub!
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1377f8)->((nil),00000008)
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x40042 0x00000000

and i have to do cntrl-alt-f1 followed by cntrl-alt-f7 to even have a normal X as before.Any help would be great.Thankx in advance
Sorry but i don't know how to do code blocks on this forum!

---

### Post by methodtwo on 2008-08-26
I guess i just might need a newer version of wine right?

---

### Post by snowpine on 2008-08-26
As far as I know, iTunes does not work with Wine. Sadly, Apple has no interest whatsoever in Linux customers. :(

There are some excellent alternatives, though, like Amarok, Rhythmbox, Banshee, etc. so hopefully you'll find one you like. Good luck!

---

