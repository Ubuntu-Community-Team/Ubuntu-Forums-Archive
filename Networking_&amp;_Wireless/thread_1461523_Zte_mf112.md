---
title: "Zte mf112"
date: 2010-04-24
forum: Networking &amp; Wireless
---

### Post by Olmy on 2010-04-24
Does anyone know if the ZTE MF112 3g wireless dongle (as supplied by 3 in the UK) works with ubuntu?

I've found all sorts of other ZTE dongles mentioned but not this one...

Thanks in advance...

---

### Post by pdc on 2010-04-24
Does the 3 network not allow you a 3 day trial period;

it's called try before you buy ..........

Did you google on your question: 

if nothing posted on google ......... you are going to have to be the trailblazer ..........

---

### Post by pabc on 2010-05-22
from a googlecache webpage - the original page appears dead;

"Anyway on to mobile computing. I picked up a PAYG dongle – A **ZTE** **MF112** –  from Three pretty cheap and thought I’d try broadband on the run. By the  way this works fine with **Ubuntu** Lucid Lynx. The only trick is the dongle  mounts as a CD drive – just eject it using the file manager then set up  your network connection using Network Manager ((icon at top right of  screen)."

So that would be a yes then

---

### Post by yenrab on 2010-05-25
> **pabc said:**
> from a googlecache webpage - the original page appears dead;

"just eject it using the file manager then set up  your network connection using Network Manager ((icon at top right of  screen)."


I've just bought one of these, and can confirm that this method works in both my installed 9.10 system and on a 10.04 live CD. I'm posting this through the 3 network.

On 9.10 I eject the drive and then click the network manager icon in the task bar, click "3 Internet" and it connects.

On 10.04 its similar but I have to answer some questions in dialog boxes. The only bit I found tricky was that I needed to select "Britain (UK)" from the menu, and I initially looked for United Kingdom and England in the alphabetical list.

The dongle also has a place to insert a micro-sd card, and it works as a memory stick if you put one in.

I didn't think of ejecting the drive until I read about it here, so I think it would be really good if there's a way to change something in ubuntu to make this unnecessary, and possibly also to pop up some sort of notification when the dongle is plugged in.

---

### Post by carkat on 2010-05-29
I've just bought one of these, too, but ran into some issues (ubuntu lucid with newest updates):

1) no disk appears, so nothing can be ejected. no connection possible.
2) a further investigation in this issue showed a strange behaviour:

-- plugging in the dongle while the system is up and running will do nothing, though lsusb says i attached a pendrive (see attached lsusb.log1 and dmesg.log1)
-- plugging in the dongle BEFORE starting up the system recognizes it most of the time (not always) as hsdpa modem but no connection can be established (see attached lsusb.log2 and dmesg.log2)
-- in very rare cases the dongle is recognized (plugging in while the system is up and running) and a connection can be established (see attached lsusb.log3 and dmesg.log.3 in the next posting)

note: usb-modeswitch is installed.

any help would be greatly appreciated!
thanks a lot - carkat

---

### Post by carkat on 2010-05-29
the last logfile:

---

### Post by pdc on 2010-05-29
in dmesg.log1 you get this

> 89.768426] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0
[   89.768446] option 1-6:1.1: GSM modem (1-port) converter detected
[   89.768544] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1
[   89.768561] option 1-6:1.2: GSM modem (1-port) converter detected
[   89.769786] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2

that means it is ready to go:

configure as here

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

how to create a mobile broadband connection 

10.04 flips these devices automatically; you just need to configure ..

let us know how you get along

I don't believe you needed usb_modeswitch

and dmesg.log3 says the same thing as above

> USB **Serial support registered for GSM modem** (1-port)
[  193.711934] option 1-6:1.0: GSM modem (1-port) converter detected
[  193.713345] usb 1-6: **GSM modem (1-port) converter now attached to ttyUSB0**
[  193.713373] option 1-6:1.1: GSM modem (1-port) converter detected
[  193.713516] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1
[  193.713535] option 1-6:1.2: GSM modem (1-port) converter detected
[  193.714775] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2

which country are you in carkat? which provider?

incidentally, you will see from this thread

[http://www.backports.ubuntuforums.org/showthread.php?p=9204995](http://www.backports.ubuntuforums.org/showthread.php?p=9204995)

that the Scotsman reported that with 10.04 he plugged in an ZTE MF112 and it just sorta worked ...........

---

### Post by carkat on 2010-05-30
thanks a lot for the quick reply!

so i removed usb-modeswitch with the same result in dmesg -> seems it is not needed...

then i tried the how-to from pharscape.org and it seems the hso module is not loaded. with
```
**find /lib/modules/`uname -r` -name 'hso.ko'**
```
i can see that the module is installed but
```
**lsmod | grep hso**
```
gives me nothing.

installing ozerocdoff gives the same result.

the configuration of the network manager is working (i'm located in austria, provider is "yesss") since i was using it with another gsm-modem (huawei e1552) without issues.

any ideas?

---

### Post by carkat on 2010-05-30
ok, so i plugged it in again and it's working now (one of the rare cases...).
```
lsmod | grep hso
``` still gives nothing so i would assume it is not needed?

---

### Post by pdc on 2010-05-30
great!

when I said

> configure as here

[http://www.pharscape.org/networkmana...an-modems.html](http://www.pharscape.org/networkmana...an-modems.html)

how to create a mobile broadband connection 

I forgot to include

> **Go halfway down page** 

and read the entry that says ... *create a mobile broadband connection* ............

Sorry; (have a read at that section now ..)

glad it is working

perhaps taking out usb_modeswitch worked, as 10.04 autoflips these devices now:

they are getting very close to plug and play ... or plug and configure and play ...

(So hso was **NEVER** part of the plan ..............)

---

### Post by carkat on 2010-05-30
thaks a lot for your help!

i think the issue was some kind of conflict with usb-modeswitch. when i plug in the device now it works... 

one last remark: when i plug in the device BEFORE booting the system the dongle wouldn't work. though in this case it is possible to connect via Sakis3G ( [http://www.sakis3g.org/](http://www.sakis3g.org/) )

---

### Post by Phillip Spencer on 2010-07-31
Thanks for this thread... I found it very helpful after getting a ZTE112 with a mobile broadband contract with 3 in the UK.  It works with two laptops, one running Karmic the other running Lucid.  Oddly, karmic is more straightforward!

On the Karmic laptop, I plug in, the "3" icon comes up and, after the first time through for setup, when I click "Eject" the icon goes from the desktop and the network connection starts.

On the Lucid laptop, when I plug in nothing appears to happen automatically.  I have to go to "Places" drop-down, "Mount" the dongle as a CD drive, close the file manager and then "Eject".  Mostly it starts the auto-connection but sometimes does not, so I have to click on the network status icon where it shows as an available connection which I can then activate.  A bit of a pain but at least it works!

---

### Post by UbuKunubi on 2010-10-30
> **Phillip Spencer said:**
> Thanks for this thread... I found it very helpful after getting a ZTE112 with a mobile broadband contract with 3 in the UK.  <...... snip ......> 
 I have to go to "Places" drop-down, "Mount" the dongle as a CD drive, close the file manager and then "Eject".  Mostly it starts the auto-connection but sometimes does not, so I have to click on the network status icon where it shows as an available connection which I can then activate.  A bit of a pain but at least it works!

Hi there!
I also have one of these dongles running on Ubuntu 10.04 lts.
To solve the problem of ejecting the drive by waiting for the view to open for showing the files, do this:

[1] right click on your panel, and select 'Add to panel...'
[2] select the top item, 'custom app launcher', then click Add button
[3] change the type of launcher to 'application in terminal'.
I gave mine the following details:
[4] changed icon to 'engine' blue cog type, just because.....
[5] entered 'GET ONLINE' as its name, and 'eject the 3 CD rom' as its comment.
[6] in command type (or copy and paste from here)
```

 eject /dev/disk/by-label/3Connect

```
[7] click OK, and job done. 

When you first plug in the dongle and the light is solid green, simple click the button and then  your free to start the connection from the 'network' icon near your clock.

Hope this helps,
Ubu

---

### Post by carkat on 2010-10-31
> **carkat said:**
> thaks a lot for your help!

i think the issue was some kind of conflict with usb-modeswitch. when i plug in the device now it works... 

one last remark: when i plug in the device BEFORE booting the system the dongle wouldn't work. though in this case it is possible to connect via Sakis3G ( [http://www.sakis3g.org/](http://www.sakis3g.org/) )

hi, me again. after some time of using the device i have to say that my problems still persist.

after plugging in the dongle the connection sometimes pops up in the network status menu and sometimes not. unfortunately most of the time not. plugging it off and on again (a few times) resolves the problem.

oh, and sakis3g doesn't help...

any hints?

thanks a lot,
carlos

---

### Post by spaceshipguy on 2011-02-16
I have one of these.
I go to configure VPN connections - even though I have already set up my connection - from the dropdown and then mobile broadband then add (then often a message comes up telling me I am disconnected)
Then I open a terminal and type lsusb
Then I wait five or six minutes and the modem icon (a very pretty 3) appears on my desktop
Then when I go to the connection drop down my modem is listed as an option, just the way I set it up.
I click it and it connects.

Bit of a run around, but it works every time - but only if the dongle is inserted after startup and about 10 seconds on my quite-fast lappy.

---

### Post by jby601 on 2012-04-13
I got my ZTE MF112 dongle working as follows in Ubuntu 10.04:

As root, I added a text file with the name: 19d2:0103 to /etc/usb_modeswitch.d
This file has the following contents:

########################################################
# ZTE MF112 (written 12 April 2012)
# Info from: [www.draisberghof.de/usb_modeswitch/device_reference.txt](www.draisberghof.de/usb_modeswitch/device_reference.txt)

DefaultVendor= 0x19d2
DefaultProduct=0x0103

TargetVendor=  0x19d2
TargetProduct= 0x0031

CheckSuccess=20

MessageContent="5553424312345678000000000000061b000000020000000000000000000000"
MessageContent2="55534243876543212000000080000c85010101180101010101000000000000"

NeedResponse=1



Then, as root, I added these lines for an MF112 to /lib/udev/rules.d/40-usb_modeswitch:

# ZTE MF112
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="0103", RUN+="usb_modeswitch '%b/%k'"


Now my computer switched the dongle from the 'installation' CDROM mode to the serial communication mode automatically and all that I have then to do is select the dongle in the Network Manager.

---

