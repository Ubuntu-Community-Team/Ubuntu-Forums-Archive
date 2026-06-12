---
title: "MPD playback stops on logout"
date: 2009-11-10
forum: Multimedia Software
---

### Post by thfz on 2009-11-10
I've installed MPD and currently have it streaming to an Icecast server. I've done this before, and everything works fine with authentication and playback, that is until I log out. When I log out, the currently playing song will finish, and then MPD stops streaming and will not start again until I log back in and use Sonata or mpc to start playing again.

Is anyone aware of why this occurs or how to fix it? I can't find anything except maybe a PulseAudio problem that could be the cause.

System Information:

Ubuntu 9.10 32-bit
Linux AcerDesktop2 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

---

### Post by aperomsik on 2009-11-26
I have the same problem. It was working fine in Jaunty but in Karmic mpd is fishy. The other thing is that it works OK when I am logged in but when my wife logs in it doesn't let her start mpd playing again.

---

### Post by aperomsik on 2009-11-26
Looks like it's pretty complicated. 

There are some workarounds listed on this launchpad bug:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192735](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192735)

but they don't quite work for me. The basic issue seems to be that MPD is supposed to be able to start its own pulseaudio instance but it doesn't seem to work... so it uses yours, and that process exits when you log out.

Hmm... maybe as a cheesy workaround we could set the "allow tcp connection" preferences there for user "gdm", whose pulseaudio client seems to be always running.

---

### Post by aperomsik on 2009-11-26
Well, that didn't work out quite as I expected. I used a trick similar to the one described [here]("http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html") to run paprefs for the user gdm, and enabled network access to gdm's pulseaudio instance... and the result was that mpd would play when the login window was showing, and pause when someone else was logged in. 

Which leaves me feeling that PulseAudio as implemented in karmic is a technically impressive means of achieving exactly what I don't happen to want.

So, despite the condescending warnings [here]("http://pulseaudio.org/wiki/WhatIsWrongWithSystemMode") (a link which I found in /var/log/messages!), it seems that for a home mpd music server, running PulseAudio in system mode is the way to go.

To achieve that, I changed /etc/default/pulseaudio so it says PULSEAUDIO_SYSTEM_START=1 (instead of zero), and added the line mentioned in the previously reference launchpad bug's [comments]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192735/comments/8"), "load-module module-native-protocol-tcp auth-anonymous=1" (without quotes), but I added it to /etc/pulse/system.pa instead of /etc/pulse/default.pa .

Now everything seems to be working as desired: mpd keeps playing when I log out, and when my wife logs in she can control it too.

---

