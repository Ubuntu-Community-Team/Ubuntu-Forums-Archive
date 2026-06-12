---
title: "Installing Ubuntu Server onto USB"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by aidave on 2009-01-20
**Howto: Install Ubuntu Server without a CD Drive**

Hi, here is a little how-to guide I wrote.  Hope it helps.

**Creating the First USB Source Stick**

We could skip this first step if we have a working USB CD drive.  Ours wasnt recognized by our motherboard.  If you do have a CD drive, burn an ISO image of Ubuntu Server 8.04.1 and boot with that.  You can then skip to the next major step: "Creating the Second USB Target Stick".  You should probably use 8.04.2 now that it is out, so if you want, adjust this accordingly, but it was written for 8.04.1.

Using an external Linux computer, attach the first USB key.
Then run from the command line:
	
```

	sudo fdisk -l

```

To find your USB device name.  Should be &#8220;sdb&#8221; or something.  We will use &#8220;sdx&#8221; for our purposes, replace with the appropriate device name.


Format the first USB stick:

```

	sudo umount /dev/sdx1
	sudo fdisk /dev/sdx
		* type p to show the existing partition and d to delete it    
		* type p again to show any remaining partitions 
			(if partitions exist, repeat the previous step)    
		* type n to make a new partition    
		* type p for primary partition          
			o type 1 to make this the first partition          
			o hit enter to use the default 1st cylinder          
			o type +1G to set the partition size          
			o type a to make this partition active          
			o type 1 to select partition 1          
			o type t to change the partition filesystem          
			o type 6 to select the fat16 file 
		* type w to write the new partition table
	sudo umount /dev/sdx1
	sudo mkfs -t vfat /dev/sdx1

```

Create a directory for this install and download the proper files:

```

	mkdir usbboot
	cd usbboot
	wget http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/initrd.gz
	wget http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/vmlinuz

```

You will have to download the ISO image (ubuntu-8.04.1-server-i386.iso).  Copy the ISO image to "usbboot"

Make a bootable Linux server install.  

This will be our source USB to create a target USB stick.  It cannot be used as an actual server.  

```

	sudo mkdir -p /mnt/flash
	sudo mount -t vfat /dev/sdx1 /mnt/flash
	sudo syslinux -s /dev/sdx1
	sudo mkdir -p /mnt/iso
	sudo mount -o loop ubuntu-8.04.1-server-i386.iso /mnt/iso
	sudo cp -R /mnt/iso/isolinux/* /mnt/flash
	sudo mv /mnt/flash/isolinux.cfg /mnt/flash/syslinux.cfg
	sudo mkdir -p /mnt/flash/install
	sudo cp vmlinuz /mnt/flash/install
	sudo cp initrd.gz /mnt/flash/install
	sudo cp ubuntu-8.04.1-server-i386.iso /mnt/flash
	sudo install-mbr /dev/sdx
	sudo umount /mnt/flash
	sudo umount /mnt/iso

```

You will now have a bootable USB key.  The image can potentially be replaced with another Linux ISO, although you will need the right vmlinuz and initrd files for your distribution.

You will need to set the computer BIOS to allow for USB HD boot, and make sure the USB HD boot has proper priority.

You will then be able to install Ubuntu Server onto a hard drive or another USB key. Again, if you have a CDROM drive you don't need this guide.

---

### Post by aidave on 2009-01-20
Ooops, this was supposed to be in the Server forum.

I found that it was easy to install Ubuntu Desktop onto USB.  But for some reason the server wasnt so easy.  So here is a guide.  It is for 8.04.1 but can easily be switched to another ISO.

---

