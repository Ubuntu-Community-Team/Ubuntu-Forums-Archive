---
title: "Can't install wireless network driver"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by indra_best on 2010-09-10
**[COLOR=Black]Can't install wireless network driver. The output of 'lsmod' is:[/COLOR]**

Module                  Size  Used by
ndiswrapper           183164  0
i915                  172552  2
drm                   142208  3 i915
ipv6                  239348  10
sbs                    10940  0
sbshc                   4500  1 sbs
acpi_cpufreq            7808  0
cpufreq_stats           4728  0
cpufreq_ondemand        7080  2
cpufreq_conservative     7048  0
cpufreq_performance     1300  0
cpufreq_powersave       1268  0
freq_table              3476  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
iptable_filter          2324  0
ip_tables              10916  1 iptable_filter
x_tables               13592  1 ip_tables
parport_pc             24292  0
lp                      9412  0
parport                30572  2 parport_pc,lp
snd_hda_codec_idt      55764  1
btusb                  11592  0
joydev                  9728  0
snd_hda_intel          24712  0
bluetooth              54148  1 btusb
mac80211              204728  0
snd_hda_codec          57204  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6776  1 snd_hda_codec
snd_pcm_oss            37728  0
snd_mixer_oss          14324  1 snd_pcm_oss
snd_pcm                67704  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
cfg80211               61268  1 mac80211
uvcvideo               58016  0
led_class               3608  0
input_polldev           3132  0
psmouse                41732  0
videodev               37056  1 uvcvideo
v4l1_compat            13336  2 uvcvideo,videodev
serio_raw               5016  0
video                  18024  1 i915
snd_seq_dummy           2424  0
output                  2388  1 video
rtc_cmos               10156  0
rtc_core               15792  1 rtc_cmos
rtc_lib                 2388  1 rtc_core
snd_seq_oss            27328  0
iTCO_wdt               10584  0
iTCO_vendor_support     2840  1 iTCO_wdt
snd_seq_midi            5952  0
snd_rawmidi            19488  1 snd_seq_midi
snd_seq_midi_event      5972  2 snd_seq_oss,snd_seq_midi
snd_seq                47568  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
wmi                     5960  0
snd_timer              19068  2 snd_pcm,snd_seq
snd_seq_device          6048  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    50468  12 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               5856  1 snd
intel_agp              26108  1
shpchp                 31560  0
snd_page_alloc          7836  2 snd_hda_intel,snd_pcm
agpgart                29356  3 drm,intel_agp
dell_laptop             3380  0
rfkill                  9328  3 dell_laptop
dcdbas                  7092  1 dell_laptop
evdev                   9120  15
sg                     25064  0
sky2                   45464  0
ata_generic             4536  0
pata_acpi               3892  0
fuse                   53104  1

[B]And the output of 'sudo rmmod ssb' is:

ERROR: Module ssb does not exist in /proc/modules

Please help me...[/B]

---

### Post by MaindotC on 2010-09-10
Please try following the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  Why are you trying to remove ssb?

---

### Post by indra_best on 2010-09-17
hello, i have tried [Ubuntu Wireless Troubleshooting Guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") but i am getting confused. 

The o/p of [FONT=monospace]
[/FONT]
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

and
sudo ifup lo

ifup: interface lo already configured

and
sudo ifup eth0

ifup: interface eth0 already configured

---

### Post by bkratz on 2010-09-17
> **indra_best said:**
> hello, i have tried [Ubuntu Wireless Troubleshooting Guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") but i am getting confused. 

The o/p of [FONT=monospace]
[/FONT]
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

and
sudo ifup lo

ifup: interface lo already configured

and
sudo ifup eth0

ifup: interface eth0 already configured




Generally eth0 is your wired connection to ethernet. What did you discover was your wireless card from the guide?


You could also find with

lspci -nn

---

### Post by grahammechanical on 2010-09-17
Hi Indra_best

May I suggest that we go back to the beginning? I am not an expert so I cannot give you much help. Have you noticed the network manager icon in the top panel to the right? It should show several curved bands radiating upwards. There should be a red exclamation sign against it. This tells you that the network connection has failed, whether it is by wireless or wire (ethernet). Left click on it. Do you see a list of nearby wireless networks. If so then your wireless card is being detected. Try right clicking and unchecking Enable networking and then check it again to enable it. What happens?

regards

---

