---
title: "HOWTO: Compile OpenAL Soft to fix &quot;crackly sound&quot; in many games"
date: 2008-03-16
forum: Multimedia &amp; Video
---

### Post by Robvdl on 2008-03-16
Many games in Ubuntu produce a horrible,crackly sound on anything but a Creative Labs sound card, for example: Supertux, Chromium.

It took me a while to realise that this is because of a very old, buggy openal driver shipped with Ubuntu. Here is the bug page for it:

[https://bugs.launchpad.net/ubuntu/+source/openal/+bug/194919](https://bugs.launchpad.net/ubuntu/+source/openal/+bug/194919)

OpenAL Soft is a software implementation of the OpenAL spec, more information can be found on the official website:

[http://kcat.strangesoft.net/openal.html](http://kcat.strangesoft.net/openal.html)

Open a terminal window and type:

```
wget http://kcat.strangesoft.net/openal-releases/openal-soft-1.3.253.tar.bz2
tar xvjf openal-soft-1.3.253.tar.bz2
cd openal-soft-1.3.253/CMakeConf
sudo apt-get install cmake libasound2-dev
cmake ..
make
sudo make install
sudo mv /usr/lib/libopenal.so.0 /usr/lib/libopenal.so.0.bak
sudo mv /usr/lib/libopenal.so.0.0.0 /usr/lib/libopenal.so.0.0.0.bak
sudo ln -s /usr/local/lib/libopenal.so.1.3.253 /usr/lib/libopenal.so.0
sudo ln -s /usr/local/lib/libopenal.so.1.3.253 /usr/lib/libopenal.so.0.0.0
cd ../../
rm openal-soft-1.3.253.tar.bz2
sudo rm -r openal-soft-1.3.253

```

---

### Post by mikeym on 2008-04-16
Hi, 

You're missing at least one step (from what I can tell trying to follow your instructions):

```

sudo apt-get install libasound2-dev

```

For me it compiled without ALSA support otherwise. 

However I'm getting the following error trying to run *supertux2* after install:

```

AL lib: alsa.c:190: Wait timeout... buffer size too low?

```

And I'm getting no sound. Although it is one up on the old OpenAL in that it didn't have sound either and it crashed on exit.

---

### Post by mikeym on 2008-04-18
* Bump * Sorry (again)!

---

### Post by Robvdl on 2008-04-19
Hi. I probably already had libasound2-dev installed on my system when I wrote the howto, so I have adjusted my post and added it in.

The error you are getting about the buffer being too small, I am not experiencing this myself. Maybe it could be sound card specific.  I have tried Open AL Soft on my creative audigy 4 card, and a few onboard cards mainly on Ubuntu Gutsy, and have not received this error in supertux. What distro are you using? I have not tried this in Ubuntu Hardy yet.

---

### Post by mikeym on 2008-04-22
Hi,

The problem I was having was a PowerPC issue. I realized that I wasn't getting any sound at all after the initial drums on boot. I recompiled the kernel to version 2.6.25 which has a fix for ppc sound issues. (To do with the soundcard reporting itself as DEAD or something.)

And everything is up and running well including OpenAL Soft. :)

Thanks!

P.S.

I'm using hardy.

---

### Post by Megatog615 on 2008-05-16
Anyone wanna try making a new libopenal0a package out of this?

---

### Post by alfredio on 2008-05-22
BE CAREFUL!

This howto is broken for me, and is probably broken for any Ubuntu system.

After a package manager is ran, all manually modified links to OpenAL Soft
libraries will be messed up, because of the "deferred ldconfig" process that is invoked after a package is installed. So the old openal library will
be used again.

I still have no solution for this (ldconfig correctly puts OpenAL Soft under
the libopenal.so.1 symlink, which is not what we want). Ideas are really welcome.

Cheers

---

### Post by alfredio on 2008-05-23
Cristian Klein has a "gross hack" solution to install OpenAL Soft on Ubuntu. See
[https://bugs.launchpad.net/ubuntu/+source/openal/+bug/194919]("https://bugs.launchpad.net/ubuntu/+source/openal/+bug/194919")
If you have 32-bit flavor of Ubuntu, then it's easy: just execute the command described in
[http://cristiklein.c7obs.net/public/kiwi/openal/test-openal.txt](http://cristiklein.c7obs.net/public/kiwi/openal/test-openal.txt)
and you're done.
Unfortunately, Cristian does not provide packages for amd64. Nevertheless I managed to create them from his sources. I'm not redistributing them, because I was not able to sign them, but I'll give you instructions on how to compile them.

```

sudo aptitude install devscripts cmake
cd /tmp
dget -x http://cristiklein.c7obs.net/public/kiwi/openal/openal-soft_1.3.253.dsc
cd openal-soft-1.3.253
rm CMakeCache.txt
cmake
dbuild
# dbuild may complain about missing build-dependencies. Please manually
# install them, and re-run dbuild
cd ..
dkpg -i libopenal0a-soft_1.3.253_amd64.deb
dget -x http://cristiklein.c7obs.net/public/kiwi/openal/openal_0.0.8-4ubuntu2-0kiwi1.dsc
cd openal-0.0.8-4ubuntu2
dbuild
cd ..
dpkg -i libopenal0a_0.0.8-4ubuntu2-0kiwi1_all.deb

```

If you want to be "clean", open aptitude and mark the libopenal0a-soft as automatically installed. Please do remember to remove these packages, once OpenAL Soft will be officially supported by Ubuntu.

Note: the http site is currently unavailable for me, it was available some hours ago...

---

