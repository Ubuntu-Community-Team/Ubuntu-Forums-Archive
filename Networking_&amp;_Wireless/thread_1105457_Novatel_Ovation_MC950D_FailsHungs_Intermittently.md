---
title: "Novatel Ovation MC950D Fails/Hungs Intermittently"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by nhoeller on 2009-03-24
I have successfully connected a Novatel MC950D 3G modem to a PC running Unbuntu 8.10 server using a udev rule to release the ZeroCD and a simple wvdial script.  I am using the options.ko driver and getting reasonable speeds (800kbps down, 200kbps up).

Intermittently (4 times today), the modem stops working.  Symptoms:
[LIST]
[*]pppd reports modem has hung up (code=16)
[*]both /dev/ttyUSB0 and /dev/ttyUSB1 disconnect
[*]3B modem reconnects to USB port as usb-storage
[*]udev rule is involved
[*]option driver detects GSM modem and connects as ttyUSB0&1 or sometimes ttyUSB1&2
[*]wvdial is not able to communicate with the modem
[*]modem LED flashing rapidly in sort of a pinkish color (not listed in the manual or troubleshooting guide)
[/LIST]

I need to unplug/replug the modem and restart wvdial to get the modem working again.  My local provider has no clue (not trained on Linux).  

Any ideas what is going on and what I might do to resolve this problem?  

Is there a way using software to simulate unplugging/replugging the modem so I can automate recovery?
[INDENT]Thanks, Norbert[/INDENT]

---

### Post by Sylslay on 2009-03-24
Mayby it is heatup?
I use bowl from kitchen table as signal amplifier and noise canceling and working great with Huawei 3g modem. Just ordinary BOWL!!!! === internet 3 times faster.

---

### Post by Sylslay on 2009-03-24
Once I tape few ordinary sawing nidles, under my modem and it start behavor very wrong, seems like yours, flashing, disconnectiq with wvdial.So I took off nidles.  So I only put it to bowl and test upload and dowlaoad speed.

---

### Post by GeorgeVita on 2009-03-25
Hi **nhoeller**,
can you check the modem with other PC and/or Operating System?

The disconnect reason could be hardware, software or caused by the provider. Many times you could have 5 bars signal but no mobile internet (stuck) because your provider cannot serve you.

In your case it seems to be a hardware reason because you are missing /dev/ttyUSBx for a while the led is flashing in a weird style and when you remove it and plug it again it works again. Also the problem appears randomly.

Take a look at my thread: [http://forum.huawei.com/jive4/thread.jspa?threadID=323666](http://forum.huawei.com/jive4/thread.jspa?threadID=323666)

Hi **Sylslay**, I thing it would be better to use an extention cable (just cables without circuit) as described in the above link.

Regards,
George

---

### Post by nhoeller on 2009-03-25
George, interesting!  I am using a tri-tip USB cable to increase power to the modem and an extension cable so that I can position the modem near a window.  I tested without the extension cable and with only one of the USB connections of the tri-tip plugged in, but have not tried with the 3G modem plugged directly into the PC.

I will wire up your 2nd 'patch' and see if that helps.  I may also build another PC to try and eliminate hardware issues with the USB port.  I would get the 3G modem replaced but am having difficulty convincing tech support that it might be a modem problem.  Intermittent issues are always fun...
     Thanks, Norbert

---

### Post by nhoeller on 2009-03-29
George, I wired up your 2nd USB cable patch.  The good news is that the modem worked when I plugged it in.  The bad news is that the modem hung again last night.  I double-checked the wiring and the pin connections (the wires on my cable had different colors from your diagram) and am satisfied that the USB cable patch is correct.

Strangely, I am not seeing this problem when the modem is connected to my Vista laptop.  Maybe I was just lucky.

I will build another software router with Windows XP and Linux.  That should help me narrow down whether the problem is hardware or software.
     Thanks, Norbert

---

### Post by nhoeller on 2009-03-29
I just had the modem fail again.  Normally, the modem connects to the cell network over HSUPA.  When I unplugged/replugged the modem, the lights suggested it was connecting via EDGE.  A second attempt connected via HSDPA.  Is it possible that the modem needs to communicate with the driver when switching between cell platforms, and the Linux 'option' driver is not responding properly?  

It could also be an issue with my wvdial script.  I am using:

[INDENT][Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 912600
Init1 = ATZ
Init2 = AT&FE0V1X1&D2&C1S0=0
Stupid Mode = on
Modem Type = USB Modem
Phone = *99#
ISDN = 0
[/INDENT]

---

### Post by GeorgeVita on 2009-03-29
> **nhoeller said:**
> ...
I would get the 3G modem replaced but am having difficulty convincing tech support that it might be a modem problem...

Because everything is "compatible" and "they know better"!

> **nhoeller said:**
> ...
Strangely, I am not seeing this problem when the modem is connected to my Vista laptop...

You have to cross check by booting a Live CD (Ubuntu 8.10 ?) to the Vista laptop and use Network Manager to connect. This test will show you if it is a h/w reason.

About HSPA and EDGE switching, many users note that they have some problems, I believe this is more Provider oriented that an O.S. problem. There are some AT commands asking from the modem to use only 3G/HSPA but there is no documentation published except some posts to various forums.

I think that you must find a steady condition laptop/modem/good 3G signal and test the modem for the randomly disconnects which may be caused by a h/w (power) reason. This is the only you can solve with the cable patch.

About your /etc/wvdial.conf: most users use "analog modem" instead of "USB modem" and some providers need the APN definition:
**Init3 =AT+CGDCONT=1,"IP","internet"**
(in place of "internet" you have to place the proper APN for your provider)

After plugging the modem again, wait for the 3G modem state (usually the blue light) and then try to connect.

If you have any system message when disconnected (wvdial, dmesg) post it here. Have you tried to use Network Manager 0.7?

Regards,
George

---

### Post by nhoeller on 2009-03-29
George, in reverse order, I saw the same problem when I tested the modem on Ubuntu 8.10 desktop with Network Manager 0.7.  X-Windows is deadly slow on the PC I am using, so I did not install Gnome or KDE when I rebuilt the system with Ubuntu 8.10 server.  The APN information is already 'known' by the modem (verified through minicom).

My Vista system is my work laptop - too much on my plate right now to dedicated it to a potentially long-running Live CD test :)

Below are the syslog entries around the latest problem.  The modem detaches and immediately reattaches.  My udev rule disconnects the ZeroCD so that the option driver can grab the device.  Most of the time it appears as ttyUSB0/1, but I have seen it show up as ttyUSB1/2.  

Mar 29 13:02:59 300PL kernel: [142120.140359] usb 1-2.4: USB disconnect, address 23
Mar 29 13:02:59 300PL kernel: [142120.143494] option 1-2.4:1.0: device disconnected
Mar 29 13:02:59 300PL kernel: [142120.145360] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Mar 29 13:02:59 300PL kernel: [142120.155013] option 1-2.4:1.1: device disconnected
Mar 29 13:02:59 300PL pppd[15345]: Modem hangup
Mar 29 13:02:59 300PL pppd[15345]: Connect time 307.2 minutes.
Mar 29 13:02:59 300PL pppd[15345]: Sent 2831521 bytes, received 16614180 bytes.
Mar 29 13:02:59 300PL pppd[15345]: Connection terminated.
Mar 29 13:02:59 300PL pppd[15345]: Exit.
Mar 29 13:02:59 300PL kernel: [142120.561284] usb 1-2.4: new full speed USB device using uhci_hcd and address 24
Mar 29 13:02:59 300PL kernel: [142120.601593] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Mar 29 13:02:59 300PL kernel: [142120.691916] usb 1-2.4: configuration #1 chosen from 1 choice
Mar 29 13:02:59 300PL kernel: [142120.693550] option 1-2.4:1.0: GSM modem (1-port) converter detected
Mar 29 13:02:59 300PL kernel: [142120.694367] usb 1-2.4: GSM modem (1-port) converter now attached to ttyUSB0
Mar 29 13:02:59 300PL kernel: [142120.698727] option 1-2.4:1.1: GSM modem (1-port) converter detected
Mar 29 13:02:59 300PL kernel: [142120.699425] usb 1-2.4: GSM modem (1-port) converter now attached to ttyUSB1

From previous failures, wvdial/pppd report that the connection to the modem was lost (error = 16, I recall).  If I try to start wvdial with the modem in the 'madly blinking' state, it cannot communicate with the device.

I am going to try to find someone at Novatel on Monday who can talk intelligently about their device.
        Thanks, Norbert

---

### Post by nhoeller on 2009-03-30
George, I corrected the 'Modem Type' and also removed the Init2 string.  I was just going to say that the modem had stayed up the longest time ever (1111 minutes) when it failed.  Syslog shows same sequence as above.  wvdial log shows:

[INDENT]--> Disconnecting at Mon Mar 30 11:35:11 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Disconnecting at Mon Mar 30 11:35:11 2009[/INDENT]

pppd error 16 is "The link was terminated by the modem hanging up".

If I run wvdial while the modem is in its 'madly blinking' state, I get back 

[INDENT]--> Cannot open /dev/ttuUSB0:Device or resource busy.[/INDENT]

I tried running minicom against the port - it hung 'Initializing Modem'.  Killing minicom caused it to hang 'Resetting Modem'.  Rebooting Ubuntu did not help because power to the USB port never dropped.   

In parallel with continuing to diagnosing the problem, I have an idea about how to automate resetting the modem.  I have an [Arduino]("http://www.arduino.cc/") controller that can listen on the PC serial port and in turn control a 'normally closed' relay wired into the power line of the USB cable.  From your understanding of USB cables, is that all I need to do, or do I need to open/close all four leads?
     Thanks, Norbert

---

### Post by GeorgeVita on 2009-03-30
EDIT: tech info added

> **nhoeller said:**
> 
Mar 29 13:02:59 300PL kernel: [142120.140359] usb 1-2.4: USB disconnect, address 23
Mar 29 13:02:59 300PL kernel: [142120.143494] option 1-2.4:1.0: device disconnected
Mar 29 13:02:59 300PL kernel: [142120.145360] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Mar 29 13:02:59 300PL kernel: [142120.155013] option 1-2.4:1.1: device disconnected
Mar 29 13:02:59 300PL pppd[15345]: Modem hangup
Mar 29 13:02:59 300PL pppd[15345]: Connect time 307.2 minutes.
Mar 29 13:02:59 300PL pppd[15345]: Sent 2831521 bytes, received 16614180 bytes.
Mar 29 13:02:59 300PL pppd[15345]: Connection terminated.
Mar 29 13:02:59 300PL pppd[15345]: Exit.
Mar 29 13:02:59 300PL kernel: [142120.561284] usb 1-2.4: new full speed USB device using uhci_hcd and address 24
Mar 29 13:02:59 300PL kernel: [142120.601593] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Mar 29 13:02:59 300PL kernel: [142120.691916] usb 1-2.4: configuration #1 chosen from 1 choice


The above seems to be a h/w reset caused by the modem (circuit or firmware) or a momentary power loss. The modem did not stuck (brown out) but restarted and recognized by the system. Also the system rearranges /dev/ttyUSBx starting from 0 because wvdial exited normally. In another case the connecting program stuck holding the /dev/ttyUSB0 resulting in a rearrangement to /dev/ttyUSB1 & 2

If the above caused by a power problem could be fixed with the patched cable.

> **nhoeller said:**
> 
--> Disconnecting at Mon Mar 30 11:35:11 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Disconnecting at Mon Mar 30 11:35:11 2009
...
...If I run wvdial while the modem is in its 'madly blinking' state, I get back 

--> Cannot open /dev/ttuUSB0: Device or resource busy.

I tried running minicom against the port - it hung 'Initializing Modem'.  Killing minicom caused it to hang 'Resetting Modem'.  Rebooting Ubuntu did not help because power to the USB port never dropped.   


In the above case the modem is in an ERROR state with its firmware knowing or not this Error condition (the 'madly blinking' could be random or a status). We are sure that power removal is a solution.

> **nhoeller said:**
> From your understanding of USB cables, is that all I need to do, or do I need to open/close all four leads?

The best is to open/close at least 3 leads (V+ and data). As it is simpler to open/close only the V+ (red cable) you have to try it. If the modem is well designed will reset fully even if the line driver has data signals.

Finally **Init2 = AT&FE0V1X1&D2&C1S0=0** it is very good because of AT&F which restores factory defaults, useful when using the modem with windows where we don't know the exact settings (via control panel you can enable and check the modem log file to see some of them).

Using minicom you can try **AT&F** then **ATZ** and **AT&V** to see factory default settings.
(**minicom -s** starts minicom without initializing showing the main menu)

Regards,
George

---

### Post by nhoeller on 2009-04-02
Latest news...  I built a new PC with Windows XP, NAT32 and the official MobiLink software.  It ran right through the night, I tried to get technical support at Novatel to call me back.  Shortly after hanging up the phone, the Novatel modem hung - same symptoms.  MobiLink was unable to connect to the device.  

Since I have the problem on different hardware and different software (with and without the 'USB cable patch' to rule out stray electrical gremlins), I have convinced the wireless carrier to replace the modem.  Unfortunately, they are only shipping a ZTE modem which appears not to be popular with the Linux community.  I may yet be stuck with the MC950D and will need to implement automation to power-cycle the modem.  

I will admit that I am getting quite attached to having an Internet connection with 150ms latency, compared to 70+0ms latency of my satellite connection (and the random bandwidth degradation from their Fair Access Policy).

---

### Post by GeorgeVita on 2009-04-02
> **nhoeller said:**
> ...
Since I have the problem on different hardware and different software...


We must think that it is a modem's fault.

Can you do a final h/w test? Power the modem with an external 5VDC power supply rated at least 1A (best is a linear type with a 7805 regulator good heatsink and capacitors over 1000uF) or even better a bench PSU.

What is the signal strength in your position? (see it from WinXP or with the **AT+CSQ** from minicom)

Some ZTE types are working like: MF626, MF628, MF632 AND MF627 AND MF636 (mine) with modifications.

If it helps I could do some tests with my MF636 and local provider for comparison.

G

---

### Post by nhoeller on 2009-04-02
George, I currently have the modem plugged into a powered USB hub.  The power supply is rated at 2.5A - it is one of the regulated power supplies, but I have no idea what the internals look like.  

I was so annoyed I forgot to ask what model of ZTE they were shipping me.  I should get it shortly.  

Signal strength is typically 3 bars out of 5.  Sometimes I see 4 bars, sometimes it drops to 2.  

Is there a way to check signal strength while wvdial is using the modem?  I trying pointing minicom at /dev/ttyUSB1, but got no answer.

---

### Post by GeorgeVita on 2009-04-02
When I was using a Huawei E170, been connected via /dev/ttyUSB0 could used minicom to test some AT commands via /dev/ttyUSB1. Setup minicom before your efforts or use **minicom -s** and **serial port setup** from the menu. In case of misspelling it stucks and usually ... you have to reboot!

I am going to test the above with the ZTE.
[COLOR="DarkOrange"]EDIT:> [/COLOR]ok worked, not fully tested.
Modem attached as /dev/ttyUSB0-1-2-3 connected via /dev/ttyUSB3 minicom at /dev/ttyUSB1
Tested with **AT**, **AT+CSQ** and **ATI**

**[COLOR="Magenta"]NEW EDIT:[/COLOR]** Can you check from: System > Administration > System Log > click on daemon.log
scroll down and find the lines regarding the ttyUSBx (modem) at disconnection time. My idea is a problem caused by a System or modem timeout. System timeout when idle/suspend/screensaver. My modem disappeared from Network Manager after screen saving! I could not connect till I made a real h/w disconnection. Lets try to debug it.

G

---

### Post by nhoeller on 2009-04-23
George, I received a ZTE MF636 as a replacement for the Novatel.  After enabling and testing the device on Vista, I moved it to the Ubuntu server.  Although **usb_modeswitch** seemed to work initially, it would not switch the device out of its ZeroCD mode after I rebooted.  Your trick of sending an **AT+ZCDRUN=8** command to the modem to disable ZeroCD saved the day.  In general, the ZTE modem appears to deliver better throughput than the Novatel.  

The modem intermittently hangs just like the Novatel, although the symptoms are different.  I see the following errors in syslog:

[INDENT]Apr 23 03:51:33 300PL pppd[16581]: No response to 4 echo-requests
Apr 23 03:51:33 300PL pppd[16581]: Serial link appears to be disconnected.
Apr 23 03:51:33 300PL pppd[16581]: Connect time 601.6 minutes.
Apr 23 03:51:33 300PL pppd[16581]: Sent 26748373 bytes, received 132386910 bytes.
Apr 23 03:51:39 300PL pppd[16581]: Connection terminated.[/INDENT]

The modem does not disconnect from the USB port - the **/dev/ttyUSB0-2** devices still exist.  Sometimes the modem shows a solid green light (indicating that it is registered but not connected on a 2G network), sometimes the modem light goes off completely.  In the former state, **wvdial** cannot communicate with the modem (**Modem not responding** to ATZ commands).  **daemon.log** shows nothing relevant to the problem. 

Since I have connection issues with multiple modems on multiple PCs and operating systems, I suspect the modems are not properly handling some sort of carrier problem.  Unfortunately, the carrier has not stated any sort of Linux support for the ZTE and reproducing the problem on Windows will have to wait.  

I have installed your cable patch to eliminate power issues.  The next step is to build a device that will interrupt and restore USB power under control of the Ubuntu server.  I am hoping I can also use this device to power off the modem during server bootup - Ubuntu hangs during hardware detection if the modem is plugged in (**dmesg** shows the modem is detected and **/dev/ttyUSB0-2** ports are added but the filesystems have not been mounted).  It may be a problem with my **udev** rules.

---

### Post by GeorgeVita on 2009-04-24
Hi Norbert,
taking account of the differences we have in our s/w and h/w configuration, I can only give some thoughts for your debugging.

> **nhoeller said:**
> ...The modem intermittently hangs just like the Novatel, although the symptoms are different.  I see the following errors in syslog:

[INDENT]Apr 23 03:51:33 300PL pppd[16581]: No response to 4 echo-requests
Apr 23 03:51:33 300PL pppd[16581]: Serial link appears to be disconnected.
Apr 23 03:51:33 300PL pppd[16581]: Connect time 601.6 minutes.
Apr 23 03:51:33 300PL pppd[16581]: Sent 26748373 bytes, received 132386910 bytes.
Apr 23 03:51:39 300PL pppd[16581]: Connection terminated.[/INDENT]

The modem does not disconnect from the USB port - the **/dev/ttyUSB0-2** devices still exist.

This disconnection could be done from your provider (mobile phone company). They possibly cannot or do not want a 10 hours connection. Another reason could be a s/w or h/w timeout into the modem (?).

> **nhoeller said:**
> ...Sometimes the modem shows a solid green light (indicating that it is registered but not connected on a 2G network), **sometimes the modem light goes off completely**.

This could be the modem's timeout. This can be tested or altered by loading a "dummy" page which reloads itself after a fixed time period. You can make an .html file (I don't know how) or open a tab with a page which has this function (test this one: [http://www.emsc-csem.org/](http://www.emsc-csem.org/)).

Using above trick you have to pay attention to the data traffic instead of paying a lot of money to the provider!

> **nhoeller said:**
> ...In the former state, **wvdial** cannot communicate with the modem (**Modem not responding** to ATZ commands).  **daemon.log** shows nothing relevant to the problem.

The modem must be in a sleep mode or stucked. I have faced this problem with my ZTE MF636 one or two times in the past but I couldn't repeat it in order to debug it.
Also in my case the cable patch fixes the Huawei's h/w reset problem and not the ZTE one. I realize that ZTE works better (data rate) with a small extention cable to gain RF signal or in direct connection with the USB port (using a notebook where the metal parts are less than with a desktop).

Concluding, if your application must be "bullet proof" you have to check your idea to add extra h/w and simulate the manual restart (& replug) condition.

Regards,
George

---

### Post by nhoeller on 2009-05-10
Two steps forward, one step back.  The modem has actually been reasonably reliable recently, or rather wvdial detects that the connection has failed and automatically restarts the connection.  The modem may stay up for several hundred minutes and then require a restart after only 4 minutes.  Except for today (which has been particularly bad), I have only had to manually unplug/plug the modem a few times a week.

I have built a circuit on top of an Arduino controller ([http://arduino.cc](http://arduino.cc)) that incorporates George's power filter and a relay cut into the USB power line.  I can send serial device commands to the Arduino over its USB port.  Unfortunately, the current crop of Arduino boards automatically reset themselves when a serial connection is established, as part of support for automating the process of uploading new code to the Arduino.  I am testing out various ways of getting around the resets.

One thing I noticed is that the ZTE modem sometimes connects on /dev/ttyUSB0-3, sometimes only on /dev/ttyUSB0-2.  It seems that the highest ttyUSB device is the one I need to use for wvdial.

---

### Post by radolin on 2009-05-12
Hi Norbert,

unfortunately I can't help with the modem reset problem, but only about the Arduino reset one :).

You can try a software solution by disabling the HUPCL (hang up on close) flag of the virtual COM port, so DTR is not lowered after a disconnect. 

The other 100% sure way is a hardware solution - you just need to remove one of the 100nF capacitors - details here [http://www.arduino.cc/playground/Main/DisablingAutoResetOnSerialConnection](http://www.arduino.cc/playground/Main/DisablingAutoResetOnSerialConnection)

Also if your machine has real COM/LPT port you can just control the relay with it and avoid the whole Arduino thing. Since you already have external 5V supply for the USB hub with one transistor, a couple of resistors and a protection diode you'll be able to switch the relay directly.

Btw I am researching what 3G modem to buy and was looking into the ZTE MF626  but am a bit scared after this stories. It will not be my primary inet conection, so if it works for 1-2 hours will be enough but still ... 
Any advice?

Regards,
Rado

---

### Post by nhoeller on 2009-05-12
Rado, I will test the -hupcl flag on stty as soon as I get a chance.  I did try a Perl script (from the Arduino forum) to disable DTR and send the required characters to the Arduino.  It sort of worked, in so far as the Arduino did not reset itself.  However, the Arduino still did not recognize the character.  I added a trailing '0A'x and had the Arduino echo back what it saw, but must not have the right 'magic incantation'.

Thanks for the tip on using a COM/LPT1 port directly - definitely cheaper than the setup I have now.  The current PC has a COM port.  I will be replacing it with a laptop as soon as I can free one up - no COM port but it does have an LPT port.  

I am not sure my experiences are any reflection on the ZTE MF626.  In general, this modem is giving better bandwidth than the Novatel Ovation MC950D.  Being able to turn off the ZeroCD is a nice feature - one less thing to worry about on Linux.  I would say that it freezes up less often.  What I am seeing are temporary conditions where wvdial detects that the connection is not responding and automatically recovers.  Most of the time, I do not even notice.  

I do not know if this happened with the Novatel modem, since at the time I was not monitoring the logs as closely as I am doing now.  My suspicion is that the problem is a glitch in the carrier's network.  It is even possible that the connection would come back by itself if I disabled wvdial recovery.  I also suspect that the modem freezes are caused by something happening at the carrier - they seem related to a switch from HSUPA to EDGE.
      Regards, Norbert

---

### Post by nhoeller on 2009-05-13
Rado, adding the **-hupcl** option on the **stty** command for the the Arduino port worked like a charm.  I can now use **echo** to communicate with the Arduino.  

```
stty -F /dev/ttyUSB3 cs8 9600 ignbrk -brkint -icrnl -imaxbel -opost -onlcr -isig -icanon -iexten -echo -echoe -echok -echoctl -echoke noflsh -ixon -crtscts 
```

Thanks, Norbert

---

### Post by radolin on 2009-05-14
I'm glad I helped.

Since you seem OK with it I am not so worried about buying the 626 now :).

My only previous experience with mobile broadband was through a Nokia GSM phone hooked up via bluetooth to the PC, and I got the same disconnects, even on average every 10 minutes. I felt like I have traveled back in time, when I was using a noisy analog phone line and a 14.4 modem :). I talked numerous times with the mobile operator support but they weren't of any help. So it might after all be a carrier issue and not one with the modem.

Greetings,
Rado

---

### Post by nhoeller on 2009-06-11
George, you mentioned in [http://ubuntuforums.org/showpost.php?p=7002604&postcount=15](http://ubuntuforums.org/showpost.php?p=7002604&postcount=15) that you were able to use minicome to talk to the other ports presented by the 3G modem.  In my case, the MF636 connects on dev/ttyUSB0, 1 and 2.  wvdial is using dev/ttyUSB2.  If I connect via minicom to other of the other ports, it appears the modem hangs (or rather my connection to the Internet fails).  

I tried removing all the initialization, reset and dial strings from the minicom profile.  If I start minicom, it displays the 'Press CTRL-A Z' message and hangs.
     
I have had some bandwidth/reliability issues recently that I think were related to my carrier switching from HSUPA to EDGE and GPRS.  I was hoping to confirm this on Linux without have to plug the modem into a Windows box.
     Thanks, Norbert

---

### Post by GeorgeVita on 2009-06-12
Hi Norbert,

last days I "messed up" all my Ubuntu systems... (I have only various 9.04)!

Before writing a post I always try to TEST everything by myself. When I wrote it I am sure it worked. As I remember it was on 8.04 installation and from terminal "**minicom -s**". You are right, must remove all init lines, select the same Baud rate to wvdial and minicom (115200 is most reliable and standard for tests).

As developers of Ubuntu trying to get the best from 3G modems sometimes they scramble all ports! You can try only in previous versions where the system cannot find the modem at all! At recent 9.04 there are some stucks/resets with this modem. Also wvdial is not included, usbserial is not an external driver, etc.

I have no 8.04 or 8.10 installation at this time. I tested the new idea below:

1. AT+ZCDRUN=8 (from windows) to modem
2. Boot Ubuntu 8.10 LiveCD (you may use installation).
3. Attach MF636 on USB (no SIM PIN lock!)
4. **lsusb** shows **19d2 : 0031**
5. **ls /dev/ttyU*** shows no port created
6. **sudo modprobe usbserial vendor=0x19d2 product=0x0031**
7. **ls /dev/ttyU*** shows **/dev/ttyUSB0 /dev/ttyUSB1 /dev/ttyUSB2**
8. sudo gedit /etc/wvdial.conf
9. write tested data into gedit, save, exit, ignore any error messages
10. **sudo wvdial** ... connected
11. GET **minicom** via Synaptic Package Manager
12. from a 2nd terminal window: **minicom -s**
13. choose **Serial port setup**
14. **A- ... /dev/ttyUSB1**
15. press ESC
16. choose **Modem and dialling**
17. edit **A** to become "**~^M~AT^M** (CR AT CR)
18. delete all contents into **B**
19. press ESC
20. press ESC

Now you will see some "status" text running.
Try **AT+CSQ** you will get the signal strength (GSM mode).
Some commands may affect the main /dev/ttyUSB2 port and disconnect.
Try some commands: **ATI AT&V**

Note that I wrote this post and testing above connected fine!
All this done "on the fly"...running from the 8.10 LiveCD.

Regards,
George

[COLOR="Blue"]P.S. Also take a look at my post#4 of [http://ubuntuforums.org/showthread.php?t=1181615](http://ubuntuforums.org/showthread.php?t=1181615)[/COLOR]

---

### Post by nhoeller on 2009-06-12
George, I am not having much luck.  For some reason, the ZTE MF636 is connecting on /dev/ttyUSB0 through USB3.  wvdial is running on /dev/ttyUSB3.  I created minicom profiles for ttyUSB2 and ttyUSB1, identical except for the port.

```

# Machine-generated file - use "minicom -s" to change parameters.
pu port             /dev/ttyUSB2
pu minit            ~^M~AT^M
pu mreset

```

I did not change any of the other settings:
```

A - Init string ......... ~^M~AT^M   
B - Reset string ........         
C - Dialing prefix #1.... ATDT  
D - Dialing suffix #1.... ^M 
E - Dialing prefix #2.... ATDP   
F - Dialing suffix #2.... ^M  
G - Dialing prefix #3.... ATX1DT   
H - Dialing suffix #3.... ;X4D^M  
I - Connect string ...... CONNECT    
J - No connect strings .. NO CARRIER            BUSY  
                          NO DIALTONE           VOICE  
K - Hang-up string ...... ~~+++~~ATH^M    
L - Dial cancel string .. ^M      
                                                                           
M - Dial time ........... 45      Q - Auto bps detect ..... No  
N - Delay before redial . 2       R - Modem has DCD line .. Yes   
O - Number of tries ..... 10      S - Status line shows ... DTE speed 
P - DTR drop time (0=no). 1       T - Multi-line untag .... No  

``` 

The usb2 profile connects:
```
Welcome to minicom 2.3

OPTIONS: I18n
Compiled on Oct 24 2008, 06:37:44.
Port /dev/ttyUSB2

                 Press CTRL-A Z for help on special keys

```

It is not hung (CTRL-A Z works), but it will not accept any input or display any response.  

The usb1 profile sits at 'Initializing Modem'.

I tried echoing "AT" to /dev/ttyUSB2 and USB1, and using the 'cp /dev/ttyUSBx myUSBx' command to capture the output.  The echo command completes on both ports, but I see no response from the modem.  Echoing to /dev/ttyUSB0 hangs the echo command.  I wonder if I have to set up the USB2 port with the same specs as wvdial is using?  I may need to do some USB Snooping under Windows to see how the 'official' software talks to the ZTE modem.

---

### Post by GeorgeVita on 2009-06-12
Hi Norbert,
you are using 8.10 server while I used 8.10 desktop and  8.10 LiveCD. Also as you are trying "a long term" use without rebooting possibly you have "accumulated" adjustments and resulting to a variable starting point.

Find an 8.10 LiveCD and test my previous post step by step to verify and confirm our "compatibility". There is an extreme case to have different version of firmware inside the modem ... but do not try to upgrade anything now!

When connected to minicom (assuming it will not hang) the other channel sends always some "status" reporting the "UMTS" or "HSPA" switch on network! Other command (I don't remember now) can show you amount of data transfered...

Two more tests and one warning:
- Boot with the modem attached, **ls /dev/ttyU*** shows 0-1-2-3
- Shut Down. Boot without the modem, wait till system fully loads, attach modem: **ls /dev/ttyU*** shows 0-1-2
Always the highest is usable for data while -1 or -2 is the 2nd usable port. AFTER a "failed try" I would remove/reattach modem, shut down, boot again. Always in the same manner till find the steady condition. It is painful but this is a "lab test".

The Warning now: Upgrading to 9.04 you may loose the ability to connect via your ZTE modem! Developers have changed everything. 

Regards,
George

---

### Post by iponeverything on 2009-11-11
I was having this problem with my ZTE MF626. I stumbled onto this solution while trying to solve another problem.. 

I installed cu and expect via apt-get and then I run following script to fix the issue. I have it run automatically every time I insert the modem. I have now gone 2 days without a lockup. (before I was lucky to make it 3 hours)  

Do a "chown uucp /dev/ttyUSB1" first..

# ========= script start

#!/usr/bin/expect --

set Init3 "AT+CPBS=\"SM\""
set Init4 "AT+CPMS=\"SM\",\"SM\",\"\""

spawn cu -l /dev/ttyUSB1
expect "Connected."

sleep 2

send "AT\r"
expect "OK"

send "AT\r"
expect "OK"

send "$Init3\r"
expect "OK"

send "AT\r"
expect "OK"

send "$Init3\r"
expect "OK"

send "AT\r"
expect "OK"

send "$Init4\r"
expect "OK"

send "AT\r"
expect "OK"

send "$Init4\r"
expect "OK"

exit

# ======= script end

---

### Post by GeorgeVita on 2009-11-11
Hi **iponeverything**,
this command stops the '+ZUSIMR' message sending repeatedly the modem, but I think this is stopped when connected:

> **Sergiu Bivol said:**
> ...
You are right, **+ZUSIMR: 2** means that the modem does not know where to store the SMS messages. I found that issuing the commands 
```
AT+CPBS="SM"\r\n
AT+CPMS="SM","SM",""\r\n

```
solve this problem until unplugging the modem. However, I cannot test them, since I do not get the +ZUSIMR messages...

If your problem comes back, check if you can adjust any 'inactivity timer' as **ATS7=60 S30=0**
At any time you can see 'default' configuration using a terminal program (like minicom) and check output of **AT&V**

Regards,
George

---

### Post by iponeverything on 2009-11-13
Thanks George, that is helpful.

I think that in my case the +ZUSIMR messages where starting anyway and causing things to get mucked somehow. I could fire up minicom on ttyUSB1 and see the +ZUSIMR:2 messages popping up. 

Also, about a third of the time after a fresh boot, wvdial would get hung on this messages.. 

I have put a script in place to monitor connection and if it hangs to try to redial.. Though what I had found was that most of time the ZTE MF626 would get itself into a an un-recoverable state -- the only solution would be completely shut down system so the dongle would lose power and revert to storage mode. (a soft reboot would keep usb devices powered up) And then to power up the system with wol packet from another machine on the network. 

Oddly enough, this GSM connection is the most reliable and fast connection for here in Dushanbe. It's not terribly economical, but its not too bad either.. I can easily hit 200k/sec doing package upgrades sometimes. I was very surprised, I knew that a new fiber turned up here last year - but I didn't think that I could get on it..

---

