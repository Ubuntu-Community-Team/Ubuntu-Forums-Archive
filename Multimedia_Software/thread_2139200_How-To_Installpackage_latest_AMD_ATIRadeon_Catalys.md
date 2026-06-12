---
title: "How-To Install/package latest AMD ATI/Radeon Catalyst proprietary drivers"
date: 2013-04-26
forum: Multimedia Software
---

### Post by dentaku65 on 2013-04-26
Two days ago the new AMD Catalyst proprietary display driver has been release (software version 12.104).
Here the way to compile the DEB packages from the automated installer released by AMD.

This works perfect on my box:
> Xubuntu 12.10 Quantal 64bit
Kernel: 3.5.0-27-generic

Check your ATI card:
```
lspci -v |grep VGA
```

Check the latest official build available:
[http://support.amd.com/it/gpudownload/linux/Pages/radeon_linux.aspx]("http://support.amd.com/it/gpudownload/linux/Pages/radeon_linux.aspx")

Check the release notes of the build:
[http://support.amd.com/us/kbarticles/Pages/amdcatalyst13-4linreleasenotes.aspx]("http://support.amd.com/us/kbarticles/Pages/amdcatalyst13-4linreleasenotes.aspx")

Install the dipendencies (in [COLOR="#FF0000"]red[/COLOR] needed only for 64bit version):
```
sudo apt-get install build-essential fakeroot debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases [COLOR="#FF0000"]ia32-libs[/COLOR]
```

Compile and create DEB packages (in [COLOR="#FF0000"]red[/COLOR] the versioning, can be quantal or raring):
```
mkdir $HOME/ati_source
```
```
cd $HOME/ati_source
```
```
wget http://www2.ati.com/drivers/linux/amd-catalyst-13.4-linux-x86.x86_64.zip
```
```
unzip amd-catalyst-13.4-linux-x86.x86_64.zip
```
```
chmod +x amd-catalyst-13.4-linux-x86.x86_64.run
```
```
./amd-catalyst-13.4-linux-x86.x86_64.run --extract ./src
```
```
cd ./src
```
```
./ati-installer.sh [COLOR="#FF0000"]12.104[/COLOR] --buildpkg Ubuntu/[COLOR="#FF0000"]quantal[/COLOR]
```
```
cd ..
```

Check the DEB packages and install:
```
ls -alirt
```
```
sudo apt-get remove "fglrx*"
```
```
sudo dpkg -i *.deb
```

Reboot. Done!

**Optional** - Re-create xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
```
sudo aticonfig --initial -f
```

Reboot. Done!

---

### Post by dentaku65 on 2013-05-29
Today has been released the new beta driver 13.6 and, as first preview looks very promisng on my box.
[http://support.amd.com/it/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/it/gpudownload/linux/Pages/radeon_linux.aspx)
The deb packaging procedure is the same as described in post #1

Change the file to download and, of course, change the versioning (in [COLOR="#FF0000"]red[/COLOR] the versioning, can be quantal or raring):
```
./ati-installer.sh [COLOR="#FF0000"]13.101[/COLOR] --buildpkg Ubuntu/[COLOR="#FF0000"]quantal[/COLOR]
```
Because this driver is a beta release, AMD put an horrible watermark image stating that this driver is beta :confused:
anyway, to take out this watermark image edit the signature file (thanks to [jfernyhough]("http://ubuntuforums.org/showthread.php?t=2074962&p=12312011#post12312011")):
```
sudo nano /etc/ati/signature
```
Replace:
```
UNSIGNED
```
With this string (in a single line):
```
9777c589791007f4aeef06c922ad54a2:ae59f5b9572136d99fdd36f0109d358fa643f2bd4a2644d9efbb4fe91a9f6590a145:f612f0b01f2565cd9bd834f8119b309bae11a1ed4a2661c49fdf3fad11986cc4f641f1ba1f2265909a8e34ff1699309bf211a7eb4d7662cd9f8e3faf14986d92f646f1bc
```
Save. Reboot. Done!

---

### Post by PendragonUK on 2013-09-24
After following the instructions in the first post my PC boots, I can log in but I end up with a black screen and the mouse pointer. I can move the pointer but the screen is just black.

---

### Post by Yellow Pasque on 2013-09-24
Well, if you're using Ubuntu 13.04/Raring, then I hope you didn't use the "--buildpkg Ubuntu/quantal" part..
(It would be Ubuntu/raring in that case.)

---

### Post by dentaku65 on 2013-09-26
> **PendragonUK said:**
> After following the instructions in the first post my PC boots, I can log in but I end up with a black screen and the mouse pointer. I can move the pointer but the screen is just black.

Hi,
which ubuntu version are you using? And which ATI card?

---

