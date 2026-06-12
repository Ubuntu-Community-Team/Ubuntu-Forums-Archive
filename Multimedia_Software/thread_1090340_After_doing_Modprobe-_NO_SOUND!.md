---
title: "After doing Modprobe- NO SOUND!"
date: 2009-03-08
forum: Multimedia Software
---

### Post by kelinu on 2009-03-08
Hi,
So, my problem is that I have my sound card a Realtek ALC 883, and it was working fine out of the box.  I got audio playbacka dn everything but what I did not get Microphone Support.  I searched around a bit and came to [this]("http://www.linuxquestions.org/questions/linux-hardware-18/microphone-does-not-work-with-realtek-alc883-hda-555391/")
I scrolled down a little, and came across the following command: modprobe -i snd-hda-intel model=6stack-dig.  The guy said that everything should work after that, so I tried it.  I then tried to record and got the usual result...nothing.  So nothing fixed there.  Then I tried to play some audio and got an unusual result...an error telling me: The audio device is busy. Is another application using it?

So then I kind of freaked and remembered that I could fish out my motherboard driver cd so that just maybe there were some drivers for linux for my sound card. There were.  They came with a nifty script to do all the installing for you.  I installed, rebooted, and tried to play some audio. Same error.  I then opened up the Sound Mixer (the default one in the panel) and went to file-->Change Device.  And there was Realtek ALC883 (OSS Mixer).  I freaked again, selected it and tried to play some audio again. Same error.

So now I need that if I had just not done that modprobe command and installed the drivers my Mic and Audio would work....so is there any way to stop the modprobe or something?

Help is EXTREMELY appreciated,

Michael

---

### Post by kelinu on 2009-03-08
*bump*

---

### Post by fayezderya on 2009-03-08
hi modprobe -i will load the module

try modprobe -r this will unload the module. since your problems started after this command executed. 

type the same command as before but replace the -i option with the -r.

so your new command will be. 

modprobe -r snd-hda-intel model=6stack-dig

---

### Post by kelinu on 2009-03-08
> **fayezderya said:**
> hi modprobe -i will load the module

try modprobe -r this will unload the module. since your problems started after this command executed. 

type the same command as before but replace the -i option with the -r.

so your new command will be. 

modprobe -r snd-hda-intel model=6stack-dig


After doing that command, I get FATAL: Module snd_hda_intel is in use.

What now!?

---

### Post by Ravernomina on 2009-03-08
try going into sound system>preferences>sound see if you can find the option for  ALSA. if so set everything for alsa accept for your sound capture and ur sound mixer should be set on your sound card. If that does not work try looking around for the Pulse audio option u can use that for now until this problem is solved :l

    Ravernomina

P.S. Set ur mixer to ur Sound card but ALSA mixer. as an example say ur card is intel so it would look like this Intel (alsa Mixer)

---

### Post by fayezderya on 2009-03-09
as the "comprehensive sound problem solution guide" says at this link 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
your sound might be working properly but after a while "due to tinkering" it stops working. it would be a good idea to uninstall the sound package and reinstall every thing from a fresh copy. 

the code to reinstall is 

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

and to reinstall them back again

sudo apt-get install linux-sound-base alsa-base alsa-utils

remark while removing the packages, the gdm package might be removed along with another package, so you might need to reinstall these packages again with the same command: 

sudo apt-get install gdm

I hope this will work. since you had no problem before.

---

### Post by kelinu on 2009-03-09
> **fayezderya said:**
> as the "comprehensive sound problem solution guide" says at this link 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
your sound might be working properly but after a while "due to tinkering" it stops working. it would be a good idea to uninstall the sound package and reinstall every thing from a fresh copy. 

the code to reinstall is 

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

and to reinstall them back again

sudo apt-get install linux-sound-base alsa-base alsa-utils

remark while removing the packages, the gdm package might be removed along with another package, so you might need to reinstall these packages again with the same command: 

sudo apt-get install gdm

I hope this will work. since you had no problem before.

Using your instructions, I get exactly the same problem as before, but now I also get another one where the Welcome Screen tells me that it cannot find the human theme in GDM.

Should I just go ahead and reformat or can you guys do something about my audio problem before formattting?

Why ME!? WHy ME!? :(

---

### Post by fayezderya on 2009-03-09
did gdm get uninstalled when you used the commands and if it did, did you reinstall gdm. 

did any package other than gdm get uninstalled in the process and did you reinstall them. 

if you can't remember

sudo apt-get update

will check if there is any packages to be installed. 

sudo apt-get install will install them. 

another thing is you can set your appearance to use another theme. 
go to system --> preferences --> appearance and change the theme. 
that is concerning the human theme. 

concerning the sound problem. 
did you get the same error back as in sound working but mic. not working. 

or did you get the same error back as in the sound did not work. 
do not format. I think there must be a way to fix this.

---

### Post by fayezderya on 2009-03-09
another question 

do you mean after reinstalling the alsa-base and alsa-utils packages from scratch you got the same error and nothing changed

also I need to know 

model of your laptop. 

and the out put of these commands 

aplay -l 

lspci

also the content of this file /etc/modprobe.d/alsa-base

---

### Post by fayezderya on 2009-03-09
also the out put of this command 

lsmod

---

### Post by MttJocy on 2009-03-10
> **kelinu said:**
> Using your instructions, I get exactly the same problem as before, but now I also get another one where the Welcome Screen tells me that it cannot find the human theme in GDM.

Should I just go ahead and reformat or can you guys do something about my audio problem before formattting?

Why ME!? WHy ME!? :(

With regards to the problem with the theme you can get the human theme back using this command:
> sudo apt-get install ubuntu-gdm-themes

This will install the ubuntu themes for GDM which include the default human theme.

Alternatively you could of course choose a different theme it is a matter of personal preference after all.  If you can't find any GDM themes you like try this command to add more themes to choose from.
> sudo apt-get install ubuntu-gdm-themes gdm-themes
That will install all the themes available in the repository, still other themes for GDM can be found online.


I am sorry that none of this helps with your original audio problem but I hoped it may be useful to you anyway in light of your other issue.

---

### Post by kelinu on 2009-03-10
fayezderya:

Thanks for your interest in my problem.  Lets forget about the new problem with the themes for now and focus more on the audio problem...I'm sure I can sort out the themes on my own.

I got the same problem exactly as before...no sound and no microphone even after reinstalling alsa-base and alsa-utils.  I do not use a laptop...but you can see the specs of my computer in the signature.  I have [this motherboard]("http://www.ciao.co.uk/ASUS_P5VD2_X__6574888")
  
Output of commands:

aplay -l 
> **** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


lspci
> 00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
05:05.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)


lsmod
> Module                  Size  Used by
vmnet                  48340  13 
af_packet              23812  2 
vsock                  21952  0 
vmci                   55136  1 vsock
vmmon                  71200  0 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  2 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
sbs                    15112  0 
video                  19856  0 
output                  4736  1 video
sbshc                   7680  1 sbs
container               5632  0 
dock                   11280  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
lp                     12324  0 
snd_hda_intel         344728  1 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
evdev                  13056  4 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
psmouse                40336  0 
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
serio_raw               7940  0 
snd                    56996  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
acx                    98692  0 
gspca                 643920  0 
soundcore               8800  1 snd
nvidia               7825536  34 
videodev               29440  1 gspca
v4l2_common            18304  1 videodev
v4l1_compat            15492  1 videodev
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
button                  9232  0 
via_agp                11136  1 
agpgart                34760  2 nvidia,via_agp
i2c_viapro              9876  0 
i2c_core               24832  2 nvidia,i2c_viapro
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  3 
pata_via               13316  0 
sata_via               12420  2 
pata_jmicron            7040  0 
floppy                 59588  0 
ehci_hcd               37900  0 
ahci                   28420  0 
r8169                  32900  0 
pata_acpi               8320  0 
uhci_hcd               27024  0 
ata_generic             8324  0 
usbcore               146028  5 acx,gspca,ehci_hcd,uhci_hcd
libata                159344  6 pata_via,sata_via,pata_jmicron,ahci,pata_acpi,ata_generic
scsi_mod              151436  4 sr_mod,sg,sd_mod,libata
thermal                16796  0 
processor              36872  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 


Content of /etc/modprobe.d/alsa-base:
> # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

I really appreciate the help you're giving me,
Michael

---

### Post by kelinu on 2009-03-20
*bump*

---

