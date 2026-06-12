---
title: "[SOLVED] directv serial control"
date: 2008-05-25
forum: Mythbuntu
---

### Post by nrune on 2008-05-25
Mythbuntu is working well, I am having issues controlling to directv sat box which is a d10-100. I made a serial to mini rj11 cable from this guide:

[http://www.mythtv.org/wiki/index.php/Controlling_DirecTV_Set_Top_Box_(STB)_via_USB_or_Serial](http://www.mythtv.org/wiki/index.php/Controlling_DirecTV_Set_Top_Box_(STB)_via_USB_or_Serial)

I have tested the cable that I made using my multimeter and all the pin outs are correct and test good.

when I run to test the script I get 

```
nrune@mythtv:~$ ./directv.pl 245
Error excessive retries

```

My guess is that my serial port on the motherboard is not set up correctly,but I am not sure in Linux how to fix this. I have done some searching and I am still not really sure how to troubleshoot this. 

Dmesg serial related stuff

```
[   28.982770] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   28.982914] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.983063] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   28.983530] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.983722] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
``` 

I only have one serial port and one parallel port. 4 usb ports. My motherboard is an Asus A8R-MX and serial ports are enabled in bios. 


Any help appreciated

---

### Post by tgm4883 on 2008-05-25
I had that same problem.  One thing to try is to turn off both the mythtv box and the directv box.  Then turn the directv box on, then turn on the mythtv box.  Another thing to make sure is that you are using the correct settings for your box.  I think you need to pass the "box_type D10" option at the command line.

---

### Post by nrune on 2008-05-25
Okay tried all of that, including the reboot and still getting excessive retries.  Any other ideas?

Mike

Installed statserial and got this...
```
Device: /dev/ttyS0

Signal  Pin  Pin  Direction  Status  Full
Name    (25) (9)  (computer)         Name
-----   ---  ---  ---------  ------  -----
FG       1    -      -           -   Frame Ground
TxD      2    3      out         -   Transmit Data
RxD      3    2      in          -   Receive  Data
RTS      4    7      out         1   Request To Send
CTS      5    8      in          0   Clear To Send
DSR      6    6      in          0   Data Set Ready
GND      7    5      -           -   Signal Ground
DCD      8    1      in          0   Data Carrier Detect
DTR     20    4      out         1   Data Terminal Ready
RI      22    9      in          0   Ring Indicator

```

does this mean my cable is okay or screwed up. 

thanks for any help. 

Mike

---

### Post by tgm4883 on 2008-05-25
I'm not entirely sure, I bought known working cables.  I remember reading somewhere that the error may be caused by (I think) the tx and rx cables being reversed.  You might want to google on the mythtv wiki to see if thats right though.

---

### Post by nrune on 2008-06-04
Okay well I have the same problem after getting an official cable. 

```
Device: /dev/ttyS2

Signal  Pin  Pin  Direction  Status  Full
Name    (25) (9)  (computer)         Name
-----   ---  ---  ---------  ------  -----
FG       1    -      -           -   Frame Ground
TxD      2    3      out         -   Transmit Data
RxD      3    2      in          -   Receive  Data
RTS      4    7      out         1   Request To Send
CTS      5    8      in          0   Clear To Send
DSR      6    6      in          0   Data Set Ready
GND      7    5      -           -   Signal Ground
DCD      8    1      in          0   Data Carrier Detect
DTR     20    4      out         1   Data Terminal Ready
RI      22    9      in          0   Ring Indicator

```

```
nrune@mythtv:~$ sudo ./directv.pl box_type D10-100 port /dev/ttyS0 off
[sudo] password for nrune: 
getattr: Input/output error
nrune@mythtv:~$ sudo ./directv.pl box_type D10-100 port /dev/ttyS1 off
getattr: Input/output error
nrune@mythtv:~$ sudo ./directv.pl box_type D10-100 port /dev/ttyS2 off
Error excessive retries

```

Same problems after changing bios settings.  Any ideas? 

Mike

---

### Post by nrune on 2008-06-04
Dmesg output

[   26.928061] Linux agpgart interface v0.102
[   26.928063] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.928269] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   26.928405] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[   26.928820] 00:0b: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[   26.929010] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A


and later on

[   43.779043] lirc_serial: port 02f8 already in use
[   43.779046] lirc_serial: use 'setserial /dev/ttySX uart none'
[   43.779048] lirc_serial: or compile the serial port driver as module and
[   43.779050] lirc_serial: make sure this module is loaded first

The 0x3e8 on ttyS2 is the current setting in bios.  So is the low speed port turned on the d10?  and how would I know it is turned on?

---

### Post by nrune on 2008-06-04
Talked with script author, turns out serial port is nonfunctional. on to usb to serial..  ugg one more part....

---

### Post by macbookpro2 on 2008-07-28
I currently have (2) D11-100 boxes hooked up to a PVR-500. Most of the time everything works great. Both are hooked up to serial ports on the motherboard (/dev/ttyS0 and /dev/ttyS1) >> Null Modem Serial Cable >> USB to Serial Adapter >> D11 USB port. Sometimes for no reason and with no warning recordings start failing due to a channel change error (this almost always happens to one and not the other box). Unplugging and replugging the USB cable from the cable box fixes the problem. I thought I had a solution of resetting the cable box once a day using a cron job, but that does not seem to be working. Both receivers work most of the time, both fail some of the time (not at the same time). I can live with physically resetting the boxes when they fail, but I wanted to know if anyone has good ideas on how to alert me when a failure happens, and also ideally is there a way to auto failover to the other available tuners when one fails. I am pretty sure you can rearrange the priorities of your tuners, but I never know which one will fail.

---

### Post by microdot71 on 2009-11-10
> **macbookpro2 said:**
> I currently have (2) D11-100 boxes hooked up to a PVR-500. Most of the time everything works great. Both are hooked up to serial ports on the motherboard (/dev/ttyS0 and /dev/ttyS1) >> Null Modem Serial Cable >> USB to Serial Adapter >> D11 USB port. Sometimes for no reason and with no warning recordings start failing due to a channel change error (this almost always happens to one and not the other box). Unplugging and replugging the USB cable from the cable box fixes the problem. I thought I had a solution of resetting the cable box once a day using a cron job, but that does not seem to be working. Both receivers work most of the time, both fail some of the time (not at the same time). I can live with physically resetting the boxes when they fail, but I wanted to know if anyone has good ideas on how to alert me when a failure happens, and also ideally is there a way to auto failover to the other available tuners when one fails. I am pretty sure you can rearrange the priorities of your tuners, but I never know which one will fail.

You might have some luck with a cron job. I have an H23-200 with the usb "serial" port on the back.  I change channels through a Patterson USB TV Translator cable using the directv.pl script that I found on this site: [http://www.pdp8online.com/directv/directv.shtml]("http://www.pdp8online.com/directv/directv.shtml"). 

I was having this issue where channel changes would work for a day or so then stop.  It looks like the "serial" port on the back of the H23 times out and the only way to fix it is to press the reset button.  

So what I did was get the changes working after a reset then I coded a cron job to issue the command to get the receiver's signal strength every half hour (I do it at 17 and 47 after the hour so that it doesn't interfere with actual recording). This seems to keep the receiver's serial port alive. 

It's a kludge, I know, but maybe you can do something similar.

---

