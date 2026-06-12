---
title: "Sharing my Jack/Alsa setup"
date: 2007-07-04
forum: Multimedia &amp; Video
---

### Post by fackamato on 2007-07-04
Hi guys

I just wanted to share my jackd/alsa setup. The way I have it set up now is that with qjackctl, I have enabled a jack server, and with .asoundrc ( or /etc/asound.conf if you wish) I redirect all alsa output to jack. This way I can have multiple alsa sources playing at the same time, while also running jack application, and it is all very synched :) (I don't know how to benchmark the synch, but playing several movies at once etc works flawlessy).

Here is my .asoundrc:

```
  pcm.jack {
                type jack
                playback_ports {
                        0 alsa_pcm:playback_1
                        0 alsa_pcm:playback_2
                        0 alsa_pcm:playback_3
                        0 alsa_pcm:playback_4
                        0 alsa_pcm:playback_5
                        1 alsa_pcm:playback_6
                }
                capture_ports {
                        0 alsa_pcm:capture_1
                        1 alsa_pcm:capture_2
                }
        }

pcm.!default {
                type plug
                slave { pcm "jack" }
        }

        pcm.jack {
                type jack
                playback_ports {
                       0 alsa_pcm:playback_1
                       1 alsa_pcm:playback_2
               }
                capture_ports {
                       0 alsa_pcm:capture_1
                        1 alsa_pcm:capture_2
                }
        } 

```

Except all the ordinary jack packages (along with qjackctl) there is one more package that you need to install, libasound2-plugins. **However**, the version shipped with Feisty has got jack support *disabled* because it build depends on a package in multiverse, and you can't have a package in main which builddepends on something in multiverse I have learned. Therefore we shall rebuild the package with jack output support ourselves:

```
apt-get install build-essential devscripts
apt-get build-dep libasound2-plugins && apt-get install libjack-dev && apt-get source libasound2-plugins
```

Now edit alsa-plugins-1.0.13/debian/control and add libjack-dev to the Build-Depends-line like this:

```
Build-Depends: debhelper (>= 5.0.37), dpatch, autotools-dev, libjack-dev, libasound2-dev (>=1.0.12), libpulse-dev, libsamplerate0-dev | libsamplerate-dev
```

Now go tp alsa-plugins-1.0.13/  and do:

```
debuild -uc -us
```

After it has been built, install it like:

```
dpkg -i ../libasound2-plugins_1.0.13-3ubuntu1_i386.deb
```

Now log in and out and/or restart alsa ( sudo /etc/init.d/alsa-utils restart ) and set up qjackctl. I have it set up like this:

```
Realtime enabled
Frames/Period: 256
Sample rate: 48000
Interface: (default)
```

Oh that's right, you need to change some settings before starting jack to be able to use realtime with jack (at least when running the stock/low-latency kernel):

```
sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - memlock 250000 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'
```

(kindly stolen from [http://ubuntuforums.org/showthread.php?t=447915](http://ubuntuforums.org/showthread.php?t=447915)) :)

Now start jack from qjackctl, check messages to see that everything is alright. Now open some application that uses alsa (you can even start esd at this point if it is configured to use alsa, it will work (unless something is wrong :P), however I don't use esd myself because I didn't experience it to be fully stable in this kind of configuration) and play a movie clip or some tune, open another program and do the same. Click connect in the JACK Audio Connection Kit (qjackctl) to see what's going on :).

Now it should work! If you have any question, please don't hesitate to ask.

Credits also go to crimsun @ #ubuntustudio @ freenode for helping me with this. Thanks!

**edit:** Here is a screenshot of the whole thing: [http://tinyurl.com/2hy3jx](http://tinyurl.com/2hy3jx)

---

### Post by fackamato on 2007-07-05
I uploaded the package so you don't have to recompile it yourself :), just install this: [http://files-upload.com/350747/libasound2-plugins_1.0.13-3ubuntu1_i386..deb.html](http://files-upload.com/350747/libasound2-plugins_1.0.13-3ubuntu1_i386..deb.html) .

Note that the update manager will try to "update" our new libasound, because the version number is the same as in the repo (I think this is a bug with apt or something), just don't update it and you'll be ok.

---

### Post by Bartisimo on 2007-07-05
Hello,
It does not work for me.

I am new to this but these are my messages:


15:37:12.510 Patchbay deactivated.
15:37:12.521 Statistics reset.
15:37:12.557 MIDI connection graph change.
15:37:12.726 MIDI connection change.
15:37:21.202 Startup script...
15:37:21.202 artsshell -q terminate
can't create mcop directory
Creating link /home/ad/.kde/socket-ubuntu.
15:37:21.435 Startup script terminated with exit status=256.
15:37:21.437 JACK is starting...
15:37:21.439 jackd -R -dalsa -dhw:0 -r48000 -p128 -n2
15:37:21.442 JACK was started with PID=17035 (0x428b).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|128|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
15:37:21.569 JACK was stopped successfully.
15:37:21.571 Post-shutdown script...
15:37:21.572 killall jackd
jackd(6384): Operation not permitted
jackd: no process killed
15:37:21.785 Post-shutdown script terminated with exit status=256.
15:37:23.585 Could not connect to JACK server as client. Please check the messages window for more info.

---

### Post by fackamato on 2007-07-05
Have you disabled the sound server? (esd)

It locks the device. Disable it in System > Preferences > Sound > Sound and untick the ESD box.

When you start jack after that, you can tick it again and esd will start and output through JACK **however** I've found it to be extremely unstable (the JACK server crashes sometimes when esd is active and in use). I don't use esd :), everything I uses goes directly through JACK or via jacklaunch (wraps alsa to JACK), or, automatically "just works" by the .asoundrtc configuration.

---

### Post by Bartisimo on 2007-07-06
Thank you for the reply.

I will try this out as soon as I can

---

### Post by Batuhan on 2007-08-24
Thanks for this info! I use a fasttrack pro usb card and tried your solution. Because I want Jack to be started all the time(as the software I mostly use depends on jack) but I want to be able to use native alsa apps at the same time so connecting them all to jack is a great option.

However things don't work as expected.

After following your tut;

I play a video with mplayer, it starts fine, i hear the sound and see the connection in jack, but then mplayer freees in 2-3 seconds then dies.

Totem player works fine, I can see the connection and it plays fine. I can live with totem.

But, in firefox, I go to youtube.com and once a movie starts playing, a loop occurs, new connections added to jack connections graph continuously(numbers incrementing in connection name), I mean hundreds of new input devices here, until jack blows up and dies. I tried to use firefox with aoss but the same thing.

To summarise: I want to use jack with other alsa software at the same time. What can I do do improve the situation?

Any advices on this? 

Thanks!

---

### Post by Batuhan on 2007-08-26
Anyone?

I actually wanted to be able to run any number of alsa enabled applications at the same time, and partially achieved it. 

I'm just not sure about Jack. I use Jack from alsa backend too, but if I start jack, all my applications that use alsa stop making sounds. Is this normal? I don't really have to have all those applications connected to Jack patchbays(as this option is very buggy at the moment). It is fine if I can use Jack and alsa enabled applications at the same time(without them being connected to jack).

Any advices on this?

---

### Post by HellMind on 2007-10-28
Your config is wrong
why you got  2 
pcm.jack  ?



> **fackamato said:**
> Hi guys

I just wanted to share my jackd/alsa setup. The way I have it set up now is that with qjackctl, I have enabled a jack server, and with .asoundrc ( or /etc/asound.conf if you wish) I redirect all alsa output to jack. This way I can have multiple alsa sources playing at the same time, while also running jack application, and it is all very synched :) (I don't know how to benchmark the synch, but playing several movies at once etc works flawlessy).

Here is my .asoundrc:

```
  pcm.jack {
                type jack
                playback_ports {
                        0 alsa_pcm:playback_1
                        0 alsa_pcm:playback_2
                        0 alsa_pcm:playback_3
                        0 alsa_pcm:playback_4
                        0 alsa_pcm:playback_5
                        1 alsa_pcm:playback_6
                }
                capture_ports {
                        0 alsa_pcm:capture_1
                        1 alsa_pcm:capture_2
                }
        }

pcm.!default {
                type plug
                slave { pcm "jack" }
        }

        pcm.jack {
                type jack
                playback_ports {
                       0 alsa_pcm:playback_1
                       1 alsa_pcm:playback_2
               }
                capture_ports {
                       0 alsa_pcm:capture_1
                        1 alsa_pcm:capture_2
                }
        } 

```

Except all the ordinary jack packages (along with qjackctl) there is one more package that you need to install, libasound2-plugins. **However**, the version shipped with Feisty has got jack support *disabled* because it build depends on a package in multiverse, and you can't have a package in main which builddepends on something in multiverse I have learned. Therefore we shall rebuild the package with jack output support ourselves:

```
apt-get install build-essential devscripts
apt-get build-dep libasound2-plugins && apt-get install libjack-dev && apt-get source libasound2-plugins
```

Now edit alsa-plugins-1.0.13/debian/control and add libjack-dev to the Build-Depends-line like this:

```
Build-Depends: debhelper (>= 5.0.37), dpatch, autotools-dev, libjack-dev, libasound2-dev (>=1.0.12), libpulse-dev, libsamplerate0-dev | libsamplerate-dev
```

Now go tp alsa-plugins-1.0.13/  and do:

```
debuild -uc -us
```

After it has been built, install it like:

```
dpkg -i ../libasound2-plugins_1.0.13-3ubuntu1_i386.deb
```

Now log in and out and/or restart alsa ( sudo /etc/init.d/alsa-utils restart ) and set up qjackctl. I have it set up like this:

```
Realtime enabled
Frames/Period: 256
Sample rate: 48000
Interface: (default)
```

Oh that's right, you need to change some settings before starting jack to be able to use realtime with jack (at least when running the stock/low-latency kernel):

```
sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - memlock 250000 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'
```

(kindly stolen from [http://ubuntuforums.org/showthread.php?t=447915](http://ubuntuforums.org/showthread.php?t=447915)) :)

Now start jack from qjackctl, check messages to see that everything is alright. Now open some application that uses alsa (you can even start esd at this point if it is configured to use alsa, it will work (unless something is wrong :P), however I don't use esd myself because I didn't experience it to be fully stable in this kind of configuration) and play a movie clip or some tune, open another program and do the same. Click connect in the JACK Audio Connection Kit (qjackctl) to see what's going on :).

Now it should work! If you have any question, please don't hesitate to ask.

Credits also go to crimsun @ #ubuntustudio @ freenode for helping me with this. Thanks!

**edit:** Here is a screenshot of the whole thing: [http://tinyurl.com/2hy3jx](http://tinyurl.com/2hy3jx)

---

