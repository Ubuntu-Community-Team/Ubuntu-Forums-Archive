---
title: "Error when Installing AMD 13.1 Legacy drivers"
date: 2013-02-25
forum: Multimedia Software
---

### Post by jerm1027 on 2013-02-25
Hello all, I have an old gaming notebook with an ATi Mobility Radeon 4650 GPU. I went to the AMD site, put in the necessary info, and they have the [Catalyst 13.1 Legacy driver package]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx"), which I have been unable to install. I followed the instructions on the [unofficial radeon driver wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29"), but I got an error when building the package.

```

jeremy@jeremy-laptop ~/Downloads $ sudo sh ./amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run --buildpkg Ubuntu/quantal
Created directory fglrx-install.YWuVw9
Verifying archive integrity... All good.
Uncompressing AMD Catalyst(TM) Proprietary Driver-8.97.100.7....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/quantal
Error: Distro Version entered incorrectly or not supported, use --listpkg to identify valid distro versions
Error: Distro Version entered incorrectly or not supported, use --listpkg to identify valid distro versions
Removing temporary directory: fglrx-install.YWuVw9

```I proceeded with the installation by just running the install script without building the packages, and it seemed to go smoothly, until the end, and it gave me an error:
```

Check if system has the tools required for installation.
Uninstalling any previously installed drivers.

Creating symlink /var/lib/dkms/fglrx/8.97.100.7/source ->
                 /usr/src/fglrx-8.97.100.7

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
cd /var/lib/dkms/fglrx/8.97.100.7/build; sh make.sh --nohints --uname_r=3.5.0-17-generic --norootcheck....(bad exit status: 1)
[Error] Kernel Module : Failed to build fglrx-8.97.100.7 with DKMS
[Error] Kernel Module : Removing fglrx-8.97.100.7 from DKMS

------------------------------
Deleting module version: 8.97.100.7
completely from the DKMS tree.
------------------------------
Done.
[Reboot] Kernel Module : update-initramfs

```Now, I'm either not using any driver, or the most generic driver possible:
```
jeremy@jeremy-laptop ~/Downloads $ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```Can someone help me out?

---

### Post by Yellow Pasque on 2013-02-26
> **jerm1027 said:**
> I proceeded with the installation by just running the install script without building the packages

Bad idea. The first thing you should do is clean that up: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx)

Then when you have your system working again, you can try again. Catalyst legacy doesn't work on quantal without some hacking. As the section by the big red warning says:

> ATI RadeonHD 2x00 - 4xx0 cards: If you have one of these cards, you do have the option of using the Catalyst Legacy driver, but only if you downgrade your Xserver version (the Catalyst Legacy driver does not support the kernel version (3.5) or the Xserver version (1.13) that Ubuntu Quantal/12.10 uses). This can be done really easily by following the instructions given at [https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx) This PPA downgrades the Xserver and install a patched version of fglrx that supports kernel version 3.5 of Ubuntu Quantal. 

---

### Post by QIII on 2013-02-26
I am alarmed by the number of times I see this recommended and have tried to remain polite in several threads.

This sort of thing effectively breaks your install and leaves you with an unknown future.

I would recommend either:

1.  Using the open source Radeon driver.

2.  Using 12.04 or 12.04.1 (but not 12.04.2) and the fglrx driver from the repo.  12.04 will be supported for a very long time.

---

### Post by Yellow Pasque on 2013-02-26
> **QIII said:**
> I am alarmed by the number of times I see this recommended

You mean downgrading the Xserver? I agree it's not good practice and a total hack, but the reports I've seen about the PPA are positive (after some initial hiccups when it first started), so it is one alternative I mention.

---

### Post by QIII on 2013-02-26
Not speaking of you in particular.  Presented as an option is certainly fair.  Recommended as the killer solution is what I find disturbing.

You also gave a clear caveat.

---

### Post by Yellow Pasque on 2013-02-26
It's a fair assessment, and I'll be more careful with language in the future. I try to strike a balance between promoting it as a "killer solution" and "ZOMG, irreversible breakage ahead and you keep the pieces!"

---

### Post by QIII on 2013-02-26
I haven't seen you at either extreme! :)

---

### Post by jerm1027 on 2013-02-26
> **Temüjin said:**
> Bad idea. The first thing you should do is clean that up: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx)

Then when you have your system working again, you can try again. Catalyst legacy doesn't work on quantal without some hacking. As the section by the big red warning says:

Yeah, I don't think the warning was very clear, and when I saw that the driver version was 13.1, I assumed it wasn't legacy, as legacy drivers in the past have been much older.

> **QIII said:**
> I am alarmed by the number of times I see this recommended and have tried to remain polite in several threads.

This sort of thing effectively breaks your install and leaves you with an unknown future.

I would recommend either:

1.  Using the open source Radeon driver.

2.  Using 12.04 or 12.04.1 (but not 12.04.2) and the fglrx driver from the repo.  12.04 will be supported for a very long time.

Then I will downgrade. I don't need to running the latest and greatest. As I've said, the lack of power control with the Open source driver causing my cooling fan to frequently ramp up to 4000RPM, which needless to say, is very loud. I also plan on using this for Steam (on Linux), so I could also use the performance boost.

Thanks for the help. I'll post an update if I get things working again.

---

### Post by Yellow Pasque on 2013-02-26
> **jerm1027 said:**
> Yeah, I don't think the warning was very clear

Suggestions on how to make it clearer are welcome...

---

### Post by jerm1027 on 2013-02-26
Probably some clarification (partially AMD's fault, since "legacy" is nowhere to be found on download page, and it's pretty hidden in the file name) that the cards are no longer supported by the current driver model. When I first read it, I assumed the legacy driver was 12.6 (or whatever it was), and when AMD gave me 13.1, I thought "Oh, I can either install legacy 12.x drivers, or the new 13.1 drivers? sweet" and proceeded with installation. The first time, I literally copy and pasted every command without giving a second look, as this was the 4th machine I've installed the drivers on in the past week or so, and the whole process went through without error, until I rebooted, and I was on the generic driver. I tried removing the driver and re-installing the open-source drivers, and I ended up breaking Xorg.

I posted this thread after my second attempt.

I was thinking something along the lines "These cards are no longer supported by the current driver, however, you have the option of using legacy driver <legacy driver version>. This driver is not supported on Ubuntu 12.10 because of incompatibility with newer version of Xorg. You will either need to downgrade Xorg, or use Ubuntu 12.04 in order to use the legacy driver"

---

### Post by Yellow Pasque on 2013-02-26
> The first time, I literally copy and pasted every command without giving a second look

I think that's at least a minor part of the problem (The filename does say 'legacy' in it). The main problem (ignoring the fact that AMD won't update recent "legacy" drivers for newer X/kernel) is the AMD/ATI site, but we can't control that.

---

