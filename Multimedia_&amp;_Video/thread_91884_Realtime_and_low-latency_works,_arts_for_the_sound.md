---
title: "Realtime and low-latency works, arts for the sound system does not"
date: 2005-11-18
forum: Multimedia &amp; Video
---

### Post by mathieujohnson on 2005-11-18
Hi,
after searching on the web and forums a lot about realtime kernels and low-latency patches for doing audio work.
I actually have been going on and off on kubuntu and demudi and dynebolic and fedora core 4 with ccrma patches and all.
well, fedora core never worked on my system.
dynebolic was weird.
So the only 2 that worked and looked good were demudi wich is amazing for audio but really lacks updates for the apps, its kde 3.3 and amarok 1.2
anyway lots of functions are in kubuntu that I really appreciate but kubuntu is not workable for audio, latencies of 30ms is not good at all!
but with demudi i can get 2ms going great.
so I though hay, maby I could use the demudi kernel on kubuntu.
well, guess what, I made it possible, not hard really, you just need to dpkg -i everything that you need.
But my main problem now, (its not really a big one though it would be cool) is to get the sound system running through jack, that way, its not a hassle to play audio with amarok and switch to a video in vlc or a recording app and all.
In demudi for the sound system there was a device labeled as jack audio or something like that, and in kubuntu its not availlable.
Now, i really don't mind to not have the sound server on as sound notifications are really useless to my day to day work, but getting reliable performance out of amarok and the likes is quite necessary.
anybody wants to help me, its probably just a library missing or something.
any help will be greatly appreciated.
and if anybody needs help to install the multimedia kernels and preemption patch, I could probably create a little how-to.
thanx
Mathieu

p.s. sorry for the lenght, I thought putting my background would probably be important. anyways

---

### Post by ygarl on 2005-11-18
WOW! That's exactly what I'm wrestling with!

I am a musician and currently using Dyne:Bolic and Agnula (which refuses absolutely to connect my inputs to the Mixer on Ardour!). Dyne:bolic *is* kinda wierd, but at least it has low latency and memory use. I installed Ardour on Ubuntu, which works just fine except with the very high latency (as you can see). So I have a slick distro with lousy latency, a not-so-slick distro with no way to record anything, and a wierd distro which won't give me a high enough screen resolution to see all the mixer on Ardour which DOES work!

I installed the package for JACK using Synaptic, which worked ok... You sure you can't find it???
(Try searching for QJackCTL - I think that installs Jack as a dependency - but you'll probably have to turn on the Universe, Multivere,  etc repositories).
But you have a Multimedia Kernel running and that's GOLD to me. 
How did you do that? I have Agnula (Demundi) installed as an alternate Boot method so I actually *have* the kernel in the other distro...

A short how-to would be brilliant. (I'm sort of mid-level on the Newbie - Guru scale so the terminal doesn't scare me at all... Lots of practice compiling from code as well - Thanks Fedora Core 2 & 3!)

Ta!

---

### Post by mathieujohnson on 2005-11-18
the qjackctl is not the app that I am missing, actually I had it from the kubuntu repos, and took the ones from the agnula cd wich is more up to date, actually, qjackctl is older on the cd but jackd is up to date.

I will write a clean little how to, i think a lot of people a looking forward to this.
Though, seriously, its really easy to do, and I don't know why nobody thought about that.
basicly, all you do is pop the agnula cd in (after a nice (k)ubuntu install) and you dpkg -i the .deb that you need.
I started with installing hydrogen-drumkits wich is lacking from kubuntu.
then I though, hay, I should try the kernel headers, now, this is not simple as you need to select the good one, but if you've been lurking around an agnula install on your computer well, you probably spoted wich one is installed on your system (those kernel headers and images are the one you need) I'd have to do it all over again to get all the packages in the right install order, but basicly, go for the one you feel should be first and fill in the dependencies one by one. there is at least 10-15 packages to be installed If i recall correctly.

and well, once you got everything you wanted from the cd, you reboot and at the grub boot up, select the multimedia kernel and VOILA

I still have my problem with the sound server (the one in the system settings) basicly its the arts library or something. when i load the sound server it adds arts inputs and outputs to jack and every other app (amarok and the like) will be going through the sound server "arts" thingy.

kind of hard to explain, but I had the best routability I could ever imagine on agnula, but I could not live with the old versions!

anyway, I will try and write something easier for everyone if there is more people asking for it.

---

### Post by ygarl on 2005-11-18
Hmmm.. I seem to be using ALSA, via one of the guides here. I ironically have no *sound *issues, but *latency *issues (which the average person never would even know about). 
Meanwhile, your *latency *is sorted more or less, but you have *sound *issues.

What a strange world!
I don't use Arts whatsoever... perhaps we could sort out the ALSA drivers instead and use those. I'll have a sit-down and look up the ALSA guides, but I KNOW esd is nasty in any case.

---

### Post by mathieujohnson on 2005-11-18
yeah, I know how arts and esd is no good.
but the problem is that i can't compile the newer alsa drivers and the new alsa plugins.
basicly, I have the low latency kernel runngin just fine, but since I made a half working install of the new alsa drivers, well, things went wrong and I can't access the sound card in the low latency kernel now, but I do have it on the regular kernel.
anyhow, what sound card do you have?
I'm on a rme multiface sounds good, but without the low latency kernel, amarok skips a lot when doing almost nothing on my computer, so it was really a needed thing to have the low latency kernel wich makes everything sound oriented just work better for some reason.

so, anyway, I will try again later to compile those new drivers and if I can get them to work with the plugins, I think I'll be all set for what I wanted.

---

### Post by mathieujohnson on 2005-11-19
while compiling the alsa plugins wich i beleive will make me able to run alsa through jack that way every alsa app can be routed through jack for obviously helpfull purposes. well, I get an error stating how jack is not present in the pkg config path.
here is what I get:"checking for jack >= 0.98... Package jack was not found in the pkg-config search path. Perhaps you should add the directory containing `jack.pc' to the PKG_CONFIG_PATH environment variable No package 'jack' found
configure: error: Library requirements (jack >= 0.98) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them."

can somebody tell me how to change this, I've got jack running in realtime at 2.9ms without any problems. I would really like for this thing to work.
thanx
Mathieu

---

### Post by mathieujohnson on 2005-11-19
all right, it seems all I was missing is the dev package of the jack lib.
I will reboot to see if everything works like I wanted.
though, things are already great!

---

### Post by mathieujohnson on 2005-11-26
a low latency kernel install how to is coming.
let me know if some are interested or not.
I've got 2 people as of yet, but the more there is the faster I will work on this task (wich would need me to reinstall my system to get things in the right order and all good)
so please let me know if you are interested!

---

### Post by yaaarrrgg on 2005-11-30
yes...I'm interested too.  I just checked out ardour.  the package looks awesome, but the latency is noticable when using multitracking.

---

### Post by aum11 on 2005-11-30
Yes please.

I am attempting to do recording and editing under Ubuntu.  

Your howto is much appreciated as I am still quite a noob.

---

### Post by hardbop200 on 2005-12-01
I am definately interested in how to get low-latency for my 5.10 system, would be very grateful to the writer of a how-to for doing so.  I've been kicking myself with this for awhile - my hardware is old and crappy, and I need all of the help I can get to get jack+ALSA+et al to run properly.

Thanks in advance,

Josh

---

### Post by mathieujohnson on 2005-12-01
well I just posted the how to, it seems like it takes some time before its up there, so, I'll post the link in this thread when the post is up, or if you have the link before I do, post it up here so more people get the how to.

I am currently playing around elive's distro, I installed the live cd and am trying out jack version 100 wich seems to enable alsa patching trough jack, I will report if things work out as it seems to be the best way to get every audio things working through jack.

until then, there's xmms and mplayer that supports jack and all the "pro" audio apps of course, hence its not so bad already.

---

### Post by hardbop200 on 2005-12-01
Wonderful!  Please let me know the link when you get it up.

One more question - does your HOW-TO address installing the latest ALSA from the sources on 5.10?

---

### Post by mathieujohnson on 2005-12-01
no it does not.
but it should be fairly easy, though IIRC the alsa drivers are included in the kernel wich eleminates somehow the possibility to compile your own.
I guess you would have to compile a kernel by hand to get the newest alsa drivers.
though you can compile every other files from the alsa website without any problems.

hope this helps

---

### Post by mathieujohnson on 2005-12-02
[http://ubuntuforums.org/showthread.php?t=97453](http://ubuntuforums.org/showthread.php?t=97453)

that's the link, hope you guys get it working.

---

