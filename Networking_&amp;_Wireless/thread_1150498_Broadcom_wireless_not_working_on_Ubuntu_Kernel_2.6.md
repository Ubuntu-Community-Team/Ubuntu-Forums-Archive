---
title: "Broadcom wireless not working on Ubuntu Kernel 2.6.28-12-Generic"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by cyberedsun on 2009-05-06
I have just upgraded Ubuntu kernel from 2.6.28-11 to the new 2.6.28-12 and got my Broadcom wireless on my HP TX1000 not detected. 

I tried to boot using kernel 2.6.28-11 but no luck either. 

Can anyone have any solution?

Thanks a lot!

--- ---

---

### Post by crom.osec on 2009-05-06
Except from the obvious case when you've stopped the wireless, you should check (using console) lspci to see if the card is listed and also dmesg to see what were the problems with the card.

---

### Post by twinkel1961 on 2009-05-06
Same problem here on ACER Extensa 5220

after automatic upgrade this morning, WLAN proprietary driver has disappeared (gnome:system/admin/hardware drivers)

uname -a:
[FONT="Fixedsys"]Linux twinkel-5220 2.6.28-12-generic #43-Ubuntu SMP Fri May 1 19:27:06 UTC 2009 i686 GNU/Linux[/FONT]

lspci:
[FONT="Fixedsys"]04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)[/FONT]

ps: update manager suggested a partial update which i did. now update manager has a greyed-out Linux-restriced-modules-generic.

---

### Post by pastalavista on 2009-05-06
I had the same problem. No proprietary drivers and no wireless after updating the kernel. I rebooted to the previous kernel, which had been working with or without the use of the madwifi driver, and I deactivated it. I was using it because it seemed a little bit faster (more bandwidth) but the connection held. Then I rebooted into the new kernel and the open source driver worked. I now have no proprietary drivers since updating to Jaunty also nullified my flgrx-ATI graphic driver. I guess this is progress. Tear down the old so you can build up the new...

---

### Post by crom.osec on 2009-05-06
pastalavista, I was able to install on 2.6.28-11-generic the flgrx for ati radeon hd2400, compiling the package provided by ati. It works good, so you may try to find the driver at [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

I haven't updated to 2.6.28-12, I usually wait a little before going to new kernel :P.

If your wifi card doesn't work on new kernel and it worked before, it may (usually) be due to wrong driver used. The proprietary drivers are replaced by best match (which sometime is not best). You should try first to reinstall the old proprietary drivers.

---

### Post by cyberedsun on 2009-05-06
lspci and I got the card listed as follows:

> 03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)


dmesg and I had the results as in the enclosed file.

Still have no clue...

:guitar:

---

### Post by cyberedsun on 2009-05-06
I did an update [System - Administration - Update Manager] then reboot into old kernel 2.6.28-11 and the Broadcom is back to normal. 

:KS

---

### Post by crom.osec on 2009-05-06
I don't see your card in dmseg. It seems that your system is not able to recognize it.
Search for old driver and try to compile it.
You may want to try this:
[http://onlyubuntu.blogspot.com/2008/10/how-to-setup-broadcom-wireless-bcm4312.html](http://onlyubuntu.blogspot.com/2008/10/how-to-setup-broadcom-wireless-bcm4312.html)

Is for an older kernel version, but it may work.

---

### Post by cyberedsun on 2009-05-06
I think the developers of kernel 2.6.28-12 forgot to include the Broadcom wireless. Hope they will fix it soon.

Meanwhile, let's rock :guitar:

---

### Post by pastalavista on 2009-05-06
Thanks crom.osec I was considering forcing the install of linux-restricted-modules-generic (which is greyed out also.. "uninstallable") to reinstall the flgrx and madwifi drivers but the open source ones are working, though not their best. But since things are working well enough for me now, and I don't use 3d graphics and the slowness of wifi is negligible, I don't want to push my luck. I have already reinstalled twice trying to upgrade my ATI graphics. I think I'll give the developers a chance to make things right. At least until things get too bad.

---

### Post by tawie on 2009-05-06
same problem here, have to use 2.6.28-11 again, hope fix soon.

---

### Post by woodsby on 2009-05-06
How are you guys upgrading to 2.6.28-12?  I don't see it in the repositories yet... I've been waiting for it for a few days... impatiently

---

### Post by pastalavista on 2009-05-06
> **woodsby said:**
> How are you guys upgrading to 2.6.28-12?  I don't see it in the repositories yet... I've been waiting for it for a few days... impatiently
```
sudo apt-get dist-upgrade
```

oh, I'm not sure but I believe you need to check "proposed" in your Software Sources

---

### Post by woodsby on 2009-05-06
Pastala, I did that, but I still don't see 2.6.28-12 available in my update manager or in the package manager... what updates do you have enabled (backports? proposed?)  Are you running 386 or amd64?

Pastala, i tried dist-upgrade as well... still nothing... sorry to take this thread way off topic, but that kernel release will fix my lirc....

---

### Post by pastalavista on 2009-05-06
> what updates do you have enabled (backports? proposed?) Are you running 386 or amd64?I'm using the i386 version. I have backports and proposed checked.

---

### Post by woodsby on 2009-05-06
> **pastalavista said:**
> I'm using the i386 version. I have backports and proposed checked.

I have backports and proposed checked. I see the updates available in the update manager, but it won't let me select them for update... strange... I guess I'll wait a few more days... must be an amd64 thing...

---

### Post by AaronMT on 2009-05-07
Breaks my  Dell Inspiron 1501's wireless

---

### Post by mrprefect on 2009-05-08
2.6.28-12 breaks my wireless as well on my HP TX1220ca

lspci:
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

had to go back a kernel version to get it to work again...

---

### Post by bitterjug on 2009-05-08
I seem to have the same problem. I got the partial upgrade this morning. I'm on AMD64:

```
$ uname -a
Linux moleskine 2.6.28-12-generic #43-Ubuntu SMP Fri May 1 19:31:32 UTC 2009 x86_64 GNU/Linux
```

When I looked for the device, I found it unclaimed:

```
$ sudo lshw -C net
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0

```

Since it was working ok this morning before the upgrade I had a look in /var/log/messages:

```
May  8 07:52:37 moleskine kernel: [   15.455871] eth1: Broadcom BCM4328 802.11 Wireless Controller 5.10.79.10

```

But nothing appeared today until I started trying to get it up by loading the b43 driver

```
# tail -f /var/log/messages &
# modprobe b43
mark@moleskine:/var/log$ May  8 22:02:12 moleskine kernel: [ 7873.524192] cfg80211: Calling CRDA to update world regulatory domain
May  8 22:02:12 moleskine kernel: [ 7873.560862] cfg80211: World regulatory domain updated:
May  8 22:02:12 moleskine kernel: [ 7873.560874] ^I(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May  8 22:02:12 moleskine kernel: [ 7873.560880] ^I(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  8 22:02:12 moleskine kernel: [ 7873.560886] ^I(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May  8 22:02:12 moleskine kernel: [ 7873.560891] ^I(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May  8 22:02:12 moleskine kernel: [ 7873.560896] ^I(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  8 22:02:12 moleskine kernel: [ 7873.560901] ^I(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  8 22:02:12 moleskine kernel: [ 7873.566420] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[LK1E] -> GSI 19 (level, high) -> IRQ 19
May  8 22:02:12 moleskine kernel: [ 7873.632181] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
May  8 22:02:12 moleskine kernel: [ 7873.650806] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]

```

Although this attaches a driver to the deivce

I still cant' get any wifi
```
 $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

Since this thread refers to booting 2.6.28-11 I'm about to try that. But I'd love to know how to resolve this with the latest kernel. 

Bj

---

### Post by twinkel1961 on 2009-05-08
I just installed the generic modules that were being held back from the standard Ubuntu repositories. The new kernel (2.6.28-12) now contains the broadcom STA wireless driver and wireless is woring ok again.

Going forward again from 2.6.28-11 to 2.6.28-12

reminder to self: do not install partial upgrades any more!!!

case closed as far as I am concerned.
:guitar:

---

### Post by cyberedsun on 2009-05-09
The Ubuntu team had a recent updates on non-free modules and the Broadcom wireless is working well now. 

Bravo to Ubuntu! Let's rock :guitar:

---

### Post by TCarlsen on 2009-05-28
i still can't get my hp tx1000 wireless to work :(

---

