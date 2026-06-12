---
title: "nvidia vs alsa"
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by pellgarlic on 2006-06-14
ok, this is really starting to wind me up - i'm pretty sure it started when i wanted to install alsa drivers for my m-audio audiophile 2496 sound card. (as one of my main uses of my computer is recording and mixing my own songs). 

i had already (successfully) installed the nvidia 8762 drivers from the repositories, and set up my winmodem (requiring a manual compile and install). however, my sound was lacking - system sounds would not play, and anyway, i wanted the alsa drivers for their low-latency ability (ref: my desire to record my songs on my computer). 

so, after many failed atempts to manually compile and instal the alsa drivers, getting numerous error messages about whatever.ko not being found, curses library being needed, and other things, i ended up installing a lot of stuff to try and fix it:

libncurses5-dev
alsa-source
linux-source-2.6.15 (2.6.15-23.39)
various linux-headers and linux-source packages
other things that i can't remember now

at some point, i have no idea when (possible right at the start, when i began trying to install the alsa drivers. although it could have been even before that...) i ended up with a new kernel: 2.6.15-23-686 (the reason i didn't notice is because i have recently wiped windows entirely from my hard drive, and installed ubuntu by itself, so grub's menu was set to not show by default). when i did notice this, i installed the linux-headers and linux-sources for the 686 kernel, and eventually got my alsa drivers working (at least 99% working - the sequencer is giving me problems and i don't know what to do to fix it). 

but as a by-product of the new kernel, my nvidia drivers and modem drivers no longer functioned. so, recompiling and reinstalling the modem driver worked fine. couldn't say the same about the nvidia drivers though - kept getting that weird blue screen with "x server cannot start" or whatever it says, i can't remember exactly off-hand. anyway, using nano to edit the xorg.conf file got me back to the desktop. so i figured out i might need the linux-restricted-modules for the 686 kernel, which i installed, and managed to get the nvidia drivers working. 

"hooray!" i thought, "now i just need to switch that 1024 x 768 resoution back to my lcd-monitor's native 1280 x 1024, and everything's working again..." but no, the highest resolution i can get is the one it's already at. 

so i guess there are a couple of questions i have for the ubuntistas here:

1. is there any way i can find out when that 686 kernel was installed, and with what package?

2. am i doing this all bass-ackwards (so to speak...). i mean, should i be doing these things in a certain order? do some things need to be installed before others? (i.e. nvidia then alsa, or alsa then nvidia).

3. should i really be compiling my own kernel from scratch in order to get these things working properly? (i would also like to get suspend2 working, which i think requires a kernel compile) if so, can i patch a kernel with all these things (i.e. alsa drivers, nvidia drivers, suspend2) or am i going to have to choose between them?  i could just revert to the "nv" driver, but i really want the nvidia drivers working too.

is there a guardian angel out there with answer to all my problems? or at least someone with a suggestion or two?...

[Edit: question 4. or at least, is there something i can do to try and regain my 1280 x 1024 resolution? if i could just do that, things would be *almost* perfect...]

[Edit2: ok, scratch question 4 - i found it out:

sudo dpkg-reconfigure xserver-xorg

allows reconfiguration of graphics card, monitor keyboard and mouse, so i got my 1280 x 1024 back :) 

i would still be insterested in answers to the above questions though...]

---

### Post by Sutekh on 2006-06-14
[quote=pellgarlic]
1. is there any way i can find out when that 686 kernel was installed, and with what package?[/quote] You can use this to determine the kernel version```
uname -r
``` To have installed the 686 kernel, you would have installed one of these three packages.

linux-686 - installs the latest kernel *and* restricted modules package (easiest way to get NVIDIA divers is to install the restricted-modules package and repository NVIDIA package)

linux-image-386 - installs the latest kernel *only *(at the moment 2.6.15-23-686 but will change)
 
linux-image-2.6.15-23-686 - installs the kernel version 2.6.15-23-686 *specifically*.

[quote=pellgarlic]
2. am i doing this all bass-ackwards (so to speak...). i mean, should i be doing these things in a certain order? do some things need to be installed before others? (i.e. nvidia then alsa, or alsa then nvidia).[/quote] ALSA should be installed by default. Was sound working for you after installation? 

It won't make any differnce in any case.

[quote=pellgarlic]
3. should i really be compiling my own kernel from scratch in order to get these things working properly? (i would also like to get suspend2 working, which i think requires a kernel compile) if so, can i patch a kernel with all these things (i.e. alsa drivers, nvidia drivers, suspend2) or am i going to have to choose between them? i could just revert to the "nv" driver, but i really want the nvidia drivers working too.[/quote] No you shouldn't need to compile a kernel for these things, which should be fairly trivial. What is your graphics card model?

Patching a kernel or *modprobe*'ing a kernel is what happens when you install the NVIDIA drivers. A kernel module is created which is then inserted into the kernel. If you use a kernel from the Ubuntu repsoitories, you can use the NVIDIA module from the Ubuntu repositories. If you create/compile your own kernel, these NVIDIA modules must be created from the NVIDIA installer on their web site.

You should be able to do the same for the other things like suspend, but I'm afraid that's more than I've ever looked into.

---

### Post by pellgarlic on 2006-06-15
@sutekh - 

thanks for that excellent post - it made a few fuzzy things a lot clearer for me :) i had actually already used "uname -r" - that's how i realised i had a 686 kernel in the first place, but the rest of the info in your post was much appreciated!

i searched synaptic's "history" for the packages you mentioned (i actually used "linux*"), and could find no trace of them. i am unsure how to check when packages were installed that were not done using synaptic. i guess there might be a dpkg option to show the date of installation for packages it has installed, but i can't find it, and as i don't know how the kernel was installed, i don't even know if dpkg was used. 

i wonder if it's possible the kernel was installed when i first installed dapper? i did a clean install a couple of days after its "full" release, having just wiped my dead windows partitions to dedicate all my space to ubuntu, so grub's menu was hidden, and i had no reason to check what kernel i was using - i just assumed it was the 386 one. i thought i could check the "date modified" for the vmlinuz files to see when it was installed, but they both say "23rd May", which must be when the developers made it, as that date is before the final release of the dapper cd.

as for the alsa issue, i was under the impression that the alsa-drivers were included in ubuntu, but alsa-lib and alsa-utils were not. i was following the instructions on [http://www.alsa-project.org/](http://www.alsa-project.org/) for my soundcard, which stated i had to install alsa-drivers, alsa-lib and alsa-utils. i thought it best to (re)install alsa-drivers, even though ubuntu already had them, just to make sure i had corresponding versions of alsa-lib and alsa-utils.

after reading your statement that alsa should be installed by default, i checked at [http://packages.ubuntu.com/dapper/allpackages.en.txt.gz](http://packages.ubuntu.com/dapper/allpackages.en.txt.gz) and sure enough, it lists seemingly all the alsa stuff i would need. (although i can't see an "alsa-drivers" or "alsa-lib" package, there are others there that seem to fulfil an equivalent purpose). after initial ubuntu installation, i did have sound, but not "event" sounds. as i believed i needed to install alsa anyway, i thought that would fix that. i also seem to recall that running commands like "alsa-conf" and such produced errors saying "not installed". it seems likely that i was just using the wrong commands, but i took it to confirm my already existing impression that some alsa stuff was not installed.

i'm considering starting from scratch again (seems i spend a lot of time doing that - did it with windows, and i'm dong it with linux too :) 'cos i mess about with things a lot, but i like to have a tidy "base") and maybe i'll set up a "parallel" ubuntu partition, a clone, to "experiment" on, leaving my working system intact...

---

### Post by Sutekh on 2006-06-15
> **pellgarlic]
i searched synaptic's "history" for the packages you mentioned (i actually used "linux*"), and could find no trace of them. i am unsure how to check when packages were installed that were not done using synaptic. i guess there might be a dpkg option to show the date of installation for packages it has installed, but i can't find it, and as i don't know how the kernel was installed, i don't even know if dpkg was used. [/quote]So you used apt-get to install the new kernel? Something like this?
```
sudo apt-get install linux*
``` Are you sure? That would have installed a whole lot of packages including several kernels. I'd say you probably installed the linux-686 package. 

Just search for 'linux' in Synaptic to see what packages are installed.  

As for a history of commands, if its not *too* long ago, you can use```
history
```to find the command you used.
```
history | grep apt-get
```Will only list commands containing apt-get.


[quote=pellgarlic]
i wonder if it's possible the kernel was installed when i first installed dapper?[/quote]The Ubuntu installer, to save space on the CD, only contains and installs the 386 kernel as you suspected it might. 


[quote=pellgarlic]
after reading your statement that alsa should be installed by default, i checked at [http://packages.ubuntu.com/dapper/allpackages.en.txt.gz]("http://packages.ubuntu.com/dapper/allpackages.en.txt.gz") and sure enough, it lists seemingly all the alsa stuff i would need. (although i can't see an "alsa-drivers" or "alsa-lib" package, there are others there that seem to fulfil an equivalent purpose).
[/quote]The two packages that Ubuntu should install by default are the **alsa-base** and **alsa-utils** packages. They are the alsa-drivers, alsa-lib, alsa-utils all nicely built into a Ubuntu specific package. You don't need any other packages to be able to use your sound. They are also a newish release (1.0.10) and really should work. 

If you have sound problems, you should try to resolve them with these packages before installing the new release (1.0.11) from source. It could have even worse effects, as I have discovered myself.


[quote=pellgarlic]after initial ubuntu installation, i did have sound, but not "event" sounds[/quote] If you have a problem with system sounds, there are two things to consider said:**
> 
... maybe i'll set up a "parallel" ubuntu partition, a clone, to "experiment" on, leaving my working system intact...If you can, avoid the hassle of reinstalling, and try installing a separate instance of Ubuntu. Then you will know what is needed to fix your problems.

Hope this gets you somewhere closer to resolving them.

---

### Post by pellgarlic on 2006-06-16
hi again sutekh -

when i said "i actually used linux*" i meant that i used that string in the search function of synaptic's "history" viewer, to find out when any packages beginning with "Linux" were installed. this of course, gave results including linux-headers, and linux-source, but not linux-image.

so, i did not mean that i used apt-get to install the linux-image. in fact, i have no idea how the new kernel got on there - i am not aware of how or when it happened, what program was used, or anything. although i reckon it must have been when i was messing about, installing stuff trying to get alsa-1.0.11 to work...

the problem with the sound was: when booting up, there was no "startup" sound, and when shutting down, there was no "shutdown" sound. also, when i tried to preview these sounds in the "sound events" window, i would get only silence. other sounds worked ok. the sound server was activated, and no other sounds were playing when i tried to play the startup and shutdown sounds.

that's good info to know about what alsa stuff is included with dapper though - thanks for that. now i know i don't need to mess with that if i go the reinstall route.

---

### Post by pellgarlic on 2006-06-18
ok, i've reinstalled dapper (being the anal, pedantic perfectionist that i am, i couldn't leave it the way it was :) )

i double-checked, and the alsa packages are indeed present, however the sound is not working properly:

- there are no startup or shutdown sounds (although the files themselves play fine when opened individually). 

- when i type "esd" into the terminal, i get these error messages:

```
Audio device open for 44.1Khz, stereo, 16bit failed
Trying 44.1Khz, 8bit stereo.
Audio device open for 44.1Khz, stereo, 8bit failed
Trying 48Khz, 16bit stereo.
Audio device open for 48Khz, stereo,16bit failed
Trying 22.05Khz, 8bit stereo.
Audio device open for 22.05Khz, stereo, 8bit failed
Trying 44.1Khz, 16bit mono.
Audio device open for 44.1Khz, mono, 8bit failed
Trying 22.05Khz, 8bit mono.
Audio device open for 22.05Khz, mono, 8bit failed
Trying 11.025Khz, 8bit stereo.
Audio device open for 11.025Khz, stereo, 8bit failed
Trying 11.025Khz, 8bit mono.
Audio device open for 11.025Khz, mono, 8bit failed
Trying 8.192Khz, 8bit mono.
Audio device open for 8.192Khz, mono, 8bit failed
Trying 8Khz, 8bit mono.
Sound device inadequate for Esound. Fatal.
```

when i try to play songs i had recorded in "ardour" that i had made before i reinstalled, and also been able to play back ok, there is now no sound. 

i ran "gstreamer-properties", and alsa is selected as the default for audio input and output, so it's not that.

i believe that the problem may be to do with esd not being properly configured to use alsa, but i can't figure out how to do this - the information on alsa's and esd's websites seem to be a bit outdated - the alsa site doesn't mention configuring for esd at all, as far as i can see, and the esd website doesn't seem to have been updated since about 2000 or so.

---

### Post by pellgarlic on 2006-06-19
just for the record, i realised that part of my "problem" was my own stupidity/ignorance - 

the reason i couldn't hear the previous session i had made in in ardour was that the jack connections weren't correct - when i originally made the session in ardour, the default option was to "automatically connect track outputs to master outs". when i opened the session after my reinstall, the connections were not reinstated, so the audio was not being fed to ...anywhere at all, actually! #-o 

so, i made a new "test" session to see how it did it automatically, then opened my previous session and reproduced the connections, and voila - spag bol a la supreme! i closed the session and reopened it, and the connections were gone again, so i redid the connections again, *saved the session* and reopened it again, and the connections were reinstated correctly. 

don't know why they were lost before - perhaps because of reinstalling ubuntu, but i would have thought that the connections were stored in the session files somewhere, and as all the hardware and setup was the same as before, that the connections would still be valid... oh well, at least i got it sorted... kind of. now the session plays back at the wrong speed - too fast - even though i'm pretty sure i have all the bitrate and sample rates the same as they were when i made the recordings. guess it's time for a new thread. ;) 

although, i *am* still getting that error :

"Audio device open for 44.1Khz, stereo, 16bit failed
Trying 44.1Khz, 8bit stereo.
...............................................
...............................................
Audio device open for 8.192Khz, mono, 8bit failed
Trying 8Khz, 8bit mono.
Sound device inadequate for Esound. Fatal." 

which i guess must be something in gnome trying to use oss or esd instead of alsa, even though i don't want it to, and i can't figure out why, or where to change it...

---

### Post by pellgarlic on 2006-06-23
just figured out how i got the 686 kernel!

one word: "automatic update" (:) yeah, i know that's two words!)

last time i did it, it asked me to restart, but i didn't realise why. that's when i ended up with the 686 kernel. i just did another "update" today, and it asked me to restart. this struck a chord, so i hit "esc" as grub was booting, and lo and behold - i had another new kernel! (the first time i got the 2.6.15-23-686 kernel. this time, i got the 2.6.15-25-686 kernel).

obviously, i didn't read through the list of items the update was actually going to update, or i would have spotted the kernel in there. 

i think there should really be some kind of warning about this - automatic update should say "you have selected to install a new kernel - are you sure? some packages (e.g. nvidia drivers, manually compiled modem drivers etc) may not work". 

as it is, there is no indication at all, unless you check every package the update will install, and i have no doubt that many people will do what i did, and just click "apply". well, i actually started to scan through them, but there were 95, so i got a bit bored and didn't read them all :)

it was particularly confusing for me, because i have no other os than ubuntu on my computer, so grub's menu was set as "hidden" by default, so the first time i got the new kernel through "automatic update", i never noticed until i came to the problem i stated in the first post of this thread.

---

