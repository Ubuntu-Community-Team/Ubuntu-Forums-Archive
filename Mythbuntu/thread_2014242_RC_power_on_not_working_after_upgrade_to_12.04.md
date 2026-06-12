---
title: "RC power on not working after upgrade to 12.04"
date: 2012-07-01
forum: Mythbuntu
---

### Post by mymythtv on 2012-07-01
hi

I upgraded from working 0.24/10.4 LTS to 0.25/12.04 LTS, and after the that there were problems with IMON remote not working as earlier  :-(

1) Had to reconfigure lirc to use devinput because of ir now in kernel
2) Not all keys working - fixed by extending imon_pad key table with missing keys

Everythings seems ok so far, but one issue remains. In 10.04 it was possible to power on by remote/RC, but that isn't working in 12.04.
Current kernel is 3.2.0-26, and downgrading to 2.6.32-41 made that work again.

I'm not sure how kernel should interfere as system is "powered off" and therefore should be hardware triggered by imon ( connected to USB ) ?!?

I could be that new somehow disables feature on next boot, but right now I'm clueless and therefore hoping somebody else have had similar issues.

Looking high and low reweals other problems, but none directly related to RC power on

IMON hw is ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller

---

### Post by Lester_Burnham on 2012-07-02
Hi,

Did you have anything in /etc/rc.local to enable the remote wake the PC before?
I take it, that it was waing from suspend?

Lester

---

### Post by mymythtv on 2012-07-02
Hi

No - nothing speciel configured in 10.04. It just worked out of the box...
It's not from suspend - it's a complete powerdown. I'm also able to power on by hitting "space bar" on keyboard, and thats still work..

I'll also noticed that /sys/bus/usb/devices/*/power/wakeup is missing when booting 3.2 kernel, but is there under 2.6.32.
Also tried to "echo enabled > wakeup", but that's not possible ( as suggested in another thread )

I think that it could be imon kernel driver still not working ( have seen a lot of notes on that ). Using imon_pad btw - not MCE

Will try to get a "sevice window" again tonight - if wife permits :-)

BTW: found this earlier regarding kernel change
[http://wilsonet.com/?page_id=95]("http://wilsonet.com/?page_id=95")

the quote seems to be right :-)

> Fedora users have actually been coping with some work-in-progress changes in this arena for some time (an input layer imon driver has been around in Fedora for some time now, the lirc_zilog driver has been included for ages, i2c changes that hit the kernel back in 2.6.33 have long since been encountered), but Ubuntu users jumping from the 2.6.32.x based kernel in the prior release to a 2.6.35.x plus newer upstream based kernel are likely going to encounter a slightly more bumpy ride.


/Bjarne

---

### Post by Lester_Burnham on 2012-07-02
Hi,

I just thought I'd fire up the system I have here with an imon media lab (Thermaltake Bach) on it, hit the power button on the remote and it woke up from full off!

This was with mythbuntu 12.04. I think the remote is setup as an imon vf/ir

Lester

Ps. Good luch there, but won't boot properly cause I can hear heads crashing! :)

---

### Post by mymythtv on 2012-07-02
Hi

Great to hear that it IS possible in 12.04 ;-)

...but then questions rise...
My hw is identified as ID 15c2:ffdc SoundGraph Inc. iMON PAD, and it might be that they behave different.

You say you define it as "imon vf/ir", but I didn't have that opportunity - unless we are talking LIRC. Here I defined it as "imon PAD" which I thought was the obvious answer ?!

Might try to fiddle with lirc settings, but I have the feeling that the problem lies deeper :-(

I'm afraid it's another night without sleep ;-)

/Bjarne

---

### Post by Lester_Burnham on 2012-07-02
> **mymythtv said:**
> Hi

Great to hear that it IS possible in 12.04 ;-)

...but then questions rise...
My hw is identified as ID 15c2:ffdc SoundGraph Inc. iMON PAD, and it might be that they behave different.

You say you define it as "imon vf/ir", but I didn't have that opportunity - unless we are talking LIRC. Here I defined it as "imon PAD" which I thought was the obvious answer ?!

Might try to fiddle with lirc settings, but I have the feeling that the problem lies deeper :-(

I'm afraid it's another night without sleep ;-)

/Bjarne

Hi,

My settings/info:
lsusb
> Bus 002 Device 003: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Mythbuntu Control Centre
> Soundgraph iMon MultiMedian IR/VFD
Mythbuntu Version
> lester@BACH:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename:	precise


Power off sorted out the clicking HDD :) (very old 80gb)

Lester

---

### Post by mymythtv on 2012-07-02
Hi

Sound very much like my setup...

I'll go for a spin tonight ( after dark :-)  )

Might be the lirc installation messing up, so I'm going to remove it completly...
I'll let you know the outcome ..

/Bjarne

PS. Good to hear the old drive is still spinning after a few kicks ;-)

---

### Post by Lester_Burnham on 2012-07-02
Hi again,

The more I think about it! It seems weird that it has anything to do with lirc when the system is shutdown completely.

The only difference seems to be related to using devinput vs lirc. So it must be!

Good luck,
Lester

---

### Post by guyrichie@hotmail.com on 2012-07-02
Hello mymythtv,

I know this sounds funny, but whilst upgrading to 12.04 LTS, did you change any BIOS settings - i.e. load setup defaults?

My BIOS will wake / start on only certain USB inputs (1-4), but must be enabled in BIOS.  Have a look in your motherboard BIOS manual to see if this is applicable and check if the RC USB receiver is in the same USB port from your working 10.4 LTS install?

Many thanks,
Guy.

---

### Post by mymythtv on 2012-07-02
Hi

No - didn't change anything regarding HW - IR reciever is physical located in same location....
Did look into bios to se if anythin has changed, but no :-(

I have a keyboard attached, and were able to switch on by "spacebar". Also changed that to verify HW setup - no problems :-(

Actually waited 2 month after release just to make sure that "basic bugs" were sorted out... :-)

Booted into 2.6.32 kernel yesterday, did a "shutdown -h" and after that I was able to turn on by remote..
Switched back to 3.2.25, shutdown again and where then unable to to switch on..

Will give it a go tonight ( if time permits ), removing lirc completely and only going for kernel IR - might be lirc doing something....

/Bjarne

---

### Post by mymythtv on 2012-07-02
Hi

Got my "window" to play a little :-)

Removed lirc completely, but still nogo. Actually it was defined as
> Soundgraph iMON PAD IR/VFD - not the MultiMedian version, but I doubt there is any difference avoiding power on by rc..

Regarding imon, the output from dmesg says:

> bjarne@mythbuntu:~$ dmesg |grep imon
[   28.252621] imon 3-7:1.0: 0xffdc iMON VFD, iMON IR (id 0x24)
[   28.252625] imon 3-7:1.0: imon_set_display_type: overriding display type to 1 via modparam
[   28.292078] Registered IR keymap rc-imon-pad
[   28.308195] imon 3-7:1.0: iMON device (15c2:ffdc, intf0) on usb<3:3> initialized
[   28.308226] usbcore: registered new interface driver imon
bjarne@mythbuntu:~$

There is actually two ir receivers, but one is on hauppauge card.

> root@mythbuntu:/home/bjarne# ir-keytable 
Found /sys/class/rc/rc0/ (/dev/input/event6) with:
	Driver imon, table rc-imon-pad
	Supported protocols: other 
	Enabled protocols: other 
	Repeat delay = 500 ms, repeat period = 125 ms
Found /sys/class/rc/rc1/ (/dev/input/event7) with:
	Driver cx88xx, table rc-hauppauge
	Supported protocols: NEC RC-5 RC-6 JVC SONY LIRC other 
	Enabled protocols: NEC RC-5 RC-6 JVC SONY LIRC other 
	Repeat delay = 500 ms, repeat period = 125 ms

The USB devices are:

> bjarne@mythbuntu:~$ lsusb -t
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/8p, 12M
    |__ Port 4: Dev 2, If 0, Class=HID, Driver=usbhid, 1.5M
    |__ Port 4: Dev 2, If 1, Class=HID, Driver=usbhid, 1.5M
    |__ Port 7: Dev 3, If 0, Class=>ifc, Driver=imon, 1.5M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/4p, 480M
    |__ Port 1: Dev 2, If 0, Class=vend., Driver=dvb_usb_dib0700, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
    |__ Port 1: Dev 2, If 0, Class=stor., Driver=usb-storage, 480M
bjarne@mythbuntu:~$

So here the imon driver gets loaded correct.

It seems that keys are recognized by driver, but myth dosn't get all events/keys.
KEY_RIGHT, KEY_LEFT, KEY_ENTER are keys working, but KEY_STOP isn't 

> root@mythbuntu:/home/bjarne# ir-keytable -t
Testing events. Please, press CTRL-C to abort.
1341260830.536678: event MSC: scancode = 100007f
1341260830.536682: event key down: KEY_RIGHT (0x006a)
1341260830.536683: event sync
1341260830.786798: event key up: KEY_RIGHT (0x006a)
1341260830.786799: event sync
1341260834.936606: event MSC: scancode = 2b9715b7
1341260834.936610: event key down: KEY_STOP (0x0080)
1341260834.936611: event sync
1341260986.988528: event MSC: scancode = 28a195b7
1341260986.988532: event key down: KEY_ENTER (0x001c)
1341260986.988533: event sync

Also it seems the mouse/keyboard is actually switching between mouse and keyboard, so remote is behaving as expected :-)

Right now I'm thinking of getting my hands on a MCE remote to test if it's the Soundgraph PAD remote not working as expected together with 12.04 - seems to be an option ( imon_mce ?! )...

> bjarne@mythbuntu:/lib/udev/rc_keymaps$ ls -la imon*
-rw-r--r-- 1 root root 1756 Feb 10 20:58 imon_mce
-rw-r--r-- 1 root root 1706 Jun 29 21:38 imon_pad
bjarne@mythbuntu:/lib/udev/rc_keymaps$ 

...but that's going to be tomorrow - window is closed for today; schedules are running again ;-)

/Bjarne

---

### Post by Lester_Burnham on 2012-07-03
Hi,

The buttons not working in mythtv, will more than likely just be button names being different in your lircrc or wherever they are configured for mythtv.

Depends if you're using lirc as a bridge or direct devinput.

Lester

---

### Post by mymythtv on 2012-07-03
Hi Lester

Lirc is configured as devinput - mythtv/lirc configuration changed to fit accordingly. Using lirc, all keys are working 100% as under 10.04 - except "power on" ( famous WAF factor :-)  )...
Pressing "spacebar" on keyboard starts, so bios is still working as expected from HW perspetive

Removing lirc totally leaving kernel imon alone, keys are recognized by kernel ( ir-keytable ), but NOT mythtv. Still - no "power on" ( "ir-keytable -t" shows KEY_POWERON when pressed ... . The same goes for evtest - keys are recognized by kernel driver.. ( Using /lib/udev/rc_keymaps/imon_pad )
 - but that's another problem getting mythtv to work without lirc :-)

I have the feeling that the USB wakeup somehow gets disabled under 3.2 kernel on hardware regarding the iMON driver( maybe since IR driver got into kernel in 2.6 - never used those kernels for my htpc ?!? ) ??

This should be 100% HW based at the time I press "power on"...


/Bjarne
Will try to get another window tonight :-)

---

### Post by Lester_Burnham on 2012-07-03
> **mymythtv said:**
> Hi Lester

Lirc is configured as devinput - mythtv/lirc configuration changed to fit accordingly. Using lirc, all keys are working 100% as under 10.04 - except "power on" ( famous WAF factor :-)  )...
Pressing "spacebar" on keyboard starts, so bios is still working as expected from HW perspetive

Removing lirc totally leaving kernel imon alone, keys are recognized by kernel ( ir-keytable ), but NOT mythtv. Still - no "power on" ( "ir-keytable -t" shows KEY_POWERON when pressed ... . The same goes for evtest - keys are recognized by kernel driver.. ( Using /lib/udev/rc_keymaps/imon_pad )
 - but that's another problem getting mythtv to work without lirc :-)

I have the feeling that the USB wakeup somehow gets disabled under 3.2 kernel on hardware regarding the iMON driver( maybe since IR driver got into kernel in 2.6 - never used those kernels for my htpc ?!? ) ??

This should be 100% HW based at the time I press "power on"...


/Bjarne
Will try to get another window tonight :-)
Hi,

Yeah, WAF is higher importance for sure (key to buying new hardware to play with :))

If you're not using lirc as a bridge with devinput, from my understanding you need a lircrc with the program commands in it, either in home directory or /etc/lirc.

I totally agree that it should be HW based, as the machine is completely off.  I'm stumped!

Let me know if there's some commands I can run for you to see what is enabled or not on mine.

Lester

---

### Post by mymythtv on 2012-07-03
Hi Lester

Yes - WAF factor is iportant - my old graphics wasn't "low noise", so I was _ordered_ to upgrade...
...which I understood as "everything" should be upgraded ;-) ;-)

Ah - well. Might have to clarify my setup regarding lirc - when are we talking bridge/devinput and/or "native lirc" :-)

I'm at work right now, so I can't provide my configs, but in 10.04 - without kernel support for IR - it was "classic" lirc with *lircrc *configuration and *hardware.conf* ( placed in /etc/lirc ). Worked well - also the "power on"

New setup is 
REMOTEDRIVER=devinput
REMOTE_LIRCD_CONF=lircd.conf.devinput ( off my head... )

So yes - it's bridging. Sorry for the confusion :-)

Some interesting thing could be which scancode is sent by KEY_POWERON - As I rember, that key wasn't defined in imon_pad "out of the box". Had to add that together with some other keys. 

Could you please try to run the following commands and collect output ( might need to stop lirc first ). 
 
> ir-keytable
ir-keytable -r
ir-keytable -t
irw
evtest


to read the config and scancode for KEY_POWERON ?!

---

### Post by Lester_Burnham on 2012-07-03
Hi,

I don't have ir-keytable installed. Yet :)

So running sudo evtest
> lester@BACH:~$ sudo evtest
No device specified, trying to scan all of /dev/input/event*
Available devices:
/dev/input/event0:	Power Button
/dev/input/event1:	Power Button
/dev/input/event2:	AT Translated Set 2 keyboard
/dev/input/event3:	Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)
/dev/input/event4:	iMON Panel, Knob and Mouse(15c2:ffdc)
/dev/input/event5:	iMON Remote (15c2:ffdc)
Select the device event number [0-5]: 5
Input driver version is 1.0.1
Input device ID: bus 0x3 vendor 0x15c2 product 0xffdc version 0x0
Input device name: "iMON Remote (15c2:ffdc)"
Supported events:
  Event type 0 (EV_SYN)
  Event type 1 (EV_KEY)
    Event code 1 (KEY_ESC)
    Event code 14 (KEY_BACKSPACE)
    Event code 28 (KEY_ENTER)
    Event code 57 (KEY_SPACE)
    Event code 103 (KEY_UP)
    Event code 105 (KEY_LEFT)
    Event code 106 (KEY_RIGHT)
    Event code 108 (KEY_DOWN)
    Event code 113 (KEY_MUTE)
    Event code 114 (KEY_VOLUMEDOWN)
    Event code 115 (KEY_VOLUMEUP)
    Event code 116 (KEY_POWER)
    Event code 119 (KEY_PAUSE)
    Event code 127 (KEY_COMPOSE)
    Event code 128 (KEY_STOP)
    Event code 139 (KEY_MENU)
    Event code 154 (KEY_CYCLEWINDOWS)
    Event code 156 (KEY_BOOKMARKS)
    Event code 161 (KEY_EJECTCD)
    Event code 162 (KEY_EJECTCLOSECD)
    Event code 167 (KEY_RECORD)
    Event code 168 (KEY_REWIND)
    Event code 174 (KEY_EXIT)
    Event code 204 (KEY_DASHBOARD)
    Event code 207 (KEY_PLAY)
    Event code 208 (KEY_FASTFORWARD)
    Event code 212 (KEY_CAMERA)
    Event code 226 (KEY_MEDIA)
    Event code 272 (BTN_LEFT)
    Event code 273 (BTN_RIGHT)
    Event code 359 (KEY_TIME)
    Event code 368 (KEY_LANGUAGE)
    Event code 370 (KEY_SUBTITLE)
    Event code 372 (KEY_ZOOM)
    Event code 374 (KEY_KEYBOARD)
    Event code 375 (KEY_SCREEN)
    Event code 377 (KEY_TV)
    Event code 389 (KEY_DVD)
    Event code 392 (KEY_AUDIO)
    Event code 393 (KEY_VIDEO)
    Event code 402 (KEY_CHANNELUP)
    Event code 403 (KEY_CHANNELDOWN)
    Event code 407 (KEY_NEXT)
    Event code 412 (KEY_PREVIOUS)
    Event code 438 (KEY_CONTEXT_MENU)
    Event code 442 (?)
    Event code 512 (KEY_NUMERIC_0)
    Event code 513 (KEY_NUMERIC_1)
    Event code 514 (KEY_NUMERIC_2)
    Event code 515 (KEY_NUMERIC_3)
    Event code 516 (KEY_NUMERIC_4)
    Event code 517 (KEY_NUMERIC_5)
    Event code 518 (KEY_NUMERIC_6)
    Event code 519 (KEY_NUMERIC_7)
    Event code 520 (KEY_NUMERIC_8)
    Event code 521 (KEY_NUMERIC_9)
    Event code 522 (KEY_NUMERIC_STAR)
    Event code 523 (KEY_NUMERIC_POUND)
  Event type 4 (EV_MSC)
    Event code 4 (MSC_SCAN)
  Event type 20 (EV_REP)
Testing ... (interrupt to exit)
Event: time 1341312159.840573, type 4 (EV_MSC), code 4 (MSC_SCAN), value 289115b7
Event: time 1341312159.840580, type 1 (EV_KEY), code 116 (KEY_POWER), value 1
Event: time 1341312159.840582, -------------- SYN_REPORT ------------
Event: time 1341312160.092516, type 1 (EV_KEY), code 116 (KEY_POWER), value 0

Using irw, the remote does not act like a normal MCE remote. It's acting more like a keyboard. Right mouse brings up shortcut menu.

In mythtv the pad does the arrows, enter and esc. works also. That's about it though.

I will use MCC and try a re-configure to another imon

Lester

edit: ir-keytable has no code for Power button.
> lester@BACH:~$ sudo ir-keytable
[sudo] password for lester: 
Found /sys/class/rc/rc0/ (/dev/input/event5) with:
	Driver imon, table rc-imon-pad
	Supported protocols: other 
	Enabled protocols: 
	Repeat delay = 500 ms, repeat period = 125 ms


---

### Post by mymythtv on 2012-07-03
Hi Lester

Thanx - off my head from where I'm sitting ( @work )it looks very much like my setup/keys. Will check when I'll get back home...

In the meantime I found this thread:
[http://forum.xbmc.org/showthread.php?tid=76944]("http://forum.xbmc.org/showthread.php?tid=76944")

Just started to read it, but it LOOKS like that some change has been adapted into kernel around 2.6.32+ regarding usb/wakeup/suspend caused by usb-webcam interfering...

As I read it, it hits every RC with newer kernels, but I have to read it all before making conslusions.

Will read it and see if there is a conclusion/solution..

/Bjarne

---

### Post by mymythtv on 2012-07-04
Well - took another turn last night, but without success :-(

I tried to follow several guides regarding "wakeup" workarounds, but with no success.
Those included > echo USB? > /proc/acpi/wakeup 
echo enabled > /sys/bus/.../power/wakeup in multiple combinations, but that didn't do the trick.

As last I tried to boot different kernels. Currently I have the following available:

> bjarne@mythbuntu:/boot/grub$ grep title menu.lst
# title         Windows 95/98/NT/2000
# title         Linux
title           Ubuntu 12.04 LTS, kernel 3.2.0-26-generic-pae
title           Ubuntu 12.04 LTS, kernel 3.2.0-26-generic-pae (recovery mode)
title           Ubuntu 12.04 LTS, kernel 3.2.0-26-generic
title           Ubuntu 12.04 LTS, kernel 3.2.0-26-generic (recovery mode)
title           Ubuntu 12.04 LTS, kernel 3.2.0-25-generic-pae
title           Ubuntu 12.04 LTS, kernel 3.2.0-25-generic-pae (recovery mode)
title           Ubuntu 12.04 LTS, kernel 3.2.0-25-generic
title           Ubuntu 12.04 LTS, kernel 3.2.0-25-generic (recovery mode)
title           Ubuntu 12.04 LTS, kernel 2.6.32-41-generic
title           Ubuntu 12.04 LTS, kernel 2.6.32-41-generic (recovery mode)
title           Ubuntu 12.04 LTS, kernel 2.6.31-22-generic
title           Ubuntu 12.04 LTS, kernel 2.6.31-22-generic (recovery mode)
title           Ubuntu 12.04 LTS, memtest86+
bjarne@mythbuntu:/boot/grub$


3.2.0-26 and 3.2.0.25 didn't work ( no power on by RC )
2.6.32-41 DID work ( no changes, just press the button and htpc came on :-)  )
2.6.31-22 has always worked - kept kernel around due to other issues :-)

WAF factor is getting low, so I'm proberly going to downgrade to 2.6.32-41, reconfigure lirc "as in the old days" and then live with that for now :-(

/Bjarne

---

