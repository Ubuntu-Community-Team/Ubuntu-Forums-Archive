---
title: "lirc and streamzap on upgrade from 10.04 to 10.10"
date: 2010-10-12
forum: Mythbuntu
---

### Post by davidstoll on 2010-10-12
My frontend uses a streamzap remote and has been working for a couple of years.  However, in this last update, oddly enough, the select button no longer functions.  I see the red light flash on the ir receiver when I hit the button, but nothing happens.  However, all the other buttons seem to work just fine.  I also had mythtv control center re-create the ~/.lirc/ files.  I even deleted them (actually moved them) and the new files were created fresh.  I've restarted lirc and have even rebooted.

I also tried to run Boxee and XBMC and I had the same problem.

When I run irw from the command line I get garbage, rather then the normal information about what buttons you press.

I used the remote on another computer and the select button works fine.

Can anyone help me with this strange issue?

---

### Post by xinix on 2010-10-13
Have you tried reconfiguring lirc? 

```
sudo dpkg-reconfigure lirc
```

---

### Post by davidstoll on 2010-10-13
> **xinix said:**
> Have you tried reconfiguring lirc? 

```
sudo dpkg-reconfigure lirc
```

Well, I did through a GUI in MythTV called the Myth Control Center.  I changed it to a different controller and then back to SnapStream.

I also followed what you suggested above (which is why I see the resemblance).  The options are exactly the same.

I ran the command you suggested above, but I doubt it will make a difference because it looked like the same thing i tried.  I can't check it until I have physical access to the box.  Unfortunately, I don't have high hopes.

I also noticed that more than the "select/ok" button is not functioning.

---

### Post by davidstoll on 2010-10-13
no luck  :(

Just checked, the reconfigure didn't help.

I'm not sure if this helps, but again, the "irw" command gives me garbage when I click buttons.  Normally, I would expect information to be displayed on the command prompt with what button and hex code it is associated with.

---

### Post by xinix on 2010-10-13
It sounds like the remote is just fine since it works on another computer.  Was this other system upgraded to 10.10 as well or a fresh install?

I'm not sure about this problem, but you might look at this since it does describe the issue with garbage in irw.

[http://www.lirc.org/html/devinput.html](http://www.lirc.org/html/devinput.html)

---

### Post by davidstoll on 2010-10-13
> **xinix said:**
> It sounds like the remote is just fine since it works on another computer.  Was this other system upgraded to 10.10 as well or a fresh install?

I'm not sure about this problem, but you might look at this since it does describe the issue with garbage in irw.

[http://www.lirc.org/html/devinput.html](http://www.lirc.org/html/devinput.html)

Yes, the other system was upgraded in the same fashion.
As far as the link, hal doesn't seem to be installed, in fact, I've never installed it on any system as far as I know.

The only difference between the two systems in their upgrade is that I had a problem upgrading the problem machine and this is what I did, you can even see my post...

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/639933](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/639933)

Essentially, I had to install x11-common_7.5+6ubuntu3_all.deb, which is a maverick version of x11-common....before I isntalled maverick.

---

### Post by davidstoll on 2010-10-14
When I do a...
ls -l /dev/input/by-id/
...I don't see the USB IR receiver/remote listed on the problem machine, but I do see it on my working machine.  It is a streamzap remote.

Per this page([http://www.ubuntusolutions.org/](http://www.ubuntusolutions.org/)), down by "USB Remote Control", it describes similar simptoms and a solution similar to what was described previously in this thread.  However, I don't see that it is listed using the command above.  It must be that the receiver is not being correctly detected?  But it is being detected because it does function in a very limited way.

How can I find out how (where) it is being detected?

---

### Post by superm1 on 2010-10-14
So I think the streamzap remote is actually changed a bit - and the lirc package hasn't been updated for it.  Couple of things to try, and depending on your results, you should file a bug to get things fixed properly for others via an SRU and new releases.

1) Try changing the module in /etc/lirc/hardware.conf from lirc_streamzap to streamzap.
2) Try running without the lirc package.  The module "streamzap" should be loaded, and some buttons might just work properly.  Generally numbers and enter.

---

### Post by davidstoll on 2010-10-14
> **superm1 said:**
> So I think the streamzap remote is actually changed a bit - and the lirc package hasn't been updated for it.  Couple of things to try, and depending on your results, you should file a bug to get things fixed properly for others via an SRU and new releases.

1) Try changing the module in /etc/lirc/hardware.conf from lirc_streamzap to streamzap.
2) Try running without the lirc package.  The module "streamzap" should be loaded, and some buttons might just work properly.  Generally numbers and enter.

Here is my hardware.conf
My module line is a little different...

```
$ cat /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Streamzap PC Remote"
REMOTE_MODULES="lirc_dev streamzap"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="streamzap/lircd.conf.streamzap"
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
```

---

### Post by superm1 on 2010-10-14
> **davidstoll said:**
> Here is my hardware.conf
My module line is a little different...

```
$ cat /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Streamzap PC Remote"
REMOTE_MODULES="lirc_dev streamzap"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="streamzap/lircd.conf.streamzap"
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
```

OK so it's loading streamzap for you.  That's correct.  So it's not working in that configuration.  Try disabling lirc (you can just stop it with the init script - /etc/init.d/lirc stop) and see if it works with the native configuration with the module in the OS with a few number keys.

---

### Post by xinix on 2010-10-14
> **superm1 said:**
> OK so it's loading streamzap for you.  That's correct.  So it's not working in that configuration.  Try disabling lirc (you can just stop it with the init script - /etc/init.d/lirc stop) and see if it works with the native configuration with the module in the OS with a few number keys.

For me it's the arrows, the volume and the power keys that work using a streamzap (from '05 if it makes a difference) without lirc.  These work even if I leave lirc running and configured to my regular use (non streamzap) remote that uses the same ir receiver.

---

### Post by davidstoll on 2010-10-14
> **superm1 said:**
> OK so it's loading streamzap for you.  That's correct.  So it's not working in that configuration.  Try disabling lirc (you can just stop it with the init script - /etc/init.d/lirc stop) and see if it works with the native configuration with the module in the OS with a few number keys.

Killing lirc doesn't seem to make a difference.  :(

After I stop lirc, the same couple of buttons work and the same buttons that don't work, continue to not work.  hmmm

Any other thoughts?

---

### Post by superm1 on 2010-10-14
Well if you have some working without lirc, you might be able to xmodmap the missing buttons.

---

### Post by davidstoll on 2010-10-15
> **superm1 said:**
> Well if you have some working without lirc, you might be able to xmodmap the missing buttons.

```
$ sudo apt-get install xmodmap
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package xmodmap is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  x11-xserver-utils

E: Package 'xmodmap' has no installation candidate

```

---

### Post by superm1 on 2010-10-15
> **davidstoll said:**
> ```
$ sudo apt-get install xmodmap
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package xmodmap is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  x11-xserver-utils

E: Package 'xmodmap' has no installation candidate

```

Yeah, that package x11-xserver-utils is where you would find it.

---

### Post by davidstoll on 2010-10-15
Unfortunately, this is probably a bit more than I can handle.  I would really rather know why it stopped working because it was working just fine before....

I'm almost to the point where maybe I should just buy a different remote, but that sucks and kind of defeats the purpose of linux...figure out what is wrong and fix it.

Should (and how) should I file a bug report?  Or is it even a bug?

---

### Post by xinix on 2010-10-15
you could get another remote like you mentioned, if you do keep in mind that the streamzap ir receiver works with other remotes.  I personally use the one that came with my tv since it has buttons that switch it to control other devices like a dvr or dvd player.
Another option would be to save the money and do a backup and reinstall the OS.  On second thought you could boot a 10.10 live cd and install lirc to see if it will work.  If it does then maybe reinstall the OS; after all you did have problems upgrading and the issues may lie deeper than the X11 package you had trouble with.  A third option would be to do a "apt-get purge lirc" and reinstall the drivers.

---

### Post by davidstoll on 2010-10-15
> **xinix said:**
> you could get another remote like you mentioned, if you do keep in mind that the streamzap ir receiver works with other remotes.  I personally use the one that came with my tv since it has buttons that switch it to control other devices like a dvr or dvd player.
Another option would be to save the money and do a backup and reinstall the OS.  On second thought you could boot a 10.10 live cd and install lirc to see if it will work.  If it does then maybe reinstall the OS; after all you did have problems upgrading and the issues may lie deeper than the X11 package you had trouble with.  A third option would be to do a "apt-get purge lirc" and reinstall the drivers.

Purging was a good idea because I only removed...but alas, it did not work.  :(

Also, when I did purge lirc, the same basic functionality remained...i.e. up, down, left right, but that is about it.  So, it's like lirc is not even being used (or is being trumped by something else).  I wonder if the remote is being detected as some other kind of device or something....?

Unfortunately, this computer does not have an optical drive, so booting to a cd/dvd is not a particularly easy task.  I guess I could do this and reinstall, but it's just a matter of having to re-setup everything...and it might not fix it if it is a bug.

By the way, I just changed the remote to a Microsoft MCE remote and my remote didn't work at all on this machine (and it's working fine on my other one)....hmmm.

---

### Post by davidstoll on 2010-10-16
I hooked up an external CD and booted up the live CD.  The remote worked.  I even ran irw and it gave me what I expected.

So, I reformatted and re-installed (using ext4 rather than ext3, not sure if that is important, but it was different from what I have done before).

Ok, so now up and down works, but left right doesn't.  Also, the OK button works and also the exit button.

The irw command gives me what I expect, but with garbage in between.

But the bottom line is that it still isn't working properly.

```
$ irw
00000000000028d0 00 UP Streamzap_PC_Remote
^[[A00000000000028d0 00 UP Streamzap_PC_Remote
^[[A00000000000028d0 01 UP Streamzap_PC_Remote
00000000000028d4 00 DOWN Streamzap_PC_Remote
^[[B00000000000028d4 01 DOWN Streamzap_PC_Remote
00000000000028d3 00 RIGHT Streamzap_PC_Remote
^[[C00000000000028d3 01 RIGHT Streamzap_PC_Remote
00000000000028d1 00 LEFT Streamzap_PC_Remote
^[[D00000000000028d1 01 LEFT Streamzap_PC_Remote
00000000000028d1 00 LEFT Streamzap_PC_Remote
^[[D00000000000028d1 01 LEFT Streamzap_PC_Remote
00000000000028d1 00 LEFT Streamzap_PC_Remote
^[[D00000000000028d1 01 LEFT Streamzap_PC_Remote
00000000000028d1 00 LEFT Streamzap_PC_Remote
^[[D00000000000028d1 01 LEFT Streamzap_PC_Remote
00000000000028d1 02 LEFT Streamzap_PC_Remote
00000000000028d1 03 LEFT Streamzap_PC_Remote
00000000000028d1 04 LEFT Streamzap_PC_Remote
^[[D00000000000028d1 05 LEFT Streamzap_PC_Remote
^[[D^[[D^[[D^[[D^[[D00000000000028d0 00 UP Streamzap_PC_Remote
^[[A00000000000028d3 00 RIGHT Streamzap_PC_Remote
^[[C00000000000028d3 01 RIGHT Streamzap_PC_Remote
00000000000028d3 02 RIGHT Streamzap_PC_Remote
00000000000028d3 03 RIGHT Streamzap_PC_Remote
^[[C^[[C00000000000028d1 00 LEFT Streamzap_PC_Remote
^[[D00000000000028d1 01 LEFT Streamzap_PC_Remote
00000000000028d1 02 LEFT Streamzap_PC_Remote
00000000000028d3 00 RIGHT Streamzap_PC_Remote
^[[C00000000000028d3 01 RIGHT Streamzap_PC_Remote
^[[C^[[C^[[C^[[C^[[C^[[C^[[C00000000000028d2 00 OK Streamzap_PC_Remote
00000000000028d2 01 OK Streamzap_PC_Remote
```

It shouldn't have that extra crap.  It's like it was working, but then an update broke something...I don't know...

---

### Post by davidstoll on 2010-10-16
So, maybe the garbage isn't really important in solving this problem.

I decided to try and change one of the ~/.lirc/* files so that up was down and down was up.  When I changed it, I noticed some behavior that made me think I should just comment out both the up and down buttons all together...and while I'm at it, I'll just comment out the left and right button functionallity too.

Well, now all the buttons work.  So, it was getting the up/down/left/right from somewhere else.  I checked the other ~/.lirc/* files, but don't see anything suspicious.

From where is it getting the up/down/left/right commands?  If I can answer that, I probably know where the original problem existed.

/home/david/.lirc/mythtv
is attached, but had to add .txt as extension so I could attach it

---

### Post by novellahub on 2010-10-16
I just updated my 10.04 Frontend to the latest kernel and updates it offered.  I am now getting the same condition with the multiple key presses.  Selecting a older kernel version during bootup, I don't see this issue. I have the same Streamzap remote.

---

### Post by davidstoll on 2010-10-16
> **novellahub said:**
> I just updated my 10.04 Frontend to the latest kernel and updates it offered.  I am now getting the same condition with the multiple key presses.  Selecting a older kernel version during bootup, I don't see this issue. I have the same Streamzap remote.

Well, it doesn't really "fix" the problem, but try commenting out some of the buttons that are giving you the issue in ~/.lirc/mythtv  or whatever file is appropriate for you in the ~/.lirc/  folder.

Then, just restart lirc or reboot.

Let me know how it goes.

---

### Post by steve.pinkham on 2010-10-16
I have the same multiple keypress problem.  If I turn off lircd, only the arrow keys work.  When I start lircd, everything else works, but there's 2 keypresses for each of the arrow keys.

I assume the options are to(in order of my preference):
1)configure the in-kernel driver to work correctly
2)turn off the in-kernel driver
3)turn off the arrow keys in lirc

I know how to do 3), how would I do 1 or 2?

---

### Post by BobW on 2010-10-17
Same problem here - so far your option 3 is the only one I've been able to get working.

---

### Post by davidstoll on 2010-10-17
I also use XBMC and the select/ok button isn't working in that program...wow, what the heck is going on?

Is that happening to anyone else?

---

### Post by BobW on 2010-10-17
Looking in the kernel source I find
drivers/media/IR/rc-streamzap.c
drivers/media/IR/keymaps/rc-streamzap.c
This looks liek a USB driver to talk to the Streamzap remote.

The keymap file has:
        { 0x28c0, KEY_NUMERIC_0 },
        { 0x28c1, KEY_NUMERIC_1 },
        { 0x28c2, KEY_NUMERIC_2 },
        { 0x28c3, KEY_NUMERIC_3 },
        { 0x28c4, KEY_NUMERIC_4 },
        { 0x28c5, KEY_NUMERIC_5 },
        { 0x28c6, KEY_NUMERIC_6 },
        { 0x28c7, KEY_NUMERIC_7 },
        { 0x28c8, KEY_NUMERIC_8 },
        { 0x28c9, KEY_NUMERIC_9 },
        { 0x28ca, KEY_POWER },
        { 0x28cb, KEY_MUTE },
        { 0x28cc, KEY_CHANNELUP },
        { 0x28cd, KEY_VOLUMEUP },
        { 0x28ce, KEY_CHANNELDOWN },
        { 0x28cf, KEY_VOLUMEDOWN },
        { 0x28d0, KEY_UP },
        { 0x28d1, KEY_LEFT },
        { 0x28d2, KEY_OK },
        { 0x28d3, KEY_RIGHT },
        { 0x28d4, KEY_DOWN },
        { 0x28d5, KEY_MENU },
        { 0x28d6, KEY_EXIT },
        { 0x28d7, KEY_PLAY },
        { 0x28d8, KEY_PAUSE },
        { 0x28d9, KEY_STOP },
        { 0x28da, KEY_BACK },
        { 0x28db, KEY_FORWARD },
        { 0x28dc, KEY_RECORD },
        { 0x28dd, KEY_REWIND },
        { 0x28de, KEY_FASTFORWARD },
        { 0x28e0, KEY_RED },
        { 0x28e1, KEY_GREEN },
        { 0x28e2, KEY_YELLOW },
        { 0x28e3, KEY_BLUE },

It might be possible to get map these keycodes to useful functions within an application to get all the buttons working using this driver.

---

### Post by alien878 on 2010-10-17
I had a similar problem with my remote.  Some keys (up/down/left/right) working, but others not, no matter now much I tried and I couldn't understand why.

It turns out that my remote is recognized as a keyboard.  If lirc is not running, there is still basic keyboard functionality independent of lirc, but not all of they keys work.  I needed to reconfigure lirc from scratch.

Basically, the main tools to use are:

irrecord to make sure the device is read, the correct modules are loaded and generate a keymap.

Then start lircd (make sure it is started, 10.10 has some issues...)

Then make sure that lircd is getting the button presses using irw.

Note that I didn't have the double key press once lircd started working.  It seems that lircd somehow disabled the keyboard functionality.

---

### Post by davidstoll on 2010-10-17
> **alien878 said:**
> I had a similar problem with my remote.  Some keys (up/down/left/right) working, but others not, no matter now much I tried and I couldn't understand why.

It turns out that my remote is recognized as a keyboard.  If lirc is not running, there is still basic keyboard functionality independent of lirc, but not all of they keys work.  I needed to reconfigure lirc from scratch.

Basically, the main tools to use are:

irrecord to make sure the device is read, the correct modules are loaded and generate a keymap.

Then start lircd (make sure it is started, 10.10 has some issues...)

Then make sure that lircd is getting the button presses using irw.

Note that I didn't have the double key press once lircd started working.  It seems that lircd somehow disabled the keyboard functionality.

This seems to be a bug.  How/where do we report it?

---

### Post by magatz on 2010-10-17
Me too ..... :(

My remote (streamzap) works, but sometime looks like my htpc  is receiving a double click, sometime one click.... and /var/log/messagges if full on these messages


Oct 17 19:42:13 htpc kernel: [ 1011.805425] streamzap 6-2:1.0: streamzap_callback: received urb, len 2
Oct 17 19:42:13 htpc kernel: [ 1011.805430] streamzap 6-2:1.0: sz idx 0: f
Oct 17 19:42:13 htpc kernel: [ 1011.805435] streamzap 6-2:1.0: sz idx 1: ff
Oct 17 19:42:30 htpc kernel: [ 1028.949812] streamzap 6-2:1.0: streamzap_callback: received urb, len 2
Oct 17 19:42:30 htpc kernel: [ 1028.949817] streamzap 6-2:1.0: sz idx 0: f
Oct 17 19:42:30 htpc kernel: [ 1028.949823] streamzap 6-2:1.0: sz idx 1: ff
Oct 17 19:42:39 htpc kernel: [ 1037.486006] streamzap 6-2:1.0: streamzap_callback: received urb, len 2
Oct 17 19:42:39 htpc kernel: [ 1037.486011] streamzap 6-2:1.0: sz idx 0: f
Oct 17 19:42:39 htpc kernel: [ 1037.486016] streamzap 6-2:1.0: sz idx 1: ff

i really think is something inside the kernel

My 2€ cents

---

### Post by davidstoll on 2010-10-17
> **magatz said:**
> Me too ..... :(

My remote (streamzap) works, but sometime looks like my htpc  is receiving a double click, sometime one click.... and /var/log/messagges if full on these messages


Oct 17 19:42:13 htpc kernel: [ 1011.805425] streamzap 6-2:1.0: streamzap_callback: received urb, len 2
Oct 17 19:42:13 htpc kernel: [ 1011.805430] streamzap 6-2:1.0: sz idx 0: f
Oct 17 19:42:13 htpc kernel: [ 1011.805435] streamzap 6-2:1.0: sz idx 1: ff
Oct 17 19:42:30 htpc kernel: [ 1028.949812] streamzap 6-2:1.0: streamzap_callback: received urb, len 2
Oct 17 19:42:30 htpc kernel: [ 1028.949817] streamzap 6-2:1.0: sz idx 0: f
Oct 17 19:42:30 htpc kernel: [ 1028.949823] streamzap 6-2:1.0: sz idx 1: ff
Oct 17 19:42:39 htpc kernel: [ 1037.486006] streamzap 6-2:1.0: streamzap_callback: received urb, len 2
Oct 17 19:42:39 htpc kernel: [ 1037.486011] streamzap 6-2:1.0: sz idx 0: f
Oct 17 19:42:39 htpc kernel: [ 1037.486016] streamzap 6-2:1.0: sz idx 1: ff

i really think is something inside the kernel

My 2€ cents

To get by, comment out the arrow buttons in the appropriate ~/.lirc/?  file.  Not perfect, but at least it will eliminate the double arrows.  Won't fix my select/ok button problem, but it's a start.

---

### Post by jabjoe on 2010-10-17
I think the root of this problem is that the streamzap remote is an input for xinput and lirc. If you do 'xinput list' you will see streamzap listed in 10.10 but not 10.04. So MythTV, XBMC, etc, is getting two event for each streamzap key pressed. One from xinput and one from lirc.

So I think we need to remove streamzap from xinput. I can see an argument that if remotes can be keyboards, they should be, then lirc isn't need at all, one system instead of two. But the problem I have with that is that I'm running XBMC on the second screen from the same graphics card, thus the same X session, so uses the same inputs; and I'll be damned if I have a set up were someone using XBMC with the remote does anything to the desktop screen. So unless there is a way of setting a xinput to be used only by a single window (XBMC), I'm going with removing streamzap form xinput and keeping with lirc. (If there is a way, I guess I use xmodmap to map OK/Select to return + plus any other keys not doing anything without lirc, remove/stop lirc and I'm done.)

Once I've got streamzap removed from xinput, if that is the source of the problem, I can move from the 10.04 partition to the 10.10 as this was the only issue. :-)

---

### Post by jabjoe on 2010-10-17
OK, tested theory, and it seams to be true. The double events for Streamzap do seam to be because it's registered under both xinput and lirc, because removing it (well preventing from ever getting added) from xinput, means events are only coming from lirc, and so XBMC is only getting single events. So pressing up means it goes up one, not two.

To do this, I added the line

ATTRS{name}=="Streamzap*", GOTO="persistent_input_end"

to the top of /lib/udev/rules.d/60-persistent-input.rules

This works, but what worries me is the line

# do not edit this file, it will be overwritten on update

so I need to find a better place to prevent it being registered to xinput. But progress! :-)

---

### Post by verevi on 2010-10-17
Glad you found this! I will be watching closely--I have the same issue. 

Is there any easy way to solve it if I do not have multiple sessions like you described? I just have a simple setup. I'd like to fix this without mucking up the system too much.

Thanks for the help.

---

### Post by davidstoll on 2010-10-18
Even if I kill lirc, my select button still doesn't operate.

Can someone assist me in filing a bug....or is this a bug?

---

### Post by jabjoe on 2010-10-18
Looks like there might be another solution.

[http://www.spinics.net/lists/xorg/msg48268.html](http://www.spinics.net/lists/xorg/msg48268.html)

use inputlirc with its -g (grab) option.

Not looked another further yet as at the moment things are working. Until 60-persistent-input.rules is updated. I was thinking maybe an extra rule file to remove anything 60-persistent-input.rules does for the StreamZap, extra rule files won't be touched. Maybe inputlirc would be better.

---

### Post by davidstoll on 2010-10-18
> **jabjoe said:**
> Looks like there might be another solution.

[http://www.spinics.net/lists/xorg/msg48268.html](http://www.spinics.net/lists/xorg/msg48268.html)

use inputlirc with its -g (grab) option.

Not looked another further yet as at the moment things are working. Until 60-persistent-input.rules is updated. I was thinking maybe an extra rule file to remove anything 60-persistent-input.rules does for the StreamZap, extra rule files won't be touched. Maybe inputlirc would be better.

I don't even have inputlirc installed.  Unless you are suggesting to install it as a way to help, but I'm not sure if that is the best way to go, but I guess it's an option.  Seems like the other ways reported here are easier.

We just need to get it fixed or have a more official way of fixing it that won't break with every update.

All my lirc customization files and even my mythtv menu items get crushed on each mythtv update...that's ridiculous.

---

### Post by jabjoe on 2010-10-19
> **davidstoll said:**
> Even if I kill lirc, my select button still doesn't operate.

If you kill lirc, you only have xinput, which doesn't seam to have select mapped to anything, least not anything I've noticed being noticed yet.

I didn't have any problems with lirc not working. The problem I have was that xinput was working with the StreamZap at the same time. So I hobbled xinput's udev script to script over StreamZap and not add it to X's input devices. Now I have the StreamZap just dealt with by lirc, but I know it's a hack and a future update may remove my changes to the udev script. So I need to find a better way I can forget about once it's done. :-)

---

### Post by novellahub on 2010-10-19
I just found this on the Mythtv users group.  Maybe this is a solution:

[http://www.gossamer-threads.com/lists/mythtv/users/456626](http://www.gossamer-threads.com/lists/mythtv/users/456626)

---

### Post by straxus on 2010-10-19
Here's a way I worked out to disable xinput's Streamzap input, leaving only lirc to handle the remote:

Run:
```
xinput list
```
Look for "Streamzap PC Remote Infrared Receiver" and note the id #.  Mine was 14.

Now run the following, but replace "14" with your id #:
```
 xinput list-props 14
```

Part of what you should see will read:
```
Device Enabled (121):   1
```
If you see a number other than 121, make a note of it and alter the next command accordingly

Again, replace "14" with your id #:
```
xinput set-prop 14 121 0
```

Now xinput will ignore your Streamzap, and lirc can operate on it's own.  But this command will have to be run every session.  I haven't tried yet, but I think we should be able to put it into /etc/X11/xinit/xinitrc and have a permanent solution.

---

### Post by superm1 on 2010-10-19
> **straxus said:**
> Here's a way I worked out to disable xinput's Streamzap input, leaving only lirc to handle the remote:

Run:
```
xinput list
```
Look for "Streamzap PC Remote Infrared Receiver" and note the id #.  Mine was 14.

Now run the following, but replace "14" with your id #:
```
 xinput list-props 14
```

Part of what you should see will read:
```
Device Enabled (121):   1
```
If you see a number other than 121, make a note of it and alter the next command accordingly

Again, replace "14" with your id #:
```
xinput set-prop 14 121 0
```

Now xinput will ignore your Streamzap, and lirc can operate on it's own.  But this command will have to be run every session.  I haven't tried yet, but I think we should be able to put it into /etc/X11/xinit/xinitrc and have a permanent solution.
Would you mind filing a bug about this exact behavior you're seeing?  From some discussion in #mythbuntu-dev, it sounds like we might have a solution for this that modifies the lirc init script.  If it works you can help to test the SRU so this can get kicked out for everyone.

```
ubuntu-bug lirc
``` will file it for you.

---

### Post by straxus on 2010-10-19
> **superm1 said:**
> Would you mind filing a bug about this exact behavior you're seeing?  From some discussion in #mythbuntu-dev, it sounds like we might have a solution for this that modifies the lirc init script.  If it works you can help to test the SRU so this can get kicked out for everyone.

```
ubuntu-bug lirc
``` will file it for you.

I've never filed a bug-report before, but I'll give it a shot this evening.

---

### Post by davidstoll on 2010-10-19
> **jabjoe said:**
> OK, tested theory, and it seams to be true. The double events for Streamzap do seam to be because it's registered under both xinput and lirc, because removing it (well preventing from ever getting added) from xinput, means events are only coming from lirc, and so XBMC is only getting single events. So pressing up means it goes up one, not two.

To do this, I added the line

ATTRS{name}=="Streamzap*", GOTO="persistent_input_end"

to the top of /lib/udev/rules.d/60-persistent-input.rules

This works, but what worries me is the line

# do not edit this file, it will be overwritten on update

so I need to find a better place to prevent it being registered to xinput. But progress! :-)


Unfortunately, if I add this, my remote completely stops working.  I get no functionality whatsoever.  :(

---

### Post by straxus on 2010-10-19
> **davidstoll said:**
> All my lirc customization files and even my mythtv menu items get crushed on each mythtv update...that's ridiculous.

I know this is a bit off-topic, but as far as mythtv menu items go, you should create a new menu rather than edit an existing one.  Then you won't have them blown away by an update.  If "defaultmenu" is your thing then:

```
 sudo cp /usr/share/mythtv/themes/defaultmenu/ /usr/share/mythtv/themes/custommenu -r
```

Then make your customizations.  You *must* change the theme name in themeinfo.xml.  Then goto setup-> appearance and switch to your custom menu.

I don't know why you are losing lirc settings with every update.  I've been using mythbuntu since 7.10 and can't recall that ever happening to me.  What file do you store your settings in?

---

### Post by alien878 on 2010-10-20
> **straxus said:**
> I know this is a bit off-topic, but as far as mythtv menu items go, you should create a new menu rather than edit an existing one.  Then you won't have them blown away by an update.  If "defaultmenu" is your thing then:

```
 sudo cp /usr/share/mythtv/themes/defaultmenu/ /usr/share/mythtv/themes/custommenu -r
```That will work, but you won't get theme updates for menus you haven't customized.

You can override a single menu by copying it to ~/.mythtv/ and editing.  Ex. cp /usr/share/mythtv/themes/defaultmenu/mainmenu.xml ~/.mythtv/

---

### Post by jabjoe on 2010-10-21
> Unfortunately, if I add this, my remote completely stops working. I get no functionality whatsoever. 

That's because previously it was only xinput that was picking up your remote's signals. Disabling your streamzap for xinput, means you have no signals processed at all now. The solution is to now get your streamzap working with lirc again. The problem I had was that both lirc and xinput where processing the signals from streamzap. Hope this helps. :-)

---

### Post by jabjoe on 2010-10-21
> 
Here's a way I worked out to disable xinput's Streamzap input, leaving only lirc to handle the remote:

Run:
Code:

xinput list

Look for "Streamzap PC Remote Infrared Receiver" and note the id #. Mine was 14.

Now run the following, but replace "14" with your id #:
Code:

 xinput list-props 14

Part of what you should see will read:
Code:

Device Enabled (121):   1

If you see a number other than 121, make a note of it and alter the next command accordingly

Again, replace "14" with your id #:
Code:

xinput set-prop 14 121 0

Now xinput will ignore your Streamzap, and lirc can operate on it's own. But this command will have to be run every session. I haven't tried yet, but I think we should be able to put it into /etc/X11/xinit/xinitrc and have a permanent solution.


Different way achieving the same thing, stopping xinput dealing with our streamzap too! (I think yours is probably cleaner). I think the bug fix is to change /etc/init.d/lirc so it removes devices it's going to use from xinput, doing something like what you suggest.

---

### Post by alien878 on 2010-10-21
Just to add to the confusion....

I just discovered there are *three* possible places where IR key presses may be interpreted.  Lircd, xinput *and* ir-core in the kernel.

If you are using lircd, see [http://www.gossamer-threads.com/lists/mythtv/users/456911](http://www.gossamer-threads.com/lists/mythtv/users/456911) on how to disable ir-core.

I really wish someone would document how to configure ir-core.

---

### Post by davidstoll on 2010-10-21
If this is affecting you, please go here and click the link at the top that asks if the bug is affecting you.

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/663651](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/663651)

---

### Post by kraftcheck on 2010-10-25
> **straxus said:**
> Here's a way I worked out to disable xinput's Streamzap input, leaving only lirc to handle the remote:

Run:
```
xinput list
```
Look for "Streamzap PC Remote Infrared Receiver" and note the id #.  Mine was 14.

Now run the following, but replace "14" with your id #:
```
 xinput list-props 14
```

Part of what you should see will read:
```
Device Enabled (121):   1
```
If you see a number other than 121, make a note of it and alter the next command accordingly

Again, replace "14" with your id #:
```
xinput set-prop 14 121 0
```

Now xinput will ignore your Streamzap, and lirc can operate on it's own.  But this command will have to be run every session.  I haven't tried yet, but I think we should be able to put it into /etc/X11/xinit/xinitrc and have a permanent solution.

I was also seeing duplicate key responses in Mythtv and this solution worked for me.  I generalized it a little bit so that it is (hopefully) safe in the presence of system changes (changing Xinput IDs and such).  I created the file /etc/X11/Xsession.d/91no-streamzap-keyboard :
```

# Remove Streamzap remote from X input sources because getting both
# keyboard events and lirc events results in many apps (e.g. mythtv)
# getting duplicate events

# Get device ID for Streamzap
ID=`xinput list | sed -e 's/^.*Streamzap.*id=\([0-9][0-9]*\).*$/\1/p' -e d`
# If there is a streamzap device
if [ -n "$ID" ]; then
  # Get property ID for 'Enabled' property
  PROP=`xinput list-props $ID | sed -e 's/^.*Device Enabled (\([0-9][0-9]*\)):.*$/\1/p' -e d`
  # Set enabled property to zero if we can find its ID
  test -n "$PROP" && xinput set-prop $ID $PROP 0
fi

```

---

### Post by lionsnob on 2010-10-31
Thanks kraftcheck.  Your script worked for me.

---

### Post by squarooticus on 2010-11-07
You guys are making way too much work for yourselves. There is a very simple solution to this problem: create a something.conf file in /etc/modprobe.d with just

blacklist streamzap
blacklist rc_streamzap

in it.  Then reboot and voila! Things should be back to the way they were in 10.04.

FWIW, I agree with the poster who said that xinput is not the right solution for remotes at the moment: MythTV, Boxee, and mplayer (for instance) all have different key bindings and provide no way to remap them.  Until this is solved, lircd—as terrible as it is—is the less bad of the two solutions.

---

### Post by verevi on 2010-11-08
Hey. squarooticus,

I tried the blacklist method, but it did nothing--I still have the double arrow presses. Any suggestions on why it may not have worked?

Thanks for the help

---

### Post by squarooticus on 2010-11-09
> **verevi said:**
> Hey. squarooticus,

I tried the blacklist method, but it did nothing--I still have the double arrow presses. Any suggestions on why it may not have worked?

Thanks for the help

As root, lsmod and see whether streamzap or rc_streamzap are still loaded into the kernel.

---

### Post by davidstoll on 2010-11-15
> **squarooticus said:**
> You guys are making way too much work for yourselves. There is a very simple solution to this problem: create a something.conf file in /etc/modprobe.d with just

blacklist streamzap
blacklist rc_streamzap

in it.  Then reboot and voila! Things should be back to the way they were in 10.04.

FWIW, I agree with the poster who said that xinput is not the right solution for remotes at the moment: MythTV, Boxee, and mplayer (for instance) all have different key bindings and provide no way to remap them.  Until this is solved, lircd—as terrible as it is—is the less bad of the two solutions.


On my system, doing this disabled my remote completely.

The best option for me was to comment out the 4 directional buttons in the appropriate file located in ~/.lirc/ 

In my opinion, that is just as easy to do and just as easy to undo if/when necessary.

---

### Post by benlyboy on 2010-11-17
Hi 

My hard drive crashed, and I lost my system so I will be starting over using mythbuntu 10.10. 
What I was wondering is, is there anything I could do during install to help with this problem as I do have a streamzap remote
                                                    

thanks

---

### Post by davidstoll on 2010-11-17
> **benlyboy said:**
> Hi 

My hard drive crashed, and I lost my system so I will be starting over using mythbuntu 10.10. 
What I was wondering is, is there anything I could do during install to help with this problem as I do have a streamzap remote
                                                    

thanks

No, it's a problem with 10.10 itself.  The solution is very very simple.  Follow the procedure directly above (post #54).  Just use your favorite text editor and comment out the buttons that are causing you duplicate key presses.  Very easy to do...and undo when (if?) the fix gets pushed through.

---

### Post by asvravi on 2010-11-22
I think this xinput thing is bad in more ways than one. I had the "power" button mapped to stop/start MythTV. With the new kernel changes, pressing it immediately shuts down the entire system - it acts as a true power button for the system! And it is hardcoded into the kernel without any way to change or disable it. I had to hack it with an initrc script to disable IR devices on xinput based on pattern matching of the manufacturer name (ugh)!

Sadly, even after disabling the xinput device and reloading the old lirc modules in place of the new kernel modules, I still could not get it to create the /dev/lirc0. Only option was to go back to an older kernel version.

---

### Post by BlinkAdvice on 2010-11-26
I had the same problem today so I checked XBMC Wiki and like a day ago someone put up a detailed article on how to set up Streamzap with Ubuntu. It worked for me (I used LIRC + Xinput disable using xord.conf.d).
[URL="http://wiki.xbmc.org/index.php?title=Streamzap_PC_Remote"]
http://wiki.xbmc.org/index.php?title=Streamzap_PC_Remote[/URL]


Maybe it can help you guys?

---

### Post by davidstoll on 2010-12-01
> **BlinkAdvice said:**
> I had the same problem today so I checked XBMC Wiki and like a day ago someone put up a detailed article on how to set up Streamzap with Ubuntu. It worked for me (I used LIRC + Xinput disable using xord.conf.d).
[URL="http://wiki.xbmc.org/index.php?title=Streamzap_PC_Remote"]
http://wiki.xbmc.org/index.php?title=Streamzap_PC_Remote[/URL]


Maybe it can help you guys?

Yes, that does fix MythTV, but ironically, the Streamzap will not work to control XBMC or Boxee...

Any ideas?

---

### Post by yawlhoo on 2010-12-02
I have had a different problem from multiple keypresses after upgrading 10.04->10.10.  The Streamzap remote worked, but very sluggishly, you'd have to push the buttons from close by the ir receiver, not all presses would register, etc.  I found that dmesg was being bombed with streamzap callback log messages, and even felt command-line sluggishness when ssh'd into the box.

It seems that with the latest kernel 2.6.35-22 the lirc_streamzap kernel module is no more and instead streamzap and rc_streamzap are being loaded.  These don't work very well!  By editing /etc/default/grub I've fallen back several kernel versions, to 2.6.32-22-generic, which does have the older streamzap kernel modules:

$ uname -a
Linux xxx.xxx 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
$ lsmod |grep streamzap
lirc_streamzap          8016  1 
lirc_dev                8884  3 lirc_streamzap

and now the streamzap remote works the way it used to prior to upgrading Mythbuntu and its kernel.

---

### Post by yawlhoo on 2010-12-05
I found an easier way that works for the latest kernel: install the kernel-source package, then the lirc-modules-source package. During the install of the latter package the lirc modules are automatically built using DKMS.  As a safeguard I also blacklisted the rc_streamzap and streamzap modules in  /etc/modules.d/blacklist.conf.

Voila:

$ uname -r
2.6.35-22-generic
$ lsmod |grep streamzap
lirc_streamzap          8569  1 
lirc_dev                9510  3 lirc_streamzap

---

### Post by chrisinspace on 2010-12-26
> **yawlhoo said:**
> I found an easier way that works for the latest kernel: install the kernel-source package, then the lirc-modules-source package. During the install of the latter package the lirc modules are automatically built using DKMS.

What is the kernel-source package?  When I run:

```
sudo apt-get install kernel-source 
```

I get:

```
Package kernel-source is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
```

---

### Post by chrisinspace on 2010-12-28
Does anyone know the answer to this or know of another work-around?  I have tried everything suggested in this thread, the [Launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/663651") and at the [XBMC site]("http://wiki.xbmc.org/index.php?title=Streamzap_PC_Remote#Option_1:_Disable_Streamzap_Xinput_Device_usign_Xorg_Configuration").  When I 'irw', it seems to receive commands from all of the buttons just fine, but in all remote-compatible apps, only some of the buttons work.  I bought this remote because of it's reputation for working well with lirc, but I have had no luck.

---

### Post by cedyathome on 2011-01-06
I started getting two keystrokes every time I hit any of the arrow keys. The other keys worked fine.

I used the solution mentioned here
[http://www.lirc.org/html/devinput.html](http://www.lirc.org/html/devinput.html)
and that fixed the issue.

If irw is seeing the keys, but only a few are working, make sure that your 
~/.mythtv/lircrc file is properly configured to send the right key strokes to mythtv.

---

### Post by davidstoll on 2011-01-06
> **chrisinspace said:**
> Does anyone know the answer to this or know of another work-around?  I have tried everything suggested in this thread, the [Launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/663651") and at the [XBMC site]("http://wiki.xbmc.org/index.php?title=Streamzap_PC_Remote#Option_1:_Disable_Streamzap_Xinput_Device_usign_Xorg_Configuration").  When I 'irw', it seems to receive commands from all of the buttons just fine, but in all remote-compatible apps, only some of the buttons work.  I bought this remote because of it's reputation for working well with lirc, but I have had no luck.

Well, the post just above this is a bit complicated.  Here is a much easier method...

As stated earlier in this thread, just comment out the four arrow buttons in the appropriate   ~/.lirc/   file.

so probably...
gedit ~/.lirc/mythtv

But replace "mythtv" with whatever program is giving you the problem.

Comment all 4 arrow sets.  Each grouping has like 8 lines that each need to be commented out (i.e. put a # in front of each line), but it is very obvious and very easy.  Just search for UP, DOWN, LEFT and RIGHT.  Each set starts with "being" and ends with "end".

then restart lirc or reboot the computer

sudo /etc/init.d/lirc restart

This will eliminate the double key presses for the 4 arrow buttons.

Repeat for other buttons that are giving you double hits.

---

### Post by jabjoe on 2011-01-09
I finally got annoyed enough by the steamzap dmesg messages swamping everything to have a look. (It unrelated to the double event issue.)

I think the problem is in the driver:

/drivers/media/IR/streamzap.c

in the function streamzap_callback

The lines:

dev_info(sz->dev, "%s: received urb, len %d\n", __func__, len);

and

dev_info(sz->dev, "sz idx %d: %x\n",
i, (unsigned char)sz->buf_in[i]);

which, as you can see are the messages swamping dmesg.

I think what is meant to happen is that these lines are only done if "debug" is true. Then you can control this logging with the "/sys/module/streamzap/parameters/debug" file. But the debug variable isn't acturally used and these lines are always executed if there is data.

Hope this helps someone!

---

### Post by chrisinspace on 2011-01-15
> **davidstoll said:**
> 
As stated earlier in this thread, just comment out the four arrow buttons in the appropriate   ~/.lirc/   file.

so probably...
gedit ~/.lirc/mythtv

But replace "mythtv" with whatever program is giving you the problem.


I don't have a ~/.lirc folder.

---

### Post by davidstoll on 2011-01-15
> **chrisinspace said:**
> I don't have a ~/.lirc folder.

1) Make sure lirc is installed.

2) The ~/.lirc folder is invisable, so it might be there, but a normal "ls" or normal view in your file manager may not show it.

If you still don't have a ~/.lirc folder after 1) and 2), then I have no idea.

---

### Post by Goldengel on 2011-01-16
Hello everybody,

I want to hook up to the other people in this thread. I don't understand much about this but I think, my problem is a bit different to the other here.

I have upgraded to 10.10 too and want the old behavior back. Unlike the others here, my streamzap remote is only configured to use irexec. And doing special commands. The UP and DOWN buttons usually were not used to anything similar to pressing the up or down key on the keyboard. Now each time I press it, besides the correct action, other events are trigered. For me, personally that change is a big fail.

I dont't want anything other than this cascade:
    Remote --> lircd --> irexec --> command
I don't want any x-Events to be triggered or anything of this new stuff. When I press any button on my remote, screen turns back on from standby - that's annoying!

To solve this, I'd like to know, what part of Ubuntu 10.10 was changed and is responsible form this new "function" or is there even a way to completely go back to the old behavior? Where are those changes documented?

All my efforts led to either no lirc at all or lirc with additional events.

Can anyone give me a hint? Thanks in advance

Julian

---

### Post by Goldengel on 2011-01-16
Hello everybody,

I want to hook up to the other people in this thread. I don't understand much about this but I think, my problem is a bit different to the other here.

I have upgraded to 10.10 too and want the old behavior back. Unlike the others here, my streamzap remote is only configured to use irexec. And doing special commands. The UP and DOWN buttons usually were not used to anything similar to pressing the up or down key on the keyboard. Now each time I press it, besides the correct action, other events are trigered. For me, personally that change is a big fail.

I dont't want anything other than this cascade:
    Remote --> lircd --> irexec --> command
I don't want any x-Events to be triggered or anything of this new stuff. When I press any button on my remote, screen turns back on from standby - that's annoying!

To solve this, I'd like to know, what part of Ubuntu 10.10 was changed and is responsible form this new "function" or is there even a way to completely go back to the old behavior? Where are those changes documented?

All my efforts led to either no lirc at all or lirc with additional events.

Can anyone give me a hint? Thanks in advance

Julian

---

### Post by Goldengel on 2011-01-16
Hello everybody,

I want to hook up to the other people in this thread. I don't understand much about this but I think, my problem is a bit different to the other here.

I have upgraded to 10.10 too and want the old behavior back. Unlike the others here, my streamzap remote is only configured to use irexec. And doing special commands. The UP and DOWN buttons usually were not used to anything similar to pressing the up or down key on the keyboard. Now each time I press it, besides the correct action, other events are trigered. For me, personally that change is a big fail.

I dont't want anything other than this cascade:
    Remote --> lircd --> irexec --> command
I don't want any x-Events to be triggered or anything of this new stuff. When I press any button on my remote, screen turns back on from standby - that's annoying!

To solve this, I'd like to know, what part of Ubuntu 10.10 was changed and is responsible form this new "function" or is there even a way to completely go back to the old behavior? Where are those changes documented?

All my efforts led to either no lirc at all or lirc with additional events.

Can anyone give me a hint? Thanks in advance

Julian

---

### Post by Goldengel on 2011-01-16
DEL PLS - Sorry - what happend here?

---

### Post by Goldengel on 2011-01-16
DEL PLS - Sorry - what happend here?

---

### Post by squarooticus on 2011-02-06
> **davidstoll said:**
> On my system, doing this disabled my remote completely.

FYI, I figured out why this was probably affecting you and not me: I had previously installed lirc-modules-source. The lirc modules appear to have vanished from the regular kernel image package.

---

