---
title: "Skype Intermittently Stops Its Sound Connection"
date: 2010-03-09
forum: Multimedia Software
---

### Post by Volomike2 on 2010-03-09
On my Acer laptop, I have **Ubuntu 8.04.4 LTS** and a **static version** of the **Skype Beta 2.1**, specifically version 2.1.0.81. I recently made the upgrade to it from an earlier version because I needed to have the screensharing feature to work. Previously Screensharing from others was showing up in a tiny window I couldn't resize. But the Skype Beta 2.1 works fine regarding screensharing.

But the problem I'm having now is that the sound intermittently goes away, but only for Skype. It seems to go away if I walk away from my laptop for a long time. When this occurs, I cannot hear or record sound through Skype, but it works fine through other applications. If I shut Skype back down once it is in this failed state, and come back in, then it remains in this failed state. The only resolution is a reboot, and then it's fine again.

The only thing I can think might be the issue is the Gnome Power Manager, perhaps? I mean, my fan on my laptop spins down if I walk away for a long time, so I know some kind of laptop power management is engaging.

I tried following this guide:

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

And it suggested removing PulseAudio and using esound instead. Well, I tried that and rebooted, and my desktop wouldn't boot properly. So, I did CTRL+ALT+F2, logged in, and then did "sudo apt-get update; sudo apt-get install ubuntu-desktop". All was well again, but unfortunately it brought back PulseAudio again.

---

### Post by Volomike2 on 2010-03-09
I'm still monitoring this situation, but I just installed Part B of this doc...

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

...but on step 4 I had a lockup on logout and just had to reboot for the fix.

So far my laptop has gone into its low power mode (not sleep, not hibernate, but low power mode when I walk away, where the fan spins down) a few times and when I come back out and test Skype 2.1 Beta 2 static, it's doing just fine.

I'm not out of the woods just yet, and am still testing, but so far, it's good on Ubuntu 8.04.4 LTS (32bit version on AMD64 chipset).

---

### Post by Volomike2 on 2010-03-09
So far, this looks to be the resolution on how to install Skype 2.1 Beta 2 on Ubuntu 8.04.4 LTS Hardy Heron. The sound is still working even if I leave the laptop for a few hours.

---

### Post by Volomike2 on 2010-03-10
Well, it failed again. All it took was me to wait overnight for some reason. I came back this morning and it fails to provide any sound.

If I reboot, Skype works again -- but only for a day.

Thanks, Skype! Losers.

---

### Post by Volomike2 on 2010-03-10
So I reverted back to the 2.0.0.72 version on Ubuntu 8.04.4 LTS Hardy Heron, but I had serious sound issues and only in Skype. Here's how I resolved them.

At first when I did the test call, it failed immediately after going back to Ubuntu 8.04.4. I could adjust the Skype Sound Devices settings to this, however, and it sort of worked, but only in one ear:

Sound In: HDA ATI SB (hw:SB,0)
Sound Out: Pulse
Ringing: Pulse

So, I had to remove pulseaudio and add it back in again. And I had to do so with the default apt sources, not any new ones suggested on some Skype help page. So, that step was:

$ sudo apt-get update
$ sudo apt-get --remove pulseaudio

I then rebooted.

$ sudo apt-get --install pulseaudio

At that point, sound worked again in both ears, but was stuttering. There's a fix for that. You edit "/etc/pulse/daemon.conf" (as root) and uncomment the lines:

default-fragments = ?
default-fragment-size-msec = ?

I set default-fragments to 8 and default-fragment-size-msec to 10. You may want to try with that first, and then change those values as necessary until you get the pulseaudio stuttering to go away.

Anyway, after making that file change, I had to reboot because pulseaudio doesn't like to be unloaded and reloaded except by a reboot for some reason.

When I did this, the sound quality was fantastic again.

---

