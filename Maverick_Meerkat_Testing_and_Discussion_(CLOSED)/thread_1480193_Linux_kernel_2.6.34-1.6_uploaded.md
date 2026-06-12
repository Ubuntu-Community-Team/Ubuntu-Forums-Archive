---
title: "Linux kernel 2.6.34-1.6 uploaded"
date: 2010-05-11
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by int on 2010-05-11
> 
We have just uploaded the first Maverick linux kernel.  This was most
recently rebased on the upstream 2.6.34-rc7 kernel.  Please note the new
version and the ABI:

   [https://www.launchpad.net/ubuntu/+source/linux/2.6.34-1.6](https://www.launchpad.net/ubuntu/+source/linux/2.6.34-1.6)

Thanks,
Leann.

---

### Post by portis on 2010-05-11
Yes, it's still under compilation.
I'm using 2.6.34-1.5 from maintainer's PPA.
So far so good.

---

### Post by fluteflute on 2010-05-11
Failed to build on amd64 which is what my install is...

---

### Post by Tompalaz on 2010-05-11
Everything works fine here with the debs from ubuntu mainline.
My wireless won't work though. 

I have a Broadcom

---

### Post by LKjell on 2010-05-11
That would be nice. Just hope it does not have network problems like the other in that series.

---

### Post by dino99 on 2010-05-12
2.6.34-1-generic-pae: 

pcieport 0000:00:01.0: Failed to receive control of PCIe PME service: no _OSC support
pcie_pme: probe of 0000:00:01.0:pcie01 failed with error -13

---

### Post by dino99 on 2010-05-12
new built: 2.6.34-2.6~10.04~ricotz1

---

### Post by screaminj3sus on 2010-05-12
> **Tompalaz said:**
> 

I have a Broadcom

broadcomm = ](*,)

---

### Post by jppr on 2010-05-12
[https://launchpad.net/ubuntu/maverick/+source/linux/2.6.34-2.7](https://launchpad.net/ubuntu/maverick/+source/linux/2.6.34-2.7)

---

### Post by Tompalaz on 2010-05-13
> **screaminj3sus said:**
> broadcomm = ](*,)
I know, plug an pray [-o<
With the bcmwl-kernel-source installed, it plays nicely with me.
But I'm always unable to try new kernels.

---

### Post by vikrant82 on 2010-05-13
> My wireless won't work though. 

I have a Broadcom

You should be able to install (and build) bcmwl-kernel-source if you copy some header files to appropriate place in mainline kernels.

For e.g. all I have to do is copy 4 header files from ```
/usr/src/linux-headers-2.6.34-020634rc7-generic/include/generated/
``` to ```
/usr/src/linux-headers-2.6.34-020634rc7-generic/include/linux/
``` and I am able to install bcmwl-kernel-source. It successfully builds and installs ```
/lib/modules/2.6.34-020634rc7-generic/updates/dkms/wl.ko
```

Good luck :)

---

### Post by plun on 2010-05-13
Meta package built and out..

[https://lists.ubuntu.com/archives/maverick-changes/2010-May/000140.html](https://lists.ubuntu.com/archives/maverick-changes/2010-May/000140.html)

---

### Post by Tompalaz on 2010-05-13
> **vikrant82 said:**
> You should be able to install (and build) bcmwl-kernel-source if you copy some header files to appropriate place in mainline kernels.

For e.g. all I have to do is copy 4 header files from ```
/usr/src/linux-headers-2.6.34-020634rc7-generic/include/generated/
``` to ```
/usr/src/linux-headers-2.6.34-020634rc7-generic/include/linux/
``` and I am able to install bcmwl-kernel-source. It successfully builds and installs ```
/lib/modules/2.6.34-020634rc7-generic/updates/dkms/wl.ko
```

Good luck :)

Awsome, worked like a charm!
Thank you

---

### Post by wojox on 2010-05-13
I don't have Linux kernel 2.6.34-1.6 

I have Linux kernel 2.6.34-2.1 sitting in limbo (unmet dependencies)

I'm currently running 2.6.32-22-generic


Is this normal behavior for testing? This is my first time at it.

Is there something I can do to resolve those unmet dependencies for 2.6.34-2.1?

I should probably just sit tight for now huh?

---

### Post by ranch hand on 2010-05-14
wojox
You are fine.  They are getting their newer kernel from a ppa on launchpad.

We just started this cycle so what we are running is pretty much 10.04 which uses the .32 kernel.  I read that we are supposed to, eventually, be running .35.

There will be a lot of kernel upgrades coming down the pipe here directly.  Expect breakage.  Have FUN.

The kernel sitting on the repo will shake loose soon enough.  Don't, as the y say around here, getcher panties in a twist.

---

### Post by wojox on 2010-05-14
Cool, thanks ranch hand.

---

### Post by ranch hand on 2010-05-14
> **wojox said:**
> Cool, thanks ranch hand.
My first testing cycle was 9.10 so I know how confusing this can be.

The best advice I ca ngive you is learn to do all your updates with apt.  Do not use
```

sudo apt0get dist-upgrade

```
which will install some held back packages until you know it is safe to do so.

Learn to chroot.

I really hope you are not using this as your production OS and that you have a stable Ubuntu installed somewhere (it is a lot quicker to chroot if you do not have to boot to a live CD).

Breakage will occur and the only thing you can do is keep updating, which can be done in recovery mode if you are lucky (instead of chroot), until it is fixed.

File bugs.  That is what we are here for.  Our job is to break it, file bugs, let the devs fix it.

Read the STICKIES.  By the end of this you will be very tired of folks that don't and do things like use Update Mangler for partial upgrades when there is a sticky (real well written) explaining why this is stupid most of the time.

---

### Post by wojox on 2010-05-14
Thanks for the advice. I'll go over that stuff.

This is my Desktop machine. I dual boot with Fedora 12.

My Laptop and Server are production though.

Thanks again. :)

---

### Post by ranch hand on 2010-05-14
That is nice.  You should be able to get to files and such through Fedora and chroot in from there if you have to.

I have all my stuff on one computer.  Right now I am on 9.04 on my main internal.  During the day I turn this drive, and usually the other internal, off in bios and run the testing OS as my production OS from a dual HDD external enclosure with a number of installs so that I have some "throw aways" to test iffy upgrades (all of them) on before it hits the install I use.

I, perhaps foolishly, trust the devs to catch anything that will fry my hardware (MB etc) but I really do not want the test platform in contact with my stable stuff.  I have a couple stable installs on the test platform.  Two 320GB HDDs gives you room for a lot of installs.

---

### Post by DougieFresh4U on 2010-05-14
I have seen the **2.6.34.2.7** kernel around. But in Synaptic, I see it says Lucid after the kernel :confused:

---

### Post by plun on 2010-05-14
> **DougieFresh4U said:**
> I have seen the **2.6.34.2.7** kernel around. But in Synaptic, I see it says Lucid after the kernel :confused:

2.6.34-2.9 is available with Synaptic.

[https://lists.ubuntu.com/archives/maverick-changes/2010-May/000184.html](https://lists.ubuntu.com/archives/maverick-changes/2010-May/000184.html)

Search for linux-image and linux-headers


A dist-upgrade from terminal will probably also fix this. Already running this kernel.

---

### Post by DougieFresh4U on 2010-05-14
> **plun said:**
> 2.6.34-2.9 is available with Synaptic.

[https://lists.ubuntu.com/archives/maverick-changes/2010-May/000184.html](https://lists.ubuntu.com/archives/maverick-changes/2010-May/000184.html)

Search for linux-image and linux-headers


A dist-upgrade from terminal will probably also fix this. Already running this kernel.

Good morning plun.
Thanks :)

---

### Post by LKjell on 2010-05-14
Just to be sure but the nouveau that is in lucid is it compatible with the kernel?

---

### Post by plun on 2010-05-14
> **LKjell said:**
> Just to be sure but the nouveau that is in lucid is it compatible with the kernel?

Well, I am not using Nouveau and have no interest for that software.

Works perfectly with nVidias driver !

---

### Post by jppr on 2010-05-14
Works perfectly with Nouveau :popcorn:

---

### Post by Longinus00 on 2010-05-14
> **plun said:**
> Well, I am not using Nouveau and have no interest for that software.

Works perfectly with nVidias driver !

What an incredibly helpful post! I'm sure LKjell appreciates the answer.

---

### Post by plun on 2010-05-14
> **Longinus00 said:**
> What an incredibly helpful post! I'm sure LKjell appreciates the answer.

Ok... sorry for that.

I just define Nouveau as pure crap...!

---

### Post by taavikko on 2010-05-14
> **plun said:**
> 
I just define Nouveau as pure crap...!

At least something works compared to binary blob
on 330m

-Brightness control
-Resolution (nvidia doesn't recognize dfp correctly)

---

### Post by LKjell on 2010-05-14
Well I do not mind. Just want to make sure that it does not bork my comp when I install the new kernel. I've heard a lot of unfriendly backward compatible.

---

### Post by donniezazen on 2010-05-14
Latest kernel broke my network device (Broadcom in Dell E1505).

The biggest lesson i have learned in testing Ubuntu is never delete the old kernel files. They come handy. Hope they fix it soon. I just loaded old kernel from the grub menu and it worked for now.

---

### Post by rubenverweij on 2010-05-14
> **jppr said:**
> Works perfectly with Nouveau :popcorn:
Could you please tell me how? I have version 1:0.0.15+git20100219+9b4118d-0ubuntu5 installed and my dual head isn't recognised, it seems I'm back to vesa. Shouldn't we wait for the drivers to be updated? The old drivers aren't compatible with this kernel I believe.
> On Monday, nouveau git tree went straight from 2.6.32 to 2.6.34-rc2. One backlight API change in 2.6.34-rc2 breaks compatibility with older kernels (< 2.6.34-rc2), so people doing out-of-tree builds will have to update their kernel to rc2. Alternatively, you could try to revert the backlight commit. 
(from [http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/))

---

### Post by LKjell on 2010-05-14
> **soham_1207 said:**
> Latest kernel broke my network device (Broadcom in Dell E1505).

The biggest lesson i have learned in testing Ubuntu is never delete the old kernel files. They come handy. Hope they fix it soon. I just loaded old kernel from the grub menu and it worked for now.

I have not tested the maverick one yet. But those I have tested the network works just that the speed is decreased a lot. I can't download and upload with the same speed.

---

### Post by lonniehenry on 2010-05-14
updated to 2.6.34-2-generic and it broke wireless.  I was using a Mvix Nubbin (appears as a Dlink) which uses a ralink driver and worked with 2.6.32 kernal in maverick and lucid if I blacklisted the rt2800usb.  I plug in an older Linksys G-usb wireless and it connects using the linksys.  If I check networks in NM it shows the connection using linksys and it shows the Nubbin as a Ralink with device not ready.  How do I go about figuring out what to do to make this work with the new kernel?
Thanks in advance.

---

### Post by Slug71 on 2010-05-17
2.6.34 has been released.

---

### Post by imamdxl on 2010-06-02
I am Ubuntu 9.10 and want to use 2.6.34.
any info

---

### Post by moviemaniac on 2010-06-02
@imamdxl: [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

---

### Post by imamdxl on 2010-06-02
Thanks!

but is there any prebuild kernel deb because I don't wana compile

---

### Post by moviemaniac on 2010-06-02
There you go: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by imamdxl on 2010-06-02
Thanks buddy.
I will try lucid one.

---

### Post by zika on 2010-06-02
> **imamdxl said:**
> Thanks buddy.
I will try lucid one.We will not have "maverick" in mainline (2.6.34 or 2.6.35) for quite some time... Am I wrong?

---

### Post by andrewthomas on 2010-06-02
> **zika said:**
> We will not have "maverick" in mainline (2.6.34 or 2.6.35) for quite some time... Am I wrong?
You are correct.  If I remember correctly, they only build the mainline kernels against the headers from stable repos

---

