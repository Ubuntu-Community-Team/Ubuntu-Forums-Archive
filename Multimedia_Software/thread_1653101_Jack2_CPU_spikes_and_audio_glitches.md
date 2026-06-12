---
title: "Jack2 CPU spikes and audio glitches"
date: 2010-12-26
forum: Multimedia Software
---

### Post by dewdrop_world on 2010-12-26
Starting here with this question, though I'm not sure if this is the right board. Mods, feel free to move the thread if appropriate.

I switched over to Jack2 a couple of weeks ago and I like the fact that an xrun doesn't mean instant death to the client. But I'm a bit disturbed by one strange behavior. Occasionally qjackctl reports a large spike in CPU usage for DSP. Even when clients are mostly idle (that is, SuperCollider has just a couple of active synth nodes, doing nothing more than panning and level scaling), this still happens periodically. The result is a glitch in the audio output.

It seems to be more frequent when some program is using the network.

I discussed this over on linuxmusicians just after installing Jack2, and they said the priority of Jack's real-time thread was too low and other threads were probably blocking it. So I raised it -- now it's 72, set in qjackctl and verifiable by ps.

```
ps -Leo class,comm,rtprio | grep jackd
TS  jackdbus             -
TS  jackd                -
TS  jackd                -
FF  jackd               72
TS  jackd                -
```

But the issue still occurs.

The other thing they told me to do is to use Jack2 in synchronous mode: jackd -S etc. That helped insofar as it stopped Jack messages from filling up the SuperCollider console output, but it didn't stop the CPU spikes or the glitches.

I also wrote a little piece of code to get the first few lines of 'top' output when SC detected a spike. Overall CPU use in the system is far below Jack's DSP statistic when a spike happens.

I can deal with the glitches when I'm composing at home, but it's not good in a live performance situation. Disabling the network interface is also not the answer -- my current project involves communication with other machines by UDP packets. (Though, even in that case, I can disable Internet connectivity and stick to a local router.)

Basically, I want to find out what other (kernel?) processes have higher priority, and bring the priority down if possible.

Advice?

TIA,
James

---

### Post by dewdrop_world on 2010-12-26
Oh hello, actually there's a boatload of high-priority stuff.

```
ps -Leo class,comm,rtprio | grep -E [^-]$
CLS COMMAND         RTPRIO
FF  migration/0         99
FF  watchdog/0          99
FF  migration/1         99
FF  migration/2         99
FF  migration/3         99
FF  migration/1         99
FF  migration/2         99
FF  migration/3         99
RR  rtkit-daemon        99
FF  migration/1         99
FF  migration/2         99
FF  migration/3         99
FF  migration/1         99
FF  migration/2         99
FF  migration/3         99
FF  migration/1         99
FF  migration/2         99
FF  migration/3         99
FF  migration/1         99
FF  migration/2         99
FF  migration/3         99
FF  migration/1         99
FF  watchdog/1          99
FF  migration/2         99
FF  watchdog/2          99
FF  migration/3         99
FF  watchdog/3          99
```

So... how do I control it, make these bad boys chill out?

James

---

### Post by cchhrriiss121212 on 2010-12-26
> Basically, I want to find out what other (kernel?) processes have higher priority, and bring the priority down if possible.

Advice?
I would just raise jack's rtprio up to 99 rather than lowering all the others. All the jack tutorials I have seen recommend at least a value of 90.

---

### Post by dewdrop_world on 2010-12-26
> **cchhrriiss121212 said:**
> I would just raise jack's rtprio up to 99 rather than lowering all the others. All the jack tutorials I have seen recommend at least a value of 90.

Nope, that didn't help. (BTW qjackctl doesn't allow a priority higher than 89! So I hacked up my own sh script to start it at the command line.)

I got a suggestion elsewhere to turn off CPU frequency scaling (and SMT and turbo boost, but I didn't see those options in the bios). That hasn't eliminated the spikes but it's made them smaller and less frequent (or at least they seem to happen as often).

As far as I can tell, SMT aka hyperthreading is enabled, but I hear that can be detrimental to real-time audio.* I see some old forum threads about enabling hyperthreading, but nothing explaining how to disable it. Does anyone know?

* [http://comments.gmane.org/gmane.comp.audio.supercollider.devel/31165](http://comments.gmane.org/gmane.comp.audio.supercollider.devel/31165)

> for low-latency applications, i strongly suggest to disable hyperthreading: it 
may increase throughput, but at the cost of latency. some time ago, i have done 
some benchmarks on the effects of hyperthreading on the scheduling latency of 
the os. it was raising the worst-case latency by about 250 microseconds. (for a 
block-size of 64 samples at 44100hz, it would reduce the performance in the 
worst case by about 20%).

btw, i doubt that hyperthreading will speed up any number-crunching application. 
from my understanding, it is better suited for server/database workloads.Thanks,
James

---

### Post by cchhrriiss121212 on 2010-12-27
I thought jack used the rtprio value set in audio.conf?

Hyperthreading should be available as an option in your BIOS, you might need to update it to get the option, but it will depend on your mobo.

---

### Post by dewdrop_world on 2010-12-27
> **cchhrriiss121212 said:**
> I thought jack used the rtprio value set in audio.conf?

Perhaps it does from the command line. But, qjackctl has a box for  priority that is limited to 89. When you start Jack by qjackctl, it  appears to overwrite .jackdrc with the latest setup options and the  command line in this file includes the -P switch. I had been using  qjackctl to run a post-startup script.

It seems to be impossible to set priority to (default) in qjackctl.

> Hyperthreading should be available as an option in your BIOS, you might need to update it to get the option, but it will depend on your mobo.Yeah, it's not there. I just took the question to the hardware manufacturer's forum.

Thanks,
James

---

### Post by cchhrriiss121212 on 2010-12-28
> 
It seems to be impossible to set priority to (default) in qjackctl.I have mine set to (default), what happens if you try entering it?

Edit: scratch that, it seems that setting it to default gives an rtprio of 10.

Further edit:
According to [here]("http://ubuntuforums.org/showthread.php?t=706183") and [here]("http://manpages.ubuntu.com/manpages/hardy/man2/rtprio.2.html"), a *lower* rtprio value means a higher priority, so I think this setting is not the issue here.

---

### Post by dewdrop_world on 2010-12-28
Oh, interesting. I was basing my setting on some hearsay from the linuxmusicians forum. I'm trying with a lower priority number now.

The spike appears to occur most often when the OS is opening a connection to a remote server -- usually I see it with HTTP, but I've also seen it when my IMAP client is trying to connect to the mail server (that is, I leave the client alone for a while and it closes the old connection -- then when I update, it opens a new connection and can spike at that time). Strange that an activity that does not need to be real-time can interfere with real-time processes...

Thanks,
James

---

