---
title: "ATI Remote Wonter Plus not working"
date: 2011-11-05
forum: Mythbuntu
---

### Post by bonbasket on 2011-11-05
I am trying to get my ATI Remote Wonder Plus remote control working under the latest release Mythbuntu 11.10.

I read a lot of posts that this remote is supposed to be supported two ways, either via the kernel as a keyboard/mouse or via LIRC using the remote.

Most of the posts for this remote are old prior to 2008 which is about when the kernel's were updated with plug and play support.  So I am assuming these remotes are supposed to  be plug and play and I am missing something in my setup?

My problem is it does not work plug and play.  The remote is recognized when I plug in the USB receiver as an ati_remote using lsmod command.  I also see the remote in the mouse settings menu as one of my mice but it still does not work.

Does anyone have any support with setting up this remote on linux ubuntu?

My remote works fine under windows vista business so I know the hardware works.  

How do I assign the channel?  Looking at the driver code it support a "channel_mask" which by default is set to 0 so it is supposed to receive on all 16 channels supported by  this remote.  Do I need to rebuild the driver to and patch the kernel to use the same remote on multiple computers?  Is there a config file or environment variable which I can used to set the "channel_mask" so  that the ATI driver does not use the default.  I would be happy first getting the remote on any channel.

My other thought is that this is an ATI remote wonder plus which is supposed to be a upgrade of the original ATI remote wonder.  The ATI Remote Wonder 2 is supposedly different from the original and plus.  That is like why my remote is seen as a ati_remote instead of an ati_remote2 when I lsmod.  The myth wiki talks about patching the kernel  for the remote wonder plus.  Is this necessary?  I would suspect that some of the buttons work but nothing appear to work.

I tried testing it with "xev", mashing on all the buttons did not see any output.

I have also made some attempts setting up my remote with lirc using mythbuntu IR setup control center but it also did not work.  Following instructions on the myth wiki.  The wiki does not seem to talk about setting up or changing channels.  I have read other posts for setting channels using lirc... again most of them old posts.  The lirc talks about blacklisting the ATI kernel driver which is what I tried.  

I would think it would be best to first get the ATI kernel / mouse / keyboard working before I play with lirc or at least it responding to some of its input.

I have tried various linux machines, have even tried it on mythbuntu 10.10 kernel 2.6.35.  When running with kernel,  ati_remote was not blacklisted and LIRC was not installed. 

I have 64 bit dell machines optiplex and precision workstation but have also tried it on my laptop and old Pentium  III machines running 32 bit OS.  No success...

I  have also read reviews about ATI Remote Wonder 2 working fine with mythbuntu and linux.

Any help would be appreciated.   Even with other ATI remotes are they supposed to be plug and play? or do I have to black list other input devices.

---

### Post by bonbasket on 2011-11-13
I finally got the remote ATI remote wonder plus remote working.   :D  Plain and  simple you need to patch the driver module to get it to work, but read on if you are interested in some of my research and experience with these remotes.

After purchasing an original "ATI remote wonder" remote I found out it was plug and play with the standard keyboard/mouse driver "ati_remote" module which comes with Mythbuntu 11.11 kernel 3.0.0-12-generic.

Plug in the orig remote wonder usb transceiver (the one with a led on it) and the mouse works and most of the standard buttons on the remote work.  What doesn't work are some of the buttons which do not map nicely to X11 keyboard I expected this after reading posts.  The buttons can be mapped later using xev and key mapping.  You basically have to map your buttons to little used keyboard keys. 

The ATI remote wonder plus is essentially the same remote as the original remote it.  Physically it is smaller lighter uses less batteries and has twice the range as the original ati wonder remote.  It is unfortunately not plug and play with current linux kernels (someone should update the kernel drivers).  Well it is in a way, its USB receiver (the one without a LED) will be detected as an ATI remote.  It just will not receive signals from the "ATI remote wonder plus".  But it will receive signals from the original ATI remote wonder and appears to be fully functional.  

To get the "ATI remote wonder plus" to work you need to patch the ati_remote kernel driver module. 
Once you do this both the original and the plus remote will work with either USB receiver (orig or plus).

So to patch the kernel module I used these two web pages as reference, you absolutely need the mythtv page as it has the patch:

[http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html)

[http://www.mythtv.org/wiki/ATI_Remote_Wonder_Plus](http://www.mythtv.org/wiki/ATI_Remote_Wonder_Plus)

The mythtv page instructs you to rebuild your kernel with a new ati_remote_plus module.  I did not know how to rebuild the kernel (well my mythbuntu distro did not come with the kernel code) so I followed instructions for just rebuilding a kernel module.  

After rebuilding the module and testing it I found out that the new module I made was basically plug and play for both remotes so I just replaced the original ati_remote.ko file.  I will outline my build instructions for those interested:

1.  I downloaded the kernel image for my distro and installed it.  This installs the kernel headers and the zipped up kernel code.  The zipped up kernel contains the original ati_remote.c driver code while the headers are needed for compiling the module.  To get your kernel image:

sudo apt-get source linux-image-$(uname -r)

2.  Follow the mythtv remote patch instructions for patching the ati_remote module.  No need to change the name this patch appears compatible with both remotes.  I expect it will work for both 64 bit and 32 bit distros.  I tested the remote on both 32 and 64 bit and it worked but so far I have only patched my 32 bit distro.  Here are my somewhat modified instructions:

So from my unziped package linux.3.0.orig or something:
cp /usr/src/linux-3.0/drivers/input/misc/ati_remote.c to ~/ati_remote_plus/.

Copy the following patch (the one on the mythtv rw+ web page) to ~/ati_remote_plus/ati_remote.patch

Apply the patch in the following manner:
cd ~/ati_remote_plus
patch ati_remote.c ati_remote_plus.patch 

3.  Back to my changes create the following Makefile for building rebuilding the only patched kernel module (not the whole kernel):

Edit: 
~/ati_remote_plus/Makefile 
and insert:

##################################
obj-m += ati_remote.o
 
all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
 
clean:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
###################################

Finally compile it type:

make

The build is quick and creates the kernel module:

~/ati_remote_plus/ati_remote.ko

4.  So like I said after doing a bunch of lsmod and insmod I found this driver works for both orig and plus remotes so to install the module permanently over the original ati_remote.ko kernel module :

Backup old mod and install new mod:

cd /lib/modules/`uname -r`/kernel/drivers/input/misc
sudo cp ati_remote.ko ati_remote.ko.orig
sudo cp ~/ati_remote_plus/ati_remote.ko .

5.  Reboot and try out the either remote or usb receiver, original "ati remote wonder" or "ati_remote_wonder_plus.  The remote will be plug and play try lsmod | grep ati  you will see ati_remote mod install when you plug in either usb device.


That all that is need to get ati_remote  wonder plus to work under ubuntu linux no lirc code is needed it is a keyboard/mouse you can map keys using X11 and use lirc for another remote.  

I have not mapped all my keys to mythtv yet but the myth pages seem pretty strait forward, plus I am sure you will want to do your own mapping.  I plan on mapping apps / scripts and other code to remote keys.  

So I will talk about the ati remote wonder features...

The ATI remote wonder plus is not a IR remote it is RF which means it will go through walls etc... so it will work through cabinets or even better you pipe the video and sound from your front end in your living room to your bedroom add still use the remote or another remote from your bedroom.  The ATI remote plus manuals say it has 60 foot range the original has 30 ft range.

The next thing you need to know is you can optionally assign a channel to the remote the remotes support up to 16 channels or if you have 16 remotes you can control 16 computers.  The driver uses a channel mask so you can mask out what remotes you would want to control what PC.  This feature actually gives this remote some interesting flexibility.

First this is how you set the mask, read the ati_remote.c and ati_remote2.c files for how to configure each remote.  In summary, all remotes program the same way, you hold down a button, press the channel number 1-16, press the button gain the remote led will flash your channel number.  Use hand button for orig ati remote, pc button for ati remote II, and the "ATI" button on the ATI remote plus.

So to configure you computer you need to specify the modeprobe channel_mask option.  As I said it is a bit mask you set bits default is zero for all channels are enabled.  Setting the mask only turns off remotes your computer will receive.  Bit 1 (value 1) has no effect.  For example 32 (100000) will not allow remote channel 5.  ~32 0x1FFDF will only allow remote 5 which is what you probably want if you use multiple remotes in your house.  To set this channel_mask add the remote file:

sudo emacs /etc/modprobe.d/ati_remote.conf

Insert:

#blacklist ati_remote
options ati_remote channel_mask=32

That file will let you test out how the mask only blocks channel 5 remotes.


The channel mask actually allows some interesting configuration options for future development with this remote.  It should allow a particular computer, I.E. your backend which may be running all the time to turn on your front end computers.  

If the ati_driver is modified to mask out all options but the power button then the channel received from a remote control can be used to turn on a computer remotely using wake up on lan option configured in bios to wake up a remote front end on your home network.

I will elaborate a little, not all computers support wake on usb, for one it wastes power and two if it does the you need to figure out how the wake on usb works with your ATI remote.  I tried on my laptop with windows and it didn't wake so it may mean more driver changes for wake on usb.

Wake on lan is fairly easy to configure and is supported by linux and mythtv via ethernet mac address. wol <mac_address>.  So lets assume your mythtv backend is always on.  If you plug in a usb receiver in the backend and modify the kernel module ati_remote.c code to ignore the channel mask whenever the power button is pressed so that it will then use the channel id to wake up on lan the front end that remote controls.  The power button then can be used to turn on or off a particular front end.  60 feet is pretty far to reach any computer in your house if your backend is centralized.

Furthermore adding this functionality to a front end or any linux computer with a usb receiver in your house will allow you to extend the range of the wake on lan feature...  Basically you are using the rf remote to tell the one or multiple computers in your house to wake up the computer / front end mapped to your remote.

I have to get other things working first before I try it out but it sounds feasible.  Ideally a network based remote like a tablet / ipod with IR (I read about an android tablet which has this functionality) will give you the ultimate flexibility.  Until then you can use a cheap ATI RF remote to control any computer in your house.

ATI remotes are X10 based so they may be able to control X10 devices like lights etc...  next on my play list.  I driver code indicates the X10 lola remote is supposed to work with the ati driver.  

I read that the ATI remote wonder II is a Philps remote with ATI name.  I do have one but  no receiver yet... so I tried it with my current usb receivers for orig ati remote and ati rw+ and it did not work.  I expected this as there is an ati_remote2 driver module for linux.  It is clear to me the orig and plus remotes are  more available and cheaper than the ati2 remote, they may also be more flexible since they are interchangeable.  From what I read about the ATI2 remote is it supports a similar 60 ft range.  The one interesting thing it does have is 5 mode buttons (4 aux and 1 pc button).  Essentially giving this remote 4 times as many button inputs as the original remotes.  I guess you could use these buttons to control additional apps although you may need lirc because X11 currently only supports 256 key codes.  I sill like the feel of this control's mouse, but its buttons are smaller and harder to reach than the orig and + remotes.  I have a few ati2 remotes and receivers on the way to try this out.

---

### Post by krodik on 2012-07-31
Hi, I have the same remote control and I'm trying to follow the directions, but the patch seems to fail  every time I try to patch it.

I'm getting the following error:

patching file ati_remote_plus.c
Hunk #1 succeeded at 174 (offset 13 lines).
Hunk #2 succeeded at 270 (offset 14 lines).
Hunk #3 succeeded at 273 (offset 14 lines).
Hunk #4 FAILED at 421.
Hunk #5 succeeded at 440 (offset 14 lines).
Hunk #6 succeeded at 442 (offset 14 lines).
Hunk #7 succeeded at 482 (offset -13 lines).
Hunk #8 succeeded at 514 (offset -13 lines).
Hunk #9 succeeded at 805 (offset 37 lines).
1 out of 9 hunks FAILED -- saving rejects to file ati_remote_plus.c.rej

The file ati_remote_plus.c.rej that it generates:

*** /dev/null
--- /dev/null
***************
*** 421
-                if ((((ati_remote_tbl[i].data1 & 0x0f) == (d1 & 0x0f))) && 
--- 430,432 -----
+
+               /* gregf - commented out to allow for added keys.
+                if ((((ati_remote_tbl[i].data1 & 0x0f) == (d1 & 0x0f))) &&


But I'm not sure what's going on. 

Any help would be appreciated.

Thanks...

---

### Post by O2Blevel on 2012-08-01
If you're not using the same kernel as the OP, you probably need to find a patch that will work with your kernel.

---

### Post by bonbasket on 2012-08-01
I have not tried this with the latest kernels...  I used 3.0.0 ...
I would suggest patching the version I used and then doing diffs against  your lasted driver to see what may have changed. 

you can find the the driver I used here:

[http://lxr.free-electrons.com/source/drivers/input/misc/ati_remote.c?v=3.0](http://lxr.free-electrons.com/source/drivers/input/misc/ati_remote.c?v=3.0)

You may want to check the mythtv page to see if they have a newer patch?

I plan on on upgrading to new version of myth tv later If I get it to work I will re post what I did.

---

### Post by krodik on 2012-08-02
I tried doing that, but I guess the ati_remote.c has changed. The old patch doesn't work anymore and there isn't a newer patch. 

Please let me know if you upgrade and get it to work.

---

