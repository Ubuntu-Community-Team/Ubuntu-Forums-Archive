---
title: "iCon 401 3G USB modem not connecting in Ubuntu 9.04 (Jaunty)"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by Junkieman on 2009-05-15
Hi all. I upgraded from Intrepid to Jaunty, and now I can't connect to the net anymore. I hope someone out there can help me fix this, I'd like to stay with Jaunty if I can!

NetworkManager shows my device, but when I try connect to the net it tells me, without any wait, that I have been disconnected. The sys logs (below) return the message 'timeout', if less-than a second is even a waiting period ;)

I made sure my system was up to date before I upgraded using the alternate CD method. I have a dd backup of my OS partition if it comes to that :/

While on Intrepid [I tried a few ways]("http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=109") to get the iCON 401 3G modem working, and eventually got it sorted with this really useful [Pharscape post]("http://pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html"). (Involving disabling the ZeroCD modem state, and compiling the Option hso module )

As far as I can tell, the ZeroCD mode is disabled on my modem, it doesn't show up as a storage device (lsusb), and a call to usb_modeswitch tells me the device is switched already. After I connect it I can see ttyHS0..x devices, the modem is ttyHS2.

```
wesley@vesta:/tmp/udev$ sudo lsusb
...snip...
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 019: ID 0af0:7401 Option 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
...snip...
```

a dmesg says otherwise after I attach the modem:
```
:$ dmesg | tail
[ 3364.989301] hso0: Disabled Privacy Extensions
[ 3364.990104] usb-storage: probe of 1-3:1.8 failed with error -5
[ 3364.990724] usb-storage: probe of 1-3:1.9 failed with error -5
[ 3364.991355] scsi29 : SCSI emulation for USB Mass Storage devices
[ 3364.991731] usb-storage: device found at 9
[ 3364.991733] usb-storage: waiting for device to settle before scanning
[ 3369.988520] usb-storage: device scan complete
[ 3369.989140] scsi 29:0:0:0: Direct-Access     ZCOption HSUPA Modem           PQ: 0 ANSI: 2
[ 3369.993068] sd 29:0:0:0: [sdc] Attached SCSI removable disk
[ 3369.993130] sd 29:0:0:0: Attached scsi generic sg3 type 0
```

The upgrade also left me with multiple hso modules, but they shouldn't cause problems since they are for a specific kernel, right? Here they are:

```
wesley@vesta:/tmp$ find /lib/modules/ -name 'hso.ko'
/lib/modules/2.6.27-11-generic/kernel/drivers/net/usb/hso.ko
/lib/modules/2.6.28-11-generic/kernel/drivers/net/usb/hso.ko
/lib/modules/2.6.28-11-generic/kernel/drivers/net/wwan/hso.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/net/wwan/hso.ko
```

I compiled the latest Option drivers as [shown on Pharscape]("http://www.pharscape.org/forum/index.php?topic=720.0"), no joy. I also entertained the idea of it being a [NetworkManager bug]("https://bugs.edge.launchpad.net/ubuntu/+source/network-manager/+bug/368325/"), the workaround (entering a dummy user/passwd) still won't let me connect.

Has anyone any experience with this or any other Option 3G USB modem in Jaunty? 

Any tips would be helpful at this point! :D

*Here is a log after I try to connect to the net through NetworkManager:*
```
May 14 20:05:40 vesta NetworkManager: <debug> [1242324340.469180] nm_serial_device_open(): (ttyHS2) opening device... 
May 14 20:05:40 vesta NetworkManager: <info>  Activation (ttyHS2) Stage 1 of 5 (Device Prepare) complete. 
May 14 20:05:40 vesta NetworkManager: <info>  (ttyHS2): powering up... 
May 14 20:05:40 vesta NetworkManager: <info>  Registered on Home network 
May 14 20:05:40 vesta NetworkManager: <info>  Associated with network: +COPS: 0,0,"VodaCom-SA",2 
May 14 20:05:40 vesta kernel: [ 3481.498583] usb 1-3: USB disconnect, address 11
May 14 20:05:40 vesta NetworkManager: <WARN>  dial_done(): Dialing timed out 
May 14 20:05:40 vesta NetworkManager: <info>  (ttyHS2): device state change: 4 -> 9 
May 14 20:05:40 vesta NetworkManager: <debug> [1242324340.918638] nm_serial_device_close(): Closing device 'ttyHS2' 
May 14 20:05:40 vesta NetworkManager: <info>  Marking connection 'the matrix' invalid. 
May 14 20:05:40 vesta NetworkManager: <info>  Activation (ttyHS2) failed. 
May 14 20:05:40 vesta NetworkManager: <info>  (ttyHS2): device state change: 9 -> 3 
May 14 20:05:40 vesta NetworkManager: <info>  (ttyHS2): deactivating device (reason: 0). 
```

---

### Post by lusepuster on 2009-05-16
I have the same issue, and would be very happy if anyone could help me fix this.

---

### Post by Chiapo on 2009-05-18
I'm also unable to connect using my internal 3G/HSDPA/UMTS/EDGE modem.
Network Manager doesn't recognize the Qualcomm 9121 as a modem.
Tried wvdial, and that took quite a few trips into windows to download the respective dependencies.
Tried modeswitch... No luck there.
Tried finding "usbserials" to no avail...
Signed, "Stuck using Windoze"

---

### Post by Junkieman on 2009-05-18
I took a chance assuming the modem would still work after the upgrade, and I cant afford to be offline for too long.

I have to go back to Intrepid for my modem to work! Will keep this thread open since this issue is unresolved, and I'll also help anyone else with this problem, however I can - A [VM ]("http://www.vmware.com/products/player/")should allow me to try out any drivers/changes until then ;)

I'll upgrade once it's safe to do so, until then a clean install should do me good! (Had the previous OS since 7.10 Gutsy!)

---

### Post by GeorgeVita on 2009-05-19
Hi **Junkieman**,

> Registered on Home network
Associated with network: +COPS: 0,0,"VodaCom-SA",2

in your 1st post the log shows a connection established in 3G (UMTS) mode! Can you try some basic tests (if already did not)?

- delete any connection (Network Manager, Broadband Connection)
- add again your connection but be sure for APN, Phone#, user & password (remember your working data with 8.10 or ask your provider)
- try again

EDIT: try also with the Wireless Disabled

Regards,
George

---

### Post by Junkieman on 2009-05-20
Hi George, thanks for the suggestions! 

I have tried those, recreated my connection in Network Manager, using a custom APN without a user name + password, and again with bogus credentials. 

I am sure the details are right, as I can connect through the 3G modem on my work notebook (ms win v6.0.6). Also from a clean 8.10 install, I use udev to disable zeroCD as [shown here]("http://pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html"), and the modem works 100%. 

I'm pretty confident it's related to the Jaunty release, if I can find what changed between the two releases I could maybe solve this.

This is on my home desktop PC, there's no wireless to complicate the problem ;)

---

### Post by coy on 2009-06-21
> **Junkieman said:**
> Hi George, thanks for the suggestions! 

I have tried those, recreated my connection in Network Manager, using a custom APN without a user name + password, and again with bogus credentials. 

I am sure the details are right, as I can connect through the 3G modem on my work notebook (ms win v6.0.6). Also from a clean 8.10 install, I use udev to disable zeroCD as [shown here]("http://pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html"), and the modem works 100%. 

I'm pretty confident it's related to the Jaunty release, if I can find what changed between the two releases I could maybe solve this.

This is on my home desktop PC, there's no wireless to complicate the problem ;)
I have the same problem on Dell Studio 1537.  The modem is made by Option from AT&T they call it quicksilver

---

### Post by baker126 on 2009-06-21
I just got my Quicksilver to work....I am using right now to post this reply.  I deleted all my Mobile Broadband connections and set up a new one, 3g.  The only information I supplied was the phone number, *99#.  I connected immediately.  

Hope this helps.

---

### Post by Junkieman on 2009-06-22
@baker good stuff! My Option iCON 401 isn't being as compliant in Jaunty, yet!

---

### Post by DonnieP on 2009-07-05
I finally got the AT&T QuickSilver broadband modem working with Jaunty using HSOconnect build 128 from PHARscape.

---

### Post by HandeH on 2009-07-12
.

---

### Post by HandeH on 2009-07-12
I'm also unable to connect. First I followed instructions of [http://peck.org.uk/ozerocdoff.html](http://peck.org.uk/ozerocdoff.html). Then, after trying to connect using Network-Manager there was printed in syslog: 

```
Jul  1 21:04:25 *** NetworkManager: <info>  Activation (ttyHS2) starting connection 'Wekkula' 
Jul  1 21:04:25 *** NetworkManager: <info>  (ttyHS2): device state change: 3 -> 4 
Jul  1 21:04:25 *** NetworkManager: <info>  Activation (ttyHS2) Stage 1 of 5 (Device Prepare) scheduled... 
Jul  1 21:04:25 *** NetworkManager: <info>  Activation (ttyHS2) Stage 1 of 5 (Device Prepare) started... 
Jul  1 21:04:25 *** NetworkManager: <debug> [1246471465.402694] nm_serial_device_open(): (ttyHS2) opening device... 
Jul  1 21:04:25 *** NetworkManager: <info>  Activation (ttyHS2) Stage 1 of 5 (Device Prepare) complete. 
Jul  1 21:04:25 *** NetworkManager: <info>  (ttyHS2): powering up... 
Jul  1 21:04:25 *** NetworkManager: <info>  Registered on Home network 
Jul  1 21:04:25 *** NetworkManager: <info>  Associated with network: +COPS: 0,0,"Welho",2 
Jul  1 21:04:25 *** NetworkManager: <WARN>  dial_done(): Dialing timed out 
Jul  1 21:04:25 *** NetworkManager: <info>  (ttyHS2): device state change: 4 -> 9 
Jul  1 21:04:25 *** NetworkManager: <debug> [1246471465.834104] nm_serial_device_close(): Closing device 'ttyHS2' 
Jul  1 21:04:25 *** kernel: [  143.640644] usb 1-8: USB disconnect, address 4
Jul  1 21:04:25 *** kernel: [  143.643451] BUG: unable to handle kernel NULL pointer dereference at 0000003c
Jul  1 21:04:25 *** kernel: [  143.643458] IP: [<c04fd983>] mutex_unlock+0x3/0x10
Jul  1 21:04:25 *** kernel: [  143.643468] *pde = 00000000 
Jul  1 21:04:25 *** kernel: [  143.643474] Oops: 0002 [#1] SMP 
Jul  1 21:04:25 *** kernel: [  143.643477] last sysfs file: /sys/devices/platform/acer-wmi/rfkill/rfkill0/state
Jul  1 21:04:25 *** kernel: [  143.643482] Dumping ftrace buffer:
Jul  1 21:04:25 *** kernel: [  143.643486]    (ftrace buffer empty)
Jul  1 21:04:25 *** kernel: [  143.643489] Modules linked in: rfkill_input i915 drm binfmt_misc ppdev bridge stp bnep lp parport hso snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss arc4 snd_pcm ecb snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi pcmcia b43 snd_seq_midi_event iTCO_wdt joydev snd_seq snd_timer snd_seq_device iTCO_vendor_support mac80211 yenta_socket rsrc_nonstatic acer_wmi snd soundcore cfg80211 pcspkr psmouse pcmcia_core snd_page_alloc led_class input_polldev serio_raw intel_agp agpgart video output usbhid 8139too 8139cp mii ssb usb_storage fbcon tileblit font bitblit softcursor
Jul  1 21:04:25 *** kernel: [  143.643541] 
Jul  1 21:04:25 *** kernel: [  143.643545] Pid: 2869, comm: NetworkManager Not tainted (2.6.28-13-generic #44-Ubuntu) Aspire 3620
Jul  1 21:04:25 *** kernel: [  143.643549] EIP: 0060:[<c04fd983>] EFLAGS: 00010206 CPU: 0
Jul  1 21:04:25 *** kernel: [  143.643553] EIP is at mutex_unlock+0x3/0x10
Jul  1 21:04:25 *** kernel: [  143.643556] EAX: 0000003c EBX: f66fd840 ECX: f609ef00 EDX: 00000001
Jul  1 21:04:25 *** kernel: [  143.643559] ESI: 00000001 EDI: 00000000 EBP: f5eabe7c ESP: f5eabe7c
Jul  1 21:04:25 *** kernel: [  143.643562]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Jul  1 21:04:25 *** kernel: [  143.643565] Process NetworkManager (pid: 2869, ti=f5eaa000 task=f5e10000 task.ti=f5eaa000)
Jul  1 21:04:25 *** kernel: [  143.643568] Stack:
Jul  1 21:04:25 *** kernel: [  143.643570]  f5eabe98 f7cc8083 00000000 c0625d0b ed763800 ed763800 f66ee540 f5eabf40
Jul  1 21:04:25 *** kernel: [  143.643578]  c032d397 00000007 00000001 00000009 00190001 ed763800 ed794a80 00000000
Jul  1 21:04:25 *** kernel: [  143.643585]  f5eabed0 00000286 00000000 f5eabf3c 00000000 f5eabeec c0152a0a 00000000
Jul  1 21:04:25 *** kernel: [  143.643593] Call Trace:
Jul  1 21:04:25 *** kernel: [  143.643596]  [<f7cc8083>] ? hso_serial_close+0x63/0xf0 [hso]
Jul  1 21:04:25 *** kernel: [  143.643607]  [<c032d397>] ? tty_release_dev+0x147/0x4d0
Jul  1 21:04:25 *** kernel: [  143.643614]  [<c0152a0a>] ? hrtimer_try_to_cancel+0x3a/0x90
Jul  1 21:04:25 *** kernel: [  143.643620]  [<c0152a71>] ? hrtimer_cancel+0x11/0x20
Jul  1 21:04:25 *** kernel: [  143.643624]  [<c04fded9>] ? do_nanosleep+0x99/0xc0
Jul  1 21:04:25 *** kernel: [  143.643628]  [<c032d732>] ? tty_release+0x12/0x20
Jul  1 21:04:25 *** kernel: [  143.643632]  [<c01bea44>] ? __fput+0xb4/0x1c0
Jul  1 21:04:25 *** kernel: [  143.643638]  [<c01beb6f>] ? fput+0x1f/0x30
Jul  1 21:04:25 *** kernel: [  143.643642]  [<c01bb559>] ? filp_close+0x49/0x70
Jul  1 21:04:25 *** kernel: [  143.643646]  [<c01bb5fa>] ? sys_close+0x7a/0xc0
Jul  1 21:04:25 *** kernel: [  143.643650]  [<c0103f6b>] ? sysenter_do_call+0x12/0x2f
Jul  1 21:04:25 *** kernel: [  143.643655] Code: 04 24 89 d8 c7 45 e8 00 ed 14 c0 e8 e8 fe ff ff 8b 5d f4 8b 75 f8 8b 7d fc 89 ec 5d c3 00 00 00 00 00 00 00 00 00 00 00 55 89 e5 <3e> ff 00 7f 05 e8 43 01 00 00 5d c3 90 55 ba 01 00 00 00 89 e5 
Jul  1 21:04:25 *** kernel: [  143.643697] EIP: [<c04fd983>] mutex_unlock+0x3/0x10 SS:ESP 0068:f5eabe7c
Jul  1 21:04:25 *** kernel: [  143.643704] ---[ end trace fe91c6f6868257ef ]---
Jul  1 21:04:30 *** kernel: [  148.504175] usb 1-8: new high speed USB device using ehci_hcd and address 5
Jul  1 21:04:30 *** kernel: [  148.640290] usb 1-8: configuration #1 chosen from 1 choice
Jul  1 21:04:30 *** kernel: [  148.641478] scsi14 : SCSI emulation for USB Mass Storage devices
Jul  1 21:04:30 *** kernel: [  148.642018] usb-storage: device found at 5
Jul  1 21:04:30 *** kernel: [  148.642021] usb-storage: waiting for device to settle before scanning
Jul  1 21:04:31 *** kernel: [  149.761999] usb 1-8: USB disconnect, address 5
Jul  1 21:04:32 *** kernel: [  150.008034] usb 1-8: new high speed USB device using ehci_hcd and address 6
Jul  1 21:04:32 *** kernel: [  150.144232] usb 1-8: configuration #1 chosen from 1 choice
Jul  1 21:04:32 *** kernel: [  150.146890] usb-storage: probe of 1-8:1.0 failed with error -5
Jul  1 21:04:32 *** kernel: [  150.147912] usb-storage: probe of 1-8:1.1 failed with error -5
Jul  1 21:04:32 *** kernel: [  150.148886] usb-storage: probe of 1-8:1.2 failed with error -5
Jul  1 21:04:32 *** kernel: [  150.149654] usb-storage: probe of 1-8:1.3 failed with error -5
Jul  1 21:04:32 *** kernel: [  150.150512] usb-storage: probe of 1-8:1.4 failed with error -5
Jul  1 21:04:32 *** kernel: [  150.151280] usb-storage: probe of 1-8:1.5 failed with error -5
Jul  1 21:04:32 *** kernel: [  150.152666] usb-storage: probe of 1-8:1.6 failed with error -5
Jul  1 21:04:32 *** kernel: [  150.153562] usb-storage: probe of 1-8:1.7 failed with error -5
Jul  1 21:04:32 *** kernel: [  150.154529] hso0: Disabled Privacy Extensions
Jul  1 21:04:32 *** kernel: [  150.155608] usb-storage: probe of 1-8:1.8 failed with error -5
Jul  1 21:04:32 *** kernel: [  150.157023] usb-storage: probe of 1-8:1.9 failed with error -5
Jul  1 21:04:32 *** kernel: [  150.158001] scsi25 : SCSI emulation for USB Mass Storage devices
Jul  1 21:04:32 *** kernel: [  150.158525] usb-storage: device found at 6
Jul  1 21:04:32 *** kernel: [  150.158528] usb-storage: waiting for device to settle before scanning
Jul  1 21:04:37 *** kernel: [  155.156505] usb-storage: device scan complete
Jul  1 21:04:37 *** kernel: [  155.156997] scsi 25:0:0:0: Direct-Access     ZCOption HSUPA Modem           PQ: 0 ANSI: 2
Jul  1 21:04:37 *** kernel: [  155.161141] sd 25:0:0:0: [sdb] Attached SCSI removable disk
Jul  1 21:04:37 *** kernel: [  155.161247] sd 25:0:0:0: Attached scsi generic sg2 type 0
```

Mobile broadband connection is provided by Finnish operator called Welho [http://www.welho.fi](http://www.welho.fi), who have made instructions for Intrepid [here]("http://www.welho.fi/LinkClick.aspx?link=Welho_fi%2fAsiakaspalvelu%2findex.pdf&tabid=637") (pdf).

---

### Post by Junkieman on 2009-07-14
@DonnieP thanks for the feedback, glad you're connected.

@HandeH maybe try the [HSO driver]("http://www.pharscape.org/hso.html") if your device is supported (check the link).

---

### Post by HandeH on 2009-07-14
> **Junkieman said:**
> 
@HandeH maybe try the [HSO driver]("http://www.pharscape.org/hso.html") if your device is supported (check the link).

Thanks for an advice. My device is iCon 401 (as there is in the topic of this thread). Do you still suggest to try that link? I'm interested in trying to submit a bug report, so any help is appreciated.

---

### Post by Junkieman on 2009-07-15
Hi HandeH, I couldn't get my 401 working on Jaunty, that's why I went back to Intrepid; I don't think it's as much a bug as it is a case of new hardware with unsupported drivers.

I did not completely pass off the bug-theory, but the instructions for this [reported bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/368325") didn't help me specifically.

The HSO 1.2 driver is included in Intrepid, which is why the iCon 401 works on [Intrepid after these instructions]("http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html"), but I didn't get that far in Jaunty.

I'm sure the HSO driver will reach a stage where it will work, so keep on trying the new versions that come out :p

Edit: As in my OP, try the [bug workaround]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/368325/comments/21"), it might work for you.

---

### Post by HandeH on 2009-07-15
> **Junkieman said:**
> 

Edit: As in my OP, try the [bug workaround]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/368325/comments/21"), it might work for you.

Dummy values for username and password have not helped for iCon 401 in Jaunty.

---

### Post by HandeH on 2009-08-06
Good news at last! :D
It seems to be soon working for everybody. Here is a workaround I discovered yesterday. 

I have found out that the coming NetworkManager 0.7.1 will fix this (Option Icon 401 not working). Until the packages are ready and updated to Ubuntu's main repositories, you might want to visit [PPA for Network-manager]("https://launchpad.net/~network-manager/+archive/ppa") to add their personal repository to your system's software sources. 

Then update your system. 
It should work automatically, but if needed do it manually by updating network-manager and network-manager-applet and their dependencies and remove (e.g. by Synaptic) libmbca0. 

You still have to have [ozerocdoff]("http://peck.org.uk/ozerocdoff.html") utility compiled (it's easy!), which needs at least libusb-dev and patch (or dpkg-dev) installed before hand. After that the plugged USB modem will be recognized as a modem and not a CD-drive.

**Note**: This how to is not updated anymore!

---

### Post by DonnieP on 2009-08-10
> **HandeH said:**
> Good news at last! :D
It seems to be soon working for everybody. Here is a workaround I discovered yesterday. 

I have found out that the coming NetworkManager 0.7.1 will fix this (Option Icon 401 not working). Until the packages are ready and updated to Ubuntu's main repositories, you might want to visit [PPA for Network-manager]("https://launchpad.net/~network-manager/+archive/ppa") to add their personal repository to your system's software sources. 

Unfortunately, this doesn't work for me for the Icon 322 3G (AT&T QuickSilver).

---

