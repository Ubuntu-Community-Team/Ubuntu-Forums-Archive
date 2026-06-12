---
title: "Cannot surf the web, fresh 11.04"
date: 2011-09-30
forum: Networking &amp; Wireless
---

### Post by silverbullet007 on 2011-09-30
Background info:

Dell Precision T3400
Broadcom 57xx embedded nic
Fresh install of Natty 11.04


I noticed earlier today that Network Manager shows that I'm connected, I could browse to Yahoo, or CNN but not Google.  I searched that and tried changing my interfaces files to include:
"auto eth0
iface eth0 inet dhcp"

After a reboot NM displayed no connections.  Then I could not browse anyhting.  Mind you I can nslookup all day long but I could not ping or traceroute anything.

So I reverted the interfaces file, rebooted and NM works again not however I still cannot browse any web site.

I've tried using both our internal DNS servers and googles free ones to no avail.  Is there a known issue I'm missing?  If not what else can I try here?

I have another nic to test with but it's a broadcom and at home currently.

Thanks

*EDIT* I can browse my internal network, open shares off servers, printer to networked printers, etc.


I realize usually questions like this are rather stupid, and are usually user error but having not really used Ubuntu since 8.04 I'm feeling lost.

---

### Post by silverbullet007 on 2011-10-03
Wow.. no thoughts?

I know what you people are thinking.. but I swear this is a completely fresh install.  I haven't had the time yet to install any additional apps.  Running on bone-stock hardware..

This morning I rebooted again, Firefox times out browsing to its homepage which is still start.ubuntu.com and chromium times out pulling up Google.com.

System Monitor shows a constant 5-9kbps on the rx side.. and wow.  TX has zero activity, I tried refreshing the page in Firefox and rx jumped to 11-ish kbps however tx remains zero.  Weird.

---

### Post by praseodym on 2011-10-03
Hi,

please show

```
lspci -nnk | grep -iA2 net
ifconfig -a
iwconfig
lsmod
rfkill list
cat /etc/network/interfaces
```

---

### Post by jonobr on 2011-10-03
ok, So internally you work ok, getting outside doesnt?

maybe post ifconfig and the contents of /etc/resolv.conf

when you do an nslookup what is doing your resolution?
Can you resolv internal and external addresses?

What server does it show as the resolver, is that correct?

---

### Post by silverbullet007 on 2011-10-03
> **praseodym said:**
> Hi,

please show

```
lspci -nnk | grep -iA2 net
ifconfig -a
iwconfig
lsmod
rfkill list
cat /etc/network/interfaces
```

```
allanon@Apollo:~$ lspci -nnk | grep -iA2 net
04:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express [14e4:167a] (rev 02)
	Subsystem: Dell Precision T3400 [1028:0214]
	Kernel driver in use: tg3

allanon@Apollo:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:c9:3a:15:bb  
          inet addr:10.1.1.201  Bcast:10.1.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83587 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49388535 (49.3 MB)  TX bytes:2048103 (2.0 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

allanon@Apollo:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

allanon@Apollo:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
vboxnetadp             13323  0 
vboxnetflt             27855  0 
vboxdrv               219250  2 vboxnetadp,vboxnetflt
vesafb                 13449  1 
snd_hda_codec_analog    75442  1 
joydev                 17322  0 
usbhid                 41704  0 
snd_hda_intel          28209  2 
snd_hda_codec          90901  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
nvidia               7098106  34 
snd_rawmidi            25269  1 snd_seq_midi
hid                    77084  1 usbhid
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
snd                    55295  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59039  0 
dcdbas                 14054  0 
parport_pc             32111  1 
serio_raw              12990  0 
x38_edac               12960  0 
edac_core              42881  2 x38_edac
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
ahci                   21591  3 
tg3                   131476  0 
libahci                25548  1 ahci

allanon@Apollo:~$ rfkill list
allanon@Apollo:~$ 

allanon@Apollo:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

---

### Post by silverbullet007 on 2011-10-03
> **jonobr said:**
> ok, So internally you work ok, getting outside doesnt?

maybe post ifconfig and the contents of /etc/resolv.conf

when you do an nslookup what is doing your resolution?
Can you resolv internal and external addresses?

What server does it show as the resolver, is that correct?

```
allanon@Apollo:~$ cat /etc/resolv.conf
domain
search
nameserver 8.8.8.8
nameserver 8.8.4.4

allanon@Apollo:~$ nslookup mail.google.com
;; connection timed out; no servers could be reached

allanon@Apollo:~$ nslookup www.cnn.com
;; connection timed out; no servers could be reached



```

The two Google DNS ip's are what I specified in Network-Manager.. however apparently they cannot resolve anything.

---

### Post by silverbullet007 on 2011-10-03
I have changed the DNS servers listed in NM and opted to go with our internal DNS servers instead.  Im now able to very quickly resolve external servers... I am now able to surf to about 75% of the websites I attempt.  Gmail, Logmein.. places do not work.

---

### Post by silverbullet007 on 2011-10-03
Ok so Ill repost in a new thread since this one has been given the death-stare.

---

