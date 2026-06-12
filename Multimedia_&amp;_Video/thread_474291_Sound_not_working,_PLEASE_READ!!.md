---
title: "Sound not working, PLEASE READ!!"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by Master_Z on 2007-06-14
I am new here, and I recently installed Ubuntu 7.04 (Feisty Fawn I think). I like it, but my sound wont play at all. I have downloaded MP3 codecs and my MP3s open and stream, but no sound plays. My soundcard is a sigmatel high definition audio codec, and my laptop is a gateway mt3705. Do I need to install linux specific drivers for it? If so, where can I find these? I could really use some sound right now, so PLEASE reply, Thank you.

---

### Post by coffeecat on 2007-06-15
> **Master_Z said:**
> My soundcard is a sigmatel high definition audio codec, and my laptop is a gateway mt3705. Do I need to install linux specific drivers for it?

Let's see if it's a problem of the soundcard being detected or a problem with the mp3-playing app. Go to System > Preferences > Sound. Press the Test button under Sound Events, Sound Playback. Do you hear anything?

If not, open a terminal and do:

```
sudo lspci
```Look for the line with 'Audio' in it and post that. That will tell us which sound chipset you have. If in doubt post the whole of the output. Remember that you can copy and paste from a terminal into the forum message box but that the keyboard shortcuts are different.

Now from a terminal, do:

```
sudo lsmod | grep snd
```That will list all the kernel sound modules (drivers) that you have in memory. Post the output.

**Edit:** Simple things first! :) I'm assuming you're using Ubuntu/gnome here and not Kubuntu/KDE. Look on the upper panel towards the right. There's a little icon like a loudspeaker. Double-click it and the Volume Control/Alsa mixer will open. Make sure all the channels are unmuted and the control sliders are near the top. It varies from hardware to hardware but PCM and Front are the important ones here.

---

### Post by audiedog on 2007-06-17
While I am not the original poster, I have the same problem on the same Gateway Laptop. Your assumptions are correct - I am using Ubuntu, and I checked the mixer for muted channels, there are none.  I checked the sound with the Test button as you suggested - a popup came up labeled "testing pipeline" with a progress bar that never got past 15% or so complete. When the sound didn't work after installing Ubuntu, I followed the advice in the article [HdaIntelSoundHowTo]("https://help.ubuntu.com/community/HdaIntelSoundHowto"). I downloaded and installed the newest ALSA driver, library and utilities. I also set the codec to 3stack, ref, and laptop in the alsa-base file. None of them worked after rebooting for each change. 

For reference purposes, this is a brand new model of laptop (only a month or two old), and it was built by Gateway to support the Windows Vista release. In the output below, the reference to SB450 HD Audio (rev 01) worries me, because perhaps the ALSA driver for SB450 is incompatible with the SB450 rev 01 of the sound card. I would really like to replace Vista for good on this laptop, but I need the sound to work for my daughter's movies. 

I appreciate your help.

P.S You asked the original poster to give you some information, and here are the results of those commands as you requested (I encourage the original poster to do this as well, particularly if that person did not follow the article linked to above):

output from ```
sudo lspci
```
-----------------------
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

output from ```
sudo lsmod grep snd
```
-------------------------------
snd_hda_intel         244632  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17792  1 snd_pcm_oss
snd_pcm                81028  2 snd_hda_intel,snd_pcm_oss
snd_seq_oss            35200  0 
snd_seq_midi_event      8576  1 snd_seq_oss
snd_seq                54000  4 snd_seq_oss,snd_seq_midi_event
snd_timer              24196  2 snd_pcm,snd_seq
snd_seq_device          9612  2 snd_seq_oss,snd_seq
snd                    56324  10 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm

---

### Post by Xaero Evo on 2007-06-17
err. i think i have the same problem too.. my laptop built in speaker doesnt work but when i plugged in my headphone, it works.. so dont mind if i seek help here .. 
here, this is the first output : ( i dont know which is the one :( )
> xaero@xaero-linux-laptop:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 110M / GeForce Go 7300 (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
xaero@xaero-linux-laptop:~$ 
and this is the second one.. :
> sudo lsmod | grep snd
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
xaero@xaero-linux-laptop:~$ 


---

### Post by coffeecat on 2007-06-17
**audiedog**, I have no experience of that ATI audio device, but a quick google showed me that there are quite a few people out there with the same problem. Also, a forum search came up with [this thread]("http://ubuntuforums.org/showthread.php?t=474425&highlight=ATI+Technologies+Inc+SB450+HDA+Audio") among others. Have a look at the last post. Perhaps the fix is there. I'm confused as to why configuring the use of the Intel sound kernel module should help but, as I said, I have no experience of the ATI device. There is a kernel module for the AC97 ATI device but perhaps the High Definition device uses the Intel HD driver. I really don't know.

Sorry I can't help any more than this.

**Xaero Evo**, yours is not the same issue as the OP. I would think your problem is a hardware one, but I could be wrong. You have a:

>  00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)and you have the correct kernel driver in memory, viz snd_hda_intel. Indeed you are getting sound. I suggest you start your own thread.

---

### Post by psyke83 on 2007-06-17
Hi,

Try opening a terminal, running "alsamixer", scrolling to the right to find the "External Amplifier" control, and press the "m" key to toggle its mute/unmute status, then try playing audio again.

---

### Post by eggdeng on 2007-06-17
> I also set the codec to 3stack, ref, and laptop in the alsa-base file.

I have seen that Gateway laptops with Sigmatel audio devices require you to add the line 

```
options snd-hda-intel probe_mask=1
```
or
```
options snd-hda-intel model=test enable-msi=1 probe-mask=1
```

to the end of  /etc/modprobe.d/alsa-base.

---

### Post by AJYablo on 2007-06-17
Gateway MX3422
no sound aswell...
Nothing muted in alsa or gnome.
I also tried 1.0.14

lspci:
```
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
```

lsmod
```
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm

```


Any ideas to get sound?

Thanks!

---

### Post by Xaero Evo on 2007-06-17
> **psyke83 said:**
> Hi,

Try opening a terminal, running "alsamixer", scrolling to the right to find the "External Amplifier" control, and press the "m" key to toggle its mute/unmute status, then try playing audio again.

OMG! Thank You soo much! now it works! .. but still its a litle strange.. i need to unmute Surround?
--but it works now.. thanks..
[img]http://xs216.xs.to/xs216/07251/alsamixerpic.jpg[/img]

---

### Post by bambit on 2007-06-23
lspci:

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)


victoria@victoria-laptop:~$ sudo lsmod | grep snd
snd_hdsp               51716  0 
snd_intel8x0           34332  1 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_usb_audio          79744  1 
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_pcm                79876  5 snd_hdsp,snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm_oss
snd_usb_lib            17280  1 snd_usb_audio
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_rawmidi            25472  3 snd_hdsp,snd_seq_midi,snd_usb_lib
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd_hwdep               9988  2 snd_hdsp,snd_usb_audio
snd                    54020  18 snd_hdsp,snd_intel8x0,snd_ac97_codec,snd_seq_oss,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_rawmidi,snd_seq_device,snd_hwdep
soundcore               8672  1 snd
snd_page_alloc         10888  3 snd_hdsp,snd_intel8x0,snd_pcm
usbcore               134280  6 snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd

when I run the tests from System > Preferences > Sound, i get beeps from the USB speakers, but nothing when i play movies or audio files.

---

### Post by oxalá on 2007-06-23
My sound plays well in all cases, but I can't seem to record from my microphone, even though I can hear audio from my mic.

02:0d.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)

snd_ens1371            27552  1 
gameport               16520  1 snd_ens1371
snd_ac97_codec         98464  1 snd_ens1371
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  1 snd_pcm

---

