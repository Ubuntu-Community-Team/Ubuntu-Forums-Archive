---
title: "HOW-TO enable audioscrobbler support in cmus"
date: 2010-01-24
forum: Multimedia Software
---

### Post by koleoptero on 2010-01-24
Cmus is a wonderful application for playing music in the terminal. A patch has been released to enable audioscrobbler support but the version in the ubuntu repositories doesn't have it applied. I thought I'd create this quick guide to install it with the patch in ubuntu since I found none available and had to do some research myself. 

First of all we need to be sure we have the dependencies and tools needed for the task. Make sure you have enabled the multiverse repositories and then open up a terminal and install what we'll need to get the source, apply the patch and compile it:

```
sudo apt-get install git-core libncurses5-dev
```

Then go to your home directory, *git* the source of cmus and get in there to work with it:

```
cd ~
git clone git://gitorious.org/cmus/cmus.git
cd cmus
```

Then get the patch and apply it:

```
wget --no-check-certificate https://www.github.com/hunner/cmus-audioscrobbler/raw/master/cmus-as.patch
patch < cmus-as.patch
```

Get the dependencies needed for cmus:

```
sudo apt-get build-dep cmus
```

And at last compile and install the program:

```
./configure
make
sudo make install
```

Now to setup cmus with our audioscrobbler account:

```
cd ~
mkdir .cmus
cd .cmus
nano rc
```

In the rc file you now have open in nano enter the following 3 lines:

```
set as_enable=true
set as_user=YOUR_LAST.FM_USERNAME
set as_pass=YOUR_PASSWORD
```

replacing of course the things in capitals with your actual username and password. Hit ctrl+o, enter, ctrl+x to save the file and exit nano.

And you're done! Run cmus, play some music and see it in action. If you want to disable/enable submission on the fly you just have to enter in cmus the commands:

```
:set as_enable=false
:set as_enable=true
```

respectively. You can do the same for your username and password but I believe that cmus won't remember your settings the next time you run it, so it's not very useful.

Hope this helps someone out there. Have fun.

EDIT: Links updated for latest version. Should work for every version from now on. Enjoy!

---

### Post by stormdragon2976 on 2010-11-02
Hi,
The patch fails in a couple of places and make also fails. ./configure succeeded though, so something must have changed. Any idea how to fix it? Here's the output:
patch < as.patch
patching file Makefile
Hunk #2 FAILED at 30.
1 out of 2 hunks FAILED -- saving rejects to file Makefile.rej
patching file as.c
patching file as.h
patching file cmus.c
patching file command_mode.c
patching file lib.c
Hunk #1 succeeded at 9 with fuzz 2 (offset 1 line).
Hunk #2 succeeded at 371 (offset 1 line).
patching file md5.c
patching file md5.h
patching file network.c
patching file network.h
patching file options.c
patching file pl.c
Hunk #2 succeeded at 88 (offset 1 line).
patching file player.c
patching file strlib.c
patching file strlib.h
patching file tree.c
patching file ui_curses.c
Hunk #1 succeeded at 1371 (offset 3 lines).
patching file ui_curses.h
patch unexpectedly ends in middle of line
Hunk #2 succeeded at 50 with fuzz 1.
stormdragon@stormdragon-laptop:~/cmus$ ./configure
checking for program gcc... /usr/bin/gcc
checking for CFLAGS -std=gnu99 -pipe -Wall -Wshadow -Wcast-align -Wpointer-arith -Wwrite-strings -Wundef -Wmissing-prototypes -Wredundant-decls -Wextra -Wno-sign-compare -Wformat-security... yes
checking for CFLAGS -Wdeclaration-after-statement... yes
checking for CFLAGS -Wold-style-definition... yes
checking for CFLAGS -Wno-pointer-sign... yes
checking for CFLAGS -Werror-implicit-function-declaration... yes
checking for CFLAGS -Wno-unused-parameter... yes
checking if CC can generate dependency information... yes
checking byte order... little-endian
checking for DL_LIBS (-ldl -Wl,--export-dynamic)... yes
checking for PTHREAD_LIBS (-lpthread)... yes
checking for realtime scheduling... yes
checking for NCURSES_LIBS (-lncursesw)... yes
checking for working ncurses setup... yes
checking for function resizeterm... yes
checking for function use_default_colors... yes
checking for ICONV_LIBS (-liconv)... no
assuming libc contains iconv
checking for FLAC_LIBS (-lFLAC -lm)... yes
checking for program pkg-config... /usr/bin/pkg-config
checking for MAD_LIBS (pkg-config)... -lmad
checking for MAD_CFLAGS (pkg-config)...
checking for MODPLUG_LIBS (pkg-config)... -lmodplug
checking for MODPLUG_CFLAGS (pkg-config)... -I/usr/include/libmodplug
checking for header <mpc/mpcdec.h>... no
checking for MPC_LIBS (-lmpcdec)... yes
checking for VORBIS_LIBS (pkg-config)... -lvorbisfile -lvorbis -lm -logg
checking for VORBIS_CFLAGS (pkg-config)...
checking for WAVPACK_LIBS (pkg-config)... -lwavpack -lm
checking for WAVPACK_CFLAGS (pkg-config)...
checking for header <mp4v2/mp4v2.h>... no
checking for header <neaacdec.h>... yes
checking for MP4_LIBS (-lmp4v2 -lfaad -lm)... no
checking for header <neaacdec.h>... yes
checking for AAC_LIBS (-lfaad -lm)... yes
checking for FFMPEG_LIBS (pkg-config)... -pthread -L/usr/local/lib -lavformat -lavcodec -ldl -lX11 -lXext -lXfixes -lasound -lxvidcore -lx264 -lvpx -lvorbisenc -lvorbis -ltheoraenc -ltheoradec -logg -lopencore-amrwb -lopencore-amrnb -lmp3lame -lfaac -lm -lz -lavcore -lavutil
checking for FFMPEG_CFLAGS (pkg-config)... -I/usr/local/include
checking for header <ffmpeg/avcodec.h>... no
checking for PULSE_LIBS (pkg-config)... -lpulse
checking for PULSE_CFLAGS (pkg-config)... -D_REENTRANT
checking for ALSA_LIBS (pkg-config)... -lasound
checking for ALSA_CFLAGS (pkg-config)... -I/usr/include/alsa
checking for AO_LIBS (pkg-config)... -lao -lpthread -ldl
checking for AO_CFLAGS (pkg-config)...
checking for program artsc-config... no
checking for header <sys/soundcard.h>... yes
checking for header <sys/audioio.h>... no
stormdragon@stormdragon-laptop:~/cmus$ make
   CC     browser.o
   CC     cmus.o
   CC     command_mode.o
   CC     filters.o
   CC     help.o
   CC     input.o
   CC     keys.o
   CC     lib.o
   CC     options.o
   CC     output.o
   CC     pl.o
   CC     player.o
   CC     server.o
   CC     search.o
   CC     search_mode.o
   CC     tree.o
   CC     ui_curses.o
ui_curses.c: In function 'errno_msg':
ui_curses.c:1397: warning: format not a string literal and no format arguments
   LD     cmus
command_mode.o: In function `cmd_seek':
/home/stormdragon/cmus/command_mode.c:535: undefined reference to `as_hook'
command_mode.o: In function `cmd_p_stop':
/home/stormdragon/cmus/command_mode.c:1343: undefined reference to `as_hook'
command_mode.o: In function `cmd_p_prev':
/home/stormdragon/cmus/command_mode.c:1337: undefined reference to `as_hook'
command_mode.o: In function `cmd_p_next':
/home/stormdragon/cmus/command_mode.c:1317: undefined reference to `as_hook'
lib.o: In function `sorted_set_selected':
/home/stormdragon/cmus/lib.c:374: undefined reference to `as_hook'
options.o: In function `get_as_enable':
/usr/include/bits/string3.h:107: undefined reference to `as_enable'
options.o: In function `get_as_user':
/usr/include/bits/string3.h:123: undefined reference to `as_authinfo'
options.o: In function `get_as_pass':
/usr/include/bits/string3.h:123: undefined reference to `as_authinfo'
options.o: In function `set_as_user':
/usr/include/bits/string3.h:123: undefined reference to `as_authinfo'
options.o: In function `set_as_user':
/home/stormdragon/cmus/options.c:290: undefined reference to `as_authinfo'
options.o: In function `set_as_pass':
/usr/include/bits/string3.h:123: undefined reference to `as_authinfo'
options.o:/home/stormdragon/cmus/options.c:278: more undefined references to `as_authinfo' follow
options.o: In function `set_as_enable':
/home/stormdragon/cmus/options.c:437: undefined reference to `as_enable'
/home/stormdragon/cmus/options.c:436: undefined reference to `as_enable'
/home/stormdragon/cmus/options.c:442: undefined reference to `as_enable'
options.o: In function `toggle_as_enable':
/home/stormdragon/cmus/options.c:450: undefined reference to `as_enable'
options.o: In function `set_as_enable':
/home/stormdragon/cmus/options.c:444: undefined reference to `as_exit'
/home/stormdragon/cmus/options.c:439: undefined reference to `as_init'
pl.o: In function `pl_set_selected':
/home/stormdragon/cmus/pl.c:91: undefined reference to `as_hook'
player.o: In function `get_next':
/home/stormdragon/cmus/player.c:320: undefined reference to `as_hook'
/home/stormdragon/cmus/player.c:320: undefined reference to `as_hook'
tree.o: In function `tree_set_selected':
/home/stormdragon/cmus/tree.c:376: undefined reference to `as_hook'
collect2: ld returned 1 exit status
make: *** [cmus] Error 1

---

### Post by koleoptero on 2010-11-03
I'll check to see if there's a new version of it, so it'll need an updated patch, and fix it if I can. :)

EDIT: updated, should work now. :)

---

### Post by stormdragon2976 on 2010-11-03
Hi,
It works great now, thanks. I noticed that there are now settings for as_user and as_pass in ~/.cmus/autosave. So, I was wondering if it would be ok to set everything there instead of creating the rc file? Also do you know if there is a way to bind a key to run an external command?

---

### Post by koleoptero on 2010-11-03
> **stormdragon2976 said:**
> Hi,
It works great now, thanks. I noticed that there are now settings for as_user and as_pass in ~/.cmus/autosave. So, I was wondering if it would be ok to set everything there instead of creating the rc file? Also do you know if there is a way to bind a key to run an external command?

I have no idea about the settings, didn't notice them (since I had the rc already set-up). You can try them and see if it works. The old method does work though so I'll keep that in the how-to.

As for the keybinding I also have no idea, sorry. :(

---

### Post by VolatileMember on 2011-04-25
Hello,

the preferred way for audioscrobbler support in cmus is via status display programs, e.g. CmuScrobbler. See here:
[http://cmus.sourceforge.net/wiki/doku.php?id=status_display_programs](http://cmus.sourceforge.net/wiki/doku.php?id=status_display_programs)

Running external programs in cmus is possible with :run (for selected files) or with :shell (since version 2.4.0).

---

### Post by koleoptero on 2011-04-26
> **VolatileMember said:**
> Hello,

the preferred way for audioscrobbler support in cmus is via status display programs, e.g. CmuScrobbler. See here:
[http://cmus.sourceforge.net/wiki/doku.php?id=status_display_programs](http://cmus.sourceforge.net/wiki/doku.php?id=status_display_programs)

Running external programs in cmus is possible with :run (for selected files) or with :shell (since version 2.4.0).

I used that method for the dynamic playlists thingy. I'll have to dig into how these things work and update this guide one day. :)

---

### Post by ihatethisflavorsomuch on 2012-09-01
I followed this to the very letter and I keep coming up with this:

cmus is already listening on socket /home/wayne/.cmus/socket

Fixed my problem by starting cmus with:

```
cmus --listen=[port]
```

Your "tutorial" here doesn't do anything except error during the ./configure & make steps.

---

