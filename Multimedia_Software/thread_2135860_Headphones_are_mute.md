---
title: "Headphones are mute"
date: 2013-04-15
forum: Multimedia Software
---

### Post by Yasso on 2013-04-15
When plugging in my headphones jack the sound is turned to mute and no sound come out , but sound works fine with no headphones
also in my alsamixer there is not automute option.

detailed information :

```
.sh && bash alsa-info.sh
--2013-04-15 21:15:38--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org (www.alsa-project.org)... 77.48.224.243
Connecting to www.alsa-project.org (www.alsa-project.org)|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;hb=refs/heads/build;f=alsa/utils/alsa-info.sh [following]
--2013-04-15 21:15:39--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;hb=refs/heads/build;f=alsa/utils/alsa-info.sh
Resolving git.alsa-project.org (git.alsa-project.org)... 77.48.224.243
Connecting to git.alsa-project.org (git.alsa-project.org)|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/x-sh]
Saving to: `alsa-info.sh'


    [    <=>                                ] 27,785      31.8K/s   in 0.9s    


2013-04-15 21:15:42 (31.8 KB/s) - `alsa-info.sh' saved [27785]


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



```

---

