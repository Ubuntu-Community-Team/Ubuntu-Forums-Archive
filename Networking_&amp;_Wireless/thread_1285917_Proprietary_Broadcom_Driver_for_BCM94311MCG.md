---
title: "Proprietary Broadcom Driver for BCM94311MCG"
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by nbesteman2136 on 2009-10-08
After updating through the ethernet card, Ubuntu managed to find the proprietary driver necessary to make my BCM94311MCG card (14e4:4311) operational. The problem is, however, that after each reboot, Ubuntu seems to 'forget' that the proprietary driver is working and the Wi-Fi card is thus deactivated and the driver in System -> Adminstrator -> Hardware Drivers is listed as 'Not in Use.' All one needs to do is deactivate the driver and then reactivate it. When this is done, the Wi-Fi begins to work immediately, but then Ubuntu demands a Reboot to make the necessary changes. When Ubuntu is rebooted, however, it again forgets that the driver works and the process must be repeated. Thus, the Wi-Fi does work but it is annoying to deactivate and then reactivate it after each reboot. Is there a fix to this problem? 
   Thanks for any assistance!

---

### Post by mikewhatever on 2009-10-08
Look at lsmod output to see if the module is loaded. If that's the problem, add the module to /etc/modules so that it loads at boot.

---

### Post by nbesteman2136 on 2009-10-08
I'm so sorry, but i'm such a newbie that it is unclear to me how to check the lsmod...Could you provide a step-by-step instruction please?
  Thank you again for your response....

---

### Post by nbesteman2136 on 2009-10-08
Ok,
  Sure enough as you said, when Ubuntu first boots there is no driver loaded for the Wi-Fi card according to lsmod...In fact, in Device Manager, there is no line for 'info.linux.driver,' at boot. When the Hardware Driver is deactivated and then reactivated, however, the line 'info.linux.driver' suddenly appears with the string 'wl.' 
   I then typed in /etc/modules in the terminal as suggested, but the terminal then informs me that permission is denied. Why am I being denied permission when I am the administrator of the computer?

---

### Post by 01mf02 on 2009-10-08
With WiFi NOT working, do the following:

1.) Go to Application -> Accessories -> Terminal.
2.) Type 'lsmod' and press ENTER. Look for stuff like 'bcm' etc.

If you can't find anything appropriate at first, do your procedure in Hardware Drivers to make WiFi work, then repeat the steps above.

Should you find something bcm-like now, post it here.

---

### Post by 01mf02 on 2009-10-08
To respond to your new reply, you can edit every file with root rights by running "gksu gedit" or "sudo nano".

---

### Post by nbesteman2136 on 2009-10-08
Nothing resembling 'BCM' appears in lsmod. The only thing that looks similar to the Broadcom driver listed in Device Manager under info.linux.driver is 'wl' which is the below, third line down....

LSMOD:

af_packet              23812  4 
ieee80211_crypt_tkip    11648  0 
wl                   1278932  0 
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,wl
ipv6                  268164  10 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
ppdev                  10372  0 
powernow_k8            16704  1 
cpufreq_ondemand        9740  1 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
sbs                    15112  0 
container               5632  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
snd_hda_intel         346264  2 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78724  2 snd_hda_intel,snd_pcm_oss
ndiswrapper           192920  0 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               7940  0 
wmi_acer                9644  0 
video                  19856  8 
output                  4736  1 video
snd                    56996  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                40336  0 
nvidia               7825536  26 
button                  9232  0 
i2c_nforce2             7680  0 
agpgart                34760  1 nvidia
battery                14212  0 
ac                      6916  0 
i2c_core               24832  2 nvidia,i2c_nforce2
k8temp                  6656  0 
soundcore               8800  1 snd
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
evdev                  13056  8 
pcspkr                  4224  0 
ext3                  136968  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
sata_nv                27656  2 
pata_amd               14212  0 
ata_generic             8324  0 
forcedeth              51980  0 
pata_acpi               8320  0 
ehci_hcd               37900  0 
ohci_hcd               26640  0 
libata                159728  4 sata_nv,pata_amd,ata_generic,pata_acpi
scsi_mod              151692  4 sg,sr_mod,sd_mod,libata
usbcore               146412  4 ndiswrapper,ehci_hcd,ohci_hcd
thermal                16796  0 
processor              36616  2 powernow_k8,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3584  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 


Any ideas?

---

### Post by mikewhatever on 2009-10-08
Yes, wl is the module. I suspect it's not loaded at boot, and you can check that with 
**lsmod | grep wl**. If the output is blank after a reboot, run [s]gksudo nautilus /etc/modules[/s] 'gksudo gedit /etc/modules' and add wl.
To manually load the module, run **sudo modprobe wl**

---

### Post by nbesteman2136 on 2009-10-08
As you expected command 'lsmod | grep wl' returns a blank after a reboot. Typing command 'sudo modprobe wl' instantly adds the info.linux.driver string of 'wl' to the Wi-Fi card properties in Device Manager and instantly connects the Wi-Fi card to my wireless network. 
    It seems, as you said, that this manual fix is again forgotten after each reboot, at which point 'sudo modprobe wl' needs to be added again within the terminal. 
    Also attempted the nautilus fix you suggested by typing 'gksudo nautilus /etc/modules'
 However, when this is typed the terminal immediately lists an error message found below:

########################################################

nathan@Azia:~$ gksudo nautilus /etc/modules
Initializing nautilus-share extension

** (nautilus:6071): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

seahorse nautilus module shutdown

########################################################

When the Nautilus window does appear, an error message is displayed reading - 'Couldn't Display /etc/modules' - 'The location is not a folder.' 

   Doing the manual fix isn't a hassle...but Ubuntu should automatically load 'wl' Furthermore where is the Nautilus error message coming from, not to mention the fact that it doesn't seem to allow an addition to /etc/modules?

---

### Post by mikewhatever on 2009-10-08
Oops, sorry, wrong command. I'll correct in the post above too.

gksudo gedit /etc/modules

---

### Post by kevdog on 2009-10-08
I think the command would be

echo wl | sudo tee -a /etc/modules

---

### Post by nbesteman2136 on 2009-10-09
Yes!!! The network card driver now loads immediately after reboot. Thank you so much!

---

