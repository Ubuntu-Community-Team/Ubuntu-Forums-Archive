---
title: "Sound problem"
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by Adisuki on 2007-12-07
Grrr... i finaly installed ubuntu gutsy 7.10, and damn... and i have no sound...
I mean, i am a linux beginner, and it realy bothers me that everything is autoset, and the sound... NOT... :p

I have a laptop and a realtek sound card... 
Then, when i go to the SOUND -configuration and click TEST it runst TESTING... forever... lol...

Please help me...

btw. i downloaded the realtek linux drivers(a audiopack.tar.bz2 file with 3 tar.bz2 files in it : alsa lib,driver and utils) ,.. and it tells me in the readme.txt this:
> Automatic install:
execute

  ./install


I supose that i should paste the file location in the terminal and add this commands, i did that, but the terminal spills out: Permission denied ... lol..

There are manual install instrucitions too, but they confuse me even more :P

Help please :D

---

### Post by mali2297 on 2007-12-07
To install something system-wide, you have to use sudo. Try
```

sudo ./install

```

For more info:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Adisuki on 2007-12-07
> **mali2297 said:**
> To install something system-wide, you have to use sudo. Try
```

sudo ./install

```

For more info:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

./install command not found ... sorry, but be more specific... i am a EXwinXP user... hehe;)

---

### Post by mali2297 on 2007-12-07
> **Adisuki said:**
> ./install command not found ... sorry, but be more specific... i am a EXwinXP user... hehe;)

Redo what you did last time... 
> 
supose that i should paste the file location in the terminal and add this commands, i did that, but the terminal spills out: Permission denied ...


Permission denied means probably that you have to add sudo in front of the command that you typed in.

---

### Post by Adisuki on 2007-12-07
> **mali2297 said:**
> Redo what you did last time... 


Permission denied means probably that you have to add sudo in front of the command that you typed in.

nope,thats not it :P
Doesn't work...

Look.. this is my file:
/home/adisuki/Downloads/realtek-linux-audiopack-4.07a.tar.bz2

now... what should i ttype in the terminal, if the automatic install is like i said in the first post :p

---

### Post by mali2297 on 2007-12-07
First extract the archive:
```

tar -xvjf /home/adisuki/Downloads/realtek-linux-audiopack-4.07a.tar.bz2

```
Look through the output, where is the file **install** extracted?
Say it is path/to/install, then
```

sudo path/to/install

```
If it doesn't work, post the output of the commands.

---

### Post by Adisuki on 2007-12-07
ok... this is extracted...

> ./realtek-linux-audiopack-4.07a/
./realtek-linux-audiopack-4.07a/Readme.txt
./realtek-linux-audiopack-4.07a/version
./realtek-linux-audiopack-4.07a/alsa-driver-rt20071002.tar.bz2
./realtek-linux-audiopack-4.07a/alsa-lib-1.0.14.tar.bz2
./realtek-linux-audiopack-4.07a/install
./realtek-linux-audiopack-4.07a/alsa-utils-1.0.14.tar.bz2
./realtek-linux-audiopack-4.07a/test.wav.bz2


i do the "sudo /home/adisuki/realtek-linux-audiopack-4.07a/install" thing... and it gives me...

> .: 7: Can't open ./version


---

### Post by Adisuki on 2007-12-07
**HERE IS THE README.TXT**
When I come to the 3.b step... i gives me:

> checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.



> The source code copy from [www.alsa-project.org](www.alsa-project.org).      ver:3.3-4
Linux Source Code for ALC audio codec
Support Codec list:
====AC97 Codec=====
ALC100,100P
ALC200,200P
ALC650D
ALC650E
ALC650F
ALC650
ALC655
ALC653
ALC658
ALC658D
ALC850
ALC101
ALC202
ALC250
ALC203

====HD Audio codec ====
ALC260
ALC262
ALC268
ALC660
ALC660VD
ALC861
ALC861VD
ALC880
ALC882
ALC883
ALC885
ALC888
ALC889A

Installation:
This Source Code is from [www.alsa-project.org](www.alsa-project.org).
For driver installation, please follow below steps. 

Automatic install:
execute

  ./install

Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Turn on sound support (soundcore module, default turn on)

Step 3. Complied source code
	a. cd alsa-driver-1.0.xx
**	b. ./configure**
	c. make
	d. make install
	e. ./snddevices

Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
 	(Please refer to the attached modules.conf)
	 
        snd-xxxx is the card ID.

	-- Azalia controller --ALC880 ALC882 ALC260 ALC262 ALC883 ALC885 ALC888
	   --- Intel ICH6 ICH7 ---------
               snd-hda-intel
           --- ATI chipset -----
	       snd-atiixp

        -- AC97 controller --ALC655 ALC650 ALC250 ALC255
           --- Intel ICH6 ICH7 , SiS 7012 and NVidia----------
               snd-intel8x0
           --- Via8233 Via686a  -------------------------------    
	       snd-via82xx
           --- ATI Chipset  -------------------------------
	       snd-atiixp

        Copy and paste this to the bottom of your /etc/modules.conf or /etc/modprobe.conf file.
	# ALSA portion
          alias char-major-116 snd
          alias snd-card-0 snd-xxxx     
        # OSS/Free portion
          alias char-major-14 soundcore
          alias sound-slot-0 snd-card-0
        # card #1
          alias sound-service-0-0 snd-mixer-oss
          alias sound-service-0-1 snd-seq-oss
          alias sound-service-0-3 snd-pcm-oss
          alias sound-service-0-8 snd-seq-oss
          alias sound-service-0-12 snd-pcm-oss

Step 5. reboot your machine

Step 6. Use the alsamixer the disable mute (All audio line default is mute)
        *Must to compile and to install the ALSA library and utility. (Use automatic install is already install)
        excute alsamixer

Note: 	1. The most detail information, can refer the alsa-kernel/Documenttation/ALSA-Configuration.txt in the azx-021705.tar.bz2.
	2. Kernel Version must be 2.2.14 or later.
	3. All mixer channels are muted by default. You must use a native
		or OSS mixer program to unmute appropriate channels.
	4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux.
	5. The driver added to support the SPDIF functoin. 	
	6. a. You can download the alsa-lib-1.0.9 and alsa-utils-1.0.9a form the [www.alsa-project.org](www.alsa-project.org), then unzip and install them. 
	   b. Suggest use "alsamixer" to control mixer function.
	   c. Used "alsaconf" can autodetect which drive you need to install (step 4). 	
        7. SUSE Distribution must install the ncurses package. 

---

### Post by NotRoot:-) on 2007-12-07
[http://ubuntuforums.org/showthread.php?t=588708](http://ubuntuforums.org/showthread.php?t=588708)   looks like it was also a problem and solution for a Realtek sound card.  Hopefully this will help you out.

I found this on the Known gutsy bugs and workarounds at :  [http://ubuntuforums.org/showthread.php?t=595825&highlight=gutsy+known+bugs](http://ubuntuforums.org/showthread.php?t=595825&highlight=gutsy+known+bugs)

---

### Post by mali2297 on 2007-12-08
> **Adisuki said:**
> ok... this is extracted...



i do the "sudo /home/adisuki/realtek-linux-audiopack-4.07a/install" thing... and it gives me...

I'm sorry, I didn't think of that, the install must be done from the correct directory. Try
```

cd /home/adisuki/realtek-linux-audiopack-4.07a
sudo ./install

```

---

### Post by mali2297 on 2007-12-08
Also, have you done the basic troubleshooting?
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

That is, check
```

aplay -l
lspci -v | grep -A 5 [Aa]udio

```

---

