---
title: "Sound stops"
date: 2011-04-30
forum: Multimedia Software
---

### Post by LaptopU on 2011-04-30
I had problems under Maverick with sound just stopping and I would need to kill alsa and restart it, the sound would then come back on.  So when Natty came out this week I thought I would do a fresh install and that would solve the problem.

Brand new fresh install yet I'm still having problems.  My machine will play audio fine for anything between a few minutes and several hours, then the audio will stop dead.  Movie Player and Banshee both stop, the time sliders do not move and if it is a video it freezes.  If it is a web page with audio then Firefox freezes.

Yet if I wait a couple of minutes I hear a click and the audio comes back on as if nothing happened.

My sound card is built into my Gigabyte motherboard.  Whilst not directly related I also get a stuttering on my machine during the startup sound even though it is a good spec machine.

Any help please?

---

### Post by KegHead on 2011-04-30
Hi!

Is your bios up to date?

KegHead

---

### Post by lidex on 2011-04-30
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by LaptopU on 2011-05-01
Thanks for your advice so far.  My alsa info link is [http://www.alsa-project.org/db/?f=dfd9dcb772dfe23e863f1aca4419cd562fe09339](http://www.alsa-project.org/db/?f=dfd9dcb772dfe23e863f1aca4419cd562fe09339)

As I mentioned earlier this is a brand new clean Natty installation, however I was experiencing problems under Maverick which I chalked down to something being corrupted along the way.  Is it possible a change happened to alsa around 2-3 months ago and that version has made it across to Natty?  This is around the time I started having problems.

---

### Post by LaptopU on 2011-05-01
> **KegHead said:**
> Hi!

Is your bios up to date?

KegHead

Just checked with manufacturer's site and yes I have the latest version.

Incidentally I have been on Ubuntu since Hardy and the startup sound worked fine, but since Lucid it stutters.  I have noticed some others are having the problem but it seems to be a known yet unfixed bug.

---

### Post by PhonicLynx on 2011-05-01
I've reported the same problem in another thread... and I've not been able to solve it so far either.

---

### Post by LaptopU on 2011-05-01
So this is a problem for others?  Is there a bug report for it?

I even had the cover off my PC vacuuming it out earlier to make sure it's not a silly problem like dust on the motherboard causing a short somehow.

How long have you had the problem?

---

### Post by lidex on 2011-05-01
Can you post this output please:
```
dmesg | grep ac97
```

---

### Post by LaptopU on 2011-05-01
Here you go

[   11.624051] intel8x0_measure_ac97_clock: measured 55896 usecs (2693 samples)

Thanks for all the help so far.

---

### Post by lidex on 2011-05-01
I'm not really sure what to grep in dmesg for ac97 so can you do me a favor? Run this command in terminal please:
```
dmesg | less
```
Scroll to a section showing codec/alsa/intel8x0 information and cut-and-paste that block of text into your next post. Thanks.

---

### Post by LaptopU on 2011-05-02
[   11.436096] intel8x0_measure_ac97_clock: measured 55771 usecs (2687 samples)
[   11.436104] intel8x0: clocking to 48000

Is that the info you're looking for?

I have noticed at least three other recently started threads on this topic, I think perhaps I am just one person affected by a larger problem.  Here are a couple of the other threads:

[http://ubuntuforums.org/showthread.php?t=1746855](http://ubuntuforums.org/showthread.php?t=1746855)
[http://ubuntuforums.org/showthread.php?t=1743200](http://ubuntuforums.org/showthread.php?t=1743200)

Could this problem be caused by the recent kernel?

---

### Post by LaptopU on 2011-05-02
I have added my comments to [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/704809?comments=all](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/704809?comments=all) in the hope this gets resolved.

---

