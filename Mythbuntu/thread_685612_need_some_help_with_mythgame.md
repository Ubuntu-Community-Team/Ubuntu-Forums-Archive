---
title: "need some help with mythgame"
date: 2008-02-02
forum: Mythbuntu
---

### Post by onesojourner on 2008-02-02
I need to get a snes and nes emulator going on my myth box. I have tried everything and I think I have things so messed up there will be no way to fix it. I am going to do a fresh install of mythbuntu tonight.

I assume that mythgame is set up already so I just need to ad emulators. is that right?

I have followed and refollowed the instructions on the [myhtgame set up wiki]("http://www.mythtv.org/wiki/index.php/MythGameEmulationSetup")

```
 ZSNES

Homepage: http://www.zsnes.com/

Version: 1.51

ZNES requires a mouse for configuration in the GUI, keyboard support is not fully implemented. Fortunately the configuration only has to be done once. You might want to take this time to map unused buttons on your controller to common GUI functions, such as exit, save, and load.

Start ZSNES to create the config file. I recommend setting the option 2x Super SAI Engine under Configuration > Video so the picture looks smoother. To map joypad buttons to GUI functions, set the option under Misc -> Game Keys such as exit and press a button on your controller.

After configuring ZSNES and exiting you must copy the configuration (by default ~/.zsnes) to the mythtv user directory (probably ~mythtv/.zsnes).


Note:
(Current as of 06/20/2006) FC5 users may encounter issues compiling the 1.42 version. Consider getting the CVS version from SourceForge.

(Current as of 03/22/2007) If you experience crackly sound when running roms (under Ubuntu 6.10 at least) , make sure that you use the libsdl1.2-oss package, and not libsdl1.2-all. It seens that ZSNES is optimized to use oss and not alsa.

Add a new player in MythGame's setup:

Player Name: SNES 
Type: SNES 
Command: zsnes -k 25 -m 
Rom Path: /usr/emulators/snes/roms

[edit]
SNES9x

Homepage: http://www.snes9x.com/

Version: 1.43

An alternate SNES emulator is called SNES9x. The quality of this emulator is near to ZSNES, if not better. It has no frontend on Linux but frontends just get in the way on MythTV. Everything can be configured through the command line, and most options work for all games, so once you have it set up you only need to modify command line options when you change hardware, like joysticks.

To view the configuration options run snes9x -h.

On many linux distributions to utilize full screen mode in SNES9x you need to add the SUID bit to your SNES9x binary. This is a security risk, but it makes games much more enjoyable. To add the SUID bit, do this:

 chmod 4750 `which snes9x`

Please adjust group and world permissions as necessary to suit your distribution.

Add a new player in MythGame's setup:

Player Name: SNES 
Type: SNES9X 
Command: snes9x -stereo -r 6 -tr -fs
Rom Path: /usr/emulators/snes/roms

I don't believe there is a -fs or -tr option for snes9x. If there is... I couldn't find via google so please state a source. 
```


nothing I have done seems to work. After my fresh install I need to keep my roms on a seperate partition. So far I have not found a good how-to. if some one has one please point me in the right direction.

---

### Post by newlinux on 2008-02-02
That wiki worked for me. Maybe you could tell us more of what you did and what problems you are having. For me, I found it best to get the emulators working outside of myth. are you having problems with the emulators or with configuring mythgame?

I use fceu for nes, and zsnes for snes, and I also have PS1 emulator setup (PSX).

---

### Post by onesojourner on 2008-02-03
alright for zsnes I installed it and ran it an the machine. To get it working in myth is the next thing up. 

```
After configuring ZSNES and exiting you must copy the configuration (by default ~/.zsnes) to the mythtv user directory (probably ~mythtv/.zsnes).
```

I don't have a file in mythtv called .zsnes.

---

### Post by newlinux on 2008-02-03
It should be a directory ~/.zsnes from whatever user you ran it as. You ran it with a ROM and it worked fine? It created one on both the machines I ran it on... hmmm...

do you have a file called  zguicfgl.dat anywhere on your system?

---

### Post by onesojourner on 2008-02-03
I have the .znes file in my home folder. I don't have a the file mythtv/.zsnes.

---

### Post by newlinux on 2008-02-03
Then all you need to do for that step is make a link to it in your .mythtv directory

```

ln -s ~/.zsnes /home/mythtv/.mythtv/
```

---

### Post by newlinux on 2008-02-04
If you run myth as a user other than mythv then you probably need to link it to that user's .mythtv directory, e.g.

```

ln -s ~/.znses /home/*username*/.mythtv/
```

---

### Post by onesojourner on 2008-02-05
ok I got that done. I have my roms at media/mcstorage2/roms/nes and  media/mcstorage2/roms/snes.  how can I tell mythgame to search that directory?

---

### Post by newlinux on 2008-02-05
I'm not at my machine now, but I think you go to:

Utilities/Setup > Setup > Media Settings > Game Settings > Game Players

Add an NES (and SNES) game player and specify where the ROMS, screenshots, and path to emulators, etc. You can also setup commandline parameters. There is some opiton somewhere in game settings to do an "in-depth game scan." That might be what you are looking for.

---

