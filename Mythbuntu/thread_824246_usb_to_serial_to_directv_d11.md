---
title: "usb to serial to directv d11"
date: 2008-06-09
forum: Mythbuntu
---

### Post by webwalker on 2008-06-09
OK, so I've just about pulled all my hair out and I'm ready to ask for help. (Not something I do easily.)

Motherboard is ABit AB9 Pro with no serial ports. (Boo.)

I installed a USB to Serial cable and in dmesg get:
```

[   49.289180] usb 7-2: pl2303 converter now attached to ttyUSB0

```
So far so good. I connected an identical cable (identical!) to the D11-500. I installed a null modem cable between them and then install the directv.pl version 1.9. Baud is 9600 (per the instructions) the port is /dev/ttyUSB0.

Got the following output:
```

root@phaeton:/usr/local/bin# /usr/local/bin/directv.pl verbose get_channel
SEND: 0xFA [ú] 0x87 [] 0x0 []
RECV: Timeout Error


SEND: 0xFA [ú] 0x87 [] 0x0 []
RECV: Timeout Error


SEND: 0xFA [ú] 0x87 [] 0x0 []
RECV: Timeout Error


SEND: 0xFA [ú] 0x87 [] 0x0 []
RECV: Timeout Error


Error excessive retries

```

==
So I'm stumped. I've spent hours online looking for hints, tips, or a flat out 'no this doesn't work' but I'm dead in the water.

Any helpful suggestions would be greatly appreciated. 

M

---

### Post by tgm4883 on 2008-06-09
> **webwalker said:**
> OK, so I've just about pulled all my hair out and I'm ready to ask for help. (Not something I do easily.)

Motherboard is ABit AB9 Pro with no serial ports. (Boo.)

I installed a USB to Serial cable and in dmesg get:
```

[   49.289180] usb 7-2: pl2303 converter now attached to ttyUSB0

```
So far so good. I connected an identical cable (identical!) to the D11-500. I installed a null modem cable between them and then install the directv.pl version 1.9. Baud is 9600 (per the instructions) the port is /dev/ttyUSB0.

Got the following output:
```

root@phaeton:/usr/local/bin# /usr/local/bin/directv.pl verbose get_channel
SEND: 0xFA [ú] 0x87 [] 0x0 []
RECV: Timeout Error


SEND: 0xFA [ú] 0x87 [] 0x0 []
RECV: Timeout Error


SEND: 0xFA [ú] 0x87 [] 0x0 []
RECV: Timeout Error


SEND: 0xFA [ú] 0x87 [] 0x0 []
RECV: Timeout Error


Error excessive retries

```

==
So I'm stumped. I've spent hours online looking for hints, tips, or a flat out 'no this doesn't work' but I'm dead in the water.

Any helpful suggestions would be greatly appreciated. 

M

Try turning off both boxes, then turn on the directv box, then turn on the mythbox and try again

---

### Post by webwalker on 2008-06-10
Will do. 

FYI some more info:

About 6 months ago I was using the Paterson USB TV translator. Worked great, but this was with a different chassis, one that had a standard serial port. 

When I changed chassis to the new board (sans Serial Port) I couldn't get TV translator working With a USB<->Serial adapter; I assumed that it would not work and found the instructions to use two USB to Serial devices with a null modem rollover in between.

I have since confirmed with Paterson Tech that the TV Translator SHOULD work in the configuration USB<->Serial<->TV-Translator<->D11-500.

This leads me to believe that I'm doing something wrong on the PC host side that is preventing the connection from working correctly.

I will perform the power up sequencing tonight based on what you describe.

Any additional suggests that you might load on now would be appreciated, that way I can try them tonight as well.

M

---

### Post by tgm4883 on 2008-06-10
Well I can confirm that the paterson TV Translator works with a usb to serial to tv translator.  That is how mine is setup on a directv D11-800.  I was having the same problem as you and powering up in the sequence above fixed it.

you could also try permissions, here is mine
```
-rwx------ 1 mythtv mythtv 20899 2008-05-13 16:51 directv.pl

```

I've also included my directv.pl from that machine that has that box.
You might also try the baud rate -115200 which is the other baud rate the script suggests for that box.

:EDIT:
Bah apparently ubuntuforums doesn't like .pl files.  It's inside the zip now.

---

### Post by webwalker on 2008-06-10
OK, here's the latest update:

I connected my Paterson TV Translator to my laptop (via USB, no serial on the laptop either) and launched their configurator, just to make sure things were up to date.

Interestingly, they were not. The TVT was at version 1.16, current was 1.17. This shouldn't matter. But just in case....I updated.

I now have the TVT installed in the following configuration:

AbitAB9Pro-USB<->USB<-PL2303->Serial<->Paterson TVT<->USB<->D11-500

I'm running the power cycle sequence now.

M

---

### Post by webwalker on 2008-06-10
Update:

No change. Power off on both host and D11 box. D11 box on. 30 seconds later, host on.

Ran your D11-800_directv.pl with

```
./D11-800_directv.pl verbose baudrate 9600 box_type D11 get_signal
SEND: 0xFA [ú] 0x90 [] 0x0 []
RECV: Timeout Error


SEND: 0xFA [ú] 0x90 [] 0x0 []
RECV: Timeout Error


SEND: 0xFA [ú] 0x90 [] 0x0 []
RECV: Timeout Error


SEND: 0xFA [ú] 0x90 [] 0x0 []
RECV: Timeout Error


Error excessive retries

```

Figured that I was almost back to 'out of ideas' but checked the diff on the two directv.pl files:

```
root@phaeton:~# diff D11-800_directv.pl /usr/local/bin/directv.pl               88c88
< $baudrate = "9600";
---
> $baudrate = "115200";
100c100
< $box_type = "RCA";
---
> $box_type = "D11";

```

So they're the same, except for the already over ridden baudrate and box_type.

Please note that I am running this script outside of mythtv, just as the root user, following the old proverb: if you can't get it working outside of mythtv, don't expect it to work inside mythtv.'

Back to the drawing board. Suggestions? :confused:

---

### Post by webwalker on 2008-06-11
Umm...BUMP?:(

---

### Post by webwalker on 2008-06-11
Yet another update from the original poster:

I was finally able to dig out an ancient laptop with Win2K on it (and a serial port!), install the TVtranslator configuration app and run the diagnostic procedure recommended there.

[http://www.patersontech.com/support/TvtTroubleshooting.aspx]("http://www.patersontech.com/support/TvtTroubleshooting.aspx")

The USB end goes in the D11-500 tuner, the serial port stays connected to the laptop. Opened the test window so I was able to send changes. (It noted that serial was connected, but USB be was not, which was correct: The USB end was connected to the D11, which the app can't see.)

I send the change channel command that toggles between channels 100 and 201, both channels that will work with a DirecTV tuner even without a auth card.

It works. Unfortunately. :(

So I'm back to trying to figure out why the hell I can't send messages to it from Linux. I am past frustrated at this stage. I even dropped back to a chassis I had that was running Gutsy and tried to send commands via directv.pl. No change. Same crap.

Any,any,any help...please!

---

### Post by tgm4883 on 2008-06-18
hmm

lets try this 
```
./directv.pl baudrate 115200 box_type D11 get_signal

```

---

### Post by webwalker on 2008-06-18
I unplugged the D11 first to make sure it booted with the TV translator already plugged in.

Then I ran the following commands and have included their output:

```

root@phaeton:~# dmesg | grep -e serial | grep usb
[   50.800380] usbcore: registered new interface driver usbserial
[   50.800444] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   50.800524] usbcore: registered new interface driver usbserial_generic
[   50.800574] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   50.840989] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for pl2303
[   50.841681] /build/buildd/linux-2.6.24/drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor driver
root@phaeton:~# setserial -a /dev/ttyUSB0                                       
Cannot get serial info: Invalid argument
root@phaeton:~# lsusb | grep -i Serial                                          
Bus 004 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
root@phaeton:~# /usr/local/bin/directv.pl verbose port /dev/ttyUSB0 baudrate 115200 box_type D11 get_signal
SEND: 0xFA [ú] 0x90 [] 0x0 []
RECV: Timeout Error


SEND: 0xFA [ú] 0x90 [] 0x0 []
RECV: Timeout Error


SEND: 0xFA [ú] 0x90 [] 0x0 []
RECV: Timeout Error


SEND: 0xFA [ú] 0x90 [] 0x0 []
RECV: Timeout Error


Error excessive retries
```

---

### Post by tgm4883 on 2008-06-19
I'm running out of ideas.  Make sure that it is /dev/ttyUSB0 and not like USB1 or something.  Also, try a different command such as off or on.  Try unplugging the directv box (power) leave the usb connected, reboot the machine, then plug the directv box back in

---

### Post by webwalker on 2008-06-19
The pl2303 is reported in dmesg as connected to /dev/ttyUSB0, and it does state 'connected' in dmesg.

I will run the following procedure and report back:

Configuration:
host <->USB to Serial-pl2303<->TV Translator<->D11-500

Power off all
Power on D11
Power on Host

Any other test suggestions?

---

### Post by webwalker on 2008-06-19
Well, I ran the procedure stated above and got exactly the same thing.

I even shifted from using the get_signal to using off as part of the test sequence. No change, other than the signal being sent.

At this point, I don't know what else to do.

Does anyone have any experience with PCI-e 1x based serial ports or PCI based serial ports? I'm pretty much dead in the water (and $500+ in to the project.

M

---

### Post by webwalker on 2008-06-28
That's it; I'm done with the Prolific chipset.

I ditched the USB to DB9 and replaced it with a pci-e dual serial port. Worked out of the box.

I spent 30+ hours diagnosing this. What a p*ssing waste!

M

---

### Post by apollyonis on 2008-09-14
Inquiring minds are curious as to which PCI-E dual serial port you went with - mine may be a similar situation and I'd rather try to get something that is known good.

---

### Post by ac7nj on 2008-09-19
first thing is I'm new to linux but I have a lot of experance with USB to serial coverters.

Not all USB to SERIAL coverters are the same some don't work as complete serial devices and some do. radio shack has a USB to SERIAL converter for example that will NOT work and EasySync, part number 540-0070 works well. I don't recomend one over the other I have found that 50% of the converters out there work.

Randy

---

