---
title: "Resetting Sound packages on Jaunty"
date: 2009-05-25
forum: Multimedia Software
---

### Post by kaele on 2009-05-25
I'm running Jaunty and I was trying to get Scummvm audio to work for the Curse of Monkey Island and something went wrong, I can't get any audio to work at all now. I've followed the sticky audio guide to no avail.

When I installed I downloaded everything I could for ALSA drivers, but I'm not that savvy with linux yet and I don't know if pulse got in the way.


```

:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
:~$ lspci -v |grep Audio
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)

:~$ modprobe -l |grep atiixp
updates/alsa/pci/snd-atiixp.ko
updates/alsa/pci/snd-atiixp-modem.ko

Also I noticed a weird setting in the /etc/group file:
audio:x:29:pulse

I tried changing it to my user name, but it didn't fix the issue.


```

---

### Post by 73ckn797 on 2009-05-25
It may seem simple and may not actually work but did the individual sound settings get muted? The mute may be off when right clicking on the speaker icon in the upper panel. Go to volume control and make sure none of those are muted as can be seen with the small icon below each level adjuster.

---

### Post by kaele on 2009-05-25
Yes I have tried all those things. I went through step by step and followed everything in the Audio Sticky solution thread, and followed each suggestion for failed steps, I purged alsa packages and reinstalled, I compiled alsa fresh, and the only thing in that step that doesnt seem to be working as intended is when you type:

sudo modprobe snd-

when I press tab nothing pops up, although when I do modprobe -l I see that snd-atiixp is listed. I don't know what else could be causing the problem except maybe other packages.

I'm really trying to avoid doing yet another complete re-install, I just would like to tear down all my sound related packages and bring them back to jaunty defaults.

---

### Post by 73ckn797 on 2009-05-25
Have installed restricted or Medibuntu packages?

---

### Post by kaele on 2009-05-26
Yes, I've got both repositories included in my package manager. I've also searched far and wide for a variety of solutions. None of which really apply to my situation, so I had to post a new thread. I don't know if there's more information I should post here or not.

---

### Post by kaele on 2009-05-27
Just an update. I backed up my home directory and reinstalled Jaunty again, I followed all the installation packages on [http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04](http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04) and things were working fine.

I then went through [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) to make sure I wasn't missing any sound or video packages.

After I restarted I had no sound. I get sound at the login page, both my login ready and login success sounds work fine. But the moment I get into gnome, nothing plays. I thought it might have been just this account, but making new accounts doesn't help either.

Can someone please help? I'm not even tinkering with settings, I'm just copy and pasting package install lines from other confirmed guides. I just don't understand how the login sounds work but nothing else.

---

### Post by kaele on 2009-05-27
That's weird, I retract my message. It seems to be working now after rebooting twice. hm. Strange.

---

