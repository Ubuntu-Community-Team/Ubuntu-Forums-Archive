---
title: "Modem Keeps Disconnecting !"
date: 2005-12-31
forum: Networking &amp; Wireless
---

### Post by medya on 2005-12-31
hey ... 

I have a winmodem , Smart Spirt Zoltrix 56K, Internal , Com3 , HCF Conexant.
I had a head ache to make it dial and finally I made it dial by installing driver from  
[http://www.linuxant.com/drivers/hcf/full/downloads.php?PHPSESSID=adb05828abc6526e5c6238ef1b06e630](http://www.linuxant.com/drivers/hcf/full/downloads.php?PHPSESSID=adb05828abc6526e5c6238ef1b06e630)

but now the problem is when it connects to internet it dissconnects after 2 seconds.

whats the problem ?

I suspect that i havent set the numbers right... there is a number something like 115700 ... I have didnt touch it in the PPPCONFIG .

as you know God Damn linuxant.com , sells the drivers for $20, and those who cant buy the driver , can use the free version , which limits the speed to 14.4KB,

how I can solve this problem...why it keeps on disconneting ? anything I should set for that 14.4 speed limit?

God Damn Linxuant, they are torturing all of us to make some money...

---

### Post by medya on 2006-01-01
so nobody is going to help this poor guy ? :confused:

---

### Post by medya on 2006-01-02
I am still crying....

---

### Post by rahz on 2006-01-03
That number relates to modem speed. Most are at 115200 I thought. Don't know if that's the source of your problem though. 
You might want to look at your system logs file to see if you get any sort of error messages, when it hangs up? I had a couple of modem problems early on, and by looking at the sys log I could see what my problem was.

rahz

---

### Post by medya on 2006-01-03
and how I can access to my log ?

if i dont lunch firefox, my connection wouldnt be dissonncted.... [I can hear the noise on the phone]
just when I try to access internet it disconnects.. :(

---

### Post by wanger123 on 2006-01-03
Ok, tell me how you configured your connection (pppconfig?). Do you also have an ethernet card that you use on that computer (probably not - unless it's a laptop) Please supply your etc/ppp/options, etc/chatscripts/pap, etc/chatscripts/provider and etc/ppp/peers/provider files. Have you tried using kppp or gnome-ppp Also what error do you get? Is it pppd daemon died unexpectedly: exit status 1, 2, 15 or 16??? 

Before you try to connect next time, open a terminal and type: tail -f /var/log/messages and then press enter
you should see scrolling messages once you try to connect (with a different terminal window) which should tell you why the connection failed

cheers wanger

---

### Post by medya on 2006-01-03
[QUOTE=wanger123]Ok, tell me how you configured your connection (pppconfig?). Do you also have an ethernet card that you use on that computer (probably not - unless it's a laptop) Please supply your etc/ppp/options, etc/chatscripts/pap, etc/chatscripts/provider and etc/ppp/peers/provider files. Have you tried using kppp or gnome-ppp Also what error do you get? Is it pppd daemon died unexpectedly: exit status 1, 2, 15 or 16??? 

Before you try to connect next time, open a terminal and type: tail -f /var/log/messages and then press enter
you should see scrolling messages once you try to connect (with a different terminal window) which should tell you why the connection failed

cheers wanger[/QUOTE]


Hey tanks for your reply , I do have a Lan Card on my motherboard .
i configed it with pppconfig.


here is the result of tail.

```
Jan  4 02:25:27 localhost kernel: [4295450.407000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
Jan  4 02:25:27 localhost kernel: [4295450.407000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan  4 02:25:27 localhost kernel: [4295450.546000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jan  4 02:25:27 localhost kernel: [4295450.546000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jan  4 02:25:27 localhost pppd[11151]: pppd 2.4.3 started by dyaoko, uid 1000
Jan  4 02:25:28 localhost chat[11152]: abort on (BUSY)
Jan  4 02:25:28 localhost chat[11152]: abort on (NO CARRIER)
Jan  4 02:25:28 localhost chat[11152]: abort on (VOICE)
Jan  4 02:25:28 localhost chat[11152]: abort on (NO DIALTONE)
Jan  4 02:25:28 localhost chat[11152]: abort on (NO DIAL TONE)
Jan  4 02:25:28 localhost chat[11152]: abort on (NO ANSWER)
Jan  4 02:25:28 localhost chat[11152]: abort on (DELAYED)
Jan  4 02:25:28 localhost chat[11152]: send (ATZ^M)
Jan  4 02:25:28 localhost chat[11152]: expect (OK)
Jan  4 02:25:28 localhost chat[11152]: ATZ^M^M
Jan  4 02:25:28 localhost chat[11152]: OK
Jan  4 02:25:28 localhost chat[11152]:  -- got it
Jan  4 02:25:28 localhost chat[11152]: send (ATDT9713207^M)
Jan  4 02:25:28 localhost chat[11152]: expect (CONNECT)
Jan  4 02:25:28 localhost chat[11152]: ^M
Jan  4 02:25:52 localhost chat[11152]: ATDT9713207^M^M
Jan  4 02:25:52 localhost chat[11152]: CONNECT
Jan  4 02:25:52 localhost chat[11152]:  -- got it
Jan  4 02:25:52 localhost chat[11152]: send (\d)
Jan  4 02:25:53 localhost pppd[11151]: Serial connection established.
Jan  4 02:25:53 localhost pppd[11151]: Using interface ppp0
Jan  4 02:25:53 localhost pppd[11151]: Connect: ppp0 <--> /dev/ttySHCF0
Jan  4 02:25:54 localhost pppd[11151]: PAP authentication succeeded
Jan  4 02:25:54 localhost kernel: [4295477.991000] PPP BSD Compression module registered
Jan  4 02:25:54 localhost kernel: [4295478.053000] PPP Deflate Compression module registered
Jan  4 02:25:55 localhost pppd[11151]: local  IP address 81.12.8.21
Jan  4 02:25:55 localhost pppd[11151]: remote IP address 81.12.8.246
Jan  4 02:25:55 localhost pppd[11151]: primary   DNS address 81.12.8.245
Jan  4 02:27:09 localhost pppd[11151]: Hangup (SIGHUP)
Jan  4 02:27:09 localhost pppd[11151]: Modem hangup
Jan  4 02:27:09 localhost pppd[11151]: Connect time 1.3 minutes.
Jan  4 02:27:09 localhost pppd[11151]: Sent 8205 bytes, received 1307 bytes.
Jan  4 02:27:09 localhost pppd[11151]: Connection terminated.
Jan  4 02:27:11 localhost pppd[11151]: Exit
```.

---

### Post by medya on 2006-01-04
Ping , somebody help please !

---

### Post by wanger123 on 2006-01-13
Hi, I needed to put these two modem init strings in:

init 1: ATZ
init 2: AT&F V1 E1 S0=0 &C1 &D2 s10=250 +FCLASS=0

the second one contains s10=250. This tells the modem not to hangup unless it loses the carrier for at least 25 seconds.

Not sure where pppconfig puts these settings (as I use kppp) but you could look in /etc/chatscripts/pap and/or /etc/chatscripts/provider and add the second init string under ATZ.

Also, if you are using ethernet and have a defaultroute set you need to add replacedefaultroute underneath defaultroute in /etc/ppp/peers/provider.

Finally, if ppp does not replace your existing nameservers (DNS servers) from another location eg work, you may need to comment them out by putting # in front of them in /etc/resolv.conf

hope it helps

wanger

---

### Post by medya on 2006-01-18
sorry no use , doesnt work yet.

---

### Post by yigal.weinstein on 2006-01-18
Did you try linmodem.com?  That is the diagnostic tests?  That is do you have the right driver installed?

---

### Post by yigal.weinstein on 2006-01-18
Sorry a little bit drunk not linmodem.com but [http://www.linmodems.org]("http://www.linmodems.org").

---

### Post by gohlip on 2006-01-18
Firstly, let me start by saying that I hesitate to respond to your problem because I think I am not proficient in Linux and I am not sure this may work for you. But seeing your troubles you had gone through, heck, why not give it a try.
Just don't get angry with me if it doesn't.

Try  "sudo apt-get install ifplugd"

I had been tinkering with a similar problem, went through various procedures, installed gnome desktop, tried to reconfig the files, etc. and I think the above did the trick.

Good Luck.

---

### Post by scunc_dvl on 2006-08-21
I've been working on figuring out the root of the lack-of-ppp problem for *days and days*. Sure, splurging on a hardware modem got me 56k without paying for some silly software key, but the whole ppp-support could be made easier to work with from the pppd and kernel modules right to the lack of scripting features in wvdial (which only lets you a little flexibility in the chat script it seems with "Default Reply", which I need for my silly ISP asking for my "login host" address which I never 
really unserstood.. Anyways, that may be the problem, but enough of that, I'm... very lost, and not happy.

In short: pppd dies with exit code 16 ("The link was terminated by the modem hanging up.") or on one occaision code 11 ("The peer system failed (or refused) to authenticate itself."). Apparantly my isp is hanging up as soon as authentication finishes and PPP begins (though I can put a "pause" at the end of my script and see ~{k283{38xx garbage, but even "expect ~{" doesn't seem to help).

[SIZE="1"](On the other hand, I'm least bitter about kppp, which at least does a good job of containing most of the complexity of setting up dialup)[/SIZE]

I don't know where to begin, as I don't even know the root cause(s), and I've spent enough time so I give up... Here's stuff I logged, to be complete but not spammy..

(I'm going to try dialing my university to see if it is my isp being anal) ](*,) 

```

Output of 'sudo kppp' when it runs
----------
Opener: received OpenDevice
Opener: received ExecPPPDaemon
In parent: pppd pid 11267
Opener: received OpenResolv
Couldn't find interface ppp0: No such device
Kernel supports ppp alright.
Couldn't find interface ppp0: No such device
It was pppd that died
pppd exited with return value 16
Sending 11241 a SIGUSR1
Opener: received RemoveSecret
Opener: received RemoveSecret
Opener: received OpenResolv
Opener: received OpenResolv
Opener: received RemoveLock
Opener: received PPPDExitStatus
Opener: received PPPDExitStatus
Opener: received OpenSysLog
-----------

Dialog box
---
The pppd daemon died unexpectedly!
Exit status: 16
See 'man pppd' for an explanation of the error codes or take a look at the kppp FAQ on http://developer.kde.org/~kppp/index.html
---------

My PPP logfile (doesn't tell me much other than a hangup)
---------
Aug 21 01:44:15 localhost pppd[11634]: pppd 2.4.3 started by root, uid 0
Aug 21 01:44:15 localhost pppd[11634]: using channel 4
Aug 21 01:44:15 localhost pppd[11634]: Using interface ppp0
Aug 21 01:44:15 localhost pppd[11634]: Connect: ppp0 <--> /dev/ttyS14
Aug 21 01:44:15 localhost pppd[11634]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x4642575e> <pcomp> <accomp>]
Aug 21 01:44:15 localhost pppd[11634]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x4642575e> <pcomp> <accomp>]
Aug 21 01:44:15 localhost pppd[11634]: rcvd [LCP ConfReq id=0x49 <asyncmap 0xa0000> <magic 0x6fb886e9> <pcomp> <accomp>]
Aug 21 01:44:15 localhost pppd[11634]: sent [LCP ConfAck id=0x49 <asyncmap 0xa0000> <magic 0x6fb886e9> <pcomp> <accomp>]
Aug 21 01:44:15 localhost pppd[11634]: sent [LCP EchoReq id=0x0 magic=0x4642575e]
Aug 21 01:44:15 localhost pppd[11634]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Aug 21 01:44:15 localhost pppd[11634]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0>]
Aug 21 01:44:16 localhost pppd[11634]: rcvd [LCP TermReq id=0x4a]
Aug 21 01:44:16 localhost pppd[11634]: LCP terminated by peer
Aug 21 01:44:16 localhost pppd[11634]: sent [LCP TermAck id=0x4a]
Aug 21 01:44:17 localhost pppd[11634]: Hangup (SIGHUP)
Aug 21 01:44:17 localhost pppd[11634]: Modem hangup
Aug 21 01:44:17 localhost pppd[11634]: Connection terminated.
Aug 21 01:44:17 localhost pppd[11634]: Exit.
----------









My modules listed by lsmod
----------
$ lsmod
skunkpimp@scuncdvl:~$ lsmod
Module                  Size  Used by
ppp_deflate             6976  0
zlib_deflate           23192  1 ppp_deflate
bsd_comp                6528  0
ppp_async              12032  0
ppp_generic            30944  3 ppp_deflate,bsd_comp,ppp_async
nvidia               5426868  12
cpufreq_userspace       5456  0
cpufreq_stats           6088  0
freq_table              5320  1 cpufreq_stats
cpufreq_powersave       2240  0
cpufreq_ondemand        7340  0
cpufreq_conservative     8364  0
slip                   14592  1
slhc                    7808  2 ppp_generic,slip
capifs                  6928  1
video                  17288  0
tc1100_wmi              8008  0
sony_acpi               6104  0
pcc_acpi               13568  0
hotkey                 10568  0
dev_acpi               14788  0
i2c_acpi_ec             6400  0
button                  7776  0
battery                10568  0
container               5120  0
ac                      5640  0
ipv6                  266176  8
af_packet              23692  4
tsdev                   9152  0
irtty_sir               9728  0
sir_dev                20568  1 irtty_sir
irda                  198576  2 irtty_sir,sir_dev
crc_ccitt               2560  2 ppp_async,irda
floppy                 66616  0
pcspkr                  4048  0
ohci1394               34252  0
snd_intel8x0           35968  1
snd_ac97_codec         92376  1 snd_intel8x0
snd_pcm_oss            55008  0
snd_mixer_oss          18880  1 snd_pcm_oss
snd_pcm                97036  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11856  2 snd_intel8x0,snd_pcm
i2c_nforce2             7936  0
i2c_core               24152  3 nvidia,i2c_acpi_ec,i2c_nforce2
dm_mod                 59128  1
snd_seq_dummy           4356  0
snd_seq_oss            34816  0
snd_seq_midi           10048  0
snd_rawmidi            28384  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                56320  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25352  2 snd_pcm,snd_seq
snd_seq_device          9872  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
evdev                  11008  0
snd                    59560  13 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              11232  1 snd
sr_mod                 18468  0
sbp2                   25416  0
ieee1394              366584  2 ohci1394,sbp2
rtc                    13960  0
psmouse                29572  0
mousedev               13220  1
parport_pc             37736  1
lp                     13960  0
parport                40460  2 parport_pc,lp
md                     46272  0
ext3                  135888  1
jbd                    58480  1 ext3
mbcache                10824  1 ext3
thermal                14992  0
processor              25556  1 thermal
fan                     5256  0
usbhid                 36448  0
forcedeth              23360  0
ehci_hcd               33864  0
ohci_hcd               21252  0
ide_cd                 43296  0
cdrom                  39400  2 sr_mod,ide_cd
ide_disk               18176  3
ide_generic             1792  0
sata_nv                10884  0
libata                 56072  1 sata_nv
scsi_mod              151920  3 sr_mod,sbp2,libata
amd74xx                15280  1
ide_core              157188  4 ide_cd,ide_disk,ide_generic,amd74xx
unix                   30072  371
vesafb                  9252  0
capability              6088  0
commoncap               8576  1 capability
vga16fb                12864  1
vgastate                9344  1 vga16fb
softcursor              2880  2 vesafb,vga16fb
cfbimgblt               3264  2 vesafb,vga16fb
cfbfillrect             4864  2 vesafb,vga16fb

cfbcopyarea             4352  2 vesafb,vga16fb
fbcon                  38272  72
tileblit                2880  1 fbcon
font                    9024  1 fbcon
bitblit                 6080  1 fbcon






crap from /var/log/messages (I didn't bother doing a "sudo ifconfig eth0 down"), I thought since ppp0 never appears even in "ifconfig -a", something's missing in my set of modules.
Aug 21 00:03:29 localhost kernel: [ 1099.191786] device eth0 left promiscuous mode
Aug 21 00:03:31 localhost diald[8306]: Calling site 192.168.0.2
Aug 21 00:03:31 localhost diald[8306]: No devices free to call out on.
Aug 21 00:03:32 localhost diald[8306]: Connect script failed.
Aug 21 00:03:32 localhost diald[8306]: Delaying 1 seconds before clear to dial.
Aug 21 00:03:35 localhost diald[8306]: Calling site 192.168.0.2
Aug 21 00:03:35 localhost diald[8306]: No devices free to call out on.
Aug 21 00:03:35 localhost diald[8306]: Connect script failed.
Aug 21 00:03:35 localhost diald[8306]: Delaying 1 seconds before clear to dial.
Aug 21 00:03:38 localhost diald[8306]: Calling site 192.168.0.2
Aug 21 00:03:38 localhost diald[8306]: No devices free to call out on.
Aug 21 00:03:39 localhost diald[8306]: Connect script failed.
Aug 21 00:03:39 localhost diald[8306]: Delaying 1 seconds before clear to dial.
Aug 21 00:03:42 localhost diald[8306]: Calling site 192.168.0.2
Aug 21 00:03:42 localhost diald[8306]: No devices free to call out on.
Aug 21 00:03:42 localhost diald[8306]: Connect script failed.
Aug 21 00:03:42 localhost diald[8306]: Delaying 1 seconds before clear to dial.
Aug 21 00:03:45 localhost diald[8306]: Calling site 192.168.0.2
Aug 21 00:03:45 localhost diald[8306]: No devices free to call out on.
Aug 21 00:03:46 localhost diald[8306]: Connect script failed.
Aug 21 00:03:46 localhost diald[8306]: Delaying 1 seconds before clear to dial.
Aug 21 00:04:10 localhost kernel: [ 1140.376242] eth0: Promiscuous mode enabled.
Aug 21 00:04:10 localhost kernel: [ 1140.376356] device eth0 entered promiscuous mode
Aug 21 00:15:21 localhost kernel: [ 1810.380154] PPP generic driver version 2.4.2
Aug 21 00:15:21 localhost pppd[11267]: pppd 2.4.3 started by root, uid 0
Aug 21 00:15:21 localhost pppd[11267]: Using interface ppp0
Aug 21 00:15:21 localhost pppd[11267]: Connect: ppp0 <--> /dev/ttyS14
Aug 21 00:15:21 localhost kernel: [ 1810.760660] PPP BSD Compression module registered
Aug 21 00:15:21 localhost kernel: [ 1810.786382] PPP Deflate Compression module registered
Aug 21 00:15:21 localhost pppd[11267]: LCP terminated by peer
Aug 21 00:15:22 localhost pppd[11267]: Hangup (SIGHUP)
Aug 21 00:15:22 localhost pppd[11267]: Modem hangup
Aug 21 00:15:22 localhost pppd[11267]: Connection terminated.
Aug 21 00:15:22 localhost pppd[11267]: Exit.
Aug 21 00:17:08 localhost kernel: [ 1917.385606] device eth0 left promiscuous mode
Aug 21 00:20:18 localhost pppd[11345]: pppd 2.4.3 started by root, uid 0
Aug 21 00:20:18 localhost pppd[11345]: Using interface ppp0
Aug 21 00:20:18 localhost pppd[11345]: Connect: ppp0 <--> /dev/ttyS14
Aug 21 00:20:19 localhost pppd[11345]: LCP terminated by peer
Aug 21 00:20:20 localhost pppd[11345]: Hangup (SIGHUP)
Aug 21 00:20:20 localhost pppd[11345]: Modem hangup
Aug 21 00:20:20 localhost pppd[11345]: Connection terminated.
Aug 21 00:20:20 localhost pppd[11345]: Exit.
--------------------------------





After changing some stuff (4:20am August 21)
dialog box:
The pppd daemon died unexpectedly!
Exit status: 10
See 'man pppd' for an explanation of the error codes or take a look at the kppp FAQ on http://developer.kde.org/~kppp/index.html

It seems this looks different for once (though dialing again did a repeat of much of what has already happend)
Aug 21 04:20:15 localhost pppd[12836]: pppd 2.4.3 started by root, uid 0
Aug 21 04:20:15 localhost pppd[12836]: using channel 17
Aug 21 04:20:15 localhost pppd[12836]: Using interface ppp0
Aug 21 04:20:15 localhost pppd[12836]: Connect: ppp0 <--> /dev/ttyS14
Aug 21 04:20:15 localhost pppd[12836]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x5081c164> <pcomp> <accomp>]
Aug 21 04:20:16 localhost pppd[12836]: rcvd [LCP ConfReq id=0x46 <asyncmap 0xa0000> <magic 0xaf23d566> <pcomp> <accomp>]
Aug 21 04:20:16 localhost pppd[12836]: sent [LCP ConfAck id=0x46 <asyncmap 0xa0000> <magic 0xaf23d566> <pcomp> <accomp>]
Aug 21 04:20:16 localhost pppd[12836]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x5081c164> <pcomp> <accomp>]
Aug 21 04:20:16 localhost pppd[12836]: sent [LCP EchoReq id=0x0 magic=0x5081c164]
Aug 21 04:20:16 localhost pppd[12836]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Aug 21 04:20:16 localhost pppd[12836]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0>]
Aug 21 04:20:16 localhost pppd[12836]: rcvd [LCP TermReq id=0x47]
Aug 21 04:20:16 localhost pppd[12836]: LCP terminated by peer
Aug 21 04:20:16 localhost pppd[12836]: sent [LCP TermAck id=0x47]
Aug 21 04:20:19 localhost pppd[12836]: Connection terminated.
Aug 21 04:20:19 localhost pppd[12836]: using channel 18
Aug 21 04:20:19 localhost pppd[12836]: Using interface ppp0
Aug 21 04:20:19 localhost pppd[12836]: Connect: ppp0 <--> /dev/ttyS14
Aug 21 04:20:19 localhost pppd[12836]: sent [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0x23254bbc> <pcomp> <accomp>]
Aug 21 04:20:19 localhost pppd[12836]: sent [LCP TermReq id=0x3]
Aug 21 04:20:19 localhost pppd[12836]: tcflush failed: Bad file descriptor
Aug 21 04:20:19 localhost pppd[12836]: tcsetattr: Invalid argument (line 1011)
Aug 21 04:20:19 localhost pppd[12836]: Exit.


It looks like it was just failing in a differetn place that time


```

---

### Post by fragmented_user on 2006-09-07
> **scunc_dvl said:**
> I've been working on figuring out the root of the lack-of-ppp problem for *days and days*. Sure, splurging on a hardware modem got me 56k without paying for some sill...Anyways, that may be the problem, but enough of that, I'm... very lost, and not happy.

In short: pppd dies with exit code 16 ("The link was terminated by the modem hanging up.") or on one occaision code 11 ("The peer system failed (or refused) to authenticate itself."). Apparantly my isp is hanging up as soon as authentication finishes and PPP begins (though I can put a "pause" at the end of my script and see ~{k283{38xx garbage, but even "expect ~{" doesn't seem to help).

[SIZE="1"](On the other hand, I'm least bitter about kppp, which at least does a good job of containing most of the complexity of setting up dialup)[/SIZE]

I don't know where to begin, as I don't even know the root cause(s), and I've spent enough time so I give up... Here's stuff I logged, to be complete but not spammy..

(I'm going to try dialing my university to see if it is my isp being anal) ](*,) 

```

Output of 'sudo kppp' when it runs
----------
Opener: received OpenDevice
Opener: received ExecPPPDaemon
...
Aug 21 04:20:19 localhost pppd[12836]: tcsetattr: Invalid argument (line 1011)
Aug 21 04:20:19 localhost pppd[12836]: Exit.


It looks like it was just failing in a differetn place that time


```



I had a similar problem even when using kppp. The following thread helped me sort some things out.

[http://www.linuxselfhelp.com/forum/viewtopic.phtml?p=2491](http://www.linuxselfhelp.com/forum/viewtopic.phtml?p=2491)

> 
PostPosted: Sun Jul 10, 2005 5:59 pm    Post subject: kppp woes  	Reply with quote
I experienced the same problem setting up a new ppp conection. I am running Mandriva (nee Mandrake) 10.1 on a Dell Lattitude D800

After some digging in the on-line kppp manual, I discovered the section on Login Scripts. The problem appears to be that once the connection is established, kppp doesn't know how to negotiate the handshaking with the remote server.

To solve this problem, I created a new account under the "Accounts" tab
In the Accounts pop-up, I entered the name and phone number and selected the "Login Script" tab

The "Login Script" window has a pull down menu with the various acceptable Hayes-compatible commands and a place to enter options to that command. Using this I created the following script:

Expect name:
Send <My Login>
Expect code:
PWPrompt Passcode:
Expect Pool>
Send ppp

Admittedly, this is a trivial script, but it works I recommend checking out the manual (mine came with the distro). They have many examples that helped me get my config working.

The conversation goes as follows:

kppp expects a string containing name: When it gets it, it sends my login name.
kppp then expects a string containing code: (my modem pool sends "Passcode:" instead of "Password:") When kppp gets code: it opens up a dialog window and asks for my Passcode. (My modem pool uses SecurID, so my password changes every 60 seconds).
kppp finally expects the string "Pool>" to which it responds ppp This causes the ppp session to be established.

This seemed to work for me...hope it helps you as well.


---

### Post by scunc_dvl on 2006-09-08
I don't think I have that problem anymore. My ISP is a lil different:

> [I]
    1          Slip
    2          PPP
    3          Quit
Selection:[/I] 

For that I have "Expect *Selection*" then "Send *2*" for PPP.


Whether or not I use kppp, it crashes as soon as this script ends. If I pause for a number of seconds, it will print up "~{{6{83{~{" garbage like it's supposed to (after it says *"Async interface address is unnumbered (Loopback1) Your IP address is 205.200.62.208. MTU is 1500 bytes*", but whenever the pause ends the pppd daemon crashes.

I have read some other scripts and it has helped some to put "Expect ~" then "Send ppp"..or "Expect ~{" or "Expect \~\{" and so on... still those hacks didn't work for me in the past (though I will get off my connection just to try it once more...) I think by then it's not the scripts responsibility to do any more work but what do I know

---

### Post by scunc_dvl on 2006-12-14
FIXED - 
My ISP requires wvdial, with this added to */etc/wvdial.conf*:

Stupid Mode = 1
Default Reply = Localhost (or whatever Login Host wants to be)

kppp apparantly doesn't have stupid mode, as it requires initiating pppd before the script, it's unique to wvdial :/

---

