---
title: "Only dummy output available kernel 3.19"
date: 2015-08-25
forum: Multimedia Software
---

### Post by f_padia on 2015-08-25
Hi,

I have both the 3.19 and 4.10 kernel installed on my Ubuntu 15.04 installation on a Dell Inspiron 7348 laptop. I used to use the 4.1 kernel daily until recently for some reason the wifi stopped connecting to my home network. I went back to the 3.19 kernel and I found the sound doesnt work. All I see in the sound settings is Dummy output. In alsamixer I see 'this device does not have any controls...' Here are some details of my Alsa settings  [http://www.alsa-project.org/db/?f=2f45ce40186975a05f3b1a9e93810c5183906386](http://www.alsa-project.org/db/?f=2f45ce40186975a05f3b1a9e93810c5183906386)

Can anyone help diagnose what the problem is? I cant understand why the sound would work in one kernel but not another on the same system.

Thanks

---

### Post by Yellow Pasque on 2015-08-25
Does it help if you get rid of these lines you added?
```
snd_hda_intel: model=dell-s14
snd_hda_intel: model=dell-vostro-3500
```
Reboot after you delete/comment the lines.

---

### Post by f_padia on 2015-08-27
> **Temüjin said:**
> Does it help if you get rid of these lines you added?
```
snd_hda_intel: model=dell-s14
snd_hda_intel: model=dell-vostro-3500
```
Reboot after you delete/comment the lines.

I only added those lines after reading around and reading it as a possible solution. So sound wasnt working without the lines, unfortunately.

---

### Post by Yellow Pasque on 2015-08-27
You should still remove those lines. Your system uses a Realtek audio codec and those model names are for Sigmatel/IDT codecs.

If you need to use the latest audio module/driver, install [https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201508262147%7Eubuntu15.04.1_all.deb](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201508262147%7Eubuntu15.04.1_all.deb)

---

### Post by f_padia on 2015-08-28
> **Temüjin said:**
> You should still remove those lines. Your system uses a Realtek audio codec and those model names are for Sigmatel/IDT codecs.

If you need to use the latest audio module/driver, install [https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201508262147%7Eubuntu15.04.1_all.deb](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201508262147%7Eubuntu15.04.1_all.deb)


Removed the lines and installed the linked package and sound works again! Many many many many thanks!

---

