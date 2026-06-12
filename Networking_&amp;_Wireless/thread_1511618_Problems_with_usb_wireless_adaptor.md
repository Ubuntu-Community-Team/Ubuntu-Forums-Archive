---
title: "Problems with usb wireless adaptor"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by Nidding on 2010-06-17
I recently bought a TRENDnet TEW-648UB wireless adaptor but I can't seem to get it to work. When I plug it in the light on the 'WPS button' flashes, but nothing else happens. Does anyone know if 10.04 is supposed to support this devise and if not, how to get it to work?

---

### Post by Nidding on 2010-06-17
Bump

---

### Post by Nidding on 2010-06-18
Anyone?

---

### Post by b k on 2010-06-18
> **Nidding said:**
> I recently bought a TRENDnet TEW-648UB wireless adaptor but I can't seem to get it to work. When I plug it in the light on the 'WPS button' flashes, but nothing else happens. Does anyone know if 10.04 is supposed to support this devise and if not, how to get it to work?

Hi, I am quite new to Ubuntu myself but I read and learn a lot from this forum and info from the internet.

Perhaps you could start by posting the outputs of 

```
lsusb
```

```
lsmod
```

```
sudo lshw -C network
```

You can save the outputs to a text file and transfer (via usb dongle) to a internet enabled computer for posting back here.

Hopefully some one more IT savvy can help.

I will try to at least provide some useful links.

Thanks

---

### Post by Nidding on 2010-06-29
```
nidding@nidding-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:009d Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0bda:8171 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 15d9:0a33 Dexon Mouse
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```
nidding@nidding-desktop:~$ lsmod
Module                  Size  Used by
nls_utf8                1069  0 
isofs                  29250  0 
ppp_deflate             3682  0 
zlib_deflate           19568  1 ppp_deflate
bsd_comp                4811  0 
ppp_async               6734  0 
crc_ccitt               1339  1 ppp_async
binfmt_misc             6587  1 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  35102  71 
tileblit                2031  1 fbcon
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  1 
vgastate                8961  1 vga16fb
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  282354  1 
dell_wmi                1793  0 
drm_kms_helper         29297  1 i915
ppdev                   5259  0 
dcdbas                  5422  0 
option                 15654  0 
usbserial              33019  1 option
soundcore               6620  1 snd
drm                   162471  3 i915,drm_kms_helper
intel_agp              24177  2 i915
psmouse                63245  0 
serio_raw               3978  0 
parport_pc             25962  1 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
joydev                  8708  0 
shpchp                 28820  0 
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
agpgart                31724  3 drm,intel_agp
output                  1871  1 video
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
hid_microsoft           2647  0 
b44                    25542  0 
usb_storage            39425  0 
ssb                    37336  1 b44
usbhid                 36110  0 
hid                    67032  2 hid_microsoft,usbhid
floppy                 53016  0 
mii                     4381  1 b44

```
and
```
nidding@nidding-desktop:~$ sudo lshw -C network
[sudo] password for nidding: 
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:be:5f:1d
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:17 memory:fe9fe000-fe9fffff memory:28000000-28003fff(prefetchable)

```
Hope this can shed some light on what's wrong :)

---

### Post by b k on 2010-06-30
Hi there, there appears to be a workable solution for a usb wireless adapter with the same device ID [COLOR=Red]0bda:8171[/COLOR] at this link [http://csiuo.com/drupal/content/installing-driver-hiro-h50193-wireless-usb-network-adapter-0bda8171-under-ubuntu-104](http://csiuo.com/drupal/content/installing-driver-hiro-h50193-wireless-usb-network-adapter-0bda8171-under-ubuntu-104)

You must decide whether or not to give it a try.

Please use copy and paste technique to get the codes/commands into a Terminal window on the Ubuntu machine with the wireless problem.

The Terminal commands/codes are as follows (these are taken from the above link):

```
echo 'install r8192s_usb modprobe --ignore-install r8192s_usb ; /bin/echo "0bda 8171" > /sys/bus/usb/drivers/rtl819xU/new_id' | sudo tee /etc/modprobe.d/r8192s_usb.conf
``````
sudo ln -s /lib/firmware/RTL8192SE /lib/firmware/RTL8192SU
``````
sudo modprobe -rf r8192s_usb
```
```
sudo modprobe r8192s_usb
```All credit goes to the person who posted at the above link.

Good luck and  let us know if it works.

---

### Post by owenbot on 2010-08-27
Thank you b k for the repost! works perfectly!

---

### Post by idavid2013 on 2010-08-29
:confused: I've the same usb wireless adapter and the solution above didn't worked for me. Could see the AP but can't connect (keep on asking for the password).
So I decided to compile the Realtek's driver for Linux from their site: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=231&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=231&DownTypeID=3&GetDown=false&Downloads=true)
Just downloaded archive, followed instructions that is in there and everything works perfectly. Hope that will help someone else out there.
Ubuntu ROCKS :guitar:

---

### Post by erkiha on 2010-09-27
If somebody in this thread has tew-648ub usb wifi device, please add your comments, results onto following bug in order to get it working out of box: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/645824](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/645824)

regards,

erki

---

### Post by Nidding on 2010-10-03
> **b k said:**
> Hi there, there appears to be a workable solution for a usb wireless adapter with the same device ID [COLOR=Red]0bda:8171[/COLOR] at this link [http://csiuo.com/drupal/content/installing-driver-hiro-h50193-wireless-usb-network-adapter-0bda8171-under-ubuntu-104](http://csiuo.com/drupal/content/installing-driver-hiro-h50193-wireless-usb-network-adapter-0bda8171-under-ubuntu-104)

You must decide whether or not to give it a try.

Please use copy and paste technique to get the codes/commands into a Terminal window on the Ubuntu machine with the wireless problem.

The Terminal commands/codes are as follows (these are taken from the above link):

```
echo 'install r8192s_usb modprobe --ignore-install r8192s_usb ; /bin/echo "0bda 8171" > /sys/bus/usb/drivers/rtl819xU/new_id' | sudo tee /etc/modprobe.d/r8192s_usb.conf
``````
sudo ln -s /lib/firmware/RTL8192SE /lib/firmware/RTL8192SU
``````
sudo modprobe -rf r8192s_usb
```
```
sudo modprobe r8192s_usb
```All credit goes to the person who posted at the above link.

Good luck and  let us know if it works.

This seems to work for me as well, as I can now see the local networks and try to connect to them. However, I can't seem to actually connect to my own, which is kind of a puzzle to me. This could easily be due to a security setting I have overlooked however.

---

### Post by erkiha on 2010-10-12
> **Nidding said:**
> This seems to work for me as well, as I can now see the local networks and try to connect to them. However, I can't seem to actually connect to my own, which is kind of a puzzle to me. This could easily be due to a security setting I have overlooked however.

Same for me, this helps to recognize device but I'm still not able to connect.

---

### Post by tdjokic on 2011-06-05
O my God! It Works, thank you guys a lot! It is this adapter: [http://www.amazon.com/BlueProton-High-Gain-802-11n-Wireless-compatible/dp/B003JKXFHI/ref=sr_1_35?ie=UTF8&qid=1303659680&sr=8-35](http://www.amazon.com/BlueProton-High-Gain-802-11n-Wireless-compatible/dp/B003JKXFHI/ref=sr_1_35?ie=UTF8&qid=1303659680&sr=8-35) They call it "Chipset: RTL8188SU" but computer says it is 8171.

---

### Post by bswylie on 2012-05-12
Hi,

The procedure described by b k works for me, until I restart the computer. After the restart, the procedure must be followed again to set up the TEW-648 wireless adapter.

I'd upgrade to the latest LTS but I am using LinuxCNC which is not supported on 12.04 yet.

Any ideas? I'd be really grateful.

Kind regards,
Brian

---

### Post by morrism on 2012-10-11
> **idavid2013 said:**
> :confused: I've the same usb wireless adapter and the solution above didn't worked for me. Could see the AP but can't connect (keep on asking for the password).
So I decided to compile the Realtek's driver for Linux from their site: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=231&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=231&DownTypeID=3&GetDown=false&Downloads=true)
Just downloaded archive, followed instructions that is in there and everything works perfectly. Hope that will help someone else out there.
Ubuntu ROCKS :guitar:

I have the Realtek 8191. Working with an Acer x1430 desktop PC. I have downloaded said files. However, I cannot find the instructions, there are a lot of folders and not much in the way of workable code. Anyone able to help?
I have tried the synaptic package manager route but no luck there.

---

