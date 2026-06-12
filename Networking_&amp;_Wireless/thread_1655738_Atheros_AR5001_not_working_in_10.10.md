---
title: "Atheros AR5001 not working in 10.10"
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by bones221 on 2010-12-30
I got a used computer (Toshiba Satellite A215-S5829) for Christmas, and it was running Vista *shudder* so I decided to wipe the hard drive, and install the latest Ubuntu.  This is my first real foray into linux, and I've loved the system, but the only problem I've had with is so far is I can't get the wireless to work.  I believe the card it has is Atheros AR5001, and I've tried installing the "madwifi" drivers, but I can't get them to register.  I've been following the suggestions of dozens of different forum posts and answers I've found scattered around the internet, but I haven't been able to get anything to work correctly.

When I view the "Additional Drivers" in System > Administration, it says "Alternate Atheros "madwifi" driver: This driver is activated but in use," but when I click on the internet icon in the top panel, it only gives me the wired connection.  It used to also give me the wireless option, just without ever successfully finding any wireless networks to which it could connect.  Like I said, I've done about a half-dozen different things without any success.  Any help would be appreciated.

---

### Post by PatchesTheCaveman on 2010-12-30
Hi bones221, sorry to hear you're having trouble with your wireless.

I'm going to have you collect some information so we can try and figure out what's going on.  First, go to Applications > Accessories > Terminal on your top panel.  Then, in the black box that appears, type the following and press Enter:
```
lspci -v
```

Copy and paste that into a post here (or if you can find it, just the part that talks about your wireless card).  That will tell us all the details of your card and what drivers are presently loaded for it.

Then, run this command:
```
lsmod
```
and copy and paste it here too.  Those are all the kernel modules, so maybe we can see if the madwifi driver is installed but not loaded.

Next, run this command:
```
sudo iwconfig
```
You'll need to provide your password.  That will tell us about all the wireless network interfaces on your machine.  Copy and paste it here too.

Finally, run this:
```
sudo grep -i madwifi && grep -i ath5k
```
and copy and paste it here.  That will show us any error messages from the kernel regarding your hardware.

Thanks a lot!

---

### Post by bones221 on 2010-12-30
This is going to be 3/4's wacky because I'm viewing/replying to the post on my iPod while running Terminal on my laptop. If you need any more in-depth info, I'll have to wait until Monday when I can get a wired connection again. Anyway, "lspci" tells me it's the AR5001 Atheros wireless adapter, and one of the lines says "Kernel modules: ath_pci, ath5k". Neither module appears in "lsmod". "iwconfig" reports only "lo" and "eth0" and they both say "no wireless extensions". And the last command doesn't seem to be doing anything. Not successfully, anyway. How long is it supposed to take? All I get is a blank line in the Terminal window for several minutes (Ithink it's been about 10).

---

### Post by bones221 on 2011-01-04
K, so in the process of following one suggestion after another, I thought that maybe I had just gummed up everything.  So I re-installed, and, following the suggestion found here: [https://help.ubuntu.com/10.10/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.10/internet/C/troubleshooting-wireless.html) I went through ndiswrapper.  I found and installed the net5211.inf through the Windows Wireless Drivers, and it says "net5211 / Hardware present: Yes" but I still can't access any wireless networks.  Also, while clicking through the network icon at the top panel, I think I accidentally disabled wireless networks, and now it won't even appear for me to re-enable it.

Also, here are the results of those commands (I haven't installed the madwifi again, yet)

lspci -v:
```
14:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
    Subsystem: AMBIT Microsystem Corp. AR5007EG 802.11bg NIC
    Flags: fast devsel, IRQ 19
    Memory at f8200000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel modules: ath5k

```

lsmod:
```

Module                  Size  Used by
ndiswrapper           184207  0 
aes_i586                7280  185 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
dm_crypt               11385  0 
joydev                  8735  0 
snd_hda_codec_realtek   217980  1 
snd_hda_intel          22107  2 
pcmcia                 35973  0 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_7xx1               3766  0 
psmouse                59033  0 
tifm_core               6089  1 tifm_7xx1
yenta_socket           21518  0 
pcmcia_rsrc            10566  1 yenta_socket
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore                880  1 snd
serio_raw               4022  0 
shpchp                 29886  0 
k8temp                  3132  0 
i2c_piix4               8635  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
radeon                825934  3 
ttm                    56633  1 radeon
ahci                   19013  0 
drm_kms_helper         30200  1 radeon
sdhci_pci               6339  0 
firewire_ohci          21106  0 
drm                   168054  5 radeon,ttm,drm_kms_helper
video                  18712  0 
ati_agp                 5202  0 
output                  1883  1 video
sdhci                  15890  1 sdhci_pci
led_class               2633  1 sdhci
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
libahci                21667  3 ahci
i2c_algo_bit            5168  1 radeon
r8169                  36489  0 
pata_atiixp             3288  0 
agpgart                32011  3 ttm,drm,ati_agp
mii                     4425  1 r8169

```

sudo iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

And as always, running sudo grep -i ath5k results in absolutely nothing.  How long should it take to return the results?  Am I doing something wrong?  Is there something I should be doing before I run that?

---

