---
title: "firmware AR9271"
date: 2011-02-24
forum: Networking &amp; Wireless
---

### Post by joecoolman on 2011-02-24
Hello, I'm very new in Ubuntu and Linux in general.
I have the TL-WN422G v2 antenna and I read I need (among other stuff) the firmware file in lib/firmware. I go to site of Linux and download the ar9271.fw but it's 0 byte (???). So, I download the raw file (50 Kb) and put it in my lib/firmware and I change the owner to root:root and restart my notebook. The comand iwconfig doesn't show the atheros driver (I downloaded the compatwirless and loaded), when the antenna is plugged. The command sudo lsmod | grep ath9k doesn't show me nothing.
What am I doing wrong? and what kind of file is .bin.part? how can load it ? :confused:

Any help will be appreciated

---

### Post by chili555 on 2011-02-24
If you can hook up the ethernet and get an internet connection, please do:```
sudo apt-get install linux-firmware
```Reboot and you should be all set.

If not, let's try to extract the raw file you said you have. What is its file extension? zip or tar.gz or what?

I think the driver that will load is ath9k_htc.

---

### Post by joecoolman on 2011-02-25
Hello Chili555

The raw file I´ve downloaded from [http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=tree](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=tree)
If you see, the extension of the raw file is (rare name).bin.part
What do I do with that file?

---

### Post by chili555 on 2011-02-25
I haven't the faintest idea, I am sorry to say. How about the attached?

Drag and drop it from a USB key to your desktop; right-click and select 'Extract Here.' Then, in a terminal, do:```
cd Desktop
sudo cp ar9271.fw /lib/firmware
sudo modprobe ath9k_htc
iwconfig
```

---

