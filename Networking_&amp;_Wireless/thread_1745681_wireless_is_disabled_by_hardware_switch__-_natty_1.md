---
title: "wireless is disabled by hardware switch  - natty 11.04"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by Melotten on 2011-05-01
HI all, 
I'm running natty 11.04 and wireless was working properly till yesterday night. now is not possible to see any network.

I'm on a dell inspiron 1545 and the Broadcom STA drivers are already installed.

tried already a rfkill unblock all, but the results still this:

```

0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no


```

but the result of this command is changing all the time, few minutes before I got this one:

```

0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes


```

any idea how to solve this? tried to reboot couple of time without results.

the weird thing is that yesterday night and from the very beginning never had an issue with the connection.

Any idea? I think there are lot of people out there with the same issue isn't?

---

### Post by Bucic on 2011-05-01
This is the result of the outrageous f45up of wireless net drivers in 11.04 **and I'm also looking for a permanent solution** to this issue.

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677)

So much for the great "let's eliminate paper cut bugs" talk... :mad:

---

### Post by northd_tech on 2011-05-01
I know that some "software" wireless interfaces apparently need Windows 7 (or possibly Vista) in order to "enable" the hardware switch.  If you still have a Windows partition (dual-boot), that might be worth a try.

Also, it would be good to specify which Broadcom wireless interface (and configuration) you have by running the following terminal commands:

```
lspci -vvnn | grep 14e4

sudo lshw -C network

lsmod

ifconfig

iwconfig

```

That said, Ubuntu 11.xx seems to have many recent "issues" with wireless and wireless firmware (I'm still using Ubuntu 10.04.2 LTS and the Broadcom STA driver and it works quite well "out of the box").  :/

---

### Post by Bucic on 2011-05-01
Unfortunatelly (or not :) ) it's a single system machine. Here's the terminal return of all the commands you listed:

```

...@nx6125:~$ lspci -vvnn | grep 14e4
02:01.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet [14e4:169c] (rev 03)
02:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
...@nx6125:~$ sudo lshw -c network
[sudo] password for hg1: 
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0f:b0:74:9e:36
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=5788-v3.26 latency=64 link=no mingnt=64 multicast=yes port=twisted pair
       resources: irq:23 memory:d0000000-d000ffff
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: memory:d0010000-d0011fff



...@nx6125:~$ lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
snd_atiixp             20072  2 
snd_atiixp_modem       19128  5 
snd_ac97_codec        134270  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96625  5 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi           13324  0 
radeon                982197  2 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
tifm_7xx1              13042  0 
joydev                 17606  0 
snd_timer              29602  2 snd_pcm,snd_seq
pcmcia                 49166  0 
tifm_core              15654  1 tifm_7xx1
ttm                    76664  1 radeon
drm_kms_helper         42136  1 radeon
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   227495  4 radeon,ttm,drm_kms_helper
ppdev                  17113  0 
parport_pc             36959  1 
i2c_algo_bit           13400  1 radeon
yenta_socket           27846  0 
pcmcia_rsrc            18372  1 yenta_socket
pcmcia_core            22569  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    67382  20 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  3 snd_atiixp,snd_atiixp_modem,snd_pcm
psmouse                73535  0 
lp                     17825  0 
video                  19438  0 
parport                46458  3 ppdev,parport_pc,lp
edac_core              53845  0 
hp_wmi                 13706  0 
serio_raw              13166  0 
sparse_keymap          13898  1 hp_wmi
i2c_piix4              13303  0 
shpchp                 37297  0 
k8temp                 13016  0 
edac_mce_amd           23464  0 
usbhid                 46956  0 
hid                    91020  1 usbhid
sdhci_pci              13989  0 
firewire_ohci          40370  0 
pata_atiixp            13165  3 
sdhci                  27387  1 sdhci_pci
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
tg3                   141750  0 



...@nx6125:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:74:9e:36  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

...@nx6125:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by chili555 on 2011-05-01
With due respect to my colleagues, I think it's due to a poor implemetation of the module *dell-laptop*. Please do:```
lsmod | grep dell
```If *dell-laptop* is loaded, remove it:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
```Is your wireless working now? If so, we'll need to blacklist *dell-laptop*.

---

### Post by northd_tech on 2011-05-01
Hi Bucic,

**Yours** is a Broadcom 4318 AirForce One wireless, and post #27 on the following thread seems to have recently worked for those:

[http://ubuntuforums.org/showthread.php?t=1737629&highlight=broadcom+4318&page=3](http://ubuntuforums.org/showthread.php?t=1737629&highlight=broadcom+4318&page=3)

This is also a very informative thread about Broadcom 4318's and firmware:

[B]Under what name do the non-proprietary BCM4318 drivers show up in lsmod? 
[http://ubuntuforums.org/showthread.php?t=1739872&highlight=broadcom+4318](http://ubuntuforums.org/showthread.php?t=1739872&highlight=broadcom+4318)
[/B]

---

### Post by seastar on 2011-05-01
i have been having the same problem with wireless, and so have followed this discussion.  I can confirm that the last proposal (removing dell_laptop) *did* fix the issue.

---

### Post by northd_tech on 2011-05-01
> **Bucic said:**
> 
...@nx6125:~$ lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
snd_atiixp             20072  2 
snd_atiixp_modem       19128  5 
snd_ac97_codec        134270  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96625  5 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi           13324  0 
radeon                982197  2 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
tifm_7xx1              13042  0 
joydev                 17606  0 
snd_timer              29602  2 snd_pcm,snd_seq
pcmcia                 49166  0 
tifm_core              15654  1 tifm_7xx1
ttm                    76664  1 radeon
drm_kms_helper         42136  1 radeon
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   227495  4 radeon,ttm,drm_kms_helper
ppdev                  17113  0 
parport_pc             36959  1 
i2c_algo_bit           13400  1 radeon
yenta_socket           27846  0 
pcmcia_rsrc            18372  1 yenta_socket
pcmcia_core            22569  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    67382  20 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  3 snd_atiixp,snd_atiixp_modem,snd_pcm
psmouse                73535  0 
lp                     17825  0 
video                  19438  0 
parport                46458  3 ppdev,parport_pc,lp
edac_core              53845  0 
hp_wmi                 13706  0 
serio_raw              13166  0 
sparse_keymap          13898  1 hp_wmi
i2c_piix4              13303  0 
shpchp                 37297  0 
k8temp                 13016  0 
edac_mce_amd           23464  0 
usbhid                 46956  0 
hid                    91020  1 usbhid
sdhci_pci              13989  0 
firewire_ohci          40370  0 
pata_atiixp            13165  3 
sdhci                  27387  1 sdhci_pci
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
tg3                   141750  0 


Looking at Bucic's **lsmod** output, I don't see ANY Broadcom modules loaded.  (Also, I don't see any Dell modules loaded there, and it might actually be a HP based on the module "hp_wmi" that I see loaded above- and it appears keymap-related.)

The Broadcom 4318 should have "b43" "b44" and/or "ssb" modules from what I recall- see the thread that I linked above (but I don't see **any** of those modules loaded from what Bucic posted).  Their absence makes me think that Bucic should probably follow that Broadcom 4318 thread through step-by-step from the beginning.

FYI- my working Broadcom STA wireless (Broadcom "4321AG" under Vista 64bit and "4328" under Ubuntu 10.04.2 LTS) has these modules loaded:

> **wl   **                1964968  0 
lib80211                6151  2 lib80211_crypt_tkip,wl
lib80211_crypt_tkip     8676  0 > lspci -vvnn | grep 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)


---

### Post by Bucic on 2011-05-01
> **chili555 said:**
> With due respect to my colleagues, I think it's due to a poor implemetation of the module *dell-laptop*. Please do:```
lsmod | grep dell
```If *dell-laptop* is loaded, remove it:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
```Is your wireless working now? If so, we'll need to blacklist *dell-laptop*.
Here's what I got
```
hg1@nx6125:~$ lsmod | grep dell
hg1@nx6125:~$ sudo rmmod -f dell-laptop
[sudo] password for hg1: 
ERROR: Removing 'dell_laptop': No such file or directory
hg1@nx6125:~$ sudo rfkill unblock all
hg1@nx6125:~$ 

```
The LED indicator is up but wireless is still not listed in the networking applet, not even after disconnecting the LAN cable and disabling/enabling networking.

---

### Post by chili555 on 2011-05-01
I was addressing the OP, Melotten who has:> 0: brcmwl-0: Wireless LAN
	Soft blocked: no
	[COLOR="Red"]Hard blocked: yes[/COLOR]
1: [COLOR="Red"]dell-wifi[/COLOR]: Wireless LAN
	Soft blocked: no
	Hard blocked: noSorry if I was misunderstood.

---

### Post by Bucic on 2011-05-01
can anyone assist me in troubleshooting the issue? I've already tried posts #23 and #27 from [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677) and the few commands mentioned above which gave me the LED going live.

EDIT:
What's worrying is that it seems I don't have b43 firmware installed
```
...@nx6125:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  b43-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 15.5 kB of archives.
After this operation, 81.9 kB of additional disk space will be used.
Get:1 http://pl.archive.ubuntu.com/ubuntu/ natty/main b43-fwcutter amd64 1:013-3 [15.5 kB]
Fetched 15.5 kB in 0s (173 kB/s)  
Selecting previously deselected package b43-fwcutter.
(Reading database ... 153607 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a013-3_amd64.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:013-3) ...



...@nx6125:~$ dmesg | grep b43
[ 1462.414214] b43-pci-bridge 0000:02:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 1462.585900] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[ 1462.775353] Registered led device: b43-phy0::radio
[ 1462.892103] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[ 1462.892108] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 1462.892112] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```

---

### Post by northd_tech on 2011-05-01
> **Bucic said:**
> can anyone assist me in troubleshooting the issue? I've already tried posts #23 and #27 from [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677) and the few commands mentioned above which gave me the LED going live.
That bug above applies to the Broadcom 4311, Bucic.  Your Broadcom 4318 is kind of "different" from most of the other Broadcom wireless chipsets from what I've seen.  I'm fairly certain that the "STA" fixes for the Broadcom 4311, 4312, 4321, and 4322 (as well as my "4321AG"/"4328" Broadcom) WILL NOT work for a Broadcom 4318.  I think you need the "b43 firmware" fix for that 4318 (it should be linked at post #6 above).

It is probably better to bump that first thread for the Broadcom 4318 that I linked to at post #6 (and probably to work through the thread from the beginning).  I did not see **any** of the Broadcom modules loaded in what you posted above, Bucic.

---

### Post by rl78 on 2011-05-01
Try specifying the identifier: rfkill unblock 0.

---

### Post by mezzovento on 2011-05-01
> **chili555 said:**
> With due respect to my colleagues, I think it's due to a poor implemetation of the module *dell-laptop*. Please do:```
lsmod | grep dell
```If *dell-laptop* is loaded, remove it:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
```Is your wireless working now? If so, we'll need to blacklist *dell-laptop*.

This work for me! Thanks chili555.  I have a DELL vostro 1720, ubuntu 11.04 64 bit. Before chili555 suggestion:

```
$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
8: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```switching the hardware button on/off affect only the 3: phy0 block, but the dell-wifi remain the same.

---

### Post by Melotten on 2011-05-01
All this is weird folks.

I spent almost 30 minutes playing with the rfkill command, having different results all the time. after that, after using the option unblock.. magically the wireless came back.

I'm so surprised, there are so many dell laptop around.. I think we will lose a lot of newbies with this issue.

I see the issue seems very common and I would like to help, could you please indicate me the "escalation" of troubleshooting steps to follow?

I will modify my first post so the people will find immediatley a solution.

I would put as first the rfkill command, is easy and seems working quite quickly. what you think?

---

### Post by Bucic on 2011-05-02
> **northd_tech said:**
> That bug above applies to the Broadcom 4311, Bucic.  Your Broadcom 4318 is kind of "different" from most of the other Broadcom wireless chipsets from what I've seen.  I'm fairly certain that the "STA" fixes for the Broadcom 4311, 4312, 4321, and 4322 (as well as my "4321AG"/"4328" Broadcom) WILL NOT work for a Broadcom 4318.  I think you need the "b43 firmware" fix for that 4318 (it should be linked at post #6 above).

It is probably better to bump that first thread for the Broadcom 4318 that I linked to at post #6 (and probably to work through the thread from the beginning).  I did not see **any** of the Broadcom modules loaded in what you posted above, Bucic.
Thanks for the guidance. I've started a new topic here if anyone could help me out [http://ubuntuforums.org/showthread.php?p=10757762](http://ubuntuforums.org/showthread.php?p=10757762)

---

### Post by MKdx on 2011-05-03
I can confirm that wireless settings in Windows influence hard blocked key in [brcmwl]:

```
brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

I have lenovo laptop, had problem with acer_wmi but worked around that by 'blacklisting' it. However, [brcmwl] issue seems to only get 'fixed by setting software switch in Windows to ON.

I will investigate it further when I have time, hope this might be of help.

---

### Post by libiamo on 2011-05-06
I have the same laptop and had the same problem;

Please try to press F2 (or maybe Fn+F2) on your keyboard, wait a few seconds. 

This fixed the problem for me.

---

### Post by garfieldpbj on 2011-05-07
Hi

I just want to report that a solution, when using the Lenovo s10-3s (probably the same trick for s10-3 or any other Lenovo) might be to boot into windows, and use the "hardware switch", which is actually the Fn+F5 combination, turn wifi on, and reboot..

I posted this here because I was very frustrated not been able to solve my problem and read a lot of forum posts without help, therefore I posted one solution here even though it might be a bit off topic..

/Peter

---

### Post by kalkems on 2011-05-10
I have a Acer Travelmate 6292 and have had my wireless hardblocked. Solved this with the following:

sudo service network-manager stop

sudo rmmod acer_wmi

sudo modprobe acer_wmi

sudo rfkill unblock all

(Checked that everything was unblocked)

sudo service network-manager start

Wireless started without problems.:)

/ernie

---

### Post by apwiggins on 2011-05-10
With My Inspiron 1501, I'm also seeing this bug where the wireless is hardblocked.  To complicate matters, I'm having a problem in that the keycode for the wireless button [Fn-F2] isn't mapped.
```
May 10 17:14:51 ubuntu-dell kernel: [  191.862248] kbd_keycode: 15 callbacks suppressed
May 10 17:14:51 ubuntu-dell kernel: [  191.862257] keyboard: can't emulate rawmode for keycode 240
May 10 17:14:51 ubuntu-dell kernel: [  191.862296] keyboard: can't emulate rawmode for keycode 240
```

Any suggestions?

> **chili555 said:**
> With due respect to my colleagues, I think it's due to a poor implemetation of the module *dell-laptop*. Please do:```
lsmod | grep dell
```If *dell-laptop* is loaded, remove it:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
```Is your wireless working now? If so, we'll need to blacklist *dell-laptop*.

---

### Post by chili555 on 2011-05-10
> **apwiggins said:**
> With My Inspiron 1501, I'm also seeing this bug where the wireless is hardblocked.  To complicate matters, I'm having a problem in that the keycode for the wireless button [Fn-F2] isn't mapped.
```
May 10 17:14:51 ubuntu-dell kernel: [  191.862248] kbd_keycode: 15 callbacks suppressed
May 10 17:14:51 ubuntu-dell kernel: [  191.862257] keyboard: can't emulate rawmode for keycode 240
May 10 17:14:51 ubuntu-dell kernel: [  191.862296] keyboard: can't emulate rawmode for keycode 240
```

Any suggestions?Did anything improve after you removed dell-laptop?

---

### Post by apwiggins on 2011-05-10
Thanks for the pointer, but no, I have already removed it.  No joy.  

This is a real backward step from 10.10 and many previous versions on this Dell hardware.  I recall having these kinds of keycode problems three or four years ago (7.04 or 7.10 IIRC) with an Acer laptop, but not with this hardware.

> **chili555 said:**
> Did anything improve after you removed dell-laptop?

---

### Post by nm_geo on 2011-05-10
[COLOR=Red]sudo rmmod -f dell-laptop


[/COLOR]Question: Not to sure but is it removed?  Looks like the command should be.

```
sudo rmmod -f dell_laptop
```

Well I thought it might not work BUT I was WRONG.... Checked it and [COLOR=Red]sudo rmmod -f dell-laptop
worked just fine... 
[/COLOR]

---

### Post by chili555 on 2011-05-10
> Well I thought it might not work BUT I was WRONG.... Checked it and sudo rmmod -f dell-laptop
worked just fine... Meaning the wireless works just fine without dell-laptop? If so, we can blacklist it.

---

### Post by nm_geo on 2011-05-10
> **chili555 said:**
> Meaning the wireless works just fine without dell-laptop? If so, we can blacklist it.

That seems logical to me... However I just removed the module and then restarted it here..  It has no adverse effect on my laptop but I am not having the OP's issue. I was just curious as to what it might do.. :)

Let me rmmod it again and reboot .. Dang I like testing LOL

---

### Post by chili555 on 2011-05-10
> However I just removed the module and then restarted it here.If you reboot, the rmmod disappears. I think you need to do:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
```Do NOT reboot. Is your wireless working?

---

### Post by nm_geo on 2011-05-10
> **chili555 said:**
> If you reboot, the rmmod disappears. I think you need to do:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
```Do NOT reboot. Is your wireless working?
 
chili555 I was just testing my laptop to see if it would reboot after blacklisting the dell_laptop module. And yes it did without any rfkill commands.  

lsmod | grep dell

```
bigdad@bigdad-Latitude-D620:~$ lsmod | grep dell
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi
```

---

### Post by L33T17 on 2011-05-11
> **chili555 said:**
> If you reboot, the rmmod disappears. I think you need to do:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
```Do NOT reboot. Is your wireless working?

Wow thanks man! This fixed it for me!

---

### Post by chili555 on 2011-05-11
> **L33T17 said:**
> Wow thanks man! This fixed it for me!If you want to make it permanent, do:```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```

---

### Post by converge2ashish on 2011-05-16
It is not working for me. Mine is Dell XPS M1530. Any suggestions please.

Thanks,

---

### Post by chili555 on 2011-05-17
> **converge2ashish said:**
> It is not working for me. Mine is Dell XPS M1530. Any suggestions please.

Thanks,Please run and post:```
rfkill list all
lsmod | grep dell
```Thanks.

---

### Post by DarrenMayLin on 2011-05-17
My Inspiron 1501 has been working on Ubuntu 10.10 after some work within Ubuntu to initially get the wireless going.  After upgrading to 11.04 at the end of last month the [Fn-F2] wouldn't work to enable wireless networking.  I googled around and came across some articles to do with my Broadcom card but none seemed to work.  It seems that in the last few weeks others have started having the exact same problem.

lsmod | grep dell 

revealed:

dell_wmi              12681  0
sparse_keymap    13898  1 dell_wmi
dell_laptop           13827  0
dcdbas                 14438  1 dell_laptop

tried:

sudo rmmod -f dell-laptop
sudo rfkill unblock all

Without rebooting, [Fn-F2] still is not lighting up the wifi led.

I think when I was following some of the suggestions regarding my Broadcom card at the end of last month I may have deleted something that is now required.

If anyone has any further suggetions they would be valued.

Chilli555, thanks for the help you've been on here and elsewhere.  I notice you've been helping out for quite a while.

---

### Post by chili555 on 2011-05-17
> tried:

sudo rmmod -f dell-laptop
sudo rfkill unblock all

Without rebooting, [Fn-F2] still is not lighting up the wifi led.Putting the state of the LED aside for now, do those steps actually enable your wireless?

Thank you for your kind comments.

---

### Post by DarrenMayLin on 2011-05-17
> **chili555 said:**
> Putting the state of the LED aside for now, do those steps actually enable your wireless?
 
Rebooted and tried [Fn-F2] but the wifi LED is still not lit up.  The cone shaped icon in the top right hand corner of the screen is empty.  Clicking it reveals that the "Wired Network", "device not managed", "Wireless Networks" and "device not ready (firmware missing)" options are not available.  All other options are available to be selected but "Enable Networking" and "Enable Wireless" options have an additional tick to their left.

I think this still indicates that wireless is unavailable, though there are two wireless networks visible to other computer nearby.

Thanks again!

---

### Post by converge2ashish on 2011-05-17
> **chili555 said:**
> Please run and post:```
rfkill list all
lsmod | grep dell
```Thanks.


Hi Chili555,

I pasted the code and output below for your kind reference.

~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

~$ lsmod | grep dell
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi
dell_laptop            13515  0 
dcdbas                 14054  1 dell_laptop

~$ sudo rmmod -f dell-laptop
[sudo] password for : 

~$ sudo rfkill unblock all

~$ rfkill list all
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

~$ lsmod | grep dell
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi

After this I tried pressing the Key combination Fn+F2. 
Still Wifi is not working (Ref - attached snap shot). Wifi LED is also not glowing.  

Thanks for your time,
Ashish

---

### Post by chili555 on 2011-05-17
@Darren--

I am starting to think your problem is not the wireless switch, but that the drivers and/or firmware are not correctly installed. Please post:```
lspci -nn
iwconfig
```

---

### Post by chili555 on 2011-05-17
> 2: phy0: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR]That suggests a switch or slider is in the Off position. Please check.

---

### Post by DarrenMayLin on 2011-05-17
> **chili555 said:**
>  ... Please post:```
lspci -nn
iwconfig
```
  
~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 13)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
08:01.0 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
08:01.1 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01)
~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.


@Chilli555 - Thanks for your continued analysis.

---

### Post by chili555 on 2011-05-17
> Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)This works with the module *wl*. Now let's see:```
lsmod | grep wl
dmesg | grep wl
```Thanks.

---

### Post by converge2ashish on 2011-05-17
> **chili555 said:**
> That suggests a switch or slider is in the Off position. Please check.

Hey chili555, you are wonderful. :-) Wireless switch was indeed in off position. I slided it and it is working again. 

Thanks a lot,
Ashish

P.S. I was not aware of the position of WiFi hardware switch. I am attaching the right hand side snap shot of the XPS1530 which I took from Dell site 
[http://support.dell.com/support/edocs/systems/xpsm1530/en/OM/about.htm#wp1212382](http://support.dell.com/support/edocs/systems/xpsm1530/en/OM/about.htm#wp1212382)

---

### Post by DarrenMayLin on 2011-05-18
> **chili555 said:**
> ... Now let's see:```
lsmod | grep wl
dmesg | grep wl
```

The above code didn't have any visible output.  This was the entry in byobu:

Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-8-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

~$ lsmod | grep wl
~$ dmesg | grep wl
~$

@Chilli555 Thanks for the explanation of the module.

---

### Post by chili555 on 2011-05-18
> **DarrenMayLin said:**
> The above code didn't have any visible output.  This was the entry in byobu:

Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-8-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

~$ lsmod | grep wl
~$ dmesg | grep wl
~$

@Chilli555 Thanks for the explanation of the module.Please connect an ethernet cable and do:```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```Now is your wireless working?

---

### Post by jvm985 on 2011-05-20
> **chili555 said:**
> With due respect to my colleagues, I think it's due to a poor implemetation of the module *dell-laptop*. Please do:```
lsmod | grep dell
```If *dell-laptop* is loaded, remove it:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
```Is your wireless working now? If so, we'll need to blacklist *dell-laptop*.

This solution works for the Latitude D520. Thanks.

---

### Post by brianfactors on 2011-05-21
I have the same laptop as the original poster and had problems when I clean installed natty. (no problems in Lucid)

At first the Advanced Driver "wizard" (windoze lingo I know... what else could you call them?) wouldn't install the Broadcom driver, but I got over that with help from: [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

Then I had the same message: wireless disabled by a hardware switch. I can confirm [@chili555]("http://ubuntuforums.org/member.php?u=35909") method. Removing dell_laptop did seem to fix the problem (after reboot).

---

### Post by MKdx on 2011-05-22
> **MKdx said:**
> I can confirm that wireless settings in Windows influence hard blocked key in [brcmwl]:

```
brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

I have lenovo laptop, had problem with acer_wmi but worked around that by 'blacklisting' it. However, [brcmwl] issue seems to only get 'fixed by setting software switch in Windows to ON.

I got around to check this bit more last week, though the wireless state is affected by how it's set in Windows, Windows is not needed to set it back in Linux.

For some reason [brcmwl] state can't be altered unless [acer_wmi] is still loaded. So to get wireless to work at startup, a sequence similar to this is need:
```
rfkill unblock all
sudo rmmod acer_wmi
```
This will unblock all devices before removing [acer_wmi], to ensure [brcmwl] is not blocked. Wireless should start regardless of Windows availability/setting. This should work for most lenovo laptops/netbooks, possibly other brands with some variation.

---

### Post by pearlzilla on 2011-06-05
> **rl78 said:**
> Try specifying the identifier: rfkill unblock 0.

This worked for me.  Will I need to run it each time I boot, or is there a way to automate it at start-up?

---

### Post by chili555 on 2011-06-05
> **pearlzilla said:**
> This worked for me.  Will I need to run it each time I boot, or is there a way to automate it at start-up?If that is all you need to do, that is, you don't need to rmmod any laptop or wmi drivers, then do:```
sudo gedit /etc/rc.local
```Add one line above exit 0```
rfkill unblock 0
```Proofread carefully, save and close gedit.

---

### Post by thatstrangeguy on 2011-06-12
[SIZE=4]I did every thing i have done so far and this is what i get what next it killed the dell but the hard lock still it there on brcmwl


[/SIZE]```
tanoah@tanoah-Inspiron-1545:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
tanoah@tanoah-Inspiron-1545:~$ sudo rmmod -f dell-laptop
tanoah@tanoah-Inspiron-1545:~$ sudo rfkill unblock all
tanoah@tanoah-Inspiron-1545:~$ rfkill list
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
tanoah@tanoah-Inspiron-1545:~$ sudo rfkill unblock all
tanoah@tanoah-Inspiron-1545:~$ sudo ifconfig eth1 up
tanoah@tanoah-Inspiron-1545:~$ sudo rfkill unblock all
tanoah@tanoah-Inspiron-1545:~$ rfkill list
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
tanoah@tanoah-Inspiron-1545:~$
 
```

---

### Post by chili555 on 2011-06-12
> [COLOR="Red"]Hard blocked: yes[/COLOR]Are you quite sure the hardware switch or key combination is in the On position?

---

### Post by randolf_ambrose on 2011-06-14
> **L33T17 said:**
> Wow thanks man! This fixed it for me!

of all the tiresome efforts, this one just did the wonder..!:popcorn:

---

### Post by craq on 2011-07-02
excellent, that worked for me too:
sudo rmmod -f dell-laptop

rfkill was showing that I had a Hardware switch off, but the hardware switch (Fn+F2) wasn't working until I disabled dell-laptop.

Thanks Chili!

---

### Post by Rainbow_Rising on 2011-07-30
Hi guys,

Just installed 11.04 this afternoon on an old HP laptop, same issue, I will try that command you tried for Dell to see if it works on HP, otherwise, I will reinstall 10

---

### Post by bkratz on 2011-07-30
> **Rainbow_Rising said:**
> Hi guys,

Just installed 11.04 this afternoon on an old HP laptop, same issue, I will try that command you tried for Dell to see if it works on HP, otherwise, I will reinstall 10



You might save yourself some time and look ( and paste here)  at the output of 

rfkill list all

If no blocks are shown the problem is probably something else.

---

### Post by wvargas on 2011-08-02
Here is a simple solution that *did* work for me on HP with Broadcom

as root:

1. modprobe broadcom
2. rfkill block all
3. rfkill unblock all

my wireless connection is now working fine again

---

### Post by dmdip on 2011-08-03
I faced a similar problem of an abrupt wireless disconnection on a Dell XPS 15 which I bought a couple of days back and as suggested did :
rmmod -f dell-laptop
sudo rfkill unblock

This did not fix the problem, but a simple <fn>-F2 (the hardware switch for the laptop) brought back the wireless.

Since dell-laptop was not at fault in my case, I would like to add it back. However, I do not know how to do this and could not get any clear answer from googling the web. 

Would greatly appreciate if someone could shed some light on this. Though I have been an ubuntu user for 2-3 years, I am not at all familiar with the kernel and commands to manipulate it.

Thanks in anticipation.

---

### Post by bkratz on 2011-08-03
> **dmdip said:**
> I faced a similar problem of an abrupt wireless disconnection on a Dell XPS 15 which I bought a couple of days back and as suggested did :
rmmod -f dell-laptop
sudo rfkill unblock

This did not fix the problem, but a simple <fn>-F2 (the hardware switch for the laptop) brought back the wireless.

Since dell-laptop was not at fault in my case, I would like to add it back. However, I do not know how to do this and could not get any clear answer from googling the web. 

Would greatly appreciate if someone could shed some light on this. Though I have been an ubuntu user for 2-3 years, I am not at all familiar with the kernel and commands to manipulate it.

Thanks in anticipation.



If all you did was

rmmod -f dell-laptop
sudo rfkill unblock

and did not do the step of blacklisting the module, rebooting should add it back in with no additional effort required.

---

### Post by dmdip on 2011-08-03
It is indeed back - thanks very much!

---

### Post by dmdip on 2011-08-03
> **bkratz said:**
> If all you did was

rmmod -f dell-laptop
sudo rfkill unblock

and did not do the step of blacklisting the module, rebooting should add it back in with no additional effort required.


It is indeed back! Thanks very much!

---

### Post by mark5656 on 2011-08-05
edit: ok, its not soft or hard blocked, but it still wont show my router... its 2WIRE, but it cant find it for some reason....

---

### Post by montydhanjal on 2011-08-28
> **chili555 said:**
> With due respect to my colleagues, I think it's due to a poor implemetation of the module *dell-laptop*. Please do:```
lsmod | grep dell
```If *dell-laptop* is loaded, remove it:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
```Is your wireless working now? If so, we'll need to blacklist *dell-laptop*.

thank you very much. It worked for me :)

---

### Post by matheusrotta on 2011-08-31
[SIZE=2][FONT=Arial]I have 11.04 as well.
You see, every computer has a wireless switch, but some of them have it as a button, others have shortcuts on the keyboard. The shortcut for wireless connection can usually be seen on your computer manual. I have an Acer and its shortcut is FN+F3.
You should try finding it there. If the switch is not the problem then you should continue trying rfkill or other commands on the terminal. But I'm new to Ubuntu so I can't help you with that.[/FONT][/SIZE]

---

### Post by huiejr on 2011-08-31
This is what I had to do to get my dell studio 1537 working:
 

 plug network cable into wireless router to gain network access
 

 list hardware  
 l**spci -vnn | grep 14e4**
 

 I was able to tell that my hardware was supported by the b43-fwcutter package.  Learned this at the following site:
 

 [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
 

 Install b43-fwcutter package
 **sudo apt-get install b43-fwcutter ** 
 

 then I had to go to the SYSTEM SETTINGS > HARDWARE > ADDITIONAL DRIVERS
 and activate the driver.  REBOOT.   
 

 **rfkill list **
 

 0: dell-wifi: Wireless LAN 
     Soft blocked: no 
     Hard blocked: yes 
 1: brcmwl-0: Wireless LAN 
     Soft blocked: no 
     Hard blocked: no 
 

 **lsmod | grep dell **
 dell_wmi                    12681  0  
 sparse_keymap          13898  1 dell_wmi 
 dell_laptop                 13827  0  
 dcdbas                        14438  1 dell_laptop 
 

 **sudo rmmod -f dell_laptop **
 

 **sudo rfkill unblock all**
  
  **rfkill list **
 1: brcmwl-0: Wireless LAN 
     Soft blocked: no 
     Hard blocked: no 
 

 It works and thanks to the posters on this thread:P

And don't forget to blacklist dell-laptop as mentioned earlier thread.

---

### Post by Ubuntiac on 2011-09-22
This is driving me natty! er Batty!

Dell 1501 + Kubuntu natty + maverick version of bcmwl-kernel-source installed.

I've unblacklisted bcm43xx in blacklist.conf. Dell_laptop and dell-wmi are running at startup.

sudo rfkill list says both hardware and software locked on dell-wifi
if I do sudo rmmod dell_laptop I get a notification "Wireless activated" and rfkill list returns nothing. Unfortunately although I am able to tick wireless, no wireless networks show up and the wifi light doesn't turn on, even if I fn+f2.

With the current version of bcm-kernel-source sudo rfkill list returns nothing. Killing dell_laptop still shows the same activation message, but there is no checkbox to turn on wirless.

Halp!

---

### Post by chili555 on 2011-09-22
> I've unblacklisted bcm43xx in blacklist.conf. That has nothing to do with anything. Please add to the blacklist.conf file:```
blacklist dell-laptop
```Reboot and let us see:```
rfkill list all
iwconfig
```Thanks.

---

### Post by Gordon D on 2011-09-22
None of the suggested solutions above worked for me. Eventually downgraded bcmwl-kernel-source to previous release as per bug below:-

Reply #36 in [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677) worked for me. 

Dell Latitude D420


lspci -nnk | grep -iA2 net
```
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
	Subsystem: Dell Device [1028:01d6]
	Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
	Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
	Kernel driver in use: wl

```

Hope this helps

---

### Post by By-Tor66 on 2011-09-26
> **chili555 said:**
> With due respect to my colleagues, I think it's due to a poor implemetation of the module *dell-laptop*. Please do:```
lsmod | grep dell
```If *dell-laptop* is loaded, remove it:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
```Is your wireless working now? If so, we'll need to blacklist *dell-laptop*.
 
Chili this brought my wifi light on, but still no connection.  I have a dell inspiron 700m with a broadcom 4306 wireless apadter.

---

### Post by chili555 on 2011-09-26
> **By-Tor66 said:**
> Chili this brought my wifi light on, but still no connection.  I have a dell inspiron 700m with a broadcom 4306 wireless apadter.This thread is a bit long in the tooth. Would you please start your own new thread? Post:```
lspci -nn | grep 0280
dmesg | grep b43
```Leave a link here and I'll be right there.

---

### Post by lee_can on 2011-10-12
HI all, 
I'm running natty 11.04 on lenovo G560 but unfortunately wireless is not working properly as the wireless is disable by hardware switch.
I have tried all the posts mentioned here, but i didn't know how to fix this issue.
Can anyone help please?

for your information, please find below in case helps to identify my problem.
```
e33@e33-G560:~$ uname -a
Linux e33-G560 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
e33@e33-G560:~$ 
``````

e33@e33-G560:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Pe33@e33-G560:~$ modinfo ssb  | grep 4318
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
e33@e33-G560:~$ wer=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

``````

e33@e33-G560:~$ lspci -vvnn | grep 14e4
e33@e33-G560:~$ 

``````
e33@e33-G560:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
e33@e33-G560:~$ dmesg | grep b43
e33@e33-G560:~$ 

``````
e33@e33-G560:~$ modinfo ssb  | grep 4318
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
e33@e33-G560:~$ 
e33@e33-G560:~$ modinfo wl  | grep 4318
e33@e33-G560:~$ 

``````
e33@e33-G560:~$ rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
e33@e33-G560:~$ 

``````
e33@e33-G560:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
05:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)
e33@e33-G560:~$ 
```Thanks in advance

---

### Post by Rolandmaffia on 2011-11-14
> **chili555 said:**
> With due respect to my colleagues, I think it's due to a poor implemetation of the module *dell-laptop*. Please do:```
lsmod | grep dell
```If *dell-laptop* is loaded, remove it:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
```Is your wireless working now? If so, we'll need to blacklist *dell-laptop*.

I had same issue with Dell Inspiron 1120. Somehow, with disabling, reenabling it came back OK. I won't use the hardware button anymore. Thanks!

---

### Post by themightyrumpus on 2012-01-27
> **chili555 said:**
> With due respect to my colleagues, I think it's due to a poor implemetation of the module *dell-laptop*. Please do:```
lsmod | grep dell
```If *dell-laptop* is loaded, remove it:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
```Is your wireless working now? If so, we'll need to blacklist *dell-laptop*.
Dell Inspiron 1545 n series, Broadcom chipset, I have had Ubuntu since 7, internal upgrade for each new distro upgrade.

This jumped up out of nowhere for me, 11.04 was working fine since I put it on ((with some minor cosmetic problems like ccsm totally dying on me)) but all of a sudden my "wireless disabled by hardware" bit me and my F2 key ((which used to shut off wireless and turn it back on just fine)) would not turn on the wireless.

This fix worked.

bummer, but glad to be back :popcorn:

---

### Post by chili555 on 2012-01-28
> This fix worked.

bummer, but glad to be backIf you are ready to make it permanent, blacklist dell-laptop:```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```

---

### Post by rawatmohinder on 2012-03-25
Hi Chili555,

Thanks a lot for your advice. it fixed by wireless issue. I was searching this problem resolution for 3-4 hours but then when i realize that my wireless driver could be correct, issue is wireless card is disabled. Thanks a lot again for your time to write this article.

Thanks
Mahi

---

### Post by rawatmohinder on 2012-03-25
Hi All,

Just to add, I have a Dell Vostro1520 and my wireless driver is b43 and wireless was not working with ubuntu 11.10. There were two issues. One issue which is discussed in the thread.

1.) Dell wireless card was disabled
2.) Secondly wireless driver was wrong.

How to fix wireless driver problem
-------------------------------------------
$ sudo apt-get update
$ sudo apt-get install firmware-b43-installer ( if it did not work, try below command)
$sudo apt-get install firmware-b43-lpphy-installer ( it depends on wirless card model, if this also does not work, it will give you a suggestion based on your hardware, run suggested command)
$ sudo apt-get remove bcmwl-kernel-source
$ sudo reboot

How to enable dell wireless card
-----------------------------------------
$ rfkill lits ( is it showing any card blocked: yes)

run below mentioned commands to fix
------------------------------------------------
 [FONT=Cumberland AMT,Cumberland,Courier New,Liberation Mono,Nimbus Mono L,DejaVu Sans Mono,Courier,Lucida Sans Typewriter,Lucida Typewriter,Monaco,Monospaced]sudo rmmod -f dell-laptop[/FONT]                               [FONT=Cumberland AMT,Cumberland,Courier New,Liberation Mono,Nimbus Mono L,DejaVu Sans Mono,Courier,Lucida Sans Typewriter,Lucida Typewriter,Monaco,Monospaced]
sudo rfkill unblock all[/FONT]       
         
Confirm, if your wireless is working now? if yes, then Thanks to Chili555 he only provided solution to enable Dell driver.
but first part was not there is this post and i spent 3-4 hours to resolve this problem but if you see this post, you can fix it fast and that is the reason i thought of writting it and giving back to community

Thanks
Mohinder

---

### Post by rscricket on 2012-12-03
I tried rfkill etc but it didn't really work for me.

Finally  the following works every time - I have wireless mouse and when I get 'wireless disabled' - I simply take out the mouse's usb connector. This causes wifi to re-trigger automatically and connect. 

It seems that usb devices may be interfering with wifi.

Hope this helps.

---

### Post by jonessoda219 on 2013-03-15
Does anyone know how to fix this with a lenovo ideapad s10-3? Im running an atheros 9285 adapter with all drivers needed. Please post steps to fix it.
Thank you.

---

### Post by regrock100 on 2013-06-21
Ok,
I did everything on this thread and probably on a few more threads and it does not work for me. I just downloaded Ubuntu 13 and after years of using Fedora, i thought this would be a good move for my family. Well, i'm stuck on day 1. I have a Dell Latitude D630. Please help me out. I don't want to repeat what i did because i went through everything and did everything. 

Thank you.

---

### Post by Hadaka on 2013-06-21
@regrock100...Hi, please post the output of...
```
lspci -nnk | grep -iA3 net
lsmod
sudo rfkill list all
```
thanks

---

### Post by regrock100 on 2013-06-22
reggie@reggie-Latitude-D630:~$ lspci -nnk | grep -iA3 net
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
    Subsystem: Dell Device [1028:01f9]
    Kernel driver in use: tg3
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
    Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
    Kernel driver in use: wl

reggie@reggie-Latitude-D630:~$ lsmod
Module                  Size  Used by
parport_pc             27504  0 
ppdev                  12817  0 
bnep                   17669  2 
rfcomm                 37420  0 
bluetooth             202069  10 bnep,rfcomm
snd_hda_codec_idt      63896  1 
wl                   4134820  1 
snd_hda_intel          38307  3 
snd_hda_codec         117580  2 snd_hda_codec_idt,snd_hda_intel
coretemp               13131  0 
joydev                 17097  0 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
i915                  535544  3 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
kvm                   376505  0 
snd_rawmidi            25114  1 snd_seq_midi
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
drm_kms_helper         47545  1 i915
drm                   228489  4 i915,drm_kms_helper
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
psmouse                81038  0 
i2c_algo_bit           13197  1 i915
snd_timer              24411  2 snd_pcm,snd_seq
dell_wmi               12601  0 
pcmcia                 39544  0 
gpio_ich               13236  0 
snd                    56485  15 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
sparse_keymap          13658  1 dell_wmi
yenta_socket           27095  0 
dcdbas                 14021  0 
serio_raw              13031  0 
lib80211               14040  1 wl
pcmcia_rsrc            18191  1 yenta_socket
mac_hid                13037  0 
soundcore              12600  1 snd
cfg80211              436177  1 wl
pcmcia_core            21505  3 pcmcia,pcmcia_rsrc,yenta_socket
microcode              18286  0 
wmi                    18590  1 dell_wmi
lpc_ich                16925  0 
video                  18894  1 i915
binfmt_misc            17260  1 
ext2                   63166  1 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
firewire_ohci          35292  0 
firewire_core          61718  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
tg3                   143666  0 
ptp                    18189  1 tg3
pps_core               13736  1 ptp

reggie@reggie-Latitude-D630:~$ sudo rfkill list all
[sudo] password for reggie:

---

### Post by chili555 on 2013-06-22
> Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)Please get a temporary ethernet connection and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet, reboot and let us hear your report.

---

### Post by regrock100 on 2013-06-22
That worked!!! Thank you very much. Is there anything else i need to do?

---

### Post by Hadaka on 2013-06-22
@regrock100...glad its working..and nope
nothing more to do. Ignore the proprietary dirver offer
for whatever reason..it offers the incorrect driver..you now
have the correct one.
Have Fun!!

---

