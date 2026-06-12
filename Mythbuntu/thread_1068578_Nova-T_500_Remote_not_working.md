---
title: "Nova-T 500 Remote not working"
date: 2009-02-13
forum: Mythbuntu
---

### Post by teamwalrus on 2009-02-13
Hello,  I've installed Mythbuntu 8.10 on my PC with a NovaT 500 card which is working perfectly.  However I've been unable to get the usb remote to work at all.  I've tested it on a windows machine and it works fine there.  The remote is the all black one supplied with the Hauppauge Nova-t 500 capture card.

Even when I run 'irw' to to test the remote nothing happens.  Pressing buttons on the remote causes the remote LED and receive LED to flash, but nothing appears on the terminal window.

The remote does appear on the system:
```
I: Bus=0003 Vendor=2040 Product=9950 Version=0100
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:01:06.2-1/ir0
S: Sysfs=/devices/pci0000:00/0000:00:08.0/0000:01:06.2/usb5/5-1/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=14afc336 284284d 0 0 0 4 80058000 2190 40000801 9e96c0 0 900200 ffd
```

I've tried the help from this thread
[http://ubuntuforums.org/showthread.php?t=985311](http://ubuntuforums.org/showthread.php?t=985311)

And using the files from this page
[http://mythkiwi.com/index.php/remository?func=select&id=5](http://mythkiwi.com/index.php/remository?func=select&id=5)

But still no luck.

I'm a complete novice with ubuntu so hope I'm missing something obvious that someone can assist me with.

Below are the files that I think may help to see what I've got setup.

Any help would be greatly appreciated.

/etc/udev/rules.d/60-symlinks.rules
```
# This file establishes user-friendly symlinks to devices according to
# Ubuntu policy.  See udev(7) for syntax.
#
# The names of the actual devices themselves must not be set here, but
# in 20-names.rules; the permissions and ownership of those devices
# should be set in 40-permissions.rules.

# Compatibility symlinks for /dev/scd* devices
SUBSYSTEMS=="scsi", KERNEL=="sr[0-9]*", SYMLINK+="%k"

# Compatibility symlinks for USB printers
SUBSYSTEMS=="usb", KERNEL=="lp[0-9]*",  SYMLINK+="usb%k"

# Compatibility symlink for the CMOS RTC
SUBSYSTEM=="rtc", DRIVERS=="rtc_cmos", SYMLINK+="rtc"

# Create /dev/pilot symlink for Palm Pilots
KERNEL=="ttyUSB*", ATTRS{product}=="Palm Handheld*|Handspring *|palmOne Handheld", \
                                        SYMLINK+="pilot"

# Reverse mapping for /sys/dev
SUBSYSTEM=="block", SYMLINK+="block/%M:%m"
SUBSYSTEM!="block", SYMLINK+="char/%M:%m"

# Create /dev/input/irremote symlink for Nova-T 500
KERNEL=="event*", ATTRS{name}=="IR-receiver inside an USB DVB receiver", SYMLINK+="input/irremote"

```

/etc/lirc/hardware.conf
```
# /etc/lirc/hardware.conf
# for help setting this up goto http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI
# but remember that mythbuntu has a different prefix to the lines

REMOTE="Custom"
REMOTE_MODULES=""
REMOTE_DRIVER="dev/input"
REMOTE_DEVICE="/dev/input/irremote"
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/hauppauge/novat.conf"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

```

/usr/share/hal/fdi/preprobe/20thirdparty/novat.fdi
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
<device>
        <match key="info.product" string="IR-receiver inside an USB DVB receiver">
                <merge key="info.ignore" type="bool">true</merge>
        </match>
</device>
</deviceinfo>
```

/usr/share/lirc/remotes/hauppauge/novat.conf
```
#/usr/share/lirc/remotes/hauppauge/novat.conf
# brand:                       Hauppauge NOVA-T-500
# model no. of remote control: Hauppage Nova-T-500
#

begin remote

 name  NOVA-T500
 bits           16
 eps            30
 aeps          100

 one             0     0
 zero            0     0
 pre_data_bits   16
 pre_data       0x1
 gap          199999
 toggle_bit      0


     begin codes
         Go                       0x0162
         Power                    0x0074
         TV                       0x0179
         Videos                   0x0189
         Music                    0x0188
         Pictures                 0x00E2
         Guide                    0x016D
         Radio                    0x0181
         ArrowUp                  0x0067
         ArrowLeft                0x0069
         OK                       0x0160
         ArrowRight               0x006A
         ArrowDown                0x006C
         BackExit                 0x009E
         Menu                     0x008B
         VolumeUp                 0x0073
         VolumeDown               0x0072
         PrevCh                   0x016B
         Mute                     0x0071
         ChannelUp                0x0192
         ChannelDown              0x0193
         Record                   0x00A7
         Rewind                   0x00A8
         SkipBack                 0x0195
         Play                     0x00CF
         Pause                    0x0077
         Stop                     0x0080
         Fwdwind                  0x00D0
         SkipFwd                  0x0197
         1                        0x0002
         2                        0x0003
         3                        0x0004
         4                        0x0005
         5                        0x0006
         6                        0x0007
         7                        0x0008
         8                        0x0009
         9                        0x000A
         Star                     0x0037
         0                        0x000B
         #                        0x0029
         Red                      0x018E
         Green                    0x018F
         Yellow                   0x0190
         Blue                     0x0191
     end codes

end remote

```

/etc/lirc/lircd.conf
```
  GNU nano 2.0.7                            File: /etc/lirc/lircd.conf                                                                

#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Hauppauge Nova-T 500 remote:
include /usr/share/lirc/remotes/hauppauge/novat.conf

```

---

### Post by scary_jeff on 2009-02-13
I had problems setting my remote up, and solved it in the end by sudo apt-get remove --purge lirc, then when reinstalling lircd, selecting my remote from the list in the lirc setup thing. There's probably a way to run this setup utility without reinstalling, but I couldn't find it.

Also, my remote recently stopped working following some update. The solution was to build and install v4l-dvb from the latest source. See post number 7 _[here]("http://ubuntuforums.org/showthread.php?t=994447")_, but only download and build the driver, don't make any modifications (the modifications detailed in that post are now included in the latest source).

Hope this helps.

[edit] actually, since the remote is detected, it's probably not the v4l-dvb thing [/edit]
[edit] to remove lirc instead of lircd [edit]

---

### Post by teamwalrus on 2009-02-13
> **scary_jeff said:**
> I had problems setting my remote up, and solved it in the end by sudo apt-get remove --purge lircd, then when reinstalling lircd, selecting my remote from the list in the lirc setup thing. 

When I tried removing lircd I got an error that there was no package.  Instead I did 'apt-get remove --purge lirc' which worked.  Then did 'apt-get install lirc' which ran the setup program.

However nothing appears to have changed.  'irw' still does not return any codes when pressing buttons on the remote.

---

### Post by nickrout on 2009-02-13
just posting to mark the thread really, as I have a friend with the same remote (all black) and similar results.

---

### Post by scary_jeff on 2009-02-13
Does irw give an error of some kind, just return straight to the prompt, or just sit and do nothing?

If you run dmesg | grep lirc, does it say anything about a remote control driver? It seems weird that lircd wasn't found to uninstall; if that command doesn't give you anything, you probably need to install lircd.

---

### Post by olddave on 2009-02-13
Hi all
Done all of the things suggested here.
Here is the output from what scary_jeff said.
dave@recorder:~$ dmesg | grep lirc
[   49.334512] lirc_dev: IR Remote Control driver registered, at major 61 
[   49.442885] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.33 $
[   49.442890] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   49.747065] lirc_dev: lirc_register_plugin: sample_rate: 0
[   49.757039] lirc_mceusb2[2]: SMK eHome Infrared Transceiver on usb3:2
[   49.757111] usbcore: registered new interface driver lirc_mceusb2
[ 4993.458209] usbcore: deregistering interface driver lirc_mceusb2
[ 4993.459579] lirc_mceusb2[2]: usb remote disconnected
[ 5138.937095] lirc_dev: IR Remote Control driver registered, at major 61 
dave@recorder:~$ 
irw does nothing just seems to hang..
Thanks olddave

---

### Post by teamwalrus on 2009-02-13
> **scary_jeff said:**
> Does irw give an error of some kind, just return straight to the prompt, or just sit and do nothing?

If you run dmesg | grep lirc, does it say anything about a remote control driver? It seems weird that lircd wasn't found to uninstall; if that command doesn't give you anything, you probably need to install lircd.

scary_jeff; the irw gives no prompting at all.  Nothing appears on screen after starting the command.  CTRL+C exits it fine.

dmesg | grep lirc
```
[   11.823535] lirc_dev: IR Remote Control driver registered, major 61 
[   11.827024] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
[   11.827027] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   12.234749] lirc_dev: lirc_register_plugin: sample_rate: 0
[   12.246747] lirc_mceusb2[2]: SMK eHome Infrared Transceiver on usb3:2
[   12.246832] usbcore: registered new interface driver lirc_mceusb2
[   86.482316] usbcore: deregistering interface driver lirc_mceusb2
[   86.483467] lirc_mceusb2[2]: usb remote disconnected

```

If you think I need to install lircd can you help a novice with some prompt help.  Is that 'sudo apt-get get install lircd' or something similar?

---

### Post by teamwalrus on 2009-02-14
Actually I think lircd is installed/running.

```

ps -ef |grep lirc
root      4077     1  0 17:30 ?        00:00:00 /usr/sbin/lircd --driver=devinput --device=/dev/input/irremote
brian     6425  6403  0 17:32 pts/0    00:00:00 grep lirc

```

Also 'ls /dev/l*' shows
```

/dev/lirc0  /dev/lircd  /dev/log  /dev/loop0  /dev/lp0

```

Now if I do 'sudo cat /dev/lirc0' and press the buttons on the remote, each time I press a button, code appears on the screen.  I think thats good :)

However the command 'irw' still shows nothing when the remote buttons are pressed.

Any other ideas are greatly appreciated.

---

### Post by smbm on 2009-02-14
I've had this problem since I got the card. 

I've been trying every couple of months to get it working to no avail.

I'll definitely be following this thread for ideas.

Good luck teamwalrus

---

### Post by teamwalrus on 2009-02-14
smbm, I'm afraid if I'm gonna find a solution we'll need a lot more than luck :)

As I said I can 'cat /dev/lirc0' and get the remote data coming through.

I can even run
```
sudo irrecord -d /dev/lirc0 myremote
```
and use irrecord to create my own remote definition file by pressing the buttons on the remote.  That all worked fine.
(then copied the new file to '/usr/share/lirc/remotes/hauppauge/' and updated /etc/lirc/hardware.conf to use my new definition file).

But I can not get 'irw' to work.  

I tried changing '/etc/lirc/hardware.conf' so that defining the device was 'REMOTE_DEVICE="/dev/lirc0"' instead of 'REMOTE_DEVICE="/dev/input/irremote"'.   I had hoped that maybe if there is data coming through /dev/lirc0 then maybe I could use that.... but no.  Still not working.

I'll keep banging away at it.

---

### Post by scary_jeff on 2009-02-15
I'm not an expert but I think if irw just does nothing, then it has at least managed to connect to lircd.

As for the dmesg output, this bit seems odd:

[   86.482316] usbcore: deregistering interface driver lirc_mceusb2
[   86.483467] lirc_mceusb2[2]: usb remote disconnected

Maybe there's a power saving option or something? The driver being unregistered makes it even more strange that cat dev/lirc0 gives some output... I'm afraid I'm a bit lost at this point :(

Try ls -l /dev/input . Mine shows irremote permissions are 777.If yours doesn't show all permissions, try sudo chmod 777 /dev/input/irremote.

Your guess was right on installing lircd. If trying to remove it says that it doesn't exist, I would give this a go. iirc it has some configuration steps that were what eventually got my remote to work.

Actually, what's this about an MCE remote? Do you have two IR receivers connected? If so, how do you know which receiver is picking up which remote? I would definitely get rid of any 2nd remote while trying to get the NovaT to work.

---

### Post by freak42 on 2009-02-15
are you sure that the entry in your *.fdi file is correct and hal doesn't grab your remote and let's it act as a keyboard?

my *.fdi file looks like this:
```
<?xml version="1.0" encoding="UTF-8"?>

<!-- 
  This file must reside in:

  /usr/share/hal/fdi/preprobe/20thirdparty
  
  It will cause HAL ignore the Nova-T Stick's remote control event device, which will allow LIRC to capture it  
-->

<deviceinfo version="0.2">

<device>
	<match key="info.product" string="Nova-T Stick">
		<merge key="info.ignore" type="bool">true</merge>
	</match>
</device>

</deviceinfo>

```

the 'string' is from this line of output from lshal:
  usb_device.product = 'Nova-T Stick'  (string)

---

### Post by teamwalrus on 2009-02-16
scarey_jeff; there is only the one remote connected.  The USB one that came with the Nova-t 500 card.

I did have a USB wireless keyboard+mouse connected.  However I'm sure that receiver for that wasn't picking up the remote (I physically positioned the remote so only the remote receiver would receive it).

Removing the wireless keyboard/mouse AND the remote and doing 'dmesg | grep lirc' returns nothing.  Plugging in the remote (and reboot) and then doing the same command returns.

```
dmesg | grep lirc
[   11.322277] lirc_dev: IR Remote Control driver registered, major 61
[   11.378317] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
[   11.378320] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   11.850113] lirc_dev: lirc_register_plugin: sample_rate: 0
[   11.862114] lirc_mceusb2[2]: SMK eHome Infrared Transceiver on usb1:2
[   11.862214] usbcore: registered new interface driver lirc_mceusb2

```

Makes no difference to 'irw' or myth testing with the wireless/keyboard removed.

My '/dev/input/irremote' has the same 777 permission as you.

--
freak42;

My file looks like this:
usr/share/hal/fdi/preprobe/20thirdparty/novat.fdi

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
<device>
        <match key="info.product" string="IR-receiver inside an USB DVB receiver">
                <merge key="info.ignore" type="bool">true</merge>
        </match>
</device>
</deviceinfo>

```

In lshal I do have this line:
```
input.product = 'IR-receiver inside an USB DVB receiver'  (string)
```

However you say it should match the **usb_device.product**, not **info.product**.  On my system I have:

```

lsham | grep usb_device.product
  usb_device.product = '2.0 root hub'  (string)
  usb_device.product_id = 2  (0x2)  (int)
  usb_device.product = 'WinTV Nova-DT'  (string)
  usb_device.product_id = 39248  (0x9950)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.product = '2.0 root hub'  (string)
  usb_device.product_id = 2  (0x2)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.product = 'M-UV69a/HP M-UV96 Optical Wheel Mouse'  (string)
  usb_device.product_id = 49174  (0xc016)  (int)
  usb_device.product = '2.0 root hub'  (string)
  usb_device.product_id = 2  (0x2)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.product = 'Smart Card Keyboard'  (string)
  usb_device.product_id = 4132  (0x1024)  (int)
  usb_device.product = 'eHome Infrared Receiver'  (string)
  usb_device.product_id = 802  (0x322)  (int)

```

I tried (changed string):

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
<device>
        <match key="info.product" string="WinTV Nova-DT">
                <merge key="info.ignore" type="bool">true</merge>
        </match>
</device>
</deviceinfo>

```

And tried (changed string, and match key):

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
<device>
        <match key="usb_device.product" string="WinTV Nova-DT">
                <merge key="info.ignore" type="bool">true</merge>
        </match>
</device>
</deviceinfo>

```

And tried (changed string):

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
<device>
        <match key="info.product" string="eHome Infrared Receiver">
                <merge key="info.ignore" type="bool">true</merge>
        </match>
</device>
</deviceinfo>

```

After each of the above changes I did a reboot and tested 'irw' and mythtv.  No response from any of the changes to the file.  I've restored the .fdi file back to its original state.

Thanks for the suggestion guys.  I do appreciate them.  Am going to bang my head against a wall now for a while....

---

### Post by teamwalrus on 2009-02-17
I read somewhere (in the plethera of forum threads) that I should be able to start lircd manually with the following command after stopping the service.

```
sudo /etc/init.d/lirc stop
 * Stopping remote control daemon(s): LIRC                               [ OK ]
sudo lircd -n /etc/lirc/hardware.conf
lircd-0.8.3[6510]: error in configfile line 4
lircd-0.8.3[6510]: reading of config file failed
lircd-0.8.3[6510]: lircd(userspace) ready

```

As you can see its reporting an error in the config file.
Here is the file.

```
# /etc/lirc/hardware.conf
#Chosen Remote Control
REMOTE="Hauppauge Nova-T 500"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/irremote"
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/hauppauge/novat.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
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

So its saying the line **REMOTE_MODULES=""** is incorrect.  When I compare it with other files on the net it looks correct.  If I comment out this line, the error just moves down to the next line **REMOTE_DRIVER="devinput"**, and if I comment out that line, the error moves down again......

Means nothing to me, but maybe someone else?

---

### Post by scary_jeff on 2009-02-17
OK, it looks like your NovaT 500 is different to mine then. Mine came with an IR sensor that plugs into the TV card itself.

Did you try installing / reinstalling lirc? I think this generates a hardware.conf for you in its setup wizard thing.

[edit] to say 'lirc' instead of 'lircd' [edit]

---

### Post by teamwalrus on 2009-02-17
The only socket on my capture card is for the antenna connection.  The remote I received looks like the attached (although the receiver is a little more rounded, then square) and connects via usb.

I can not install lircd using the command you recommended.  I must be doing something wrong.

```

sudo apt-get get install lircd
E: Invalid operation get

~$ sudo apt-get install lircd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lircd

```

---

### Post by scary_jeff on 2009-02-17
Oh, looks like I didn't remember what I did correctly, sorry!

Maybe I reinstalled lirc completely... yea that's probably it. But if this does work and you are able to select a remote, it looks like you wouldn't want to select the nova-t, because that did work for me, and your remote is totally different.
There's probably a generic MCE remote option, I'm assuming there's some standard that all MCE remotes adhere to. This might be your best bet.

---

### Post by teamwalrus on 2009-02-17
scary_jeff; I did remove and reinstall lirc (ref post #3 of this thread) however as you've said maybe my remote config is incorrect.

As previously stated I did use the command
```
sudo irrecord -d /dev/lirc0 myremote
``` to create my own remote config file.

So I would assume that the codes(?) in the file are correct as they were generated each time I pressed a button on the remote.

HOWEVER the 'labels' or names for each of the buttons I just made up myself as I related them to the buttons on the remote.  Perhaps the labels need to be something specific for it to work?  For example perhaps the play button must be labeled 'Play' and I have it as 'play' so its not working?  Just a thought.

I've got no idea what the output of 'irw' SHOULD be.  Does it just output raw data like 'cat /dev/lirc0' or does it only output labels, or only data mapped to labels in the remote config file?

I'll try your suggestion reinstalling lirc and using the wizard to select a 'generic' MCE remote and see how that goes.  Thanks.

---

### Post by teamwalrus on 2009-02-18
Oh my kingdom for a piece of paper that says 'This is not a Hauppauge remote'.

I removed lirc, reboot, reinstalled lirc.  The setup wizard started automatically.

This time I selected the remote as 'Windows Media Center Remotes (new version Philips et'.  Another reboot.

Ran 'irw' and I get a response when keys pressed on the remote!!!
Started Mythtv, but the remote wouldn't work.

Ran the Mythbuntu Control Center and reselected the remote so it generated, well whatever it needed to generate.  Tested Mythtv again.  And its working!!

I think some of the buttons on the remote are not mapping but I will play around with that.

Thank you very much for your help.  Much appreciated!

---

### Post by scary_jeff on 2009-02-18
Great news!

Does anybody know if there's a way to run the lirc wizard without reinstalling it?

---

### Post by olddave on 2009-02-20
Hi All
After reading on here and on the Internet there seems to be several different remote controls and receivers. Mine is the same remote as teamwalrus but my IR receiver is smaller then the one shown. When i reinstalled lirc got to the gui and i selected the Windows MCE (new philips) then the IR receiver i selected windows MCE direct TV IR receiver. Then when i got back to the desktop and put the cmd irw and pressed buttons on the remote got out put in the terminal window (so good so far).
But when i try to use the remote in myth TV i get nothing. so does any one how to get the remote working in myth..
Thanks olddave

---

### Post by scary_jeff on 2009-02-21
You need to create a .lircrc file. I think there's a generator for this somewhere in the frontend setup utility, but if you can't find that, try _[here]("http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI#Remote_Control")_, but you can ignore the bit about vbetool and visudo unless you want the power button to turn your monitor off.

---

### Post by pjbgravely on 2009-02-23
> **scary_jeff said:**
> Great news!

Does anybody know if there's a way to run the lirc wizard without reinstalling it?


sudo dpkg-reconfigure lircd

should do the trick.

Paul

---

### Post by olddave on 2009-03-06
Hi all.
scary_jeff i created a .lircrc file that got some buttons working but only a few. When i compared the lirc file and the lircrc files some of the button names where wrong eg the button for the volume was vol in the lirc file and volume in the lircrc file. so all i did was change the mismatched buttons and they all work now.
Thanks for all the help.
olddave

---

