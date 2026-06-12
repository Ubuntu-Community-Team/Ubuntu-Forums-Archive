---
title: "Network card issue caused by the wrong driver that was installed dring the OS inst."
date: 2011-07-04
forum: Networking &amp; Wireless
---

### Post by Dolke on 2011-07-04
Hi there. 

I'm new with Linux operating system, but I'm advanced user of the PCs in general and right now I have one frustrating problem with the network.

I installed newest Ubuntu system, 11.04, Natty-Narwhal, and PC is running smoothly. It is solid machine, Celeron 430, 1 gb of DDR2 memory and I have both LAN card and graphics integrated on the mobo which is MSI 7529, based on G31/P35/P31 chipset. 

I plugged lan cable directly from my PC to the ADSL router. There is another Win Xp machine on the same router and it has connection, and internet is working fine. Right now Im writing from the Win 7 laptop, which is connected to the same router via wifi link... all working like a charm...

But, when I plug the Ubuntu desk I cannot get access to bot lan and internet...

I searched the net and it seems that ubuntu didnt install proper driver during the OS installation. Here are some diagnostics of the current config and state:

```

Module                  Size  Used by
binfmt_misc            13213  1 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
i915                  450944  3 
drm_kms_helper         40745  1 i915
drm                   180037  4 i915,drm_kms_helper
psmouse                73312  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13184  1 i915
serio_raw              12990  0 
ppdev                  12849  0 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32111  1 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
r8169                  42534  0 
floppy                 60032  0 
*****************************************************************
eth0      Link encap:Ethernet  HWaddr 00:24:21:34:62:b7  
          inet6 addr: fe80::224:21ff:fe34:62b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1529 (1.5 KB)  TX bytes:4070 (4.0 KB)
          Interrupt:42 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8304 (8.3 KB)  TX bytes:8304 (8.3 KB)
*****************************************************************
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 529c
	Physical Slot: 33
	Flags: bus master, fast devsel, latency 0, IRQ 42
	I/O ports at e800 [size=256]
	Memory at febff000 (64-bit, non-prefetchable) [size=4K]
	Expansion ROM at febc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

``` 

As you can see I need to install driver named r8101 instead this one r8169 and I think it will work that way. I found driver [here]("http://www.google.com/search?rlz=1C1AVSC_enRS438RS438&aq=f&sourceid=chrome&ie=UTF-8&q=RTL+8101+linux+driver#hl=en&rlz=1C1AVSC_enRS438RS438&sa=X&ei=8fQRTofvBJHMswb0p5jhDg&ved=0CBYQBSgA&q=RTL8101e+linux+driver&spell=1&bav=on.2,or.r_gc.r_pw.&fp=c306e119a7d85f91&biw=1366&bih=667") only problem is  dont know how to replace them :)

Help needed, ty in advance.
Dean

---

### Post by chili555 on 2011-07-04
I wonder why you think it loaded the wrong driver; is it just because it didn't connect automatically? Are there any clues here?```
dmesg | grep -e r81 -e eth
```Thanks.

---

### Post by MaindotC on 2011-07-04
You can remove the r8169 with the "rmmod" command, and then use "insmod" for the r8101.  If the r8169 keeps on loading you can blacklist it so the operating system will stop loading it on boot.

```
dvorjak@dvorjak:~$ sudo lsmod | grep r8169
dvorjak@dvorjak:~$ sudo modprobe r8169
dvorjak@dvorjak:~$ sudo lsmod | grep r8169
r8169                  42534  0 
dvorjak@dvorjak:~$ sudo rmmod r8169
dvorjak@dvorjak:~$ sudo lsmod | grep r8169
```

---

### Post by Dolke on 2011-07-05
> **chili555 said:**
> I wonder why you think it loaded the wrong driver; is it just because it didn't connect automatically? Are there any clues here?```
dmesg | grep -e r81 -e eth
```Thanks.

There is no connection at all, while on the other PC that runs XP which is also directly connected to the ADSL router everything works fine.

I believe that my ethernet controller which is built in my mobo doesn't work with the driver that Ubuntu loaded.

I also found [this]("http://ubuntuforums.org/showthread.php?t=843398") topic but I didnt figure out what I need to do.

@MaindotC

Ty for taking interest in my issue and for providing these commands, but I'm unable to remove this driver using rmmod.
Im getting error that permission for deletion is denied.

Also I edited blacklist.conf file and added r8169 but it just keep loading... no luck of installing this other driver  r8101 either... :(

---

### Post by chili555 on 2011-07-05
In some cases, there is another underlying problem that prevents ethernet from working at all. Installing another driver is unlikely to resolve an underlying problem, if there is one. I suggest that we see if there is or is not another problem that prevents connection. If there is no apparent problem, then let's move on to r8101. Please run and post:```
dmesg | grep -e r81 -e eth
lspci -nn | grep 0200
```I'm afraid my colleague MaindotC got ahead of himself. It's a bit premature to remove r8169 and load r8101 if we haven't even built r8101 yet. He assumed you knew that rmmod and blacklisting are sudo activities; e.g.:```
sudo rmmod <some_driver>
```However, until we do some troubleshooting and decide that r8101 is our solution, it's premature to suggest it.

---

### Post by ratcheer on 2011-07-05
I had a similar problem where Ubuntu installed r8169 instead of r8168. Installing r8168 fixed my problem 100%

See post #6 in this thread: [http://ubuntuforums.org/showthread.php?t=1784635](http://ubuntuforums.org/showthread.php?t=1784635)

Tim

---

### Post by Dolke on 2011-07-05
Ty sir, I understand completely.

At this moment I'm not in the office so I'll try this new set of commands tomorrow. Until then, best regards

---

### Post by Dolke on 2011-07-05
> **ratcheer said:**
> I had a similar problem where Ubuntu installed r8169 instead of r8168. Installing r8168 fixed my problem 100%

See post #6 in this thread: [http://ubuntuforums.org/showthread.php?t=1784635](http://ubuntuforums.org/showthread.php?t=1784635)

Tim

Great. Thank you . I'll give that a go also, tomorrow.

---

### Post by Dolke on 2011-07-06
@ratcheer

Sir, I followed your instructions, downloaded driver from Realtek website, and tried to install it, but without success. When I run "sudo lspci -v" command I'm only getting lo adapter, there is no eth adapter info and in the read me file is written that it must appear if installation was OK.

Also, I followed your instructions anyway and after update command I rebooted the PC. Even r8169 driver is blacklisted, Ubuntu loads it again. Also, I removed it by using rmmod cmd, but again it is still present in the system and that is also visible when I type "lspci -v".

P.S. I just tried LAN cable to my win 7 laptop, network works perfectly and that includes internet access.

Why is so hard to load and unload driver in Ubuntu?
If ubuntu is the most user friendly UNIX-based os, than Im king of the Zamunda xD

---

### Post by ratcheer on 2011-07-06
Dolke, I am sorry that did not work for you. The first time I ever did it was about three weeks ago and, luckily for me, it worked just like it said it would. If it hadn't, I would have been lost too.

Oddly, I had to do the same thing for both my ethernet card and my wireless card. I am still puzzled as to why Ubuntu chose the wrong driver for two common cards.

Tim

---

