---
title: "Mobile broadband pcmcia card doesn't work with ubuntu 9.10"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by viktorfulop on 2010-01-24
So here's the thing: I have a mobile broadband pcmcia card that worked just well on jaunty, but as I installed karmic it doesn't work, coz it mounts the card's storage but doesn't recognize the hardware. The help says I need the package 'udev-extras', but there's no such package for karmic and the one for jaunty doesn't work with karmic. Can somebody help me somehow on this issue?

---

### Post by GeorgeVita on 2010-01-24
Hi **viktorfulop**, welcome to this forum!

There are 2 points to check:

1. try to eject any virtual 'CD-ROM' and then look for any port created
2. update your Ubuntu 9.10 using other internet connection (wifi/ethernet)

To determine system activity for your modem:
- boot without the card inserted
- from a terminal window: **sudo dmesg -c** (will show and clear log)
- insert card, **wait** 20-30 seconds
- from terminal: **dmesg** (will show all NEW activity)
- if you notice any 'CD-ROM ... **srX**' try to eject it from icon or using '**sudo eject srX**'

Post any progress for new ideas.

Regards,
George

---

### Post by viktorfulop on 2010-01-26
Hi George,
thanks for the reply. I couldn't do an update with another connection, because karmic also doesn't work with my built-in wireless card. I did sudo lshw -C network and it sees the card but it is disabled I don't know how to enable it (mainly because I'm pretty new for linux systems). So if you can please help me in this issue too. Also, I did the steps you mentioned, I'm gonna post the results, maybe it helps something also this way.
After I did the sudo dmesg -c I inserted the card, waited than got this from the dmesg:

```
[  174.888050] usb 2-4: new full speed USB device using ohci_hcd and address 2
[  175.095280] usb 2-4: configuration #1 chosen from 1 choice
[  175.101628] scsi4 : SCSI emulation for USB Mass Storage devices
[  175.101929] usb 2-4: USB disconnect, address 2
[  175.102003] usb-storage: device found at 2
[  175.102008] usb-storage: waiting for device to settle before scanning
[  176.644044] usb 2-4: new full speed USB device using ohci_hcd and address 3
[  176.851270] usb 2-4: configuration #1 chosen from 1 choice
[  176.865308] scsi7 : SCSI emulation for USB Mass Storage devices
[  176.866855] usb-storage: device found at 3
[  176.866862] usb-storage: waiting for device to settle before scanning
[  176.912997] usbcore: registered new interface driver usbserial
[  176.913033] USB Serial support registered for generic
[  176.913111] usbcore: registered new interface driver usbserial_generic
[  176.913116] usbserial: USB Serial Driver core
[  176.923257] USB Serial support registered for GSM modem (1-port)
[  176.923351] option 2-4:1.0: GSM modem (1-port) converter detected
[  176.923511] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[  176.923532] option 2-4:1.1: GSM modem (1-port) converter detected
[  176.923632] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[  176.923669] usbcore: registered new interface driver option
[  176.923674] option: v0.7.2:USB Driver for GSM modems
[  181.865170] usb-storage: device scan complete
[  181.869150] scsi 7:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  181.901107] sr1: scsi-1 drive
[  181.901367] sr 7:0:0:0: Attached scsi CD-ROM sr1
[  181.901504] sr 7:0:0:0: Attached scsi generic sg3 type 5
[  187.514084] option: option_instat_callback: error -108
[  187.515285] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  187.515315] option 2-4:1.0: device disconnected
[  187.515433] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  187.515468] option 2-4:1.1: device disconnected
[  187.688048] usb 2-4: reset full speed USB device using ohci_hcd and address 3
[  187.889292] option 2-4:1.1: GSM modem (1-port) converter detected
[  187.889457] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[  187.897909] option 2-4:1.0: GSM modem (1-port) converter detected
[  187.898094] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[  189.536083] option: option_instat_callback: error -108
[  189.537295] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  189.537324] option 2-4:1.0: device disconnected
[  189.537442] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  189.537476] option 2-4:1.1: device disconnected
[  189.712050] usb 2-4: reset full speed USB device using ohci_hcd and address 3
[  189.913291] option 2-4:1.1: GSM modem (1-port) converter detected
[  189.913456] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[  189.922103] option 2-4:1.0: GSM modem (1-port) converter detected
[  189.922289] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[  190.221080] option: option_instat_callback: error -108
[  190.222271] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  190.222299] option 2-4:1.0: device disconnected
[  190.222422] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  190.222457] option 2-4:1.1: device disconnected
[  190.396047] usb 2-4: reset full speed USB device using ohci_hcd and address 3
[  190.597284] option 2-4:1.1: GSM modem (1-port) converter detected
[  190.597450] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[  190.606366] option 2-4:1.0: GSM modem (1-port) converter detected
[  190.606546] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[  190.647079] option: option_instat_callback: error -108
[  190.672357] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  190.672397] option 2-4:1.0: device disconnected
[  190.672522] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  190.672557] option 2-4:1.1: device disconnected
[  190.848049] usb 2-4: reset full speed USB device using ohci_hcd and address 3
[  191.049290] option 2-4:1.1: GSM modem (1-port) converter detected
[  191.049457] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[  191.058215] option 2-4:1.0: GSM modem (1-port) converter detected
[  191.058393] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[  191.152076] option: option_instat_callback: error -108
[  191.152274] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  191.152312] option 2-4:1.0: device disconnected
[  191.152434] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  191.152468] option 2-4:1.1: device disconnected
[  191.328068] usb 2-4: reset full speed USB device using ohci_hcd and address 3
[  191.529283] option 2-4:1.1: GSM modem (1-port) converter detected
[  191.529458] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[  191.538526] option 2-4:1.0: GSM modem (1-port) converter detected
[  191.538710] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[  191.889075] option: option_instat_callback: error -108
[  191.889205] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  191.889223] option 2-4:1.0: device disconnected
[  191.889284] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  191.889301] option 2-4:1.1: device disconnected
[  192.064055] usb 2-4: reset full speed USB device using ohci_hcd and address 3
[  192.266297] option 2-4:1.1: GSM modem (1-port) converter detected
[  192.266466] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[  192.277206] option 2-4:1.0: GSM modem (1-port) converter detected
[  192.277398] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[  192.368080] option: option_instat_callback: error -108
[  192.368279] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  192.368321] option 2-4:1.0: device disconnected
[  192.368443] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  192.368476] option 2-4:1.1: device disconnected
[  192.544068] usb 2-4: reset full speed USB device using ohci_hcd and address 3
[  192.745292] option 2-4:1.1: GSM modem (1-port) converter detected
[  192.745458] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[  192.760331] option 2-4:1.0: GSM modem (1-port) converter detected
[  192.760513] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[  192.832136] ISO 9660 Extensions: Microsoft Joliet Level 3
[  192.852082] option: option_instat_callback: error -108
[  192.852350] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  192.852388] option 2-4:1.0: device disconnected
[  192.852510] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  192.852542] option 2-4:1.1: device disconnected
[  193.028057] usb 2-4: reset full speed USB device using ohci_hcd and address 3
[  193.229565] option 2-4:1.1: GSM modem (1-port) converter detected
[  193.229856] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[  193.252666] option 2-4:1.0: GSM modem (1-port) converter detected
[  193.252847] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[  193.260184] ISOFS: changing to secondary root
[  193.289079] option: option_instat_callback: error -108
[  193.290789] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  193.290833] option 2-4:1.0: device disconnected
[  193.290952] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  193.290986] option 2-4:1.1: device disconnected
[  193.452671] usb 2-4: reset full speed USB device using ohci_hcd and address 3
[  193.645232] option 2-4:1.1: GSM modem (1-port) converter detected
[  193.645343] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[  193.656344] option 2-4:1.0: GSM modem (1-port) converter detected
[  193.656464] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[  193.705076] option: option_instat_callback: error -108
[  193.707220] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  193.707247] option 2-4:1.0: device disconnected
[  193.707319] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  193.707337] option 2-4:1.1: device disconnected
[  193.880067] usb 2-4: reset full speed USB device using ohci_hcd and address 3
[  194.081292] option 2-4:1.1: GSM modem (1-port) converter detected
[  194.081459] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[  194.090023] option 2-4:1.0: GSM modem (1-port) converter detected
[  194.090215] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[  194.202084] option: option_instat_callback: error -108
[  194.203104] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  194.203148] option 2-4:1.0: device disconnected
[  194.203275] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  194.203309] option 2-4:1.1: device disconnected
[  194.380061] usb 2-4: reset full speed USB device using ohci_hcd and address 3
[  194.581356] option 2-4:1.1: GSM modem (1-port) converter detected
[  194.581494] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[  194.592409] option 2-4:1.0: GSM modem (1-port) converter detected
[  194.592531] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[  194.631076] option: option_instat_callback: error -108
[  194.631269] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  194.631309] option 2-4:1.0: device disconnected
[  194.631432] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  194.631464] option 2-4:1.1: device disconnected
[  194.804068] usb 2-4: reset full speed USB device using ohci_hcd and address 3
[  195.005621] option 2-4:1.1: GSM modem (1-port) converter detected
[  195.005802] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[  195.005928] option 2-4:1.0: GSM modem (1-port) converter detected
[  195.006046] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[  195.202083] option: option_instat_callback: error -108
[  195.203115] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  195.203141] option 2-4:1.0: device disconnected
[  195.203206] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  195.203223] option 2-4:1.1: device disconnected
[  195.376258] usb 2-4: reset full speed USB device using ohci_hcd and address 3
[  195.565304] option 2-4:1.1: GSM modem (1-port) converter detected
[  195.565473] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[  195.574257] option 2-4:1.0: GSM modem (1-port) converter detected
[  195.574442] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[  195.605088] option: option_instat_callback: error -108
[  195.608515] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  195.608555] option 2-4:1.0: device disconnected
[  195.608668] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  195.608701] option 2-4:1.1: device disconnected
[  195.788048] usb 2-4: reset full speed USB device using ohci_hcd and address 3
[  195.989303] option 2-4:1.1: GSM modem (1-port) converter detected
[  195.989470] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[  195.998544] option 2-4:1.0: GSM modem (1-port) converter detected
[  195.998729] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[  196.022087] option: option_instat_callback: error -108
[  196.024609] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  196.024649] option 2-4:1.0: device disconnected
[  196.024768] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  196.024804] option 2-4:1.1: device disconnected
[  196.200045] usb 2-4: reset full speed USB device using ohci_hcd and address 3
[  196.401294] option 2-4:1.1: GSM modem (1-port) converter detected
[  196.401464] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[  196.410224] option 2-4:1.0: GSM modem (1-port) converter detected
[  196.410406] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[  197.491084] option: option_instat_callback: error -108
[  197.492923] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  197.492966] option 2-4:1.0: device disconnected
[  197.493092] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  197.493127] option 2-4:1.1: device disconnected
[  197.668080] usb 2-4: reset full speed USB device using ohci_hcd and address 3
[  197.869292] option 2-4:1.1: GSM modem (1-port) converter detected
[  197.869458] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[  197.878197] option 2-4:1.0: GSM modem (1-port) converter detected
[  197.878383] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
```

Than I ejected it from terminal (ejected sr1, if I got it right from this log), but still no use. As I clicked on edit connections at the connections icon next to the time&date thing, and clicked the mobile broadband tab and clicked add, the roll-down thing where the devices should be listed was still gray and it said some kind of "use these settings for any device" or something. Even if I created a connection this way with the proper settings it wouldn't connect or do anything.

After I physically removed the device I got this with dmesg:

```
[  748.704320] usb 2-4: USB disconnect, address 5
[  748.704521] option: option_instat_callback: error -108
[  748.704848] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  748.704886] option 2-4:1.0: device disconnected
[  748.705110] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  748.705142] option 2-4:1.1: device disconnected
```

Please tell me whether this info was somewhat helpful or should I do the whole thing again when I completed an update (somehow)?
Thanks in advance,
Viktor

---

### Post by GeorgeVita on 2010-01-26
Hi **viktorfulop**, looping attachment/disconnection of ttyUSBx ports was a [bug]("https://launchpad.net/bugs/446146") at initial kernel (LiveCD) of 9.10

Best way: update using wifi or ethernet connection

If you cannot get online, you can try to install a newer kernel manually. Our problem is that we are not sure if that problem is caused only from the kernel [bug #446146]("https://launchpad.net/bugs/446146")
On any linux machine you can download the 3 packages (**i386**) running the following script

```
#!/bin/sh
wget -c http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-17-generic_2.6.31-17.54_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.31-17_2.6.31-17.54_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.31-17-generic_2.6.31-17.54_i386.deb
```
(or run 3 'wget' commands in terminal, or use the links 'http://archi...' on any OS)

Copy these files to a directory on the pc 'to be updated' and use:
System > Administration > Synaptic Package Manager
from menu File > Add Downloaded Packages > point to that directory
and follow directions to install.
(more on this 'offline' method at '[Dial-up Redux]("http://ubuntuforums.org/showthread.php?t=1377619")' thread)

I hope above will work for you, as we are not sure that the reason is just the kernel...

Regards,
George

---

### Post by viktorfulop on 2010-02-06
Hi George,
thanks for the tips. It took me a while to find a connection with a cable but finally I managed to get one, and updated the whole thing, and voilá, both my wifi card and the mobile card are working now. It was then the kernel which produced these problems. The mobile card doesn't work when I plug it in, though, first I have to unmount it to be recognised as a modem, but that's the smallest problem to have... The thing that I don't understand is that both network cards worked with jaunty at first, without having to update anything or doing other 'errands'. Why did the kernel evolve in a 'negative' way then...?
Anyways, thanks for your help, I'm glad it works now.
Regards,
Viktor

---

