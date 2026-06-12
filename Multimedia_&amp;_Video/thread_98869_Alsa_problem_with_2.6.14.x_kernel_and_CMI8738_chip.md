---
title: "Alsa problem with 2.6.14.x kernel and CMI8738 chip"
date: 2005-12-04
forum: Multimedia &amp; Video
---

### Post by ankitrohatgi on 2005-12-04
Hi,

I have an on-board CMI8738 audio chip on a x86. I recently compiled 2.6.14 and 2.6.14.3 kernels on my ubuntu breezy and ALSA refuses to play audio on both. However, ALSA gives no problems with the 2.6.13.4 kernel and the SAME .config file. Please help :( .

Here are some specs:

* Output of *lspci | grep audio* is:

0000:00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

* /proc/asound/card0/cmipci file exists when I boot with 2.6.14.3

* Errors on bootup:
amixer: Mixer attach hw:0 error: No such file or directory
amixer: Mixer attach hw:0 error: No such file or directory
amixer: Mixer attach hw:0 error: No such file or directory
(several such lines)

* Output of *lsmod*
<pre>
Module                  Size  Used by
binfmt_misc             5128  1
fan                     1604  0
button                  2704  0
thermal                 6920  0
processor               8940  1 thermal
ipv6                  166848  12
snd_cmipci             16704  0
snd_pcm_oss            31712  0
snd_mixer_oss          10304  1 snd_pcm_oss
snd_pcm                47176  2 snd_cmipci,snd_pcm_oss
snd_page_alloc          4360  1 snd_pcm
snd_opl3_lib            4736  1 snd_cmipci
snd_timer              12036  2 snd_pcm,snd_opl3_lib
snd_hwdep               3616  1 snd_opl3_lib
snd_mpu401_uart         2688  1 snd_cmipci
snd_rawmidi            11232  1 snd_mpu401_uart
snd_seq_device          3468  2 snd_opl3_lib,snd_rawmidi
snd                    25764  10 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               3360  1 snd
generic                 2500  0 [permanent]
ohci_hcd               12356  0
usbcore                65664  2 ohci_hcd
ntfs                   74480  1
nls_iso8859_1           2880  1
nls_cp437               4416  2
nvidia               3645052  12
unix                   14640  287
</pre>

* The kernel has the right mocule build and I haven't touched any files in /etc.

Thanks,
Ankit

---

### Post by ankitrohatgi on 2005-12-04
Also, there's no /dev/dsp after the bootup is complete.

---

### Post by ankitrohatgi on 2005-12-05
FIXED IT! PHEW!!

Looks like my /dev/snd/* devices were missing. Simply running /usr/share/alsa-base/snddevices did the trick.

The following link was very helpful:
       [http://alsa.opensrc.org/TroubleShooting]("http://alsa.opensrc.org/TroubleShooting")

---

### Post by ankitrohatgi on 2005-12-05
A problem persists...

The /dev/snd* vanishes when I reboot. I get the same set of problem unless I run snddevices manually. How do I enable /dev/snd* creation at boot up?

Thanks,
Ankit

---

### Post by Ptero-4 on 2005-12-05
You got to create a udev rule for that.

---

### Post by ankitrohatgi on 2005-12-05
Sorry udev newbie here :|

Could you provide a bit more help? Some link or idea would do.

Thanks,
Ankit

---

