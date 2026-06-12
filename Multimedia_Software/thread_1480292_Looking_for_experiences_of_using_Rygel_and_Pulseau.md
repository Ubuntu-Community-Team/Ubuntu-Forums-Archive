---
title: "Looking for experiences of using Rygel and Pulseaudio"
date: 2010-05-11
forum: Multimedia Software
---

### Post by daniel karlsson on 2010-05-11
Dear Everyone,

I've experimented a bit with Rygel and Pulseaudio in Lucid and have sofar not managed to do anything useful.

What I would like to do is to stream output from e.g. Spotify to any of my DLNA devices (PS3, Samsung TV, XBMC, Onkyo Receiver, ...).

When I try to connect to Rygel from a device this happens:
May 11 19:13:23 * pulseaudio[1718]: xmalloc.c: Assertion 'size > 0' failed at 
pulse/xmalloc.c:62, function pa_xmalloc(). Aborting.
May 11 19:13:23 * kernel: [ 5484.124382] __ratelimit: 47 callbacks suppressed
May 11 19:13:23 * kernel: [ 5484.124387] rygel[1733]: segfault at 0 ip 00007fd
ebadbae70 sp 00007fff31503898 error 4 in libdbus-1.so.3.4.0[7fdebad94000+3d000]

Versions:
rygel                                      0.4.10-2                                              GNOME UPnP/DLNA services
pulseaudio                                 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14       PulseAudio sound server

Anyone with better experiences of Rygel and Pulse?

Regards,
Daniel

---

### Post by Scepticer on 2010-05-15
I've been trying to get this to work too for some time. I'm very new to Linux, been running Ubuntu 10.04 Netbook edition on an EEE for a few days only. :)

Anyway, I've come as far as I have been able to get both my PS3 and Pioneer receiver to discover Rygel/pulseaudio (streaming shows as "Audio on ubuntu", files as what I have specified in the Rygel preferences). I also got it working when it comes to streaming mp3-files to those devices. My goal was however to get the system sound (or really spotify sound) from my EEE to go through DLNA to those devices. Not working yet. I see the streams on the devices by they can not connect to and play them...

Rygel 0.4.10-2
Pulseaudio 0.9.21

...and all gstreamer, pulsaudio 'extra' packages I found in the Ubuntu software center...

Any tips appreciated here too. ...and I'll report back here if I make any progress. :)

EDIT: Oh yeah. I think the reason why I got the DLNA service to show up was that I discovered that Rygel had created an icon under "Other". Clicking that one I think made the DLNA service to show. I suspect something wasn't started. (Sorry I can't give so much more details, total linux newbie just trying everything :) )

---

### Post by dnns on 2010-12-28
Bumping - looking for a similar solution. Need one DLNA/UPnP channel that outputs whatever the computer is playing to a DLNA/UPnP capable media server.

Rygel seems promising in the options it provides (adds a PulseAudio output channel called DLNA/UPnP streaming) but is lacking in actual implementation.

Up to now I'm only able to access the media stored on my PC which makes Rygel on par with Mediatomb in my eyes.

Anyone had luck streaming whatever the PC is playing to a media receiver via UPnP?

(Using WDTV live player, Ubuntu 10.10)

---

### Post by xlash on 2011-01-30
Did you have any success?

I also would like to do this :

Stream all sound to remote Onkyo AVR or PS3. My goal is to be able to select my sound output as Remote streaming to my Onkyo NR-708 receiver. 

I can do that with Windows Media Player 12 (choose stream to and it detects the remote device). No luck with OSX yet either.

Thanks

---

### Post by belrik on 2011-03-30
Any news on this? I'm very keen to use this for a PulseAudio output to a Roku Soundbridge.  It'd be a perfect complement so my setup.

Unfortunately there's little to zero information available and it seems that the Rygel people broke the previous implementation at some point by changing the MediaServer spec and I see no reports of a recent working configuration. 

If anyone has done this please chime in, it'd be great to hear from you.

---

### Post by bradleee on 2011-07-04
[See workaround here]("http://ubuntuforums.org/showpost.php?p=11010331&postcount=4").

Native PA->DBUS->Rygel support broke when rygel went to dbus mediaserver2 before PA left dbus mediaserver1. The above post is a workaround that works for me; hopefully more recent versions of PA support mediaserver2 natively and the PA->DBUS->Rygel chain works again (rather than my PA->gstreamer->wavpack->rygel chain). For the time being though I have this working with my PS3 (which is a UPnP DLNA device and can consume most rygel output).

---

