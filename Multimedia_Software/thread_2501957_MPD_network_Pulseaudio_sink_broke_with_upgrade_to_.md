---
title: "MPD network Pulseaudio sink broke with upgrade to 24.04"
date: 2024-10-28
forum: Multimedia Software
---

### Post by zeero_k on 2024-10-28
For years I have been running MPD on a headless server in my basement, sending music to various devices throughout the house via Pulseaudio network sinks and centrally controlling it with various MPD control apps; it’s all worked great for years. The server running MPD is currently running Ubuntu Server 22.04, and many of the remote devices are running Kubuntu 22.04, although in my garage I have one really old Pentium 4 machine that is dedicated to being a headless MPD audio sink, and I’ve left it running Ubuntu server 14.04 because it boots faster than any more recent versions; still works great for that dedicated purpose!

Recently I upgraded one of the remote devices from Kubuntu 22.04 to 24.04, but now the pulseaudio link between the MPD server and that device is broken and I can't figure out how to fix it. The MPD feed used to show up as an application in the the volume control in Kubuntu, and I could adjust the volume there and whatnot. Now it doesn’t show up on that machine after the upgrade. On the server, /var/log/mpd/mpd.log, says the following when I try to enable the output to the newly-upgraded kubuntu machine (which is called bluey-kubuntu)

Oct 27 18:54 : exception: Failed to open "pulse to bluey-kubuntu " (pulse); failed to connect: Connection refused

I’ve done google searches about how to enable pulseaudio network sinks and modified /etc/pulse/default.pa to enable the load-module module-native-protocol-tcp, copied the file ~/.config/pulse/cookie from another machine that works, also got paprefs working using the symlink hack, but none of that is working. Also I’ve compared these files with another machine running Kubuntu 22.04 that is still working fine as a remote sink, and it doesn’t look like any any of these had to be modified to to get it to work as a remote sink. 

Any ideas? I’m now afraid to upgrade any of these other machines or the server to 24.04 because MPD is one of my main uses of all these machines.

---

### Post by zeero_k on 2024-11-11
Update: I’m giving up on using pulseaudio for transmitting audio over the LAN. Instead I installed snapserver on the server running MPD and set up a MPD fifo output to /tmp/snapfifo, per snapserver’s instructions.

On the target machine running Kubuntu 24.04, I installed snapclient, and to my amazement it immediately picked up the stream and started playing it without any configuration needed. The only problem with this default configuration is that snapclient runs daemonized and sends the output directly to the default sound device via ALSA. I would prefer to be able to control the volume and device through the KDE Plasma volume control on the target machine. I accomplished this by making a simple script to launch snapclient with the command: > snapclient --player pulse and adding this as an Autostart application in System Settings > Startup and Shutdown. I also had to put some gobbledygook in the file /etc/default/snapclient in order to prevent the daemon from launching (the gobbledygook was my attempt to launch snapclient and attach it to the logged-in user by specifying options in this file, but that didn’t work and instead crashed the daemon :P)

I have this set up now on a couple of machines running KDE that I want to be able to play the stream from the MPD server. An advantage of this setup is that all of the outputs are now all perfectly synced, which wasn’t happening before using the individual Pulseaudio network sink connections. The drawback of this setup is that I can’t control outputs to the target machines individually using MPD control apps (i.e. on my phone), but overall I think it’s a good tradeoff. There’s also a bit of a popping noise when the stream first starts up during the syncing process, but it’s not too annoying.

I still have no idea why the upgrade from Kubuntu 22.04 to 24.04 on the target machine broke the pulseaudio connection.

Next on the agenda is to see if snapclient will work on the old headless receiver running Ubuntu 14.04.

---

