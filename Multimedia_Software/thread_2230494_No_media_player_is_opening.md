---
title: "No media player is opening"
date: 2014-06-19
forum: Multimedia Software
---

### Post by Tanmay_Das on 2014-06-19
This is the weirdest situation I have ever encountered in my more than 5 years of linux usage.

Today I made 3 notable changes to my system for which I think I am unable to run SMPlayer and VLC Media Player. I can only run the default player, Totem.

0) As always, I sudo apt-get updated my Ubuntu 14.04.
1) I attempted to install MonoDevelp 5. But I needed Mono Runtime 3.x.x or higher installed. I tried to install that and I successfully failed.
2) I installed the latest version of Code::Blocks IDE from a tarball and during the installation it was warning me that some packages (codeblocks-contrib, codeblocks-* or something similar) were not installed because of the dependencies. But the IDE was running fine and I didn't face any problem with that. But suddenly I noticed a red notification icon on Ubuntu Top Panel. I clicked there and found that there is a problem with broken packages. After 1 hour of googling, I fixed that by uninstalling Code::Blocks.

After installing Code::Blocks I can't run my favorite SMPlayer anymore. I installed VLC few minutes ago. Which is also unable to run. Now, what is causing the problem and how can I fix it?

---

### Post by SeijiSensei on 2014-06-20
This thread is marked [SOLVED].  Is it really?

I'd start by seeing if you can play a video using mplayer itself from the command prompt.  SMPlayer is simply a front-end for the mplayer software. Try running
```
mplayer /path/to/some/video.file
```
Mplayer should report any problems it encounters.  If you need more details, use "mplayer -v" for more "verbosity."

---

