---
title: "Synaptic stuck while installing linux-image-2.6.35.2"
date: 2010-06-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2010-06-09
Hello,

My synaptic stuck while installing linux-image-2.6.35.2 at following stage.
> update-initramfs: Generating /boot/initrd.img-2.6.35-2-generic

I had to restart the system to close synaptic. I am now not able to use synaptic. It says to run dpkg --configure -a and here too i am stuck at above mentioned stage.

Thanks.

---

### Post by garvinrick4 on 2010-06-09
Have you tried to remove synaptic and reinstall with a clean one? If the first one does not work.
```
sudo apt-get -f install
```If package is still broken. You did try already with:dpkg --configure -a

Here is to remove and fetch new one.
```
sudo apt-get remove synaptic
``````
sudo apt-get clean
``````
sudo apt-get install synaptic
```

---

### Post by donniezazen on 2010-06-10
> **garvinrick4 said:**
> Have you tried to remove synaptic and reinstall with a clean one? If the first one does not work.
```
sudo apt-get -f install
```If package is still broken. You did try already with:dpkg --configure -a

Here is to remove and fetch new one.
```
sudo apt-get remove synaptic
``````
sudo apt-get clean
``````
sudo apt-get install synaptic
```

I am not able to run apt-get. I get the error that dpkg was interrupted please run dpkg --configure -a which freezes at the above mentioned error.

Thanks.

---

### Post by ranch hand on 2010-06-10
Try running;
```

sudo apt-get -f update

```
and then. if that updated your list;
[code]
sudo apt-get -f upgrade
[code]

---

### Post by seeker5528 on 2010-06-10
Try:

```
sudo dpkg --force-depends --force-remove-reinstreq --purge linux-image-2.6.35-2-generic
apt-get update
apt-get -f install
```

The packages linux-image and linux-image-generic are metapackages, so it is OK if they get removed.

If the above commands don't trigger the re-install of linux-image-2.6.35-2-generic then type to command:

```
sudo apt-get install linux-image-generic
```

If you still have one or more kernels install removing linux-image-2.6.35-2-generic should not be a big deal, if it is the only one installed you don't want to reboot without getting it re-installed again.

My best guess would be if you have already reboot since having this issue, you probably have an older kernel package still installed.

If in doubt you can always look in '/boot/' to see what initrd* files exist.
 
If there is still a failure while installing linux-image-2.6.35-2-generic, then you can try:

```
sudo dpkg --force-remove-reinstreq --purge linux-image-2.6.35-2-generic
```

Which, theoretically, should cause the metapackages to be removed in addition to linux-image-2.6.35-2-generic so you can see what other updates are available and get them installed before attempting to install the kernel again linux-image-generic again.

Later, Seeker

---

