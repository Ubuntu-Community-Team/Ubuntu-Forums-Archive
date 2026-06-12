---
title: "X server restarts abnormally"
date: 2011-09-25
forum: Multimedia Software
---

### Post by radiobert on 2011-09-25
Today I was watching a video clip on youtube in firefox. And, by chance, I clicked the "system settings" from the kickoff application launcher, and the X server restarts, returning the screen to login page. 

I decided to try to do the same thing again, open a youtube video in firefox, and then starting the "system settings". After a few tries I am sure that there's a bug in the X server or the graphics driver itself. 
(I am using Kubuntu 10.04, with proprietary Ati driver (fglrx))
Supposedly, a crash handling program should start, and automatically generate the backtrace so that I can file a bug report, but I am not sure how to activate the "debugging feature" of kubuntu. Anyway, I managed to get some info from the system log, as shown below: 


```
2011-09-25 18:51:23    tyf-desktop    kernel    [34201.378961] [fglrx] IRQ 30 Disabled
2011-09-25 18:51:23    tyf-desktop    python    io/hpmud/hpmud.c 367: [21051] hpmud_exit()
2011-09-25 18:51:24    tyf-desktop    scim-bridge    FIXME: not implemented yet: ScimBridgeAgentPanelListenerImpl::slot_exit ()
2011-09-25 18:51:24    tyf-desktop        Error creating socket
2011-09-25 18:51:24    tyf-desktop        socket 
2011-09-25 18:51:24    tyf-desktop        syscall failed
2011-09-25 18:51:24    tyf-desktop        
2011-09-25 18:51:24    tyf-desktop        Success
2011-09-25 18:51:24    tyf-desktop        tyf-desktop
2011-09-25 18:51:24    tyf-desktop    kdm[1013]    X server for display :0 terminated unexpectedly
2011-09-25 18:51:24    tyf-desktop    kernel    [34201.429522] ALSA hda_codec.c:1471: hda_codec_cleanup_stream: NID=0x2
2011-09-25 18:51:24    tyf-desktop    kernel    [34201.429525] ALSA hda_codec.c:1471: hda_codec_cleanup_stream: NID=0x3
2011-09-25 18:51:24    tyf-desktop    kernel    [34201.429528] ALSA hda_codec.c:1471: hda_codec_cleanup_stream: NID=0x4
2011-09-25 18:51:24    tyf-desktop    kernel    [34201.429530] ALSA hda_codec.c:1471: hda_codec_cleanup_stream: NID=0x5
2011-09-25 18:51:24    tyf-desktop    kernel    [34201.429532] ALSA hda_codec.c:1471: hda_codec_cleanup_stream: NID=0x6
2011-09-25 18:51:24    tyf-desktop    acpid    client 20752[0:0] has disconnected
2011-09-25 18:51:24    tyf-desktop    acpid    client connected from 22586[0:0]
2011-09-25 18:51:24    tyf-desktop    acpid    1 client rule loaded

```

---

### Post by radiobert on 2011-09-25
While investigating further, I found that the problem occurs only when desktop compositing is enabled.

---

### Post by radiobert on 2011-09-26
Another funny thing is that, google chrome does not make X server restart.....So, is it the problem of firefox or X server or kernel?

---

