---
title: "MythTV on ubuntu 8.10/WinTV-PVR-150 - Beginner trouble"
date: 2009-02-06
forum: Multimedia Software
---

### Post by BB2008 on 2009-02-06
Hi Folks:

I am trying to setup my ubuntu box with a mythTV setup using my old WinTV-PVR-150 PCI card. I think I have the backend setup cirrectly, but when i start the frontend on the same machine and try to watch TV, I get a blank black screen for about 4o seconds, after which the mythtv frontend startup menu starts to show again.

I started mythfrontend from the command line, and this is what I see when I click the watch TV button:

```

2009-02-06 20:57:29.892 Connecting to backend server: 192.168.1.100:6543 (try 1 of 5)
2009-02-06 20:57:29.893 Using protocol version 40
2009-02-06 20:57:29.905 TV: Attempting to change from None to WatchingLiveTV
2009-02-06 20:57:29.906 Using protocol version 40
2009-02-06 20:57:31.213 DPMS Deactivated 
2009-02-06 20:58:11.117 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-02-06 20:58:11.117 TV Error: LiveTV not successfully started
2009-02-06 20:58:11.124 TV: Deleting TV Chain in destructor
2009-02-06 20:58:11.131 DPMS Reactivated.
2009-02-06 20:58:39.439 Deleting UPnP client...

```

Let me know if you need more information or dumps, will be glad to do that. Any help is very appreciated!

Thanks!

---

### Post by wolfen69 on 2009-02-06
did you select the right modules during setup? it will give the v4l modules by default unless you change it to pvrx50 from a pull down menu. you can always do the setup over again without reinstalling.

---

### Post by BB2008 on 2009-02-07
> **wolfen69 said:**
> did you select the right modules during setup? it will give the v4l modules by default unless you change it to pvrx50 from a pull down menu. you can always do the setup over again without reinstalling.

You are right! Thank for showing me the way - much appreciated. I was going with the default setting as I thought that based on the probe, myth was already showing that it detected PVR-150, so I thought I do not need to fiddle with the other settings. Turns out I had to, and once I selected the right option, it worked fine!

Enjoying TV on my monitor now!
:popcorn:

---

