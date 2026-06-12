---
title: "audacious and alsa"
date: 2007-03-02
forum: Multimedia &amp; Video
---

### Post by chikko on 2007-03-02
hey guys,
i just finished installing Ubuntu 6.10 on my brother's computer, and wanted him to use Audacious (this software is great, really!) but i got to a spot which didn't happen to me before:
audacious won't play any file it is given (i installed the 1.3.0-rc2 's from the audacious homepage - the plug-ins as well) and every time i try to feed it with one, i throws the following message:

Unable to play files.

The following files could not be played. Please check that:
1. they are accessible.
2. you have enabled the media plugins required.

from a little research i made, and from comparing the preferences on my lap-top, i understand that i should pick ALSA as my current output plug-in  - but for a strange reason ALSA is not on that list!! (all i have there are the OSS output plugin, NULL output plugin and the Disk Writer plugin.

i also tried installing audacious again, this time from the repos, but it's still running the 1.3.0-rc2 version that i make installed in the first place.. <confused>

help?.. :)

thanks!

---

### Post by david_2001 on 2007-03-02
> **chikko said:**
> 

i also tried installing audacious again, this time from the repos, but it's still running the 1.3.0-rc2 version that i make installed in the first place.. <confused>


I don't know this program but if you compiled from source and didn't change the installation directory prefix when running ./configure then the audacious binary will be in /usr/local/bin.  The audacious binary from the deb package will be installed in /usr/bin.  If /usr/local/bin comes before /usr/bin in $PATH then it will be the compiled binary that runs and not the binary from the deb package if audacious is typed at a console prompt.  If you still have the source then running "make uninstall" ought to remove the compiled binary.

---

### Post by chikko on 2007-03-03
> **david_2001 said:**
> I don't know this program but if you compiled from source and didn't change the installation directory prefix when running ./configure then the audacious binary will be in /usr/local/bin.  The audacious binary from the deb package will be installed in /usr/bin.  If /usr/local/bin comes before /usr/bin in $PATH then it will be the compiled binary that runs and not the binary from the deb package if audacious is typed at a console prompt.  If you still have the source then running "make uninstall" ought to remove the compiled binary.

thanks David :)

"make uninstall" says that there are no build rules and do nothing.
when i tried to ./configure again, i noticed the following lines:
Configuration:

```
  Install path:                           

  Output Plugins
  --------------
  Open Sound System (oss):                yes
**  Advanced Linux Sound Arch. (alsa):      no**
  Enlightenment Sound Daemon (esd):       no
  Jack Audio Connection Kit (jack):       no
  Analog Realtime Synthesizer (arts):     no
  BSD/SUN audio output (sun):             no
  PulseAudio sound server (pulse_audio):  no
  Mac OS X sound support (CoreAudio):     no
  Null Audio output (null):               yes
```

how can i get inside that configuration and change the alsa setting to true..?
(needless to say that xmms and other player installed on my system are using alsa..)

---

### Post by david_2001 on 2007-03-03
If there are no uninstall rules then you will need to find and delete the previously compiled audacious files manually from /usr/local (take a look at the README file that comes with the audacious source).

Normally, there should be no need to edit any of the configuration files before compiling.  Install the libasound2-dev package for alsa plus the "-dev" packages for the various other compilation dependencies before running ./configure again for audacious-plugins.

I downloaded the audacious and audacious-plugins sources and compiled them for myself just to see.  This is what I got at the end of the ./configure run for audacious-plugins:

>   Output Plugins
  --------------
  Open Sound System (oss):                yes
  Advanced Linux Sound Arch. (alsa):      yes
  Enlightenment Sound Daemon (esd):       yes
  Jack Audio Connection Kit (jack):       no
  Analog Realtime Synthesizer (arts):     yes
  BSD/SUN audio output (sun):             no
  PulseAudio sound server (pulse_audio):  no
  Mac OS X sound support (CoreAudio):     no
  Lame encoder (lame):                    yes
  Null Audio output (null):               yes

and a screenshot of audacious running on my PC is attached.

---

