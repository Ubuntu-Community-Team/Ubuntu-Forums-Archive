---
title: "Banglalion Dongle usb modem not connect in Ubuntu 10"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by tariqul73 on 2010-05-29
Dear All
I use Banglalion WiMax usb dongle modem. I like to use it in ubuntu os. When I connect it to my Desktop PC's usb port, it respond nothing. How can I solve this problem. I am a new user in ubuntu os.

My device name us211 WiMax usb adapter.

I need help.

---

### Post by pdc on 2010-05-30
if you open a terminal: System: accessories: terminal

and type 

> lsusb

and tell the result for this device?

---

### Post by tariqul73 on 2010-05-30
> **tariqul73 said:**
> Dear All
I use Banglalion WiMax usb dongle modem. I like to use it in ubuntu os. When I connect it to my Desktop PC's usb port, it respond nothing. How can I solve this problem. I am a new user in ubuntu os.

My device name us211 WiMax usb adapter.

I need help.

When I use the lsusb command, the following message are shown-

   Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
  Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
  Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
  Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
  Bus 001 Device 004: ID 198f:0220 Beceem Communications Inc. 
  
  Bus 001 Device 002: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
  
  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by pdc on 2010-05-30
have a google search on 

> linux 198f:0220

and 

> ubuntu 198f:0220

and

> fedora 198f:0220

and see if you find anything helpful

I will check back later

____________

I note also that this USB device has been flipped (by usb_modeswitch) to give this ID

it would initially show as 

> ID 198f:bccd in an older system: 

here is its usb_modeswitch entry

> # Beceem BCSM250
#
# Contributor: Alexander Gordeev

;DefaultVendor= 0x198f
;DefaultProduct=0xbccd

;TargetVendor=  0x198f
;TargetProduct= 0x0220

# only for reference and 0.x versions
# MessageEndpoint=2

MessageContent="55534243f0298d8124000000800006bc626563240000000000000000000000"


---

### Post by shababhsiddique on 2010-09-26
so what was the solution?

make a rule in udev? with these? or how. plz tell me

# Beceem BCSM250
#
# Contributor: Alexander Gordeev

;DefaultVendor= 0x198f
;DefaultProduct=0xbccd

;TargetVendor=  0x198f
;TargetProduct= 0x0220

# only for reference and 0.x versions
# MessageEndpoint=2

MessageContent="55534243f0298d8124000000800006bc62  6563240000000000000000000000"

---

### Post by shababhsiddique on 2010-09-26
so. should i just run-

sudo usb_modeswitch -v 0x198f -p 0xbccd -V 0x198f -P 0x0220 -m 2

---

### Post by dewsworld on 2010-10-17
Same problem here!

---

### Post by muntasir_120 on 2011-04-24
I have the same problem. My modem is a ZTE ax 226 USB Dongle. Plugging it on in Ubuntu 10.10 has no effect although the modem's LED lights up. Here's the output of lsusb (note I am booting Ubuntu from my USB pen drive so that shows up as well):

```
Bus 002 Device 005: ID 19d2:bccd ONDA Communication S.p.A. 
Bus 002 Device 004: ID 090c:1000 Feiya Technology Corp. Flash Drive
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0402:9665 ALi Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I know I can just run Windows in a VM and use that to gain internet access, but I am running it on a laptop and don't really want to run a VM on it all the time.

Is there any general solution to this problem?

---

### Post by Anwarshah on 2011-07-01
I have got a solution to this problem. [In this russian forum]("http://www.opennet.ru/openforum/vslu...ID3/71759.html"), But I cannot try this now

---

### Post by Anwarshah on 2011-07-01
Banglalion introduces new device ZTE AX226 Modem. I successfully modeswitched this device from 19d2:bccd to 19d2:0172 which is a modem.But the driver is not ready yet. I found a solution in this [russian forum]("http://www.opennet.ru/openforum/vslu...ID3/71759.html") . Please raise your voice about this problem

---

### Post by Blackreaper17 on 2011-10-21
can u please tell the solution as I am also facing the same problem

---

### Post by u_know_who on 2012-04-13
Well, i am installed ubuntu in my hdd with vmware while still having windows7 and i can now run internet (banglalion usb modem) in ubuntu through VMWare (in fact i am ubuntu os while making this comment)

---

### Post by ILUVU on 2012-05-28
Hi tariqul73,

Good news for U and your us211 WiMax usb adapter.

Go to this page,
[http://luv2know.wordpress.com/](http://luv2know.wordpress.com/)

inshalla you must find the solution of your us211. 

also anyone will be able to use Banglalion modem in ubuntu 100 % working

---

