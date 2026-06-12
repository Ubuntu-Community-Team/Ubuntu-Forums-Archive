---
title: "Unable to play a VC-1 encoded MKV movie in vlc."
date: 2010-06-04
forum: Multimedia Software
---

### Post by Shadow_22k on 2010-06-04
Hello,
I am currently trying to play a VC-1 encoded MKV-file under Linux  (Ubuntu 10 / latest Mint, both are affected), but VLC reports that it isn't able to decode WVC-1. **VLC is  able to play this file under [COLOR=Blue]Fedora 13[/COLOR], OS X and Windows, while both mplayer and ffplay are able to play this movie under Ubuntu 10 and Linux Mint.**

I made two log files that where previously posted on the VLC forum, where I was told that it looks like there is a problem with the avcodec. I have basic experience with compiling stuff, but my knowledge of C++ and the linux internals is close to null. Which packages do I need to build from source in order recreate avcodec and its dpendendcies?

Link to error log running Ubuntu 10 and latest "Linux Mint" (reinstalled multiple times):
[http://pastebin.com/MnmYrMaD](http://pastebin.com/MnmYrMaD)

Link to log running Fedora13 (works, but I prefer debian based linux):
[http://pastebin.com/aVx65eVQ](http://pastebin.com/aVx65eVQ)

And last but not least a link to my thread on the VLC board:
[http://forum.videolan.org/viewtopic.php?f=13&t=76309](http://forum.videolan.org/viewtopic.php?f=13&t=76309)

regards

---

### Post by Shadow_2k on 2010-06-04
I've got it working by following this guide (clean up of some packages, compiled x264 and VLC from GIT): [http://www.webupd8.org/2010/01/how-to-compile-vlc-and-vlmc-from-git-in.html](http://www.webupd8.org/2010/01/how-to-compile-vlc-and-vlmc-from-git-in.html)

GIT release used:
[http://nightlies.videolan.org/build/source/branch-20100604-0208/vlc-snapshot-branch-1.1.0-20100604.tar.bz2](http://nightlies.videolan.org/build/source/branch-20100604-0208/vlc-snapshot-branch-1.1.0-20100604.tar.bz2)

---

