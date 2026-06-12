---
title: "How to force stop pulseaudio service"
date: 2012-10-04
forum: Multimedia Software
---

### Post by ternyk on 2012-10-04
Hello,

I'm trying to get the proper suspend/resume functionality in my desktop computer (Ubuntu 12.04). It's running MythTV (backend and frontend) with the help of Hauppauge 1300 DVB-T tuner card and doesn't work currently - after the resume myth is reporting that all tuner cards are in use.
To fix it I want to restart myth and tuner modules:
1) stop mythbackend
2) unload all tuner card modules (cx88_dvb, cx88_blackbird, cx88xx, cx88_alsa.. etc) 
and on resume start it again.
But it seems that I cannot unload cx88_alsa because pulseaudio is using it. I've tried ```
sudo service pulseaudio stop
``` but it didn't stop the daemon.
When I edited the /etc/pulse/client.conf and set:
```

autospawn = no
daemon-binary = /usr/bin/true

```
then I could stop the service but after the reboot I haven't got any sound.
So what is the proper way to handle pulseaudio stop?

---

### Post by BicyclerBoy on 2012-10-04
service pulseaudio force-stop 
maybe ??

---

### Post by ternyk on 2012-10-04
> **BicyclerBoy said:**
> service pulseaudio force-stop 
maybe ??

Yes, I know but the same effect - didn't stop the pulseaudio daemon.

---

### Post by BicyclerBoy on 2012-10-04
ps ch -C pulseaudio -o pid

Then using kill on the pid value.

Or start the daemon with option use-pid-file=, then use the value in that file to kill it..
It respawns unless set not to (as you have done)

pasuspender docs mention it is able to do this ?

---

### Post by ternyk on 2012-10-04
> **BicyclerBoy said:**
> ps ch -C pulseaudio -o pid

Then using kill on the pid value.

Or start the daemon with option use-pid-file=, then use the value in that file to kill it..
It respawns unless set not to (as you have done)

pasuspender docs mention it is able to do this ?

Thanks, I'll try this. But I'm thinking that I'm doing it wrong because I have a default per-user pulse audio instance. So that's the reason why stopping it by service pulseaudio stop doesn't work.

I think I need to kill the pulseaudio as you suggested (or by pulseaudio -k, with autospawn=no) but after resume start pulseuadio as a user which was running pulse before suspend (hmmm, how to do it?)

---

### Post by sahabcse on 2012-10-04
run the below command in terminal

killall -9 pulseaudio

or

ps -ax | grep -i pulseaudio

it list the PID value

then run

kill -9 PID

---

### Post by ternyk on 2012-10-04
> **sahabcse said:**
> run the below command in terminal

killall -9 pulseaudio

or

ps -ax | grep -i pulseaudio

it list the PID value

then run

kill -9 PID


Thanks, but how to start pulseaudio again after resume? I suppose that scripts in /etc/pm/suspend/... are run by the root so after resume pulseaudio should be run by something like su - myusername pulseaudio --start? Or maybe should I run start-pulseaudio-x11?

---

### Post by sahabcse on 2012-10-05
type

pulseaudio

in terminal

---

