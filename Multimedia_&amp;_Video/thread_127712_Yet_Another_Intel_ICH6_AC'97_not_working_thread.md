---
title: "Yet Another Intel ICH6 AC'97 not working thread"
date: 2006-02-09
forum: Multimedia &amp; Video
---

### Post by Ecm.ca.us on 2006-02-09
Yeah.

I have a Dell Optiplex GX280. The onboard sound card is not detected by System->Preferences->Sound or by the Volume Control app, but is detected by alsamixer. Needless to say, I have no sound.

I tried the instructions [here]("http://makuchaku.info/amnesty/#configuresoundproperly") first off. 

I also tried [this]("http://linux.iuplog.com/default.asp?item=94639"), [this]("https://wiki.ubuntu.com/HowToSetupSoundCards") ( intel8x0 is compiled, and seems to be detecting a sound card), [this]("https://wiki.ubuntu.com/HowToSetupSoundCards") (using alsa-base 1.0.9) and the instructions [here]("http://ubuntuforums.org/showthread.php?t=104757&highlight=AD1981B") (although I'm not getting the login drums).

[This]("http://ubuntuforums.org/showthread.php?t=87849") didn't apply, as I can't get into the preferences on Volume Control when it insists I have no sound card, but I did mute external amp in alsamixer.

I even [Googled]("http://www.google.com/search?hs=bOc&hl=en&lr=&client=firefox&rls=org.mozilla%3Aen-US%3Aunofficial&q=ubuntu+configure++Intel+ICH6+Analog+Devices+AD1981B+&btnG=Search"). Not a lot of help there.

Here's some troubleshooting output:

:~$ sudo cat /proc/asound/cards
0 [ICH6           ]: ICH4 - Intel ICH6
                     [COLOR="Red"]Intel ICH6 with AD1981B[/COLOR] at 0xdffffe00, irq 23

:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

:~$ lspci | grep audio
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

:~$ sudo ls -l /dev/dsp
crw-rw-rw-  1 root audio 14, 3 2006-02-09 05:57 /dev/dsp

:~$ dmesg | grep intel
[4294713.750000] intel8x0_measure_ac97_clock: measured 49254 usecs
[4294713.750000] intel8x0: clocking to 48000

:~$ sudo cat /etc/asound.conf

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

:~$ aplay -l
aplay: device_list:218: no soundcards found...

Interestingly enough, although I did a sudo chmod 666 /dev/dsp, I still can't get aplay to acknowledge the sound card unless I sudo it.

Everything I tried seemed to make it worse - it stops recognizing the card even this far - and at one point I broke alsamixer. The output above is the current state, as I reinstalled Breezy and went through the [configure sound properly]("http://makuchaku.info/amnesty/#configuresoundproperly") instructions again.

Please let me know what patently obvious step I missed, as I can't see it.

---

### Post by Ecm.ca.us on 2006-02-16
Got nothing, then? Good to know I'm not the only one stumped. 

I'm beginning to think it's a hardware problem.

---

### Post by monsieurcanard on 2006-02-18
I have the same problem :( There's this thread:
[http://ubuntuforums.org/showthread.php?t=76019&page=8&highlight=i915+sound](http://ubuntuforums.org/showthread.php?t=76019&page=8&highlight=i915+sound)

...but they're not using the same AC97 chipset as us. My laptop is a Packard Bell (NEC) EasyNote A8202.

I'm using Alsa 1.0.11rc2.

Matt :(

---

### Post by Ecm.ca.us on 2006-02-28
Still nothing.

I'm thinking USB sound card as a solution.

---

### Post by ecki on 2006-03-02
Alsa accesses the soundcards through /dev/snd/* and it seems you have no permissions to read/write these files.

               Ecki

---

### Post by Ecm.ca.us on 2006-03-02
**That** would be the patently obvious step I missed. 

Ran a chmod 666 on /dev/snd/* as I didn't have read/write permissions. I'll let y'all know when I have a minute to restart sound.

---

### Post by Ecm.ca.us on 2006-03-02
Nope, no joy:

> :~$ sudo ls -l /dev/dsp
crw-rw----  1 root audio 14, 3 2006-03-02 06:22 /dev/dsp
:~$ sudo chmod 666 /dev/dsp
:~$ sudo ls -l /dev/snd/ 
total 0
crw-rw----  1 root audio 116,  0 2006-03-02 06:22 controlC0
crw-rw----  1 root audio 116, 24 2006-03-02 06:22 pcmC0D0c
crw-rw----  1 root audio 116, 16 2006-03-02 06:22 pcmC0D0p
crw-rw----  1 root audio 116, 25 2006-03-02 06:22 pcmC0D1c
crw-rw----  1 root audio 116, 26 2006-03-02 06:22 pcmC0D2c
crw-rw----  1 root audio 116, 27 2006-03-02 06:22 pcmC0D3c
crw-rw----  1 root audio 116, 20 2006-03-02 06:22 pcmC0D4p
crw-rw----  1 root audio 116,  1 2006-03-02 06:21 seq
crw-rw----  1 root audio 116, 33 2006-03-02 06:21 timer
:~$ sudo chmod 666 /dev/snd
:~$ sudo chmod -R 666 /dev/snd
:~$ sudo ls -l /dev/snd/
total 0
crw-rw-rw-  1 root audio 116,  0 2006-03-02 06:22 controlC0
crw-rw-rw-  1 root audio 116, 24 2006-03-02 06:22 pcmC0D0c
crw-rw-rw-  1 root audio 116, 16 2006-03-02 06:22 pcmC0D0p
crw-rw-rw-  1 root audio 116, 25 2006-03-02 06:22 pcmC0D1c
crw-rw-rw-  1 root audio 116, 26 2006-03-02 06:22 pcmC0D2c
crw-rw-rw-  1 root audio 116, 27 2006-03-02 06:22 pcmC0D3c
crw-rw-rw-  1 root audio 116, 20 2006-03-02 06:22 pcmC0D4p
crw-rw-rw-  1 root audio 116,  1 2006-03-02 06:21 seq
crw-rw-rw-  1 root audio 116, 33 2006-03-02 06:21 timer
:~$ sudo ls -l /dev/dsp
crw-rw-rw-  1 root audio 14, 3 2006-03-02 06:22 /dev/dsp
:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: Permission denied
:~$ aplay -l
aplay: device_list:218: no soundcards found...
:~$ sudo /etc/init.d/alsa-utils restart  * Shutting down ALSA...                                                 [ ok ]
 * Setting up ALSA...                                                    [ ok ]
:~$ aplay -l
aplay: device_list:218: no soundcards found...
:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
:~$


---

### Post by Ecm.ca.us on 2006-03-02
I also note that my earlier chmod of /dev/dsp got reset. Can't say as I like that.

---

### Post by public_void on 2006-03-04
Hey, I had a kinda similar problem but my sound just stopped, fixed it now by changing settings in alsamixer. Sounds work fine now.

Heres some of mine outputs, hope you can compare to see if theres anything different. I had no sound for two days and it drove me mad.

Have you got all needed packages and do you know if it works in another OS, just to prove it works.

Packages I have (After a search for alsa):
alsa-utils
gstreamer0.8-alsa
libasound2
libasound2-dev
libesd-alsa0
libpt-plugins-alsa
linux-sound-base

```
lspci | grep audio
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
```

```
cat /proc/asound/cards
0 [ICH6           ]: ICH4 - Intel ICH6
                     Intel ICH6 with unknown codec at 0xb0040800, irq 9

```

```
ls -l /dev/dsp
crw-rw----  1 root audio 14, 3 2006-03-04 09:02 /dev/dsp

```

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
dmesg | grep intel
[4294700.946000] intel8x0_measure_ac97_clock: measured 49774 usecs
[4294700.946000] intel8x0: clocking to 48000
[4294701.935000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294736.323000] Modules linked in: i82365 rsrc_nonstatic pcmcia_core ipt_limit iptable_mangle ipt_LOG ipt_MASQUERADE iptable_nat ipt_TOS ipt_REJECT ip_conntrack_irc ip_conntrack_ftp ipt_state ip_conntrack iptable_filter ip_tables i915 drm video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi i2c_acpi_ec i2c_core button battery container ac ipv6 af_packet ndiswrapper rtc ipw2200 firmware_class ieee80211 ieee80211_crypt tpm_nsc tpm snd_intel8x0 snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc intel_agp agpgart nls_utf8 ntfs dm_mod joydev evdev tsdev psmouse mousedev parport_pc lp parport md ext3 jbd thermal processor fan usbhid 8139too 8139cp mii ehci_hcd uhci_hcd usbcore ide_cd cdrom ide_disk ide_generic piix ide_core unix vesafb capability commoncap vga16fb vgastate softcursor cfbimgblt cfbfillrect cfbcopyarea fbcon tileblit font bitblit

```

---

### Post by jam'ez on 2006-03-11
i have the same problem, i did the same as the above post. i get the same out come!
 aplay -l
the only difference is that i get the first subdevices as 1/1 where as you got 0/1 if that makes any difference?

**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Dont know what to do, alsa mixer looks fine too

---

### Post by pdangel on 2007-07-09
Sorry to resurrect an old thread. But after couple weeks of googling for help this thread repeatedly was the one on top. So I figured I would post here how I fixed the issue for myself.

I did not have an asound.conf file !!!!
Found a site that gave some steps on how to setup sound for Gnome and it fixed my issue (and I thought it was a GX 280 issue the whole time)

[http://makuchaku.info/amnesty/#configuresoundproperly](http://makuchaku.info/amnesty/#configuresoundproperly)

I followed all the steps, including removing the check boxes for sound clips to use ESD and with out restarting any processes I had sound on the next flash video clip I played.

Again I am hoping to post here and help any one else that has been looking a fix.

---

