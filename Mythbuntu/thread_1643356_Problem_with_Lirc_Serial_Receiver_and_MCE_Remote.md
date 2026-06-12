---
title: "Problem with Lirc Serial Receiver and MCE Remote"
date: 2010-12-11
forum: Mythbuntu
---

### Post by tanquef on 2010-12-11
Hello

I just received a lirc serial receiver that bought through ebay and i´m trying to use it with my MCE remote controller (dont have a USB RECEIVER)

the problem is that if i choose the MCE remotes option in the Mythtv Center, then it tries to receive codes from a USB receiver and not the serial port.

how can i change this??


any help would be appreciated!!

---

### Post by thatguruguy on 2010-12-12
Is it a receiver that someone built?  If so, set it up like a home-brew receiver.  There are various "how to" guides in the forums.

---

### Post by tanquef on 2010-12-12
> **thatguruguy said:**
> Is it a receiver that someone built?  If so, set it up like a home-brew receiver.  There are various "how to" guides in the forums.

Thanks for your reply!

can you point me to the right direction? because i checked the HOWTOs sticky, and also make a few searches, and coulndt find any solution...the only post with a similar problem bought a new usbmce receiver...

---

### Post by ian dobson on 2010-12-12
Hi,

maybe have a look here [http://ubuntuforums.org/showthread.php?t=572318&highlight=home+brew](http://ubuntuforums.org/showthread.php?t=572318&highlight=home+brew)

or just search for home brew here in the forum.

Regards
Ian Dobson

---

### Post by tanquef on 2010-12-12
i follow up this tutorial

[http://www.mythtv.org/wiki/Ubuntu_Serial_Lirc_Install](http://www.mythtv.org/wiki/Ubuntu_Serial_Lirc_Install)

it works great, but after i reboot the computer i couldnt make it to work again, no matter if i repeat the steps, the serial doesnt reveive any signals at all...

---

### Post by ian dobson on 2010-12-12
Hi,

What do you have in your /etc/setserial.conf file?

I have 
```

@myth-frontend:~# cat /etc/setserial.conf
#
###PORT STATE GENERATED USING AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
###AUTOSAVE###
#
# If you want to configure this file by hand, use
# dpkg-reconfigure setserial
# and change the configuration mode of the file to MANUAL. If you do not do this, this file may be overwritten automatically the next time you upgrade the
# package.
#
/dev/ttyS1 uart none

```

Normally linux takes control of serial ports and creates a tty connected to it. To use the serial port in lirc you need to tell linux not to use it.

Also do you have a /etc/init/setserial.conf file?

Regards
Ian Dobson

---

### Post by tanquef on 2010-12-12
> **ian dobson said:**
> Hi,

What do you have in your /etc/setserial.conf file?

I have 
```

@myth-frontend:~# cat /etc/setserial.conf
#
###PORT STATE GENERATED USING AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
###AUTOSAVE###
#
# If you want to configure this file by hand, use
# dpkg-reconfigure setserial
# and change the configuration mode of the file to MANUAL. If you do not do this, this file may be overwritten automatically the next time you upgrade the
# package.
#
/dev/ttyS1 uart none

```Normally linux takes control of serial ports and creates a tty connected to it. To use the serial port in lirc you need to tell linux not to use it.

Also do you have a /etc/init/setserial.conf file?

Regards
Ian Dobson

Ok i guess we are making some progress, because i dont have a /etc/setserial.conf file

can you walk me to it? but i need like an idiots guide, cause i dont know the linux commands yet (i ve been copy and paste all day)

---

### Post by ian dobson on 2010-12-12
Hi,

Just do sudo dpkg-reconfigure setserial

and say than the serial port your using for lirc should not be used by linux.

Regards
Ian Dobson

---

### Post by tanquef on 2010-12-12
one quick question, how can i tell which com port im using?

i have a 
**Intel BOXD945GCLF Intel Atom processor 230 Intel 945GC Mini ITX Motherboard/CPU Combo**


and i checked on the bios, but there is no info about the port, irq and address.

the motherboard only has one seria and one parallel port...

is there a command i could run to check this?

---

### Post by ian dobson on 2010-12-12
Hi,

If you only have one serial port then it's comm1 (/dev/ttyS0) but it wouldn't hurt to set ttyS0 and ttyS1.

Also maybe have a look in the system boot log file (sudo dmesg|more) looking for errors from lirc.

Regards
Ian Dobson

---

### Post by tanquef on 2010-12-12
> **ian dobson said:**
> Hi,

If you only have one serial port then it's comm1 (/dev/ttyS0) but it wouldn't hurt to set ttyS0 and ttyS1.

Also maybe have a look in the system boot log file (sudo dmesg|more) looking for errors from lirc.

Regards
Ian Dobson


ok, i run the command you told me, and this is the part i read from lirc, however there is no /dev/ttyS0)

```

[  841.803484] lirc_dev: IR Remote Control driver registered, major 61 
[  841.825493] IR NEC protocol handler initialized
[  841.827394] usbcore: registered new interface driver mceusb
[  841.833263] IR RC5(x) protocol handler initialized
[  841.839018] IR RC6 protocol handler initialized
[  841.844958] IR JVC protocol handler initialized
[  841.852037] IR Sony protocol handler initialized
[  841.857097] ir_lirc_codec: Unknown symbol lirc_dev_fop_poll (err 0)
[  841.857488] ir_lirc_codec: Unknown symbol lirc_dev_fop_open (err 0)
[  841.857809] ir_lirc_codec: disagrees about version of symbol lirc_get_pdata
[  841.857817] ir_lirc_codec: Unknown symbol lirc_get_pdata (err -22)
[  841.858142] ir_lirc_codec: Unknown symbol lirc_dev_fop_close (err 0)
[  841.858437] ir_lirc_codec: Unknown symbol lirc_dev_fop_read (err 0)
[  841.858695] ir_lirc_codec: disagrees about version of symbol lirc_register_dr
iver
[  841.858702] ir_lirc_codec: Unknown symbol lirc_register_driver (err -22)
[  841.859359] ir_lirc_codec: Unknown symbol lirc_dev_fop_ioctl (err 0)
[ 1902.368035] lirc_serial: auto-detected active low receiver
[ 1902.368044] lirc_dev: lirc_register_driver: sample_rate: 0
[ 1902.368205] lirc_serial $Revision: 5.108 $ registered
[25899.304098] usb 4-1: USB disconnect, address 2
[25908.053051] usb 4-1: new low speed USB device using uhci_hcd and address 3
[25908.261405] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/
usb4/4-1/4-1:1.0/input/input4
[25908.261829] generic-usb 0003:046D:C51B.0003: input,hidraw0: USB HID v1.11 Mou
se [Logitech USB Receiver] on usb-0000:00:1d.2-1/input0
[25908.276483] generic-usb 0003:046D:C51B.0004: hiddev96,hidraw1: USB HID v1.11 
Device [Logitech USB Receiver] on usb-0000:00:1d.2-1/input1

```

---

### Post by thatguruguy on 2010-12-12
You're still showing a usb receiver.  Why?

You may want to completely remove lirc and reinstall it.  Here's a guide on setting up a serial receiver:

[http://ubuntuforums.org/showthread.php?p=8741679#post8741679](http://ubuntuforums.org/showthread.php?p=8741679#post8741679)

---

### Post by tanquef on 2010-12-14
> **thatguruguy said:**
> You're still showing a usb receiver.  Why?

You may want to completely remove lirc and reinstall it.  Here's a guide on setting up a serial receiver:

[http://ubuntuforums.org/showthread.php?p=8741679#post8741679](http://ubuntuforums.org/showthread.php?p=8741679#post8741679)


thats the last guide i follow up, however when i reach the MODE2 command, i press the keys on the remote and there are no vital signs...

also the report was do it after the tutorial you linked me.

there are 2 things i didnt do it, since when i reach the mode2 part there were no keys, i didnt continue the tutorial, and also i didnt reboot the pc.

not sure if that has something to do with it, i still have the computer powered without reboot since that step, so i can continue from there if its needed...

---

### Post by tanquef on 2010-12-18
any new hints?

---

### Post by ian dobson on 2010-12-19
Hi,

What do you have in your /etc/lirc/hardware.conf?

On my frontend I have :-

```
 cat hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
[B][U]REMOTE="Home-brew (16x50 UART***patible serial port)"
#REMOTE_MODULES="lirc_dev lirc_serial"
REMOTE_MODULES="lirc_serial"[/U][/B]
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
REMOTE_SOCKET=""
TRANSMITTER_SOCKET=""
```

Note the lirc_serial line.

Regards
Ian Dobson

---

