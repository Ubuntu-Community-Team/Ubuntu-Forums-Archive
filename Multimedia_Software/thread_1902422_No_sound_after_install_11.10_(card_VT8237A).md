---
title: "No sound after install 11.10 (card VT8237A)"
date: 2011-12-30
forum: Multimedia Software
---

### Post by ccesarjj on 2011-12-30
Hi,

I've just made a new install of Xubuntu 11.10 in an old PC. Everything seems to work fine, but I've got no sound. When I type **aplay -l** in a terminal the system indicates there are no soundcards installed. Using **lspci** I realized the actual audiocard installed is a VT8237A/VT8251. I tried reinstalling alsa-base and alsa-utils, but nothing happened. I tried compiling the ALSA-Drivers from scratch, but I wasn't successful.

Does anybody know how to get the sound working? Any help would be really appreciated.

Regards
CC

---

### Post by lidex on 2011-12-31
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by ccesarjj on 2011-12-31
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

Thanks, I got the following link for the output
[http://www.alsa-project.org/db/?f=f768b31482fda7dd50699614857d7bfe72615acd]("http://www.alsa-project.org/db/?f=f768b31482fda7dd50699614857d7bfe72615acd")

---

### Post by lidex on 2011-12-31
Looks like alsa is not installed properly. Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

Not sure if all these are present in xubuntu so may complain about it.

---

### Post by ccesarjj on 2012-01-02
I've reinstalled the packages, but the soundcard is still not recognized. I ran again the alsa-info-script and got the following output:
[http://www.alsa-project.org/db/?f=be4c02b8ebc387250a73d36143b7cd3ae436b3b9](http://www.alsa-project.org/db/?f=be4c02b8ebc387250a73d36143b7cd3ae436b3b9)

Any further recommendation?

---

### Post by lidex on 2012-01-03
> **ccesarjj said:**
> I've reinstalled the packages, but the soundcard is still not recognized. I ran again the alsa-info-script and got the following output:
[http://www.alsa-project.org/db/?f=be4c02b8ebc387250a73d36143b7cd3ae436b3b9](http://www.alsa-project.org/db/?f=be4c02b8ebc387250a73d36143b7cd3ae436b3b9)

Any further recommendation?

Try forcing the sound module:
```
sudo modprobe snd-hda-intel
```
Now check aplay:
```
aplay -l
```

In any event, would like to see MB info:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

Could be a kernel issue, try updating.
```
sudo apt-get update && sudo apt-get upgrade
```
```
sudo update-grub
```
Reboot.

---

### Post by saqwe on 2012-01-29
Hi I've got the same problem, no sound after update to 11.10

MSI Wind, with newest xubuntu and all updates

here's what the script gave me:
[http://www.alsa-project.org/db/?f=db8f3dc338a8db8097ec04697750ebbeb277ce05](http://www.alsa-project.org/db/?f=db8f3dc338a8db8097ec04697750ebbeb277ce05)

thank you

---

### Post by saqwe on 2012-02-08
> **saqwe said:**
> Hi I've got the same problem, no sound after update to 11.10

MSI Wind, with newest xubuntu and all updates

here's what the script gave me:
[http://www.alsa-project.org/db/?f=db8f3dc338a8db8097ec04697750ebbeb277ce05](http://www.alsa-project.org/db/?f=db8f3dc338a8db8097ec04697750ebbeb277ce05)

thank you

das problem war das nicht der hda-mixer sondern der pulseaduio-mixer gemuted war

---

