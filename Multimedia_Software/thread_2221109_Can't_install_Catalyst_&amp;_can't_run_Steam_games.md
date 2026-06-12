---
title: "Can't install Catalyst &amp; can't run Steam games"
date: 2014-04-30
forum: Multimedia Software
---

### Post by niburu1 on 2014-04-30
My computer was running just fine a few days ago--I was running all my Steam games using the open source driver (oibaf ppa for latest mesa) on a mainline kernel (3.14.1). I tried to install Catalyst 14.4 stable as I've always installed Catalyst drivers (build distro specific packages and install the debs) and the installation seemed to work, but at the end when running aticonfig, it wouldn't find the command. I noticed it was installed to the correct location but apparently the path wasn't updated. I rebooted and noticed the open source drivers were still being used. amdcccle also wouldn't launch (not because of bad path---though that was still an issue).

I'm now running the open source drivers but I can't get Steam games to run. When launching Steam I get a dialog box popping up which states:

OpenGL GLX context is not using direct rendering, which may cause performance problems.
For more information visit [https://support.steampowered.com/kb_article.php?ref=9938-EYZB-7457](https://support.steampowered.com/kb_article.php?ref=9938-EYZB-7457).

The KB article provided no help. In Steam, when I try to launch a 3D game, I get no visible error, or with some (e.g. Dota 2) I get:

Could not find required OpenGL entry point 'glGetError'! Either your video card is unsupported, or your OpenGL driver needs to be updated.

So it seems that trying to install Catalyst 14.4 mucked up my opengl configuration. Anyone know how I can fix this? I would be super grateful!

---

### Post by dannyboy79 on 2014-04-30
this happened to me at one point when i was messing around with amd drivers and oibaf's ppa, what has happened is that some of your symlinks pointing to the correct 32bit opengl libraries have become broken. steam is a 32bit program. sad to say that in the end it was easier for me to perform a reinstall than figure out all the symlinks. i believe i created a thread about it within the games & leisure section about one of the amd catalyst versions when it was released. I'll see if i can link to it and maybe it'll help you but maybe not.

heres the link: [http://ubuntuforums.org/archive/index.php/t-2189530.html](http://ubuntuforums.org/archive/index.php/t-2189530.html)

---

### Post by niburu1 on 2014-04-30
Just before reading your post I had purged the oibaf ppa which fixed the Steam issue. I was able to load Dota 2 and it seemed to perform on a par when running mesa 10.2 from oibaf.

I thought this would solve my Catalyst installation issue, but it didn't. I still can't get the darn driver to install. Did you have trouble installing Catalyst when you were updating from oibaf?

---

### Post by monkeybrain20122 on 2014-04-30
I think your kernel 3.14.1 may be the problem.You may need to downgrade your kernel (I mean remove it, not just log in to an old one). fglrx is picky about kernels.

I tried to install fglrx in 13.10 with a kernel newer than stock Ubuntu's and got all kinds of errors (sudo apt-get install in the terminal) that were related to kernel version. I think it might have worked if I removed the kernel and used a stock Ubuntu one but I didn't bother as I was very happy with oibaf (I did purge oibaf berore I tried installing Catalyst. It was not a big problem for me to test different driver as I have cloned my root partition, took 4 minutes to restore if anything went wrong)

---

### Post by QIII on 2014-04-30
aticonfig was deprecated for amdconfig quite some time ago.  It's possible ATI got rid of it completely.

Try amdconfig and let us know if that works.

---

### Post by niburu1 on 2014-04-30
I already tried removing all kernels except stock. Didn't work. Also, I never had a problem installing Catalyst on Kubuntu 13.10 using mainline kernels, so not sure why I've got a problem now.

aticonfig was still present in the fglrx folder, along with amdconfig. (I had a look through the installed files.) Neither worked. They spat out an error that no compatible device was found and that I should reinstall the driver (or something like that). Trying to run amdcccle gave a similar error in a dialog box.

While I have all my stuff backed up, it would be a real pain having to reinstall from scratch! I should start keeping daily snapshots.

---

### Post by QIII on 2014-04-30
"No compatible device" is interesting, assuming you are not running an older RV chipset (< HD 5200 series or so.)  What model is the GPU?

---

### Post by niburu1 on 2014-05-01
it's a Radeon 7600D (A10-5800K APU), so it's not old and it's been supported by all other Catalyst versions. Not sure what's going on here.

---

