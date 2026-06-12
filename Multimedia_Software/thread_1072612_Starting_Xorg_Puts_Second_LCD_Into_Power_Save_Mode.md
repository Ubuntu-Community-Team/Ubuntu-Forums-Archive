---
title: "Starting Xorg Puts Second LCD Into Power Save Mode"
date: 2009-02-17
forum: Multimedia Software
---

### Post by tsuehpsyde on 2009-02-17
So, I have a rather strange and frustrating problem. After a few days of troubleshooting and not having any luck at all, I'm turning here, hopefully for some help.

I have an ATi FireGL V3600 and dual Dell LCD widescreen 19" monitors (dunno the model off hand). A few days ago, I accidentally bumped my secondary monitor's cable and unplugged it. It went into sleep mode, I go look and find the cable not plugged into the card anymore. I plug it back in, and it stays in Power Save mode (no input coming in).

Confused (I've had it unplug before without issue), I reboot. I see the BIOS screen, the boot screen, et cetera, but when xorg starts, it kills the secondary monitor and it goes into sleep mode.

I was using Ubuntu 8.04LTS with EnvyNG drivers, fwiw. I then switched back to the stock driver and was able to get cloned screens (both monitors working fine), and the "stock" ATi 3D driver only gave me a white screen. I was able to re-install EnvyNG's driver without issue, but again, only one screen would work, second would be in power save mode.

I restored xorg.conf from backed up version from a month before, and from 4 months before, neither fixed it. I did a dpkg-reconfigure on xorg and that worked with the stock 2D driver for cloned screen, but installing the EnvyNG driver caused it to go back to single screen mode again. I wiped the Ati CCCC config file, no dice. I also looked at the xorg log file and nothing interesting was there either.

I've booted into the LiveCD and it also clones the screen, so the hardware is fine.

As a last ditch effort, I did a dist-upgrade to 8.10, which luckily has a stable version of the 3D driver EnvyNG was using (so I don't have to use that anymore to get a decent driver). However, my sleepy monitor still follows me over. :(

I'm seriously at a loss here and I'm about to wipe the system and start over. There *HAS* to be a config SOMEWHERE that's sitting around that I can't find that's holding my monitor hostage. I've looked though, and no dice.

I've done extensive searching for the past 5 days, and all I find are how-tos for setup (which I don't need). Sadly, most come up as threads that are 2 years old and how to hack dual monitors in. I'm unable to find anyone having my exact issue.

Some help on this issue would be extremely appreciated so I can get back to work instead of messing with this second monitor. I'd already have wiped the system, but the 8.10 LiveCD was throwing errors when booting, so I figured I'd come here and ask you guys. If worse comes to worse, I'll just nuke it and go 8.04 -> 8.10 again and start over.

It's just really annoying. I've used Linux for years and I'm far from a "noob", but I really for the life of me cannot figure out why my system is disabling my second monitor. It makes no sense.

Thanks in advance for any help.

---

### Post by tsuehpsyde on 2009-02-17
I found the issue, so I thought I would reply back here with the answer for anyone who wants it. =)

You have to go into the ATi Catalyst Control Center. Click on "Display Manager" so the arrow goes down. If you're having my symptoms (and my problem), you should see your two monitors:

Digital Monitor (1)
Digital Monitor (-)

Click on Display Manager so it's highlighted, then select the (-) monitor in the drop-down, the monitor should show up with a red border around it right above the drop-down. Click any of the settings below (in my case, BigDesktop to the right) and whamo! Monitor no longer sleeping.

I am unaware why the monitor went into disabled mode inside the ATi CCC. I guess they figure if you unplug it, you must never want it again. Yeah, I don't get it.

I also did reset the config file for the ATi CCC, but I guess this setting still hung around. Either way, it's fixed now. Maybe this will help someone else out in the future. :)

---

