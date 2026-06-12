---
title: "Annoying problem related to cpu power saving"
date: 2009-10-25
forum: Mythbuntu
---

### Post by whosmatt on 2009-10-25
I have a combined frontend / backend running on an AMD Athlon x2 4050e.  The cpu runs at 1.0 GHz most of the time, and steps up to 1.7, 1.8, 2.0, and 2.1 GHz depending on load. 

The problem is this:  when watching TV, if I have 2 HD feeds coming in (using PIP) the picure and audio stutter terribly.  I found out that this is because the CPU is running at 1.0 GHz and choking.  The workaround is to ssh into the box and start something (like FAH, but sometimes even htop is enough) to kick the frequency up a notch.  Once that happens, playback is fine, even if I quit the process hog.  The frequency will stay elevated until I stop using PIP.

FYI i use screen to tell me the current CPU freq.

Is there a more elegant fix or work-around?  I'm not into having the cpu run full throttle all the time because a) it uses too much power and b) it makes the computer loud.  

Thanks,

Matt

---

### Post by slamhound on 2009-10-25
This page describes some steps you can take:

[http://www.pantz.org/software/cpufreq/usingcpufreqonlinux.html](http://www.pantz.org/software/cpufreq/usingcpufreqonlinux.html)

There is a lot here, and you may not need to go through all the steps if some of these things are already set up on your system (they were by default on mine). Simply running this command:

sudo sh -c "echo 20 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold"

usually works for me.  It lowers the threshold for bumping up the CPU, but frequency will still come down when it is not being used.  The problem is making this setting stick.  I have to rerun the command at least every time I startup, and it seems that I sometimes need to rerun it later.  But it tends to work well most of the time.  The page has instructions for making the setting permanent, but I haven't tried them yet.

---

### Post by whosmatt on 2009-10-26
Thanks for the tip; I will have a look at the link.  Generally I only have the problem on Sundays when I've got 2 HD football games going at the same time, so I've got a little while to figure it out.

-M

---

