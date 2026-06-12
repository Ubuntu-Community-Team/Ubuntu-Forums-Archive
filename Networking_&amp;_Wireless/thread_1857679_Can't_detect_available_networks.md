---
title: "Can't detect available networks"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by sellarsjanet52 on 2011-10-10
I recently deactivated wireless networks on my mini computer when I went on a plane trip. Now I can't get it back to show networks. I've spent about an hour between reading the manuals and calling Dell for support. My problem is still not resolved.

---

### Post by wildmanne39 on 2011-10-10
Hi, welcome to the forum! Please open a terminal ctrl+alt+t then copy and paste these commands into it, then copy and paste the output here:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by sellarsjanet52 on 2011-10-11
[FONT=Batang][SIZE=3]Got it. Thanks. I copied and pasted below and also attached the Word document if that is easier to read.[/SIZE][/FONT]

[FONT=Batang][SIZE=3]janet@janet:~$ cat /etc/lsb-release; uname -a[/SIZE][/FONT]
[FONT=Batang][SIZE=3]DISTRIB_ID=Ubuntu[/SIZE][/FONT]
[FONT=Batang][SIZE=3]DISTRIB_RELEASE=8.04[/SIZE][/FONT]
[FONT=Batang][SIZE=3]DISTRIB_CODENAME=hardy[/SIZE][/FONT]
[FONT=Batang][SIZE=3]DISTRIB_DESCRIPTION="Ubuntu 8.04.2"[/SIZE][/FONT]
[FONT=Batang][SIZE=3]Linux janet 2.6.24-29-lpia #1 SMP Thu May 26 09:13:33 UTC 2011 i686 GNU/Linux[/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]janet@janet:~$ sudo lshw -C network[/SIZE][/FONT]
[FONT=Batang][SIZE=3][sudo] password for janet:[/SIZE][/FONT]
[FONT=Batang][SIZE=3]sudo: lshw: command not found[/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]janet@janet:~$ lspci -nnk | grep -iA2 net[/SIZE][/FONT]
[FONT=Batang][SIZE=3]lspci: invalid option -- k[/SIZE][/FONT]
[FONT=Batang][SIZE=3]Usage: lspci [<switches>][/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]-v Be verbose[/SIZE][/FONT]
[FONT=Batang][SIZE=3]-n Show numeric ID's[/SIZE][/FONT]
[FONT=Batang][SIZE=3]-nn Show both textual and numeric ID's (names & numbers)[/SIZE][/FONT]
[FONT=Batang][SIZE=3]-b Bus-centric view (PCI addresses and IRQ's instead of those seen by the CPU)[/SIZE][/FONT]
[FONT=Batang][SIZE=3]-x Show hex-dump of the standard portion of config space[/SIZE][/FONT]
[FONT=Batang][SIZE=3]-xxx Show hex-dump of the whole config space (dangerous; root only)[/SIZE][/FONT]
[FONT=Batang][SIZE=3]-xxxx Show hex-dump of the 4096-byte extended config space (root only)[/SIZE][/FONT]
[FONT=Batang][SIZE=3]-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]] Show only devices in selected slots[/SIZE][/FONT]
[FONT=Batang][SIZE=3]-d [<vendor>]:[<device>] Show only selected devices[/SIZE][/FONT]
[FONT=Batang][SIZE=3]-t Show bus tree[/SIZE][/FONT]
[FONT=Batang][SIZE=3]-m Produce machine-readable output[/SIZE][/FONT]
[FONT=Batang][SIZE=3]-i <file> Use specified ID database instead of /usr/share/misc/pci.ids.gz[/SIZE][/FONT]
[FONT=Batang][SIZE=3]-D Always show domain numbers[/SIZE][/FONT]
[FONT=Batang][SIZE=3]-M Enable `bus mapping' mode (dangerous; root only)[/SIZE][/FONT]
[FONT=Batang][SIZE=3]-P <dir> Use specified directory instead of /proc/bus/pci[/SIZE][/FONT]
[FONT=Batang][SIZE=3]-H <mode> Use direct hardware access (<mode> = 1 or 2)[/SIZE][/FONT]
[FONT=Batang][SIZE=3]-F <file> Read configuration data from given file[/SIZE][/FONT]
[FONT=Batang][SIZE=3]-G Enable PCI access debugging[/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]janet@janet:~$ iwconfig[/SIZE][/FONT]
[FONT=Batang][SIZE=3]lo no wireless extensions.[/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]eth0 no wireless extensions.[/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]sms no wireless extensions.[/SIZE][/FONT]
 
 
[FONT=Batang][SIZE=3]janet@janet:~$ rfkill list all[/SIZE][/FONT]
[FONT=Batang][SIZE=3]bash: rfkill: command not found[/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]janet@janet:~$ lsmod[/SIZE][/FONT]
[FONT=Batang][SIZE=3]Module Size Used by[/SIZE][/FONT]
[FONT=Batang][SIZE=3]parport_pc 36260 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]ppdev 10372 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]parport 37704 2 parport_pc,ppdev[/SIZE][/FONT]
[FONT=Batang][SIZE=3]sms1xxx 42116 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]mbm 7424 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]cdc_ether 7168 1 mbm[/SIZE][/FONT]
[FONT=Batang][SIZE=3]cdc_acm 18976 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]uvcvideo 58244 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]compat_ioctl32 2304 1 uvcvideo[/SIZE][/FONT]
[FONT=Batang][SIZE=3]videodev 29440 1 uvcvideo[/SIZE][/FONT]
[FONT=Batang][SIZE=3]v4l1_compat 15492 2 uvcvideo,videodev[/SIZE][/FONT]
[FONT=Batang][SIZE=3]v4l2_common 18304 2 uvcvideo,videodev[/SIZE][/FONT]
[FONT=Batang][SIZE=3]rfcomm 41488 2[/SIZE][/FONT]
[FONT=Batang][SIZE=3]l2cap 25600 13 rfcomm[/SIZE][/FONT]
[FONT=Batang][SIZE=3]hci_usb 16540 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]bluetooth 60900 5 rfcomm,l2cap,hci_usb[/SIZE][/FONT]
[FONT=Batang][SIZE=3]i915 32640 2[/SIZE][/FONT]
[FONT=Batang][SIZE=3]acpi_cpufreq 10796 1[/SIZE][/FONT]
[FONT=Batang][SIZE=3]cpufreq_stats 7104 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]cpufreq_conservative 8712 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]cpufreq_powersave 2688 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]cpufreq_userspace 5156 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]drm 82324 3 i915[/SIZE][/FONT]
[FONT=Batang][SIZE=3]intel_agp 25492 1[/SIZE][/FONT]
[FONT=Batang][SIZE=3]agpgart 34760 3 drm,intel_agp[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_seq_midi 9376 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_seq_oss 35456 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_seq_dummy 4868 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_pcm_oss 42144 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_hda_intel 368176 2[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_seq_midi_event 8320 2 snd_seq_midi,snd_seq_oss[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_rawmidi 25760 1 snd_seq_midi[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_hwdep 10500 1 snd_hda_intel[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_pcm 78724 2 snd_pcm_oss,snd_hda_intel[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_page_alloc 11400 2 snd_hda_intel,snd_pcm[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_mixer_oss 17920 1 snd_pcm_oss[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_seq 54224 6 snd_seq_midi,snd_seq_oss,snd_seq_dummy,snd_seq_midi_event[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_timer 24836 2 snd_pcm,snd_seq[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_seq_device 9612 5 snd_seq_midi,snd_seq_oss,snd_seq_dummy,snd_rawmidi,snd_seq[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd 56996 15 snd_seq_oss,snd_seq_dummy,snd_pcm_oss,snd_hda_intel,snd_rawmidi,snd_hwdep,snd_pcm,snd_mixer_oss,snd_seq,snd_timer,snd_seq_device[/SIZE][/FONT]
[FONT=Batang][SIZE=3]soundcore 8800 1 snd[/SIZE][/FONT]
[FONT=Batang][SIZE=3]aes_i586 33536 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]dm_crypt 14980 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]dm_mod 60612 1 dm_crypt[/SIZE][/FONT]
[FONT=Batang][SIZE=3]ieee80211_crypt_tkip 11520 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]r8169 34692 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]ieee80211_crypt 6912 1 ieee80211_crypt_tkip[/SIZE][/FONT]
[FONT=Batang][SIZE=3]iTCO_wdt 13092 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]iTCO_vendor_support 4868 1 iTCO_wdt[/SIZE][/FONT]
[FONT=Batang][SIZE=3]serio_raw 7940 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]psmouse 68200 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]iptable_nat 8324 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]nf_nat 20268 1 iptable_nat[/SIZE][/FONT]
[FONT=Batang][SIZE=3]nf_conntrack_ipv4 19208 2 iptable_nat[/SIZE][/FONT]
[FONT=Batang][SIZE=3]nf_conntrack 65984 3 iptable_nat,nf_nat,nf_conntrack_ipv4[/SIZE][/FONT]
[FONT=Batang][SIZE=3]iptable_mangle 3712 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]iptable_filter 3840 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]ip_tables 14820 3 iptable_nat,iptable_mangle,iptable_filter[/SIZE][/FONT]
[FONT=Batang][SIZE=3]x_tables 16132 2 iptable_nat,ip_tables[/SIZE][/FONT]
[FONT=Batang][SIZE=3]fuse 50324 1[/SIZE][/FONT]
[FONT=Batang][SIZE=3]ahci 28548 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]squashfs 49032 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]unionfs 78032 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]ehci_hcd 37900 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]usbhid 32256 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]hid 38912 1 usbhid[/SIZE][/FONT]
[FONT=Batang][SIZE=3]isofs 36132 0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]zlib_inflate 18176 2 squashfs,isofs[/SIZE][/FONT]

---

### Post by wildmanne39 on 2011-10-11
Hi, first most of my commands were not recognized I am guessing because it is such an old version of ubuntu.

You should upgrade to at least 10.04 it has long term support.

With 8.04 you will not be able to get updates or install software from synaptic, this includes security updates so your system will be at risk for viruses that it would not normally be at risk for.

If you still want to keep 8.04 try this command please:
```
lspci -nn | grep 0280
```
Also install rfkill and run this command again if it will let you install applications.
```
rfkill list all
```
Thank you

---

### Post by sellarsjanet52 on 2011-10-11
Ok. Thank you. I'll upgrade to the newest supported version.

---

### Post by wildmanne39 on 2011-10-11
Hi, your welcome!

---

