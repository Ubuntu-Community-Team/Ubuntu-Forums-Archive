---
title: "HVR 950Q install problems"
date: 2010-01-02
forum: Multimedia Software
---

### Post by drive_guy on 2010-01-02
I am running Mythbuntu 9.10 with Karmic Koala.

I have read the other posts about getting the Hauppauge HVR-950Q working and they are not working for me.  Here is the output from /var/log/dmesg.  I think the problem is something with xc5000 because of this line "xc5000: Unknown parameter `#avoid'"

Any help would be greatly appreciated.  I have been working all year (2 days) on this.

```
[   10.080573] tveeprom 0-0050: Hauppauge model 72001, rev B3F0, serial# 6097319
[   10.080577] tveeprom 0-0050: MAC address is 00-0D-FE-5D-09-A7
[   10.080580] tveeprom 0-0050: tuner model is Xceive XC5000 (idx 150, type 76)
[   10.080583] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   10.080586] tveeprom 0-0050: audio processor is AU8522 (idx 44)
[   10.080588] tveeprom 0-0050: decoder processor is AU8522 (idx 42)
[   10.080590] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter
[   10.080593] hauppauge_eeprom: hauppauge eeprom: model=72001
[   10.107228] au8522 0-0047: creating new instance
[   10.107230] au8522_decoder creating new instance...
[   10.134535]   alloc irq_desc for 22 on node -1
[   10.134538]   alloc kstat_irqs on node -1
[   10.134544] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.134571] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.188574] tuner 0-0061: chip found @ 0xc2 (au0828)
[   10.524935] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   10.684639] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   10.684713] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   10.684759] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   10.684808] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   10.684857] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   10.684905] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   10.684952] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   10.893373] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   10.893376] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   10.893558] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   11.018349] xc5000: Unknown parameter `#avoid'
[   11.028795] DVB: Unable to find symbol xc5000_attach()
[   11.029082] au8522 0-0047: attaching existing instance
[   11.042871] xc5000: Unknown parameter `#avoid'
[   11.052762] DVB: Unable to find symbol xc5000_attach()
[   11.052765] DVB: registering new adapter (au0828)
[   11.052768] DVB: registering adapter 0 frontend 0 (Auvitek AU8522 QAM/8VSB Frontend)...
[   11.052972] Registered device AU0828 [Hauppauge HVR950Q]
[   11.107925] usbcore: registered new interface driver snd-usb-audio
[   11.108917] usbcore: registered new interface driver au0828

```

---

### Post by joiningtheherd on 2010-01-06
Just edit the file which halts the firmware reload.  Place #avoid ... on a new line.  Udev and modprobe do not support mid-line commenting.

---

### Post by drive_guy on 2010-01-10
Do you have any more information about how to do that?

---

### Post by iondiode on 2010-01-13
I'm not positive ,but based on other threads I've seen, there is a file that can be created in /etc/modules.d called xc5000.something

one line in that file has a comment at the end of the line that the parser isn't liking.

Open that file in a text editor and remove the # avoid and everything after it on that line.

Then reboot and that error message should be gone

---

### Post by markackerman8@gmail.com on 2010-03-20
Thanks it worked for me after grappling with it for 2 days ... THANKS!

It fixed this error as well! 

linux-26yx:~ # modprobe xc5000 no_poweroff=1
FATAL: Error inserting xc5000 (/lib/modules/2.6.31.12-0.1-desktop/kernel/drivers/media/common/tuners/xc5000.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

