---
title: "Sound card not detected"
date: 2005-11-03
forum: Multimedia &amp; Video
---

### Post by Kirk Wolf on 2005-11-03
I have a Biostar CRU51-M7 MB with a Nforce 410 chipset and onboard sound.

According to the ALSA site, it should be detected as an intel8x0, but its not.

Here's what lspcpi | grep audio says:

0000:00:10.2 Multimedia audio controller: nVidia Corporation: Unknown device 026 b (rev a2)

Can anyone tell me how to install the snd-intel8x0 driver?  It looks like Ubuntu doesn't have alsaconf, so any help would be appreciated.

Thanks, 
Kirk Wolf

---

### Post by Kirk Wolf on 2005-11-04
I installed snd-intel8x0 via:

sudo modprobe snd-intel8x0

lsmod | grep snd shows:

snd_intel8x0           30144  0
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm

But I still don't have any "sound cards"...

more /proc/asound/cards   shows:
--- no soundcards ---

sudo alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

The ALSA docs seem to suggest that I need to run "alsaconf", but as I understand it this is not available in Breezy (?).

I really don't know where to go from here.  I'll offer someone a $20 paypal or Amazon gift certificate if you can help me get this sound card working.

---

### Post by Diod on 2005-11-04
U should download the utils from the alsa website and configure, make and make install them. Then u should try alsaconf

EDIT: nm sry, i switched alsaconf with alsamixer... nm what i just said sorry

Download the newest alsa drivers from [http://www.alsa-project.org/](http://www.alsa-project.org/) and install them, somewhere at the last step it runs alsaconf i believe

---

### Post by Kirk Wolf on 2005-11-04
I'm sorry, its not clear which drivers that you mean for me to install or exactly where they are.  Are then not debian packages for the latest drivers already built somewhere?

---

### Post by Navyblue on 2005-11-05
You could intall alsa-utils from the Debian unstable repository. Part of the thread below might help you on how to do it.

[http://www.ubuntuforums.org/showthread.php?t=85212](http://www.ubuntuforums.org/showthread.php?t=85212)

---

### Post by Kirk Wolf on 2005-11-05
Thanks.  I'll give that a try.

---

### Post by Kirk Wolf on 2005-11-07
Tried per your instructions (after installing modconf and alsa-utils from debian unstable).  alsaconf did not detect the nvidia sound chip (as intel8x0).  I couldn't figure out how to force it.

---

### Post by milli on 2005-11-12
I just picked up a Biostar TForce 6100-939 mobo, Athlon 64 X2 3800+, GeForce 7800GT, etc..

I got sound to work by using the NVidia nvsound OSS driver, but it really sucks since it's stuck at 48khz, the driver doesn't support resampling apparently.  Causes quake3 and et to stutter, even the video.  So that was a nonstarter...

So I got sound to work much better (luckily) by just adding the PCI identifier to the intel8x0 ALSA driver...  kind-of a pain, but it requires re-compiling the kernel.  :(   But it's not so hard on Breezy.

Here's what I did:

[LIST=1]
[*]Pulled down latest and greatest kernel, 2.6.14.2 as of this writing  [http://www.kernel.org/](http://www.kernel.org/)
[*][FONT="Courier New"]$ cd /usr/src; tar xfvj /path/linux-2.6.14.2.tar.bz2[/FONT]
(I highly recommend not doing this as root...  but you do have to [FONT="Courier New"]chmod o+rw /usr/src[/FONT] to do so as non-root)
[*]After kernel is extracted, [FONT="Courier New"]cd linux-2.6.14.2[/FONT]
[*][FONT="Courier New"]$ cp /boot/config-2.6.12-9-amd64-k8-smp .config[/FONT]
If you do not have a dual-core CPU, drop '-smp' 
[*]Apply this patch:
[FONT="Courier New"]$ patch -p1 < [/FONT]
```
--- linux-2.6.14.2/sound/pci/intel8x0.c 2005-11-10 22:33:12.000000000 -0700
+++ linux-source-2.6.14.2-1-amd64-k8-smp/sound/pci/intel8x0.c   2005-11-12 03:30:38.000000000 -0700
@@ -407,6 +407,7 @@
        { 0x10de, 0x008a, PCI_ANY_ID, PCI_ANY_ID, 0, 0, DEVICE_NFORCE },        /* CK8 */
        { 0x10de, 0x00da, PCI_ANY_ID, PCI_ANY_ID, 0, 0, DEVICE_NFORCE },        /* NFORCE3 */
        { 0x10de, 0x00ea, PCI_ANY_ID, PCI_ANY_ID, 0, 0, DEVICE_NFORCE },        /* CK8S */
+       { 0x10de, 0x026b, PCI_ANY_ID, PCI_ANY_ID, 0, 0, DEVICE_NFORCE },        /* NFORCE4 */
        { 0x1022, 0x746d, PCI_ANY_ID, PCI_ANY_ID, 0, 0, DEVICE_INTEL }, /* AMD8111 */
        { 0x1022, 0x7445, PCI_ANY_ID, PCI_ANY_ID, 0, 0, DEVICE_INTEL }, /* AMD768 */
        { 0x10b9, 0x5455, PCI_ANY_ID, PCI_ANY_ID, 0, 0, DEVICE_ALI },   /* Ali5455 */
@@ -2769,6 +2770,7 @@
        { PCI_DEVICE_ID_NVIDIA_MCP1_AUDIO, "NVidia nForce" },
        { PCI_DEVICE_ID_NVIDIA_MCP2_AUDIO, "NVidia nForce2" },
        { PCI_DEVICE_ID_NVIDIA_MCP3_AUDIO, "NVidia nForce3" },
+       { 0x026b, "NVidia nForce4" },
        { PCI_DEVICE_ID_NVIDIA_CK8S_AUDIO, "NVidia CK8S" },
        { PCI_DEVICE_ID_NVIDIA_CK804_AUDIO, "NVidia CK804" },
        { PCI_DEVICE_ID_NVIDIA_CK8_AUDIO, "NVidia CK8" },

```
[*]Compile the kernel....  you will need to [FONT="Courier New"]apt-get install[/FONT] the packages **kernel-package**, **gcc-3.4**, and **fakeroot**
[FONT="Courier New"]$ CONCURRENCY_LEVEL=2 CC=gcc-3.4 fakeroot make-kpkg --initrd --append-to-version -1-amd64-k8-smp kernel-image[/FONT]
Again, if you don't have dual-core, drop the '-smp' and you can also drop the CONCURRENCY_LEVEL environment variable since that won't help with just one CPU
You will be asked a lot of questions.  It's safe to just hit return to them all (about 50 times), or you can pay attention and see if you want any of the new stuff.
[*]Wait for kernel to complie...  with a dual-core CPU and the concurrency level at 2, it uses both CPUs and just flies through the compile..  :-D
[*]After it's all built, [FONT="Courier New"]cd /usr/src; sudo dpkg -i kernel-image-2.6.14.2-1-amd64-k8-smp_1_amd64.dep[/FONT]
Again, modulo -smp
[*]Reboot
[*]Enjoy ALSA Sound, auto-detected at startup
[/LIST]

---

### Post by milli on 2005-11-12
Oh, and to get sound to work okay in quake3 and et (quake3 engine), you have to use OSS emulation and set a couple of things so mmap works.  I modified [FONT="Courier New"]/etc/init.d/alsa-utils[/FONT], the alsa startup script, to do that for me...  and for quake4, you just use OSS emulation, i.e., [FONT="Courier New"]./quake4.x86 +set s_driver oss[/FONT]...  and there's a little more to it for quake4 (have to install the 32-bit SDL libraries).

[FONT="Courier New"]cd /etc/init.d; patch  < [/FONT]

```
--- alsa-utils  2005-11-12 11:22:31.000000000 -0700
+++ alsa-utils.orig     2005-11-12 11:27:41.000000000 -0700
@@ -252,16 +252,6 @@
        fi
 }
 
-quake3_engine_oss_fixup()
-{
-       echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
-       echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
-       echo "quake3-smp.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
-       echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
-       echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
-       echo "quake3-smp.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
-}
-
 # If a card identifier is provided in $2 then regard it as an error
 # if that card is not present; otherwise don't regard it as an error.
 
@@ -278,7 +268,6 @@
                sanify_levels "$TARGET_CARD" || EXITSTATUS=1
                restore_levels "$TARGET_CARD" >/dev/null 2>&1 || :
        fi
-       quake3_engine_oss_fixup
        print_end_msg_and_exit "$EXITSTATUS" "done" "failed"
        ;;
   stop)

```

I'm also using the following for my ~/.asoundrc file, to pump everything through the mixer (all sound sources get mixed...)  so now I can leave IRC up and hear the beeps.  ;-)

```
pcm.mixit {
  type dmix
  ipc_key 50555
  slave {
    pcm "hw:0,0"
    period_time 0
    period_size 1024
    buffer_size 8192
    rate 48000
  }
  bindings {
    0 0
    1 1
  }
}

pcm.!default {
  type plug
  slave.pcm mixit
}

pcm.dsp0 {
  type plug
  slave.pcm mixit
}

ctl.mixer0 {
  type hw
  card 0
}
```

---

### Post by Kirk Wolf on 2005-11-14
Thanks for all of your help, but I finally gave up trying to get my Nvidia built-in sound to work... seems like to much trouble to rebuild kernels... I ended up just buying a cheap Soundblaster PCI card which detected and works fine.

---

