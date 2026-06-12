---
title: "nvidia ion2 zbox 510D HDMI"
date: 2010-10-11
forum: Multimedia Software
---

### Post by unixtime on 2010-10-11
zbox 510D almost working out of the box with Ubuntu 10.10

Install/Upgrade Ubuntu 10.10

Install the nvidia drivers --> reboot

Open your fav. terminal
```

cd /etc/modprobe.d/ [ ENTER ]
sudo vi alsa-base.conf [ ENTER ] 

```
Add the following line to the file and save it.
```

options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2

```
Create a new file in the same directory /etc/modprobe.d/
```

sudo vi blacklist-nvidia.conf

```
Paste the following content
```

blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-96
blacklist nvidia-173
alias nvidia nvidia-current

```
Save and reboot

Good Luck!

---

### Post by snizzo92 on 2010-10-11
this make ubuntu use the nvidia graphic card?

---

### Post by unixtime on 2010-10-11
This will enable the HDMI sound output on ZOTAC ZBOX HD-ID11
Here is the spec for the device I'm using [http://zotac.com/index.php?option=com_wrapper&view=wrapper&Itemid=100083&lang=en]("http://zotac.com/index.php?option=com_wrapper&view=wrapper&Itemid=100083&lang=en")

So yes, the nvidia HDMI sound will pass-through the snd-hda-intel or the realtek device.

---

