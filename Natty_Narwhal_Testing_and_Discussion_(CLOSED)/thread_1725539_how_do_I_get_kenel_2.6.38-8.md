---
title: "how do I get kenel 2.6.38-8?"
date: 2011-04-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by beew on 2011-04-09
As the title says I am keeping up with all the updates but I am still on 2.6.38-7

> mb@test:~$ uname -r
2.6.38-7-generic
I think the most up to date kernel should be 2.6.38-8, right? For one thing the braodcom wireless driver seem to require 2.6.38-8 to build.

Thanks.

---

### Post by Harry33 on 2011-04-10
> **beew said:**
> As the title says I am keeping up with all the updates but I am still on 2.6.38-7
I think the most up to date kernel should be 2.6.38-8, right? For one thing the braodcom wireless driver seem to require 2.6.38-8 to build.
Thanks.

This is the Launchpad link where you can find the latest 2.6.38-8.41 kernel.
First choose your architecture (from "Builds"), 32-bit or 64-bit.

Here:
[https://launchpad.net/ubuntu/+source/linux/2.6.38-8.41](https://launchpad.net/ubuntu/+source/linux/2.6.38-8.41)

The latest kernel is also in official Natty repositories and you already should have received it through Update-Manager.
See from Synaptic, can you find it from the list.

---

### Post by andrew.46 on 2011-04-10
Or live on the bleeding edge:

```
andrew@skamandros~$ uname -r
2.6.39-rc2-ads
```

:)

---

### Post by VinDSL on 2011-04-10
> **andrew.46 said:**
> Or live on the bleeding edge:

```
andrew@skamandros~$ uname -r
2.6.39-rc2-ads
```

:)

Heh!  :D

```
vindsl@Zuul:~$ uname -a
Linux Zuul 2.6.39-999-generic #201104091127 SMP Sat Apr 9 12:55:05 UTC 2011 i686 i686 i386 GNU/Linux

```

---

### Post by VinDSL on 2011-04-10
> **beew said:**
> I think the most up to date kernel should be 2.6.38-8, right? [...]

I'd try the mainline kernel...

Linkage:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.2-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.2-natty/)


Sorry for being rudimentary (you probably have your own method), but...

For my machine, I'd download...

```
linux-headers-2.6.38-02063802-generic_2.6.38-02063802.201103281246_**[COLOR="Red"]i386.deb[/COLOR]**
linux-headers-2.6.38-02063802_2.6.38-02063802.201103281246_**[COLOR="red"]all.deb[/COLOR]**
linux-image-2.6.38-02063802-generic_2.6.38-02063802.201103281246_**[COLOR="red"]i386.deb[/COLOR]**
```

I put them in ~/home/<username>/Downloads/Kernel

Open a terminal, navigate to that folder, then...

```
sudo dpkg -i *.deb
```

Some ppl swear by mainline kernels, and I'm becoming a believer.

I've been installing the dailys lately, and haven't had any problems!

---

### Post by andrew.46 on 2011-04-10
> **VinDSL said:**
> 

```
Linux Zuul**[COLOR="Red"] 2.6.39-999-generic #201104091127[/COLOR]** SMP Sat Apr 9 12:55:05 UTC 2011 i686 i686 i386 GNU/Linux

```

I have not seen that naming convention, is that from a PPA with rc2 or is it a daily build a bit closer to the bleeding edge? (The date seems to suggest a daily build). I will have to say on my own system 2.6.39-rc2 has been very, very stable... mine is a vanilla kernel from [http://www.kernel.org/](http://www.kernel.org/)...

---

### Post by VinDSL on 2011-04-10
> **andrew.46 said:**
> I have not seen that naming convention, is that from a PPA with rc2 or is it a daily build a bit closer to the bleeding edge?
Yep, I'm running dailys.

From the build log, for that kernel...

```
commit:94c8a984ae2adbd9a9626fb42e0f2faf3e36e86f series:natty abinum:999 ...
full_version<2.6.39-rc2>
version<2.6.39>
long<v2.6.39-rc2-120-g94c8a98>
abinum<999>
```

If you wanna play:  :D

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by beew on 2011-04-10
Thanks for all the suggestions. However I thought this should be in the repo because it seems that my wireless driver expects it.

See this thread.[http://ubuntuforums.org/showthread.php?t=1723376&page=3](http://ubuntuforums.org/showthread.php?t=1723376&page=3)

There was no mention of installing 2.6.38-8 via ppa other sources. just simple sudo apt-get install. Am I missing something? (that wouldn't work because I can't find the 2.6.38-8 kernel in synaptic)

---

### Post by MAFoElffen on 2011-04-10
> **VinDSL said:**
> Yep, I'm running dailys.

From the build log, for that kernel...

```
commit:94c8a984ae2adbd9a9626fb42e0f2faf3e36e86f series:natty abinum:999 ...
full_version<2.6.39-rc2>
version<2.6.39>
long<v2.6.39-rc2-120-g94c8a98>
abinum<999>
```If you wanna play:  :D

[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
Curious now.... How would that work for me if I wanted to play with the natty linux2.6.3x.x-generic**-pae** kernels?

Seems to me a new entertaining challenge.

---

### Post by Harry33 on 2011-04-10
> **beew said:**
> Thanks for all the suggestions. However I thought this should be in the repo because it seems that my wireless driver expects it.
...
There was no mention of installing 2.6.38-8 via ppa other sources. just simple sudo apt-get install. Am I missing something? (that wouldn't work because I can't find the 2.6.38-8 kernel in synaptic)

The latest 2.6.38-8.41 kernel is in Natty official repos.
Perhaps you should try downloading from the main server repositories.
This kernel has been there from 6th April.

---

### Post by beew on 2011-04-10
> **Harry33 said:**
> The latest 2.6.38-8.41 kernel is in Natty official repos.
Perhaps you should try downloading from the main server repositories.
This kernel has been there from 6th April.

Ok, Checked Synaptic and the kenel 2.6.38-8.22 appeared to be installed (yes, I use the main server repo)

But runing unname -r in the terminal  I still get

> $ uname -r
2.6.38-7-generic


---

### Post by cecilpierce on 2011-04-10
That has happen to me a few times, don't know why but check and see if all 3 files are there in synaptic.

---

### Post by KegHead on 2011-04-10
Hi!

Thanks to VinDSL 

I'm up to date!

KegHead

---

### Post by VinDSL on 2011-04-10
> **cecilpierce said:**
> That has happen to me a few times, don't know why but check and see if all 3 files are there in synaptic.
Another possibility...

When I first installed 2.6.39-999, Grub2 stuck it in "Previous versions", thus hid it from view at boot.

So, maybe 2.6.38-8 is playing hide n' seek?!?!?!?


> **KegHead said:**
> Hi!

Thanks to VinDSL 

I'm up to date!

KegHead

You're welcome!  ;)

---

### Post by beew on 2011-04-10
Linux kernel 2.6.38-8.41 and all the header files are installed based on Synaptic. But uname -r still says that I have 2.6.38-7 (and so does the boot menu)

What am I missing?

I think this is the reason why wireless isn't working.

[http://ubuntuforums.org/showthread.php?t=1723376](http://ubuntuforums.org/showthread.php?t=1723376)

---

### Post by nm_geo on 2011-04-10
> **beew said:**
> Linux kernel 2.6.38-8.41 and all the header files are installed based on Synaptic. But uname -r still says that I have 2.6.38-7 (and so does the boot menu)

What am I missing?

I think this is the reason why wireless isn't working.

[http://ubuntuforums.org/showthread.php?t=1723376](http://ubuntuforums.org/showthread.php?t=1723376)

Are you dual booting from 10.10 or Lucid 10.04 as the main boot?  I am and sometimes I forget to update grub on the version that controls grub.
Just a thought!

---

### Post by beew on 2011-04-10
> **nm_geo said:**
> Are you dual booting from 10.10 or Lucid 10.04 as the main boot?  I am and sometimes I forget to update grub on the version that controls grub.
Just a thought!

Yes I am and Maverick is controlling grub. But I have never had to update grub in Maverick before to have new kernel in Natty showing up in the boot menu.  Also the output of the unname -r command should not have anything to do with it.

But anyway I will update grub in Mav and see what happens. Thanks for the suggestion.

---

### Post by beew on 2011-04-10
> **nm_geo said:**
> Are you dual booting from 10.10 or Lucid 10.04 as the main boot?  I am and sometimes I forget to update grub on the version that controls grub.
Just a thought!

Oh! What do I know. Just updated grub in Maverick as you said and everything works now. uname -r reports the kernel version correctly and my wireless is working. Learn something new everday. :)

I just don't understand why I didn't have to do this for previous kernel upgrades. Thanks a ton!

---

### Post by andrew.46 on 2011-04-11
Has anybody tried compiling the kernel from source? I have been doing this routinely for a while now but on my *other* distro, not Ubuntu....

---

### Post by Harry33 on 2011-04-11
> **beew said:**
> Oh! What do I know. Just updated grub in Maverick as you said and everything works now. uname -r reports the kernel version correctly and my wireless is working. Learn something new everday. :)
I just don't understand why I didn't have to do this for previous kernel upgrades. Thanks a ton!

So you can make this thread SOLVED.

BTW. There is a new kernel subversion in Launchpad (2.6.38-8.42).
Here:
[https://launchpad.net/ubuntu/natty/+source/linux/2.6.38-8.42](https://launchpad.net/ubuntu/natty/+source/linux/2.6.38-8.42)

---

### Post by VinDSL on 2011-04-11
> **Harry33 said:**
> So you can make this thread SOLVED.

BTW. There is a new kernel subversion in Launchpad (2.6.38-8.42).
Here:
[https://launchpad.net/ubuntu/natty/+source/linux/2.6.38-8.42](https://launchpad.net/ubuntu/natty/+source/linux/2.6.38-8.42)
That's amazing...

I just did an omnibus update, and 2.6.38-8.42 was in there.

There were also a zillion other updates... Banshee, CPP, Firefox, g++. gir1.2, grub, dozens of libraries, modemmanager, mouse tweaks, os-prober, overlay-scrollbar, pulseaudio, blah, blah, blah...

I *thought*... If 2.6.39-999 (2.6.39 rc2) boots, it'll be a miracle.

Well, it was a miracle, but it booted.  :D

OK, I'm going to go update the daily mainline kernel.  If it builds, it be be another miracle.  LoL!

Wish me luck!

---

### Post by VinDSL on 2011-04-11
Dude!  This thing is flying!

The build went well...

```

vindsl@Zuul:~$ cd Downloads
vindsl@Zuul:~/Downloads$ cd Kernel
vindsl@Zuul:~/Downloads/Kernel$ sudo dpkg -i *.deb
[sudo] password for vindsl: 
(Reading database ... 243222 files and directories currently installed.)
Preparing to replace linux-headers-2.6.39-999 2.6.39-999.201104091127 (using linux-headers-2.6.39-999_2.6.39-999.201104110905_all.deb) ...
Unpacking replacement linux-headers-2.6.39-999 ...
Preparing to replace linux-headers-2.6.39-999-generic 2.6.39-999.201104091127 (using linux-headers-2.6.39-999-generic_2.6.39-999.201104110905_i386.deb) ...
Unpacking replacement linux-headers-2.6.39-999-generic ...
Preparing to replace linux-image-2.6.39-999-generic 2.6.39-999.201104091127 (using linux-image-2.6.39-999-generic_2.6.39-999.201104110905_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.39-999-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
Setting up linux-headers-2.6.39-999 (2.6.39-999.201104110905) ...
Setting up linux-headers-2.6.39-999-generic (2.6.39-999.201104110905) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
 * dkms: running auto installation service for kernel 2.6.39-999-generic                                                                                                     
 *       nvidia-current (270.30)...                                                                                                                                   [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
Setting up linux-image-2.6.39-999-generic (2.6.39-999.201104110905) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.39-999-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.39-999.201104091127 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.39-999.201104091127 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
 * dkms: running auto installation service for kernel 2.6.39-999-generic                                                                                                     
 *       nvidia-current (270.30)...                                                                                                                                   [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.39-999-generic
Found initrd image: /boot/initrd.img-2.6.39-999-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.10 (10.10) on /dev/sda1
done
vindsl@Zuul:~/Downloads/Kernel$ 

```

Heh!  Let's see if it boots...

---

### Post by lucazade on 2011-04-11
> **VinDSL said:**
> Dude!  This thing is flying!

The build went well...

```

vindsl@Zuul:~$ cd Downloads
vindsl@Zuul:~/Downloads$ cd Kernel
vindsl@Zuul:~/Downloads/Kernel$ sudo dpkg -i *.deb
[sudo] password for vindsl: 
(Reading database ... 243222 files and directories currently installed.)
Preparing to replace linux-headers-2.6.39-999 2.6.39-999.201104091127 (using linux-headers-2.6.39-999_2.6.39-999.201104110905_all.deb) ...
Unpacking replacement linux-headers-2.6.39-999 ...
Preparing to replace linux-headers-2.6.39-999-generic 2.6.39-999.201104091127 (using linux-headers-2.6.39-999-generic_2.6.39-999.201104110905_i386.deb) ...
Unpacking replacement linux-headers-2.6.39-999-generic ...
Preparing to replace linux-image-2.6.39-999-generic 2.6.39-999.201104091127 (using linux-image-2.6.39-999-generic_2.6.39-999.201104110905_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.39-999-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
Setting up linux-headers-2.6.39-999 (2.6.39-999.201104110905) ...
Setting up linux-headers-2.6.39-999-generic (2.6.39-999.201104110905) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
 * dkms: running auto installation service for kernel 2.6.39-999-generic                                                                                                     
 *       nvidia-current (270.30)...                                                                                                                                   [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
Setting up linux-image-2.6.39-999-generic (2.6.39-999.201104110905) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.39-999-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.39-999.201104091127 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.39-999.201104091127 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
 * dkms: running auto installation service for kernel 2.6.39-999-generic                                                                                                     
 *       nvidia-current (270.30)...                                                                                                                                   [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.39-999-generic
Found initrd image: /boot/initrd.img-2.6.39-999-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.10 (10.10) on /dev/sda1
done
vindsl@Zuul:~/Downloads/Kernel$ 

```

Heh!  Let's see if it boots...

.. exploded? :D

---

### Post by VinDSL on 2011-04-11
It booted!

2.6.39 is a snooze!  Never seen such a mellow rc!

You guys ought to try it...

OK, I'm gonna go play Farmville for a while, and get a couple of hours sleep.

Latez!  ;)

---

### Post by nm_geo on 2011-04-11
> **beew said:**
> Oh! What do I know. Just updated grub in Maverick as you said and everything works now. uname -r reports the kernel version correctly and my wireless is working. Learn something new everday. :)

I just don't understand why I didn't have to do this for previous kernel upgrades. Thanks a ton!

Glad that was it !!:P
Like I said it happens to me all the time. i upgrade the testing flavor and forget to update grub on my main booting flavor.  It occurs after a kernel upgrade     2.6.38-9 will require the grub update here too.

---

