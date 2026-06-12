---
title: "HOWTO: Sibelius 5 under Wine"
date: 2010-09-15
forum: Multimedia Software
---

### Post by mathiaho on 2010-09-15
[FONT=System][SIZE=2]Hi everyone!

I have been a lurker here for quite some time, and since this forum have helped me solve all my ubuntu-related problems, I've decided to give something back.

Sibelius 5 is a powerful musical notation program. Sibelius is, as a tool for notation, arranging and composing, in my opinion superior to both commercial (Finale) and open (musescore, NtEd, rosegarden) programs.

This guide will help you install a Sibelius 5[/SIZE][/FONT][FONT=System][SIZE=2] under Wine[/SIZE][/FONT][FONT=System][SIZE=2], working with MIDI playback. It might work with other versions too. If you know, please let me know! (I've heard Sibelius 4 is much the same except that you don't need wineasio)

I am by no means an expert, so please tell me if you think there's bloat or errors in this guide. This guide is mostly a collection of advice from others and I will give credit where credit's due.

This works under lucid, both the 32 and 64 bits versions.  
[/SIZE][/FONT][FONT=System][SIZE=2]
Contents:
1. Installation
2. Software Synthesizers
3. Additional Settings
4. Bugs/Troubleshooting



[/SIZE]**[SIZE=3]INSTALLATION[/SIZE]**[/FONT] [FONT=System][SIZE=2]


[/SIZE][/FONT]  [FONT=System][SIZE=2]Guide from WineHQ  in quotes [/SIZE][/FONT][FONT=System][SIZE=2](source: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10843](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10843))

> 1.Install wine and wine-dev                 ```

sudo apt-get install wine1.2 wine1.2-dev

```> 2) Get winetricks: in terminal enter 'wget  [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)' (without quotes, and assume the  same for all terminal entries below)                

3) In terminal enter 'sh winetricks' and select:                

corefonts                
dotnet11                 
dotnet20                 
gdiplus                 
msxml3                 
msxml4                 
msxml6                 
vcrun6                
vcrun2005                
vcrun2005sp1                 

(This is one step where there may be some bloat. dotnet20 and  the last three are definitely needed, the rest I install to be safe).[/SIZE][/FONT][FONT=System][SIZE=2]
[/SIZE][/FONT][FONT=System][SIZE=2]I can't find "vcrun2005sp1" (note it's not the same as "vc2005sp1"), and I have successfully installed Sibelius without it, so I have concluded you don't need it. 

*Edit: I have problems installing dotnet11, but I have managed to install sibelius 5 anyway.
[/SIZE][/FONT] [FONT=System][SIZE=2]
[/SIZE][/FONT]> [FONT=System][SIZE=2]4) Install wineasio.[/SIZE][/FONT][FONT=System][SIZE=2]
Ok, you'll need two things:
 wineasio: [http://sourceforge.net/projects/wineasio/](http://sourceforge.net/projects/wineasio/)
Asio SDK: [http://www.steinberg.net/en/company/developer/src_user.html](http://www.steinberg.net/en/company/developer/src_user.html)

Create an account at steinberg.net, and download the asio SDK.

When you're  done, follow these guidelines (my thanks goes to forum user kgi), note the difference if you're using 32 or 64 bits architecture:

> **kgi said:**
> I've got wineasio 0.7.5 working on an amd64 system.  Here's what you'll need. Bear in mind that the 64-bit install is harder  than the 32-bit install. Note that there USED to be separate forks of  wineasio for 64-bit use (called "wineasio-x" or "wineasio-64"). These  are NO LONGER NEEDED: wineasio and jack can run fine on a 64-bit system.

Here's the easy version for a 32-bit install:

First of all, install the prerequisites:

```

sudo apt-get install wine1.2 wine1.2-dev libjack0 libjack-dev checkinstall

```(if you have no build environment, you'll need that; try something like:

```

sudo apt-get install build-essential pkg-config

```as a starting point).

Next, get asio.h from the Steinberg SDK. When you've got this, hold on to it, as it's a pain to keep on having to re-download.

Next, download wineasio-0.7.5.tar.bz2 from sourceforge. Untar it using the command:

```

tar jxvf wineasio-0.7.5.tar.bz2

```cd into the directory, and type:

```

make
sudo checkinstall make install

```Answer a few questions for checkinstall (like the version) and it  will build a nice ad-hoc .deb for you, which you can install using  "dpkg -i" and uninstall using "dpkg -P".

Now for the harder part. If you're on amd64, you will need a few  additional steps. I forget the exact soup of 32-bit libs I had to  install; try:

```

sudo apt-get install libc6-dev-i386 lib32stdc++6 ia32-libs gcc-multilib g++-multilib

```(The reason I'm unsure is that I was also building jackdmp, and I'm not 100% sure which was required for which).

Then, in the Makefile, make the following changes:

In the line starting "wineasio_dll_LDFLAGS" (line 31, in version 0.7.5),
add the directive:

```

-m32

```In other words, the lines that originally look like this:

```

wineasio_dll_LDFLAGS  = -shared \
                        $(wineasio_dll_MODULE:%=%.spec) \
                        -mnocygwin

```should read something like:

```

wineasio_dll_LDFLAGS  = -m32 -shared \
                        $(wineasio_dll_MODULE:%=%.spec) \
                        -mnocygwin

```In the "install:" stanza at the bottom, change the install command
from:

```

    cp wineasio.dll.so $(PREFIX)/lib/wine

```to:

```

    cp wineasio.dll.so $(PREFIX)/lib32/wine/

```(Notice the trailing slash: this is good practice as if the  directory doesn't exist an error will be raised, whereas without it, the  Makefile will silently copy your .so file to a new file called  "/usr/lib32/wine").

Now you can make and install as before, and run:

```

regsvr32 wineasio

```(Note that this shouldn't be done as root)

This version of wineasio works great for me; I can run Reaper and the Native Instruments Kontakt Player demo.

Hope this helps.

Enjoy!

When that's done, let's return to the wineHQ howto:

> 6) Enter the Sibelius 5 DVD, and find the location of the installer msi -  on mine it's /Windows/Sibelius/SibeliusEnglishInstaller.msi                 

In terminal enter 'wine msiexec /i /SibeliusEnglishInstaller.msi and wait for install.                

7) Find the "Other Applications" section of the Sibelius DVD and install Sibelius Sounds Essentials (SSE_Setup.exe)

8) I recommend changing Wine's Audio driver to "OSS" using winecfg. It seems more stable to me.                My experience says otherwise. I recommend the ALSA WINE drivers. It might be different if you want to actually use Sibelius sound essentials (I prefer using Qsynth).
If you know you're not going to use Sibelius Sound Essentials, install them anyway. I have experienced weird bugs if they are not installed.

Congratulations, you should now have a working Sibelius 5 installation.
[/SIZE][/FONT]                                                    [FONT=System][SIZE=2]

**[SIZE=3]SOFTWARE SYNTHESIZER[/SIZE]** (TiMidity or Qsynth/fluidsynth)[/SIZE][/FONT][FONT=System][SIZE=2]
[/SIZE][/FONT][FONT=System][SIZE=2]
[/SIZE][/FONT][FONT=System][SIZE=2]For MIDI playback you will need a softsynth.

I have tried both TiMidity and Qsynth , and I reccomend Qsynth. 
With Qsynth I have no problems with latency at all, which I have with Timidity.

if you know other programs you think are better, please let us know in the comments.

[B]Qsynth:
[/B]
1. Install Qsynth from the software centre.
note that it installs JACK Control for you, and that JACK asks for realtime privileges. Grant Jack his wish. 

2. Qsynth has no default soundfont, so you'll have to download one (look below for a link to the soundfont I use). When you've got the .sf2 file, open Qsynth, click the setup button, go to the soundfont tab and add your soundfont.

3. Now you can choose what audio driver to use with Qsynth. I have tried ALSA and JACK. ALSA is hassle-free and easy, but might not work as good on slower computers. JACK, on the other hand, is a bit harder but very robust.

My desktop computer runs Qsynth with ALSA with no problems
My netbook experiences distortion while running Qsynth with ALSA. Running under JACK, it gets the occasional xrun, but not so often that it bothers me. Latency is no problem at all.

[B]ALSA
[/B] 
Open Qsynth, click the Setup button, go to the Audio tab and select ALSA where it says "Audio Driver". Click OK and answer yes when Qsynth asks for an engine restart.

Open Sibelius and go to Play > Playback devices and activate "Synth input port" and enjoy the music

[/SIZE][/FONT][FONT=System][SIZE=2][B]JACK

[/B]Open JACK Control and start the server. 

If it refuses to start, you probably have to make yourself a member of the group "audio" ([/SIZE][/FONT][FONT=System][SIZE=2]System>Administration>Users and groups[/SIZE][/FONT][FONT=System][SIZE=2]). 
You should also open /etc/security/limits.conf and add the lines:
```
@audio   -  rtprio     99
@audio   -  memlock    unlimited 
```[/SIZE][/FONT][FONT=System][SIZE=2]
This step may actually make Qsynth work better under ALSA as well, but I'm not 100% shure. If you have problems with ALSA, but are hesitant when it comes to JACK, you probably should try this.

You'll have to log out and in for the changes to take effect.

[/SIZE][/FONT][FONT=System][SIZE=2]After starting the JACK server; open Qsynth, click the Setup button, go to the Audio tab and select JACK where it says "Audio Driver"[/SIZE][/FONT][FONT=System][SIZE=2]. Click OK and answer yes when Qsynth asks for an engine restart.
[/SIZE][/FONT][FONT=System][SIZE=2]
[/SIZE][/FONT][FONT=System][SIZE=2]Open Sibelius and go to Play > Playback devices and activate "Synth input port" and enjoy the music

If you have problems with JACK, please search the forums, as I will probably not be able to help you.
[/SIZE][/FONT][FONT=System][SIZE=2]
[/SIZE][/FONT][FONT=System][SIZE=2]**Timidity:**

1. Install "TiMidity++ MIDI sequencer" from the software centre.

2. Activate "TiMidity port 0" in Sibelius (Play>Playback Devices...)

I've had some troubles with the timidity daemon. If you lose MIDI playback after a restart, or if timidity is locking your soundcard please try the following:

3. Deactivate the timidity Daemon from starting automaticly from script, and instead add it to startup programs (I have no idea why this works):

```
sudo gedit /etc/default/timidity
```find the line saying 
```
#TIM_ALSASEQ=false
``` and uncomment it. Save.

Then in System>Preferences>Startup Programs add a command saying ```
timidity -iA
``` (you can name it whatever you want, just to remember what it is)
[/SIZE][/FONT][FONT=System][SIZE=2]
4. In System>Administration>Users and groups make yourself a member of the group "audio"[/SIZE][/FONT][FONT=System][SIZE=2]

[/SIZE][/FONT][SIZE=2]5. If you think the default effects in timidity are annoying (I think so) then:

```
sudo gedit /etc/timidity/timidity.cfg
```find the line saying

 ```
## If you have a slow CPU, uncomment these:
```and do as it says. Then save.

6. Try different soundfonts (.sf2 files). Do a search and you will find  lots on the web. By default timidity uses freepats.cfg. To change this:

```
sudo gedit /etc/timidity/timidity.cfg
```Scroll to the end of the document. Make it look like this:

```

# By default, try to use the instrument patches from freepats:
# source /etc/timidity/freepats.cfg


# alternatively, you can use the fluid-soundfont:
# source /etc/timidity/fluidr3_gm.cfg
# source /etc/timidity/fluidr3_gs.cfg

soundfont /directory/directory/soundfont.sf2
```Notice I have commented the line saying "source /etc/timidity/freepats.cfg"[/SIZE]
[FONT=System][SIZE=2]

[/SIZE]**[SIZE=3]ADDITIONAL SETTINGS[/SIZE]**[/FONT]  [FONT=System][SIZE=2]


[/SIZE][/FONT]  [FONT=System][SIZE=2]1. First of all, you should add the Wine repositories, so you'll get updates. See this page:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

This will make the smoothing of text and notes work, among other things.

2. **Soundfonts**

I prefer using the oldschool [Roland SC-55 soundfont]("http://www.mediafire.com/?nundyjjtcnm"), because it's the least fancy and most basic soundfont you'll find (it's a lot like the basic microsoft windows midi sound). You might differ in taste, though. If you know any good soundfonts, please let us know in a reply!

If you are looking for soundfonts, [this page]("http://sourceforge.net/apps/trac/fluidsynth/wiki/SoundFont") might be a good place to start[/SIZE][/FONT]

[FONT=System][SIZE=2] 
[/SIZE][/FONT][FONT=System]**[SIZE=3]BUGS / [/SIZE]**[/FONT][FONT=System]**[SIZE=3]TROUBLESHOOTING[/SIZE]**[/FONT] [FONT=System][SIZE=2]
[/SIZE][/FONT]
[FONT=System][SIZE=2]
Bugs that I experience:

1. **Sibelius gets laggy after the score has reached some amount of complexity.**[/SIZE][/FONT][FONT=System][SIZE=2]

Reason: Smoothing of text and notes makes sibelius laggy.[/SIZE][/FONT][FONT=System][SIZE=2]

Solution: File>Preferences>Display[/SIZE][/FONT][FONT=System][SIZE=2]
In the "Smoothing" area, go to settings and change it to "fastest"

It won't look as good, but it will be responsive (It gets laggy on windows and mac as well)[/SIZE][/FONT][FONT=System][SIZE=2]


2. **Dynamics are not displayed correctly**[/SIZE][/FONT][FONT=System][SIZE=2]

when adding dynamics, ctrl+f ctrl+m ctrl+p gives the nice "forte" "mezzo" and "piano" signs.
Sometimes this doesn't work in sibelius under wine, only giving lowercase "f" "m" and "p"'s

Reason: I have no clue. This is strange.[/SIZE][/FONT][FONT=System][SIZE=2]

Solution: first type the dynamic sign, and then type an uppercase letter. Then remove the uppercase letter.[/SIZE][/FONT][FONT=System][SIZE=2]

example: "ctrl+f shift+f backspace" will give you a nice "forte"-sign.[/SIZE][/FONT][FONT=System][SIZE=2]


3[/SIZE][/FONT][FONT=System][SIZE=2]. **Sibelius starts fine, but freezes when opening or creating a score.**

Reason: This happens (for me at least) if I select "Midi Through Port 0" as the playback device.

Solution: Open sibelius (but not a score), and go to:

Play>Playback Devices

then select another playback device.

NOTE: You have to start your synth before starting Sibelius for sibelius to detect it.


4. **Sibelius freezes while starting up.**

Reason: Dotnet20 problem

Solution: Reinstall Dotnet20 (winetricks will do the job)[/SIZE][/FONT]
[FONT=System][SIZE=2][B]

I hope anyone will find this helpful. Please let me know if this works for you and if you have any additional tips or thoughts.
[/B][/SIZE][/FONT][FONT=System][SIZE=2]
**-mathiaho**[/SIZE][/FONT]

---

### Post by Old Woman on 2010-10-12
> I've had some troubles with the  timidity daemon. If you lose MIDI playback after a restart, or if  timidity is locking your soundcard please try the following:

3. Deactivate the timidity Daemon from starting automaticly from script,  and instead add it to startup programs (I have no idea why this works):

     Code:
     sudo gedit /etc/default/timidity 
find the line saying 
     Code:
     #TIM_ALSASEQ=false 
 and uncomment it. Save.

Then in System>Preferences>Startup Programs add a command saying      Code:
     timidity -iA
Thank you so much for that advice. I don't use Sibelius, but I've been trying for days to get MIDI playback in Van Basco's, using Wine. I'm using Xubuntu, by the way, so I added the daemon command to  XFCE 4 Settings Manager - Session and Startup. Now everything works  :)

---

### Post by mathiaho on 2010-10-12
That's great!

---

### Post by mathiaho on 2012-03-23
If anyone stumbles by this old thread:

I probably can't help with Sibelius related issues any more, as I've converted to musescore

It's a really nice program. It does have a lot of the same functions as sibelius (although, not all of them), and it seems more stable and robust to me. Much easier under Linux as well, as it's native:

[http://musescore.org/](http://musescore.org/)

---

