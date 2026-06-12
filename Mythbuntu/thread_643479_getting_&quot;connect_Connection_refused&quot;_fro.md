---
title: "getting &quot;connect: Connection refused&quot; from irw"
date: 2007-12-17
forum: Mythbuntu
---

### Post by bmturney on 2007-12-17
I just about have Myth working... one of the few remaining problems is that not all of the buttons on my remote are working.  So I'm trying to run irw to collected needed information, and when I run **sudo irw** I get the message **connect: Connection refused**

Any help will be greatly appreciated.

---

### Post by oobe-feisty on 2007-12-17
that is strange that connection refused msg is normally caused by drivers that arnt loaded or lircd is not configured properly BTW you dont need to use sudo to run irw perhaps that is the problem if only numbers and volume is working its likely that you are not using the correct lircd.conf or the correct modules either way  you can find out what the key presses should be outputting inside lircd.conf which is what i assume you are trying to achieve the the irw command

---

### Post by bmturney on 2007-12-17
> **oobe-feisty said:**
> that is strange that connection refused msg is normally caused by drivers that arnt loaded or lircd is not configured properly BTW you dont need to use sudo to run irw perhaps that is the problem if only numbers and volume is working its likely that you are not using the correct lircd.conf or the correct modules either way  you can find out what the key presses should be outputting inside lircd.conf which is what i assume you are trying to achieve the the irw command

I tried running the **irw** command without the sudo and I get the same message.  As is, the numbers work the up-down-left-right direction arrows work.  My main problem right now is that the pause, play and stop buttons don't work.  (I'm using VLC has my media player if that matters).  

I looked at the lircd.conf file in /etc/lirc (I may be looking in the wrong place... not sure).  The description of the remote seems correct.  Although I'm not completely sure on that either.  I'm using a MCE remote and USB receiver that came with a Dell laptop that I bought a year or so ago.

Anyway, I was thinking that all that I needed to do was to run irw and figure out what codes were being sent by the respective buttons on the remote and then just update the lircd.conf file to match the codes I'm seeing... am I going about this all wrong?

I'm a n00b in case you couldn't tell... :^)

---

### Post by oobe-feisty on 2007-12-18
its pretty likely that the IR reciever onboard the laptop is not supported it doesnt matter so much what remote you are using as the IR reciever needs to be supported

a good way to find out more info about the reciever you are using is to run "dmesg | grep IR" and look carefullly for your remote reciever as you will most likely be given other out aswell

---

### Post by Nikas on 2007-12-18
Use:
 irrecord --device=/dev/lirc0 test.conf
You may need to change "/dev/lirc0" to fit your install.

Follow the instructions.
This will make a test.conf that you can compare with lircd.conf.
Replace the codes in lircd.conf with the generated codes in test.conf.

You can use test.conf as lircd.conf directly but this can cause problems with MythTV.
You cant use irw to collect your codes. Use irrecord.

---

### Post by bmturney on 2007-12-18
> **oobe-feisty said:**
> its pretty likely that the IR reciever onboard the laptop is not supported it doesnt matter so much what remote you are using as the IR reciever needs to be supported

a good way to find out more info about the reciever you are using is to run "dmesg | grep IR" and look carefullly for your remote reciever as you will most likely be given other out aswell

I ran the dmesg command you listed and it shows up there as "Philips RCS USB IR Combo Device"  This IR receiver is a USB device its not built into the laptop itself.

---

### Post by bmturney on 2007-12-18
> **Nikas said:**
> Use:
 irrecord --device=/dev/lirc0 test.conf
You may need to change "/dev/lirc0" to fit your install.

Follow the instructions.
This will make a test.conf that you can compare with lircd.conf.
Replace the codes in lircd.conf with the generated codes in test.conf.

You can use test.conf as lircd.conf directly but this can cause problems with MythTV.
You cant use irw to collect your codes. Use irrecord.


I ran the irrecord command that you listed above, and I got a message "could not init hardware (lircd running ? --> close it, check permissions)

being the n00b that I am, how do I shut down lircd?

---

### Post by Nikas on 2007-12-18
> **bmturney said:**
> I ran the irrecord command that you listed above, and I got a message "could not init hardware (lircd running ? --> close it, check permissions)

being the n00b that I am, how do I shut down lircd?

You ran the command as super user (su) or used sudo?

Kill ircd.
Find the right pid: ps -e
And then: sudo kill xxxx

You said that some buttons worked? Seems like lircd works then...

Do you have a /dev/lirc0? Check permissions too.
Also.. post your/etc/lirc/hardware.conf

---

### Post by bmturney on 2007-12-18
I've made a little progress (very little progress) since my last post... I stopped and restarted lirc and ran the command **sudo irrecord --device=/dev/lircd test.conf**.  It went through a couple of instructional screens and then it said "Press Return now to start recording".  When I press Enter I get a message that says it can't find /etc/lircd

to answer your question, No I do not have /dev/lirc0 directory... the only lirc* object I have under /dev is /lircd (thus the reason I used /etc/lircd in the irrecord command above)

Also, my /etc/lirc/hardware.conf file looks like this > # /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)"

# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES="lirc_dev lirc_mceusb2"

# Default configuration files for your hardware if any
LIRCD_CONF="mceusb/lircd.conf.mceusb"
LIRCMD_CONF=""

---

### Post by bmturney on 2007-12-18
> **Nikas said:**
> 
Kill ircd.
Find the right pid: ps -e
And then: sudo kill xxxx


When I run ps -e I do not see anything like ircd

---

### Post by Nikas on 2007-12-18
> **bmturney said:**
> When I run ps -e I do not see anything like ircd

I'm new to this and i got my stuff working by installing a newer version of lirc. (0.8.3pre1)

Try this:
```
sudo wget http://launchpadlibrarian.net/10229062/lirc_0.8.3%7Epre1-0ubuntu1_i386.deb
```

Then install with:
```
sudo dpkg -i lirc_0.8.3~pre1-0ubuntu1_i386.deb
```

Reboot.

---

### Post by bmturney on 2007-12-19
i'm currently on 0.8.2 of lirc... I tried the download that you mention.. however I'm running on an AMD64 platform, so the i386 download doesn't work on my system.  I tried finding 0.8.3 for A64 but couldn't find it anywhere... any ideas where I can get my hands on it?

---

### Post by OffAxis on 2007-12-19
don't worry; it should work.
>>edit: I take that back, I think it'll work, but I may have accidentally installed a 32 bit ubuntu on my amd64 box.

what kernel are you using?
and what version of ubuntu?

that pre-release package is targeted for the next release but does work on gutsy.

---

### Post by tohc1 on 2007-12-19
Could you post the complete output of the "dmesg | grep IR" command and maybe "dmesg | grep input" if its different.

I think you need to find which device is your ir reciever and then tell lirc to use this.

if the ir reciever is assigned to /class/input/inputX then you need change the lines in hardware.conf to:

DEVICE="/dev/input/eventX" 

DRIVER="dev/input"

---

### Post by OffAxis on 2007-12-19
> When I press Enter I get a message that says it can't find /etc/lircd


sounds like you're starting/stopping lircd with 
```
sudo lirc start
```

which looks for lircd.conf in the **/etc** folder.

you've gotta run through the init.d
```
sudo /etc/init.d/lirc start
```
and then it'll look in the **/etc/lirc** folder.

By the way, that .8.3 package probably won't fix your problem; the major impetus for installing that is to fix the broken serial port infrared drivers (irman), which isn't your problem.

---

### Post by bmturney on 2007-12-19
Here is the output from **dmesg | grep IR**

> [    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[   14.841621] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.841809] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 *10 11 14 15)
[   14.841991] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.842175] ACPI: PCI Interrupt Link [LNK4] (IRQs *5 7 9 10 11 14 15)
[   14.842358] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 *7 9 10 11 14 15)
[   14.842540] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.842723] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 *11 14 15)
[   14.842905] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.843089] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
[   14.843271] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.843468] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 *7 9 10 11 14 15)
[   14.843650] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.843834] ACPI: PCI Interrupt Link [LAZA] (IRQs *5 7 9 10 11 14 15)
[   14.844024] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 *11 14 15)
[   14.844206] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.844390] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 *7 9 10 11 14 15)
[   14.844577] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 11 14 *15)
[   14.844760] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.844944] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
[   14.845132] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
[   14.845359] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   14.845571] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[   14.845781] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   14.845991] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[   14.846201] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
[   14.846412] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   14.846623] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0
[   14.846837] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   14.847048] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   14.847259] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   14.847480] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   14.847691] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   14.847903] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0
[   14.848115] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[   14.848327] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   14.848539] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   14.848750] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   14.848962] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   14.849174] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   14.849390] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   14.849603] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   14.853578] PCI: Using ACPI for IRQ routing
[   14.853736] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[   15.616157] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.412240] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   17.412252] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 23
[   17.587167] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   17.587181] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 22
[   17.694972] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[   17.694984] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 21
[   19.096866] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[   19.096878] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 20
[   19.747989] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   19.748002] ACPI: PCI Interrupt 0000:04:07.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[   20.115860] input: Philips RCS USB IR Combo Device as /class/input/input2
[   20.115865] input: USB HID v1.00 Keyboard [Philips RCS USB IR Combo Device] on usb-0000:00:0b.0-7
[   20.127852] input: Philips RCS USB IR Combo Device as /class/input/input3
[   20.127883] input,hiddev96: USB HID v1.00 Device [Philips RCS USB IR Combo Device] on usb-0000:00:0b.0-7
[   25.691235] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   25.691248] ACPI: PCI Interrupt 0000:04:09.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 17
[   26.634454] tveeprom 2-0050: has radio, has no IR receiver, has no IR transmitter
[   30.393712] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   30.393715] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [AAZA] -> GSI 23 (level, low) -> IRQ 23
[   46.275478] lirc_dev: IR Remote Control driver registered, at major 61 
[   46.283084] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.33 $


I'm using Mythbuntu 7.10, as for the version of the kernel, ??? whatever version came on the Live CD... (I'm a Linux n00b in case you couldn't tell)  Let me know what I need to do to determine the version of the kernel and I will post it...

---

### Post by bmturney on 2007-12-19
> **tohc1 said:**
> Could you post the complete output of the "dmesg | grep IR" command and maybe "dmesg | grep input" if its different.

I think you need to find which device is your ir reciever and then tell lirc to use this.

if the ir reciever is assigned to /class/input/inputX then you need change the lines in hardware.conf to:

DEVICE="/dev/input/eventX" 

DRIVER="dev/input"

How do I determine which device is my IR receiver?

---

### Post by bmturney on 2007-12-19
Also, just another question... I'm using vlc as my media player.  I went into the Settings->Preferences->Interface->Control Interface and turned on the infrared remote control interface... was this correct to do?

Also, there are a number of hot keys programable through vlc to control the media and the app.  Am I supposed to be mapping those hot keys to buttons on the remote, and if so, where/how do I assign those hot keys to their corresponding button on the remote.

---

### Post by Nikas on 2007-12-20
> **bmturney said:**
> How do I determine which device is my IR receiver?

[ 20.127852] input: Philips RCS USB IR Combo Device as /class/input/input3

---

### Post by bmturney on 2007-12-22
OK... I have the hardware.conf file updated with /class/input/input3 for the DEVICE.    I also stop and restarted lirc and the Pause, Play, Stop buttons still not not work on the remote.  

I also tried to run **irrecord --device=/class/input/input3 test.conf** but it says /class/input/input3 does not exist.

also, trying to run irw... I still get the "connection refused" message.

What should I try now?  I'm completely out of ideas...

---

### Post by tohc1 on 2008-01-01
> OK... I have the hardware.conf file updated with /class/input/input3 for the DEVICE.
In your hardware.conf try:

DEVICE="/dev/input/event3" 

If that still doesn't work it might be using input 2 (from your dmesg post)
> 
[ 20.115860] input: Philips RCS USB IR Combo Device as /class/input/input2
[ 20.115865] input: USB HID v1.00 Keyboard [Philips RCS USB IR Combo Device] on usb-0000:00:0b.0-7
[ 20.127852] input: Philips RCS USB IR Combo Device as /class/input/input3
[ 20.127883] input,hiddev96: USB HID v1.00 Device [Philips RCS USB IR Combo Device] on usb-0000:00:0b.0-7

so try DEVICE="/dev/input/event2" as well

---

### Post by volkswagner on 2008-01-02
Are you still irw getting connection refused?  If so what remote is selected in mythbuntu control centre?  If it is an RF remote you will get connection refused since they don't use IR.

---

### Post by Xcerca on 2008-09-10
I'm sort of having the same probelm, irw /dev/usb/hiddev1 says 'connect: Connection refused' I think i'm getting close but i had some questions...

I found the device useing cat /dev/usb/hiddev1 and when i push buttons i get an output , then i do irrecord and when i look at the file it makes, there are remote codes next to the names i put in. What do i need to do from here?

I can use irrecord -d /dev/usb/hiddev1 -H sb0540 /etc/lircd.conf to record my buttons and it seems to work, but is that correct location for the lircd.conf ? there is also a /etc/lirc/lircd.conf , i'm not sure which one to write to but it seems to me like they mirror each other when i change one.

 what files do i need to have configured properly for lirc to work , /etc/lirc/lircd.conf and /etc/lirc/hardware.conf right ?

---

