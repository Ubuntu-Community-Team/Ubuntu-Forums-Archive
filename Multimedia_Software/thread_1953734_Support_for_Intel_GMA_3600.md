---
title: "Support for Intel GMA 3600?"
date: 2012-04-06
forum: Multimedia Software
---

### Post by petermg on 2012-04-06
I did some googling and seems like my integrated video chip isn't supported in Ubuntu right now.  Do I have any options other than just using the VESA driver that it's defaulted to?  I mean, is there any hope that support will come for this video chip?  Works great in Windows7....  comon' Ubuntu!!!

11.10

---

### Post by Yellow Pasque on 2012-04-06
> **petermg said:**
> Works great in Windows7....  comon' Ubuntu!!!
It's not Ubuntu's/Linux's fault that the GPU maker (PowerVR) won't release code or even documentation..

---

### Post by petermg on 2012-04-07
> **Temüjin said:**
> It's not Ubuntu's/Linux's fault that the GPU maker (PowerVR) won't release code or even documentation..

Does this mean I should try and install this driver?
[https://launchpad.net/ubuntu/+source/powervr-omap3](https://launchpad.net/ubuntu/+source/powervr-omap3)

---

### Post by Yellow Pasque on 2012-04-07
> **petermg said:**
> Does this mean I should try and install this driver?
[https://launchpad.net/ubuntu/+source/powervr-omap3](https://launchpad.net/ubuntu/+source/powervr-omap3)
No. Those packages are for a different GPU (and they use ARM architecture).

---

### Post by h113331pp on 2012-04-08
Let me apologize my poor English,I`m not a native speaker.

So is there a way to get gma 3600 working fine?

I google for a while and find maybe kernel 3.3 could solve the problem.

But when I configure the 3.3 kernel, only see gma 500 support(experiment), should I turn this on?

I`ve tired about the vesa driver, only 4 modes of resolution available : (

---

### Post by iqmaster on 2012-04-10
I have hp mini 210 with gma 3650. I did a 3.4-rc1 custom kernel install hoping I will get X working. but still no luck. Xorg configures automatically with xorg -configure but when I run X, I only get a blank screen. 
any ideas guys

Thanks

---

### Post by klisanor on 2012-04-11
Tried to reconfigure Xorg on my Samsung NC110-P05, Intel n2600 Cedar Trail-M based netbook with GMA 3600 but still no luck. Only 800x600.

---

### Post by h113331pp on 2012-04-12
Just tried meego, and it can work!!!

now I can change my resolution from 1024x576 to 1920x1080.(but now I can`t switch lower such as 

800x600 or 640x480, but who cares?)

I check the kernel and driver, kernel is 3.0.0-4.1-adaptation-pc, driver is pvr_drv.so

Next goal is to find a way to make the kernel and driver can work with ubuntu 12.04.

---

### Post by klisanor on 2012-04-14
I also have 1024x600 on my GMA 3600 on Atom n2600 with MeeGo OS.

I am about to install Lubuntu 11.10, download the latest stable kernel 3.3.1 from kernel.org and build it with GMA 3600 support. Some people say it works!

---

### Post by iqmaster on 2012-04-15
I am despair. Does anyone please has an idea on how to enable acceleration on this card. Atom N2800.
I tried the latest kernel with Arch linux and no luck too.
Does psb/gma500 with fbdev works???
Is there a way to take the closed source driver from the Meego OS?

IQMASTER

---

### Post by klisanor on 2012-04-17
My netbook is Samsung NC110-P05 on Atom n2600 (Cedar Trail-M) with Intel GMA 3600

I compiled lots of kernels and here are the results:
1) stock **3.0.0-17**: only *800x600*
2) latest stable kernel **3.3.2**: works on *1024x600*
3) latest from git **3.4.0-rc3**: works on *1024x600*

I compiled **3.4.0-rc3** (git) this way:
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

I compiled **3.3.2** this way:
```
wget http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.3.2.tar.bz2
tar jxf linux-3.3.2.tar.bz2
cd linux-3.3.2
make menuconfig
#press / to find "3600", enable GMA 3600 support
make-kpkg clean
CONCURRENCY_LEVEL=`getconf _NPROCESSORS_ONLN` fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
cd ..
sudo dpkg -i *.deb
cd /lib/modules && ls # here I take module-name-for-new-kernel for next update-initramfs
sudo update-initramfs -ck module-name-for-new-kernel
sudo update-grub
sudo reboot
```

**BUT!** 
VGA does not work on any of the kernels above
On kernels **3.3.2** and **3.4.0-rc3** my WiFi card does NOT work.

```
sudo ifconfig
eth0      Link encap: Ethernet  HWaddr *********
lo        Link encap: Local Loopback
```

My WiFi card is:
```
lspci | grep Network
01:00.0 Network controller: Intel Corporation Centrino Wireless-N 130 (rev 34)
```

I tried to download the latest iwlwifi ucode from Intel ([http://intellinuxwireless.org/](http://intellinuxwireless.org/)), but still have no luck
```
cd $HOME
#check latest iwlwifi version here: http://intellinuxwireless.org/?n=Downloads
wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6000g2b-ucode-18.168.6.1.tgz
tar -zxf iwlwifi-6000g2b-ucode-18.168.6.1.tgz
sudo mv iwlwifi-6000g2b-ucode-18.168.6.1/iwlwifi-6000g2b-6.ucode /lib/firmware/
```

On the kernel installing stage (dpkg -i) I also had these warnings:
```
"W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168f-2.fw for module r8169"
"W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168f-1.fw for module r8169"
```

```
ls /lib/firmware/rtl_nic/
rtl8168d-1.fw, rtl8168d-2.fw, rtl8168e-1.fw, rtl8168e-2.fw, rtl8168e-3.fw

```

Indeed I don't have the mentioned above rtl8168f-2, rtl8168f-1.

I can say that my WiFi card is not blocked by other apps. I checked it using rfkill.

---

### Post by iqmaster on 2012-04-17
I tried to get it working with the mainline kernel rc2 and I too had the same problem with wireless.

It is killing me. I am now using Meego OS and it is working really good. I will stick with Meego until someone comes up with a fully functional driver or somehow ports the driver from Meego.

---

### Post by h113331pp on 2012-04-17
BAD NEWS : (

I take gtkperf on meego (using pvr driver) and ubuntu 12.04(using fbdev) both on 1600x1200,

and find out the difference in total time is very very LARGE!

ubuntu12.04 would done in about 15s, but meego is about 190s and more.

I`m very disappointed :( and no reason to get the driver to ubuntu12.04.

---

### Post by iqmaster on 2012-04-18
What you mean by no reason to get the driver to ubuntu12.04.

---

### Post by klisanor on 2012-04-20
After playing around in MeeGo (with working resolution) I got tired of its bugs. Later on I decided to install Debian Wheezy (Testing). After installing Debian I built the latest stable 3.3.2 kernel from kernel.org. Now I have 1024x600 resolution and WiFi works. To get it working I had to put on my USB stick 3 non-free files: 2 *.uboot firmware files for my WiFi card (Intel Wireless Centrino N-130) and 1 file for Ethernet (from Realtek).

It seems like one should put these drivers on the USB stick while installing Ubuntu. I tried to put them to my /lib/firmware/ after Ubuntu install but it didn't work. My kernel was built with turned on "Hotplug firmware loading support". I think there are some other unresolved dependencies.

---

### Post by tenebraefiddler on 2012-04-22
I would like to know if when the 1024x600 resolution work, you have 3d support (as with Meego) or you are still stucked with only 2d graphics.

Is it possible to ?
- Use directly Meego kernel with ubuntu
- Build a Ubuntu chroot environment on Meego (it may be slow with a netbook)

---

### Post by h113331pp on 2012-04-22
It`s possible to use meego`s kernel in 12.04.

and you`ll find that your pc boot on with the framebuffer (not the vesafb)

and you can get into xfce(this is the one I only tested) by using "fbdev" driver

By the way, I did ripped the driver from meego and test it.but I got no luck :(

it will ask you to match the Xorg version(which meego is 1.9.0 and ubuntu is 1.11)

after I recompile my Xorg to 1.9.0 still cannot get the driver working.

just hope Imagination Technologies can release the source code not just the binary driver :(

or we have to wait very long time to get the SGX545 supported.

---

### Post by yfaney on 2012-04-23
I did following that and made it~

Code:
wget [http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.3.2.tar.bz2](http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.3.2.tar.bz2)
tar jxf linux-3.3.2.tar.bz2
cd linux-3.3.2
make menuconfig
#press / to find "3600", enable GMA 3600 support
#exclude everything which contains this string "rtc"
make-kpkg clean
CONCURRENCY_LEVEL=`getconf _NPROCESSORS_ONLN` fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
cd ..
sudo dpkg -i *.deb

but I've got another problem : display getting mad after resuming from sleep mode

plz see attached file

---

### Post by ciccio1210 on 2012-04-24
Same problem after standby...

---

### Post by h113331pp on 2012-04-24
to yfaney:

                so what driver you are using now?is vesa or fbdev?Can the driver change the resolution?

---

### Post by yfaney on 2012-04-26
to ciccio1210 : 
Wow,its not only for me... Finally, we may have to wait new drivers in new kernel...

to h113331pp :
Now Im using gma3600 driver without sleep mode~~~ Waiting new kernel...
Oh,the resolution 1024x600 is available~

---

### Post by r-mo on 2012-04-26
3.3.2 is using fbdev here.  I've actually built without taking out all the rtc modules and wireless does work (this is on an asus 1015cx), it's just network manager doesn't see any of the interfaces.  I configured it before updating the kernel and it's connecting just fine.

---

### Post by r-mo on 2012-04-26
Having said that I get the same scrambled graphics problem when waking up from sleep.

---

### Post by h113331pp on 2012-04-26
to r-mo:
             thanks :) this is really helpful.
 
             I also wander if 3.3.2 use fbdev, could you change resolution by xrandr? or someway to change 
resolution without logout?

              By the way, I`ve used kernel 3.3 previous, and I could not change resolution when using fbdev and only 3 resolution available using vesa.

---

### Post by r-mo on 2012-04-26
I only see 1024x600 in xrandr but that's not surprising as it's all the netbook panel will support.  It's the same if I use the 3.0.0-adaptation kernel from MeeGo.  The meego kernel probably works a bit better but for some reason it's compiled without nfs support which I really need.  I guess recompiling it is a no go? The latest kernel source I can find on the meego site is for 2.6.38

---

### Post by h113331pp on 2012-04-27
Still working to get kernel source from meego

---

### Post by h113331pp on 2012-04-29
to r-mo:

Got the kernel source and patch!

hope this will be helpful for you:

[http://mirrors.kernel.org/meego/updates/1.2.0/repos/oss/source/kernel-adaptation-pc-3.0.0-8.1.src.rpm](http://mirrors.kernel.org/meego/updates/1.2.0/repos/oss/source/kernel-adaptation-pc-3.0.0-8.1.src.rpm)

I also want the nfs and aufs support :)

---

### Post by xceedsys on 2012-04-29
I compile the kernel source, it seems the driver is loaded but when startx, it causes an exception, see below is the Xorg.0.log
and dmesg printout,

it seems that  driver is loaded, as I checked in the source

Edit: bodhi.zazen - removed long log.

Please do not post long blocks of text like that, use attachments.

---

### Post by h113331pp on 2012-04-29
I see some pvr module warning.

maybe you should use the pvr driver and xorg server I ripped from meego in previous post?

I also failed to startx when I only use pvr driver with original xorg server in 12.04 (the version in 12.04 is 1.11.3).

but I do success startx when I both replace the xorg server and pvr driver.(they both are binary file, just replace them)

to [U]xceedsys:

[/U]      oops, sorry I think you are r-mo. and I want to know what the kernel you use? is it 3.3 or 3.0 which I ripped from meego?

I strongly suggest to use the meego`s kernel,.

---

### Post by xceedsys on 2012-04-29
i took these files from 
[http://download.meego.com/live/devel:/cdv/MeeGo_1.2.0_CedarTrail/src/](http://download.meego.com/live/devel:/cdv/MeeGo_1.2.0_CedarTrail/src/)

as i'm not in my other office, i can't check what i have done
basically i use buildroot to compile th whole thing and test it on the board.

I'll try to check tonite.
I can not download from the rapid site, any other place you can put ?

---

### Post by xceedsys on 2012-04-29
I took the kernel from 
[http://download.meego.com/live/devel:/cdv/MeeGo_1.2.0_CedarTrail/src/kernel-adaptation-pc-3.0.0-2.1.src.rpm](http://download.meego.com/live/devel:/cdv/MeeGo_1.2.0_CedarTrail/src/kernel-adaptation-pc-3.0.0-2.1.src.rpm)

and 
[http://download.meego.com/live/devel:/cdv/MeeGo_1.2.0_CedarTrail/src/libx86-1.1-1.1.src.rpm](http://download.meego.com/live/devel:/cdv/MeeGo_1.2.0_CedarTrail/src/libx86-1.1-1.1.src.rpm)

and compile it.
then boot it.

---

### Post by h113331pp on 2012-04-29
to xceedsys:

um... the links you post looks like a little bit old.

the newest kernel is 3.0.0-8.1 and your is 3.0.0-2.1.

I have to say the meego`s office site is really s**k, it mixed out of date files and fresh files around the site.

---

### Post by xceedsys on 2012-04-29
Ya meego site has lots of files every where, maybe it is the version problem,
i try later. I cannot download from the rapidshare it always give error, anywhere you can post thoese files ?

I think my ISP is blocking these sites, I got my friend from
to get for me.

---

### Post by h113331pp on 2012-04-29
to xceedsys:
                      that`s weird. I check the rapidshare links and they still work for me now.

or what share space you use the most? I can also upload file to another place.

I will check this thread after I finished my launch and rest to 13:00(in my place now is 11:52).

Since the MU is gone, it`s very **inconvenient** to share files :(  

F**KING the SOPA!

---

### Post by xceedsys on 2012-04-29
hey, we are in the same time zone, anyway i go my friend from a neighbour country to do it for me, should have it by after lunch

---

### Post by astroman3001gt on 2012-04-30
Hey,

Just bought an ASUS EEEPC 1025c, with an Intel GMA3650.
Just installed Ubuntu 12.04 and I have the same problem with the resolution.

If there is anything that I can try, please let me know.
I see that you are trying different kernels. I never successfully compiled a kernel :) Can you update the instruction and tell me best what kernel version shall I try it?

Thanks,

---

### Post by h113331pp on 2012-05-01
to  astroman3001gt:
                                    Just download the 3 rapidshare files I post above,and replace all of them(the kernel, pvr driver, xorg server, they all are binary files, so you don`t have compile anything).

I assume you know where to put the kernel files(vmlinuz and initrd.gz).

---

### Post by astroman3001gt on 2012-05-01
HI,

I tried to put them in the /boot and changed the grub.cfg. But I think I did something wrong. Can you give me the right instruction?

Thank you

---

### Post by h113331pp on 2012-05-01
> **astroman3001gt said:**
> HI,

I tried to put them in the /boot and changed the grub.cfg. But I think I did something wrong. Can you give me the right instruction?

Thank you

Ubuntu had changed to grub2 since 9.10, and it`s using  /boot/grub/grub.cfg instead /boot/grub/menu.lst. So make sure you are editing the right configure file. 

can you check your grub version?

---

### Post by xceedsys on 2012-05-01
if you are using grub2, below is my example, 
you may need to put video=LVDS-1:d after  /boot/vmlinuz 
if you have problems with the screen. e.g. :
inux   /boot/vmlinuz video=LVDS-1:d root=UUID=bbd8dbf0-31c0-419a-ac2a-3b636cf018b9 ro splash 

you will need to change the uuid : D=bbd8dbf0-31c0-419a-ac2a-3b636cf018b9
to what is in your grub.cfg
also 
and initrd  /boot/initrd0.img

to 
your exist ubunto existing initrd, e.g. initrd  /boot/initrd.img-3.2.0-24-generic-pae 

you can find and figure it out all these are in the existing grub.cfg file itself



### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Ubuntu, with Meego rip' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set=root bbd8dbf0-31c0-419a-ac2a-3b636cf018b9
        linux   /boot/vmlinuz root=UUID=bbd8dbf0-31c0-419a-ac2a-3b636cf018b9 ro splash 
        initrd  /boot/initrd0.img
}

---

### Post by The Rnegade on 2012-05-02
> **petermg said:**
> I did some googling and seems like my integrated video chip isn't supported in Ubuntu right now.  Do I have any options other than just using the VESA driver that it's defaulted to?  I mean, is there any hope that support will come for this video chip?  Works great in Windows7....  comon' Ubuntu!!!

11.10

itntel video cards and sound cards seem to be very hostile towards linux operation systems

---

### Post by astroman3001gt on 2012-05-02
Hi,

Thanks for the help, I will try this later on the night, when I arrive at home ;)

Just to be sure, regarding the xorg 1.9 and the driver. I guess the instructions are just to extract them in /. Right?

---

### Post by h113331pp on 2012-05-02
yes, just extract and replace, this is work when I was using 12.04 beta2 and now.

---

### Post by xceedsys on 2012-05-02
hi h113331pp,
can you side runs opengl ? or hardware accerlation video ?

---

### Post by astroman3001gt on 2012-05-02
Hey,

I tried, but it didn't work...
It got stuck at some point loading the kernel and when trying to mount the partitions...

---

### Post by h113331pp on 2012-05-02
to [xceedsys]("http://ubuntuforums.org/member.php?u=1627004"):
                      I run glxgears and got fps about 300 up, but I `m not sure is this hardware 3d acceleration.
Can you give me some method to try?

I also want to get the picture to prove but I can`t :( because I run the 12.04 in N2800 target board, and I only install so few package  that I can`t use print screen.

to astroman3001gt:
                                I have a feeling that you still not configure your grub.cfg correctly. did the kernel panic happen when boot? if not, I guess it just can`t find the right place to mount your root file system.

---

### Post by Ibidem on 2012-05-02
To check for 3D:
```
glxinfo|grep renderer
```
Will probably say something about SGI, if you're using the in-kernel driver. 
SGI == Software 3d
For the proprietary driver, you might get 3d accel.

Might use scrot for screenshots?  But I suspect that will look sane in the pictures, somehow.
Try hibernating instead of sleep...

Regarding kernels, I'll suggest the same thing I did over in the Debian forums:
```
make; make deb-pkg 
```
Should leave a .deb or few in ../ - install those.
That will work much better than manually installing the kernel or using make-kpkg.

---

### Post by h113331pp on 2012-05-02
To Ibidem:
                  thanks! :) this is what I got:

user@atcs-client:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa X11
GL_EXT_vertex_array_bgra, GL_NV_conditional_render, 

so do I have hardware or software 3D acceleration?

by the way, the meego is build from frdora, so I only got the kernel SRPM package(also post the URL in previous post under the 3 rapidshare files), I suggest to install fedora in VMware and build the kernel in it with fedora`s tool, "rpmbuild" , will be much easier. :)

---

### Post by xceedsys on 2012-05-02
to [h113331pp]("http://ubuntuforums.org/member.php?u=1607977")

thanks, for the reply
i'm can't get those glxgears to show, glxinfo did not show any opengl info, mayby I'm missing something
or did not install.
found this [http://mirrors.kernel.org/meego/updates/1.2.0/images/meego-netbook-ia32-cedartrail/meego-netbook-ia32-cedartrail-1.2.0-update6.iso](http://mirrors.kernel.org/meego/updates/1.2.0/images/meego-netbook-ia32-cedartrail/meego-netbook-ia32-cedartrail-1.2.0-update6.iso)
if anyone like to make a try and post the result.

---

### Post by Yong Khun on 2012-05-02
To [h113331pp]("http://ubuntuforums.org/member.php?u=1607977"),

the fps 300 is high, you should have the hardware acceleration.
I tried install Ubuntu 12.04 LTS (the final desktop release), and the apply the 3 tar balls you provided in the rapidshare, but it could not boot up. The error in the Xorg.0.log shows that no screen detected. Can you share the details steps how you setup your system with such hardware acceleration?

Thanks!

---

### Post by xceedsys on 2012-05-03
when I run there is an error below, any idea ?

and glxinfo gives direct render

$ glxgears
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/tls/pvr_dri.so
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/pvr_dri.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Permission denied)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Permission denied)
drmOpenByBusid: drmOpenMinor returns -13
drmOpenDevice: node name is /dev/dri/card1
drmOpenByBusid: drmOpenMinor returns -1



# glxinfo |grep -render
PVRDRIInitPVR2D: PVR2D device index (0)direct rendering: Yes
OpenGL renderer string: PowerVR SGX545

---

### Post by h113331pp on 2012-05-03
to 120203831:
                        just give what the share space you use in usual, I will update to there.

---

### Post by h113331pp on 2012-05-03
to 120203831:
                       I`m afraid I can`t. these packages are all larger than 10MB, I can`t use mail to send, sorry. :(

astroman3001gt:
                            That might be possible, I`m not sure, I just repeat what I`ve done on my target board before,and this is the step:

1.I put the kernel and initrd.
2.extract and put the kernel module
3.extract and put the xorg
4.extract and put the driver
5.edit the syslinux.cfg(I use syslinux to boot my target board), and don`t forget add  video=LVDS-1:d after  /boot/vmlinuz .

and it works again. by the way , I use the Xfce and gdm instead unity and lightdm.

I still looking to borrow the notebook, once I borrowed one, I will take a tutor video and upload to youtube.

---

### Post by Binary-Synapse on 2012-05-03
Hello.
 
I also cannot resume from standby. Same weird graphic output.
I'm using a Classmate Netbook with Atom N2600, Ubuntu 11.10 with a manually compilled kernel (v3.4-rc5).
 
Any updates or support for this?
 
Thank you

---

### Post by astroman3001gt on 2012-05-03
at h113331pp

I will be waiting for that tutorial on youtube ;)

---

### Post by dbergeba on 2012-05-03
This worked perfect for me! I've been trying to solve this bug for so long! Thanks! At least I con switch to 1024x600 on an Asus EeePC 1011cx with GMA3600.

> **klisanor said:**
> My netbook is Samsung NC110-P05 on Atom n2600 (Cedar Trail-M) with Intel GMA 3600

I compiled lots of kernels and here are the results:
1) stock **3.0.0-17**: only *800x600*
2) latest stable kernel **3.3.2**: works on *1024x600*
3) latest from git **3.4.0-rc3**: works on *1024x600*

I compiled **3.4.0-rc3** (git) this way:
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

I compiled **3.3.2** this way:
```
wget http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.3.2.tar.bz2
tar jxf linux-3.3.2.tar.bz2
cd linux-3.3.2
make menuconfig
#press / to find "3600", enable GMA 3600 support
make-kpkg clean
CONCURRENCY_LEVEL=`getconf _NPROCESSORS_ONLN` fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
cd ..
sudo dpkg -i *.deb
cd /lib/modules && ls # here I take module-name-for-new-kernel for next update-initramfs
sudo update-initramfs -ck module-name-for-new-kernel
sudo update-grub
sudo reboot
```**BUT!** 
VGA does not work on any of the kernels above
On kernels **3.3.2** and **3.4.0-rc3** my WiFi card does NOT work.

```
sudo ifconfig
eth0      Link encap: Ethernet  HWaddr *********
lo        Link encap: Local Loopback
```My WiFi card is:
```
lspci | grep Network
01:00.0 Network controller: Intel Corporation Centrino Wireless-N 130 (rev 34)
```I tried to download the latest iwlwifi ucode from Intel ([http://intellinuxwireless.org/](http://intellinuxwireless.org/)), but still have no luck
```
cd $HOME
#check latest iwlwifi version here: http://intellinuxwireless.org/?n=Downloads
wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6000g2b-ucode-18.168.6.1.tgz
tar -zxf iwlwifi-6000g2b-ucode-18.168.6.1.tgz
sudo mv iwlwifi-6000g2b-ucode-18.168.6.1/iwlwifi-6000g2b-6.ucode /lib/firmware/
```On the kernel installing stage (dpkg -i) I also had these warnings:
```
"W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168f-2.fw for module r8169"
"W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168f-1.fw for module r8169"
``````
ls /lib/firmware/rtl_nic/
rtl8168d-1.fw, rtl8168d-2.fw, rtl8168e-1.fw, rtl8168e-2.fw, rtl8168e-3.fw

```Indeed I don't have the mentioned above rtl8168f-2, rtl8168f-1.

I can say that my WiFi card is not blocked by other apps. I checked it using rfkill.

---

### Post by h113331pp on 2012-05-04
Still no luck :( 
No one want to lend me the notebook.
and some guys write me letters to ask is my work true.
So I offer this video to prove:
[http://youtu.be/SiotNlH8feI](http://youtu.be/SiotNlH8feI)

If still no notebook borrowable, I will consider to use usb HD and usb CD-ROM to make the tutor OR just let it go, I still have a lot of another works to do. :(

---

### Post by astroman3001gt on 2012-05-04
Hey guys,

Just to say that I compiled my first kernel for the first time. It took quite a lot of time, but It works almost perfectly.

I compiled 2) latest stable kernel 3.3.2: like the instructions were presented here.

For know the only problem that I found is that I cannot change the brightness of my screen. It is always at maximum. If someone has any idea about this let me know.

Tomorrow I will test the system better.

To h113331pp: The video was very nice to watch, If you find a notebook, use the camera in the right way  ;)

---

### Post by klisanor on 2012-05-05
Brightness
```
sudo setpci -s "00:02.0" F4.B=**CC**
```
(change the last CC to any number from 00 to FF)

---

### Post by astroman3001gt on 2012-05-05
at klisanor:
Thanks, it works perfectly, just need to be careful to not put 00 :)

---

### Post by kashyapkopparam on 2012-05-08
i tries all the methods, installed ubuntu 6 times... still no luck. meego is also acting weird on my netbook. What to do?

---

### Post by the pwner224 on 2012-05-08
Over here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/934956](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/934956) it says that the fix has been released for the bug. But you people claim that it isn't working. So my question is that if I get a netbook with a GMA 3600 will it work out of the box with Precise Pangolin? Since Launchpad says it is a regression, will it work with Oneiric if it doesn't work with Precise? I don't need it to work perfectly out of the box, as long as there is a way to fix it once Ubuntu is installed.

Thanks.

---

### Post by Ibidem on 2012-05-08
Sorry it took so long getting back to you...

Mesa X11 is another name for the software renderer.
If it mentions the hardware or manufacturer, it's hardware.
(PowerVR SGX545 is hardware)

---

### Post by macktheripper on 2012-05-09
Hi

> **dbergeba said:**
> This worked perfect for me! I've been trying to solve this bug for so long! Thanks! At least I con switch to 1024x600 on an Asus EeePC 1011cx with GMA3600.

What exactly have you done? I have the same netbook, but I still can't switch to 1024x600 with the newest kernel.

Thanks

---

### Post by Deepak A on 2012-05-09
> **yfaney said:**
> I did following that and made it~

Code:
wget [http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.3.2.tar.bz2](http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.3.2.tar.bz2)
tar jxf linux-3.3.2.tar.bz2
cd linux-3.3.2
make menuconfig
#press / to find "3600", enable GMA 3600 support
#exclude everything which contains this string "rtc"
make-kpkg clean
CONCURRENCY_LEVEL=`getconf _NPROCESSORS_ONLN` fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
cd ..
sudo dpkg -i *.deb

but I've got another problem : display getting mad after resuming from sleep mode

plz see attached file



While running the line [CONCURRENCY_LEVEL=`getconf _NPROCESSORS_ONLN` fakeroot make-kpkg--initrd --append-to-version=-custom kernel_image kernel_headers ], it works. but at some point it giving this error....  ERROR STARTS with the line 

"make: the `-j' option requires a positive integral argument"

root@user-desktop:/home/user/linux-3.3.2# CONCURRENCY_LEVEL='getconf_NPROCESSOR_ONLN' fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
exec make kpkg_version=12.036+nmu2 -f /usr/share/kernel-package/ruleset/minimal.mk debian APPEND_TO_VERSION=-custom  INITRD=YES 
====== making target debian/stamp/conf/minimal_debian [new prereqs: ]======
This is kernel package version 12.036+nmu2.
test -d debian             || mkdir debian
test ! -e stamp-building || rm -f stamp-building
install -p -m 755 /usr/share/kernel-package/rules debian/rules
for file in ChangeLog  Control  Control.bin86 config templates.in rules; do                                      \
            cp -f  /usr/share/kernel-package/$file ./debian/;                               \
        done
for dir  in Config docs examples ruleset scripts pkg po;  do                                      \
          cp -af /usr/share/kernel-package/$dir  ./debian/;                                 \
        done
test -f debian/control || sed         -e 's/=V/3.3.2-custom/g'  \
                -e 's/=D/3.3.2-custom-10.00.Custom/g'         -e 's/=A/amd64/g'  \
        -e 's/=SA//g'  \
        -e 's/=I//g'                    \
        -e 's/=CV/3.3/g'                \
        -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g'        \
        -e 's/=ST/linux/g'      -e 's/=B/x86_64/g'    \
                  /usr/share/kernel-package/Control > debian/control
test -f debian/changelog ||  sed -e 's/=V/3.3.2-custom/g'       \
            -e 's/=D/3.3.2-custom-10.00.Custom/g'        -e 's/=A/amd64/g'       \
            -e 's/=ST/linux/g'     -e 's/=B/x86_64/g'         \
            -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g'                            \
             /usr/share/kernel-package/changelog > debian/changelog
chmod 0644 debian/control debian/changelog
test -d ./debian/stamp || mkdir debian/stamp 
make -f debian/rules debian/stamp/conf/kernel-conf
make[1]: Entering directory `/home/user/linux-3.3.2'
====== making target debian/stamp/conf/kernel-conf [new prereqs: ]======
make EXTRAVERSION=-custom   ARCH=x86_64 \
                    oldconfig;
make[2]: Entering directory `/home/user/linux-3.3.2'
scripts/kconfig/conf --oldconfig Kconfig
#
# configuration written to .config
#
make[2]: Leaving directory `/home/user/linux-3.3.2'
make EXTRAVERSION=-custom   ARCH=x86_64 prepare
make[2]: Entering directory `/home/user/linux-3.3.2'
scripts/kconfig/conf --silentoldconfig Kconfig
make[2]: Leaving directory `/home/user/linux-3.3.2'
make[2]: Entering directory `/home/user/linux-3.3.2'
make[3]: Nothing to be done for `all'.
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  CALL    scripts/checksyscalls.sh
make[2]: Leaving directory `/home/user/linux-3.3.2'
echo done > debian/stamp/conf/kernel-conf
make[1]: Leaving directory `/home/user/linux-3.3.2'
make -f debian/rules debian/stamp/conf/full-changelog
make[1]: Entering directory `/home/user/linux-3.3.2'
====== making target debian/stamp/conf/full-changelog [new prereqs: ]======
for file in ChangeLog  Control  Control.bin86 config templates.in rules; do                \
         cp -f  /usr/share/kernel-package/$file ./debian/;            \
    done
for dir  in Config docs examples ruleset scripts pkg po;    do                \
       cp -af /usr/share/kernel-package/$dir  ./debian/;                \
    done
install -p -m 755 /usr/share/kernel-package/rules debian/rules
sed         -e 's/=V/3.3.2-custom/g'  \
                -e 's/=D/3.3.2-custom-10.00.Custom/g'         -e 's/=A/amd64/g'  \
        -e 's/=SA//g'  \
        -e 's/=I//g'                    \
        -e 's/=CV/3.3/g'                \
        -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g'        \
        -e 's/=ST/linux/g'      -e 's/=B/x86_64/g'    \
                  /usr/share/kernel-package/Control > debian/control
sed -e 's/=V/3.3.2-custom/g' -e 's/=D/3.3.2-custom-10.00.Custom/g'          \
        -e 's/=A/amd64/g' -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g' \
        -e 's/=ST/linux/g'     -e 's/=B/x86_64/g'          \
        /usr/share/kernel-package/changelog > debian/changelog
chmod 0644 debian/control debian/changelog
make -f debian/rules debian/stamp/conf/kernel-conf
make[2]: Entering directory `/home/user/linux-3.3.2'
make[2]: `debian/stamp/conf/kernel-conf' is up to date.
make[2]: Leaving directory `/home/user/linux-3.3.2'
make[1]: Leaving directory `/home/user/linux-3.3.2'
echo done > debian/stamp/conf/minimal_debian
exec debian/rules  APPEND_TO_VERSION=-custom  INITRD=YES  kernel_image kernel_headers 
====== making target debian/stamp/conf/vars [new prereqs: ]======

====== making target debian/stamp/build/kernel [new prereqs: vars]======
This is kernel package version 12.036+nmu2.
restore_upstream_debianization
test ! -f scripts/package/builddeb.kpkg-dist ||    mv -f scripts/package/builddeb.kpkg-dist scripts/package/builddeb
test ! -f scripts/package/Makefile.kpkg-dist ||    mv -f scripts/package/Makefile.kpkg-dist scripts/package/Makefile
/usr/bin/make -jgetconf_NPROCESSOR_ONLN EXTRAVERSION=-custom  ARCH=x86_64 \
                 bzIma

##########[ERROR STARTS HERE]#####################

make: the `-j' option requires a positive integral argument
Usage: make [options] [target] ...
Options:
  -b, -m                      Ignored for compatibility.
  -B, --always-make           Unconditionally make all targets.
  -C DIRECTORY, --directory=DIRECTORY
                              Change to DIRECTORY before doing anything.
  -d                          Print lots of debugging information.
  --debug[=FLAGS]             Print various types of debugging information.
  -e, --environment-overrides
                              Environment variables override makefiles.
  -f FILE, --file=FILE, --makefile=FILE
                              Read FILE as a makefile.
  -h, --help                  Print this message and exit.
  -i, --ignore-errors         Ignore errors from commands.
  -I DIRECTORY, --include-dir=DIRECTORY
                              Search DIRECTORY for included makefiles.
  -j [N], --jobs[=N]          Allow N jobs at once; infinite jobs with no arg.
  -k, --keep-going            Keep going when some targets can't be made.
  -l [N], --load-average[=N], --max-load[=N]
                              Don't start multiple jobs unless load is below N.
  -L, --check-symlink-times   Use the latest mtime between symlinks and target.
  -n, --just-print, --dry-run, --recon
                              Don't actually run any commands; just print them.
  -o FILE, --old-file=FILE, --assume-old=FILE
                              Consider FILE to be very old and don't remake it.
  -p, --print-data-base       Print make's internal database.
  -q, --question              Run no commands; exit status says if up to date.
  -r, --no-builtin-rules      Disable the built-in implicit rules.
  -R, --no-builtin-variables  Disable the built-in variable settings.
  -s, --silent, --quiet       Don't echo commands.
  -S, --no-keep-going, --stop
                              Turns off -k.
  -t, --touch                 Touch targets instead of remaking them.
  -v, --version               Print the version number of make and exit.
  -w, --print-directory       Print the current directory.
  --no-print-directory        Turn off -w, even if it was turned on implicitly.
  -W FILE, --what-if=FILE, --new-file=FILE, --assume-new=FILE
                              Consider FILE to be infinitely new.
  --warn-undefined-variables  Warn when an undefined variable is referenced.

This program built for x86_64-pc-linux-gnu
Report bugs to <bug-make@gnu.org>
make: *** [debian/stamp/build/kernel] Error 2
root@user-desktop:/home/user/linux-3.3.2#

What to do? please help me....

---

### Post by kashyapkopparam on 2012-05-10
I installed kernel according to the post. But now no wireless. Ihave a Broadcom BCM4313 wireless card. Has anyone got the resolution and the WiFi to work?

---

### Post by axw on 2012-05-11
It appears that the GMA 3600/3650 extension of gma500 module in the current kernel (3.4-RC6) indeed works using fbdev xorg driver, but screen resolution is limited to 1600x1200. I guess this is due to still unresolved [8 mb memory limit issue]("http://askubuntu.com/questions/120866/cannot-set-monitor-to-native-resolution").

Did anyone actually succeed running 1920x1200 using GMA 3600/3650 kernel native driver?

UPDATE: as some one mentioned earlier in this thread, 1600x1200 is possible once LVDS is turned off using grub's parameter "video=LVDS-1:d"

UPDATE2: 1920x1200 is there after applying latest patches from git (current linux-next branch, newer than 3.4-RC6). Probably 25 Apr "gma500: support 1080p" by Alan Cox did the job. Unfortunately, xorg is limited to 16 bpp.

UPDATE3: video playback sucks horribly, no gpu acceleration here

---

### Post by tdguchi on 2012-05-12
I have compiled some kernel versions (3.3.2 3.3.5 3.4-rc6) and activate gma3600/3650 driver, and only I have fixed the screen resolution, i dont have 3D aceleration, and I cant adjust brightness.. (its at 100%) anyone has an idea to fix these problems?

thanks

PD: Im using an eeepc 1025c with n2800 and ubuntu 12.04

---

### Post by nosilverbullet on 2012-05-13
> **klisanor said:**
> 

**BUT!** 
VGA does not work on any of the kernels above
My WiFi card is:
```
lspci | grep Network
01:00.0 Network controller: Intel Corporation Centrino Wireless-N 130 (rev 34)
```

I tried to download the latest iwlwifi ucode from Intel ([http://intellinuxwireless.org/](http://intellinuxwireless.org/)), but still have no luck
```
cd $HOME
#check latest iwlwifi version here: http://intellinuxwireless.org/?n=Downloads
wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6000g2b-ucode-18.168.6.1.tgz
tar -zxf iwlwifi-6000g2b-ucode-18.168.6.1.tgz
sudo mv iwlwifi-6000g2b-ucode-18.168.6.1/iwlwifi-6000g2b-6.ucode /lib/firmware/
```


Maybe you should try the previous version: iwlwifi-6000g2b-5.ucode. It can be downloaded from [http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6000g2b-ucode-17.168.5.2.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6000g2b-ucode-17.168.5.2.tgz) and works fine with MeeGo's 3.0.0 kernel I am currently playing with.

---

### Post by macktheripper on 2012-05-14
> **tdguchi said:**
> I have compiled some kernel versions (3.3.2 3.3.5 3.4-rc6) and activate gma3600/3650 driver, and only I have fixed the screen resolution, i dont have 3D aceleration, and I cant adjust brightness.. (its at 100%) anyone has an idea to fix these problems?

thanks

PD: Im using an eeepc 1025c with n2800 and ubuntu 12.04

I have also compiled the 3.4-rc6 kernel, but the screen resolution is still not working. How have you activated the gma3600/3650 driver?

Thanks

---

### Post by xceedsys on 2012-05-14
it appears that there are 2 drivers for gma3600/3650 (pvrsrvkm/ gma3600 using gma500 driver)
- pvrsrvkm : in meego [http://mirrors.kernel.org/meego/updates/1.2.0/repos/oss/source/kernel-adaptation-pc-3.0.0-8.1.src.rpm](http://mirrors.kernel.org/meego/updates/1.2.0/repos/oss/source/kernel-adaptation-pc-3.0.0-8.1.src.rpm)
under Device Driver --> Stagging --> cdv, mark <*> to enable

warning you may not be able to boot into your HD if anything goes wrong, i would suggest that you have an linux installer, just in-case below did not work, you can do a re-install.

- you will need to compile the source with the patched in it and with cdv enabled, and all other drivers required by your pc, you can follow [http://www.sysdesign.ca/guides/linux_kernel.html](http://www.sysdesign.ca/guides/linux_kernel.html), replace kernel file with above.

- after compiling, you will need to apply the meego rip supplied by h113331pp, search back this thread
or 
- apply this cdv_drivers_to_patched.rar [http://www.funp.net/861786](http://www.funp.net/861786) 
    rename cdv_drivers_to_patched.rar to cdv_drivers_to_patched.tar.bz2
    just copy overwrite all files in their respective folders
 contains above patches, also i have maplyer-vaapi which you can test to play HD video files, e.g. mplayer-vaapi -vo vaapi myHDVideofile.mp4

- change your grub.cfg and add video=LVDS-1:d 
  as the cdv driver default to this LVDS video port, rendering vga to a lower resolution.

- reboot and if all go well, it will boot and shows a login screen.
- you can use vainfo and glxinfo to list out if all the modes are there
- use mplayer-vaapi to play a HD video, to see if it works

- if you boot into a login screen and the keyboard/mouse is not responding 
 then you need to enable/add the following lines in /etc/X11/xorg.conf.d/cdv-pvr.conf

Section "ServerFlags"
    Option "AutoAddDevices" "false"
EndSection

gma500 : found in kernel source 3.0.x and above
#press / to find "3600", enable GMA 3600 support
it was also used for Intel EMGD drivers
did not try this.


i hope above will help.

---

### Post by tdguchi on 2012-05-14
> **macktheripper said:**
> I have also compiled the 3.4-rc6 kernel, but the screen resolution is still not working. How have you activated the gma3600/3650 driver?

Thanks

In the Kernel configuration

Device drivers/Graphics support/Direct Rendering Manager/

activate Intel GMA5/600 KMS Framebuffer then you have two options more, one of these is tje intel gma3600/3650 support (experimental) activate it, and compile, it works, but only fixes the screen resolution...

---

### Post by macktheripper on 2012-05-14
> **tdguchi said:**
> In the Kernel configuration

Device drivers/Graphics support/Direct Rendering Manager/

activate Intel GMA5/600 KMS Framebuffer then you have two options more, one of these is tje intel gma3600/3650 support (experimental) activate it, and compile, it works, but only fixes the screen resolution...

Thank you so much! :guitar:

---

### Post by dnaeon on 2012-05-16
Hello,

Like many others here I've got the same problems with my new Acer D270 which comes with N2600 - no decent graphics driver in Linux yet.

I've installed a new kernel (3.3) on my Debian Wheezy system with enabled GMA3600 and managed to get somewhat better graphics performance, but still the performance is quite annoying.

I've seen here people managed to get a MeeGo kernel with the binary blob for GMA 3600 on a Ubuntu system.

Could you please share some performance results (for example from glxgears) with the MeeGo kernel and driver on your Ubuntu systems compared to a stock Linux kernel with GMA3600 enabled? 

Thanks and regards,
Marin

---

### Post by r00ty on 2012-05-16
Hi everyone. I'm a n00b when it comes to linux. 

I have an ASUS 1025C and need to fix this horrific 800x600 issue. 

I downloaded the 3 rapidshare files and have no idea what to do next.

Thanks a million for any and all help!

---

### Post by marcio123 on 2012-05-17
Is there a way to get VGA port to work ?

---

### Post by r00ty on 2012-05-17
Thanks tdguchi!

I only installed one of the files but my resolution is back to good and everything else seems to be working fine still.

---

### Post by nosilverbullet on 2012-05-18
> **tdguchi said:**
> Forget that files, i have compiled the last version of the kernel (3,4-rc7) with gma3600/3650 support


Does the graphics work after resume on your system?

---

### Post by marcio123 on 2012-05-18
I have hp mini 210 with n2800 and graphic works after resume but VGA does not work on all kernels :/

---

### Post by tdguchi on 2012-05-18
> **nosilverbullet said:**
> Does the graphics work after resume on your system?

No, that problem cant be fixed until intel releases a good driver

---

### Post by JohnDanzig on 2012-05-19
> **marcio123 said:**
> Is there a way to get VGA port to work ?

First of all I`d like to thank you all for the continous help over the  last  years on my way to get rid of Windoof and becoming an Ubuntu  Fanboy. ;)
I already learnt a lot, but this problem is far beyond my abilities.
I bought an Asus 1011CX a few weeks ago without checking wether there are Ubuntu drivers available.
Too bad... -.-
Anyway...I managed to get an res. of 1280x800 (thanks to the great  advice in this thread) and I think it's okay as long as I use the  netbook as the mobile device it is supposed to be.
But I also do use it as a desktop PC and sitting at the desk, staring at  10" screen sucks...espcially if theres a 19" TFT standing right behind  the netbook... -.-
So if anyone has any ideas how to make the HDMI port work properly, I`d be fprever grateful...

---

### Post by gene simmons on 2012-05-19
hi all,great thread,i have a acer d270 cedar trail with intel 3600 graphics,i have ubuntu 12.04 running well with kernel 3.2 but my hdmi isnt recognized,i installed kernel 3.3 and that didnt have wireess and the broadcom driver woulddnt install got an error,i tried the custom 3.4 posted on here and not only wouldnt wireless work the etherenet hardwire didnt work iether and under monitor i still only had a resolution of 1024x600 with no mirror image for hdmi available,i dont care about graphics much i would just like to be able to watch hdmi avi movies on this thing like i bought it for,do u guys have hdmi working with ubuntu 12,04?

---

### Post by chaveiro on 2012-05-19
Hello

I'm using an Intel DN2800MT board with Atom n2800 headless with Ubuntu 12.04 default kernel 3.2.0-24-generic. 
Can i get any help with the 3.4.x kernel GMA3650 support that allows to set GPU on low power mode to reduce global consumption?

I've did all tweeks already to reduce power usage and cant pass below 9.36W.
In windows 8 CP without any tweeks, just letting disk spinoff and monitor off i got 8.9W.

Not much of a difference but i believe it's the gpu.

UPDATE:
Tried the Ubuntu 3.3.6 kernel on the link below and got no image from vga, reverted to original.
[http://www.upubuntu.com/2012/05/how-to-install-linux-kernel-336-via-ppa.html](http://www.upubuntu.com/2012/05/how-to-install-linux-kernel-336-via-ppa.html)
Any advice?

---

### Post by Alex976 on 2012-05-20
I'm using an Intel DN2800MT, too. At first I installed Ubuntu 12.4. After that I installed the both files from tdguchi with the 3.4 Kernel, to get support for the GMA 3600/3650 chip. But it's still not working.

Wenn I reboot the PC, there is no graphic output. Not at the VGA port and not at the HDMI port. On both ports my monitor shows a message that it doesn't get a signal and switches to standby mode :-/

What can be the problem? What can I do?

I'm trying to get this working for more than 2 months now. Everything what I try doesn't work. It's really annoying...

---

### Post by chaveiro on 2012-05-20
So the problem is generic for DN2800MT boards / GMA3650 GPUs.

No video VGA or HDMI output on kernels 3.3.x - 3.4.x

Maybe the developpers are using Atom laptops and only activate LVDS or whatever, i could not change it with grub option.
For the record i've 4gb single dimm, and 64 bits ubuntu.
I realy like to see this sorted out and can do any test on my board if it helps any dev.


Intel is realling scruing popularity on Atom brand here for not even minimal support on linux to their own boards.
Eg. vga/hdmi output and power management to reduce consumption

---

### Post by ragingxrivers on 2012-05-21
Any progress? Is there a guaranteed solution?

Kindly post any links or step-by-step solutions to the Intel GMA 3600 problem.

Thanks! ;)

---

### Post by axw on 2012-05-21
> **chaveiro said:**
> So the problem is generic for DN2800MT boards / GMA3650 GPUs.

No video VGA or HDMI output on kernels 3.3.x - 3.4.x

HDMI output *does* work on D2700DC which has the same GMA3650 chipset and is also a cedar view motherboard.

There are patches in the linux-next branch which solve the issue. What worked for me was 
1) take the 3.4-RC7 tree branch, unzip
2) copy the current contents of the gma500/ folder from the linux next-branch over 3.4-RC7 files
3) re-compile the kernel as 3.4-RC7 (well, with a slightly modified gma500 driver ;)

Give it some time to load because the specific kernel booted me directly into xorg instead of console. Also, I have disabled LVDS  by appending this to existing GRUB_CMDLINE_LINUX entries: video=LVDS-1:d

---

### Post by lcman on 2012-05-21
I have an Atom N2800 with GMA 3600 netbook and I have "some" graphics support.

I can watch some Youtube videos and stuff but HD doesn't work and DVDs will usually stutter.

Basically, I don't have HW acceleration. I had to compile kernel 3.3.4 to get basic rendering though because I was stuck at 800x600 and Unity was acting all weird on me.

I'm gonna try building the Meego Kernel and if it works, I'll provide you guys with binaries.

---

### Post by gene simmons on 2012-05-21
i have the acer d270 with hdmi and i tried mint 12 lxde and hdmi worked,there wasnt much for resolution options but it worked,i had it installed to hardrive but i changed to ubuntu 12.04 hoping it would be better,i didnt like the lxde desktop,i may try the reg mint and see if it will work on hdmi,i bought this netbook to watch movies on and as of now i have to boot to windows to do that which hurts so much haha

---

### Post by nasty000 on 2012-05-23
> **axw said:**
> HDMI output *does* work on D2700DC which has the same GMA3650 chipset and is also a cedar view motherboard.

I've got this exact motherboard and I would love to get a working copy of Ubuntu on it. Can you elaborate "does work"?

Does HD video play? How good?
Any HW acceleration?

Thanks!

---

### Post by axw on 2012-05-23
> **nasty000 said:**
> I've got this exact motherboard and I would love to get a working copy of Ubuntu on it. Can you elaborate "does work"?

Does HD video play? How good?
Any HW acceleration? 

Sadly, only 2D support. No HW video acceleration is implemented even in the current linux-next branch.

HD/DVD/Bluray videos are not viewable. Using vlc, most lower quality videos are acceptable (eg. 700mb divx type) thanks to the cpu. Not all, though.

---

### Post by bodhi.zazen on 2012-05-24
Hey all, I see similar problems with the GMA3600 as with the older gma500.

FYI: A driver is under development in the kernel and you should contact the Ubuntu kernel team, last I looked they were compiling this driver.

FYI: There is little to no support for compiling a kernel. If you want to do so see:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

> Building and using a custom kernel will make it very difficult to get support for your system.

While it is a learning experience to compile your own kernel, you will not be allowed to file bugs on the custom-built kernel (if you do, they will be Rejected without further explanation).

[http://bodhizazen.net/Tutorials/kernel](http://bodhizazen.net/Tutorials/kernel)

As with the gma500, I am seeing a lot of advice being given to compile kernels without support (documentation) , without a gma3600 team, and without a ppa.

If you are going to continue with this activity, compiling custom kernels, providing kernel modules, please form a gma3600 team similar to the gma500 team

[https://launchpad.net/~gma500](https://launchpad.net/~gma500)

In general we do not mind "experimental drivers", but we expect warnings to new users, documentation, and peer reviewed packages.

These third party kernel modules outside of a ppa are not tolerated here.

You should be filing bug reports with Launchpad or kernel.org 

I will leave this thread open for now , but if the above behavior is not corrected, it will be subject to staff review and closure.

---

### Post by gene simmons on 2012-05-25
weird update on my acer d270,doesnt show hdmi monitor in displays and i cant change the resolution from 1024x600.i decided to try booting the pc with the hdmi cord plugged into the tv,to my surprise the resolution changed to 1024x768 and hdmi was working,i watched a movie yaaaa,still no resolution options but it worked so im not complaining so guys if your hdmi isnt working try booting while its plugged in,mite help,

---

### Post by jnetman1 on 2012-05-26
You are on the right track compiling the newer version of the kernel with updated gma500 drivers, however you need a few extra pieces to get everything working. To fix the resume problem, you need to disable the default sleep script, which borks the framebuffer on resume. Open a terminal and:

```
sudo touch /etc/pm/sleep.d/99video

```
To get the external ports to show so that typical screen utilities will see them, go get the code for the freedesktop xf86-modesetting driver here:

[http://xorg.freedesktop.org/archive/individual/driver/xf86-video-modesetting-0.2.0.tar.gz](http://xorg.freedesktop.org/archive/individual/driver/xf86-video-modesetting-0.2.0.tar.gz)

Extract the tarball, then open a terminal and:

```
sudo apt-get build-dep xserver-xorg-video-intel
cd [directory where you extracted]/xf86-video-modesetting-0.2.0
./configure --prefix=/usr && make && sudo make install

```

Almost there - now we need to update our /etc/X11/xorg.conf. You probably don't have one, so 

```
sudo gedit /etc/X11/xorg.conf
```

and copy the following settings into the file:

```
Section "Module"
	Load  "dri"
	Load  "dbe"
	Load  "record"
	Load  "extmod"
	Load  "dri2"
	Load  "glx"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "kmsdev"             	# <str>
        #Option     "ShadowFB"           	# [<bool>]
	Identifier  "Card0"
	Driver      "modesetting"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
	Identifier  "Card1"
	Driver      "fbdev"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier  "Card2"
	Driver      "vesa"
	BusID       "PCI:0:2:0"
EndSection


Section "DRI"
	Mode  0666
EndSection


```

Reboot, and you'll be using all FOSS drivers (no hacky Meego extracts/downgrades) and everything should work almost as well as it does on ubermix ([http://ubermix.org](http://ubermix.org)). You'll still have an issue with the internal display going black when you deactivate an external display, which you can fix with a simple vt switch (ctrl-alt-f1, alt-f7).

---

### Post by jnetman1 on 2012-05-26
Brightness control isn't quite there yet, however you can work around it on some devices with

```
sudo gedit /etc/default/grub
```

then locate the line that looks like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

and change it to this:

```
GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi=Linux acpi_backlight=vendor quiet splash"
```

Save, then

```
sudo update-grub
```

reboot, and try your brightness controls. Doesn't work on Acer for some reason, but works on other devices.

---

### Post by nosilverbullet on 2012-05-28
> **jnetman1 said:**
> To fix the resume problem, you need to disable the default sleep script, which borks the framebuffer on resume. Open a terminal and:

```
sudo touch /etc/pm/sleep.d/99video

```


Wow, that helps! Thank you!

I just got an email from Intel's developer: "I was actually reporting that problem back to canonical for pm-util script issue before. There's no need to do vbe repost as driver will ensure to reset everything. ;) So looks like they haven't changed their script for that."

---

### Post by pmcon on 2012-05-28
for ubuntu precise
 [http://www.silentpcreview.com/forums/vi ... 9&p=558348]("http://www.silentpcreview.com/forums/viewtopic.php?f=28&t=63959&p=558348")

thanks to gryle,works for my he post this :
There is a ppa repository with drivers for ubuntu 12.04 in here: [http://ppa.launchpad.net/sarvatt/cedarview/ubuntu/](http://ppa.launchpad.net/sarvatt/cedarview/ubuntu/)

I've managed to get accelerated X working in Ubuntu 12.04 with these steps:

#Add repository in [http://ppa.launchpad.net/sarvatt/cedarview/ubuntu/](http://ppa.launchpad.net/sarvatt/cedarview/ubuntu/) :
sudo add-apt-repository ppa:sarvatt/cedarview
sudo apt-get install add-apt-key
sudo add-apt-key  0x4c96de60854c4636
sudo apt-get update

# Add video=LVDS-1:d to GRUB_CMDLINE_LINUX_DEFAULT variable
sudo vi /etc/default/grub

# if you're using PAE kernel, remove it and install generic kernel
sudo apt-get install linux-headers-generic linux-image-generic
sudo apt-get remove linux-headers-generic-pae linux-image-generic-pae

sudo apt-get install cedarview-drm libva-cedarview-vaapi-driver cedarview-graphics-drivers

#Change Option "AIGLX" to "Off" because 3D isn't working
sudo vi /usr/share/intel-cdv/X11/xorg.conf.d/61-cdv-pvr.conf

sudo update-grub2

---

### Post by gene simmons on 2012-05-29
ok not sure what i did worong but my sytem is messed up,i followd the instructions to install the new driver and now i cant access my windows7 partition,it doesnt show up in the grub,it shows up when i do a update grub but its not there and i can only boot in ubuntu in gnome no effects,with the kernel in the intstructions i cant get the graphics to work,the pc is so slow and the fonts are unreadable its in a weird resolution also,and in the kernel i was using,the mouse doesnt work and theres no graphics at all  and it wont boot,how can i unistall all the stuff that was installed,so frustrated,i just want tot watch a movie on my tv via hdmi on this thing using ubuntu,now i cant access my windows either,please help

---

### Post by gryle on 2012-05-29
> **gene simmons said:**
> ok not sure what i did worong but my sytem is messed up,i followd the instructions to install the new driver and now i cant access my windows7 partition,it doesnt show up in the grub,it shows up when i do a update grub but its not there and i can only boot in ubuntu in gnome no effects,with the kernel in the intstructions i cant get the graphics to work,the pc is so slow and the fonts are unreadable its in a weird resolution also,and in the kernel i was using,the mouse doesnt work and theres no graphics at all  and it wont boot,how can i unistall all the stuff that was installed,so frustrated,i just want tot watch a movie on my tv via hdmi on this thing using ubuntu,now i cant access my windows either,please help

Hi

It was me who wrote those instruction in the silentpcreview forum.
Try removing the file /etc/grub.d/11_custom_cmdline and update grub again
That file is installed by the cedarview-drm but it seems buggy
I also changed the console from graphics to text mode on boot up . I think I did it by setting GRUB_CMDLINE_LINUX_DEFAULT="" in /etc/default/grub
I still get some crash reports from gnome-settings-daemon that seem related to xrandr. Haven't investigated that problem yet.

---

### Post by marcio123 on 2012-05-29
Does VGA port work ? 

Is it possible to do it in 11.04 with 2.6 kernel ?

---

### Post by pmcon on 2012-05-29
[gryle]("http://ubuntuforums.org/member.php?u=502944") it is better then custom kernel 3.3... with cedar support i did before 150fps
now i had 180-200 fps on glxgears 
 

On dn2800mt board hdmi works with sound and full hd i can watch movies hd , it works best for me. 
3d not supported for  ubuntu we must wait

here are resolution on kubuntu [IMG]http://http://pmcon.info/snapshot1.png[/IMG]

pmcon

---

### Post by pmcon on 2012-05-29
[http://http://pmcon.info/snapshot1.png](http://http://pmcon.info/snapshot1.png)

resolution kubuntu

---

### Post by pmcon on 2012-05-29
VGA and hdmi ports works change primari in bios.
 after restart BIOS prompt shows on primary monitor then go both

lvds did not know, cant test bat i see in monitor setings on Kubuntu, gnome  monitor settings hacks so i switch to Kubuntu.

pmcon

---

### Post by bodhi.zazen on 2012-05-29
> **marcio123 said:**
> Does VGA port work ? 

Is it possible to do it in 11.04 with 2.6 kernel ?

The driver is in rapid development and not available in a 2.6 kernel.

I highly suggest you use Ubuntu 12.10 (currently in early development) to perhaps Fedora 17 (released today) so as to have as high a kernel as possible.

---

### Post by tdguchi on 2012-05-29
> **pmcon said:**
> for ubuntu precise
 [http://www.silentpcreview.com/forums/vi ... 9&p=558348]("http://www.silentpcreview.com/forums/viewtopic.php?f=28&t=63959&p=558348")

thanks to gryle,works for my he post this :
There is a ppa repository with drivers for ubuntu 12.04 in here: [http://ppa.launchpad.net/sarvatt/cedarview/ubuntu/](http://ppa.launchpad.net/sarvatt/cedarview/ubuntu/)

I've managed to get accelerated X working in Ubuntu 12.04 with these steps:

#Add repository in [http://ppa.launchpad.net/sarvatt/cedarview/ubuntu/](http://ppa.launchpad.net/sarvatt/cedarview/ubuntu/) :
sudo add-apt-repository ppa:sarvatt/cedarview
sudo apt-get install add-apt-key
sudo add-apt-key  0x4c96de60854c4636
sudo apt-get update

# Add video=LVDS-1:d to GRUB_CMDLINE_LINUX_DEFAULT variable
sudo vi /etc/default/grub

# if you're using PAE kernel, remove it and install generic kernel
sudo apt-get install linux-headers-generic linux-image-generic
sudo apt-get remove linux-headers-generic-pae linux-image-generic-pae

sudo apt-get install cedarview-drm libva-cedarview-vaapi-driver cedarview-graphics-drivers

#Change Option "AIGLX" to "Off" because 3D isn't working
sudo vi /usr/share/intel-cdv/X11/xorg.conf.d/61-cdv-pvr.conf

sudo update-grub2

I have follow these steps, but when I boot he kernel, it works, but  I have only a black screen.... how can I fix it?

PD:I have already removed he file in /etc/grub.d to bea ble to boot windows 7

---

### Post by nosilverbullet on 2012-05-30
> **tdguchi said:**
> I have follow these steps, but when I boot he kernel, it works, but  I have only a black screen.... how can I fix it?


Try to undo this step:

```
# Add video=LVDS-1:d to GRUB_CMDLINE_LINUX_DEFAULT variable
sudo vi /etc/default/grub
```

It is supposed to turn off some non-existent screen device, but on my Samsung NC-110 it turned off the actual screen, because I do not have a non-existent screen device. I guess you have the same problem.

---

### Post by tdguchi on 2012-05-30
> **nosilverbullet said:**
> Try to undo this step:

```
# Add video=LVDS-1:d to GRUB_CMDLINE_LINUX_DEFAULT variable
sudo vi /etc/default/grub
```

It is supposed to turn off some non-existent screen device, but on my Samsung NC-110 it turned off the actual screen, because I do not have a non-existent screen device. I guess you have the same problem.

Yes, thats the problem, fixed!

---

### Post by marcio123 on 2012-05-30
> **tdguchi said:**
> 
PD:I have already removed he file in /etc/grub.d to bea ble to boot windows 7

What did You remove to be able to boot to windows 7 ? 


I did all the steps on my HP MINI 210-4160ew. 
1) External VGA port works but grapfics in UNITY or Gnome is very slow. 
2) Sleep/resume is impossible (black screen after resume)

---

### Post by gryle on 2012-05-30
> **tdguchi said:**
> Yes, thats the problem, fixed!

Yes, that step was meant for people using a motherboard connected to a monitor (in my case it's an intel D2700DC using HDMI out).
Those using a notebook should not add the video=LVDS-1:d kernel option

---

### Post by gryle on 2012-05-30
> **marcio123 said:**
> What did You remove to be able to boot to windows 7 ? 


I did all the steps on my HP MINI 210-4160ew. 
1) External VGA port works but grapfics in UNITY or Gnome is very slow. 
2) Sleep/resume is impossible (black screen after resume)

Remove the /etc/grub.d/11_custom_cmdline file
My system also crashes when resuming from suspend with ubuntu 12.04.
With fedora 16 it resumes fine

---

### Post by gene simmons on 2012-05-30
> **gryle said:**
> Hi

It was me who wrote those instruction in the silentpcreview forum.
Try removing the file /etc/grub.d/11_custom_cmdline and update grub again
That file is installed by the cedarview-drm but it seems buggy
I also changed the console from graphics to text mode on boot up . I think I did it by setting GRUB_CMDLINE_LINUX_DEFAULT="" in /etc/default/grub
I still get some crash reports from gnome-settings-daemon that seem related to xrandr. Haven't investigated that problem yet.


thanx for the fix,that file was the prob,my system works now but its pretty suggish,kinda slow to respond to stuff and when resuming i get weird squiggly resolution lines,i love that the brightness feature now works and hdmi works,yaaaa but the slugish behavior is kinda annoying,i also get the error reports daily when i restart,again thanx for the fix,i will folow this thread to see if theres any updates to make my machine better

---

### Post by bodhi.zazen on 2012-06-02
> **h113331pp said:**
> Yes, you`re right, now you see all the solution about GMA3600 is 2 directions:

I have to warn that you have to know what you are doing brfore you use a customed kernnel. 

1. use customed kernel + framebuffer driver(fbdev) / VESA
2. use customed kernel + customed X server + meego driver(pvr)
[U][B]
[FONT=Arial]unfortunately, the meego only have i386 version.

[/FONT][/B][/U]

I will again warn this community. This thread is again starting to go in an undesirable direction.

I am sort of willing to give you an opportunity, but I expect you all to for a team and work on documentation if you are going to use third party repos (meego) and custom kernels.

There is (was) a gma500 team

[https://launchpad.net/~gma500](https://launchpad.net/~gma500)

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

While they were active, maintaining a ppa and documentation, we allowed this sort of activity here.

But when they fell inactive ....

I hope you get the idea.

---

### Post by h113331pp on 2012-06-02
> **bodhi.zazen said:**
> I will again warn this community. This thread is again starting to go in an undesirable direction.

I am sort of willing to give you an opportunity, but I expect you all to for a team and work on documentation if you are going to use third party repos (meego) and custom kernels.

There is (was) a gma500 team

[https://launchpad.net/~gma500]("https://launchpad.net/%7Egma500")

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

While they were active, maintaining a ppa and documentation, we allowed this sort of activity here.

But when they fell inactive ....

I hope you get the idea.

OK ... I got it.

If some one else ask this, I will never say any word and any hint of it.

actually, all I concern now is how the efficiency the pvr which gryle ripped.

---

### Post by gryle on 2012-06-03
Hi

There seems to be some misunderstandings, and it's probably my fault for not making it clear where the ppa repository refered to in the instructions I posted in the silentpcreview forum (that was transcribed in this forum) came from.

The ppa in [http://ppa.launchpad.net/sarvatt/cedarview/ubuntu/](http://ppa.launchpad.net/sarvatt/cedarview/ubuntu/) is from Robert Hooker from Canonical: [https://wiki.ubuntu.com/Sarvatt](https://wiki.ubuntu.com/Sarvatt)
I found it by googling.

From what I found in irc logs, support for cedarview was being considered in Ubuntu 12.04 but it didn't make it for the final release.

You can find some more information about the current status in this irc log: [http://irclogs.ubuntu.com/2012/05/11/%23ubuntu-devel.txt](http://irclogs.ubuntu.com/2012/05/11/%23ubuntu-devel.txt)

---

### Post by kashyapkopparam on 2012-06-06
will the driver be included in the next stable release of the kernel?

---

### Post by kashyapkopparam on 2012-06-06
> **bodhi.zazen said:**
> The driver is in rapid development and not available in a 2.6 kernel.

I highly suggest you use Ubuntu 12.10 (currently in early development) to perhaps Fedora 17 (released today) so as to have as high a kernel as possible.
but updating the kernel to the latest to get the drivers on Precise is same as fedora 17 and 12.10 right?

---

### Post by utkarsh009 on 2012-06-06
Hi guys! I have successfully compiled Linux kernel 3.4.0 on Ubuntu 12.04 and unity 2D is working for me. But I still cannot play HD or full HD videos. Although 480p videos are running smooth with default movie player and ffmpeg plugin (VLC doesn't work well) but I need at least 720p support to view most of my videos. Is there any way to play 1080p or 720p videos smoothly?
I have Asus 1015cx with atom n2600 and gma3600.
Please help guys ......

---

### Post by bodhi.zazen on 2012-06-06
> **kashyapkopparam said:**
> but updating the kernel to the latest to get the drivers on Precise is same as fedora 17 and 12.10 right?

What do you mean by "updating the kernel". Ubuntu 12.04 uses a 3.2 kernel. Fedora and 12.10 use a 3.4 kernel


> **utkarsh009 said:**
> Hi guys! I have successfully compiled Linux kernel 3.4.0 on Ubuntu 12.04 and unity 2D is working for me. But I still cannot play HD or full HD videos. Although 480p videos are running smooth with default movie player and ffmpeg plugin (VLC doesn't work well) but I need at least 720p support to view most of my videos. Is there any way to play 1080p or 720p videos smoothly?
I have Asus 1015cx with atom n2600 and gma3600.
Please help guys ......

If you are expecting your gma3600 to be a mulitmedia powerhouse running Linux you are going to be disappointed. Intel has a long history , dating back to the gma500, of not supporting Linux on these graphics cards.

As far as I know, the open source driver only supports 2d graphics.

Several people have had varying degrees of success with the closed source driver, but these people have not provided documentation or properly packaged .deb despite multiple requests.

You can file a bug report with kernel.org, complain to Intel regarding the lack of support for Linux, or my advice is that next time you purchase hardware, purchase Linux compatible hardware.

You can buy with Linux pre-installed from several vendors including Dell, System76, and Zareason.

Or you can check hardware compatibility lists.

[http://www.h-node.org/](http://www.h-node.org/)

---

### Post by teel on 2012-06-06
There is a thread on Intel Community forum regarding sgx545 support for linux: [http://communities.intel.com/message/158158](http://communities.intel.com/message/158158)
It's more about complaining than trying to figure out the solution, but anyway Intel apparently ignores it.

I already posted some private messages to Intel, suprisingly one guy answered that he was going to pass the question to his colleagues.

---

### Post by utkarsh009 on 2012-06-06
[QUOTE=bodhi.zazen]

my advice is that next time you purchase hardware, purchase Linux compatible hardware.

You can buy with Linux pre-installed from several vendors including Dell, System76, and Zareason.

Or you can check hardware compatibility lists.

[http://www.h-node.org/](http://www.h-node.org/)[/QUOTE]

I didn't buy that super slow machine. I got it as a prize in an all India cyber Olympiad (I got rank one). I'd have definitely opted for Linux supported hardware if I had a choice. Btw, is full HD video supported on meego for cedar trail? If I install it in an ext3 partition, will grub 2 recognize it?

---

### Post by bodhi.zazen on 2012-06-06
> **teel said:**
> There is a thread on Intel Community forum regarding sgx545 support for linux: [http://communities.intel.com/message/158158](http://communities.intel.com/message/158158)
It's more about complaining than trying to figure out the solution, but anyway Intel apparently ignores it.

I already posted some private messages to Intel, suprisingly one guy answered that he was going to pass the question to his colleagues.

+1 My experience with the GMA500 has really turned me off to Intel. 

To see them continue with the same bad behavior with the 3600 is worse.

I suggest everyone on this thread direct your frustrations to Intel. You should all register an account and voice your displeasure, ask for support

[http://communities.intel.com/message/158158](http://communities.intel.com/message/158158)

> **utkarsh009 said:**
> I didn't buy that super slow machine. I got it as a prize in an all India cyber Olympiad (I got rank one). I'd have definitely opted for Linux supported hardware if I had a choice. Btw, is full HD video supported on meego for cedar trail? If I install it in an ext3 partition, will grub 2 recognize it?

Well, sell it and buy a linux compatible netbook or laptop.

Honestly, rather then complaining on these forums you need to take up your issues with Intel and vote with your pocketbook.

How do you expect to get the attention of Intel if you keep buying their products and complaining on the Ubuntu forums? I bet no one from Intel has even read this thread.

---

### Post by pmcon on 2012-06-06
tray use all core with mplayer on command line

mplayer -lavdopts threads=4  /home/...../yourfile.xxx

---

### Post by gene simmons on 2012-06-06
well had a long day formatting the aacer aand i decided to install ubuntu 12.10 as i read it has gma support out of the box,well it installed fine and yes it has gma support but so much other stuff doesnt work,no brightness control,no hdmi and no battery icon while in gnome desktop,oh ya it didnt have gnome ither i had to install that,what a disapointment,i should have tried it first i guess,i also tried fedora 17 which also has gma suport but again no hdmi,is this little netbook that stupid,i am now in the process of formatting again and installing 12.04 and installling the gma 500 driver from here,it worked the best until i screwed it up haha,

---

### Post by kashyapkopparam on 2012-06-07
does resume from suspend, wireless drivers etc work on fedora 17?

---

### Post by janiemiec on 2012-06-07
Hello,
I have the following netbook;

Asus EeePC 1015CX
Intel Atom CPU N2600
1.60GHz
1GB RAM

I wanted to install Ubuntu 12.04 alongside with Windows using the Wubi installer. In order to test how the system would look like, I have created a boot-able USB and tested the system when it started. It all looks fine but the main thing I noticed is that the system operate in 800x600 graphics. Where as Windows 7 (Starter) is able to work in 1024x600.
When looking through the internet I found a short article talking about editing some kind of file.  My problem is that I am a newbe when it comes to Ubuntu and file editing. So could someone please write me simple step-by-step instructions of how to enable 1024x600 screen resolution (Please note that the only option that is available in the screen setting of the system is 800x600.

Thank you.

---

### Post by Alex976 on 2012-06-08
I followed exactly the steps [pmcon]("http://ubuntuforums.org/member.php?u=1621310") described in #97. When I restart Ubuntu 12.4 after that, I get the desired resolution of 1920x1080, but there are only coloured stripes and pixels instead of the desktop. The screen ist completely waste...

I tried this on a DN2800MT. Have I to do different steps for this board?

---

### Post by utkarsh009 on 2012-06-09
> **janiemiec said:**
> Hello,
I have the following netbook;

Asus EeePC 1015CX
Intel Atom CPU N2600
1.60GHz
1GB RAM

I wanted to install Ubuntu 12.04 alongside with Windows using the Wubi installer. In order to test how the system would look like, I have created a boot-able USB and tested the system when it started. It all looks fine but the main thing I noticed is that the system operate in 800x600 graphics. Where as Windows 7 (Starter) is able to work in 1024x600.
When looking through the internet I found a short article talking about editing some kind of file.  My problem is that I am a newbe when it comes to Ubuntu and file editing. So could someone please write me simple step-by-step instructions of how to enable 1024x600 screen resolution (Please note that the only option that is available in the screen setting of the system is 800x600.

Thank you.
Compile Linux kernel 3.4.0 or 3.3.7 to get the desired resolution but beware that you won't be able to play HD or full HD video and will only be able to get 2D support and no open gl acceleration. Intel did not release any driver for Linux except meego which is almost dead as they're focusing on tizen.

---

### Post by stefandebacker on 2012-06-09
I am testing a HP Mini 110-4100 with Intel Atom CPU N2600 and GMA 3600

Installing and upgrading ubuntu 12.04 i386 made everything work out of the box in Unity. Except for the screen that was not really performing well on youtube and movies. 

I found this post which seems to help: [http://blog.uninstall.it/tag/gma3600/](http://blog.uninstall.it/tag/gma3600/)

I followed the "(K)ubuntu installation", except I didn't download and install (k)ubuntu, of course.

So far movies play well in totem, I have a resolution of 1024x600, suspend and resume, sound and sound hotkeys, wireless lan, wireless hotkey and lan all work

What doesn't work are the hotkeys to set brightness, the external screen connector and hotkey.

---

### Post by bodhi.zazen on 2012-06-09
If you want a 3.4 kernel, use Fedora 17 or Ubuntu 12.10. Ubuntu 12.10 is in alpha and likely to be unstable.

---

### Post by cylent on 2012-06-09
> **bodhi.zazen said:**
> 
If you are expecting your gma3600 to be a mulitmedia powerhouse running Linux you are going to be disappointed. Intel has a long history , dating back to the gma500, of not supporting Linux on these graphics cards.

As far as I know, the open source driver only supports 2d graphics.

Several people have had varying degrees of success with the closed source driver, but these people have not provided documentation or properly packaged .deb despite multiple requests.

You can file a bug report with kernel.org, complain to Intel regarding the lack of support for Linux, or my advice is that next time you purchase hardware, purchase Linux compatible hardware.

You can buy with Linux pre-installed from several vendors including Dell, System76, and Zareason.

Or you can check hardware compatibility lists.

[http://www.h-node.org/](http://www.h-node.org/)

WOW! absolutely WOW! i mean damn.
I have heard the saying "Honesty is the best policy" but not like that... take it easy there, bud.

And then i have to ask the following:

Lately i've been really interested in purchasing a netbook -- i first purchased a AMD Fusion C60 powered netbook and found it to be soooo underpowered. It literally was sooo slow no matter what i did.

So i headed to the store and really liked the look and feel of the Lenovo Ideapad s110 netbook. Sadly though it has the n2600 atom processor with the dreaded GMA 3600 ...

even though the gma3600 wasnt supported -- ubuntu 12.04 on the ideapad s110 with the n2600 felt more responsive and better than the c60 experience so i liked it. but then i got stuck with no support for the graphics adapter.

Now -- if i were to give this netbook away to a a family member and buy another which atom would be most compatible and whether to avoid amd all-together again? even though AMD has the best graphics support with both Opensource and Closed source drivers available yet it just was feeling too slow. maybe that was acers fault?

---

### Post by bodhi.zazen on 2012-06-10
> **cylent said:**
> And then i have to ask the following:

Lately i've been really interested in purchasing a netbook -- i first purchased a AMD Fusion C60 powered netbook and found it to be soooo underpowered. It literally was sooo slow no matter what i did.

If you find netbooks "underpowered" I suggest you look at more laptops. I think you are expecting too much from netbook performance.

> So i headed to the store and really liked the look and feel of the Lenovo Ideapad s110 netbook. Sadly though it has the n2600 atom processor with the dreaded GMA 3600 ...

even though the gma3600 wasnt supported -- ubuntu 12.04 on the ideapad s110 with the n2600 felt more responsive and better than the c60 experience so i liked it. but then i got stuck with no support for the graphics adapter.

Now -- if i were to give this netbook away to a a family member and buy another which atom would be most compatible and whether to avoid amd all-together again? even though AMD has the best graphics support with both Opensource and Closed source drivers available yet it just was feeling too slow. maybe that was acers fault?

Aye, you have to check compatibility or buy with linux pre-installed.

---

### Post by cylent on 2012-06-10
> **bodhi.zazen said:**
> If you find netbooks "underpowered" I suggest you look at more laptops. I think you are expecting too much from netbook performance.



Aye, you have to check compatibility or buy with Linux per-installed.

there are many variants of the intel atom ... i wouldn't know standing at the store what has what.

however all the amd fusions have a radeon and all those are supported.

in the meantime i went ahead and installed fedora 17 and it had the correct resolution. however it still seemed extremely sluggish. i guess that's just netbook performance?

Still trying to figure out how this guy achieved a video driver install on this video: [http://www.youtube.com/watch?v=bpQwcOaI8J8](http://www.youtube.com/watch?v=bpQwcOaI8J8)

all he says is "using Fedora-based Linux with a video driver implemented by us". whatever that means.

---

### Post by marcio123 on 2012-06-11
I have 2 hp mini's. 

First has N570 with GMA and second N2800 with GMA. 

On first I have ubuntu 11.04 (on 11.10 or 12.04 3G does not work) and it very smooth 

N2800 has better GMA  but the performance is way worse :/ (ubuntu 12.04 with added drivers)

---

### Post by chrisfuss on 2012-06-14
Hi,

I do have one Intel DN2800MT board thought I can use it for a xbmc appliance. The driver issue is disappointing though... 

I managed to compile a 3.4.2 kernel with GMA support and set res to full hd works so far connected to the TV. Video decoding though is horrible. 

But I have an idea, would a Broadcom Crystal HD decoder card help? Its a half size mini PCIe card and would still fit next to the mSATA card.

What you guys think would I be able to decode full HD movies? Or should I rather add a NVIDIA GPU?

Thx

---

### Post by bodhi.zazen on 2012-06-14
> **chrisfuss said:**
> Hi,

I do have one Intel DN2800MT board thought I can use it for a xbmc appliance. The driver issue is disappointing though... 

I managed to compile a 3.4.2 kernel with GMA support and set res to full hd works so far connected to the TV. Video decoding though is horrible. 

But I have an idea, would a Broadcom Crystal HD decoder card help? Its a half size mini PCIe card and would still fit next to the mSATA card.

What you guys think would I be able to decode full HD movies? Or should I rather add a NVIDIA GPU?

Thx

I would purchase linux compatible hardware in a heartbeat, much less hassle.

---

### Post by xceedsys on 2012-06-22
anyone care to try this :

instructions :
[http://people.freedesktop.org/~zhen/cedarview/README.cedarview.media](http://people.freedesktop.org/~zhen/cedarview/README.cedarview.media)
[http://people.freedesktop.org/~zhen/cedarview/README.cedarview](http://people.freedesktop.org/~zhen/cedarview/README.cedarview)

files are found here :
[http://people.freedesktop.org/~zhen/cedarview/](http://people.freedesktop.org/~zhen/cedarview/)


taken from link : [http://blog.uninstall.it/](http://blog.uninstall.it/)

---

### Post by phaseform on 2012-06-25
@xceedsys
Im very interested to try the "upstream 'gma500' driver" but since I'm not very proficient at linux, Im worried my computer may go awol for good if I try this, which would really suck after a day of getting it up to this stage. 

Any positive reports?
Im using a PowerVR SGX545, which does show a reasonable graphic, just cant play any video with acceptable screen rate

---

### Post by bookan on 2012-06-25
Windows 7 starter is an awful, clunky, limited, resource-wasting OS. I hope there is an easy to install Ubuntu solution with graphics working and proper screen resolutions for the EeePc 1025C soon!  Today I saw that Asus are launching a notebook with Ubuntu 12.04 preinstalled. It has the same atom chip as the 1025C. Does that mean that there is a graphics fix that will be available for 12.04 also for us with 1025C?  [http://www.asus.com/Eee/Eee_PC/Eee_PC_1225C/#specifications](http://www.asus.com/Eee/Eee_PC/Eee_PC_1225C/#specifications)

---

### Post by q.dinar on 2012-06-26
ubuntu quantal (12.10) alpha1 cd iso works. i have written it with unetbootin first, it has not worked, then with ubuntu usb creator, it has worked in live usb drive mode, with correct resolution, and with wifi (it is here in "iwconfig"). this is asus eeepc seashell...
on installation if you cannot edit partitions, do not turn it off, just wait.
after installation it boots to black screen. going to recovery mode, (press shift for that in grub time ie after start of computer booting), and selecting resuming normal load in recovery mode, makes it load normal visible desktop.
btw it is possible to install gnome 2, install gnome-panel package for that. alt+right click to add applets. to select gnome 2 press little ubuntu(i do not remember well) logo at top right corner of password box in login screen. (this is teached/told to me in irc, #ubuntu+1 ).
going to recovery mode, then root console, then "shutdown -r now" makes it restart and grub boot menu appears, without timer. press enter and it also loads normally. but after restart there is again black screen.

---

### Post by XabiX on 2012-06-26
If quantal works then it means that we can find those drivers in some deb?

As it's in Alpha version, I would prefer just to upgrade some packages than to upgrade to an Alpha version with the risk to lose it all :-(

---

### Post by kashyapkopparam on 2012-06-27
Can we hope that the drivers will get better with later Quantal releases?

---

### Post by XabiX on 2012-06-27
Could it be worth?

No we all hope that.
When I see this thread I start to doubt as Intel doesn't communicate at all and ignores all their customers
[http://communities.intel.com/thread/29157?start=30&tstart=0]("http://communities.intel.com/thread/29157?start=30&tstart=0")

Did anyone find a way to have audio through the HDMI?

---

### Post by b1994mi on 2012-06-27
Yooo guys check this out! [http://www.youtube.com/watch?v=bpQwcOaI8J8](http://www.youtube.com/watch?v=bpQwcOaI8J8)

Someone runs Fedora Based Linux on N2600 Lenovo Ideapad! Sorry if this is an outdated news.

Another news for those who can wait until next year : [http://www.zdnet.com/blog/computers/with-ivy-bridge-graphics-could-intels-valley-view-atom-processor-save-netbooks/7798](http://www.zdnet.com/blog/computers/with-ivy-bridge-graphics-could-intels-valley-view-atom-processor-save-netbooks/7798)

Intel is about to launch their new Atom Processor in 2013. :D

---

### Post by rickydoodah on 2012-06-27
Shouldn't be long now seeing as ASUS has just released a Cedar Trail Netbook with ubuntu pre-installed!!

[http://www.asus.com/Eee/Eee_PC/Eee_PC_1225C/](http://www.asus.com/Eee/Eee_PC/Eee_PC_1225C/)

Rick

---

### Post by q.dinar on 2012-06-27
"... quantal ... it boots to black screen"
if to edit grub menu item and add " nomodeset" to line with "ro quiet splash" [s]it works[/s]. no, it does not work. explanation of it: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) .

---

### Post by mikewhatever on 2012-06-28
> **rickydoodah said:**
> Shouldn't be long now seeing as ASUS has just released a Cedar Trail Netbook with ubuntu pre-installed!!

[http://www.asus.com/Eee/Eee_PC/Eee_PC_1225C/](http://www.asus.com/Eee/Eee_PC/Eee_PC_1225C/)

Rick

Dell released its GMA500 Mini 10 netbooks in 2009, and I am still waiting. 
It's an odd move by Asus, as the machine with 12.04 preinstalled would be barely usable, that is, unless it has a driver built in. There is nothing for Linux in the downloads section.

---

### Post by bodhi.zazen on 2012-06-28
I am closing this thread for now. Sort of the bottom line is that this hardware is not supported by Intel on Linux.

Please direct your complaints and frustrations to Intel.

See - [http://communities.intel.com/thread/29157?start=0&tstart=0](http://communities.intel.com/thread/29157?start=0&tstart=0)

In terms of open source, there is a driver in the mainline kernel. It is not fully functional. Compile or install a mainline kernel if you wish, but this activity is not supported.

[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

> The mainline kernels builds are produced for debugging purposes and therefore come with no support. Use them at your own risk. 

and 

[https://help.ubuntu.com/community/Kernel/Compile/](https://help.ubuntu.com/community/Kernel/Compile/)

> Building and using a custom kernel will make it very difficult to get support for your system.

While it is a learning experience to compile your own kernel, you will not be allowed to file bugs on the custom-built kernel (if you do, they will be Rejected without further explanation).

If you have a commercial support contract with Ubuntu/Canonical, this will void such support.

My advice is to not purchase this hardware and expect to run Linux on it.

If you wish to work on experimental drivers, closed or open source, form a team on LP similar to the now defunct GMA500 team.

[https://launchpad.net/~gma500](https://launchpad.net/~gma500)

Feel free to let the FC know once you have a working group.

Otherwise, this thread continues to make unsubstantiated claims and advise experimental drivers without sufficient documentation. I think I have given you all, as a group, sufficient time to get your act together.

---

