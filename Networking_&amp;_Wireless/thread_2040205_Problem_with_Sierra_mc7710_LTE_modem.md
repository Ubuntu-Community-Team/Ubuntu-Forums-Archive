---
title: "Problem with Sierra mc7710 LTE modem"
date: 2012-08-10
forum: Networking &amp; Wireless
---

### Post by mansson on 2012-08-10
Hi,

I have a new Vaio laptop with a built-in 4G LTE modem Sierra mc7710 that I can't get to work in Ubuntu, it works perfect in Windows.
 
The first problem seams to be that the radio is not enabled, it stays in Low power mode
```
AT!GSTATUS?
!GSTATUS: 
Current Time:  602              Temperature: 3t 5
Bootup Time:   1                Mode:        LOW POWER MODE 
System mode:   Unknown          PS state:    Not attached 
GMM (PS) state:DEREGISTERED     NO SERVICE     
MM (CS) state: IDLE             NO SERVICE     


```I have tried with AT+CFUN=1 to enable the radio but there is no difference. In Windows when I have enabled the modem AT!GSTATUS show that the modem is connected and not in Low Power Mode.

I have tried with different version of the kernel even 3.6.0 rc1 but without success. I have tried both via network-manager and with sierra ip direct

---

### Post by bmork on 2012-08-28
> **mansson said:**
> Hi,

I have a new Vaio laptop with a built-in 4G LTE modem Sierra mc7710 that I can't get to work in Ubuntu, it works perfect in Windows.
 
The first problem seams to be that the radio is not enabled, it stays in Low power mode
```
AT!GSTATUS?
!GSTATUS: 
Current Time:  602              Temperature: 3t 5
Bootup Time:   1                Mode:        LOW POWER MODE 
System mode:   Unknown          PS state:    Not attached 
GMM (PS) state:DEREGISTERED     NO SERVICE     
MM (CS) state: IDLE             NO SERVICE     


```I have tried with AT+CFUN=1 to enable the radio but there is no difference. In Windows when I have enabled the modem AT!GSTATUS show that the modem is connected and not in Low Power Mode.


What does
```

rfkill list

```display? The MC7710 can be configured to either power off or enter low power mode on an external rfkill signal.  Maybe the problem is that Sony has configured it for low power mode?


> 
I have tried with different version of the kernel even 3.6.0 rc1 but without success. I have tried both via network-manager and with sierra ip directI don't think the DirectIP drivers will work with the default configuration of the MC7710 in a Vaio, but I am very interested in having that assumption confirmed.  Is the device ID 1199:68a2? dmesg or lsusb will tell you.

A full dmesg dump right after boot is interesting in any case.  There might be issues with some ACPI or WMI driver on such a new laptop, and this could very well cause problems like unwanted rfkill blocking.

BTW, Did you build the qmi_wwan driver in the 3.6.0 rc1 kernel? Did it load successfully, giving you /dev/cdc-wdmX and wwanY devices?

---

### Post by mansson on 2012-09-16
> **bmork said:**
> What does
```

rfkill list

```display? The MC7710 can be configured to either power off or enter low power mode on an external rfkill signal.  Maybe the problem is that Sony has configured it for low power mode?

Yes it seams like it's low power mode. I had actually to enable the modem in Windows or I wouldn't see it at all with lsusb or /dev/ttyusb0-2 didn't show up neither. When I have enabled the modem in Windows with the Sony network tool kit then it showed up in Linux as well.
> 
I don't think the DirectIP drivers will work with the default configuration of the MC7710 in a Vaio, but I am very interested in having that assumption confirmed.  Is the device ID 1199:68a2? dmesg or lsusb will tell you.
The device ID is correct
Bus 001 Device 006: ID 1199:68a2 Sierra Wireless, Inc. 
```

rfkill list
0: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: sony-wwan: Wireless WAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```> 
A full dmesg dump right after boot is interesting in any case.  There might be issues with some ACPI or WMI driver on such a new laptop, and this could very well cause problems like unwanted rfkill blocking.

BTW, Did you build the qmi_wwan driver in the 3.6.0 rc1 kernel? Did it load successfully, giving you /dev/cdc-wdmX and wwanY devices?The dmesg dump is here [URL="http://pastebin.com/GUdTxykG"]http://pastebin.com/GUdTxykG
[/URL] 
/dev/cdc-wd1 are there but not /dev/wwanY

---

### Post by bmork on 2012-09-16
> **mansson said:**
> Yes it seams like it's low power mode. I had actually to enable the modem in Windows or I wouldn't see it at all with lsusb or /dev/ttyusb0-2 didn't show up neither. When I have enabled the modem in Windows with the Sony network tool kit then it showed up in Linux as well.

 And it was after this it was locked in low power mode in Linux?

> 
The device ID is correct
Bus 001 Device 006: ID 1199:68a2 Sierra Wireless, Inc. 
Right.  That is what I expected.  It means that the MC7710 card is in QMI mode, and supported by the qmi_wwan and qcserial drivers in recent kernels.

> 
```

rfkill list
0: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: sony-wwan: Wireless WAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```Well, that looks good.  The *sony-wwan* device is recognized, and is not blocked.
> 
The dmesg dump is here [URL="http://pastebin.com/GUdTxykG"]http://pastebin.com/GUdTxykG
[/URL] Weird.  I cannot see the module mentioned at all there.  Which is obviously bogus as it shows up in the lsusb output and drivers are loaded and working (must be as you can issue AT commands to the module).

> 
/dev/cdc-wd1 are there but not /dev/wwanYThe last one should be a netdevice.  It will show up as wwan0 if you do 
"ifconfig -a" or "ip link show".


I have tried a few settings on my MC7710 module, but I am unable to recreate a problem similar to this.  Could you try a few AT show commands and see if there is something obvious in the output (I am including the output from my module for reference):

```

at!custom?
!CUSTOM: 
            PUKPRMPT            0x01
            MEPCODE             0x01
            ISVOICEN            0x02
            PRLREGION           0x01
            PCSCDISABLE         0x03
            GPSENABLE           0x01
            GPSLPM              0x01


OK
at!pcinfo?
State: 1 (ONLINE)
LPM force flags - W_DISABLE:0, User:0, Temp:0, Volt:0
W_DISABLE: 0
Poweroff mode: 1
LPM Persistent: 0


OK
at+cfun=0
OK
at!pcinfo?
State: 0 (LPM)
LPM force flags - W_DISABLE:0, User:1, Temp:0, Volt:0
W_DISABLE: 0
Poweroff mode: 1
LPM Persistent: 0


OK

```The "LPM force flags" should indicate why the module is in LPM.  "W_DISABLE" is the PCIe input pin used by the rfkill switch. "User" means that LPM was enabled using AT commands (or another user control protocol like CnS or QMI). "Temp" and "Volt" means the module powered down due to sensor readings outside the acceptable range.  And I believe the "LPM Persistent" setting is also interesting here.  But even if I tried to enable it, I could not recreate your problem.  The module stil worked as expected, starting up in whatever mode it was shut down in, but still allowing me to enter online mode using AT+CFUN=1

---

### Post by mansson on 2012-09-16
> **bmork said:**
> And it was after this it was locked in low power mode in Linux?

It's in low power mode in Linux, before I enabled the modem in Windows it was not visible at all in Linux, lsusb didn't show the modem.
> 
Right.  That is what I expected.  It means that the MC7710 card is in QMI mode, and supported by the qmi_wwan and qcserial drivers in recent kernels.

Well, that looks good.  The *sony-wwan* device is recognized, and is not blocked.
Weird.  I cannot see the module mentioned at all there.  Which is obviously bogus as it shows up in the lsusb output and drivers are loaded and working (must be as you can issue AT commands to the module).

The last one should be a netdevice.  It will show up as wwan0 if you do 
"ifconfig -a" or "ip link show".
```
ifconfig -a show
wwan0     Link encap:Ethernet  HWaddr 1a:a8:9d:3d:e3:ca  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```> 
I have tried a few settings on my MC7710 module, but I am unable to recreate a problem similar to this.  Could you try a few AT show commands and see if there is something obvious in the output (I am including the output from my module for reference):

```

at!custom?
!CUSTOM: 
            PUKPRMPT            0x01
            MEPCODE             0x01
            ISVOICEN            0x02
            PRLREGION           0x01
            PCSCDISABLE         0x03
            GPSENABLE           0x01
            GPSLPM              0x01


OK
at!pcinfo?
State: 1 (ONLINE)
LPM force flags - W_DISABLE:0, User:0, Temp:0, Volt:0
W_DISABLE: 0
Poweroff mode: 1
LPM Persistent: 0


OK
at+cfun=0
OK
at!pcinfo?
State: 0 (LPM)
LPM force flags - W_DISABLE:0, User:1, Temp:0, Volt:0
W_DISABLE: 0
Poweroff mode: 1
LPM Persistent: 0


OK

``````

at!custom?
!CUSTOM: 
            PUKPRMPT            0x01
            MEPCODE             0x01
            ISVOICEN            0x02
            PRLREGION           0x01
            PCSCDISABLE         0x03
            GPSENABLE           0x01
            AUTONETWORKMODE     0x02
            GPSLPM              0x01
            GPSSEL              0x01

at!pcinfo?
State: 0 (LPM)
LPM force flags - W_DISABLE:1, User:1, Temp:0, Volt:0
W_DISABLE: 1
Poweroff mode: 0
LPM Persistent: 0

at+cfun=0
OK

at!pcinfo?
State: 0 (LPM)
LPM force flags - W_DISABLE:1, User:1, Temp:0, Volt:0
W_DISABLE: 1
Poweroff mode: 0
LPM Persistent: 0


OK

OK

```> 
The "LPM force flags" should indicate why the module is in LPM.  "W_DISABLE" is the PCIe input pin used by the rfkill switch. "User" means that LPM was enabled using AT commands (or another user control protocol like CnS or QMI). "Temp" and "Volt" means the module powered down due to sensor readings outside the acceptable range.  And I believe the "LPM Persistent" setting is also interesting here.  But even if I tried to enable it, I could not recreate your problem.  The module stil worked as expected, starting up in whatever mode it was shut down in, but still allowing me to enter online mode using AT+CFUN=1I tried CFUN=1 but it's the same output
```

OK
at+cfun=1
OK
at!pcinfo?
State: 0 (LPM)
LPM force flags - W_DISABLE:1, User:1, Temp:0, Volt:0
W_DISABLE: 1
Poweroff mode: 0
LPM Persistent: 0

OK

```

---

### Post by bmork on 2012-09-17
> **mansson said:**
> ```

at!pcinfo?
State: 0 (LPM)
LPM force flags - W_DISABLE:1, User:1, Temp:0, Volt:0
W_DISABLE: 1
Poweroff mode: 0
LPM Persistent: 0


OK

```

Right.  That was very useful.  It confirms my first thought:  The  W_DISABLE input is asserted, and the card is configured to go to LPM  instead of powering down on this signal.

So that means the the  rfkill output was wrong.  The rfkill signal is in fact active, and that is why  you cannot disable LPM.  I have no idea how to fix that, but it could be  a simple matter of updating the sony-laptop driver with details of this  laptop.  I suggest you contact the maintainer of that driver with as  much info as possible about your laptop and the problem.  According to  the get_maintainer script, that would be

```

Mattia Dongili <malattia@linux.it> (maintainer:SONY VAIO CONTROL...)
Matthew Garrett <mjg@redhat.com> (maintainer:X86 PLATFORM DRIVERS)
platform-driver-x86@vger.kernel.org (open list:SONY VAIO CONTROL...)

```

---

### Post by mansson on 2012-09-18
Thank you[SIZE=2] [/SIZE][SIZE=2]Bjørn, I will do that [/SIZE]

---

### Post by bmork on 2012-10-15
Just for reference, this bug now seems to be resolved upstream:
[https://bugzilla.kernel.org/show_bug.cgi?id=47751](https://bugzilla.kernel.org/show_bug.cgi?id=47751)


Bjørn

---

### Post by iklymov on 2012-10-16
Well, actually no (I'm the author of that bugreport). I can connect to modem, it registers in network, but never connects for actual data transfer:
```

AT!GSTATUS?
!GSTATUS: 
Current Time:  1350             Temperature: 32
Bootup Time:   1                Mode:        ONLINE         
System mode:   WCDMA            PS state:    Attached     
WCDMA band:    WCDMA 2100 
WCDMA channel: 10662
GMM (PS) state:REGISTERED       NORMAL SERVICE 
MM (CS) state: IDLE             NORMAL SERVICE 

WCDMA L1 State:L1M_PCH_SLEEP    RRC State:   DISCONNECTED   
RX level C0:   -68              LAC:         1389 (5001)
RX level C1:   -106             Cell ID:     01F5C481 (32883841)


OK
AT+CGDCONT?
+CGDCONT: 1,"IP","3g.utel.ua","0.0.0.0",0,0
+CGDCONT: 2,"IP","3g.utel.ua","0.0.0.0",0,0

OK
AT!SCACT=1,1
+CME ERROR: no network service


```
Any suggestions? (PPP mode do not work also, i can connect with this APN on my windows)

---

### Post by bmork on 2012-10-16
> **iklymov said:**
> Well, actually no (I'm the author of that bugreport). I can connect to modem, it registers in network, but never connects for actual data transfer:
```

AT!SCACT=1,1
+CME ERROR: no network service


```Any suggestions? (PPP mode do not work also, i can connect with this APN on my windows)

PPP should work, so there are probably more issues here...

But the AT!SCACT error is expected.  That will only work if the modem is in DirectIP mode, and AFAIK the Vaio module is running in QMI mode by default.  I would leave it that way too, if I were you. Sony may whitelist these modules, and changing the mode will change the USB PID.  If they are as difficult as Lenovo then the laptop won't even boot if the whitelist check fails.

To connect the wwan0 interface in QMI mode you will need to use QMI.  ModemManager support for that is in progress, but not quite ready for production yet. But you can use the cli tools coming with libqmi (which the MM support will be based on). See
[http://lists.freedesktop.org/mailman/listinfo/libqmi-devel](http://lists.freedesktop.org/mailman/listinfo/libqmi-devel)
[http://cgit.freedesktop.org/libqmi]("http://cgit.freedesktop.org/libqmii")

I typically connect manually like this:
```

 qmicli -d /dev/cdc-wdm0  --dms-uim-verify-pin=PIN,xxxx
 qmi-network /dev/cdc-wdm0 start
 dhclient -d -4 wwan0

```This will of course be a lot simpler once the MM support is ready and NetworkManager supports the new MM version (which is not quite there yet, either)

Note that all this is about wwan0.  Using ppp over the ttyUSBx supporting AT commands (most likely ttyUSB2) should just work as with any 3G modem.  So if you can't get that working then there is something else we need to sort out.


Bjørn

---

### Post by iklymov on 2012-10-16
```
--> Waiting for carrier.
ATDT*99***1#
CONNECT 100000000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Oct 16 21:50:54 2012
--> Pid of pppd: 11021
--> Using interface ppp0
```
And stuck indefinitely (no IP adresses received)

UPDATE: qmicli working, PPP not

---

### Post by noonien on 2012-10-16
Now it finaly works for me using a patched arch kernel (3.6.1) and qmi-network on a Sony S-Series SVS1311C5E - seems to be similar architecture.

Thanks everyone for your work!

---

### Post by bmork on 2012-10-17
> **iklymov said:**
> ```
--> Waiting for carrier.
ATDT*99***1#
CONNECT 100000000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Oct 16 21:50:54 2012
--> Pid of pppd: 11021
--> Using interface ppp0
```And stuck indefinitely (no IP adresses received)

UPDATE: qmicli working, PPP not

Great that something is working.

Regarding the PPP, you could try running pppd with the "debug" option and see what happens.  Sounds like it is connecting but something fails during authentication or IPCP.  Maybe you are requesting some IP addresse the peer doesn't like or something.  The only way to find out is looking at the debug output.

---

### Post by mansson on 2012-11-01
Hi,

I can confirm that it works for me as well with qmicli. I am running 3.6.1

Thank you very much for the effort. I am looking forward to have it integrated in the manager

/Ulf

---

### Post by mansson on 2012-11-07
Hmm,

I was a little bit quick there. It works sometimes and fails sometimes

I run 
```
sudo qmi-network /dev/cdc-wdm1 start

```
and most of the time I get this
```
Starting network with 'qmicli -d /dev/cdc-wdm1 --wds-start-network=  --client-no-release-cid'...
error: couldn't start network: QMI protocol error (14): 'CallFailed'
call end reason (3): generic-no-service
verbose call end reason (2,204): [internal] unknown-cause
Saving state... (CID: 53)
error: network start failed, no packet data handle
Clearing state...
```

And then after several tries it works, but sometimes it doesn't work at all. I have no clue  why it works some time and some not

---

### Post by bmork on 2012-11-10
> **mansson said:**
> Hmm,

I was a little bit quick there. It works sometimes and fails sometimes

I run 
```
sudo qmi-network /dev/cdc-wdm1 start

```and most of the time I get this
```
Starting network with 'qmicli -d /dev/cdc-wdm1 --wds-start-network=  --client-no-release-cid'...
error: couldn't start network: QMI protocol error (14): 'CallFailed'
call end reason (3): generic-no-service
verbose call end reason (2,204): [internal] unknown-cause
Saving state... (CID: 53)
error: network start failed, no packet data handle
Clearing state...
```And then after several tries it works, but sometimes it doesn't work at all. I have no clue  why it works some time and some not

This is where full ModemManager support will make a big difference.  What you are seeing is either a network registration problem or a reject from the network for some reason. There really isn't much else you can do about it than what you already found out: Try again.

No, this user interface isn't very friendly.  But that is because these tools never were intended to be anything but development helpers.  Please take it for what it is, and help finishing the ModemManager/NetworkManager integration if you have the ability to do that.  It cannot explain those error codes any better, but it will give you signal monitoring and other useful realtime quality measurements which will help you debugging connectivity problems.

---

### Post by Kondor71 on 2012-11-11
Where did you find MC7710 module in your system? I cannot find it to improve my settings...

lsusb and rfkill -list show that my system has find the modem....

---

### Post by bmork on 2012-11-11
> **Kondor71 said:**
> Where did you find MC7710 module in your system? I cannot find it to improve my settings...

lsusb and rfkill -list show that my system has find the modem....

I do not understand what you mean here.  Please show us what you do see, and explain why you expect to see something else.

Most people should expect to **not** find a MC7710 module in their system.  That's normal ;-)

---

### Post by mansson on 2012-11-11
> **bmork said:**
> This is where full ModemManager support will make a big difference.  What you are seeing is either a network registration problem or a reject from the network for some reason. There really isn't much else you can do about it than what you already found out: Try again.

No, this user interface isn't very friendly.  But that is because these tools never were intended to be anything but development helpers.  Please take it for what it is, and help finishing the ModemManager/NetworkManager integration if you have the ability to do that.  It cannot explain those error codes any better, but it will give you signal monitoring and other useful realtime quality measurements which will help you debugging connectivity problems.

Thanks for the reply. I now have a loop running until I have connection. I will see if I can help in any way with ModemManager/NetworkManager

---

### Post by Kondor71 on 2012-11-12
2 bmork: you and your friends write:

> --> Waiting for carrier.
ATDT*99***1#
CONNECT 100000000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Oct 16 21:50:54 2012
--> Pid of pppd: 11021
--> Using interface ppp0

> sudo qmi-network /dev/cdc-wdm1 start

I try to make my LTE modem work but I can't find in my system where i can do such tings and commands... Is it more clear? (sorry for my bad English)

About my system:
```
Linux kondor71-SVZ1311Z9RXI 3.6.3-030603-generic #201210211349 SMP Sun Oct 21 17:50:41 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

-lsusb
```
Bus 001 Device 006: ID 1199:68a2 Sierra Wireless, Inc. 
```

-rfkill list
```
0: sony-wifi: Wireless LAN
Soft blocked: no
Hard blocked: no
1: sony-bluetooth: Bluetooth
Soft blocked: no
Hard blocked: no
2: sony-wwan: Wireless WAN
Soft blocked: no
Hard blocked: no
3: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
4: hci0: Bluetooth
Soft blocked: no
Hard blocked: no

```

-ifconfig -a
```
wwan0     Link encap:Ethernet  HWaddr 82:b7:c4:46:7a:c4  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

But it doesn't work... and I don't know what to do...

---

### Post by bmork on 2012-11-12
> **Kondor71 said:**
> 
```
0: sony-wifi: Wireless LAN
Soft blocked: no
Hard blocked: no
1: sony-bluetooth: Bluetooth
Soft blocked: no
Hard blocked: no
2: sony-wwan: Wireless WAN
Soft blocked: no
Hard blocked: no
3: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
4: hci0: Bluetooth
Soft blocked: no
Hard blocked: no

```

OK, so it is another Sony.  Then the first thing to check is if you need to patch the sony-laptop driver.  Use minicom or another terminal application on the /dev/ttyUSB2 devices and write

```

at!pcinfo?

```If the result is this, then the modem is held in low power mode by rfkill:

```

State: 0 (LPM)
LPM force flags - W_DISABLE:1, User:1, Temp:0, Volt:0
W_DISABLE: 1
Poweroff mode: 0
LPM Persistent: 0

```I don't think the patch has gone into mainline yet (it was recently reposted), but you can get it from this bugreport:
[https://bugzilla.kernel.org/show_bug.cgi?id=47751](https://bugzilla.kernel.org/show_bug.cgi?id=47751)

That should in theory be enough to get the modem working in ppp mode over the /dev/ttyUSB2 serial port.

> 
```
wwan0     Link encap:Ethernet  HWaddr 82:b7:c4:46:7a:c4  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```But it doesn't work... and I don't know what to do...If you want to use the wwan0 interface, then you need the tools from here:
[http://cgit.freedesktop.org/libqmi](http://cgit.freedesktop.org/libqmi)

You will find usage instructions in this thread.  But as mentioned before:  This is mostly for those interesting in testing it out, and maybe help with further development of the real end user tools like ModemManager.  It does work, but be prepared for less user-friendlyness than normal...

Using the modem in PPP mode, like most older modems, should work just fine with current ModemManager versions.

---

### Post by bmork on 2012-11-13
Just a FYI if you do not want to deal with a git repo:  The first release of libqmi was just made:
[http://ftp.gnome.org/pub/gnome/sources/libqmi/1.0/libqmi-1.0.tar.xz](http://ftp.gnome.org/pub/gnome/sources/libqmi/1.0/libqmi-1.0.tar.xz)

But this is still a library intended for ModemManager integration, and the included command line utilities are only development tools.

---

### Post by Kondor71 on 2013-03-17
Dear Friends, after installation kernel 3.8.3 all problems has solved.

Install libqmi then in terminal:
> qmi-network /dev/cdc-wdm0 start
dhclient -d -4 wwan0

and LTE (Yota) works on 12.10... Let's Rock!

---

