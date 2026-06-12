---
title: "Directv"
date: 2008-10-03
forum: Mythbuntu
---

### Post by murmsk on 2008-10-03
I am having trouble getting mythtv connect to my d11 directv box. I have followed the instructions, choose a usb-serial converter on the list, downloaded directv.pl, booted directv first them mythtv ... but it still ignores me. I get no error messages just doesn't work. Any ideas

why can't we just use a usb connector without going through the null modem cable?

steve

---

### Post by tgm4883 on 2008-10-03
> **murmsk said:**
> I am having trouble getting mythtv connect to my d11 directv box. I have followed the instructions, choose a usb-serial converter on the list, downloaded directv.pl, booted directv first them mythtv ... but it still ignores me. I get no error messages just doesn't work. Any ideas

why can't we just use a usb connector without going through the null modem cable?

steve

From [http://www.mythtv.org/wiki/index.php/Talk:Controlling_DirecTV_Set_Top_Box_(STB)_via_USB_or_Serial](http://www.mythtv.org/wiki/index.php/Talk:Controlling_DirecTV_Set_Top_Box_(STB)_via_USB_or_Serial)

>  Why USB to serial? Why not USB to USB?

If the DirectTV receiver has a USB port and my MythTV PC has a USB port, why can't I connect them with a USB cable? Why do we have to connect USB to serial?

Answer: Perhaps using a USB Bridge cable you can connect the PC to the STB but haven't tested that. This is a special USB cable with a small electronic circuit in the middle, You can't use a direct USB A/A cable, this can burn your USB ports!!!

I found a USB null modem cable (USB NMC-2.5m) seen on this page [http://www.ftdichip.com/Products/EvaluationKits/USB-USBNullModem.htm](http://www.ftdichip.com/Products/EvaluationKits/USB-USBNullModem.htm) Does anyone have experience using this connector for the D11 STB? Mgpalmer 18:25, 25 September 2008 (UTC)
[edit]


Note that not all usb-> serial cables are the same.  Where did you get yours from?

---

### Post by murmsk on 2008-10-13
I bought a Sabrent form newegg which is said to be compatible. 

 Is there a command that I can type into the terminal to check hardware vs. software.

---

### Post by murmsk on 2008-10-13
in another post someone mentioned running the command

directv.pl verbose get_channel

when I do I get a command not found

thanks  steve

---

### Post by murmsk on 2008-10-13
I forgot the ./

now ./directv.pl verbose get_channel  

SEND: 0xFA [ú] 0x87 [] 0x0 []
RECV: Timeout Error


SEND: 0xFA [ú] 0x87 [] 0x0 []
RECV: Timeout Error


SEND: 0xFA [ú] 0x87 [] 0x0 []
RECV: Timeout Error

any ideas?
steve

---

### Post by fenian on 2008-10-14
Did you change the serial port settings in the script?

If not open a terminal and type

dmesg

It should list your usb serial adapter ,probably as /dev/ttyUSB0

Find this line in the directv.pl script..

$serport = "/dev/ttyS0";  

and change it to this

$serport = "/dev/ttyUSB0";

You can also change the baud rate to 115200 and see if that helps.

---

