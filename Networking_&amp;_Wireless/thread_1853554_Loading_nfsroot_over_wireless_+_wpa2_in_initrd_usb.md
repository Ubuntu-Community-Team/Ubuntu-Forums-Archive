---
title: "Loading nfsroot over wireless + wpa2 in initrd usb boot"
date: 2011-10-02
forum: Networking &amp; Wireless
---

### Post by tobias_84 on 2011-10-02
Hi All!


I'm setting up a small diskless machine and I want it to load up over wireless.

I already have a computer running diskless over wired network and that works fine.

I have been trying to get a initrd-image that loads up the wireless from a usb-drive but can't get it work.


The minimal installation works fine loading b43 modules and depending modules, and acerhk and acer_acpi that is needed to activate the wireless soft button.

Running wpa_supplicant to connect over my wpa2 network also work.

But how do I get all this to work in the initrd image so I can load the root system over wireless.

I do know that it's not fast over wireless and it don't have to be.

---

### Post by tobias_84 on 2011-10-07
Well got it working now!

Made a custom initrd image and added wpa_supplicant and required libraries manually and got it to work.

Basic settings:

/etc/initramfs-tools/initramfs.conf
```

MODULES=most
BUSYBOX=y
BOOT=local
DEVICE=wlan0
NFSROOT=auto

```

/etc/initramfs-tools/modules
added:
```

acerhk 
acer_acpi 
rfkill 
mac80211 
input-polldev 
led-class 
ssb 
b43 

```

Made this file and chmod +x it.
/etc/initramfs-tools/scripts/nfs-top/wifi
```

PREREQ="udev"

prereqs()
{
        echo "$PREREQ"
}

case $1 in
# get pre-requisites
prereqs)
        prereqs
        exit 0
        ;;
esac


sleep 3
echo modprobing \o/
modprobe aes_i586
modprobe ecb
modprobe geode_aes
modprobe blkcipher
modprobe cfg80211
modprobe acerhk
modprobe acer_acpi
modprobe rfkill
modprobe mac80211
modprobe input-polldev
modprobe led-class
modprobe ssb
modprobe b43
echo sista!
echo 1 wirelessled
echo 1 > /proc/driver/acerhk/wirelessled
sleep 10

#/bin/loadkeys /etc/console/boottime.kmap.gz
#modprobe -Qb dm_crypt
#modprobe -Qb aes_i586
#modprobe -Qb sha256
if grep -q splash /proc/cmdline; then
    /bin/chvt 1
fi
sleep 3

if grep -q splash /proc/cmdline; then
       /sbin/usplash -c &
       sleep 1
fi

/sbin/wpa_supplicant -Dwext -iwlan0 -c /etc/wpa_supplicant.conf &
echo wpa_supplicant gjord
sleep 10
echo ip-confs
ipconfig wlan0 &

```


make your new initrd.img file

You can edit your initrd.img by extracting the file, make changes and pack it all up again.

Extract:
```

zcat initrd.img | cpio -i -d

```
Packing:
```

find . | cpio -o -H newc | gzip -9 > ../initrd.img

```


Some files I added:
```

/sbin/wpa_supplicant
/etc/wpa_supplicant.conf

```

```

/usr/lib $ ls -l
libcrypto.so.0.9.8
libdbus-1.so.3
libssl.so.0.9.8
libz.so.1

```

In the initrd image I did go into /scripts and moved the local file to local_org and copy nfs to local.

I created my USB stick whit extlinux package.


Well this is not a howto, just some hints if anyone else is trying this to.

Hit me whit some questions and I will try to answer them.

---

### Post by n1gp on 2012-11-07
Thanks for sharing this info, it was helpful.

I have been using Debian Live netboot for booting some touchscreen
wall mounted pc's that control my home automation setup.

They are wired ethernet and I wanted to try setting one up to connect
wirelessly.

I got it to work, but it has connectivity problems. I basically took their
initrd thats setup for nfs mounting of the rootfs and modified it to
boot the kernel and initrd from flash card, bring up wifi, then nfs mount
the rootfs.

It works, but it takes quite a while to load and boot using an 802.11g
network. And even then it gets a lot of "*NFS server* is not responding"
timeouts. It doesn't seem to be a signal problem as it still happens
sitting right next to the AP and the signal strength is reported as
strong.

I think I'll end up putting the rootfs on the flash card as well and just use
the wifi for the home automation server<->client communication.

Just thought I'd share this with you and if you have any ideas on improving
the timeout issue, I'd love to hear them.

---

### Post by wildmanne39 on 2012-11-07
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

