---
title: "Wired network is &quot;unmanaged&quot; and consequently not working"
date: 2013-04-26
forum: Networking &amp; Wireless
---

### Post by GeorgeLSpencer on 2013-04-26
After trying to unsuccessfully setup a wireless network on Ubuntu 12.04 desktop TLS, using ndiswrappers, I now find that my ethernet connection is not working. When I look in system Settings, under Network, it shows the Wired network as "unmanaged". Looking at the ethernet hub, I can see that the three lights (10/100, half/full, and link/act) are slowly blinking. With a normal Ethernet connection, these lights will be continually on. Obviously, I have somehow messed up the network settings. Is there some way to get this working consistently. It is strange, but with some boots, the ethernet will start correctly; but with most boots it does not.  On some reboots the wired network will show "Cable unplugged"; even when it isn't. Quite frustrating.

---

### Post by Hadaka on 2013-04-26
Hi George and welcome to the forum.
The ndiswrapper is usually a last resort
wireless driver and may be what is hosing
up your ethernet, Let's unload that and then
see which driver would be best for your wireless.
please open a terminal  ctrl/alt/t..then COPY and
paste the following..
To unload the ndiswrapper..some of these commands
"may" produce an error..but..it is important to do each
one anyway.
```
sudo modprobe -rfv ndiswrapper
sudo apt-get remove --purge ndisgtk ndiswrapper*
sudo rm /etc/modprobe.d/ndis*
sudo rm -r /etc/ndiswrapper/*
sudo rm /etc/modprobe.d/blacklist

```
then boot and see if your ethernet is back to normal
*IF ethernet returns to normal...please COPY these
commands at a terminal..
```
lspci -nn | egrep '0200|0280
lsmod
rfkill list all
```
then post the results.
thanks.

---

### Post by Iowan on 2013-04-26
Are there more than these two lines in */etc/network/interfaces*?
```
auto lo
iface lo inet loopback

```

---

### Post by GeorgeLSpencer on 2013-04-26
Hi Hadaka,

Thanks for the suggestions. I removed ndiswrappers, as per your instructions, cold booted a couple of times, but without any success on the networking side. Here are the results of the commands: 

```
george@spencer-i7:~$ lspci -nn | egrep '0200|0280'
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
george@spencer-i7:~$ lsmod
Module                  Size  Used by
vesafb                 13518  1 
parport_pc             32115  0 
ppdev                  12850  0 
bnep                   17791  2 
rfcomm                 38104  0 
bluetooth             189585  10 bnep,rfcomm
coretemp               13362  0 
kvm_intel             127736  0 
kvm                   365556  1 kvm_intel
usblp                  17893  0 
gpio_ich               13160  0
mxm_wmi                12894  0 
snd_hda_codec_realtek    64959  1 
microcode              18396  0 
psmouse                91022  0 
serio_raw              13032  0 
snd_hda_intel          32983  3 
ndiswrapper           196777  0 
snd_hda_codec         116477  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
snd_pcm                81124  2 snd_hda_intel,snd_hda_codec
lpc_ich                16993  0 
snd_seq_midi           13133  0 
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18745  1 mxm_wmi
snd                    62675  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13078  0 
nvidia              10258145  40 
soundcore              14636  1 snd
i7core_edac            23302  0 
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
edac_core              46231  3 i7core_edac
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
firewire_ohci          36110  0 
firewire_core          61957  1 firewire_ohci
floppy                 60214  0 
crc_itu_t              12628  1 firewire_core
r8169                  56853  0 
ahci                   25621  0 
libahci                26166  1 ahci
pata_jmicron           12652  0 
usb_storage            39757  2 
george@spencer-i7:~$ rfkill list all
george@spencer-i7:~$ 
```

However, I note that ndiswrappers is still showing in the lsmod listing. 
Thanks for your help!

---

### Post by GeorgeLSpencer on 2013-04-26
Hi Lowan,

I have tried many things with /etc/network/interfaces but none appear to have any effect. The configuration I was last using was:
```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 10.0.0.1
network 10.0.0.0
netmask 255.255.255.0
gateway 10.0.0.138
dns-nameservers 61.9.226.33 61.9.211.33
```

Commenting out each of the lines from auto eth0 down, so that the file only mentions the loopback interface, and then rebooting, has no effect. 

One other characteristic which may mean something to you, I have noticed that after the grub menu I now get a Ubuntu startup screen, and the message: "Waiting for Network configuration". Not sure whether this is relevant.

---

### Post by Hadaka on 2013-04-27
Hi, thanks for the info, please do..
```
cat /etc/modules
```
*IF ndiswrapper is in /etc/modules
then do...
```
sudo gedit etc/modules
```
and REMOVE it.
also..i noticed only the info on your wired card was
displayed..not the wireless..so please do ...
```
lspci -nn | grep 0280
```
i would also do as suggested and save the info in your
/etc/network/interfaces then edit that file and remove all
but..
```
auto lo
iface lo inet loopback 
```
then restore the info once you get the wireless working.
post the results.

---

### Post by GeorgeLSpencer on 2013-04-27
Hi Hadaka,

You were right about the /etc/modules still having an entry for ndiswrappers. I removed this, cleaned all lines from /etc/network/interfaces, other than the loopback entries, and the Ethernet is now working. The Ethernet is not necessarily working when I initially log in to Ubuntu; but if I wait, it eventually comes up. The delay is rather variable.

Thanks for your help, and that is one interesting pizza. I won't close this right now; as I want to see whether it is still working tomorrow.

---

