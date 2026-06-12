---
title: "SquashFS error: unable to read"
date: 2010-09-12
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ofir_k on 2010-09-12
Hello,

Last week I decided to install the latest development version of  10.10 (beta). I downloaded the netbook version, although I have a regular laptop, I want to test the new netbook gui.

Anyway, I downloaded ubuntu-10.10-beta-netbook-i386.iso and used the usb-creator tool to create a bootable usb.

As mentioned in the release notes, I chose not to use persistence storage (I never do, actually). I checked the MD5 sum of the iso, before creating the usb. I also checked the files created in the usb by going to the usb directory and using the command:
```
md5sum -c md5sum.txt | grep -v "OK$"
```
Nothing appeared which indicates that all files are OK.

I also checked the usb at the first menu after booting from the usb (the one with try ubuntu, install ubuntu, memory test etc).

Until now it seems that everything is fine. In addition to the above I also run a memory test which passed with no problems.

HOWEVER, I can't boot into Ubuntu using this, or any other usb stick (for all of them I did the checks from above!). Everytime I try to boot, I get the following errors:
> SQUASHFS error: Unable to read page, block 241fa7b2
SQUASHFS error: Unable to read fragment cache entry [241fa7b2] 
These message keeps repeating itself over and over again:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169298&stc=1&d=1284325398[/IMG]

Finally, I tried booting using the same usb(s) and the same test, on a different computer, but I got the same errors :(

I searched the forums, by using the search of this forums and by using google but it seems no body has this exact problem.

Any help will be appreciated! :)

---

### Post by jfernyhough on 2010-09-12
This is an error with the image (or if it's on a CD a problem with the burn). Redownload and check the checksum of the image.

---

### Post by ofir_k on 2010-09-12
I already downloaded the Iso image 3 times and also from 2 different Internet connections. I checked the images' MD5 sums and also checked the usb.

I think it is important to mention that I used the same usb stick to installed ubuntu 10.04 yesterday and with no problems _at all_.

since my last post I run another memtest and it passed. I also checked the desktop edition, but with no luck :-(

As far as I can see, it seems to be a bug in ubuntu. 

Any ideas?

---

### Post by jfernyhough on 2010-09-12
Weird.

Have you tried booting it from a CD or in a VM?

---

### Post by ezsit on 2010-09-12
> I think it is important to mention that I used the same usb stick to installed ubuntu 10.04 yesterday and with no problems at all.

since my last post I run another memtest and it passed. I also checked the desktop edition, but with no luck

As far as I can see, it seems to be a bug in ubuntu. 

Sounds like a fault with the usb stick. Try the CD or another stick. USB sticks can develop problems all the time. I've had several over the years become unusable.

---

### Post by ranch hand on 2010-09-12
Or booting directly from grub.  Must be in a root directory;
```

echo "Adding Mangy Moose ISO on sda10" >&2 
cat << EOF
menuentry "Mangy Moose ISO on /dev/sda10" {
loopback loop (hd0,10)/etc/aa/maverick-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/etc/aa/maverick-desktop-amd64.iso noprompt 
initrd (loop)/casper/initrd.lz
}
EOF

```
mine are in a directory I created /etc/aa you will need to edit that entry for your box and ISO if you want to try that.

That one, by the way, boots fine.

---

### Post by ofir_k on 2010-09-13
> **jfernyhough said:**
> Weird.

Have you tried booting it from a CD or in a VM?

From CD and a VM it works perfectly. I will try today to test it from another USB stick and report back here.

> Or booting directly from grub. Must be in a root directory;
Code:
echo "Adding Mangy Moose ISO on sda10" >&2 
cat << EOF
menuentry "Mangy Moose ISO on /dev/sda10" {
loopback loop (hd0,10)/etc/aa/maverick-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/etc/aa/maverick-desktop-amd64.iso noprompt 
initrd (loop)/casper/initrd.lz
}
EOF
mine are in a directory I created /etc/aa you will need to edit that entry for your box and ISO if you want to try that.

That one, by the way, boots fine.

Looks like an interesting solution. What I need to do with the commands you wrote above in order to make it runnable from grub2?

Thanks!

---

### Post by ranch hand on 2010-09-13
You just put it in the /etc/grub.d/40_custom file and;
```

sudo update-grub

```
It should boot stat to the desktop if every thing is right.

---

### Post by sbubba on 2010-09-21
@ranch hand: thanks for your trick, I've solved the problem of the boot from usb!

---

### Post by ofir_k on 2010-09-21
It took me sometime to find another USB stick.

I now used a 4GB SanDisk disk-on-key and it worked like a charm.

Thank you all for your help!

---

