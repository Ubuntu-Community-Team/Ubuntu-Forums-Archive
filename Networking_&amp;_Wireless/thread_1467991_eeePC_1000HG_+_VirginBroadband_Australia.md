---
title: "eeePC 1000HG + VirginBroadband Australia"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by alawson on 2010-05-01
Hi all,

I have an eeePC 1000HG, basically identical to the 1000H but with an integrated 3G modem.

Installed Lucid last night - very smooth install. Thanks to all involved!

Mostly the netbook works fine, the only big problem is the 3G modem will not connect to the network.

I added a "Mobile Broadband" network connection from the network icon at the top right.

The OS has detected a modem, it reports as a "HUAWEI Technology HUAWEI Mobile" in the mobile broadband network setup wizard, and as the follwing with lsusb;

Bus 001 Device 002: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem

I don't know whether that's correct - I can't find information anywhere which definitively specifies which model of modem is in there.... I did find some reference to it being a Huawei E770V, but I don't know if that's true or not. I have installed the modeswitch packages from Synaptic, which made no apparent difference.

I followed the wizard and picked Australia as a location and Virgin Mobile as a provider and Mobile Broadband as a billing plan.

When I try and connect I just get an error saying the connection failed.

The modem worked out of the box under eeebuntu 3.

Can anybody help me resolve this?

Thanks for any assistance!

---

### Post by alexfish on 2010-05-01
Some of the Huawie devices have problems with the ID's

See below

                                 # Huawei E169
#
# Contributor: Dale Lane

;DefaultVendor=  [COLOR=Navy]0x12d1[/COLOR];
;DefaultProduct= [COLOR=Navy]0x1001[/COLOR]

;TargetClass=    0xff

# choose one of these:
;DetachStorageOnly=1
;HuaweiMode=1

########################################################
# Huawei E1550
# Huawei E1750
#
# Contributor: Anders Blomdell, Ahmed Soliman

;DefaultVendor=  0x12d1
;DefaultProduct= 0x1446

;TargetVendor=   [COLOR=Navy]0x12d1[/COLOR]
;TargetProduct=  [COLOR=Navy]0x1001[/COLOR]

# only for reference and 0.x versions
# MessageEndpoint=0x01

;MessageContent="55534243123456780000000000000011060000000000000000000000000000" 

Although the actual device is not listed ; but as you say it did work

try this command from the terminal ; whist the modem is connected and post the results

dmesg | grep -e "modem" -e "tty" 

thanks in advance

alexfish

---

### Post by alawson on 2010-05-01
Thanks for the reply!

Below is the output as requested;

```
andy@little-rascal:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[   12.386826] USB Serial support registered for GSM modem (1-port)
[   12.386940] option 1-6:1.0: GSM modem (1-port) converter detected
[   12.387235] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0
[   12.387277] option 1-6:1.1: GSM modem (1-port) converter detected
[   12.387461] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1
[   12.387499] option 1-6:1.2: GSM modem (1-port) converter detected
[   12.387696] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2
[   12.387781] option: v0.7.2:USB Driver for GSM modems
```

---

### Post by alexfish on 2010-05-01
according to the above the modem is fine :
so it looks like a configuration problem .could be  either your details of your ISP, or the Network Manager via the Modem Manager picking up the wrong port

here is what you can try
1. double check your provider details in Network Manager
2. boot up the computer without the dongle 
3. open up a terminal an enter this command

Code:
tail -f /var/log/syslog


**tail** is a  command which outputs the last 10 lines of a file, with the -f option it  continues to monitor the file and keeps outputing any further additions  appended to the file in real time.


4. plug the dongle and monitor what happens in the terminal/ save this bit to a file
5. try to make a connection with the network manager
6. save the outputs / post the results of both

---

### Post by alawson on 2010-05-01
I'm not sure of the connection settings.
I know I have the right APN, but I can't remember the other bits and bobs. I'll boot it up with an eeebuntu liveCD tomorrow and see if it autosenses correctly and works, then I can make a note of the settings and ensure they're the same in Lucid.

I can't disconnect the modem - it's integrated into the netbook (Asus eeePC 1000HG). There doesn't seem to be a way to disable it except in the BIOS, under Windows and eeebuntu there is eeePC specific software to enable/disable the wifi, webcam, etc. Doesn't seem to be installed by default with Lucid, and I haven't tracked it down yet....

Is there anything I could grep the syslog for that might help?

Thanks for your help!

---

### Post by alexfish on 2010-05-01
Not really

but try 

Code:

cat /var/log/syslog

look for some lines that look like below

May  1 11:35:32 alexfish-desktop modem-manager: (ttyUSB1) opening serial device...
May  1 11:35:32 alexfish-desktop modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
May  1 11:35:32 alexfish-desktop modem-manager: (ttyUSB0) opening serial device...
May  1 11:35:32 alexfish-desktop modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
May  1 11:35:32 alexfish-desktop modem-manager: (ttyUSB2) opening serial device...
May  1 11:35:32 alexfish-desktop modem-manager: (ttyUSB2): probe requested by pl

[COLOR=Navy]May  1 11:37:48 alexfish-desktop modem-manager: (ttyUSB2) opening serial device.[/COLOR]

May  1 11:37:49 alexfish-desktop NetworkManager: <info>  Activation (ttyUSB2) Stage 2 of 5 (Device Configure) scheduled...
[COLOR=Navy]May  1 11:37:49 alexfish-desktop NetworkManager: <info>  Activation (ttyUSB2) Stage 2 of 5 (Device Configure) starting...

[COLOR=Black]What does your log show

 Can you check the versions of the network manager and the modem manager and post these as well

[COLOR=Blue][COLOR=Black]ADDED [/COLOR];if the modem is integrated then still use the the [/COLOR][/COLOR][/COLOR][COLOR=Blue]tail -f /var/log/syslog

also from the above we can check which port the modem manager and network manager is using[/COLOR] [COLOR=Blue]

If your modem has more than one control line then it is important that the Correct tttyX is used ' [/COLOR] [COLOR=Blue]

[/COLOR][COLOR=Navy][COLOR=Black][COLOR=Blue][COLOR=Black]All the above info is necessary ; although suggestions can  be made ;but  We need to confirm [/COLOR][/COLOR][/COLOR][/COLOR], you will notice from some  threads some use wvdial or other method to get a connection ; IE: they can force the modem to use the correct port if it has more than one control line

the reason / 

[http://ubuntuforums.org/showthread.php?t=1466490](http://ubuntuforums.org/showthread.php?t=1466490)
[COLOR=Blue][COLOR=Black]
[/COLOR][/COLOR] [COLOR=Navy][COLOR=Black][COLOR=Blue][COLOR=Black] thanks in advance


[/COLOR][/COLOR] 
alexfish
[/COLOR][/COLOR]

---

### Post by pdc on 2010-05-01
Virgin Australia 

I wonder if "disable CHAP" is the issue ......... one needs to do that for Virgin Oz .........

the APN settings I believe are 

> VirginInternet........ I guess that is okay for you and already set?
	
and the advice from here 


[https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

is 

> Need to **disable CHAP** (via Network Manager, edit settings, PPP settings tab) 

...... sounds to me like the modem is seen and you have configured;

can I suggest you RIGHT-CLICK on network manager; select edit connections; select to edit your virgin entry:

select the PPP Settings tab;

Click on the Configure Methods tab;

turn off the CHAP button; save; close;

now left-click network manager; select Virgin ; any joy?

---

### Post by alawson on 2010-05-02
Thanks, alexfish.

I contacted VirginMobile, and it looks like the settings are okay. The only change they recommend is that authentication be set to PAP only. As stated by pdc above, disable CHAP, and then I went on and disabled EAP, MSCHAP and MSCHAPv2 also. Otherwise the settings defined by the setup wizard when you create the connection are fine. This SIM is on a VirginBroadband plan, so I had to select Mobile Broadband, instead of Mobile Internet at the third (I think) dialogue in the wizard.

This didn't help tho. Thanks for trying pdc!

So I tried running a tail -f on the syslog and activating the connection in network manager and I got the following;

```
May  2 21:44:37 little-rascal NetworkManager: <info>  Activation (ttyUSB0) starting connection 'Virgin Mobile Mobile Broadband'
May  2 21:44:37 little-rascal NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 (reason 0)
May  2 21:44:37 little-rascal NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
May  2 21:44:37 little-rascal NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
May  2 21:44:37 little-rascal NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
May  2 21:44:37 little-rascal NetworkManager: <WARN>  stage1_prepare_done(): GSM modem connection failed: (32) Sending command failed: device is not enabled
May  2 21:44:37 little-rascal NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 9 (reason 1)
May  2 21:44:37 little-rascal NetworkManager: <info>  Marking connection 'Virgin Mobile Mobile Broadband' invalid.
May  2 21:44:37 little-rascal NetworkManager: <info>  Activation (ttyUSB0) failed.
May  2 21:44:37 little-rascal NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 (reason 0)
May  2 21:44:37 little-rascal NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0).
May  2 21:44:37 little-rascal modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (connected -> disconnecting)
May  2 21:44:37 little-rascal modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (disconnecting -> connected)
```

Of interest to me is this little snippet;

```
May  2 21:44:37 little-rascal NetworkManager: <WARN>  stage1_prepare_done(): GSM modem connection failed: (32) Sending command failed: device is not enabled
```

Which I think indicates that the modem is not working. From a bit of closer inspection I reckon the modem might be a Huawei EM770 - any ideas how to configure one of these?

Cheers!

---

### Post by alawson on 2010-05-02
I found this bug listed;
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/441177](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/441177)

Which seems to pretty much describe my problem, but following that thread into another bug (446146) indicates that its already been fixed....

Can anyone interpret the bug listings and tell me what I'm sposed to do to fix this?

Thanks!

---

### Post by alexfish on 2010-05-03
hi

looking at the above 

1.the modem may have a fault if the control line for the modem ,port{ttyx} is correct;
2.the wrong control line is been selected by the system, ie the modem manager is enumerating the device on the wrong port.
3 or definitely a bug / but I also remember this modem did work on Lucid pre releases

try to configure the modem with [SIZE=2]ppp[/SIZE] look at the thread below ;and when you get to the bit about the Ports try the different ports listed from your outputs highlighted in red
[   12.387235] usb 1-6: GSM modem (1-port) converter now attached to [COLOR=Black]ttyUSB0[/COLOR]
[   12.387277] option 1-6:1.1: GSM modem (1-port) converter detected
[   12.387461] usb 1-6: GSM modem (1-port) converter now attached to [COLOR=Red]ttyUSB1[/COLOR]
[   12.387499] option 1-6:1.2: GSM modem (1-port) converter detected
[   12.387696] usb 1-6: GSM modem (1-port) converter now attached to [COLOR=Red]ttyUSB2[/COLOR]


[http://ubuntuforums.org/showthread.php?t=1466490](http://ubuntuforums.org/showthread.php?t=1466490)

Post #11 example PPP { pap }



regards

alexfish

---

### Post by alexfish on 2010-05-06
Hi

have looked up the modem manager as regards the above bugs reports

may be installing git will help to resolve the problems , but can't say 

                                 

 [http://cgit.freedesktop.org/ModemManager/ModemManager/](http://cgit.freedesktop.org/ModemManager/ModemManager/)
 

 [http://sourceforge.net/apps/mediawiki/mbm/index.php?title=MBM](http://sourceforge.net/apps/mediawiki/mbm/index.php?title=MBM)
 

 [https://help.ubuntu.com/community/Git](https://help.ubuntu.com/community/Git)

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by alawson on 2010-05-06
Thanks for all your help, alexfish.

I don't have the skills necessary to install anything that complex, and I need to use the PC now, so I'll have to revert to XP for a bit. Do you think a general resolution is in the pipeline?

Bummer.

---

### Post by alexfish on 2010-05-07
Hi

as a workaround you could Try PPP , it also has a wizard , 

and select the tty ports manually ,you would have to try each one in turn 

have a look here 

                                 

 [http://ubuntuforums.org/showthread.php?t=1466490](http://ubuntuforums.org/showthread.php?t=1466490)
 

  post #11 , but also read throw the first post


don't be afraid to experiment with the connection as there quite easy to edit


the answer to bugs etc , bugs in ubuntu are usually device relative, and sometimes it takes a few weeks to iron out, or you could try out Ubuntu 9.04 then come back to 10.04 when it is more stable ,if you have alternate means of connection then wait for the updates, 



regards


alexfish

---

### Post by Paqman on 2010-07-29
I can confirm that this device is now working OOTB on Lucid.

---

