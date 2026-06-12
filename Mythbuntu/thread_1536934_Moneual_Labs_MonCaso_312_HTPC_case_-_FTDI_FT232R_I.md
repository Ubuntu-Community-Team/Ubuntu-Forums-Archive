---
title: "Moneual Labs MonCaso 312 HTPC case - FTDI FT232R IR Remote Lirc Problems"
date: 2010-07-22
forum: Mythbuntu
---

### Post by 8link on 2010-07-22
Hello all,

I purchased a Moneual Labs MonoCaso 312 HTPC case that included an IR remote control based on the FTDI FT232R USB to serial chip. I'm running mythbuntu 10.04.  The remote is working pre-post as a power button.   I've spent the last month researching and attempting to get it up and running but have had no luck.  I hope you guys can assist.

I'm not sure the device is being properly initialized.  When I run ```
cat /proc/bus/devices
``` The FT232R is not listed.

dmesg output:
```
dmesg | grep lirc
[ 2463.113384] lirc_dev: IR Remote Control driver registered, major 61 
[ 2464.012031] lirc_serial: auto-detected active low receiver
[ 2464.012040] lirc_dev: lirc_register_driver: sample_rate: 0
[ 2464.012187] lirc_serial $Revision: 5.104 $ registered

``````
dmesg | grep serial
[    2.312185] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.592847] usbcore: registered new interface driver usbserial
[   16.594612] usbcore: registered new interface driver usbserial_generic
[   16.594622] usbserial: USB Serial Driver core
[ 2464.012031] lirc_serial: auto-detected active low receiver
[ 2464.012187] lirc_serial $Revision: 5.104 $ registered

```setserial output:
```

setserial /dev/ttyUSB0
/dev/ttyUSB0, UART: unknown, Port: 0x0000, IRQ: 0, Flags: low_latency

```This seems like it might be a problem?

/etc/lirc/hardware.conf:
```

# /etc/lirc/hardware.conf                
#                                        
#Chosen Remote Control                   
REMOTE="VLSystem MPlay Blast"            
REMOTE_MODULES=""                        
REMOTE_DRIVER="mplay"                    
REMOTE_DEVICE="/dev/ttyUSB0"             
REMOTE_LIRCD_CONF=""                     
REMOTE_LIRCD_ARGS=""                     

#Chosen IR Transmitter
TRANSMITTER="None"    
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="" 
TRANSMITTER_DEVICE="" 
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD=true

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
REMOTE_MODEL="MPlay Blast"
REMOTE_VENDOR="VLSystem"

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="Serial Port Receiver"
RECEIVER_VENDOR="Generic"

```/etc/lirc/lircd.conf:
```

# /etc/lirc/hardware.conf                
#                                        
#Chosen Remote Control                   
REMOTE="VLSystem MPlay Blast"            
REMOTE_MODULES=""                        
REMOTE_DRIVER="mplay"                    
REMOTE_DEVICE="/dev/ttyUSB0"             
REMOTE_LIRCD_CONF=""                     
REMOTE_LIRCD_ARGS=""                     

#Chosen IR Transmitter
TRANSMITTER="None"    
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="" 
TRANSMITTER_DEVICE="" 
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD=true

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
REMOTE_MODEL="MPlay Blast"
REMOTE_VENDOR="VLSystem"

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="Serial Port Receiver"
RECEIVER_VENDOR="Generic"
frontend@frontend:~/zalmanremote$ 
frontend@frontend:~/zalmanremote$ cat /etc/lirc/lircd.conf
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

#Configuration for the VLSystem MPlay Blast remote:
include "/usr/share/lirc/remotes/vlsystem/lircd.conf.mplay"

```I've tried many different drivers [usb_uirt, uirt2, raw, ftdi, mplay] and used different lircd.conf configs.  Nothing has worked.

I've never seen any output from irw or mode2.  The device is loading at /dev/ttyUSB0 but I get no output when issuing ```
cat /dev/ttyUSB0 | hexdump 
```I'm sure I've missed or done something stupid and would really appreciate any guidance you can provide.

Thanks
8

---

### Post by justme123 on 2010-08-01
Hello 8link,

i have the same problem with the same case and remote control. Whatever i tried so far it didn't work. It seems also that only the power button is proper recognised at least if u configure lirc via gui (here it was recognised 2 times at my system).
All other input from the remote control ain't recognised. 

Actually i have also no solution, maybe a new lirc version (beta svn version) with the latest
libFTDI sources would help, at least lots of ppl seem to have problems with the FTDI chips and linux.  :(

A similar problem was here with a Zalman HD135 (maybe same or at least similar chip)
[http://old.nabble.com/Help-with-VLSystems-MPlay-Blast-td26067350.html#a26067350](http://old.nabble.com/Help-with-VLSystems-MPlay-Blast-td26067350.html#a26067350)
also there was no solution except that the problem was maybe a problem with the kernel driver.

Since i have a very basic understanding only from linux dunno if it would make a difference to change the ftdi driver and use the one
listed here [http://www.ftdichip.com/Drivers/D2XX.htm](http://www.ftdichip.com/Drivers/D2XX.htm)

Further infos regarding that chip are here at A. J. Huitsing Website [http://www.huitsing.nl/irftdi/](http://www.huitsing.nl/irftdi/) where he says ... "something funky going on with the FTDI chips" ... dunno if that is somehow related to our problems.

Found more infos here about a patch regarding an Issue aboutthe broken ftdi serial driver ( but seems not to work for everyone) [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460857](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460857)

If i try to record my own buttons i get the following error, i assume you get the same ?

sudo irrecord -d /dev/ttyUSB0 irrecord.out

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not get hardware features
irrecord: this device driver does not support the LIRC ioctl interface
irrecord: major number of /dev/ttyUSB0 is 188
irrecord: LIRC major number is 61
irrecord: check if /dev/ttyUSB0 is a LIRC device
irrecord: could not init hardware (lircd running ? --> close it, check permissions)

this is my output from lsusb 

Bus 004 Device 002: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0403 Future Technology Devices International, Ltd
  idProduct          0x6001 FT232 USB-Serial (UART) IC
  bcdDevice            6.00
  iManufacturer           1
  iProduct                2
  iSerial                 3
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               90mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              2
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)


One last thing since your conf file contains "Zalmanremote" did u try already that custom made Zalman driver here
[http://zalman.ostergaard.net/lirc.html](http://zalman.ostergaard.net/lirc.html) also it is for a Zalman HD160XT it seems to be the same chip?


No Idea what to do now :(

---

### Post by 8link on 2010-08-02
Justme -

Glad to know I'm not the only one experiencing this problem.  Seems we've been hitting the same links to boot.

I haven't tried irrecord [figured if irw displays nothing, irrecord would as well] but I'll try it and reply back.

I did try the Zalmanremote driver.  It didn't work either.

One thing I failed to specify in my first post was kernel version I'm running.  As the problem may very well be due to a broken/fixed/broken kernel driver the running kernel seems quite relevant.  I will likely try to update to the latest kernel and see if that affects any change.

If you find something please post up, I'll do the same.

8

---

### Post by justme123 on 2010-08-03
hi 8link,

What i'm also still not sure about is is the correct solution here to try the mplay driver for the VLSystem MPlay (also it's based on FT232R) or would be the ftdi driver (for FTDI FT232-based IR Receiver) the correct one ? At least the more i read about lirc and possible settings the more confused i get hehe.

---

### Post by justme123 on 2010-08-08
tried now to compile a new lirc version from cvs inlcuding libftdi 0.18
from here [http://www.intra2net.com/en/developer/libftdi/download.php](http://www.intra2net.com/en/developer/libftdi/download.php)
but no real success with either "mplay" or "ftdi" driver

---

### Post by justme123 on 2010-08-10
the communication between libftdi 0.18 and the ftdi chipset seems to work
at least all included tools give me some answer kinda

what just irritates me is this here from the baud_test program

real baudrate used: 9600
this test should take 10.42 seconds
and took 47.6141 seconds, this is 2100 baud or factor 0.219

should i lower down the baudrate on the port somehow ?
also still no idea what driver and configuration is the correct one :(

---

### Post by 8link on 2010-08-11
I'm not sure that your baud rate test is providing you any real data.  **setserial** output lists the UART as unknown because its a virtual com port that hasn't been configured.
I poked around a bit and noticed that while ftdi_so is creating /dev/ttyUSB0 it isn't creating a dev that can be used with lirc as well, a dev with a major number of 61.
This points to the fact that the kernel support of the ftdi driver may very well be forked up.
I think.

---

### Post by justme123 on 2010-08-14
8link i agree with u kinda, at least either that or lirc is somehow buggy there or i'm to stupid (could be also the case :P).

 At least from all supplied grogramms from the latest  libftdi 0.18 (bitbang and so on)
i get some result kinda also i dunno if that are real results.

The major number 61 from what i remember used to come up also only if i tried the lirc_dev/serial driver from lirc, it didn't show up using mplay or ftdi.

---

### Post by justme123 on 2010-08-28
Ok still no luck even with the "new" 2.6.35 Kernel and a new ftdi_sio 1.6 there
still the same issues, tried it with the older 0.8.6 lirc and also the newer 0.8.7rcs.

Only the PowerButton works every other button of the remote ain't working :(

---

### Post by DemonBob on 2010-08-28
What is the output of ls -l /dev/input/by-id when you have the remote hooked up. We may be able to get it to work with a different program.

---

### Post by justme123 on 2010-08-29
Hi DemonBob,

the output from ls -l /dev/input/by-id is 
cannot access /dev/input/by-id: No such file or directory

using only /dev/input gives me

total 0
crw-r----- 1 root root 13, 64 2010-08-29 17:24 event0
crw-r----- 1 root root 13, 65 2010-08-29 17:24 event1
crw-r----- 1 root root 13, 66 2010-08-29 17:24 event2
crw-r----- 1 root root 13, 67 2010-08-29 17:24 event3
crw-r----- 1 root root 13, 63 2010-08-29 17:24 mice
crw-r----- 1 root root 13, 32 2010-08-29 17:24 mouse0

but it is listed under 
/dev/serial/by-id/usb-FTDI_FT232R_USB_UART_A600aPdp-if00-port0

and

/dev/serial/by-path/pci-0000:00:04.0-usb-0:3:1.0-port0

---

### Post by DemonBob on 2010-08-29
With it being listed in serial, i don't know if this would work. I make no garentees. 


Download [http://www.bedroomlan.org/projects/evrouter](http://www.bedroomlan.org/projects/evrouter) make sure to select the correct one 32 vs 64. 

Onc installed run evrouter -d 

Start pressing buttons on your remote. If you get out like below, then we may be in bussiness. If not.... then i don't think it will work. 

```
Acme USB Keyboard" "/dev/input/event1" none key/257 "fill this in!"
              "Acme USB Keyboard" "/dev/input/event1" shift key/257 "fill this in!"
              "Acme USB Keyboard" "/dev/input/event1" alt key/256 "fill this in!"
              "Acme USB Keyboard" "/dev/input/event1" none key/155 "fill this in
```

---

### Post by justme123 on 2010-08-30
i don't see a big difference in the hardware setup the moncaso is using with it's FTDI chip
to other ones i think either the ftdi setup with lirc should work kinda, i'm just not sure what i need to setup there for example as device.

Looking here [http://www.huitsing.nl/irftdi/](http://www.huitsing.nl/irftdi/) it seems maybe this would be enough in hardware.conf

REMOTE_DRIVER="ftdi"                    
REMOTE_DEVICE="serial=A600aPdp"

but not sure about it ... and that's the main problem what's exactly needed there as setup.

At least i think the provided samples in libftdi seem to work but since they're way more basic than lirc ....

i'll try the proggy u suggested tomorrow but i doubt this can work since the remote ain't a HID device.

---

### Post by justme123 on 2010-08-31
DemonBob nope doesn't work 
it doesn't find the device

---

### Post by justme123 on 2010-09-04
ok, since i wasn't able to verify anything (button presses under linux) so far i checked it under windows at least the remote control file for the vl systems seems to be correct or better said the button codes in the conf file, the same hex codes are transmitted to windows after pressing a button ... so far so good ...

After setting now again "mplay" as driver and adding some more debug Logprints to hw_mplay.c i finally have the feeling the mplay driver is kinda never called at least my debug info in mplay_init never shows up either in syslog or in the lircd debug log ....:confused:

---

### Post by justme123 on 2010-09-20
think it seems now i got it working (at least under xbmc i don't use Mythbuntu) after playing around with the mplay driver and making some modifications to it, i still need to look into some keymappings but all in all it looks promissing :)

---

### Post by cyber7 on 2010-09-21
Please could you tell me how you did this?
 
I also have this case and trying to get my XBMC-LIVE environment working.
 
Cheers
Cyber7

---

### Post by justme123 on 2010-09-22
Hi cyber7,

the following did work for me

1. Get the Lirc Sources
2. find and open in the daemons folder the hw_mplay.c driver
3. exchange the the existing code in mplay_init with the following
```

int mplay_init(void)
{
        int result = 1;
        struct termios portset;
        signed int len;
        char buf = 0x96;
        char psResponse [11];
           
        LOGPRINTF(1, "Entering mplay_init()");
        /* Creation of a lock file for the port */
        if (!tty_create_lock(hw.device)) {
                logprintf(LOG_ERR,   "Could not create the lock file");
                LOGPRINTF(1, "Could not create the lock file");
                result = 0;
            }
            LOGPRINTF(0, "open serial port");
        /* Try to open serial port */
        if ((hw.fd = open(hw.device, O_RDWR | O_NOCTTY )) < 0) {
                logprintf(LOG_ERR,   "Could not open the serial port");
                LOGPRINTF(1, "Could not open the serial port");
                tty_delete_lock();
                result = 0;
            }
        /* Get serial device parameters */
        if (tcgetattr(hw.fd, &portset) < 0) {
              logprintf(LOG_ERR, "Could not get serial port attributes");
              LOGPRINTF(1, "Could not get serial port attributes");
               mplay_deinit();
                result = 0;
            }
          portset.c_cflag &= ~PARENB;
        portset.c_cflag &= ~CSTOPB;
        portset.c_cflag &= ~CSIZE;
        portset.c_cflag = B57600 | CS8;
        portset.c_cflag |= (CLOCAL | CREAD);
        portset.c_iflag |= (IXON | IXOFF | IXANY);
        portset.c_oflag &= ~OPOST;
        portset.c_lflag &= ~(ICANON|ECHOE| ECHO|ISIG );
        portset.c_cc[VSTART] = 0x11;    
        portset.c_cc[VSTOP]  = 0x13;  
        portset.c_cc[VEOF]   = 0x20;                            
        portset.c_cc[VMIN]     = 1;
        portset.c_cc[VTIME]     = 3;              

        if (tcsetattr(hw.fd, TCSANOW, &portset) < 0) {
             logprintf(LOG_ERR, "Error setting TCSANOW mode of serial device");
              LOGPRINTF(1, "Error setting TCSANOW mode of serial device"); 
              mplay_deinit();
               result = 0;    
        }    
    
        len = write(hw.fd, &buf, 1);
        if (len < 0) {
               LOGPRINTF(LOG_ERR,"couldn't write to device");    
               mplay_deinit();
               result = 0;    
        }    
           len = read(hw.fd, &psResponse,11); 
         if (len < 0)
            {
                        LOGPRINTF(1,"No data recieved during reading");    
                        mplay_deinit();
                       result = 0;    
        }
        else
        {
                        LOGPRINTF(1,"read chars: %s", psResponse);
           } 
    
            if (tcgetattr(hw.fd, &portset) < 0) {
               logprintf(LOG_ERR, "Could not get serial port attributes");
              LOGPRINTF(1, "Could not get serial port attributes");
               mplay_deinit();
                result = 0;
            }    
        portset.c_cflag &= ~PARENB;
        portset.c_cflag &= ~CSTOPB;
        portset.c_cflag &= ~CSIZE;
        portset.c_cflag = B57600 | CS8;
        portset.c_cflag |= (CLOCAL | CREAD);
        portset.c_iflag |= (IXON | IXOFF | IXANY);
        portset.c_oflag &= ~OPOST;
        portset.c_lflag &= ~(ICANON|ECHOE| ECHO|ISIG );
        portset.c_cc[VSTART] = 0x11;    
        portset.c_cc[VSTOP]  = 0x13;  
        portset.c_cc[VEOF]   = 0x1C;                            
        portset.c_cc[VMIN]     = 1;
        portset.c_cc[VTIME]     = 3;    

        if (tcsetattr(hw.fd, TCSANOW, &portset) < 0){
            logprintf(LOG_ERR, "Error setting TCSANOW mode of serial device");
            LOGPRINTF(1, "Error setting TCSANOW mode of serial device");   
            mplay_deinit();
             result = 0;    
        }
        return result;
} 

```

4. compile lirc and use the mplay driver and as remote device REMOTE_DEVICE="/dev/ttyUSB0
5. you can use as template remote the VLSystem MPlay Blast it's pretty much the same remote lirc ours only the gap is a little bit different and a few buttons it seems.
I recorded later my own didn't tried if that makes a difference or if it works also without problems
6. Don't forget to change the Lircmap.xml and add either your own recorded remote or the VLSystem if that works also 

Hopefully i didn't forget anything

---

### Post by justme123 on 2010-10-08
did that work for you or for someone else with a moncaso 312 ("new remote") except myself ?

---

### Post by MacUsers on 2010-10-09
Hi there,

I've recently purchased a MonCaso 320 (similar to 312 w/a VFD) case and struggling to IR receiver to work. Presently it doesn't do anything more that switching on and off the computer. [COLOR=RoyalBlue]* lsusb*[/COLOR] lists the device correctly (I believe): 

```
Bus 003 Device 002: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0403 Future Technology Devices International, Ltd
  idProduct          0x6001 FT232 USB-Serial (UART) IC
  bcdDevice            6.00
  iManufacturer           1 FTDI
  iProduct                2 FT232R USB UART
  iSerial                 3 A600dyfH
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               90mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              2 FT232R USB UART
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)
```Do you have any suggestion/advise for me, please? Cheers!!

---

### Post by justme123 on 2010-10-09
Hi MacUsers,

how to get the display working not sure about it. sorry. The remote could maybe also work with my modified mplay driver from lirc also i'm not sure about since i don't have it, at least you could give it a try to get at least for now the remote working.
The important part at least for my moncaso 312 was to send the single byte 0x96 to enable the reciever if that don't work for your device the only advice i can give you try the same like i did. Install windows on a hdd and monitor the communication on the serial port and see what happends when you start the mplay software.
I had to try a couple of different configurations in the termios structure you could play with it also around, my device i.e. didn't like something else than b57000 as baudrate and also not if i open it O_NONBLOCK. Maybe also have a look here [http://lcdproc.org/](http://lcdproc.org/) for the display and modify the mplay driver slightly if it don't work out of the box even.

I hope this maybe helps you a little bit.

---

### Post by MacUsers on 2010-10-09
Many thanks justme, for your replay. I'll give it a try shortly. Moneual technical support is absolutely useless, normally they don't replay at all. After reading the various story about Moneual IR, my only hope is you, as you got it working somehow. I think, 312 and 320 is exactly the same, only difference is the higher price tag for a VFD. As I was told by the one of the retailer, all the time I was thinking it's a SoundGraph iMon device and trying to set it up like that, until yesterday.  I'll let you know how it goes. Cheers!!

---

### Post by justme123 on 2010-10-10
Hi MacUsers,
yep didn't get any answer also in the last time from them after asking for some infos :confused:.
I think since ur device uses the same Mplay Driver it should be the same OEM device from 
[http://www.vlsys.co.kr](http://www.vlsys.co.kr) like mine just with vfd, so my mod to the mplay driver from lirc could work at least for the remote part.

---

### Post by MacUsers on 2010-10-10
> **justme123 said:**
> ... OEM device from [http://www.vlsys.co.kr](http://www.vlsys.co.kr) like mine just with vfd, so my mod to the mplay driver from lirc could work at least for the remote part.For last 2 days, I'm trying to open vlsys.co.kr but no joy yet; being timed out all the time. Do you see the same thing as well? Cheers!!

---

### Post by justme123 on 2010-10-10
no the site works for me, slooooooow but it works
but u don't get any infos or something there anywas all in all for the Moncaso
so not really a problem

---

### Post by MacUsers on 2010-10-10
Hi JustMe, 
Just trying your way..... couple of questions:
> **justme123 said:**
> 4. compile lirc and use the mplay driver and as remote device REMOTE_DEVICE="/dev/ttyUSB0How to use the mplay drive? Do you mean ***REMOTE_DRIVER="mplay"*** in the hardware.conf? Can you post your hardware.conf please?
> **justme123 said:**
> 5. you can use as template remote the VLSystem MPlay Blast it's pretty much the same remote lirc ours only the gap is a little bit different and a few buttons it seems.
What exactly does it mean? Also, where can I get the the VLSystem MPlay template?
> **justme123 said:**
> 6. Don't forget to change the Lircmap.xml and add either your own recorded remote or the VLSystem if that works also Can I have a look in your  Lircmap.xml as well please (as you've already guessed, why!!). 
Sorry for my silly questions and thanks a lot for giving us "hope". Cheers!!

---

### Post by MacUsers on 2010-10-11
> **MacUsers said:**
> How to use the mplay drive? Do you mean ***REMOTE_DRIVER="mplay"*** in the hardware.conf?Just ignore this question: I've figured that out what you mean. When installed from binary, there isn't any hardware.conf - is it? Cheers!!

---

### Post by justme123 on 2010-10-11
hm hehe honestly i dunno anymore if there is a hardware.conf auto generated or not.
Anyways this is the one i actually use ...
REMOTE="Moncaso_312" is bascially nearly a clone of the existing mplay remote template u'll find that here in the lirc dir \remotes\vlsystem\lircd.conf.mplay

Since u don't have that use as remote instead  VLSystem_MPlay_Blast like i mentioned before just a few buttons are different (maybe more on your moncaso 320) and the gap.

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control

REMOTE="Moncaso_312"            
REMOTE_MODULES=""                        
REMOTE_DRIVER="mplay"                    
REMOTE_DEVICE="/dev/ttyUSB0"             
REMOTE_LIRCD_CONF=""                     
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
```> What exactly does it mean? Also, where can I get the the VLSystem MPlay template?Honestly said i have no clue !!!!! :P i noticed it only after comparing my own recorderd template and the VLSystem MPlay. VlSystem Mplay template is in lirc dir here \remotes\vlsystem\lircd.conf.mplay


> Can I have a look in your  Lircmap.xml as well please (as you've already guessed, why!!). 
Sorry for my silly questions and thanks a lot for giving us "hope". Cheers!!     sure here it is (i called my Template Moncaso_312 use whatever never name u want just make sure it's the same name you use everywhere, the rest of the Lircmap.xml is unchanged i just pasted it under the exisiting <remote device="mceusb"> section.

```
<remote device="Moncaso_312">
        <play>Play</play>
        <pause>Pause</pause>
        <stop>Stop</stop>
        <forward>FF</forward>
        <reverse>Rew</reverse>
        <left>Left</left>
        <right>Right</right>
        <up>Up</up>
        <down>Down</down>
        <select>OK</select>
        <pageplus>Ch+</pageplus>
        <pageminus>Ch-</pageminus>
        <back>Back</back>
        <menu>Menu</menu>
        <title>Hotkey</title>
        <info>More</info>
        <skipplus>Next</skipplus>
        <skipminus>Prev</skipminus>
        <display>Aspect</display>
        <start>Home</start>
        <record>Record</record>
        <volumeplus>Vol+</volumeplus>
        <volumeminus>Vol-</volumeminus>
        <mute>Mute</mute>
        <power>PwrOn</power>
        <myvideo>Movie</myvideo>
        <mymusic>Music</mymusic>
        <mypictures>Photo</mypictures>
        <mytv>TV</mytv>
        <one>1</one>
        <two>2</two>
        <three>3</three>
        <four>4</four>
        <five>5</five>
        <six>6</six>
        <seven>7</seven>
        <eight>8</eight>
        <nine>9</nine>
        <zero>0</zero>
    </remote>
```ah anyways i include now also my template for the remote

```

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.7(mplay) on Mon Sep 20 12:12:30 2010
#
# contributed by 
#
# brand:    Monueal Moncaso 312 "new Remote"
# model no. of remote control:  VL System OEM
# devices being controlled by this remote:
#

begin remote

  name  Moncaso_312
  bits            8
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          107899
  toggle_bit_mask 0x0

      begin codes
          PwrOff                   0x41
          PwrOn                    0x55
          Hotkey                   0x5A
          DVD                      0x14
          Menu                     0x5C
          Sleep                    0x58
          Rec                      0x11
          Play                     0x09
          Eject                    0x5E
          Rew                      0x0D
          Pause                    0x05
          FF                       0x15
          Prev                     0x1A
          Stop                     0x01
          Next                     0x1E
          Full_Screen              0x0C
          Ratio                    0x10
          Task_Switcher            0x17
          Movie                    0x40
          Music                    0x56
          Photo                    0x45
          TV                       0x46
          OK                       0x42
          Up                       0x19
          Left                     0x54
          Right                    0x43
          Down                     0x1D
          Back                     0x0B
          Exit                     0x1F
          Mute                     0x4A
          More                     0x4B
          Open                     0x04
          Vol+                     0x0A
          Vol-                     0x0E
          CH+                      0x12
          CH-                      0x16
          1                        0x4D
          2                        0x4E
          3                        0x4F
          4                        0x50
          5                        0x51
          6                        0x52
          7                        0x53
          8                        0x03
          9                        0x07
          0                        0x4C
          Quick_Guide              0x08
          Timer                    0x18
      end codes

end remote
```

---

### Post by MacUsers on 2010-10-11
> **justme123 said:**
> ah anyways i include now also my template for the remote This is the lircd.conf, right? So, did you have to manually create the "/etc/lirc" directory to put hardware.conf and the lirc.conf in it? Cheers!!

---

### Post by justme123 on 2010-10-11
ahhhh oki now i got your problem there.
I used the existing entries i still had from a normal lirc installation before via apt-get install lirc but since i was forced to modify the driver i uninstalled lirc again but the dir and the scripts didn't get deleted i think

yep it is basically my lirc.conf, also i made a extra file for it and copied  to /usr/share/lirc/remotes/vlsystem/lircd.conf.monc312"
so my lirc.conf is now include "/usr/share/lirc/remotes/vlsystem/lircd.conf.monc312" but that's just a personal taste i think

i think this also should work (also not sure it's needed or 100% correct)

install lirc the "normal" way if u didn't have that already before via apt-get install, get the sources and modify the mplay driver and so on ...
at this point i'm not sure (linux newbie) the first "normal" lirc installation puts everything into /usr/sbin while after u did your own compilation of lirc everything goes into /usr/local/sbin what is now first loaded here ....
now modify the existing /etc/init.d/lirc you should have from the normal installation and exchange every /usr/sbin/ to /usr/local/sbin/ and also
/usr/bin/ to /usr/local/bin/, you can probably copy also everything u compiled before to /usr/sbin and /usr/bin and leave the /etc/init.d/lirc untouched.

does that makes still sense here for you ?

---

### Post by MacUsers on 2010-10-11
> **justme123 said:**
> yep it is basically my lirc.conf, also i made a  extra file for it and copied  to  /usr/share/lirc/remotes/vlsystem/lircd.conf.monc312"
so my lirc.conf is now include  "/usr/share/lirc/remotes/vlsystem/lircd.conf.monc312" but that's just a  personal taste i thinkThat's the original way of doing it. I'm  do the same thing as well.
> **justme123 said:**
> you can probably  copy also everything u compiled before to /usr/sbin and /usr/bin and  leave the /etc/init.d/lirc untouched.I wouldn't do that. I'd  rather create/modify the init.d start-up script.  
> **justme123 said:**
> does that makes still sense here for you  ?Yes, pretty much, cuz it's working now. At least I can see the  stdout data pressing the remote button. BTW, did you ever tried the mplay  driver with the standard apt-get installed lirc? I didn't but interested  to know the result. 

Another question: Do you have code for the Eject button? This is the remote I'm using:

[IMG]http://farm5.static.flickr.com/4132/5073176546_53cbff2bc9_z.jpg[/IMG]

Is it the same as yours? Cheers!!

---

### Post by justme123 on 2010-10-12
you should be able ofc also to reccord every button you need by yourself now with irrecord

> Yes, pretty much, cuz it's working now. At least I can see the  stdout  data pressing the remote button. BTW, did you ever tried the mplay   driver with the standard apt-get installed lirc? I didn't but interested   to know the result.  yep i tried every combination that i could imagine like the Thread Starter here also, it failed.
I was never able to recieve any keypress from the remote.


> Another question: Do you have code for the Eject button? This is the remote I'm using:According to my config file the ejject button should be:  Ejject 0x5e
but i personally never used it in xbmc so far. Yep looks like you have the same remote, at least mine looks pretty much like yours.

So all in all your remote is working now also ?

---

### Post by MacUsers on 2010-10-12
> **justme123 said:**
> So all in all your remote is working now also ?YES - in the first place, NO - as soon as I install LCDproc for the VFD. I'm no clue why this is happening. Others seem to get it working on other machines e.g. Zalman HD135, seems to be using the same VLSys display. :mad: Cheers!!

---

### Post by MacUsers on 2010-10-12
> **justme123 said:**
> you should be able ofc also to reccord every button you need by yourself now with irrecordYes! I totally forgot about that; I'm getting old. BTW, I rerecorded all the keys, and that's what I have now. Posting here for future reference and/or if anyone else finds it's helpful.
(***Note:*** I didn't able to record the REC key - it's coming as [COLOR=Blue]0x42[/COLOR], which is actually OK key)
```
begin codes
        Power                   0x41
        MediaCenter             0x55

        HotKey                  0x5A
        DVD                     0x14
        Menu                    0x5C
        Sleep                   0x58

        [COLOR=Gray]Rec                     0x00[/COLOR]
        Play                    0x09
        Eject                   0x5E
        Rew                     0x0D
        Pause                   0x05
        FFwd                    0x15
        Prev                    0x1A
        Stop                    0x01
        Next                    0x1E

        FullScreen              0x0C
        AspectRatio             0x10
        SwitchTask              0x17

        Movie                   0x40
        Music                   0x56
        Photos                  0x45
        TV                      0x46

        Up                      0x19
        Down                    0x1D
        OK                      0x42
        Left                    0x54
        Right                   0x43

        Back                    0x0B
        Exit                    0x1F
        Mute                    0x4A
        Info                    0x4B
        Open                    0x04

        Vol+                    0x0A
        Vol-                    0x0E
        Ch+                     0x12
        Ch-                     0x16

        1                       0x4D
        2                       0x4E
        3                       0x4F
        4                       0x50
        5                       0x51
        6                       0x52
        7                       0x53
        8                       0x03
        9                       0x07
        0                       0x4C
        Guide                   0x08
        Timer                   0x18
end codes
```I yet to figure out why LCDproc and LIRC doesn't  like each other at all. Cheers!!

---

### Post by justme123 on 2010-10-13
> e.g. Zalman HD135, seems to be using the same VLSys display.
 nope i don't think this is the same, especially i was never able to get any result from baudrates with 38400. so maybe check the hd44780-mplay.c driver there and try instead of 38400 57600 as baudrate for lcdproc but all in all i can't help you much with lcdproc sorry. 

> Yes! I totally forgot about that; I'm getting old. BTW, I rerecorded all  the keys, and that's what I have now. Posting here for future reference  and/or if anyone else finds it's helpful.
(***Note:*** I didn't able to record the REC key - it's coming as [COLOR=Blue]0x42[/COLOR], which is actually OK key)

ok your keys look so exactly like mine i posted already on site 3 of this thread as lirc ready template. The rec button is 0x11.:P

---

### Post by MacUsers on 2010-10-13
> **justme123 said:**
> nope i don't think this is the same, especially i was never able to get any result from baudrates with 38400. so maybe check the hd44780-mplay.c driver there and try instead of 38400 57600 as baudrate for lcdproc but all in all i can't help you much with lcdproc sorry.Don't worry about it, at least I have the remote working, thanks to you. I found [this post ]("http://forum.xbmc.org/showthread.php?t=45924")in the XBMC forum and followed the instruction, but no joy yet. I also tried 57600, which gave me slightly better result - with 38400, the screen goes completely blank and remote stops working as well but with 57600, remote stays operational and I see the default MONEUAL on the screen. Just one thing, if I use ***LCDd -f -r 5 -s 0***, I get screen full of these:[INDENT][I]screenlist_process()
screenlist_switch(s=[_server_screen])[/I]
[/INDENT]```
Server running in foreground
Listening for queries on 127.0.0.1:13666
screenlist_init()
driver_load(name="hd44780", filename="/usr/lib64/lcdproc/hd44780.so")
HD44780: using ConnectionType: mplay
HD44780: Matrix key 3 0: "Enter"
HD44780: Matrix key 3 1: "Up"
HD44780: Matrix key 3 2: "Down"
HD44780: Matrix key 3 3: "Escape"
hd44780: Using hd44780_default charmap
HD44780: lis2: Using device: /dev/ttyUSB0
HD44780: lis2: using speed: 57600
Key "Escape" is now reserved exclusively by client [-1]
Key "Enter" is now reserved shared by client [-1]
Key "Up" is now reserved shared by client [-1]
Key "Down" is now reserved shared by client [-1]
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_switch: switched to screen [_server_screen]
screenlist_process()
screenlist_process()
screenlist_process()
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_process()
screenlist_switch(s=[_server_screen])
```Do you have any idea what is this?

> **justme123 said:**
> ok your keys look so exactly like mine i posted already on site 3 of this thread as lirc ready template. The rec button is 0x11.:P
Unfortunately, 0x11 doesn't seem to be working  - I don't get any thing on the irw screen pressing Rec button. Again, I really don't really have any use for that button but it's good to know. Cheers!!

---

### Post by justme123 on 2010-10-13
> Unfortunately, 0x11 doesn't seem to be working  - I don't get any thing  on the irw screen pressing Rec button. Again, I really don't really have  any use for that button but it's good to know. Cheers!! 	 hm that's pretty odd no clue why that's happening especially since every other button works

> 
Do you have any idea what is this? uhm nope never used lcdproc, i have absolutly no idea about it or how to use it, sorry

u might play also a little bit around with the termios structure in the mplay driver of lcdproc
and / or set some more "debug" infos here and than to gain some more infos.
But all in all i'm just shooting in the dark without the same hardware.

---

### Post by MacUsers on 2010-10-17
Discovered another thing: if LCDproc is running, remote stops working after walking up from sleep. Another thing in the list to fix. Cheers!!

---

### Post by justme123 on 2010-10-17
yep have seen your post @ xbmc forum
but this can be probably only get fixed if you analyse what's happening on the serial port
it might be that actually lcdproc kills somehow lirc.

The only advice i can give you kinda is try to monitor under windows what's going on when you start the mplay software.

Just in case u tried maybe also the lirc driver from lcdproc (now idea how that works there) i saw at one line 
that it switches to nonblock ...

/* socket shouldn't block lcdd */
    if (fcntl(p->lircin_fd, F_SETFL, O_NONBLOCK) < 0){

when i was trying to get the remote working with lirc, this used to be also a problem at least from what i remember.

---

### Post by justme123 on 2010-10-19
btw it looks like you used the lis2 driver from lcdproc

> [FONT=monospace]hd44780: Using hd44780_default charmap
HD44780: lis2: Using device: /dev/ttyUSB0
HD44780: lis2: using speed: 57600[/FONT]

maybe try also the mplay driver, actually i can't access anymore the vlsystems website
but i think this might be closer to your device

---

### Post by jackhill99 on 2011-02-18
justme123, you legend! Followed your instructions and finally got the remote working on my 320 case. Many thanks for posting all your config and source changes.

I do have one slight problem though with the first boot which I'm trying to identify. I boot up into XBMC and the remote works for about 6 or 7 key presses before freezing. Restarting lirc fixes the problem until I reboot so I would like to know if I missed something when setting it up and if there is a way to fix this permanently?

I first installed lirc, compiled the source with your changes to mplay, apt-get removed lirc, then copied all the generated lirc binaries over to /usr/bin and /usr/sbin. 

I don't have lcdproc installed so was wondering if there is anything else I should check?

Thanks again


EDIT - Some more info to add. When it freezes I run irw and the right directional button registers so lirc is still up. I've tried disabling auto booting into XBMC but that has no affect. When booting into Ubuntu, I have about 5 seconds of remote time before it stops processing the majority of the commands. I also lost the ability to power down my pc using the remote after compiling lirc.

Hopefully someone has a fix for me. 

Thanks

---

### Post by justme123 on 2011-02-27
Hi jackhill99,

uhm sorry nope no real idea what can cause this that it stops working never hat that problem so far myself. Maybe enable the debug logging and have a look what's happening there (or post it here), i have only the 312 case so can't test it. But i have to admit that i currently have some odd problem myself here with the newer kernel Versions. The rewind button ain't working anymore in xbmc also every other button works like it should do.

Actually you can use btw lirc 0.9.0pre1 and newer versions without my "hack" of the old driver. A "new" not really documented driver called "mplay2" is there now included. So u don't need to uninstall any exisiting version of lirc or anything else, except that u need to modify in /etc/init.d/lirc to point to your user modules after compile.

To use the driver u need to *use ./configure --with-driver=mplay2* if you compile lirc from sources and use in hardware.conf REMOTE_DRIVER="mplay2"

---

### Post by jackhill99 on 2011-02-28
> **justme123 said:**
> Hi jackhill99,

uhm sorry nope no real idea what can cause this that it stops working never hat that problem so far myself. Maybe enable the debug logging and have a look what's happening there (or post it here), i have only the 312 case so can't test it. But i have to admit that i currently have some odd problem myself here with the newer kernel Versions. The rewind button ain't working anymore in xbmc also every other button works like it should do.

Actually you can use btw lirc 0.9.0pre1 and newer versions without my "hack" of the old driver. A "new" not really documented driver called "mplay2" is there now included. So u don't need to uninstall any exisiting version of lirc or anything else, except that u need to modify in /etc/init.d/lirc to point to your user modules after compile.

To use the driver u need to *use ./configure --with-driver=mplay2* if you compile lirc from sources and use in hardware.conf REMOTE_DRIVER="mplay2"

Thanks for the reply. I've actually give up on Linux until these problems are addressed. Spent way too many nights trying to get everything working in harmony and eventually went the Windows 7 route. I did want to build a Media PVR but will wait now until the plugins mature a bit. I might try that new lirc build on a thumb drive installation.

Thanks again

---

### Post by ikus060 on 2011-05-29
In an effort to make it easier to understand how to setup Ubuntu with MonCaso 312 and others. I created a wiki page : [https://wiki.ubuntu.com/Lirc/MonCaso312](https://wiki.ubuntu.com/Lirc/MonCaso312)

I invites anyone to improve this wiki.

---

### Post by justme123 on 2011-06-03
Hi ikus060,

there is a little typo in ur wiki the driver is called 
DRIVER="mplay2" and not DRIVER="mplay"

but except that everything looks fine and thx for putting it together
in a short and simple form :D

---

### Post by rleibman on 2011-06-10
ikus060... you are awesome, the wiki you put together is simple and well written. It works... almost.
I followed your steps, and up to the point where I use irw everything is fine, I get a bunch of messages as I press keys in the remote control.
However mythtv does not seem to know anything about the remote control and it doesn't work, I imagine I have to enable something in mythtv in order for it to work. Before installing the 0.9 version of lirc I used to get a list of available remotes in the Mythbuntu Control Centre, but they are no longer there.

Thanks,

Roberto

---

### Post by rleibman on 2011-06-10
Anwsering myself... 
Yeah, the list of controls is no longer available. However I managed to get the control working with mythbuntu by running
mythbuntu-lirc-generator

Thanks again!

Roberto

---

### Post by Tumke29 on 2011-06-25
> **justme123 said:**
> Hi ikus060,

there is a little typo in ur wiki the driver is called 
DRIVER="mplay2" and not DRIVER="mplay"

but except that everything looks fine and thx for putting it together
in a short and simple form :D

Hey Justme,

thanks that you give us the solution to this mplay problem in ubuntu. But i'm still struggeling to get this thing to work. I really hope you can help me.

I'm using Linux XBMCLive 2.6.32-26-generic Ubuntu 10.04.1 LTS - XBMCLive Dharma and i had Lirc 0.8 running. Because of the new mplay2 driver i followed the wiki and try to install Lirc 0.9.0. But i cant install it. Can you please describe me step by step how to install / compile ? lirc 0.9.0 on my system by terminal? 

i tried this:

wget [http://ftp.de.debian.org/debian/pool/main/l/lirc/lirc_0.9.0~pre1.orig.tar.bz2](http://ftp.de.debian.org/debian/pool/main/l/lirc/lirc_0.9.0~pre1.orig.tar.bz2)

than xbmc downloads the file in the /home/xbmc folder

Whats next? 

Thanks,  Tom

---

### Post by justme123 on 2011-07-04
Hi Tumke29,

sorry for the late reply i assume you didn't try to compile it so far ?
Not sure what version that is there but i assume it's the same like the one from [www.lirc.org]("http://www.lirc.org") otherwise grab the one from [www.lirc.org]("http://www.lirc.org").

First step would be to extract the packed file.

So use tar -jxvf lirc_0.9.0~pre1.orig.tar.bz2 to extract all the file and than you can follow the steps in wiki that ikus060 put togeather from this thread here.

Maybe you need to add some extra files to your xbmc setup, lirc needs them if you want to compile it.

*sudo apt-get install libtool automake autoconf dialog*

1. change to the lirc dir
2. *./autogen.sh *
3. [I]./configure --with-driver=mplay2
4. [/I][I]make && make install

As long as you didn't remove your old lirc version you just need now to change the paths in [/I]/etc/init.d/lirc
from /usr/sbin to /usr/local/sbin/ and also /usr/bin to /usr/local/bin

If you still have problems feel free to ask.

Ah one thing i missed you need to change also the Lircmap.xml

---

### Post by richardss2 on 2011-08-05
Hi All, I've got a VFD & remote that I'm 95% sure to be the same as the one in the MonCaso 320 case. 

I've followed the excellent information/guidance in this thread and have the remote working - thank you all for this.

The remote stops working when waking from suspend (irw also reports nothing, and restarting LIRC does not help). This occurs with and without LIRCproc installed. The bottom of this page offers a solution which has not worked for me: **[http://wiki.xbmc.org/index.php?title=Ubuntu_Suspend_/_Wake](http://wiki.xbmc.org/index.php?title=Ubuntu_Suspend_/_Wake)**

I'm also having no luck with the VFD either - the best I have achieved on the this is a series of garbled characters. This is after following the instructions at the start of this thread: **[http://forum.xbmc.org/showthread.php?t=45924](http://forum.xbmc.org/showthread.php?t=45924)** (I am pretty sure this is a slightly different VDF however). I tried this with both the patched 0.5.2 and the new 0.5.4 (which apparently does not need patching).

Has anyone got any pointers on either of these problems?

Many thanks, 
Richard

---

### Post by justme123 on 2011-08-06
Hi richardss2,

nope sorry, i personally own only a moncaso 312 so i would just shoot in the dark ... like i did with the moncaso 320 in this thread

---

### Post by cyber7 on 2011-08-21
@justme123
Hi guys
After leaving this box for quite a while I have decided to get it back up-and-running.  I have followed all the posts, mostly from justme123 and have the remote up and running in linux.

My setup is:
Moneual MonCaso 312 with XBMC10.1-live loaded.

My dilemma:
1. In linux I can see the remote and pressing buttons gives me info.
2. In XBMC, nothing.  The remote does not work.

I have got an idea this is becuase of some mapping that is suppose to happen...

What I have done so far:
1. Installed XBMC FRESH.
2. apt-get update
3. wget [http://ftp.de.debian.org/debian/pool/main/l/lirc/lirc_0.9.0~pre1.orig.tar.bz2](http://ftp.de.debian.org/debian/pool/main/l/lirc/lirc_0.9.0~pre1.orig.tar.bz2)
4. tar -jxvf lirc_0.9.0~pre1.orig.tar.bz2
5. apt-get install libtool automake autoconf dialog
6. ./configure --with-driver=mplay2
7. make && make install
8. Changed the paths in /etc/init.d/lirc (from /usr/ to /usr/local/)
9. Changed /etc/lirc/hardware.conf to have ONLY:
```

    REMOTE_DRIVER="mplay2"
    REMOTE_DEVICE="/dev/ttyUSB0"

```

If I then reboot the machine and open a ssh console and run irw, I get the keystrokes!
<yahoo!!! at this stage!!!>

Added the following keymap to the Lircmap.xml file an WALLA - everything works.
```

<remote device="Moncaso_312">
        <play>Play</play>
        <pause>Pause</pause>
        <stop>Stop</stop>
        <forward>FF</forward>
        <reverse>Rew</reverse>
        <left>Left</left>
        <right>Right</right>
        <up>Up</up>
        <down>Down</down>
        <select>OK</select>
        <pageplus>Ch+</pageplus>
        <pageminus>Ch-</pageminus>
        <back>Back</back>
        <menu>Menu</menu>
        <title>Hotkey</title>
        <info>More</info>
        <skipplus>Next</skipplus>
        <skipminus>Prev</skipminus>
        <display>Aspect</display>
        <start>Home</start>
        <record>Record</record>
        <volumeplus>Vol+</volumeplus>
        <volumeminus>Vol-</volumeminus>
        <mute>Mute</mute>
        <power>PwrOn</power>
        <myvideo>Movie</myvideo>
        <mymusic>Music</mymusic>
        <mypictures>Photo</mypictures>
        <mytv>TV</mytv>
        <one>1</one>
        <two>2</two>
        <three>3</three>
        <four>4</four>
        <five>5</five>
        <six>6</six>
        <seven>7</seven>
        <eight>8</eight>
        <nine>9</nine>
        <zero>0</zero>
    </remote>

```
Thank you everyone and you can use these instructions.  They work 100%!

Kind regards
Aubrey

---

### Post by womiha on 2011-09-12
This thread has been extremely helpful, thanx to all contributors, particularly to justme123. I got [LIRC]("http://www.lirc.org/") working with MonCaso 320. This would have been impossible without the hints in this thread.

For me, two points were unresolved:

[LIST]
[*]The record key did not work. This is caused by some kind of misconfiguration of the serial device.
[*]There was no control possibility for the display.
[/LIST]
So I have spent some leisure time on the MonCaso 320 IR/VFD combination. I have an alternative implementation of the mplay-driver of the LIRC package, and I have developed an [LCDproc]("http://lcdproc.org/") driver.

First, for LIRC, I have replaced the function "mplay2_init" in LIRC 0.9.0-pre1 by:
```

/* Mplay2 serial baud rate */
#define MPLAY2_BAUD_RATE 57600

/* Mplay2 initialisation character sent to device */
#define MPLAY2_INIT_CHAR 0x96

/* Mplay2 initialisation length of response to intialisation character */
#define MPLAY2_INIT_RESPONSE_LENGTH 11

/**************************************************************************
 * Sends initialisation character to  Moncaso 312/320 IR device
 * (helper function for mplay2_init).
 * Return 1 on success, 0 on error.
 **************************************************************************/
static int mplay2_send_init_char(void)
{
    const char init = MPLAY2_INIT_CHAR;

    if (write(hw.fd, &init, 1) < 0) {
        return 0;
    } else {
        return 1;
    }
}

/**************************************************************************
 * Retrieves initialisation response from Moncaso 312/320 IR device
 * (helper function for mplay2_init).
 * Moncaso 320 returns ".M428.M428.".
 * Return 1 on success, 0 on error.
 **************************************************************************/
static int mplay2_retrieve_init_response(void)
{
    int i;
    char response[MPLAY2_INIT_RESPONSE_LENGTH + 1]; /* contains string terminating zero */

    /* Reset response buffer */
    memset(response, 0, sizeof(response));

    /* Read-function blocks until characters arrive from serial device */
    fcntl(hw.fd, F_SETFL, 0);
    /* Get response to initialisation character */
    for (i = 0; i < MPLAY2_INIT_RESPONSE_LENGTH; i++) {
        /* Get next character (blocks until arrival in order to avoid polling) */
        if (read(hw.fd, &response[i], 1) < 0) {
            return 0;
        }
    }
    /* restore non-blocking behaviour */
    fcntl(hw.fd, F_SETFL, FNDELAY);
    LOGPRINTF(1, "Device initialisation response: %s", response);

    return 1;
}

/**************************************************************************
 * Locks and initialises the serial port, Moncaso 312/320 variant.
 * This function is called by the LIRC daemon when the first client
 * registers itself.
 * Return 1 on success, 0 on error.
 **************************************************************************/
int mplay2_init(void)
{
    int result = 1;

    LOGPRINTF(1, "Entering mplay_init()");

    /* Creation of a lock file for the port */
    if (!tty_create_lock(hw.device)) {
        logprintf(LOG_ERR, "Could not create the lock file");
        result = 0;
    }
    /* Try to open serial port */
    else if ((hw.fd = open(hw.device, O_RDWR | O_NONBLOCK | O_NOCTTY)) < 0) {
        logprintf(LOG_ERR, "Could not open the serial port");
        result =  0;
    }
    /* Serial port configuration */
    else if (!tty_reset(hw.fd) || !tty_setbaud(hw.fd, MPLAY2_BAUD_RATE)) {
        logprintf(LOG_ERR, "Could not configure the serial port for '%s'", hw.device);
        result = 0;
    }
    /* Send initialisation character to device and retrieve response */
    else if (mplay2_send_init_char() == 0 || mplay2_retrieve_init_response() == 0) {
        logprintf(LOG_ERR, "Could not initialise device");
        result = 0;
    }

    /* Clean up if an error has occured */
    if (result == 0) {
        logperror(LOG_ERR, "mplay2_init()");
        mplay_deinit();
    }

    return result;
}

```Is anybody out there who could verify this change with MonCaso 312 or 320? If the modification works I would propose to submit the change to the LIRC developers.

@justme123: Do you have any hints how to contact LIRC developers best? I would also like to submit the LIRC configuration file.

Second for, for LCDproc I am going to submit a patch to the LCDproc developers (also attached here as vlsys_m428.patch.gz).

Both LIRC and LCDproc work quite well together.

For LCDproc, I have written some scripts for a VDR (video recorder) setup basing upon [yaVDR]("http://www.yavdr.org/"):

[LIST]
[*]The knob toggles the display (switch on/off, which is a bit tricky as there seems to be no bounce protection).
[*]The LCDproc displays three screens in turn:
[LIST]
[*]The television show title of the current or next timer to be recorded
[*]The schedule of the current or next timer
[*]The current date and time
[/LIST]

 
[/LIST]
So, I have been using IR and VFD in parallel sucessfully quite for a while.


If you need some more details, have some questions, or want some binaries: you are welcome!

On the other hand: If anybody happens to have some more knowledge on technical manuals about the IR (MonCaso 312) or IR/VFD (MonCaso 320): please let me know!

---

### Post by womiha on 2011-09-12
@richardss2:

The problem with the stand-by and wake-up seems to be a bug in the ftdi_sio driver or in the kernel. The serial device is mapped to another path name. Before stand-by, e.g., it is found at /dev/ttyUSB0, after wake-up it is found at /dev/ttyUSB1. Consequently, a restart of LIRC does not help as it does not find the device anymore.

A work-around is possible by unloading and reloading the driver by the command "modprobe".

---

### Post by justme123 on 2011-09-17
Hi womiha,

usually the best way to submit your patch would be i think to send it to the lirc-list.
link @ sourceforge here [http://sourceforge.net/mailarchive/forum.php?forum_name=lirc-list](http://sourceforge.net/mailarchive/forum.php?forum_name=lirc-list) at least that was what i did.

---

### Post by womiha on 2011-09-20
justme123, thank you for your reply. I am going to submit the change to the lirc mailing list.

By the way, now I know why the rec button did not work in the previous setup. It was interpreted as flow character 0x11 (XON) and therefore ignored.

And finally, the work on the lcdproc driver is going on, patches have been submitted.

---

### Post by justme123 on 2011-09-21
hm not sure if i understood u right but hope so ... u couldn't record the keypress for the
record button with lirc ?

---

### Post by womiha on 2011-09-21
Correct, the record button was out of order. Pressing this button produces 0x11. 

Searching around the net reveals other users having the same problem (also in the beginning of this thread), but assuming other values for the record button. Those values arose from previous button presses.

---

### Post by justme123 on 2011-09-22
hm odd that button was no problem for me to record ... but from one day to another the rwd button stopped working (at least i think it was that one from rememberence).
Actually i'm not sure since i was to lazy to check if it was a hw issue or not) but i think i happened after a update one day and just remapped that button to fast rwd.

---

### Post by womiha on 2011-10-23
Meanwhile, I have implemented a driver supporting the MonCaso 312/320 wheel, and working reliably with the record button.

The IR device reports the angle of the knob in a Gray code, which is monitored by a polling thread. The Gray code is hidden in two status lines of the serial port. More information is given in the source code in the attached patch.

Specifying the option "nowheel" after the driver as in [FONT=Courier New]DRIVER="/dev/ttyUSB0,nowheel" [/FONT]or[FONT=Courier New] --driver="/dev/ttyUSB0,nowheel"[/FONT] prevents the driver from creating a polling thread. Then, the driver just creates a file descriptor, where the LIRC framework reads from. This is the behaviour of the currently delivered driver.

The driver returns the additional codes 0x80 (counter clockwise, "left") and 0x81 (clockwise, "right"), the code 0x82 (knob pressed) was already present. See attached LIRC configuration file.

I am going to submit this patch to LIRC, but I would like to read some feedback here.

---

### Post by justme123 on 2011-10-26
womiha did u use a fresh install of the 0.9er lirc or was it already somehow modified by u ?
Actually i get only a bunch of errors when i try to apply your patch :confused:

Hunk #1 FAILED at 467.
Hunk #2 FAILED at 638.
Hunk #3 FAILED at 1189.
Hunk #4 FAILED at 1196.
Hunk #5 FAILED at 1669.
5 out of 5 hunks FAILED -- saving rejects to file configure.ac.rej
patching file daemons/hw_mplay.c
Hunk #1 FAILED at 17.
Hunk #2 FAILED at 61.
Hunk #3 FAILED at 72.
Hunk #4 FAILED at 104.
Hunk #5 FAILED at 119.
Hunk #6 FAILED at 131.
Hunk #7 FAILED at 141.
Hunk #8 FAILED at 301.
Hunk #9 FAILED at 366.
9 out of 9 hunks FAILED -- saving rejects to file daemons/hw_mplay.c.rej
patching file daemons/hw_mplay.h
Hunk #1 FAILED at 27.

---

### Post by womiha on 2011-10-27
Well, I got [http://sourceforge.net/projects/lirc/files/LIRC/0.9.0/lirc-0.9.0.tar.bz2/download](http://sourceforge.net/projects/lirc/files/LIRC/0.9.0/lirc-0.9.0.tar.bz2/download), extracted it to a folder, changed into this folder with [FONT=Courier New]cd[/FONT] and applied the patch with [FONT=Courier New]patch -p1 < /path/to/lirc.0.9.0.patch[/FONT]. The patch was correctly applied, and binaries could be built.

---

### Post by justme123 on 2011-10-28
hm not sure what went wrong, patch works now ...
so far seems everything still works like before with my 312er ... still wakes up after shutdown and buttons are still working

i see my hint @ lirc list regarding the wheel did help u kinda ;)

---

### Post by womiha on 2011-10-28
> **justme123 said:**
> so far seems everything still works like before with my 312er ... still wakes up after shutdown and buttons are still working

Thanks for the feedback, this gives a little more confidence.

> **justme123 said:**
> i see my hint @ lirc list regarding the wheel did help u kinda ;)

Yes, it was a very good hint :D


By the way, I replaced the patch in the post, there was little bug and a mismatch with logging levels. Looked many times at the code, and now, today, the first look, ... #-o

---

### Post by fritz222 on 2011-12-12
Hi guys

I tried this on my Ubuntu 11.10 and it didn't worked. I have no hardware.conf and I have no /etc/init.d/lirc.

This is what the  ./configure --with-driver=mplay2 command gave back:
[http://pastebin.com/qpYD23ET](http://pastebin.com/qpYD23ET)


What I've done till now:
- I created the missing files manually with the content from this tutorial. (See post #57)
- IRW gives this back:```
xbmc@htpc:~/lirc-0.9.0-pre1$ irw
connect: Connection refused
xbmc@htpc:~/lirc-0.9.0-pre1$ sudo irw
connect: Connection refused
xbmc@htpc:~/lirc-0.9.0-pre1$

```

- When I run this command: 
```
sudo apt-get install lirc lirc-x liblircclient0 inputlirc 
```

I see the points when I run:```
sudo irrecord -H mplay2 -d /dev/ttyUSB0 ~/test
```

I do see the dots and I can execute irw but irw doesnt rects on my remote.

Can somebody help me get that run in Ubuntu 11.10?
Thank you very much!
fritz222

---

### Post by justme123 on 2011-12-13
HI fritz222,

just from memory i think irw was never working with the driver and the device but i might be wrong here ... easiest way to get the missing hardware.conf file and /etc/init.d/lirc is the way to did already sudo apt-get install lirc ... you should have now the files you need or am i wrong ? Ubuntu 10.10 (personally don't have it) seems to use already the 0.9.0 Lirc Version so no need to compile it yourself (except you want/need womiha's modifications for the moncaso 320 i think so far they're not added, might be also wrong here) than you need to compile his sources.

You need to change at least your hardware.conf and lircd.conf (check post 44) but be aware that there is a typo in the wiki the driver is called mplay2 NOT mplay

For what device do you need your lirc version Moncaso 312 or 320 ? 

Greetings 
justme

---

### Post by fritz222 on 2011-12-13
Now I got IRW running. I just had to do /etc/init.d/lirc restart.

But now I got 2 problems left:

1. I have to do /etc/init.d/lirc restart everytime when I reboot. How can I make it start automatically on bootup?

2. It doesn't anything in XBMC although I added the stuff in Lircmap.xml from post 52.

Does anybody has an idea?

Thank you very much for helping me.
fritz222

P.S I got a Moncaso 312.

---

### Post by justme123 on 2011-12-14
Hm that it doesn't auto start is pretty odd ... could you post the log files ?
What version do you use now the custom compiled one or the one you got via apt-get ?

Did you create the remote template for the moncaso (see post 28) otherwise it ain't working or just put the remote codes into /etc/lirc/lircd.conf  like mentioned at the wiki ?

---

### Post by fritz222 on 2011-12-14
Do you mean  /var/log/lircd with log file? (As you may have guessed I'm a Linux noob)
```
Dec 13 20:26:36 htpc lircd: lircd(mplay2) ready, using /var/run/lirc/lircd
Dec 13 20:29:26 htpc lircd: caught signal
Dec 13 20:29:26 htpc lircd: lircd(mplay2) ready, using /var/run/lirc/lircd
Dec 13 20:31:11 htpc lircd: accepted new client on /var/run/lirc/lircd
Dec 13 20:31:23 htpc lircd: removed client
Dec 13 20:40:30 htpc lircd: accepted new client on /var/run/lirc/lircd
Dec 13 20:40:38 htpc lircd: removed client
Dec 13 20:41:07 htpc lircd: caught signal
Dec 13 20:41:42 htpc lircd: lircd(mplay2) ready, using /var/run/lirc/lircd
Dec 13 20:45:46 htpc lircd: caught signal
Dec 13 20:45:46 htpc lircd: lircd(mplay2) ready, using /var/run/lirc/lircd
Dec 13 20:45:49 htpc lircd: accepted new client on /var/run/lirc/lircd
Dec 13 20:46:06 htpc lircd: removed client
Dec 13 21:08:44 htpc lircd: caught signal
Dec 13 21:09:18 htpc lircd: lircd(mplay2) ready, using /var/run/lirc/lircd
Dec 13 21:11:50 htpc lircd: caught signal
Dec 13 21:11:50 htpc lircd: lircd(mplay2) ready, using /var/run/lirc/lircd
Dec 13 21:16:51 htpc lircd: accepted new client on /var/run/lirc/lircd
Dec 13 21:17:09 htpc lircd: removed client
Dec 13 21:17:19 htpc lircd: caught signal
Dec 13 21:17:53 htpc lircd: lircd(mplay2) ready, using /var/run/lirc/lircdor
Dec 13 21:20:32 htpc lircd: caught signal
Dec 13 21:20:32 htpc lircd: lircd(mplay2) ready, using /var/run/lirc/lircd
Dec 13 21:20:36 htpc lircd: accepted new client on /var/run/lirc/lircd
Dec 13 21:20:41 htpc lircd: removed client
Dec 13 21:35:08 htpc lircd: caught signal
Dec 13 21:35:42 htpc lircd: lircd(mplay2) ready, using /var/run/lirc/lircd
Dec 13 21:39:19 htpc lircd: caught signal
Dec 13 21:39:19 htpc lircd: lircd(mplay2) ready, using /var/run/lirc/lircd
Dec 13 21:39:39 htpc lircd: accepted new client on /var/run/lirc/lircd
Dec 13 21:39:44 htpc lircd: removed client
Dec 13 21:43:06 htpc lircd: caught signal
Dec 13 21:43:06 htpc lircd: lircd(mplay2) ready, using /var/run/lirc/lircd
Dec 13 21:43:17 htpc lircd: accepted new client on /var/run/lirc/lircd
Dec 13 21:43:26 htpc lircd: removed client
Dec 13 21:52:20 htpc lircd: caught signal
Dec 14 18:08:45 htpc lircd: lircd(mplay2) ready, using /var/run/lirc/lircd
Dec 14 18:12:46 htpc lircd: caught signal
Dec 14 18:12:52 htpc lircd: lircd(mplay2) ready, using /var/run/lirc/lircd
Dec 14 18:13:01 htpc lircd: accepted new client on /var/run/lirc/lircd
Dec 14 18:13:11 htpc lircd: removed client
Dec 14 18:14:24 htpc lircd: accepted new client on /var/run/lirc/lircd
Dec 14 18:14:36 htpc lircd: removed client
Dec 14 18:19:00 htpc lircd: caught signal
Dec 14 18:27:23 htpc lircd: lircd(mplay2) ready, using /var/run/lirc/lircd
Dec 14 18:27:27 htpc lircd: accepted new client on /var/run/lirc/lircd
Dec 14 18:27:33 htpc lircd: removed client
Dec 14 18:27:59 htpc lircd: accepted new client on /var/run/lirc/lircd
Dec 14 18:37:31 htpc lircd: caught signal
Dec 14 18:38:08 htpc lircd: lircd(mplay2) ready, using /var/run/lirc/lircd
Dec 14 18:38:43 htpc lircd: accepted new client on /var/run/lirc/lircd

```I first Installed  0.9.0-pre1 with ./configure --with-driver=mplay2 make && make install.

Then I did 
sudo apt-get install lirc lirc-x liblircclient0 inputlirc 

 in order to get irw working.

I did everything like in post 28, but no success. :(

EDIT: EVERYTHING IS WORKING FINE KNOW. I HAVE NO IDEA WHAT WAS THE THING THAT MADE IT WORKING. 

Thank you for your help.

---

### Post by justme123 on 2011-12-15
Hm i assume there is still something wrong also it is working actually.
There should be NO need to install and compile it manually anymore in ubuntu 10.10 like you did. sudo apt-get install lirc should be all you need to do if you want it working with xbmc (-live) Version at least. But since u did a apt-install i guess your own compiled version ain't used anyways at least as long as you didn't modified anything else to point it to the bin files.
Yup everything you need to do should be mentioned in post 28 like you did at least for ubuntu 10.10 (but didn't test it so far).
But as long as it works for now :)

---

### Post by cyber7 on 2012-01-02
Hi Guys
Over the last couple of days I have re-built my mono 312 and the following steps get you going on XBMC:


1. Installed XBMC FRESH.
2. ```
apt-get update
```
3. ```
wget http://ftp.de.debian.org/debian/pool/main/l/lirc/lirc_0.9.0~pre1.orig.tar.bz2
```
4. ```
tar -jxvf lirc_0.9.0~pre1.orig.tar.bz2
```
5. ```
apt-get install libtool automake autoconf dialog
```
   ```
cd lirc-0.9.0-pre1/
```
6. ```
./configure --with-driver=mplay2
```
7. ```
make && make install
```
8. Changed the paths in /etc/init.d/lirc (from /usr/ to /usr/local/)
   ```
vi /etc/init.d/lirc
   :1,$ s/\/usr\//\/usr\/local\//g
```
9. Changed /etc/lirc/hardware.conf to have ONLY:
Code:
    REMOTE_DRIVER="mplay2"
    REMOTE_DEVICE="/dev/ttyUSB0"
10. Edit the file /etc/lirc/lircd.conf as follow :

```
begin remote
  name  Moncaso_312
  bits            8
  eps            30
  aeps          100
  one             0     0
  zero            0     0
  gap          107899
  toggle_bit_mask 0x0

      begin codes
          PwrOff                   0x41
          PwrOn                    0x55
          Hotkey                   0x5A
          DVD                      0x14
          Menu                     0x5C
          Sleep                    0x58
          Rec                      0x11
          Play                     0x09
          Eject                    0x5E
          Rew                      0x0D
          Pause                    0x05
          FF                       0x15
          Prev                     0x1A
          Stop                     0x01
          Next                     0x1E
          Full_Screen              0x0C
          Ratio                    0x10
          Task_Switcher            0x17
          Movie                    0x40
          Music                    0x56
          Photo                    0x45
          TV                       0x46
          OK                       0x42
          Up                       0x19
          Left                     0x54
          Right                    0x43
          Down                     0x1D
          Back                     0x0B
          Exit                     0x1F
          Mute                     0x4A
          More                     0x4B
          Open                     0x04
          Vol+                     0x0A
          Vol-                     0x0E
          CH+                      0x12
          CH-                      0x16
          1                        0x4D
          2                        0x4E
          3                        0x4F
          4                        0x50
          5                        0x51
          6                        0x52
          7                        0x53
          8                        0x03
          9                        0x07
          0                        0x4C
          Quick_Guide              0x08
          Timer                    0x18
      end codes
end remote

```
If I then reboot the machine and open a ssh console and run irw, I get the keystrokes!
<yahoo!!! at this stage!!!>

Added the following keymap to the /usr/share/xbmc/system/Lircmap.xml file and WALLA - everything works.

```
<remote device="Moncaso_312">
        <play>Play</play>
        <pause>Pause</pause>
        <stop>Stop</stop>
        <forward>FF</forward>
        <reverse>Rew</reverse>
        <left>Left</left>
        <right>Right</right>
        <up>Up</up>
        <down>Down</down>
        <select>OK</select>
        <pageplus>Ch+</pageplus>
        <pageminus>Ch-</pageminus>
        <back>Back</back>
        <menu>Menu</menu>
        <title>Hotkey</title>
        <info>More</info>
        <skipplus>Next</skipplus>
        <skipminus>Prev</skipminus>
        <display>Aspect</display>
        <start>Home</start>
        <record>Record</record>
        <volumeplus>Vol+</volumeplus>
        <volumeminus>Vol-</volumeminus>
        <mute>Mute</mute>
        <power>PwrOn</power>
        <myvideo>Movie</myvideo>
        <mymusic>Music</mymusic>
        <mypictures>Photo</mypictures>
        <mytv>TV</mytv>
        <one>1</one>
        <two>2</two>
        <three>3</three>
        <four>4</four>
        <five>5</five>
        <six>6</six>
        <seven>7</seven>
        <eight>8</eight>
        <nine>9</nine>
        <zero>0</zero>
	<obc5e>Eject</obc5e>
</remote>
```

Thank you everyone and you can use these instructions. They work 100%!

---

### Post by MacUsers on 2012-01-18
Hi there,

Has anyone successfully complied LIRC (v0.9.0) after applying [womiha]("http://ubuntuforums.org/member.php?u=1429003")'s patch yet?
[http://ubuntuforums.org/showpost.php?p=11385428&postcount=60](http://ubuntuforums.org/showpost.php?p=11385428&postcount=60)

I always end up with these error:
```

libhw_module.a(hw_mplay.o): In function `mplayfamily_deinit':
/root/LIRC/lirc-0.9.0/daemons/hw_mplay.c:670: undefined reference to `pthread_cancel'
/root/LIRC/lirc-0.9.0/daemons/hw_mplay.c:674: undefined reference to `pthread_join'
libhw_module.a(hw_mplay.o): In function `mplayfamily_set_listener_period':
/root/LIRC/lirc-0.9.0/daemons/hw_mplay.c:314: undefined reference to `clock_gettime'
libhw_module.a(hw_mplay.o): In function `mplayfamily_init':
/root/LIRC/lirc-0.9.0/daemons/hw_mplay.c:623: undefined reference to `pthread_create'
libhw_module.a(hw_mplay.o): In function `mplayfamily_listen':
/root/LIRC/lirc-0.9.0/daemons/hw_mplay.c:496: undefined reference to `__pthread_register_cancel'
/root/LIRC/lirc-0.9.0/daemons/hw_mplay.c:546: undefined reference to `__pthread_unregister_cancel'
collect2: ld returned 1 exit status
make[3]: *** [irrecord] Error 1
make[3]: Leaving directory `/root/LIRC/lirc-0.9.0/daemons'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/root/LIRC/lirc-0.9.0/daemons'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/LIRC/lirc-0.9.0'
make: *** [all] Error 2
```

Any idea what might be still missing? Cheers!!

---

### Post by womiha on 2012-01-18
Hi MacUsers!

OK, the driver needs the pthreads-library, and obviously that library is not linked in your build run.

Did you execute the [FONT=Courier New]autoconf[/FONT] command, and then the [FONT=Courier New]configure[/FONT]-script? There should appear a line ```
lircd_LDADD =  libhw_module.a -lpthread -lrt
```in the daemons directory makefile.

---

### Post by MacUsers on 2012-01-19
Sorry, my bad! Forgot to run [FONT=Courier New]autoconf[/FONT] command; all okay now. Cheers!!

---

### Post by dvandermeer on 2012-02-10
Hi,

I hope someone can help me. I have been trying to get things to work perfectly with my MonCaso 320 and apart from the remote working almost perfectly I cannot get the display working or get the rec button on the remote working. After searching the internet for information I stumbled onto this site.
I saw some patches from womiha and applied them to a fresh version of lirc 0.9.0 and it does so without any problems. After this I start the configure with:
./configure --prefix=/usr --with-driver=mplay2
And then make but I get the following error:

make[3]: Leaving directory `/mnt/hd/filesystem/usr/src/lirc-0.9.0/daemons'
make[2]: Leaving directory `/mnt/hd/filesystem/usr/src/lirc-0.9.0/daemons'
Making all in tools
make[2]: Entering directory `/mnt/hd/filesystem/usr/src/lirc-0.9.0/tools'
/bin/sh ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT lirc_client.lo -MD -MP -MF .deps/lirc_client.Tpo -c -o lirc_client.lo lirc_client.c
mv -f .deps/lirc_client.Tpo .deps/lirc_client.Plo
mv: cannot stat `.deps/lirc_client.Tpo': No such file or directory
make[2]: *** [lirc_client.lo] Error 1
make[2]: Leaving directory `/mnt/hd/filesystem/usr/src/lirc-0.9.0/tools'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/mnt/hd/filesystem/usr/src/lirc-0.9.0'
make: *** [all] Error 2

I have tried everything to get it working but without success. Without the patches it compiles without problems. Even compiling first, applying patches and the compiling again doesn't work.

Does anyone (maybe womita) have a clue as to what's going on?


Thanks,

Dennis

---

### Post by justme123 on 2012-02-12
Hi Dennis,

doubt it will make a big difference but did u try the configure without the --prefix=/usr ?

---

### Post by womiha on 2012-02-13
Hi Dennis!

The line 
```

/bin/sh ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.  -I.. -I..    -O2 -g -Wall -MT lirc_client.lo -MD -MP -MF  .deps/lirc_client.Tpo -c -o lirc_client.lo lirc_client.c

```should produce some log output. The immediately following mv-command looks strange here. I would expect at least some error message here.

Could you please have a look for the same line if you compile your lirc without the patch? I expect some log-output. Please post the command line plus output here.

---

### Post by dvandermeer on 2012-02-15
As soon as my motherboard is back I will try this. Unfortunately I started having the weird harddisk / harddisk controller bug: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550559](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550559)

I hope I will get my system back soon so I can test it.
Thanks for the suggestions.

---

### Post by dvandermeer on 2012-02-17
Here is the output without the patch. As you can see, no error messages. Compile just continues. I will have to say that I use Slackware 17.37 and not Ubuntu but the source for lirc is just the default source.

```
Making all in tools
make[2]: Entering directory `/mnt/hd/filesystem/usr/src/lirc-0.9.0/tools'
/bin/sh ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT lirc_client.lo -MD -MP -MF .deps/lirc_client.Tpo -c -o lirc_client.lo lirc_client.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -I.. -O2 -g -Wall -MT lirc_client.lo -MD -MP -MF .deps/lirc_client.Tpo -c lirc_client.c  -fPIC -DPIC -o .libs/lirc_client.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -I.. -O2 -g -Wall -MT lirc_client.lo -MD -MP -MF .deps/lirc_client.Tpo -c lirc_client.c -o lirc_client.o >/dev/null 2>&1
mv -f .deps/lirc_client.Tpo .deps/lirc_client.Plo
/bin/sh ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall -version-info 2:1:2  -o liblirc_client.la -rpath /usr/lib lirc_client.lo
libtool: link: gcc -shared  .libs/lirc_client.o      -Wl,-soname -Wl,liblirc_client.so.0 -o .libs/liblirc_client.so.0.2.1
libtool: link: (cd ".libs" && rm -f "liblirc_client.so.0" && ln -s "liblirc_client.so.0.2.1" "liblirc_client.so.0")
libtool: link: (cd ".libs" && rm -f "liblirc_client.so" && ln -s "liblirc_client.so.0.2.1" "liblirc_client.so")
libtool: link: ar cru .libs/liblirc_client.a  lirc_client.o
libtool: link: ranlib .libs/liblirc_client.a
libtool: link: ( cd ".libs" && rm -f "liblirc_client.la" && ln -s "../liblirc_client.la" "liblirc_client.la" )
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT irw.o -MD -MP -MF .deps/irw.Tpo -c -o irw.o irw.c
mv -f .deps/irw.Tpo .deps/irw.Po
/bin/sh ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o irw irw.o
libtool: link: gcc -O2 -g -Wall -o irw irw.o
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT irpty.o -MD -MP -MF .deps/irpty.Tpo -c -o irpty.o irpty.c
mv -f .deps/irpty.Tpo .deps/irpty.Po
/bin/sh ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o irpty irpty.o liblirc_client.la -lutil
libtool: link: gcc -O2 -g -Wall -o .libs/irpty irpty.o  ./.libs/liblirc_client.so -lutil
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT irexec.o -MD -MP -MF .deps/irexec.Tpo -c -o irexec.o irexec.c
mv -f .deps/irexec.Tpo .deps/irexec.Po
/bin/sh ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o irexec irexec.o liblirc_client.la
libtool: link: gcc -O2 -g -Wall -o .libs/irexec irexec.o  ./.libs/liblirc_client.so
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT ircat.o -MD -MP -MF .deps/ircat.Tpo -c -o ircat.o ircat.c
mv -f .deps/ircat.Tpo .deps/ircat.Po
/bin/sh ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o ircat ircat.o liblirc_client.la
libtool: link: gcc -O2 -g -Wall -o .libs/ircat ircat.o  ./.libs/liblirc_client.so
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT mode2.o -MD -MP -MF .deps/mode2.Tpo -c -o mode2.o mode2.c
mv -f .deps/mode2.Tpo .deps/mode2.Po
/bin/sh ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o mode2 mode2.o ../daemons/libhw_module.a
libtool: link: gcc -O2 -g -Wall -o mode2 mode2.o  ../daemons/libhw_module.a
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT irsend.o -MD -MP -MF .deps/irsend.Tpo -c -o irsend.o irsend.c
mv -f .deps/irsend.Tpo .deps/irsend.Po
/bin/sh ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o irsend irsend.o
libtool: link: gcc -O2 -g -Wall -o irsend irsend.o
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT lircrcd.o -MD -MP -MF .deps/lircrcd.Tpo -c -o lircrcd.o lircrcd.c
mv -f .deps/lircrcd.Tpo .deps/lircrcd.Po
/bin/sh ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o lircrcd lircrcd.o liblirc_client.la
libtool: link: gcc -O2 -g -Wall -o .libs/lircrcd lircrcd.o  ./.libs/liblirc_client.so
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT smode2.o -MD -MP -MF .deps/smode2.Tpo -c -o smode2.o smode2.c
mv -f .deps/smode2.Tpo .deps/smode2.Po
/bin/sh ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o smode2 smode2.o -lvga -lvgagl
libtool: link: gcc -O2 -g -Wall -o smode2 smode2.o  -lvga -lvgagl
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT irxevent.o -MD -MP -MF .deps/irxevent.Tpo -c -o irxevent.o irxevent.c
irxevent.c:137:15: warning: 'w' defined but not used
mv -f .deps/irxevent.Tpo .deps/irxevent.Po
/bin/sh ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o irxevent irxevent.o -lSM -lICE -lX11  liblirc_client.la
libtool: link: gcc -O2 -g -Wall -o .libs/irxevent irxevent.o  /usr/lib64/libSM.so /usr/lib64/libuuid.so /usr/lib64/libICE.so /usr/lib64/libX11.so /usr/lib64/libxcb.so /usr/lib64/libXau.so /usr/lib64/libXdmcp.so -ldl ./.libs/liblirc_client.so
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT xmode2.o -MD -MP -MF .deps/xmode2.Tpo -c -o xmode2.o xmode2.c
mv -f .deps/xmode2.Tpo .deps/xmode2.Po
/bin/sh ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o xmode2 xmode2.o ../daemons/libhw_module.a -lSM -lICE -lX11
libtool: link: gcc -O2 -g -Wall -o xmode2 xmode2.o  ../daemons/libhw_module.a /usr/lib64/libSM.so /usr/lib64/libuuid.so /usr/lib64/libICE.so /usr/lib64/libX11.so /usr/lib64/libxcb.so /usr/lib64/libXau.so /usr/lib64/libXdmcp.so -ldl
echo "#! /usr/bin/python" >pronto2lirc
cat pronto2lirc.py >>pronto2lirc
chmod +x pronto2lirc
make[2]: Leaving directory `/mnt/hd/filesystem/usr/src/lirc-0.9.0/tools'
Making all in doc
make[2]: Entering directory `/mnt/hd/filesystem/usr/src/lirc-0.9.0/doc'
Making all in man
make[3]: Entering directory `/mnt/hd/filesystem/usr/src/lirc-0.9.0/doc/man'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/mnt/hd/filesystem/usr/src/lirc-0.9.0/doc/man'
make[3]: Entering directory `/mnt/hd/filesystem/usr/src/lirc-0.9.0/doc'
gcc -DHAVE_CONFIG_H -I. -I..     -O2 -g -Wall -MT man2html.o -MD -MP -MF .deps/man2html.Tpo -c -o man2html.o man2html.c
mv -f .deps/man2html.Tpo .deps/man2html.Po
/bin/sh ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o man2html man2html.o
libtool: link: gcc -O2 -g -Wall -o man2html man2html.o
make[3]: Leaving directory `/mnt/hd/filesystem/usr/src/lirc-0.9.0/doc'
make[2]: Leaving directory `/mnt/hd/filesystem/usr/src/lirc-0.9.0/doc'
make[2]: Entering directory `/mnt/hd/filesystem/usr/src/lirc-0.9.0'
make[2]: Leaving directory `/mnt/hd/filesystem/usr/src/lirc-0.9.0'
make[1]: Leaving directory `/mnt/hd/filesystem/usr/src/lirc-0.9.0'
```

The full command that I used for the compile:

```
./configure --prefix=/usr --with-driver=mplay2
```And leaving out the --prefix=/usr did not help

I did adjust the configure script and changed the "mv" commands into "cp" commands and with that I am able to finish the compile eventually but this leaves only a couple of executables with most of them missing

---

### Post by womiha on 2012-02-18
The output is the same as for me here. Sorry, I cannot tell what is going wrong. On the other hand, as [FONT=Courier New]libtool[/FONT] seems to cause the trouble, I list some suggestions here.

The patch modifies three files:

[LIST]
[*][FONT=Courier New]configure.ac[/FONT]
[*][FONT=Courier New]hw_mplay.c[/FONT]
[*][FONT=Courier New]hw_mplay.h[/FONT]
[/LIST]
The change of [FONT=Courier New]configure.ac[/FONT] requires to execute [FONT=Courier New]autoconf[/FONT], which generates new configuration scripts. Perhaps there is some kind of incompatibility here.

Some ideas to play with:

[LIST]
[*]Try to to execute [FONT=Courier New]autoreconf[/FONT] instead of [FONT=Courier New]autoconf[/FONT]
[*]Try to execute [FONT=Courier New]autoreconf --install[/FONT]
[*]Try to execute [FONT=Courier New]./configure --with-driver=mplay2 --enable-libtool-lock[/FONT]
[*]Try to change into the tool directory, and call [FONT=Courier New]make[/FONT] from there.
[/LIST]
Just a few guesses. But perhaps we are lucky...

---

### Post by dvandermeer on 2012-02-18
> **womiha said:**
> ......<cut>

Some ideas to play with:

[LIST]
[*]Try to to execute [FONT=Courier New]autoreconf[/FONT] instead of [FONT=Courier New]autoconf[/FONT]
[*]Try to execute [FONT=Courier New]autoreconf --install[/FONT]
[*]Try to execute [FONT=Courier New]./configure --with-driver=mplay2 --enable-libtool-lock[/FONT]
[*]Try to change into the tool directory, and call [FONT=Courier New]make[/FONT] from there.
[/LIST]
Just a few guesses. But perhaps we are lucky...

Thanks alot!!! The "autoreconf --install before I do the ./configure did the trick.
It now compiles without problems. Maybe a libtool version mismatch or something.
You have been a great help. 

Now I can continue with configuring the remote for all the buttons and also the volume control on the unit. 
After this I can hopefully also get the display to work in XBMC and then I am a totally happy guy :-)

Anyway, this patch solves the problem of the Rec remote key not giving a key code, right?
Does it also solve the issue with some of the keys giving similar codes back?
For example: Rewind = 0x0a, which is the same as Volume +

---

### Post by womiha on 2012-02-19
> **dvandermeer said:**
> Anyway, this patch solves the problem of the Rec remote key not giving a key code, right?
Does it also solve the issue with some of the keys giving similar codes back?
For example: Rewind = 0x0a, which is the same as Volume +

Yes, the patch fixes the rec key problem.

I have not observed the behaviour with the rewind/volume key; I have been using my RC now for a few months without problems. But it might remove your key trouble, as basically some codes had been interpreted before as control codes for the serial line. And 0x0a looks like such a code.

---

### Post by dvandermeer on 2012-02-22
Thanks for all the support. It all seems to work. I did not test the duplicate keys yet but my display is finally working!! I got tired of looking at the "Moneual" text :)
What I did notice that in the configuration the display is set to 20x4 (default setting) but as far as I can see my display can only do 1 line. Which is too bad because with movies that last more than 1 hour the display starts scrolling constantly because there is too much text for 1 line.

---

### Post by richardss2 on 2012-04-01
Hi,
After many months away from this I'm excited to see womiha has got the VFD working - Well done!!

I see from the LCDproc mailing list ([http://comments.gmane.org/gmane.comp.sysutils.lcdproc/13653](http://comments.gmane.org/gmane.comp.sysutils.lcdproc/13653)) that the patch has been added to the latest release, but I cannot see any sign of it in version 0.5.5 (the latest). 

I've installed the latest 'nightly build' and your driver is in there. Running a command like "lcdproc -s 127.0.0.1 -p 13666 C" however doesent make any change to the display. running "lcdproc -v" does return "LCDproc 0.5dev", so I assume it is installed ok... but could easily be wrong! Any suggestions?


Thanks for your earlier suggestion on restarting the driver to resolve the remote not working after suspend. Instead I renamed the device to ttyUSB0 on resume if it was named ttyUSB1. Probably not the neatest way I grant you!


By the way,
I spoke to the manufacturers of the VFD a few months ago who assured me that it wasn't possible to connect through Linux - perhaps you would like to share the good news with them?

---

### Post by richardss2 on 2012-04-02
Hi, 
I got the display working last night - thank you all for the advice in this thread, and especially to womiha for the driver!

The problem I was facing if anyone else runs into it was the LCDd.conf file was being read from /usr/local/etc/, not from /etc which was the version I was configuring.

womiha, have you had any luck with the screen's icons? I'm not sure the software I'm using (XBMCbuntu) can output to them anyway.

Thanks again!

---

### Post by womiha on 2012-04-02
> **richardss2 said:**
> 
By the way,
I spoke to the manufacturers of the VFD a few months ago who assured me that it wasn't possible to connect through Linux - perhaps you would like to share the good news with them?

Really? Judging their web-site, I estimated the contact-probability to zero. I am interested, so if you have some hints how to establish a contact...

---

### Post by womiha on 2012-04-02
> **richardss2 said:**
> 
womiha, have you had any luck with the screen's icons? I'm not sure the software I'm using (XBMCbuntu) can output to them anyway.


Meanwhile I know how to control the icons.

However, icons (in the sense of symbols) are not yet supported by LDCproc. There are discussions ongoing how to extend LDCproc for a generic use of icons. This is not a high priority task, but it is an active task. Consequently, XBMC (nor any other client) is able to access the icons.

Controlling the icons is rather easy. If there is some interest in that, I can give a couple of hints how to extend the driver for a use of icons (until there is a solution available for LDCproc).

---

### Post by richardss2 on 2012-04-14
> **womiha said:**
> Really? Judging their web-site, I estimated the contact-probability to zero. I am interested, so if you have some hints how to establish a contact...

I spoke (briefly) to a "VL./Kim" at vlsys <at> vlsys <dot> co <dot> kr

The VFD board is the MMX428

---

### Post by LightScape66 on 2012-07-07
> **womiha said:**
> I am going to submit this patch to LIRC, but I would like to read some feedback here.

Hello and many thanks for your work. I appreciate it very much, cause I have an Moncaso312 and only the IR part works at this time. I will try this patch within the next days.

How do I have to install that?

I wrote the quote similar to the installation howto from wiki.xbmc.org concerning the Moncaso 312 (wich works for the IR part)....

> 
 apt-get update
 tar -jxvf lirc....
 patch -p0 < .....patch
 apt-get install libtool automake autoconf dialog
 cd lirc-0.9.0-pre1/
 ./configure --with-driver=mplay2
 make && make install



and will the file /etc/lirc/hardware.conf be okay with this content:
> 
REMOTE_DRIVER="mplay2"
 REMOTE_DEVICE="/dev/ttyUSB0"


Thanks in advance,
bye,
Tom

---

### Post by LightScape66 on 2012-07-07
Okay... now I am very frustrated....

I made the download of the source, applied the path from wohima, learned, that I hat do use autoreconf or whatever it's named...
I started ./configure.... and then make && make install. I could compile without the errors...

But... no /etc/init.d/lirc and no /etc/lirc/hardware.conf....

*grummel*

Okay, I installed lirc via apt-get install....

To be sure, I ran again ./configure... and the make commands to install the right binary...

Then I had these two files, so I modified them. After rebooting, irw could read the remote, but not the knob.

I am using Ubuntu 12.04 (standard install) and I installed xbmc simply via apt-get isntall xbmc. The case is a 312-er.... fortunately no display (but a 46-er SONY X4500!).

What can be wrong? How can I see, if the installed binary is correct? The timestamp (looked with ps-ef | grep lirc for the right path) was actual...

Kind regards,
Tom

---

### Post by womiha on 2012-07-09
Hello Tom, thanks for giving the driver a try. Well, I know, this stuff gets easily frustrating. It took me some time.

Hm, as far as I know there happened some changes for Ubuntu 12.04. It seems as some LIRC parts have been moved to the kernel. I am no expert for this subject, and I have only Ubuntu 11.04 at hand, sorry.

Anyway, let's try to get this stuff work. Keep in mind, I can only test for Ubuntu 11.04.

Did you add the extra buttons [FONT=Courier New]Turn_Left[/FONT], [FONT=Courier New]Turn_Right[/FONT] and[FONT=Courier New] Knob[/FONT] to [FONT=Courier New]/etc/lirc/lircd.conf[/FONT]?

Do a [FONT=Courier New]configure[/FONT] with paths explicitly set, and debugging enabled:
```
./configure --enable-debug --with-driver=mplay2 --prefix=/usr --sysconfdir=/etc
```The paths have to match your system.

Please ensure that there is no lirc stuff running:
```
sudo service lirc stop
```Maybe you want to check this with
```
ps -ef | grep -i lirc
```Then, start the lirc-daemon manually:
```
sudo lircd -n -D3 -Hmplay2 /etc/lirc/lircd.conf
```There is much output, but the interesting part starts with "[FONT=Courier New]lircd: config file read[/FONT]". Do you see this line?

Now, continue the test by starting [FONT=Courier New]irw[/FONT]. The next debug output lines appear with the running [FONT=Courier New]lircd[/FONT]. What do you see?

As next step, turn the knob left, then right. Finally, press the button. What is the output with [FONT=Courier New]lircd[/FONT]?

Did you see any output for [FONT=Courier New]irw[/FONT]?

---

### Post by Horfic on 2012-07-13
Hi,
first at all I really have to thank womiha for his great lirc driver. Works out of the box^^

Second, would it be possible to add a long press knob to the lirc driver?

Third, how is the support for lcdproc going on or more specifically your driver support for the icons?

I downloaded lcdproc 0.5.4 and applied your patch and then configured it with driver vlsys_m428 but I'm getting an error during make

```
make[3]: *** Keine Regel vorhanden, um das Target Â»vlsys_m428.oÂ«,
  benÃ¶tigt von Â»vlsys_m428.soÂ«, zu erstellen.  Schluss.
```Here is what i did to reproduce:
```
apt-get install libftdi1 libftdipp-dev libftdi-dev libftdipp1
apt-get build-dep lcdproc
cd /tmp
wget http://downloads.sourceforge.net/project/lcdproc/lcdproc/0.5.4/lcdproc-0.5.4.tar.gz
tar xvfz lcdproc-0.5.4.tar.gz
patch -p0 < vlsys_m428.patch
cd lcdproc-0.5.4
./configure --enable-drivers=vlsys_m428
make && make install
```Maybe you could give me a hint how to compile it and get it to work.

PS: Thanks again.

PPS: For everyone who has trouble with the lirc. Here is what i did:
```
cd /tmp
wget http://sourceforge.net/projects/lirc/files/LIRC/0.9.0/lirc-0.9.0.tar.bz2
tar -jxf lirc-0.9.0.tar.bz2
patch -p0 < lirc-0.9.0.patch
apt-get install libtool automake autoconf dialog
autoreconf --install
./configure --with-driver=mplay2 --enable-libtool-lock
make && make install
```Regards,
Horfic

---

### Post by womiha on 2012-07-15
> **Horfic said:**
> Hi,
first at all I really have to thank womiha for his great lirc driver. Works out of the box^^

Glad to hear the driver helps some folks out there. :D

> **Horfic said:**
> 
Second, would it be possible to add a long press knob to the lirc driver?

Yes, it is possible. The knob behaves different than the remote buttons: It produces spurious knob presses (no debouncing?), and does not report repetitions. The good news is that I have an idea how to suppress those spurious presses in an easy manner in the somewhat tricky knob/wheel support. Allow me a couple of days for implementation and test. You are going to read here for upcoming extensions.

> **Horfic said:**
> 
Third, how is the support for lcdproc going on or more specifically your driver support for the icons?

Well, the interface presented to LCDproc clients has been under discussion. The subject will re-appear on the mailing list of LCDproc, and the plan is to deliver icon support with the next release but one.

> **Horfic said:**
> 
I downloaded lcdproc 0.5.4 and applied your patch and then configured it with driver vlsys_m428 but I'm getting an error during make

Perhaps it is just a missing [FONT=Courier New]autoconf[/FONT] or [FONT=Courier New]autoreconf[/FONT]. Maybe the posts [#73]("http://ubuntuforums.org/showpost.php?p=11622448&postcount=73") and [#80]("http://ubuntuforums.org/showpost.php?p=11698429&postcount=80") are helpful here.

---

### Post by LightScape66 on 2012-07-15
> **womiha said:**
> Hello Tom, thanks for giving the driver a try. 
.....

Hello WOMIHA,
yes I did and I didn't regret it, cause it works now. Cause I really didn't use the correct lircd.conf, so there were Knob & Co. missing. Therefor, IRW couldn't send output.

After adding these 3 Hexcodes in lircd.conf and adding them to Lircmap.xml, it works fine...

Thanks for your patience.

Bye,
Tom

---

### Post by Horfic on 2012-07-16
> **womiha said:**
> Perhaps it is just a missing [FONT=Courier New]autoconf[/FONT] or [FONT=Courier New]autoreconf[/FONT]. Maybe the posts [#73]("http://ubuntuforums.org/showpost.php?p=11622448&postcount=73") and [#80]("http://ubuntuforums.org/showpost.php?p=11698429&postcount=80") are helpful here.
Well I also tried autoconf and autoreconf, but without success.

Maybe a little tut like you did for lirc?

Regards,
Horfic

---

### Post by LightScape66 on 2012-07-16
> **womiha said:**
> Glad to hear the driver helps some folks out there. :D


Yes, it is possible. The knob behaves different than the remote buttons: It produces spurious knob presses (no debouncing?), and does not report repetitions. The good news is that I have an idea how to suppress those spurious presses in an easy manner in the somewhat tricky knob/wheel support. Allow me a couple of days for implementation and test. You are going to read here for upcoming extensions.


Hello, you're doing a great work! (chapeau!)

Maybe, it will be easier to debounce this button by soldering a 10nF capacitor parallel to the knob-switch? (I guess, 10nF will be enough capacity.)

What I am thinking about, then you can select between a short press, a longer one and a double-click.

Bye,
Tom

---

### Post by LightScape66 on 2012-07-18
Okay, 10nF may not be enough, but it is a step into the right direction. I will check 47nF later... i soldered the capictor directly onto the pcb with the knob. looks like it should be....

47nF also don't work... I will try other values later. If it doesn't, maybe I will program an ATmega 328p to do the job... maybe with some other special features (e.g. HW reset)...

---

### Post by womiha on 2012-07-21
> **Horfic said:**
> 
Maybe a little tut like you did for lirc?


**Patching and compiling:**
```

user@htpc:/tmp/work$ ls
lcdproc-0.5.4.tar.gz  vlsys_m428.patch

user@htpc:/tmp/work$ tar xzf lcdproc-0.5.4.tar.gz

user@htpc:/tmp/work$ cd lcdproc-0.5.4

user@htpc:/tmp/work/lcdproc-0.5.4$ patch -p1 < ../vlsys_m428.patch 
patching file acinclude.m4
patching file docs/LCDd.8.in
patching file docs/lcdproc-user/drivers/vlsys_m428.docbook
patching file docs/lcdproc-user/drivers.docbook
patching file docs/lcdproc-user/lcdproc-user.docbook
patching file LCDd.conf
patching file server/drivers/Makefile.am
patching file server/drivers/vlsys_m428.c
patching file server/drivers/vlsys_m428.h

user@htpc:/tmp/work/lcdproc-0.5.4$ autoreconf --install

user@htpc:/tmp/work/lcdproc-0.5.4$ ./configure --prefix=/usr --sysconfdir=/etc --enable-drivers=vlsys_m428 --enable-debug

user@htpc:/tmp/work/lcdproc-0.5.4$ make

```I am afraid I have introduced some confusion with the patch format. Sorry for that, I am not thus experienced with patch conventions.

**Installation:** You may type [FONT=Courier New]make install[/FONT], but I recommend the package [FONT=Courier New]checkinstall[/FONT] for Debian or Ubuntu users.

---

### Post by womiha on 2012-07-21
Here comes a LIRC patch ([FONT=Courier New]lirc-0.9.0.patch.gz[/FONT]) with improved handling of the wheel/knob (turn and press actions). The patch removes knob bouncing effects, and has removed some subtle bugs when using wheel/knob and IR control in parallel.

Summary:

[LIST]
[*]One knob press - one LIRC event
[*]Multiple fast knob presses - multiple LIRC events with correct repetition count
[/LIST]
You may check this behaviour with [FONT=Courier New]irw[/FONT]. With a little practice you are able to produce "single clicks", "double clicks", "triple clicks", etc. Here an example with single click, double click, triple click:
```

user@htpc:/tmp/work/lcdproc-0.5.4$ irw
0000000000000082 00 Knob Moncaso_320
0000000000000082 00 Knob Moncaso_320
0000000000000082 01 Knob Moncaso_320
0000000000000082 00 Knob Moncaso_320
0000000000000082 01 Knob Moncaso_320
0000000000000082 02 Knob Moncaso_320
```The source code delivered by the patch contains some constants (particularly [FONT=Courier New]MIN_TIME_BETWEEN_PRESSES[/FONT], [FONT=Courier New]MAX_TIME_KNOB_PRESS_IS_REPETITION[/FONT]) where you can tune the debouncing and multiple press behaviour.

I decided against the introduction of a special code for a double click as I would leave the handling of repetitions to clients. Clients have to use multiple button presses as they would have to do for any other button. (OK, the true reason is that it gets too complicated ;)) By the way, reporting a long knob press is not possible, the hardware produces alway short events (possibly followed by spurious bouncing events).

---

### Post by pip78 on 2012-12-10
Hopefully I can get some help here. I have a moncaso 312. Walk you through what I've done so far. I have a clean install of ubuntu 12.04 running xbmc on it. I installed lirc using apt-get. I then followed post #92 to get the patched version of lirc. I then used apt-get remove lirc. After that I followed post #71 to change all my files. At this point I can run irw and see all the key presses on my remote, include rec and rew acting like they should. I open xbmc but the remote doesn't do anything. Am I missing a setting in XBMC? Am I missing some other file or something? I've checked and double checked my lircd.conf file and my Lircmap.xml file and everything seems kosher. And just so it's pointed out, my linux skills aren't the best. Thanks.

Is there supposed to be a keymap.xml file of some sort in $HOME/.xbmc/userdata/keymaps?

---

### Post by nickrout on 2012-12-10
> **pip78 said:**
> Hopefully I can get some help here. I have a moncaso 312. Walk you through what I've done so far. I have a clean install of ubuntu 12.04 running xbmc on it. I installed lirc using apt-get. I then followed post #92 to get the patched version of lirc. I then used apt-get remove lirc. After that I followed post #71 to change all my files. At this point I can run irw and see all the key presses on my remote, include rec and rew acting like they should. I open xbmc but the remote doesn't do anything. Am I missing a setting in XBMC? Am I missing some other file or something? I've checked and double checked my lircd.conf file and my Lircmap.xml file and everything seems kosher. And just so it's pointed out, my linux skills aren't the best. Thanks.

Is there supposed to be a keymap.xml file of some sort in $HOME/.xbmc/userdata/keymaps?This is actually a mythbuntu (ie mythtv) forum, but hey we all like to help.

Googling pretty soon found this for me:

[http://wiki.xbmc.org/index.php?title=HOW-TO:Install_XBMC_on_a_Moneual_Labs_MonCaso_312_HTPC_case](http://wiki.xbmc.org/index.php?title=HOW-TO:Install_XBMC_on_a_Moneual_Labs_MonCaso_312_HTPC_case)

I hope it helps. It seems like you do need a keymap file, and thers one provided there for you :)

---

### Post by justme123 on 2012-12-18
that wiki is basically only a short form of this thread here ):P
also it ain't up to date anymore after womiha took over the work of the driver and added a couple of fixes to the driver.

Yep you need to modify the Lircmap.xml yourself.

---

