---
title: "ALSA missing drivers"
date: 2005-11-23
forum: Multimedia &amp; Video
---

### Post by jpdrawneek on 2005-11-23
Need some help!

Just installed 5.10 and it does not have the drivers for my sound card :(

I have a darla24 which has been part of the alsa main drivers since 1.0.9, but when I installed hoary it did not have the drivers!!

So any idea how I can get these drivers back into hoary since there part of alsa, because this is for a student radio palyout setup and this is pretty show stopping!

Any help would be great!
Also what do I need to download to compile it from alsa from source since I am not use to debian way of doing things?

---

### Post by narcolept on 2005-11-23
```
sudo apt-get install alsa-base
```

Once alsa is installed,

```
sudo apt-cache search alsa
```

and grab anything else you're going to need.

---

### Post by jpdrawneek on 2005-11-23
[QUOTE=narcolept]```
sudo apt-get install alsa-base
```

Once alsa is installed,

```
sudo apt-cache search alsa
```

and grab anything else you're going to need.[/QUOTE]


K done all that, did not help at all?

I got alsa installed but the ubuntu alsa package has got the echo drivers missing so re-installing it is not going to help.

From the look i need to completely recompile alsa to put the drivers back in, unless there a ubuntu package some where with all the drivers?

So how do I compile alsa in ubuntu?  What packages do i need, like kernel source, headers, which compiler?

---

### Post by narcolept on 2005-11-23
```
 sudo apt-get install build-essential 
```

For all your compilers, accessories, etc.  Then grab the kernel source necessary for your kernel, and compile.

---

### Post by jpdrawneek on 2005-11-23
Downloaded alsa-1.0.10 and tried to compile it, but could not due to a ld error!

ld: crt1.o: no such file: no such directory

Any idea how you install gcc properly on kubuntu so it work?

---

### Post by narcolept on 2005-11-23
Should be able to get it with apt-get install gcc, if it's not already installed.

---

### Post by jpdrawneek on 2005-11-23
[QUOTE=narcolept]```
 sudo apt-get install build-essential 
```

For all your compilers, accessories, etc.  Then grab the kernel source necessary for your kernel, and compile.[/QUOTE]

Thanks, compiling now

---

### Post by jpdrawneek on 2005-11-23
Right new error:

FATAL: Error inserting snd_darla24 (/lib/modules/2.6.12-9-386/kernel/sound/pci/echoaudio/snd-darla24.ko): invalid module format

FATAL: Error running install command for snd_darla24

Ok any idea what I done wrong?

Followed these instructions:
[http://ubuntuforums.org/showthread.php?t=21211&highlight=compiling+alsa](http://ubuntuforums.org/showthread.php?t=21211&highlight=compiling+alsa)

---

### Post by Teroedni on 2005-11-23
your runnig as superuser right?

and your machine is 32 bit?

is this your card [http://www.pcrecording.com/darla.htm](http://www.pcrecording.com/darla.htm)

---

### Post by jpdrawneek on 2005-11-23
[QUOTE=Teroedni]your runnig as superuser right?

and your machine is 32 bit?

is this your card [http://www.pcrecording.com/darla.htm](http://www.pcrecording.com/darla.htm)[/QUOTE]

Yes to all of the above, your point?

---

### Post by Teroedni on 2005-11-23
Can you try to follow this howto [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Echo+Digital+Audio+Corporation&card=Darla.&chip=Motorola+56301&module=darla20](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Echo+Digital+Audio+Corporation&card=Darla.&chip=Motorola+56301&module=darla20)

---

### Post by jpdrawneek on 2005-11-23
[QUOTE=Teroedni]Can you try to follow this howto [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Echo+Digital+Audio+Corporation&card=Darla.&chip=Motorola+56301&module=darla20](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Echo+Digital+Audio+Corporation&card=Darla.&chip=Motorola+56301&module=darla20)[/QUOTE]

Followed it, still same fault with loading the module into the kernel.

Any ideas people?

---

### Post by Teroedni on 2005-11-23
you tried all the options 
it were a lot of different solutuions there
also note this !!!!

Note to debian users: You need to save this information into a file in the /etc/modutils/ directory (Eg. /etc/modutils/alsa) and run update-modules

# ALSA portion
        alias char-major-116 snd
        alias snd-card-0 snd-darla20
	# module options should go here

        # OSS/Free portion
        alias char-major-14 soundcore
        alias sound-slot-0 snd-card-0
	
	# card #1
	alias sound-service-0-0 snd-mixer-oss
	alias sound-service-0-1 snd-seq-oss
	alias sound-service-0-3 snd-pcm-oss
	alias sound-service-0-8 snd-seq-oss
	alias sound-service-0-12 snd-pcm-oss

as ubuntu =debian yopu need to add it

---

### Post by jpdrawneek on 2005-11-23
[QUOTE=Teroedni]you tried all the options 
it were a lot of different solutuions there
also note this !!!!

Note to debian users: You need to save this information into a file in the /etc/modutils/ directory (Eg. /etc/modutils/alsa) and run update-modules

# ALSA portion
        alias char-major-116 snd
        alias snd-card-0 snd-darla20
	# module options should go here

        # OSS/Free portion
        alias char-major-14 soundcore
        alias sound-slot-0 snd-card-0
	
	# card #1
	alias sound-service-0-0 snd-mixer-oss
	alias sound-service-0-1 snd-seq-oss
	alias sound-service-0-3 snd-pcm-oss
	alias sound-service-0-8 snd-seq-oss
	alias sound-service-0-12 snd-pcm-oss

as ubuntu =debian yopu need to add it[/QUOTE]


Done all that -> no joy

Could it not be a problem with the driver, could it be the kernel stuff it is linked to?
the kernel i am useing seems to be 2.6.12.16
but its down loaded lots of header files - the packages seem to range 2.6.12.9 to 2.6.12.16
so any idea whats up with it?

---

### Post by jpdrawneek on 2005-11-23
K, one re-install later....

What I do not like is that it pulls down a lower version of the kernel headers, and this is what it links the drivers to.
Any idea where I can get linux-headers-2.6.12.16 from?
Also what was the 5.10 compiled in, because that may be causing a problem?
As I said, i am new to debian but not to linux in general.

---

### Post by jpdrawneek on 2005-11-25
k, managed to get the sound card to work.

I nuked ubuntu and went back to SuSE did a compile from stock cd install, using alsa-1.0.10 and it just worked!

i think there must be a problem with the build-essential as it drags down for me the wrong header and other crazy stuff.

So the method is sound, just the build enviroment in ubuntu had an error.

---

### Post by ChrisLKirby on 2007-04-20
i also have a Darla24 with Feisty. Is removing Feisty and installing SUSE the only option to get this card to work???

---

### Post by sgx on 2007-04-20
> **ChrisLKirby said:**
> i also have a Darla24 with Feisty. Is removing Feisty and installing SUSE the only option to get this card to work???
I hate to say it, but pro audio is an ubuntu afterthought, and 'home' audio has been bungled, so Mepis, Suse, Fedora, may all be less problematic...I just installed Knoppix 5.1 from dvd, and added all the Debian audio apps, and have a suse 10 with packman and jacklab repositories for audio, and a fedora6 with ccrma repository for audio apps...maudio 24/96 card is flawless on all...good luck with the darla! The right kernels are crucial, that is for sure!
[www.jacklab.net](www.jacklab.net)
 is a good new suse audio-centric distro...

---

