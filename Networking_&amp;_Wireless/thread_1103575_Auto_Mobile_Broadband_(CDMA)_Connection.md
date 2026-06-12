---
title: "Auto Mobile Broadband (CDMA) Connection"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by carterw65 on 2009-03-22
Hey all. I am using a Pantech PX-500 card from Sprint. Everything was working just fine until I did a system update and it changed the card to USB1 from USB0. I went in and changed the conf file for wvdial to USB1 and all is well there. But, when I try to use the Auto Mobile Broadband (CDMA) Connection it is still set to USB0 and I can't figure out how to change it. I tried deleting and reconfiguring, but it still goes to USB0.

Any thoughts?   :?:

Thanks,
Bill

---

### Post by carterw65 on 2009-03-23
Does anyone have any idea about this?

---

### Post by carterw65 on 2009-03-23
Does anyone have any idea about this?

---

### Post by GeorgeVita on 2009-03-23
Hi **carterw65**, some thoughts and questions to help "investigation"! 

what version of Ubuntu are you using?
Are you trying to connect running **wvdial** program or using Network Manager?
How did you first configure your modem? Is it detected automatically by the system or you used any other terminal command (modprobe usbserial ...)? Did you (in past) "trim" any other file which maybe now restored to defaults because of recent update?

Regards,
George

---

### Post by carterw65 on 2009-03-23
> **GeorgeVita said:**
> Hi **carterw65**, some thoughts and questions to help "investigation"! 

what version of Ubuntu are you using?
Are you trying to connect running **wvdial** program or using Network Manager?
How did you first configure your modem? Is it detected automatically by the system or you used any other terminal command (modprobe usbserial ...)? Did you (in past) "trim" any other file which maybe now restored to defaults because of recent update?

Regards,
George

I am using Ubuntu 8.10. I am using the network manager. I am not sure how this was originally configured, I did so many things to get the card to work. I was using wvdial and stumbled upon the network manager and it worked, although it would arbitrarily disconnect (very annoying sometimes). The card used to work on USB0 on both wvdial and network manager and for some reason it switched to USB1 and I had the change the wvdial file. I don't know how to get network manager to switch to USB1.

As far as the updates are concerned. I just update the system when it says updates are available. I am not savvy enough to know what is good or bad with them.

Thanks for your help!

---

### Post by carterw65 on 2009-03-23
When I try to connect with the network manager, it says "Dialing Mobile Broadband Device ttyUSB0..."

It then fails and says "The network connection has been disconnected".

---

### Post by GeorgeVita on 2009-03-24
Do some tests as below:

Open a terminal window, type **lsusb** (or **lspci**) to see actual vendor/product numbers of your modem. Copy here the results.

Boot with and without the modem inserted, wait for the system to stabilize, and from terminal: **ls /dev/ttyUSB*** to find all serial communication ports.

Do you have any other serial communication device that using /dev/ttyUSB0 ?

G

---

### Post by DDR524US on 2009-04-08
I'm having the exact same problems as carterw65.  Last worked several months ago, now same same message:

> When I try to connect with the network manager, it says "Dialing Mobile Broadband Device ttyUSB0..."

It then fails and says "The network connection has been disconnected". 

Any ideas?

---

### Post by GeorgeVita on 2009-04-09
Hi **DDR524US**,

please boot without the modem, wait the system to stabilize, attach the modem, wait 15-20 seconds try the following terminal commands:

**dmesg**
**lsusb**
**ls /dev/ttyU***

Post here the last lines of dmesg (concerning /dev/ttyUSBx and usbserial) and also the output of the other two commands.

Regards,
George

---

### Post by DDR524US on 2009-04-09
Thanks for the Reply George. The response to dmseg was lengthly, I hope I've included the section that is pertinent.

> [  317.177010] ohci_hcd 0000:06:00.1: irq 17, io mem 0x54001000
[  317.262812] usb usb5: configuration #1 chosen from 1 choice
[  317.263666] hub 5-0:1.0: USB hub found
[  317.264051] hub 5-0:1.0: 1 port detected
[  321.088054] usb 4-1: new full speed USB device using ohci_hcd and address 2
[  321.300598] usb 4-1: configuration #1 chosen from 1 choice
[  321.752312] usbcore: registered new interface driver usbserial
[  321.753546] usbserial: USB Serial support registered for generic
[  321.754702] usbcore: registered new interface driver usbserial_generic
[  321.754712] usbserial: USB Serial Driver core
[  321.765291] usbserial: USB Serial support registered for GSM modem (1-port)
[  321.766711] option 4-1:1.0: GSM modem (1-port) converter detected
[  321.768204] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[  321.769526] option 4-1:1.1: GSM modem (1-port) converter detected
[  321.770901] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[  321.772273] option 4-1:1.2: GSM modem (1-port) converter detected
[  321.773641] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[  321.774953] usbcore: registered new interface driver option
[  321.774963] option: USB Driver for GSM modems: v0.7.2
[  321.878342] usbcore: registered new interface driver cdc_acm
[  321.879697] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters

> agatha@Laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 106c:3702 Curitel Communications, Inc. Pantech PX-500
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Did I type this command correctly?
> agatha@Laptop:~$ ls/dev/ttyU*
bash: ls/dev/ttyU*: No such file or directory


I am running 8.10 Ubuntu and had successfully been using the Sprint PX-500 aircard for several months without issue.  I don't know precisely when it stopped functioning as I normally use this laptop with wireless access to my home network.  When I took the laptop on a trip, I found found the Pantech PX-500 had stopped working.  I had not made any changes to the system other than the automated updates.buntu 

Any help would be appreciated, I am new to Ubuntu so I'll probably need the a bit more detail if remedial actions are necessary.

Regards,
DDR

---

### Post by techlive on 2009-04-09
Hi All,

I am using BSNL EVDO Broadband connection in India, I am using this connection using wvdial utility , but I think there is an option in Network Manager to configure it to connect automatically at boot/login...please help..

Thanks in Advance!

---

### Post by GeorgeVita on 2009-04-09
Hi **DDR524US**,

the **dmesg** command shows all system activity, which seems to setup 3 ports for your modem, **lsusb** command shows all USB peripherals attached and their vendor : product IDs and **ls /dev/ttyU*** (there is a space after **ls**) will list all these serial communication ports.

Your modem exists in Systems info so it should work directly with Network Manager. Please Delete and Add again the connection: right click Network Manager icon (2 PC screens), Edit connections, Mobile Broadband, click on your provider if exists and delete this entry, Add again selecting your provider (check country also). Be careful to choose the right connection type if there are more than one.

Then Edit again this connection and see the **Number** and **APN** setting. Check with your provider if these are correct. Post here these data and your country/provider/account type (if any) to check also.

As general note I suppose you have NO SIM PIN CHECK and your SIM is useable for data connection.

--------
Hi **techlive**,
please supply the info asked in post#9 of this thread (i suppose it is on previous page). Add also your country/provider/account type (if any) in case we need them.

Regards,
George

---

### Post by DDR524US on 2009-04-09
Still no luck.

I deleted Auto Mobile Broadband (CDMA) Connection in Network Manager, then reinserted the PCI Card PX-500.  My carrier is Sprint, so I could not use the edit provider screen.  

Network Manager detects the aircard, and lists the number (#777) which is correct according to the PDF "Wireless Mobile Broadband Setup Guide for Linux OS".  What is the **APN** setting?  I didn't see a window for it.

I corrected the command ls /dev/ttyU* and here are the results:
> agatha@Laptop:~$ ls /dev/ttyU*
/dev/ttyUSB0  /dev/ttyUSB1  /dev/ttyUSB2

The PX-500 does not have a SIM card that I am aware of.

Any thoughts?

Again, thanks.
DDR

---

### Post by GeorgeVita on 2009-04-10
From post#4 of [http://ubuntuforums.org/showthread.php?p=6939331](http://ubuntuforums.org/showthread.php?p=6939331)
and post#1 of [http://ubuntuforums.org/showthread.php?t=343989](http://ubuntuforums.org/showthread.php?t=343989)

I found also that you have to fill in (not shown within your posts):
**Username**: 1234567890 @ sprintpcs.com (replace 1234567890 with data card&#8217;s &#8220;phone number&#8221;, no dashes, no spaces)
**Password**: your sprint password

In case the above does not work, below is the connecting method via wvdial:

Open a terminal window and run: **sudo gedit /etc/wvdial.conf**
Copy paste the following into file (delete old lines if exist):

[Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 115200
Username = **1234567890 @ sprintpcs.com** (NO SPACES, replace 1234567890 with real phone No.)
Password = **your sprint password**
Phone = #777
Stupid Mode =1
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
#Init3 =AT+CGDCONT=1,"IP","internet"
#Init4 = ATM0

Save and Exit from gedit.

From a terminal window run: **sudo wvdial**
Click on Firefox icon, remove **Work Offline** mode with **ALT+F W** and browse.
In case of disconnection post the output here.

Regards,
George

---

### Post by techlive on 2009-04-11
Hi George,

I am attaching the results of the commands mentioned in reply#9.

---

### Post by GeorgeVita on 2009-04-11
We are trying to ADD a new file with the specific vendor and product IDs. The HAL will (?) see it as a CDMA modem and help Network Manager do the rest? Lets try it!

Open a terminal window:
**sudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem_Q.fdi**

Copy the following code into the text editor window:

```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- xml -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="info.category" string="serial">

<!-- ***************************************************** 
	ID 05c6:3197 Qualcomm, Inc. CDMA Wireless Modem/PhoneUSB devices
     ***************************************************** --> 
      <match key="@info.parent:usb.vendor_id" int="0x05c6">
        <match key="@info.parent:usb.product_id" int="0x3197">
          <match key="@info.parent:usb.interface.number" int="0">
            <append key="modem.command_sets" type="strlist">IS-707-A</append>
          </match>
        </match>
      </match>

<!-- ***************************************************** 
			generic keys
     ***************************************************** --> 

      <!-- set common properties for all above matched modem devices -->
      <match key="modem.command_sets" exists="true">
        <append key="info.capabilities" type="strlist">modem</append>
      </match>

    </match>
  </device>
</deviceinfo>

```

Save, Exit from gedit. Shut down. Boot without the modem, wait for the system to stabilize, plug in the modem. After a while a message will appear over the Network Manager icon (2 PC screens up right) and help you create a Mobile Broadband connection. After created, click to Network Manager icon, and click to your provider. You must be connected!

If the wizard does not appear right click Network Manager icon, Edit Connections, Mobile Broadband, Add, check Country and select provider.

G

---

### Post by lswb on 2009-04-11
Just FYI, as a kind of backdoor way to change NM configuration, Network Manager stores it's settings in the gconf database. If you can't find out how to change the USBx setting from the NM user interface, try Main Menu/Applications/System Tools/Configuration Editor, then in the Config editor application, select Edit/Find, check the 2 "Search also...." boxes, and search for USB0. If you find a key that looks like it is used by Network Manager, you could try changing it to USB1 and see if that works.

---

### Post by GeorgeVita on 2009-04-12
Hi **lswb**, thanks for the suggestion!

With menus of 8.10 I had to ADD it:
- right click on Applications
- Edit Menus
- System Tools
- Configuration Editor
- Close

I also try searching for all combinations of USB like USB0 USB1 ... ttyUSB0 ttyUSB1 ... /dev/ttyUSB0 ... and nothing found!

Can you suggest a search string (from any configuration) that will give a hit to check it? Do I have to use other level of permissions to search?

Thanks,
George

---

### Post by lswb on 2009-04-14
I don't have any other suggestions for finding the gconf key that NM uses. I use 8.04 for daily use rather than 8.10 and there are some differences in NM between the 2. However, it occurs to me that (in my experience anyway) a CDMA modem gets a device name like ttyACM0 rather than ttyUSB0. I see from the dmesg output you posted that your device registers several USB serial devices as well as an acm device. If you have a /dev/ttyACM0 device after installing the card, you could try using that as the device name instead of ttyUSBx. 

I do have 8.10 installed (though rarely used) on a different partition on my system and I have configured a CDMA cell phone as a tethered modem using the ttyACM0 device. I did this using pppconfig rather than using NM though. For me it was less headaches, IMHO Network Manager is not ready for prime time yet.

---

### Post by DDR524US on 2009-05-01
I never was able to get my Sprint Pantech aircard to work.  However, upon upgrading to Ubuntu 9.04, it works now perfectly.  I'm at a loss to explain why it worked for several months under 8.10 then stopped.  Perhaps some updates changed a setting?

Thanks to all who volunteered suggestions.

---

