---
title: "AV-710 asound.state killed gnome. Help!"
date: 2007-03-12
forum: Multimedia &amp; Video
---

### Post by hotspoons on 2007-03-12
So here's the problem. I have been trying to get my $23 Chaintech AV-710 to use the Wolfson DAC (look [Here]("http://www.head-fi.org/forums/showthread.php?t=75655") for general information...I have the asound.state I used bookmarked on my dead computer) by using a custom asound.state file, running 'sudo alsactl restore' at a shell, and hoping for the best. Before I ran this command, sound worked fine out of the standard (but inferior) front channel. Thusfar, all that happened was I got pink noise (static) from the rear surround channel that has the high quality DAC's, and sound stopped coming out of the front channels. Then sound stopped coming out all together when I started changing settings in the mixer app, and any program that used sound stopped responding and would crash upon launching. Anyhow, this happened the last time I tried this on an old load that eventually had the sound FUBAR, the same thing happened.

This is what is now happening. After entering my login information into GDM, where normally the splash screen appears for starting GNOME, the PC just stops and nothing happens. The hard drive stops crunching. It will sit there for hours. The keyboard and mouse still work, and I can CTRL-ALT Fx to a terminal or CTRL-ALT-BKSPC to restart X, but the same thing happens each time I try to log in. 

I can find nothing in any log file that would give me a clue to what to fix. I do know that 'aplay' runs and hangs (I presume playing the login sound), telling me that something in alsa is messed up.

I tried 'dpkg-reconfigure alsa-base alsa-utils', removing asound.state and running alsactl restore, restarting the alsa-utils, and just about everything I can think of. This is still a fresh load without much time into it, so if I need to blow it away, so be it.

However, are there any configuration files or anything in alsa that could be causing this? I really would like to get sound card to work, but it seems my attempts at hacking it to use a different output ruined my system.

As a temporary workaround, I blacklisted the snd_ice1724 module in /etc/modprobe.d/blacklist file, and now Gnome logs in, but now I have no sound. But what configuration file am I missing that would hang alsa? Thanks for any help you can give me.

BTW, the system is a core2-duo on an i965g motherboard, geforce 7950GT graphics, and the problem happens on both Feisty and Edgy. And I would really really like to use this sound card as I do pro audio and wanted to give some of the sound apps (ardour2 mostly) a try, but I can't sacrifice the m-audio delta 10/10 card from my windows-based DAW any time in the near future. 

-Rich

---

