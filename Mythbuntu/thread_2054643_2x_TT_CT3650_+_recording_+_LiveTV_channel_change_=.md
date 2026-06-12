---
title: "2x TT CT3650 + recording + LiveTV channel change = corrupted video"
date: 2012-09-07
forum: Mythbuntu
---

### Post by Henk Poley on 2012-09-07
I've finally gotten my second TechnoTrend CT-3650 CI back from repairs. But as soon as I plugin both of them, start a recording keep one tuner busy, I get corrupted video when I change channels. These USB tuners need at least kernel 3.2 to work out of the box. I built a 3.3 kernel for my Mythbuntu 10.04 setup, which worked well the past months.

I've already tried:
* Each tuner connected alone works just fine
* Swapped around Alphacrypts (my CAM)
* Upgrading to latest DVB drivers (via media_build.git) and kernel (3.3.6 -> 3.5.3). 
* Setting a 500 ms wait period when tuning channels, in mythtv-setup
* Plugging one in the back, and one in the front USB ports, so *should* use different USB channels and not some internal hub.

I'm currently recompiling Linux 3.5.3 with various debug options enabled, both general (mostly locking stuff) and specific for the dvb_usb & dvb_usb_ttusb2 modules.

I wonder what I can do next to find out what's going on ?

---

### Post by nickrout on 2012-09-08
> **Henk Poley said:**
> I've finally gotten my second TechnoTrend CT-3650 CI back from repairs. But as soon as I plugin both of them, start a recording keep one tuner busy, I get corrupted video when I change channels. These USB tuners need at least kernel 3.2 to work out of the box. I built a 3.3 kernel for my Mythbuntu 10.04 setup, which worked well the past months.

I've already tried:
* Each tuner connected alone works just fine
* Swapped around Alphacrypts (my CAM)
* Upgrading to latest DVB drivers (via media_build.git) and kernel (3.3.6 -> 3.5.3). 
* Setting a 500 ms wait period when tuning channels, in mythtv-setup
* Plugging one in the back, and one in the front USB ports, so *should* use different USB channels and not some internal hub.

I'm currently recompiling Linux 3.5.3 with various debug options enabled, both general (mostly locking stuff) and specific for the dvb_usb & dvb_usb_ttusb2 modules.

I wonder what I can do next to find out what's going on ?you could look in your log files as the channel changes.

you could update mythtv to latest 0.25-fixes.

you look at the output of lsusb to see if they are both on usb 2.0 ports.

---

### Post by Henk Poley on 2012-09-08
> **nickrout said:**
> you could look in your log files as the channel changes.

you could update mythtv to latest 0.25-fixes.

you look at the output of lsusb to see if they are both on usb 2.0 ports.
1. `dmesg` *sometimes* mutters something about "DVB CAM link initialisation failed :(" when I change channels. But I would expect to get no discernable video data at all without a properly set up CAM. While this looks 'corrupt' but ever so often faces pop up and stuff moves around as if a the scene was painted over with some digital artifact pattern. So I think some data is dropped out of the stream before it reaches the disk.

2. I'm running 0.25-fixes (MythTV Version : v0.25.2-18-g05a3d73)

3. They are on USB2.0
```
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/8p, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
    |__ Port 2: Dev 2, If 0, Class=vend., Driver=, 480M
    |__ Port 6: Dev 3, If 0, Class=vend., Driver=, 480M
```

At the moment I've managed to make the dvb drivers not load, so I'm recompiling the kernel again. Now just some minimal debug options added in on top of ubuntu's 2.6.32-42-generic with `yes '' | make oldconfig`. Too overzealous with stripping optional drivers I guess.

---

### Post by nickrout on 2012-09-08
> **Henk Poley said:**
> 1. `dmesg` *sometimes* mutters something about "DVB CAM link initialisation failed :(" when I change channels. But I would expect to get no discernable video data at all without a properly set up CAM. While this looks 'corrupt' but ever so often faces pop up and stuff moves around as if a the scene was painted over with some digital artifact pattern. So I think some data is dropped out of the stream before it reaches the disk.i was talking about your mythtv logs. But the dmesg message is possibly related. I don'tknow what encrypted video looks like when you try and play it.

Also it could be some tuning error.> 

2. I'm running 0.25-fixes (MythTV Version : v0.25.2-18-g05a3d73)

3. They are on USB2.0
```
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/8p, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
    |__ Port 2: Dev 2, If 0, Class=vend., Driver=, 480M
    |__ Port 6: Dev 3, If 0, Class=vend., Driver=, 480M
```

At the moment I've managed to make the dvb drivers not load, so I'm recompiling the kernel again. Now just some minimal debug options added in on top of ubuntu's 2.6.32-42-generic with `yes '' | make oldconfig`. Too overzealous with stripping optional drivers I guess.

---

### Post by Henk Poley on 2012-09-10
> **nickrout said:**
> Also it could be some tuning error.
The devices work well individually. But yeah, it could still be some driver funkyness when multiple tuners are involved.

Do you have a link to a howto for some other DVB-C viewing application? I've tried a couple but couldn't really get them to work with my setup, most of them require a specific 'scan' format from a specific application. It's quite opaque what's needed. Kaffeine sort of looks like it can scan on its own, but only finds one transport and doesn't show any video when tuning to the few stations found.

---

### Post by Henk Poley on 2012-09-10
If I'm reading it correctly there is much less communication to the CAM on "connection id 0x0" than to 0x1 (I suppose these identify the two different CAMs).

I've loaded dvb_usb with CAM debugging turned on:
```
sudo rmmod -f dvb_usb_ttusb2 dvb_usb dvb_core
sudo modprobe dvb_core cam_debug=1
sudo modprobe dvb_usb
sudo modprobe dvb_usb_ttusb2
``` 

Now if I check the logs for CAM messages on connection id 0x0 I just see these (all the while I'm switchin between tuners several times)
```
$ grep "connection id 0x0" /var/log/messages
Sep 10 14:01:38 Oehoe kernel: [ 8397.355045] Received CA packet for slot 0 connection id 0x0 last_frag:0 size:0x2
Sep 10 14:01:38 Oehoe kernel: [ 8397.357798] Wrote CA packet for slot 0, connection id 0x0 last_frag:0 size:0x2
Sep 10 14:02:44 Oehoe kernel: [ 8463.413329] Received CA packet for slot 0 connection id 0x0 last_frag:0 size:0x2
Sep 10 14:02:44 Oehoe kernel: [ 8463.416078] Wrote CA packet for slot 0, connection id 0x0 last_frag:0 size:0x2
Sep 10 14:03:21 Oehoe kernel: [ 8500.371808] Received CA packet for slot 0 connection id 0x0 last_frag:0 size:0x2
Sep 10 14:03:21 Oehoe kernel: [ 8500.374569] Wrote CA packet for slot 0, connection id 0x0 last_frag:0 size:0x2
Sep 10 14:04:17 Oehoe kernel: [ 8556.891830] Received CA packet for slot 0 connection id 0x0 last_frag:0 size:0x2
Sep 10 14:04:17 Oehoe kernel: [ 8556.894588] Wrote CA packet for slot 0, connection id 0x0 last_frag:0 size:0x2
Sep 10 14:06:39 Oehoe kernel: [ 8699.171808] Received CA packet for slot 0 connection id 0x0 last_frag:0 size:0x2
Sep 10 14:06:39 Oehoe kernel: [ 8699.174554] Wrote CA packet for slot 0, connection id 0x0 last_frag:0 size:0x2
Sep 10 14:09:13 Oehoe kernel: [ 8852.922532] Received CA packet for slot 0 connection id 0x0 last_frag:0 size:0x2
Sep 10 14:09:13 Oehoe kernel: [ 8852.925289] Wrote CA packet for slot 0, connection id 0x0 last_frag:0 size:0x2
Sep 10 14:09:33 Oehoe kernel: [ 8872.922934] Received CA packet for slot 0 connection id 0x0 last_frag:0 size:0x2
Sep 10 14:09:33 Oehoe kernel: [ 8872.925686] Wrote CA packet for slot 0, connection id 0x0 last_frag:0 size:0x2
Sep 10 14:11:13 Oehoe kernel: [ 8972.644734] Received CA packet for slot 0 connection id 0x0 last_frag:0 size:0x2
Sep 10 14:11:13 Oehoe kernel: [ 8972.648748] Wrote CA packet for slot 0, connection id 0x0 last_frag:0 size:0x2
Sep 10 14:12:13 Oehoe kernel: [ 9033.073206] Received CA packet for slot 0 connection id 0x0 last_frag:0 size:0x2
Sep 10 14:12:13 Oehoe kernel: [ 9033.075977] Wrote CA packet for slot 0, connection id 0x0 last_frag:0 size:0x2
Sep 10 14:13:59 Oehoe kernel: [ 9138.921807] Received CA packet for slot 0 connection id 0x0 last_frag:0 size:0x2
Sep 10 14:13:59 Oehoe kernel: [ 9138.925076] Wrote CA packet for slot 0, connection id 0x0 last_frag:0 size:0x2
```
This only seems to send/receive a packet of size 0x2.

While to connection id 0x1 many different sizes messages are sent (I do some logfile mangling with `cut` and `uniq`!):
```
$ grep "connection id 0x1" /var/log/messages | cut -b 46- | sort | uniq 
Received CA packet for slot 0 connection id 0x1 last_frag:1 size:0x13
Received CA packet for slot 0 connection id 0x1 last_frag:1 size:0x14
Received CA packet for slot 0 connection id 0x1 last_frag:1 size:0x15
Received CA packet for slot 0 connection id 0x1 last_frag:1 size:0x23
Received CA packet for slot 0 connection id 0x1 last_frag:1 size:0x31
Received CA packet for slot 0 connection id 0x1 last_frag:1 size:0x6
Received CA packet for slot 0 connection id 0x1 last_frag:1 size:0x6b
Received CA packet for slot 0 connection id 0x1 last_frag:1 size:0x7e
Received CA packet for slot 0 connection id 0x1 last_frag:1 size:0x9
Received CA packet for slot 0 connection id 0x1 last_frag:1 size:0xd
Received CA packet for slot 0 connection id 0x1 last_frag:1 size:0xf
Wrote CA packet for slot 0, connection id 0x1 last_frag:1 size:0x14
Wrote CA packet for slot 0, connection id 0x1 last_frag:1 size:0x1d
Wrote CA packet for slot 0, connection id 0x1 last_frag:1 size:0x21
Wrote CA packet for slot 0, connection id 0x1 last_frag:1 size:0x24
Wrote CA packet for slot 0, connection id 0x1 last_frag:1 size:0x27
Wrote CA packet for slot 0, connection id 0x1 last_frag:1 size:0x29
Wrote CA packet for slot 0, connection id 0x1 last_frag:1 size:0x2e
Wrote CA packet for slot 0, connection id 0x1 last_frag:1 size:0x3d
Wrote CA packet for slot 0, connection id 0x1 last_frag:1 size:0x5
Wrote CA packet for slot 0, connection id 0x1 last_frag:1 size:0xa
Wrote CA packet for slot 0, connection id 0x1 last_frag:1 size:0xd
Wrote CA packet for slot 0, connection id 0x1 last_frag:1 size:0xe
Wrote CA packet for slot 0, connection id 0x1 last_frag:1 size:0xf
```

I guess somehow mythtv or dvb_core is trying to use the CAM in the other hardware device for a different tuner. Though "connection id" might mean something different.

For good measure, same for connection id 0x0:
```
grep "connection id 0x0" /var/log/messages | cut -b 46- | sort | uniq
Received CA packet for slot 0 connection id 0x0 last_frag:0 size:0x2
Wrote CA packet for slot 0, connection id 0x0 last_frag:0 size:0x2
```

Edit: it appears "connection id" does not refer to different physical CAM cards. At least id 0x1 still shows up with just one CT-3650 connected.

---

### Post by Henk Poley on 2012-09-10
I patched the code in drivers/media/dvb/dvb-core/dvb_ca_en50221.c to display the /dev/dvb/adapter# id:
```
--- dvb_ca_en50221.c.bak	2012-09-10 15:53:45.000000000 +0200
+++ dvb_ca_en50221.c	2012-09-10 15:58:25.000000000 +0200
@@ -680,7 +680,7 @@
 		memcpy(ebuf, buf, bytes_read);
 	}
 
-	dprintk("Received CA packet for slot %i connection id 0x%x last_frag:%i size:0x%x\n", slot,
+	dprintk("Received CA packet on adapter %d, for slot %i connection id 0x%x last_frag:%i size:0x%x\n", ca->dvbdev->adapter->num, slot,
 		buf[0], (buf[1] & 0x80) == 0, bytes_read);
 
 	/* wake up readers when a last_fragment is received */
@@ -769,7 +769,7 @@
 	}
 	status = bytes_write;
 
-	dprintk("Wrote CA packet for slot %i, connection id 0x%x last_frag:%i size:0x%x\n", slot,
+	dprintk("Wrote CA packet for adapter %d, for slot %i, connection id 0x%x last_frag:%i size:0x%x\n", ca->dvbdev->adapter->num, slot,
 		buf[0], (buf[1] & 0x80) == 0, bytes_write);
 
 exit:

```

But now mythtv doesn't record anything to its LiveTV buffer and frontend errors out, "Error opening jump program file buffer".

The above does give both adapter 0 and 1 in /var/log/messages, so that's nice.

---

### Post by Henk Poley on 2012-09-10
> **Henk Poley said:**
> But now mythtv doesn't record anything to its LiveTV buffer and frontend errors out, "Error opening jump program file buffer".
Strangely enough a remote frontend (running OS X) can start LiveTV, while the frontend&backend combo can't ??

For good measure I tried dual tuner with the remote frontend, but that's still broken :P

---

### Post by Henk Poley on 2012-12-03
> **Henk Poley said:**
> 3. They are on USB2.0
```
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/8p, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
    |__ Port 2: Dev 2, If 0, Class=vend., Driver=, 480M
    |__ Port 6: Dev 3, If 0, Class=vend., Driver=, 480M
```
The above layout (two devices per Bus) means the two CT-3650 share bandwidth. 

I solved this by adding a PCIe card that adds USB3.0 ports, and plugging in one CT-3650 in one of the new USB3.0 ports.

---

