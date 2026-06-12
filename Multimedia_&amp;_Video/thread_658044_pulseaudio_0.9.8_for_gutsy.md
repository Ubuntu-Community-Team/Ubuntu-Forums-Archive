---
title: "pulseaudio 0.9.8 for gutsy"
date: 2008-01-04
forum: Multimedia &amp; Video
---

### Post by nightfrost on 2008-01-04
Since it seems the pulseaudio package which is part of gutsy has some powersaving issues and are no good for laptops, I just attempted to build the hardy packages from the source debs in a gutsy environment. I have hardly tried them yet but if anyone is to lazy to build them on their own, I've uploaded an archive  [here]("http://www.naderehvandi.net/backup/pulseaudio-packages.tar.gz") with the packages.

(I'm not sure which thread this should go under, as it isn't a support question... Sorry if it's wrong)

---

### Post by 6205 on 2008-01-04
Uhm...what is the difference between Pulse Audio and current audio in Gutsy. What's the contribution of PA?

---

### Post by nightfrost on 2008-01-04
I've only been using it for a short while but so far I can say this is one of the coolest piece of softwares I've used. For example it can make your audio device available with zeroconf so that other computers on the network can use your audio device to playback music (could be handy if only one computer is connected to the sound system). Also, you can adjust the volume of every stream independent of every other stream. That is, you can turn the volume down on rhythmbox while watching a youtube video. 

I think there's a PA entry in the ubuntu wiki with the regular use cases part, check it out...

---

### Post by Newcomer Johannes on 2008-01-04
> Since it seems the pulseaudio package which is part of gutsy has some powersaving issues and are no good for laptops
Do you mean, that pulseaudio 0.9.6 doesn`t support 24bit audio cards.
I had read it in  
[this]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4070771") thread.

Perhaps you could compile the [_source code of pulseaudio 0.9.8_]("http://www.pulseaudio.org/wiki/DownloadPulseAudio") yourself. But unfortunately it haven`t work by me.:(
I hope you have more luck.:)

sorry for my bad english, I`m from Germany.

---

### Post by nightfrost on 2008-01-04
> **Newcomer Johannes said:**
> Do you mean, that pulseaudio 0.9.6 doesn`t support 24bit audio cards.
I had read it in  
[this]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4070771") thread.

Perhaps you could compile the [_source code of pulseaudio 0.9.8_]("http://www.pulseaudio.org/wiki/DownloadPulseAudio") yourself. But unfortunately it haven`t work by me.:(
I hope you have more luck.:)

sorry for my bad english, I`m from Germany.

Maybe I wasn't clear enough, but the packages in the archive I linked to in the first post contain pulseaudio 0.9.8 packages for gutsy.

About support for 24bit audio cards, I have no clue...

---

### Post by Newcomer Johannes on 2008-01-05
> Maybe I wasn't clear enough, but the packages in the archive I linked to in the first post contain pulseaudio 0.9.8 packages for gutsy.
oh sorry, I didn`t read your post exactly and didn`t open the link.](*,)

thank you very much for the pulseaudio 0.9.8 packages. It works fine now.:)

---

### Post by mfeif on 2008-01-19
nightfrost,

I'd like to try compiling these for x86_64 (what I'm using)... unless you did that already.

Did you just apt-get the sources one by one, modify the dependendies (on all of them!) to support the Gutsy version of libc?

---

### Post by nightfrost on 2008-01-20
> **mfeif said:**
> nightfrost,

I'd like to try compiling these for x86_64 (what I'm using)... unless you did that already.

Did you just apt-get the sources one by one, modify the dependendies (on all of them!) to support the Gutsy version of libc?

Actually, it's easier than you can possibly imagine. First I added the correct hardy deb-src line to /etc/apt/sources.list. Then I just ran 'apt-get source pulseaudio'. After the source packages were retrieved and unpacked, I changed directory to the pulseaudio source dir, where I ran 'dpkg-buildpackage -rfakeroot -uc -b'. This will tell you what packages you miss. After installing them, run the command again and it will build most of the pulseaudio packages. Everything will be build against the gutsy libs. You don't need to edit any configuration file :-)

The only ones that are not part of the 'pulseaudio' source package, are the gst-module, libao-module and libflashsupport. That's it.


Is anyone actually using my uploaded packages? Cause Hardy has new versions up that I've compiled, and I could easily upload them instead of the ones there now. Just let me know in this thread.

---

### Post by mfeif on 2008-01-20
Thanks very much! I'll try it.

---

### Post by ocarinahuff on 2008-01-27
This works great for my Dell Vostro 1500!  Headphones now turn off speakers when plugged in.  As far as I can tell it works great.

:guitar:

Note:  extra configuration is needed, goto pulseaudio.org and follow instructions in link "Perfect Setup"

Edit:  There's a new solution to get headphones working.  Just install linux-backports-modules and libasound2-plugins.  worked for me.  Pulseaudio also works, but the configuration work needed caused problems with some of my apps,  Best to wait until Hardy for pulseaudio.

---

### Post by akaihola on 2008-02-06
> **nightfrost said:**
> Is anyone actually using my uploaded packages? Cause Hardy has new versions up that I've compiled, and I could easily upload them instead of the ones there now. Just let me know in this thread.

I'm using the 0.9.8 packages from your tarball, and they work fine, except most games have hiccups in music and effects. I wonder if the 0.9.9 version would fix that.

---

### Post by nightfrost on 2008-02-06
I'll upload the 0.9.9 if I manage to build them on gutsy.
I'll post back to let you know either way.

---

### Post by nightfrost on 2008-02-06
Alright, the packages are uploaded, get them here: [http://www.naderehvandi.net/backup/pulseaudio-0.9.9-packages.tar.gz](http://www.naderehvandi.net/backup/pulseaudio-0.9.9-packages.tar.gz)

Please post here to confirm of they work, and  whether they solve the audio problem while playing games.

Cheers!

---

### Post by akaihola on 2008-02-06
> **nightfrost said:**
> Alright, the packages are uploaded, get them here: [http://www.naderehvandi.net/backup/pulseaudio-0.9.9-packages.tar.gz](http://www.naderehvandi.net/backup/pulseaudio-0.9.9-packages.tar.gz)

Please post here to confirm of they work, and  whether they solve the audio problem while playing games.

I actually already compiled them myself using the instructions provided earlier in this thread, but it didn't solve the sound hiccup problem.

---

### Post by Newcomer Johannes on 2008-03-01
Could someone compile pulseaudio 0.9.9 for amd64, please?
I don't understand your instruction, how to compile it, sorry.
I'm a really noob, but perhaps someone could tell really easy how to compile it.:)

---

### Post by rockyraccoon on 2008-03-14
i installed the 0.9.9 debs and they got me most of the way towards getting it working. thanks!

---

