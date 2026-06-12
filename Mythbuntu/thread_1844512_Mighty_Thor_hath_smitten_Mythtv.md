---
title: "Mighty Thor hath smitten Mythtv"
date: 2011-09-15
forum: Mythbuntu
---

### Post by klc5555 on 2011-09-15
Just a heads up for those who like to watch DVDs in their Mythtv HTPCs hooked to their wide-screen TVs. Paramount appears to have begun using a new copy protection scheme with the release of the new Thor DVD that seems to render the DVD essentially unplayable in Linux.

In addition to the 99 bogus titles technique used by Disney/Sony for years, the new Paramount DVDs appear to interact with libdvdnav and/or libdvdcss so that Xine or mplayer believe the disc to be corrupt, and vlc will simply segfault. The Linux versions of Handbrake and HandbrakeCLI will also segfault on these discs.

The current Windows version of VLC also apparently crashes on these discs, though oddly enough not the Windows version of HandBrake. If one uses a DVD translation-layer utility like AnyDVD (which has been freshly patched in the last week or so specifically with Thor in mind) one can then successfully access the correct title on the disc with normal Windows players, or with other software like the Windows version of HandBrake. 

But these DVDs appear to be completely unplayable directly in Linux/Mythtv, unless one hooks a standalone DVD player into a TV tuner feed (or directly to their tv screen). 

The only lengthy discussion of these Paramount discs I'm aware of is on the Windows forum pertaining to AnyDVD here: [http://forum.slysoft.com/showthread.php?t=49481](http://forum.slysoft.com/showthread.php?t=49481)

---

### Post by nickrout on 2011-09-15
have you tried makemkv?

---

### Post by klc5555 on 2011-09-15
Haven't tried it yet. I'll compile and give it a go at the next convenient opportunity. I'm not too terribly hopeful about the Linux version, whose version numbering would appear to indicate that it's some two years old. And if the Linux version relies on libdvdnav and libdvdcss2, then it would be expected to experience difficulties similar to the other applications mentioned.

On the other hand, the makemkv forum reports some success with the Paramount Blu-ray of Thor, but posters by-and-large do not indicate which OS and app version is in use. I would expect that it's the Windows version.

---

### Post by nickrout on 2011-09-15
> **klc5555 said:**
> Haven't tried it yet. I'll compile and give it a go at the next convenient opportunity. I'm not too terribly hopeful about the Linux version, whose version numbering would appear to indicate that it's some two years old. And if the Linux version relies on libdvdnav and libdvdcss2, then it would be expected to experience difficulties similar to the other applications mentioned.

On the other hand, the makemkv forum reports some success with the Paramount Blu-ray of Thor, but posters by-and-large do not indicate which OS and app version is in use. I would expect that it's the Windows version.

the version numbering of the current linux version is the same version as for the current windows version - 1.6.14.

As far as I can tell makemkvcon (which does the work) does not depend on libdvdnav or libdvdcss2.:

```
nick@nick-VirtualBox:~$ ldd /usr/bin/makemkvcon 
	linux-gate.so.1 =>  (0x00322000)
	libmakemkv.so.1 => /usr/lib/libmakemkv.so.1 (0x00400000)
	libdriveio.so.0 => /usr/lib/libdriveio.so.0 (0x00e85000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00a65000)
	libc.so.6 => /lib/libc.so.6 (0x00cc2000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00738000)
	librt.so.1 => /lib/librt.so.1 (0x0070c000)
	libcrypto.so.0.9.8 => /lib/libcrypto.so.0.9.8 (0x00110000)
	libz.so.1 => /lib/libz.so.1 (0x00b6f000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x002d3000)
	/lib/ld-linux.so.2 (0x00c92000)
	libm.so.6 => /lib/libm.so.6 (0x0038d000)
	libdl.so.2 => /lib/libdl.so.2 (0x004ac000)

```

It just appears to rely on standard linux libraries, except for libmakemkv.so.1. But libmakemkv just seems to rely on standard libraries.

```
nick@nick-VirtualBox:~$ ldd /usr/lib/libmakemkv.so.1
	linux-gate.so.1 =>  (0x00cca000)
	libc.so.6 => /lib/libc.so.6 (0x00e80000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00764000)
	libcrypto.so.0.9.8 => /lib/libcrypto.so.0.9.8 (0x00176000)
	libz.so.1 => /lib/libz.so.1 (0x0086f000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00ce6000)
	/lib/ld-linux.so.2 (0x00a05000)
	libm.so.6 => /lib/libm.so.6 (0x002c5000)
	libdl.so.2 => /lib/libdl.so.2 (0x002eb000)

```

So your pessimism may be misplaced :)

PS I hate those little silver disks. Teenagers leave them on the floor, the dog sits on them and the cat plays with them. Even if they are in the cover, it can never be found. Rip them to hard drive and put the originals at the back of the cupboard. Some windows DVD ripping software works under wine.

---

### Post by klc5555 on 2011-09-16
> **nickrout said:**
> 

PS I hate those little silver disks. Teenagers leave them on the floor, the dog sits on them and the cat plays with them. Even if they are in the cover, it can never be found. Rip them to hard drive and put the originals at the back of the cupboard. Some windows DVD ripping software works under wine.

I also find the physical disks obnoxious, and tend to play everything from files. So I will give makemkv a go next time, since everything else Linux seems to segfault with these Paramount discs.

The Windows version of HandBrake has no difficulty with the actual ripping of the DVD in question (I don't know at the moment whether Win HandBrake runs in Wine). But WinHandBrake can't identify the correct title of the 99 titles it finds. In the absence of a useable version of VLC for these discs, a translation utility like the recently-patched AnyDVD is useful, because it suppresses all titles from the view of HandBrake except the correct title.

But the Windows version of HandBrake is agonizingly slow (generally processes at under 3 frames per second), and the kids are not necessarily understanding of why they have to wait 18-26 hours to watch their new movie. :)

The main point is that Mythtv users who stumble across one of these new Paramount discs in the near future can expect to have an unpleasant time of it. Unless they have configured their setups to pipe a standalone DVD player through a TV tuner card, whereupon these movies would be post-processed like any other recorded TV stream in Myth.

---

### Post by rickyrockrat on 2011-09-16
I tried the latest VLC 1.1.11, compiled from source, and it segfaults.

makemkvcon/makemkv does *not* work on this movie (it sorta does - see below). I'm using the latest version. It can't figure out which title is the real one and wants to rip all 99 of them.  It will start the rip, but always dies just before the end, and the frustrating thing is that it does not leave the partial file, which does play (don't know if it is the right order or not).  You can use ddrescue on it, and it works without errors.  So I have a backup of the iso - but still unplayable.


I left it run over night on all of the titles, and it hangs up somewhere along the line.  It gives me cryptic:

Debug log started at Fri Sep 16 06:52:32 2011 , written by MakeMKV v1.6.14 linux(x64-release)
Using 524544KB for read cache.
001005:0000 MakeMKV v1.6.14 linux(x64-release) started
001004:0000 Debug logging enabled, log will be saved as /home/doug/MakeMKV_log.txt
005072:0000 Backing up disc into folder "temp"
001003:0020 DEBUG: Code 0 at jt/(OKew-9h$uj:29399680
001003:0020 DEBUG: Code 0 at ~|GA,EVLe|dVky`9<a,U:121274101
001003:0020 DEBUG: Code 233 at hqPmEnZnfSHRG3W18/Bd1/DE:0
005069:0080 Backup failed
005080:0204 Backup failed.
Application exited at Fri Sep 16 06:52:47 2011

Further inspection of the titles that were ripped (not sure why they didn't get erased), title 22 looks like the whole movie. I just don't know if it is out of order (like can happen with Disuckney movies).  So makemkv looks like it sorta works with these movies.  It rips the previews as well.  I'll let you know if the movie plays OK.

I used to be dead set against pirating movies, but not anymore. When the studios make it so you can't play your own movies so they can get filthy rich, you either download it or don't watch it.  Perhaps not watching it is a better idea, since most of what comes out of hollywood is absolute trash anyway.

I'm trying handbrake on Linux on this, and you are right it is very slow (says 14H for 26H of movie).  Hopefully it does the job. I'll report back on it.  I didn't detect any titles, but it did figure out the movie size, and it's doing something. Hopefully it's the right something. - apparently not.

Curious. If I rip directly from the DVD, it just stops with no DVD activity for a long time at about 70M. If I rip from the iso, it thinks it has 26 hours of video, but stops at about 900M (~1 hour), and the resulting video is not decrypted using mp4. 

I tried DVDFab, but it does not decrypt the movie, however this was on the iso. I'm still trying to figure out how to get my DVD recognized by DVDFab..here it is:

```
sudo mkdir /media/cdrom0
```
```
echo "/dev/sr0   /media/cdrom0   udf,iso9660 user,noauto,exec   0 0" |sudo tee -a /etc/fstab
```
```
cd ~/.wine/dosdevices
ln -s /media/cdrom0 e:
```
```
mount /media/cdrom
```
run DVDFab.  It turns out that DVDFab will only decrypt if it is run on the DVD, and it has just occured to me that because the only way to back up your movies is to decrypt them - then all movies get stored as unencrypted.

DVDFab also has a 2-3 second lip sync problem but the makemkv does not.  So for this movie, I guess makemkv wins on Linux.

---

### Post by klc5555 on 2011-09-16
> **rickyrockrat said:**
> I tried the latest VLC 1.1.11, compiled from source, and it segfaults.

makemkvcon/makemkv does *not* work on this movie. I'm using the latest version. ...

I'm trying handbrake on Linux on this, and you are right it is very slow.  Hopefully it does the job. I'll report back on it.  I didn't detect any titles, but it did figure out the movie size, and it's doing something. Hopefully it's the right something.

You were able to get the _Linux_ version of HandBrake to not segfault on this movie? I wasn't able to do this with 0.9.4 (or 0.9.3 --I couldn't immediately try 0.9.5 because of dependency issues).

The Windows version of HandBrake 0.9.4 was what I had success with, but on its own it wanted to process the longest title (title 1) rather than the correct title, which appears to vary from batch to batch and region to region (On mine it was way down at title 24 of the 99) In lieu of a usable VLC, some utility has to establish the correct title.

But you're right, an awful lot of work just to be able to play a pretty inferior movie on your Myth home theater. I think I will avoid buying further Paramount discs until their playing situation in Linux is somewhat less problematical.

---

### Post by rickyrockrat on 2011-09-16
Paramount? Care about Linux users? Heck we have a hard enough time getting hardware vendors paying attention, much less these bozos.  They never do learn, though, and there's lots of people that just say the heck with it - just download the movie - it's free and it's easier.

We need to hit them where it hurts - revoke the 1999 legislation (in the US) that their lobbyists put there in the first place.

> You were able to get the _Linux_ version of HandBrake to not segfault on this movie?
Yes. its 0.9.5. Maybe some process segfaulted, but the GUI didn't.

It's title 24, and I used makemkv to extract it, but what a PITA.

---

### Post by sixtyfive on 2011-09-16
They have added two hidden files in the VIDEO_TS directory. One of these files has the unicode name "\001v\001i\001d\001e\001o\001_\001t\001s\001.\001i\001f\001o", or "video_ts.ifo" except with a binary "1" (instead of "0") as the MSB of each unicode character.

libdvdnav processes unicode by (incorrectly) stripping off the MSB, leaving "video_ts.ifo". This causes problems because there are two versions of "VIDEO_TS.IFO" and the second hidden/unicode one points to bogus data. Unfortunately libdvdnav uses the second one and since it has the wrong signature you get the error message.

I replaced the function Unicodedecode() in dvd_udf.c from the libdvdnav/libdvdread library in HandBrake and it seems to fix it. Still having problems playing back with "xine". They also seem to be doing something interesting with the VM commands.

jim

static int
Unicodedecode(uint8_t *data, int len, char *target)
{
  len--;
  data++;
  if (data[-1] == 8 )
    memcpy(target, data, len);
  else if (data[-1] == 16) {
    int i;

    for (i = 0; i < len; i++) {
      if (data[i*2] == 0)
        target[i] = data[i*2+1];
      else
        target[i] = 0;
    }
  }
  target[len] = '\0';

  return 0;
}

---

### Post by rickyrockrat on 2011-09-16
You Stinkin' ROCK, Jim.

This fixes VLC from segfaulting and it plays the movie.  I've attached a patch.  You want me to file a bug report or do you want to?  I'll be glad to give you all the credit.

Thanks, Man!!

[http://ubuntuforums.org/attachment.php?attachmentid=202305&stc=1&d=1316203842](http://ubuntuforums.org/attachment.php?attachmentid=202305&stc=1&d=1316203842)[http://ubuntuforums.org/attachment.php?attachmentid=202305&stc=1&d=1316203842]("http://ubuntuforums.org/attachment.php?attachmentid=202305&stc=1&d=1316203842")

Just FYI, this fix is for libdvdread-4.1.3, source can be found here:
[http://www.mplayerhq.hu/MPlayer/releases/dvdnav/libdvdread-4.1.3.tar.bz2]("http://www.mplayerhq.hu/MPlayer/releases/dvdnav/libdvdread-4.1.3.tar.bz2")

This also fixed Mplayer, dvdbackup, and anybody else that uses libdvdread. Nice work.

---

### Post by sixtyfive on 2011-09-16
Go ahead and report the bug. Just exactly who are you reporting it to? Everyone seems to have their own version of libdvdnav/libdvdread or patches to a known release. The MPlayer guys haven't released an update in three years.

jim

---

### Post by klc5555 on 2011-09-16
> **sixtyfive said:**
> They have added two hidden files in the VIDEO_TS directory. One of these files has the unicode name "\001v\001i\001d\001e\001o\001_\001t\001s\001.\001i\001f\001o", or "video_ts.ifo" except with a binary "1" (instead of "0") as the MSB of each unicode character.

libdvdnav processes unicode by (incorrectly) stripping off the MSB, leaving "video_ts.ifo". This causes problems because there are two versions of "VIDEO_TS.IFO" and the second hidden/unicode one points to bogus data. Unfortunately libdvdnav uses the second one and since it has the wrong signature you get the error message.

I replaced the function Unicodedecode() in dvd_udf.c from the libdvdnav/libdvdread library in HandBrake and it seems to fix it. Still having problems playing back with "xine". They also seem to be doing something interesting with the VM commands.

jim

static int
Unicodedecode(uint8_t *data, int len, char *target)
{
  len--;
  data++;
  if (data[-1] == 8 )
    memcpy(target, data, len);
  else if (data[-1] == 16) {
    int i;

    for (i = 0; i < len; i++) {
      if (data[i*2] == 0)
        target[i] = data[i*2+1];
      else
        target[i] = 0;
    }
  }
  target[len] = '\0';

  return 0;
}

Well done!

A lot of folks in the Linux community owe you one!

Many thanks.

---

### Post by rickyrockrat on 2011-09-17
Jim,
I'm filing a bug with both Debian and Ubuntu, and it should flow from there ever where else.

Not sure why these packages have been abandoned.

[https://bugs.launchpad.net/ubuntu/+source/libdvdread/+bug/852345](https://bugs.launchpad.net/ubuntu/+source/libdvdread/+bug/852345)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=641881](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=641881)

---

### Post by rickcorp on 2011-09-17
Do you have to recompile the library? Not super up on these types of mods.. 

Thanks
Rick

---

### Post by rickyrockrat on 2011-09-17
Yes, but it's simple.
download that tarball, and the patch then 
```
sudo apt-get install build-essential
tar -xjf libdvdread-4.1.3.tar.bz2
cd libdvdread-4.1.3
patch -p1 <libdvdread-4.1.3.MSB-fix.patch.txt
./configure
make
sudo make install
```

---

### Post by cowb0y on 2011-09-17
Big thanks for the patch, which solves the issue. Once again, open source triumphs over corporate greed.  BTW, I'm watching Thor on DVD from Netflix, so am paying (indirectly) to be screwed with by the studios. :popcorn:

---

### Post by BicyclerBoy on 2011-09-17
Thanks from here too.

The HandBrake project folks are very receptive of such things..
That project is easily the most DVD capable of any Linux program.

The HandBrake nightly updates could have this included in a few days..

---

### Post by nickrout on 2011-09-18
> **BicyclerBoy said:**
> Thanks from here too.

The HandBrake project folks are very receptive of such things..
That project is easily the most DVD capable of any Linux program.

The HandBrake nightly updates could have this included in a few days..


Have you submitted it to them?

How thoroughly has the patch been tested?

---

### Post by shawnggraham on 2011-09-19
Ok so...from a typical Ubuntu users viewpoint..where are we on this cause I got to tell you I OWN 4 COPYS OF THIS DISK (because I own a video store) and all my machines are Ubuntu Linux so I cant watch it! Report a bug? Tell me where to report it if that will get this moving. I use this OS because its reliable. The OSC needs this not only reported...but out and working in record time. If you get this out your the shining star for all the distros to watch.. Paramount and anyone else that does this sort of thing needs to understand that breaking legit purchases will not be tolerated and that their RND costs for this sort of thing are a total waist of time for them and us.  Lets get this patch applied and pushed to LTS and beyond. We need this in a package not a patch to source. Lets send a message to these people that they are straight up just wasting money and time with this sort of crap. Start making good movies and stop wasting time on this sort of thing.  I have several ubuntu boxes and a couple of virtual enviroments to test things in..tell me what version to install and send me a package..ill test whatever you got.

---

### Post by nickrout on 2011-09-19
> **shawnggraham said:**
> Ok so...from a typical Ubuntu users viewpoint..where are we on this cause I got to tell you I OWN 4 COPYS OF THIS DISK (because I own a video store) and all my machines are Ubuntu Linux so I cant watch it! Report a bug? Tell me where to report it if that will get this moving. I use this OS because its reliable. The OSC needs this not only reported...but out and working in record time. If you get this out your the shining star for all the distros to watch.. Paramount and anyone else that does this sort of thing needs to understand that breaking legit purchases will not be tolerated and that their RND costs for this sort of thing are a total waist of time for them and us.  Lets get this patch applied and pushed to LTS and beyond. We need this in a package not a patch to source. Lets send a message to these people that they are straight up just wasting money and time with this sort of crap. Start making good movies and stop wasting time on this sort of thing.  I have several ubuntu boxes and a couple of virtual enviroments to test things in..tell me what version to install and send me a package..ill test whatever you got.

Although I agree with your sentiments about the short sightedness of Paramount's philosophy and business methods, your post reads a little like the rant of someone who likes to use a free$ and reliable operating system but who is not prepared to give anything back.

If you are just wanting to get your own systems fixed then follow the instructions already given, they are simple enough.

If you want to contribute and be part of the community, then:

1. learn how to create a ppa; and

2. learn how to put a patched version of an existing package on there; 

3. profit. (not actually, that's part of the ethos :)   )

Frankly though this will just encourage linuxistas to download a file and use that. There are versions up to 1080p out there.

---

### Post by BicyclerBoy on 2011-09-19
Sorry I haven't tried the patch yet..
Don't have any affected DVDs.
Might rent a couple to try.
MythTV might be interested. MarkK did a lot of work to improve DVD playback.

Someone is really on to it..
[http://lists.mplayerhq.hu/pipermail/dvdnav-discuss/2011-September/001435.html](http://lists.mplayerhq.hu/pipermail/dvdnav-discuss/2011-September/001435.html)

@shawng
Owning DVD & Bluray discs does not give or guarantee the right to be able to play them on any equipment.

There is no such guarantee that your compliant DVD/BD player will work with new discs.
Your compliant BD player can be permanent shutdown by a BD disc.

Only windows & OSX are mpeg-la compliant PC OS licensed for DVD/BD playback.

---

### Post by Scott Belden on 2011-09-19
Could you give me a hint were that text goes, so I can watch this dumb movie I rented. ouch. Thanks, Scott

---

### Post by nickrout on 2011-09-19
> **Scott Belden said:**
> Could you give me a hint were that text goes, so I can watch this dumb movie I rented. ouch. Thanks, Scott

Download the source for libdvdread.

download the patch

untar the source and cd into the libdvdread_4.xxx/ directory.

run ```
patch -p1 < ../patchfile.txtx (or whetever you called it.
```

run ```
./configure
make
sudo make install
```

---

### Post by BicyclerBoy on 2011-09-20
I think it is *possibly* not quite so simple..
It depends on where the media apps come from & how.

Std ubuntu packaged applications are built using the shared libraries. run-time shared libs.

Media apps from external ppa are very likely using self-contained lib packages i.e. compile time linked libraries.

If you build your media app from source then almost 100% likely to be built from private patched library source. When you build the app you do not install the component libraries.

i.e MythTV in std ubuntu has a dependency on libdvdnav
MythTV from 3rd party ppa does not.
MythTV source code contains a private source copy of libdvdnav/read.

You can get libdvdnav code from mplayer.hu via svn.
Need to configure as shared library before make. But this not very helpful.

If you are using an updated media player that is outside of standard ubuntu packages, you need to download the source code & patch & build.

---

### Post by andyd273 on 2011-09-23
> **rickyrockrat said:**
> Yes, but it's simple.
download that tarball, and the patch then 
```
sudo apt-get install build-essential
tar -xjf libdvdread-4.1.3.tar.bz2
cd libdvdread-4.1.3
patch -p1 <libdvdread-4.1.3.MSB-fix.patch.txt
./configure
make
sudo make install
```

Curious, do you think this process will work on OSX?
I like to back up my DVDs in case the child gets ahold of them.
I get this error when I try it...
```
cd obj && gcc -dynamiclib -Wl,-single_module -Wl,-read_only_relocs,suppress  -ldl -Wl,-soname=libdvdread.so.4 -o libdvdread.so dvd_input.so dvd_reader.so dvd_udf.so ifo_print.so ifo_read.so md5.so nav_print.so nav_read.so bitreader.so
ld: unknown option: -soname=libdvdread.so.4
collect2: ld returned 1 exit status
make: *** [libdvdread.so] Error 1
```


The MakeMKV method did work, but talk about a messy process. It would be nice if it was streamlined.

---

### Post by Gryvine on 2011-09-23
thank you for providing the fix!

---

### Post by bvess on 2011-09-24
I tried this but get the following error at sudo make install

"install -d /usr/local/bin
install: cannot create directory `/usr/local/bin': File exists
make: *** [install-dvdread-config] Error 1"

Thanks

---

### Post by TuxHerder on 2011-09-26
There is a ppa (for natty andoneiric) for this listed in the comments at [https://bugs.launchpad.net/ubuntu/+source/libdvdread/+bug/852345](https://bugs.launchpad.net/ubuntu/+source/libdvdread/+bug/852345)

ppa page: [https://launchpad.net/~bryce/+archive/lp852345]("https://launchpad.net/%7Ebryce/+archive/lp852345")

I haven't tried this (and it looks like a fix is/will be released soon through the normal channels), but if you're desperate. . .

---

### Post by mikedoty on 2011-09-28
I'd like to thank sixtyfive/Jim and rockyrockrat for the time and helpful instructions.  This resolved the issue perfectly for me, although I remain skeptical that this Thor will prove worth the hassle.  Future Paramount movies, maybe!  ;)

---

### Post by addyp on 2011-09-28
> **rickyrockrat said:**
> Yes, but it's simple.
download that tarball, and the patch then 
```
sudo apt-get install build-essential
tar -xjf libdvdread-4.1.3.tar.bz2
cd libdvdread-4.1.3
patch -p1 <libdvdread-4.1.3.MSB-fix.patch.txt
./configure
make
sudo make install
```



new to Ubuntu. Tried to figure this out. got to "patch" then this happened.

[B]patching file src/dvd_udf.c
Reversed (or previously applied) patch detected!  Assume -R? [n] 
Apply anyway? [n] y
Hunk #1 FAILED at 331.
1 out of 1 hunk FAILED -- saving rejects to file src/dvd_udf.c.rej
[/B]
I said yes. But it says it fails. Does this mean the patch is already applied? If so, I still can't view the video in VLC or Movie Player. It's still scrambled. If not, where did I go wrong Linux pros? Anything else I can do? Thanks. Any help is appreciated. I've been at this for a couple of hours today and last night. So frustrated.

I sux at Linux but I still love it!

---

### Post by jrhughes on 2011-09-29
[FONT=Verdana][SIZE=2]Hey thanks for the patch. I never actually got it to work so I ending up reinstalling libdvdread4 in synaptic and then using [/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2]```
sudo /usr/share/doc/libdvdread4/install-css.sh
```[/SIZE][/FONT][FONT=Verdana][SIZE=2]
to reinstall libdvdcss. Then just for the heck of it, I tried Thor again and it is now working! I looked at lsdvd and it still reports no VTS_TMAPT but the process continues. So I think that the code may have been updated in [/SIZE][/FONT][FONT=Verdana][SIZE=2]libdvdread4[/SIZE][/FONT][FONT=Verdana][SIZE=2]. In any case a simple reinstall maybe worth a shot before patching. [/SIZE][/FONT]

---

### Post by rickyrockrat on 2011-09-29
The bug report has been accepted and is now in debian and ubuntu repos.  I can't tell you which ones, but it should filter back to LTS soon.

[https://bugs.launchpad.net/bugs/852345](https://bugs.launchpad.net/bugs/852345)

It is in libdvdread - 4.1.3-10ubuntu4, is only available for natty here:
[https://launchpad.net/~bryce/+archive/lp852345](https://launchpad.net/~bryce/+archive/lp852345)

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=641881](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=641881)
It is in libdvdread-dbg_4.1.4-1219-4 on debian  (according to the bug report)

mplayer discussion (not sure anything has happened yet)
[http://lists.mplayerhq.hu/pipermail/dvdnav-discuss/2011-September/001435.html](http://lists.mplayerhq.hu/pipermail/dvdnav-discuss/2011-September/001435.html)

---

### Post by rickyrockrat on 2011-09-29
> **addyp said:**
> new to Ubuntu. Tried to figure this out. got to "patch" then this happened.

[B]patching file src/dvd_udf.c
Reversed (or previously applied) patch detected!  Assume -R? [n] 
Apply anyway? [n] y
Hunk #1 FAILED at 331.
1 out of 1 hunk FAILED -- saving rejects to file src/dvd_udf.c.rej
[/B]
I said yes. But it says it fails. Does this mean the patch is already applied?

No, patch wasn't applied, but you can look in src/dvd_udf.c, then search for 'Unicode'.  It's possible you somehow got a patched version of libdvdread4.

if you want, you can hand edit it. Just delete the current function and put this in it's place:
(note: I've changed it slightly, but it's functionally the same)
```

static int Unicodedecode( uint8_t *data, int len, char *target )
{
  len--;

  if (data[0] == 8 )
      memcpy(target, &data[1], len);
  else if (data[0] == 16) {
    int i;
    data++;
    for (i = 0; i < len; i++) {
      if (data[i*2] == 0)
        target[i] = data[i*2+1];
      else
        target[i] = 0;
    }
  }
  target[len] = '\0';
return 0;
}

```

---

### Post by rickyrockrat on 2011-09-29
@nickrout

You forgot to configure with your instructions. Please try not to add to the confusion with incomplete/incorrect instructions.

Since it is such a simple change, it's been tested throughly, and with many different developers.

---

### Post by nickrout on 2011-09-29
> **rickyrockrat said:**
> @nickrout

You forgot to configure with your instructions. Please try not to add to the confusion with incomplete/incorrect instructions.

Since it is such a simple change, it's been tested throughly, and with many different developers.

fixed to reduce confusion. Thanks for pointing out my error!

---

### Post by gary987 on 2011-10-02
If you're a handbrake user, the latest subversion worked fine for me, selecting track 10, or if not try track 24.

I compiled it in Gentoo, but is should work the same in ubuntu

Cheers, 

Gary

---

### Post by pakraticus on 2011-10-03
There is a flaw in the presented patch.
One broken utf decoder is being replaced with another broken utf decoder.
'\x01v\x01i'... is VALID utf-16_be

Per [http://www.osta.org/specs/pdf/udf260.pdf](http://www.osta.org/specs/pdf/udf260.pdf) section 2.1.1 and 

NOTE: This encoding causes characters written with a CompressionID of 16 to 
be effectively written in big endian format. 

Linux kernel gets this right, try mounting the DVD image with the unhide options provides the correct filenames

&#374;&#361;&#356;&#357;&#367;&#351;&#372;&#371;&#302;&#354;&#373;&#368;
&#374;&#361;&#356;&#357;&#367;&#351;&#372;&#371;&#302;&#361;&#358;&#367;

Section 6.7 of the above PDF provides two decode algorhythms.

---

### Post by Keith Hedger on 2011-10-04
sixtyfive! what can I say thanks!!!! just installed dvdread from source and applied your patch and presto Thor works! been going round in circles trying to fix this ( oddly a really  old install of debian that I use as a rescue system has a version of mplayer that works with this DVD, weird huh! ).
By the way I'm using slackware64

---

### Post by malcom2073 on 2011-10-08
Downloaded libdvdread source, patched, compiled and installed, with no luck. My VLC (And any other app using libdvdread) still crashes on trying to read Thor dvd. Anyone else have it still crashing?

---

### Post by Keith Hedger on 2011-10-10
> **malcom2073 said:**
> Downloaded libdvdread source, patched, compiled and installed, with no luck. My VLC (And any other app using libdvdread) still crashes on trying to read Thor dvd. Anyone else have it still crashing?

Are you sure that these progs are using libdvdread and not their internal versions? mplayer for instance has to be told to use the external version explicitly, otherwise it defaults to using it's own internal version, according to ldd my version of vlc isn't linked against dvdread so I asume it uses its internal version and so it crashes when trying to load THOR where as mplayer which I compiled to use the external library plays THOR fine.

---

### Post by rickyrockrat on 2011-10-11
Gents,
It's true Mplayer uses it's own libdvdread. I've a patch attached for it along with a patch that auto-sets -dvd-device when it sees VIDEO_TS in the Mplayer file browser. This file has two different patches, for two different mplayer.svn versions. If you don't know how to grab a specific version from svn, please google it.
[http://ubuntuforums.org/attachment.php?attachmentid=204030&stc=1&d=1318359039]("http://ubuntuforums.org/attachment.php?attachmentid=204030&stc=1&d=1318359039")

Now for the good news, the original patch has been applied against Natty, but they need testers, and I've already returned the Thor movie. Can someone please test for us?

[https://bugs.launchpad.net/ubuntu/+source/libdvdread/+bug/852345]("https://bugs.launchpad.net/ubuntu/+source/libdvdread/+bug/852345")

How to use -proposed:
[https://wiki.ubuntu.com/Testing/EnableProposed]("https://wiki.ubuntu.com/Testing/EnableProposed")

Thanks!

---

### Post by rickyrockrat on 2011-10-11
oops. I hit submit twice - too much coffee!!

---

### Post by jacrider on 2011-10-16
> **gary987 said:**
> If you're a handbrake user, the latest subversion worked fine for me, selecting track 10, or if not try track 24.

I compiled it in Gentoo, but is should work the same in ubuntu



Any chance you have any advice on how to do this with 11.10?  Would love to get my Thor disk onto my network.

Thanks.

---

### Post by JohnAStebbins on 2011-10-17
> **jacrider said:**
> Any chance you have any advice on how to do this with 11.10?  Would love to get my Thor disk onto my network.

Thanks.

[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

The HandBrake nightly builds have an 11.10 version.

---

### Post by jacrider on 2011-10-17
> **JohnAStebbins said:**
> [https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

The HandBrake nightly builds have an 11.10 version.

Perfect!  I didn't have the snapshots in my repositories.

Thor is now encoding.

---

### Post by AlecJ on 2011-10-21
My mythbox is using 10.04lts how do I patch it, can't find the file I need to patch?

---

### Post by TheMiz on 2011-10-29
So I got Thor to encode with Handbrake after copying the Video_TS folder to my Mac's desktop, then encoding it from there.  I had to use Fairmount to be able to copy the Video_TS folder.  Is there a way to copy an encoded video_TS folder to your hard drive in ubuntu?  Is there a program that acts like Fairmount for the Mac?

---

### Post by nickrout on 2011-10-29
What does fairmount do? Does it decypt and cop or just copy?

---

### Post by TheMiz on 2011-10-29
Fairmount on the Mac just decrypts. It uses VLC and mounts the disc as an unencrypted drive.

It would be nice to know if I could do this in Ubuntu.

---

### Post by Keith Hedger on 2011-10-30
Fairmount is not available for linux but if worse comes to worse why not mount it in osx and share it with your linuxbox, not the best solution but it works as a last resort. I use this script to mount osx when I have no other choice```
#!/bin/bash

PASS=LINUXBOXADMINPASSWORD
PASS2=LOGINPASSWORDFOROSX
echo $PASS | sudo -S mkdir /media/OSX
echo $PASS | sudo -S chown -R keithhedger:keithhedger /media/OSX
echo $PASS2 | sshfs -o password_stdin ***.***.***.***:/ /media/OSX
```
change the ip address and the relevent passwords

---

### Post by Keith Hedger on 2011-11-01
The latest SVN version of mplayer rips thor quite easily

---

### Post by TuxHerder on 2011-11-04
patched libdvdread4 for Ubuntu 11.04 has been made available as update, and it works :)

/still waiting for 10.04

---

### Post by rickyrockrat on 2011-11-27
Here's another patch. It seems after applying the patch, it now will read movies it wouldn't before...and hits a new bug, where it segfaults.

I've fixed this too and submitted bug reports:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=649790]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=649790")

[https://bugs.launchpad.net/ubuntu/+source/libdvdread/+bug/894170]("https://bugs.launchpad.net/ubuntu/+source/libdvdread/+bug/894170")

With this patch, I was able to read Captain America (Title 25) and Cars 2 (title 18).  The kicker, though, is to use a patched version of the libdvdread supplied by mplayer.

I've attached the patch for SVN version 34027 of mplayer, and includes the both patches mentioned in this thread.  If you already have the patched version of libdvdread, then just grab the second patch.

```
diff -ru mplayer.r34027.svn.0/libdvdread4/dvd_udf.c mplayer.r34027.svn/libdvdread4/dvd_udf.c
--- mplayer.r34027.svn.0/libdvdread4/dvd_udf.c  2011-08-29 13:47:44.000000000 -0600
+++ mplayer.r34027.svn/libdvdread4/dvd_udf.c    2011-09-29 10:15:35.000000000 -0600
@@ -328,17 +328,22 @@

 static int Unicodedecode( uint8_t *data, int len, char *target )
 {
-  int p = 1, i = 0;
-
-  if( ( data[ 0 ] == 8 ) || ( data[ 0 ] == 16 ) ) do {
-    if( data[ 0 ] == 16 ) p++;  /* Ignore MSB of unicode16 */
-    if( p < len ) {
-      target[ i++ ] = data[ p++ ];
+  len--;
+  
+  if (data[0] == 8 )
+      memcpy(target, &data[1], len);
+  else if (data[0] == 16) {
+    int i;
+    data++;
+    for (i = 0; i < len; i++) {
+      if (data[i*2] == 0)
+        target[i] = data[i*2+1];
+      else
+        target[i] = 0;
     }
-  } while( p < len );
-
-  target[ i ] = '\0';
-  return 0;
+  }
+  target[len] = '\0';
+return 0;
 }

 static int UDFDescriptor( uint8_t *data, uint16_t *TagID )
```

```
diff -ru mplayer.r34027.svn.0/libdvdread4/ifo_read.c mplayer.r34027.svn/libdvdread4/ifo_read.c
--- mplayer.r34027.svn.0/libdvdread4/ifo_read.c 2011-08-29 13:47:44.000000000 -0600
+++ mplayer.r34027.svn/libdvdread4/ifo_read.c   2011-11-23 16:14:20.000000000 -0700
@@ -1081,7 +1081,11 @@
     ifoFree_TT_SRPT(ifofile);
     return 0;
   }
-
+  if( tt_srpt->nr_of_srpts>info_length/sizeof(title_info_t)){
+    fprintf(stderr,"libdvdread: data mismatch->info_length (%ld)!= nr_of_srpts (%d). Truncating.\n",
+     info_length/sizeof(title_info_t),tt_srpt->nr_of_srpts);
+    tt_srpt->nr_of_srpts=info_length/sizeof(title_info_t);
+  }
   for(i =  0; i < tt_srpt->nr_of_srpts; i++) {
     B2N_16(tt_srpt->title[i].nr_of_ptts);
     B2N_16(tt_srpt->title[i].parental_id);
```
Have I mentioned that I hate all the Bull**** we have to go through just to watch a movie we legally bought or rented!?

---

### Post by sharkcohen on 2011-12-24
Where can I download the source for libdvdread?  The link on the first page of this thread seems to be dead, and I cannot find what I need via google.

Also, will this patch work for ubuntu 10.04?

---

### Post by nickrout on 2011-12-29
> **sharkcohen said:**
> Where can I download the source for libdvdread?  The link on the first page of this thread seems to be dead, and I cannot find what I need via google.

Also, will this patch work for ubuntu 10.04?

apt-get source libdvdread

---

### Post by Keith Hedger on 2011-12-30
> **sharkcohen said:**
> Where can I download the source for libdvdread?  The link on the first page of this thread seems to be dead, and I cannot find what I need via google.

Also, will this patch work for ubuntu 10.04?

Or here:
[http://www.mplayerhq.hu/MPlayer/releases/dvdnav-old/libdvdread-4.1.3.tar.bz2](http://www.mplayerhq.hu/MPlayer/releases/dvdnav-old/libdvdread-4.1.3.tar.bz2)

---

### Post by FreddyAV on 2012-01-06
Hi

I have downloaded the source files from [https://launchpad.net/~bryce/+archive/lp852345/+packages](https://launchpad.net/~bryce/+archive/lp852345/+packages) for libdvdread4 and compiled them on a Kubuntu 10.04.3 LTS machine and made a deb for that. I also tried installing it on an other Ubuntu 10.04.3 LTS machine (sudo dpkg -i filename.deb). It seems to work so far in VLC. XBMC seems to be compiled with its own libdvdread unfortunately.

Anyway, here it is, with absolutly no warranty or any support, my deb for Ubuntu 10.04.3 LTS AMD64 with the libdvdread4 from Oneric.

---

### Post by FreddyAV on 2012-01-07
I have now also succesfully merged the relevant changes into the xbmc from the team-xbmc ppa for 10.04 AMD64. If anyone needs this please let me know. (I should mention that I am a semi-regular visitor to the forum)

---

