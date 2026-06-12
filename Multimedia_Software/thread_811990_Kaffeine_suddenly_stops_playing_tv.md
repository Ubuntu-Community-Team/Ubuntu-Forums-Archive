---
title: "Kaffeine suddenly stops playing tv"
date: 2008-05-29
forum: Multimedia Software
---

### Post by raaki on 2008-05-29
Dear Ubuntu Users,

 i brought Hauppauge WinTv Nova-T stick and installed successfully on my ubuntu.i installed kaffeine and Metv to watch.

recently after installing updates i restarted the system,

when i open kaffeine player i couldn't find 6th option DIGITAL TV at all.(prev when ever my tv stick is connected it automatically displays all the 6 options)

when i open Metv it says :NO TUNER DEVICE

when i do lsusb , i found find my tv stick

i reinstalled twice but nothing changed

can any one help me regarding this problem?

---

### Post by xc3RnbFO8P on 2008-05-29
Do you dual boot or have Windows PC?

---

### Post by raaki on 2008-05-29
> **Ringi said:**
> Do you dual boot or have Windows PC?


yes i dual boot.preinstalled OS was windows  vista home

---

### Post by xc3RnbFO8P on 2008-05-29
Then "warm" (you have to feel it geting warm) the stick in Windows and restart to Ubuntu and try to open Kaffeine again. 
You can also run dmesg and then start Kaffeine.

---

### Post by raaki on 2008-05-29
> **Ringi said:**
> Then "warm" (you have to feel it geting warm) the stick in Windows and restart to Ubuntu and try to open Kaffeine again. 
You can also run dmesg and then start Kaffeine.


 i tried the options as you said,but it is still the same.in windows it is working fine.

---

### Post by xc3RnbFO8P on 2008-05-29
Did you install v4l-dvb?,
if you did recompile it again.

---

### Post by raaki on 2008-05-29
> **Ringi said:**
> Did you install v4l-dvb?,
if you did recompile it again.


i recompiled twice,but no change

when i type kaffeine in terminal ...
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found

 and open kaffeine window without digital tv option

---

### Post by xc3RnbFO8P on 2008-05-29
I am gonna try this usb stick tomorrow, haven't try it in Hardy Heron.
I let you know how it goes.

---

### Post by steefjeqv on 2008-05-30
Hi,

Did you try modprobe ?

In terminal :

sudo modprobe --verbose --remove dvb-usb-dib0700
sudo modprobe --verbose dvb-usb-dib0700 

Then try inserting your usb tuner.

Greetings,
Steven

---

### Post by raaki on 2008-05-31
> **steefjeqv said:**
> Hi,

Did you try modprobe ?

In terminal :

sudo modprobe --verbose --remove dvb-usb-dib0700
sudo modprobe --verbose dvb-usb-dib0700 

Then try inserting your usb tuner.

Greetings,
Steven

hi steeve i tried above options,but there is no change,still it detect my usb stick but i canot watch tv

this is the output when i do lsusb

Bus 007 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 046d:c050 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 006: ID 2040:7070 Hauppauge 
Bus 004 Device 005: ID 05a9:7670 OmniVision Technologies, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000

---

### Post by steefjeqv on 2008-05-31
Hi,

It seems that your tuner isn't recognized.

This may be a firmware problem.

I've found this thread on the Ubuntu forums :

[http://ph.ubuntuforums.com/showthread.php?t=421110]("http://ph.ubuntuforums.com/showthread.php?t=421110")

Look at the first post. The thread starter tom56 is very kindly providing updated firmware packaged in deb format.

Installing these may solve your problem.

Greetings,
Steven

---

### Post by raaki on 2008-05-31
> **steefjeqv said:**
> Hi,

It seems that your tuner isn't recognized.

This may be a firmware problem.

I've found this thread on the Ubuntu forums :

[http://ph.ubuntuforums.com/showthread.php?t=421110]("http://ph.ubuntuforums.com/showthread.php?t=421110")

Look at the first post. The thread starter tom56 is very kindly providing updated firmware packaged in deb format.

Installing these may solve your problem.

Greetings,
Steven

before reinstalling is it necessary to delete the old files or it do by itself?

bcoz last time when i ttry to reinstall it shoes some eroor stating that some dir and files are already present and it couldnt go further stating exit

---

### Post by steefjeqv on 2008-05-31
Hi,

No need for removing or reinstalling.

These packages only add missing firmware files to your /lib/firmware directory.

Greetings,
Steven

---

### Post by raaki on 2008-05-31
> **steefjeqv said:**
> Hi,

No need for removing or reinstalling.

These packages only add missing firmware files to your /lib/firmware directory.

Greetings,
Steven

hi Steven

i followed the steps and when i run kaffeine in terminal this op is generated


kbuildsycoca running...
DCOP Cleaning up dead connections.
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found

and still i cant see digital tv option
when i click me tv it says no tuner device

---

### Post by steefjeqv on 2008-05-31
Hi,

Maybe Kaffeine has a problem with it's DVB support ?

You can test your USB DVB-t using DVB-utils. You can install this app :

sudo apt-get install dvb-utils

Then use the following command line :

scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/your location in Germany

Replace your location in Germany by the correction location mentioned in the dvb-t directory of dvb-utils.

I suppose you've already tried installing the newest version of the DVB driver (as in this link).

[http://ubuntuforums.org/showthread.php?t=752968]("http://ubuntuforums.org/showthread.php?t=752968")

I'm going out to do some gardening now, so you won't be hearing from me the next couple of hours.

Please keep me posted.

Greetings,
Steven

---

### Post by raaki on 2008-05-31
> **steefjeqv said:**
> Hi,

Maybe Kaffeine has a problem with it's DVB support ?

You can test your USB DVB-t using DVB-utils. You can install this app :

sudo apt-get install dvb-utils

Then use the following command line :

scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/your location in Germany

Replace your location in Germany by the correction location mentioned in the dvb-t directory of dvb-utils.

I suppose you've already tried installing the newest version of the DVB driver (as in this link).

[http://ubuntuforums.org/showthread.php?t=752968]("http://ubuntuforums.org/showthread.php?t=752968")

I'm going out to do some gardening now, so you won't be hearing from me the next couple of hours.

Please keep me posted.

Greetings,
Steven

hi steven,

i already installed the newest version
 the op i got 

scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/de-Hannover
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

---

### Post by mtron on 2008-05-31
raki, please provide "dmesg" log.

best is to unplug the stick, run "dmesg" from a terminal, now pop in the stick & run "dmesg | tail" again

another way is to search /var/log/messages to see what went wrong before.
```
less /var/log/messages | grep -i dvb
```

in the last lines you should see some output like: 

> May 26 18:37:02 mtron-desktop kernel: [   33.146301] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
May 26 18:37:02 mtron-desktop kernel: [   33.211755] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-01.fw'
May 26 18:37:02 mtron-desktop kernel: [   33.963790] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
May 26 18:37:02 mtron-desktop kernel: [   33.963868] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
May 26 18:37:02 mtron-desktop kernel: [   33.964114] DVB: registering new adapter (Hauppauge Nova-T Stick).
May 26 18:37:02 mtron-desktop kernel: [   34.237802] DVB: registering frontend 1 (DiBcom 7000MA/MB/PA/PB/MC)...
May 26 18:37:02 mtron-desktop kernel: [   34.746390] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
May 26 18:37:02 mtron-desktop kernel: [   34.746420] usbcore: registered new interface driver dvb_usb_dib0700

Post your output if the command above please.

---

### Post by raaki on 2008-05-31
> **mtron said:**
> raki, please provide "dmesg" log.

best is to unplug the stick, run "dmesg" from a terminal, now pop in the stick & run "dmesg | tail" again

another way is to search /var/log/messages to see what went wrong before.
```
less /var/log/messages | grep -i dvb
```

in the last lines you should see some output like: 



Post your output if the command above please.


hi,

when i do dmesg | tail i get

[   49.956459]   groups: 02 01
[   52.049108] eth0: no IPv6 routers present
[   90.826586] usb 4-2: new high speed USB device using ehci_hcd and address 5
[   90.959295] usb 4-2: configuration #1 chosen from 1 choice
[  895.320040] usb 4-2: USB disconnect, address 5
[  900.987080] usb 4-2: new high speed USB device using ehci_hcd and address 6
[  901.008508] usb 4-2: configuration #1 chosen from 1 choice
[  997.543967] usb 4-2: USB disconnect, address 6
[ 1008.750015] usb 4-2: new high speed USB device using ehci_hcd and address 7
[ 1008.792453] usb 4-2: configuration #1 chosen from 1 choice


and

~$ less /var/log/messages | grep -i dvb
May 31 09:09:11 Hemu kernel: [  946.373250] cx88/2: cx2388x dvb driver version 0.0.6 loaded
May 31 09:09:11 Hemu kernel: [  946.373253] cx88/2: registering cx8802 driver, type: dvb access: shared

---

### Post by xc3RnbFO8P on 2008-05-31
Does your usb TVcard get warm when it is connected?

---

### Post by raaki on 2008-05-31
> **Ringi said:**
> Does your usb TVcard get warm when it is connected?

no

---

### Post by xc3RnbFO8P on 2008-05-31
Sometimes it helps to "warm it up" in Windows,
when it is warm, plug it in Ubuntu and run dmesg.
The card must be warm to get connected.

---

### Post by raaki on 2008-05-31
> **Ringi said:**
> Sometimes it helps to "warm it up" in Windows,
when it is warm, plug it in Ubuntu and run dmesg.
The card must be warm to get connected.

i will give a try andcome back to you

---

### Post by tom56 on 2008-05-31
1) What did you do to get it to work in the first place?
2) What were the updates that stopped it working?

This page might be useful but don't try any of the instructions on it unless you're sure they'll fix it - [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-Nova-T-Stick](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-Nova-T-Stick)

---

### Post by raaki on 2008-05-31
> **tom56 said:**
> 1) What did you do to get it to work in the first place?
2) What were the updates that stopped it working?

This page might be useful but don't try any of the instructions on it unless you're sure they'll fix it - [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-Nova-T-Stick](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-Nova-T-Stick)
Hi tom,

i previously installed by searching  the web . i am not sure about the previous steps ,at that time it didn't work with kaffeine

later i installed me tv with the following steps from the post described by tom man .[http://ubuntuforums.org/showthread.php?t=752968](http://ubuntuforums.org/showthread.php?t=752968)
 and it starts working with both metv and kaffeiene.

one week it went fine until i installed the updates(i didn't check what are the updates) i installed and switched it off

the next day  when i switch on kaffeine i didn't see digital tv option.

when i start me tv it says :no tuner found

---

### Post by steefjeqv on 2008-05-31
Hi raaki,

When your PC starts up you should see the grub loader.

Are there different kernel versions available for selection ?
If so, try an older version.

Greetings,
Steven

---

### Post by raaki on 2008-06-01
> **steefjeqv said:**
> Hi raaki,

When your PC starts up you should see the grub loader.

Are there different kernel versions available for selection ?
If so, try an older version.

Greetings,
Steven

Hi Steven

thanks for the idea,it works in old version.

but i have one more question.in order to work on the latest grub what are the updates are changes i need to make

---

### Post by steefjeqv on 2008-06-04
Hi raaki,

The problem seems to be a bug in the most recent kernel version.
It has been solved in 2.6.25, but unfortunately this kernel version isn't available through standard Ubuntu updates (yet).

The solution mentioned in this thread unfortunately didn't work for you :

[http://ubuntuforums.org/showthread.php?p=4834676]("http://ubuntuforums.org/showthread.php?p=4834676")

Greetings,
Steven

---

