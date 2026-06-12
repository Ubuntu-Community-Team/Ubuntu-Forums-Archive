---
title: "configuring pulseaudio"
date: 2013-02-07
forum: Multimedia Software
---

### Post by LowFidelity on 2013-02-07
Running ubuntu 12.10 with 3.5.0-23-lowlatency kernel for audio purposes and 12.04-1 minimal server with nginx, openssh, pulse/alsa and not much else yet. (ignore the 11.04 natty on my info, that was like 2 years ago and I don't post here often.)

I recently installed a server on an old box and I remembered that pulse can send audio through the network so I got the idea to hook up the server to my sound system and install pulse/alsa onto the server, which should let me connect my laptop's pulse to the server and play music like that.

Well I got it to work with some tinkering thanks to [**this**]("http://wiki.openwrt.org/doc/howto/pulseaudio") and [**that**]("http://askubuntu.com/questions/28176/how-do-i-run-pulseaudio-in-a-headless-server-installation"), and now I'm installing avahi/zeroconf on the server for automatic discovery, but before I do that I'd like to address a few issues I have with my current setup:

1)Lots and lots of stuttering -- if I've looked in the right places this seems to currently be a known problem with pulse. How annoying. I mention this not because I expect a solution any time soon but just to voice my irritation.

2)For some reason when I connect pulse to the server the transports in various music players (gmusicbrowser, audacious...totem won't even play, what?) stop moving even though the music itself plays (with stutters every some two minutes). When the song ends, the player doesn't seem to detect it and I have to manually tell the player to move onto the next song. Is this a known bug in pulse/is there any way to fix it?

3)Is it just me or are the pulse configuration files stupidly ambiguous? I have not yet successfully found a way to modify the initial configuration for the pulse daemon. This problem is three-fold: 

i. I can't get the pulse daemon on the server to load at startup.

ii. Whenever I switch back to the local soundcard on my laptop the pulse daemon on the server decides to exit for some reason and I have to reload it (the daemon) when I want to use it again.

iii. I also have to manually load the modules necessary for the network communication on both the server and the laptop (module-native-protocol-tcp the server and module-tunnel-sink on the laptop...and with zeroconf, it'll (also?) be module-zeroconf-publish and module-zeroconf-discover) every single time I want to connect.

Various websites mention /etc/pulse/system.pa, and the file itself also has multiple lines of load-module's, but even when I put in my modules they still don't want to load. Same thing with loading pulse automatically on the server, I have no idea how to go about doing that, and as far as I'm aware the pulseaudio documentation is frankly terrible.

Does anybody know how to go about fixing these problems/know of not-terrible pulse documentation? The ubuntu pulse documentation is literally 6 years old (good job on the website ui overhaul though ubuntu lol) and doesn't even mention pulse with networking (not that getting 6-year-outdated computer advice would probably even help). I dig pulse's network capabilities, definitely one if its cooler features, but damn is pulse problematic.

---

### Post by LowFidelity on 2013-02-07
Actually I found out how to automatically load modules into pulse when it starts thanks to the Archwiki (almost forgot about the archwiki, it's definitely pretty good with its documentation). The comments in default.pa says that default.pa loads when pulse is started in user-mode instead of system mode. Still can't figure out how to load pulse at startup on my server though.

---

### Post by LowFidelity on 2013-02-20
bump...

---

