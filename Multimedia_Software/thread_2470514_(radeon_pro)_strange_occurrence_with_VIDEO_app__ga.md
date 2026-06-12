---
title: "(radeon_pro) strange occurrence with VIDEO app / garbled image"
date: 2022-01-02
forum: Multimedia Software
---

### Post by csae2608 on 2022-01-02
Hello,

i have noticed an occurrence,

that a file that would previously play normally in VIDEO app (Ubuntu 18.04)
after installation of Radeon Pro Drivers from here

[https://www.amd.com/en/support/professional-graphics/radeon-pro/radeon-pro-wx-x100-series/radeon-pro-wx-2100](https://www.amd.com/en/support/professional-graphics/radeon-pro/radeon-pro-wx-x100-series/radeon-pro-wx-2100)


would give a garbled image upon playback with the same VIDEO app.

Playback with other players (mpv, vlc) seems to function normally.


here is a short clip that illustrates the garbled video, maybe someone can recongize the issue

[https://streamable.com/gpjqp3](https://streamable.com/gpjqp3)


What am i missing?


Thanks!

---

### Post by KBar on 2022-01-02
I don't know what's wrong exactly but I'd recommend letting Ubuntu autoinstall drivers. 
```
sudo ubuntu-drivers autoinstall
```

---

### Post by csae2608 on 2022-01-02
yes, i did that with nvidia card before, but doesnt seem to function for this radeon pro
> sudo ubuntu-drivers autoinstall
No drivers found for installation.



---

### Post by KBar on 2022-01-02
I see.

Could you try reinstalling **totem**? If that doesn't help, try installing the *gnome-codec-install* package.

---

### Post by csae2608 on 2022-01-02
> **KBar said:**
> I see.

Could you try reinstalling **totem**? If that doesn't help, try installing the *gnome-codec-install* package.

reinstalling totem would not fix,
gnome-codec-install would result

```
 sudo apt install gnome-codec-install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'sessioninstaller' instead of 'gnome-codec-install'
The following packages were automatically installed and are no longer required:
  gnome-software-common libappstream-glib8
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  app-install-data
[B]The following packages will be REMOVED:
  gnome-software gnome-software-plugin-snap ubuntu-software[/B]
The following NEW packages will be installed:
  app-install-data sessioninstaller
0 upgraded, 2 newly installed, 3 to remove and 0 not upgraded.
Need to get 15,1 MB of archives.
After this operation, 43,7 MB of additional disk space will be used.
Do you want to continue? [Y/n] n


```

so i rather avoided it.

---

### Post by KBar on 2022-01-02
How about this?

```
sudo apt-get update && apt-get install --install-suggests totem
```

---

### Post by csae2608 on 2022-01-03
```
sudo apt-get install --install-suggests totem
totem is already the newest version (3.26.0-0ubuntu6.2).

```

---

### Post by slooksterpsv on 2022-01-07
If you run totem from the terminal, you should see some output regarding what's happening. However, I anticipate that the video is garbled due to a driver glitch. Do you have the restricted codecs installed on the system? Are these web videos webm, h.264 or h.265? Usually these are in the form of gstreamer plugins (part of the restricted codecs). Try those and let us know.

---

### Post by csae2608 on 2022-01-08
yes, thanks, it seems it is actually some driver issue, as previously (before installing the driver) everything fine, also during installation, but upon reboot, it seems the graphical glitch is back.
However, totem seems to think everything is ok, as it does not produce any message in terminal, and the video plays fine, albeit in those strange colours.

[https://streamable.com/e5o70q](https://streamable.com/e5o70q)

---

### Post by QIII on 2022-01-08
Hello.

Did you switch from an NVIDIA card to AMD on this machine?  If so, did you remove the NVIDIA driver *before* installing the AMD driver?

What is the exact model of your GPU?

Would you please post the results of 

```
lsmod | grep amdgpu
```

and 

```
lsmod | grep radeon
```

This will help determine which driver for AMD graphics is loaded and running in the kernel.

---

### Post by csae2608 on 2022-01-09
yes, i had Nvidia, but those driver should have been deleted as in the meantime i installed the OS anew.

```
**lsmod | grep amdgpu**
amdgpu               6864896  53
amd_iommu_v2           20480  1 amdgpu
amdttm                 69632  1 amdgpu
amd_sched              36864  1 amdgpu
amdkcl                 24576  3 amd_sched,amdttm,amdgpu
drm_kms_helper        188416  1 amdgpu
drm                   491520  24 drm_kms_helper,amdttm,amdgpu,amdkcl
i2c_algo_bit           16384  1 amdgpu

```

```
**lsmod | grep radeon**

(no output)

```


the graphics card is AMD Radeon Pro WX 2100 2GB

---

### Post by QIII on 2022-01-09
OK.  So let me be sure:  

You are still using 18.04?

Totem is the only player that does not work?

---

### Post by csae2608 on 2022-01-09
yes, 18.04, well, it works, but in the way as shown in the sample video, with the garbled colours.

i tried 20.04 and 22.04, but don§t feel comfortable updating yet.

EDIT: yes, only the VIDEO app is showing this behaviour, mpv and vlc seem work just fine.

---

### Post by QIII on 2022-01-09
If 18.04, is is 18.04.5 with the Hardware Enablement Stack (HWE)?

The Radeon Pro driver overlay is very sensitive to specific releases.  For instance, the installation you will find for 20.04 at the URL you cited is for 20.04.3.  Somewhere I saw a page for "older" versions, which I assume would work for, say 20.04.

Anyway, the 18.04 driver on that page is specifically for 18.04.5 HWE.

All that said:  If it is working with other video players and not one in particular, I'd have to wonder if it is the particular odd-man-out that is not playing nice with the driver/hardware.  The question may not be about hardware at all.

---

### Post by csae2608 on 2022-01-10
i am no long term user, just downloaded the latest 18.04 LTS from website,

```
NAME="Ubuntu"
VERSION="18.04.6 LTS (Bionic Beaver)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 18.04.6 LTS"
VERSION_ID="18.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=bionic
UBUNTU_CODENAME=bionic


```

```
uname -a
Linux rich-MS-7A38 5.4.0-92-generic #103~18.04.2-Ubuntu SMP Wed Dec 1 16:50:36 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

```

and i actualy dont know what HWE is, if it is meant 18.04 with kernel for 20.04 or what,
the drivers seem to work just fine, with the exception of the Video app, which is set as default, so it kept me wondering.

noticed that this app also sometimes complains of missing codecs, where other apps seem to work just fine.
Otherwise, sorry to see Totem Plugins left deprecated, used it quite along time, was my favorite firefox plugin!

---

