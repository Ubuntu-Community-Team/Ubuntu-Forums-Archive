---
title: "Lost audio after update"
date: 2009-02-14
forum: Multimedia Software
---

### Post by LocoMan on 2009-02-14
Greetings.

I updates ubuntu a couple days ago (the update icon on top). I got an error that some packages couldn't be retrieved from servers, I continued. Then gave me a list of packages that couldn't be retrieved (I think). Then it asked me to restart, I did, and now I lost audio.

The mixer icon has a red X on it, and if I click on it I get first

```
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.
```

then

```
No volume control GStreamer plugins and/or devices found.
```

Still asks me to upgrade, but when I try it, it just tells me the couldn't retrieve error again and shows this:

```
W: Failed to fetch http://ve.archive.ubuntu.com/ubuntu/pool/main/l/linux-ubuntu-modules-2.6.24/linux-ubuntu-modules-2.6.24-23-generic_2.6.24-23.36_i386.deb
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://ve.archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.5+nobinonly-0ubuntu0.8.04.1_i386.deb
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://ve.archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.5+nobinonly-0ubuntu0.8.04.1_i386.deb
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://ve.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.0.5+nobinonly-0ubuntu0.8.04.1_i386.deb
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://ve.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0_3.0.5+nobinonly-0ubuntu0.8.04.1_i386.deb
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://ve.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox_3.0.5+nobinonly-0ubuntu0.8.04.1_all.deb
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://ve.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-gnome-support_3.0.5+nobinonly-0ubuntu0.8.04.1_all.deb
  404 Not Found [IP: 91.189.88.45 80]
```

I have no idea what to do, or how to start troubleshooting it.

---

### Post by LocoMan on 2009-02-16
Bumping this.. I'd really hate having to reinstall ubuntu, it took me a while to get it all configured just like I liked... :(

---

### Post by LocoMan on 2009-02-17
Just a quick reply to let anyone interested (or having the same problem) to know that I fixed it following this guide:

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

No real idea what caused it, but followed all instructions, the driver was there (atiixp) but wasn't working, uninstalled and installed everything alsa related, and nothing, until I tried the part about compiling the drivers from scratch.

---

### Post by DavidTangye on 2009-02-18
The "Failed to fetch http://ve.archive.ubuntu.com/ubuntu" messages seem to indicate that you cannot get those packages from your country's Ubuntu distro archive.
Try again now. Perhaps the archive is fixed. Else perhaps try another repository, eg in Synaptic: Settings -> Repositories -> Download From [somewhere else].

---

