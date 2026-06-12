---
title: "Enable Wireless - unchecked and greyed out"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by Lisalives on 2010-03-06
Hi everyone,

I'm hoping you can help with a query.  I'm running Ubuntu Linux 9.10 and have been connected to my wireless modem/router (linksys) without any trouble.

Until today, when I foolishly decided to change my system password.  I was prompted for my network password which I thought I had correct, but apparently didn't.  Now, when I click on my icon for internet connections the 'enable wireless' button is unchecked, and greyed out, so I can't click it back on.

I logged into my modem/router and re-set the password, and that's all okay.

In the meantime I'm connected via the cable to the router.

I checked the settings and my network is disabled as per below.  I've unplugged and restarted the linksys, and also my laptop several times.

I know this set up works, I just need to find the 'switch' to turn the wireless networking back on.

Thanks for your help!
Lisa

lisa@lisa-laptop:~$ sudo lshw -C network
[sudo] password for lisa: 
  *-network DISABLED      
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:15:af:1e:a5:bf
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:dc7f0000-dc7fffff
lisa@lisa-laptop:~$ ^C
lisa@lisa-laptop:~$ ^C
lisa@lisa-laptop:~$

---

### Post by chili555 on 2010-03-06
> *-network [COLOR="Red"]DISABLED[/COLOR]
description: Wireless interface
product: AR5001 Wireless Network Adapter> I just need to find the 'switch' to turn the wireless networking back on.That's exactly what it looks like. Please post:```
rfkill list
```Thanks.

---

### Post by Lisalives on 2010-03-06
thanks for your help :P

is this what you are after?

lisa@lisa-laptop:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
lisa@lisa-laptop:~$

---

### Post by chili555 on 2010-03-06
Yes! This means there is a hardware switch or slider somewhere on your laptop that switches the wireless on and off. It is switched off.> lisa@lisa-laptop:~$ rfkill list
0: phy0: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR]Find it, switch it and be back in business.> I just need to find the 'switch' to turn the wireless networking back on.Totally.

---

### Post by zeiger on 2010-06-21
I have the exact same problem!

The command ```
rfkill list
``` gives the following for me: 
 
> 
Wireless Hardware Switch On 
0: dell-wifi: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
1: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
 
 
Wireless Hardware Switch Off 
0: dell-wifi: Wireless LAN 
    Soft blocked: yes 
    Hard blocked: yes 
1: phy0: Wireless LAN 
    Soft blocked: yes 
    Hard blocked: yes 
 
 
Wireless Hardware Switch On Again 
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: [COLOR=Red]yes[/COLOR]
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
 

Wireless Hardware Switch Off Again
0: dell-wifi: Wireless LAN 
    Soft blocked: yes 
    Hard blocked: yes 
1: phy0: Wireless LAN 
    Soft blocked: yes 
    Hard blocked: yes


and so on....

Any idea why this is happening? I have another Gateway Laptop where I have no problems at all connecting to wireless networks. So is this some driver problem or a bug?

Any quick fixes? 

I'm on Ubuntu 10.04 and my Wireless Card is:
Intel Wireless 6200 AGN

---

### Post by arqbrulo on 2010-07-04
I have a Dell Inspiron 1720 where, if I reboot my computer with the wifi switch turned ON, I cannot connect to any wifi networks, the "enable wireless" is unchecked and grayed out. However, if I make sure to have my switch in the OFF position when it's rebooting, once I log in, I turn ON my wifi and I am able to connect. It really sucks having to remember to turn off my wifi, or even worse, having to reboot my computer just because I forgot to turn it off. This happens to me with both Broadcom drivers. Here are some outputs:
```
lspci | grep Broadcom
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```
```
rfkill list
0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: dell-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
```
Any help is really appreciated.

EDIT: After reading a few more posts, I found that by running "sudo rmmod -f dell-laptop" I am able to turn on the wifi.

---

### Post by spawnywhippet on 2010-09-01
I have a similar problem, following a re-installation of 10.04. 
Wireless Network in Network Manager is greyed out and not enabled: 

lshw -C network

 *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wlan0
       version: 61
       serial: 00:1d:e0:67:7b:03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:d8000000-d8001fff


My WiFi switch (keyboard/LED switch) does not light up when I turn it on and off:

rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
andy@ubuntu-laptop:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

The wireless hardware is enabled at power on and not disabled in the BIOS.
It works perfectly when I boot Windows, and also worked perfectly with my previous Ubuntu 10.04 installation.

I have even reinstalled 10.04 while the wireless was toggled 'On' and it made no difference.

---

### Post by grahammechanical on 2010-09-01
When visiting my sister recently, I checked out her laptop (make not noticed). Her daughter had put a stickly label on the top of the screen saying "switch off wireless." I guess there was a reason for this. By the way, the OS is Vista. So, this problem of needing to switch off wireless in hardware before re-booting might not be a Ubuntu problem.

regards

---

### Post by chili555 on 2010-09-01
> My WiFi switch (keyboard/LED switch) does not light up when I turn it on and offWhat kind of laptop is it? Please tell us the brand and model.

---

### Post by spawnywhippet on 2010-09-01
> **chili555 said:**
> What kind of laptop is it? Please tell us the brand and model.

HP 6910p

---

### Post by chili555 on 2010-09-01
> **spawnywhippet said:**
> HP 6910pThere is a module that usually gets loaded called hp-wmi.> $ modinfo hp-wmi
filename:       /lib/modules/2.6.32-22-generic/kernel/drivers/platform/x86/hp-wmi.ko
alias:          wmi:5FB7F034-2C63-45e9-BE91-3D44E2C707E4
alias:          wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C
license:        GPL
description:    [COLOR="Red"]HP laptop WMI hotkeys driver[/COLOR]You can verify if it's loaded with:```
lsmod | grep wmi
```Perhaps it is not working correctly. Please try:```
sudo rmmod -f hp-wmi
```Now manipulate the wireless switch and run:```
rfkill list
```See if any switch presses coax the wireless to life. The LED may or may not be a reliable indicator.

---

### Post by chili555 on 2010-09-01
I also noticed this: [http://mandriva.598463.n5.nabble.com/Bug-59890-NEW-Intel-PRO-Wireless-3945ABG-doesn-t-work-in-Mandriva-2010-1-rc2-live-cd-td618377.html](http://mandriva.598463.n5.nabble.com/Bug-59890-NEW-Intel-PRO-Wireless-3945ABG-doesn-t-work-in-Mandriva-2010-1-rc2-live-cd-td618377.html)

Especially comment #6:```
The hardware killswitch and the software killswitch has ended up out of sync,
so when you disable the hw switch, the sw switch gets enabled, and when you
enable the hw switch, the sw switch gets disabled.

In both cases either the hw or the sw switch blocks the wireless from working.

There is a bug, either in the hardware, firmware or in the linux code that does
not protect theese from getting out of sync. I'll check upstream if something
like this is fixed...

The rfkill utility is helpful in getting them in sync again. you really only
need the "rfkill unblock all" to get it back in sync

```You might try booting with the wireless switch off and then turn it on and see if the wireless is working. You might also try:```
sudo rfkill unblock all
```

---

### Post by spawnywhippet on 2010-09-01
> **chili555 said:**
> There is a module that usually gets loaded called hp-wmi.You can verify if it's loaded with:```
lsmod | grep wmi
```

I have no clue what this means, but I guess its not good :
```
ubuntu-laptop:~$ lsmod | grep wmi
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71106  16 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
```

> **chili555 said:**
> 
Perhaps it is not working correctly. Please try:```
sudo rmmod -f hp-wmi
```
Seems not to be loaded, how do I install this?:
```
ubuntu-laptop:~$ sudo rmmod -f hp-wmi
[sudo] password for andy: 
ERROR: Removing 'hp_wmi': No such file or directory
```

> **chili555 said:**
> 
Now manipulate the wireless switch and run:```
rfkill list
```See if any switch presses coax the wireless to life. The LED may or may not be a reliable indicator.
I guess this will have no chance of working if the WMI isn't even loaded?

---

### Post by chili555 on 2010-09-01
I believe it's included in the kernel. Please try:```
sudo modprobe hp-wmi
```Post any errors or warnings.

---

### Post by spawnywhippet on 2010-09-01
> **chili555 said:**
> I believe it's included in the kernel. Please try:```
sudo modprobe hp-wmi
```Post any errors or warnings.

OK, 'sudo modprobe hp-wmi' didn't seem to do anything, so I added it to /etc/modules and rebooted.

```
ubuntu-laptop:~$ lsmod | grep wmi
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
hp_wmi                  5321  0 
snd                    71106  16 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
```

But now it gets weirder. Toggling the Wireless switch enables the bluetooth now, but doesn't seem to want to know the WiFi card.
```

andy@ubuntu-laptop:~$ rfkill unblock all
andy@ubuntu-laptop:~$ rfkill list
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hp-wwan: Wireless WAN
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

Still cannot enable Wireless, its all greyed out....
```

  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wlan0
       version: 61
       serial: 00:1d:e0:67:7b:03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:d8000000-d8001fff
```

---

### Post by ISIRC10 on 2010-09-06
I have been running Ubuntu 8.04 for a while on my Dell Vostro 1520 laptop, and recently switched to 10.04. However, the only way I can get a wireless connection is if I turn the computer on with the wifi switch in the off position, and then turning it on once I have logged in. Otherwise, my network manager has the option of enabling wireless networks greyed out and unchecked. Is there something I can do about this whole switching off thing, or do I just have to buckle down and remember to turn wifi off before I boot up?

---

### Post by arqbrulo on 2010-09-06
> **ISIRC10 said:**
> I have been running Ubuntu 8.04 for a while on my Dell Vostro 1520 laptop, and recently switched to 10.04. However, the only way I can get a wireless connection is if I turn the computer on with the wifi switch in the off position, and then turning it on once I have logged in. Otherwise, my network manager has the option of enabling wireless networks greyed out and unchecked. Is there something I can do about this whole switching off thing, or do I just have to buckle down and remember to turn wifi off before I boot up?

You can do as I did on my Dell Inspiron, in terminal run "sudo rmmod -f dell-laptop". That did it for me.

---

### Post by chili555 on 2010-09-06
If that works for you, then do:```
sudo su
echo dell-laptop >> /etc/modprobe.d/blacklist.conf
exit
```The module will then be blacklisted permanently.

---

### Post by spawnywhippet on 2010-09-07
I have now solved my WLAN card issue. I ended up physically removing the wireless card from the laptop, booting into Ubuntu, then shutting down and refitting the card.

I then booted into Ubuntu with the wireless switch in the 'On' position and Ubuntu immediately detected a wireless network. 

The WiFi toggle switch now correctly operates also.

---

### Post by chili555 on 2010-09-07
Glad it's working now.

---

### Post by iharacomix on 2010-09-07
First-timer asking for help. ^^'

I have a strange problem with the wireless too, where the Enable Wireless option is unchecked and grayed out. (Dell Inspiron n5010)

When I run 'rfkill list' and 'sudo lshw -C network' one way I get this:

--
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: **no**
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: **no**
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: **yes**
--
  *-network DISABLED      
       description: Wireless interface
       product: WiMAX/WiFi Link 6050 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       logical name: wlan0
       version: 57
       serial: 00:23:15:1d:3b:d0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.32-24-generic firmware=9.201.4.1 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:34 memory:fbc00000-fbc01fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 02
       serial: a4:ba:db:c8:66:be
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=75.191.248.135 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:33 ioport:e000(size=256) memory:d0b10000-d0b10fff(prefetchable) memory:d0b00000-d0b0ffff(prefetchable) memory:fb200000-fb21ffff(prefetchable)
--

However, when I press the wireless key and run the two again, it changes to *this*:

--
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: **yes**
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: **yes**
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: **no**
--
  *-network               
       description: Wireless interface
       product: WiMAX/WiFi Link 6050 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       logical name: wlan0
       version: 57
       serial: 00:23:15:1d:3b:d0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.32-24-generic firmware=9.201.4.1 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:34 memory:fbc00000-fbc01fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 02
       serial: a4:ba:db:c8:66:be
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=75.191.248.135 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:33 ioport:e000(size=256) memory:d0b10000-d0b10fff(prefetchable) memory:d0b00000-d0b0ffff(prefetchable) memory:fb200000-fb21ffff(prefetchable)
--

... and that goes back and forth.

Any advice?

---

### Post by chili555 on 2010-09-07
Please run:```
sudo rmmod -f dell-laptop
```Repeat the tests. If the wireless is working now, do:```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```Then the errant module will be permanently blacklisted.

---

### Post by iharacomix on 2010-09-07
I followed your instructions and it worked, my wireless is fine.
But can you, by any chance, tell me what '**sudo rmmod -f dell-laptop**' does, and why it needed to be handled as it did ('**echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf**')?

I'm trying to learn some stuff here at the same time, and hopefully, this will help me help others. ^^

---

### Post by hockeytux on 2010-09-07
Ive got the same problem on an Acer Aspire One but neither the 'rfkill unblock all' nor the 'sudo rmmod -f sn-netbook' have any effect.

Am I missing something here? Whats the correct name of the module for Acer Aspire Ones?

---

### Post by bkratz on 2010-09-07
> **iharacomix said:**
> I followed your instructions and it worked, my wireless is fine.
But can you, by any chance, tell me what '**sudo rmmod -f dell-laptop**' does, and why it needed to be handled as it did ('**echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf**')?

I'm trying to learn some stuff here at the same time, and hopefully, this will help me help others. ^^


The first command temporarily removed the dell-laptop module. It would have returned at the next boot. The second made it permanent by not allowing it to load at boot-time (blacklisted it).

From an earlier Dr Chili post (must be coffee-ing!)

```
February 24th, 2010, 09:41 AM
dell-laptop is supposed to enable some functions that are unique to Dell. As you can see, it doesn't work well. I suspect that it conflicts with another similar module, dell-wmi. If you notice that other functions now don't work correctly, obviously reverse the removal.
.
.
.

dell-laptop is now blacklisted and will not reload on boot, unless, of course, you edit /etc/modprobe.d/blacklist.conf to remove the blacklist line.
```

---

### Post by chili555 on 2010-09-07
> **hockeytux said:**
> Ive got the same problem on an Acer Aspire One but neither the 'rfkill unblock all' nor the 'sudo rmmod -f sn-netbook' have any effect.

Am I missing something here? Whats the correct name of the module for Acer Aspire Ones?Would you please start a new thread and PM me if I don't catch it right away?

---

### Post by chili555 on 2010-09-07
> The first command temporarily removed the dell-laptop module. It would have returned at the next boot. The second made it permanent by not allowing it to load at boot-time (blacklisted it).Exactly correct!> From an earlier Dr Chili post (*must be coffee-ing!*)Also exactly correct!

---

### Post by iharacomix on 2010-09-07
Thanks, (Dr?) Chili and bkratz, for the help/information! ^^

---

### Post by chakkday on 2010-09-07
> **chili555 said:**
> Please run:```
sudo rmmod -f dell-laptop
```Repeat the tests. If the wireless is working now, do:```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```Then the errant module will be permanently blacklisted.

This thing should be a sticky !! 

It was a life saver for me. 

Any idea why this happened ? Is there an issue with 10.4 or was there a later update that I took ? 

But - thanks a lot for all who contributed to this simple 2 step solution.. saved me lot of grief.

I've created an account on the forum to just thank you guys !

---

### Post by chili555 on 2010-09-07
> Any idea why this happened ? Is there an issue with 10.4 or was there a later update that I took ? I think *dell-laptop*, the module that translates key presses to kernel activity, has been flaky for some time, not just in 10.04. It is ironic that the fix is to just remove it. 

See, for instance, posts #3 and 4 here: [http://ubuntuforums.org/showthread.php?t=1414946](http://ubuntuforums.org/showthread.php?t=1414946)

---

### Post by iharacomix on 2010-09-08
chakkday: I created an account on the forum just to ask the question! XD

---

### Post by yifangt on 2010-09-30
Could you please help me out of the same problem with my Compaq laptop? 
It seems to me the problem started after I update my ubuntu 9.0 to ubuntu 10.4.

I tried all the methods above, sometime worked, but most of the time did not! Appreciate if you can show me the permanent change. Thanks a lot!

 Yifang

---

### Post by chili555 on 2010-10-01
> **yifangt said:**
> Could you please help me out of the same problem with my Compaq laptop? 
It seems to me the problem started after I update my ubuntu 9.0 to ubuntu 10.4.

I tried all the methods above, sometime worked, but most of the time did not! Appreciate if you can show me the permanent change. Thanks a lot!

 YifangSince most of the thread above concerns the module *dell-laptop* and you have a Compaq, would you please start a new thread and post:```
rfkill list all
```PM me the link, please.

---

### Post by baldy4eva on 2010-10-24
I have an HP g60 running a vanilla Maverick installation, and the wifi has cease working. I've tried booting while pressing the switch and various other combinations of switch presses, but nothing is seeming to work. 

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
cliff@Moonshot:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

```Any help would be much appreciated

---

### Post by chili555 on 2010-10-24
Since most of the thread above concerns the module dell-laptop and you have an HP, would you please start a new thread? Please send me a private message with the link.

---

### Post by diamanthunden on 2010-11-04
Hi and thanks for the useful posts above!

My Dell Studio 10 with Ubuntu 10.10 has a similar problem, Enable Wireless is greyed out. rfkill also says my Wireless LAN is hard blocked. 

Running rmmod -f dell-laptop makes the Wireless not greyed out, so that works. But i still cannot see any wireless networks in network manager. Running iwlist scan just says eth1 doesn't support scanning. Iwconfig says:

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

Any help?

Thanks :)

Ben

---

### Post by violettoulli on 2011-01-30
hi there
i have the same problem as lisa and the rfkill list tells me the same i.e.:

0: phy0: Wireless LAN
     Soft blocked: no
     Hard block: yes

now my computer is a TOSHIBA EQUIUM.

what do you mean there's a switch somewhere? never so any switch on my computer for the wireless?

Can anybody help?
thanks
vio

---

### Post by chili555 on 2011-01-30
> **violettoulli said:**
> hi there
i have the same problem as lisa and the rfkill list tells me the same i.e.:

0: phy0: Wireless LAN
     Soft blocked: no
     Hard block: yes

now my computer is a TOSHIBA EQUIUM.

what do you mean there's a switch somewhere? never so any switch on my computer for the wireless?

Can anybody help?
thanks
vioCould you please give us the exact model number?

---

