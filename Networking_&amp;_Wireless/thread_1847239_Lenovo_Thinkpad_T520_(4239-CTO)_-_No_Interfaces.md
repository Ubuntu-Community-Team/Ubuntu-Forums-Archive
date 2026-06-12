---
title: "Lenovo Thinkpad T520 (4239-CTO) - No Interfaces"
date: 2011-09-20
forum: Networking &amp; Wireless
---

### Post by Spaceman Spiff on 2011-09-20
Hello all,

  Received my new work laptop today.  Would like to use the latest Ubuntu LTS so I installed Ubuntu 10.04(64 bit).  Currently having driver issues with the networking.  I am working from my personal laptop so I will be unable to link the exact output, but I will be able to supply the necessary info.

lspci -nn: Reveals a Network controller [0280], Realtek [10ec: 8176]

ifconfig -a: Only reveals the lo. (iwconfig reveals nothing)

I would like to at least begin with my **wired** adapter.  There seems to be plenty of documentation for the wireless adapter.  HOWEVER, I have been unable to find any similar situations with the wired adapter not working.  Where can I find a driver for this mess.

Steps Taken so far:
1) Searched for drivers on the lenovo website (which sucks.)
2) Disabled Wake on LAN in the bios.

Any help would be appreciated, thank you very much.  At

---

### Post by Spaceman Spiff on 2011-09-20
Update:  Discovered this machine has a Intel 82579 LM NIC.  Thus, I downloaded the Linux driver from Intel's website... However, I am running 64 bit and I think the driver is for 32 bit.  Nevertheless I will try.  Any further advice would be great, thank you.

Works.

... Hate you Lenovo, so very much.

---

### Post by praseodym on 2011-09-20
Hi,

please show:

```
lspci -nnk | grep -iA2 net
iwconfig
ifconfig -a
lsmod
rfkill list
```

---

### Post by Senplanet on 2011-09-20
I have the same problem. I just installed ubuntu 10.04 on new lenovo e125 (without CD-ROM) via USBstick. I do  not have any eth0, My output for 

```
lspci -nnk | grep -iA2 net
iwconfig
ifconfig -a
lsmod
rfkill list
```is >

```

uran@atmo:~$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
02:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)
03:00.0 Class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)

uran@atmo:~$ iwconfig
lo        no wireless extensions.

pan0      no wireless extensions.

uran@atmo:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)

pan0      Link encap:Ethernet  HWaddr fa:de:44:db:47:08  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


uran@atmo:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10866  1 
fat                    55350  1 vfat
binfmt_misc             7960  1 
rfcomm                 40393  4 
ppdev                   6375  0 
sco                     9649  2 
bridge                 53152  0 
stp                     2171  1 bridge
bnep                   11884  2 
l2cap                  34807  16 rfcomm,bnep
snd_hda_codec_atihdmi     3023  1 
snd_hda_intel          25805  2 
snd_hda_codec          85759  2 snd_hda_codec_atihdmi,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62851  0 
videodev               40518  1 uvcvideo
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
v4l1_compat            15495  2 uvcvideo,videodev
softcursor              1565  1 bitblit
v4l2_compat_ioctl32    11892  1 videodev
btusb                  13097  2 
bluetooth              58685  9 rfcomm,sco,bnep,l2cap,btusb
snd                    71283  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  20623  0 
output                  2503  1 video
psmouse                65040  0 
serio_raw               4918  0 
i2c_piix4               9639  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
vga16fb                12757  1 
vgastate                9857  1 vga16fb
lp                      9336  0 
parport                37160  2 ppdev,lp
usb_storage            50377  1 
ahci                   38030  3 

uran@atmo:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


```

---

### Post by praseodym on 2011-09-21
Try this driver:

```
sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/3140032/rtl8192ce_linux_2.6.0006.0321.2011.tar.gz
tar xvf rtl8192ce_linux_2.6.0006.0321.2011.tar.gz
cd rtl8192ce_linux_2.6.0006.0321.2011/
make clean
make
```
Then try
```
sudo make install
```
If there are error messages here, move the module by hand, if not reboot:
```
sudo cp HAL/rtl8192/r8192ce_pci.ko /lib/modules/$(uname -r)/kernel/net/wireless/
sudo depmod -a
sudo modprobe -v r8192ce_pci
sudo update-initramfs -u
```

---

### Post by Spaceman Spiff on 2011-09-29
I apologize for the late response.  I fixed my solution.

The Lenotov T520 contained an Intel NIC which I determined from Windows 7.  I went to Intel's website and downloaded their driver...

the e1000e, installed, and it works.

Hopefully this will save someone the time I wasted ... Lenovos....

---

### Post by krtica on 2011-10-18
I'm very interested in a way you managed to install 10.04 on your T520, since I'v got one as well.

I installed 11.04 on mine, but I'm not satisfied. It's not quite stable and some of 10.04 features are lost.

Since this laptop is with Sandy Bridge chip, did you use backported kernel?
Are special keys working?
Does it have some issues in general?

Ty.

---

### Post by krtica on 2011-10-24
Finally! :D

I managed to install Lucid Lynx on my Thinkpad T520. :mrgreen: Such joy!

Here is the whole process:


1. Download latest ISO at [http://www.ubuntu.com/download/ubuntu/download]("http://www.ubuntu.com/download/ubuntu/download")

2. Download latest Intel e1000e driver at [http://downloadcenter.intel.com/]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&lang=eng&OSVersion=Linux*&DownloadType=%0ADrivers%0A") and save downloaded file to USB drive.

3. Start your laptop and choose live session (“*Try Ubuntu*“).

You’ll notice that there is no any kind of network connection at the moment.
Mount your USB drive and go to the folder where your Intel e1000e driver is located.
Untar/unzip archive:
```
tar zxf e1000e-x.x.x.tar.gz
```
Change to the driver src directory:
```
cd e1000e-x.x.x/src/
```
Compile the driver module:
```
sudo make install
```
Load the module using either the insmod or modprobe command:
```
sudo modprobe e1000e
```
At this point your network adapter should start working. Detailed information about installing the driver can be found on [http://downloadmirror.intel.com/15817/eng/README.txt]("http://downloadmirror.intel.com/15817/eng/README.txt")

4. Now when you are able to connect to Internet you can install Ubuntu.

5. After restarting a computer, you have to repeat procedure for installing network card. (step 3)

6. Now you have to add next ppa’s:
```
apt-add-repository ppa:canonical-kernel-team/ppa
apt-add-repository ppa:glasen/intel-driver
apt-add-repository ppa:f-hackenberger/x220-intel-mesa
apt-get update
```

7. Install latest available backport kernel:
```
sudo apt-get install -y linux-image-generic-lts-backport-oneiric linux-headers-generic-lts-backport-oneiric
```
 
8. Update your packages:
```
sudo apt-get dist-upgrade -y
```
 
9. Restart your computer.

Voila! **Everything** works for me. (At least things that I have tested: eth, wifi, buttons, display, sound, mic, camera, suspend, hibernate,...)

Maybe this is not the best or smartest way to do it, but it worked for me, and I finally got back my favorite OS. =D>

---

### Post by Spaceman Spiff on 2011-11-07
krtica, awesome write up.  I am still new to linux, and I am confused as to why you needed to do such a complex install of 10.04?  I simply put the 64 bit cd in and installed.  I am assuming I did something wrong :confused:  Thanks for any advice!

Edit:  Yes all my special keys work (I am assuming you mean volume buttons and such).  So far only one specific issue.  I had to turn off the "Optimus" technology in the BIOS to install NVidia's proprietary drivers.  I also had to do the typical Lenovo wireless card driver install.  What does this mean for me?  Everytime the kernel headers upgrade, I have to spent a few minutes rebuilding and installing all my drivers.  Lucky for me, they all came with AWESOME readmes.

---

### Post by krtica on 2011-11-09
Spaceman,
I wanted 10.04 specifically, not any other Ubuntu, like 11.04 or 11.10. I tried those also, and they worked 'out of box'. But stability in some apps under 11.04 and 11.10 was a big issue for me.

Since 10.04 was released before of kernels that support my hardware (as network and wireless card, graphic card (Intel HD 3000, I think) and "Sandy Bridge" processor) I couldn't install it without additional workarounds.

I also find other useful things for Lenovo ThinkPad T520.
If you have that laptop, you may be interested in this:

[http://putokaz.wordpress.com/2011/10/24/improving-power-consumption-on-ubuntu-laptop-with-sandy-bridge-processor/](http://putokaz.wordpress.com/2011/10/24/improving-power-consumption-on-ubuntu-laptop-with-sandy-bridge-processor/)

[http://putokaz.wordpress.com/2011/11/02/fixing-cpu-fan-on-lenovo-thinkpad-t520/](http://putokaz.wordpress.com/2011/11/02/fixing-cpu-fan-on-lenovo-thinkpad-t520/)

---

### Post by Spaceman Spiff on 2011-12-01
krtica, I am running 10.04, I had no problem installing right off a live 64 bit cd.  The only difficulty was finding all those drivers afterwards.  Is my install not taking full advantage of my CPU?

---

### Post by krtica on 2011-12-02
Hm... Not sure. You managed to install it from Live CD with no problems, so I'm not sure do we have same hardware. :/
I have found many improvements after I have done things described on those links.
So, in my case, I realy found some improvments on my system.

---

### Post by fifteenrabbits on 2012-01-28
Hey there krtica.

I installed onto my 42435uu using your instructions. Everything went as it should.

The problem is, now apt is looking to update some stuff and I'm given TWO different kernels to update to at the same time. One from the standard repository (which wants to update to a kernel with the same name as the one that I have now) and one from the canonical-kernel-team repository which I added from your instructions. That kernel seems to be a downgrade from 3.0.0-15-generic to 2.6.32-38-generic-pae.

What should I do?

Thanks!

---

### Post by fifteenrabbits on 2012-02-09
I'm still having this problem. Nobody?

All these "updates" are piling up in synaptic. Mostly an array from the ppa that I got the backport from.

---

### Post by krtica on 2012-02-10
Don't worry, it's normal. I'm receiving both updates, but I use only 3.x.
Graphics won't work with 2.x
You should go in synaptic and "completely remove" all old kernels you don't use any more.
After removing old kernels, go to terminal and run command:
```
update-grub
```

---

