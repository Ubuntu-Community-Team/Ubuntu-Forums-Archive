---
title: "PulseAudio only working in one direction over network"
date: 2011-08-06
forum: Multimedia Software
---

### Post by pyraz on 2011-08-06
I'm trying to use PulseAudio to forward audio from my laptop to my MediaCenter, which is of course hooked up to my home stereo. Both systems are running Ubuntu 11.04. While I set up my laptop much longer ago, to the best of my recollection they have PulseAudio set up the same way, with the same applications (ie. padevchooser, pavucontrol, paprefs, etc.) and same settings. However, it only works to send audio from the MediaCenter to my laptop. It's great to see the network functionality working, but the audio is going the wrong way! I can't make it work in reverse.

For testing purposes, I enabled the following setting on BOTH computers:
[LIST]
[*]Network Access > Make discoverable PulseAudio network sound devices available locally
[*]Network Server > Enable network access to local sound devices
[*]Network Server > Allow other machines on the LAN to discover local sound devices
[*]Network Server > Don't require authentication
[/LIST]

This produced the following screens:
On the Laptop:
[IMG]http://dl.dropbox.com/u/244184/Laptop-1.png[/IMG]
And
[IMG]http://dl.dropbox.com/u/244184/Laptop-2.png[/IMG]

On the MediaCenter:
[IMG]http://dl.dropbox.com/u/244184/MediaCenter1.png[/IMG]
And
[IMG]http://dl.dropbox.com/u/244184/MediaCenter2.png[/IMG]

As you can see, the laptop is visible in the "Playback" section locally, and in the "Output" section on the MediaCenter. However, despite the MediaCenter having the exact same settings, it is not visible in it's "Playback" section, nor on the "Output" section of the laptop.

The MediaCenter is plugged into my router, while my laptop is on WiFi. The MediaCenter has a static IP, while my laptop has dynamic. I can ssh into the MediaCenter without a problem from the laptop, and can ping it as well. So, it seems they can communicate just fine.

The only other difference I can think of is that I'm using the HDMI output of the MediaCenter, while using the regular internal analog output on my laptop.

Anyone have any ideas what I need to change on the MediaCenter to make it visible as a PulseAudio server?

Thanks,
Trevor

---

### Post by CatKiller on 2011-08-07
> **pyraz said:**
> Anyone have any ideas what I need to change on the MediaCenter to make it visible as a PulseAudio server?

I think you're doing it the wrong way round. You want your Media Centre to connect to your laptop's PulseAudio server.

I've not had a serious play with this, but that's my understanding of how it works.

---

### Post by pyraz on 2011-08-07
Yes CatKiller, you are exactly correct. I do want it the other way around. But when I try to make the MediaCenter the "server", and the laptop the "source", the laptop can not see the PulseAudio server on the Media Center. As you can see from the screenshots above, when I make the laptop the "server", it enables another option in the "playback" section of the pavucontrol on the laptop, as well as an option in the "output" section on the MediaCenter. However, with the same settings enabled on the MediaCenter, the PulseAdudio server on the MediaCenter appears neither in the "playback" section of pavucontrol on the MediaCenter, nor the "output" section of pavucontrol on the laptop.

That's the crux of my problem. The two PulseAudio systems can clearly communicate, but only when the laptop is acting as "server" and MediaCenter as "source". I ran a diff on the /etc/pulse/daemon.conf and /etc/pulse/default.pa on both computers and all the settings are exactly the same. Why can't I use my laptop as a "source" and my MediaCenter as a "server"?

---

### Post by pyraz on 2011-08-07
Ahh the wonders of going to bed and coming to the problem again in the morning :)

Fixed it, I needed to add root to the "pulse" and "pulse-access" groups on the MediaCenter.

Cheers!

---

