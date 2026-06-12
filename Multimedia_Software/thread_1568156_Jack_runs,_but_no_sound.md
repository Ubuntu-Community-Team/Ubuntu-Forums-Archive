---
title: "Jack runs, but no sound"
date: 2010-09-04
forum: Multimedia Software
---

### Post by MegaLoler on 2010-09-04
Jack runs, but I can't get sound to play through it.  Another thing that happens is when I launch jack, all audio in the system, whether its connected to jack or not, goes off.  There are no errors or anything in the messages window.  And I checked to see if it was connected to the correct interface.  I have a mac mini and I run ppc lucid lynx.  The system does detect my hardware, and its not muted.  All I want to do is use MusE.  Is there maybe anyway to run MusE without jack?

---

### Post by MegaLoler on 2010-09-04
Okay so i found out that all the audio shuts off when the JACK control program is running, whether actual jackd is running or not.  I also found that i dont know how to start jack from the command line.

This is what i get when i run "jackd" in the command line:

jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    383205
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


usage: jackd [ --no-realtime OR -r ]
             [ --realtime OR -R [ --realtime-priority OR -P priority ] ]
      (the two previous arguments are mutually exclusive. The default is --realtime)
             [ --name OR -n server-name ]
             [ --no-mlock OR -m ]
             [ --unlock OR -u ]
             [ --timeout OR -t client-timeout-in-msecs ]
             [ --port-max OR -p maximum-number-of-ports]
             [ --debug-timer OR -D ]
             [ --no-sanity-checks OR -N ]
             [ --verbose OR -v ]
             [ --clocksource OR -c [ c(ycle) | h(pet) | s(ystem) ]
             [ --replace-registry ]
             [ --silent OR -s ]
             [ --version OR -V ]
             [ --nozombies OR -Z ]
         -d backend [ ... backend args ... ]
             Available backends may include: alsa, dummy, freebob, firewire, net, oss, sun, or portaudio.

       jackd -d backend --help
             to display options for each backend


/etc/limits.conf did not exist, so i created it and added the line that it wanted, but i got the same thing when i tried to start jack.

---

### Post by MegaLoler on 2010-09-04
I found out that there is more to the command than just "jackd" :P
this is what JACK control runs:
  [COLOR=Black][COLOR=#990099]/usr/bin/jackd -r -m -dalsa -dhw:0 -r44100 -p1024 -n2 -P[/COLOR][/COLOR]
[COLOR=#990099][COLOR=Black]I ran that[/COLOR] [COLOR=Black]in terminal and it said that another application was using that interface.  I assume that that is why JACK control mutes all of the system audio.  So I quit rhythm box and tried again, and it worked.  Maybe MusE is the problem?  maybe muse wont play the audio?  But i cant test it, because I dont know how to get audacity to play through JACK.  I tried setting it from alsa to jack but it just gave an error[/COLOR]
[/COLOR]

---

### Post by lidex on 2010-09-05
Have a look here:
[http://ohioloco.ubuntuforums.org/showthread.php?t=843012](http://ohioloco.ubuntuforums.org/showthread.php?t=843012)
Scroll down to this section - 'Ubuntu Studio and Jack'

---

