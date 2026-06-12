---
title: "RealTek RTL-8188CUs working well-how to"
date: 2012-12-09
forum: Networking &amp; Wireless
---

### Post by kurt18947 on 2012-12-09
There are threads here about people having trouble with the Edimax ew-7811un nano wifi adapter and presumably other brands that use the RealTek 8188CUs chip.  I find that mine will work - when first plugged in.  The LED stays on steady.  After a few minutes the connection will fail.  Unplug and replug will work - for a few minutes then it will fail again.  Here is the procedure I've followed to make this adapter work reliably.  This is with Ubuntu Gnome 1210 but the same procedure worked with Mint 13.

First item of business was to download the correct driver from RealTek's web site using a reliable network connection.  Next  I  plugged the 8188CUs device in and ran 'lsmod' noting which modules were loaded.  The relevant modules I noted were "rtl8192cu", "rtl8192c_common" and "rtlwifi".  I then opened gedit with sudo privileges and navigated to /etc/modprobe.d/blacklist.conf.  I then added to the end of the file this:

```
# Blacklist native RealTek 8188CUs drivers
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

```Save the file and close.  I then renamed the downloaded Realtek folder (long file name) to something shorter and easier to type, in my case rtl8188.  I had extracted the file to my desktop so the folder was /Desktop/rtl8188.  Navigate to this folder and in the folder should be a file named "install.sh".  I plugged the adapter in and typed this command:

```
sudo bash install.sh
```Let the script run, restart and I was in business.  I will keep the Realtek folder where I can find it again though.  A new image/kernel will require running the script again.  The Edimax seems like a great little adapter for a portable with failed/problematic/poorly supported WiFi, it only protrudes from the USB socket 10-12 mm.  The signal level and link quality are every bit as  strong as larger USB WiFi adapters and it doesn't seem to run warm at all.    I hope someone will find this useful.

Edit to add:  The correct module for both the RTL8188CUs and RTL8192SU (Dlink DWA-131) appears to be r8712u.

---

### Post by ahallubuntu on 2012-12-09
Right.  One more thing: add the name of the new module (e.g. "8192cu") to the end of the file /etc/modules so the module will load automatically at each reboot.

To clarify what you said about the kernel:  if you simply do an Ubuntu update that includes a new kernel, you'll need to re-build the module.

The Realtek 8188/8192 chipset is used in many of those generic little mini-USB WiFi dongles from numerous manufacturers, including some you can buy cheaply on eBay and Amazon.

---

### Post by Sertorius on 2012-12-09
Thank you very much, Kurt. It looks like you have solved a problem that has annoyed me for three days!

---

### Post by kurt18947 on 2012-12-10
> **ahallubuntu said:**
> Right.  One more thing: add the name of the new module (e.g. "8192cu") to the end of the file /etc/modules so the module will load automatically at each reboot.

To clarify what you said about the kernel:  if you simply do an Ubuntu update that includes a new kernel, you'll need to re-build the module.

The Realtek 8188/8192 chipset is used in many of those generic little mini-USB WiFi dongles from numerous manufacturers, including some you can buy cheaply on eBay and Amazon.

Right.  There appear to be two common chipsets for the tiny (nano) adapters, RTL8188CUs and one from I think Ralink.  What surprised me about the tiny Edimax was signal strength.  I expected pretty weak signal strength because there's no room for a larger antenna.  In an 1800 sq. ft. wood frame/drywall house the signal strength is very good.

---

### Post by manolomanolo on 2013-01-08
> **kurt18947 said:**
> Edit to add:  The correct module for both the RTL8188CUs and RTL8192SU (Dlink DWA-131) appears to be r8712u.

First of all, thanks so much for your guide.
I followed it and finally my wifi dongle seems to work perfectly.

Just some notes.
[LIST=1]
[*] I have the ***Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter*** and I found the RTL8188CUS drivers [HERE]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true"). So, please note that I downloaded and installed the RTL8188CUS drivers, not the r8712u.
[*]I followed your guide after making a fresh install of Kubuntu 12.10. So, in order to install the drivers I also needed to install the ***gcc***, the ***linux*** and the ***build-essential*** packages from repositories in order to let the installation process go on without errors.
[/LIST]

Thank you again!

---

### Post by kurt18947 on 2013-01-08
> **kurt18947 said:**
> There are threads here about people having trouble with the Edimax ew-7811un nano wifi adapter and presumably other brands that use the RealTek 8188CUs chip.  I find that mine will work - when first plugged in.  The LED stays on steady.  After a few minutes the connection will fail.  Unplug and replug will work - for a few minutes then it will fail again.  Here is the procedure I've followed to make this adapter work reliably.  This is with Ubuntu Gnome 1210 but the same procedure worked with Mint 13.

First item of business was to download the correct driver from RealTek's web site using a reliable network connection.  Next  I  plugged the 8188CUs device in and ran 'lsmod' noting which modules were loaded.  The relevant modules I noted were "rtl8192cu", "rtl8192c_common" and "rtlwifi".  I then opened gedit with sudo privileges and navigated to /etc/modprobe.d/blacklist.conf.  I then added to the end of the file this:

```
# Blacklist native RealTek 8188CUs drivers
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

```Save the file and close.  I then renamed the downloaded Realtek folder (long file name) to something shorter and easier to type, in my case rtl8188.  I had extracted the file to my desktop so the folder was /Desktop/rtl8188.  Navigate to this folder and in the folder should be a file named "install.sh".  I plugged the adapter in and typed this command:

```
sudo bash install.sh
```Let the script run, restart and I was in business.  I will keep the Realtek folder where I can find it again though.  A new image/kernel will require running the script again.  The Edimax seems like a great little adapter for a portable with failed/problematic/poorly supported WiFi, it only protrudes from the USB socket 10-12 mm.  The signal level and link quality are every bit as  strong as larger USB WiFi adapters and it doesn't seem to run warm at all.    I hope someone will find this useful.



.

---

### Post by kurt18947 on 2013-01-08
> **manolomanolo said:**
> First of all, thanks so much for your guide.
I followed it and finally my wifi dongle seems to work perfectly.

Just some notes.
[LIST=1]
[*] I have the ***Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter*** and I found the RTL8188CUS drivers [HERE]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true"). So, please note that I downloaded and installed the RTL8188CUS drivers, not the r8712u.
[*]I followed your guide after making a fresh install of Kubuntu 12.10. So, in order to install the drivers I also needed to install the ***gcc***, the ***linux*** and the ***build-essential*** packages from repositories in order to let the installation process go on without errors.
[/LIST]

Thank you again!

I'm glad it worked for you.  I edited my post above to remove the reference to the r8712u module.  That works with my 8192SU adapter, it does not work with the 8188CUs and I'm not certain where it came from.  I believe rtl8192CU is the default for the 8192SU chipset.  Backport perhaps?   The 8188CUs driver does work.  I did not have to add the packages you did.  Perhaps Ubuntu Gnome (whatever its name) includes them by default, kubuntu does not?

Edit:  I found that the r8712u module is the replacement for the rtl8192CU module as of Nov. 2012.

---

### Post by stealthdave on 2013-03-22
If you're trying to compile this module on a more modern kernel (in my case 3.7.0-7-generic), then you'll need to patch the code as described here:

[https://ask.fedoraproject.org/question/9638/realtek-8192cu-fedora-18/](https://ask.fedoraproject.org/question/9638/realtek-8192cu-fedora-18/)

There is a patch on Launchpad the completely does the trick here:

Bug report link: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1030858/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1030858/)
Direct patch link: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1030858/+attachment/3465019/+files/use_kthread_run.patch](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1030858/+attachment/3465019/+files/use_kthread_run.patch)

You need to have a launchpad account and be logged in to download the patch.

It took me several MONTHS to figure all of this out, so thanks to everyone who helped me put together the pieces!  Hopefully this will save someone else a few months of grief! ;)

- Dave

---

### Post by tim_phillips on 2013-04-26
Thought i'd add my solution

I've attached a script and patch that fixes up the 'implicit' error and the 'symbol' error, and then compiles and installs.

tested on 3.8 and 3.9 kernels.

put the script (sh file) and the patch (txt file) in the same folder as the downloaded file ( RTL8192xC_USB_linux_v3.4.4_4749.20121105.zip from [http://tinyurl.com/c4v34vq](http://tinyurl.com/c4v34vq) )

run the script as root or sudo

don't forget to blacklist the native drivers:
put a file in to /etc/modprobe.d/ with this in it
```

# Blacklist native RealTek 8188CUs drivers
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

```

---

### Post by tim_phillips on 2013-04-27
even easier....

i've uploaded a deb file that will compile, install, and DKMS the drivers for you.

[https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/](https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/)

---

### Post by tjeremiah on 2013-04-27
^ thanks for the DEB.
> **tim_phillips said:**
> Thought i'd add my solution

I've attached a script and patch that fixes up the 'implicit' error and the 'symbol' error, and then compiles and installs.

tested on 3.8 and 3.9 kernels.

put the script (sh file) and the patch (txt file) in the same folder as the downloaded file ( RTL8192xC_USB_linux_v3.4.4_4749.20121105.zip from [http://tinyurl.com/c4v34vq](http://tinyurl.com/c4v34vq) )

run the script as root or sudo

don't forget to blacklist the native drivers:
put a file in to /etc/modprobe.d/ with this in it
```

# Blacklist native RealTek 8188CUs drivers
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

```

Thank You guys so much!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!1 This needs to be a STICKY!

---

### Post by kurt18947 on 2013-04-28
:KS  Worked perfectly!  Thank you so much!  And I agree with making this a sticky.  I'll attach the install output.  There was a  "install script not executable" message but everything works.  I installed using gdebi.  I initially tried without a network connection, copying on a USB drive.  I got an error message that it was unable to download files.  Plugged in another network adapter and it installed as expected.

```
Selecting previously unselected package dkms.
(Reading database ... 164527 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.2.0.3-1.1ubuntu2_all.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.4-2ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.2.0.3-1.1ubuntu2) ...
Setting up fakeroot (1.18.4-2ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Selecting previously unselected package rtl8192cu-tjp-dkms.
(Reading database ... 164611 files and directories currently installed.)
Unpacking rtl8192cu-tjp-dkms (from .../rtl8192cu-tjp-dkms_0ubuntu1.1_all.deb) ...
Setting up rtl8192cu-tjp-dkms (0ubuntu1.1) ...
Loading new rtl8192cu_tjp-0ubuntu1.1 DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-19-generic
Building for architecture x86_64
Building initial module for 3.8.0-19-generic
Done.

8192cu:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.8.0-19-generic/updates/dkms/

: The post_install script is not executable.

depmod.......

Backing up initrd.img-3.8.0-19-generic to /boot/initrd.img-3.8.0-19-generic.old-dkms
Making new initrd.img-3.8.0-19-generic
(If next boot fails, revert to initrd.img-3.8.0-19-generic.old-dkms image)
update-initramfs....

DKMS: install completed.
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-19-generic

```

---

### Post by tim_phillips on 2013-05-01
thanks for the feedback. glad it has helped.
i've modified it - just for cosmetic reasons to remove that error message that kurt mentioned.
cheers,
tim.

[link to deb package on google code]("https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/downloads/list")

---

### Post by Glockmonkee on 2013-05-12
> **tim_phillips said:**
> even easier....

i've uploaded a deb file that will compile, install, and DKMS the drivers for you.

[https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/](https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/)

OMG!

I've been looking for this for so long.

Thanks a lot!

---

### Post by oscaralvarez on 2013-05-16
Please Help me

Hi I have a problem I have a USB Wireless TL-WN723N, I followed the solution changing blacklist and installing the .deb without problems, and reboot but my device no works
$lsmod

Module                  Size  Used by
parport_pc             28152  0 
bnep                   18036  2 
ppdev                  17073  0 
rfcomm                 42641  16 
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_realtek    78399  1 
joydev                 17377  0 
arc4                   12615  2 
brcmsmac              550698  0 
uvcvideo               80847  0 
cordic                 12574  1 brcmsmac
brcmutil               14755  1 brcmsmac
videobuf2_vmalloc      13056  1 uvcvideo
mac80211              606457  1 brcmsmac
videobuf2_memops       13202  1 videobuf2_vmalloc
coretemp               13355  0 
snd_hda_intel          39619  3 
cfg80211              510937  2 brcmsmac,mac80211
kvm_intel             132891  0 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
kvm                   443165  1 kvm_intel
snd_hwdep              13602  1 snd_hda_codec
i915                  600351  7 
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
videobuf2_core         40513  1 uvcvideo
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
drm_kms_helper         49394  1 i915
snd                    68876  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
videodev              129260  2 uvcvideo,videobuf2_core
lp                     17759  0 
drm                   286313  3 i915,drm_kms_helper
psmouse                95870  0 
soundcore              12680  1 snd
mei                    41158  0 
parport                46345  3 lp,ppdev,parport_pc
bcma                   41051  1 brcmsmac
lpc_ich                17061  0 
intel_ips              17978  0 
samsung_laptop         14532  0 
btusb                  22474  0 
i2c_algo_bit           13413  1 i915
serio_raw              13215  0 
mac_hid                13205  0 
bluetooth             228619  22 bnep,btusb,rfcomm
microcode              22881  0 
video                  19390  2 i915,samsung_laptop
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
sky2                   57977  0 
ahci                   25731  3 
libahci                31364  1 ahci


oscar@samsung-tech:~$ lsusb
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0ac8:c33f Z-Star Microelectronics Corp. Webcam
Bus 001 Device 004: ID 0bda:8179 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 002 Device 004: ID 0a5c:219c Broadcom Corp.


Xubuntu 13.04 64 bits- Kernel 3.8.0-21. Samsung Laptop Intel

---

### Post by tim_phillips on 2013-05-17
Oscar,
Wrong driver for your device i think.
Your TL-WN723N device has an RTL8188SU chipset not RTL8188CUS.
Tim.

---

### Post by kurt18947 on 2013-05-17
Tim is correct.  Here is some information about your device:

[http://wikidevi.com/wiki/TP-LINK_TL-WN723N_v1](http://wikidevi.com/wiki/TP-LINK_TL-WN723N_v1)

Note the caution about multiple versions of the same model # using different chip sets.  That bugs me but the majority of users (windows & mac) don't know and don't care.  I see these entries:

brcmsmac              550698  0
brcmutil               14755  1 brcmsmac  and similar.

I'm wondering if your device has a Broadcom chipset.

---

### Post by oscaralvarez on 2013-05-17
Tim and Kurt

Thankssss, so much, I solved it!, you are right I was installing wrong driver, I search the correct driver for my TL-WN723N ver 3. although the driver isn't  RTL8188CUS, the correct driver for me is RTL8188EU,

How I solved exactly?

I download driver for [TP-LINK_TL-WN723N_v3]("http://wikidevi.com/wiki/TP-LINK_TL-WN723N_v1") the first file in gitub:  

Xubuntu 12.10  use this ->  [https://github.com/liwei/rpi-rtl8188eu](https://github.com/liwei/rpi-rtl8188eu)
Xubuntu 13.04  use this ->  [https://github.com/purchae/rtl8188eu](https://github.com/purchae/rtl8188eu)

And unzip  file, 
$ cd directory_driver_unzipped
$ sudo make
$ make install

Reboot my pc and worked it

PD:
> brcmsmac              550698  0
brcmutil               14755  1 brcmsmac  and similar.

Because I testing the USB wireless adapter in my laptop (although it have the wireless "broadcom chipset" fine ) this install testing is for a customer, and just I have my laptop for this case :)

---

### Post by kurt18947 on 2013-05-17
Nice detective work Oscar.  No shortage of RTL8188 variants, is there?  Perhaps your adapter supports 13 WiFi channels vs. 11 channels in N. America?

---

### Post by I_ated_it on 2013-05-18
This worked great thanks a lot!  I just bought a monoprice branded RealTek RTL8192CU to replace a ralink adapter that got crushed (it still worked but the signal wasnt great).

My speed isnt as good as I expected but that may be unrelated.

---

### Post by intrloper on 2013-05-24
I have yet to try the *.deb method but wanted to ask if there is a difference in *CU and *CUS that would matter?

I have the Asus USB-N13 with the V.2 RTL8192CU chipset but notice on the realtek site there is two different listings for CU and CUS. 

Thank you for any help you can give and I_ated_it thank you for pointing me to this thread.

---

### Post by kurt18947 on 2013-05-25
I'm not 100% certain but I believe they use the same package.  You could download both and compare them, or you might be able to tell just by comparing the file names.

---

### Post by mtk.sugi on 2013-05-26
Thanks! This solution worked my ubuntu13.04.

> **tim_phillips said:**
> Thought i'd add my solution

I've attached a script and patch that fixes up the 'implicit' error and the 'symbol' error, and then compiles and installs.

tested on 3.8 and 3.9 kernels.

put the script (sh file) and the patch (txt file) in the same folder as the downloaded file ( RTL8192xC_USB_linux_v3.4.4_4749.20121105.zip from [http://tinyurl.com/c4v34vq](http://tinyurl.com/c4v34vq) )

run the script as root or sudo

don't forget to blacklist the native drivers:
put a file in to /etc/modprobe.d/ with this in it
```

# Blacklist native RealTek 8188CUs drivers
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

```

---

### Post by capricious71 on 2013-06-07
> **tim_phillips said:**
> even easier....

i've uploaded a deb file that will compile, install, and DKMS the drivers for you.

[https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/](https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/)


I just wanted to say a big THANK YOU for this. I've been trying to get this working for several days. It worked perfectly on Lubuntu 13.04.

---

### Post by robbo87 on 2013-06-10
> **tim_phillips said:**
> Thought i'd add my solution

I've attached a script and patch that fixes up the 'implicit' error and the 'symbol' error, and then compiles and installs.

tested on 3.8 and 3.9 kernels.

put the script (sh file) and the patch (txt file) in the same folder as the downloaded file ( RTL8192xC_USB_linux_v3.4.4_4749.20121105.zip from [http://tinyurl.com/c4v34vq](http://tinyurl.com/c4v34vq) )

run the script as root or sudo

don't forget to blacklist the native drivers:
put a file in to /etc/modprobe.d/ with this in it
```

# Blacklist native RealTek 8188CUs drivers
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

```

I've just followed this guide and run the script in the terminal and changed the blacklist.conf file but now after loading wicd I get no wireless connectivity at all, Have I maybe used the wrong driver? 

I have an edimax nano usb adapter. 

I'm new to Linux/ubuntu so not 100% what to do here.

Before trying the above method I tried installing with the deb file that you compiled but when opening up with the software centre it never seemed to install.

---

### Post by kurt18947 on 2013-06-10
> **robbo87 said:**
> I've just followed this guide and run the script in the terminal and changed the blacklist.conf file but now after loading wicd I get no wireless connectivity at all, Have I maybe used the wrong driver? 

I have an edimax nano usb adapter. 

I'm new to Linux/ubuntu so not 100% what to do here.

Before trying the above method I tried installing with the deb file that you compiled but when opening up with the software centre it never seemed to install.

You have to install the .deb package in order for it to work.  It didn't work because you blacklisted the 'native' drivers and didn't install an replacement.  I find Ubuntu software center a little persnickity with 'external' packages.  I have Gdebi installed for such purposes, it's an oldie but goodie found in the repositories.  You could also do it via command line but I'm no expert there.  I imagine ```
sudo dpkg -i <package name>
```
would work but again,  but I'm no command line wizard.  I can copy/paste with the best of 'em though:P.  

I'm having a  somewhat off topic thought when talking about installing .deb packages.  If you're new to Linux/Debian/Ubuntu, you want to use a little discretion when installing .deb packages.  Packages found in the repositories or on reputable sites such as webupd8 are in all liklihood not malicious.  There was however a .deb package some months ago on an artwork site that would remove the operating system when installed.  Simply use a little discretion and judgment.  Leave the > Ooo! this looks like a neat cursor in this banner ad! <click>  to the Windows folks

---

### Post by robbo87 on 2013-06-10
Thanks for getting back to me, I forgot to add that before I did the blacklisting I ran in the terminal the script that is in one of the earlier downloads which had been added into the folder of the driver download as instructed and that seemed to install ok. 

I'll give the other method of installing the deb package a go and see what happens, i've since reversed the blacklist.conf mod and got back some wireless functionality although it's very hap hazard.

---

### Post by kurt18947 on 2013-06-10
> **robbo87 said:**
> Thanks for getting back to me, I forgot to add that before I did the blacklisting I ran in the terminal the script that is in one of the earlier downloads which had been added into the folder of the driver download as instructed and that seemed to install ok. 

I'll give the other method of installing the deb package a go and see what happens, i've since reversed the blacklist.conf mod and got back some wireless functionality although it's very hap hazard.

Haphazard is a good description of that adapter using the native driver.  It doesn't improve with use either IME.

---

### Post by robbo87 on 2013-06-10
I've just gone to install the deb package using the GDebi installer and it says that "same version is already installed"

Now I'm stumped


Edit, here is the information from the "wireless script" that is on another thread if this is any help 

```
*************** info trace ***************

***** uname -a *****

Linux martin-Presario-F500-RY574EA-ABU 3.5.0-32-generic #53~precise1-Ubuntu SMP Wed May 29 20:35:31 UTC 2013 i686 athlon i386 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

***** lspci *****

00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Kernel driver in use: forcedeth

***** lsusb *****

Bus 001 Device 002: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Bus 002 Device 002: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 002 Device 003: ID 0c45:7000 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 045e:00b4 Microsoft Corp. 
Bus 002 Device 007: ID 15d9:0a4c Trust International B.V. USB+PS/2 Optical Mouse

***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"virginmedia4098985"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

rtl8192cu              67480  0 
rtl8192c_common        47696  1 rtl8192cu
rtlwifi                65304  1 rtl8192cu
mac80211              475546  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              181041  2 rtlwifi,mac80211

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [virginmedia4098985] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *virginmedia4098985: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 76 WPA2

  IPv4 Settings:
    Address:         192.168.0.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             194.168.4.100
    DNS:             194.168.8.100


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"virginmedia4098985"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000567327b02
                    Extra: Last beacon: 688ms ago
                    IE: Unknown: 001276697267696E6D6564696134303938393835
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD7E0050F204104A0001101044000102103B0001031047001004AA7F10ED0680E162349311D137BD32102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F20400011011000743473331303144100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180201F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** dmesg *****

[   20.065466] rtl8192cu: Chip version 0x10
[   20.252932] rtl8192cu: MAC address: <MAC address removed>
[   20.252940] rtl8192cu: Board Type 0
[   20.253200] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   20.253310] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[   20.351463] Error: Driver 'rtl8192cu' is already registered, aborting...
[   20.644472] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   20.645200] rtlwifi: wireless switch is on
[   20.674707] rtl8192cu: MAC auto ON okay!
[   20.710971] rtl8192cu: Tx queue select: 0x05
[   21.162264] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.162958] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.716719] wlan0: authenticate with <MAC address removed>
[   24.740775] wlan0: send auth to <MAC address removed> (try 1/3)
[   24.743861] wlan0: authenticated
[   24.756039] wlan0: associate with <MAC address removed> (try 1/3)
[   24.761352] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   24.761391] wlan0: associated
[   24.761630] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1654.501830] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1659.667383] wlan0: authenticate with <MAC address removed>
[ 1659.695568] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1659.698183] wlan0: authenticated
[ 1659.724053] wlan0: associate with <MAC address removed> (try 1/3)
[ 1659.728431] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 1659.728505] wlan0: associated
[ 2050.393043] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2051.364498] wlan0: authenticate with <MAC address removed>
[ 2051.398334] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2051.400772] wlan0: authenticated
[ 2051.416116] wlan0: associate with <MAC address removed> (try 1/3)
[ 2051.421066] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 2051.421115] wlan0: associated

****************** done ******************

```

---

### Post by kurt18947 on 2013-06-10
Have you reinstated the blacklist?  I looked at my 'lsmod' output on the notebook running the ew-7811Un.  The only Realtek related entry I see is "8192cu".  There is no "rtl*" anything.  When I run the command "modinfo 8192cu" I get many lines of output.  The ones that matter, I think are:[INDENT]
-filename:  /lib/modules/3.8.0-23-generic/updates/dkms/8192cu.ko (This is Ubuntu 13.04)

-version:  v3.4.4_4749.20121105

-author:  Realtek Semiconductor Corp.[/INDENT]

Let us know how you get along.

---

### Post by BSherwood on 2013-06-11
I am having the exact same problem as stated in the first post about connection drops and packet loss etc. . . 
*note - i've only been using linux a week or so, been trying to get internet to work well whole time :-/

i have 
```
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 44
    I/O ports at d000 [size=256]
    Memory at e8010000 (64-bit, prefetchable) [size=4K]
    Memory at e8000000 (64-bit, prefetchable) [size=64K]
    [virtual] Expansion ROM at e8020000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8168
    Kernel modules: r8168

```
kernel
```
 3.5.0-32-generic 
```
driver package I am currently using (from the realtek site listed in the unixblogger link below)
```
r8168-8.035.00.tar.bz2
```
i followed [http://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/](http://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/)  to update my driver and blacklist "r8169"

the connect got fast, but i still get random disconnects.  . . 

I tried to blacklist
```

# Blacklist native RealTek 8188CUs drivers
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

```
then install the driver again.
 but that totally stopped my Edimax adapter from working at all. (no lights or connection)
Is there a something different I should be doing since my realtek version is a little different? Are there other drivers I need for the Edimax adapter?

---

### Post by ahallubuntu on 2013-06-11
~

---

### Post by kurt18947 on 2013-06-12
I'm pretty sure the 8169 is wired ethernet, not wireless.  The blacklisting disabled the wireless as it should have and there was no alternative or replacement available.

---

### Post by dauntless77 on 2013-06-14
Ok sounds a bit longer than Moopi's but seems like a plan. I found another usb wireless adapter called Panda it was on amazon.com said it supported Linux and a whole host of os's. check it out, let me know your thoughts. [http://www.amazon.com/Panda-150Mbps-Wireless-N-2-4GHz-Adapter/dp/B00762YNMG/ref=sr_1_2?ie=UTF8&qid=1371186591&sr=8-2&keywords=panda+wireless+usb](http://www.amazon.com/Panda-150Mbps-Wireless-N-2-4GHz-Adapter/dp/B00762YNMG/ref=sr_1_2?ie=UTF8&qid=1371186591&sr=8-2&keywords=panda+wireless+usb)

---

### Post by kurt18947 on 2013-06-14
> **dauntless77 said:**
> Ok sounds a bit longer than Moopi's but seems like a plan. I found another usb wireless adapter called Panda it was on amazon.com said it supported Linux and a whole host of os's. check it out, let me know your thoughts. [http://www.amazon.com/Panda-150Mbps-Wireless-N-2-4GHz-Adapter/dp/B00762YNMG/ref=sr_1_2?ie=UTF8&qid=1371186591&sr=8-2&keywords=panda+wireless+usb](http://www.amazon.com/Panda-150Mbps-Wireless-N-2-4GHz-Adapter/dp/B00762YNMG/ref=sr_1_2?ie=UTF8&qid=1371186591&sr=8-2&keywords=panda+wireless+usb)

I don't know for certain but I suspect this device may use an RT5370 chipset based on the wording of the listing.  The RT5370 is not plug 'n' play on kernels older than about 3.5.x or thereabouts.  To use on an older distro I'm pretty sure you'd need to download & build drivers.  I have a no-name RT5370 device which is plug 'n' play on Ubuntu13.04.  It connects with no user intervention but signal strength and throughput are inferior to every other wireless adapter I have.  That may be because it's a no-name $6 Ebay wonder, I have no other RT5370 devices to compare it to.

I did try plugging the RT5370 device into a machine running another distro with a 2.6.38 kernel.  The adapter was like Sgt. Schultz from the TV show "Hogan's heroes" -  "I see nothing, I know nothing!"  That in part is why I'm sceptical about the Panda device working on a distro using an older kernel.  This is one area where newer kernels are a huge improvement -- wireless support.  The only adapter I'd be pretty confident about working "out-of-the-box" on older distros/kernel/images is one using RealTek's RTL8187B chipset.  I have a TrendNet TEW-424UB v.3 which has been plug -n- play for me since Ubuntu 9.04 or 9.10.  This is G speed though and not particularly fast even for a G speed device.

---

### Post by dauntless77 on 2013-06-14
Makes sense. I failed to mention I'm working with a Broadcom chip set bcm43 type. But odds are, it being an older kernel I'm probably going to have to download and build driver. I'm just thinking about installing mint 15 altogether. I have a gateway amd and got it working with the Broadcom. However my other laptop which is a Dell Inspiron Intel, with a Broadcom chipset bcm43. I got it to recognize and activate the card but cant seem to enable  wifi. Its using mint 10. I know, I throw you a curve ball, sorry. I have a clue what it might be, I'm thinking because its an Intel processor, and the iso is an amd64. Is that a possibility.? Maybe I answered my own question. 8-[

---

### Post by kurt18947 on 2013-06-14
> **dauntless77 said:**
> Makes sense. I failed to mention I'm working with a Broadcom chip set bcm43 type. But odds are, it being an older kernel I'm probably going to have to download and build driver. I'm just thinking about installing mint 15 altogether. I have a gateway amd and got it working with the Broadcom. However my other laptop which is a Dell Inspiron Intel, with a Broadcom chipset bcm43. I got it to recognize and activate the card but cant seem to enable  wifi. Its using mint 10. I know, I throw you a curve ball, sorry. I have a clue what it might be, **I'm thinking because its an Intel processor, and the iso is an amd64. Is that a possibility.? Maybe I answered my own question.** 8-[

Nah, the naming is kinda deceptive.  AMD64 should really be called something like X86-64 or something, it works fine on Intel systems.  64 bit linux used to have some hardware issues but I believe those are pretty much resolved.  Not all Broadcom chips are problematic though some are.  In view of the fact that support for Mint 10 ended in April, upgrading is probably not a bad idea.  I'm not that familiar with Mint, I know it sort of parallels Ubuntu.  The thing to be aware of with Ubuntu is they've halved the support period for non-LTS releases from 18 months to 9.  Does Mint have a means to upgrade in place, or do you have to reinstall?

---

### Post by lesaaa on 2013-06-15
Hello guys, I have RealTek 725N usb wifi module, running ubuntu 13.04, downloaded 8192CU drivers, when I try "sudo bash install.sh" i get this at the end:

```
Authentication requested [root] for make driver:
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.8.0-25-generic/build M=/home/sasa/Downloads/RTL8192CU/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105  modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-25-generic'
  CC [M]  /home/sasa/Downloads/RTL8192CU/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.o
In file included from /home/sasa/Downloads/RTL8192CU/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.c:23:0:
/home/sasa/Downloads/RTL8192CU/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_service.h: In function &#8216;thread_enter&#8217;:
/home/sasa/Downloads/RTL8192CU/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_service.h:575:2: error: implicit declaration of function &#8216;daemonize&#8217; [-Werror=implicit-function-declaration]
In file included from /home/sasa/Downloads/RTL8192CU/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/sasa/Downloads/RTL8192CU/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.c:24:
/home/sasa/Downloads/RTL8192CU/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function &#8216;rxmem_to_recvframe&#8217;:
/home/sasa/Downloads/RTL8192CU/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sasa/Downloads/RTL8192CU/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
cc1: some warnings being treated as errors
make[2]: *** [/home/sasa/Downloads/RTL8192CU/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/sasa/Downloads/RTL8192CU/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-25-generic'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################



```

Can anyone help me ?

---

### Post by dauntless77 on 2013-06-15
Right, I believe Mint 10 is no longer supported and so I would just have to install the latest mint which is mint 15. I have heard something about that mint is based off of Debian and I have also heard its off of Ubuntu, its probably Debian thought. My thoughts however, I think a usb wireless adapter should work on a new Linux favor pretty flawlessly out of the box.

---

### Post by kurt18947 on 2013-06-15
lesaaa, the driver on Realtek's site hasn't been updated to work with kernels/images newer than about 3.5.x.  Ubuntu 13.04 uses kernel 3.8.x.  Check the beginning of this thread, specifically posts # 8-10.

---

### Post by dauntless77 on 2013-06-15
so I assume you have zero wireless connection.? I would hard wire to internet,. Have you gone to software manager? If not I would go there and type in realtek in the search. you should see "nictools-pci". by installing it should help you with the driver issue. so if it doesn't work just get it installed and redo the script you entered earlier, it should help. let me know how it goes. I had a similar problem but on mint and with a Broadcom chip set.

---

### Post by kurt18947 on 2013-06-15
> **dauntless77 said:**
> Right, I believe Mint 10 is no longer supported and so I would just have to install the latest mint which is mint 15. I have heard something about that mint is based off of Debian and I have also heard its off of Ubuntu, its probably Debian thought. My thoughts however, I think a usb wireless adapter should work on a new Linux favor pretty flawlessly out of the box.

And if the manufacturer chooses to cooperate, they generally do e.g. Intel.  If a manufacturer chooses to not disclose the inner workings of their hardware for competitive reasons, it's much more difficult and time consuming to reverse engineer drivers & firmware.  Also remember that even if not one *nix user bought a certain manufacturer's products, what % of computer users would that manufacturer lose?  Business and commercial customers might care, the customer who really just wants an appliance won't even notice that lack of *nix support.

---

### Post by dauntless77 on 2013-06-15
Kurt, so "nictools-pci"  wont work? The driver might not be the latest but it possibly can work. Do you think?

---

### Post by dauntless77 on 2013-06-15
Yeah I could see that. But would you think these drivers that the majority are written in C/ C++ code should be scalable and versatile  in todays tech world. Maybe less 20 years ago though. I hope it does become like the pharmacy industry, where you need a pill for every single ailment. lol.

---

### Post by darchbold on 2013-06-15
This worked for me! Thanks!

ASUS USB-N13 B1 in Ubuntu 13.04

(the required files are attached to the quoted post)

> **tim_phillips said:**
> Thought i'd add my solution

I've attached a script and patch that fixes up the 'implicit' error and the 'symbol' error, and then compiles and installs.

tested on 3.8 and 3.9 kernels.

put the script (sh file) and the patch (txt file) in the same folder as the downloaded file ( RTL8192xC_USB_linux_v3.4.4_4749.20121105.zip from [http://tinyurl.com/c4v34vq](http://tinyurl.com/c4v34vq) )

run the script as root or sudo

don't forget to blacklist the native drivers:
put a file in to /etc/modprobe.d/ with this in it
```

# Blacklist native RealTek 8188CUs drivers
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

```

---

### Post by kurt18947 on 2013-06-15
> **dauntless77 said:**
> Kurt, so "nictools-pci"  wont work? The driver might not be the latest but it possibly can work. Do you think?

Dunno.  I installed Tim Phillips' .deb file, it works very well, survives kernel/image updates etc.  I have no reason to try anything else.

---

### Post by sefosmaria on 2013-06-16
I followed the instructions of the 1st post and I made it to work.The problem that came up is that my notebook crashes everytime I try to unplug the edimax usb card.The desktop turns to black with full of messages, it freezes there and the caps-lock indicator blinks fast. The only solution is to reboot.Any idea?
My OS is Ubuntu 12.10.

---

### Post by dauntless77 on 2013-06-16
Hmm. I  would probably reinstall Ubuntu,. Which post are you referring to, there is a lot of posts? Ideally you would want to keep the usb card in, if you have security concerns just disable your wireless router (turn it off or unplug cat5 from data port).

---

### Post by kurt18947 on 2013-06-16
> **sefosmaria said:**
> I followed the instructions of the 1st post and I made it to work.The problem that came up is that my notebook crashes everytime I try to unplug the edimax usb card.The desktop turns to black with full of messages, it freezes there and the caps-lock indicator blinks fast. The only solution is to reboot.Any idea?
My OS is Ubuntu 12.10.

Interesting!  I have the same thing - the flashing capslock & numlock indicate a kernel panic.  I tried disabling wifi then unplugging the adapter - kernel panic. Next I tried unloading the module using "sudo modprobe -r 8192cu" and had the same thing happen without unplugging the adapter, kernel panic.  Rebooted into 12.04 which is  using the driver from Realtek, not the deb file from Tim.  Same reaction to being unplugged - kernel panic.  It appears to be an issue with the driver from Realtek.  I guess the solution is to shut down before removing the adapter.  This is one of those times it'd be nice to have a Linux/Ubuntu equivalent to the Windows applet that enables clean removal of hardware devices.

---

### Post by sefosmaria on 2013-06-16
> **dauntless77 said:**
> Hmm. I  would probably reinstall Ubuntu,. Which post are you referring to, there is a lot of posts? Ideally you would want to keep the usb card in, if you have security concerns just disable your wireless router (turn it off or unplug cat5 from data port).

I followed instructions from posts #1,#5,#10. This kernel panic is also happening on 12.04 and 13.04 versions.I really think of coming back to windows ](*,)

---

### Post by kurt18947 on 2013-06-16
> **sefosmaria said:**
> I followed instructions from posts #1,#5,#10. This kernel panic is also happening on 12.04 and 13.04 versions.I really think of coming back to windows ](*,)

Is it THAT bad?  :shock:

:D

Why do you need to unplug the adapter?  If you don't need the USB port, why not just turn wireless off using the nm-applet icon in the upper right corner when you want to disable wi-fi and leave the adapter plugged in?  It is true that unplugging a wifi adapter shouldn't cause a kernel panic.  I have a couple others that I can unplug with no issue, including a RealTek 8192SU based adapter.  I guess it's just the 8192CU driver.

---

### Post by lesaaa on 2013-06-17
Guy can you help me with this patch: it says 
**Extract the driver latest driver (released 2012/11/12), extract the  archive in the directory "driver", apply patch "patch -p1 > use _  kthread_run.patch", make/make install, and finally "modprobe 8192cu".**

So, here is patch [https://launchpadlibrarian.net/126334555/use_kthread_run.patch](https://launchpadlibrarian.net/126334555/use_kthread_run.patch)

To what type of file do I save it, and what than, what do i type into terminal to patch the driver ?

Thank you in advance !

---

### Post by CodingNoob on 2013-06-20
I have tried everything that has been suggested here step by step and I seem to continuously get the same error. 
Please could someone assist me, not the most experienced when it comes to Ubuntu (13.04, not sure of kernel, Digitus Dn-7045 wireless device (Realtek rtl8192cu chipset)

The significant error that i can see is that there is an implicit declaration of the function 'daemonize'

##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
	rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105.tar.gz
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/clean
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ieee80211.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ht.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_event.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_sreset.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/recv_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/generic.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/little_endian.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/swabb.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/swab.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/big_endian.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/pci_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CPhyReg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_service.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/pci_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CPhyCfg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_pwrctrl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DETestHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_version.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ethernet.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_br_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_qos.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_p2p.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/xmit_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mp_ioctl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/pci_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CEHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/mlme_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/h2clbk.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops_xp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_vendor_req.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_eeprom.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/farray.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DPhyCfg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ioctl_cfg80211.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_dm.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/if_ether.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types_ce.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_security.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl_rtl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DUHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/wlan_bssdef.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mlme_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DPhyReg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/wifi.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_event.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DEHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CUHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/nic_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_intf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops_ce.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops_linux.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/circ_buf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_byteorder.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl_set.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_dm.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mlme.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/mp_custom_oid.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ip.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl_query.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/hal_init.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_conf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DUTestHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types_linux.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/autoconf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_ce_service.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_efuse.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_io.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ieee80211_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/cmd_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sta_info.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_iol.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_debug.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types_xp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_android.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/basic_types.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mp_phy_regdef.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_rf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mlme.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_eeprom.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_io.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_br_ext.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/.tmp_rtw_wlan_util.o
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mp_ioctl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_iol.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_p2p.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_set.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_debug.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_xmit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ieee80211.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mlme_ext.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_pwrctrl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_security.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_query.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_rtl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_sta_mgt.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_wlan_util.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/.rtw_wlan_util.o.d
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/efuse/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/efuse/rtw_efuse.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_recv.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/Makefile
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/ifcfg-wlan0
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/wlan0dhcp
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/osdep_service.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/pci_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/usb_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_cfg80211.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/xmit_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/mlme_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/os_intfs.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/recv_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/sdio_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/rtw_android.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/Kconfig
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_sreset.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_dm.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_hal_init.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_cmd.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_phycfg.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_ce.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_led.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_halinit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/Hal8192CUHWImg_wowlan.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_xp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rf6052.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_mp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/hal_init.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105
Authentication requested [root] for make clean:
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm .tmp_versions -fr ; rm Module.symvers -fr
rm -fr Module.markers ; rm -fr modules.order
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8192c/usb ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8192c ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
Authentication requested [root] for make driver:
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.8.0-19-generic/build M=/home/linuxmediaserver/Desktop/Realtek/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105  modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
  CC [M]  /home/linuxmediaserver/Desktop/Realtek/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.o
In file included from /home/linuxmediaserver/Desktop/Realtek/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.c:23:0:
/home/linuxmediaserver/Desktop/Realtek/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_service.h: In function &#8216;thread_enter&#8217;:
/home/linuxmediaserver/Desktop/Realtek/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_service.h:575:2: error: implicit declaration of function &#8216;daemonize&#8217; [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/home/linuxmediaserver/Desktop/Realtek/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/linuxmediaserver/Desktop/Realtek/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################

Any assistance would be greatly appreciated.

---

### Post by CodingNoob on 2013-06-20
I also attempted the GED install and the software center says that the dependency is not satisfiable (>=1.95)

Sorry for the above script not being in a textbook, thought i had it in there but clearly not.

---

### Post by KristofU on 2013-07-06
Hello, 

 I too had problems with the built-in rtl8192cu driver, but managed to get my dongle working with the 8192cu driver from the deb package created by Tim ([https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/](https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/)) (Thanks Tim!)  

However, I am experiencing very slow download rates - only about 0.39 Mbps, while with the same Wifi dongle I easily get 4Mbps in Windows. 

 Anyone experiencing the same? I'm running Ubuntu 13.04.  

By the way, when connecting to my AP, I see that, initially, I'm connected at 150Mbps, but after a few secs, I get dropped to 65Mbps, according to iwconfig: 
> 
wlan0     IEEE 802.11bgn  ESSID:"testnet"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 5C:35:3B:FF:FF:FF   
          Bit Rate:65 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=96/100  Signal level=-72 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

  
Things I tried: 
[LIST]
[*]upgraded my kernel to 3.9.9-030909 - built-in driver still doesnt work, Tim's driver works the same as in 3.8 kernel. 
[*]used Windows driver with Ndiswrapper - same poor speed. 
[*]changed bit rate manually to a lower bit rate using "iwconfig wlan0 rate 54M" - but that didnt seem to work - reported bit rate was still 65Mbpss 
[*]forced usage of 802.11b by configuring that on my AP - this dropped the connection speed to 11Mb/s, and slightly improved the download speed to 0.60Mbps. 
[/LIST]

Also, according to iwlist, I have only 4 bit rates:  
> wlan0     4 available bit-rates :
      1 Mb/s
      2 Mb/s
      5.5 Mb/s
      11 Mb/s
          Current Bit Rate:65 Mb/s

I've also disabled power management by creating a /etc/modprobe.d/8192cu.conf with
> options 8192cu rtw_power_mgnt=0 rtw_enusbss=0  

Are others able to run at normal speeds? Any other ideas I could try?  

Thank you 

 Kristof

---

### Post by kurt18947 on 2013-07-06
KristofU I'm sorry to hear of your problem.  Is your adapter an RTL-8188CUs?  I think that driver is used on several chipsets.  My Edimax EW-7811Un is perfect, I consistently max out my internet connection at 25 Mb./sec. so I haven't had to do any trouble shooting using RealTek's driver with Tims's fixes.  Perhaps someone else will have a thought.

---

### Post by KristofU on 2013-07-07
kurt18947, thanks for your message.

Yes, I'v the RTL-8188cu chipset - some info:
> $ hwinfo --wlan
> hal.1: read hal dataprocess 13613: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
34: USB 00.0: 0282 WLAN controller                              
  [Created at usb.122]
  Unique ID: hSuP.x9IMWGGtcg8
  Parent ID: pBe4.9T1GDCLyFd9
  SysFS ID: /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0
  SysFS BusID: 2-2:1.0
  Hardware Class: network
  Model: "Realtek 802.11n WLAN Adapter"
  Hotplug: USB
  Vendor: usb 0x0bda "Realtek Semiconductor Corp."
  Device: usb 0x8176 "802.11n WLAN Adapter"
  Revision: "2.00"
  Serial ID: "00e04c000001"
  Driver: "rtl8192cu"
  Driver Modules: "8192cu"
  Device File: wlan0
  Features: WLAN
  Speed: 480 Mbps
  HW Address: 00:13:ef:80:10:8c
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472
  WLAN bitrates: 1 2 5.5 11
  WLAN encryption modes: TKIP CCMP
  WLAN authentication modes: open wpa-psk wpa-eap
  Module Alias: "usb:v0BDAp8176d0200dc00dsc00dp00icFFiscFFipFFin00"
  Driver Info #0:
    Driver Status: rtl8192cu is active
    Driver Activation Cmd: "modprobe rtl8192cu"
  Driver Info #1:
    Driver Status: 8192cu is active
    Driver Activation Cmd: "modprobe 8192cu"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #33 (Hub)


and 

> $ lsusb -v

Bus 002 Device 010: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0x8176 RTL8188CUS 802.11n WLAN Adapter
  bcdDevice            2.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1


Does that help?

---

### Post by kurt18947 on 2013-07-07
I have nowhere near the knowledge of others here.  Is this a notebook or desktop?  If a notebook, could you take it to another WiFi source such as a cafe or library?  If your machine works well using another wifi source, the problem is likely your router or access point.  If your machine works the same when connected to other wifi sources as your home network, there's probably something crossways with your machine.

Another thing you could try - assuming you have access - would be to reset your router or access point to factory defaults including disabling any encryption.  You don't want to leave encryption disabled for long but a few minutes may not be risky.  Make sure you know the default user name & password before doing a reset, though.  N speed can cause problems for some so disable it, use only G speed or B & G.

---

### Post by praseodym on 2013-07-07
Hi,

rtl8192/8188CU/S needs a patch for 13.04. There is a precompiled package available here:

[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107)

---

### Post by praseodym on 2013-07-07
double post

---

### Post by KristofU on 2013-07-07
kurt18947, thanks, tried all that, doesnt seem to help.

praseodym, yes, that is Tim's solution that I already have applied - which works, but very slowly (see earlier post).

At this point, I'm giving up on this dongle, I'll get a TL-WN721N which reportedly works fine.

Thanks for all the help!

---

### Post by oseb on 2013-07-08
I want a patch that works on kernel 3.10.
I failed to build on patch Saucy 13.10.

---

### Post by van hanegen on 2013-08-24
[**[COLOR=#000000]tim_phillips[/COLOR]**]("http://ubuntuforums.org/member.php?u=464774") solution works  fine wth my ubuntu 13.04. And despite any kernel updates, everything is just flying.
Thank you very much indeed!

---

### Post by kurt18947 on 2013-08-28
I started another thread because the solution I found may apply to other adapters as well.  I plugged Edimax EW-7811Un into a machine running 13.10.  The module did not load automatically, I had to load it manually.  Same story, the adapter was found, worked for a few minutes then quit.  This time however there was a useful message in 'dmesg'.  It said the package "nss-myhostname" was not installed.  I installed that package and rebooted.  That *seems* to have enabled the Edimax to work properly on my desktop machine, it stayed functioning for a couple hours.   It'll be interesting to see if this solution works - or doesn't - for others.

---

### Post by praseodym on 2013-08-28
Did it work with the native driver or the compiled one?

---

### Post by Anwar_Mahmood on 2013-08-28
Thank You!!! This worked great. There's one enhancement request I have; installation didn't work first time. I'm not an expert, so I didn't know that I'd first need to download and install DKMS ([http://linux.dell.com/dkms/](http://linux.dell.com/dkms/)) first.  Once I did that, your .DEB installed fine.  Have left an "issue" on code.google.com, merely in case you wish to add it to the wiki page :-)

---

### Post by Anwar_Mahmood on 2013-08-28
Hi All,

For the benefit of others, these instructions apply to

Netgear G54/N150 Wireless USB Micro Adapter, model WNA1000M

[http://www.netgear.co.uk/home/products/wireless-adapters/simplesharing/WNA1000M.aspx](http://www.netgear.co.uk/home/products/wireless-adapters/simplesharing/WNA1000M.aspx)

[FONT=courier new]user@computer:~$ **lsusb**[/FONT]
[FONT=courier new]Bus 001 Device 002: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS][/FONT]

Kind regards,

Anwar

---

### Post by kurt18947 on 2013-08-28
> **praseodym said:**
> Did it work with the native driver or the compiled one?
The native driver.

---

### Post by kurt18947 on 2013-09-04
My latest update on this adapter.  I just installed the daily Ubuntu gnome 13.10. Current updates and nm-applet & wpa_supplicant have issues with this adapter, they're both the subject of crash reports.  An RT5370-based adapter functions as expected on the same install.  The mystery is that I have another 13.10 install on another machine that has been in place for a month or longer.  The 8188CUs works pretty well on that install.

---

### Post by praseodym on 2013-09-04
Solution for the patched driver package for this ID here:

[http://ubuntuforums.org/showthread.php?t=2171245&p=12778064#post12778064](http://ubuntuforums.org/showthread.php?t=2171245&p=12778064#post12778064)

The ID is not part of the driver by default

---

### Post by kurt18947 on 2013-09-04
> **praseodym said:**
> Solution for the patched driver package for this ID here:

[http://ubuntuforums.org/showthread.php?t=2171245&p=12778064#post12778064](http://ubuntuforums.org/showthread.php?t=2171245&p=12778064#post12778064)

The ID is not part of the driver by default

Hi praseodym,

Yes, I saw your post and though "Ohhh, so that's the problem".  I think in my case the adapter is included in the driver.  I'm using a different 8188CUs adapter than superluigibro7 on the other thread.  He has a Netgear WNA1000m, I have an Edimax EW-7811Un.  The USB I.D. is ID 7392:7811 and that appears to be included in the driver.  I'm getting quite a few crash reports on the machine that is problematic so I suspect something to do with nm-applet and/or WPA-supplicant.  I'm posting this from another machine with Ubuntu 13.10 and the Edimax EW7811Un adapter.  It's working quite reliably using the native driver and the package I'd mentioned earlier.  The machine I'm having trouble with has a fresh install of Ubuntu gnome 13.10.  I did see one interesting thing in dmesg on the non-functioning machine but foolishly didn't save it.  Something about 'trap' and 2 strings of numbers and letters.

---

### Post by Kootee on 2013-09-06
Hi, i have the TL-WN725N WiFi, and unfortunately blacklisting (I've pasted blacklist commands from this thread's first post to /etc/modprobe.d/blacklist.conf) and installation of .deb file (1.6 newest version) doesn't help. The card doesn't appear in nm. I've checked WiFi on Windows, and it's working good, so the problem is on Ubuntu. System restart doesn't help.

My Ubuntu is 13.04 x64 version. 'ifconfig' doesn't show the card. 'lsusb' gives standard 'Bus 003 Device 002: ID 0bda:8179 Realtek Semiconductor Corp.' for this device. Could you help me solve the problem please?

---

### Post by praseodym on 2013-09-07
For the device 0bda:8179 you need this driver:

[http://forum.ubuntuusers.de/post/5536902/](http://forum.ubuntuusers.de/post/5536902/)

---

### Post by pbhj2 on 2013-09-13
Woo-hoo - the patched driver works now for me using a TP-Link USB wifi dongle. :D

This is the first time I've set up wifi on my main linux box (Kubuntu 13.04) and I just assumed that I'd messed up nameservers or got multiple IPs the same connecting or hadn't got the necessary packages installed ... but no it was the driver all along. Damn!

Kudos to tim_phillips for the patch files and script, many thanks.

Did get some compiler warnings - presumably because I'm on amd64 and they've assumed 32bit pointers, eg:
> /home/user/code+downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]


Saw a stackoverflow or similar thread on how to fix that but I'm leaving well alone whilst it's working!

---

### Post by pbhj2 on 2013-09-19
**Oh dear. Spoke too soon.** (see above)

It worked. It worked long enough to convince me to write a post here. Than it died and never came back for more than a single second, just long enough to register the connection was running and download a few bytes, no more. Just long enough to enter the overlong wifi password in to NetworkManager before hard locking (kernel panic I suppose). Strikes me that -W-int-to-pointer issue may have caused address lookups outside the reserved memory space - perhaps this problem (of mine) is just because I'm on x86_64?

So I'd tried both main options presented here: patching the code from Realtek and the DKMS enabled .deb file and neither would bring the TL-WN823N up for more than a second without causing a hard lock.

**My solution - get a new dongle.** So now I've bought the TP-Link WN722N and it's working without any intervention at all (it's Atheros using the ath9k modules that were pre-installed in my Kubuntu 13.04 raring). I've blogged about trying to get the [rtl8192cu.ko/8192cu.ko modules working for me and about the new WN722N that just works]("http://alicious.com/working-ubuntu-wifi-adapter/"). If anyone wants more info - either about what I tried for the WN823N or about the plug-and-play ability of the new adapter - then please do ask. FWIW new adapter is running at 6.5Mb/s according to iwconfig but "iw list" tells me the highest rate available is 54Mbps. Whatever, it's saturating my ADSL2 connection so I'm happy. 

;0)>

---

### Post by allen4 on 2013-09-20
Thank sweet baby Jesus! After a huge struggle I now have 13.04 wireless! This fixes the TP Link WN822N V3, and I am saturating the full 150mp/s.  Thank you for making this .deb file!!

---

### Post by xuan2 on 2013-09-27
Guys

I just uploaded a similar issue  (Realtek WLAN) with my system details. can you pls review and help?

[http://ubuntuforums.org/showthread.php?t=2177039&p=12800173#post12800173](http://ubuntuforums.org/showthread.php?t=2177039&p=12800173#post12800173)

I trying to help a poor and old man who cant buy new system.

---

### Post by domingo777i on 2013-09-28
Thank you soo much how did you figure this out?  i tried blacklisting; downloading the drivers off realtek, unlugging replugging looking at the .sh file and nothing....  i have linux mint 15 by the way... and thankx again!!!!

Kdomin0

---

### Post by olavjunior on 2013-09-29
Installed the deb on 13.10, but doesn't work for me. I have the TL-WN725N. Doesn't the deb work under 13.10? Any dependensies I don't have?

iwconfig gives:
lo        no wireless extensions.
eth0      no wireless extensions.

And the lsmod doesn't show anything with "rtl" in it... Please help

---

### Post by praseodym on 2013-09-29
Check:
```

sudo apt-get install linux-headers-$(uname -r) build-essential dkms
```
Outputs:
```

lsmod
rfkill list
sudo iwlist scan
iwlist chan
cat /etc/resolv.conf
```

---

### Post by olavjunior on 2013-09-29
> **praseodym said:**
> Check:
```

sudo apt-get install linux-headers-$(uname -r) build-essential dkms
```
Outputs:
```

lsmod
rfkill list
sudo iwlist scan
iwlist chan
cat /etc/resolv.conf
```

lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     40516  4 
snd_hda_codec_analog    75523  1 
rfcomm                 53664  0 
bnep                   18893  2 
bluetooth             323534  10 bnep,rfcomm
binfmt_misc            13140  1 
joydev                 17097  0 
coretemp               13195  0 
kvm_intel             128218  0 
kvm                   364766  1 kvm_intel
hid_logitech_dj        18165  0 
gpio_ich               13229  0 
dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
ppdev                  17391  0 
dcdbas                 14383  0 
usbhid                 47361  0 
hid                    86953  4 usbhid,hid_logitech_dj
snd_hda_intel          42658  5 
snd_hda_codec         164003  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_analog
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
microcode              18830  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
psmouse                90642  0 
snd                    60790  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_analog,snd_seq_midi
serio_raw              13189  0 
lpc_ich                16864  0 
nvidia               8511866  39 
i7core_edac            23458  0 
drm                   242354  2 nvidia
edac_core              51256  2 i7core_edac
wmi                    18590  1 dell_wmi
soundcore              12600  1 snd
parport_pc             31981  1 
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
tg3                   152066  0 
ahci                   25579  1 
libahci                26554  1 ahci
ptp                    18156  1 tg3
pps_core               18546  1 ptp

rfkill gives no output

sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

iwlist chan
lo        no frequency information.

eth0      no frequency information.

cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1

---

### Post by praseodym on 2013-09-29
Load the driver by hand:
```

sudo modprobe -v 8192cu
echo 8192cu | sudo tee -a /etc/modules
```

---

### Post by olavjunior on 2013-09-29
Oups! Seems that the deb won't install correctly. Didn't se that earliger when I did it through the software cener, but terminal gave me an error

sudo dpkg -i rtl8192cu-tjp-dkms_1.6_all.deb
[sudo] password for olav: 
(Leser database ... 208858 filer og kataloger er for øyeblikket installerte.)
Gjør klar til å bytte ut rtl8192cu-tjp-dkms 1.6 (ved bruk av rtl8192cu-tjp-dkms_1.6_all.deb) ...

------------------------------
Deleting module version: 1.6
completely from the DKMS tree.
------------------------------
Done.
Pakker ut erstatningen rtl8192cu-tjp-dkms ...
Setter opp rtl8192cu-tjp-dkms (1.6) ...
Loading new rtl8192cu-tjp-1.6 DKMS files...
First Installation: checking all kernels...
Building only for 3.11.0-9-generic
Building for architecture i686
Building initial module for 3.11.0-9-generic
Error! Bad return status for module build on kernel: 3.11.0-9-generic (i686)
Consult /var/lib/dkms/rtl8192cu-tjp/1.6/build/make.log for more information.

EDIT: Log attached

---

### Post by olavjunior on 2013-09-29
I got it to work by a github from some guy over at peppermint 

> sudo apt-get install build-essential linux-headers-generic git

then:
Code:
mkdir ~/RTL8188EU

then:
Code:
cd ~/RTL8188EU

then:
Code:
git clone git://github.com/lwfinger/rtl8188eu.git

then:
Code:
cd ~/RTL8188EU/rtl8188eu

then:
Code:
make

then:
Code:
sudo make install

Restarted and everything works now like a charm. I didn't even do the last part  of the guide:

> Code:
sudo depmod -a

then:
Code:
sudo update-initramfs -u

then:
Code:
sudo modprobe 8188eu

EDIT: My only problem is that I have NO IDEA of what that github code did. So if the source disappears I'm lost. Or maybe I can just recompile after new kernels?

---

### Post by gabrielboaglio on 2013-10-05
Hola! Para todos aquellos que estén buscando la solución a esto, a mi me sirvió este artículo.
(Tengo actualmente KUbuntu 13.04 con kernel 3.9.0-030900-generic, y un adaptador TP-LINK WN822N)
[URL="http://zauwn.blogspot.com.ar/2013/08/edup-realtek-semicondutor-corp.html"]
http://zauwn.blogspot.com.ar/2013/08/edup-realtek-semicondutor-corp.html[/URL]

Puntualmente, la parte donde dice:

[COLOR=#333333][FONT=Georgia]git clone [https://github.com/dz0ny/rt8192cu.git](https://github.com/dz0ny/rt8192cu.git)[/FONT][/COLOR]
[COLOR=#333333][FONT=Georgia]cd rt8192cu[/FONT][/COLOR]
[COLOR=#333333][FONT=Georgia]make[/FONT][/COLOR]
[COLOR=#333333][FONT=Georgia]sudo make install
[/FONT][/COLOR]
Para que arranque la placa wifi sin necesidad de reiniciar, como ultimo paso hice un:

sudo modprobe 8192cu


Saludos!
Gabriel

---

### Post by Stratis_Evangelinos on 2013-10-15
Thanks[SIZE=4][COLOR=#000000][/COLOR][/SIZE]olavjunior, that worked for me [COLOR=#333333][FONT=Arial]TP-LINK's Mini Wireless N USB Adapter  ([/FONT][/COLOR][COLOR=#333333][FONT=Arial]TL-WN723N v2) on [/FONT][/COLOR]Ubuntu 13.04.

---

### Post by tjeremiah on 2013-10-16
the methods used in this thread no longer work for me when using ubuntu13
10 :mad:

I've read ever new post. tried the new and the old solutions with no positive results.

---

### Post by alvarito-barberberecho on 2013-10-17
> **tjeremiah said:**
> the methods used in this thread no longer work for me when using ubuntu13
10 :mad:

I've read ever new post. tried the new and the old solutions with no positive results.

I happens the same as you :(:(

I think it's because we are using the 64bit version

---

### Post by PY8xX4T on 2013-10-23
Hello guys I've just installed ubuntu 13.10 and have issues with WN725N TP-LINK Wifi stick. Can someone help me and walk through the installation of this stick-dirver?

```
uname -a
Linux crow 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:12:00 UTC 2013 i686 i686 i686 GNU/Linux
```

What I did:
1. Run this commands ```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
```
2.
```

lsmod
rfkill list
sudo iwlist scan
iwlist chan
cat /etc/resolv.conf

```

3. Dowloaded this one 
```
http://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/downloads/detail?name=rtl8192cu-tjp-dkms_1.6_all.deb&can=2&q= 
```
and installed it.

4. Run this one and it's result.
```
sudo modprobe -v 8192cu
FATAL: Module 8192cu not found.
```


EDITED: I have model TP-LINK TL-WN725N v2.0

WBR

---

### Post by kurt18947 on 2013-10-23
> **PY8xX4T said:**
> Hello guys I've just installed ubuntu 13.10 and have issues with WN725N TP-LINK Wifi stick. Can someone help me and walk through the installation of this stick-dirver?

```
uname -a
Linux crow 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:12:00 UTC 2013 i686 i686 i686 GNU/Linux
```

What I did:
1. Run this commands ```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
```
2.
```

lsmod
rfkill list
sudo iwlist scan
iwlist chan
cat /etc/resolv.conf

```

3. Dowloaded this one 
```
http://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/downloads/detail?name=rtl8192cu-tjp-dkms_1.6_all.deb&can=2&q= 
```
and installed it.

4. Run this one and it's result.
```
sudo modprobe -v 8192cu
FATAL: Module 8192cu not found.
```


EDITED: I have model TP-LINK TL-WN725N v2.0

WBR

Yes, Tim Patterson's .deb file only works with 13.04 (and perhaps earlier?)  It will not work in 13.10. Have you tried just plugging in your adapter?  Mine will sorta work, it'll work for several minutes then stop responding.  I've had decent luck stopping wifi via the applet, pause a couple seconds then starting it again.  It seems to be dependent on the machine and the wireless access point/router.  I also get prompts to re-authenticate periodically.  So far I'm having better success with an RTL8192CU device using the native driver.

---

### Post by Herber on 2013-10-23
I have an Edimax  EW-7811Un dongle with a 64bit Ubuntu 13.10 build.  The wireless shows my home network but is unable to establish any connection.  It would appear from the above posts, that the procedures above will not work, does anyone have a solution for 64bit 13.10?

---

### Post by kurt18947 on 2013-10-24
> **Herber said:**
> I have an Edimax  EW-7811Un dongle with a 64bit Ubuntu 13.10 build.  The wireless shows my home network but is unable to establish any connection.  It would appear from the above posts, that the procedures above will not work, does anyone have a solution for 64bit 13.10?

My only thought would be email RealTek, perhaps they'd send you something 'unofficial'.  I'd think they'd release a driver that would work with  kernels newer than 3.5.x.

---

### Post by PY8xX4T on 2013-10-24
> **kurt18947 said:**
> Yes, Tim Patterson's .deb file only works with 13.04 (and perhaps earlier?)  It will not work in 13.10. Have you tried just plugging in your adapter?  Mine will sorta work, it'll work for several minutes then stop responding.  I've had decent luck stopping wifi via the applet, pause a couple seconds then starting it again.  It seems to be dependent on the machine and the wireless access point/router.  I also get prompts to re-authenticate periodically.  So far I'm having better success with an RTL8192CU device using the native driver.

So I need 13.04. Can you please describe where to download it because at official download page there is no 13.04 version. And can you please describe how to install on clear ubuntu 13.04 drivers for WN725N ? 

I know that there are a lots of such manuals for this but I really get stuck with it.  I've already trie diffirent version of ubuntu and a lot ofdifferent drivers but no luck.

WBR

---

### Post by van hanegen on 2013-10-25
> **PY8xX4T said:**
> So I need 13.04. Can you please describe where to download it because at official download page there is no 13.04 version. And can you please describe how to install on clear ubuntu 13.04 drivers for WN725N ? 

I know that there are a lots of such manuals for this but I really get stuck with it.  I've already trie diffirent version of ubuntu and a lot ofdifferent drivers but no luck.

WBR
You need just to tape "13.04 ubuntu download" in your brouser.
(one of the numerous links for example: [http://www.omgubuntu.co.uk/2013/04/ubuntu-13-04-download](http://www.omgubuntu.co.uk/2013/04/ubuntu-13-04-download)).
And to install WN725N driver (incidentally, I got the same dongle), you have to input commands from the attached file in your terminal (you need to be connected, though).
best wishes

---

### Post by kurt18947 on 2013-10-26
> **PY8xX4T said:**
> So I need 13.04. Can you please describe where to download it because at official download page there is no 13.04 version. And can you please describe how to install on clear ubuntu 13.04 drivers for WN725N ? 

I know that there are a lots of such manuals for this but I really get stuck with it.  I've already trie diffirent version of ubuntu and a lot ofdifferent drivers but no luck.

WBR

Yes, for 13.04 Tim Patterson's .deb file should work.  12.10 is the last version that Realtek's driver works on.  Tim Patterson started with the official driver and cleaned up the problems caused by the 12.10 -> 13.04 changes.

[https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/](https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/)

---

### Post by praseodym on 2013-10-27
Hi,

for 13.10 you need a patched driver. Check here:

[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#Realtek-rtl8192cu-s-Treiber-fuer-13-10](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#Realtek-rtl8192cu-s-Treiber-fuer-13-10)

---

### Post by van hanegen on 2013-10-27
And here's the solution to this issue from our forum:
[http://ubuntuforums.org/showthread.php?t=2148130&page=2](http://ubuntuforums.org/showthread.php?t=2148130&page=2)
It works well with my [SIZE=2]TP-LINK TL-WN725N[/SIZE] USB dongle (13.10 clean lnstall).

---

### Post by cccharles1 on 2014-03-05
> **kurt18947 said:**
> I'm glad it worked for you. I edited my post above to remove the reference to the r8712u module. That works with my 8192SU adapter, it does not work with the 8188CUs and I'm not certain where it came from. I believe rtl8192CU is the default for the 8192SU chipset. Backport perhaps? The 8188CUs driver does work. I did not have to add the packages you did. Perhaps Ubuntu Gnome (whatever its name) includes them by default, kubuntu does not?

Edit:  I found that the r8712u module is the replacement for the rtl8192CU module as of Nov. 2012.


Thank you very much.

This worked excellently and first time for me without a problem.

I too am amazed at the signal strength of these nano adapters. Mine shows 100% two rooms away from the router. :p

---

### Post by lukebenes on 2014-04-03
> **praseodym said:**
> Hi,

for 13.10 you need a patched driver. Check here:

[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#Realtek-rtl8192cu-s-Treiber-fuer-13-10](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#Realtek-rtl8192cu-s-Treiber-fuer-13-10)

I have 13.10 with an Edimax EW-7811Un ( Realtek RTL8188CUS ) 

The best solution I have found is to follow the instructions at:
[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

These patched official drivers have been working great for me, resolving all my issues with packet loss and dropped connections.

---

### Post by kurt18947 on 2014-04-05
> **lukebenes said:**
> I have 13.10 with an Edimax EW-7811Un ( Realtek RTL8188CUS ) 

The best solution I have found is to follow the instructions at:
[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

These patched official drivers have been working great for me, resolving all my issues with packet loss and dropped connections.

The patch above also works on the installs of 14.04 I've tried.  The speed seems slower than in 13.10 but it's a stable connection.  An RTL8192CU adapter on 14.04 indicates much better speed than my 8188CUS adapter though I only have one 8188CUs adapter and it may have hardware issues, I don't know.  I also find it interesting that when using the RTL8192CU adapter with Mint 16 or SolydX live USBs, the adapters seem stable (no dropped connections/restarts required) without installing the rtl8192cu-fixes patch.  I have no idea what's different between *buntu and Mint/SolydX but something seems to be.  This is also a live session, not installed.

---

### Post by hauke3 on 2014-04-15
What exactly does

 "don't forget to blacklist the native drivers:
put a file in to /etc/modprobe.d/ with this in it"

mean?

Thanks for helping!

---

### Post by praseodym on 2014-04-15
It means, after the installation execute

```
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
and reboot.

---

### Post by mike_s2 on 2014-05-12
> **kurt18947 said:**
> The patch above also works on the installs of 14.04 I've tried.  The speed seems slower than in 13.10 but it's a stable connection.  An RTL8192CU adapter on 14.04 indicates much better speed than my 8188CUS adapter though I only have one 8188CUs adapter and it may have hardware issues, I don't know.  I also find it interesting that when using the RTL8192CU adapter with Mint 16 or SolydX live USBs, the adapters seem stable (no dropped connections/restarts required) without installing the rtl8192cu-fixes patch.  I have no idea what's different between *buntu and Mint/SolydX but something seems to be.  This is also a live session, not installed.

OMG. Thank you guys so much... I had just upgraded from Ubuntu 12.04 LTS to 14.04, and the driver straight from the RealTek site that I used w/ 12.04 (filename RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911.zip) now refuses to complete compilation on 14.04.  The linked fix at [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes) worked beautifully...20 minutes in, and full signal. Beautiful... No more dropped connections, I hope!!!

(Off topic, but w/ all the issues I've had w/ the built in wifi on my Toshiba laptop and even the EDIMAX Wifi dongle I purchased as a workaround, next time, I think I'm going w/ a Ubuntu vendor, like System76 next time...)

PS. Also, the driver included in 14.04 LTS for the RTL-8188CUS works for about 15 minutes then dies.

---

### Post by timdp on 2014-05-19
Hi, I'm just switching my Mum over from Windows Vista to Ubuntu 12.04 64 bit (latest updates).

Everything is going smoothly, apart from the Wireless adapter (Edimax EW-7811UN) which frequently drops connection to the router.

I've tried the RTL download and the build failed, is the linked fix (pvaret) suitable for me?

---

### Post by praseodym on 2014-05-19
Hi,

which kernel is in use? Please show
```

uname -a
```
Does LAN work?

---

### Post by timdp on 2014-05-21
Hi thanks.

Kernel  is 3.11.0.0-20-generic #35-precise1-Ubuntu SMP Fri May 2 21:32:55 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Not sure about LAN (I'm not in front of it right now).

The wireless dongle is working intermittently at the moment.

---

### Post by praseodym on 2014-05-21
So, change the driver:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.8
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

---

### Post by timdp on 2014-05-23
Thanks very much praseodym, that's worked perfectly.

Will that change be affected by any software updates she applies, or is it a permanent fix?

---

### Post by praseodym on 2014-05-23
Its permanent, "dlms" will build the driver on each kernel update

---

### Post by rcocchiararo on 2014-09-30
On the github fix site it says:

> [COLOR=#333333][FONT=Helvetica Neue]This driver is known to work with some RTL8192CU devices like the Belkin N300, and should work with some 8188CUS, RTL8188CE-VAU and RTL8188RU devices as well. However, it is known not to work well with devices using dual antennas, such as the TP-Link WN8200ND, due to an incomplete MIMO implementation in the upstream driver.[/FONT][/COLOR]

I have that TP-link dual antenna device. After installing this, instead of having the connection... not connect without reason, i am asked for the wifi password again.

Is this normal for dual antenna devices? i expected it to underperform, not to... not connect >P

I am running kubuntu 14.10

---

### Post by praseodym on 2014-10-02
Which kernel does 14.10 use?

**uname -a**

---

### Post by rcocchiararo on 2014-10-02
> Linux Z 3.16.0-18-generic #25-Ubuntu SMP Fri Sep 26 02:44:15 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

The stock included driver fails to connect but says nothing, this other one asks for the wifi password again.

I have a second tp link card that works, but has less range and less max theorical speed.

---

### Post by praseodym on 2014-10-03
Meanwhile the driver was updated. Delete it and download it again:

```
sudo dkms install 8192cu/[COLOR="#FF0000"]1.9[/COLOR]
```

---

### Post by rcocchiararo on 2014-10-03
> **praseodym said:**
> Meanwhile the driver was updated. Delete it and download it again:

```
sudo dkms install 8192cu/[COLOR=#FF0000]1.9[/COLOR]
```

when was this updated? 

In any case, how do i delete it? Just renaming the folder and downloading it again, and trying that, wont work:

rcocchiararo@Z:~/Dev$ sudo dkms install 8192cu/1.9Module 8192cu/1.9 already installed on kernel 3.16.0-18-generic/x86_64

EDIT: i found how, 1.9 was already installed tho, that was what i had, but maybe there was an update with no version change? testing

sudo dkms remove 8192cu/[COLOR=#FF0000]1.9 --all[/COLOR]

---

### Post by avi95 on 2014-10-05
Hey, 

I just bought the NetGear WNA1000M 802.11bgn [Realtek RTL8188CUS] USB adapter yesterday.
It works perfectly with my WIndows 10 Technical Preview, but on Ubuntu 14.04 1 LTS, it doesn't work at all. 

I've spent the whole of yesterday crawling through forums, trying various methods/fixes/patches etc, without any luck.
You guys are my last hope. Any help would be really appreciated.

---

### Post by jeremy31 on 2014-10-05
> **avi95 said:**
> Hey, 

I just bought the NetGear WNA1000M 802.11bgn [Realtek RTL8188CUS] USB adapter yesterday.
It works perfectly with my WIndows 10 Technical Preview, but on Ubuntu 14.04 1 LTS, it doesn't work at all. 

I've spent the whole of yesterday crawling through forums, trying various methods/fixes/patches etc, without any luck.
You guys are my last hope. Any help would be really appreciated.

Follow the instructions on how to run the wireless_script found [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by praseodym on 2014-10-05
Change the driver via cable connection:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```

Reboot

---

### Post by rcocchiararo on 2014-10-05
have you tried the driver from his github? it IS your last choice.

It does not work on kubuntu 14.10 for my dual antenna device tho.

---

### Post by avi95 on 2014-10-05
Tried that. Didn't work.
What else can I do?

---

### Post by rcocchiararo on 2014-10-05
> **avi95 said:**
> Tried that. Didn't work.
What else can I do?

then you are like me, screwed :(

My [COLOR=#333333][FONT=Helvetica Neue]TP-Link WN8200ND does nothing with the built in driver, and with this fix, keeps asking for the password.

Meanwhile, i am using another usb card that is slower and with less range, considering going back to windows >P[/FONT][/COLOR]

---

### Post by rcocchiararo on 2014-10-05
meanwhile, i ran the wireless script[ATTACH]256966[/ATTACH]

---

### Post by jeremy31 on 2014-10-05
> **rcocchiararo said:**
> meanwhile, i ran the wireless script[ATTACH]256966[/ATTACH]

Is there a reason ath9k modules are loaded when there doesn't appear to be any atheros device?

---

### Post by rcocchiararo on 2014-10-05
> **jeremy31 said:**
> Is there a reason ath9k modules are loaded when there doesn't appear to be any atheros device?

I believe they are from my secondary wireless card (also usb).

It was unpluged when i tried the more powerfull one.

---

### Post by jeremy31 on 2014-10-05
Any chance of using an internal card or are there no slot available?

---

### Post by rcocchiararo on 2014-10-05
> **jeremy31 said:**
> Any chance of using an internal card or are there no slot available?

I do not own PCI/PCIE wireless cards.

How would that help tho? I mean, i have a slower USB card with one antenna that i am using, but i would love to use the more powerfull dual antenna one.

i believe this fixed driver wont help tho, and i found a bug report that is pretty long where the developers of the opensource drivers failed to help too, so my only option might be to buy a long cable and send it from my router to my pc, or go back to windows.

---

### Post by praseodym on 2014-10-05
Please show the output of

```
lsmod

```
completely.

---

### Post by rcocchiararo on 2014-10-05
> kvm_intel             143514  0 snd_rawmidi            30876  1 snd_seq_midi
kvm                   455570  1 kvm_intel
snd_seq                67224  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
serio_raw              13434  0 
snd_timer              29513  2 snd_pcm,snd_seq
joydev                 17344  0 
snd                    87611  19 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
lpc_ich                21093  0 
soundcore              15052  2 snd,snd_hda_codec
amd_iommu_v2           18903  1 fglrx
et131x                 35359  0 
i7core_edac            24139  0 
edac_core              56549  2 i7core_edac
shpchp                 37040  0 
mac_hid                13227  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
xfs                   921700  4 
libcrc32c              12644  1 xfs
pata_acpi              13053  0 
uas                    23264  0 
usb_storage            66398  1 uas
hid_generic            12559  0 
usbhid                 52574  0 
hid                   110426  2 hid_generic,usbhid
psmouse               106512  0 
r8169                  71471  0 
ahci                   29966  6 
mii                    13934  1 r8169
libahci                32424  1 ahci
pata_jmicron           12775  0 
rcocchiararo@Z:~$ clear
rcocchiararo@Z:~$ lsmod
Module                  Size  Used by
ctr                    13049  2 
ccm                    17731  2 
ath9k_htc              75111  0 
ath9k_common           25638  1 ath9k_htc
ath9k_hw              446568  2 ath9k_common,ath9k_htc
ath                    29052  3 ath9k_common,ath9k_htc,ath9k_hw
arc4                   12608  4 
rtl8192cu              67670  0 
rtl_usb                18448  1 rtl8192cu
rtlwifi                64237  2 rtl_usb,rtl8192cu
rtl8192c_common        53170  1 rtl8192cu
mac80211              660599  4 rtl_usb,rtlwifi,ath9k_htc,rtl8192cu
cfg80211              510218  5 ath,ath9k_common,mac80211,rtlwifi,ath9k_htc
bnep                   19543  2 
rfcomm                 69509  0 
bluetooth             446190  10 bnep,rfcomm
6lowpan_iphc           18702  1 bluetooth
snd_hda_codec_realtek    76887  1 
snd_hda_codec_generic    68914  1 snd_hda_codec_realtek
fglrx                9311101  125 
snd_hda_codec_hdmi     47547  1 
gpio_ich               13579  0 
snd_hda_intel          30379  4 
snd_hda_controller     35152  1 snd_hda_intel
snd_hda_codec         139675  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
snd_pcm               104102  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
coretemp               13441  0 
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
kvm_intel             143514  0 
snd_rawmidi            30876  1 snd_seq_midi
kvm                   455570  1 kvm_intel
snd_seq                67224  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
serio_raw              13434  0 
snd_timer              29513  2 snd_pcm,snd_seq
joydev                 17344  0 
snd                    87611  19 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
lpc_ich                21093  0 
soundcore              15052  2 snd,snd_hda_codec
amd_iommu_v2           18903  1 fglrx
et131x                 35359  0 
i7core_edac            24139  0 
edac_core              56549  2 i7core_edac
shpchp                 37040  0 
mac_hid                13227  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
xfs                   921700  4 
libcrc32c              12644  1 xfs
pata_acpi              13053  0 
uas                    23264  0 
usb_storage            66398  1 uas
hid_generic            12559  0 
usbhid                 52574  0 
hid                   110426  2 hid_generic,usbhid
psmouse               106512  0 
r8169                  71471  0 
ahci                   29966  6 
mii                    13934  1 r8169
libahci                32424  1 ahci
pata_jmicron           12775  0

Right now your fixed driver is not installed because there was a kernel update (3.16.0-20-generic, 3.16.0-16-generic before), and i wanted to see if something had changed, but it did not.

---

### Post by praseodym on 2014-10-06
Obviously, the "old" driver is not blacklisted. Check this one first:
```

sudo modprobe -rfv ath9k_htc rtl8192cu
sudo modprobe -v rtl8192cu
```
Replug the stick and check the connection

---

### Post by rcocchiararo on 2014-10-06
> **praseodym said:**
> Obviously, the "old" driver is not blacklisted. Check this one first:
```

sudo modprobe -rfv ath9k_htc rtl8192cu
sudo modprobe -v rtl8192cu
```
Replug the stick and check the connection

As i said, that information is with your driver removed and the old one no longer blacklisted.

If the old driver is in action, when i try to connect, it tries to do it for a while, then stops, with no messages.

If the new driver is installed and working, and the old one blacklisted, it tries for a while and then asks for the password.

I correctly installed your driver and blacklisted the old one with your files.

Any sense in trying your instructions after knowing this? (i just ask cause i need to reinstall it all again, i had given up >P )

---

### Post by praseodym on 2014-10-07
Which of the access points of the wireless script is yours? Change the encryption mode to pure WPA2-AES (CCMP) in your router (check the manual) and set IPv6 to "Ignore" in the network-manager profile

---

### Post by rcocchiararo on 2014-10-07
My access point is "Z".

I tried with that, and also with no security at all.

If i set it to no security, it just fails to connect and says nothing, like the stock driver.

I don't have ipv6 in my house (or in argentina >P), but will look into that nonetheless.

---

### Post by praseodym on 2014-10-08
But the network-manager tries to use IPv6, so try deactivating

---

### Post by rcocchiararo on 2014-10-08
Ok, i tested both with your driver and the stock one:

1) wifi with no password
2) wifi like you said

In both cases, with ipv6 set  to ignore.

Same results as before.

It seems this won work for this tplink card, and realtek has not updated their drivers since... forever.

PS: i tried this after rebooting without the other wireless card, so no ath* driver loaded.

---

### Post by el mariachi on 2014-10-09
Hello! I bought an ALFA AWUS036NHR which has an RTL8188RU chip. I tried using the patch from pvaret, but it's not working. The native drivers are blacklisted, the led blinks like it should but it won't get connection and on secured networks keeps asking for the password and won't connect.

Ubuntu 14.04
```

Linux koi 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

lsusb
```

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 003 Device 006: ID 0bda:817f Realtek Semiconductor Corp. RTL8188RU 802.11n WLAN Adapter
Bus 003 Device 003: ID 062a:4101 Creative Labs 
Bus 003 Device 002: ID 174f:1474 Syntek 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lsmod
```

Module                  Size  Used by
8192cu                527283  0 
bbswitch               13943  0 
bnep                   19624  2 
rfcomm                 69160  8 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_realtek    65580  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
snd_hda_intel          56451  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
parport_pc             32701  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
ppdev                  17671  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
lp                     17759  0 
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
parport                42348  3 lp,ppdev,parport_pc
arc4                   12608  2 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
ath9k                 164164  0 
kvm                   451511  0 
ath9k_common           13551  1 ath9k
crct10dif_pclmul       14289  0 
ath9k_hw              453856  2 ath9k_common,ath9k
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
mac80211              630653  1 ath9k
joydev                 17381  0 
serio_raw              13462  0 
cfg80211              484040  3 ath,ath9k,mac80211
lpc_ich                21080  0 
ath3k                  13318  0 
btusb                  32412  0 
bluetooth             391136  23 bnep,ath3k,btusb,rfcomm
mei_me                 18627  0 
mei                    82276  1 mei_me
i915                  783805  5 
ideapad_laptop         18216  0 
sparse_keymap          13948  1 ideapad_laptop
drm_kms_helper         53081  1 i915
wmi                    19177  0 
video                  19476  1 i915
drm                   303102  4 i915,drm_kms_helper
mac_hid                13205  0 
soundcore              12680  1 snd
i2c_algo_bit           13413  1 i915
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid
ahci                   25819  3 
psmouse               106678  0 
alx                    32452  0 
libahci                32716  1 ahci
mdio                   13807  1 alx

```

is there a new patch somewhere?
not sure if downgrading to kernel 3.11 would be very wise

---

### Post by el mariachi on 2014-10-10
it seems these drivers may show some promise:
[https://github.com/FreedomBen/rtl8188ce-linux-driver](https://github.com/FreedomBen/rtl8188ce-linux-driver)

currently, using kernel 3.16 they fail do keep the connection up, probably due to lack of "no power management" option

---

### Post by rcocchiararo on 2014-10-10
> **el mariachi said:**
> it seems these drivers may show some promise:
[https://github.com/FreedomBen/rtl8188ce-linux-driver](https://github.com/FreedomBen/rtl8188ce-linux-driver)

currently, using kernel 3.16 they fail do keep the connection up, probably due to lack of "no power management" option

My "[COLOR=#333333][FONT=Helvetica Neue]TP-Link WN8200ND[/FONT][/COLOR]" (rtl8192cu) seems to not be compatible (at least on kubuntu 14.10 using the ubuntu 14.04 branch), it either shows the same error as the stock driver, or i installed it wrongly because the instructions are for 8192ce.

The installation offers to disable power management tho, did you skip that?

---

### Post by el mariachi on 2014-10-11
The installation offers that option, but it in fact does nothing, since the actual module does not include a power management parameter. It's a bug which will be fixed eventually, the guy just needs some time ;)

---

### Post by rcocchiararo on 2014-10-12
i see.

Do you have any idea about my particular card with that driver, or should i go buy tons of meters of cable ? XD

---

### Post by praseodym on 2014-10-12
The drtiver folder for 8192cu contains a file named:

cat 8192cu-disable-power-management.conf 
```
# Disable power management in the 8192cu driver. This works around a bug in
# some hardware where the device never wakes back up.
# Credit goes to Saqib Razaq (https://github.com/s-razaq) for the fix.

# rtw_power_mgnt=0 disables power saving
# rtw_enusbss=0 disables USB autosuspend
options 8192cu rtw_power_mgnt=0 rtw_enusbss=0
```
Try moving the file:
```

sudo cp rtl8192-fixes/8192cu-disable-power-management.conf /etc/modprobe.d/
```
Reload the driver
```

sudo modprobe -rfv 8192cu
sudo modprobe -v 8192cu
```
Replug the stick and check
```

iwconfig
dmesg | grep 8192
```

---

### Post by el mariachi on 2014-10-16
The 8192cu driver keeps asking for the password. The driver I mentioned is newer and connects correctly, but after seconds disconnects and has no parameters besides "debug"

---

### Post by rcocchiararo on 2014-10-16
> **el mariachi said:**
> The 8192cu driver keeps asking for the password. The driver I mentioned is newer and connects correctly, but after seconds disconnects and has no parameters besides "debug"

in my case, this thread's driver keeps asking for the password, and the one you mentioned does the same that the stock one does (tho maybe, i installed it wrong, since i have the 8192cu)

---

### Post by Subito_Piano on 2014-12-23
Hi! I am unable to install the [rtl8192cu-tjp-dkms_1.6_all.deb]("https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/downloads/detail?name=rtl8192cu-tjp-dkms_1.6_all.deb") file listed on page one.  My "Airlink101 AWLL5099 Wireless N 150 Ultra Mini USB Adapter" simply does not show up.  Interestingly, it does work in Lucid Puppy Linux -- based, of course, on Lucid Ubuntu.

Of course, when dpkg failed to install the above deb it created a make.log file at /var/lib/dkms/rtl8192cu-tjp/1.6/build/make.log, attached: [ATTACH]258747[/ATTACH] 

I am running Ubuntu Studio, 3.13.0-43-lowlatency kernel.  Using an earlier generic kernel didn't make a diffference.

output of lsusb:
```
Bus 002 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 002 Device 002: ID 5986:0190 Acer, Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
output of lsmod:
```
cuse                   13445  3 
acer_wmi               32522  0 
arc4                   12608  2 
rt2800pci              13606  0 
rt2800mmio             16841  1 rt2800pci
rt2800lib              89076  2 rt2800pci,rt2800mmio
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  2 rt2800pci,rt2800mmio
rt2x00lib              55307  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
rts5139               331166  0 
mac80211              638933  3 rt2x00lib,rt2x00pci,rt2800lib
uvcvideo               80885  0 
kvm_amd                60026  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
kvm                   455768  1 kvm_amd
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
bnep                   19624  2 
cfg80211              496328  2 mac80211,rt2x00lib
rfcomm                 69160  0 
bluetooth             395387  10 bnep,rfcomm
sp5100_tco             13979  0 
joydev                 17332  0 
snd_hda_codec_conexant    57441  1 
serio_raw              13413  0 
eeprom_93cx6           13344  1 rt2800pci
k10temp                13126  0 
crc_ccitt              12707  1 rt2800lib
snd_hda_codec_hdmi     46368  1 
i2c_piix4              22155  0 
snd_hda_intel          52306  5 
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102040  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
binfmt_misc            17468  1 
ideapad_laptop         18216  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
sparse_keymap          13948  2 acer_wmi,ideapad_laptop
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69273  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
video                  19476  1 acer_wmi
wmi                    19177  1 acer_wmi
mac_hid                13205  0 
soundcore              12680  1 snd
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
nls_iso8859_1          12713  2 
psmouse               102569  0 
r8169                  67581  0 
mii                    13934  1 r8169
ahci                   25819  5 
libahci                32716  1 ahci
```
FWIW, i blacklisted as directed in /etc/modprobe.d/: 
```
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi
```
as well as disabling power management:
```
options 8192cu rtw_power_mgnt=0 rtw_enusbss=0
```
Any assitance appreciated - thanks in advance.

---

### Post by praseodym on 2014-12-23
This is the driver for kernel up to 3.8. For new kernels:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

---

### Post by Subito_Piano on 2014-12-23
Still no joy.  :-(

Actually, I ran across those same commands earlier yesterday and tried them.  I also installed the above-metioned deb -- thru synaptic.  Today i uninstalled the deb and attempted to (re-)follow your intsructions, but of course, it all was already done.

More info -- i ran wireless_script and got this:
```

########## wireless info START ##########

Report from: 23 Dec 2014 10:46 EST -0500

Booted last: 23 Dec 2014 10:39 EST -0500

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-43-lowlatency #72-Ubuntu SMP PREEMPT Mon Dec 8 20:00:12 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Lenovo Device [17aa:397b]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
    Subsystem: Lenovo Device [17aa:f101]
    Kernel driver in use: rt2800pci

##### lsusb #############################

Bus 002 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 002 Device 002: ID 5986:0190 Acer, Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### lsmod #############################

rt2800pci              13606  0 
rt2800mmio             16841  1 rt2800pci
rt2800lib              89076  2 rt2800pci,rt2800mmio
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  2 rt2800pci,rt2800mmio
rt2x00lib              55307  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              638933  3 rt2x00lib,rt2x00pci,rt2800lib
acer_wmi               32522  0 
cfg80211              496328  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
wmi                    19177  1 acer_wmi
ideapad_laptop         18216  0 
sparse_keymap          13948  2 acer_wmi,ideapad_laptop
video                  19476  1 acer_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::3e97:eff:fe03:dd20/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9695 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10346 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1475313 (1.4 MB)  TX bytes:1527743 (1.5 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search integrity

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/ECC_Wireless]] (600 root)
[connection] id=ECC_Wireless | type=802-11-wireless
[802-11-wireless] ssid=ECC_Wireless | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ECA_Wireless 1]] (600 root)
[connection] id=ECA_Wireless 1 | type=802-11-wireless
[802-11-wireless] ssid=ECA_Wireless | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ECA_Wireless]] (600 root)
[connection] id=ECA_Wireless | type=802-11-wireless
[802-11-wireless] ssid=ECA_Wireless | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/infected]] (600 root)
[connection] id=infected | type=802-11-wireless
[802-11-wireless] ssid=infected | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/3.13.0-43-lowlatency/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     5C88E1E4BD840C950F493E4
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.13.0-43-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3D:49:E4:87:9E:93:BA:94:77:84:39:3E:2A:D0:DA:C2:31:72:A2:07
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/3.13.0-43-lowlatency/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     A6B5D01725492005F5918FA
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       3.13.0-43-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3D:49:E4:87:9E:93:BA:94:77:84:39:3E:2A:D0:DA:C2:31:72:A2:07
sig_hashalgo:   sha512

[rt2800lib]
filename:       /lib/modules/3.13.0-43-lowlatency/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     3AF2621F166C8604D7D8AA5
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.13.0-43-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3D:49:E4:87:9E:93:BA:94:77:84:39:3E:2A:D0:DA:C2:31:72:A2:07
sig_hashalgo:   sha512

[rt2x00pci]
filename:       /lib/modules/3.13.0-43-lowlatency/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     1B9A9CB4CAAB78DFE7974EA
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.13.0-43-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3D:49:E4:87:9E:93:BA:94:77:84:39:3E:2A:D0:DA:C2:31:72:A2:07
sig_hashalgo:   sha512

[rt2x00mmio]
filename:       /lib/modules/3.13.0-43-lowlatency/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     37A76810C0FE9E4E11476DA
depends:        rt2x00lib
intree:         Y
vermagic:       3.13.0-43-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3D:49:E4:87:9E:93:BA:94:77:84:39:3E:2A:D0:DA:C2:31:72:A2:07
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.13.0-43-lowlatency/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     6B233AA4E9B794582FA258B
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-43-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3D:49:E4:87:9E:93:BA:94:77:84:39:3E:2A:D0:DA:C2:31:72:A2:07
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-43-lowlatency/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     446B3604A9C5461044DD691
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-43-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3D:49:E4:87:9E:93:BA:94:77:84:39:3E:2A:D0:DA:C2:31:72:A2:07
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-43-lowlatency/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-43-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3D:49:E4:87:9E:93:BA:94:77:84:39:3E:2A:D0:DA:C2:31:72:A2:07
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800pci]
nohwcrypt: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi
blacklist rtl8192cu

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/ndiswrapper.conf]
alias usb:v0BDAp8176d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp8178d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp8192d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0DF6p0052d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2019pED17d*dc*dsc*dp*ic*isc*ip* ndiswrapper

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1814:0x3090 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (zd1211rw)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"

##### dmesg #############################

[   13.267667] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3090, rev 3213 detected
[   13.342821] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0005 detected
[   15.043929] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############

```
also -- note the hard and soft blocking:
```
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```
rfkill unblock all does not help.  The story is that the internal card apparently died -- or else the switch died.  It was working fine for a year and a half, then became permanently hard-blocked; it would not work in either Ubuntu Studio or in Puppy.  I can't remember if this happened just after a kernel upgrade or not -- but of course, that would not affect testing it in Puppy.  I figgered buying a usb plug would be easier that repair/replacement -- especially if it turns out that the the wi-fi switch failed.  Duh, I got used to everything working fine in Linux and never checked compatibility before i picked this adapter up.  Hardinfo does not see it.  

Not real happy with this Lenovo S205 -- i love the size but there are weird keyboard issues (some keys fail to respond though i tried two different keyboards), some usb inconsistencies (i don't think that is the present issue), and now this.  My sons' cheap Acer Chromebook simply "feels" better built than this.  Next time i'll have to look for a pro-grade, not a consumer-grade unit. [IMG]http://mysterdee.com/smilies/think.png[/IMG]

Any thoughts?

---

### Post by praseodym on 2014-12-23
The "hard block" is set, this is why no wifi works. The internal card should also work, too. Try
```

sudo rmmod ideapad_laptop
sudo rfkill unblock all
```

---

### Post by Subito_Piano on 2014-12-23
Doing that leaves only phy0,and it is still hard blocked.   Of course, rebooting restores wlan1 and doesn't help.  I'm not geting something here.  Is phy0 the usb wifi, i assume?

Also, i have BOTH network-manager AND wicd installed at the moment, out of desperation.  IDK if that compounds the problem.

---

### Post by Subito_Piano on 2014-12-23
OK -- doing the happy dance here...  [IMG]http://mysterdee.com/smilies/smiley_piano.gif[/IMG]

After following your instructions and rebooting to no success, i went back to basics (duh!) -- rebooted to advanced options, fixed broken packages, apt-get autoremove (fwiw), and file system check.  Rebooted - bingo, the onboard card works again. 

So the little Airlink (still not recognized  :? ) will head off to the Windows machine in the sound booth at church....no money -- lost but ignorance (or stupidity) can cost a lot of time!  

THANK YOU,  for your time and assistance...i appreciate it.  Good to be back on the forums again after a long hiatus.
[CENTER]
[/CENTER]

---

### Post by Subito_Piano on 2015-01-09
ADDENDUM for anyone wandering thru here in the future....

I upgraded my kernel to 3.13.0-43-lowlatency (a dumb but deserate move) and of course lost my wifi.  The command "rfkill list all" did not even show my wifi (wlan0).  I retried all the above to no success.  I loaded Puppy to see if it recognized the wireless card -- it did.  I manually connected in Puppy, rebooted into Ubuntu, and voilà!  m wireless snapped back to life -- ***?!?!?!??!?***[B][I]  :confused:
[/I][/B]
Of course, this makes absolutely no sense to me -- but now that i think about it, when i had this problem a couple weeks ago, i loaded Puppy at some point before posting the previous reply -- so apparently starting up in Puppy triggered something to make the Ralink wifi re-appear to Ubuntu.  

Weird.

If anyone can explain -- enlighten me!

---

### Post by praseodym on 2015-01-10
Please check
```

dkms status
modinfo 8192cu | egrep 'versi|filen'
locate 8192cu.ko | grep lib
uname -a
```
Did you try
```

sudo dkms autoinstall
```

---

### Post by Subito_Piano on 2015-01-10
Output:
```
~$ dkms status
8192cu, 1.9, 3.13.0-43-lowlatency, x86_64: installed
8192cu, 3.1.2590: added

~$ modinfo 8192cu | egrep 'versi|filen'
filename:       /lib/modules/3.13.0-43-lowlatency/updates/dkms/8192cu.ko
version:        v4.0.2_9000.20130911
srcversion:     13A6B22485A38D2E78BDD43
vermagic:       3.13.0-43-lowlatency SMP preempt mod_unload modversions 
parm:           rtw_chip_version:int

~$ locate 8192cu.ko | grep lib
/lib/modules/3.13.0-40-lowlatency/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
/lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
/lib/modules/3.13.0-43-lowlatency/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
/lib/modules/3.13.0-43-lowlatency/updates/dkms/8192cu.ko
/var/lib/dkms/8192cu/1.9/3.13.0-43-lowlatency/x86_64/module/8192cu.ko

~$ uname -a
Linux user-laptop 3.13.0-43-lowlatency #72-Ubuntu SMP PREEMPT Mon Dec 8 20:00:12 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```
I did not try ```
sudo dkms
``` -- because the wifi IS working now and i'm a little skittish about messing with it.  If you say "sudo dkms" is harmless, i'll try it -- after all, i want to figure this thing out! 

FWIW, note that when i was still trying to get it to work, i DID try the sggested routines from the above posts, including ```
sudo dkms install 8192cu/1.9
``` and ```
sudo dkms add ./rtl8192cu-fixes
``` -- but still it didn't spring back to life, even after several restarts, until i booted into and out of Puppy as noted before.  (Obviously, i'm not promoting one distro over another here.)

Now, i'm not familiar with many of the commands others suggest, often i just use them.  ;) IDK if i should just run dkms after each kernel upgrade or what--??? 

Interesting, doing a litle research, i find that Dell engineers came up with DKMS for us *nix users.   Kudos to Michael D. & crew! =d>

---

### Post by Subito_Piano on 2015-01-10
Output:
```
~$ dkms status
8192cu, 1.9, 3.13.0-43-lowlatency, x86_64: installed
8192cu, 3.1.2590: added

~$ modinfo 8192cu | egrep 'versi|filen'
filename:       /lib/modules/3.13.0-43-lowlatency/updates/dkms/8192cu.ko
version:        v4.0.2_9000.20130911
srcversion:     13A6B22485A38D2E78BDD43
vermagic:       3.13.0-43-lowlatency SMP preempt mod_unload modversions 
parm:           rtw_chip_version:int

~$ locate 8192cu.ko | grep lib
/lib/modules/3.13.0-40-lowlatency/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
/lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
/lib/modules/3.13.0-43-lowlatency/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
/lib/modules/3.13.0-43-lowlatency/updates/dkms/8192cu.ko
/var/lib/dkms/8192cu/1.9/3.13.0-43-lowlatency/x86_64/module/8192cu.ko

~$ uname -a
Linux user-laptop 3.13.0-43-lowlatency #72-Ubuntu SMP PREEMPT Mon Dec 8 20:00:12 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```
I did not try ```
sudo dkms autoinstall
``` -- because the wifi IS working now and i'm a little skittish about messing with it.  If you say "sudo dkms" is harmless, i'll try it -- after all, i want to figure this thing out! 

FWIW, note that when i was still trying to get it to work, i DID try the sggested routines from the above posts, including ```
sudo dkms install 8192cu/1.9
``` and ```
sudo dkms add ./rtl8192cu-fixes
``` -- but still it didn't spring back to life, even after several restarts, until i booted into and out of Puppy as noted before.  (Obviously, i'm not promoting one distro over another here.)

Now, i'm not familiar with many of the commands others suggest, often i just use them.  ;) IDK if i should just run "dkms autoinstall" after each kernel upgrade or what--??? 

Interesting, doing a litle research, i find that Dell engineers came up with DKMS for us *nix users.   Kudos to Michael D. & crew! =d>

Thank you for hanging with me on this.  :-)

---

### Post by vctor2 on 2015-02-03
Hi i don't know if this should go here but, I've tried all the ways mentioned to install my rtl8188C wlan adapter on kali linux via virtualbox, the error i get when trying to install the drivers is this:
 /lib/modules/3.14-kali1-amd64/build: No such file or directory. Stop.
Can't find the solution I hope you can help me to get it work

---

### Post by Hugo_Mendez on 2015-11-10
I have a Netgear WNA1000Mv2 [http://support.netgear.com/product/WNA1000Mv2](http://support.netgear.com/product/WNA1000Mv2) 

Im lost at getting it working, has anybody had any success with this usb dongle? Any help would be much appreciated, thanks guys!

---

### Post by praseodym on 2015-11-11
Please show the outputs of
```

lsusb
lsmod
iwconfig
```
with the stick plugged. Does LAN work?

---

### Post by heady2 on 2015-11-21
Guys, there is a new driver: RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911 
Surprise, it doesn't compile either on 3.8 with very similar errors (implicit includes).

EDIT: Haha. Didn't notice the multiple pages. Please ignore

---

