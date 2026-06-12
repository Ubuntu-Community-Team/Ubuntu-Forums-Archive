---
title: "Microsoft MCE Keyboard"
date: 2008-01-08
forum: Mythbuntu
---

### Post by donjuan2001 on 2008-01-08
Hello, I considering on purchasing this type of keyboard. 

[http://www.tomshardware.com/2005/08/15/microsoft_mce_keyboard/](http://www.tomshardware.com/2005/08/15/microsoft_mce_keyboard/)

Can anyone point me to a how-to for setting up this keyboard in mythbuntu? 

Thanks

---

### Post by ruminant1 on 2008-12-20
This thread has what you're looking for, including a kludge I just figured out to make the build work in Intrepid.

[http://ubuntuforums.org/showthread.php?t=941129]("http://ubuntuforums.org/showthread.php?t=941129")

I usually delete lirc_mod_mceusb2 from /etc/lirc/hardware.conf and replace it with lirc_mod_mce.  The two packages historically conflicted, though I haven't confirmed that's the case under Intrepid.

Oh, one more thing: the instructions tell you to copy the kernel module into /lib/modules/$YOURKERNEL/misc, but that directory didn't exist so the copy turned my module into a file called 'misc'.  This caused some serious head scratching when I couldn't load a module I just created.  

I put it in, /lib/modules/`uname -r`/updates/dkms , but you can mkdir misc if you like instead.

---

### Post by jfenton78 on 2008-12-21
I was looking at getting this keyboard also. Ebay has some for $25...not a bad price. Can anyone comment on whether this works with the IR in the Antec Fusion. The IR is specifically a soundgraph IR/VFD.

---

### Post by Surfless on 2009-01-12
HI I'm a brand new Ubuntu convert and while I'm setup to a functional level, I've got this keyboard/mouse and can't get them to work. Has this progressed to being a solution - I'm that new that I don't know what pretty much any of that means?


Thanks in advance!

---

### Post by north_pole on 2009-04-30
YEEES! Finally I've made it all work. Here's an HOW-TO for Ubuntu Jaunty Jackalope 9.04:
 
1. Install some required modules with
 
```
$ sudo apt-get install lirc lirc-modules-source module-assistant 
```2. and then run the following command
 
```
$ sudo dpkg-reconfigure lirc-modules-source 
```3. Open the the hardware.conf file with this command
 
```
$ sudo gedit /etc/lirc/hardware.conf 
```4. Change two of the lines so they look like this:
 
```
REMOTE_MODULES="lirc_mod_mce"
 
LOAD_MODULES="true" 
```Save and exit.
 
5. Run the following commands
 
```
$ sudo m-a update,prepare
 
$ sudo m-a clean lirc
 
$ sudo m-a a-i -f lirc    (if this one fails, choose "skip and continue with the next operation")
 
$ sudo depmod -a
```6. Download and unpack the attached files "lircd.conf" and "lircrc". Put them in /etc/lirc.
 
7. Now download the lirc_mod_mce v.0.1.5 file from [http://sourceforge.net/project/showf...kage_id=203215]("http://sourceforge.net/project/showfiles.php?group_id=171688&package_id=203215"), but be sure to download version 0.1.5 and NOT the v0.2.0. The later one has the famous "keypress repeats forever"-bug and should be avoided. Unpack the archive on e.g. your desktop.
 
8. Replace the "lirc_dev.h" file with the one located in "/usr/src/%YOUR_LIRC_VERSION%/drivers/lirc_dev"
 
9. In the file named "lirc_mod_mce.c", you have to change one of the lines:
 
```
input_dev->cdev.dev = &dev->dev;
 
to
 
input_dev->dev.parent = &dev->dev; 
```Save and exit.
 
10. Now, execute
 
```
$ sudo make 
```11. Create a new directory in "/lib/modules/%YOUR_CURRENT_KERNEL%" and name it "misc".
 
12. Some extra files have been created in the "lirc_mod_mce" directory.
One of them is "lirc_mod_mce.ko". Copy it to the new directory you've just created.
 
13. Run
 
```
sudo depmod -a
 
modprobe lirc_mod_mce 
```14. At last we have to blacklist the "lirc_mceusb2" module. Otherwise it will
interfere with the "lirc_mod_mce" one and make all of our work useless. Execute:
 
```
$ sudo gedit /etc/modprobe.d/blacklist.conf 
```and add the line
 
```
blacklist lirc_mceusb2
```on an own row e.g. in the bottom of the file. Save and close.
 
15. Reboot
 
16. And VOILA! Your MCE Keyboard should now be working!

---

### Post by lonicera on 2009-05-02
Hi, 

I have same keyboard and I have same problem too. I followed the instruction but i couldn't install my keyboard and remote control, Although i had no problem during the process :(. My dmesg | grep lirc output is



[   12.663695] lirc_dev: IR Remote Control driver registered, major 61 
[   12.685771] lirc_mod_mce: Input driver for Microsoft MCE 2005 keyboard v0.1.5
[   12.685773] lirc_mod_mce: Florian Demski
[   12.686773] usbcore: registered new interface driver lirc_mod_mce

---

### Post by north_pole on 2009-05-03
And this is from my setup, which still works just fine.

```
[    9.615596] lirc_dev: IR Remote Control driver registered, major 61 
[    9.624880] lirc_mod_mce: Input driver for Microsoft MCE 2005 keyboard v0.1.5
[    9.624883] lirc_mod_mce: Florian Demski
[   10.013118] lirc_dev: lirc_register_plugin: sample_rate: 0
[   10.024073] lirc_mod_mce[2]: Philips eHome Infrared Transceiver on usb2:2
[   10.024121] usbcore: registered new interface driver lirc_mod_mce

```

---

### Post by lonicera on 2009-05-03
I want to ask something, I am receive following message, when i run "sudo m-a a-i -f lirc". Is it normal?. Then I have selected "skip and continue with the next operation" option as you write.  Also when I install lirc, which remote and IR transmiter should I  select.

The source tarball could not be found!
Package lirc-modules-source not installed?
Running "m-a -f get lirc-modules-source" may help.
"/usr/share/modass/packages/default.sh" build KVERS=2.6.28-11-generic KSRC=/usr/src/linux-headers-2.6.28-11-generic KDREV=2.6.28-11.42 kdist_image
find: &#8220;/usr/src/modules/lirc*&#8221;: No such file or directory

Thanks your interest

---

### Post by north_pole on 2009-05-06
> I am receive following message, when i run "sudo m-a a-i -f lirc". Is it normal?
lirc_modules_source should have been installed in the first step of the how-to. Let's neglect this error at the moment.

> Also when I install lirc, which remote and IR transmiter should I  select.
Don't know if it matters, but I think I chose the mce_usb2 driver along with the "Custom" transmitter selection.

---

### Post by dan100 on 2009-06-08
Thanks North Pole.

I followed your instructions and it worked ok.
If anything the mouse works better than it did in WIN XP.

---

### Post by fatmonk on 2009-06-10
To anyone who has got this keyboard working...

Can you tell me if all of the transport (play, pause, record etc)  and other 'Media Centre' keys (Guide, DVD menu etc) work with Myth?

I've seen a few other MCE keyboards and the reveoews all said that they will work with Linux, but that tha 'special MCE keys' don't work.

If they do on this keyboard, and its not too big a deal to set up, then this is a definite one to consider for me...

EDIT: And I've just searched Amazon.co.uk and [they have them]("http://www.amazon.co.uk/gp/product/B000B78GD0?ie=UTF8&tag=gonmad-21&linkCode=as2&camp=1634&creative=6738&creativeASIN=B000B78GD0") for under 40GBP, available right now (June 09). Am very tempted so really want to know if those buttons work now... (despite the poor reviews on Amazon)



Cheers,

FM

---

### Post by dibs28 on 2009-06-10
Hi thanks for this got my keyboard working great, but my Microsoft RC no longer works? Any ideas, kinda think something is wrong in the hardware conf file as there is already a line for remote in this file.

---

### Post by roundhay on 2009-06-23
I have also followed the instructions posted in this forum and have managed to get the MS MCE Keyboard to work but the MS RC stops working. Is there a way to get both to work?

I have posted the outputs of relevant commands in the following thread but have not had any replies so far....

[http://ubuntuforums.org/showthread.php?t=1173465](http://ubuntuforums.org/showthread.php?t=1173465)

---

### Post by haggertyg on 2009-11-01
HI All

Wa using thsi OK in Jaunty, but then I upgraded to Karmic ... :-(

I thought it may be an issue with the mod_mce module, so I also tried the latest version, but is doesn't seem to want to compile.

Anyone else had the same problems?

Cheers
Giles

---

### Post by severee on 2009-11-07
Same here. Followed all the steps up to 'sudo make' and in Karmic it does not build.
Please help.

---

### Post by leeko on 2009-11-08
Bump for more info! 

I've got exactly the same issue - ms mce remote keyboard/mouse, karmic 9.10, lirc_mod_mce won't build. Please help! My front room box is crippled until I get the thing working....

Thanks,

Lee

---

### Post by leeko on 2009-11-24
Is there really no-one who's figured this out? I thought this was a popular keyboard...

Help!

---

### Post by byronmyth on 2009-11-25
Oh dear, I had this working in 9.04, haven't tried in 9.10 I usually VNC into the box if I need to type something. Isn't it about time this worked by default?

---

### Post by leeko on 2009-11-27
I thought so... 

But, it's been about 2-3 weeks since I posted about this (in this thread, and another). So far, no-one has offered any advice on how to get around this issue. 

Unfortunately, my linuxing skills don't extend as far as troubleshooting kernel module install issues... So, until someone kind offers to help work though this, we're stuck with $40 turkeys for keyboards. 

I'm trying hard to stick with linux, having switched from windows about a year back. But, issues like this require such a huge time-sink to figure out that it's really difficult to justify at times. 

Maybe I'm just feeling a bit fed up, since my mythtv media centre has just lost its sound output after the last update (again)... I keep hoping that this will "settle down" and become magically stable sometime soon...

Lee

---

### Post by singedwings on 2009-11-29
This is what I get when I do 'make'

```
make -C /lib/modules/2.6.31-15-generic/build SUBDIRS=/home/tv/lirc_mod_mce modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
  CC [M]  /home/tv/lirc_mod_mce/lirc_mod_mce.o
/home/tv/lirc_mod_mce/lirc_mod_mce.c: In function ‘unregister_from_lirc’:
/home/tv/lirc_mod_mce/lirc_mod_mce.c:725: error: implicit declaration of function ‘lirc_unregister_plugin’
/home/tv/lirc_mod_mce/lirc_mod_mce.c:725: error: dereferencing pointer to incomplete type
/home/tv/lirc_mod_mce/lirc_mod_mce.c:728: error: dereferencing pointer to incomplete type
/home/tv/lirc_mod_mce/lirc_mod_mce.c:738: error: dereferencing pointer to incomplete type
/home/tv/lirc_mod_mce/lirc_mod_mce.c:751: error: dereferencing pointer to incomplete type
/home/tv/lirc_mod_mce/lirc_mod_mce.c:752: error: dereferencing pointer to incomplete type
/home/tv/lirc_mod_mce/lirc_mod_mce.c: In function ‘send_packet_to_lirc’:
/home/tv/lirc_mod_mce/lirc_mod_mce.c:800: error: implicit declaration of function ‘lirc_buffer_write_1’
/home/tv/lirc_mod_mce/lirc_mod_mce.c:800: error: dereferencing pointer to incomplete type
/home/tv/lirc_mod_mce/lirc_mod_mce.c:802: error: dereferencing pointer to incomplete type
/home/tv/lirc_mod_mce/lirc_mod_mce.c: In function ‘usb_remote_probe’:
/home/tv/lirc_mod_mce/lirc_mod_mce.c:1220: error: invalid application of ‘sizeof’ to incomplete type ‘struct lirc_plugin’ 
/home/tv/lirc_mod_mce/lirc_mod_mce.c:1232: error: invalid application of ‘sizeof’ to incomplete type ‘struct lirc_plugin’ 
/home/tv/lirc_mod_mce/lirc_mod_mce.c:1234: error: dereferencing pointer to incomplete type
/home/tv/lirc_mod_mce/lirc_mod_mce.c:1235: error: dereferencing pointer to incomplete type
/home/tv/lirc_mod_mce/lirc_mod_mce.c:1236: error: dereferencing pointer to incomplete type
/home/tv/lirc_mod_mce/lirc_mod_mce.c:1239: error: dereferencing pointer to incomplete type
/home/tv/lirc_mod_mce/lirc_mod_mce.c:1240: error: dereferencing pointer to incomplete type
/home/tv/lirc_mod_mce/lirc_mod_mce.c:1241: error: dereferencing pointer to incomplete type
/home/tv/lirc_mod_mce/lirc_mod_mce.c:1242: error: dereferencing pointer to incomplete type
/home/tv/lirc_mod_mce/lirc_mod_mce.c:1243: error: dereferencing pointer to incomplete type
/home/tv/lirc_mod_mce/lirc_mod_mce.c:1244: error: dereferencing pointer to incomplete type
/home/tv/lirc_mod_mce/lirc_mod_mce.c:1245: error: dereferencing pointer to incomplete type
/home/tv/lirc_mod_mce/lirc_mod_mce.c:1246: error: dereferencing pointer to incomplete type
/home/tv/lirc_mod_mce/lirc_mod_mce.c:1251: error: implicit declaration of function ‘lirc_register_plugin’
/home/tv/lirc_mod_mce/lirc_mod_mce.c:1276: error: dereferencing pointer to incomplete type
make[2]: *** [/home/tv/lirc_mod_mce/lirc_mod_mce.o] Error 1
make[1]: *** [_module_/home/tv/lirc_mod_mce] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
make: *** [default] Error 2

```

What does this mean???

---

### Post by seiye on 2009-12-25
same problem.  please help.  Thanks.

---

### Post by kefa on 2009-12-26
anybody got this keyboard working with ubuntu 9.10?

---

### Post by leeko on 2010-01-02
bump... anyone?

L

---

### Post by SoapSeller on 2010-01-02
I've got the keyboard to work in 9.10.

To get it work, follow the steps from the first page,
and instead of step 9, extract the attached file to the source directory.
Enjoy it (:

I'm still working on the remote part...

---

### Post by custardweasel on 2010-01-06
Hey Soap seller,

I followed your instructions and I got the keyboard to work with mythbuntu 9.1! Horay!  Unfortunately though I'm getting the "keys repeat forever" bug that is mentioned in the original instructions.

Also the remote is not working as you describe.

Have you seen the repeat bug or know do you know of a workaround?
Should I try the 0.2.1 version of lirc_mod_mce?

Let me know how you're going, I'd love for the keyboard and that remote part to both work, right now with mythbuntu 9.1 I can either have the remote working with lirc_modmce or I can have the keyboard kind of working with lirc_mod_mce.

Thanks for your help so far.
Dylan.

---

### Post by LAltinell on 2010-01-09
I'm trying to get this module to work, but it just won't.

You were saying that you got this to work by extract it to the source folder. Can you specify exactly which one that is?

I have managed to get this module working under previus versions of  Ubuntu.

However, my MythTV-box runs ArchLinux with Openbox. Everything else is working fine, but this would be the final step...

Just to be clear, I'm trying this on a eeepc running vanilla Ubuntu 9.10

To the future, can't we request to get this driver in the kernel?
It doesn't require lirc to work with the keyboard, right?

---

### Post by LAltinell on 2010-01-18
Bump! :)

I really need answer to this question!

I'm sorry if I offended anyone by bumping this thread!

---

### Post by skysurf76 on 2010-01-30
Instructions in this thread are confirmed to work by myself on a fresh install of Ubuntu 9.10.

I am using a Phillips eHome ir receiver which Ubuntu automatically recognizes and which is verified by the output of lsusb.

Do NOT install lirc after the fresh install.  If you install it and mess with it before following the instructions in this thread you can screw things up.  Just follow the instructions step by step on the first page of this thread, and when you reach step 9 STOP and go to page 3 and download the file that is posted on that page and read the instructions in that post.

That poster instructs us to NOT do step 9 in the first page instructions, and instead take the file he provided and replace the one that would have been used had we followed the instructions on the first page.  Step 9 on the first page has us modify a file in gedit.  We do not need to do that because the file that we got on page 3 of this post has already been modified.

Additionally in step 8 when we are told to replace lirc_dev.h in the source directory, he is telling us to use the lirc_dev.h file that is ON OUR COMPUTER and put it into the directory we are working in that contains all of the SOURCE files that we will be using to make the final "driver" module.

One more thing.  After you reboot make sure to go into a terminal window and type...

sudo lirc

This will start lirc.  It does not start by default.  If you try to run sudo lirc with an instance of it already running it will tell you that is already running.

Thats all the advice I have.  Took me about the last 3 hours to get it working so I figured I would take the time to post the things that were giving me trouble.  I'll try to keep an eye on this thread in case someone can't get it to work and maybe I can be of some help.

I have to go lookup how to make a daemon run automatically.  Sucks being a noob. lol

---

### Post by singedwings on 2010-01-31
I have followed the instructions in the previous post for 9.10. I am not running mythbuntu, but normal ubuntu with myth. When I did the first instruction 'sudo apt-get install lirc lirc-modules-source module-assistant' I was asked to choose my remote control, so I chose windows media center (all). Was this the right thing to do, should I have put none?

After finishing the instructions the keyboard does not work and 'dmesg | grep lirc' gives me```
[    7.567259] lirc_dev: IR Remote Control driver registered, major 61 
[    7.618648] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[    7.618653] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[    8.013117] lirc_dev: lirc_register_driver: sample_rate: 0
[    8.019245] lirc_mceusb[4]: SMK CORPORATION MCE TRANCEIVR Emulator Device 2006 on usb2:4
[    8.019320] usbcore: registered new interface driver lirc_mceusb
[   17.501499] lirc_mod_mce: Input driver for Microsoft MCE 2005 keyboard v0.1.5
[   17.501502] lirc_mod_mce: Florian Demski
[   17.503416] usbcore: registered new interface driver lirc_mod_mce
``` Any ideas?

---

### Post by north_pole on 2010-01-31
Anyone who have managed getting both keyboard and remote working at the same time? I'm using the 0.21 version of lirc_mod_mce.

---

### Post by singedwings on 2010-02-07
bump

---

### Post by wunschkandidat13 on 2010-02-09
Hi folks,

I played around a bit and googled about the MCE Remote and Karmic Problem.

I found this: [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/445175](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/445175)
There it says: 
 - merged 1st-gen mceusb device support into lirc_mceusb2,
      renamed lirc_mceusb2 to lirc_mceusb

Meaning that the old lirc_mceusb2 was moved/renamed to lirc_mceusb.
All you need to do is blacklist the lirc_mceusb module.

If you go to the /etc/modprobe.d/blacklist.conf
and add a 
blacklist lirc_mceusb

Then, at least for me, the MCE Remote is working as a normal keyboard. 
The Mouse is not yet working, but I will investigate further.

Regards,
wunschkandidat13

---

### Post by BradSinner on 2010-02-10
I cannot get the mce keyboard to work at all. If I use my logitech harmony remote and set it to work as media center keyboard, it works and registers keypresses i "irw".
But when set to work as a mce keyboard, it dont work and do not register keypresses at all in "irw".

In Windows it works fine out of the box.

---

### Post by wunschkandidat13 on 2010-02-11
Hi folks,

after a long day of testing and researching, I found the solution to the Problem that Remote and Keyboard are not working in parallel.

Add 

```
ioctl: lirc_ioctl,
```after 
```
write:  lirc_write,
```in Line 957 of the lirc_mod_mce.c (from the file of page 3 (SoapSeller's post)).

It should then look like this:

```
static struct file_operations lirc_fops =
{
  write:  lirc_write,
  ioctl: lirc_ioctl,
};

```The reason is, that there was a change in lirc_dev.h in LIRC 0.8.5.
(Ubuntu 9.04 uses 0.8.4, Ubuntu 9.10 uses 0.8.6)

Have fun,

wunschkandidat13

---

### Post by SoapSeller on 2010-02-26
Finally I've managed to find some time to work on this issue,
good thing that first I returned to this post.

wunschkandidat13 solution work great.
I now have the keyboard, mouse and remote working.

---

### Post by ryanolf on 2010-03-01
My IR receiver is not supported by the 0.1.5 version (a Topseed device, evidently), but it is supported in 0.2.1. I applied SoapSeller's changes to the 0.2.1 version, and have attached it here. The file should be dropped in for the lirc_mod_mce.c file in the standard instructions. This file includes the changes suggested so far. It compiles and my keyboard/remote/mouse work...

Except that the keyboard is unusable for me due to the "infinite keypress" bug that you can read about, where hitting a key once results in Ubuntu responding as if that key were being held down. Does anyone know how to modify the 0.1.5 version to work with the Topseed (just adding the device id and merging the changes that reference Topseed in 0.2.1 does not work), or work around this bug? I'm so close!

Perhaps with the attached file, more people will try 0.2.1 and find a solution.

---

### Post by Delfairen on 2010-03-08
Hi Wunsch

After doing this I assume we have to make it again and then copy the ko file back to the directory listed

> **wunschkandidat13 said:**
> Hi folks,

after a long day of testing and researching, I found the solution to the Problem that Remote and Keyboard are not working in parallel.

Add 

```
ioctl: lirc_ioctl,
```after 
```
write:  lirc_write,
```in Line 957 of the lirc_mod_mce.c (from the file of page 3 (SoapSeller's post)).

It should then look like this:

```
static struct file_operations lirc_fops =
{
  write:  lirc_write,
  ioctl: lirc_ioctl,
};

```The reason is, that there was a change in lirc_dev.h in LIRC 0.8.5.
(Ubuntu 9.04 uses 0.8.4, Ubuntu 9.10 uses 0.8.6)

Have fun,

wunschkandidat13

---

### Post by Quazza on 2010-03-13
Hi Guys,

I have tried to set this up on Mythbuntu 9.10 without success, when I try to run 

```
modprobe lirc_mod_mce
```

I get the below error 

```
FATAL: Module lirc_mod_mce not found.
```

I have done all the steps from first page but grabbed the file from soapsellers post and also added completed the changes from wunschkandidat13 post, so now I am currently stumped.  :(

any ideas ??

PS - I have just gone through this again and this is the output I get from doing 'sudo make'

```
jase@mythtv-frontend:/tmp/lirc_mod_mce$ sudo make
make -C /lib/modules/2.6.31-20-generic/build SUBDIRS=/tmp/lirc_mod_mce modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /tmp/lirc_mod_mce/lirc_mod_mce.o
/tmp/lirc_mod_mce/lirc_mod_mce.c: In function &#8216;lirc_write&#8217;:
/tmp/lirc_mod_mce/lirc_mod_mce.c:877: warning: the frame size of 1456 bytes is larger than 1024 bytes
/tmp/lirc_mod_mce/lirc_mod_mce.c: In function &#8216;do_rc5_keys&#8217;:
/tmp/lirc_mod_mce/lirc_mod_mce.c:391: warning: the frame size of 4020 bytes is larger than 1024 bytes
/tmp/lirc_mod_mce/lirc_mod_mce.c: In function &#8216;do_rc5_mouse&#8217;:
/tmp/lirc_mod_mce/lirc_mod_mce.c:479: warning: the frame size of 4016 bytes is larger than 1024 bytes
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/lirc_mod_mce/lirc_mod_mce.mod.o
  LD [M]  /tmp/lirc_mod_mce/lirc_mod_mce.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
```

PPS - I must have done something wrong prior to doing the make as now I am not getting an error when running 

```
sudo modprobe lirc_mod_mce
```

Is there suppose to be any output after running this command as there is nothing appearing on the screen? The reason I ask is that now the remote is working but the keyboard is only working from the duplicate remote keys not the keyboard(QWERTY) or mouse.

---

### Post by singedwings on 2010-03-18
Sorry I still seem to be doing something wrong and can only get the qwerty + mouse bit working and not the remote buttons. Could someone clarify something for me.

I am using ubuntu 9.10 and to get the normal media centre remote working all I have to do is```
sudo apt-get install lirc lirc-modules-source module-assistant
```which throws up the dialog to select your remote, select 'windows media centre remote/transceivers', then click ok - job done. 

So when doing this for the keyboard what should I select? None, custom or the 'windows media centre remote/transceivers'?

If what I have done so for is correct some of the following instructions seem to be doing the same things??```
sudo dpkg-reconfigure lirc-modules-source
``` and ```
sudo m-a a-i -f lirc
```which does not work for me I get ```
Updated infos about 1 packages
unpack 
The source tarball could not be found!
Package lirc-modules-source not installed?
Running "m-a -f get lirc-modules-source" may help.
"/usr/share/modass/packages/default.sh" build KVERS=2.6.31-20-generic KSRC=/usr/src/linux KDREV=2.6.31-20.58 kdist_image
find: ‘/usr/src/modules/lirc*’: No such file or directory
``` in the instructions it says '(if this one fails, choose "skip and continue with the next operation")', but is this error the one to skip??

All help gratefully accepted.

---

### Post by singedwings on 2010-03-24
bump

---

### Post by tzaddik on 2010-03-24
> **north_pole said:**
> 
8. Replace the "lirc_dev.h" file with the one located in "/usr/src/%YOUR_LIRC_VERSION%/drivers/lirc_dev"


This file doesn't exist on mine. Wondering what I've done wrong as no one else seems to of had this issue.

My remote worked just by installing lirc. Would like to have the keyboard working as well though.

Any help is much appreciated. :)

---

### Post by singedwings on 2010-04-05
bump

---

### Post by evey on 2010-05-27
Regarding the keyboard repeat issue, I came across this : 

[http://www.roadflares.org/blog/?p=1045](http://www.roadflares.org/blog/?p=1045)

scroll right down and Ryan Reading seems to have a potential solution.

I've just purchased a MCE keyboard and just realised that the qwerty keys aren't working but don't want to risk killing off the working remote - yet.

---

### Post by ro_nn_er on 2010-06-07
Sadfully I can not get this to work. After the alterations needed such as ioctl and using the lib_mod_mce.c file on page 3 of this thread it finally compiled, but after copying the .ko file and doing the depmod and modprobe stuff, I do not receive any errors or anything so I reboot, but after it's done rebooting, both the remote and keyboard do not work.
 
I have my logitech harmony one set up as microsoft mce keyboard and using this on windows 7 it works flawlessly (the IR receiver is an SMK one), but I want to move over to linux for running XBMC on it.
 
When I do dmesg | grep lirc I get the following output:
 
[ 11.093716] lirc_dev: IR Remote Control driver registered, major 61
[ 11.136862] lirc_mod_mce: Input driver for Microsoft MCE 2005 keyboard v0.1.5
[ 11.136866] lirc_mod_mce: Florian Demski
[ 11.138706] usbcore: registered new interface driver lirc_mod_mce
 
When using "irw" it does not respond to anything.
 
What's worse, if I use mode2 -d /dev/lircd it doesn't respond as well.
When I installed the XBMC Live cd to harddisk (which is an ubuntu karmic) it installed lirc with lirc_mceusb and it used /dev/lirc0 and both "irw" and "mode2" responded. "irw" only responded to the remote keys and not the keyboard signals and "mode2" responded to both.
 
I almost can't believe that lirc does not have initial support for the MCE keyboard and that it's this hard to get it to work.
 
Anyone have any ideas what could be wrong? I reaaaally want to move away from windows 7 to run my mediacenter on.

---

### Post by bdragos on 2010-06-25
I'm trying to install the driver in 10.04. I followed the steps from page 1 and I included the extra file from page 3 but I got errors. 

When I run:

sudo modprobe lirc_mod_mce

I get:

FATAL: Error inserting lirc_mod_mce (/lib/modules/2.6.32-22-generic-pae/misc/lirc_mod_mce.ko): Unknown symbol in module, or unknown parameter (see dmesg)

dmesg output:

[  675.759477] lirc_mod_mce: disagrees about version of symbol lirc_register_driver
[  675.759482] lirc_mod_mce: Unknown symbol lirc_register_driver

Any idea what may cause this? Has someone successfully used the keyboard with the 10.04 release?

Thank you,
Dragos

---

### Post by Aythadis on 2010-07-10
I hate to add my beef to this but I happen to be yet another Linux user who has this keyboard. I bought it while I used Windows primarily, but started to use it 50/50. All I guess we can do is search.

---

### Post by jon47 on 2010-07-23
> **Aythadis said:**
> I hate to add my beef to this but I happen to be yet another Linux user who has this keyboard. I bought it while I used Windows primarily, but started to use it 50/50. All I guess we can do is search.

And I'm another.  And I finally sat down and scratched my head and worked out how to make it work so you need search no longer ;).

I've written things up here:  [http://sites.hedgerows.org.uk/lirc-mod-mce/](http://sites.hedgerows.org.uk/lirc-mod-mce/)

but in brief I've built a package which makes it all work:
[LIST]
[*]download [http://sites.hedgerows.org.uk/lirc-mod-mce/lirc-mod-mce-dkms_0.8.6a_all.deb]("http://sites.hedgerows.org.uk/lirc-mod-mce/lirc-mod-mce-dkms_0.8.6a_all.deb?attredirects=0")
[*]do:
[*][FONT="Courier New"]sudo apt-get install lirc[/FONT]
[*][FONT="Courier New"]sudo apt-get --purge remove lirc-modules-source[/FONT]
[*][FONT="Courier New"]sudo dpkg -i lirc-mod-mce-dkms_0.8.6a_all.deb[/FONT]
[/LIST]
You'll also need to edit /etc/lirc/hardware.conf - in particular set the line [FONT="Courier New"]REMOTE_MODULES="lirc_dev lirc_mod_mce"[/FONT], and to use a remote control or the remote keys on the keyboard you'll need a /etc/lirc/lircd.conf.

There's also a source tarball on my site if you don't trust my packaging...

Hope this helps,
Jon

---

### Post by GuiGuy on 2010-07-23
> **jon47 said:**
> And I'm another.  And I finally sat down and scratched my head and worked out how to make it work so you need search no longer ;).

Hope this helps,
Jon

Hi Jon,
Thanks for that. I've read through what you've done but I am not quite sure whether to risk it. Seems everytime I try to get the keyboard working something else gets broken and in the end I have no remote at all.

Do you have a recommendation for a 'fallback' position?

---

### Post by jon47 on 2010-07-24
> **GuiGuy said:**
> Hi Jon,
... I am not quite sure whether to risk it...

Do you have a recommendation for a 'fallback' position?

The easy fallback is to a full backup taken just before you install the new package.  But if that's not feasible for any reason, and you've actually got the keyboard or remote working in some form then I'd suggest:

- if you have modified sources for lirc or lirc_mod_mce in /usr/src take a copy of them.
- if you've modified anything in /etc/lirc, take a copy (my package doesn't change anything here, but the instructions tell you to, so grab a copy so you can go back afterwards)
- make a note of what lirc packages are installed - something like 'aptitude search lirc' will list all lirc related packages and show if they're installed

then remove lirc-modules-source and install my package.  If it doesn't work, remove my package and reinstall lirc-modules-source.  Restore your mods, and recompile/install as you did before.

Of course, if you don't have a working remote or keyboard, then there's nothing to reinstall, so you've got little to lose.

Cheers
Jon

---

### Post by Novae on 2010-07-24
> **jon47 said:**
> And I'm another.  And I finally sat down and scratched my head and worked out how to make it work so you need search no longer ;).

I've written things up here:  [http://sites.hedgerows.org.uk/lirc-mod-mce/](http://sites.hedgerows.org.uk/lirc-mod-mce/)

Just wanted to say a big thanks for that :) i was able to use your package to get the bits and pieces i needed to get this module working on Arch Linux :)

---

### Post by bdragos on 2010-08-02
> **jon47 said:**
> And I'm another.  And I finally sat down and scratched my head and worked out how to make it work so you need search no longer ;).

I've written things up here:  [http://sites.hedgerows.org.uk/lirc-mod-mce/](http://sites.hedgerows.org.uk/lirc-mod-mce/)



Thank you jon47! After several months I finally get some input from my keyboard thanks to your how-to. 

Unfortunately I am now experiencing the infinite key press issue. Every time I press a key it is repeated for ever and it makes the keyboard unusable. 

Is there anything I can do to solve this one?

Thank you,
Dragos

---

### Post by jeffeulogy on 2010-08-02
i'll second that. with your package i was able to get the keyboard and mouse working which is way better than before but this keypress thing has me scratching my head.

---

### Post by tixe on 2010-08-30
I managed to almost eliminate the repeat problems using Ryan Reading's advice from [http://www.roadflares.org/blog/?p=1045](http://www.roadflares.org/blog/?p=1045) (scroll to bottom)

1. Download the source tarball from [http://sites.hedgerows.org.uk/lirc-mod-mce/](http://sites.hedgerows.org.uk/lirc-mod-mce/)

2. Unpack in /usr/src as described

3. Edit /usr/src/lirc-mod-mce-0.8.6a/drivers/lirc_mod_mce/lirc_mod_mce.c 
Change according to [http://www.roadflares.org/blog/?p=1045](http://www.roadflares.org/blog/?p=1045) 

Change around line 660
```
if (ir->buf_in[offset] == MCE_CONTROL_HEADER)
break;
``` to this:
 ```
if (ir->buf_in[offset] == MCE_CONTROL_HEADER)
{
/* If we hit this, it&#8217;s the end of the current transmission,
analyze everything up to this point */
do_analyze(ir, &ir->peaks[ir->sync_pos], ir->peak_index - ir->sync_pos + 1);
break;
}
```4. Follow the further instructions under "The not-so-easy option" on  [http://sites.hedgerows.org.uk/lirc-mod-mce/](http://sites.hedgerows.org.uk/lirc-mod-mce/)


[LIST]
[*]sudo dkms add -m lirc-mod-mce -v 0.8.6a
[*]sudo dkms build -m lirc-mod-mce -v 0.8.6a
[*]sudo dkms install -m lirc-mod-mce -v 0.8.6a
[/LIST]
5. Reboot

---

### Post by bdragos on 2010-09-09
Thank you tixe ! Right now I'm writing with my MCE keyboard. The repetition still happens from time to time but now it's manageable. 

One addition to your 'how to', I had to restart the computer in order for the changes to take effect. 

Thank again,
Dragos

---

### Post by jon47 on 2010-09-16
> **bdragos said:**
> Unfortunately I am now experiencing the infinite key press issue. Every time I press a key it is repeated for ever and it makes the keyboard unusable. 

Is there anything I can do to solve this one?


Ryan Reading sent me a patch which fixes this.  I need to find some time to test it (hopefully this evening), and then I'll build an updated package with the fix. The patch is more extensive than the notes elsewhere on this thread, so I suspect Ryan has done more work on fixing it properly.  I'll find out later... :-)

Cheers
Jon

---

### Post by ybickes on 2010-10-25
i tried on 10.10

whats wrong with that..
> 
home@homeserver:~/Desktop$ cd lirc_mod_mce/
home@homeserver:~/Desktop/lirc_mod_mce$ ls
COPYING  kcompat.h  lirc_dev.h  lirc.h  lirc_mod_mce.c  Makefile
home@homeserver:~/Desktop/lirc_mod_mce$ sudo make
make -C /lib/modules/2.6.35-22-generic-pae/build SUBDIRS=/home/home/Desktop/lirc_mod_mce modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic-pae'
  CC [M]  /home/home/Desktop/lirc_mod_mce/lirc_mod_mce.o
In file included from /home/home/Desktop/lirc_mod_mce/lirc_mod_mce.c:74:
/home/home/Desktop/lirc_mod_mce/lirc_dev.h:31: fatal error: drivers/lirc.h: No such file or directory
compilation terminated.
make[2]: *** [/home/home/Desktop/lirc_mod_mce/lirc_mod_mce.o] Error 1
make[1]: *** [_module_/home/home/Desktop/lirc_mod_mce] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic-pae'
make: *** [default] Error 2
home@homeserver:~/Desktop/lirc_mod_mce$ 



---

### Post by jon47 on 2010-11-07
> **ybickes said:**
> i tried on 10.10 whats wrong with that..

You've got two problems:

(a) first and foremost, lirc-mod-mce 0.3.0 works on Ubuntu 10.04 - it doesn't work on 10.10.  Yet.  (and prior versions don't work even on 10.04.)
(b) you've got a broken package - lirc.h is in lirc-mod-mce 0.3.0, so the fact that you're getting an it's-not-there error means that your tarball is broken.  But as per point (a) fixing this won't make it compile anyway.

You've got three options:
1. Go back to 10.04 - it's a LTS version of ubuntu, so will be actively supported for some time yet.

2. port lirc-mod-mce to ubuntu 10.10 yourself (which I accept isn't feasible for many users)

3. hang on until I or someone else gets around to doing it.  Unfortunately for 10.10 users my media system runs 10.04 and is chugging along quite nicely, and I don't have a pressing need to port mod-mce.  But I do now have a virtual machine running 10.10, so I've got the infrastructure I need to do it, just need the time...

Cheers
Jon

---

### Post by danmint101 on 2010-12-05
I have the mce keyboard working on Linux Mint 10 Julia which is based on Ubuntu 10.10.

It's working based on jon47's code and instructions from [http://sites.hedgerows.org.uk/lirc-mod-mce/](http://sites.hedgerows.org.uk/lirc-mod-mce/)

Follow the steps below.

# sudo apt-get install lirc
# sudo apt-get --purge remove lirc-modules-source

Download and extract the file lirc-mod-mce-0.3.0.tar.bz2 from [http://sourceforge.net/projects/mod-mce/files/](http://sourceforge.net/projects/mod-mce/files/)

Open the file lirc-mod-mce-0.3.0/drivers/lirc_dev/lirc_dev.c and replace the line '#include <linux/autoconf.h>' with '#include <generated/autoconf.h>'
Open the file lirc-mod-mce-0.3.0/drivers/lirc_mod_mce/lirc_mod_mce.c
Replace 'usb_buffer_alloc' to 'usb_alloc_coherent'
Replace 'usb_buffer_free' to 'usb_free_coherent' (this is in there twice)

Now this module should build on 10.10

Copy it to /usr/src

sudo dkms add -m lirc-mod-mce -v 0.3.0
sudo dkms build -m lirc-mod-mce -v 0.3.0
sudo dkms install -m lirc-mod-mce -v 0.3.0

Edit the file /etc/modprobe.d/blacklist.conf and add 'blacklist mceusb' at the end and save

Then sudo update-initramfs -u -k all

Then re-boot

After rebooting it should work. If not run sudo dpkg-reconfigure lirc to reconfigure lirc.

---

### Post by crooper on 2010-12-20
> **danmint101 said:**
> I have the mce keyboard working on Linux Mint 10 Julia which is based on Ubuntu 10.10.

It's working based on jon47's code and instructions from [http://sites.hedgerows.org.uk/lirc-mod-mce/](http://sites.hedgerows.org.uk/lirc-mod-mce/)

Follow the steps below.

# sudo apt-get install lirc
# sudo apt-get --purge remove lirc-modules-source

Download and extract the file lirc-mod-mce-0.3.0.tar.bz2 from [http://sourceforge.net/projects/mod-mce/files/](http://sourceforge.net/projects/mod-mce/files/)

Open the file lirc-mod-mce-0.3.0/drivers/lirc_dev/lirc_dev.c and replace the line '#include <linux/autoconf.h>' with '#include <generated/autoconf.h>'
Open the file lirc-mod-mce-0.3.0/drivers/lirc_mod_mce/lirc_mod_mce.c
Replace 'usb_buffer_alloc' to 'usb_alloc_coherent'
Replace 'usb_buffer_free' to 'usb_free_coherent' (this is in there twice)

Now this module should build on 10.10

Copy it to /usr/src

sudo dkms add -m lirc-mod-mce -v 0.3.0
sudo dkms build -m lirc-mod-mce -v 0.3.0
sudo dkms install -m lirc-mod-mce -v 0.3.0

Edit the file /etc/modprobe.d/blacklist.conf and add 'blacklist mceusb' at the end and save

Then sudo update-initramfs -u -k all

Then re-boot

After rebooting it should work. If not run sudo dpkg-reconfigure lirc to reconfigure lirc.

0.3.1 package contents is different than 0.3.0. so i use 0.3.1 but  
when i try "sudo dkms build -m lirc-mod-mce -v 0.3.1"

it says" binary package for lirc-mod-mce: 0.3.1 not found"

can you help ?

edit: i tried with 0.3.0 and nothing have changed.. binary package for lirc-mod-mce: 0.3.0 not found

---

### Post by jon47 on 2010-12-21
> **crooper said:**
> 0.3.1 package contents is different than 0.3.0. so i use 0.3.1 but  
when i try "sudo dkms build -m lirc-mod-mce -v 0.3.1"

it says" binary package for lirc-mod-mce: 0.3.1 not found"

can you help ?

edit: i tried with 0.3.0 and nothing have changed.. binary package for lirc-mod-mce: 0.3.0 not found

It's much easier to help you if you actually post the whole error message.  However it looks like you've got a compile error, but quite what's causing this is impossible to tell from the info you've provided.

The error message should also say something like
"Consult the make.log in the build directory
/var/lib/dkms/lirc-mod-mce/0.3.1/build/ for more information."

- if you look at that file, you might be able to see what's wrong, if you can't then post or PM me a copy and I'll have  a look.

Jon

---

### Post by jon47 on 2010-12-23
I've finally got a ppa up and running with working lirc-mod-mce stuff for both Ubuntu 10.04 and 10.10.

To install, first remove any previous versions of lirc-mod-mce - if you used my older pre-packaged .debs, then this should work for you:
$[FONT="Courier New"] sudo apt-get purge lirc-mod-mce-dkms[/FONT]

if you hand-built it, then you'll need
[FONT="Courier New"]$ dkms remove -m lirc-mod-mce -v <version> --all[/FONT]

then add the ppa, and install a couple of packages:
[FONT="Courier New"]$ sudo apt-add-repository ppa:jon-hedgerows/lirc-mod-mce
$ sudo apt-get update
$ sudo apt-get install lirc lirc-modules-source[/FONT]

if you've previously had lirc installed then
[FONT="Courier New"]$ sudo apt-get upgrade
$ dpkg-reconfigure lirc[/FONT]

when configuring lirc, choose Windows Media Center remotes.

and it should all work nicely... :-)

Cheers
jon

---

### Post by Jungleboss on 2011-01-21
Does anyone have a complete MCE keyboard lircd.conf ? I'm planning to use my Harmony One.

---

### Post by Canix on 2011-01-25
I'm running XBCM Live 10 and is trying to use my Harmony One configured as a "MCE Keyboard". I have followed **Jon47**'s example:
 
[FONT=Courier New]$ sudo apt-add-repository ppa:jon-hedgerows/lirc-mod-mce[/FONT]
[FONT=Courier New]$ sudo apt-get update[/FONT]
[FONT=Courier New]$ sudo apt-get install lirc lirc-modules-source[/FONT]
 
I have selected "Windows Media Center Transceivers/Remotes (All)".
 
Using my standard Microsoft MCE remote it works fine, but once I clicked one button on the Harmony One configured as a "MCE Keyboard", I'm experiencing the infinite key press issue.
 
Do I need to follow **tixie**'s post and edit the file lirc_mod_mce.c ?
 
**Jon47** do you have a complete guide for this?
 
thanks in advance!
 
Cheers

---

### Post by cclein on 2011-02-04
Jon, I gave this a try on 10.04 and it worked great but I had some suspend issues with XBMCLive so I thought I'd give the XBMCFreak distro a try. It's 10.10 based with kernel inux XBMCLive 2.6.37-12-generic #26-Ubuntu SMP. Here are the errors I get during boot...

[   11.616660] lirc_dev: IR Remote Control driver registered, major 61 
[   11.618026] ir_lirc_codec: Unknown symbol lirc_dev_fop_poll (err 0)
[   11.618615] ir_lirc_codec: Unknown symbol lirc_dev_fop_open (err 0)
[   11.619068] ir_lirc_codec: disagrees about version of symbol lirc_get_pdata
[   11.619081] ir_lirc_codec: Unknown symbol lirc_get_pdata (err -22)
[   11.619568] ir_lirc_codec: Unknown symbol lirc_dev_fop_close (err 0)
[   11.619965] ir_lirc_codec: Unknown symbol lirc_dev_fop_read (err 0)
[   11.620397] ir_lirc_codec: disagrees about version of symbol lirc_register_driver
[   11.620409] ir_lirc_codec: Unknown symbol lirc_register_driver (err -22)
[   11.621360] ir_lirc_codec: Unknown symbol lirc_dev_fop_ioctl (err 0)
[   11.920228] lirc_mod_mce: Windows Media Center Edition USB IR Keyboard and Transceiver driver for LIRC 0.4.0
[   11.920242] lirc_mod_mce: Jon Davies <jon@hedgerows.org.uk>, Ryan Reading, Florian Demski, Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   11.920526] usbcore: registered new interface driver lirc_mod_mce

After install neither keyboard or remote work properly. Any tips on getting it to work?

Cheers,

Chris


> **jon47 said:**
> I've finally got a ppa up and running with working lirc-mod-mce stuff for both Ubuntu 10.04 and 10.10.

To install, first remove any previous versions of lirc-mod-mce - if you used my older pre-packaged .debs, then this should work for you:
$[FONT="Courier New"] sudo apt-get purge lirc-mod-mce-dkms[/FONT]

if you hand-built it, then you'll need
[FONT="Courier New"]$ dkms remove -m lirc-mod-mce -v <version> --all[/FONT]

then add the ppa, and install a couple of packages:
[FONT="Courier New"]$ sudo apt-add-repository ppa:jon-hedgerows/lirc-mod-mce
$ sudo apt-get update
$ sudo apt-get install lirc lirc-modules-source[/FONT]

if you've previously had lirc installed then
[FONT="Courier New"]$ sudo apt-get upgrade
$ dpkg-reconfigure lirc[/FONT]

when configuring lirc, choose Windows Media Center remotes.

and it should all work nicely... :-)

Cheers
jon

---

### Post by SMC - FM on 2011-07-31
Hello,

I'm sorry to bring up this old post.
I bought a Microsoft MCE Keybord (version 1) on a jumble sale and I'm trying to get it to work. Without succes... I added John's PPA and installed lirc as posted. But after a few reboots the keyboard still did not work.

Now after some reseach I discovered on the Launchpad PPA page
([https://launchpad.net/~jon-hedgerows/+archive/lirc-mod-mce](https://launchpad.net/~jon-hedgerows/+archive/lirc-mod-mce)) that Natty (11.04) is shipped with a newer version of lirc (0.8.7-0ubuntu4.2) So maybe that's the problem?

remote buttons (volume control/mute) do work, keyboard and mouse pointer don't work... 

Greetz

---

