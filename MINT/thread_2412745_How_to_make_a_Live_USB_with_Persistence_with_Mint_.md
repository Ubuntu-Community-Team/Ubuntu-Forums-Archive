---
title: "How to make a Live USB with Persistence with Mint 19?"
date: 2019-02-16
forum: MINT
---

### Post by tinker123 on 2019-02-16
How can I created a Mint 19 Live USB stick with persistence?

Can I do it with a USB thumb drive that is only 4gigs?

I've seen a lot of suggestions for how to do it using Windows tools, but I don't have windows.  I'm on a PC with Linux Mint 19.

I tried using this lone document using all linux tools, but UNetbootin kept hanging at 51%. ( I upped the suggested sizes to accommodate the Mint 19 ISO ).

[http://tuxtweaks.com/2014/03/create-linux-mint-persistent-live-usb/](http://tuxtweaks.com/2014/03/create-linux-mint-persistent-live-usb/)

Can anyone suggest other docs for doing this?

---

### Post by Redalien0304 on 2019-02-16
Try Pinguy [https://pinguyos.com/2018/04/pinguy-builder-for-buntu-17-04-17-10-18-04-using-ubiquity/](https://pinguyos.com/2018/04/pinguy-builder-for-buntu-17-04-17-10-18-04-using-ubiquity/)
There are a couple of tutorials, just Google them

---

### Post by tinker123 on 2019-02-16
> **Redalien0304 said:**
> Try Pinguy [https://pinguyos.com/2018/04/pinguy-builder-for-buntu-17-04-17-10-18-04-using-ubiquity/](https://pinguyos.com/2018/04/pinguy-builder-for-buntu-17-04-17-10-18-04-using-ubiquity/)
There are a couple of tutorials, just Google them


That link doesn't have anything related to my question and I have googled, a lot, and have only found out of date tutorials.

Thanks for posting back at least.

---

### Post by Frogs Hair on 2019-02-16
I have not tried this. 

[https://www.reddit.com/r/linuxmint/comments/93c16u/how_to_easily_create_a_persistent_linux_mint_usb/](https://www.reddit.com/r/linuxmint/comments/93c16u/how_to_easily_create_a_persistent_linux_mint_usb/)

---

### Post by yancek on 2019-02-16
If you are not having any luck with software meant to create a bootable/persistent usb, you could try doing it manually.  Use your current Mint to install Grub to the usb.  Make sure you understand device/partition naming conventions so you get the correct drive  The link below explains this under number 6 in the section via the Live CD terminal.  This will work from an installed system.  

[https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal](https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal)

Once you have done this, you need to manually create a grub.cfg file in the /boot/grub/directory from a template such as at tbe link below.

 [http://mirrors.ircam.fr/pub/crux/opt/2.8/grub2/grub.cfg.sample](http://mirrors.ircam.fr/pub/crux/opt/2.8/grub2/grub.cfg.sample)

Replace the example menuentries with a correct one for the Mint iso, example below.  You need to enter the exact name of the Mint iso and have the correct partition.  Then use whatever method (terminal, file manager) you want to copy the Mint iso to that partition on the usb.  While still in your installed Mint system, use GParted and unmount the partition to which you have copied the Mint iso, shrink it to just over the size of the data on the partition, then click the partition tab in GParted and select new and create a partition with the remaining space on the usb.  Label it casper-rw and format it with an ext filesystem.  When you boot the usb it should boot Mint and you should see the casper-rw partition under /media/mint and be able to create directories/files there.  With a 4GB drive, you won't be able to do much.  This process is a little more complicated than using unetbootin or similar software but it works. 

```
menuentry "Linux Mint Mate 19" {
    loopback loop (hd0,1)/linuxmint-19-mate-64bit-v2.iso
    linux (loop)/casper/vmlinuz  boot=casper iso-scan/filename=/linuxmint-19-mate-64bit-v2.iso quiet splash --
    initrd (loop)/casper/initrd.lz
}
```

One advantage of this process is that you can simply copy more iso files of different Linux systems and simply add an entry in grub.cfg to boot it and the casper-rw partition will be available from the other OS's.  Not really applicable in your situation with such as small usb.  Good luck.

---

### Post by C.S.Cameron on 2019-02-16
@Yancek: The OP asked for persistence, easy enough to modify your menuentry adding persistence thus: ... quiet splash **persistence** --
A partition labeled casper-rw can be created if more than 4GB is needed, or a casper-rw file can be created using dd if less than 4GB is needed.

          sudo dd if=/dev/zero of=casper-rw bs=1M count=512

          sudo mkfs.ext3 -L casper-rw -F casper-rw

Where 512 is the size of the persistence file.

Place the casper-rw file in the root of the USB.

---

### Post by kurt18947 on 2019-02-17
What do you want the newly created USB to do? The reason I ask is that it's possible to install a fully functional Mint install onto a USB drive, I have one. This USB cannot be used to install to another machine and I don't think it can be used to manipulate/repair an install using Gparted on another drive like a live USB can. It certainly will save anything created or downloaded though. It depends on what functions you desire.

---

