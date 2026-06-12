---
title: "Problem with h264enc in 10.04"
date: 2010-08-05
forum: Multimedia Software
---

### Post by PC_load_letter on 2010-08-05
I use the script h264enc (installed from the repos) to encode my dvds into avi and mp4. It was working flawlessly under 9.10, now I get the error that MEncoder doesn't support AAC encoding??!!! I have installed all the restricted drivers and I can play dvds, mp4's, ...whatever. Any idea what to do here?

Thanks.

---

### Post by luigi_mb on 2010-08-05
h264enc (and xvidenc and divxenc) get updated quite frequently. Go to 

[http://opendesktop.org/](http://opendesktop.org/)

and look for the latest version(s) under Multimedia. Installation and uninstallation are very simple. If you go this way, use Synaptic first to uninstall the package.

/luigi

---

### Post by PC_load_letter on 2010-08-05
I installed the latest version (via the deb file on the main home page) and still no go with the AAC encoding (the default audio encoding option) here is the error message I got:

**$ h264enc -1p -p ehq**
eventually (with all default options) yields:
 
```
-> MEncoder has exited with a non-zero value!
-> Exiting in function: mencoder_exit()
```

At lease before I updated it used to give more meaningful error. 
Any ideas?

---

### Post by mc4man on 2010-08-05
If you're using the the lucid repo mplayer/mencoder then it depends on the lucid ffmpeg libs where aac encoding has been disabled.
Easy way would be to get a newer, unencumbered mplayer/mencoder from a ppa, there are many, here's one (from the smplayer dev

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

(edit Otherwise you could try adding medibuntu repo and updating your ffmpeg libs to their 'extra' versions - a newr mplayer/mencoder is probably better

---

### Post by Linuxforall on 2010-08-05
Using latest compiled mplayer following andrew's excellent direction is the best way out here, you just need to remove the disable mencoder from the commands.

---

### Post by PC_load_letter on 2010-08-05
> **Linuxforall said:**
> Using latest compiled mplayer following andrew's excellent direction is the best way out here, you just need to remove the disable mencoder from the commands.

Assuming Andrew = mc4man, will do it as soon I find the time, I'll probably use the PPA.

But when you said remove the old mencoder, do you mean manually from the script? 

Another thing, which should probably deserve a big rant thread, was the disabling of the AAC encoding mentioned in the Lucid release notes? Or anywhere?

---

### Post by andrew.46 on 2010-08-05
Hi Linuxfoall,

> **Linuxforall said:**
> Using latest compiled mplayer following andrew's excellent direction is the best way out here, you just need to remove the disable mencoder from the commands.

You would also need to add a few extra files. Best to follow FakeOutdoorsman's guide for x264 and then the -dev files for faac and lame, this would provide a solid start.

Andrew

---

### Post by andrew.46 on 2010-08-05
Hi PC_load,

> **PC_load_letter said:**
> Assuming Andrew = mc4man...

No, I am the good looking one :)

Andrew

---

### Post by mc4man on 2010-08-06
> No, I am the good looking one
Undoubtedly - being an impressionable type, you'll always be the guy in your previous avatar to me..
> 
I'll probably use the PPA.
The quickest / easiest first step - if you think a newer mplayer/mencoder/x264 build(s) is the way to go then the mentioned how-to's will do you fine - You'll need to change the configure in the mplayer guide and most likely use use a slightly different checkinstall command

---

