---
title: "VLC fullscreen problem"
date: 2008-09-05
forum: Multimedia Software
---

### Post by nexusgx on 2008-09-05
I have a problem when putting a video into fullscreen.

When I first open the video in window mode, it plays just fine, no problems. When I make it go full screen, i lose the video, but can still hear the audio. When i go back to window mode, there is, what seems like, a black semi-transparent layer of some sort over the entire screen with the exception of about a 5px border around the screen. This layer doesn't interfer with normal mouse and keyboard operations, but it is difficult trying to work at half brightness. The layer does not go away, even after closing VLC, which makes me wonder if there is something else going on outside of VLC itself.

So my question is, is there a way to fix this or prevent this from happening other than not going fullscreen anymore?

I have an ATI radeon x800 card, which i have tried with both drivers installed and not installed. I have also tried uninstalling and reinstalling, which did nothing. I am running Kubuntu 8.04

---

### Post by jbrown96 on 2008-09-05
Are you using the composite features of Kwin or Compiz. I know that compiz has a setting that allows video playback to work. You may need to install the compiz settings manager (ccsm i believe). I looked through kwin's settings with kde4.1.1 and could find a plugin like that. Try disabling the compositing. Have you tried any other video players to see if the same problem occurs?

---

### Post by nexusgx on 2008-09-05
Yes, I have successfully used Kaffeine in fullscreen mode and then reverted back to normal with no problems.  I just tried this now.

I had compiz on here once before but had to get rid of it because it was giving me just a blank white screen.

---

### Post by jbrown96 on 2008-09-05
Try changing the output modules in preferences-->video-->output modules. You have to check the advanced options. Try the openGL and X11 modes... or ascii which is my favorite.

---

### Post by nexusgx on 2008-09-05
> **jbrown96 said:**
> Try changing the output modules in preferences-->video-->output modules. You have to check the advanced options. Try the openGL and X11 modes... or ascii which is my favorite.

thanks, That got the video to show up, but it still leaves that semi-transparent area over the whole screen.

---

### Post by nexusgx on 2008-09-05
I seem to have gotten it to stop leaving that semi-transparent area by selecting XVideo extension as my output.  Thanks for all your help!

---

