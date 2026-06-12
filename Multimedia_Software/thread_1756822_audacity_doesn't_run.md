---
title: "audacity doesn't run"
date: 2011-05-12
forum: Multimedia Software
---

### Post by david.medine on 2011-05-12
I am running a recent install of Natty on an AMD64 and I have attempted to install audacity in the conventional way (sudo apt-get install audacity) but the damn thing doesn't run.  Here is what my terminal tells me when I type 'audacity':

 ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
audacity: symbol lookup error: audacity: undefined symbol: Pa_GetStreamHostApiType

In general sound works fine on my machine. I run pd a lot and I write my own audio code in C using port audio as an API. It looks like Audacity is having trouble with portaudio, though due to the 'undefined symbol: Pa_GetStreamHostApiType' as that is a portaudio call. I have tried installing audacity from source but it complains that it needs wxWidgets version 2.4 (wxWidgets are up to 2.8 already) which is also very mysterious.

Anyone else have trouble with audacity on Natty?

---

### Post by mc4man on 2011-05-12
> I have tried installing audacity from source but it complains that it needs wxWidgets version 2.4 (wxWidgets are up to 2.8 already) which is also very mysterious.

Whether building is going to help don't know (audacity works fine here but don't use port

Maybe your trying to build the 1.2.6 version which would need the older wx libs, ubuntu uses, (and has for quite some time) the 1.3.X source

---

### Post by david.medine on 2011-05-13
You are right, I did have the older version. I am attempting to build 1.3.13, but am now having this error:

checking for wx-config... /usr/local/bin/wx-config

  Warning: No config found to match: /usr/local/bin/wx-config --unicode=yes --version
           in /usr/local/lib/wx/config
  If you require this configuration, please install the desired
  library build.  If this is part of an automated configuration
  test and no other errors occur, you may safely ignore it.
  You may use wx-config --list to see all configs available in
  the default prefix.

configure: Checking that the chosen version of wxWidgets is 2.8.x
configure: error: Unable to locate a suitable configuration of wxWidgets v2.8.x or higher.
The currently available configurations are listed below.  If necessary, either
install the package for your distribution or download the latest version of
wxWidgets
from [http://wxwidgets.org](http://wxwidgets.org).

    Default config is gtk2-ansi-release-2.8

  Default config will be used for output

It seems like the wx and gtk2 libraries are in the right place (/usr/local/lib) but audacity's configure is not happy. I was poling around the web for any info on gtk2-ansi-release-2.8 and that seems to be correct also.

---

### Post by mc4man on 2011-05-13
Not sure why your wx-conf and related libs are in /usr/local unless you manually installed them?

Because natty uses 1.3.X, a sudo apt-get build-dep audacity would provide all that's needed
You may want to do that (get rid of /usr/local install

Something to keep in mind - if there are multiple versions of wx* libs installed then wx-config is set as an alternative, likely last installed is the default.

Can be ck.ed or switched here (showing my current where only 2.8 is installed, the way set is preferred in most cases (gtk2
```
~$ sudo update-alternatives --config wx-config
There are 2 choices for the alternative wx-config (providing /usr/bin/wx-config).

  Selection    Path                                         Priority   Status
------------------------------------------------------------
* 0            /usr/lib/wx/config/gtk2-unicode-release-2.8   288       auto mode
  1            /usr/lib/wx/config/base-unicode-release-2.8   287       manual mode
  2            /usr/lib/wx/config/gtk2-unicode-release-2.8   288       manual mode

Press enter to keep the current choice[*], or type selection number:

```

---

### Post by CVGH on 2011-05-13
Have you tried the nightly builds ppa?
```
sudo add-apt-repository ppa:audacity-team/daily

```

---

### Post by wd5gnr on 2011-07-12
I am having this same problem. When I start audacity it dies with:

audacity: symbol lookup error: audacity: undefined symbol: Pa_GetStreamHostApiType

Used to work. Very embarrassing as my wife is wanting me to put some music on a CD for a niece's wedding!

I've tried the daily build, reinstall PortAudio, etc. No go.

Any ideas?

---

### Post by CVGH on 2011-07-12
I would go here and ask:
[http://forum.audacityteam.org/](http://forum.audacityteam.org/)

---

### Post by wd5gnr on 2011-07-24
Ok I figured it out. Hopefully this will help someone else.

I do development on this machine and at some point in the past I apparently installed my own version of portaudio in /usr/local/lib! 

Audacity wanted the "official" version (apparently I turned off some API when I built mine). 

I figured this out by doing this:

ldd /usr/bin/audacity | grep portaudio

I noticed the lib was coming from /usr/local/lib

So the answer was to remove the custom version, do an ldconfig, and Audacity is back! Woo hoo!

---

### Post by david.medine on 2011-07-27
Way to be, wd5gnr!

I just started looking at this again after a hiatus as I am in a place where not having audacity is a real inconvenience.

I confess that I don't yet understand how to fix this, but if this is the root of the problem, then it is only a matter of time. I have now got the 'official' portaudio libs (I think), but they are still alluding audacity. I can figure out how to deal with ldconfig (I should probably know how to do this anyway), but if you are feeling generous, you could post a step by step maybe?   ;)

---

### Post by david.medine on 2011-07-27
OK, so that was pretty easy.

The details of the fix are thus:

1. get the 'official' portaudio libraries into /usr/lib -- I just used the synaptic package manager to do this, look for libportaudio.dev

2. run this bit of code from root 
```

> sudo rm /usr/local/lib/libportaudio.* 

```actually, I moved the files to another directory just to be on the safe side, but all my audio is running fine, so I think I am in the clear

3. do the ldconfig thing
```

> ldconfig -n /usr/lib

```I wonder if that third step is necessary? Anyway that's what I did and audacity works like a charm now.

Thanks wd5gnr!

---

