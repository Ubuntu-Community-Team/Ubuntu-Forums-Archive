---
title: "Ubuntu 10.4 / SMS / Sierra Wireless"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by mikecanada on 2010-05-30
Hi,
Is it possible using Ubuntu 10.4 and a Sierra Wireless 306 usb modem to receive SMS messages ? This is because the Watcher program in the usb stick will not appear on Linux otherwise the modem works great.

               Thanks Mike

---

### Post by pdc on 2010-05-30
not easily that I know of:

two options:

vodafone have a group called betavine that develop software: VMC vodafone mobile connect; they found ubuntu buggy last year, and provide only a debian build now .... I think ... but you can connect to any device with it .. it is not just for vodafone; you can send SMS with VMC ......

so VMC one dials in using it, rather than network manager

gammu: we sort of think SHOULD work, but doesn't seem to ..

eg 

[http://ubuntuforums.org/showthread.php?p=9382823](http://ubuntuforums.org/showthread.php?p=9382823)

an ongoing thread; alexfish may well pick this up and comment; he is very knowledgable on these things

if you do some investigating

---

### Post by mikecanada on 2010-05-30
Yeah I trying pot luck here,1 Phone Manager 2 Wammu 3 SIM- IM, think WAMMU needs GAMMU. Not sure when I used Ubuntu Software Center if it downloaded the GAMMU part so I will go back and try that angle.The provider is Telus.
                 Thanks I will keep it posted one way or the other.

---

### Post by pdc on 2010-05-30
post #4 alexfish makes reference to gammu/wammu

[http://ubuntuforums.org/showthread.php?t=1466490](http://ubuntuforums.org/showthread.php?t=1466490)

I downloaded it on an older ubuntu and it wouldn't run and I didn't spend the time to work at it

---

### Post by mikecanada on 2010-05-30
Okay I went back and downloaded the other part in case it was not included and no luck.O well just keep plugging away.... Thanks

---

### Post by pdc on 2010-05-30
not sure if you downloaded gammu or wammu;

wammu is the GUI:

[http://wammu.eu/](http://wammu.eu/)

on the above link, are screenshots of how to configure

this page lists supported devices

[http://wammu.eu/phones/sierra/](http://wammu.eu/phones/sierra/)

it is identifying which port your device on is the critical one

> dmesg } grep tty will list the ports: you may have to try ttyUSB0 and then ttyUSB1 etc .......

another programme I see is called wader; just discovered it;

it was developed from the VMC: and has ubuntu builds;

have a read at their website: 

it sounds interesting

---

