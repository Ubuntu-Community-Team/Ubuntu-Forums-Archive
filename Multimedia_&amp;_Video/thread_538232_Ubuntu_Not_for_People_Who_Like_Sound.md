---
title: "Ubuntu: Not for People Who Like Sound"
date: 2007-08-29
forum: Multimedia &amp; Video
---

### Post by MusicProducer on 2007-08-29
There is no sound in Ubuntu.

---

### Post by misfitpierce on 2007-08-29
You may want to show your hardware so we can help with this. lscpi in terminal should show it. Also don't say Ubuntu : Not for ppl who dont like sound. Try something like Ubuntu : Not for ppl who dont try to figure out how to make sound work... kidding it should be Help with sound not working in Ubuntu. :)

---

### Post by MusicProducer on 2007-08-29
> **misfitpierce said:**
> You may want to show your hardware so we can help with this. lscpi in terminal should show it. Also don't say Ubuntu : Not for ppl who dont like sound. Try something like Ubuntu : Not for ppl who dont try to figure out how to make sound work... kidding it should be Help with sound not working in Ubuntu. :)

I'd tried that, people just stared and said nothing. Thanks for the advice, but it gave me:

> 
me@me-desktop:~$ lscpi
bash: lscpi: command not found
me@me-desktop:~$ 


---

### Post by Gremlinzzz on 2007-08-29
Try a kernel upgrade report back if it works for you
[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)
:guitar:

---

### Post by SoPa on 2007-08-29
There are a lot of thread about this problem. With Feisty's upgrade, a new group has been created for Audio devices. By default, you are not part of this group and therefore, you cannot hear/change the sounds settings.

Open a terminal, and type in "gksu users-admin"
Enter your password
Select your account and click on the "Properties" button
Select the "User Privileges" Tab
Make sure "Use audio devices" is selected and click OK
Log Off and Log On again, you should here the sound back

Also, the command that mistfitpierce wanted you to give a try at was "lspci" not lscpi, damn keyboard :D

---

### Post by MusicProducer on 2007-08-29
> **SoPa said:**
> Also, the command that mistfitpierce wanted you to give a try at was "lspci" not lscpi, damn keyboard :D
Thank you. I got:
```
me@me-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:08.0 Communication controller: Intel Corporation 536EP Data Fax Modem
00:0e.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)
me@me-desktop:~$ 

```

---

### Post by MusicProducer on 2007-08-29
> **SoPa said:**
> Make sure "Use audio devices" is selected

I did what you said, and "Use audio devices" was already selected. Still no sound here.

Sound was working until a couple of day ago, when I installed totem-xine in place of totem-gstreamer. I did this in order to play a DVD, which hadn't worked with totem-gstreamer.

The sound disappeared when I switched back to totem-gstreamer, IIRC. Now, there's no sound, whether I use xine or gstreamer.

---

### Post by MusicProducer on 2007-08-29
> **Gremlinzzz said:**
> Try a kernel upgrade report back if it works for you
[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)
:guitar:
Thanks for the advice. I hesitate to do that, since at one point I did have sound with my current kernel, and I probably shouldn't experiment until my luck improves.

---

### Post by MusicProducer on 2007-08-30
> **MusicProducer said:**
> Still no sound here.
.

---

### Post by MusicProducer on 2007-08-30
I'm a programmer, I don't mind debugging, but I need a clue where to start.

---

### Post by yabbadabbadont on 2007-08-30
```
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
```
The Alsa driver for that sound chip is notoriously buggy...  which is why I have it disabled in my BIOS and slapped a cheap Soundblaster card in my machine to use instead.  However, the place to start debugging this would be to check which sound related kernel modules are loaded.  What is the output when you run "lsmod" in a terminal window?  (You should see snd-via82xx in there somewhere or it won't work)

---

### Post by MusicProducer on 2007-08-30
> **yabbadabbadont said:**
> What is the output when you run "lsmod" in a terminal window?
```
me@me-desktop:~$ lsmod
Module                  Size  Used by
isofs                  36284  1 
udf                    85252  0 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
via                    44160  3 
drm                    81044  4 via
ipv6                  268960  8 
powernow_k8            16064  0 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9228  1 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8200  0 
freq_table              5792  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
tc1100_wmi              8068  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
dock                   10268  0 
container               5248  0 
video                  16388  0 
ac                      6020  0 
battery                10756  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
sbs                    15652  0 
i2c_ec                  6016  1 sbs
button                  8720  0 
sbp2                   23812  0 
lp                     12452  0 
fuse                   46612  0 
snd_via82xx            29208  1 
gameport               16520  1 snd_via82xx
snd_ac97_codec         98464  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9472  1 snd_via82xx
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
usblp                  14848  0 
usbhid                 26592  0 
snd                    54020  13 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hid                    27392  1 usbhid
ide_cd                 32672  1 
cdrom                  37664  1 ide_cd
pcspkr                  4224  0 
k8temp                  6656  0 
amd64_agp              13700  1 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
soundcore               8672  1 snd
i2c_viapro             10132  0 
i2c_core               22656  2 i2c_ec,i2c_viapro
agpgart                35400  2 drm,amd64_agp
af_packet              23816  2 
tsdev                   8768  0 
evdev                  11008  3 
via82cxxx              10372  0 [permanent]
generic                 5124  0 [permanent]
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  3 
floppy                 59524  0 
ehci_hcd               34188  0 
ata_generic             9092  0 
uhci_hcd               25360  0 
usbcore               134280  5 usblp,usbhid,ehci_hcd,uhci_hcd
sata_via               12548  2 
libata                125720  2 ata_generic,sata_via
scsi_mod              142348  4 sbp2,sg,sd_mod,libata
via_velocity           33668  0 
crc_ccitt               3072  1 via_velocity
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
thermal                14856  0 
processor              31048  2 powernow_k8,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
me@me-desktop:~$ 

```
> You should see snd-via82xx in there somewhere or it won't work
It's in there.

---

### Post by MusicProducer on 2007-08-30
> **yabbadabbadont said:**
> The Alsa driver for that sound chip is notoriously buggy...  which is why I have it disabled in my BIOS and slapped a cheap Soundblaster card in my machine to use instead.
Thanks for the info. For what it's worth, I had sound for about 6 weeks, until I needed to switch from totem-gstreamer to totem-xime in order to play a DVD.

---

### Post by yabbadabbadont on 2007-08-30
> **MusicProducer said:**
> Thanks for the info. For what it's worth, I had sound for about 6 weeks, until I needed to switch from totem-gstreamer to totem-xime in order to play a DVD.

Whoops...  I read that in your earlier post and completely forgot about it.  Sorry.  I've been up all night.  :)

Let's eliminate a few things to see if you can get any sound at all.  In a terminal window, run alsamixer and make sure that both the master and pcm channels are unmuted and set to a reasonable sound level.   (hit escape to exit) Now cd into the /usr/share/sounds directory.  There should be some sound files there with which you can test.  Now try to play one using the 'aplay' alsa command line utility.  e.g.  aplay somefile.wav  Does that produce any sound?

I'm heading off to bed but I'll check back here in the afternoon (US/Central time).

---

### Post by MusicProducer on 2007-08-30
> **yabbadabbadont said:**
> Whoops...  I read that in your earlier post and completely forgot about it.  Sorry.  I've been up all night.  :)
No problem. I really appreciate any ideas here; plus, anything I learn about the Ubuntu sound-system in the process will be helpful if I ever attempt to code audio-software.
> Let's eliminate a few things to see if you can get any sound at all.  In a terminal window, run alsamixer and make sure that both the master and pcm channels are unmuted and set to a reasonable sound level.   (hit escape to exit)
done
> Now cd into the /usr/share/sounds directory.  There should be some sound files there with which you can test.  Now try to play one using the 'aplay' alsa command line utility.  e.g.  aplay somefile.wav  Does that produce any sound?
No sound from that:
```
me@me-desktop:/usr/share/sounds$ cd /usr/share/sounds
me@me-desktop:/usr/share/sounds$ aplay error.wav 
Playing WAVE 'error.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Mono
me@me-desktop:/usr/share/sounds$ aplay info.wav 
Playing WAVE 'info.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Mono
me@me-desktop:/usr/share/sounds$ 
```
> I'm heading off to bed but I'll check back here in the afternoon (US/Central time).
I appreciate it.

---

### Post by yabbadabbadont on 2007-08-30
Since that didn't work, and no errors or warnings were displayed, I would guess that there is something wrong at a pretty low level in the system.  Beats me what it could be though.  :?  If you have /home on its own partition, you might consider backing up your /etc directory and then reinstalling.  That would be a last resort though.  You might try searching in Synaptic for packages with 'alsa' in the name.  Select only the ones that are already installed.  Then right click on one of them and take the option to reinstall the package.  (or you may just want to wait a bit and see if someone else has any better suggestions :))

---

### Post by MusicProducer on 2007-08-31
> **yabbadabbadont said:**
> Since that didn't work, and no errors or warnings were displayed, I would guess that there is something wrong at a pretty low level in the system.  Beats me what it could be though.  :?  If you have /home on its own partition, you might consider backing up your /etc directory and then reinstalling.  That would be a last resort though.  You might try searching in Synaptic for packages with 'alsa' in the name.  Select only the ones that are already installed.  Then right click on one of them and take the option to reinstall the package.  (or you may just want to wait a bit and see if someone else has any better suggestions :))
When I double-click the speaker icon, go to the File:Change Device menu, and change the device away from "VIA 8237 (Alsa mixer)" to "Realtek ALC358D (OSS Mixer)", I also get no sound. I don't know if this bypasses the Alsa mixer? But, for what it's worth.

---

### Post by MusicProducer on 2007-08-31
> **yabbadabbadont said:**
> You might try searching in Synaptic for packages with 'alsa' in the name.  Select only the ones that are already installed.  Then right click on one of them and take the option to reinstall the package.
done; still no sound.

---

### Post by yabbadabbadont on 2007-08-31
The OSS layer is emulated by Alsa now days.  It was a good idea to try though.  I'm out of ideas.  :(

---

### Post by MusicProducer on 2007-08-31
> **yabbadabbadont said:**
> Since that didn't work, and no errors or warnings were displayed, I would guess that there is something wrong at a pretty low level in the system.  Beats me what it could be though.  :?  If you have /home on its own partition, you might consider backing up your /etc directory and then reinstalling.  That would be a last resort though.  You might try searching in Synaptic for packages with 'alsa' in the name.  Select only the ones that are already installed.  Then right click on one of them and take the option to reinstall the package.  (or you may just want to wait a bit and see if someone else has any better suggestions :))
Thanks for your help; all your ideas seem worthwhile. I'm not going to reinstall, as I believe I installed correctly the first time.

I have written low-level audio code for Windows. I have written commercial sound drivers for Creative Labs. I am willing and able to work for free to debug this problem I'm having with Ubuntu. What a disappointment.

---

### Post by MusicProducer on 2007-08-31
> **yabbadabbadont said:**
> The OSS layer is emulated by Alsa now days.  It was a good idea to try though.  I'm out of ideas.  :(
Thanks for the info.

---

### Post by pljones on 2007-08-31
I take it you can get sound when running Windows, just not when running Ubuntu?

---

### Post by MusicProducer on 2007-09-01
> **pljones said:**
> I take it you can get sound when running Windows, just not when running Ubuntu?
I had sound when I was running Windows on this computer. I haven't run Windows since I installed Ubuntu, but I need to install a Windows partition anyway, for other reasons. I'm in a bad mood for reasons unrelated to Ubuntu, so I'm sorry if I sound like sour grapes about software that's free. Ubuntu is clearly awesome, even if sound doesn't happen to work for me.

I'll restate the point:
> Sound was working until a couple of day ago, when I installed totem-xine in place of totem-gstreamer. I did this in order to play a DVD, which hadn't worked with totem-gstreamer. 
The sound disappeared when I switched back to totem-gstreamer, IIRC. Now, there's no sound, whether I use xine or gstreamer.
I'm guessing my loss of sound was related to switching back and forth between gstreamer and xine, but that's all I know, and I don't understand what those things are.

---

### Post by Sepero on 2007-09-12
gstreamer and xine are video/media players.

Try creating a guest user on your system. See if your guest user has sound.
If the guest does Not have sound, then we know it is a problem with something in the system.
If the guest does have sound, then we know it's a problem in your local settings.

---

