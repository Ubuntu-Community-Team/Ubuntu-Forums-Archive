---
title: "Remember CPU frequency across reboots? (indicator-cpufreq + acpi-cpufreq)"
date: 2020-03-06
forum: MINT
---

### Post by The Bright Side on 2020-03-06
Hello everybody! After my CPU started overheating frequently in short, intense spikes a few days ago, I disabled the intel_pstate CPU frequency scaling driver (which used to be able to disable my CPU's turbo boost) and am now running acpi-cpufreq instead.

Using indicator-cpufreq, I can manually set my CPU's frequency to 3 GHz without turbo mode (which keeps it nice and cool!):

[screenshot]("http://www.brandartery.com/randomstuff/cpufreq-manuallyset.jpg")

However, after reboot, it resets to "ondemand", which results in those short, massive temp bursts whenever I do something mundane like launching Opera:

[screenshot]("http://www.brandartery.com/randomstuff/cpufreq-afterreboot.jpg")

Is there a way to make it remember my desired setting?

nb, this is happening to me on Linux Mint 19.3, but since the underlying technology is the same, I figured I'd post here too and see if you guys have any experience with this and found a solution.

---

### Post by howefield on 2020-03-06
Moved to the "*MINT*" forum.

---

### Post by The Bright Side on 2020-03-07
For anbody wondering the same thing, I think I found the solution. You can set a frequency cap in /etc/init.d/cpufrequtils, for me it was line 44: 

MAX_SPEED="0"

Change the 0 to any fixed frequency you'd like. You can poll for the available options using a command, which is explained in the comments inside the cpufrequtils file. It's very well annotated.

---

