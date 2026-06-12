---
title: "Alsa problem on install of 12.04 (?)"
date: 2012-10-20
forum: Multimedia Software
---

### Post by dairysound on 2012-10-20
Hi there

I did a fresh install of 12.04 on a new Intel Core2 Duo CPU E6550 @ 2.33GHz × 2 and I'm getting no sound: dummy audio in the sound settings and it can't find my soundcard. I think the problem is with Alsa so I went here [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo) and the link to the output of wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh  is:

[http://www.alsaproject.org/db/f=349f8edca6e927deb9518cc1a00819b1ff922ca0](http://www.alsaproject.org/db/f=349f8edca6e927deb9518cc1a00819b1ff922ca0)

I have an external audio interface (Tascam US-100) which works but that's for my laptop (I'm a musician!) and I don't particularly want to go and buy one just for this. Problem is the plan for this pc is to play mp3's and internet radio through my stereo!

Any advice gratefully accepted.

Thanks

Dan

---

### Post by dairysound on 2012-10-20
Don't think the link is working!

Here's the output:

dan@dan-desktop:~$ cd ~/
dan@dan-desktop:~$ wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
--2012-10-20 21:57:10--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org](www.alsa-project.org) ([www.alsa-project.org](www.alsa-project.org))... 77.48.224.243
Connecting to [www.alsa-project.org](www.alsa-project.org) ([www.alsa-project.org)|77.48.224.243|:80](www.alsa-project.org)|77.48.224.243|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;hb=refs/heads/build;f=alsa/utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;hb=refs/heads/build;f=alsa/utils/alsa-info.sh) [following]
--2012-10-20 21:57:10--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;hb=refs/heads/build;f=alsa/utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;hb=refs/heads/build;f=alsa/utils/alsa-info.sh)
Resolving git.alsa-project.org (git.alsa-project.org)... 77.48.224.243
Connecting to git.alsa-project.org (git.alsa-project.org)|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/x-sh]
Saving to: `alsa-info.sh'

    [ <=>                                   ] 27,785      --.-K/s   in 0.06s   

2012-10-20 21:57:10 (435 KB/s) - `alsa-info.sh' saved [27785]

ALSA Information Script v 0.4.61
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

/sbin/alsactl: save_state:1580: No soundcards found...
cat: /tmp/alsa-info.v5hwHKnPNN/alsactl.tmp: No such file or directory
Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ...  Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=349f8edca6e927deb9518cc1a00819b1ff922ca0](http://www.alsa-project.org/db/?f=349f8edca6e927deb9518cc1a00819b1ff922ca0)

Please inform the person helping you.

---

### Post by dairysound on 2012-10-22
OK well I just used the external soundcard I mentioned in my first post. Works very well.

I guess that counts as Solved!

---

