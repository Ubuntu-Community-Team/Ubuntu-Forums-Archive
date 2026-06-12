---
title: "Turning wireless back on"
date: 2011-06-09
forum: Networking &amp; Wireless
---

### Post by Priceguy on 2011-06-09
I'm feeling really dumb. When I first installed Ubuntu on my laptop a few years ago it automatically found a bunch of wireless networks and since I don't use wireless networking I turned the function off. Now I need to use it and can't figure out how I turned it off or how to turn it back on.

I'm running Ubuntu 10.04. There is a hardware switch but it's turned on and when I boot to Windows it finds wireless networks. The connection manager shows nothing under the Wireless tab and iwlist scan gives the following result:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.

---

### Post by hakermania on 2011-06-09
My way (maybe there's a much easier way)
1) Install aircrack-ng
2) ```
ifconfig wlan0 up
```
```
airmong-ng start wlan0
```

I don't know if this is gonna work but it works on my laptop when network is down

---

### Post by chili555 on 2011-06-09
> (maybe there's a much easier way)Indeed there is:```
rfkill list all
sudo rfkill unblock all
```Post back if you need more help.

---

### Post by Priceguy on 2011-06-09
I think I do. When I did rfkill list all I got

```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

I then did sudo rfkill unblock all, but I still can't find wireless networks and iwlist scan returns the same result as before.

---

### Post by chili555 on 2011-06-09
Let's see:```
iwconfig wlan0
```Do you know what your wireless driver is? Maybe we have a conflict. If you do not know it, please run and post:```
lsmod
```Thanks.

---

### Post by Priceguy on 2011-06-09
iwconfig wlan0 returned:

```
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

Under System - Administration - Hardware Drivers I have two wireless drivers, Broadcom B43 and Broadcom STA Proprietary; they are both inactivated so I tried activating Broadcom B43 but still couldn't find wireless networks.

lsmod returned:

```
Module                  Size  Used by
binfmt_misc             6587  1 
rfcomm                 33421  4 
sco                     7917  2 
ppdev                   5259  0 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
vboxdrv               168753  0 
snd_hda_codec_atihdmi     2367  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec_idt      52042  1 
snd_hda_intel          22069  4 
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
arc4                    1153  2 
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                677684  2 
snd_timer              19098  2 snd_pcm,snd_seq
joydev                  8740  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49943  1 radeon
b43                   163556  0 
hp_accel               11144  0 
uvcvideo               57374  0 
drm_kms_helper         29329  1 radeon
lis3lv02d               6096  1 hp_accel
mac80211              205402  1 b43
usblp                  10481  0 
snd                    54244  20 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
drm                   162377  4 radeon,ttm,drm_kms_helper
ati_agp                 5094  0 
input_polldev           2482  1 lis3lv02d
btusb                  10989  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
video                  17375  0 
k8temp                  3152  0 
psmouse                63245  0 
serio_raw               3978  0 
output                  1871  1 video
i2c_piix4               8335  0 
cfg80211              126144  2 b43,mac80211
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
led_class               2864  2 b43,hp_accel
i2c_algo_bit            5028  1 radeon
agpgart                31724  3 ttm,drm,ati_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67096  1 usbhid
usb_storage            39841  0 
r8169                  34140  0 
pata_atiixp             3148  0 
ssb                    38934  1 b43
mii                     4381  1 r8169
ahci                   32360  2 
```

---

### Post by chili555 on 2011-06-09
b43 and ssb are apparently your wireless driver. Let's have a look at:```
dmesg | grep b43
lspci -nnk 
```Just show us the Broadcom wireless part of the last command.

---

### Post by Priceguy on 2011-06-10
dmesg | grep b43 produced several error messages telling me to download firmware from wireless.kernel.org, which told me to run sudo apt-get install b43-fwcutter, which I did followed by a reboot. Right-clicking the connection manager now doesn't even show "Wireless" which it did before and iwlist scan doesn't show wlan0 anymore.

dmesg | grep b43 now returns
```
[    1.197445] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.197456] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
```

and lspci -nnk returns
```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb
```

---

### Post by chili555 on 2011-06-10
Let's see:```
lsmod | grep -e b43 -e wl
rfkill list all
dmesg | grep wlan
```Thanks.

---

### Post by Priceguy on 2011-06-10
Neither the lsmod or dmesg commands returned anything; rfkill list all returns:
```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

Thanks for all your help; I just wish I understood what we were doing at all... :)

---

### Post by chili555 on 2011-06-10
> I just wish I understood what we were doing at all... :)Sometimes, I wish I knew what to do, too! I am a bit stumped. Notice in post #4 it reported the status of your wireless LAN? Now it doesn't. I wonder why. It's sort of like your wireless card has gone away on vacation. The correct driver and firmware don't start up the wireless card, connect and start downloading mp3s and pictures of the cat from the grandparents!!!

Now Dr. Chili will do exploratory surgery. We are going to collect a lot of data and put it all in a text file and zip it up so I can analyze it. Please reboot, open a terminal and do:```
dmesg > price.txt
ls -al /lib/firmware/b43 >> price.txt
lsmod >> price.txt
lspci -nnk >> price.txt
sudo cat /var/log/syslog | tail -n50 >> price.txt
zip price.zip price.txt
```In your user directory you will find a file called price.zip. Attach it to your reply using the paperclip tool at the top of the reply box.

Let's hope we find a startling revelation we can fix so you can get connected.

---

### Post by Priceguy on 2011-06-10
Here we go. Again, thanks.

---

### Post by chili555 on 2011-06-10
There are a ton of these and variations in dmesg:> ACPI Error (psargs-0359): [TPOS] Namespace lookup failure, AE_NOT_FOUNDThis is worth Googling and maybe asking someone over on General Help. I read a few reports that suggest the issue is solved in later kernel versions. You might try a live CD of a later version of Ubuntu and see if it goes away and your computer boots and runs a lot smoother.

Please try:```
sudo modprobe b43
iwconfig
```Now do you have a working wireless interface, wlan0 perhaps? If not, get to a wired ethernet connection and do:```
sudo apt-get install bcmwl-kernel-source dkms
```Reboot and give us your report.

---

### Post by Priceguy on 2011-06-11
After modprobe iwconfig returns:```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

And now iwlist scan finds a bunch of networks! Success! Just one more question, hopefully: how do I get these to show up in the connection manager and subsequently connect to them? I've never used wireless under Ubuntu before.

---

### Post by chili555 on 2011-06-11
If iwlist finds them, then Network Manager should find them. Please see attached. Click the icon and see if they are there.

Let's be sure b43 loads automatically from now on:```
sudo su
echo b43 >> /etc/modules
exit
```Now let's be very sure nothing is set up to block it. Is there any suspicious b43 stuff here?```
ls /etc/modprobe.d
```

---

### Post by Priceguy on 2011-06-13
It works brilliantly and there's nothing about b43 in modprobe.d. Thanks a lot!

---

