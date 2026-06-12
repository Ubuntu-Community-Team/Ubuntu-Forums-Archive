---
title: "How to Blacklist Default Drivers in Ubuntu 11.10?"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by Mr kmil on 2011-10-20
Hello, all.

I've been trying to install ndiswrapper so that I could use a Windows supported wireless cardbus, but I can't seem to figure out how to blacklist the default drivers. Would anyone know how to do that? Everywhere I've checked has given me outdated techniques.

Thanks!

---

### Post by wildmanne39 on 2011-10-20
Hi, what is the driver you want to blacklist and i will give you the command.

Are you sure you need or want ndiswrapper it is not usually the best way to go if there is a linux driver that works.
Thank you

---

### Post by Mr kmil on 2011-10-20
I actually don't know the driver. I know that it doesn't work properly, and needs to be blacklisted. You wouldn't happen to know how I can find that out, would you?

---

### Post by wildmanne39 on 2011-10-20
Hi, yes I do please post the results of:
```
lspci -nnk | grep -iA2 net
```
```
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Mr kmil on 2011-10-20
> 02:04.0 Ethernet controller [0200]: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 [8086:1229] (rev 09)
	Subsystem: Intel Corporation EtherExpress PRO/100 P Mobile Combo Adapter [8086:2201]
	Kernel driver in use: e100
--
03:00.0 Network controller [0280]: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] [1260:3890] (rev 01)
	Subsystem: Accton Technology Corporation Device [1113:a301]
	Kernel driver in use: p54pci


The second one got > Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
arc4                   12473  2 
p54pci                 17098  0 
p54common              32741  1 p54pci
mac80211              272785  2 p54pci,p54common
cfg80211              172392  2 p54common,mac80211
joydev                 17393  0 
ppdev                  12849  0 
snd_intel8x0           33318  1 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
radeon                925020  2 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ttm                    65224  1 radeon
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         32889  1 radeon
pcmcia                 39822  0 
drm                   192226  4 radeon,ttm,drm_kms_helper
snd                    55902  9 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73673  0 
serio_raw              12990  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
irda                  185428  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit           13199  1 radeon
crc_ccitt              12595  2 p54common,irda
parport_pc             32114  1 
binfmt_misc            17292  1 
shpchp                 32356  0 
ndiswrapper           193669  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usb_storage            44173  1 
uas                    17699  0 
e100                   36289  0 
floppy                 60310  0 


---

### Post by wildmanne39 on 2011-10-20
Hi, if you do not mind let&#347; try to get the linux driver working and get rid of the ndiswrapper for now.

Please do this:
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
Run the commands one at a time.

Then disconnect your wired connection and do this:
```
sudo ifconfig wlan0 down
sudo rmmod -f p54common
sudo modprobe p54common nohwcrypt=1
sudo ifconfig wlan0 up
```
give it a few seconds to come on and make sure you have wireless enabled in the top right corner of the screen in the internet icon.

If this works we will need to make it permanent.
Thank you

---

### Post by Mr kmil on 2011-10-20
When I try the first command, I get > WARNING: /etc/modprobe.d/blacklist.conf line 57: ignoring bad line starting with 'sudo'


The second gave me > E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
Should I be worried about that?

---

### Post by wildmanne39 on 2011-10-20
Hi, did you run them one line at a time by coping and pasting?

Make sure when you high light each line that you scroll all the way over so you high light the complete line then paste it into the terminal, those errors make no since to me. 

The second error you received can happen if you are trying to install something and you have a problem with apt-get, I guess it will occur when trying to remove something also so try it again and if you still get that second error we will have to try to fix it.
Thank you

---

### Post by Mr kmil on 2011-10-20
I did indeed copy and paste on line at a time. I even tried writing it word for word, but I still get the same response.

---

### Post by wildmanne39 on 2011-10-20
Hi, I just ran those commands on my system and they work like they were suppose too.

I am wondering if you are having issues from doing an upgrade and not a clean install, I myself had problems after the upgrade and I had to do a clean install.

This is the way to blacklist the driver now that I know the name but I still believe it would be best to avoid ndiswrapper if possible.
```
sudo su
echo "blacklist p54common" >> /etc/modprobe.d/blacklist.conf
exit
```
Thank you

---

### Post by Mr kmil on 2011-10-21
Thank you very much. If this doesn't work, I will do a clean install and try using the original drivers.

---

### Post by wildmanne39 on 2011-10-22
Hi okay.
Good Luck

---

### Post by mym2f on 2011-10-23
Hi everyone (especially wildmanne39) ......

 I have recently updated to Ubuntu 11.10 64-bit and my kernel is 3.0.0-12-generic ......

 I can not change the channel for mon0 to anything but channel -1 .......

 My ath9k_htc was working great with 2.6.39 kernel and compat-wireless-2011-08-27 after patching.

 Which version of compat-wireless do I need to install ? and are the old patches works with that ?

I have tried compat-wireless-2011-10-21 with the old patches and everything went fine except when I run dirver-select or make ==> an error appear saying unexpected end or something in line 127, so I believe it does not compile with the current kernel or the patches are outdated for this kernel. :confused:

 Please tell me that I do not need to go back to an older version to make my wireless injection works !!!!

 Thank you :)

---

### Post by wildmanne39 on 2011-10-23
Hi, did you try the driver that comes with 11.10 before you installed compat?

I did some research and I did not find anything that said injection is supported, I really do not know anything about injection.
Thank you

---

### Post by mym2f on 2011-10-28
Thank you very much wildmanne39 ..... :)

I will accept the all-new Ubuntu without the injection support ....

However, I wonder if you can help me with this version since I kind of new to linux and about half of the cool software did not work.:(

I followed the instructions specified at Official Ubuntu Documentation Website and in YouTube videos but no good resutls achieved.

These are two programs that I could not install successfully:

Kdenlive === Video Editing Software === failed bcuz MLT's SDL module problem

Handbrake ==== Video Conversion Software.

(Please tell me if I need to move this discussion to Multimedia & Video section)

Thank you

---

### Post by wildmanne39 on 2011-10-28
Hi, yes you should start a new thread on that topic because this is networking and we are only suppose to work on the issue that the title describes.
Thank you

---

