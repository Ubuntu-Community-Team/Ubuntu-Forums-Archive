---
title: "Mixxx gives lots of xruns"
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by nlz on 2008-03-10
When i run Mixxx i get a awfull lot of Xruns, first i thought it was because direct rendering wasn't working, but that isn't the case. Even in simple mode, when there are almost no graphics, i get really tons of xruns. 
But when i for instance run Jamin, H20, Audacious, Ardour 2, Sooperlooper and Meterbridge, i have no problems (read: xruns) at all!

Normally is have 11,6 msecs latency in Jack with running the realtime kernel. I tried setting the latency to 1000's of msecs, but i keep on getting xruns with mixxx. 

My CPU isn't even on 50% of it's capacity when mixxx and Jack are running. Should i maybe set priority to mixxx or something?

What's going on, and how can i fix it? Mixxx is the last thing that's on my wishlist for my livesets..

---

### Post by kapello on 2008-03-10
not sure about mixxx specifically but I had general problems with xruns and had some success with these settings in JackControl:

Frames/Period: 512
Periods/Buffer: 3

For me, the default of Periods/Buffer 2 seems to give lots of xruns. Setting to 3 doesn't seem to cause me any problems.

---

### Post by GameGod on 2008-03-10
nlz: does your videocard have direct rendering and/or do you have good drivers installed?

Also, does changing the waveform view in the settings to "simple" help at all?

You might want to try the latest beta as well, tons has stuff has changed in Mixxx 1.6.0 beta2: [http://www.mixxx.org/download.php]("http://www.mixxx.org/download.php")

---

### Post by nlz on 2008-03-10
@ kapello: as you could have read, i fiddled a lot with Jack, and changing those setting didn't work at all

@ gamegod
Hi gamegod,

I'm having troubles with getting direct rendering working with my radeon mobility x1600(as you can read here. But even if the waveform view is set to simple, i get the same amount of xruns.

and then i have another handicap: i'm using internet from behind a proxy server which blocks everything with xxx in it, so it ain't easy troubleshooting!

i'll try downloading the new mixxx though i-bypass ([www.greenrabbit.org](www.greenrabbit.org))

---

### Post by GameGod on 2008-03-11
Ok, let me know if the new version helps.... thanks!

---

### Post by nlz on 2008-03-11
wow, this new mixxx looks SLICK, very nice. You guys really did a good job, thanks a lot.

I didn't get everything up and running yet. When i had Jack running, mixxx said that it couldn't find the audio device. When i started mixxx without Jack running it also couldn't get hold of my soundcard. But when i selected dmix, everything jumped into the right setting (ALSA, soundcard etc).
In alsa i also had no xruns that i could hear.

But how do i get mixxx to work with jack? The good old mixxx-with-jack command gave the following output:

```
qnuf@mediaction:~$ mixxx-with-jack
Debug: Starting up...
JACK tmpdir identified as [/dev/shm]
Debug: Api name: OSS
Debug: Api name: ALSA
Debug: Api name: JACK Audio Connection Kit
Debug: type signal
Debug: type marks
Debug: type signal
Debug: type marks
Debug: playlist name Default
Segmentation fault (core dumped)
qnuf@mediaction:~$ 
 
```

but i think this is because it refers back to the old mixxx, doesn't it?
How should i get it working with jack? there must be a easy work around.. 

Thanks again..

---

### Post by GameGod on 2008-03-11
The lack of JACK is caused by a bug in the PortAudio package in Gutsy. This has been fixed in Hardy for 32-bit users at the moment.

In the meantime, you can compile and install PortAudio yourself:

```

sudo apt-get build-dep libportaudio2
sudo apt-get install libjack-dev
svn co https://www.portaudio.com/repos/portaudio/branches/v19-devel
cd v19-devel
./configure --prefix=/usr
make
make install

```

After you install, start JACK before running Mixxx and JACK should appear. Sorry for the inconvenience (this has been a pain for tons of our users).

---

### Post by nlz on 2008-03-11
when i type 'sudo apt-get build-dep libportaudio2' i get
```

qnuf@mediaction:~$ sudo apt-get build-dep libportaudio2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for portaudio19
```

although i've got the libportaudio2 package ( i checked it in synaptic)

and then it start's complaining:

```
qnuf@mediaction:~$ svn co https://www.portaudio.com/repos/portaudio/branches/v19-devel
svn: PROPFIND request failed on '/repos/portaudio/branches/v19-devel'
svn: PROPFIND of '/repos/portaudio/branches/v19-devel': could not connect to server (https://www.portaudio.com)
qnuf@mediaction:~$ sudo apt-get build-dep libportaudio2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for portaudio19
```

---

### Post by nlz on 2008-03-11
your website (linuxrevolutions) is unreachable for me btw..

---

### Post by kapello on 2008-03-11
I read that you tried "setting the latency to 1000s of seconds", with no description of which settings you altered to achieve that. my suggestion may well have reduced your latency, depending on what your previous settings were -  information you did not give.

and you're welcome.

---

### Post by nlz on 2008-03-12
i'm terribly sorry kapello. but setting the period/buffer should affect all programs, not just one. So that was not a solution to my problem. Don't feel offended.

but that doesn't solve the problem..

gamegod?

---

### Post by kapello on 2008-03-13
nlz yr right, i'm embarassed, apologies

---

### Post by GameGod on 2008-03-15
Ok, nlz, I'd recommend opening up a bug report in Mixxx's bug tracker so that this issue doesn't get lost:

[https://launchpad.net/mixxx](https://launchpad.net/mixxx)

More Mixxx developers will have their eyes on it that way, and we won't forget about it.

Thanks!

---

### Post by nlz on 2008-03-17
i found a nice how-to for compiling mixxx for jackd support on the mixxx wiki (mixxx.org/wiki), which was a bit bigger then you howto. i will try that one first and report back here.

thanks.

---

### Post by nlz on 2008-03-17
i'm halfway, i think.

It worked to compile portaudio through the advices given on the mixxx wiki. I only had to configure SVN (subversion) for my proxy settings. 
After that i tried to build mixxx, but the SVN link on the wiki seemed to be broken so i'm now donwloading mixxx to reinstall and then i hope it works.  I'll report back..

---

### Post by nlz on 2008-03-17
OK gamegod, one more question

now i try to compile mixxx with scons (the new installer) it seems to look for QT4 packages that are not there

```
qnuf@mediaction:~/Desktop/mixxx-1.6.0beta2$ sudo scons prefix=/usr djconsole=1 install
[sudo] password for qnuf:
scons: Reading SConscript files ...
Platform: Linux
QT path: /usr/share/qt4
Loading qt4 tool...
/home/qnuf/Desktop/mixxx-1.6.0beta2/src/qt4.py:234: DeprecationWarning: raising a string exception is deprecated
  raise "Qt4 command '" + command + "' not found. Tried: " + fullpath1 + " and "+ fullpath2
Qt4 command 'moc' not found. Tried: /usr/share/qt4/bin/moc-qt4 and /usr/share/qt4/bin/moc: None:
  File "/home/qnuf/Desktop/mixxx-1.6.0beta2/SConstruct", line 2:
    SConscript(File('src/SConscript'), build_dir=Dir('src/.obj'), duplicate=0)
  File "/usr/lib/scons/SCons/Script/SConscript.py", line 583:
    return apply(method, args, kw)
  File "/usr/lib/scons/SCons/Script/SConscript.py", line 520:
    return apply(_SConscript, [self.fs,] + files, subst_kw)
  File "/usr/lib/scons/SCons/Script/SConscript.py", line 245:
    exec _file_ in call_stack[-1].globals
  File "/home/qnuf/Desktop/mixxx-1.6.0beta2/src/SConscript", line 143:
    env = Environment(tools=['default','qt4', 'msvs'], toolpath=['../', './'], QTDIR=flags_qtdir, QT_LIB='', ENV = os.environ)
  File "/usr/lib/scons/SCons/Environment.py", line 794:
    apply_tools(self, tools, toolpath)
  File "/usr/lib/scons/SCons/Environment.py", line 137:
    env.Tool(tool)
  File "/usr/lib/scons/SCons/Environment.py", line 1340:
    tool(self)
  File "/usr/lib/scons/SCons/Tool/__init__.py", line 157:
    apply(self.generate, ( env, ) + args, kw)
  File "/home/qnuf/Desktop/mixxx-1.6.0beta2/src/qt4.py", line 251:
    QT4_MOC = locateQt4Command(env,'moc', env['QTDIR']),
  File "/home/qnuf/Desktop/mixxx-1.6.0beta2/src/qt4.py", line 234:
    raise "Qt4 command '" + command + "' not found. Tried: " + fullpath1 + " and "+ fullpath2
```


And when i look in that directory 

```

qnuf@mediaction:~/Desktop/mixxx-1.6.0beta2$ cd /usr/share/qt4
qnuf@mediaction:/usr/share/qt4$ ls -a
.  ..  translations
qnuf@mediaction:/usr/share/qt4$ 
```

i'm having all QT4 core packages installed, or should i also install all the dev packages?

---

### Post by GameGod on 2008-03-19
Hi nlz, yes, you need the -dev packages for QT4 installed as well.

---

### Post by nlz on 2008-03-25
hmmmz,

I reinstalled Ubuntu and all my drivers to have direct rendering, but even with portaudio compiled and mixxx running i get a lot of Xruns, even without playing music. I think that means some thing's wrong.

Every one is four/five times i fire up mixxx, i also get this error code:
```

ASSERT: "m_pControlObject" in file src/controlobjectthread.cpp, line 32
```

---

### Post by GameGod on 2008-03-25
Hey nlz,

Ok, that's a bad sign. It looks like there's something fishy going on in beta2. I made a possible bug fix this over the weekend in Mixxx's SVN. Would you be willing to compile the latest version from SVN and report back if you're still experiencing problems?
An easy HOWTO for compiling Mixxx from SVN is here: [http://www.mixxx.org/wiki/doku.php/compiling_on_linux](http://www.mixxx.org/wiki/doku.php/compiling_on_linux)

Thanks!

---

### Post by nlz on 2008-03-26
thanks gg,

i'll be more than happy to try it out! But there is one problem, i can't get the mixxx packages through SVN since there is a hard filter in the proxy server we use at the university for everything with xxx in it. I can use a[ bypass site]("http://www.greenrabbit.org") to visit the site and download from the site, but not through SVN, sorry!

I think it must be a problem in portaudio, because i have no problem when i use mixxx in ALSA. But when i use the slider bar for latency, i get the following error again.

```
ASSERT: "m_pControlObject" in file src/controlobjectthread.cpp, line 32
```

and then mixxx shuts down...

if you post it at another server (none mixxx) i can download it...

---

### Post by jukingeo on 2008-07-17
> **kapello said:**
> not sure about mixxx specifically but I had general problems with xruns and had some success with these settings in JackControl:

Frames/Period: 512
Periods/Buffer: 3

For me, the default of Periods/Buffer 2 seems to give lots of xruns. Setting to 3 doesn't seem to cause me any problems.

Thanx a bunch...this fixed the xrun problem for me, but I had to set my buffers to "4".

Geo

---

