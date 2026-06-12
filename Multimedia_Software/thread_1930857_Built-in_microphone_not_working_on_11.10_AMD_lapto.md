---
title: "Built-in microphone not working on 11.10 AMD laptop"
date: 2012-02-24
forum: Multimedia Software
---

### Post by dpapathanasiou on 2012-02-24
I have a new Lenovo G575 laptop with an AMD Fusion E-300 cpu.

I installed the 11.10 AMD desktop version using the CD iso with no problems, and the built-in sound card played audio immediately.

The built-in microphone, however, doesn't work.

I tried editing the /etc/modprobe.d/alsa-base.conf file by adding this line at the end and rebooting, but that did not solve the problem:

```
options snd-hda-intel position_fix=1
```I checked my sound settings, using both alsamixer and the gui, and while the mic is not muted, I don't see a specific microphone object to select.

The only "Connector" option is "Analog Input":

[IMG]http://i.imgur.com/EFfev.png[/IMG]

And in the alsamixer view, I don't see a component described as "Mic" or "Microphone" as shown in the troubleshooting guide:

[IMG]http://i.imgur.com/D1q7W.png[/IMG]

So is there a hardware configuration or driver issue I need to fix?

---

### Post by dpapathanasiou on 2012-02-24
So I did some more searching for laptop built-in microphone problems, and I came upon this recent post [http://bernaerts.dyndns.org/linux/202-ubuntu-acer-ao722](http://bernaerts.dyndns.org/linux/202-ubuntu-acer-ao722) about an Acer laptop.

He was running 11.04, but I thought his fix might work for me as well, so I tried the following steps:

```
# sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
# sudo apt-get update
# sudo apt-get install linux-alsa-driver-modules-$(uname -r)
# sudo apt-get install pavucontrol 
```Unfortunately, the 11.10 kernel is different, and I got this message:

```
E: Unable to locate package linux-alsa-driver-modules-3.0.0-16-generic
E: Couldn't find any package by regex 'linux-alsa-driver-modules-3.0.0-16-generic'

```And so the problem remains.

I also found this long bug report, also about the built-in mic for a laptop [http://web.archiveorange.com/archive/v/LLXmLkyhla4r65AzCppg](http://web.archiveorange.com/archive/v/LLXmLkyhla4r65AzCppg) which ends with the message:

```
This bug was filed against a series that is no longer supported 
and so is being marked as Won't Fix.
```So does this mean there's no way to get the built-in mic working?

I did see in other threads that people reported external usb microphones will work, but rather than purchasing one of those, I did want to see if I could get the built-in one functioning at all.

Any advice?

---

### Post by dpapathanasiou on 2012-02-24
Just out of curiosity, I went and installed the latest debian (v. 6.0.4) on the same machine, to see what would happen.

It turns out that all the sound functions, including the built-in speakers and microphone, work right from the beginning, without having to tweak any alsa configurations or do anything else.

So that was puzzling and disappointing.

Puzzling b/c I thought ubuntu was an advanced version of debian, and if a particular hardware configuration works on debian it would also work on ubuntu (i.e., since ubuntu has incorporated what debian has accepted and tested).

Disappointing b/c I'm not really pleased with debian otherwise, and I would much rather prefer to run ubuntu on that laptop.

---

### Post by dpapathanasiou on 2012-02-25
After discovering this thread [http://ubuntuforums.org/showthread.php?t=1728441](http://ubuntuforums.org/showthread.php?t=1728441) and then this article on Intel HDA Audio [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) I expected to be able to solve the problem.

Unfortunately, no matter which value of MODEL I use in this line of the /etc/modprobe.d/alsa-base.conf file:

```
options snd-hda-intel model=MODEL
```The microphone simply doesn't work.

Here are all the possible model values, according to the /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz file on my machine:

```
lenovo-3000    Lenovo 3000 y410
  lenovo-101e     Lenovo laptop
  lenovo-101e    Lenovo 101E
  lenovo-nb0763    Lenovo NB0763
  lenovo-ms7195-dig Lenovo MS7195
  lenovo-sky    Lenovo Sky
  lenovo    Lenovo 3000 C200
  thinkpad    Lenovo Thinkpad X300
  thinkpad    Lenovo Thinkpad T60/X60/Z60
  thinkpad    Lenovo Thinkpad T61/X61
  laptop-automute 2-channel with EAPD and HP-automute (Lenovo N100)
  ideapad    Lenovo IdeaPad laptop
  lenovo-x200    Lenovo X200 laptop
  asus        Asus K52JU, Lenovo G560
  ideapad       Lenovo IdeaPad U150
  thinkpad    Lenovo Thinkpad

```I even tried model=asus since my machine (G575) is closest to the G560 model, and unlike the T or X versions.

So I'm giving up on using the internal mic for now, and will try an external one next, though I'll continue to monitor this forum for any updates or suggestions.

---

### Post by Yellow Pasque on 2012-02-25
Try the latest ALSA driver: [https://launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily](https://launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily)

If that doesn't work, report the bug on Launchpad, especially since it's a regression.

---

### Post by dpapathanasiou on 2012-02-26
> **Temüjin said:**
> Try the latest ALSA driver: [https://launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily](https://launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily)

If that doesn't work, report the bug on Launchpad, especially since it's a regression.

Thanks for the suggestion, I'll try it.

I was also thinking of a different strategy: is there a simple way to use the alsa from the debian live dvd and apply it to my ubunutu installation?

The alsa-base.conf file on the live dvd was significantly different from the ubunutu version, so I copied it off the dvd, and tried it in /etc/modprobe.d but it didn't work.

There is probably one or more drivers I'd need to copy as well, though I'm not sure which, or if the idea is even possible.

It's just frustrating to run debian off the live dvd and have the mic work, when the mic is completely dead under ubuntu.

---

### Post by dpapathanasiou on 2012-02-28
> **Temüjin said:**
> Try the latest ALSA driver: [https://launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily]("https://launchpad.net/%7Eubuntu-audio-dev/+archive/alsa-daily")

If that doesn't work, report the bug on Launchpad, especially since it's a regression.

Thanks, this worked!

More specifically, I added the ubuntu-audio-dev/alsa-daily ppa and did sudo apt-get update; sudo apt-get upgrade.

I also added this line to the /etc/modprobe.d/alsa-base.conf file:

```
options snd-hda-intel model=asus
``` It turns out that 'asus' is indeed the correct value for model, since  according to the /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz  file, 'asus' corresponds to the Lenovo G560 machine, which is a close  relative of the one I have.

Thank you again for suggesting the alsa daily builds.

---

