---
title: "Wireless not working on HP mini 220 with Ubuntu 10.04"
date: 2012-02-17
forum: Networking &amp; Wireless
---

### Post by jotso23 on 2012-02-17
I just got this new laptop and I installed ubuntu 10.04 on it first thing, however it doesn't seem to believe that it has a wifi card installed and is not even giving me the option of turning my wifi on. Because of this the wifi button on the keyboard always shows a red light, I hope that fixing whatever is happening with the wifi will fix the light. Oh, the mute button light also doesn't change color (it remains red) I hope, and believe, that all of these 3 things are connected to the problem of the wifi card. As a last note, when first configuring Windows 7 starter, the wifi definitely worked, so I don't believe that it is a hardware issue.

Thanks in advance for any help you can give me,

Jotso23

---

### Post by jotso23 on 2012-02-17
Scratch that sorry, I have a mini 210, if that makes a difference.

---

### Post by wildmanne39 on 2012-02-18
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by jotso23 on 2012-02-18
Thanks for replying, And here are the results.

```
jordan@jordan-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
Linux jordan-laptop 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 GNU/Linux
jordan@jordan-laptop:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Kernel driver in use: r8169
    Kernel modules: r8169
02:00.0 Network controller [0280]: RaLink Device [1814:5390]
jordan@jordan-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jordan@jordan-laptop:~$ rfkill list all
jordan@jordan-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_idt      52042  0 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
uvcvideo               57438  0 
video                  17375  0 
videodev               34425  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
output                  1871  1 video
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63677  0 
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
vga16fb                11385  1 
vgastate                8961  1 vga16fb
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            40033  0 
ahci                   32680  2 
r8169                  34140  0 
mii                     4381  1 r8169

```

---

### Post by josephmills on 2012-02-18
hello there have you had a chance to read this thread   POST # 58 ? 

[http://ubuntuforums.org/showthread.php?t=1779005&page=6](http://ubuntuforums.org/showthread.php?t=1779005&page=6)

---

### Post by jotso23 on 2012-02-18
I hadn't had a chance to look at that, thank you for it, how do i know which wireless card I have thought? it sounds like, based off reading that post, that I need to know which I have.

---

### Post by josephmills on 2012-02-18
you have the ```
02:00.0 Network controller [0280]: RaLink Device [1814:5390]
``` version of your card. this is then important part 1814:5390  so go to the ralink site and match up.

---

### Post by jotso23 on 2012-02-18
[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501) i went to this page and couldn't find that one, is there something I'm missing?

---

### Post by josephmills on 2012-02-18
> **jotso23 said:**
> [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501) i went to this page and couldn't find that one, is there something I'm missing?

 RT539xPCIe    aka [http://www.ralinktech.com/en/04_support/license.php?sn=5001](http://www.ralinktech.com/en/04_support/license.php?sn=5001)

let us know how it goes

---

### Post by jotso23 on 2012-02-18
Alright, I've gotten down to the first part of the code section and I typed in the first line and this is what happened: ```
jordan@jordan-laptop:~$ cd setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO
bash: cd: setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO: No such file or directory
jordan@jordan-laptop:~$ 

```

---

### Post by josephmills on 2012-02-18
could we see a ```
ls ~/Downloads 
```  thanks

---

### Post by jotso23 on 2012-02-18
I typed that in and this is all I got back:

```
jordan@jordan-laptop:~$ ls ~/Downloads
jordan@jordan-laptop:~$ 
```

---

### Post by josephmills on 2012-02-18
Oh No :>) jk 
Where are you storing your Downloaded files ? Did you download the driver?

---

### Post by jotso23 on 2012-02-18
Ah, it looks like I've been storing them in the 'jordan' folder.

---

### Post by josephmills on 2012-02-18
> **jotso23 said:**
> Ah, it looks like I've been storing them in the 'jordan' folder.

ohh cool can we see a ```
ls /home/jordan/
```thanks

---

### Post by jotso23 on 2012-02-18
Here you go:

```
jordan@jordan-laptop:~$ ls /home/jordan/
Desktop    Downloads         Music     Public     Videos
Documents  examples.desktop  Pictures  Templates
jordan@jordan-laptop:~$ 


```

---

### Post by jotso23 on 2012-02-18
I thought this one might be more helpful:

```
jordan@jordan-laptop:~$ ls /home/jordan/Downloads
2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL
jordan@jordan-laptop:~$ 

```

---

### Post by wildmanne39 on 2012-02-19
[QUOTE=jotso23;11699077]I thought this one might be more helpful:

```
jordan@jordan-laptop:~$ ls /home/jordan/Downloads
2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL
jordan@jordan-laptop:~$ Hi, let's do it the easy way.

You will just copy and paste the commands one line at a time and watch the terminal for errors.
[CODE]sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms patch fakeroot unzip
wget http://media.cdn.ubuntu-de.org/forum/attachments/3208747/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip
unzip angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip
cd angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/
sudo make
sudo make install
sudo modprobe -v rt5390sta
sudo depmod -a
sudo update-initramfs -u 
``` 
Then reboot with your wired connection unplugged.
Thanks

---

### Post by jotso23 on 2012-02-19
Thank you so much!! you are truly an angel made human to help a man as you have. Again thank you!

---

### Post by wildmanne39 on 2012-02-19
Hi, your welcome, please use thread tools at the top of the page and mark thread as solved.
Thanks

---

