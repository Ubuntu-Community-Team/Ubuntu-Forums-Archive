---
title: "ndiswrapper: wlan0 Gone After Reboot"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by nesquik on 2011-06-11
I removed my b43xx driver and installed ndiswrapper using this [guide]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

It worked fine, but after a reboot wlan0 was gone:
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

It's installed:
```
sudo ndiswrapper -l
bcmwl5a : driver installed
	device (14E4:4318) present (alternate driver: ssb)
```

and loaded:
```
lsmod | grep ndiswrapper
ndiswrapper           192828  0
```

Thanks for help.

---

### Post by westie457 on 2011-06-11
May I suggest you pliug in an athernet cable then re-install b43fwcutter and at the same time install firmware-b43-installer, then remove ndiswrapper. All of this is done in Synaptic. 

After that reboot and you should have wireless working again.

Good luck

---

### Post by nesquik on 2011-06-11
I need to use ndiswrapper because Ad-hoc is not working when using b43.

---

### Post by nesquik on 2011-06-11
```
$ cat /etc/modprobe.d/ndiswrapper.conf
alias pci:v000014E4d00004301sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004303sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004307sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004321sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv*sd*bc*sc*i* ndiswrapper
```

Shouldn't there be something like "alias wlan0 ndiswrapper"?

---

### Post by nesquik on 2011-06-11
Solved. ssb wasn't properly blacklisted. Since adding "blacklist ssb" to blacklist.conf doesn't work, I had to do this workaround:
```
$ cp /boot/initrd.img-`uname -r` somewheresafe
$ sudo update-initramfs -u
$ sudo reboot
```

---

