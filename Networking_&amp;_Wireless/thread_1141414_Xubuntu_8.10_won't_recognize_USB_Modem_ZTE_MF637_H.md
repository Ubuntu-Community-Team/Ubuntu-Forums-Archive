---
title: "Xubuntu 8.10 won't recognize USB Modem ZTE MF637 HSUPA"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by Fazl on 2009-04-28
Please bear with me as I am a n00b at Xubuntu (Xubuntu 8.10 Intrepid as far as I can tell) running an XFCE desktop.

I have a ZTE MF637 Broadband dongle which I cannot connect to the internet with. I see that there have been problems with the older MF622, MF626, MF628 and MF632 but I don't see anything about the MF637. I've been trying to get mine working using the same solutions but have come to a dead end where i don't see what the modification for (gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi) file which was reported in bug #305968. On top of that, I tried to do the modification for what IS in the file and I don't seem to have permissions to do it and I don't know how to give myself those permissions. What I am hoping is that these bugs are already resolved, but if they are, I don't understand how they still exist since I only downloaded and installed my Xubuntu 8.10 Intrepid about 18 days ago.

A little background on my problem: I bought the USB dongle to connect to the internet faster than what I have now. Currently I am connecting through a Motorola C380 and using it as a modem via USB. It is only getting about 10kps at max so I bought this dongle hoping it would work just as easily but unfortunately not the case. I went online to try to see if there were any packages i could install via Synaptic Package Manager that might help. I've installed a few which managed to make the Dongle's light go blue (3G operational) instead of the steady red (communication error). With this, i thought I was making some progress but no luck after that. I've downloaded a few other packages but none seem to help. They were "3G managing" packages for 3G dongles.

Originally I thought the issue was that my computer was not even recognizing the dongle because when i went to Terminal and punched in LSUSB, or DMESG, i never got any change. The other thing is that I am using a PCMCIA to USB adapter card for my USB devices. These devices all work fine but when I plug in the dongle, the PCMCIA card freezes up and I lose communication from it. I have to remove the dongle and reset my PCMCIA card and then the devices work again.

I think thats all the information I can tell. I don't know of anything else to do.

-----------------------------

Here is a bit of an update as I have been trying to get this to work. It turns out that part of the problem is the dongle's interface with my Nexxtec PCMCIA card. When the dongle is plugged into it, it freezes the card up so it does not show up on the LSUSB commanded device list.

I plugged the dongle into my replicator USB port (I am using an IBM T43 with a replicator dock) and I got a device id --- Bus 002 Device 006: ID 19d2:2000. Now checking this against my 10-modem.fdi file, this vendor ID is correct as it comes up with ZTE or ONDA, but the device ID is wrong as it should be 0002. I tried a couple of different things including modifying the 10-modem.fdi file but to no avail. The computer does not recognize the device as anything other than the "Bus 002 Device 006: ID 19d2:2000" identification.

Next, I did some research with a lot of help from another fellow Linux user and came across USB_modeswitch. I already had the file installed but had to change the conf file. This is the part I changed (or de-commented):

########################################################
# ZTE MF628
#
# Captured with "usbmon". Has a micro SD slot which can be
# activated alternatively
#
# Contributor: Alvaro Lopes <alvieboy at alvie dot com>

DefaultVendor= 0x19d2
DefaultProduct= 0x2000

# To modem mode:

TargetVendor= 0x19d2
TargetProduct= 0x0015

MessageEndpoint=0x08
MessageContent="5553424312345678000000000000061b000000030000000000000000000000"

# To SD slot mode:

;TargetVendor= 0x05c6
;TargetProduct= 0x2001

;MessageEndpoint=0x08
;MessageContent="55534243123456782000000080000a86010101180101010101000000000000"

;ResponseEndpoint=7

########################################################

With that done, I believe that I should have been able to enact the usb_modeswitch to engage the Broadband part of the dongle and disengage the ZeroCD (false pendrive) portion. Unfortunately that did not work either so the next step was to Blacklist the usb-storage by (sudo gedit /etc/modprobe.d/blacklist). I did that hoping that it would bring the USB storage back to the default but that didn't work either. After trying that and retrying the usb_modeswitch, i keep getting the notorious (-2) error which states that the device cannot unlock or communicate. This is the error.

sudo usb_modeswitch

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.6 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices
 No target device found
Looking for default devices
 Found default devices (1)
Prepare switching, accessing latest device
Looking for active default driver to detach it
 No driver found. Device probably not initialized. Trying to continue ...
Setting up communication with device
Trying to send the message
 Sending the message returned error -2, trying to continue ...
-> See /proc/bus/usb/devices (or call lsusb) for changes. Bye

Can anyone help me here? I know there is a way to get this working, I just need to find it.

-----------------------------------------------------

Second update here....

Here is a bit more of an update on my problem. I continued on troubleshooting and came across this set of commands in one of the forums and tried it out. This is what I did.

sudo gedit /etc/udev/rules.d/ZTEMF622.rules

With that, I created a rules file for the ZTEMF637 even though the name was 622, I didn't see it to matter much since the product and vendor Ids are identical. Next, I filed in the file with...

ACTION!="add", GOTO="ZTE_End"

# Is this the ZeroCD device?
SUBSYSTEM=="usb", SYSFS{idProduct}=="2000",
SYSFS{idVendor}=="19d2", GOTO="ZTE_ZeroCD"

# Is this the actual modem?
SUBSYSTEM=="usb", SYSFS{idProduct}=="0001",
SYSFS{idVendor}=="19d2", GOTO="ZTE_Modem"

LABEL="ZTE_ZeroCD"
# This is the ZeroCD part of the card, remove
# the usb_storage kernel module so
# it does not get treated like a storage device
RUN+="/usr/src/usb_modeswitch-0.9.2/usb_modeswitch -d 1 -v 0x19d2 -p 0x2000 -V 0x19d2 -P 0x0001"

LABEL="ZTE_Modem"
# This is the Modem part of the card, let's
# load usbserial with the correct vendor
# and product ID's so we get our usb serial devices
RUN+="/sbin/modprobe usbserial vendor=0x19d2 product=0x0001",
# Make users belonging to the dialout group
# able to use the usb serial devices.
MODE="660", GROUP="dialout"

LABEL="ZTE_End"

And then I saved this file in the location I made it in ( etc/udev/rules.d/ZTEMF622.rules )

Next, I did this

sudo gedit /etc/wvdial.conf

[Dialer Defaults]

Init2 = ATZ

Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Stupid Mode = 1

Modem Type = Analog Modem

ISDN = 0

Phone = *99#

Modem = /dev/ttyUSB0

Username = user

Dial Command = ATDT

Password = pass

Baud = 460800

I saved the file and closed it. Then I shut my computer down and rebooted and tried the sudo wvdial command and I got

--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory

Now this is where I stand now although I HAVE noticed some interesting changes. I no longer have the same issue with my PCMCIA card interfacing with the dongle. If I reboot the system with the dongle in the PCMCIA card, the card functions fine AND the dongle shows up on the LSUSB commanded device list. The only problem is if I pull the dongle out, everything freezes up and my entire system becomes unstable which is odd.

Also, I noticed in DMESG that the usb-storage is now ignored for this device just as I wanted, but the same problem seems to be occurring. The device's ZeroCD sector is being shut down, but the dongle is still unable to unmount so it can be modeswitched as demanded in the Rules file. This has me a bit confused as to how to overcome this issue. I think it could be that OR that it DID modeswitch but it just can't find this /dev/ttyUSB0 file which gives it the direction to activate the broadband dongle for communication.

If anyone has any suggestions, please feel free to tell me.

It still never shows up in Network Manager if anyone is curious about that part.

---------------------------------------------------------------

Ok so whats the update for today. I guess that I have to create the ttyUSB0 file so I did that with the :

sudo mknod /dev/ttyUSB0 c 188 0

Command. Not sure if that is right, but it made the ttyUSB0. Now, instead of getting the &#8220;directory or file not found error&#8221;, I now get...

fazl@fazl-laptop:~$ sudo wvdial

--> WvDial: Internet dialer version 1.60

--> Cannot open /dev/ttyUSB0: No such device

--> Cannot open /dev/ttyUSB0: No such device

--> Cannot open /dev/ttyUSB0: No such device

Wonderful. I've exchanged one ignorance of my device for another. Nonetheless, this made me wonder a few things. One, I was wondering if all the commands were linking together properly like the rules knowing the right location of the modprobe and the mode-switch so I checked those out. Turns out that the modprobe was not in the location that the Rules file was looking in so I changed that to match. Next, I am not sure if this is right, but all the information I am looking at says that product ID for the dongle in broadband mode should be 0x0001. I checked my 10-modem.fdi file and noticed that the 0x0001 was in there and so was the 0x2000 so I took out the 2000. Its the ZeroCD anyway and shouldn't need to be there. Then I checked the modeswitch.conf file and it looked like I was changing the device ID to 0x0015 instead of 0x0001 so I changed that also.

I'm just trying to get things lined up but after a hard days work, my brain isn't firing on all cylinders. I hit the command

Wvdialconf

just to see what happens and I got this:

       fazl@fazl-laptop:~$ wvdialconf

       Editing `/etc/wvdial.conf'.

       Scanning your serial ports for a modem.

        WvModem<*1>: Cannot set information for serial port.

        ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud

        ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud

        ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

        Modem Port Scan<*1>: S1 S2 S3

        ttyACM0<Info>: Device or resource busy

        Modem Port Scan<*1>: ACM0 USB0

         Sorry, no modem was detected! Is it in use by another program?

         Did you configure it properly with setserial?

         Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

         If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

So I guess tomorrow is another day. I will have to continue my troubleshooting. Hopefully I will have a clearer head to make some more headway but I don't think I made much today. BTW, the ACM0 device source is my mobile phone.

--------------------------------------------------------------------

Finally... SUCCESS!!!! I followed these instructions and wiped out all the other instructions. This set worked perfectly for my ZTE MF637 dongle. This is not MY information. I copied it from another guy on one of the forums. His posting name was "jfernyhough" so he gets the credit. Thanks man, your method worked better than a charm! Here it is for people who haven't come across it...

jfernyhough 's method

 Howto: Connect ZTE MF627 3G modem with NM0.7
I recently bought a 3G mobile broadband modem and then realised I'd bought the wrong model - instead of getting a Huawei E160 or E169 that reportedly work OOTB with Intrepid I got a ZTE MF627 for which no information exists. On the plus side, it has a built-in MicroSD reader...

I initially raised a bug here but in the meantime have got it working. So here is a how-to.

1) Download and install usb_modeswitch
Go here and download the deb file. A direct link is here. Then install it.

This provides a way of switching the USB modem from its initial useless mode to its correct, functional modes. It will need configuring to apply to the modem.

2) Edit /etc/usb_modeswitch.conf to apply to the MF628+

Either comment the first modem configuration out, then find and uncomment the section for the MF628+, or (more easily) replace the content of the file with:

Code:

########################################################
# ZTE MF628+ (tested version from Telia / Sweden)
#
# Contributor: Joakim Wennergren
#
# Also applies to MF627 (Tested 3 UK) JF

DefaultVendor= 0x19d2
DefaultProduct= 0x2000

TargetVendor= 0x19d2
TargetProduct= 0x0031

MessageEndpoint=0x01
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"

Save it.

3) Create a udev rule to automatically run usb_modeswitch when the modem is plugged in

Create a new file called 999-zte-rules:
gksudo gedit /etc/udev/rules.d/999-zte.rules

Its content should be as follows:
Code:

SUBSYSTEM=="usb", SYSFS{idProduct}=="2000", SYSFS{idVendor}=="19d2", RUN+="/usr/sbin/usb_modeswitch"

This will trigger usb_modeswitch every time you plug in the modem. Which is useful if you want it to work automatically.

4) Add device information to HAL so network-manager recognises the device as a modem

Finally, in order for Network Manager to recognise the modem information has to be added to HAL.

Create a new file:
gksudo gedit /usr/share/hal/fdi/information/20thirdparty/20-zte-mf627.fdi

Its content should be as follows:
Code:

<!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
      <!-- ZTE MF627 HSDPA USB dongle -->
      <match key="@info.parent:usb.vendor_id" int="0x19d2">
        <match key="@info.parent:usb.product_id" int="0x0031">
          <match key="@info.parent:usb.interface.number" int="3">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
            <append key="info.capabilities" type="strlist">modem</append>
          </match>
        </match>
      </match>
  </device>
</deviceinfo>

Save it.

5) Plug in the modem
Make sure the SIM card is in the modem (and if you're using 3 UK make sure you're in a 3G area. otherwise it won't work) and plug it into your PC.

After several seconds the LED should light red as it powers up, then switch to blue when it finds a network. You can check it's working by checking dmesg: you should see entries for GSM modem, USB drive and CD drive. Once modeswitch has been triggered and the modem reboots you will be presented with the ZeroCD device (e.g. containing the 3connect software), a USB MicroSD card reader, and if everything has gone correctly, Network Manager will detect a new mobile broadband modem.

Feel free to ignore the ZeroCD device and unmount it from the desktop.

If everything has gone well dmesg should read something like:
Code:

[52022.169361] usb 5-1: new high speed USB device using ehci_hcd and address 31
[52022.169362] usb 5-1: configuration #1 chosen from 1 choice
[52022.172724] usb-storage: device ignored
[52079.232398] usb 5-1: USB disconnect, address 31
[52189.029694] usb 5-1: new high speed USB device using ehci_hcd and address 32
[52189.177064] usb 5-1: configuration #1 chosen from 1 choice
[52189.192061] usb-storage: device ignored
[52194.546308] usb 5-1: USB disconnect, address 32
[52200.032140] usb 5-1: new high speed USB device using ehci_hcd and address 33
[52200.183440] usb 5-1: configuration #1 chosen from 1 choice
[52200.184979] option 5-1:1.0: GSM modem (1-port) converter detected
[52200.185184] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
[52200.185453] option 5-1:1.1: GSM modem (1-port) converter detected
[52200.185592] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
[52200.200858] scsi28 : SCSI emulation for USB Mass Storage devices
[52200.204904] usb-storage: device found at 33
[52200.204909] usb-storage: waiting for device to settle before scanning
[52200.205113] option 5-1:1.3: GSM modem (1-port) converter detected
[52200.205304] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB2
[52205.205580] usb-storage: device scan complete
[52205.207696] scsi 28:0:0:0: Direct-Access ZTE MMC Storage 2.31 PQ: 0 ANSI: 2
[52205.210603] scsi 28:0:0:1: CD-ROM ZTE USB SCSI CD-ROM 2.31 PQ: 0 ANSI: 2
[52205.226669] sd 28:0:0:0: [sdb] Attached SCSI removable disk
[52205.228914] sd 28:0:0:0: Attached scsi generic sg2 type 0
[52205.345654] sr1: scsi-1 drive
[52205.345837] sr 28:0:0:1: Attached scsi CD-ROM sr1
[52205.346023] sr 28:0:0:1: Attached scsi generic sg3 type 5
[52218.692468] ISO 9660 Extensions: Microsoft Joliet Level 1
[52218.699732] ISOFS: changing to secondary root

(I initially tried to post this in Tips and Tricks but it hasn't appeared yet. I'm posting it here so I at least have it as a record somewhere.)

********END OF QUOTE*********

Well, I am done. I hope everyone learns what a mission it can be to get oddball equipment working on Linux but once it gets done, its satisfying. Happy computing to everyone!!

---

### Post by Fazl on 2009-04-29
Just a little more information about my problem. I am not sure if this ZTE MF637 is considered a modem, but its basically one of those 3G European spec wireless broadband things that you plug into the USB and get high speed internet. I have a PCMCIA card plugged in to provide me USB 2.0 since I have an old IBM T43 whose original USBs no longer work.

The PCMCIA card works fine when I have my memory sticks or other peripherals plugged in but when I plug in this ZTE MF637, the PCMCIA card freezes up and eventually so does my computer. I take it out and reset the card and sometimes it starts to work again (the card, not the ZTE) and sometimes I have to shut the whole computer down.

I really need some help because I am out here in a third world country and I need a good internet connection. The 10kps I am getting from my C380 motorola is just not cutting it!! Can anyone please help!!??

---

