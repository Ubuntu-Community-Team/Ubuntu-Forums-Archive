---
title: "PulseAudio Loses HDMI Sink After TV Powered Off"
date: 2012-08-25
forum: Multimedia Software
---

### Post by TroyDowling on 2012-08-25
Hello, hopefully this hasn't been solved before. I did some searching and nothing really applied to my problem.

I have an Ubuntu-based HTPC connected to my TV via HDMI for both picture and sound. The PC is running PulseAudio and, to my knowledge, is configured properly.

The problem is that, if I turn the TV on and power/reboot the server, everything works. However, if I turn the TV off and on again later, sound ceases to work. I believe this to be because PA loses the HDMI sink when the TV is powered off and fails to see it again when the TV comes back online.

I.e., when looking at the output of 'pacmd list-cards' when everything is working properly:

```

1) On-board sound card (incorrect option)
2) PCI sound card (incorrect option)
3) HDMI sound via my Radeon 5700 series (the option I want!)

```

But, after a TV power cycle, option #3 is no longer present and PA seemingly has defaulted over to one of the other options.

Solutions. Ideally, I would like to find a way to correct this behaviour so that sink #3 is not lost between TV power cycles. If this is not possible, I've been working on a second solution that involves using cron to set the correct sound setting every minute ('pactl set-card-profile 2 output:hdmi-stereo'). This second solution does not work however because PA does not re-register the HDMI sink after the TV turns back on.

So, essentially, I'm looking for advice either stopping PA from losing the correct sound sink between TV power cycles, or failing that, looking for help with the minutely cron script which sets the setting back to the correct state/card/output.

Thank you,

Troy.

---

### Post by Fredo on 2012-09-24
I have the same issue with my HTPC running Ubuntu 12.04. It has an AMD Radeon HD 6320 graphics card.

I even loose HDMI audio when I switch from PC to internal TV receiver and back to PC on the TV. I have to log out and back in again to re-gain HDMI audio output.

Any help would be appreciated. :-)

---

### Post by TroyDowling on 2012-09-24
Yeah, I'm still waiting on a solution. I discovered today though, that if I unplug and replug the HDMI cable, sound is restored quicker than a reboot. This must mean that PA dynamically polls for devices on a certain event. I just don't have any experience with PA to know how to ultilize that behaviour.

---

