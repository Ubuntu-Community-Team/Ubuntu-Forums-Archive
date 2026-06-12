---
title: "No sound  10.04"
date: 2010-04-29
forum: Multimedia Software
---

### Post by retro89 on 2010-04-29
I cant seem to get the sound working and when I click on perference then sounds and go to the output selection it has only dummy output as a option.

---

### Post by Yellow Pasque on 2010-04-29
What card do you have?
```
sudo lshw -C multimedia
```

---

### Post by lidex on 2010-04-29
What is the output of this command:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```
Terminal="Applications->Accessories->Terminal"
Did you just upgrade?
Try this:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```

Edit: One other thing. On an upgrade remnants of old config files can cause problems so do 'Part A' here:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by neotifa on 2010-04-29
Do you have the sound and video codecs installed?

---

