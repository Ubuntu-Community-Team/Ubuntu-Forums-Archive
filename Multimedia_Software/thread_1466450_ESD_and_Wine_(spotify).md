---
title: "ESD and Wine (spotify)"
date: 2010-04-30
forum: Multimedia Software
---

### Post by MikaelHolber on 2010-04-30
Dear all,

I upgraded to Lucid before the release (RC 64-bit, fresh install) and noticed that ESD for Wine was gone (opening winecfg-->Sound). After the release I did another fresh install and still have this issue.

I also did the same procedure on my Eeepc with both RC and LTS  (32-bit) and there the ESD is present and working. Has anyone else experienced this?

For my 64-bit machine I have Alsa, OSS, Jack and NAS?? Sound works if I use *pasuspender*

---

### Post by bacb on 2010-04-30
I have the same problem with Ubuntu 10.04 (64 bits), Wine and Spotify. ESD is gone. I have installed Esound, but ESD doesn't appear in the Wine conf menu and I can't hear any sound or music. 

Regards

---

### Post by c3l on 2010-05-01
I had the same problem. But it appears to be working anyways;


winecfg -> audio:
use OSS driver
Hardware acceleration: Emulated

in spotify, let the hardware acceleration be on



at least this is whats working for me;
running Kubuntu 10.04 x64 with the latest version of the standard wine in the standard repo, and the latest spotify client.

GL!

---

### Post by c3l on 2010-05-01
on a related subject, Im having a problem with my screen going black when loading any wine application (even winecfg). the screen goes back to normal after 3-5 seconds, it appears to be right after the program has loaded completly.

what might be causing this? why? and most importantly, can I fix it? 

and as I said earlier, currently running kubuntu 10.04 x64

---

### Post by bacb on 2010-05-02
thanks C3l, but this doesn't work for me :-(

---

### Post by c3l on 2010-05-02
hmm, well it did work.. until reboot. weird. and I cant get it working now.. I guess something got messed up in the right way when I was testing around yesterday

---

### Post by MikaelHolber on 2010-05-02
No luck with OSS for me either.

---

### Post by kmunro on 2010-05-03
I had the same problem after upgrading to Ubuntu 10.4. The problem is sort of solved by upgrading to the latest Spotify client but sound quality is poor and graphic performance is awful when Spotify is open on the desktop. Seems to be ok when it is just running in the notification area. Anyone else had this experience?

---

### Post by Yellow Pasque on 2010-05-03
Just use the ALSA output. Route ALSA apps to use pulseaudio like so: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

EDIT: You might also try this updated version of WINE with native pulseaudio output: [https://launchpad.net/~vivnet/+archive/vivnet-wine](https://launchpad.net/~vivnet/+archive/vivnet-wine)

---

### Post by kmunro on 2010-05-05
Thanks! Your first link seems to have sorted it for me. It didn't work immediately upon reboot although I noticed that my graphics were fine but still no sound. I then changed the settings in Wine ->Configure Wine -> Audio to "Alsa" and Hardware Acceleration to "Emulation" per an earlier post. I now have sound! Thanks guys.

---

### Post by bacb on 2010-05-05
thanks [Temüjin]("http://ubuntuforums.org/member.php?u=327594")!! It works now, with ALSA routed to PulseAudio.

---

