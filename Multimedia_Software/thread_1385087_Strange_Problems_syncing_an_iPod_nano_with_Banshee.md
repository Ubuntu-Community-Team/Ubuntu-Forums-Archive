---
title: "Strange Problems syncing an iPod nano with Banshee"
date: 2010-01-19
forum: Multimedia Software
---

### Post by The Foz on 2010-01-19
My girlfriend has a new iPod nano, which I am trying to get working properly with Ubuntu. Currently I am trying to get it to work with Banshee.

Originally, my girlfriend connected it to iTunes running under Windows, and configured it and loaded music, photos and podcasts onto it. Unfortunately for her, the Windows machine had a hardware failure, and there is no other PC running real Windows for her to use. I have some Windows Virtual Machines on my Ubuntu server, but there are known problems passing through the iPod USB connection to a KVM Virtual Machine.

I tried iTunes under Wine (using the PlayOnLinux software to install and configure), but that also doesn't work (also apparently a known problem).

So I am left with getting the iPod working with real native Ubuntu software. I tried Rhythmbox, but that doesn't seem to support writing to an iPod. Then I tried Banshee, which claims to be able to do it all.

Banshee can connect to the iPod, and I can load music and videos onto the iPod, but:
[LIST=1]
[*]Banshee cannot see any of the music already on the iPod (loaded with ITunes),
[*]The iPod cannot see any of the files (music or video, nor any new Playlists) loaded by Banshee. The files are there (I can see them by browsing the iPod device with Nautilus), and they are certainly taking up storage space, but they do not show up when using the iPod directly.
[/LIST]
It is as if there are 2 iPods: the real iPod, and a virtual iPod accessed by Banshee.

I am running Banshee 1.6 Beta 3 (1.5.2), on Jaunty (9.04).

When I first connected the iPod to Banshee it told me that, because the device had been used with a new version of iTunes, the media catalogue would have to be rebuilt, to which I agreed. I am starting to suspect that there are now 2 media catalogues on the iPod, one being used by Banshee, and the other by the iPod iteslf.

Does anyone have any ideas?

---

### Post by nothingspecial on 2010-01-19
If you have a new ipod nano with video then a miracle worker has provided a hack for this. The thread on which it appears is very long and the information you need is spread all over it so I will try and put it succinctly here.

Download the fix from [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=8568698&postcount=32") - it`s the attachment you need.

Then download the latest libgpod and gtkpod along with dependencies and the tools to build them.

```
sudo apt-get remove --purge libgpod4 gtkpod

sudo apt-get build-essential autoconf flex gettext libglib2.0-dev libgtk2.0-dev libglade2-dev libid3tag0-dev libxml-parser-perl pkg-config automake gcc git-core gtk-doc-tools libcurl4-dev libflac-dev libgnomevfs2-dev libhal-dev libvorbis-dev libmp4v2-dev libplist-dev libsqlite3-dev

git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/libgpod

git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/gtkpod
```

Then you need to apply the patch to the libgpod source code
```

tar -xvf NanoG5Fix.tar.gz 
mv itdb_sqlite.c libgpod/src/
mv itdb_sqlite_queries.h libgpod/src/
```

Compile libgpod and gtkpod

```
cd libgpod
./autogen.sh
make
sudo make install

cd ../gtkpod
./autogen.sh
make
sudo make install
```

Then you need to edit a couple of files on the ipod

First you need your ipods firewireid
```

sudo lsusb -v | grep -i Serial
```

This will give you a 16 digit long number, then use it in this file

```

gksudo gedit path_to_your_ipod/iPod_Control/Device/SysInfo
```

You need to make that file look like this

```
ModelNumStr: xC062
FirewireGuid: 0x000A27001EAF5F2C
```

Use the 16 digit number you just got for the 2nd line and the correct model code (1st line) from the list below. The 0x infront of the 16 digits is important.


```

8 Gig (silver) = xC027 (Black) = xC031 (Purple) = xC034 (Green) = xC037 (Blue) = xC040 (Yellow) = xC043 (Orange) = xC046 (Red) = xC049 (Pink) = xC050

16 Gig (silver) = xC060 (Black) = xC062 (Purple) = xC064 (Green) = xC066 (Blue) = xC068 (Yellow) = xC070 (Orange) = xC072 (Red) = xC074 (Pink) = xC075
```

Finaly you need to go to [[COLOR="Magenta"]this[/COLOR]]("http://ihash.marcansoft.com/") website and generate a hashinfo file, then place the file in ```
ipod/iPod_Control/Device/
```

This is not a perfect fix. The songs will not be in alphabetical order album art will not work and a number of other issues. However you will be able to transfer songs and video to your ipod and play them.

The libgpod devs are working on this.

I am guaranteed to have made a mistake in this post so [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1267180") is the original thread to read if something does not work

---

### Post by The Foz on 2010-01-19
Wow!

Thanks for the quick reply, and for what was obviously a lot of effort collating all that information.

I will start working through the instructions and the supporting links, and post my results.

---

### Post by The Foz on 2010-01-20
Hi nothingspecial,

I am having some problems. The 'sudo apt-get ... ' command is failing.

I assume that it should be 'sudo apt-get **install** ... '. However, running this produces the error message that "Package libcurl4-dev has no installation candidate".

Is this available in a PPA somewhere, or should I be using an alternative package such as libcurl4-gnutls-dev or libcurl4-openssl-dev (both of these packages do exist for 9.04)?

---

### Post by nothingspecial on 2010-01-20
Yes of course install should be in there, I told you I`d make mistakes, didn`t think they`d be that basic though :D

This is what I have
```

dpkg --get-selections | grep libcurl4*
libcurl3					install
libcurl3-gnutls					install
libcurl4-gnutls-dev				install

```

I wouldn`t think it would harm installing all 3.

---

### Post by The Foz on 2010-01-22
Some progress, although not as expected. 

I followed the instructions with great care. I had to build libplist from source (clone from the git repository with 
```
git clone git://github.com/JonathanBeck/libplist.git
```
and then follow the instructions to compile and install).

I have the same libcurl libraries as shown in the post above from "nothingspecial".

The iPod is now behaving **slightly differently** than before, in that with Banshee I can see 3 files (3 podcasts out of a total of 20) that are actually on the iPod. I cannot see any of the music that is on the iPod (put there with iTunes), and the iPod still cannot see anything that I copy on with Banshee.

I have retarted my system, and reinstalled Banshee.

What does now seem to work, at least partly, is gtkpod. I have gtkpod 0.99.15GIT. I can see all the music and podcast files on the iPod, and can add new content. I can't see any photos or videos though, and the playlists created in gtkpod are not visible on the iPod (expected). Using gtkpod seems to have stopped Banshee from being able to read the contents of the iPod.

hipo (for managing photo and video content) no longer works. It throws an error on start, and will not run.

Rhythmbox can see the music and podcasts on the iPod (including playlists created with gtkpod) but of course cannot write anything to the iPod.

If anyone else has had more success, I would be pleased to hear about it.

---

