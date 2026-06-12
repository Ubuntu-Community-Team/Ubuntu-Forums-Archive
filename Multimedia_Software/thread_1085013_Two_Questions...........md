---
title: "Two Questions.........."
date: 2009-03-02
forum: Multimedia Software
---

### Post by wbee on 2009-03-02
Hello,

I have a Soundblaster Audigy card installed,but it has no number. It's the plain vanilla one for about twenty dollars----that worked beautifully in windows.

I tried the "auto-detect" and it did nothing. Yes,I DID send a report to launchpad.

1. Is there a driver I can download?

---------------

I have an MSI TV ANYWHERE PLUS tv tuner card. If Ubuntu has detected it,it has fooled me so far.

2. Is there a driver I can download to use the tuner card with ubuntu?


---------------

Thank you.

wbee

---

### Post by cariboo on 2009-03-02
Open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C multimedia
```

This should  tell you whether there are drivers loaded for both devices.

I don't have an Audigy installed, as I have run out of available slots, but I do have an MSI TV@nywhere installed and working quite well, the tv tuner card is fairly old and I don't remember if it is a plus or not.

If TV tuner card is based on the Philips saa713X chipset, it is detected, but not correctly. I had to add the following to /etc/modprobe.d

```
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=17
```

copy the above and paste it into a text editor and save it as **saa7134**, then copy it to /etc/modprobe.d. cd into the directory where you saved the script the type:

```
sudo cp saa7134 /etc/modprobe.d/
```

Then reboot and your tuner card should work.

I have a directory called scripts to store reusable scripts, in my home directory that is on it's own partition, as I reinstall fairly often, running prerelease versions of Ubuntu.

Jim

---

### Post by wbee on 2009-03-03
Thank you.

---

### Post by markbuntu on 2009-03-03
For some reason the driver for the audigy cards is defaulted to digital output which disables the analog output. Go to the volume control and uncheck the digital/analog switch.

---

