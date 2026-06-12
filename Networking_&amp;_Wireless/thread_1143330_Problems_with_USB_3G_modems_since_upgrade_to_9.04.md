---
title: "Problems with USB 3G modems since upgrade to 9.04"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by chocko on 2009-04-29
I have never reported a bug before and did not want to report one if it's something specific with my config so hoping someone can help me out.

I have a 3g USB modem supplied by my provider Telstra I belive its the Sierra aircard 580

[http://www.sierrawireless.com/support/ac580_telstra.aspx](http://www.sierrawireless.com/support/ac580_telstra.aspx)

I first tried this modem with Ubuntu 8.10 and it work instantly, all I had to do was choose Telstra from the providers list and I was connected within seconds.

Since my upgrade to 9.04 my connections have been failing and I am not sure why.

lsusb shows the Sierra wireless device:

Bus 006 Device 014: ID 1199:6855 Sierra Wireless, Inc. 

dmesg shows it also:

[ 1491.472113] usb 6-1: new full speed USB device using uhci_hcd and address 14
[ 1491.633103] usb 6-1: configuration #1 chosen from 1 choice
[ 1491.636240] sierra 6-1:1.0: Sierra USB modem converter detected
[ 1491.642285] usb 6-1: Sierra USB modem converter now attached to ttyUSB0
[ 1491.642371] usb 6-1: Sierra USB modem converter now attached to ttyUSB1
[ 1491.642453] usb 6-1: Sierra USB modem converter now attached to ttyUSB2


But when I try to connect I see the following:

kernel: [ 1472.650757] sierra 6-1:1.0: Sierra USB modem converter detected
kernel: [ 1472.657972] usb 6-1: Sierra USB modem converter now attached to ttyUSB0
kernel: [ 1472.658057] usb 6-1: Sierra USB modem converter now attached to ttyUSB1
kernel: [ 1472.658137] usb 6-1: Sierra USB modem converter now attached to ttyUSB2
pppd[12486]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
pppd[12486]: pppd 2.4.5 started by root, uid 0
pppd[12486]: Using interface ppp0
pppd[12486]: Connect: ppp0 <--> /dev/ttyUSB2
pppd[12486]: PAP authentication succeeded
kernel: [ 1486.416156] usb 6-1: USB disconnect, address 13
kernel: [ 1486.416806] sierra 6-1:1.0: device disconnected
pppd[12486]: Modem hangup
pppd[12486]: Connection terminated.
pppd[12486]: Exit.
kernel: [ 1487.449621] sierra ttyUSB0: Sierra USB modem converter now disconnected from ttyUSB0
kernel: [ 1487.449769] sierra ttyUSB1: Sierra USB modem converter now disconnected from ttyUSB1
kernel: [ 1487.449900] sierra ttyUSB2: Sierra USB modem converter now disconnected from ttyUSB2
kernel: [ 1491.472113] usb 6-1: new full speed USB device using uhci_hcd and address 14
kernel: [ 1491.633103] usb 6-1: configuration #1 chosen from 1 choice
kernel: [ 1491.636240] sierra 6-1:1.0: Sierra USB modem converter detected
kernel: [ 1491.642285] usb 6-1: Sierra USB modem converter now attached to ttyUSB0
kernel: [ 1491.642371] usb 6-1: Sierra USB modem converter now attached to ttyUSB1
kernel: [ 1491.642453] usb 6-1: Sierra USB modem converter now attached to ttyUSB2

I have tried all of the Telstra profiles that come with 9.04 and they all do the same thing.

I also tried my huawei e220 which has worked in the past which although gives me different results also does not work.


My main modem is the Sierra so if anyone can offer some suggestions that would be great.

---

### Post by chocko on 2009-04-30
I have now tried this on another 9.04 host with the same result :(

---

### Post by chocko on 2009-04-30
anyone?

OK ubuntu sux, its the worst operating system I have used in a while, why can they release updates that don't reduce functionality! Windows vista is waaaaaaaaaaaay better!

---

### Post by DGortze380 on 2009-04-30
> **chocko said:**
> anyone?

OK ubuntu sux, its the worst operating system I have used in a while, why can they release updates that don't reduce functionality! Windows vista is waaaaaaaaaaaay better!

Then go run Vista.

---

### Post by sharke on 2009-04-30
I had same problem with BP3-EXT usb modem and rectified by deleting the connection in in networkmanager  rebooting and reconfiguring the connection.
Regards
Sharke

---

### Post by dLeon on 2009-04-30
Hello, 

I also had this problem after upgrading to Jaunty. While recognized, networkmanager refuse to use my USB modem. Doing ifconfig -a I saw my modem was recognized & available in /dev folder (note: mine is at /dev/ACM0). I solved this by using 'pppconfig' (Gnomeppp/Kppp is the gui type). If you adept with Window$ Network Connection configurator, you will now what to put.
Hope this can help, cheers.

---

### Post by Sheany on 2009-05-03
I've been having no end of issues with this aswell. I've given all above suggestions a try and I'm still going nowhere.

I've reverted back to 8.1 and am now having exactly the same issues!

I've tried everything i can think of, including connecting the modem on a windows laptop and then going back to the linux pc.

Not sure if anyone else is having the same issues, the other thing I'm getting is a password request to use the device. I've never had that before. Does anyone know about this? is this what's causing all my probs?

---

### Post by Cams123 on 2009-05-03
Have the same problem using gnomeppp as a work around every thing was fine in 8.10 .I too get the constant password question

---

### Post by chocko on 2009-05-03
I fixed my huawei e220 issue by changing the IPv4 settings in the connection created by the ubuntu setup tool to  'automatic PPP' instead of 'automatic PPP addresses only'

However this does not fix my original issue with the Sierra device!

I can't seem to get gnome-ppp to work with the Sierra aircard 580 either.

---

### Post by chocko on 2009-05-06
Cams how have you configured gnome-ppp? are using the same modem as me?

---

### Post by cripperz on 2009-05-06
Hi,

i have the same issue with my huawei (vodafone) 3G USB modem stick. It was working fine on Ubuntu 8.10 and only happened after upgrading it to Jaunty 9.04. Any of the ubuntu team can give us some tips on how to resolve this.

---

### Post by Cams123 on 2009-05-06
chocko I'using  e160 followed instructions for Wvdial and gnomeppp cant find the link sorry .

It is a bit hit and miss but it's better than nothing at all

---

### Post by chocko on 2009-05-07
Can anyone from the ubuntu team comment on this? Not sure if this is a bug or just a config problem but it's affecting a few people that I know of now.

---

### Post by chocko on 2009-05-07
has everyone with these issues done an upgrade? wondering if a clean installl will work? If that doesnt sadly I will be going back to 8.10

---

### Post by chocko on 2009-05-07
> **cripperz said:**
> Hi,

i have the same issue with my huawei (vodafone) 3G USB modem stick. It was working fine on Ubuntu 8.10 and only happened after upgrading it to Jaunty 9.04. Any of the ubuntu team can give us some tips on how to resolve this.

Try changing IPv4 settings to automatic (PPP) instead of automatic (PPP) addresses only. That worked for me with a e220 but not with my sierra.

---

### Post by dastasha on 2009-05-08
> Try changing IPv4 settings to automatic (PPP) instead of automatic (PPP) addresses only. That worked for me with a e220

Same issue for me except I´m using Kubuntu.
Where would I find the IPv4 settings?

---

### Post by chocko on 2009-05-08
> **dastasha said:**
> Same issue for me except I´m using Kubuntu.
Where would I find the IPv4 settings?

In network manager -> edit connections -> mobile broadband -> find your connection and edit it, you will then see a IPv4 tab

---

### Post by edibanez on 2009-05-08
I've done a clean install with kubuntu but still same problem... when I edit my network connections it only shows the main tab and ppp tab.

When I reboot my machine it also doesn't show my connection list.

---

### Post by conz on 2009-05-13
> **chocko said:**
> has everyone with these issues done an upgrade? wondering if a clean installl will work? If that doesnt sadly I will be going back to 8.10

I've upgraded to 9.04 on one system, and it no longer recognises the Vodafone 3G Huawei USB, which 8.10 recognised immediately on plugging-in.

I've not as yet tried to resolve this problem manually.

---

### Post by corrector on 2009-05-14
seems to be a lot of probs with sierra modems.
I myself use an integrated MC8780 module, which is the same module contained within the aircard 880u, I think..

Anyways, I too can confirm problems.
I can't connect anymore, it just disconnects instantly.
Had the same problems back in 8.04  and 8.10, but in some mysterious way, in mid January 2009, after a
NM update it just worked in 8.10!
But then with the new release, I clean installed 9.04 and voila, back to square one....

How will we do to address this to the developers?
Bug report?

---

### Post by sahbeewah on 2009-05-17
> **chocko said:**
> In network manager -> edit connections -> mobile broadband -> find your connection and edit it, you will then see a IPv4 tab


i had the same problem with my E220 after upgrade to 9.10 and i can vouch for this solution... it fixed my problem. thank you

---

### Post by Chiapo on 2009-05-17
I have been unsuccessful through repeated attempts at connecting to my ISP with my Acer Aspire One ZG5 running Ubuntu.
I have installed UNR 9.04 alongside Windows XP.
Windows (ugh!) connects every time.
Not so with Ubuntu.(sad face)
So far, I've been doing the Windoze shuffle with USB flash drives...
Downloaded wvdial using Windoze, saving to USB;

Boot into Ubuntu, install the .deb...
    Unresolved dependency!
        libconf* not found: (or something like that)

Boot into WinXP, download libconf* to USB;

Boot into UNR, install libconf*.deb (or whatever it was named)
    Unresolved dependency!
        libc* not found: (or something like that)
    
Boot into WinXP, download libc* to USB;

Boot into UNR, install libc*.deb (or whatever it was named)
    Unresolved dependency!
         Some other thing not found: 

Repeat until beer is all gone.

Go to sleep. :mad:


 Also saw another related thread that said to add usbserials, then add vendor code and device code to GRUB menu.lst, which resulted in an unsuccessful attempt at locating "usbserials" for Ubuntu 9.04.
Network Manager only recognizes my ethernet device, not the Qualcomm 3G modem (built in) although issuing lsusb on the CLI shows a Qualcomm device, it doesn't see it as a modem.

Tried using mode_switch, but that began another round of "the Windoze shuffle" and unresolved dependencies! (need more beer)

Maybe the beer is the problem?

Ok.
No beer for a week.
Followed instructions from several threads regarding HSDPA modem issues...
No progress...
(beer is getting tempting)
So here I am, disgruntledly surfing the net using WinXP, my Ubuntu dreams dashed again...

---

### Post by BjBlaster on 2009-05-21
I too have a sierra wireless (Express Card Blue Telstra thing) and it works perfectly under 8.10, but not under 9.04. It finds the card ok, I setup the wizard for "telstra next g card" and it dials but then reboots the card. In other words when I connect to the 3G profile in network manager it tries, but I see the power lights cycle and then it says it's disconnected.

```

[ 3090.248118] usb 5-2: USB disconnect, address 13
[ 3090.251453] sierra 5-2:1.0: device disconnected
[ 3090.744068] usb 5-2: new full speed USB device using uhci_hcd and address 14
[ 3090.908198] usb 5-2: configuration #1 chosen from 1 choice
[ 3090.910739] sierra 5-2:1.0: Sierra USB modem converter detected
[ 3090.912780] usb 5-2: Sierra USB modem converter now attached to ttyUSB0
[ 3090.912836] usb 5-2: Sierra USB modem converter now attached to ttyUSB1
[ 3090.912870] usb 5-2: Sierra USB modem converter now attached to ttyUSB2
[ 3091.304330] sierra ttyUSB3: Sierra USB modem converter now disconnected from ttyUSB3
[ 3091.304367] sierra ttyUSB4: Sierra USB modem converter now disconnected from ttyUSB4
[ 3091.304398] sierra ttyUSB5: Sierra USB modem converter now disconnected from ttyUSB5

```

It's a bugger really because 9.04 has fixed a lot of wireless WiFi driver issues and standby issues I was having but not the 3G card!

Driver info

```

$ modinfo sierra
filename:       /lib/modules/2.6.28-11-generic/kernel/drivers/usb/serial/sierra.ko
license:        GPL
version:        v.1.3.2
description:    USB Driver for Sierra Wireless USB modems
author:         Kevin Lloyd <klloyd@sierrawireless.com>
srcversion:     849FEAD771651BE184C5E16

```

Is anyone reporting this as a bug?

Cheers

Bj

---

### Post by BjBlaster on 2009-05-21
I emailed sierra and they where nice enough to send me the updated driver link 1.7

[sierra support page for linux]("http://sierrawireless.custhelp.com/app/answers/detail/a_id/500/")

I've successfully installed the new driver for kernel 28 9.04 but it still does the power cycle lockup thing as soon as I dial it. 

hmmmm

I've reported this as a bug [https://bugs.launchpad.net/ubuntu/+bug/379593](https://bugs.launchpad.net/ubuntu/+bug/379593)

---

### Post by BjBlaster on 2009-05-22
FIXED!!!!!

I updated the firmware to "AC880E_Telstra_F1_0_0_19ap" using a windows XP laptop and now it works with version 1.7.0 driver for sierra 880E under Ubuntu :) It won't however work with the driver that ships with 9.04.

I got the formware form here: [http://www.sierrawireless.com/support/](http://www.sierrawireless.com/support/)

Hope it helps someone.

Cheers

Bj

---

