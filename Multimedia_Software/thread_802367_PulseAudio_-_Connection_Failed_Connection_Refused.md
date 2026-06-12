---
title: "PulseAudio - Connection Failed: Connection Refused"
date: 2008-05-21
forum: Multimedia Software
---

### Post by Nexusx6 on 2008-05-21
Hola, I've had this problem since I installed Hardy, and though I have googled and searched for days now, a solution still eludes me. When I run "PulseAudio Device Chooser" and go to "Volume Manger" where I should be able to toggle volume for individual streams, I get this frustrating message: 
> Connection failed: Connection refused

I had found some posts that looked like they might help but all they did was make it so that sometimes after I restart PulseAudio will connect, then randomly later on in the day, it will fail. (posts are [here]("http://ubuntuforums.org/showthread.php?t=776739&highlight=pulse+connection+refused"), and [here]("http://ubuntuforums.org/showthread.php?t=759147&highlight=pulse+connection+refused") for reference)
When I try to restart PA this is what I get:
```
~$ pulseaudio -D
E: main.c: daemon startup failed.

```

I'm almost 100% sure that I've installed every package for PA also. I'm rather tired of restarting my computer just to get PA working for a while :( Any and all help is really appreciated.

**[EDIT]**]I've now been able to isolate and consistently reproduce the problem! After I restart the computer, if I don't first type in
> pulseaudio -D
before playing any sound, then I cannot initialize the daemon the rest of the session, I have to restart the whole system, not just the GUI.  So it seems like PA isn't being initialized on start up, if I can tell KDE or the kernel to fire it up, then I think the problem can be solved. How can I do this?

**[SOLVED]:** I've solved the problem for me, including restarting the PA daemon and have outlined my steps in my blog:
[http://nexsjournal.blogspot.com/2008/05/pulseaudio.html](http://nexsjournal.blogspot.com/2008/05/pulseaudio.html)
Hope it helps someone.

---

### Post by badmotor on 2008-06-15
I'd like to know - getting the exact same problem on my brother's machine with Linux Mint (which is based on Hardy).

---

### Post by Nexusx6 on 2008-06-25
I've solved the problem for me and outlined the steps I took in my blog, including restarting PA on start up:

[http://nexsjournal.blogspot.com/](http://nexsjournal.blogspot.com/)

Hope it solves your problems, email or PM me if you have any questions.

---

### Post by prince_niceguy on 2008-07-03
I was able to solve my pulse audio connection refused by using the code to start the pulse audio. Thank you!!!!

---

### Post by bobpaul on 2008-07-12
I wonder why 'sudo /etc/init.d/pulseaudio restart' does not fix the problem. That should stop pulseaudio if it's still running, and then restart it on its own. I know it doesn't, because I've tried it. ;)

---

### Post by Nexusx6 on 2008-07-13
> **prince_niceguy said:**
> I was able to solve my pulse audio connection refused by using the code to start the pulse audio. Thank you!!!!

Welcome :KS I'm glad I could help someone out

> I wonder why 'sudo /etc/init.d/pulseaudio restart' does not fix the problem. That should stop pulseaudio if it's still running, and then restart it on its own. I know it doesn't, because I've tried it.

Actually, thats a good question lol. I've found that when pulseaudio -D doesn't work on its own (sometimes it spits an error back out) killing the process and then issuing the restart brings the server back to normal working order

```
killall pulseaudio
pulseaudio -D
```

---

### Post by arajah2002 on 2008-09-28
Thanks! I found this very helpful and got my sound to work!

---

### Post by clconway on 2008-10-02
> **bobpaul said:**
> I wonder why 'sudo /etc/init.d/pulseaudio restart' does not fix the problem. That should stop pulseaudio if it's still running, and then restart it on its own. I know it doesn't, because I've tried it. ;)

The [FONT="Courier New"]/etc/init.d/pulseaudio[/FONT] script is configured to do nothing and silently exit by default. This is because PulseAudio is designed to run as a per-user daemon and not a system service. Use '[FONT="Courier New"]pulseaudio -D[/FONT]' to start the daemon instead.

To enable the [FONT="Courier New"]init.d[/FONT] script, edit [FONT="Courier New"]/etc/default/pulseaudio[/FONT] to set [FONT="Courier New"]PULSEAUDIO_SYSTEM_START=1[/FONT]

---

