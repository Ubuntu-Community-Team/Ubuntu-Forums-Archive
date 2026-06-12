---
title: "auto mute doesn't work after upgrade to 14.04.2"
date: 2015-02-25
forum: Multimedia Software
---

### Post by oleg-secondary on 2015-02-25
Hi

I've upgraded  Enablement Stacks in Ubuntu 14.04.2 (using this instruction [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) )
And now I have a problem with a sound system. When I plug in headphones, sound is coming through both speakers and headphones. Does anyone know how to fix it and make speakers mute when the headphones are plugged?

---

### Post by Yellow Pasque on 2015-02-26
Give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by oleg-secondary on 2015-02-27
More info

---

### Post by Yellow Pasque on 2015-02-27
It looks like headphone jack sensing was intentionally disabled because some Gigabyte motherboards had an issue with it:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1248116](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1248116)
[https://github.com/torvalds/linux/commit/b2c53e206967d01fd4fb6dd525f89ae738beb2e6](https://github.com/torvalds/linux/commit/b2c53e206967d01fd4fb6dd525f89ae738beb2e6)

---

### Post by Yellow Pasque on 2015-02-27
So a possible workaround might be given by doing the opposite of: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1248116/comments/12](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1248116/comments/12)

```
gksu gedit /lib/firmware/hda-jack-detect.fw
```

Copy and paste the contents below into gedit, then save and quit gedit:
```
[codec]
0x10ec0887 0x1458a002 2

[hint]
jack_detect = yes
```

Now, run following command:
```
echo "options snd-hda-intel patch=hda-jack-detect.fw" | sudo tee -a /etc/modprobe.d/hda-jack-detect.conf
```

Reboot and see if automatic mute function has returned.

---

### Post by oleg-secondary on 2015-02-27
Still doesn't work. But looks like the answer is somewhere near.
My motherboard is GA-H77-DS3H

Thanks anyway

---

### Post by Yellow Pasque on 2015-02-27
Maybe early patching wasn't the right idea here.

Let's try this:
```
sudo su
cd /sys/class/sound/hwC0D0
echo "jack_detect = yes" | tee -a hints
echo 1 > reconfig
exit
```

Now test the headphone mute.

> My motherboard is GA-H77-DS3H
Yes, but the sound device has the same PCI ID (0x1458:0xa002) as the some other Gigabyte models.

---

### Post by oleg-secondary on 2015-02-28
*echo 1 > reconfig* returns error: device is busy

but if I check *hints* before writing to it, I can see that patch was applied:
```
/sys/class/sound/hwC0D2# cat hints 
jack_detect = yes
```

---

### Post by oleg-secondary on 2015-02-28
Looking through HD-Audio.txt gave me some workaround:
/etc/modprobe.d/hda-jack-detect.conf
```
options snd-hda-intel model=nofixup
```
It could break some other stuff, but for now it works without troubles

---

