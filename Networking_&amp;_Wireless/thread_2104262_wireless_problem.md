---
title: "wireless problem"
date: 2013-01-12
forum: Networking &amp; Wireless
---

### Post by Gennu on 2013-01-12
I've first heard of something called ubuntu just two weeks ago and it was 10.10 then I've upgraded it and now I'm using 12.04.1 LTS but the wireless connection was working well on 10.10 but in 11.04 and 11.10 and 12.04 it's not working except when wired so I don't know what to do now ?

---

### Post by squakie on 2013-01-12
It probably needs a driver.  Please do the following:

[LIST]
[*]open a terminal window
[*]type lspci > ~/abs-wireless.txt <press enter>
[*]type lsusb >> ~/abs-wireless.txt <press enter>
[*]type iwconfig >> ~/abs-wireless.txt <press enter>
[*]type ifconfig >> ~/abs-wireless.txt <press enter>
[/LIST]
Please note the first line has single ">", all the rest have 2.  The above is creating a file in you home folder with some information we need.


Now post a reply back here, click the paper clip and attach the abs-wireless.txt file from your home folder.

---

### Post by Gamer Boy on 2013-01-12
Same problem here so I hope you don't mind me piggy-backing your question?

Mine says this:

martin@martin:~$ type lspci > ~/abs-wireless.txt
martin@martin:~$ lspci > ~/abs-wireless.txt
martin@martin:~$ lsusb >> ~/abs-wireless.txt
martin@martin:~$ iwconfig >> ~/abs-wireless.txt
lo        no wireless extensions.

eth0      no wireless extensions.

martin@martin:~$ ifconfig >> ~/abs-wireless.txt
martin@martin:~$

---

### Post by sandyd on 2013-01-12
Can you attach the abs-wireless.txt file thats in your home folder?

Thanks :)

---

### Post by Gamer Boy on 2013-01-12
Thanks for the reply - much appreciated.

Here it is attached now.

---

### Post by Gennu on 2013-01-12
> **squakie said:**
> It probably needs a driver.  Please do the following:

[LIST]
[*]open a terminal window
[*]type lspci > ~/abs-wireless.txt <press enter>
[*]type lsusb >> ~/abs-wireless.txt <press enter>
[*]type iwconfig >> ~/abs-wireless.txt <press enter>
[*]type ifconfig >> ~/abs-wireless.txt <press enter>
[/LIST]
Please note the first line has single ">", all the rest have 2.  The above is creating a file in you home folder with some information we need.


Now post a reply back here, click the paper clip and attach the abs-wireless.txt file from your home folder.
does it gives only one text file ??
```
ahmed@ahmed-Inspiron-N4050:~$ iwconfig >> ~/abs-wireless.txt
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by Gamer Boy on 2013-01-12
Yes - should there be more (I'm a beginner here so I'm finding my feet here)

WYSIWYG with that output I'm afraid....

---

### Post by sandyd on 2013-01-12
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/923809](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/923809)

---

### Post by squakie on 2013-01-12
> **Gamer Boy said:**
> Thanks for the reply - much appreciated.

Here it is attached now.

Follow this thread:

[http://thatguruguy.wordpress.com/2012/09/04/working-rtl8188cus-in-ubuntu-12-04/](http://thatguruguy.wordpress.com/2012/09/04/working-rtl8188cus-in-ubuntu-12-04/)

---

### Post by Gamer Boy on 2013-01-12
Thanks.

Are you saying here that there's a bug-fix been released? I ask because I installed Ubuntu 12.04.01 LTS about 10 days ago.

Also, if it is a bug-fix, I have no clue how to install it (and I'm v new to Ubuntu!) Could you give me a steer?

Thanks

PE:popcorn:

---

### Post by squakie on 2013-01-12
> **Gennu said:**
> does it gives only one text file ??
```
ahmed@ahmed-Inspiron-N4050:~$ iwconfig >> ~/abs-wireless.txt
lo        no wireless extensions.

eth0      no wireless extensions.
```

See this thread:

[http://ubuntuforums.org/showthread.php?t=2039351](http://ubuntuforums.org/showthread.php?t=2039351)

---

### Post by mörgæs on 2013-01-12
> **Gamer Boy said:**
> Thanks.

Are you saying here that there's a bug-fix been released? I ask because I installed Ubuntu 12.04.01 LTS about 10 days ago.

Also, if it is a bug-fix, I have no clue how to install it (and I'm v new to Ubuntu!) Could you give me a steer?

Thanks

PE:popcorn:

Yes, it fixed in the version Raring Ringtail, which is the development version due to release in april under the name 13.04.

You can install it now, but be warned that it is a work in progress and likely to be unstable. You might need to return to a stable version.

---

### Post by Gamer Boy on 2013-01-12
> **squakie said:**
> Follow this thread:

[http://thatguruguy.wordpress.com/2012/09/04/working-rtl8188cus-in-ubuntu-12-04/](http://thatguruguy.wordpress.com/2012/09/04/working-rtl8188cus-in-ubuntu-12-04/)

Great stuff - that worked. At least it's worked for two reboots so far!

Thanks very much - much appreciated.

---

### Post by squakie on 2013-01-12
You're welcome - here's hoping it keeps working! ;)

Now that your problem is apparently solved, you can answer this for the next person who posts on the same thing - isn't that great?  Goes to show how to get started answering threads - like the rest of us, learn one thing at a time and pass it along when you can.  There are some real experts in Ubuntu out here - I'm just a lowly guy who tries.

---

### Post by Gennu on 2013-01-13
for me it's not solved yet

---

### Post by Gennu on 2013-01-13
> **squakie said:**
> See this thread:

[http://ubuntuforums.org/showthread.php?t=2039351](http://ubuntuforums.org/showthread.php?t=2039351)

I've tried everything possible to solve this but non of them worked 
can you help me please

---

### Post by mörgæs on 2013-01-13
Please write the exact steps you tried and the exact responses / error messages you received.

---

### Post by squakie on 2013-01-15
> **Gennu said:**
> I've tried everything possible to solve this but non of them worked 
can you help me please

As morgaes mentioned above, it would greatly help to have any messages, screen prints (including what shows in network manager), and a part of your log file to see what messages the system might have spit out when initializing.

---

### Post by Gennu on 2013-01-18
> **squakie said:**
> As morgaes mentioned above, it would greatly help to have any messages, screen prints (including what shows in network manager), and a part of your log file to see what messages the system might have spit out when initializing.

[http://ubuntuforums.org/showthread.php?t=2103715](http://ubuntuforums.org/showthread.php?t=2103715)
I think that's all

---

### Post by Gennu on 2013-01-18
> **mörgæs said:**
> Please write the exact steps you tried and the exact responses / error messages you received.

read this I think it includes everything I've tried

---

### Post by squakie on 2013-01-18
If you had intended to attach a file, some data or a link, nothing came through.  You may want to repost that ;)

---

### Post by Hadaka on 2013-01-18
ooops !

---

### Post by Gennu on 2013-01-21
> **squakie said:**
> If you had intended to attach a file, some data or a link, nothing came through.  You may want to repost that ;)

[http://ubuntuforums.org/showthread.php?t=2103715](http://ubuntuforums.org/showthread.php?t=2103715)

in this link I solved the main problem but that wireless problem appeared to me so I've asked about it and in that link some of my terminal codes about that problem

  Hope you can see it now :P

---

### Post by Hadaka on 2013-01-21
Hi, it looks like you have this..
Network controller: Broadcom Corporation Device 4365 (rev 01)

to verify please do
```
lspci -nnk | grep0280 
```

*IF  ..it is 14e4-4365  then

[http://askubuntu.com/questions/215890/dell-inspiron-5720-wifi-broadcom-bcm43142-ubuntu-12-10/215923#215923](http://askubuntu.com/questions/215890/dell-inspiron-5720-wifi-broadcom-bcm43142-ubuntu-12-10/215923#215923)

---

### Post by ben222qmz7 on 2013-01-22
I am not sure if I can use this same thread also myself but I try. My problem seems to be similar with others. Can I use the same pieces of advise as for the others given here?  My computer is in this respect infamous HP6735s  I resently installed Xubuntu 12.04 and cannot find wireless net. No even my own one. I have not used any Linux in this computer before. After reading lots of stuff here I enclose copy of some command results here hoping somebody could advise me what to do:    -HP:~$ sudo lshw -class network [sudo] password for pena:    *-network                       description: Ethernet interface        product: 88E8042 PCI-E Fast Ethernet Controller        vendor: Marvell Technology Group Ltd.        physical id: 0        bus info: pci@0000:02:00.0        logical name: eth0        version: 10        serial: 00:1f:29:a0:56:b6        size: 100Mbit/s        capacity: 100Mbit/s        width: 64 bits        clock: 33MHz        capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation        configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full firmware=N/A latency=0 link=no multicast=yes port=twisted pair speed=100Mbit/s        resources: irq:43 memory:d3100000-d3103fff ioport:3000(size=256)   *-network DISABLED        description: Wireless interface        physical id: 2        logical name: wlan0        serial: 00:21:00:3a:82:d3        capabilities: ethernet physical wireless        configuration: broadcast=yes driver=b43 driverversion=3.2.0-36-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg     pena@pena-HP:~$ nm-tool  NetworkManager Tool  State: disconnected  - Device: wlan0 ----------------------------------------------------------------   Type:              802.11 WiFi   Driver:            b43   State:             unavailable   Default:           no   HW Address:        00:21:00:3A:82:D3    Capabilities:    Wireless Properties     WEP Encryption:  yes     WPA Encryption:  yes     WPA2 Encryption: yes    Wireless Access Points    - Device: eth0 -----------------------------------------------------------------   Type:              Wired   Driver:            sky2   State:             unavailable   Default:           no   HW Address:        00:1F:29:A0:56:B6    Capabilities:     Carrier Detect:  yes     Speed:           100 Mb/s    Wired Properties     Carrier:         off

---

### Post by psifunk on 2013-01-22
Hi, maybe I can be of help but please use the CODE box to give output (the # button in editor) otherwise it is a mess

---

### Post by ben222qmz7 on 2013-01-22
Sorry, I was wondering myself too what wnt wrong in my previous post.
Hope this comes OK.



```
  HP:~$ sudo lshw -class network
[sudo] password for pena: 
  *-network               
       description: Ethernet interface
       product: 88E8042 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:1f:29:a0:56:b6
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full firmware=N/A latency=0 link=no multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:d3100000-d3103fff ioport:3000(size=256)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:21:00:3a:82:d3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-36-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg




pena@pena-HP:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        00:21:00:3A:82:D3

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:1F:29:A0:56:B6

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off  
```

---

### Post by psifunk on 2013-01-22
Hi again, ok can you please for start also give the output of

```
 lspci | Network
```
```
 rfkill list wifi
```
```
 lsmod
```
```
 ls /etc/modprob.d/
```

Also, has xubuntu proposed any drivers for you to install regarding the wireless, and if so have you done this? Any other action you have taken so far regarding drivers?

---

### Post by ben222qmz7 on 2013-01-22
```
  lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780M/RS780MN [Mobility Radeon HD 3200 Graphics]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8042 PCI-E Fast Ethernet Controller (rev 10)
pena@pena-HP:~$ 
pena@pena-HP:~$  Network
Network: command not found
pena@pena-HP:~$ Network
Network: command not found
pena@pena-HP:~$ rfkill list wifi
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
pena@pena-HP:~$  lsmod
Module                  Size  Used by
binfmt_misc            17292  1 
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55605  1 vfat
usb_storage            39646  0 
uas                    17828  0 
btusb                  17948  0 
vesafb                 13516  1 
bnep                   17830  2 
rfcomm                 38139  4 
bluetooth             158479  11 btusb,bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_analog    75395  1 
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_usb_audio         101566  3 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_analog,snd_hda_intel
snd_pcm                80916  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
snd_usbmidi_lib        24603  1 snd_usb_audio
snd_seq_midi           13132  0 
snd_rawmidi            25424  2 snd_usbmidi_lib,snd_seq_midi
pl2303                 17673  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
usbserial              37173  1 pl2303
uvcvideo               67203  0 
snd_timer              28931  2 snd_pcm,snd_seq
videodev               86588  1 uvcvideo
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                86520  0 
serio_raw              13027  0 
snd                    62218  23 snd_hda_codec_analog,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fglrx                2909978  39 
k10temp                12990  0 
sp5100_tco             13495  0 
i2c_piix4              13093  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
soundcore              14635  1 snd
video                  19068  0 
hp_accel               25728  0 
lis3lv02d              19268  1 hp_accel
input_polldev          13648  1 lis3lv02d
wmi                    18744  1 hp_wmi
mac_hid                13077  0 
shpchp                 32325  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41937  0 
hid                    77428  1 usbhid
sky2                   53628  0 
pena@pena-HP:~$ ls /etc/modprob.d/
ls: cannot access /etc/modprob.d/: No such file or directory    
```

---

### Post by Cmarrero75 on 2013-01-22
gamer boy. I got the same problem and got the same result you had. 

(i.e. 


> **Gamer Boy said:**
> Same problem here so I hope you don't mind me piggy-backing your question?

Mine says this:

martin@martin:~$ type lspci > ~/abs-wireless.txt
martin@martin:~$ lspci > ~/abs-wireless.txt
martin@martin:~$ lsusb >> ~/abs-wireless.txt
martin@martin:~$ iwconfig >> ~/abs-wireless.txt
lo        no wireless extensions.

eth0      no wireless extensions.

martin@martin:~$ ifconfig >> ~/abs-wireless.txt
martin@martin:~$

what did I do wrong?

---

### Post by ben222qmz7 on 2013-01-22
About the drivers. There was a suggestion of restricted drivers but  were not downloadable. The D/L discontinued in about halfway.

---

### Post by Cmarrero75 on 2013-01-22
I guess I want to make clear that I am learning this stuff and I am complete newb. it's okay.. I have a accepted that I will seem like a moron so it's okay to mock...    So do I need to make that text file or is that beside the point now? 

I know it's a broadcom driver that is the problem. and my computer that I am using ( not right now) is a lenovo 3000- n100 (seemed like a good idea at the time) and of like the rest 11 worked perfectly fine.

---

### Post by ben222qmz7 on 2013-01-22
As the wireless connection is working on Windows, I was thinking that if  I try re-installation of Xubuntu and keep the wireless connection on during the installation.
It might help - or not. The present system was done with a wired connection only.
On Xubuntu I cannot see any wireless  connections at all now.

Has anybody tried that with any success? Although I think the problem is with
some drivers and configuration.

---

### Post by Cmarrero75 on 2013-01-22
okay. Anything I should be looking for ?

---

### Post by mörgæs on 2013-01-23
> **ben222qmz7 said:**
> The present system was done with a wired connection only.

This is by far the best approach.

Install and apply all updates using wired connection. Verify through a couple of reboots. Only when that works you can (and should) pull the plug, as the wirefree connection might switch itself off when the wired one is present.

---

### Post by mick2w on 2013-01-23
I too am watching this with interest and my level of knowledge/expertise in this is way below that of everyone else. 

When time permits I currently browse the forum to see what I can find out about what the results in the terminal mean - uphill struggle, bearing in mind the first sentence above.

Mick

---

### Post by Cmarrero75 on 2013-01-30
> **mörgæs said:**
> This is by far the best approach.

Install and apply all updates using wired connection. Verify through a couple of reboots. Only when that works you can (and should) pull the plug, as the wirefree connection might switch itself off when the wired one is present.

Yeah but a wireless connection is important. I just dont understand why I cant find the answer. I know someone must have found it yet. :KS

---

### Post by mörgæs on 2013-01-31
The thread is getting a mess, so I recommend that you open a new one with an informative title. Please run the commands

[http://ubuntuforums.org/showpost.php?p=12484089&postcount=2](http://ubuntuforums.org/showpost.php?p=12484089&postcount=2)

and post the output in CODE tags.

---

### Post by Cmarrero75 on 2013-01-31
[http://ubuntuforums.org/blah blah blah #post12484389]("http://ubuntuforums.org/showthread.php?p=12484389#post12484389")

thanks for the advice.

---

