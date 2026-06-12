---
title: "Lost wireless internet after lastest set of updates"
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by BaffledMollusc on 2006-06-16
I just downloaded that huge set of updates that arrived, and when I rebooted I had no ability to connect to the internet.

Since one of the updates was a new kernel (2.6.15-25-amd64-k8 ) I went back to the old one (2.6.15-23-amd64-k8 ) and immediately had internet connectivity again.

I'm using the 64-bit version of Ubuntu, my wireless adapter has a Texas Instruments ACX111 chipset, and I'm using WEP encryption. I'm not using ndiswrapper since WEP support for the ACX111 seems to be built into the latest kernel (well, the x.23 one at least, I'm now doubting the x.25 one).

Has anyone else had this problem? Does anyone know what the problem is with the  new kernel?

---

### Post by DeadEyes on 2006-06-16
I experienced problems too. I had to use modprobe to remove the acx and reinstall ndiswrapper.
It gave me a bit of a fright when I rebooted and the srcipt I use to connect to the net starting throwing errors.

---

### Post by BaffledMollusc on 2006-06-16
[QUOTE=DeadEyes]I experienced problems too. I had to use modprobe to remove the acx and reinstall ndiswrapper.
It gave me a bit of a fright when I rebooted and the srcipt I use to connect to the net starting throwing errors.[/QUOTE]
Do you need ndiswrapper? Like I said, my acx111 was working fine with the built-in kernel driver; I didn't need to wrap the Windows driver.

So I don't think it is an ndiswrapper problem for me. Besides, I've upgraded kernels before without problems; it's just this latest one that does weird stuff.

---

### Post by JSVH on 2006-06-16
I am having the same problem too, I am have a Dell inspiron 8200 with a Truemobile 1180 that I got working with ndiswrapper. I tried removing and reinstalling ndiswrapper, no luck. I am now just planning to boot into 2.6.15-23 from now on.

---

### Post by Mr. Picklesworth on 2006-06-16
Same here.

Looks like a serious and wide-spread problem, and it can hopefully be fixed for everyone. (We'll just hope they all have an alternative means to connect to the Internet and that the developers have pulled the update since breaking someonething which also breaks the ability to get a fix for it is a big problem).

The problem apparently is the kernel and it doesn't seem to change with what version of ndiswrapper we're on. (BTW: Does anyone know why Ubuntu uses such an old version? Methinks they don't care about wireless :P ).

Try using the older kernel. If you're using a Grub, it's pretty easy (the one with 13 instead of 15...), and if you're not, I don't know how.

---

### Post by BaffledMollusc on 2006-06-16
[QUOTE=BaffledMollusc]Do you need ndiswrapper? Like I said, my acx111 was working fine with the built-in kernel driver; I didn't need to wrap the Windows driver.

So I don't think it is an ndiswrapper problem for me. Besides, I've upgraded kernels before without problems; it's just this latest one that does weird stuff.[/QUOTE]
Okay, replying to my own problem with the solution in case it helps other people.

After lots of searching various bug reports over the past few months, I added the following line to my /etc/modprobe.d/options file:

**options acx firmware_ver=1.2.1.34**

As near as I can tell, this instructs the acx driver to use the 1.2.1.24 version of the firmware rather than the default 2.3.1.31 version (found in /lib/firmware/acx). Why this is necessary in the new kernel and not the old one is a mystery to me, if indeed this change is doing what I think it's doing.

Still, my wireless appears to work now.

---

### Post by rosslaird on 2006-06-17
ndiswrapper compiles itslef against the currnetly running kernel. When you upgrade the kernel, the driver no longer works (this is why rebooting into the old kernel does work). Every time you upgrade your kernel you also have re-compile ndiswrapper:

1. make sure you have the kerrnel headers for the new kernel
(such as by doing "sudo apt-get install linux-headers-$(uname -r)"

2. Go into the sources directory for ndiswrapper and type:
./configure
make
sudo make install

3. Use ndisgtk (get it from apt) to remove the old driver and reinstall it again.

No reboot required.

Ross

---

### Post by Mr. Picklesworth on 2006-06-17
Thanks, Ross.
I wonder if that could ever be simplified for those as daft as me but with only Ubuntu's wireless stuff to connect to the Internet...

Edit:
Actually, it's proving to be more trouble than I expected. I can't find linux-headers for 2.6.15-25, even at packages.ubuntu.com, so I can't compile it.

I guess ndiswrapper on the install CD wouldn't work either since it's compiled on the previous kernel, but that's the one that the package manager wants. (EEk!)

Lol, I'll bet this confusion happens every time the kernel is updated :P

---

### Post by beanlover on 2006-06-17
I also updated with the large update and lost my wireless as well.

I did the change to /etc/modprobe.d/options as described above and it worked well for me.

I didn't have an "acx" directory in my /lib/firmware directory so I had to create that and a subdir named 1.2.1.34.  Into there I copied the contents of /usr/src/acx-fw/fw/acx111_1.2.1.34 (the location on your machine may vary...use "locate 1.2.1.34" and you should be able to find it pretty easily).

Hope this helps others...I'm glad to get off of using ndiswrapper although I love the idea and thank the developers of it very much as it was very useful to me in the past.

B

---

### Post by NahOlos on 2006-06-17
Same with me. I updated yesterday and... oh boy. Wireless network is gone and I do not know how to fix it. I used the old kernel 23 instead of the 25 using grub and my network works again ;-)

So it is definitely the 25 which might expect a different version of the ipwxxxx driver?

---

### Post by Mr. Picklesworth on 2006-06-18
Upon removing my old ndiswrapper and attempting to reconfigure it, I am getting  error -22 at modprobe ndiswrapper.
/lib/blah/modules/ndiswrapper/ndiswrapper.ko (sorry, my file path is completely wrong. It's ndiswrapper.ko, anyway) is missing... I don't think that was my fault, and I'm sure it should have fixed itself upon reinstalling the driver (twice).
Having trouble finding what error -22 means; I'll try again in the morning.

Anyone else getting problems with freshly configuring ndiswrapper on the old kernel, or is it only me that has gone and messed it up this time?

---

### Post by siguy on 2006-06-20
This is a horrible foul up. I spent a solid week getting my wireless working the first time on 6.06. I really don't want to have to go through all this junk again.

I have a dell truemobile and though I have ndiswrapper installed, I wasn't using it, so I have no idea why reinstalling it would fix anything.

---

### Post by Mr. Picklesworth on 2006-06-20
I installed the latest version of ndiswrapper from source using the (finally!) available linux-headers package for the new kernel and it now works. Looks like a recompiled ndiswrapper wasn't given out with the kernel update, which is likely what caused some of these problems.

---

