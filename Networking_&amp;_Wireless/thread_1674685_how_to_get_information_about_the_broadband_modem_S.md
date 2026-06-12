---
title: "how to get information about the broadband modem SIM card?"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by madmax75 on 2011-01-24
How do I get information about the SIM card of my USB broadband modem, for example it's phone number, serial number and so on, in Ubuntu 10.04?

Not about the usb modem itself - just the SIM card inside it.

Is there a way to probe it from the terminal, like you probe for usb devices with *lsusb*?

---

### Post by alexfish on 2011-01-24
can have a look here

[How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490") 

if you don't have a serial terminal , look at first post on how to use two terminal

then have a look at how to get info from the device using  a serial terminal; in there are links to AT command pdf files, most types of modems are covered , as some isp's and manufacturer's have specific commands

however , sometimes not listed is AT+CLAC , this usually lists the AT commands the device will recognize

alexfish

---

### Post by madmax75 on 2011-01-24
Wow, that's a LOT to waddle through :p

For the record, I'm not having any problems connecting the modem to the internet. Most of those instructions - which are a superb in itself - are concerned about getting info about the modem device itself. That's not quite what I'm after here.

I just pondered if there is a way to probe the SIM card of the modem from the terminal or from the desktop, especially to find out it's GSM number.

But maybe there is something in there, I just have to consume a couple of weeks to read through all that ;)

Thanks!

---

### Post by alexfish on 2011-01-24
how to waddle'le into a modem with a sim card, cor buy some reading spectacles......;)

open up a terminal

enter this code

```
dmesg | grep -e "modem" -e "tty"
```does it look like 
> [   27.684299] option 1-3:1.0: GSM modem (1-port) converter detected
[   27.684480] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB0
[   27.684500] option 1-3:1.1: GSM modem (1-port) converter detected
[   27.684598] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB1
[   27.684622] option 1-3:1.3: GSM modem (1-port) converter detected[   27.684732] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB2

can confirm it is in the devs

```
ls -al /dev/serial/by-id
```does it show similar to 

> usb-ZTE_Incorporated_ZTE_CDMA_Technologies_MSM_1234567890ABCDEF-if00-port0 -> ../../ttyUSB0
usb-ZTE_Incorporated_ZTE_CDMA_Technologies_MSM_1234567890ABCDEF-if01-port0 -> ../../ttyUSB1
usb-ZTE_Incorporated_ZTE_CDMA_Technologies_MSM_1234567890ABCDEF-if03-port0 -> ../../ttyUSB2
if so you will have to make a choice which port to connect some have a modem port {data port } and also a control port

I know this device uses ttyUSB2 to connect and ttyUSB1 for getting info / if ttyUSB2 is connected (your ports may be different)

so the choice would be /dev/ttyUSB1

so from the terminal I enter this command

```
tr -s "\n" < /dev/ttyUSB1
```now open up a second terminal


enter this command

```
echo -e "AT\r\n" > /dev/ttyUSB1
```if there is a response in the first terminal "OK" then your in

if you need to enter pin code example "AT+CPIN=1234\r\n"

```
echo -e "AT+CPIN=<pincode>\r\n" > /dev/ttyUSB1
```to get general info

```
[CODE]echo -e "ATI\r\n" > /dev/ttyUSB1
```[/CODE]to get the number

```
echo -e "AT+CNUM\r\n" > /dev/ttyUSB1
```for a easy input method try this code (beware there is no error trapping , but wont harm)
and must be run in a terminal

```
#!/bin/sh
# the next line restarts using tclsh \
exec tclsh "$0" "$@"
set port [exec zenity --title "serial-port ?" --width 500 --entry --text "EG /dev/ttyUSB1"]
set x 0
set rep "AT"
while "$x == 0" {
set ans [exec zenity --title "Serial" --width 500 --entry --text $port]
            set serial [open $port "r+"]
            fconfigure $serial -mode "115200,n,8,1"
            fconfigure $serial -blocking 0 -buffering full -ttycontrol {RTS 0 DTR 1}
            set status  [fconfigure $serial -ttystatus]
            ############################################
            # AT response
            after 300
            puts $serial $ans
            after 300
            flush $serial
            after 300
            set buffer [fconfigure $serial -queue]
            set rep [read $serial]
            set rep [string trim $rep]
            puts $rep

}
######################################################
```for the rest start reading :P

to run the script..: tclsh /path/to/script

PS:
I LOVE JAVA

alexfish

---

