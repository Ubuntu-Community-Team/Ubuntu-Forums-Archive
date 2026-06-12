---
title: "Mobile broadband connects, but won't reconnect after dropped signal"
date: 2010-11-08
forum: Networking &amp; Wireless
---

### Post by ryukent on 2010-11-08
Just wondered if anyone else is experiencing this little niggle.

I'm running a ZTE MF112 HSUPA USB stick (3 broadband dongle) for wireless broadband using network-manager.

I can connect fine to mobile broadband, but every now and then, the signal drops and the connection is disconnected. When I try to reconnect it goes straight to network disconnected. It looks like it's not even trying to connect.

Then when I right click on network manager, disable mobile broadband, then enable it again, works fine..... until the next disconnect.

The point is, why do I have to keep disabling / enabling it? Pulling the dongle out works too. But there should be a workaround. Anyone have any ideas?

---

### Post by spiky001 on 2010-11-08
Mine dose the same I right click network manager disable mobile connection then renable it, then it connects

---

### Post by Chiapo on 2010-11-08
I first noticed this issue while using Fedora 13, then when I upgraded my Xubuntu system to Maverick, the same issue was present.
When the connection is dropped I would stop networking:
```
sudo stop network-manager
```
Unload my modem driver, which in my case is qcserial:
```
sudo modprobe -r qcserial
```
Then reload the modem driver:
```
sudo modprobe qcserial
```
Finally restart network-manager:
```
sudo start network-manager
```

Your modem driver will be different than mine, so you can either omit the unload/reload step, or find out which driver your device uses.

I had to create the /lib/firmware/gobi directory & copy the pertinent files from my WinXP installation, then had to make && make install the gobi_loader app to get my internal Qualcomm WWAN modem to function correctly in Fedora, much the same as I had to in *buntu.

I believe it is a kernel bug that drops the connection each time a signal change event occurs, but I can't be sure.

What I do know is that since I installed Fedora 14 LXDE, the 3g modem issue has ceased!
Fedora is known for being on the "bleeding edge" of GNU/Linux development, so your mileage may vary.

I would suggest using a newer kernel that the one shipped with *buntu 10.10.

Here is the kernel I'm currently using with Fedora 14 LXDE
```
2.6.35.6-45.fc14.i686
```

Possibly there's a similar version in the Ubuntu repos?

Good luck!

---

### Post by alexfish on 2010-11-08
> **ryukent said:**
> Just wondered if anyone else is experiencing this little niggle.

I'm running a ZTE MF112 HSUPA USB stick (3 broadband dongle) for wireless broadband using network-manager.

I can connect fine to mobile broadband, but every now and then, the signal drops and the connection is disconnected. When I try to reconnect it goes straight to network disconnected. It looks like it's not even trying to connect.

Then when I right click on network manager, disable mobile broadband, then enable it again, works fine..... until the next disconnect.

The point is, why do I have to keep disabling / enabling it? Pulling the dongle out works too. But there should be a workaround. Anyone have any ideas?

Hi

one possibility is the connection is timing out at the server end

monitor the pppd connection in  log file viewer messages

next time the connection fails the pppd should terminate
if there is a dropped server connection / re time out then pppd will still be alive

Code:

[COLOR=Blue]sudo killall pppd[/COLOR]

or and

Code:

[COLOR=Blue]killall modem-manager[/COLOR]

monitor the situation , or ask 3 if there are any problems

if it is a device issue , and if ZTE device then entering AT commands may help
use a serial terminal

stay online:

AT+ZOPRT=5

or from the terminal

echo -e "[COLOR=Blue]AT+ZOPRT=5[/COLOR]\r" > /dev/tty[COLOR=Blue]XXX[/COLOR]

where [COLOR=Blue]XXX[/COLOR] = the connection port of the device

EG tty[COLOR=Blue]USB2[/COLOR]

you can monitor any response by opening up a terminal ( do this before sending the AT command)

Code:

cat /dev/tty[COLOR=Blue]XXX[/COLOR]

where the [COLOR=Blue]XXX[/COLOR] = the same port

Close the terminals before making the connection

---

