---
title: "Need a driver for graphics card on a Sony Vaio SVE151J11M with Ubuntu"
date: 2013-09-27
forum: Multimedia Software
---

### Post by charles_davidson2 on 2013-09-27
I have installed Ubuntu on my Sony Vaio laptop today, it's a fairly new computer, 64 bit Sony Vaio SVE151J11M Intel i3-3110M 2.40GHz × 4, this computer definately has a graphics card in it. When I installed Ubuntu 12.04 LTS earlier today it said during installation that drivers could not be located for my graphics card. I have tried to locate a driver myself but I cannot do it; this is the first time I have used Linux in some years.

Now on the overview page in Ubuntu it says "Graphics Unknown", and I keep getting prompts which say "System Problem Identified Do you want to report the problem now?" on every boot up. Could someone explain in simple steps how I can locate/install an appropriate driver? Spent awhile trying to do this myself, just do not know how. Thank you

---

### Post by papibe on 2013-09-27
Hi charles_davidson2. Welcome to the forum ):P

Could you open a terminal, run this commands and post back its results?
```
lspci -nnk | grep -iA2 vga

lsmod | grep -iE 'nvidia|fglrx|radeon|nouveau|i9'
```
Regards.

---

### Post by charles_davidson2 on 2013-09-27
Hi, no problem.

a@SONY:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: Sony Corporation Device [104d:90ab]
    Kernel driver in use: i915
a@SONY:~$ lsmod | grep -iE 'nvidia|fglrx|radeon|nouveau|i9'
i915                  620571  2 
drm_kms_helper         49597  1 i915
drm                   287564  3 i915,drm_kms_helper
i2c_algo_bit           13564  1 i915
video                  19652  1 i915

---

### Post by papibe on 2013-09-27
Thanks.

You have an Intel integrated graphics card (3rd Gen Core processor Graphics Controller). The proper driver is installed, loaded and working: i915.

Everything looks OK.

Are you experiencing any problem with your graphics right now?

Regards.

---

### Post by charles_davidson2 on 2013-09-27
> **papibe said:**
> Thanks.

You have an Intel integrated graphics card (3rd Gen Core processor Graphics Controller). The proper driver is installed, loaded and working: i915.

Everything looks OK.

Are you experiencing any problem with your graphics right now?

Regards.

Ah, okay. I was messing around with it when I was waiting for you to reply, when I put that stuff in the terminal now I get this:

a@SONY:~$ lsmod | grep -iE 'nvidia|fglrx|radeon|nouveau|i9'
i915                  620571  2 
drm_kms_helper         49597  1 i915
drm                   287564  3 i915,drm_kms_helper
i2c_algo_bit           13564  1 i915
video                  19652  1 i915
a@SONY:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: Sony Corporation Device [104d:90ab]
    Kernel driver in use: i915

Some incorrect driver I don't need now? I'm still getting that damn prompt all the time on startup, that's what caused me to think there was a problem.

---

### Post by charles_davidson2 on 2013-09-27
Really sorry for making that worse. Would appreciate it if someone told me how to fix that (if required) and get rid of the damn prompt that keeps coming back.

---

### Post by papibe on 2013-09-27
I see.

You may try updating your driver for one a little more upstream.

Open a terminal and run this commands:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```
Then reboot.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by charles_davidson2 on 2013-09-27
> **papibe said:**
> I see.

You may try updating your driver for one a little more upstream.

Open a terminal and run this commands:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```
Then reboot.

Hope it helps. Let us know how it goes.
Regards.

I ran all that, the update command would not work, the upgrade one did work. After restarting I still have no problems with my graphics but the aforementioned prompt message keeps coming back and back. I will be all good once that thing is turned off.

---

### Post by Yellow Pasque on 2013-09-28
```
sudo apt-get install mesa-utils
```
[https://bugs.launchpad.net/ubuntu/+bug/946620](https://bugs.launchpad.net/ubuntu/+bug/946620)

---

### Post by charles_davidson2 on 2013-09-28
> **Temüjin said:**
> ```
sudo apt-get install mesa-utils
```
[https://bugs.launchpad.net/ubuntu/+bug/946620](https://bugs.launchpad.net/ubuntu/+bug/946620)

Thanks, I have ran this in terminal but after restarting I am still getting that prompt message. Any ideas? :confused:

---

### Post by Bucky Ball on 2013-09-28
*Thread moved to **Multimedia & Video**.*

---

### Post by Yellow Pasque on 2013-09-28
> Now on the overview page in Ubuntu it says "Graphics Unknown"
Is that still true after installing mesa-utils? If so, please show output of:
```
glxinfo
```

---

### Post by Yellow Pasque on 2013-09-28
Oh, and perhaps this may stop the prompt: [http://howtoubuntu.org/how-to-disable-apport-error-reporting-in-ubuntu#.UkctVbLPNZI](http://howtoubuntu.org/how-to-disable-apport-error-reporting-in-ubuntu#.UkctVbLPNZI)

---

### Post by charles_davidson2 on 2013-09-28
> **Temüjin said:**
> Is that still true after installing mesa-utils? If so, please show output of:
```
glxinfo
```

Yes, I ran the command you posted and it appeared to work, but the prompt continues.

Here is what that returns:

a@SONY:~$ glxinfo
name of display: :0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

---

### Post by charles_davidson2 on 2013-09-28
> **Temüjin said:**
> Oh, and perhaps this may stop the prompt: [http://howtoubuntu.org/how-to-disable-apport-error-reporting-in-ubuntu#.UkctVbLPNZI](http://howtoubuntu.org/how-to-disable-apport-error-reporting-in-ubuntu#.UkctVbLPNZI)

Thanks for that.

---

### Post by Yellow Pasque on 2013-09-28
> a@SONY:~$ glxinfo
name of display: :0
X Error of failed request: BadRequest (invalid request code or no such operation)
Major opcode of failed request: 153 (GLX)
Minor opcode of failed request: 19 (X_GLXQueryServerString)
Serial number of failed request: 12
Current serial number in output stream: 12 

Oh, well that's not good. Pastebin/attach your /var/log/Xorg.0.log

---

### Post by charles_davidson2 on 2013-09-28
> **Temüjin said:**
> Oh, well that's not good. Pastebin/attach your /var/log/Xorg.0.log

Yeah think I messed it up somewhat thanks for your help.

[http://pastebin.com/TCY3w1T0](http://pastebin.com/TCY3w1T0)

---

### Post by Yellow Pasque on 2013-09-28
```
[    22.610] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[    22.676] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    22.676]    compiled for 6.9.0, module version = 1.0.0
```
You installed the proprietary AMD GPU driver... for your intel GPU (but you're hardly the first one). The following commands should fix you up, though some of them will fail depending on how you installed the AMD driver. Just run all of them and reboot.
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx*
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo rm -rf /etc/ati
```

---

### Post by charles_davidson2 on 2013-09-28
> **Temüjin said:**
> ```
[    22.610] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[    22.676] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    22.676]    compiled for 6.9.0, module version = 1.0.0
```
You installed the proprietary AMD GPU driver... for your intel GPU (but you're hardly the first one). The following commands should fix you up, though some of them will fail depending on how you installed the AMD driver. Just run all of them and reboot.
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx*
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo rm -rf /etc/ati
```

Thank you great help.

---

