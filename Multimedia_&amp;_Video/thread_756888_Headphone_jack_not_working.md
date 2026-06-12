---
title: "Headphone jack not working"
date: 2008-04-16
forum: Multimedia &amp; Video
---

### Post by FlyingPenguin on 2008-04-16
Issue with headphone jack, no sound coming out of it.

Info

[LIST]
[*]Computer is Toshiba P-100 ST9752
[*]Sound card is HDA Intel Conexant CX20549 (Venice)
[*]Ubuntu version is Hardy Beta, because my card did not work at all on any previous version (if the problem is related to that, I will be happy with moving my post to a different forum).
[*]Microphone worked only after I selected "IntMic" in the Switches Tab.
[/LIST]

Problem

[LIST]
[*]Sound works perfectly in Vista, headphone jack included.
[*]When device is plugged in to headphone jack, the speakers do turn off, but no sound is heard through the headphones.
[*]WEIRD PART: I noticed a clicking sound in the headphones that occurs when I insert the headphones in to the jack. I found that if I insert the headphone to just the right specific point (about halfway inserted, but it has to be perfect), the headphones do in fact work!
[*]However, this is not a good solution, and I can't figure out why this would happen.
[*]*Possibly Related: Sound will only work for one program at a time. i.e. if I am listening to a song in Totem, there will be no sound in Neverball.*
[/LIST]

Fixes that did not work:

[LIST]
[*]One suggestion was the Volume Control "Switches" tab, which would have a "Headphone" checkmark box. Mine does not have this checkbox. All devices are selected in the Preferences dialog box.
[*]I have turned up all the volumes in Alsamixer except for IEC958 (would not let me move it, I don't know what it is anyway).
[/LIST]

---

### Post by drdrewdown on 2008-04-16
are you using the latest alsa drivers compiled for hdaintel audio?

---

### Post by FlyingPenguin on 2008-04-16
I'm using whatever came on the installation. Am I going to need to compile something from source here?

*(I apologize for my newbiness)*

---

### Post by drdrewdown on 2008-04-16
yes, my girlfriend has a lenovo y510 & her headphone jack was not working until we compiled the alsa drivers for hdaintel audio

do a quick search about this or look at [www.alsa-project.org](www.alsa-project.org) & there should be some how-to's on there

---

### Post by Beckstown on 2008-04-16
I have the same laptop model and also experienced the exact same problems as described above. I tried to compile the latest alsa driver, but it didn't help. However, since I am new to Ubuntu it could be my fault.

So please post whether this helped you with the problem.

Great community by the way!

---

### Post by drdrewdown on 2008-04-16
find the main thread for the lenovo y510

it should point you in the right direction

---

### Post by Beckstown on 2008-04-17
I tried the description in this page, since I think you referred to this with your comment: [http://ubuntuforums.org/showthread.php?t=687663&page=2](http://ubuntuforums.org/showthread.php?t=687663&page=2)

However, i could not specify my model in the last step(options snd-hda-intel model=MODEL). I am not sure whether or not this is the reason but this solution is not helping me with the problem.

---

### Post by drdrewdown on 2008-04-17
```
at the end of that file, add:
Code:

options snd-hda-intel model=MODEL

For model=MODEL, use one of the three options from above:

    &#8227; options snd-hda-intel model=lenovo-101e

    OR

    &#8227; options snd-hda-intel model=lenovo-nb0763

    OR

    &#8227; options snd-hda-intel model=lenovo-ms7195-dig
```

did you try all 3 of those options?  i remember having a lilttle bit of trouble at this step, but eventually followed directions after reading them closely & got it to work.. be patient my man, it will work!

---

### Post by Beckstown on 2008-04-17
I have to admit that I did not try them previous to my last post, since I thought they should be only used for lenovo laptops. I tried them now, but they had no effect on the headphone isse. I also tried 

> options snd-hda-intel model=laptop

since this seems to be the toshiba option. However, these settings had no effect.

I also tried this option, since someone suggested in the alsa forum that this fixed a similar issue for him.
> Replace the start of the line with hda-intel in it so that it starts with this: /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko:

Remove the directory /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel 
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

This all did not resolve the issue with the lacking headphone support. Therefore, I guess I have to write a bug report in the alsa forum as soon as my time permits it.

Thanks for your help!

---

### Post by Beckstown on 2008-04-17
Hey FlyingPenguin,

I hope you dont mind, but I took your bug description and used it to file a bug report at launchpad. I linked it to this post. I just wanted to speed up the process.

[https://bugs.launchpad.net/ubuntu/+bug/218817](https://bugs.launchpad.net/ubuntu/+bug/218817)

It seems to be that the headphones functioned in Gutsy Gibbon after some tinkering:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)

However, in the end several users are also reporting, that once they switched to Hardy Heron the headphones stopped working. So this problem seems to be related to hardy heron rather than to alsa.

---

### Post by shafi on 2008-04-21
I have a compaq presario c700 laptop and the wireless device and headphone jack is not working , i think it dosn't detect my headphon jack , but it detect my wireless, but i can not see it into the network manager, if any one knows please help how can i solve these two problems, I have followed alot of instructions through the ubuntu forum but they didn't work for me, please help
this is the result of the :

```

 sudo lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


```

```

 sudo lsmod | grep snd

snd_hda_intel         263712  2 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm


```

```

 ps -i

ERROR: Unsupported SysV option.
********* simple selection *********  ********* selection by list *********
-A all processes                      -C by command name
-N negate selection                   -G by real group ID (supports names)
-a all w/ tty except session leaders  -U by real user ID (supports names)
-d all except session leaders         -g by session OR by effective group name
-e all processes                      -p by process ID
T  all processes on this terminal     -s processes in the sessions given
a  all w/ tty, including other users  -t by tty
g  OBSOLETE -- DO NOT USE             -u by effective user ID (supports names)
r  only running processes             U  processes for specified users
x  processes w/o controlling ttys     t  by tty
*********** output format **********  *********** long options ***********
-o,o user-defined  -f full            --Group --User --pid --cols --ppid
-j,j job control   s  signal          --group --user --sid --rows --info
-O,O preloaded -o  v  virtual memory  --cumulative --format --deselect
-l,l long          u  user-oriented   --sort --tty --forest --version
-F   extra full    X  registers       --heading --no-heading --context
                    ********* misc options *********
-V,V  show version      L  list format codes  f  ASCII art forest
-m,m,-L,-T,H  threads   S  children in sum    -y change -l format
-M,Z  security data     c  true command name  -c scheduling class
-w,w  wide output       n  numeric WCHAN,UID  -H process hierarchy



```

** also important to mention when i plugin the head phone it doesn't mute the speaker sound!!. :(

***Regarding the wireless: ***
```

 ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1B:38:F0:03:84  
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fef0:384/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4535276 (4.3 MB)  TX bytes:759145 (741.3 KB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:324 errors:0 dropped:0 overruns:0 frame:0
          TX packets:324 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12706 (12.4 KB)  TX bytes:12706 (12.4 KB)


```

```

~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0

auto eth0


```

I also add once the code for the ath0 but it didn't works. :(

---

### Post by EXCiD3 on 2008-04-22
Try this for your Atheros card: [http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/](http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/)

As for your headphone jack, this could be a problem with Alsa or Pulse Audio. I really dont know much about that. From what i've heard about the headphone jacks are that sometimes upgrading Alsa to the latest version in Feisty and Gutsy fixed this. Its worth a shot. Short tutorial on compiling alsa here: [http://ubuntuforums.org/showthread.php?t=455147](http://ubuntuforums.org/showthread.php?t=455147)

---

### Post by shafi on 2008-04-23
thanks alotttttttttttttttt,
it worked like a charm to me, now i have the wireless option into the network manager.
I have just follow the above instruction.

first I had just face to a small problem after installing the atheros driver I couldn't connect to the internet, then i update the file **/etc/network/interface** as follow:

auto lo
iface lo inet loopback
auto eth0 
iface eth0 inet dhcp

and the problem solved.

thank you very much,
hope that i could find a solution for my headphon also :).

---

