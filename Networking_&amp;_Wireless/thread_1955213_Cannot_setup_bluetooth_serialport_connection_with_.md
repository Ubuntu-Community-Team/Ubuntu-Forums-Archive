---
title: "Cannot setup bluetooth serialport connection with phone"
date: 2012-04-09
forum: Networking &amp; Wireless
---

### Post by 0AintLifeGrand0 on 2012-04-09
Hi All,

I'm trying to connect my android phone with my Ubuntu 11.10 laptop in order to send some data back and form through a 'hyperterminal' app on the android phone. 

I've tried this in windows 7 and it works like a charm, just install virtual com port, connect with phone and send text back and forward through Android Sena Bterm and W7 Putty Terminal.

I write code for the Android phone in Eclipse under Ubuntu, and since I don't want to switch to windows I need to be able to debug and have the functionallity as described above in Ubuntu. 
The problem is that I can't seem to get the bluetooth com port working. I run into a strange problem:

Let me describe what I do:
First ran 
```
hcitool scan
```This gives me the MAC from my phone : <My:Phones:MAC>

I then first look for the SP service on my USB Bluetooth dongle:
```
sdptool browse local
```This gives: 
Service Name: Serial Port
Service Description: COM Port
Service Provider: BlueZ
Service RecHandle: 0x44d
Service Class ID List:
  "Serial Port" (0x1101)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 1
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Serial Port" (0x1101)
    Version: 0x0100

So that looks ok. Channel 1 for SP service. 
Then I look for my phones SP service: 
```
sdptool search --bdaddr <My:Phones:MAC> SP 
```It gives no output. When I look with sdptool browse. I indeed cannot find a SP service. 

I can connect to my phone, e.g. with (using rfcomm0, channel 1):
```
rfcomm connect 0  <My:Phones:MAC> 1
```Which creates a connection, but it creates something of audio service connection (which can be explained when looking at the sdptool browse results, which list a headset audio gateway service for channel 1).

Since it does work in windows, I'm sure my phone must have the SP option.

Has anyone got a clue whats going wrong here?

---

