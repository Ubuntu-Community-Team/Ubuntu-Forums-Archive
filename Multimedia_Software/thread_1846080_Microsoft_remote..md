---
title: "Microsoft remote."
date: 2011-09-18
forum: Multimedia Software
---

### Post by Lisiano on 2011-09-18
Hello all. I have a Mircrosoft remote that came with my PC, I have no idea how to set it up correctly. My machine detects it and sets it as a keyboard ```
lisiano@Lisiano-Ubuntu:~$ xinput list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Mouse                                 id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; PHILIPS MCE USB IR Receiver- Spinel plus  id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=10   [slave  keyboard (3)]
```While I don't mind that and it works but some keys don't work, ("Start", "Multimedia apps", "Scroll", Teletext, Menu, colored keys). While I don't really use those I would like to set up the Start key to start XBMC and the Multimedia apps to Key_F so it Fullscreens/Windows XBMC, Menu to Tab, etc.
lspci -v of the IR Receiver ```
Bus 003 Device 002: ID 0471:0613 Philips (or NXP) Infrared Transceiver
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0471 Philips (or NXP)
  idProduct          0x0613 Infrared Transceiver
  bcdDevice            1.01
  iManufacturer           1 PHILIPS
  iProduct                2 MCE USB IR Receiver- Spinel plus
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     427
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0002
  (Bus Powered)
  Remote Wakeup Enabled
```I have a feeling I got to use lircd but I don't know exactly how to set it up. Any pointers are appreciated.
PS. I use KDE but don't mind to install Gnome apps. To be precise, I have both KDE and Gnome.

---

### Post by Lisiano on 2011-09-21
Bumpers.

---

### Post by aeiah on 2011-09-21
im pretty sure i just did sudo apt-get install lirc and it ran a config after it installed, asking me which remote to select. there's an mce-remote that works with most.

i launch xbmc with my start button by running irexevent on boot. it just waits for the start button to be pressed and launches xbmc. no other buttons need setting up because xbmc recognises everything its self.

you might have problems with lirc conflicting with the keyboard device but hopefully not

---

### Post by Lisiano on 2011-09-21
So I ran ```
sudo dpkg-reconfigure lirc
``` Got presented a ncurses menu and picked "Windows Media Center Transceivers/Remotes (all)", Transmitter "None". kRemoteControl Daemon decided to spring into action and said I have 3 remotes "mceusb", "mceusb_haupauge", "vista_mce". Adding a test entry to play/pause amarok by pressing "1" or "One" fails in all 3 and I can still "Type" numbers with the remote.

[quote=aeiah]you might have problems with lirc conflicting with the keyboard device but hopefully not[/quote]
Probably that is why seeing how xinput list shows it as a keyboard.

---

### Post by Lisiano on 2011-09-28
Bumpers, anyone knows how to make the remote a real remote instead of a keyboard?

---

### Post by Lisiano on 2011-10-05
*Bumper*

---

### Post by Lisiano on 2011-10-10
Bumpety bump.

---

### Post by Lisiano on 2011-10-18
I bump thy thread.

---

### Post by Lisiano on 2011-10-21
&#1041;&#1072;&#1084;&#1087;-&#1090;&#1080;&#1073;&#1080;-&#1073;&#1072;&#1084;&#1087;.
(Bump-tibi-bump in Russian)

---

### Post by s13_mills on 2011-10-29
Hi there,

I don't know if this is complicated by the fact that this is a USB remote only (ie not an IR input on a TV card or what not), but you might try setting the ir-keytable to the exact one for your remote, and eliminating the two that are incorrect. If it transpires that you have a mix of the three, you can configure that too.

I have found that with my LIRC setup my remote still 'types' in a terminal, but I am able to get it to do exactly what I want within an application (which is the important bit right?)

to check your keytable right now:

```
sudo ir-keytable
``` 

To test if the events are recognised as keys, BEFORE they are parsed by LIRC:

```
sudo /etc/init.d/lirc stop
sudo ir-keytable -t
```

Press buttons, and you will see things changing. If you have output that indicates your machine knows which key you are pressing for each key, you have it set up OK (although in your case you may want to clean the table down to only the entries you need).

There is a selection of keytables available in /lib/udev/rc_keymaps, you can pick one by doing:

```
sudo ir-keytable -c
sudo ir-keytable -w /lib/udev/rc_keymaps/[INSERT TABLE YOU WANT HERE]
```

Bear in mind that changing these things may mess with your LIRC configuration.

What you COULD try (I haven't done this, but it might work) is map the scancode from one of the buttons that has an undesirable effect (like the power button trying to shutdown the computer or similar) to a completely unrelated keycode, then using your lircd.conf to map it back to the action you want. I don't know if I explained that too well - if you want clarification just ask :).

After you are done with all that, restart lirc:

```
sudo /etc/init.d/lirc/start
```

---

### Post by Lisiano on 2011-10-31
Ahhh thanks. I'm not home atm but I will try this once I get home. Sounds promising. Except I didn't understand what exactly were you referencing here
[quote=s13_mills]I don't know if this is complicated by the fact that this is a USB remote only (ie not an IR input on a TV card or what not), but you might try setting the ir-keytable to the _exact one for your remote_, and eliminating the _two that are incorrect_. If it transpires that you have a mix of the three, you can configure that too.[/quote]
I'm assuming you are talking about the "mceusb", "mceusb_haupauge" and "vista_mce" that LIRC decided to give me when I told it I have a MCE.
Note: I'm not afraid to mess up my LIRC conf since there is nothing (I think) beside what dpkg put there.

---

### Post by s13_mills on 2011-11-04
Hi again,

How did you go? Did you get it figured out?

Sorry if I was a bit unclear below:

> I don't know if this is complicated by the fact that this is a USB remote only (ie not an IR input on a TV card or what not)

I was referring to the fact that this is a remote with it's own USB receiver, as opposed to a remote that came with a TV card or similar, which has the receiver built into the TV card.

> I'm assuming you are talking about the "mceusb", "mceusb_haupauge" and "vista_mce" that LIRC decided to give me when I told it I have a MCE.

With regard to the different configurations, they are keymaps for within ir-keytable, rather than inside LIRC - it is a similar thing though, and will likely have similar names. They are all found in /lib/udev/rc_keymaps/ (from memory).

Cheers,

Andrew

---

### Post by Lisiano on 2011-11-30
Hi, I haven't been able to do anything yet till this moment, work, health, life. Anyway.
ir-keytables wasn't installed so after installing it.
```
sudo ir-keytable -t
/sys/class/rc/: No such file or directory
lisiano@Lisiano-Ubuntu:~$ cd /sys/class/rc
bash: cd: /sys/class/rc: No such file or directory
```
I don't know if this is good news or bad news... Assuming bad.

---

### Post by mutant_matt on 2011-12-02
What Kernel version are you on? (uname -a).  What Distro and version?

Sounds to me like you might have a kernel of 2.6.35 or newer?  (where the MCE stuff changed and the driver moved out of LIRC and into the main-line kernel).  This is sounds very similar to the MCE USB remote setup I just went through on Mythbuntu 11.10 where I ended up setting LIRC to Linux Devinput (from the Myth Control Centre), plugging in the eventX into hardware.conf, and ran two lircd's to link the two events together, that the "Windows Vista/Windows 7" MCE remote presents itself as (an HID Keyboard and an HID Mouse).

What is the result of: modprobe -l | grep mce

Some of the steps here are useful: [http://parker1.co.uk/mythtv_ubuntu2.php](http://parker1.co.uk/mythtv_ubuntu2.php) (Kerel Drivers/LIRC section)

If you identify the event it's using, as per the above page, you can start at the bottom and work your way up:

cat /dev/input/eventX - push buttons and see if you get garbage on the screen for each press (and if some buttons work, and some others don't)

sudo evtest /dev/input/eventX - to see what mappings are taking place

sudo /usr/sbin/lircd -H dev/input -d /dev/input/eventX -n  plus irw in another window

Matt :)

---

### Post by Lisiano on 2011-12-02
```
uname-a
Linux Lisiano-Ubuntu 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```
It started from the very purchase of this PC, I think I installed Ubuntu 10.04 or 9.10 on it. Somewhere there. Currently using Ubuntu 11.10.
```
modprobe -l | grep mce
kernel/arch/x86/kernel/cpu/mcheck/mce-xeon75xx.ko
kernel/arch/x86/kernel/cpu/mcheck/mce-inject.ko
kernel/drivers/media/rc/keymaps/rc-fusionhdtv-mce.ko
kernel/drivers/media/rc/keymaps/rc-genius-tvgo-a11mce.ko
kernel/drivers/media/rc/keymaps/rc-imon-mce.ko
kernel/drivers/media/rc/keymaps/rc-rc6-mce.ko
kernel/drivers/media/rc/mceusb.ko
kernel/drivers/edac/mce_amd_inj.ko
kernel/drivers/edac/edac_mce_amd.ko
```
```
cat /proc/bus/input/devices

I: Bus=0003 Vendor=0471 Product=0613 Version=0100
N: Name="PHILIPS MCE USB IR Receiver- Spinel plus"
P: Phys=usb-0000:00:02.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb3/3-1/3-1:1.0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 
B: PROP=0
B: EV=120013
B: KEY=c0000 40000000000 0 58000 8001e84000c004 e0beffdf01cfffff fffffffffffffffe
B: MSC=10
B: LED=1f

```
Cating /dev/input/event3 gives random garbage only on those buttons that work. 
sudo evtest /dev/input/event3 didn't show anything when I pressed these buttons:
[LIST]
[*]Multimedia Apps(?)
[*]Windows Media Center
[*]Teletext
[*]Red/Green/Yellow/Blue buttons
[/LIST]
Those buttons are exactly the ones I wish to bind to do other functions, WMC - start XBMC, Teletext - Context Menu, R/G/Y/B - Prev Page/Prev tab/Next tab/Next page (For web browsing)
And per my original question, is there any way to make these buttons work?

EDIT: [quote=mutant_matt]sudo /usr/sbin/lircd -H dev/input -d /dev/input/eventX -n plus irw in another window[/quote]
The remote stops working (No events are printed in evtest and nothing shows up in lircd and irw). The only thing that happens is that lircd say that a client connected. Once I stop irw, it says a client disconnected.

---

### Post by mutant_matt on 2011-12-02
As suspected, you're on a current Kernel where the device is using mceusb from the main-line kernel automatically (11.10 comes with 3.0.x kernel and Lirc 0.9.0).

From the cat /proc/bus/input/devices command, are you sure you don't have something like, in addition to event3:

I: Bus=0003 Vendor=0471 Product=0613 Version=0100
N: Name="PHILIPS MCE USB IR Receiver- Spinel plus"
P: Phys=usb-0000:00:02.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb3/3-1/3-1:1.0/input/input4
U: Uniq=
H: Handlers=kbd mouse1 event4

For me, some buttons work on the keyboard event (up/down/left/right/OK), some others on the mouse event (Play, Pause, green/red/blue/yellow etc), so to get them all working, a later step is to run two lircd daemons, to link the two together, to provide one set of working button events to the next layer up.

I can't remember the order you have to do everything, but it sounds like you need to setup LIRC to point at the Linux Event Layer (I did this from the Mythbuntu Control Centre which is a graphical UI), and then edit the hardware config file something like this:

 /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event3"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="devinput/lircd.conf.devinput"
REMOTE_LIRCD_ARGS=""

Hopefully, this will then allow the test lircd/irw to work?  Once that's working, you can worry about remapping/key bindings in an lircrc file for your specific app, and if required, linking two lircds together.

HTH!

Matt :)

---

### Post by Lisiano on 2011-12-03
```
lisiano@Lisiano-Ubuntu:~$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input2
U: Uniq=
H: Handlers=sysrq kbd event2 
B: PROP=0
B: EV=120013
B: KEY=10000 c020000000000 0 0 700f02000003 3803078f830f401 febfffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=0471 Product=0613 Version=0100
N: Name="PHILIPS MCE USB IR Receiver- Spinel plus"
P: Phys=usb-0000:00:02.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb3/3-1/3-1:1.0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 
B: PROP=0
B: EV=120013
B: KEY=c0000 40000000000 0 58000 8001e84000c004 e0beffdf01cfffff fffffffffffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=04f3 Product=0216 Version=0111
N: Name="USB Mouse"
P: Phys=usb-0000:00:02.0-4/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb3/3-4/3-4:1.0/input/input4
U: Uniq=
H: Handlers=mouse0 event4 
B: PROP=0
B: EV=17
B: KEY=1f0000 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA NVidia Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:07.0/sound/card0/input5
U: Uniq=
H: Handlers=event5 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA NVidia HDMI/DP,pcm=9"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:10.0/0000:02:00.1/sound/card1/input6
U: Uniq=
H: Handlers=event6 
B: PROP=0
B: EV=21
B: SW=100

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA NVidia HDMI/DP,pcm=8"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:10.0/0000:02:00.1/sound/card1/input7
U: Uniq=
H: Handlers=event7 
B: PROP=0
B: EV=21
B: SW=100

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA NVidia HDMI/DP,pcm=7"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:10.0/0000:02:00.1/sound/card1/input8
U: Uniq=
H: Handlers=event8 
B: PROP=0
B: EV=21
B: SW=100

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA NVidia HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:10.0/0000:02:00.1/sound/card1/input9
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=100

lisiano@Lisiano-Ubuntu:~$ 
``` Judging by this line ```
H: Handlers=sysrq kbd event3 
``` It's a keyboard only device so guessing no need for multiple Lircd daemons
Here is the original lirc hardware config ```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
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
Edited that to this
```
..snip..

#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event3"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="devinput/lircd.conf.devinput"
REMOTE_LIRCD_ARGS=""

..snip..
```
After a ```
sudo service lirc restart
```
The remote still works and as before, irw stops the remote from working.

EDIT: After a while (Just noticed) the remote stopped working, regardless of irw. Reverting to the old hardware.conf to see if it'll be fixed.

EDIT 2: Reverting hardware.conf fixed it.

---

### Post by mutant_matt on 2011-12-05
Hmm.  Sorry, sounds like either driver doesn't fully support your particular device!?  Presumably, you'll need help from someone smarter than I, or someone who has already got this exact device fully working, who can give you some pointers.

I tried!  Sorry.

Good luck,

Matt :)

---

### Post by toto70 on 2012-07-30
Hello,

I've the same remote and i had the same problem. I spent three days looking for the solution, and i've found the solution here :
[http://ben.periton.co.uk/2012/06/configuring-the-zotac-zbox-remote-control/](http://ben.periton.co.uk/2012/06/configuring-the-zotac-zbox-remote-control/)

The only difference is 6. Instead of using :

> SUBSYSTEM=="usb" , ATTRS{idVendor}=="0471", ATTRS{**idProduct**}=="**20cc**", SYMLINK+="remote", ACTION=="add", RUN+="/sbin/initctl --quiet emit --no-wait ir-ready"

Replace the idProduct 20cc by 0613.

---

