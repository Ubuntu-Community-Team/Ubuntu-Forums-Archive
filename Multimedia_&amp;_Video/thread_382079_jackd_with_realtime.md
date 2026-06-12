---
title: "jackd with realtime"
date: 2007-03-11
forum: Multimedia &amp; Video
---

### Post by weatherhead99 on 2007-03-11
Hi all,
I am mainly an opensuse user and I often seem to miss really easy things in ubuntu cos it's just done differently. 

I am having problems starting my JACK server with the realtime checkbox in qjackctl ticked. I've discovered if I start it with sudo then it works, and my XRUNs drop dramatically. I thought it might be that the audio group didn't have realtime privs, but on looking at the groups I found there wasn't even an audio group!! I added this group and added the necessaries to /etc/security/limits.conf as per the ubuntustudio startup guide thing. 

Can anyone tell me why I still need to run jackd (and incidentally any applications I want to connect to JACK) with sudo? I'm sure this is something really obvious that I'm just missing cos I'm one of those nancy-boy YAST addicts. 

I'm running the latest version of feisty

thanks in advance, Dan

---

### Post by jondecker76 on 2007-03-13
It has to do with the kernel - currently, realtime preemption is only available to root - therefore to take advantage of this you will have to sudo jack and all of your other apps which connect to jack. I too find this a bit of a pain.

Also - ubuntustudio ([www.ubuntustudio.org](www.ubuntustudio.org)) is supposed to be out in about a month, with a realtime patched kernel - I'm counting down the days myself.

My advice would be to wait until ubuntustudio launches. Your other options are to either continue running as root (pain), get a patched kernel (vanilla?) which has some bugs and security risks, or run without realtime enabled.

Hope this helps

---

### Post by nlz on 2007-12-04
I just installed the [realtime kernel]("https://wiki.ubuntu.com/RealTime/Gutsy") but still, Jackd only works in root. 
Since we are setting up a radio station, it is not an option to run in root full-time. Does Ubuntu Studio has access to realtime pre-emption as user (non-root) ? 

I also thought the Ubuntu Studio has a low-latency, and not a realtime kernel.

---

### Post by nlz on 2007-12-04
I looked for different possibilities to solve my problem. I found three solutions. You could:

1. Install realtime LSM from synaptic package manager, after that you can build a new kernel as described in usr/share/doc/realtime-lsm

2. Try to fix things with rlimits 

3. Install Ubuntu studio and upgrade to the realtime kernel (if you haven't done if before you upgraded it)

I tried the first two, but they didn't really worked out for me, probably because i wanted a quick succes. Installing Ubuntu studio just preconfigures everything for you. 

Go Go Jack-Ranger.

---

