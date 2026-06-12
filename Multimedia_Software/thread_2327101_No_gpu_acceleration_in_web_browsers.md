---
title: "No gpu acceleration in web browsers"
date: 2016-06-07
forum: Multimedia Software
---

### Post by Ventussi on 2016-06-07
Hello, I have a laptop: Lenovo G50-30. It has Intel Celeron N2840 CPU, 4 GB RAM. And my problem is that there's no GPU acceleration in web browsers. During regular surfing it doesn't cause any visible problems, but when I try to watch a video on YouTube and when I set resolution to 720p or more, I have constant stuttering. In Windows it doesn't occur. At least not to that extent. It seems that the only browsers that fully support GPU acceleration in this CPU are Internet Explorer and Edge - I can watch 1080p/60 fps videos without a single stutter, whereas Firefox/Chrome/Opera/Safari/Vivaldi are a no go. Unfortunately there is no IE or Edge for Ubuntu. Is there any way to do something with it so that it works properly on Firefox?

---

### Post by Linuxisfast on 2016-06-09
In Chrome enable it under chrome://flags [http://h30434.www3.hp.com/t5/Notebook-Video-Display-and-Touch/How-to-Enable-Graphics-Hardware-Acceleration-in-Google/td-p/1753971](http://h30434.www3.hp.com/t5/Notebook-Video-Display-and-Touch/How-to-Enable-Graphics-Hardware-Acceleration-in-Google/td-p/1753971)

---

### Post by X-RED_Tech on 2016-06-09
And in Firefox there's also a setting: [IMG]https://support.cdn.mozilla.net/media/uploads/gallery/images/2015-05-08-08-38-18-67e583.png[/IMG]

---

### Post by SeijiSensei on 2016-06-09
With the Flash plugin, you can enable hardware acceleration by expanding the video to full-screen, then right-clicking on the image and checking the box in the Options dialog.

---

### Post by Ventussi on 2016-06-09
@Linuxisfast
I've tried that in Google Chrome - none effect on target.

@X-RED_Tech
This option is enabled from the very beginning. It's always been. None effect on target.

@SeijiSensei
YouTube is in HTML5, not Flash anymore. There are different options now under the RMB and none of them is responsible for GPU acceleration.

---

### Post by Rob Sayer on 2016-06-09
I suspect that WebGL isn't working, which isn't all that rare in Linux unfortunately.

Try some of the tests here perhaps ...

[http://superuser.com/questions/836832/how-can-i-enable-webgl-in-my-browser](http://superuser.com/questions/836832/how-can-i-enable-webgl-in-my-browser)

... with a couple of warnings.

First, as they mention there, trying to force WebGL can damage hardware.  I wouldn't try it myself.

Second, with that CPU in a laptop I think you have an Intel Valley View/Bay Trail series integrated video card.  Check this by copying/pasting:

inxi -Fxz

into the terminal.  It'll say whiich Intel series card where it says "OpenGL renderer string:"  This is one of the only ways I know to find out which actual damn Intel video card it is.

Whatever it is, don't try to look for drivers for Intel.  They don't really do binary drivers like Nvidia or AMD.  The ones they have are only for the newest cards and they aren't reliable anyway.  Stick to the open source Intel driver.

Unfortunately I don't know of a good solution  for 3D accel in browsers in Linux.  The support doesn't seem very good and I've never been able to find a good answer.  If anyone knows one please post it.  BTW I stick to ubuntu and arch sites mostly for serious support stuff ... most blogs are rubbish and they just steal everything from the ubuntu support sites anyway ... and then present it wrong ...

---

### Post by Ventussi on 2016-06-09
It seems WebGL is enabled.

In terms of the previously mentioned command, it says as the following:

```
System:    Host: Ciri-Ubu Kernel: 4.4.0-22-generic x86_64 (64 bit gcc: 5.3.1)
           Desktop: MATE 1.12.1 (Gtk 3.18.9-1ubuntu3)
           Distro: Ubuntu 16.04 xenial
Machine:   System: LENOVO (portable) product: 80G0 v: Lenovo G50-30
           Mobo: LENOVO model: Lancer 5A6 v: NANANANANO DPK
           Bios: LENOVO v: A7CN48WW date: 08/03/2015
CPU:       Dual core Intel Celeron N2840 (-MCP-) cache: 1024 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 8652
           clock speeds: max: 2582 MHz 1: 1848 MHz 2: 1124 MHz
Graphics:  Card: Intel Atom Processor Z36xxx/Z37xxx Series Graphics & Display
           bus-ID: 00:02.0
           Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Bay Trail
           GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes
Audio:     Card Intel Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.4.0-22-generic
Network:   Card-1: Realtek RTL8723BE PCIe Wireless Network Adapter
           driver: rtl8723be port: 2000 bus-ID: 02:00.0
           IF: wlp2s0 state: up mac: <filter>
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: 1000 bus-ID: 03:00.0
           IF: enp3s0 state: down mac: <filter>
Drives:    HDD Total Size: 128.0GB (5.3% used)
           ID-1: /dev/sda model: TS128GSSD370S size: 128.0GB
Partition: ID-1: / size: 14G used: 4.9G (38%) fs: ext4 dev: /dev/sda6
           ID-2: /home size: 4.5G used: 139M (4%) fs: ext4 dev: /dev/sda7
           ID-3: swap-1 size: 1.48GB used: 0.00GB (0%) fs: swap dev: /dev/sda8
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   None detected - is lm-sensors installed and configured?
Info:      Processes: 181 Uptime: 5 min Memory: 700.1/3835.3MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.3.421) inxi: 2.2.35 

```

---

