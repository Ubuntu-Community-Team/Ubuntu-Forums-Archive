---
title: "Ksubtitleripper problem (can't enter text)"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by QOLIM on 2007-07-16
I'm ripping some of the dvd's I have.
And I want to rip the subtitles to srt's

So I downloaded ksubtitleripper
And got it working almost perfectly thanks to [this]("http://developer.berlios.de/patch/?func=detailpatch&patch_id=2068&group_id=1613") patch.

But the problem I'm still having is that I just can't type anything during the ocr
So I still can't rip them.

[http://img249.imageshack.us/my.php?image=ksubeu7.png]("http://img249.imageshack.us/my.php?image=ksubeu7.png")

Help would be appreciated

Thx,

QOLIM

---

### Post by Selanit on 2007-08-13
I have fixed this problem and submitted a new patch to the original project.  It looks to me as though ksubtitleripper is unmaintained at this time, since it hasn't been updated since May 2005.  My patch can be found here:

[Editing UI patch](http://developer.berlios.de/patch/?func=detailpatch&patch_id=2137&group_id=1613).

Here's a mini howto for the benefit of newbies.

In order to get KSubtitleRipper working, you need to do the following things:

1) Install following packages:

-- kdebase-dev
-- xlibs-dev

These provide needed library files for compiling the program.  It's possible you may need other things too, depending on what you do or don't have installed.

2) Grab a copy of [the KSubtitleRipper source code](http://download.berlios.de/ksubtitleripper/ksubtitleripper-0.3.1.tar.bz2).

3) Unpack the source code.  You can do this either by double-clicking it in the file manager and dragging its contents into a new folder, or on the command line.  On the command line, and assuming you've downloaded the file to your home directory, the commands are:

```
cd ~
bunzip2 ksubtitleripper-0.3.1.tar.bz2
tar -xvf ksubtitleripper-0.3.1.tar.bz2
```

4) Get a copy of mouse256's [gocr patch](http://developer.berlios.de/patch/download.php?id=2068).

I'm not sure what the command is to automatically apply a patch.  I eventually wound up doing it manually.  In the patch file, any line beginning with a minus needs to be removed from convertdialog.cpp, and any line beginning with a plus needs to be added into convertdialog.cpp.  Copying and pasting is fine, but be sure to delete the plus characters -- they'll prevent the file from compiling if they're present.

5) Get a copy of my [edit UI patch](http://developer.berlios.de/patch/download.php?id=2137).  Apply it to convertdialog.cpp too.

6) Compile the modified program:

```
cd ~/ksubtitleripper-0.3.1
./configure
```

If it says "Good - your configure finished" then all is well.  If it said anything else, you probably need to install some development library or other to supply a dependency of KSubtitleRipper.  You can usually figure out what this is by googling the last or next-to-last error message.

Assuming everything worked, proceed:

```
make
sudo make install
```

7) Once it's done compiling, the program's ready to be used.  Note that "make install" doesn't automatically add the binary to your programs menu.  The program's executable file is /usr/local/kde/bin/ksubtitleripper.  

It should be working from this point, but if it doesn't, you're on your own.  For what it's worth, it worked for me - I successfully ripped the subtitles to a movie today using a custom-compiled KSubtitleRipper with the two patches described above.  I don't think much of the UI; it's a pain in the butt, in fact.  But it works.

I've submitted two bugs Launchpad asking that they pass these two patches upstream to whoever maintains this package for the debian archives, so eventually it should Just Work.  But I have no idea how long it'll take to get the things integrated.

---

