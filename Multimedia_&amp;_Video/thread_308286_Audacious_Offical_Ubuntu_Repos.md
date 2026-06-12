---
title: "Audacious Offical Ubuntu Repos"
date: 2006-11-27
forum: Multimedia &amp; Video
---

### Post by Azakus on 2006-11-27
Found the official Audacious Repos for Ubuntu posted today. {UPDATE} Plugins now included in the repos!{/UPDATE}
**Added in my own repo**
[http://audacious-media-player.org/Downloads](http://audacious-media-player.org/Downloads)
#uPure64 repo (amd64 only)
## uPure64 Repository
deb [http://janvitus.interfree.it/ubuntu/](http://janvitus.interfree.it/ubuntu/) feisty-upure64 main-amd64
deb-src [http://janvitus.interfree.it/ubuntu/](http://janvitus.interfree.it/ubuntu/) feisty-upure64 main-amd64

#Offical Repos
These repos are for both i386 and AMD64
Edgy:
deb [http://static.audacious-media-player.org/ubuntu](http://static.audacious-media-player.org/ubuntu) edgy main
deb-src [http://static.audacious-media-player.org/ubuntu](http://static.audacious-media-player.org/ubuntu) edgy main

Dapper:
deb [http://static.audacious-media-player.org/ubuntu](http://static.audacious-media-player.org/ubuntu) dapper main
deb-src [http://static.audacious-media-player.org/ubuntu](http://static.audacious-media-player.org/ubuntu) dapper main

So far no PPC builds, so that might be a compile your own deal.

{Update}
Thanks to layzd2 for an i386 docklet plugin (.deb)
**i386:** [http://ubuntuforums.org/attachment.php?attachmentid=21919&d=1167503315](http://ubuntuforums.org/attachment.php?attachmentid=21919&d=1167503315)
**AMD64:** [http://ubuntuforums.org/attachment.php?attachmentid=26941&d=1173413490](http://ubuntuforums.org/attachment.php?attachmentid=26941&d=1173413490)

{3/11/2007}
Audacious ver 1.3.0 has a built-in docklet plugin that is much more stable than the ones listed above. Use that one.
{7/18/2007}
uPure64 had completely up to date audacious builds for amd64

---

### Post by niko7865 on 2006-11-27
Can't compile the plugins because audacious isn't installed, can't install audacious because it depends on the audacious-plugins package =(

---

### Post by Azakus on 2006-11-27
Ah. Too early for this then. I guess these'll have to wait until the plugin repos are up. Oh well. If you search the site, the Experimental Repos have the plugins, but for i386 only.

---

### Post by redleafong on 2006-11-29
> **niko7865 said:**
> Can't compile the plugins because audacious isn't installed, can't install audacious because it depends on the audacious-plugins package =(

Exactly the same dilemma](*,) ](*,) ](*,)

---

### Post by Azakus on 2006-12-01
Repos Updated. Now Includes Plugins!

---

### Post by wilberfan on 2006-12-01
Yaaaaaay!   My new favoritest audio player!   (This old Winamp user feels right back at home!)  :-D

---

### Post by endersshadow on 2006-12-02
Wow, great program.  My only request is to include the Docklet plugin in the plugins-extra package.  But wow.  Nearly none of my processor is used to play (compared to about 8% for Rhythmbox), and a GTK2 interface that is just phenomonal.  Thank you!!

---

### Post by zivagolee on 2006-12-03
Yep, no docklet plugin yet :(

Does anyone know to get the xf86audio keys to work with audacious?  There is a package for xmms (xmms-xf86audio) and maybe it can be ported over to audacious....

---

### Post by strawman on 2006-12-05
yes, audacious is good.  these are the presets i use with it; makes all the difference on my laptop.

[http://home.iprimus.com.au/king_willy/winamp.html](http://home.iprimus.com.au/king_willy/winamp.html)

---

### Post by lazyd2 on 2006-12-14
I made a .deb for the docklet plugin with checkinstall for Edgy

---

### Post by zivagolee on 2006-12-14
> **lazyd2 said:**
> I made a .deb for the docklet plugin with checkinstall for Edgy

Thanks for the info!  I never heard of checkinstall before.
Just tried it and created a deb file for the docklet! Sweet! ;)

---

### Post by pickarooney on 2006-12-27
Is audacious a replacement for xmms or a replacement for BMP? What's the difference between the three?

---

### Post by OffHand on 2006-12-27
> **pickarooney said:**
> Is audacious a replacement for xmms or a replacement for BMP? A replacement for both. > **pickarooney said:**
> What's the difference between the three?Audacious is still being maintained and developed.

---

### Post by TSP on 2006-12-27
Hi1 i love Audacious but i add this repos installed audacious and i lost the docklet. I always download and compile audacious, audacious plugins and the docklet, but now i can't get the source code of the docklet to compile it.
Why the docklet is not in the repos? is really usefull.
Please someone can upload the soirce code of the docklet for me?

thanks!

---

### Post by zivagolee on 2006-12-29
> **TSP said:**
> Hi1 i love Audacious but i add this repos installed audacious and i lost the docklet. I always download and compile audacious, audacious plugins and the docklet, but now i can't get the source code of the docklet to compile it.
Why the docklet is not in the repos? is really usefull.
Please someone can upload the soirce code of the docklet for me?

thanks!

From another comment above, using checkinstall, I was able to create a deb pkg.  What errors are you getting?

---

### Post by TSP on 2006-12-30
I can't find the source to compile it : ( is not in the same page listed in the audacious web. yhe deb's around here don't work, maybe because is for a old version of audacious.
I am back with BMP wich works great and use lmuch less resources.
Is all my fault, i have the audacious full working and i don't now why i add this repos to my source list and update my system. bye bye audacious after that 
Thanks for your help! :)

Cheers1

---

### Post by pickarooney on 2006-12-30
Is anyone using audacious (or even xmms) and krusader? I'm trying to set up the filetypes so that double-clicking an mp3 enqueues it in audacious. It works if the executable is set to **audacious -e %U**, in that it adds the song to the current playlist, but it also tries to open a new instance of audacious every time, leaving dozens of unsuccessfully opening applications in the task bar. 

Has anyone any idea what I mean?
I should take a screenshot, maybe.

---

### Post by Hairy_Palms on 2006-12-30
i have a package for the audacious docklet that works in edgy and feisty, ill attach it here
im just glad audacious finally got a ubuntu repos :) :)

---

### Post by SZF2001 on 2007-01-11
Uhm... Which package would I install if I'm running Breezy? Or will this not work for Breezy?

I wish my computer was faster, really.

---

### Post by Azakus on 2007-01-11
Hmm... There was a breezy repo up there a couple of weeks ago. Let me check. They used to have one, but I guess they expect that just about everyone has upgraded to Dapper at least.
Here's a script if you want it:
```
#!/bin/bash
cd ~
mkdir ./audacious
cd ./audacious
wget http://audacious-media-player.org/release/audacious-1.2.2.tgz
wget http://audacious-media-player.org/release/audacious-plugins-1.2.5.tgz
tar xzvf audacious-1.2.2.tgz
tar xzvf audacious-plugins-1.2.5.tgz
sudo aptitude update
sudo aptitude install libgtk2.0-0 libglade libtag1c2a libtag1-dev libtagc0 libtagc0-dev
cd ./audacious-1.2.2
./configure
make
sudo make install
cd ../audacious-plugins-1.2.5
./configure
make
sudo make install

```

---

### Post by Riyonuk on 2007-01-12
So this repos, I have to manually add it in syanptic?

---

### Post by Azakus on 2007-01-12
You could do that, or you could copy and paste straight into the sources.list file that synaptic checks by using "sudo gedit /etc/apt/sources.list" and paste in the information for the repository.

---

### Post by oheh on 2007-01-25
It'd be nice if you removed the post that has the docklet source file now that you have a .deb up.  I use xubuntu and I was in dependency hell for a while trying to build it from source and then I finally realized there's a deb.

---

### Post by Azakus on 2007-01-25
Added the docklet .deb to the first page.

---

### Post by Tripmonkey_uk on 2007-01-27
Cheers for the repo's. Came in very handy :D

A working DEB for version dapper, can be found on [this]("http://diuf.unifr.ch/pai/people/broccoa/linux.php") page!
Direct download link [here]("http://diuf.unifr.ch/pai/people/broccoa/deb/audacious-docklet/audacious-docklet_0.1.1-1attila1_i386.deb")!

Cheers..

---

### Post by K.Mandla on 2007-01-28
Thanks for these!

---

### Post by Omarkj on 2007-02-11
Thanks a lot.. The creators of Winamp really did hit the nail on the head when they designed it, this is a great UI.

---

### Post by Azakus on 2007-03-03
Looks like 1.3.0 is coming out to Ubuntu soon. I tried compiling it from source, but the audacious-plugins package has some errors in it so it wouldn't build.

---

### Post by Azakus on 2007-03-06
Audacious 1.3.0 is now compilable from the SVN builds.
[http://audacious-media-player.org/SVN](http://audacious-media-player.org/SVN)

---

### Post by Azakus on 2007-03-08
Taken a while, but I compiled the docklet plugin for Audacious in AMD64.

---

### Post by nenolod on 2007-03-11
> **Azakus said:**
> Taken a while, but I compiled the docklet plugin for Audacious in AMD64.

With 1.3, the docklet plugin is not needed. We have our own docklet-like plugin which is more stable.

---

### Post by Azakus on 2007-03-11
Yeah I saw that only after I installed the other docklet. The built-in one is much better.

---

### Post by nyinge on 2007-03-14
How do I compile extra stuff into audacious so that it has those plugins?  I took the stable release from its site, and after successfully compiling audacious, audacious-plugins and audacious-plugins-ugly, it was missing support for mp3 and ogg.

I compiled LAME and place the libmp3lame.so inside audacious "Input" folder along with other input plugins.  However, Audacious didn't seem to recognize the plugin.  :(

---

### Post by Azakus on 2007-03-14
Hmm, that shouldn't be happening. Here, I'll post the commands I use to compile it.
```

sudo aptitude install libglade2-dev libvorbis-dev libogg-dev libflac-dev libsdl1.2-dev
wget http://sacredspiral.co.uk/~nenolod/mcs/mcs-0.4.1.tgz
tar xzvf mcs-0.4.1.tgz
cd mcs-0.4.1
sh autogen.sh
./configure
make
sudo make install
wget http://static.audacious-media-player.org/release/audacious-1.3.1.tgz
wget http://static.audacious-media-player.org/release/audacious-plugins-1.3.1.tgz
tar xzvf audacious*
cd audacious-1.3.1
./configure
make
sudo make install
cd ../audacious-plugins-1.3.1
./configure
make
sudo make install
```

---

### Post by nyinge on 2007-03-15
> **Azakus said:**
> Hmm, that shouldn't be happening. Here, I'll post the commands I use to compile it.
```

sudo aptitude install libglade2-dev libvorbis-dev libogg-dev libflac-dev libsdl1.2-dev
wget http://sacredspiral.co.uk/~nenolod/mcs/mcs-0.4.1.tgz
tar xzvf mcs-0.4.1.tgz
cd mcs-0.4.1
sh autogen.sh
./configure
make
sudo make install
wget http://static.audacious-media-player.org/release/audacious-1.3.1.tgz
wget http://static.audacious-media-player.org/release/audacious-plugins-1.3.1.tgz
tar xzvf audacious*
cd audacious-1.3.1
./configure
make
sudo make install
cd ../audacious-plugins-1.3.1
./configure
make
sudo make install
```
Thanks.  Now, I've got things running smoothly, except for mp3 support.  The strange thing is that it shows mp3 lib (libmad) is installed, and "MPEG Audio Plugin" is present under decoder list in the Audacious preferences, however, mp3 files cannot be played.

It's only mp3.  Others work fine.  It's weird.

---

### Post by Azakus on 2007-03-16
Oh, it must be no support for it in your gstreamer codecs.
Install this codec and compile again: "gstreamer0.10-fluendo-mp3 "
And install libmad0-dev

---

### Post by sanketmedhi on 2007-03-24
Where can I get the DEBs for the latest > 1.3 version of audacious?

---

### Post by nyinge on 2007-03-24
> **Azakus said:**
> Oh, it must be no support for it in your gstreamer codecs.
Install this codec and compile again: "gstreamer0.10-fluendo-mp3 "
And install libmad0-dev

I found out that using libmad, I'm unable to play certain mp3 files, but using libmpg123, I can play all mp3s including streaming stuff.  I think it has to do with how an mp3 file is encoded.  Does anyone know why libmad is being used now?

---

### Post by Azakus on 2007-03-24
> **sanketmedhi said:**
> Where can I get the DEBs for the latest > 1.3 version of audacious?

Erg, looks like the Edgy debs aren't out by the Audacious Team yet.
Use this script to build it yourself. This will create the .deb files and install them.
```
sudo echo "deb-src http://static.audacious-media-player.org/ubuntu edgy main" >> /etc/apt/sources.list
sudo apt-get build-dep audacious audacious-plugins
sudo aptitude install checkinstall
wget http://sacredspiral.co.uk/~nenolod/mcs/mcs-0.4.1.tgz
tar xzvf mcs-0.4.1.tgz
cd mcs-0.4.1
sh autogen.sh
./configure
make
sudo checkinstall --pkgname "MCS"
wget http://static.audacious-media-player.org/release/audacious-1.3.1.tgz
wget http://static.audacious-media-player.org/release/audacious-plugins-1.3.1.tgz
tar xzvf audacious*
cd audacious-1.3.1
./configure
make
sudo checkinstall --pkgname "Audacious"
cd ../audacious-plugins-1.3.1
./configure
make
sudo checkinstall --pkgname "Audacious-Plugins"
```

---

### Post by dejitarob on 2007-03-26
> **Azakus said:**
> Erg, looks like the Edgy debs aren't out by the Audacious Team yet.
Use this script to build it yourself. This will create the .deb files and install them.
```
sudo echo "deb-src http://static.audacious-media-player.org/ubuntu edgy main" >> /etc/apt/sources.list
sudo apt-get build-dep audacious audacious-plugins
sudo aptitude install checkinstall
wget http://sacredspiral.co.uk/~nenolod/mcs/mcs-0.4.1.tgz
tar xzvf mcs-0.4.1.tgz
cd mcs-0.4.1
sh autogen.sh
./configure
make
sudo checkinstall --pkgname "MCS"
wget http://static.audacious-media-player.org/release/audacious-1.3.1.tgz
wget http://static.audacious-media-player.org/release/audacious-plugins-1.3.1.tgz
tar xzvf audacious*
cd audacious-1.3.1
./configure
make
sudo checkinstall --pkgname "Audacious"
cd ../audacious-plugins-1.3.1
./configure
make
sudo checkinstall --pkgname "Audacious-Plugins"
```

Hmm, I get 'error while loading shared libraries: libaudacious.so.5: cannot open shared object file: No such file or directory.' I tried [http://audacious-media-player.org/FAQ#8.1](http://audacious-media-player.org/FAQ#8.1) but it didn't work.

Edit: I fixed this by not using checkinstall and doing a plain 'make install' instead. I don't know what's up.

---

### Post by Azakus on 2007-03-27
> **dejitarob said:**
> Hmm, I get 'error while loading shared libraries: libaudacious.so.5: cannot open shared object file: No such file or directory.' I tried [http://audacious-media-player.org/FAQ#8.1](http://audacious-media-player.org/FAQ#8.1) but it didn't work.

Edit: I fixed this by not using checkinstall and doing a plain 'make install' instead. I don't know what's up.

Hmm. Well, I'm not an expert in checkinstall, so I'll bet it was my bad. I just use it because it gives me a .deb package I can remove easily.

---

### Post by the.unclean.cpp on 2007-03-27
Great program! Thanks for the repos!

---

### Post by dejitarob on 2007-04-09
Those repos are really out of date.

---

### Post by Azakus on 2007-04-11
Here's some more up to date repos
Only i386 binaries. 
deb [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental audacious
deb-src [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental audacious

---

### Post by Azakus on 2007-04-15
I added my own repo with version 1.3.2 on the frontpage (currently only amd64, edgy builds).

---

### Post by ashrack on 2007-04-18
I just compiled the proper DEB no checkinstall of AUDACIOUS, PLUGINS, PLUGINS-EXTRA, MCS.
So if anybody wants tell me.

---

### Post by Gammell on 2007-04-28
> **ashrack said:**
> I just compiled the proper DEB no checkinstall of AUDACIOUS, PLUGINS, PLUGINS-EXTRA, MCS.
So if anybody wants tell me.

Of what version, 1.3.2? But um, yeah. That'd be nice. Thanks.

---

### Post by ashrack on 2007-04-29
Yes

---

### Post by Azakus on 2007-07-18
Looks like the very awesome uPure64 repository now has audacious 1.3.2 for amd64.
Just add:
```
## uPure64 Repository
deb http://janvitus.interfree.it/ubuntu/ feisty-upure64 main-amd64
deb-src http://janvitus.interfree.it/ubuntu/ feisty-upure64 main-amd64
```
to /etc/apt/sources.list
GPG key can be added with ```
wget http://janvitus.interfree.it/ubuntu/2C4C84CC.gpg -O- | sudo apt-key add -
```

---

### Post by isaiasneto on 2007-10-21
thanks man!! finally I found the .deb package of docklet!! :lolflag:

---

### Post by Perfect Storm on 2007-10-21
1.4.0 will soon be out!

---

