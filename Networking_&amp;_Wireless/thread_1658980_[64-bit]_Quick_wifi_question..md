---
title: "[64-bit] Quick wifi question."
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by Tim-Tim on 2011-01-03
I dual boot windows 7 and Kubuntu on my laptop, my wireless card works on windows 7 no problem, and luckily the company also has a linux version of the driver.  My question is, how can I install packages on kubuntu without a wired internet connection, and what packages should I download to be able to install the driver on kubuntu without getting errors?

My wireless card is Realtek 8192CE.
[Here is the download page for the driver, in case I missed something.]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CE-VA4")
I am dual-booting Kubuntu/Windows 7 x64bit.

If there is any more information please let me know.

---

### Post by roton on 2011-01-04
Just save the linux driver file to your windows partition or a usb drive. Then boot into linux and either mount your windows partition or put in the usb drive.
Lastly, install the drivers (there are plenty of guides online on how to install tar.gz files).

---

### Post by Tim-Tim on 2011-01-04
> **roton said:**
> Just save the linux driver file to your windows partition or a usb drive. Then boot into linux and either mount your windows partition or put in the usb drive.
Lastly, install the drivers (there are plenty of guides online on how to install tar.gz files).

I know how to install tar.gz files.  And I did try to install the driver on my linux partition.  The problem is, I just installed kubuntu and I don't have necessary packages installed.  My question is, how do I know which packages I need to download and install before trying to install the driver again?

---

### Post by PatchesTheCaveman on 2011-01-04
You might already have gcc installed.  It comes on a default Ubuntu installation.  (Not sure about Kubuntu though.)

Try running
```
gcc --version
```
If it output's gcc's version, you're golden.  If not, downloading it might be tricky.

If it works, all you'll need are the kernel headers for your kernel version.  Figure out your kernel version by running
```
uname -r
```
Then, download the appropriate linux-headers package from [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/)

If you need to download gcc packages, you can follow the instructions I provided here to figure out the download URLs of the necessary packages:
[http://ubuntuforums.org/showpost.php?p=10313431&postcount=53](http://ubuntuforums.org/showpost.php?p=10313431&postcount=53)

---

### Post by Tim-Tim on 2011-01-05
> **PatchesTheCaveman said:**
> 
Figure out your kernel version by running
```
uname -r
```
Then, download the appropriate linux-headers package from [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/)

I did that and came up with:
```
2.6.32-24-generic
```

And when I went to that page, there were two links to the headers
[block-modules-2.6.32-24-generic-di_2.6.32-24.42_amd64.udeb]("http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/block-modules-2.6.32-24-generic-di_2.6.32-24.42_amd64.udeb")
and
[block-modules-2.6.32-24-generic-di_2.6.32-24.43_amd64.udeb]("http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/block-modules-2.6.32-24-generic-di_2.6.32-24.43_amd64.udeb")

Which one do I download?  I tried both of them and got some error regarding something about kernel dependencies.  I'll poat the exact message if you would like.

Edit:  I switched over to just plain ubuntu to skip over the gcc issues.

---

### Post by PatchesTheCaveman on 2011-01-05
That's because you wanted the *linux-headers* package, not the *block-modules* package.

Here is the correct download:  [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-24-generic_2.6.32-24.42_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-24-generic_2.6.32-24.42_amd64.deb)

---

### Post by Tim-Tim on 2011-01-06
[QUOTE=PatchesTheCaveman;10322208]That's because you wanted the *linux-headers* package, not the *block-modules* package.

Sorry about that, I didn't realize that it continued on past block modules.  Alright, so I downloaded and installed the generic headers package just fine, when I enter in
```
make install
```
It starts to compile and then I get this error
```
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/tyler/Desktop/rtl8192ce_linux_2.6.0005.1116.2010/HAL/rtl8192'
make: *** [install] Error 2
```
Then the compiling halts to a stop.  Does that mean I should download the linux kernel image from that same link as well?  Or am I completely off the mark?

---

### Post by PatchesTheCaveman on 2011-01-07
You need to run that command with sudo, e.g.
```
sudo make install
```

You might need to run the *make* command with sudo as well.

---

### Post by Tim-Tim on 2011-01-07
> **PatchesTheCaveman said:**
> You need to run that command with sudo, e.g.
```
sudo make install
```

You might need to run the *make* command with sudo as well.

I tried both of them as well, and I still get the same error.

---

