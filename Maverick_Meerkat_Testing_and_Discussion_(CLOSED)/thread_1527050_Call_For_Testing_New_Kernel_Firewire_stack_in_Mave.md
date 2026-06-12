---
title: "Call For Testing: New Kernel Firewire stack in Maverick"
date: 2010-07-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by phillw on 2010-07-08
Hiyas, the below is from my mailing list. I **have** asked that they make a posting on here, until they do I have subscribed to this thread and will reply to the e-mail. Those who have Firewire, please do check it. No shouting or politics about usb3, just how you get on with firewire :-)

Thanks,

Phill.

> Folks,
  The Ubuntu Kernel Team would like your help testing the new firewire
stack for Maverick. Please let us know the results of your testing via
this e-mail thread.

The new stack is already enabled in the latest Maverick kernel so all
that is needed is the testing at this point. Please note, this is only
for the Maverick kernel. The changes have not been made in Lucid

Further details can be found on the Call for Testing pages of the Kernel
wiki [1].

Thanks!

~JFo

[1] [https://wiki.ubuntu.com/Kernel/Testing/FirewireStack](https://wiki.ubuntu.com/Kernel/Testing/FirewireStack) 

---

### Post by kyleabaker on 2010-07-09
Wish I still had my firewire expansion. Oh well. Hope the testing goes well. ):P

---

### Post by gnomeuser on 2010-07-09
Do we have an data on how many users even have Firewire in use? I worry mostly because getting test coverage might be hard and we should at least try to identify the most used devices.

---

### Post by rhpot1991 on 2010-07-10
Has this been backported to Lucid?  Would make testing easier.

---

### Post by trulan on 2010-07-10
I guess I get to be the first to chime in with an actual test result!  Your post was enough to motivate me to morph one of my Lynx's into a Meerkat - So here we go:  Testing firewire audio with a PreSonus Firepod.

The good:  It just works.  No more annoying permissions errors, just plug it in, set jackd to use the firewire driver, and away you go.

The not-so-good:  Performance has taken a bit of a hit.  Whereas I can run stably at only a few ms latency on Karmic and Lucid, I need about 12 ms latency on the new firewire stack to be reliable.  (This is on the same kernel as I use on Lucid - 2.6.33-rt.  With the generic Maverick kernel it needs even more latency, but that's to be expected.)

**Edit:** With a bit of tweaking, I've been able to squeeze much better performance out of the new firewire stack and ffado 2.0.1.  It's all about xruns (buffer underruns or overruns) when it comes to audio performance.  I'm still seeing more xruns in the 5 ms latency range than I do on the old stack in Lucid or Karmic, but I can actually push it below 1 ms on Maverick, impossible with anything on the old stack.  So I guess things are working better than I expected.

My conclusions:  I'll stick to Lucid for my recording sessions for the time being.  But all in all it looks very promising, and worked with minimal effort.  I'll be staying tuned!

@rhpot1991:  The modules for the new firewire stack are already in Lucid's kernel, they're just blacklisted in modprobe.  To use firewire audio on the new stack in Lucid, you would need to backport the ffado drivers though.

---

### Post by phillw on 2010-07-11
Hi,

I have posted your replies back to the mailing list, thanks for the input :)

Regards,

Phill.

---

### Post by trulan on 2010-07-13
Two more notes for audio users interested in the new firewire stack:

1. On the RT kernel, when using the rtirq script to set irq priorities, you need to have 'firewire' instead of 'ohci1394' in the names list or it will miss your firewire chip.

2. The new stack does not yet support multiple devices.  So I can use one firepod excellently, but to daisychain my second firepod I have to revert to the old stack.

---

### Post by roaldz on 2010-07-15
> **trulan said:**
> I guess I get to be the first to chime in with an actual test result!  Your post was enough to motivate me to morph one of my Lynx's into a Meerkat - So here we go:  Testing firewire audio with a PreSonus Firepod.

The good:  It just works.  No more annoying permissions errors, just plug it in, set jackd to use the firewire driver, and away you go.

The not-so-good:  Performance has taken a bit of a hit.  Whereas I can run stably at only a few ms latency on Karmic and Lucid, I need about 12 ms latency on the new firewire stack to be reliable.  (This is on the same kernel as I use on Lucid - 2.6.33-rt.  With the generic Maverick kernel it needs even more latency, but that's to be expected.)

**Edit:** With a bit of tweaking, I've been able to squeeze much better performance out of the new firewire stack and ffado 2.0.1.  It's all about xruns (buffer underruns or overruns) when it comes to audio performance.  I'm still seeing more xruns in the 5 ms latency range than I do on the old stack in Lucid or Karmic, but I can actually push it below 1 ms on Maverick, impossible with anything on the old stack.  So I guess things are working better than I expected.

My conclusions:  I'll stick to Lucid for my recording sessions for the time being.  But all in all it looks very promising, and worked with minimal effort.  I'll be staying tuned!

@rhpot1991:  The modules for the new firewire stack are already in Lucid's kernel, they're just blacklisted in modprobe.  To use firewire audio on the new stack in Lucid, you would need to backport the ffado drivers though.
Interesting..
I'm on a macbook 4.1, recently installed ubuntustudio 10.04, and I did everything to get xrun-free performance, but with no luck. Almost every rt or realtime kernel (ubuntu repos, falktx's repo) didn't give me the xrun free performance i'm looking for.
I'm used to 64studio, which gave me <1ms latency, xrun-free.
I want to use ubuntustudio because i'm just used to ubuntu, the desktop effects and laptop support.

I've configured rtirq.conf and gave the right permissions to /dev/raw1394..

What's your setup? Can you give me any advice?

Thanks!

Roald

---

### Post by trulan on 2010-07-15
> **roaldz said:**
> Interesting..
I'm on a macbook 4.1, recently installed ubuntustudio 10.04, and I did everything to get xrun-free performance, but with no luck. Almost every rt or realtime kernel (ubuntu repos, falktx's repo) didn't give me the xrun free performance i'm looking for.
I'm used to 64studio, which gave me <1ms latency, xrun-free.
I want to use ubuntustudio because i'm just used to ubuntu, the desktop effects and laptop support.

I've configured rtirq.conf and gave the right permissions to /dev/raw1394..

What's your setup? Can you give me any advice?

Thanks!

Roald
My setup? That's not a simple question...
Laptop: Dell E5500,  AVlinux and Ubuntu Lucid.  Nothing but RT kernels.  Used the repos one, Falk's kernel, the default AVLinux kernel, and various custom builds of 2.6.33-rt.  They all work about the same....The only thing unique about my setup (other than the usual rtirq and permissions settings) is that I have to turn my wireless card off because it's on the same irq as my firewire card, and ffado at low latencies is quite greedy and refuses to share.
Desktop:  HP a1410n, Ubuntu Karmic, Maverick (formerly Lucid), and AVLinux.  Too many kernels to list here.  Nothing at all special about the setup that I know of.
Firewire gear: Two PreSonus Firepods, onboard Agere firewire chip (desktop), onboard Ricoh firewire chip (laptop).

Advice?  Check for irq conflicts, especially if you're on a different machine than you ran 64studio on.  And look at all the processes running and see what you can eliminate - Ubuntu tends to have a few too many 'convenience' processes and daemons running for good stable audio work.

Or, install Maverick and test the new firewire stack?  It does use a little less cpu power - but Maverick uses jackdmp (jack2) so that adds yet another twist...

---

