---
title: "ICH6 AC'97 Audio Controller - No sound!"
date: 2006-01-20
forum: Multimedia &amp; Video
---

### Post by AndriusKulikauskas on 2006-01-20
Hi. Last month I purchased a Barebones laptop and haven't had any success to get the sound to work.  Please help me!

Here is what I get from the lspci command:

0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)

(There is a note that the latter may create a naming conflict, but the instructions didn't help in my case.) [http://www.aalbiol.upv.es/ACER.html](http://www.aalbiol.upv.es/ACER.html)

I also found this: "For the soundcard, Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller, you must enable the CONFIG_SND_HDA_INTEL in the kernel. With Alsa it works without problems."
[http://www.lorenzobettini.it/linux/LinuxSonyVaioVGN-S5VP_B#Kernel](http://www.lorenzobettini.it/linux/LinuxSonyVaioVGN-S5VP_B#Kernel)
I tried that but perhaps I didn't do it right.

This may be relevant (from the same page): Modem
The modem is integrated in the sound card, Soft V92 Data Fax Modem with Smart CP, and it's obviously a softmodem. The scanModem utility downloaded from [http://linmodems.technion.ac.il](http://linmodems.technion.ac.il) reports this:
Though not displayed, an embedded soft modem may reside in this Audio card:
 0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03) Support is in an active developement stage. There is always an audio codec(s)  + (optionally) modem. ALSA HDA setup is likely automatic, but can be maually done with:
	su - root
	modprobe snd-hda-intel
 Information on the chips should map into /proc/asound/ folders.

I went through the troubleshooting page, but nothing has helped so far.
[http://linux.iuplog.com/default.asp?item=94639](http://linux.iuplog.com/default.asp?item=94639)

I note that when I start up /dev/dsp does not have any read or write privileges for the regular user.  However, when I set chmod 666, that has no effect.  I also don't get any sound if I start up an application as root.  I note that after making the change, when I reboot, it goes back to what it was (I can look that up).

I have scavenged around for different tips and found quite a lot of tricks but nothing has helped.  It would be good if I could pin down the problem some how.

I also noticed that my laptop has an fn button and the F2 button has a blue icon that seems related to sound.  But when I press them, it doesn't seem to change the situation.  I will call the store to ask about that.

I ran with Baltic-Knoppix and there was no sound, but it did tell me that I have installed modules for ac97_codec (Yamaha YMF7xx PCI audio) and i810_audio (Intel ICH audio support).

I found advice on setting different channels in Alsamixer on or off, but that hasn't helped so far.

I don't have any real evidence yet that my sound card actually works (or that it doesn't).

I downloaded some modules to have ALSA run and I have selected it as my mixer.
I also found this: [http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Intel#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Intel#matrix)

How might I proceed?

I'm stuck!

Thank you, 
Andrius

---

### Post by AndriusKulikauskas on 2006-01-21
I'm not sure this is relevant, but when my computer shuts down there is a message Shutting Down LVM Volume Groups, but I suppose that is normal.

Also, in the middle of working with Kolourpaint, I got an informational message from Artsmessage:  Sound server informational message: Error while intializing sound server:   device:default can't be opened for playback (No such device).  The sound server will continue, using the null output device.

Any thoughts on what I might do next?

---

### Post by FarEast on 2006-01-23
Have you read the thread?
[http://ubuntuforums.org/showthread.php?t=87849&highlight=ICH6](http://ubuntuforums.org/showthread.php?t=87849&highlight=ICH6)

---

### Post by AndriusKulikauskas on 2006-01-25
FarEast, Thank you - that was quite helpful.  Just as they described, I needed to disable the external amplifier.  However, sound has only appeared in a few scattered places, such as Flash pages and also once I got a test signal with the Multimedia Systems Selector (but currently I can't get that to work either).  I think that at some point I followed some instructions that were given to help get Flash pages to work (I think I installed ESD).  

Also, I noticed that when I set dev/dsp to chmod 666, as advised in the troubleshooting guide, then after I reboot it is set back to it was before.  I can't get that change to stick.  And it doesn't seem to help with the sound, either.

What should I do next?

---

### Post by FarEast on 2006-01-25
Hi;) ,

Just in case, please paste the outputs from:
$ cat /proc/asound/cards
$ cat /proc/asound/modules

I think that the module is 'snd-intel8x0'.
How about trying 'snd-intel8x0m' instead?
You can try it in the following way:
1. add 'snd-intel8x0' in /etc/hotplug/blacklist
2. Describe 'alias snd-card-0 snd-intel8x0m' in /etc/modprobe.d/sound ,
   do 'sudo update modules' and restart.

If you can compile alsa-utils from source, 'alsaconf' script is available.
[http://ubuntuforums.org/showpost.php?p=667871&postcount=7](http://ubuntuforums.org/showpost.php?p=667871&postcount=7)

---

### Post by AndriusKulikauskas on 2006-01-27
FarEast, Thank you for helping!

cat cards    yields:

0 [ICH6           ]: ICH4 - Intel ICH6
                     Intel ICH6 with AD1981B at 0xc0000800, irq 17

cat modules    yields:

0 snd_intel8x0

I have read that snd_intel8x0m is for the modem's sound.

This is from /etc/hotplug/blacklist :
# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
snd_intel8x0m

I will try out your advice.  Thank you!

---

### Post by AndriusKulikauskas on 2006-01-27
FarEast, I tried your suggestion, but it didn't notice it to have any effect.

Here is my output from lspci :

0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Po rt (rev 04)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 1 (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #3 (rev 04)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB 2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH 6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Contro ller (rev 04)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 565 3
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4362 (rev 19)
0000:06:07.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:06:07.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:06:07.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
0000:06:07.4 0805: Texas Instruments: Unknown device 8034
0000:06:09.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)

and from lsmod :

Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
speedstep_centrino      7380  1
cpufreq_userspace       4444  1
cpufreq_stats           5124  0
freq_table              4484  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  2
fglrx                 245412  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  4
rtc                    11832  0
hci_usb                13192  2
bluetooth              43012  7 rfcomm,l2cap,hci_usb
ipw2200                92680  0
firmware_class          9472  1 ipw2200
ieee80211              27012  1 ipw2200
ieee80211_crypt         5636  2 ipw2200,ieee80211
ohci1394               30644  0
yenta_socket           22540  1
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
sk98lin               166872  1
tpm_nsc                 6528  0
tpm                     9504  1 tpm_nsc
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
intel_agp              21276  1
agpgart                32328  2 fglrx,intel_agp
dm_mod                 50364  1
joydev                  9280  0
tsdev                   7616  0
evdev                   9088  1
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
sr_mod                 15652  0
sbp2                   21128  0
scsi_mod              124872  2 sr_mod,sbp2
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  0
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  2 speedstep_centrino,thermal
fan                     4740  0
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104316  4 hci_usb,ehci_hcd,uhci_hcd
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_disk               16128  3
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  761
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

Any thoughts?

---

### Post by FarEast on 2006-01-27
Hi AndriusKulikauskas,
Thanks for giving a try at my thought.
Well...
The only suggestion I can make now is trying an OSS driver.
Keep 'snd-intel8x0' in the blacklist and add 'i810_audio' in /etc/modules.

---

### Post by AndriusKulikauskas on 2006-04-20
I finally got the sound card to work, it was a matter of turning off one check mark that was turned on in the volume control, I think.

---

### Post by StyngerSmash on 2006-04-28
Hello Andre!

I'm new to this forum. Was eagerly reading this thread and was ecstatic that you finally got your sound to work :D  

I've been using SimplyMEPIS on my BenQ S52 notebook (sound on-board Intel 915GM, ICH6 family) for almost a year now, and I've no luck with the sound as yet. But now that MEPIS has turned to Ubuntu for its source pools, I thought maybe that there was a solution in these forums somehow. 

Like you, I've tried many things already. I want to know EXACTLY what you think you did to make your sound card work. My kudzu -p and lspci readings are exactly like yours.

Looking forward to your reply!

Regards, 

- STYNGERSMASH -

---

### Post by AndriusKulikauskas on 2006-04-28
Stynger, Unfortunately I can't find the link, but it was something to do with a checkmark in the Volume Control (under Applications, Sound & Video) that needed to be unchecked.  Here is a link to my notes on various things I tried:
[http://www.findbetterways.info/wiki.cgi?FindBetterWays/TheOnlineToolshed/LinuxOnLaptops](http://www.findbetterways.info/wiki.cgi?FindBetterWays/TheOnlineToolshed/LinuxOnLaptops)
Best wishes!

---

### Post by aikishugyo on 2007-08-22
The correct settings are as follows (after much frustration and experimentation):

SWITCHES: Mic Capture ON
                   Mic Boost    ON
                   (Stereo Mic ON)

OPTION:     Mic Select MIC1

RECORDING: Capture must be at some non-zero volume

PLAYBACK: Mic OFF
                    PCM and/or mono and/or other playback should be at some non-zero volume

Mine does now work in SkyPE, yay!

---

