---
title: "[SOLVED] JACKaudio via network?"
date: 2007-09-16
forum: Multimedia &amp; Video
---

### Post by marioquark on 2007-09-16
hi everybody...
anybody knows if jackd can connect more PCs via LAN?
jackaudio official site doesn't answer my question :(
thank you!
quark

---

### Post by MrHippocampus on 2007-09-16
behold the power of google, [netjack]("http://netjack.sourceforge.net/"). Its been a while since the last release but hopefully it should still work

---

### Post by marioquark on 2007-09-16
perfect, tnx!

---

### Post by marioquark on 2007-09-19
i tried out [http://netjack.sourceforge.net/](http://netjack.sourceforge.net/) . it starts correctly and creates the **net_pcm** driver in the JACK connections of both PCs, but i can't get no sound.

so **how should i use netjack**?
i'd like also to know if netjack trasports audio data (only master PC play sounds) or if every laptop plays his own music, using LAN only to synchronize. in the latter case, do i must create another alsa_pcm channel below the net_pcm one?
thanx!!!

---

### Post by marioquark on 2007-09-20
the author of netjack wrote me:
> netjack transports audio. the audio you route into net_pcm comes out on the other side of thenetwork connection.
perfect, but i could not get client's music on the master machine, what's the problem?!

---

### Post by marioquark on 2007-09-22
SOLVED!

i had to put a ```
-l 2
``` to the jacknet_client command line, to extend a little the latency... with no -l 2, all the packet were lost :)

:guitar:

---

### Post by Endolith on 2007-12-05
> **marioquark said:**
> i tried out [http://netjack.sourceforge.net/](http://netjack.sourceforge.net/) . it starts correctly and creates the **net_pcm** driver in the JACK connections of both PCs, but i can't get no sound.

Did you compile it from source or are there packages for Ubuntu?

---

### Post by marioquark on 2007-12-06
compiled from source, this time it's easy! :P

compile it then copy the created binary in /usr/bin

---

### Post by Endolith on 2007-12-06
> **marioquark said:**
> compiled from source, this time it's easy!

Compiling from source is never easy.  :-)  It's never worked for me.

---

### Post by marioquark on 2007-12-06
i could send you my binary
post me a private msg with your email...
bye

---

### Post by Endolith on 2007-12-06
> **marioquark said:**
> i could send you my binary
post me a private msg with your email...
bye

Well, if it's really simple, I should just be able to copy and paste some commands to compile it, right?

---

### Post by marioquark on 2007-12-06
here is netjack
[http://prdownloads.sourceforge.net/netjack/netjack-0.12.tar.bz2?download](http://prdownloads.sourceforge.net/netjack/netjack-0.12.tar.bz2?download)
here is jack
[http://prdownloads.sourceforge.net/jackit/jack-audio-connection-kit-0.103.0.tar.gz?download](http://prdownloads.sourceforge.net/jackit/jack-audio-connection-kit-0.103.0.tar.gz?download)
install scons with synaptic
compile with ```
scons jack_source_dir='path/to/jack-src'
```
this creates jack_net.so. copy this to /lib/jack/drivers or wherever jack looks for driver.so`s it also creates jacknet_client. a normal program. and it creates alsa_client.

---

### Post by Endolith on 2007-12-06
> **marioquark said:**
> here is netjack
[http://prdownloads.sourceforge.net/netjack/netjack-0.12.tar.bz2?download](http://prdownloads.sourceforge.net/netjack/netjack-0.12.tar.bz2?download)
here is jack
[http://prdownloads.sourceforge.net/jackit/jack-audio-connection-kit-0.103.0.tar.gz?download](http://prdownloads.sourceforge.net/jackit/jack-audio-connection-kit-0.103.0.tar.gz?download)
install scons with synaptic
compile with ```
scons jack_source_dir='path/to/jack-src'
```
this creates jack_net.so. copy this to /lib/jack/drivers or wherever jack looks for driver.so`s it also creates jacknet_client. a normal program. and it creates alsa_client.

How can you act like this is easy?  It's like learning a new language every time you want to install something.  Here's what I've figured out.  I am not at my computer, so I am doing it over SSH:

[LIST=1]
[*]I used wget to get the .bz2 file from sourceforge: **wget [http://superb-east.dl.sourceforge.net/sourceforge/netjack/netjack-0.12.tar.bz2](http://superb-east.dl.sourceforge.net/sourceforge/netjack/netjack-0.12.tar.bz2)**
[*]used **tar -xjf netjack-0.12.tar.bz2** to extract it into a folder netjack-0.12
[*]**wget [http://internap.dl.sourceforge.net/sourceforge/jackit/jack-audio-connection-kit-0.103.0.tar.gz](http://internap.dl.sourceforge.net/sourceforge/jackit/jack-audio-connection-kit-0.103.0.tar.gz)**
[*]Extracted with **tar -xf jack-audio-connection-kit-0.103.0.tar.gz** into jack-audio-connection-kit-0.103.0
[*]then if i run scons (I've never heard of scons before) in the netjack-0.12 directory, it seems to know what to do, but needs the path information
[/LIST]

But when I do **scons jack_source_dir='/home/endolith/netjack/jack-audio-connection-kit-0.103.0'** it still doesn't work:

```
scons: Reading SConscript files ...
{'jack_source_dir': '/home/endolith/netjack/jack-audio-connection-kit-0.103.0'}
Package jack was not found in the pkg-config search path.
Perhaps you should add the directory containing `jack.pc'
to the PKG_CONFIG_PATH environment variable
No package 'jack' found
Package samplerate was not found in the pkg-config search path.
Perhaps you should add the directory containing `samplerate.pc'
to the PKG_CONFIG_PATH environment variable
No package 'samplerate' found
OSError: 'pkg-config --cflags --libs jack samplerate' exited 1:
  File "/home/endolith/netjack/netjack-0.12/SConstruct", line 29:
    env.ParseConfig('pkg-config --cflags --libs jack samplerate')
  File "/usr/lib/scons/SCons/Environment.py", line 1134:
    return function(self, self.backtick(command))
  File "/usr/lib/scons/SCons/Environment.py", line 473:
    raise OSError("'%s' exited %d" % (command, status))

```

Also, is this going to conflict with my package setup?  I already have the Ubuntu jackd package installed, and I don't want to do anything that will screw everything up by installing files outside of the package manager.  I've screwed up my system enough times following online advice already...  Aren't I supposed to use something like checkinstall so that it shows up in my package manager?

Maybe I'll just wait for it to be added to the Ubuntu repositories.

---

### Post by marioquark on 2007-12-06
i think you launched from wrong directory... however: 
- scons is a different "make"
- jackd is not replaced, sources are needed only to compile netjack
- don't worry about your system: only the binary is created, then you can move it and delete all source files

---

### Post by Endolith on 2007-12-06
> **marioquark said:**
> i think you launched from wrong directory...

Well in any other directory it says scons: *** No SConstruct file found.

---

### Post by MrHippocampus on 2007-12-07
What your doing so far is correct, its failing because you don't have the source code for jack or samplerate, the sources are stored separately from the binaries. If you install libjack-dev and libsamplerate0-dev (and build-essential if you havent installed it already) you should then be able to compile it.

If it complains about any other packages not being found, just search in synaptic for the name and install the -dev for it and it should work :)

---

### Post by Endolith on 2007-12-07
> **MrHippocampus said:**
> What your doing so far is correct, its failing because you don't have the source code for jack or samplerate, the sources are stored separately from the binaries. If you install libjack-dev and libsamplerate0-dev (and build-essential if you havent installed it already) you should then be able to compile it.

If it complains about any other packages not being found, just search in synaptic for the name and install the -dev for it and it should work :)

Had to install libjack-dev libsamplerate-dev build-essential  libasound-dev and all their megabytes of dependencies.

Then give the jack path as "/home/.../jack-audio-connection-kit-0.103.0/" instead of "~/.../jack-audio-connection-kit-0.103.0"

"Easy", he says... :-)

When I get home I will try copying the jack_net.so file and trying it out.

---

### Post by Endolith on 2007-12-07
so download both source files, untar them, and then do this:

```
sudo apt-get install scons libsamplerate-dev libjack-dev libasound-dev
scons jack_source_dir="/home/endolith/Desktop/jack-audio-connection-kit-0.103.0/"

```

And then I have my jack_net.so file on both machines copied to /usr/bin/.  Now what?  :-)  I want to use audio programs on computer and have the sound come out of speakers connected to the other computer.

---

