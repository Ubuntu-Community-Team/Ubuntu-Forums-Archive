---
title: "Upgraded from 9.10 to 10.04 broke lirc."
date: 2010-10-14
forum: Mythbuntu
---

### Post by Meph1st0 on 2010-10-14
Just upgraded to 10.04 and I've noticed two problems so far.  First problem is that lirc appears to be all screwy.  I'm using the Zalman HD135 remote.  I've attempted to fix it two ways.  First I followed this thread: [http://ubuntuforums.org/showthread.php?t=671307&highlight=zalman](http://ubuntuforums.org/showthread.php?t=671307&highlight=zalman)

I was very much involved in that thread before and was able to get it working back then.  However, this didn't work for me this time.  I then tried to use Mythbuntu Control Center and select the VLSystems MPlay Blast option in the infrared portion of MCC.  

What's happening is that irw only responds back with output after several button presses (between 4 and 10 presses).

I'll get a response back like the following after pressing the RIGHT button several times:

```
jbrown@browndvr:/etc/lirc$ irw
0000000000000043 00 Right VLSystem_MPlay_Blast
0000000000000043 00 Right_UP VLSystem_MPlay_Blast

```

I'm wondering if I need to adjust the repeat option in my ~/.mythtv/lircrc file or if I need to downgrade to an older version of lirc.  I'm just not sure.  Any help is greatly appreciated.

I'll post details about the second problem in a separate post.

---

### Post by Meph1st0 on 2010-10-15
One weird thing that happened last night as I was fiddling with this lirc just started working.  I haven't a clue what I did.  it seems that after I had rebooted it started working, how cool was that, eh?  Happy times all around.  But then related to another post I've made recently about my picture being messed up I had to reboot again.  When I rebooted this second time my lirc is back to being broken again.  How cool is that?

---

### Post by ac00perw on 2010-10-17
I hate to be the guy that glums on to your woes, but I too am having this issue since upgrading to 10.04. My only guess is that the fact that it works intermittently is related to the order in which lirc modules are loading. I, too, am able to get irw to read my remote. Here I check to see if a lircd process is running and then try 'irw.' The first time it breaks so I stop and restart lirc and boom- irw starts spitting stuff out as seen below. This must be a simple issue. I wonder if having two lirc installs could be the problem? Did I read somewhere that lirc is built into 10.04? Anybody?

:~$ ps ax | grep lirc
 2683 ?        S<s    0:00 /usr/sbin/lircd --output=/var/run/lirc/lircd1 --device=/dev/lirc1 --connect=localhost 8765 --pidfile=/var/run/lirc/lircd1.pid

:~$ irw
connect: Connection refused

:~$ sudo service lirc stop
 * Stopping remote control daemon(s): LIRC
   ...done.

:~$ sudo service lirc start
 * Loading LIRC modules
   ...done.
 * Starting remote control daemon(s) : LIRC 
   ...done.

:~$ irw
0000000000001794 00 Up Hauppauge_350

---

### Post by Meph1st0 on 2010-10-19
well, I just now read that lirc is built into 10.10 but I don't know about 10.04.  Just yesterday I thought I'd just take a jump and upgrade once more to 10.10 to see if that would help any.  Well it didn't.  Here's the thread i just finished reading about lirc being built into 10.10.  I'm going to give the instructions a try in this thread and see how it goes.  I'll post back if it works for me.

[http://ubuntuforums.org/showthread.php?t=1594799](http://ubuntuforums.org/showthread.php?t=1594799)

I know this thread is talking about the MCE remote and I have the Zalman HD135.  I figure I'll just have to tailor it a little to my remote.

---

### Post by Meph1st0 on 2010-10-19
okay, so.  I do actually have a mythtv frontend that uses the MCE remote and following the thread that I had posted about yesterday fixed it.  Now I'm going to see if I can get my Zalman HD135 to work following the same general steps.

---

### Post by Meph1st0 on 2010-10-21
Okay, so following that thread didn't help me any because I couldn't figure out what I should put into the blacklist.conf file for the Zalman HD 135 remote.

However, I've found something of interest.  I've found that if I enter "screen /dev/ttyUSB0 9600" at the terminal then it'll kind of wake up lirc and it'll start working for me.  The next time I reboot I've got to reenter that command again.  I don't exactly know what that means though.

Any input on this would be very helpful.

Thanks.

---

### Post by Meph1st0 on 2010-10-28
I've come up with a basic workaround for this thread.  Basically as I had stated in my previous post; if I enter "screen /dev/ttyUSB0 9600" in the terminal then it basically wakes lirc up and my remote (and vfd dislay) starts working.  But then if I reboot then I'll have a broken lirc again and will have to reenter the command at the terminal again to bring it back.

So my workaround is that I edited the /etc/rc.local file and put the screen /dev/ttyUSB0 9600 line in there so that it does that on boot up.

Hopefully all the lirc problems will be resolved soon because I'm seeing that a lot of people are having issues with it after upgrading from 9.10.

---

### Post by Meph1st0 on 2010-10-31
Peers,

I've been fighting with this problem for two weeks now.  I've receied one response; one that was unhelpful but only to let me know that they're having the same problem as I am.  This is uncharacteristic for this forum. Is there anyone out there who can provide some actual help with this?

I thought I'd found a workaround be apparently it's not working for me anymore.  I don't know why.

Once again, here's the setup I'm running:

I know the title says i'm running 10.04 but now I'm running mythbuntu 10.10 with the 0.32.1 auto builds repo enabled as well as the mythbuntu-testing PPA.
I'm using a Zalman HD 135 case and it's accompanying remote.
I have lirc 0.8.7 installed.

I believe I have the lirc-modules-source installed.

Here's my hardware.conf:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="VLSystem MPlay Blast"
REMOTE_MODULES=""
REMOTE_DRIVER="mplay"
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="vlsystem/lircd.conf.mplay"
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

Here's my lircd.conf:
```
#
# this config file was automatically generated
# using lirc-0.8.2(mplay) on Fri Dec  7 20:04:59 2007
#
# contributed by 
#
# brand:                       VLSystem
# model no. of remote control: MPlay Blast
# devices being controlled by this remote:
#

begin remote

  name  VLSystem_MPlay_Blast
  bits            8
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          211938
  toggle_bit_mask 0x0

      begin codes
          PwrOff                   0x41
          PwrOn                    0x55
          Movies                   0x40
          Television               0x46
          Photos                   0x45
          Music                    0x56
          1                        0x4d
          2                        0x4e
          3                        0x4f
          4                        0x50
          5                        0x51
          6                        0x52
          7                        0x53
          8                        0x03
          9                        0x07
          0                        0x4c
          Vol+                     0x0a
          Vol-                     0x0e
          Ch+_Lang                 0x12
          Ch-_Page                 0x16
          Guide                    0x0f
          Back                     0x0b
          Tv                       0x13
          Ok                       0x42
          Up                       0x19
          Left                     0x54
          Right                    0x43
          Down                     0x1d
          Exit_Click               0x1f
          Task_Quick               0x17
          Run_DClick               0x1b
          Rew                      0x0d
          Play                     0x09
          Ffwd                     0x15
          Prev                     0x1a
          Stop                     0x01
          Next                     0x1e
          Pause                    0x05
          Mute                     0x4a
          Warp_Mouse               0x47
          Rec                      0x11
          DVD_Zoom                 0x14
          Detail                   0x4b
      end codes

end remote

```

Here's lspci:
```
00:00.0 Host bridge: VIA Technologies, Inc. PT880 Ultra/PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5372
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237S PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1)
03:05.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:05.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
03:05.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
03:05.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
03:07.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

```

Here's dmesg | grep lirc:
```
dmesg | grep lirc
[   17.960496] lirc_dev: IR Remote Control driver registered, major 61 
[   17.960989] ir_lirc_codec: Unknown symbol lirc_dev_fop_poll (err 0)
[   17.961096] ir_lirc_codec: Unknown symbol lirc_dev_fop_open (err 0)
[   17.961177] ir_lirc_codec: disagrees about version of symbol lirc_get_pdata
[   17.961180] ir_lirc_codec: Unknown symbol lirc_get_pdata (err -22)
[   17.961268] ir_lirc_codec: Unknown symbol lirc_dev_fop_close (err 0)
[   17.961347] ir_lirc_codec: Unknown symbol lirc_dev_fop_read (err 0)
[   17.961416] ir_lirc_codec: disagrees about version of symbol lirc_register_driver
[   17.961418] ir_lirc_codec: Unknown symbol lirc_register_driver (err -22)
[   17.961605] ir_lirc_codec: Unknown symbol lirc_dev_fop_ioctl (err 0)

```

I don't know what other information I need to provide.  Any help would be appreciated.  Thank you kindly.

---

### Post by Meph1st0 on 2010-10-31
So I just removed lirc-modules-source as I've been seeing that it shouldn't be there.  now this is what I get for dmesg | grep lirc:

```
[    9.716273] lirc_dev: IR Remote Control driver registered, major 250 

```

Despite the obvious difference in dmesg I'm still not seeing any improvement with irw or with the VFD.

Please consider this a desperate plea for help.

Respectfully,

Jonathan

---

### Post by mocha on 2010-10-31
I'm having similar problems but with an irblaster.  Seems like this bug might be related to your issue, [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/655512]("https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/655512")

I'm not exactly sure if it applies to my problem though.

---

### Post by Meph1st0 on 2010-11-01
> **mocha said:**
> I'm having similar problems but with an irblaster.  Seems like this bug might be related to your issue, [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/655512]("https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/655512")

I'm not exactly sure if it applies to my problem though.

I've seen that bug and it does appear to apply to me.  Post #41 and #42 make it appear that there's a way to fix it by removing the lirc-modules-source package but that didn't work for me. Here's some more information though to add..  Sometimes it just works all of a sudden.  I've found that if I fuss, and fuss, and fuss with the problem I get nowhere.  And then when I give up; two or three days later it'll just all of a sudden start working.  And then maybe myth crashes or I update, or something and I have to reboot and then I'm right back to where I began.  At present that's where I'm at.  I'm waiting for it to suddenly start working.  It's like I've got my own little elves from the children's story The Elves and the Shoemaker that come out at night and fix my remote problems until the next time that I have to reboot for whatever reason.

---

### Post by mocha on 2010-11-02
Check my latest post in here [http://ubuntuforums.org/showthread.php?t=1609804]("http://ubuntuforums.org/showthread.php?t=1609804")

---

### Post by Meph1st0 on 2010-11-03
It's working again.  We'll see for how long this time again.  I do still have to use the command: screen /dev/ttyUSB0 9600 to wake it up.

The steps I took (I believe) were to reinstall linux-modules-source.  I had to remove the /dev/ttyUSB0 9600 command from my /etc/rc.local file.  I then edited my /etc/lirc/hardware.conf file to include the following:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="VLSystem MPlay Blast"
REMOTE_MODULES=""
REMOTE_DRIVER="mplay"
REMOTE_DEVICE="/dev/ttyUSB0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="vlsystem/lircd.conf.mplay"
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
LOAD_MODULES="lirc_dev lirc_mplay"

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

The parts that I had to change in this file were these lines:

REMOTE_DEVICE="/dev/ttyUSB0"
LOAD_MODULES="lirc_dev lirc_mplay"

---

### Post by mocha on 2010-11-04
> **Meph1st0 said:**
> The parts that I had to change in this file were these lines:

REMOTE_DEVICE="/dev/ttyUSB0"
LOAD_MODULES="lirc_dev lirc_mplay"

Hmmm.. Those are not right.  LOAD_MODULES is a boolean.  Leave it blank if you don't want lirc to load the necessary modules or put the word "true" there if you do.  The lines REMOTE_MODULES and/or TRANSMITTER_MODULES is where you specify the actual module name(s).

REMOTE_DEVICE is supposed to be "/dev/lirc0" usually.  You specify the actual remote hardware device location (ttyUSB0) in the file /etc/modprobe.d/lirc-serial.conf (or something like that, I'm not at my box at the moment).

---

### Post by thecapsaicinkid on 2010-11-06
I raised the original bug for the HD-135. I don't actually use Lirc anymore but would like to use lcdproc. My display seems to be completely dead, I cannot get any response out of it whatsoever. It sits with the led permanently lit and the 'Welcome to Zalman' message on the display.

LCDd reports no errors but the display will not print anything from any client.

```
screen /dev/ttyUSB0 9600
```

This doesn't seem to do anything on my machine, led stays lit.

---

