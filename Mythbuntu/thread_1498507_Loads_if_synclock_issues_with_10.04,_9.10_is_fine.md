---
title: "Loads if sync/lock issues with 10.04, 9.10 is fine?"
date: 2010-05-31
forum: Mythbuntu
---

### Post by nicoloks on 2010-05-31
Hi All,

Recently upgraded my own Myth box as well as one of my friends. My Myth box contains a Dvico Dual Digital4 PCI dual tuner and my friend has a Nova-T 500 PCI dual tuner. As far as video playback and viewing of live TV, both these systems have worked flawlessly (after a few tweaks) on every version of Mythbuntu up to and including 9.10.

We decided to do a fresh install using 10.04 a few weeks ago, and ever since have been plagued with issues primarily when watching live TV, but also watching video files. The issue I'm getting is A/V sync errors and only have 3 tuners showing in system status (there should be 4) and my friend gets intermittent channel locking issues.

My friend has since thrown in the Linux towel and migrated to a Windows XP/Mediaportal combo (he was having issues with audio output over HDMI as well), however I'd rather at least try and get an understanding of what is happening first. I now have two physical hard drives installed; one with 10.04 and one with 9.10. So far the 9.10 installation has not faulted, where as the 10.04 installation continues to have the issues described above. This to me would rule out any sort of hardware level fault, so I would suspect it to be driver and/or MythTV 0.23.

Just wondering if anyone else was seeing issues like this since moving to 10.04?

---

### Post by tensberg on 2010-06-01
I am having audio sync problems as well since upgrading to 10.4. I've posted about it yesterday ([http://ubuntuforums.org/showthread.php?t=1497452](http://ubuntuforums.org/showthread.php?t=1497452)), but unfortunately have no solution yet. Do you also have the problem that the video is always behind the audio track?

Cheers
Michael

---

### Post by jb5 on 2010-06-01
> **nicoloks said:**
>  and only have 3 tuners showing in system status (there should be 4) and my friend gets intermittent channel locking issues.


Have you tried deleting your TV cards in the MBE setup, then reinstalling and re-scanning etc.

Are some of the 4 tuners, virtual tuners? If so you can re-enable the virtual tuners in the BE setup pages.

Channel locking errors - is you region going through a switchover? I went through a couple of weeks of problematic reception during the switchover period.

Have you enabled the amplifier on the nova-t card?

```
    * Very Important Turn on the onboard amplifier or you will get very poor signal strength. It is possible that this will cause you to receive no signal at all due to the amplification of signal noise regardless of signal quality. 

gksudo gedit /etc/modprobe.d/options
Add: options dvb-usb-dib0700 force_lna_activation=1 

or if you're using Ubuntu 9.04 onwards

gksudo gedit /etc/modprobe.d/options.conf
Add: options dvb-usb-dib0700 force_lna_activation=1 

```Taken from [wiki nova-t-500](http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI)

---

### Post by nicoloks on 2010-06-01
I haven't noticed the video lag. What I'm getting is an error on screen saying Myth was unable to obtain an A/V sync. This happens quit often in MythTV and has happened a few times in MythVideo, so I'm wondering if it is something to do with the Myth internal player. I just don't seem to be able to reproduce the issue on 9.10.

I did try the force_lna_activation=1 setting with the Nova-T 500, however it didn't make a difference. I'd never set this previously for my friend, so not sure why it would be an issue now. As for my own Dvico Dual Digital 4, yes some tuners will be virtual I guess. There are only two tuners on the card itself, and the other 2 just showed up after the move to 9.04 when Myth 0.21 came out. I suspect this is due to the multiplexing capabilities that were introduced with 0.21. Weird that 4 show up in 9.x and only 3 in 10.04. No change in Hardware, only software.

The Nova-T 500 and Dvico Dual Digital 4 are very popular PCI based dual tuner solutions, so if this were some driver/Myth internal issue I thought I would have seen a lot more chatter about it by now. What hardware are you using Michael? In addition to my tuner card my system has an X2 AMD 3800+, Nvida 430 based motherboard and a Nvida 8400GS PCI-E video card.

---

