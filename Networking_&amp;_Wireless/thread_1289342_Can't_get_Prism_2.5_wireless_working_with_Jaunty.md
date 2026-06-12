---
title: "Can't get Prism 2.5 wireless working with Jaunty"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by racingsnake on 2009-10-12
Hi - I know there are a lot of Atheros/Jaunty/wireless queries out there, but the fixes seem to be very config-specific, so please excuse one more...

Here's the config I'm working with:
- Tadpole Talin (OK, so old-ish, but not senile... Wireless worked OK on Intrepid)
- Intersil Prism 2.5 wireless adapter (onboard)
- Jaunty Jackalope (9.04)

What I would like to achieve is WPA connectivity... but I'm happy to start with no crypto first, if anyone can help me get that working.

Following a suggestion in another thread, I replaced Network Manager with WICD, but that just says "No Wireless Networks Found"; (wired connectivity is working fine, incidentally).

Some diagnostic data:

sudo lshw -C network 

shows 
network:0 (wired) as working, but 
network:1 as UNCLAIMED ... though it correctly identifies the adapter as a Prism 2.5 Wavelan chipset

iwconfig

shows the loopback and eth0 (wired) interfaces, but not eth1.

Also following other suggestions, I edited /etc/modprobe.d/blacklist
and added

orinoco_pci

in the hope that this would resolve a possible conflict between that and hostap...

but no improvement.


If I go to System -> Administration -> Hardware Drivers, there are no third party or proprietary drivers listed at all.


I hope someone can help...

---

### Post by chili555 on 2009-10-12
Please open a terminal and do:```
sudo modprobe hostap
```I believe that is the driver you want. Then do:```
lsmod | grep prism
```If you find any prism module loaded, unload it with:```
sudo rmmod -f prism**
```**whatever you found. It's fine if you found nothing. Now do:```
sudo lshw -C network
```Is your card still UNCLAIMED?> I would like to achieve is WPA connectivityNot likely with an ancient Prism 2.5, but let's get it working first before we ask it for its capabilities.

---

### Post by chili555 on 2009-10-12
> Not likely with an ancient Prism 2.5, but let's get it working first before we ask it for its capabilities.Well, maybe! Here is what my ancient Prism 2.5 says about its capabilities:```
chili@LAPTOP60:~$ sudo iwlist wlan1 auth
wlan1     Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP
          Current TKIP countermeasures : no
          Current Drop unencrypted : no
          Current Authentication algorithm :
		open
		shared-key
          Current Receive unencrypted EAPOL : no
```

---

### Post by racingsnake on 2009-10-12
Thanks Chili - just working through your suggested steps now.

---

### Post by racingsnake on 2009-10-12
Hm - OK, that's a bit weird. In response to 

sudo modprobe hostap 

I get

[FONT=Courier New]> @tadpole:~$ sudo modprobe hostap
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.[/FONT]

I ran lsmod for both prism and hostapp; 

[FONT=Courier New]> @tadpole:/etc/modprobe.d$ lsmod | grep prism
robin@tadpole:/etc/modprobe.d$ lsmod | grep hostap
hostap_pci            57488  0 
hostap                113924  1 hostap_pci
ieee80211_crypt    13444  1 hostap
[/FONT]

So as you can see, there were no hits for "prism".

Here's the output from the lshw command (and yes, the adapter is still shown as unclaimed...):

>   *-network:1 UNCLAIMED
       description: Network controller
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32


HTH...

---

### Post by racingsnake on 2009-10-12
More weirdness - don't know if it is significant: 

Entering 

lspci -v

gets me the following about the wireless network controller:

> 
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
    Subsystem: Askey Computer Corp. Device 7000
    Flags: medium devsel, IRQ 18
    Memory at f0000000 (32-bit, prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel modules: hostap_pci, orinoco_pci


I don't know if that means the orinoco driver is still getting loaded; I have seen others say they had to rename it to stop this happening...

---

### Post by chili555 on 2009-10-12
> I don't know if that means the orinoco driver is still getting loaded;Yes, indeed, and they are probably working against each other. Please do:```
sudo mv /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.conf
cat /etc/modprobe.d/blacklist.conf
```Please post the result. Let's check it and, possibly, make some amendments.

---

### Post by racingsnake on 2009-10-12
Here you go:
> 
@tadpole:/etc/network$ cat /etc/modprobe.d/blacklist.conf
blacklist orinoco_pci
@tadpole:/etc/network$


Just going to reboot and run lspci again...

---

### Post by racingsnake on 2009-10-12
Darn it... orinoco is still showing as being there:

> 
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
    Subsystem: Askey Computer Corp. Device 7000
    Flags: medium devsel, IRQ 18
    Memory at f0000000 (32-bit, prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel modules: hostap_pci, orinoco_pci


And yep, eth1 is still showing as UNCLAIMED
:confused:

---

### Post by chili555 on 2009-10-12
Let's try a temporary fix; if it works, we can make it permanent. Please do:```
sudo rmmod -f orinoco_pci orinoco hermes
sudo rmmod -f hostap
sudo modprobe hostap
sudo lshw -C network
```Is it still UNCLAIMED or is there an interface, eth1 or wlan0, perhaps attached?

---

### Post by racingsnake on 2009-10-12
Hi - results not entirely as expected...

> 
@tadpole:~$ sudo rmmod -f orinoco_pci orinoco hermes
ERROR: Removing 'orinoco_pci': No such file or directory
ERROR: Removing 'orinoco': No such file or directory
ERROR: Removing 'hermes': No such file or directory
@tadpole:~$ sudo rmmod -f hostap
ERROR: Removing 'hostap': Resource temporarily unavailable
@tadpole:~$ sudo modprobe hostap
@tadpole:~$ 

eth1 still show as unclaimed when I do lshw,

and according to lspci -v, both modules are still there. Am wondering whether I need to go into the /lib/modules sub-directory with the orinoco object files in and manually move/rename them.

I have to step away briefly, but will be back again later. Many thanks for your help so far...

---

### Post by chili555 on 2009-10-12
Please post *lsmod.* Thanks.

See you soon!

---

### Post by racingsnake on 2009-10-12
Here you go...

> @tadpole:~$ sudo lsmod | sort
[FONT=Fixedsys]8139cp                 27776  0 
8139too                32128  0 
ac97_bus                9856  1 snd_ac97_codec
agpgart                42696  2 drm,intel_agp
binfmt_misc            16776  1 
bitblit                13824  1 fbcon
bnep                   20224  2 
bridge                 56212  0 
drm                    96424  3 radeon
evbug                  10752  0 
fbcon                  46112  0 
floppy                 64324  0 
font                   16384  1 fbcon
hostap                113924  1 hostap_pci
hostap_pci             57488  0 
i2c_i801               17296  0 
ieee1394               94660  1 ohci1394
ieee80211_crypt        13444  1 hostap
input_polldev          11912  0 
intel_agp              34108  1 
iTCO_vendor_support    11652  1 iTCO_wdt
iTCO_wdt               19108  0 
joydev                 18368  0 
lp                     17156  0 
mii                    13312  2 8139too,8139cp
Module                  Size  Used by
ohci1394               38576  0 
output                 11008  1 video
parport                42220  3 lp,ppdev,parport_pc
parport_pc             40100  1 
pcmcia                 44748  0 
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
pcspkr                 10496  0 
ppdev                  15620  0 
psmouse                61972  0 
radeon                342816  2 
rsrc_nonstatic         19328  1 yenta_socket
serio_raw              13444  0 
shpchp                 40212  0 
snd                    62756  17 snd_intel8x0,snd_intel8x0m,snd_ac97_codec,snd_seq_oss,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_pcm,snd_timer
snd_ac97_codec        112292  2 snd_intel8x0,snd_intel8x0m
snd_intel8x0           37532  3 
snd_intel8x0m          22028  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_page_alloc         16904  3 snd_intel8x0,snd_intel8x0m,snd_pcm
snd_pcm                83076  4 snd_intel8x0,snd_intel8x0m,snd_ac97_codec,snd_pcm_oss
snd_pcm_oss            46336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_seq_dummy          10756  0 
snd_seq_midi           14336  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq_oss            37760  0 
snd_timer              29704  2 snd_seq,snd_pcm
softcursor              9984  1 bitblit
soundcore              15200  1 snd
stp                    10500  1 bridge
tileblit               10752  1 fbcon
video                  25872  0 
wbsd                   22152  0 
yenta_socket           32396  1[/FONT] 


Interestingly, hostap is in there and orinoco isn't...

---

### Post by chili555 on 2009-10-12
If you are using Network Manager, it will not allow a wireless connection if you have a wired available and connected. Please detach the ethernet cable and do:```
sudo ifconfig eth0 down
```Now let's see if the kernel has any messages about this:```
sudo cat /var/log/messages | grep hostap
sudo cat /var/log/messages | grep -i prism
iwconfig
```Thanks.

This is especially mysterious to me, because my ancient Prism 2.5 leaps to connect practically before I blink; yours should, too. These cards are well-supported in Linux.

---

### Post by racingsnake on 2009-10-12
Hi Chili - 

Nope: nothing in the log for either hostapp or prism, and iwconfig returns three hits:

lo     no wireless extensions 
eth0   no wireless extensions   (wired adapter)
pan0   no wireless extensions  (not sure what that adapter/interface is)

Hmm.

It just seems that eth1 is not recognised at all.

---

### Post by chili555 on 2009-10-12
Please open up Synaptic and install, if not already there, *hostapd* and *hostap-utils*.> Wireless worked OK on IntrepidDo you still have your Intrepid CD that you can run as a live CD so we can see what driver let the Prism work correctly? Find out with:```
lshw -C network
```I am running low on ammo/ideas/talent.

---

### Post by racingsnake on 2009-10-15
Hi Chili - apologies for the radio silence... "Real Life"(TM) has been intruding on my Linux debugging activities (the need to earn a living, etc...). I just wanted to let you know I have not gone off in a snit - just have to take care of business.

Anyway, a quick update: I launched Synaptic and searched for hostap; it returned entries for hostapd and hostap-utils, but the interesting thing was that the "Installed Version" field was blank. Hmmm. So, those are currently installing, and I will try and grab a few minutes later on to reboot, retest and so on.

Thanks again for your help up to now  -  really appreciate your guidance on this.

---

### Post by racingsnake on 2009-10-15
OK - I told Synatic to install those modules, and rebooted. Unfortunately the Prism adapter is still showing as "unclaimed"... :^(

I can't help feeling I'm missing something fundamental here. Part of me is wondering whether it's worth switching back from WICD to Network Manager now that we have changed a few other things, like the blacklist. But obviously, tools like WICD and Network Manager can't connect a device to a network if the device hasn't first been associated with a network interface... but I don't know how to make that happen in the first place. 

I know with Java Desktop System it required manually editing some network config files, but I have no idea which ones I would need to edit if I wanted to do the corresponding thing with Ubuntu. (With JDS, I was just following a sheet of instructions sent out by someone who knew what they were doing.. ;^)

---

### Post by racingsnake on 2009-10-18
Hi again Chili - 

Apologies for the delay between posts; fixing this slipped down the priority list a little.

I've got wireless working, with WPA, but not quite as planned.

I found a discarded USB wireless dongle lying around (as you do...), but couldn't tell what make it was - no identifying marks at all (!). So-ooo... put it in a USB slot, started the laptop and waited. Nothing.

I re-installed Network Manager (replacing WICD) and re-booted. Network Manager immediately detected my wireless network and prompted for a (WPA!) key. I entered that, and bingo. Works out of the box, as they say. If only I knew what make the dongle is. 

So - 
- wireless works
- WPA works
- currently streaming some music off my file server over SMB.

Life is good.

Sorry we couldn't get the integrated w/less working; I may have another try at that in due course. In the meantime, thanks again for all your help and suggestions.

---

### Post by calrogman on 2009-10-18
> **racingsnake said:**
> So-ooo... put it in a USB slot, started the laptop and waited. Nothing.

I re-installed Network Manager (replacing WICD) and re-booted. Network Manager immediately detected my wireless network and prompted for a (WPA!) key. I entered that, and bingo. Works out of the box, as they say. If only I knew what make the dongle is.

So you were using WICD instead of Network Manager the whole time?

It wasn't working because you probably didn't set the Wireless Interface option in 'Preferences>General Settings', this *must* be set for WICD to be any use, to anyone.
Find some Cat5, just in case, reinstall WICD, and set Wireless Interface to wlan0, see if it works.

I'm betting my installation of Bash that it will.

---

