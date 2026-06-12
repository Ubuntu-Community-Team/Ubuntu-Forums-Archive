---
title: "Pulseaudio and Jack in Jaunty"
date: 2009-04-29
forum: Multimedia Software
---

### Post by martron88 on 2009-04-29
I installed Jaunty fresh and got the realtime kernel going with Jack and ffado (firewire fa-101 sound card).  With the normal permissions settings modifications for firewire and rt I was up and running reasonably well (finally can get a super low latency).  Anyway, since I had pulseaudio routing through jack in Intrepid, I figured I'd do it for Jaunty.

I followed a few guides and posts (which I'll link to later) which helped me troubleshoot.

The initial problem is that module-jack-sink isn't included in Januty.  So, I had to add the following ppa to get the latest version of pulseaudio which includes it:
```
http://ppa.launchpad.net/themuso/ppa/ubuntu/dists/jaunty/main/
```

With that I reinstalled pulseaudio and added module-jack-sink.

Initial tests running jackd with
```
pactl load-module module-jack-sink channels=2
```
created a really unstable system.  Lots of Xruns every few seconds.

So I ran pulseaudio with the -vvv flag.  Found out that the jack sink isn't running in realtime.  So, I started pulseaudio with 
```
pulseaudio -vvv --realtime
```
More problems, apparently pulseaudio doesn't have permissions to run in realtime.  So, do the same thing I did for jack.  Add
```

@pulse-rt - rtprio 99
@pulse-rt - memlock 512000
@pulse-rt - nice -10

```
to /etc/security/limits.conf

I also added myself to the
```
pulse
pulse-rt
pulse-access
```
groups.  Not sure if it's necessary.

It worked!  There are many less xruns now with jack-sink.  However, some are still there.  So, looking through pulseaudio's -vvv messages, I decided that module-suspend-on-idle was kicking in really fast and seemed to be putting a delay to jack audio startup.  So, after loading pulseaudio I tried
```
pactl unload-module module-suspend-on-idle
```
before loading the jack-sink module.

More improvement.  Jack doesn't really xrun anymore and the system feels snappy.

I now have only 1 more problem.  While everything seems to be working quite well Xrun wise, I'm getting hard freezes (I can't move mouse or type on keyboard, but everything is still on screen) of my system after and indeterminate amount of time (somewhere between 1 minute and half an hour) when using pulseaudio with jack.  Usually it's when I'm trying to play from various sources or flash video.  If anyone has tips on how to log the cause of the crash so I can track it down please let me know.  My next step is to save pulseaudio's -vvv output to a file but I'm not sure it'll tell me anything useful. 

I'll report more as I get further with troubleshooting.

Cheers,
-tron

---

### Post by martron88 on 2009-04-29
So I found something in pulseaudio's logs.  It looks like if I set jackd's realtime priority to anything other that (default) and above 14, pulseaudio can't properly set the realtime priority of module-jack-sink.

```

D: module-jack-sink.c: Thread starting up
I: core-util.c: Successfully enabled SCHED_FIFO scheduling for thread, with priority 5.
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
W: module-jack-sink.c: JACK error >cannot use real-time scheduling (FIFO at priority 55) [for thread -1302357104, from thread -1302357104] (1: Operation not permitted)<
I: module-jack-sink.c: JACK thread starting up.
I: core-util.c: Successfully enabled SCHED_FIFO scheduling for thread, with priority 9.

```

core-util seems to manage to set the priority to 9, but that seems the maximum.

This may or may not be my problem with Xruns in pulseaudio.  I'm not sure.  If I run jackd with (default) realtime priority along with pulseaudio's jack sink.  Then I get a Xrun every 1 to 3 minutes.  I'd still like to make it better than that.

---

### Post by markbuntu on 2009-04-29
An xrun every 2-3 minutes could be something else. E-mail checkers are notorious for that.

There is a module-pulse-jack at the debian repos for pulse.0,9.14 and it works with jaunty, I have tested it. But since you are already using 0.9.15 I would not bother if I were you.

For now I have the 2.6.29 kernel and alsa 1.0.19 and pulse0.9.15 on my "bleeding edge" Jaunty Ubutustudio/gnome/kde4.2 64 bit. I have not really got into jack much yet,...

I am waiting for an rt kernel that will boot on my machine...*sigh*...I had to send a screenshot I took with my camera to Launchpad because it freezes up before logging anything.

---

### Post by neu2buntu on 2009-05-01
> More problems, apparently pulseaudio doesn't have permissions to run in realtime.  So, do the same thing I did for jack.  Add
     Code:
     @pulse-rt - rtprio 99
@pulse-rt - memlock 512000
@pulse-rt - nice -10

hi "martron88" i too am having problems with pulse>jack in jaunty,tried upgrading from 8.10 but had far too many bugs ,so clean installed (on acer aspire 1 1.5gb ram)... i am using the pulse jack modules through qjackctl ,but it crashes randomly and has severe xruns ,whereas in 8.10 i had no problems (even on this netbook)....     would you post your /etc/security/limits.conf so i can see how to put "jack" in there....      (not trying to hijack your post ,just want to get my sound as good as the state of 8.10 [and that was without a realtime kernel])


a lot of this is way above my head ,but always get there in the end.......   some more debugging commands that may be usefull(from searching bugs...```
pulseaudio --dump-modules
``` and ```
strace pulseaudio
```(and possibly the verbose flags !!


i have edited a few files already,so probably cant file a bug report ,and also im using a netbook... im not looking for perfection(dont mind a few xruns) i just like to be able to hover over wav/mp3/ogg samples (totem-preview) whilst working in lmms..... i will do my own post soon with all details....   :guitar::guitar: "music____yeah!!!"

---

### Post by neu2buntu on 2009-05-02
```
gksu gedit /etc/pulse/daemon.conf
``` you can change pulseaudio priority.,nice level etc here and use```
 top
``` to see what level/memory/etc the pulse and jack daemons are running at....:guitar:

---

### Post by martron88 on 2009-05-02
thanks for pointing me to daemon.conf.  That might come in handy later on.

I gave up in frustration at ffado's inability to stay alive and freebob's inability to avoid xruns.  So, I figured I'd try ubuntustudio to see if maybe it was better set up for this.

It wasn't (sort of).  After I finally got networking, nvidia etc. working properly I tried jackd and it started giving the same errors as I was seeing with the non-studio jaunty that I had installed.

Now, I've just finished re-installing ubuntustudio again with one major exception.  I've chosen an ext3 partition instead of ext4.  Though I've only been running for an hour, it immediately feels more stable.  Unfortunately I'm not at home this weekend so I can't try out my firewire interface until I get back on Monday.

The limits.conf that ubuntustudio generates adds:
```
@audio          -       rtprio          99
@audio - memlock 615278
```

memlock = 30% of my total memory.

I'll update this when I see improvements/more problems.

---

### Post by martron88 on 2009-05-04
A lot more testing has eventually led me to [https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/366352](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/366352)

I installed the custom kernel linked in that thread and so far (40 minutes or so) I haven't had a freeze while jack is running.  Good sign.  

In fact, ffado seems to have figured out how to use my onboard ricoh firewire chipset without xruns.  Something I've never managed up 'til now.  I finally have actually low latency :)

I'll let you all know if this keeps up.

---

### Post by martron88 on 2009-05-04
The custom rt kernel seems to be a big improvement.

However, the pulseaudio daemon crashes within about 30 minutes of just playing through rhythmbox.  This doesn't crash jackd so it's pretty easy to restart but I'm going to have to figure out what the cause is.  At least I don't have to reboot :)

---

### Post by demios on 2009-07-01
> **martron88 said:**
> A lot more testing has eventually led me to [https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/366352](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/366352)

I installed the custom kernel linked in that thread and so far (40 minutes or so) I haven't had a freeze while jack is running.  Good sign.  

In fact, ffado seems to have figured out how to use my onboard ricoh firewire chipset without xruns.  Something I've never managed up 'til now.  I finally have actually low latency :)

I'll let you all know if this keeps up.


I installed this custom kernel and it runs perfectly -- multitrack with my 1934 firewire interface, recording in ardour and a pd patch running for hours kind of perfect. I think it should get alot more attention, maybe even integrated with ubuntu so that we can get my broadcom and nvidia drivers working with it.

---

### Post by martron88 on 2009-07-01
I guess I forgot to update everyone on how this is going.  I've been running the custom kernel well since the start of May with great success.  I ended up getting rid of Pulseaudio because it just wasn't working out and now I'm quite happy routing all my alsa applications through jack and using my fa-101 for all audio output.

---

### Post by martron88 on 2009-07-01
I always have constant DIO errors when running PD (both extended and Vanilla) with jack under ubuntu.  Do you have any particular set up that seems to work for you?

The DIO gets quite a bit worse when using GEM as well.

---

