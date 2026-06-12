---
title: "Another ADMTek 8511 ethernet nic problem"
date: 2005-03-06
forum: Networking &amp; Wireless
---

### Post by Len on 2005-03-06
[quote="alastair"]Have a shell open and type :

sudo tail -f /var/log/syslog

Then plug in the USB/ethernet device - and see if the kernel prints out any information.[/quote]

If I leave out the device at boot (the pegasus driver is loaded at boot), nothing happens.

[quote="alastair"]If it is plugged in at boot, check the output of "dmesg" and look for USB or ethernet messages that might relate.[/quote]
```
usbcore: registered new driver hub
drivers/usb/net/pegasus.c: v0.5.12 (2003/06/06):Pegasus/Pegasus II USB Ethernet driver
usbcore: registered new driver pegasus
```
Note that I told ubuntu to load that driver at boot.

> ifconfig -a
Displays lo and sit0 only, like the thing is not connected or broken...

BUT:
[quote="len"]
It isn't even detected at the install! Fedora Core DID work perfectly with it using the pegasus driver.
When I read another topic about using modprobe when installing I did a reinstall.
I typed "modprobe pegasus" when booted from the CD, and let the installer detect the network card. This time it DID detect it, the lights on the thing went on, and the router reported that the laptop was connected.

After the install however, the thing didn't work anymore (no lights, not mentioned in ifconfig -a, nothing), so I added "pegasus" to the modules list in /etc/modules.[/quote]

And that didn't make any difference. Makes you think...

I've installed Ubuntu on a 600 MHz laptop with 64 MB (don't laugh) RAM, everything works perfectly but not that ADMTek ADM8511 USB to Ethernet adapter. I'm 100% sure that it is a 8511 chipset, I'm also 100% sure it has to work with the pegasus driver since it worked in FC3.
The only difference I see is that the driver is called "pegasus.o" in FC3, and "pegasus.c" in Ubuntu.

---

### Post by alastair on 2005-03-07
This looks a bit less optimistic than the previous issue - the driver's loaded but doesn't seem to give you a device (eth0).

I assume there is nothing else in /var/log/syslog that might point to any problem with this?

What version of Ubuntu?

What about (with device plugged in) :

cat /proc/bus/usb/devices

---

### Post by Len on 2005-03-07
I'm using the "Warty Warthog", 4.10 (that's what the CD says :).

cat /proc/bus/usb/devices gives me "cat: unknown file or directory"
After closer inspection it seems that the /proc/bus/usb/ directory is empty (ls -a). That isn't good is it?
Strange thing is: during the install the thing wasn't detected as well, and when I loaded the pegasus driver, the thing did nothing. Running the autodetect AFTER loading the pegasus driver made the thing turn on and work! I've run the autodetect in the install 5 times without loading the pegasus driver, and then it doesn't detect the device. I wish there was a way to run that "autodetect" after the install.

I just copied the syslog file to a disk using 'cp' and opened it on my Macintosh, but the file is 220 KB plain text, maybe not a good idea to post it here. I've put my webserver on, you can get it from [my computer](http://80.57.100.194/syslog.txt).

Thanks for your time again!

---

### Post by alastair on 2005-03-07
This is quite hard. Your system loads stuff in a different order to mine.

I am not sure about /proc/bus/usb/ - mine gets a "usbfs" filesystem :

usbfs on /proc/bus/usb type usbfs (rw)

Mounted from /etc/init.d/mountvirtfs - but this seems to depend on the directory being present - so maybe a module thing.

What does :

lsmod

say?

Also :

lspci -v

Your pegasus driver is loaded very early - perhaps too early? Is it loaded (lsmod)?

If it is - perhaps try and remove :

sudo rmmod pegasus

Then re-insert :

sudo modprobe pegasus

and watch the logs as you do this.

In your syslog :

uhci_hcd 0000:00:07.2: request interrupt 7 failed

is worrying - perhaps an interrupt problem? Perhaps I would be tempted to also try a boot using :

acpi=off

as a kernel arg (ESC at grub, "e" to edit kernel args, "b" to boot)/

Hope some of that helps.

---

### Post by Len on 2005-03-07
Wow, that are a lot of things to try! I'm glad there is still hope getting the thing to work, and I'm happy you noticed that error in my syslog :).

I'll work down the list, my laptop is next to this computer:

- lsmod:
```
Module                  Size  Used by
nls_cp437               6016  1
isofs                  33976  1
udf                    79876  0
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
ipv6                  230020  8
ds                     17796  4
button                  6936  0
ac                      5132  0
battery                 9740  0
ohci_hcd               19460  0
ehci_hcd               27780  0
yenta_socket           19328  0
pcmcia_core            63156  2 ds,yenta_socket
uhci_hcd               29328  0
snd_intel8x0           33068  4
snd_ac97_codec         59268  1 snd_intel8x0
snd_pcm_oss            48168  0
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85540  2 snd_intel8x0,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  2 snd_intel8x0,snd_pcm
snd_mpu401_uart         7296  1 snd_intel8x0
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  1 snd_rawmidi
snd                    50660  13 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mix er_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  3 snd
floppy                 54996  0
irtty_sir               8320  0
sir_dev                18092  1 irtty_sir
irda                  167360  2 irtty_sir,sir_dev
crc_ccitt               2432  1 irda
pcspkr                  3816  0
rtc                    12216  0
analog                 10784  0
gameport                4736  2 snd_intel8x0,analog
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
tsdev                   7168  0
evdev                   9088  0
ide_cd                 38276  1
cdrom                  35872  1 ide_cd
mousedev               10124  1
psmouse                17800  0
pegasus                22152  0
usbcore               104292  4 ohci_hcd,ehci_hcd,uhci_hcd,pegasus
ext3                  109544  1
jbd                    54552  1 ext3
ide_generic             1664  0
piix                   12576  1
ide_disk               16768  3
ide_core              125272  4 ide_cd,ide_generic,piix,ide_disk
unix                   25904  628
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

```
Pegasus is there. It doesn't mention any device next to it unfortunately.

- lspci -v:
```
0000:00:00.0 Host bridge: Intel Corp. 82440MX Host Bridge (rev 01)
0000:00:00.1 Multimedia audio controller: Intel Corp. 82440MX AC'97 Audio Controller0000:00:02.0 VGA compatible controller: Silicon Motion, Inc. SM720 Lynx3DM (rev b1)
0000:00:07.0 ISA bridge: Intel Corp. 82440MX ISA Bridge (rev 01)
0000:00:07.1 IDE interface: Intel Corp. 82440MX EIDE Controller
0000:00:07.2 USB Controller: Intel Corp. 82440MX USB Universal Host Controller
0000:00:07.3 Bridge: Intel Corp. 82440MX Power Management Controller
0000:00:09.0 Communication controller: Ambient Technologies Inc HaM controllerless modem (rev 02)
0000:00:0a.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
0000:00:0a.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)

```
Nothing about the device, but my USB controller is there (fortunately).

- rmmod pegasus -> modprobe pegasus with tail -f /var/log/syslog open in another root terminal:
```
Mar  7 23:11:09 localhost kernel: usbcore: deregistering driver pegasus
Mar  7 23:11:19 localhost kernel: drivers/usb/net/pegasus.c: v0.5.12 (2003/06/06):Pegasus/Pegasus II USB Ethernet driver
Mar  7 23:11:19 localhost kernel: usbcore: registered new driver pegasus

```
Looks OK to me, well, at least no error.

- Booting with an acpi=off argument:

Yahoooo! The thing turns on at boot!!
Now: Computer -> System configuration -> Network. Add. Next, next, DHCP, Finish, works!

But, what is that acpi thing, do I need it for something or is it just something implemented to annoy people? Wait a second: the battery meter of my laptop now reports nothing (0%), guess that's where it is for, powermanagement. Hmm...

Anyway, this is a giant step forward. Thanks you very much :D !
I guess I have to start a new topic about the acpi <-> usb hardware conflict now ;), but at least I can install and update a lot of software now!

---

### Post by alastair on 2005-03-07
Well, getting somewhere at least! ACPI is "Advanced Configuration and Power Interface" - some of it replaces APM (power management) but it is much more than that, and more complex.

See : 

[http://acpi.sourceforge.net/](http://acpi.sourceforge.net/)
[http://marc.theaimsgroup.com/?l=acpi4linux&r=1&w=2](http://marc.theaimsgroup.com/?l=acpi4linux&r=1&w=2)

This is ongoing and complex.

It (sort of) looked like an interrupt issue - and ACPI can manage (route) interrupts. I think you can turn off subsections of ACPI (not just the whole lot) - and perhaps just one part is causing your problems e.g. the arg.

pci=routeirq

(stops ACPI from doing IRQ routing - at least on kernel 2.6.10-4-386)

I think your problem might be minimised by the above - if not, the next Ubuntu release (i.e. kernel update) might help a lot. Things move fast ...

Cheers.

---

### Post by Len on 2005-03-07
Well, I'm currently updating the kernel and an additional 100 MB of packages, so maybe the problem is just solved after that. Fedora didn't have the problem, so I guess chances are high an updated Ubuntu works OK as well.

Fedora runs very fine on 64 MB RAM by the way, the Gimp runs perfectly well (Ubuntu uses 30 MB of the 64, swapping the rest). Fedora was a disaster on my old laptop ;-).
I ordered an additional 128 MB RAM though, should speed up things even more.

UPDATE:
Still the same problem with the new kernel.

pci=routeirq results in "PCI: routeirq unknown option" at boot. O well, if I put my laptop off power (so if I need to see my battery status) I don't have an internet cable anyway, so I don't mind switching arguments.

I want to try any suggestion though.

Thanks again for the solution!

EDIT: I never use the serial ports on my laptop. Would it help to turn them off in the BIOS instead of assigning an IRQ to them?

---

### Post by alastair on 2005-03-07
Not sure about the serial ports - I doubt it. Try it though.

The "pci=routeirq" might only be on some newer kernels ... not sure (I am on 2.6.10).  In fact, it might be wrong anyway.

Looking at :

<linux source>/Documentation/kernel-parameters.txt

pci=noacpi

might be better.

Might be worth installing kernel source (or docs) and looking at the "pci=option" possibilities.

Or asking on the linux-usb list (or ACPI list).

---

### Post by Len on 2005-03-07
You won't believe it, but I disabled the serial, parallel and infrared port and everything works fine!

Those were set to "Auto". I can choose from "Auto", "User", "OS" and "Disabled". Maybe if I set them to "OS" everything goes fine as well, since Linux can then assign an IRQ to them itself? I'll try :).

I'm using kernel 2.6.8.

EDIT: Oops, "auto" is the same as "OS". I have set those IRQ adresses manually, and the same problem occurs again.

I wonder why the "IRQ" is invented. Macintoshes seem to never have had them, I have had 14 of them and always put them full with hardware. No BIOS, no IRQs, no problems (except for that @$)(* SCSI termination).
O well, things are working fine now without the useless serial, infrared and parallel ports, and Ubuntu is a very friendly system, so I do not complain!

I wonder, really wonder how Fedora could set the IRQs right. Maybe it is using a newer kernel? I'll report back on this topic when the new Ubuntu release is out.

---

