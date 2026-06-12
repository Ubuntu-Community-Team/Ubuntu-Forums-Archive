---
title: "FFmpeg: can't tell if using repository or compiled version"
date: 2018-10-26
forum: Multimedia Software
---

### Post by bennywas on 2018-10-26
Hi! :) I was having p[FONT=arial]roblems with how F[/FONT]Fmpeg converts to Ogg Theora, so I figured I'd try upgrading to the most recent version of FFmpeg to see if that fixes it. But the Ubuntu repositories only have version 3.4.4 (the most recent is 4.0.2), so I *compiled* the most recent version using [this guide]("https://linuxconfig.org/install-ffmpeg-on-ubuntu-18-04-bionic-beaver-linux").

This was my first time ever "compiling" a package and I'm left with a couple questions...namely, since both the old version and the new compiled version co-existing on my computer now, how do I tell which is being used?

[FONT=courier new]apt show ffmpeg [/FONT]shows the older version:
```
Package: ffmpeg
Version: 7:3.4.4-0ubuntu0.18.04.1
```

whereas[FONT=courier new] ffmpeg -version [/FONT]shows the one I just compiled:
```
ffmpeg version N-92249-g8c73301 Copyright (c) 2000-2018 the FFmpeg developers
built with gcc 7 (Ubuntu 7.3.0-27ubuntu1~18.04)
```

So here are my questions...
**1.** Is there a way to specify which ffmpeg version to use? (so I can see if the problems I was having were fixed in the newer version)

I know there's a difference between calling, for example, python vs python3. But these ffmpeg package names look identical...I tried calling[FONT=courier new] ffmpeg4 [/FONT]for kicks and got,
```
Command 'ffmpeg4' not found, did you mean:

  command 'ffmpeg' from snap ffmpeg (4.0.2)
  command 'ffmpeg' from deb ffmpeg
```
(Also: is it weird that this lists the newer version (4.0.2) as a snap package? But[FONT=courier new] snap list [/FONT]doesn't show ffmpeg...And I mean, I compiled it; so, it's not a snap...right?...[confused])

**2a.** How do I get info on the package version I compiled? (This is a general question about compiled packages.) I learned that[FONT=courier new] apt [/FONT]and[FONT=courier new] dpkg [/FONT]aren't showing my compiled ffmpeg because those commands are only for ".deb" packages. And it seems as though the compiled version is the one that's automatically used when I call "ffmpeg", because[FONT=courier new] ffmpeg -version [/FONT]shows N-92249-g8c73301 as opposed to 3.4.4. But I'd still like to know: is there a separate command I should be using that's similar to[FONT=courier new] apt list [/FONT]but will instead show all the packages I've *compiled*?
[B]
2b.[/B] Why does[FONT=courier new] ffmpeg -version [/FONT]return "version N-92249-g8c73301"? What *is* that string of gobbledegook? I'm pretty sure this is supposed to be version 4.0.2. I found [this answer]("https://lists.ffmpeg.org/pipermail/ffmpeg-user/2012-March/005323.html") to a similar question, saying that the string at the end is the "Git sort hash", but I don't understand the directions given in that post on how to find out which "Git sort hash" corresponds to which version. (Also I know extremely little [nothing] about how Git works, so.)


Does anyone have insight into any of this?? It would be much appreciated; this is pretty fun learning how all this stuff works.

---

### Post by Holger_Gehrke on 2018-10-27
1) The order of directories in the variable PATH decides what gets called if you enter the name of an executable without a path.
```

echo $path
/home/me/bin:/home/me/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin

```
As you can see, PATH contains a colon separated list of the directories which are searched when a program is called. If I put a script named 'ls' in ~/bin (and run 'hash -r' to make the shell forget that it had previously found 'ls' in '/bin'), calling ls will run my script instead of '/bin/ls'. By giving the path to the executable I can still call the 'real' ls. Similarly you can call the ffmpeg from the deb or the self-compiled one if you know where in the filesystem each is. Use "locate -b '\ffmpeg'" ('-b' tells locate that the argument is to be treated as a basename, the backslash at the beginning of the argument stops locate from treating it as '*ffmpeg*') to find the two ffmpegs (it will find more than two files but only two will be in directories that are in PATH; if it doesn't find both, then the database 'locate' uses to speed up searches has not been updated since you installed the new version). You can selectively call either version of ffmpeg by giving the full path to the executable, so '/usr/bin/ffmpeg' will call the version from the deb, and '/usr/local/bin/ffmpeg' probably is where the new version resides (just an educated guess - a lot of software installs there when compiled from source).

The results of calling 'ffmpeg4' are not all that surprising. The shell is set up to call a program if it doesn't find a command and that program searches the package lists of dpkg and the snap-store for commands you could have meant. There is obviously a snap of ffmpeg 4.0.2 (try 'snap find ffmpeg'). It didn't and doesn't know about your compiled ffmpeg.

2a) No. You just have to do the bookkeeping on what you've compiled and where you put what yourself. And that is one of the reasons why package managers were invented.

2b) The string of hexadecimal after the 'g' is the hash value of the last commit (=a change to the source code) in the git-repository of the code you compiled. By adding 'h=value' to the url of the git-repository like so [http://git.videolan.org/?p=ffmpeg.git&h=8c73301](http://git.videolan.org/?p=ffmpeg.git&h=8c73301) you get a page telling you who made that commit, when he did so and his comment on the commit (usually a reason for the change). It's actually a lot more specific than a version number.

Holger

---

### Post by mc4man on 2018-10-27
Your compiled version was installed to ~/bin which will take precedence over any other bin directory in your $PATH so to run just use ffmpeg
To use to repo version use full path so, /usr/bin/ffmpeg

---

### Post by bennywas on 2018-10-27
Thank you so much for the info!! It's great knowing how to selectively call the version I want. The path to the older version ended up being /usr/bin/ffmpeg, and the newer one's path is /home/benny/bin/ffmpeg. :cool:

Turns out that the newer ffmpeg version doesn't solve my original converting-to-Theora-looks-like-garbage problem...but I guess it's nice to have anyway. I think I'll create another thread for that question (unless I should keep it here?).

About the "commit" described at [http://git.videolan.org/?p=ffmpeg.git&h=8c73301](http://git.videolan.org/?p=ffmpeg.git&h=8c73301):
- Is there any way to "zoom out" from that commit to see what general #.#.# version the commit falls under? (I'm assuming that because the one I downloaded was super-recent it's 4.0.2 or similar, but it'd be nice to know)
- Are all of the commits on the [summary page]("http://git.videolan.org/?p=ffmpeg.git;a=summary") actually official commits?? It looks like people are working on this and saving a new commit literally several times every hour... I guess what I'm thinking is that from what I know about GitHub, anyone can make their own branches with their own tweaks and show them online, so I'm wondering if that's what all these are or if these are actually condoned by the FFmpeg developers.

---

