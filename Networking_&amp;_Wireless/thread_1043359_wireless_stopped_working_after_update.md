---
title: "wireless stopped working after update"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by adamgram on 2009-01-18
Hello.  I'm looking for help fixing my girlfriend's laptop.  She's running Ubuntu 8.04 on a Compaq Presario A900 with an Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)  (that's what lspci tells me anyway).  The wireless card uses a restricted driver.

A couple of weeks ago she got an Ubuntu update and afterwards the wireless wouldn't work.  Under System->Administration->Network no wireless connection is listed.  Under System->Administration->Hardware Drivers there are 2 restricted driers listed, Atheros Hardware Access Layer (HAL), and Support for Atheros 802.11 wireless LAN cards.  Both have the status of 'In use' and the check box under 'enabled' is unchecked.

This is where I'm confused.  My first thought was to enable the driver, but when I check the box to enable one, the status changes to 'needs system restart', so I restart, but when it comes back up, still not checked off as 'enabled'.

My next idea was to uninstall and reinstall the drivers, but since they aren't checked as 'enabled' in the first place, I don't know how to go about doing that!  If anyone can tell me how to do this or otherwise point me in the right direction, I'd be ever so appreciative!  Thanks!

---

### Post by kevdog on 2009-01-18
Your chipset the 242x is also known as the 5007 chipset.  There are two solutions for you that I know of for this chipset. Either a patched version of the madwifi drivers, or the ath5k driver.  I'm guessing you may have had a kernel update??  -- not exactly sure.  The ath5k driver is available in the backport repositories.  You need to edit your /etc/apt/sources.list to enable the backport repositories (Remove the # sign from the repository line).  You then just need to do a sudo aptitude update && sudo aptitude safe-upgrade and I think the driver will be automatically installed for you!

---

### Post by adamgram on 2009-01-18
Thanks for the help.  Still no luck though, I enabled the line with the backports and ran those upgrade lines in the terminal but still the same behavior.  I'm using the madwifi drivers.  Maybe I should try the other one?  It seems like a pretty simple thing for me to not be understanding, but how do I disable the driver?  According to the 'hardware drivers' they're in use but not enabled?  There's nothing to uncheck.

---

### Post by adamgram on 2009-02-02
bump

---

### Post by adamgram on 2009-02-08
Still trying to fix this... I found out some of the basics that could help me figure this out... namely how to see what driver is in use and how to blacklist installed drivers I don't want to use.  So lsmod is supposed to give a list of what drivers you're using right?  My outputs are listed below, can anyone help me pick out which one is controlling the wireless card?

Module                  Size  Used by
af_packet              23812  2 
ipv6                  267908  10 
i915                   32512  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  1 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
snd_hda_intel         346136  2 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
uvcvideo               58116  0 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
serio_raw               7940  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
evdev                  13056  7 
v4l2_common            18304  2 uvcvideo,videodev
psmouse                40336  0 
ath_pci               101024  0 
wlan                  207728  1 ath_pci
snd_seq_dummy           4868  0 
ath_hal               192592  1 ath_pci
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  19856  0 
output                  4736  1 video
wmi_acer                9644  0 
button                  9232  0 
battery                14212  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
ac                      6916  0 
intel_agp              25492  1 
pcspkr                  4224  0 
snd                    56996  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                34760  3 drm,intel_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
soundcore               8800  1 snd
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sg                     36880  0 
sd_mod                 30720  4 
ata_piix               19588  0 
pata_acpi               8320  0 
usb_storage            73792  0 
libusual               19236  1 usb_storage
8139cp                 24704  0 
ata_generic             8324  0 
ahci                   28548  3 
ehci_hcd               37900  0 
libata                159600  4 ata_piix,pata_acpi,ata_generic,ahci
8139too                27520  0 
mii                     6400  2 8139cp,8139too
scsi_mod              151436  5 sr_mod,sg,sd_mod,usb_storage,libata
uhci_hcd               27024  0 
usbcore               146412  6 uvcvideo,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36488  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3

---

### Post by adamgram on 2009-02-08
der...

ath_hal               192592  1 ath_pci
wlan                  207728  1 ath_pci

nm

---

### Post by adamgram on 2009-02-08
fixed!  I downloaded another driver a while ago (i don't know where I got it, I searched everywhere online to make sure I had the latest one, but something is really screwy with madwifi.org right now), I just didn't know how to install it.  here's what I did, by all means anyone let me know if I did something wrong...

under /etc/modprobe.d/blacklist I added the line "blacklist ath_pci"
I then cd'd my way to where the driver's tarball was extracted and type 'sudo make install', rebooted, and it worked! HORRAY!!!

---

