---
title: "Dlink DWA -111 USB Wifi card on Ubuntu 12.10 in Vmware workstation"
date: 2013-04-20
forum: Networking &amp; Wireless
---

### Post by alcyonne on 2013-04-20
I am trying to make my Dlink DWA-111 work on Ubuntu 12.10 in  vmware workstation. since Vmware doesn't recognize my integrated wifi  card as a wifi card, I changed to a USB one. This one is recognized in  windows 8, but when I launch my Ubuntu VM, it doesn't work at all. I'm  still getting connected.
  Disabling the USBb from the host and activating it on the Vm:[INDENT]   lsusb
 [/INDENT]
shows me the dlink usb card
  
> lsmod   show me the rt73 module
  
>iwconfig, ifconfig, iwlist   shows nothing.
  I tried many solutions found on Google and forums as compiling drivers, getting ndiswrapper, ndisgtk. ndiswrapper -l shows me my driver with the ID of the device but when I enter sudo modprobe ndiswrapper I got:
  
FATAL:Module ndiswrapper not found.   and still no wifi on my Ubuntu.
  Any assistance will be greatly appreciated.

---

### Post by wildmanne39 on 2013-04-20
Please try:
```
echo "options rt73usb nohwcrypt=y" | sudo tee /etc/modprobe.d/rt73usb.conf
sudo modprobe -rfv rt73usb
sudo modprobe -v rt73usb
```
Thanks

---

### Post by alcyonne on 2013-04-20
here is the result

for echo "options rt73usb nohwcrypt=y" | sudo tee /etc/modprobe.d/rt73usb.conf
```

options rt73usb nohwcrypt=y
```

and for sudo modprobe -v rt73usb

```
insmod /lib/modules/3.5.0-17-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/lib/crc-itu-t.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko nohwcrypt=y
```

---

### Post by wildmanne39 on 2013-04-20
Can you connect know?
If not please copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by alcyonne on 2013-04-20
here u are for the netinfo file...
I took a loook at the file and I found a difference between lsusb in the file and when I wrote it to a terminal.
In a Terminal, lsusb shows me my usb card:

```
**Bus 001 Device 000: ID 07d1:3c06 D-Link System DWA-111 802.11bg Wireless Adapter [Ralink RT2571W]**
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 002 Device 005: ID 413c:8160 Dell Computer Corp. Wireless 365 Bluetooth
```

Thank you.

---

### Post by wildmanne39 on 2013-04-20
The driver is the correct one, but the adaptor is not shown at all in the file.

That is the exact command in the terminal or from the script it should give the same results.

Did you have the device capatured in the VM when you ran the script?

I have an adaptor that uses that same driver and it works great with that parameter.

Why do you need it to work in the vm when you can connect through the host?
Thanks

---

### Post by alcyonne on 2013-04-20
between the command in terminal and the script's result there is a difference as you can see...I ran the command on the terminal just after the end of the script
I can connect through the host using wired connection, that's what I'm doing now...My aim on ubuntu is to do some pentesting and other network scanning stuff...the problem is my networks adresses are 192.168.1.xxx and with the wired connection my ip adress on ubuntu is as 192.168.71.xxx........so when I start a scanner, to which interface should he listen and which host, the VM or the real host...SInce I got not result on listening to the ip adress of the Vm, I thought that is a matter of connection way...And as I saw in several forums and resources on the internet, the wired connection won't give me the same results as if my network card was directly bridged to the network....
Correct me if I'm wrong
Thank you

---

### Post by wildmanne39 on 2013-04-20
I have never done pentesting so I do not know about that.

Your vm should have the same ip address as your host.

Make sure your adaptor is captured by the vm then run the wireless script again and post the results of the netinfo.txt file again the one you need to post will have a number in the name since it will be a second file with the same name.
Thanks

---

### Post by alcyonne on 2013-04-20
Here you are...the new file
the vm has the same adress when we see it  form the router, because I selected NAT: so that the host and the vm  share the same ip address...but when entering ifconfig i got a different address, I think it's only between the vm and the host.
still a diffrence between lsusb in the file and in the terminal
Just something that i've just seen: when I use lsusb on terminal many times, the card doesn't show everytime.

---

### Post by wildmanne39 on 2013-04-20
There are error messages in the file you posted but I have not found a solution.

Please make sure you can see the device with the terminal then run the script again to see if it can give us more information.

Try removing the device and then plug it back in go to network manger top right corner of the screen and [COLOR="#FF0000"]make sure wireless is enabled and have your wired connection unplugged from your computer before doing any of these things.[/COLOR]
Thanks

---

### Post by alcyonne on 2013-04-20
Ok I'll try...
Otherwise I'm on a fresh new installation of ubuntu...... since the old one didn't want to start again
The cause: 
I started the ubuntu software center that asked me to update the system since 330 package have changed, I agreed, and after that it was done, ubuntu asked me to reboot...And When I did it...I got error messages, as you can see in the attached file...perhaps it has a relation with the errors in the file.

I'll keep you informed

---

### Post by wildmanne39 on 2013-04-20
That is the same mesages in the file, but it did not require you to reinstall ubuntu, if you install the exact same version it will not fix the error messages anyway I do not believe.

It did not prevent you from bootting correct? if so you could probably just remove or plug in the device to be able to boot.
Thanks

---

### Post by alcyonne on 2013-04-20
I turned of my integrated wifi card, so i don't get connected to the internet by the wired connection.
I also get my VM network setting on bridged, so the usb wifi car should have its own address in the VM. I connected the usb to the VM
always a difference between lsusb and the script's result as you can see in attached files.
Still no wifi, and no wireless detected on network manager.

Just a little remark. I tried lsusb twice, and each time the usb name is correct, the ID is correct, nut the device number changes as u can see on the attached image...is there any relation....perhaps the rt73 driver is not as stable as it should for the DWA-111?? Am I wrong...?

Thank you

P.S.: For installing a fresh ubuntu, yes the errors stopped me from starting ubuntu in tty and other starting modes....I also got a problem (resolved) about the screen that hangs on checking battery....That's why I preferred to have a new installation.

---

### Post by wildmanne39 on 2013-04-21
The driver is sound!!! I believe part of it is the bug in the kernel that is spitting out those errors maybe try to ugrade the kernel and see if that helps with the error messages.

Please post the results of:
```
cat /etc/lsb-release; uname -a
lsusb
iwconfig
rfkill list all
lsmod
nm-tool
sudo iwlist scan
```
Are you sure you installed the packages needed for the vm to use usb devices?
Thanks

---

### Post by alcyonne on 2013-04-21
The packages are installed automaticalyy when I created the VM and  specified the iso file that contain the installation...I think you are  talking about Vmware tools.
I tried other usb devices such as usb drives...and it works fine, automatically detected and their icons locked to the launcher.
results of the commands:
```
anas@ubuntu:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
anas@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
Linux ubuntu 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux
```
as you can see lsusb doesn't show the usb card, sometimes it shows it sometimes not
```
anas@ubuntu:~$ lsusb
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
anas@ubuntu:~$ lsusb
Bus 001 Device 020: ID 07d1:3c06 D-Link System DWA-111 802.11bg Wireless Adapter [Ralink RT2571W]
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
anas@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

```
anas@ubuntu:~$ rfkill list all
anas@ubuntu:~$ 
```

```
anas@ubuntu:~$ lsmod
Module                  Size  Used by
rt73usb                26662  0 
crc_itu_t              12627  1 rt73usb
rt2x00usb              19941  1 rt73usb
rt2x00lib              48562  2 rt73usb,rt2x00usb
mac80211              461161  2 rt2x00usb,rt2x00lib
cfg80211              175375  2 rt2x00lib,mac80211
uas                    17556  0 
usb_storage            39350  0 
vmhgfs                 53715  0 
vsock                  39001  0 
acpiphp                23368  0 
snd_ens1371            24446  2 
gameport               15016  1 snd_ens1371
snd_ac97_codec        105616  1 snd_ens1371
ac97_bus               12670  1 snd_ac97_codec
snd_pcm                80163  2 snd_ens1371,snd_ac97_codec
snd_seq_midi           13132  0 
coretemp               13168  0 
snd_rawmidi            25382  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
vmw_balloon            12593  0 
microcode              18209  0 
snd_timer              24411  2 snd_pcm,snd_seq
joydev                 17161  0 
psmouse                84843  0 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13031  0 
snd                    61991  11 snd_ens1371,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14599  1 snd
snd_page_alloc         14036  1 snd_pcm
vmwgfx                105346  3 
ttm                    75534  1 vmwgfx
drm                   230463  4 vmwgfx,ttm
bnep                   17707  2 
mac_hid                13037  0 
rfcomm                 37276  0 
vmci                   60344  2 vmhgfs,vsock
bluetooth             183228  10 bnep,rfcomm
parport_pc             31968  1 
ppdev                  12817  0 
i2c_piix4              12983  0 
shpchp                 32189  0 
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
hid_generic            12445  0 
mptspi                 22145  2 
mptscsih               39113  1 mptspi
mptbase                96272  2 mptspi,mptscsih
floppy                 55444  0 
usbhid                 41702  0 
hid                    82142  2 hid_generic,usbhid
vmxnet                 20715  0 
vmw_pvscsi             22043  0 
vmxnet3                44131  0 
```

nm-tool, shows my wired connection with my integrated wifi card, otherwise it shows nothing
```

nm-tool 

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            vmxnet
  State:             connected
  Default:           yes
  HW Address:        00:0C:29:01:50:FD

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.71.130
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.71.2

    DNS:             192.168.71.2
```
```

anas@ubuntu:~$ sudo iwlist scan
[sudo] password for anas: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

Still advising me to upgrade the kernel? how?

Thank you

---

### Post by alcyonne on 2013-04-23
Hi Wildman,
As you can see I have upgrade my kernel to 3.8.8
Always the same results
```
morpheus@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
Linux ubuntu 3.8.8-030808-generic #201304170248 SMP Wed Apr 17 06:58:01 UTC 2013 i686 i686 i686 GNU/Linux

morpheus@ubuntu:~$ lsusb
Bus 001 Device 000: ID 07d1:3c06 D-Link System DWA-111 802.11bg Wireless Adapter [Ralink RT2571W]
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
morpheus@ubuntu:~$ lsusb
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
morpheus@ubuntu:~$ lsusb
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

morpheus@ubuntu:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
 
morpheus@ubuntu:~$ rfkill list all
 
morpheus@ubuntu:~$ lsmod
Module                  Size  Used by
rt73usb                27028  0
crc_itu_t              12627  1 rt73usb
rt2x00usb              20099  1 rt73usb
rt2x00lib              49096  2 rt73usb,rt2x00usb
mac80211              541819  2 rt2x00usb,rt2x00lib
cfg80211              449757  2 rt2x00lib,mac80211
acpiphp                23447  0
snd_ens1371            24847  2
gameport               15088  1 snd_ens1371
snd_ac97_codec        110254  1 snd_ens1371
ac97_bus               12670  1 snd_ac97_codec
snd_pcm                85934  2 snd_ens1371,snd_ac97_codec
snd_seq_midi           13132  0
snd_rawmidi            25157  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
coretemp               13324  0
snd                    57014  11 snd_ens1371,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vmw_balloon            12700  0
soundcore              12600  1 snd
psmouse                77519  0
snd_page_alloc         18398  1 snd_pcm
joydev                 17329  0
microcode              18433  0
serio_raw              13031  0
vmwgfx                115940  3
bnep                   17852  2
rfcomm                 38400  0
ttm                    72088  1 vmwgfx
bluetooth             211395  10 bnep,rfcomm
drm                   229318  4 vmwgfx,ttm
mac_hid                13077  0
i2c_piix4              13227  0
shpchp                 32265  0
parport_pc             27612  1
ppdev                  12849  0
lp                     17455  0
parport                40930  3 parport_pc,ppdev,lp
hid_generic            12484  0
pcnet32                40884  0
floppy                 60183  0
mptspi                 22474  2
mptscsih               39532  1 mptspi
mptbase                96852  2 mptspi,mptscsih
usbhid                 46125  0
hid                    82878  2 hid_generic,usbhid
vmw_pvscsi             22352  0
vmxnet3                44671  0
 
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            pcnet32
  State:             disconnected
  Default:           no
  HW Address:        00:0C:29:B6:73:8D
 
  Capabilities:
    Carrier Detect:  yes
 
  Wired Properties
    Carrier:         on
 
morpheus@ubuntu:~$ sudo iwlist scan
[sudo] password for morpheus:
lo        Interface doesn't support scanning.
 
eth0      Interface doesn't support scanning.
```

As you can see, eveything looks like when I was using kernel 3.5....
Could this have a link with the driver...As you can see in lsusb the device doesn't show everytime I use it....maybe the driver is not stable or something else like that...?

Thank you...

---

### Post by wildmanne39 on 2013-04-23
The device not showing up has nothing to do with the driver, even if the driver is not installed you should see the device everytime.
I will do a little more research but I am not hopeful.
Thanks

---

### Post by wildmanne39 on 2013-04-23
Also can you remove all the netinfo.txt files in your home folder then run the script again and post all the output of the file because this report is missing some information and we need to see if the error messages are still present towards the bottom of the file.
Thanks

---

### Post by alcyonne on 2013-04-24
here you are :)
Thank you

---

### Post by wildmanne39 on 2013-04-24
Hi, still the same error messges and the device not showing up, I am afraid that I am out of ideas, in the bug reports there was not any real progress either.

---

