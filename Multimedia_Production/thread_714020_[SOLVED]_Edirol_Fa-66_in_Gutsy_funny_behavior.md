---
title: "[SOLVED] Edirol Fa-66 in Gutsy: funny behavior"
date: 2008-03-03
forum: Multimedia Production
---

### Post by revol on 2008-03-03
Hello, I'm posting this to help everybody uses an Edirol FA-66 firewire audio interface (maybe other freebob/ffado supported devices?) in Gutsy. To begin with, I used this inteface with Feisty and I didn't have this strange behavior.
After initial set-up, described [[COLOR="DarkOrange"]here[/COLOR]]("https://help.ubuntu.com/community/UbuntuStudioPreparation") (remembering to look at 'Firewire (ieee1393 / raw1394) sound cards and cameras' section), I started with Jack set-up. Everything appeared nice, better than in Feisty (more stable, better tollerance against x-runs), except one thing: the cpu usage, that was too high even if I was not using music software. This caused that I was unable to run old project done with Feisty, when such projects were using a discete component of my cpu, because in gutsy this cpu usage went over the max (causing often system freezing):(.
I'm a musician, so I really need low latency responce between In and Out analog signal.
My old settings for Jack (Qjackctl):
Realtime: Enabled --- Priority: 70
No Memory Lock: Disabled --- Frames/Period: 64
Unlock Memory: Disabled --- Sample Rate: 48000
Periods/Buffer: 3

With a resulting Latency of: 4 msec

The response between analog input and output, connecting them directly throught Connections panel of qjackctl, was optimum (no audible latency) but my cpu became strangely too stressed, causing the impossibility to process realtime signals like I was able to in Feisty. Here is the strange thing: tryng different solutions to this problem I found this inusual workaround: even setting up Jack with higher latencies, I have the same realtime response, with lower cpu usage!
My actual settings:
Realtime: Enabled --- Priority: 70
No Memory Lock: Disabled --- Frames/Period: 512
Unlock Memory: Disabled --- Sample Rate: 48000
Periods/Buffer: 3

With a resulting Latency of: 32 msec

32 ms of latency should be to much to feel a real time response (in my experience), but it is not! The response is like the old set-up! Now I can use the same processing power I had in Feisty...:)

Is this a Jack problem?

---

