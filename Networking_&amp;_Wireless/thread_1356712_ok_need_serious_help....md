---
title: "ok need serious help..."
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by Synoc on 2009-12-16
My Ubuntu simply will no longer stay connected to my router. I loose signal strength and it looses connection altogether every 30 seconds now. and if it takes long enough to reconnect, it forgets my WEP key and forces me to reenter it and then it asks me against 30 seconds later and so on, when it hits that point I have to disable and re-enable it two or three times ot get it to work, or restart the laptop completely to make it work for a little bit. 
it's a Dell Inspiron 1150. Dell says I have a have a DELL WIRELESS 1450, Ubuntu says it's a Broadcom B43.  and if the first quest is "how close were you to your router, the asnwer is less than 30 feet. When I was on Windows I had no trouble whatsoever connecting over 100 feet away.

BTW it seems to have trouble disconnecting the itnernet whanever I USE it. if I'm tryong load a web page, if I'm trying to dowload a file, if I'm just sitting there watching it, it seems to be fine.

---

### Post by Synoc on 2009-12-17
bump

---

### Post by dmizer on 2009-12-17
Please post the output of:
```
lshw -C network
```

---

### Post by bkratz on 2009-12-17
> **Synoc said:**
> My Ubuntu simply will no longer stay connected to my router. I loose signal strength and it looses connection altogether every 30 seconds now. and if it takes long enough to reconnect, it forgets my WEP key and forces me to reenter it and then it asks me against 30 seconds later and so on, when it hits that point I have to disable and re-enable it two or three times ot get it to work, or restart the laptop completely to make it work for a little bit. 
it's a Dell Inspiron 1150. Dell says I have a have a DELL WIRELESS 1450, Ubuntu says it's a Broadcom B43.  and if the first quest is "how close were you to your router, the asnwer is less than 30 feet. When I was on Windows I had no trouble whatsoever connecting over 100 feet away.

BTW it seems to have trouble disconnecting the itnernet whanever I USE it. if I'm tryong load a web page, if I'm trying to dowload a file, if I'm just sitting there watching it, it seems to be fine.

Went to the Dell website and it appears that there are two cards labeled "1450" one being miniPCI and one being USB.

From Dell:

"In normal operation wireless cards receive data packets identifying the presence of new wireless networks. Broadcom-based wireless cards, including select Dell Wireless cards offered on Latitude, Mobile Precision, Inspiron and XPS notebooks, are subject to a security vulnerability"

So it appears that the PCI ( at least ) uses a Broadcom chip so it is no surprise that that the B43 driver is selected.

---

### Post by Synoc on 2009-12-18
Here we go hope this helps
> 
*-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:1a:aa:93
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 multicast=yes
       resources: irq:7 memory:fcffe000-fcffffff memory:24000000-24003fff(prefetchable)
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:11 memory:fcffc000-fcffdfff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:96:b6:47:6b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.7 multicast=yes wireless=IEEE 802.11bg


---

### Post by Synoc on 2009-12-20
bump

---

### Post by dmizer on 2009-12-20
Try this: [http://johnnydopefish.blogspot.com/2009/02/ubuntu-810-dell-inspiron-5100-broadcom.html](http://johnnydopefish.blogspot.com/2009/02/ubuntu-810-dell-inspiron-5100-broadcom.html)

---

### Post by Synoc on 2009-12-25
ok I followed the intructions to a T, but I couldn't get it working last output from lshw -c Network is 
> 
*-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:1a:aa:93
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.8 latency=32 multicast=yes
       resources: irq:7 memory:fcffe000-fcffffff memory:24000000-24003fff(prefetchable)
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:11 memory:fcffc000-fcffdfff
this is after the reboot step.

---

### Post by dmizer on 2009-12-25
Please post the output of
```
ndiswrapper -l
```
and
```
lsmod
```

---

### Post by Synoc on 2009-12-25
For diswrapper -l 
> 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4324) present (alternate driver: ssb)

 and for lsmod
> 
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10272  0 
pcmcia                 36808  0 
iptable_filter          3100  0 
ndiswrapper           185404  0 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_seq_dummy           2656  0 
dell_wmi                2564  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
yenta_socket           24200  1 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
dcdbas                  7292  0 
psmouse                56500  0 
serio_raw               5280  0 
lp                      8964  0 
shpchp                 32272  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
b44                    28684  0 
ssb                    35300  1 b44
mii                     5212  1 b44
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video


---

### Post by zaphod777 on 2009-12-26
There seams to be some issues with 9.10 and wireless. 

I have a Dell XPS 1530 what I had to do was Install the linux backport modules to get the old wireless drivers and then remove network manager and install WICD. I still get some disconnects but not too frequently.

---

### Post by dmizer on 2009-12-26
> **zaphod777 said:**
> There seams to be some issues with 9.10 and wireless. 

I have a Dell XPS 1530 what I had to do was Install the linux backport modules to get the old wireless drivers and then remove network manager and install WICD. I still get some disconnects but not too frequently.

This will not be necessary. You just need to make sure the correct driver is loading for your card. I have the exact same card, and I didn't need to do any of this.

Make sure that b43-fwcutter is not installed by running this command:
```
sudo apt-get remove b43-fwcutter
```

Edit /etc/rc.local with this command:
```
gksudo gedit /etc/rc.local
```

Edit the file so it looks like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

rmmod ndiswrapper
rmmod b43legacy
rmmod ssb
modprobe ndiswrapper

exit 0
```

Save the file, reboot and see if your wireless works then.

---

### Post by bender1234 on 2009-12-26
Hi.

If you are running karmic you need to black list the b43 driver, download, compile and install a new driver from broadcom's site.

I don't have the url at hand sadly, but there is a nice howto on broadcom's site. I was struggling with this on a dell ins. box, but didn't get it up running in time.

merry xmas,
bender

---

### Post by Synoc on 2009-12-26
> **dmizer said:**
> This will not be necessary. You just need to make sure the correct driver is loading for your card. I have the exact same card, and I didn't need to do any of this.

Make sure that b43-fwcutter is not installed by running this command:
```
sudo apt-get remove b43-fwcutter
```Edit /etc/rc.local with this command:
```
gksudo gedit /etc/rc.local
```Edit the file so it looks like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

rmmod ndiswrapper
rmmod b43legacy
rmmod ssb
modprobe ndiswrapper

exit 0
```Save the file, reboot and see if your wireless works then.

Nope, nothing, what's next? or should I just do a clean install and try this again?

---

### Post by dmizer on 2009-12-27
> **Synoc said:**
> Nope, nothing, what's next? or should I just do a clean install and try this again?

Nothing so drastic.

Please reboot and post the output of:
```
lshw -C network
```
and
```
lsmod
```

---

### Post by Synoc on 2009-12-27
> 
lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:1a:aa:93
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.8 latency=32 multicast=yes
       resources: irq:7 memory:fcffe000-fcffffff memory:24000000-24003fff(prefetchable)
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:11 memory:fcffc000-fcffdfff
**@*****:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10272  0 
pcmcia                 36808  0 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
iptable_filter          3100  0 
snd_seq_oss            28576  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
yenta_socket           24200  1 
rsrc_nonstatic         11644  1 yenta_socket
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi                2564  0 
dcdbas                  7292  0 
psmouse                56500  0 
serio_raw               5280  0 
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
shpchp                 32272  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
b44                    28684  0 
ssb                    35300  1 b44
mii                     5212  1 b44
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video


sorry thought I had put that on their already. here we go.

---

### Post by dmizer on 2009-12-27
Ok, one more small change to /etc/rc.local. Edit /etc/rc.local [as before](http://ubuntuforums.org/showpost.php?p=8562114&postcount=14), and make it look like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

rmmod ndiswrapper
rmmod b43legacy
rmmod b44
rmmod ssb
modprobe ndiswrapper
modprobe b44
exit 0
```

Reboot and see if your wireless works then. If not, post the output of lshw -C network again.

---

### Post by Synoc on 2009-12-27
> **dmizer said:**
> Ok, one more small change to /etc/rc.local. Edit /etc/rc.local [as before]("http://ubuntuforums.org/showpost.php?p=8562114&postcount=14"), and make it look like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

rmmod ndiswrapper
rmmod b43legacy
rmmod b44
rmmod ssb
modprobe ndiswrapper
modprobe b44
exit 0
```Reboot and see if your wireless works then. If not, post the output of lshw -C network again.


Still work recognize that I HAVE a wireless connection in Network manager
here's the output
> 
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:1a:aa:93
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.8 latency=32 multicast=yes
       resources: irq:7 memory:fcffe000-fcffffff memory:24000000-24003fff(prefetchable)
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:11 memory:fcffc000-fcffdfff


---

### Post by dmizer on 2009-12-27
Okay, you will get disconnected from your wired connection by doing this, but try running these commands directly, and post any errors or any output:
```
sudo rmmod ndiswrapper
sudo rmmod b43legacy
sudo rmmod b44
sudo rmmod ssb
sudo modprobe ndiswrapper
```

Then post this (since you won't have a wired internet connection you'll need to save the output in a file):
```
lshw -C network
lsmod
```
Reboot to regain your wired connection.

---

### Post by Synoc on 2009-12-27
right off the bat, I get:
ERROR: Module ndiswrapper does not exist in /proc/modules
after the first line. do I continue anyway?

BTW if this whole thing works I owe you a cheese burger

---

### Post by dmizer on 2009-12-28
> **Synoc said:**
> right off the bat, I get:
ERROR: Module ndiswrapper does not exist in /proc/modules
after the first line. do I continue anyway?

BTW if this whole thing works I owe you a cheese burger

Yes, continue anyway. Post any other results. :)

---

### Post by margazhang on 2009-12-29
I would install wicd via Synaptic first and then reboot - in just two minutes you will know if it works for you. The wicd will remove NM so make sure you have wired connection before doing it. 

According to my experience, wicd always worked when I had problem with NM. 

Maybe when wicd is installed, the installation process detects and installs the right drivers? Do not know why but it worked every time when NM failed.

---

### Post by dmizer on 2009-12-29
> **margazhang said:**
> I would install wicd via Synaptic first and then reboot - in just two minutes you will know if it works for you. The wicd will remove NM so make sure you have wired connection before doing it. 

According to my experience, wicd always worked when I had problem with NM. 

Maybe when wicd is installed, the installation process detects and installs the right drivers? Do not know why but it worked every time when NM failed.

This is not a problem with Network-Manager, this is a driver problem. In this case, changing to WICD would make zero difference.

---

### Post by Synoc on 2009-12-29
ok here we go...

first errors etc.
> 
****@***-laptop:~$ sudo rmmod ndiswrapper
[sudo] password for ***: 
ERROR: Module ndiswrapper does not exist in /proc/modules
****@***-laptop:~$ sudo rmmod b43legacy
ERROR: Module b43legacy does not exist in /proc/modules
****@***-laptop:~$ sudo rmmod b44
****@***-laptop:~$ sudo rmmod ssb
****@***-laptop:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release. 
lshw -C network:
> 
*-network:0 UNCLAIMED   
       description: Ethernet controller
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=32
       resources: memory:fcffe000-fcffffff memory:24000000-24003fff(prefetchable)
  *-network:1
       description: Wireless interface
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wlan0
       version: 03
       serial: 00:90:96:b6:47:6b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+Broadcom,03/23/2006, 4.40.1 ip=192.168.0.7 latency=32 multicast=yes wireless=IEEE 802.11g
       resources: irq:11 memory:fcffc000-fcffdfff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

lsmod
> 
module                  Size  Used by
ndiswrapper           185404  0 
binfmt_misc             8356  1 
ppdev                   6688  0 
vboxnetflt             84840  0 
vboxnetadp             78344  0 
vboxdrv               121160  1 vboxnetflt
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
pcmcia                 36808  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           24200  1 
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rsrc_nonstatic         11644  1 yenta_socket
soundcore               7264  1 snd
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
joydev                 10272  0 
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
iptable_filter          3100  0 
shpchp                 32272  0 
ip_tables              11692  1 iptable_filter
lp                      8964  0 
x_tables               16544  1 ip_tables
psmouse                56500  0 
dell_wmi                2564  0 
dcdbas                  7292  0 
serio_raw               5280  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
mii                     5212  0 
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

for what it's worth, I did not have to reboot. my wireless kicked on as soon as my ethernet dropped... before that it would not even register that I HAD a wireless...

---

### Post by dmizer on 2009-12-29
> **Synoc said:**
> 
for what it's worth, I did not have to reboot. my wireless kicked on as soon as my ethernet dropped... before that it would not even register that I HAD a wireless...

Well that looks more promising. Were you able to get connected?

---

### Post by Synoc on 2009-12-29
> **dmizer said:**
> Well that looks more promising. Were you able to get connected?
I'm connected right now, I haven't rebooted yet I'm basking in the warm glow of EM radiation waves as course through me, it's glorious. should I still reboot or is there something else I should try first
indicently, I am less than 30 feet from my wireless router and I'm not even getting full isgnal strength.

---

### Post by dmizer on 2009-12-29
Well, it looks like you may not be able to use both wireless and wired at the same time. This was also a problem a while back when the ssb driver was interfering with ndiswrapper. There are bug reports on it if you care to look, you may find some alternative solutions.

For now, edit /etc/rc.local again and make it look like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

rmmod ndiswrapper
rmmod b43legacy
rmmod b44
rmmod ssb
modprobe ndiswrapper
exit 0
```

Then see if your wireless works on reboot.

If you need to use your wired connection, just run the following commands:
```
sudo modprobe ssb
sudo modprobe b44
```

---

### Post by Synoc on 2009-12-29
> **dmizer said:**
> Well, it looks like you may not be able to use both wireless and wired at the same time. This was also a problem a while back when the ssb driver was interfering with ndiswrapper. There are bug reports on it if you care to look, you may find some alternative solutions.

For now, edit /etc/rc.local again and make it look like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

rmmod ndiswrapper
rmmod b43legacy
rmmod b44
rmmod ssb
modprobe ndiswrapper
exit 0
```Then see if your wireless works on reboot.

If you need to use your wired connection, just run the following commands:
```
sudo modprobe ssb
sudo modprobe b44
```

ok upon rebooting, I lost wireless and regained my wired.
> 
*-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:1a:aa:93
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.8 latency=32 multicast=yes
       resources: irq:7 memory:fcffe000-fcffffff memory:24000000-24003fff(prefetchable)
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:11 memory:fcffc000-fcffdfff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


> 
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
vboxnetflt             84840  0 
vboxnetadp             78344  0 
vboxdrv               121160  1 vboxnetflt
joydev                 10272  0 
pcmcia                 36808  0 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
iptable_filter          3100  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi                2564  0 
dcdbas                  7292  0 
psmouse                56500  0 
serio_raw               5280  0 
yenta_socket           24200  1 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
shpchp                 32272  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
b44                    28684  0 
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
ssb                    35300  1 b44
mii                     5212  1 b44
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video


---

### Post by dmizer on 2009-12-29
Try this:
```
sudo /etc/rc.local
```

See if your wireless becomes available then.

---

### Post by Synoc on 2009-12-29
> **dmizer said:**
> Try this:
```
sudo /etc/rc.local
```See if your wireless becomes available then.
ERROR: Module ndiswrapper does not exist in /proc/modules

---

### Post by dmizer on 2009-12-29
> **Synoc said:**
> ERROR: Module ndiswrapper does not exist in /proc/modules

Yes, but does your wireless work now?

---

### Post by Synoc on 2009-12-29
nope

---

### Post by dmizer on 2009-12-29
Okay ... try this for your /etc/rc.local file:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

rmmod b43legacy
rmmod b44
rmmod ssb
modprobe ndiswrapper
exit 0
```

If unsuccessful, try running it manually as I suggested in post 29.

If still unsuccessful, try the command sequence I gave in post 19

---

### Post by Synoc on 2010-01-11
sorry for the late late late LATE reply, life is hectic getting ready for college again.
> **dmizer said:**
> Okay ... try this for your /etc/rc.local file:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

rmmod b43legacy
rmmod b44
rmmod ssb
modprobe ndiswrapper
exit 0
```If unsuccessful, try running it manually as I suggested in post 29.

If still unsuccessful, try the command sequence I gave in post 19

> 
***@****-laptop:~$ sudo rmmod b43legacy
[sudo] password for ***: 
ERROR: Module b43legacy does not exist in /proc/modules
***@****-laptop:~$ sudo rmmod b44
***@****-laptop:~$ sudo rmmod ssb
***@****-laptop:~$ sudo rmmod ndiswrapper
***@****-laptop:~$ sudo /etc/rc.local
ERROR: Module b43legacy does not exist in /proc/modules
***@****-laptop:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
***@****-laptop:~$ sudo rmmod b43legacy
ERROR: Module b43legacy does not exist in /proc/modules
***@****-laptop:~$ sudo rmmod b44
ERROR: Module b44 does not exist in /proc/modules
***@****-laptop:~$ sudo rmmod ssb
ERROR: Module ssb does not exist in /proc/modules
***@****-laptop:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
sorry it's only half an answer but it seems to be the best way to explain it.

---

### Post by Synoc on 2010-01-13
ok I couldn't help but think something was seriously screwed up, so I admit... I completely reisntalled Ubuntu. let's start from scratch

---

