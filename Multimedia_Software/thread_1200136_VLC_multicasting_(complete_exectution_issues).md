---
title: "VLC multicasting (complete exectution issues)"
date: 2009-06-29
forum: Multimedia Software
---

### Post by trefrog on 2009-06-29
I'm a little new to Ubuntu/Linux. I've used Linux a few times in the past and picked up on a lot of it quickly to get where I needed to go. I'm familiar with many commands and some ins/outs of how Linux distros 'do things around here'. I was able to set up a LAMP web server with cron jobs and a custom php.ini and Samba. So... not so new to Linux itself, just unfamiliar with many things. I work in IT.

Anyway, I loaded a fresh Ubuntu 9 for the sole purpose of running multiple instances of VLC for multicasting 'radio playlists' in a LAN to a network with roughly 100-200 workstations. Installed without a hitch and VLC installed no problem. I tried running a test using a command I found on the Google:

% vlc -vvv Music --sout udp:239.255.12.42 --ttl 12

not sure exactly what -vvv does but it looks like verbosity for the result in the terminal. I already tested this command in Windows and it works great. Now this time the VLC GUI didn't even come up and nothing happened. I can see the vlc instance Sleeping in the System Monitor and the terminal is stopped 'right in the middle' of the output.

tried killing the process and trying again without the multicast switches and it loaded fine loading the Music folder in the playlist as expected.

the really weird thing is that **now** I can't even get it to do **that much**, with the terminal freezing at some point (poss. an arbitrary point?). tried 'completely removing' VLC and reinstalling from Synaptic Package Manager. Otherwise, i'm kinda stuck at this point with my experience level.

TL;DR = computer no werk for me today :p

---

