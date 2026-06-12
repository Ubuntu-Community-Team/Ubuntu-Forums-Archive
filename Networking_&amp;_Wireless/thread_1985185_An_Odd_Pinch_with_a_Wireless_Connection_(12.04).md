---
title: "An Odd Pinch with a Wireless Connection (12.04)"
date: 2012-05-23
forum: Networking &amp; Wireless
---

### Post by Unspoken on 2012-05-23
First, I would like to point out how much of a pain this problem has become for me. I wasn't thinking it would end up how it has, but it's boiled down to lots of hoop-jumping and several hours of screaming incoherently at the top of my lungs. So I'm nowhere close to being savvy with the programming belly of Ubuntu. And I've had a problem with my current setup since the days of Hardy that I never really felt the need to address until this exact moment in time-space.

My internet doesn't not work (not a typo). I can chat on Skype, perform system/distro updates, check my Facebook status, and several other things that are cool and stuff. What ISN'T cool is how I can only go to the news feed on Facebook, and if any other link is clicked, it will never load. I can't even post this problem on the Ubuntu forum through Precise because my computer can't pass the "Submit New Thread" button; believe me, I've spent four days praying that it would (I'm posting this via iPhone... Yeah...). My e-mail cannot be checked. Ubuntu One keeps giving me the same notification that it's "uploading photo.jpg and 200 other files to the cloud," even though it has said this for a week. Needless to say, this is starting to become a problem.

I've searched through other posts in the forums, and while I haven't found a similar situation, I did compile a list of Terminal returns that should hopefully have enough info to get me started. Any help would be vastly appreciated, and I thank everyone in advance.


cat /etc/lsb-release; uname -a 
```
DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=12.04 
DISTRIB_CODENAME=precise 
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS" 
Linux Neku 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:52 UTC 2012 i686 i686 i386 GNU/Linux 
```

lspci -nnk | grep -iA2 net 
```
09:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10) 
	Subsystem: Toshiba America Info Systems Device [1179:ff31] 
	Kernel driver in use: 8139too 
-- 
09:04.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] [168c:001a] (rev 01) 
	Subsystem: Askey Computer Corp. Device [144f:7094] 
	Kernel driver in use: ath5k 
```

iwconfig 
```
lo        no wireless extensions. 

wlan0     IEEE 802.11bg  ESSID:"2WIRE013"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:25:3C:EA:85:79   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:1189   Missed beacon:0 

eth0      no wireless extensions. 
```

rfkill list all 
```
0: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
```

lsmod 
```
Module                  Size  Used by 
dm_crypt               22528  0 
joydev                 17393  0 
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep              13276  1 snd_hda_codec 
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec 
arc4                   12473  2 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi 
snd_seq_midi_event     14475  1 snd_seq_midi 
ath5k                 145127  0 
pcmcia                 39791  0 
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
ath                    19387  1 ath5k 
mac80211              436455  1 ath5k 
ppdev                  12849  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event 
bluetooth             158438  10 rfcomm,bnep 
snd_timer              28931  2 snd_pcm,snd_seq 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq 
binfmt_misc            17292  1 
cfg80211              178679  3 ath5k,ath,mac80211 
psmouse                87213  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket 
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
serio_raw              13027  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc 
soundcore              14635  1 snd 
i2c_piix4              13093  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm 
shpchp                 32325  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp 
radeon                729591  3 
ttm                    65344  1 radeon 
drm_kms_helper         45466  1 radeon 
8139too                23283  0 
drm                   197692  5 radeon,ttm,drm_kms_helper 
8139cp                 22633  0 
i2c_algo_bit           13199  1 radeon 
pata_atiixp            12999  0 
video                  19068  0 
sata_sil               13275  2 
ati_agp                13242  0 
```

---

### Post by Unspoken on 2012-05-26
This problem is getting worse, to the point that even my frequent sites aren't loading from time to time. I could really use a hand.

---

### Post by kc1di on 2012-05-26
> **Unspoken said:**
> This problem is getting worse, to the point that even my frequent sites aren't loading from time to time. I could really use a hand.

my first thought is I see two Lan cards in the machine.  Disable one of them and use the other.  See if that will help the situation.  

Then go to networking icon in panel and right click select edit connection and  click on your lan connection and edit. Check the following under Wired tab check to make sure you have the correc MAC address , under 802.1 security make sure 802.1 security is unchecked for now., under Ipv4 settings set it DHCP automatic for now. Under IPV6 set it to automatic for now. also make sure that the little check box at the bottom is that says available to all users is check. Let's start with that first.

Another what type of router are you using. and do you have any fire walls engaged on it?
oh by the way with the outputs of what you have listed there seems to be no pci wireless card installed.
if your using a usb wireless please got to terminal and enter the following and post it here.
"lsusb" -l is lower Case L.

---

### Post by Unspoken on 2012-05-26
Sorry, forgot to mention that this is a laptop: Toshiba Satellite L35-S2161. The two connections you saw were probably the ethernet port and wireless card. I'm not using USB for this, either.

The router is a 2Wire 2701HG-B. I've not had any problems with it for any other computer or device in the household. No firewalls, just regular WEP key. 

The suggestion didn't really help; certain sites still aren't loading. Ubuntu One is still annoying my notification area with the same message, as well. Sometimes, I can refresh the page a few times, and it will finally connect, but rarely does this method work.

---

### Post by gordintoronto on 2012-05-26
This is a DNS server issue. Perhaps you could post the output from: 
cat /etc/resolv.conf

By the way, WEP is totally not secure. If your router supports it, use WPA. (If I lived next door to you, it would take me a few minutes to be using your router -- and your data cap, etc.)

---

### Post by Unspoken on 2012-05-27
Thanks for the suggestion. And here is the return on that:

cat /etc/resolv.conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search gateway.2wire.net
```

---

### Post by robert shearer on 2012-05-27
> First, I would like to point out how much of a pain this problem has become for me. I wasn't thinking it would end up how it has, but it's boiled down to lots of hoop-jumping and several hours of **screaming incoherently at the top of my lungs**

You are not alone....
[http://www.starwalk.com/dory/twenty-mile.htm](http://www.starwalk.com/dory/twenty-mile.htm)
[http://www.youtube.com/watch?v=tdbhxD5B9q0](http://www.youtube.com/watch?v=tdbhxD5B9q0)

:)

---

### Post by gordintoronto on 2012-05-27
Interesting, my laptop has 12.04 installed and resolv.conf looks just like yours. However, when I click on the network icon and select "connection information" it shows the DNS servers I expected to see. Darn, it looks like something has changed in this area.

Mint 13 (version equivalent to Ubuntu 12.04) doesn't even have a resolv.conf.

Do you ever reboot your router?

---

### Post by steeldriver on 2012-05-28
Have the ath5k hardware encryption issues been fixed yet? if not then the procedure described here may be worth a try for the OP:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568090](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568090)

Anyhow yes there are a couple of significant DNS changes (resolvconf and dnsmasq) - I'm still on  11.10 everywhere and I'm trying to get my head around the new way of doing things - I found this article helpful

[http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

regards

---

### Post by gordintoronto on 2012-05-28
To net it out, the DNS Server addresses are stored in /run/nm-dns-dnsmasq.conf

The article explains the (minor) advantages of the different approach, but I'm not convinced it's worth "everything you know is obsolete."

In any case, I still suggest rebooting the router.

---

### Post by Unspoken on 2012-05-30
Rebooting doesn't do much of anything, unfortunately. Taking a look at those articles now to see if they are of any use.

Thank you to everyone for the help thus far; it's been really great to know that people are genuinely trying to solve a problem like this. :)

---

### Post by Unspoken on 2012-05-30
Thank you very much, steeldriver! The fix posted in the link provided has made it so that all the previous sites I'd tried to visit work without a hitch! Looks like it was a problem with the specific card's manufacturer.

---

### Post by steeldriver on 2012-05-30
glad to hear you got it worked out - if you can mark the thread SOLVED (via thread tools) that will ensure we keep the mods happy as well :)

---

