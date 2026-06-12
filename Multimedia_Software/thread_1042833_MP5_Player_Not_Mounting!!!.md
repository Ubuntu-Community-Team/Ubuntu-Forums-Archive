---
title: "MP5 Player Not Mounting!!!"
date: 2009-01-18
forum: Multimedia Software
---

### Post by Zetheroo on 2009-01-18
I am running Ubuntu Hardy and just got an MP5 player. When I plug it in via USB the device turns on and there is a USB logo on the screen, however no volume mounts and a few seconds later the device turns off and turns on again. This continues indefinitely.

The volume format is FAT32.

Here is the dmesg output:

  >  1.
      [ 2492.801003] usb 6-3: new high speed USB device using ehci_hcd and address 3
   2.
      [ 2493.021632] usb 6-3: configuration #1 chosen from 1 choice
   3.
      [ 2512.990692] usbcore: registered new interface driver libusual
   4.
      [ 2513.010434] Initializing USB Mass Storage driver...
   5.
      [ 2513.011577] scsi2 : SCSI emulation for USB Mass Storage devices
   6.
      [ 2513.015677] usbcore: registered new interface driver usb-storage
   7.
      [ 2513.015682] USB Mass Storage support registered.
   8.
      [ 2513.015798] usb-storage: device found at 3
   9.
      [ 2513.015801] usb-storage: waiting for device to settle before scanning
  10.
      [ 2517.610799] usb-storage: device scan complete
  11.
      [ 2517.611218] scsi 2:0:0:0: Direct-Access     Ingenic  JzSoc USB-DISK        PQ: 0 ANSI: 0
  12.
      [ 2517.611960] scsi 2:0:0:1: Direct-Access     Ingenic  JzSoc USB-DISK        PQ: 0 ANSI: 0
  13.
      [ 2517.618244] sd 2:0:0:0: [sdb] 3960832 512-byte hardware sectors (2028 MB)
  14.
      [ 2517.618883] sd 2:0:0:0: [sdb] Write Protect is off
  15.
      [ 2517.618888] sd 2:0:0:0: [sdb] Mode Sense: 00 06 00 00
  16.
      [ 2517.618891] sd 2:0:0:0: [sdb] Assuming drive cache: write through
  17.
      [ 2517.621007] sd 2:0:0:0: [sdb] 3960832 512-byte hardware sectors (2028 MB)
  18.
      [ 2517.621637] sd 2:0:0:0: [sdb] Write Protect is off
  19.
      [ 2517.621642] sd 2:0:0:0: [sdb] Mode Sense: 00 06 00 00
  20.
      [ 2517.621645] sd 2:0:0:0: [sdb] Assuming drive cache: write through
  21.
      [ 2517.621649]  sdb:<6>usb 6-3: USB disconnect, address 3
  22.
      [ 2517.800573] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
  23.
      [ 2517.800581] end_request: I/O error, dev sdb, sector 0
  24.
      [ 2517.800586] Buffer I/O error on device sdb, logical block 0
  25.
      [ 2517.800625] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
  26.
      [ 2517.800629] end_request: I/O error, dev sdb, sector 0
  27.
      [ 2517.800632] Buffer I/O error on device sdb, logical block 0
  28.
      [ 2517.800653] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
  29.
      [ 2517.800658] end_request: I/O error, dev sdb, sector 0
  30.
      [ 2517.800660] Buffer I/O error on device sdb, logical block 0
  31.
      [ 2517.800678] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
  32.
      [ 2517.800683] end_request: I/O error, dev sdb, sector 0
  33.
      [ 2517.800686] Buffer I/O error on device sdb, logical block 0
  34.
      [ 2517.800703] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
  35.
      [ 2517.800708] end_request: I/O error, dev sdb, sector 0
  36.
      [ 2517.800710] Buffer I/O error on device sdb, logical block 0
  37.
      [ 2517.800718] ldm_validate_partition_table(): Disk read failed.
  38.
      [ 2517.800731] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
  39.
      [ 2517.800735] end_request: I/O error, dev sdb, sector 0
  40.
      [ 2517.800738] Buffer I/O error on device sdb, logical block 0
  41.
      [ 2517.800754] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
  42.
      [ 2517.800759] end_request: I/O error, dev sdb, sector 0
  43.
      [ 2517.800761] Buffer I/O error on device sdb, logical block 0
  44.
      [ 2517.800778] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
  45.
      [ 2517.800782] end_request: I/O error, dev sdb, sector 0
  46.
      [ 2517.800785] Buffer I/O error on device sdb, logical block 0
  47.
      [ 2517.800837] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
  48.
      [ 2517.800842] end_request: I/O error, dev sdb, sector 0
  49.
      [ 2517.800845] Buffer I/O error on device sdb, logical block 0
  50.
      [ 2517.800853] Dev sdb: unable to read RDB block 0
  51.
      [ 2517.800867] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
  52.
      [ 2517.800872] end_request: I/O error, dev sdb, sector 0
  53.
      [ 2517.800875] Buffer I/O error on device sdb, logical block 0
  54.
      [ 2517.800891] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
  55.
      [ 2517.800896] end_request: I/O error, dev sdb, sector 0
  56.
      [ 2517.800917] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
  57.
      [ 2517.800922] end_request: I/O error, dev sdb, sector 24
  58.
      [ 2517.800938] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
  59.
      [ 2517.800942] end_request: I/O error, dev sdb, sector 24
  60.
      [ 2517.800959] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
  61.
      [ 2517.800964] end_request: I/O error, dev sdb, sector 0
  62.
      [ 2517.800981] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
  63.
      [ 2517.800985] end_request: I/O error, dev sdb, sector 0
  64.
      [ 2517.800992]  unable to read partition table
  65.
      [ 2517.801063] sd 2:0:0:0: [sdb] Attached SCSI removable disk
  66.
      [ 2517.801119] sd 2:0:0:0: Attached scsi generic sg2 type 0
  67.
      [ 2517.807992] sd 2:0:0:1: [sdc] READ CAPACITY failed
  68.
      [ 2517.807996] sd 2:0:0:1: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
  69.
      [ 2517.808000] sd 2:0:0:1: [sdc] Sense not available.
  70.
      [ 2517.808013] sd 2:0:0:1: [sdc] Write Protect is off
  71.
      [ 2517.808017] sd 2:0:0:1: [sdc] Mode Sense: 00 00 00 00
  72.
      [ 2517.808019] sd 2:0:0:1: [sdc] Assuming drive cache: write through
  73.
      [ 2517.808075] sd 2:0:0:1: [sdc] Attached SCSI removable disk
  74.
      [ 2517.808121] sd 2:0:0:1: Attached scsi generic sg3 type 0

---

### Post by Fingaluna on 2009-03-07
Zetheroo - I have the same issue with my player in Mandriva, although, once in a while I have seen the player mount as "Vfat"... I was even able to transfer some files onto it once or twice, but cannot seem to get it to behave anymore... I can get it to work well in windows, but can't get it to play nice with Either Mandriva or Xubuntu.

My player shows the following ID in WinXP: Ingenic JzSOC USB-DISK USB Device.

A few notes that might help you a little:
In Windows, the only way the player will mount is if I have the power switch on the player set to "OFF".
Here is some info on the audio setup for the player:
[http://mp4nation.net/blog/2009/02/improve-you-vx747-vx757-vx767-etc-jz47xx-chipset-players-audio/]("http://mp4nation.net/blog/2009/02/improve-you-vx747-vx757-vx767-etc-jz47xx-chipset-players-audio/")
Here is some technical info on the processor used on the device: [http://www.ingenic.cn/eng/productServ/App/JZ4740/pfCustomPage.aspx]("http://www.ingenic.cn/eng/productServ/App/JZ4740/pfCustomPage.aspx") You will note that it does say that it supports Linux...
Here is a post that shows how to make the Onda VX747 (uses the JZ4740 chip) run linux. Too bad it's all in Chinese! [http://www.ondabbs.cn/thread-35439-1-1.html]("http://www.ondabbs.cn/thread-35439-1-1.html")
Hope you can figure it out!
Cheers!

---

### Post by mulan on 2009-04-29
have you gotten anywhere with it?

my friend just bought the vx747 and it seems it starts shows the usb logo but she can't see it mounted. she uses xubuntu 9.04 so maybee thats one step forward that it doesnt power on and off. seems sad if it takes to install linux on the onda to get your computer recognising it.

Is it possible it mount but just doesnt show?

---

### Post by muhammadg on 2009-08-13
i have same problem

---

### Post by mulan on 2009-08-13
I dont know if it helps, but the other day when i tried my girlfriends onda on my computer an Packard Bell with xubuntu 9.04, it worked without any problem!

---

### Post by kvarley on 2010-04-26
Fixed! Onda VX747

Thank ali1234 over at #ubuntu-uk for this! - ali helped diagnose my problem!

Plug in player.

Open terminal:

> sudo apt-get install gparted

> sudo gparted

Select your player from the list of media, delete the partition and create a fat32 one in its place. It may ask you to assign partition tables, if so follow the instructions and use the msdos default one.

Apply the changes.

Create the folders for content on your new partition: FLASH MUSIC RECORD TXT VIDEO

Your player should now work - It may freeze when syncing, just wait before you unplug it after transfers and unmount safely.

Enjoy.

---

