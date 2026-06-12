---
title: "Intel onboard audio not detected"
date: 2011-07-08
forum: Multimedia Software
---

### Post by Osmodivs on 2011-07-08
Hello.
I have an Intel ***DG35EC*** motherboard (*Ubuntu 11.04 64bits*) , according to the MoBo spec data sheet it has:      [B]Intel 82801HB (ICH8)
Realtek ALC888S audio codec[/B]
I installed the Realtek codec with ALSA 1.2.4. like the instructions say: ./configure --with-cards=hda-intel
This is what I get with lspci -vvv 
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
    Subsystem: Intel Corporation Device d701
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 9
    Region 0: Memory at e3120000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [60] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
            ClockPM- Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; Disabled- Retrain- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100 v1] Virtual Channel
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1
        Arb:    Fixed- WRR32- WRR64- WRR128-
        Ctrl:    ArbSelect=Fixed
        Status:    InProgress-
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=01
            Status:    NegoPending- InProgress-
        VC1:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=1 ArbSelect=Fixed TC/VC=80
            Status:    NegoPending- InProgress-
    Capabilities: [130 v1] Root Complex Link
        Desc:    PortNumber=0f ComponentID=00 EltType=Config
        Link0:    Desc:    TargetPort=00 TargetComponent=00 AssocRCRB- LinkType=MemMapped LinkValid+
            Addr:    00000000fed1c000
    Kernel modules: snd-hda-intel
```I can't open alsamixer even though I reinstalled alsa-utils alsa-base
```
:~$ alsamixer
cannot open mixer: No such file or directory
aplay -l
aplay: device_list:240: no soundcards found...
:~$ sudo dimecode
Handle 0x0011, DMI type 10, 6 bytes
On Board Device Information
    Type: Sound
    Status: Enabled
    Description: Intel(R) High Definition Audio Device

```I turned ON the audio in the BIOS. I do not know what else to do, all info in the net is about specific hardware, is there a way to fix mine?

---

### Post by lidex on 2011-07-09
I don't recommend compiling alsa drivers from scratch for the inexperienced as things can go wrong and have in this case. What was the reason behind using the realtek driver? 

Start with a re-install of default drivers.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

Next use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by Osmodivs on 2011-07-09
Well, I wanted to use the Realtek driver because that's what the Intel's Technical Product Specification
says: Realtek ALC888S audio codec
So, why not?
I'll try your suggestion tomorrow, I want to have a fresh start.
(for some reason I can't acces ALSA web page and not even that wget link you gave me.)

---

### Post by lidex on 2011-07-10
The alsa kernel module supports the realtek codecs for the most part. I would only recommend the realtek driver if you can't get it to work otherwise. See this post on alsa-info script:
[http://ubuntuforums.org/showpost.php?p=11031344&postcount=4](http://ubuntuforums.org/showpost.php?p=11031344&postcount=4)

---

### Post by Syndicalist on 2011-07-10
Did they really remove aptitude in the latest Ubuntu?

---

### Post by lidex on 2011-07-10
> **Syndicalist said:**
> Did they really remove aptitude in the latest Ubuntu?

I don't know when or if it was in  the default install, but it hasn't been for awhile. I believe synaptic shares the same fate in oneiric.

---

### Post by Syndicalist on 2011-07-10
Im not sure I like the direction Ubuntu is taking. If I buy a tablet it will probably be Meego, not Unity. I wish Cononical had just focused on making an awesome desktop. Its getting weird around here.

---

### Post by Osmodivs on 2011-07-10
Hey.
I cant download and execute the .sh script from the wget link you posted.
```
--2011-07-10 16:13:59--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org... 77.48.224.243
Connecting to www.alsa-project.org|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in headers.
Retrying.
```
After 20 tries, it gives up, I've been trying to download it for hours. I can't even acces the alsa-project web page, I looked in the net for the script for downloading and I found this one in here:
[http://www.vitki.net/book/page/alsa-info-sh](http://www.vitki.net/book/page/alsa-info-sh)
I download and executed the file but it does nothing, it just stays there after I press the OK option in the greetings window.
Is there a way you can send me the .sh script so I can execute it an then paste it to pastebin the result? I would really apreciate your help.

---

### Post by lidex on 2011-07-10
See this post:
[http://ubuntuforums.org/showpost.php?p=11031344&postcount=4](http://ubuntuforums.org/showpost.php?p=11031344&postcount=4)

---

### Post by Osmodivs on 2011-07-10
Here is the result from the ALSA script:
[http://pastebin.com/nk90MuLk](http://pastebin.com/nk90MuLk)

Can you tell what's wrong with my system just by looking at that?
What is your diagnosis?

---

### Post by lidex on 2011-07-10
Go into your bios and reset to default. After booting up check this output:
```
aplay -l
```

---

### Post by Osmodivs on 2011-07-11
After resetting the BIOS to default, here is the result:
```

aplay: device_list:240: no soundcards found...

```... [-( ...

---

### Post by lidex on 2011-07-11
> **Osmodivs said:**
> After resetting the BIOS to default, here is the result:
```

aplay: device_list:240: no soundcards found...

```... [-( ...

Did you uninstall the realtek driver? Then this:
```
sudo apt-get install --reinstall linux-image-`uname -r` && sudo dpkg-reconfigure linux-image-`uname -r`
```

---

### Post by Osmodivs on 2011-07-11
I think I alredy did that, that was yourfirst suggestion.
But I did it again:
```
sudo apt-get install --reinstall linux-image-`uname -r` && sudo dpkg-reconfigure linux-image-`uname -r`
[sudo] password for osmodivs: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0 B/36.4 MB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 272027 files and directories currently installed.)
Preparing to replace linux-image-2.6.38-8-generic 2.6.38-8.42 (using .../linux-image-2.6.38-8-generic_2.6.38-8.42_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.38-8-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
Setting up linux-image-2.6.38-8-generic (2.6.38-8.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.38-8.42 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.38-8.42 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
 * dkms: running auto installation service for kernel 2.6.38-8-generic                                                           
 *       nvidia-current (270.41.19)...                                                                                    [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.38-8.42 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.38-8.42 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
 * dkms: running auto installation service for kernel 2.6.38-8-generic                                                           
 *       nvidia-current (270.41.19)...                                                                                    [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
```Rebooted and...
```
aplay: device_list:240: no soundcards found...
```I forgot to mention I have dual boot, perhaps thats one of the problems?

---

### Post by Osmodivs on 2011-07-11
I do not know what else to paste, that is all the info I have:

```
 cat /proc/asound/cards
--- no soundcards ---
osmodivs@Djiin:~$ lsmod | grep snd
snd_hda_intel          33211  0 
snd_hda_codec         103804  1 snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  8 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
```

---

### Post by lidex on 2011-07-14
No, what I meant was to reverse the process of the realtek install. Don't they provide a method of restoring default drivers if their package fails?

---

