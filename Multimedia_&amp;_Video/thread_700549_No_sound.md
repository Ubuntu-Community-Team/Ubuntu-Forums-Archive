---
title: "No sound"
date: 2008-02-18
forum: Multimedia &amp; Video
---

### Post by AcLime on 2008-02-18
My ubuntu got no sound. When I try to type sudo alsaconf and alsamixer error:

```
zygimantas@zygimantas:~$ sudo alsaconf
[sudo] password for zygimantas:
sudo: alsaconf: command not found
zygimantas@zygimantas:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
zygimantas@zygimantas:~$ 
```

What's the problem. Please answer.:(

---

### Post by jan de beuker on 2008-02-19
If you type this command in a terminal

lspci

You get a list of the pci slots
Is your soundcard listed ?
Do you have a soundcard and onboard sound? 
Go to the BIOS and switch onboard sound of
Check if ther is a know problem with your souncard

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

Jan

---

