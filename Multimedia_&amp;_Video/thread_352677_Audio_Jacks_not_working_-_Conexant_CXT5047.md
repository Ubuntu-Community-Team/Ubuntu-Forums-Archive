---
title: "Audio Jacks not working - Conexant CXT5047"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by shibz on 2007-02-03
I have a HP dv2000t laptop. For some reason I can't get my headphone jack to work right. When I plug something in, I either get audio out of both my headphones and the laptop speaker or just the laptop. I have re-compiled my alsa countless times to try and fix it using several different versions/patches. I have only been able to produce two different results.

Result 1 (default Edgy install):
* Sound only out of laptop... no headphones
* In alsamixer, both the "Master" and "PCM" control volume on my laptop speaker

Result 2 (self compile using this post [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) ):
* Sound comes out both headphones and laptop at the same time
* In alsamixer the "Master" control only changes headphone volume and "PCM" changes the speaker volume. -- So if I mute master, I still get sound out of the laptop, and none from my headphones, but if I mute PCM I get no sound at all.

Additionally, with the 2nd result, when I mute "master" the mute indicator on my laptop turns red. The default Alsa that came with Edgy didn't.

These are from alsa 1.0.14rc1 (result 2)
```
$ head -n 5 /proc/asound/card0/codec#0
Codec: Conexant CXT5047
Address: 0
Vendor Id: 0x14f15047
Subsystem Id: 0x103c30b2
Revision Id: 0x100000
```
```
$ sudo lspci -v|grep -A 5 Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, fast devsel, latency 0, IRQ 66
        Memory at d4340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
```

Does anyone have any ideas? Thanks!

---

### Post by shibz on 2007-02-04
Also, I see that some people with the same model as me have additional things in their alsamixer like "Front". I only have 2 volume controls in my alsamixer... "Master" and "PCM"

---

### Post by shibz on 2007-02-05
Update: I have tried every version from 1.0.2 to 1.0.4rc2 and none of them work with my headphone jacks. Please help!

Thanks

---

### Post by shibz on 2007-02-07
if you need more info to help me debug please ask! I have been looking for days and can't find anything about my problem

---

### Post by shibz on 2007-02-10
I just noticed that if I do aplay -L it seems to be seeing a lot more than appears in my alsamixer... so does ubuntu have alsamixer configured to exclude some controls to make things simple or something?

```
$ aplay -L
default:CARD=Intel
    HDA Intel, CONEXANT Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)

```

---

### Post by sgx on 2007-02-10
there is an app 'alsamixergui' which has more controls than the plain alsa mixer panel, install it if you have not yet done so, also install alsaoss, as this wrapper solves quite a few mysteries, and yields good luck in future quests too...

---

### Post by moeFinley on 2007-02-10
If you don't find what you need in 'alsamixergui'.  This will play a sound file to the default device which is a great way of testing.

```
aplay -D default /path/to/audio/file.wav
```

Switch it between the different devices to see if you can get the desired results, then you can configure ALSA.

---

### Post by diebels on 2007-02-17
Tobin Davis is doing great work on this driver. Get [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc2.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc2.tar.bz2) and apply the patch in this post: [http://article.gmane.org/gmane.linux.alsa.devel/44604](http://article.gmane.org/gmane.linux.alsa.devel/44604)

Speaker automute when headphones connected works for me now. Volume above 50% is distorted.

---

### Post by penvzila on 2007-02-18
How do you apply a patch?  Do I download the source, and then download the patch to the source directory?

Also, I plan on doing this in 64bit Ubuntu.  I'm assuming it's fine since I'll be compiling the drivers, but I'd like to know ahead of time if these are 32-bit only.

---

### Post by penvzila on 2007-02-19
When I tried to apply the patch, it rejected it.

---

### Post by penvzila on 2007-02-19
I didn't realize you had to ./configure before patching.  Now we'll see if it works...

---

### Post by penvzila on 2007-02-19
Alright.  After spending an embarrasingly long time on this I got my sound to work.  Ie, I have sound in my headphones, and inserting the headphone mutes the external speakers, just like it should.

The patch should be downloaded to the alsa-driver source directory, in the alsa-kernel subdirectory (took me a while to get that one.)  THEN, you do patch -p1 <nameofpatch.  Then, ./configure --with-cards=hda-intel.  After make and make install, I removed everything that showed up lspci that had to do with sound.  After that, I did modprobe snd-hda-intel, and edited the options line /etc/modprobe.d/alsa-base to simply 'laptop'.  NOT laptop-hp or test or ref, but 'laptop.'  On reboot, I had a volume control with PCM1, and PCM2.  PCM1 controls the volume of the headphones, and I muted PCM2, which controls the volume of the speakers.

---

### Post by diebels on 2007-02-20
If you move the patch inside alsa-driver-1.0.14rc2/alsa-kernel and apply it with patch -p1 < conexant-test14a.patch , it should work ok. Have no idea about 64 bit.

---

### Post by penvzila on 2007-02-20
I have it working, but I must say it is still a disappointment.  There is pretty horrible distortion at moderate to high volume.  Like, anything about about 50% of PCM.  I'm using an external amp right now to make up for it, but of course I now have a lot more background noise as a result.  So it'll do in a pinch but it's certainly nothing I'd boot into linux for.  Which is a shame, because it's so goddamn fast.

---

### Post by lapichiflati on 2007-02-24
HP DV2040 with Kubuntu Edgy
I agree that the patch is somewhat of a disappointment... Before I couldn't get jack sense to work so my onboard speakers were always on, now I can mute them (yay!), but I get the distortion problem so I have to keep it at a low level.  Also, I seem to have lost microphone functionality as a result of the patched driver.  Hmmmm.  I might have to go back to 1.0.14RC2, unless someone has advice on how to get mic functionality back.  I do appreciate all the work done on the driver, however...

---

### Post by thorsten.scherler on 2007-03-06
I followed [http://www.sundru.net/bblog-stuff/?sectionid=2]("http://www.sundru.net/bblog-stuff/?sectionid=2")
and this thread.

This solved the audio jacks problem, but  Volume above 50% is distorted.

Further I never (before patch with rc2 and after) got the mics working not internal nor external. The magic number seems to be rc1, or? :(

Will watch this thread and keep you updated if I can find something.

Thanks.

salu2

---

### Post by pixeldotz on 2007-03-06
so does rc1 fix the mic issues with the conexant cards? reason i ask is because i have an HDA-INTEL CONEXANT CXT5045 in my laptop and have compiled and installed rc2 to get audio working pretty nicely. the only problem is that the mic does not work at all.

---

### Post by lapichiflati on 2007-03-14
The latest patch, 10 march 2007 brings the CXT5047 aka Waikkiki up to date with distortion (mostly) fixed and restored mic functionality.  Yay!

[http://http://news.gmane.org/find-root.php?message_id=%3c1173546103.4531.283.camel%40razman.gruemaster.com%3e]("http://news.gmane.org/find-root.php?message_id=%3c1173546103.4531.283.camel%40razman.gruemaster.com%3e")

---

### Post by penvzila on 2007-03-19
That is really impressive that it took so little time.  I am extremely grateful.

---

### Post by diebels on 2007-03-24
I got a reject with this patch:
```
~/alsa-devel/alsa-driver-1.0.14rc3/alsa-kernel/pci/hda$ cat patch_conexant.c.rej 
*************** static void cxt5045_hp_automute(struct h
*** 634,640 ****
        spec->hp_present = snd_hda_codec_read(codec, 0x11, 0,
                                     AC_VERB_GET_PIN_SENSE, 0) & 0x80000000;
  
-       bits = (spec->hp_present || !spec->cur_eapd) ? 0x80 : 0;
        snd_hda_codec_amp_update(codec, 0x10, 0, HDA_OUTPUT, 0, 0x80, bits);
        snd_hda_codec_amp_update(codec, 0x10, 1, HDA_OUTPUT, 0, 0x80, bits);
  }
--- 549,555 ----
        spec->hp_present = snd_hda_codec_read(codec, 0x11, 0,
                                     AC_VERB_GET_PIN_SENSE, 0) & 0x80000000;
  
+       bits = (spec->hp_present || !spec->cur_eapd) ? 0x80 : 0; 
        snd_hda_codec_amp_update(codec, 0x10, 0, HDA_OUTPUT, 0, 0x80, bits);
        snd_hda_codec_amp_update(codec, 0x10, 1, HDA_OUTPUT, 0, 0x80, bits);
  }
```
Edit: guess it doesn't matter, since it's some muting code for conexant 5045

---

### Post by penvzila on 2007-05-09
> **lapichiflati said:**
> The latest patch, 10 march 2007 brings the CXT5047 aka Waikkiki up to date with distortion (mostly) fixed and restored mic functionality.  Yay!

[http://http://news.gmane.org/find-root.php?message_id=%3c1173546103.4531.283.camel%40razman.gruemaster.com%3e]("http://news.gmane.org/find-root.php?message_id=%3c1173546103.4531.283.camel%40razman.gruemaster.com%3e")


What do I apply this patch to, the latest source, or the older source that the previous patches patched?

---

### Post by penvzila on 2007-05-09
Nevermind, apparently the patches are already part of the latest release.

---

