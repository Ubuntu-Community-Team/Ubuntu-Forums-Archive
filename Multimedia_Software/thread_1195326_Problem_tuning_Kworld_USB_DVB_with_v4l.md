---
title: "Problem tuning Kworld USB DVB with v4l"
date: 2009-06-23
forum: Multimedia Software
---

### Post by geekyhawkes on 2009-06-23
I am having problems getting my Kworld U399 DVB usb stick tuned under Kubuntu 810.  

When i look in /dev/dvb0 it has all the right folders (ie demux and adapter), but tuning via DVB utils returns;

WARNING: >>> tuning failed with the
tune to: return above it.  

If i run dmesg after the tune then the following is displayed;

af9015 : command failed:2
af9013: IC2 read failed reg:d330

Higher up the dmesg output the card seems to be I.D'd correctly and initialised;


usbcore: registered new interface driver dvb_usb_af9015
usbcore: registered new interface driver prism54usb


DVB: registering adapter 1 front end 0 (afatech AF9013 DVB-T)
MXL5005S:Attached at address 0xc6
dvb-usb:schedule remote query interval 150ms
dvb-usb: Kworld PLusTV Dual DVB-T Stick (DVB-T 399U) successfully initialized and connected.


I am using qn up to date v4l lib (as far as i can tell) installed and compiled with hg as per the wiki guide at linuxtv.  

I am just going through the system log files and I am in dual tuner mode (with both adapters listed in /dev/dvb/adapter0 and 1).  From the output of my dmesg log everything seems to be loaded and working, although i am a bit confused with the following line;

dvb-usb: Kwolrd PlusTV Dual DVB-T Stick (DVB-T 399U) successfully initialized and connected.
input: Afatech DVB-T 2 as /devices/pci0000:00/0000:00:04/1/usb4/4-3/4-3:1.1/input/input10
input,hidraw1: USB HID v1.01 keyboard [Afatech DVB-T 2] on usb-0000:00:04.1-3

Am i missing something or is somehow part of the dvb being loaded as a keyboard?

I am feeling fairly out of my depth now as to how to fix this issue.  From what i can see over at Linuxtv the Kworld card is fully supported by the latest v4l lib, but i just cant get it working.

Any help, or tips, or steers would be well received as I am running out of ideas! 

Thanks.

---

### Post by geekyhawkes on 2009-06-24
Is anyone able to help?

---

### Post by xc3RnbFO8P on 2009-06-24
Did you read this:
[http://www.linuxtv.org/wiki/index.php/KWorld_399U_Dual_DVB-T_USB_tuner]("http://www.linuxtv.org/wiki/index.php/KWorld_399U_Dual_DVB-T_USB_tuner")

---

### Post by geekyhawkes on 2009-06-25
Yes i had thanks. I have both of those bits of firmware loaded as part of the v4l lib.   

Anyother ideas how i can move forward and fault find?

---

### Post by xc3RnbFO8P on 2009-06-25
As he said:
> Have successfully got this working using the built in drivers of kernel 2.6.30 (**might possibly** work with slight earlier version as well).

---

### Post by geekyhawkes on 2009-06-25
EDIT:  UPDATE


Right i might be getting somewhere.  I have manually modprobe loaded the dvb_usb_af9015 and mxl5005s modules.

When i try and tune the following is reported back;

Initial transponder 4900000000 0 2 1 3 0 0 0
Initial transponder 5140000000 0 2 1 3 0 0 0
Initial transponder 5700000000 0 2 1 3 0 0 0
ETC

>>tune to 490000: I999B8 ETC
-tune-to-transponder:I491: ERROR: FE_READ_STATUS failed : 121 Remote I/O error

this is repeated for each of the transponder tunes with the 121 Remote I/O error.

Dmesg returns the following:

mxl5005s I2C write failed
af9015: bulk message failed:-22 (8/70)
af9013: I2C read failed reg d:417


repeated several times with slightly different values for the reg d but the same theme.

Anyone have any ideas? This seems a step forwards slightly.

---

### Post by geekyhawkes on 2009-06-26
As an aside the wiki here

[http://www.linuxtv.org/wiki/index.php/KWorld_399U_Dual_DVB-T_USB_tuner](http://www.linuxtv.org/wiki/index.php/KWorld_399U_Dual_DVB-T_USB_tuner)

States the card works with kernel 2.6.30 but  UNAME -A shows that the my kernel is only 2.6.27-14-generic.

Could this be the issue, or is the kernel version a bit of a smoke screen?

---

### Post by geekyhawkes on 2009-06-27
Anyone?  Is there an easy way to upgrade / downgrade m kernel if required?

---

### Post by geekyhawkes on 2009-06-28
Im guessing it isnt an obvious fix due to the lack of replies.  Does anyone have an idea how i might move forward?

---

