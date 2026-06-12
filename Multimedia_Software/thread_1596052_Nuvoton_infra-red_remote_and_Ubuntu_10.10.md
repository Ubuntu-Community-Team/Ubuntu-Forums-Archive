---
title: "Nuvoton infra-red remote and Ubuntu 10.10?"
date: 2010-10-13
forum: Multimedia Software
---

### Post by stephanecharette on 2010-10-13
I have an ASRock ION330HT which comes with a Nuvoton infra-red remote.

The web site has some questionable out-of-date .deb files and instructions for getting it to work on older versions of Ubuntu.  Some of their deb files seem to be specific to certain linux kernels.

[http://www.asrock.com/nettop/download.asp?Model=ION%20330HT&o=Linux](http://www.asrock.com/nettop/download.asp?Model=ION%20330HT&o=Linux)

Their published instructions and .deb files aren't working for me.  I see lots of talk across multiple forums about how hard it is to get this working correctly.

Has anyone gotten the Novoton nct6775/w836x7 working with Ubuntu 10.10?

---

### Post by supertedster on 2010-10-14
Hi Stephan. I just managed to get it working now (Asrock ION 330HT, Ubuntu 10.10 Maverick, standard remote). It requires building a custom kernel with Jarod Wilson's Nuvoton patch.

I don't have time to write up a howto right now, but will post later today.


Cheers
supertedster

---

### Post by supertedster on 2010-10-14
Here's how I got the Nuvoton driver working in Maverick. I have confirmation from two users that the guide does indeed provide all necessary steps to get the Nuvoton device working with lirc. Consider it a dirty solution, though, as it's been twelve years since I last compiled a linux kernel :-) Oh, and I used the kernel sources for 2.6.35-4, I'm not yet sure whether 2.6.35-22 will work (but chances are good it will).

This guide assumes you have the rest of your system set up, including lirc (sudo apt-get install lirc).

**Step 1: Getting the kernel source**
Follow the steps for the alternate kernel build method (the Old-Fashioned Debian way) [_here_]("https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way"). Stop before running make oldconfig.

**Step 2: Applying the Nuvoton driver patch**
Download Jarod Wilson's [Nuvoton driver patch]("https://patchwork.kernel.org/patch/241391/raw/").

Apply the patch by entering the kernel source directory and typing:

```
patch -p1 < ~/Downloads/IR-add-driver-for-Nuvoton-w836x7hg-integrated-CIR.patch
```The driver itself will be patched into the kernel source tree, but for the /drivers/media/IR/Makefile you will receive an error (HUNK 1 failed). This is because a line is missing from the Makefile in the Ubuntu kernel source (obj-$(CONFIG_IR_ENE) += ene_ir.o). Because of this we will apply this part of the patch manually. Open up the drivers/media/IR/Makefile in a text editor. Find the line that says

```
obj-$(CONFIG_IR_MCEUSB) += mceusb.o
```Directly under this line, add the following:

```
obj-$(CONFIG_IR_NUVOTON) += nuvoton-cir.o
```Save the file.

[B]Step 3: Building the kernel
[/B]In the kernel source directory, type
```
make menuconfig
```Under Device Drivers > Multimedia support, select Nuvoton w836x7hg Consumer Infrared Transceiver and press space so the line says <M>. This ensures the Nuvoton driver is built as a kernel module.

Exit and save your configuration, then follow the rest of the Kernel/Compile guide from *"Now you can compile the kernel and create the packages"* onwards (you are skipping the two steps 'make oldconfig' and 'make localmodconfig', as these would modify the configuration you just made using 'make menuconfig'.). Compiling the kernel will take some time on the Asrock system, for me it took a couple of hours. When finished, install the kernel and headers and reboot.

When the system boots up, open up a terminal and type
```
modprobe nuvoton-cir
```If there are no error messages, the Nuvoton driver has been built into the kernel and should be working properly. If not, type
```
uname -r
```It should say "2.6.35.4-some-string-here" or whatever you replaced for "some-string-here". If it doesn't, you're not running your custom kernel.

[B]Step 4: Adding config files for the Nuvoton device
[/B]The Asrock driver packages for Ubuntu 10.4 don't work for Maverick out of the box, but by extracting the files from them we can get the remote working.

Download the [driver package]("http://europe.asrock.com/downloadsite/drivers/Nettop/Ubuntu/IR%2810.04%29kernel2.6.32-23.zip") from Asrock. Unzip it, and extract the appropriate .deb package (right click, Extract here -- do not install the package).

Copy the files and folders from the extracted usr directory to /usr. Then open the /usr/share/lirc/lirc.hwdb file in a text editor. Find the section called [IrDA/CIR hardware] and add the following line (note that this line is **not** identical to the line in the Asrock patch file -- I modified it to reflect the new name of the Nuvoton driver, namely nuvoton-cir):

```
Nuvoton Transceivers/Remotes;nuvoton-cir;lirc_dev nuvoton-cir;hw_default;lirc_wb677/lircd.conf.wb677;
```Next, run
```
sudo dpkg-reconfigure lirc
```and choose Nuvoton Transceivers/Remotes for remote control, and None for transmitter.

I then used
```
mythbuntu-lirc-generator
```to generate key mappings.

Be aware of that if you update to a newer kernel (via the Update Manager, for example) whether the Nuvoton receiver works or not will depend on whether the Ubuntu kernel team have included the Nuvoton patch in the kernel. To go back to your custom kernel, you will have to change your grub (bootloader) settings.

---

### Post by damnstraightrandom on 2010-10-15
Hello,

Thanks for the detailed instructions! Still, `irw` doesn't register any input, although `lsmod` shows that nuvoton-cir has been loaded successfully. Any ideas where I should look next?

---

### Post by supertedster on 2010-10-15
Glad to see you got the module compiled and running. I suppose the problem must be either 1) lirc not communicating with the nuvoton-cir device or 2) lirc not recognizing the remote.

Try
```
ps auxw | grep lirc
```to see if lircd is running. My system is running these lirc processes:
```
nobody    4827  0.0  0.0   2044   260 ?        Ss   Oct14   0:04 /usr/sbin/inputlircd /dev/input/event0 /dev/input/event1 /dev/input/event2 /dev/input/event3 /dev/input/event4 /dev/input/event5 /dev/input/event6 /dev/input/event7
root     16369  0.0  0.0   3512   588 ?        Ss   15:36   0:00 /usr/sbin/lircd --output=/var/run/lirc/lircd --device=/dev/lirc0
```If it isn't running, type
```
sudo /etc/init.d/lirc start
```Does it give any errors? If so, look at the last few lines in /var/log/syslog: ```
tail /var/log/syslog
```

Then check the lirc config files in /etc/lirc. My hardware.conf:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Nuvoton Transceivers/Remotes"
REMOTE_MODULES="lirc_dev nuvoton-cir"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="lirc_wb677/lircd.conf.wb677"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="Linux\ Input\ Layer\ compatible\ Remote"
REMOTE_VENDOR="Generic"

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="Nuvoton\ w836x7hg\ Infrared\ Remote\ Transceiver"
RECEIVER_VENDOR="Linux\ Input\ Device"

```My lircd.conf contains only one line aside from the comments:
```
include "/usr/share/lirc/remotes/lirc_wb677/lircd.conf.wb677"

```the lircd.conf.wb677 file is exactly as provided by the Asrock driver package. Might be a good idea to double-check all paths and verify all the files are there.

If this doesn't help, I would try checking if the irrecord program can get any data from your remote at all.

---

### Post by pieterp on 2010-10-15
Thank you very much for your step by step guide.

As a new user it was quite a daunting task but i tried to keep up with each step. i seem to have gotten stuck at the point where I edit the lirc.hwdb file. is this file downloaded from the asrock site or did I miss an earlier step that should bring load this file into /usr/share/lirc somehow. I just can't find the file to edit it. 
When extracting the deb package it seems to give me /share/lirc/remotes/lirc_wb677/lircd.conf.wb677. Could you point me in the right direction?

Btw the previous step (modprobe nuvoton-cir) gave me no error msg.

Thank you

---

### Post by supertedster on 2010-10-15
You're welcome pieterp. I hope we can get it to work in the end, and complete the guide so it works for everyone.
> **pieterp said:**
> i seem to have gotten stuck at the point where I  edit the lirc.hwdb file. is this file downloaded from the asrock site or  did I miss an earlier step that should bring load this file into  /usr/share/lirc somehow. I just can't find the file to edit it. 
Have you installed lirc?
```
sudo apt-get install lirc
```The lirc.hwdb file should come with the lirc package.

---

### Post by pieterp on 2010-10-16
That's it!
Just a quick test in xbmc seems to indicate that it does indeed work. So, thanks very much!

---

### Post by supertedster on 2010-10-16
> **pieterp said:**
> That's it!
Just a quick test in xbmc seems to indicate that it does indeed work. So, thanks very much!
Glad to hear it. That means the guide is more or less complete.

I wonder what damnstraightrandom did differently -- I suspect it may have to do with the line added to lirc.hwdb. I edited the original post to emphasize that this line is different from the line in the Asrock patch file, in case he took it from the patch file rather than copy and paste from my post.

---

### Post by Hombar on 2010-10-17
Supertedster,

Nice guide you have created. Understandable even for me who is beginner in Ubuntu. However I still have problems with getting the remote working.

I have a fresh install of Ubuntu 10.10 64bit on my HT-330. Went through the steps as per you guide. Did the kernel compile and running on that. Finished with all the steps and so far I have not seen any errors. I might have missed something but no idea where the problem reside. I see only one error which is during boot up the system drops a message "IR keymap rc-rc6-mce not found". I would appretiate if you could help me to troubleshoot this stuff.

One more thing. Since yesterday I am unable to boot up the Asrock with the remote. This was working before do not know why it stopped. I have replaced the batteries also but did not help. Weird...

Here are some outputs:

root@HTPC:~# uname -r
2.6.35.4-some-string-here
root@HTPC:~# 
root@HTPC:~# ps auxw | grep lirc
root      1161  0.0  0.0  32124   532 ?        Ss   14:00   0:00 /usr/sbin/lircd --output=/var/run/lirc/lircd --device=/dev/lirc0
root      1857  0.0  0.0  11336   876 pts/0    S+   14:19   0:00 grep --color=auto lirc
root@HTPC:~# 
root@HTPC:~# tail /var/log/syslog
Oct 17 14:00:06 HTPC kernel: [   24.557395] EXT4-fs (sda5): re-mounted. Opts: commit=0
Oct 17 14:00:07 HTPC init: plymouth-stop pre-start process (1529) terminated with status 1
Oct 17 14:00:07 HTPC rtkit-daemon[1435]: Successfully made thread 1549 of process 1429 (n/a) owned by '1000' RT at priority 5.
Oct 17 14:00:07 HTPC rtkit-daemon[1435]: Supervising 2 threads of 1 processes of 1 users.
Oct 17 14:00:08 HTPC rtkit-daemon[1435]: Successfully made thread 1554 of process 1554 (n/a) owned by '1000' high priority at nice level -11.
Oct 17 14:00:08 HTPC rtkit-daemon[1435]: Supervising 3 threads of 2 processes of 1 users.
Oct 17 14:00:08 HTPC pulseaudio[1554]: pid.c: Daemon already running.
Oct 17 14:00:11 HTPC kernel: [   29.340014] eth0: no IPv6 routers present
Oct 17 14:01:20 HTPC pulseaudio[1429]: ratelimit.c: 3 events suppressed
Oct 17 14:17:01 HTPC CRON[1806]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

---

### Post by supertedster on 2010-10-17
> **Hombar said:**
> I see only one error which is during boot up the system drops a message "IR keymap rc-rc6-mce not found".Could you give me the output of ```
sudo updatedb
locate rc-rc6-mce
```The updatedb command rebuilds your locate database, might take a minute or two.

My system loads the rc-rc6-mce module just fine -- it should be located at /lib/modules/2.6.35.4-some-string-here/kernel/drivers/media/IR/keymaps/rc-rc6-mce.ko. If it doesn't, I think the problem lies in your custom kernel, and you will have to go through building it again.

> **Hombar said:**
> One more thing. Since yesterday I am unable to boot up the Asrock with the remote. This was working before do not know why it stopped. I have replaced the batteries also but did not help. Weird...I've never tried booting up from a remote command, so I really don't know where to begin troubleshooting this one...

---

### Post by Hombar on 2010-10-17
> **supertedster said:**
> Could you give me the output of ```
sudo updatedb
locate rc-rc6-mce
```The updatedb command rebuilds your locate database, might take a minute or two.



This is what I get as a result for this one:

$ locate rc-rc6-mce
/home/hombar/src/linux-source-2.6.35/drivers/media/IR/keymaps/rc-rc6-mce.c
/lib/modules/2.6.35-22-generic/kernel/drivers/media/IR/keymaps/rc-rc6-mce.ko

---

### Post by supertedster on 2010-10-17
> **Hombar said:**
> This is what I get as a result for this one:

$ locate rc-rc6-mce
/home/hombar/src/linux-source-2.6.35/drivers/media/IR/keymaps/rc-rc6-mce.c
/lib/modules/2.6.35-22-generic/kernel/drivers/media/IR/keymaps/rc-rc6-mce.ko
The rc-rc6-mce module wasn't built when you compiled the kernel. If it were, it would reside in /lib/modules/2.6.35-22-some-string-here. I don't know why though. You have built the kernel from a newer kernel source than I did (2.6.35-22 rather than 2.6.35-4), this might be the reason although I doubt it. It could also be that you accidentally made some changes while in make menuconfig.

I think the best solution is to go through the steps for building the kernel again. Start by removing the old source directories so you start from scratch. Then, when doing make menuconfig, be careful and make sure that under Device Drivers > Multimedia Support, all the IR-related options are marked with an M. In the Device Drivers screen, Multimedia Support itself should have an M as well. The only thing you should really have to modify, though, is the Nuvoton driver, which isn't selected by default.

**Edit: did you run make localmodconfig while building the kernel? Don't. Don't run make oldconfig either.**

---

### Post by Hombar on 2010-10-17
> **supertedster said:**
> The rc-rc6-mce module wasn't built when you compiled the kernel. If it were, it would reside in /lib/modules/2.6.35-22-some-string-here. I don't know why though. You have built the kernel from a newer kernel source than I did (2.6.35-22 rather than 2.6.35-4), this might be the reason although I doubt it. It could also be that you accidentally made some changes while in make menuconfig.

I think the best solution is to go through the steps for building the kernel again. Start by removing the old source directories so you start from scratch. Then, when doing make menuconfig, be careful and make sure that under Device Drivers > Multimedia Support, all the IR-related options are marked with an M. In the Device Drivers screen, Multimedia Support itself should have an M as well. The only thing you should really have to modify, though, is the Nuvoton driver, which isn't selected by default.

**Edit: did you run make localmodconfig while building the kernel? Don't. Don't run make oldconfig either.**

Yeah, I did both "make localmodconfig" and "make oldconfig". So these steps needs to be skipped? Actually this was the first time when I did kernel compile so I did not know I should skip it or not. Anyway I think I will give it a try and rebuild the whole stuff again.

---

### Post by supertedster on 2010-10-17
> **Hombar said:**
> Yeah, I did both "make localmodconfig" and "make oldconfig". So these steps needs to be skipped? Actually this was the first time when I did kernel compile so I did not know I should skip it or not. Anyway I think I will give it a try and rebuild the whole stuff again.
Yeah, those commands might destroy any changes made during 'make menuconfig' as well as trim down the kernel modules to a bare minimum. I'm really new to this as well so I guess we're both learning as we go along :-) I edited the original post, emphasizing that those two steps should be skipped.

---

### Post by Hombar on 2010-10-18
Yesterday, I recompiled the kernel again. Took about 2-3 hours on the Asrock. I hope I will have some time to install the kernel today or within a few days. Will let you know how it goes. Is there anything else I need to do to get it working in XBMC? Or it is just fine once I finish with all these.
 
Thanks again for your help.

---

### Post by supertedster on 2010-10-18
> **Hombar said:**
> Yesterday, I recompiled the kernel again. Took about 2-3 hours on the Asrock. I hope I will have some time to install the kernel today or within a few days. Will let you know how it goes. Is there anything else I need to do to get it working in XBMC? Or it is just fine once I finish with all these.
 
Thanks again for your help.
You're welcome. If the kernel is built properly and you have lirc and xbmc installed with all the modifications I put in the guide, I don't see why it shouldn't work. If it doesn't, go through all the diagnostic steps we've talked about in this thread, and check all paths and files. Remember that some file operations require administrative rights, so check that any modifications you make to files in, say, a text editor, are actually being saved (save, close and reopen the file).

If the remote doesn't work in xbmc, test it with irw in case the problem is xbmc-related.

---

### Post by Hombar on 2010-10-18
I am stucked again. I am little bit lost at the end of the kernel installation. I think that is where I mess up this stuff. If I understand the guide correctly in 10.10 I need to use the --overlay-dir option during the kernel build. But the problem is the there is no "control-scripts" folder in my ~/linux-2.6.35/debian/ folder. It gives me this output:

# sudo cp linux-source-2.6.35/debian/control-scripts/{postinst,postrm,preinst,prerm} kernel-package/pkg/image/
cp: cannot stat `linux-source-2.6.35/debian/control-scripts/postinst': No such file or directory
cp: cannot stat `linux-source-2.6.35/debian/control-scripts/postrm': No such file or directory
cp: cannot stat `linux-source-2.6.35/debian/control-scripts/preinst': No such file or directory
cp: cannot stat `linux-source-2.6.35/debian/control-scripts/prerm': No such file or directory

Should I need to download the source again? Also even if it is working I guess I need to rebuild the kernel again. Damn...

Edit: I know it is under ~/src but I have moved the whole directory in ~ but it is still not working.

---

### Post by Hombar on 2010-10-18
Aye. I have downloaded the sorce again. Now I can see the directory there. Messed it up again. Will start again the whole stuff and rebuild the kernel... :)

---

### Post by supertedster on 2010-10-18
> **Hombar said:**
> I am stucked again. I am little bit lost at the end of the kernel installation. I think that is where I mess up this stuff. If I understand the guide correctly in 10.10 I need to use the --overlay-dir option during the kernel build. 
I'm pretty sure I didn't do those steps. Like my guide says, after you have installed the kernel and headers (these commands perform that task)
```
sudo dpkg -i linux-image-2.6.xx_i386.deb
sudo dpkg -i linux-headers-2.6.xx_i386.deb
```reboot and you should be good to go.

---

### Post by Hombar on 2010-10-18
> **supertedster said:**
> I'm pretty sure I didn't do those steps. Like my guide says, after you have installed the kernel and headers (these commands perform that task)
```
sudo dpkg -i linux-image-2.6.xx_i386.deb
sudo dpkg -i linux-headers-2.6.xx_i386.deb
```reboot and you should be good to go.

Tried it but now it it does not run the new kernel. I can not even see it in the grub menu. When I did the "dpkg -i xx.deb" it drops a window this part has been already installed and if I want to stop or not. If I say to continue than it runs but I can see a few errors during the process.

```
$ sudo dpkg -i linux-image-2.6.35.4-nuv_2.6.35.4-nuv-10.00.Custom_amd64.deb
[sudo] password for hombar: 
(Reading database ... 155548 files and directories currently installed.)
Preparing to replace linux-image-2.6.35.4-nuv 2.6.35.4-nuv-10.00.Custom (using linux-image-2.6.35.4-nuv_2.6.35.4-nuv-10.00.Custom_amd64.deb) ...
Examining /etc/kernel/preinst.d/
Done.
Unpacking replacement linux-image-2.6.35.4-nuv ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs 2.6.35.4-nuv /boot/vmlinuz-2.6.35.4-nuv
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35.4-nuv /boot/vmlinuz-2.6.35.4-nuv
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35.4-nuv /boot/vmlinuz-2.6.35.4-nuv
Setting up linux-image-2.6.35.4-nuv (2.6.35.4-nuv-10.00.Custom) ...
Running depmod.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35.4-nuv /boot/vmlinuz-2.6.35.4-nuv
 * dkms: running auto installation service for kernel 2.6.35.4-nuv              
 *       nvidia-current (260.19.06)...                                   [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs 2.6.35.4-nuv /boot/vmlinuz-2.6.35.4-nuv
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35.4-nuv /boot/vmlinuz-2.6.35.4-nuv
update-initramfs: Generating /boot/initrd.img-2.6.35.4-nuv
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35.4-nuv /boot/vmlinuz-2.6.35.4-nuv
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35.4-nuv.postinst line 341.
dpkg: error processing linux-image-2.6.35.4-nuv (--install):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35.4-nuv
```

---

### Post by supertedster on 2010-10-18
> **Hombar said:**
> Tried it but now it it does not run the new kernel. I can not even see it in the grub menu. When I did the "dpkg -i xx.deb" it drops a window this part has been already installed and if I want to stop or not. If I say to continue than it runs but I can see a few errors during the process.
It would probably be a good idea to first remove the old custom kernel, both linux-image and linux-headers. Then reboot, reinstall the new custom kernel and reboot again.

---

### Post by Hombar on 2010-10-19
> **supertedster said:**
> It would probably be a good idea to first remove the old custom kernel, both linux-image and linux-headers. Then reboot, reinstall the new custom kernel and reboot again.

I have removed, purged both the header and the image file. Restarted the stuff checked with "sudo dpkg -l | grep linux-he" and "linux-im" and I am sure they were not listed there. Tried again to install the header and image file and got exactly the same error I posted before. Do I need to do anything elase the "sudo dpkg -r" and "--purge" to remove these packeges from the box?

---

### Post by supertedster on 2010-10-19
> **Hombar said:**
> I have removed, purged both the header and the image file. Restarted the stuff checked with "sudo dpkg -l | grep linux-he" and "linux-im" and I am sure they were not listed there. Tried again to install the header and image file and got exactly the same error I posted before. Do I need to do anything elase the "sudo dpkg -r" and "--purge" to remove these packeges from the box?
If dpkg doesn't show them anymore, and 'uname -r' shows you running the generic (default Ubuntu) kernel, then try to reinstall your new custom kernel. Otherwise, reboot first and check again.

---

### Post by Hombar on 2010-10-20
> **supertedster said:**
> If dpkg doesn't show them anymore, and 'uname -r' shows you running the generic (default Ubuntu) kernel, then try to reinstall your new custom kernel. Otherwise, reboot first and check again.
 
I get the above mentioned error when I try to install the custom kernel image file. If I reboot the PC after it I can not choose to run the new image. On the weekend I will try to start from scratch and see how it goes.

---

### Post by supertedster on 2010-10-20
> **Hombar said:**
> I get the above mentioned error when I try to install the custom kernel image file. If I reboot the PC after it I can not choose to run the new image. On the weekend I will try to start from scratch and see how it goes.
I googled the error message, it turned up [this launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/303795"). Try
```
sudo apt-get purge nvidia-common
sudo apt-get install nvidia-common
```Then reinstall the new kernel. This seems to have helped the people who experience this bug, read the launchpad page for more info. Hopefully you won't have to start from scratch.

---

### Post by Hombar on 2010-10-24
Today started from scratch again. New install, new compile, whatever. The guide is good, however sometimes I had hard times to understand what the hell is going on since I am new to linux also. But finally I could get this remote working. 

Just one additional comment for the guide however it might be obvious for hardcore linux users. I had to install lirc before copying the files into /usr. By the defualt it is not there so have to add it with "sudo apt-get install lirc".

So stuff is working under XBMC. Have to buy an USB  TV tuner so I will try it with also MythTV.

Thanks again for you help, superstedster.

---

### Post by P-A on 2010-10-24
Great post!

I try to apply this guide on my newly installed Asrock Nettop 330HT with Ubuntu 10.10 box with kernel version 2.6.35-22-generic. 

I'm new to this and compiling the kernel is nothing I have ever done before. Seems like I'm stuck already on Step 2: Applying the Nuvoton driver patch. I have downloaded the driver patch and tried to apply it with:
patch -p1 < ~/Downloads/IR-add-driver-for-Nuvoton-w836x7hg-integrated-CIR.patch

There is no output in the console and no signs of anything going on, command does not exit, it has been quiet for an hour or so. How long shall I expect this step to take? 

Is there some pieces of information I can retrieve from my installation in order for you guys to help out here?

Regards

---

### Post by supertedster on 2010-10-24
Glad to hear it's working, Hombar.

> **P-A said:**
> I'm stuck already on Step 2: Applying the Nuvoton driver patch. I have downloaded the driver patch and tried to apply it with:
patch -p1 < ~/Downloads/IR-add-driver-for-Nuvoton-w836x7hg-integrated-CIR.patch

There is no output in the console and no signs of anything going on, command does not exit, it has been quiet for an hour or so. How long shall I expect this step to take?
Shouldn't take more than a second or two. Press Ctrl+C, you did something wrong.

1. Do you have the patch file in your /home/username/Downloads directory?
2. What directory did you cd into?
3. Did you perform the command exactly as written in the guide?


To all readers: since we know for sure that the guide provides the necessary steps to get the remote working, please try to do the following before posting:


[LIST]
[*]Google for tutorials and explanations.
[*]Get help from someone who knows their way around a linux command prompt, either via IRC or in real life.
[*]Consider installing an older version of Ubuntu. It is much easier getting the remote to work in 10.4, for example.
[*]Google it. Again.
[/LIST]

---

### Post by Hombar on 2010-10-25
> **supertedster said:**
>  
Shouldn't take more than a second or two. Press Ctrl+C, you did something wrong.


Confirmed this part should go quickly. P-A, make it sure you work in the correct directories. If you are not sure than just follow the guide as says and it should work. The kernel compile is the only part which requires hours for the hardware so make is sure everything is fine prior launching that. I had to run it three times... But at least I am getting more familiar with this stuff. :)

---

### Post by P-A on 2010-10-25
Thank you supertedster and Hombar for your replies.

You are right, I did something wrong. I accidentally omitted the "less than" character in the patch command :oops: Works much better with it (!) and now the compilation is ongoing.

Well - At least I learned to read the manual more carefully! Hope for success!
Thanx



__

---

### Post by scoppa on 2010-10-29
thank you very much [supertedster]("http://ubuntuforums.org/member.php?u=1161002") it works very well now.:P

---

### Post by bance on 2010-10-29
Hi guys, 

I'm trying to follow this 'Howto'....   I can get as far as running Jarod's patch, but when I open the makefile it's empty. Anybody got any ideas about where I'm going wrong?

TIA Steve

 uname -r
2.6.32-25-generic

---

### Post by boomstam on 2010-10-30
Updated after a second try:

I also wanted to install my remote, but did not want to build my own kernel like supertedster.

The idea with a module is that it can be inserted in an existing kernel. Try the following steps instead of the first 3 of supertedster. Also perform step 4 to complete the process.

I tried to reconstruct it order of the instructions, but could have missed some elements. The more simple approach is worth a try.

Start by installing LIRC:
```
sudo apt-get install lirc lirc-modules-source 
```Install linux headers
```
sudo apt-get install linux-headers-$(uname -r)
```Download the module [package]("http://http://www.scintilla.utwente.nl/%7Esjorsh/mod_nuvoton.tar.gz")

Extract it using:
```
tar -xvzf mod_nuvoton.tar.gz
```Enter the directory:
```
cd mod_nuvoton
```Build the module:
```
make
```Install the required ir-core module:
```
cd /lib/modules/$(uname -r)/kernel/drivers/media/IR
sudo insmod ir-core.ko
sudo modprobe ir-core
sudo depmod -a
```Go back to the directory mod_nuvoton
```
Install the nuvoton module:
sudo insmod nuvoton-cir.ko
sudo modprobe nuvoton-cir
depmod -a
```dmesg can be used to check for errors.

Do not forget to perform step 4 of supertedster.

---

### Post by J0Sb31R on 2010-10-31
@boomstam Great! but looks like your download link is not working anymore. can your re-upload?

Thanks!

> **boomstam said:**
> I also wanted to install my remote, but did not want to build my own kernel like supertedster.

The idea with a module is that it can be inserted in an existing kernel. Try the following steps instead of the first 3 of supertedster. Also perform step 4 to complete the process.

I tried to reconstruct it order of the instructions, but could have missed some elements. The more simple approach is worth a try.

Start by installing LIRC:
```
sudo apt-get install lirc
```Install linux headers
```
sudo apt-get install linux-headers-$(uname -r)
```

Download the module [package]("http://http://www.scintilla.utwente.nl/%7Esjorsh/mod_nuvoton.tar.gz")

Extract it using:
```
tar -xvzf mod_nuvoton.tar.gz
```Enter the directory:
```
cd mod_nuvoton
```Build the module:
```
make
```Install the required ir-core module:
```
cd /lib/modules/$(uname -r)/kernel/drivers/media/IR
sudo insmod ir-core.ko
sudo modprobe ir-core.ko
sudo depmod -a
```Go back to the directory mod_nuvoton
```
Install the nuvoton module:
sudo insmod nuvoton-cir.ko
sudo modprobe nuvoton-cir
depmod -a
```dmesg can be used to check for errors.

Do not forget to perform step 4 of supertedster.

---

### Post by setarcos on 2010-10-31
[J0Sb31R]("http://ubuntuforums.org/member.php?u=117746") remove the additional http// in boomstam's link (it should be [http://www.scintilla.utwente.nl/%7Esjorsh/mod_nuvoton.tar.gz](http://www.scintilla.utwente.nl/%7Esjorsh/mod_nuvoton.tar.gz) )

---

### Post by J0Sb31R on 2010-10-31
thanks! didn't see that one. Got it working. Thanks all!
> **setarcos said:**
> [J0Sb31R]("http://ubuntuforums.org/member.php?u=117746") remove the additional http// in boomstam's link (it should be [http://www.scintilla.utwente.nl/%7Esjorsh/mod_nuvoton.tar.gz](http://www.scintilla.utwente.nl/%7Esjorsh/mod_nuvoton.tar.gz) )

---

### Post by J0Sb31R on 2010-10-31
Can't get resume from stand by to work.

Can anyone confirm this?

I enabled CIR en /proc/acpi/wakeup but no go.

compiling kernel now, hope that gives a difference.

---

### Post by setarcos on 2010-10-31
I can confirm. Even after enabling in proc/acpi/resume, it doesn't work (although resume from keyboard works).

It seems to be a kernel bug in recent versions.

---

### Post by J0Sb31R on 2010-10-31
Bugger, i am so tired with nuvoton chip and linux support. i'm just going to buy an out of the box compatible MCE remote i think.. :-)

> **setarcos said:**
> I can confirm. Even after enabling in proc/acpi/resume, it doesn't work (although resume from keyboard works).

It seems to be a kernel bug in recent versions.

---

### Post by toker_ on 2010-11-04
10.10 sucks, so many bugs.  

Cant even Resume from Suspend, I cant believe that you have to re-compile a Kernel to get a 'Remote' to work.  (thats a joke)

Whats wrong with installing a driver like any other OS.

Using boomstam method 

sudo modprobe ir-core.ko  (throws an error for me), cant not proceed any further. Very annoying.

I have purchased a USB MCE IR Receiver, plugged it in a worked straight way, need to remapping keys for XBMC now.

---

### Post by dajomu on 2010-11-04
Fedora 14 now supports the Asrock ion 330ht remote-control out of the box...

---

### Post by supertedster on 2010-11-04
> **dajomu said:**
> Fedora 14 now supports the Asrock ion 330ht remote-control out of the box...
I was just contemplating switching myself. I've had troubles with my left mouse button dying on me in Maverick, and [_I'm not the only one_](https://bugs.launchpad.net/ubuntu/maverick/+source/linux/+bug/636311). Only problem is that there is currently no way that I know of to get Boxee working in Fedora...

---

### Post by Huwle on 2010-11-05
Great thread. Just what I needed to rescue my asrock mythbuntu box following an ill-advised upgrade to 10.10. That's the first time I've ever built a kernel.
The original post worked perfectly for me except when it came to installing the new kernel. Un-installing the nvidia-common package, reinstalling the new kernel, reinstalling nvidia-common did the job.

---

### Post by supertedster on 2010-11-12
_[A driver for 10.10 is now available from Asrock](http://www.asrock.com/Nettop/download.asp?Model=ION%20330HT&o=Linux)_.

---

### Post by megabrein on 2010-11-18
> **supertedster said:**
> _[A driver for 10.10 is now available from Asrock]("http://www.asrock.com/Nettop/download.asp?Model=ION%20330HT&o=Linux")_.
Unfortunately this driver does not work. Following the install instruction provided by asrock results in several [fail] messages during install. The result is that the remote does not work. I have tried several guides to fix it but screwed up my ubuntu configuration in the process. As I am using ubuntu only for a week now (trieing to get it to run on my ion 330 I have formatted the hdd and installed ubuntu for the 2nd time (no better than windows until now ;-)

I'am compiling the kernal right now :popcorn:

(:Dnever needed to do that for mr. gates.....)

---

### Post by megabrein on 2010-11-19
Aaargh....

I am at step 4 and downloaded and extracted the Asrock drivers. The custom kernel seems to be running. 

I am stuck at copying the extracted usr directory to /usr. nautilus refuses to do that and runs into a lot of errors when I try to start it with sudo nautilus.

Nautilus is my only way to handle the IR(10.4)kernel2.6.32-23. When I try cd IR(10.04)kernel2.6.32-23 I get: bash: syntax error near unexpected token `(' :o

My work around is to use nautilus to copy the share directory to my home folder. However it is not allowed to copy it to /usr

Using  "cp share /usr" results in "cp: omitting directory `share'" :-(
No idea what that means.......

I still hear the echo in my head from that nice gui who presented ubuntu as the human friendly OS. I am proud to say that I have compiled a kernal using cryptic language and absolutely no idea what's happening. 

All this just to get a response from that asrock remote. What am I doing ????????????

Anybody wants to help ?

---

### Post by louix on 2010-11-21
The driver for ubuntu 10.10 can be found here: [http://www.asrock.com/nettop/download.asp?Model=ION%20330HT-BD&o=Linux](http://www.asrock.com/nettop/download.asp?Model=ION%20330HT-BD&o=Linux)

---

### Post by setarcos on 2010-11-21
> **megabrein said:**
> Nautilus is my only way to handle the IR(10.4)kernel2.6.32-23. When I try cd IR(10.04)kernel2.6.32-23 I get: bash: syntax error near unexpected token `(' :o
You have to put a '\' before ( and ) as in cp IR\(10.04\)kernel...

Btw, I installed the driver and it worked, although I gave up on Ubuntu and just installed xbmcfreak RC with nuvoton ir support (I use the box just as a media center).

---

### Post by megabrein on 2010-11-22
> **setarcos said:**
> You have to put a '\' before ( and ) as in cp IR\(10.04\)kernel...

Btw, I installed the driver and it worked, although I gave up on Ubuntu and just installed xbmcfreak RC with nuvoton ir support (I use the box just as a media center).

Thankx Setarcos,

Adding some \ works. I'm still not able to copy the files but can cd now.

I am surprised that the asrock drivers for ubuntu 10.10 worked for you. Even after a fresh install of ubuntu it gives a list of [fail] messages and indeed does not work.

I have tried the xbmcfeak live cd. That one works flawlessly but I want to do more with my box than using it as a media center.

---

### Post by setarcos on 2010-11-24
You need to use sudo to copy the files.

Edit: btw, why are you copying files? If you follow the howto link in asrock site, the only thing you have to do in terminal is sudo dpkg -i lirc-nct677x-1.1.0-ubuntu10.10-kernel2.6.35.deb in the directory where the file named lirc-nct677x-1.1.0-ubuntu10.10-kernel2.6.35.deb is placed.

---

### Post by megabrein on 2010-11-25
> **setarcos said:**
> You need to use sudo to copy the files.

Edit: btw, why are you copying files? If you follow the howto link in asrock site, the only thing you have to do in terminal is sudo dpkg -i lirc-nct677x-1.1.0-ubuntu10.10-kernel2.6.35.deb in the directory where the file named lirc-nct677x-1.1.0-ubuntu10.10-kernel2.6.35.deb is placed.
Thanks for your answer.

When I sudo dpkg ...... the asrock driver there are 4 fail messages and the remote does not work. Therefore I am following this thread to build the custom kernal to get the remote going. I am stuck at step 4 as indicated in post #3 of this thread.

Everything went ok but I am not capable of copying the drivers because I don't know the proper command to do that. I think I need the cp command but I don't know the right formula :confused:
Regards,

Megabrein

---

### Post by setarcos on 2010-11-25
Paste here the error messages that appear after the sudo dpkg command.

Edit: to bypass the error in copying files, try tu use sudo cp -R "name of the directory"

---

### Post by megabrein on 2010-11-26
:D> **setarcos said:**
> Paste here the error messages that appear after the sudo dpkg command.

Edit: to bypass the error in copying files, try tu use sudo cp -R "name of the directory":D

Hi Setarcos,

The sudo cp -R command did the job. And guess what I am currently running my custom kernel and the remote is working perfectly :)

Thanks for your advise,

Megabrein:popcorn:

---

### Post by setarcos on 2010-11-26
I'm glad you've managed to put it to work :)

---

### Post by PatrickVogeli on 2010-12-05
Hi there,

I have an Asrock 330Ht too, and at the moment I keep running 10.04. Since this machine is only used as HTPC it's not that important to update to 10.10, but I think it would be nice. Nobody has tried the 10.10 drivers in the asrock website? I tried installing them on my laptop, and they installed and loaded fine, but of course my lappy hasn't the related hardware to try xD.

I'm not goint to compile a kernel to get the remote working.. I might just skip this release of ubuntu and hope 11.04 has the fix.

---

### Post by Trond A on 2010-12-21
Hello,

I have recently been trying to get the ASRock 100HT Nuvoton remote to work with Ubuntu, and even though I’ve tried to complete the two guides in this thread several times, these methods have still left me unsuccessful (and I am still not sure why :S )

However, I just managed to get it working - using the stock ASRock 10.10 drivers, and I suspect that the reason is that I installed the “regular” kernel instead of the PAE kernel (I got the tip from here [http://forum.xbmc.org/showpost.php?p=658379&postcount=384](http://forum.xbmc.org/showpost.php?p=658379&postcount=384) , but I have no idea if this is a mere coincidence or that the AS Rock drivers actually aren’t supposed to work with PAE).

Here are the steps I made in order to get it to work. I started out by downloading the 12.7mb Maverick Meerkat iso from here: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

(Note that I am setting up my system from scratch here, so I have no clue what consequenses this may have for existing installations)

*Choose regular install, and when the list of packages popped up, I chose to install Ubuntu Desktop, SSH server and Samba (yeah, these may be irrelevant).

*Once the installation is complete, and logged into Gnome, enter a terminal and do:
[PHP]sudo apt-get install linux-image-2.6.35-24-generic linux-headers-2.6.35-24-generic [/PHP] (I got the version number by inspecting **sudo apt-cache search linux-image**)

*After installation is complete, inspect **/boot/grub/grub.cfg** - in my case, the *generic-pae* kernels are at the top (slot 0 and safe at slot 1), while *generic* (regular) is now in slot 2 and 3. Change the setting **GRUB_DEFAULT=2** instead of **0** in **/etc/default/grub** 

*Run this and reboot [PHP]sudo update-grub[/PHP]

*Open a new terminal, and run **uname -r** to make sure the current kernel is *generic* and not *generic-pae*.

The next steps more or less follow the AS Rock installation guide at their website ( [http://www.asrock.com/Nettop/download.asp?Model=Core%20100HT-BD&o=Linux](http://www.asrock.com/Nettop/download.asp?Model=Core%20100HT-BD&o=Linux) ), but I chose to do it in the terminal instead because of the scary error messages I saw earlier when I tried to do it via Synaptic - I do not know if this actually makes any difference.

Start off by installing Lirc:

[PHP]sudo apt-get install lirc[/PHP]

Choose **none** and **none** when prompted for receiver and transmitter.

[PHP]sudo apt-get install lirc-modules-source[/PHP]


*Enter a folder where you want to download the drivers, and enter:
[PHP]
wget "http://europe.asrock.com/downloadsite/drivers/Nettop/Ubuntu/IR(10.10)2.6.35-22.zip"

unzip IR\(10.10\)2.6.35-22.zip[/PHP]

*Enter the newly created folder, and install the driver like this:

[PHP]sudo dpkg -i lirc-nct677x-1.1.0-ubuntu10.10-kernel2.6.35.deb [/PHP]

At the first prompt, scroll down and choose the **Nuvoton** device, and **none** when prompted again. 

When back at the command line, type in **irw** and test out the remote - it should dump messages to the console when buttons are pressed, and it also seems to work correctly in XBMC.

That should be it - yes, DAE is gone, so that’s not optimal. I’m curious to what conclusions the more experienced users in here can draw from this :)

Note that we didn’t have to do the latest steps from the AS Rock manual - does that make the *lirc-modules-source* redundant to install?

-Trond

---

### Post by vikjon0 on 2010-12-27
> Quote:
Originally Posted by dajomu  
Fedora 14 now supports the Asrock ion 330ht remote-control out of the box... 

I was just contemplating switching myself. 

It is not necessary to switch distro..a solution that perhaps is a bit quicker than compiling a new kernel is to upgarde to kernel 37 that also support the remote out of box. Alternatively installing a stable kernel that is supported by asrock. I have only done this on Lucid but it shouldnt be any harder on Maverick? Strangly enough I cant find any info about in what repository holds the 2.6.37 kernel for maverick...

This works fine on Lucid:

> sudo add-apt-repository ppa:kernel-ppa/ppa 
sudo apt-get update

sudo apt-get install linux-image-generic-lts-backport-natty 
(sudo apt-get install linux-image-2.6.37-10-generic)*


sudo reboot

No Lucid repository I can find have nvidia builds that works with this kernel, instead we have to install it manually.

sudo apt-get install linux-headers-$(uname -r)
sudo apt-get --purge remove nvidia-*

mkdir Downloads
cd Downloads 

wget [http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/NVIDIA-Linux-x86-260.19.29.run](http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/NVIDIA-Linux-x86-260.19.29.run)
sh NVIDIA-Linux-x86-260.19.29.run

(nvidia-installer --uninstall)**

*Tested version
**Uninstall nvidia

NB: This kernel is still in RC status.

---

### Post by vikjon0 on 2010-12-27
Ok, if anyone want to try this on 10.10 here is a ppa:
```
add-apt-repository ppa:xorg-edgers/ppa
```Only problem is that it contains alot of other stuff so be carefull with what you install and dont do a general upgrade.

EDIT:
Or download the debs from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) instead. It is probably safer

I didnt try this ppa on the asrock only in virtual machine.

---

### Post by ejosdie on 2011-02-05
Hi,

Searching the solution to the same problem, I found [here]("http://myplace.dk/2010/12/27/linux-on-asrock-core-100ht/") your answers. I will just copy&paste the solution. Credits to the writer.


ASRock has two Linux-downloads for the Core 100HT: Infrared driver for Ubuntu 10.4, and infrared driver for Ubuntu 10.10. The latter has a great manual, but there’s a lot of steps. The style in the manual is “click this, click that, type this, type that” etc., which I think is what most people want. I prefer a more terse syntax, with commands I can copy/paste to the terminal. Like this:

[INDENT]sudo apt-get update 
sudo apt-get install lirc lirc-modules-source [/INDENT]

- Remote control configuration: None 
- IR transmitter, if present: None 

unzip -d /tmp/ "IR(10.10)2.6.35-22.zip"

Install one of these, ignore errors: 
    [LIST]
[*]32 bit: sudo dpkg -i /tmp/Ubuntu\ 10.10/lirc-nct677x-1.1.0-ubuntu10.10-kernel2.6.35.deb 
[*]    64 bit: sudo dpkg -i /tmp/Ubuntu\ 10.10/lirc-nct677x-x64-1.1.0-ubuntu10.10-kernel2.6.35.deb
[/LIST]

Again, ignore errors: 
[INDENT]sudo dpkg -i /tmp/Ubuntu\ 10.10/lirc-nct677x-src-1.1.0-ubuntu10.10.deb 
cd /usr/src sudo dkms 
remove -m lirc -v 0.8.7~pre3 --all 
sudo dkms add -m lirc -v 0.8.7~pre3 
sudo dkms build -m lirc -v 0.8.7~pre3 
sudo dkms install -m lirc -v 0.8.7~pre3 --force 
sudo dpkg-reconfigure lirc [/INDENT]

- Remote control configuration: Nuvoton Transceivers/Remotes 
- IR transmitter, if present: None

Test by running the command "irw", and push some buttons on the remote. It should output the name of the buttons you press.

---

### Post by mooscape on 2011-02-06
I found getting the CIR to work the easy bit! The problem is that their drivers mess up the system. I get the following error when trying to upgrade or install new programs: 

> An error occured, please run Package Manager from the right-click menue or apt-get in the terminal to see what is wrong. The error message was :'Unknown Error:'<type 'exceptions.SystemError'>'(E:The package lirc-nct677x-src needs to be reinstalled, but I can't find an archive for it.)'This usually means that your installed packages have unmet dependencies

I have tried reinstallation and letting the system try and reconfigure the packages. Neither works. In fact the reconfigure breaks the working CIR setup. It seems I can either update my machine (Asrock 100HT) or have a working CIR, but not both.  

I wish ASRock where as keen to find a (non-clown) solution as they where to take my money.

---

### Post by bedege on 2011-02-10
Hi there

Contrary to most people who have contributed to that interesting thread, I do not own an Asrock Nettop. I just purchased a Jetway Ion-Top from Newegg. Its name is [JBC231C98-525]("http://www.jetwaycomputer.com/ITX-JBC231C98-525.html"): it has an Atom D525 together with an ION2 GPU. It is based on the NC98-525E-LF mini-ITX mobo from Jetway, nicelly fitted in a (not so) little box that has an IR receiver.

From another forum ([here]("http://forums.boxee.tv/showthread.php?t=17684")), I understand that previous version of the Jetway Ion-Top (with an Atom 330, but apparently identically looking box) used the same Nuvoton IR receiver as Asrock's, so that that gentleman was able to make his remote work on Ubuntu using one of Asrock deb package for the Nuvoton.

**Does anybody know if that same Nuvoton receiver is also used on this more recent Jetway Ion-Top?** I don't really have a clue, plus I don't have any M$ OS on that HTPC, and no plan to do so.:D Any way to figure that out with Linux, without actually installing the Nuvoton driver and giving a try?

Any help/feedback appreciated.

---

### Post by eViL_oNe on 2011-02-21
After updating to kernel 2.6.35-25, the asrock driver stopped working. I had similar problems switching from 23 to 24, but I could fix it by reinstalling the driver a couple times (until the error messages mysteriously went away and irw started working). Unfortunately, this doesn't seem to work with 25.

The nuvoton-cir driver works fine but resuming from standby seems broken, see also 

[http://sourceforge.net/mailarchive/message.php?msg_id=26985991](http://sourceforge.net/mailarchive/message.php?msg_id=26985991)

Therefore, I switched back to 24 and disabled auto-updating the kernel (by removing the linux-headers-generic and linux-image-generic packages) until this issue hopefully will be fixed.

---

### Post by eViL_oNe on 2011-03-06
Update: the resume problem was fixed: [http://sourceforge.net/mailarchive/forum.php?thread_name=7CB1D0BC-3F18-4315-89DA-9FA88A05604B%40wilsonet.com&forum_name=lirc-list](http://sourceforge.net/mailarchive/forum.php?thread_name=7CB1D0BC-3F18-4315-89DA-9FA88A05604B%40wilsonet.com&forum_name=lirc-list)

Let's see if this fix will get to 2.6.38 and Natty ;)

---

### Post by esigal on 2011-03-07
hello this is my first post to ubuntuforums, please excuse if this is ill formatted.
 
I have a jetway JC600C99 atom D525 Nvidia Ion system
I have everything installed but irw does not dump any codes to std out.
I am running the generic non PAE kernel
 
> esigal@jetway:~$ uname -r
2.6.35-22-generic

 
lirc_wb677 module is loaded
> 
esigal@jetway:~$ lsmod | grep lirc
lirc_wb677 23890 1
lirc_dev 9510 3 lirc_wb677
 
esigal@jetway:~$ dmesg | grep lirc
[ 5.352233] lirc_dev: IR Remote Control driver registered, major 61
[ 5.392597] lirc_wb677 Start calling lirc_register_driver().
[ 5.392605] lirc_dev: lirc_register_driver: sample_rate: 0
[ 5.394018] lirc_wb677 End calling lirc_register_driver().
[ 5.394028] lirc_wb677 register lirc minor: 0
[ 5.499419] lirc_wb677 : set use inc
[ 5.499454] lirc_wb677: IO Ctrl Code:-2147194624

 
Lirc is running
 
> 
esigal@jetway:~$ ps aux | grep lirc
root 1059 0.0 0.0 1844 76 ? Ss 21:04 0:00 /usr/bin/irexec -d /etc/lirc/lircrc
root 1061 0.0 0.0 3508 584 ? Ss 21:04 0:00 /usr/sbin/lircd --output=/var/run/lirc/lircd --device=/dev/lirc0
 

 
Both prior to and after lirc was installed the system supplied remote would power on/off the device and provide mouse movement and mouse clicks. none of the buttons supplied any output to irw.
My goal is to have the system recognize hauppauge remote codes to control my MythTV front end.
I have the following lines in my /etc/lirc/lircd.conf
 
>  
#Configuration for the Nuvoton Transceivers/Remotes remote:
include "/usr/share/lirc/remotes/lirc_wb677/lircd.conf.wb677"
include "/usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge"

 
Is there something I am missing?
there is a lircrc in the /home/user folder that mythtv runs as, but I assume that irw should still dump keypresses.
 
As a side question is this module going to be built in to upcoming kernels without having to patch lirc?
I really would like to avoid having to compile a custom kernel.
Any help is greatly appreciated.
thanks

---

### Post by ThomasNovin on 2011-03-16
Very nice guide in post #3. First time I compiled my own kernel in a loong time :) Worked out fine! Thanks.

We can thank higher powers (or more precisely Jarod Wilson & Nuvoton PS Team) that this driver is now finally included in the kernel in the coming Ubuntu Natty 11.04-release.

Edit: I also found that I had problem with resume from suspend via the remote. I read the post on [http://ubuntuforums.org/showpost.php?p=10481436&postcount=63](http://ubuntuforums.org/showpost.php?p=10481436&postcount=63). I changed 
/usr/src/linux-source-2.6.35/drivers/media/IR/nuvoton-cir.h row 310 to 

#define CIR_WAKE_FIFO_LEN               65

as suggested there and will now recompile the kernel. Fingers crossed..

Btw, the post in this thread on how to add the module to the current kernel instead seems easier & faster. Compiling a kernel on my ASrock ION 330-HT took 2-3 hours.

[COLOR="DarkGreen"]**Edit2: This works! Resume from suspend via the power button on the remote works perfectly after changing according to above.**[/COLOR]

---

### Post by djste on 2011-05-24
hi Thomas.
I read that you have an asrock remote and it work perfect; so I can ask you a few tips? because my remote doesn't work...
I have  ubuntu 11.04 fully updated with lirc and i have loaded nuvoton_cir module but when i try with irw, the remote show nothing on screen..
thanks

---

### Post by ThomasNovin on 2011-05-24
> **djste said:**
> hi Thomas.
I read that you have an asrock remote and it work perfect; so I can ask you a few tips? because my remote doesn't work...
I have  ubuntu 11.04 fully updated with lirc and i have loaded nuvoton_cir module but when i try with irw, the remote show nothing on screen..
thanks

I wrote a guide to get a fully working setup on Natty on XBMC forums.

[http://forum.xbmc.org/showthread.php?p=798760#post798760](http://forum.xbmc.org/showthread.php?p=798760#post798760)

---

### Post by optiix on 2011-11-15
Hello. I just followed the linked guide to get the kernel source and everything.
But before I proceed with building the kernel I shall patch as I understand?

The url to the patch is broken but I think I found it elsewhere ( [http://patchwork.linuxtv.org/patch/7592](http://patchwork.linuxtv.org/patch/7592) ) I used nano and copy / paste everything below the black "Patch" header into a new file I called "jarod.nuvoton.patch.patch" and then I used the command specified in this guide for the patching part.

This is the error I get:

optiix@optiix-server:~/linux-2.6.35$ sudo patch -p1 < /home/optiix/jarod.nuvoton.patch.patch 
patching file drivers/media/rc/nuvoton-cir.c
Hunk #1 FAILED at 624.
Hunk #2 FAILED at 637.
Hunk #3 FAILED at 1054.
3 out of 3 hunks FAILED -- saving rejects to file drivers/media/rc/nuvoton-cir.c.rej
patching file drivers/media/rc/nuvoton-cir.h
Hunk #1 FAILED at 67.
1 out of 1 hunk FAILED -- saving rejects to file drivers/media/rc/nuvoton-cir.h.rej

As you see I am in the linux kernel folder and giving the patch command the right location of the patch file. ( or? )
I have the AsRock ION 3D.

Isn't there any easier way to get this working? Why have the LIRC project not included this IR remote yet, or why do I not find any simple and working app for ubuntu with GUI that I just get to choose "Play" on the screen then a text blinks or something "Press your play button". TO make it work with lirc.  They should really make a such app :|

Thanks, optiix.

---

### Post by radic2004 on 2012-12-21
> **optiix said:**
> Hello. I just followed the linked guide to get the kernel source and everything.
But before I proceed with building the kernel I shall patch as I understand?

The url to the patch is broken but I think I found it elsewhere ( [http://patchwork.linuxtv.org/patch/7592](http://patchwork.linuxtv.org/patch/7592) ) I used nano and copy / paste everything below the black "Patch" header into a new file I called "jarod.nuvoton.patch.patch" and then I used the command specified in this guide for the patching part.

This is the error I get:

optiix@optiix-server:~/linux-2.6.35$ sudo patch -p1 < /home/optiix/jarod.nuvoton.patch.patch 
patching file drivers/media/rc/nuvoton-cir.c
Hunk #1 FAILED at 624.
Hunk #2 FAILED at 637.
Hunk #3 FAILED at 1054.
3 out of 3 hunks FAILED -- saving rejects to file drivers/media/rc/nuvoton-cir.c.rej
patching file drivers/media/rc/nuvoton-cir.h
Hunk #1 FAILED at 67.
1 out of 1 hunk FAILED -- saving rejects to file drivers/media/rc/nuvoton-cir.h.rej

As you see I am in the linux kernel folder and giving the patch command the right location of the patch file. ( or? )
I have the AsRock ION 3D.

Isn't there any easier way to get this working? Why have the LIRC project not included this IR remote yet, or why do I not find any simple and working app for ubuntu with GUI that I just get to choose "Play" on the screen then a text blinks or something "Press your play button". TO make it work with lirc.  They should really make a such app :|

Thanks, optiix.

Ubuntu 11.10+12.04 working remote on Asrock ION 330   HT
  
  First setup LIRC with a basic configuration
  For a new install sudo apt-get install lircIf LIRC is already installed sudo   dpkg-reconfigure lircRemote control configuration:
  Windows Media Center Transceivers/Remotes (all)
  IR transmitter, if present:
  None
  
  Change the default configuration to work with the Nuvoton remote
  sudo vi /etc/lirc/hardware.conf
  
  Change the following 3 lines
  REMOTE="Windows Media Center Transceivers/Remotes (all)"
  REMOTE_MODULES="lirc_dev mceusb"
  REMOTE_DRIVER=""
  
  into this
  
  REMOTE="Nuvoton Transceivers/Remotes"
  REMOTE_MODULES="lirc_dev nuvoton-cir"
  REMOTE_DRIVER="default"
  
  Restart LIRC to apply the changes
  sudo service lirc restart

---

### Post by radic2004 on 2012-12-21
[FONT=Times New Roman][SIZE=3]Ubuntu 11.10+12.04 working remote on Asrock ION 330   HT
  
  First setup LIRC with a basic configuration
  For a new install sudo apt-get install lircIf LIRC is already installed sudo   dpkg-reconfigure lircRemote control configuration:
  Windows Media Center Transceivers/Remotes (all)
  IR transmitter, if present:
  None
  
  Change the default configuration to work with the Nuvoton remote
  sudo vi /etc/lirc/hardware.conf
  
  Change the following 3 lines
  REMOTE="Windows Media Center Transceivers/Remotes (all)"
  REMOTE_MODULES="lirc_dev mceusb"
  REMOTE_DRIVER=""
  
  into this
  
  REMOTE="Nuvoton Transceivers/Remotes"
  REMOTE_MODULES="lirc_dev nuvoton-cir"
  REMOTE_DRIVER="default"
  
  Restart LIRC to apply the changes
  sudo service lirc restart [/SIZE][/FONT]

---

