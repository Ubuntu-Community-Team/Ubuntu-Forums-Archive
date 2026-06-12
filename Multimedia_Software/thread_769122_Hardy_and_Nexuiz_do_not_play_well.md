---
title: "Hardy and Nexuiz do not play well"
date: 2008-04-26
forum: Multimedia Software
---

### Post by elmer_42 on 2008-04-26
I upgraded to 8.04 yesterday and now Nexuiz doesn't work. It keeps jumping between fullscreen and a monitor-sized window. Before you ask, I have already uninstalled and reinstalled it. Here is the output of when I try to run Nexuiz from the terminal:
```
staylor@Mariner:~$ nexuiz
Nexuiz Linux 09:18:31 Mar 23 2008
Trying to load library... "libz.so.1" - loaded.
Added packfile /usr/share/games/nexuiz/data/data20080229.pk3 (3982 files)
Trying to load library... "libcurl.so.4" - loaded.
Failed to init SDL joystick subsystem: 
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Trying to load library... "libmodplug.so.0" - loaded.
Trying to load library... "libOffscreenGecko.so" "/usr/lib/games/nexuiz/libOffscreenGecko.so" - failed.
execing quake.rc
execing default.cfg
execing physicsQBR.cfg
execing newhook.cfg
execing weapons.cfg
execing normal.cfg
execing config.cfg
execing data/campaign.cfg
couldn't exec autoexec.cfg
Initializing Video Mode: fullscreen 1440x900x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.12
0 SDL joystick(s) found:
Trying to load library... "libjpeg.so.62" - loaded.
Trying to load library... "libpng12.so.0" - loaded.
Draw_CachePic: failed to load gfx/complete
Draw_CachePic: failed to load gfx/inter
Shader 'textures/Reaptxt/sun' already defined
S_Startup: initializing sound output format: 48000Hz, 16 bit, 2 channels...
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Wanted audio Specification:
	Channels  : 2
	Format    : 0x8010
	Frequency : 48000
	Samples   : 4096
Failed to open the audio device! (No available audio device)
S_Startup: sound output initialization FAILED
S_Startup: initializing sound output format: 44100Hz, 16 bit, 2 channels...
Wanted audio Specification:
	Channels  : 2
	Format    : 0x8010
	Frequency : 44100
	Samples   : 4096
Failed to open the audio device! (No available audio device)
S_Startup: sound output initialization FAILED
S_Startup: initializing sound output format: 22050Hz, 16 bit, 2 channels...
Wanted audio Specification:
	Channels  : 2
	Format    : 0x8010
	Frequency : 22050
	Samples   : 2048
Failed to open the audio device! (No available audio device)
S_Startup: sound output initialization FAILED
S_Startup: initializing sound output format: 11025Hz, 16 bit, 2 channels...
Wanted audio Specification:
	Channels  : 2
	Format    : 0x8010
	Frequency : 11025
	Samples   : 1024
Failed to open the audio device! (No available audio device)
S_Startup: sound output initialization FAILED
S_Startup: initializing sound output format: 11025Hz, 8 bit, 2 channels...
Wanted audio Specification:
	Channels  : 2
	Format    : 0x8
	Frequency : 11025
	Samples   : 1024
Failed to open the audio device! (No available audio device)
S_Startup: sound output initialization FAILED
S_Startup: initializing sound output format: 11025Hz, 8 bit, 1 channels...
Wanted audio Specification:
	Channels  : 1
	Format    : 0x8
	Frequency : 11025
	Samples   : 1024
Failed to open the audio device! (No available audio device)
S_Startup: sound output initialization FAILED
S_Startup: initializing sound output format: 8000Hz, 8 bit, 1 channels...
Wanted audio Specification:
	Channels  : 1
	Format    : 0x8
	Frequency : 8000
	Samples   : 512
Failed to open the audio device! (No available audio device)
S_Startup: sound output initialization FAILED
S_Startup: SndSys_Init failed.
Found 1 cdrom drives.
The CD in drive 0 is not an audio cd.
CDAudio_Init: No CD in player.
Can't get initial CD volume
CD Audio Initialized
Client using an automatically assigned port
Client opened a socket on address local:2
Client opened a socket on address 0.0.0.0:53412
No CD in player.
Warning: released an already released button
```

---

### Post by elmer_42 on 2008-04-26
Please help, guys. I can't figure out how to get it working.

---

### Post by LsrLine on 2008-04-28
I can confirm.  I am having the same problem.

---

### Post by Zorael on 2008-04-28
edit: Well, upon reading closer, I guess this isn't likely to solve your issue, so ignore me.
> Did you pick **completely remove** when uninstalling? Also called purge.
```
$ sudo apt-get autoremove --purge nexuiz*
```


Before reinstalling, if you want to be extra super sure, do this.
```
$ sudo updatedb
locate nexuiz
```
Hunt down and remove the files that it lists. You can likely leave out stuff in your home folder, though.

---

### Post by MagicMoonLight on 2008-04-29
:(:( Help Help I'm having the same problem and life not the same without nexuiz I may just have to go all the way back to 7.10 just to play nexuiz :(:(:(

---

### Post by msrinath80 on 2008-04-29
Please try starting nexuiz from the command line using the following command:

padsp nexuiz

---

### Post by martvi on 2008-05-01
I am having the same problem (SndSys_Init failed) with Nexuiz, and I tried the padsp command, but the result is the same: no sound.
...

---

### Post by Melcar on 2008-05-01
Why don't you just get the game directly from the Nexuiz guys?  That's what I have and it plays flawlessly.

---

### Post by herdivet on 2008-05-02
I pulled it down from nexuiz and it's not working on my AMD64 3200+ with Hardy 64.  It starts, shows the intro screen, when you choose a player mode it drops out and the mouse no longer responds until you restart the desktop or reboot.  Is the download from nexuiz working for everyone else?

Thanks in advance!

---

### Post by fatalGlory on 2008-05-02
After finding this link: 
[http://paddydempster.wordpress.com/2008/04/30/pingus-and-pulseaudio-on-hardy/](http://paddydempster.wordpress.com/2008/04/30/pingus-and-pulseaudio-on-hardy/)
I tried:
```
sudo apt-get install libsdl1.2debian-pulseaudio
```this fixed a lot of problems with SDL apps for me.  Mupen64 now works properly, XMame almost does but sound is a bit shaky.  Frets on fire still crashes though.  I think SDL is going to be a problem for hardy for a little while until things get patched.

Still try the above and see what happens, I haven't gotten around to reinstalling nexuiz, OpenArena or Quake 4 yet.  ut2004 is my flavour of choice.

---

### Post by hihihi on 2008-05-05
having the same prob here, switch between fullscreen and not, sdl??
i played today without prob after installation but now it messed up...
running on ubuntu hardy, nvidia 8400m gt, please help


edit:
when i start nexuiz under fluxbox (not gnome-desktop), which runs without compiz and all, nexuiz goes just fine. so it seems to have something with gnome/compiz!?

---

### Post by hihihi on 2008-05-24
when i do:
$ killall compiz.real

the thing runs without errors.

---

### Post by Sisyphus48 on 2008-05-31
> **msrinath80 said:**
> Please try starting nexuiz from the command line using the following command:

padsp nexuiz

My problem with Nexiuz was that I had no sound at all and no ammo (couldn't get any guns to fire).  I tried MSRINATH80'S solution: Please try starting nexuiz from the command line using the following command:

padsp nexuiz.  Nexuiz loaded fine with great sound but still couldn't fire any of my guns.  Also I still got the message, "CD Audio:Bad track number 0".
It, Nexuiz always worked fine with Gutsy.  Added 6/3/08  Got Nexuiz to play sometimes but it has actually crashed and/or hung up my system 3 or 4 times to where the only thing that I could do was restart the computer.

---

