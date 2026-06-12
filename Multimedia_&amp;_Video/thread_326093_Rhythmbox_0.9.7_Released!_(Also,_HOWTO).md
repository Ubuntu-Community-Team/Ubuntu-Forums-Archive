---
title: "Rhythmbox 0.9.7 Released! (Also, HOWTO)"
date: 2006-12-27
forum: Multimedia &amp; Video
---

### Post by PWill on 2006-12-27
Howdy all.
Rhythmbox 0.9.7 was released by GNOME just a few hours ago.
New features include:
* Use gnome-power-manager to inhibit suspend while playing
* Add support for transient metadata 
*** Plugin-ise Internet radio support**
*** Add support for the MagnaTune online store**
*** Add support for playin Last.fm radio streams**
* Even more support for broken podcast feeds
* Display placeholder when no cover art can be found

You can download the source from [http://ftp.gnome.org/pub/GNOME/sources/rhythmbox/0.9/rhythmbox-0.9.7.tar.gz](http://ftp.gnome.org/pub/GNOME/sources/rhythmbox/0.9/rhythmbox-0.9.7.tar.gz)

**STEP 1**
First, run ```
sudo apt-get build-dep rhythmbox
```
If you **do** have an iPod, you need the latest libgpod and python-gpods, which can be found here: [http://www.debian-multimedia.org/pool/main/libg/libgpod/](http://www.debian-multimedia.org/pool/main/libg/libgpod/)
If you **don't** have an iPod, skip to STEP 3[B]


STEP 2[/B]
You will need

* libgpod0_0.4.0-0.3_i386.deb
* libgpod-dev_0.4.0-0.3_i386.deb
* libgpod-common_0.4.0-0.3_all.deb
* python-gpod_0.4.0-0.3_i386.deb


Those should all install fine.

**STEP 3**
Once those are installed, you can install this deb: [http://smoothweb.net/rhythmbox_0.9.7-1_i386.deb](http://smoothweb.net/rhythmbox_0.9.7-1_i386.deb)

You might get a pop-up that says "Older Version Available in Software Repositories" but just ignore that.

NOTE: If you are an idiot like me, and screw up your libdirs when building from source sometimes, you may need to use the --force-overwrite option in dpkg (e.g., # dpkg -i --force-overwrite /path/to/rb.deb)

Have fun!

UPDATE: DEB is back up at [http://www.smoothweb.net/rhythmbox_0.9.7-1_i386.deb](http://www.smoothweb.net/rhythmbox_0.9.7-1_i386.deb)

---

### Post by Mateo on 2006-12-27
on synaptic yet?

---

### Post by Mateo on 2006-12-27
tried compiling, but missing 'gnome-vfs-2.0'.  couldn't find it through apt-get.

---

### Post by homerhomer on 2006-12-27
Here is the non-ipod one made with checkinstall
it's pretty ugly but works pretty well on my Edgy
[http://www.megaupload.com/?d=N35L2MA3](http://www.megaupload.com/?d=N35L2MA3)

---

### Post by Mateo on 2006-12-31
thank you so much homerhomer, i was going insane trying to install all of the dev dependencies.  I seriously installed at least a dozen of them.  but ran into a wall when the config said I didn't have gstreamer 0.8 an 1.0, while synaptic said otherwise.  but your DEB did the trick. kudos.

---

### Post by kikuman on 2007-01-08
Connection times out for smoothweb.net :(

---

### Post by PWill on 2007-01-08
Yeah, sorry I moved my server. I will put up a new .deb soon...

---

### Post by kikuman on 2007-01-08
Thanks a lot!  I realy wana try 0.9.7 cos it's has last.fm stream playback now :>

---

### Post by bofphile on 2007-01-09
The links to the deb packages don't work anymore. Could someone provide new links ?
Thanks.

---

### Post by Qtea on 2007-01-13
> **Mateo said:**
> tried compiling, but missing 'gnome-vfs-2.0'.  couldn't find it through apt-get.I found it (sudo apt-get install libgnome-vfs-common libgnome-vfs0) but still got blamed for having a version too old (2.0 instead of 2.7.4). No Last.fm streams this far :(.

---

### Post by PWill on 2007-01-13
> **Qtea said:**
> I found it (sudo apt-get install libgnome-vfs-common libgnome-vfs0) but still got blamed for having a version too old (2.0 instead of 2.7.4). No Last.fm streams this far :(.Did you run ```
sudo apt-get build-dep rhythmbox
```?

---

### Post by Qtea on 2007-01-19
> **xiamcitizen said:**
> Did you run ```
sudo apt-get build-dep rhythmbox
```?No, I actually did not, because I have no iPod and I was told to go straight to point 3. I now tried, but got an error message saying that dependencies can not be fulfilled.

I'll attach my error code I got when running ./configure:
```
checking for RB_CLIENT... configure: error: Package requirements (gnome-vfs-2.0 >= 2.7.4) were not met:

No package 'gnome-vfs-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables RB_CLIENT_CFLAGS
and RB_CLIENT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

---

### Post by PWill on 2007-01-19
Whoops! Sorry, I added the "sudo apt-get build-dep rhythmbox" to the wrong section.
Hm...
Can you post the error code you got when running apt-get build-dep rhythmbox?

---

### Post by Qtea on 2007-01-19
> **xiamcitizen said:**
> Can you post the error code you got when running apt-get build-dep rhythmbox?Sure, but it only comes in my native language.

```
tea@veini:~$ sudo apt-get build-dep rhythmbox
Luetaan pakettiluetteloita... Valmis
Muodostetaan riippuvuussuhteiden puu... Valmis
E: Paketointiriippuvuuksia paketille rhythmbox ei voi tyydyttää.
```

It only says that the dependencies cannot be met, nothing else.

---

### Post by Skerit on 2007-01-19
Does this mean the rhythmbox project page is, kinda, useless? Since it's latest news post is about 0.9.6 ...

---

### Post by wildkarde on 2007-01-19
> **Skerit said:**
> Does this mean the rhythmbox project page is, kinda, useless? Since it's latest news post is about 0.9.6 ...

Seems that way... [http://ftp.gnome.org/pub/GNOME/sources/rhythmbox/0.9/]("http://ftp.gnome.org/pub/GNOME/sources/rhythmbox/0.9/") shows the release...

---

### Post by wildkarde on 2007-01-19
hmm

```
$rhythmbox
/usr/local/lib/rhythmbox/plugins/artdisplay/__init__.py:139: Warning: Missing artwork icon not found: pixbuf_new_from_file_at_size() argument 1 must be string, not None
  warn ("Missing artwork icon not found: %s" % e, Warning)
```

Any ideas anyone??

---

### Post by PWill on 2007-01-20
Does Rhythmbox still launch after that?
And if so, does it still show the album art when you play songs?

---

### Post by wildkarde on 2007-01-20
> **xiamcitizen said:**
> Does Rhythmbox still launch after that?
And if so, does it still show the album art when you play songs?

No.  Rhythmbox does not launch.  I tried both the deb and also tried to compile.  Failed to launch both times.  I installed the dependencies as well.

---

### Post by klilja on 2007-01-24
Hello.  I just installed the new Rhythmbox by following the instructions in the first post.  The installation seemed to go fine.  Here are some of the problems I've experienced so far though - 

After I rebooted, my wallpaper was gone.

If I select the Magnatune option the Rhythmbox application just closes.

---

### Post by PWill on 2007-01-24
> **klilja said:**
> Hello.  I just installed the new Rhythmbox by following the instructions in the first post.  The installation seemed to go fine.  Here are some of the problems I've experienced so far though - 

After I rebooted, my wallpaper was gone.

If I select the Magnatune option the Rhythmbox application just closes.

The wallpaper issue seems unrelated, but the Magnatune issue  I can help you with.

Try running `rhythmbox' from the terminal, and tell me what it says in the terminal after you select Magnatune.

---

### Post by klilja on 2007-01-24
rhythmbox
/usr/local/lib/rhythmbox/plugins/artdisplay/__init__.py:139: Warning: Missing artwork icon not found: pixbuf_new_from_file_at_size() argument 1 must be string, not None
  warn ("Missing artwork icon not found: %s" % e, Warning)

(rhythmbox:8238): Rhythmbox-WARNING **: Unable to start mDNS browsing: MDNS service is not running
Traceback (most recent call last):
  File "/usr/local/lib/rhythmbox/plugins/magnatune/MagnatuneSource.py", line 281, in __download_update_cb
    catalog = zipfile.ZipFile(local_song_info_temp_uri.path)
  File "/usr/lib/python2.4/zipfile.py", line 210, in __init__
    self._GetContents()
  File "/usr/lib/python2.4/zipfile.py", line 230, in _GetContents
    self._RealGetContents()
  File "/usr/lib/python2.4/zipfile.py", line 240, in _RealGetContents
    endrec = _EndRecData(fp)
  File "/usr/lib/python2.4/zipfile.py", line 83, in _EndRecData
    fpin.seek(-22, 2)               # Assume no archive comment.
IOError: [Errno 22] Invalid argument

---

### Post by PWill on 2007-01-24
Hm...
Which version of Ubuntu are you on?

---

### Post by klilja on 2007-01-25
I'm on Edgy.  The CE stands for "Christian Edition".  Its just the default Edgy install with some preloaded christian software.

---

### Post by PWill on 2007-01-25
Did you run `sudo apt-get build-dep rhythmbox` ?

---

### Post by klilja on 2007-01-25
Yeah, thats the first thing I did.

---

### Post by gavintlgold on 2007-01-28
Does this work with AMD64? And if not, is there a way? The last deb that you put there says i386. Does that mean it won't work? Downloading now...

---

### Post by PWill on 2007-01-28
I haven't tried it with 64 bit, but you can go ahead and try. If it doesn't try building it from the source.

---

### Post by gavintlgold on 2007-01-28
Nope, "Error: wrong architecture"

Trying source now...

---

### Post by gavintlgold on 2007-01-28
Ok, I guess the building from source worked!

One more thing: on this blog ( [http://doctau.blogspot.com/2006/12/rhythmbox-christmas-presents.html](http://doctau.blogspot.com/2006/12/rhythmbox-christmas-presents.html) ) it says there's a visualizer plugin for Rhythmbox. Is there anyway to get this yet? Or do we just have to wait a bit?

[EDIT: If you are installing with AMD64, you have to install the amd64 ipod debs instead of the i386 ones, they're on the same page]

---

### Post by Corbelius on 2007-01-29
> **gavintlgold said:**
> Does this work with AMD64? And if not, is there a way? The last deb that you put there says i386. Does that mean it won't work? Downloading now...

If u have an Edgy Eft 64bit, u can install rhythmbox 0.9.7 from my repository (included libgpod 0.4.0).

---

### Post by gavintlgold on 2007-01-29
Ok, thanks for the repository!

---

### Post by etaham on 2007-02-01
whats the story with pyton-gpod/libgpod0 4.2?

---

### Post by mykalreborn on 2007-02-06
i've installed your deb, but when i run rhythmbox it doesn't start. so i typed it in the terminal and this is what i get:
```
rhythmbox: error while loading shared libraries: libtasn1.so.3: cannot open shared object file: No such file or directory

```

and when i try to compile it from source it sais
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... configure: error: cannot run C compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details.

```

i installed the build-dep for rhythmbox and i don't have an ipod. any suggestions?

---

### Post by PWill on 2007-02-06
Try running ```
sudo apt-get install libtasn1-3
```

---

### Post by mykalreborn on 2007-02-06
> **xiamcitizen said:**
> Try running ```
sudo apt-get install libtasn1-3
```

nope. it doesn't work. i have all the repositories and some more enabled, but it's not there. it's not in the packages.debian.org repositories either. from what i saw it was libtasn1-3 is available in edgy and feisty. i have dapper. 
:confused:

---

### Post by PWill on 2007-02-06
Ah, I guess you'll have to stick with 0.9.6 until you upgrade :(

---

### Post by mykalreborn on 2007-02-06
i don't have 0.96. i have 0.9.4.1. which has some trouble with podcasts. but i've checked out this great howto ([http://doc.gwos.org/index.php/Rhythmbox_0_9_5](http://doc.gwos.org/index.php/Rhythmbox_0_9_5)) and i think i'll install 0.9.6 from there ;)

---

### Post by Celil Rifat on 2007-02-09
Why is it not on the ubuntu repositories yet?

---

### Post by PWill on 2007-02-10
It is in Feisty :-D

---

### Post by mykalreborn on 2007-02-10
i finnaly figured out my problem. i was installing it from /mnt/share/downloadz, which is a fat32 partition and it was something to do with permisions. i put the tarball in ~/Desktop and it worked like magic. well... it took about 5 or more minutes to make, but it works great. except for the last fm which doesn't play right. it interrupts very fast and then comes back again. sounds like a bad techno song or something. anyone else have this problem?

---

### Post by ernstblaauw on 2007-02-21
A new version of Rhythmbox has been released! Version 0.9.8 can be downlaoded from the Gnome ftp server. I tried to compile it, but ```
./configure
``` quits with:
```
checking for TOTEM_PLPARSER... no
configure: error: totem playlist parsing library not found or too old
```
Thus, I tried to run ```
sudo apt-get build-dep rhythmbox
```But that command gave me this output:```

E: Could not open file /var/lib/apt/lists/nl.archive.ubuntu.com_ubuntu_dists_edgy-backports_edgy_source_Sources - open (2 No such file or directory)
```
That means, I can't install 0.9.8. Has anyone an idea how I can fix this?

---

### Post by blackdalek on 2007-08-06
How come RB 0.9.7 is in the Feisty repository but not in the Edgy repository? There is only RB 0.9.6 for Edgy. What's up with that? I want 0.9.7 on my Edgy box too.

---

