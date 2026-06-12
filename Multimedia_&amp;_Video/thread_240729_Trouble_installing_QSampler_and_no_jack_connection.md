---
title: "Trouble installing QSampler and no jack connections"
date: 2006-08-21
forum: Multimedia &amp; Video
---

### Post by Nordkraft on 2006-08-21
Hi there!
I'm trying to find an easy way to use my many gig/akai-sample discs with Ubuntu and I've come across LinuxSampler which seems like a reasonable choice. However, trying to install the QSampler frontend GUI has proven a bit difficult. This is what I get when I try to install it:

qsampler depends on libqt3c102-mt, but:
  The package libqt3c102-mt is not installed.

The problem is that this particular package has been replaced in Dapper and thus cannot be installed. Any suggestions as to how I might go about fixing this?

The second problem: LinuxSampler has no audio entry in qjackctl and I can therefore not get an output. Any suggestions as to how I might fix this?

Thanks a lot!

Cheers!:)

---

### Post by floogy on 2006-08-21
If you installed the replacement of the needed lib, you can try to find either a package for backward compatibility or install your package by using dpkg -i --force-depends (see --force-help for dtails).

---

### Post by Nordkraft on 2006-08-21
Cool. Thanks!:) 
When I run QSampler it loads up ok and seems to work, so I guess the missing package thing isn't that serious. So I'll try the dpkg -i --force-depends. 

Do you happen to know what to do about the Jack connection problem?

---

### Post by floogy on 2006-08-21
```
Creating Sampler...OK
Registered MIDI input drivers: ALSA
Registered audio output drivers: ALSA
Starting LSCP network server (0.0.0.0:8888)...OK
```

It simply uses alsa, not jack. You can try **jacklaunch linuxsampler** instead. But I don't know. That doesn't seems to work :(

But regarding your install problem: I didn't had any problem with it. It depends these packages:
```
Depends: libc6 (>= 2.3.4-1), libgcc1 (>= 1:4.0.2), libgig3c2, liblscp, libqt3-mt         (>= 3:3.3.5), libstdc++6 (>= 4.0.2-4), libx11-6, libxext6
```

```
gerhard@ubuntu:~$ apt-cache policy libqt3-mt qsampler
libqt3-mt:
  Installed: 3:3.3.6-1ubuntu6
  Candidate: 3:3.3.6-1ubuntu6
  Version table:
 *** 3:3.3.6-1ubuntu6 0
        500 http://de.archive.ubuntu.com dapper-updates/main Packages
        100 /var/lib/dpkg/status
     3:3.3.6-1ubuntu3 0
        500 http://archive.ubuntu.com dapper/main Packages
qsampler:
  Installed: 0.1.2-0ubuntu1
  Candidate: 0.1.2-0ubuntu1
  Version table:
 *** 0.1.2-0ubuntu1 0
        500 http://archive.ubuntu.com dapper/universe Packages
        100 /var/lib/dpkg/status
```

---

### Post by Nordkraft on 2006-08-21
Yeah, mine says the same thing:

```

```$ apt-cache policy libqt3-mt qsampler
libqt3-mt:
  Installeret: 3:3.3.6-1ubuntu6
  Kandidat: 3:3.3.6-1ubuntu6
  Versionstabel:
 *** 3:3.3.6-1ubuntu6 0
        500 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) dapper-updates/main Packages
        100 /var/lib/dpkg/status
     3:3.3.6-1ubuntu3 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
qsampler:
  Installeret: (ingen)
  Kandidat: 0.1.2-0ubuntu1
  Versionstabel:
     0.1.2-0ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages```

```

I can install it with no problems using apt. Unfortunately, it doesn't work out well (can't create audio device). So I installed it from CVS which worked a little better (I can create audio device:) ) but then I get this depend. problem when installing QSampler.

About the Jack connection, this guy seems to have it working:

[http://www.ubuntuforums.org/showthread.php?t=220120&highlight=linuxsampler](http://www.ubuntuforums.org/showthread.php?t=220120&highlight=linuxsampler)

:confused: 
Cheers!

---

### Post by floogy on 2006-08-21
Hmm.. yes, but he recompiled linuxsampler from the sourcepackage, with ./configure --enable-jack .

Anyway, it won't be in edgy due to license problems that break the debian policy.

gigtools doesnt seem to be an alternative to linuxsampler, though:
~$ apt-cache show gigtools
[...]
Description: command line tools for Gigasampler and DLS Level 1/2 files
 Raw file handling for audio sampler files based on DLS Level 1/2 and
 Gigasampler.
 These files are typically used in modern day audio waveform samplers.
 This package contains the following command line tools:
 .
 gigdump:
   Prints out the content of a .gig file.
 gigextract:
   Extracts samples from a .gig file.
 dlsdump:
   Prints out the content of a DLS file.
 rifftree:
   Prints out the RIFF tree of an arbitrary RIFF file.

---

### Post by Nordkraft on 2006-08-21
I tried compiling it myself too, but it didn't really work out...
Just installed it again from CVS and ran it (LinuxSampler) from the console with a script and it works perfectly!:D  - Jack and all!
...now all I need is a GUI.

---

### Post by floogy on 2006-08-21
> **Nordkraft said:**
> I tried compiling it myself too, but it didn't really work out...
Just installed it again from CVS and ran it (LinuxSampler) from the console with a script and it works perfectly!:D  - Jack and all!
...now all I need is a GUI.

Fine! How did you do that exactly (in detail)? This might be of interest for somebody, and yes, I'm curious too...
Maybe there is a way for you to use qsampler and *just paste that script into* **view-> options -> command line**

---

### Post by Nordkraft on 2006-08-21
I got the source from CVS:
```

cvs -z3 -d:pserver:anonymous@cvs.linuxsampler.org:/var/cvs/linuxsampler co libgig
cvs -z3 -d:pserver:anonymous@cvs.linuxsampler.org:/var/cvs/linuxsampler co liblscp
cvs -z3 -d:pserver:anonymous@cvs.linuxsampler.org:/var/cvs/linuxsampler co linuxsampler
```
From within each of the three created dirs I did:
```
dpkg-buildpackage -rfakeroot -b 
```
And then I installed the created .deb's (located one level above the dirs from which they were created) with
```
sudo dpkg -i *.deb
```

So much for the install. Loading up an instrument I used this command:
```
cat YOURSCRIPT.lscp | netcat -t localhost 8888
```

The script itself I got from the project homepage [http://www.linuxsampler.org/documentation.html](http://www.linuxsampler.org/documentation.html) :
```
#enable echo mode
SET ECHO 1

# load the JACK audio driver
CREATE AUDIO_OUTPUT_DEVICE JACK

# connect to ALSA playback JACK client so we can hear something
# (you can use 'GET AUDIO_OUTPUT_CHANNEL_PARAMETER INFO 0 0 JACK_BINDINGS'
#  to get all available JACK clients / ports)
SET AUDIO_OUTPUT_CHANNEL_PARAMETER 0 0 JACK_BINDINGS='alsa_pcm:playback_1'
SET AUDIO_OUTPUT_CHANNEL_PARAMETER 0 1 JACK_BINDINGS='alsa_pcm:playback_2'

# load the ALSA MIDI driver
CREATE MIDI_INPUT_DEVICE ALSA

# connect my MIDI keyboard which has ALSA seq ID '72:0'
# (see 'aconnect -i' for the IDs of your MIDI devices
#  or use 'GET MIDI_INPUT_PORT_PARAMETER INFO 0 0 ALSA_SEQ_BINDINGS')
SET MIDI_INPUT_PORT_PARAMETER 0 0 ALSA_SEQ_BINDINGS='72:0'

# setup one sampler channel
ADD CHANNEL
LOAD ENGINE gig 0
SET CHANNEL AUDIO_OUTPUT_DEVICE 0 0
SET CHANNEL MIDI_INPUT_DEVICE 0 0
LOAD INSTRUMENT '/home/me/Gigs/PMI Steinway D.gig' 0 0

# finally show our channel setup (optional of course)
GET CHANNEL INFO 0

# quit connection
QUIT
```
...substituting the relevant lines with the info to match my needs:D .

---

