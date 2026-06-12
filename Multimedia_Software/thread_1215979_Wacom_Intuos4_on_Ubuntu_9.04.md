---
title: "Wacom Intuos4 on Ubuntu 9.04"
date: 2009-07-17
forum: Multimedia Software
---

### Post by Matsuri on 2009-07-17
I know this particular subject has threads everywhere, for everything and I'm having a hell of a time trying to piece together what I need to do in order to get this to work.

I just recently received my Wacom Medium Intuos4 Pen Tablet with mouse in the mail. I ran the install scripts here:

```
sudo apt-get install xserver-xorg-input-wacom wacom-tools
```

After that, I plugged in the tablet and restarted my computer. To my dismay the tablet did not respond. The only evidence that my tablet isn't dead is one of the blue LED lights is lit up. The tablet connects via USB to my laptop.

The only thing I've noticed after running the install is that my NUM pad on my keyboard now moves the mouse instead of actually functioning like... a NUMpad. :P

Where do I go from here? It is hard to find well written documentation on this. I know my way around ubuntu... but not that well.

Thanks,
Matsuri

---

### Post by Favux on 2009-07-18
Hi Matsuri,

First problem you've run into is that the 0.8.2-2 linuxwacom in Jaunty's wacom.ko (usb kernel driver) doesn't work for the Intuos4 because it is relatively new.  So you have to compile linuxwacom 0.8.3-2 or up.  You don't install it you just copy the newly compiled wacom.ko over the 0.8.2-2 wacom.ko.  To do this you can use Section 1 of gali98's in post #104 in the HOW TO here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)  Or animone's version of it in post #129 here:  [http://ubuntuforums.org/showthread.php?t=1120029&page=13](http://ubuntuforums.org/showthread.php?t=1120029&page=13)

Now your tablet should be recogized.  The next problem you run into is that the default Jaunty 10-wacom.fdi doesn't parse the HAL wacom device names correctly into linuxwacom names.  So you can't use wacomcpl to calibrate and configure your tablet.  To fix this install the  modified 10-wacom.fdi located in post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

You should now be able to use wacomcpl.  Instructions for that are in Section 3 of the HOW TO here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

And finally to get your pad working follow ceridwen's instructions (3) in post #95 here:  [http://ubuntuforums.org/showthread.php?t=1120029&page=10](http://ubuntuforums.org/showthread.php?t=1120029&page=10)

Notice animone and ceridwen are both posting in the Intuos4 thread.  There should be other tips there for you if you scan through it.

Hope this helps.  Good luck!

---

### Post by Matsuri on 2009-07-18
Ok, slowly catching onto this. Now do I run the same apt-get script as before, restart and plug in the tablet? I understand I just copy paste the new code for the wacom.ko file however, I can't find the file.

My thought process seem sound?

---

### Post by Favux on 2009-07-18
Hi Matsuri,

Check Synaptic Package Manager that you have both Jaunty 0.8.2-2 packages installed, xserver-xorg-input-wacom and wacom-tools.  You don't need to apt get.  Then compile the new wacom.ko.  Followthe instructions step by step, copy and paste in the terminal is better than typing.  You don't need to find the newly compiled wacom.ko.  Use the copy command (cp) in gali98's or animone's HOW TO and it will copy the wacom.ko into the right place.

---

### Post by Matsuri on 2009-07-18
OK, worked through everything and the tablet works. I can use the mouse and stylus. Move them about the screen, select menus and everything. WACOMCPL still yields no choices for me to calibrate.

---

### Post by Favux on 2009-07-18
Hi Matsuri,

If you didn't see any error messages you're probably good.  Wacomcpl won't work without the new .fdi.  To see if the new wacom.ko is in place in a terminal enter:
```
dmesg | grep [Ww]acom
```
and to see what HAL is calling things:
```
xinput --list
```

Sometimes you need to restart a couple of times.  Or repeat the copy (cp) command.  Also some setups require you add "wacom" to "/etc/modules" as in post #3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949) and then restart.

---

### Post by Matsuri on 2009-07-18
I apparently didn't copy the right stuff for the new file. I fixed it everything is working how it should. Does the WACOMCPL handle the pressure sensitivity?

Thanks for all the help! Really appreciated the fast responses and the knowledge.

---

### Post by Favux on 2009-07-18
Hi Matsuri,

You're welcome.  Good deal!  Wacomcpl does generate a pressure setting in it's .xinitrc.  To get pressure set up in Gimp or Inkscape you need to configure the extended input devices.  Once you're set up with everything see near the bottom here:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

---

### Post by Matsuri on 2009-07-18
Couple more questions. I found the extended devices area for the gimp, the pressure is set to three. Now is that the pressure sensitivity of something of a different nature?

In the tutorial to get the hot keys working, how do I assign those hot keys to change my tools in the GIMP / Inkscape to say pain brush, or air brush?

THanks,
Matsuri

---

### Post by Favux on 2009-07-18
Hi Matsuri,

Sounds like things are basically working.  Nice job.

On the pressure=3 in Gimp, that's a good question.  I haven't actually changed that.  I change pressure through wacomcpl or directly editing the .xinitrc.  By the way it is a hidden file in /home/username/.  The LWP's HOW TO has explanations on PressCurve in section 9 and 5.1:  [http://linuxwacom.sourceforge.net/index.php/howto/main](http://linuxwacom.sourceforge.net/index.php/howto/main)

Your second question (along with your first) sounds like  a good one for the Intuos4 thread or Loic2's Wacom thread (the one the .fdi is on).

---

### Post by Matsuri on 2009-07-18
In the GIMP you need to manually enable for screen all of the tablet tools. Stylus, Pad, Eraser, Mouse, everything and then the tablet will detect how hard your pressing down on the pad. Having this enabled for the general use of the pad isn't really needed.

I'll be sure to post on the threat regarding the hot keys.

I've notice that using the stylus that the eraser doesn't act as an eraser in the GIMP but as whatever the selected tool is.

---

### Post by Favux on 2009-07-18
Hi Matsuri,

Something may not be quite right with your Gimp set up.  Eraser also needs to be configured as an extended input device.  Which I think you are saying.  But mine acts as an eraser with pressure.

---

### Post by Matsuri on 2009-08-02
Ok, now I have a curious problem. I had the tablet working perfectly, in every way... well minus the hot keys.

Performed the latest system update and the tablet no longer works. I remember somewhere in the heaping pile of posts I read someone addressing this problem. Any help?

---

### Post by Favux on 2009-08-02
Hi Matsuri,

Sounds like the updates included a kernel (or kernel headers) update.  That probably knocked out your new wacom.ko.  So use the copy (cp) command from the HOW TO to put it back.  Or you could recompile it since gali98 updated it to 0.8.4 and copy it back.

---

### Post by craig100 on 2009-08-25
Hi

Just bought an Intuos4 M and am astounded at how complex it is to get it working. Is there really no download from Wacom that just makes it work?  I've followed the instructions in this thread and others and the Wacom project and still can't get it working at all.  From what I understand it should work in the next Distro release 9.10, is this right?  If this is the case I'm just going to have to put it in storage till then. Can't believe Wacom let this happen, MAC and Linux both have 5% OS market share afterall!

Incredulous

Craig

---

### Post by craig100 on 2009-08-25
Forgot to mention, I'm using Ubuntu 9.04 x64 with all latest Kernel updates.

Craig

---

### Post by mcduck on 2009-08-25
Are you absolutely sure all those steps were even necessary? I mean my Intuos 3, and pretty much all other Wacom models, work out-of-the-box in 9.04, All you need to do is configure them in the programs you are using..

---

### Post by Favux on 2009-08-25
Hi craig100 and mcduck,

Yep, necessary.  We wasted quite a bit of time before we realized the problem

Basically it is simple.  The wacom.ko that comes with the default 0.8.2-2 linuxwacom in Jaunty is just a month or so to old to support the Intuos4 that is relatively new.  Starting with linuxwacom 0.8.3-2, it's wacom.ko supports the Intuos4.  The wacom.ko is the USB kernel driver.  Without the newer one USB for the Intuos4 doesn't work.

And craig100 following the HOW TO to compile the new wacom.ko is easy.

So all you do is compile the newer wacom.ko and copy it over the default Jaunty wacom.ko.  And presto USB communication to the Intuos4.  Notice you don't install the new linuxwacom you compile, just the wacom.ko.

The rest of it is just normal setting up of a Wacom tablet.  It depends on how functional you want it.

One other thing to note is that the 0.8.2-2 linuxwacom that comes default in Jaunty is "special".  It has been patched to support Xserver 1.6 and HAL.  Native linuxwacom support for Xserver 1.6 didn't happen until 0.8.3-2.  And I think most, if not all, of the HAL stuff is in the latest, 0.8.4.

Hope that clears it up.

---

### Post by craig100 on 2009-08-26
So, to be absolutely clear on this:-

I would now:-
1) Run ./uninstall against the wacom-0.8.4 package to remove it.
2) Remove any lines I added to xorg.conf
3) Replace the old 10-wacom-fdi file I had replaced
4) Ensure I have the wacom-tools and xserver-xorg-input-wacom packages installed via synaptic (which I do)

Then:-
5) Follow the HOWTO 3.3
6) Copy the newly built wacom.ko over the old one (once I find where it is)

reboot and Robert will be my uncle?

Craig

---

### Post by Favux on 2009-08-26
Hi craig100,

> 1) Run ./uninstall against the wacom-0.8.4 package to remove it.
2) Remove any lines I added to xorg.conf
3) Replace the old 10-wacom-fdi file I had replaced
Did you install linuxwacom 0.8.4?  Did you use a HOW TO?  If so which one.

Did you replace the Jaunty default 10-wacom.fdi with a new one?  If so from where?

Actually 0.8.4 should have better Intuous4 support than the default Jaunty 0.8.2-2 linuxwacom with the 0.8-4 wacom.ko does.  If it is not working then either an incorrect compile or install.  Or perhaps you forgot to copy your newly compiled wacom.ko into place?

If you are using xorg.conf you are not "suppose" to be using the wacom.fdi.  One or the other.

---

### Post by craig100 on 2009-08-26
Hi,

This is getting more and more confusing.  Basically I thought I'd put my system back together like it was before I bought the Intuos. These were items 1-3 above.

Then add the existing Ubuntu wacom support
Then overwrite the Ubuntu wacom.ko with the one created from the wacom project.

The final result would be the same as if I'd just bought the tablet and added the upgraded wacom.ko driver.

Would this not be the right way to go?

Craig

---

### Post by Favux on 2009-08-26
Hi craig100,

Sorry it's getting confusing.  I just don't know how 0.8.4 does on Jaunty with the Intuos4.  No one besides you has posted on it, I think.  0.8-4 says it has Intuos4 support in the changelogs.

If you want to get back to the default Jaunty configuration I'd suggest following Appendix 4 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  I don't think you have to worry about the wacom.ko.  The near the top of the same HOW TO is "Jaunty Users".  In 1) there is a link to gali98's Jaunty HOW TO in post #104.  You would only want to follow Section 1 of his HOW TO.

The modified wacom.fdi is in post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)  Shatterblast shows how to set up the Bamboo pad in post #188 on the same thread.  But first with the modified .fdi wacomcpl should now work.  So look at "Section 3:  Calibrating Your Tablet" on the same post/HOW TO with Appendix 4 and "Jaunty Users".  Now wacomcpl (enter it in a terminal) settings will survive a reboot and you can modify the .xinitrc it installs like shatterblast does.

Probably better for the pad is the Intuos4 thread.  Lots of tips in it.  See ceridwen's post #95 here:  [http://ubuntuforums.org/showthread.php?t=1120029&page=10](http://ubuntuforums.org/showthread.php?t=1120029&page=10)

But you won't get perfect Intuos4 support with linuxwacom 0.8.2-2.  Like I said, the Intuos4 is too new for that.  So that's why 0.8.4 might be better, if you can get it to work.

---

### Post by craig100 on 2009-08-26
Hi Favux,

I recognise all the links you've gave so I'm fairly certain my situation may be that I've perhaps made a mistake somewhere. It's the 0.8.4 version that I used.  However, as I've now returned my system to the pre-wacom state by having now carried out my items 1-3 AND have removed wacom-tools and xserver-xorg-input-wacom and rebooted, I will now follow your suggestions and report back. That way, you should find out if 0.8.4 works and I might actually get it working:)

Craig

---

### Post by craig100 on 2009-08-26
Hi Favux,

Progress so far:-
I worked down your post to the point of replacing the existing fdi file with yours.  After this point, I don't this I understand your instructions.  Immediately after swapping out the fdi file and rebooting, I ran wacomcpl in terminal. It just pops up a GIU with nothing in it other than an empty listbox and an exit button. Am I supposed to make some changes to the fdi file? I'm not sure.

Please advise.

Craig

---

### Post by craig100 on 2009-08-26
I should also point out that wacomcpl does not create a .xinitrc file in my home directory.

Craig

---

### Post by Favux on 2009-08-26
Hi craig100,

OK, this is where you're getting into unkown territory.  Did the default wacom.fdi give you anything with "xsetwacom list" or "xinput --list"?  How about the modified .fdi?  With that it sounds like "xsetwacom list" is blank which is why wacomcpl doesn't work.

The question is does a standard install of linuxwacom 0.8-4 support the HAL/.fdi features of Jaunty, or maybe that's vice versa?

Hopefully you've just installed the .fdi incorrectly and need to go over that.

Or do you need to use xorg.conf with your current setup?

Or is it possible that compiling 0.8-4 with 'libhal1-dev' installed through Synaptic Package Manager will allow you to access the wacom.fdi.  If it does it is not clear to me that the modified wacom.fdi will parse the names correctly.  Maybe the default will, maybe neither.  But if you do that you probably can't use xorg.conf.  See "Jaunty Users" 2) on that.

---

### Post by Favux on 2009-08-26
Wait a minute!  Stop everything!

I just remembered at least 1 other person with an Intuos4 wasn't getting the wacom.ko to kick in.  Try:
```
dmesg | grep [Ww]acom
```
and see if there is anything related to Wacom in the output.

If not try adding 'wacom' without the quotes to the end of "/etc/modules" and rebooting and check things out again.

---

### Post by craig100 on 2009-08-26
Ok, one step at a time....

With the new fdi file in place and entering "xsetwacom list" in terminal I get nothing, just returned to the cursor.

Entering "xinput --list" in terminal I get the following:-

"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=2	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Microsoft Natural? Ergonomic Keyboard 4000"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
"Microsoft Natural? Ergonomic Keyboard 4000"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Microsoft Microsoft Wireless Optical Mouse? 1.00"	id=5	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"FREETALK Wireless Headset FREETALK Wireless Headset"	id=6	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32

Does this tell us anything useful to determine the next step?

Craig

---

### Post by craig100 on 2009-08-26
Just saw your last post, no output at all from "dmesg | grep [Ww]acom", just returns me to the cursor.

Craig

---

### Post by Favux on 2009-08-26
Alright then that may be it.  Your wacom.ko isn't kicking in.  Try the modules thing.

---

### Post by craig100 on 2009-08-26
BINGO!!!!!!!

Added "wacom" to "/etc/modules" and rebooted. Entering "dmesg | grep [Ww]acom" gives:-

[   13.358147] input: Wacom Intuos4 6x9 as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1.1/5-1.1.1/5-1.1.1:1.0/input/input8
[   13.396363] usbcore: registered new interface driver wacom
[   13.396366] wacom: v1.49-pc-1:USB Wacom Graphire and Wacom Intuos tablet driver

Also THE TABLET NOW WORKS!!!!!

Thank you so much for you help Favux.  My next task is to see if it will work in Photoshop when running in an XP VM via VirtualBox.  But I think I'll leave that for another day.

Many thanks again.

Regards,

Craig

---

### Post by Favux on 2009-08-26
Hi Craig,

Outstanding!  You are welcome.

---

### Post by craig100 on 2009-08-26
Here are the steps I needed to take to get a Wacom Intuos4 M to work just as a mouse on Ubuntu 9.04 64 bit. Credit must go to Favux and Ping (Wacom Linux Project) for help and encouragement, I'm fairly new to Linux:-

The following are steps taken from the following posts:-
[http://ubuntuforums.org/showthread.php?t=1215979&page=3](http://ubuntuforums.org/showthread.php?t=1215979&page=3) #22
[http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11) #104 Section 1
[http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18) #176

Process from start to finish:-

   1. Installed "wacom-tools" and "xserver-xorg-input-wacom" using synaptic.
   2. "cd ./Desktop"
   3. "wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.4.tar.bz2"
   4. "sudo apt-get update"
   5. "sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev"
   6. "sudo apt-get upgrade"
   7. Then got the kernal version with: "uname -r" (needed in steps 8 and 13)
   8. I had the generic kernel so then: "sudo apt-get install linux-headers-generic" (or it would have been: "sudo apt-get install linux-headers-rt for the rt kernel")
   9. "tar xjvf linuxwacom-0.8.4.tar.bz2"
  10. "cd linuxwacom-0.8.4"
  11. "./configure --enable-wacom"
  12. "make"
  13. Then copied the wacom.ko built in step12 over the existing one in lib/modules..., so: "sudo cp ./src/2.6.28/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko" where `uname -r` is the kernel version from step 7.
  14. Changed /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi for a new one attached to [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18) #176 which clearly explains the procedure (just swapping out the file contents in a text editor, after backing up!)
  15. In a text editor added the line "wacom" to the end of the /etc/modules file
  16. Rebooted and it worked.

This has got the tablet as far as working like a mouse in Ubuntu Gnome desktop and also working in Photoshop in XP on a VirtualBox VM. The Touch Ring zooms in Firefox.  My next task is to see if I can set up the finer points like the erasure, tilt and buttons on the side of the pen.

Hope this helps someone.

Regards,

Craig

---

### Post by pointym5 on 2009-09-13
I'm very curious to see whether anyone can get the Intuos 4 to work ***with the Wacom drivers*** in a VirtualBox XP guest (on Jaunty).  I can get VirtualBox to see the tablet as a plain mouse (if I don't explicitly enable the USB device via the VirtualBox UI), and that works fine as far as it goes.  I can also get the Windows Wacom driver (within VirtualBox) to see the device when I **do** have VirtualBox recognize the USB device explicitly, and the pen correctly drives the Windows "Wacom Properties" UI, with one exception: the Windows system mouse cursor does not respond to movement of the Wacom pen. In other words, the pen has effects on the Windows desktop or within Windows applications, but Windows does not track the pen like it's a mouse. My other mouse does continue to drive the Windows mouse cursor, though I notice that if I explicitly bind *that* USB device to the VirtualBox VM then it behaves in the same way.

Wacom technical support politely told me that I was not going to get any help from them.

I have not tried VMWare, mostly because VMWare infuriates me due to unfixed bugs around the X11 keyboard mappings (that it corrupts, sometimes irreparably, resulting in reboots that I really don't have the patience for).

---

### Post by king.crimson on 2009-11-05
I have the very same problem pointym5 is describing.

I have Ubuntu 9.10 64bit as a host with XP as a guest on VirtualBox, and I'm using Wacom Intuos 4.

I've followed the very detailed post of Favux here: [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18) #176. 
This indeed, caused the Intuos 4 to work properly on the Ubuntu host, but I still have the problem described very accurately by pointym5.

My wife is an illustrator recently moved to Linux and my success in fixing this issue is the only barrier for her to stay in Linux...

Googling around I've only found guides and posts of how to fix the Wacom for Linux (which already works for me), but nothing relating its recognition by XP using VirtualBox.
 
Does anyone solved this issue yet?

Any help would be appreciated.
Thanks.

---

### Post by pointym5 on 2010-02-07
Try attaching your tablet via the VirtualBox "USB" tool on the bottom toolbar, and then turn off mouse integration. There's a little icon that looks like a mouse with a right-pointing chevron on it, and if you click on that a little "Disable" button pops up. Click "disable", and then you'll have to explicitly click in the window (WITH THE TABLET!) to get it to grab the mouse. But once it does, the tablet (for me at least) seems to work completely. I was able to bring up Corel Sketch and (I'm pretty sure) everything worked OK.

---

### Post by jesaisrien on 2010-02-09
Thanks!! I have ubuntu 9.10 installed and an intuos 3, and boy was I pulling my hair out trying to get things working. Replacing the .fdi file was all that was needed.

---

