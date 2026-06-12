---
title: "Where is usb_modeswitch package?"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by asbesto on 2010-01-07
Hi,

I can't find usb_modeswitch package, that is required to use many USB Internet dongles like O2 Surfstick 2 or Qualcomm 3g HSDPA or iCON 210 or MYWAVE FW2012P. 

Does anyone know if this package was renamed to something else or included in other packages? This utility is from 2006, so I really don't know why I can't find in Ubuntu (as I find a lot of new and BETA releases of unstable software of any kind in 9.10 :( )

Obviously my Internet Key dongle doesn't work, it will open an USB disk instead.

---

### Post by alexfish on 2010-01-07
hi

look in Synaptic , Type in the search area "modeswitch" if not there

get updates then follow this link here  Re: how to usb-modeswitch  Read documentation and info at the links .. 

			 			[SIZE=2][Ubuntu 9.10 mobile broadband can't connect]("http://ubuntuforums.org/showthread.php?t=1331660") 			[/SIZE][SIZE=2]([IMG]http://ubuntuforums.org/images/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=1331660") [2]("http://ubuntuforums.org/showthread.php?t=1331660&page=2"))
[/SIZE]

[SIZE=2]worth reading 

[/SIZE][SIZE=2][COLOR=Navy]RE: Ubuntu Linux On The Move . Connecting Modems Worth a read 

[/COLOR][/SIZE]                            [SIZE=2][http://]("http://ubuntu/")[Linux On The Move]("http://ubuntuforums.org/showthread.php?p=8530340#post8530340")
[/SIZE]

---

### Post by asbesto on 2010-01-07
No usb-modeswitch can't be found into synaptic or apt-cache search.

I only found a "modem-modeswitch" on a udev extra utilities packages, but after installing it, I have no usb-modeswitch, nor modem-modeswitch. 

](*,)

I red the above thread you gave to me: it refer to usb-modemswitch, that I can't found anywhere.

Where is it? 

So, I installed it by hand, following THIS howto:

[http://http://cluster.physik.uni-freiburg.de/~kuhnen/surfstick2/index.html]("http://http://cluster.physik.uni-freiburg.de/~kuhnen/surfstick2/index.html")

and now I can switch my device. But hey, here comes another problem:

```

root@lem:~# modprobe usbserial vendor=0x1e0e product=0x9000
FATAL: Module usbserial not found.

root@lem:~# locate usbserial
/lib/modules/2.6.28-14-generic/kernel/drivers/usb/serial/usbserial.ko
/lib/modules/2.6.28-15-generic/kernel/drivers/usb/serial/usbserial.ko
/lib/modules/2.6.28-16-generic/kernel/drivers/usb/serial/usbserial.ko
/lib/modules/2.6.28-17-generic/kernel/drivers/usb/serial/usbserial.ko
root@lem:~# uname -a
Linux lem 2.6.29-1-netbook #0array1 SMP Mon Feb 23 15:02:03 MST 2009 i686 GNU/Linux
root@lem:~# 


```

I have no words for this. ](*,)

---

### Post by alexfish on 2010-01-07
> **asbesto said:**
> No usb-modeswitch can't be found into synaptic or apt-cache search.

I only found a "modem-modeswitch" on a udev extra utilities packages, but after installing it, I have no usb-modeswitch, nor modem-modeswitch. 

](*,)

I red the above thread you gave to me: it refer to usb-modemswitch, that I can't found anywhere.

Where is it? 
Really I don't know why all this problems in 9.10!

](*,)

hi

 this may help

[http://packages.ubuntu.com/karmic/usb-modeswitch](http://packages.ubuntu.com/karmic/usb-modeswitch)

if done from the site check depends list  with your system

or try this from the terminal 

code:

sudo apt-get update

sudo apt-get install usb-modeswitch

then

[SIZE=3][COLOR=Navy].........................................................................................
RE: USB-Modeswitch[/COLOR][/SIZE]


 



there is a file at this site called [COLOR=Navy]usb_modeswitch.conf[/COLOR]

site[COLOR=Navy] PLEASE READ ALL[/COLOR] +++++++++++++++++++

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

direct link to file

[http://www.draisberghof.de/usb_modes...odeswitch.conf]("http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.conf")


>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>

[SIZE=2][COLOR=Navy]HOW TO :ACTIVATE THE  USB-Modeswitch[/COLOR][/SIZE]

open up the the terminal type in 

[SIZE=2][COLOR=Navy]sudo gedit /etc/usb_modeswitch.conf[/COLOR][/SIZE]

 make a backup of old file /delete contents the file  

paste the contents of this updated  [COLOR=Navy]file, from the site[/COLOR] 

[http://www.draisberghof.de/usb_modes...odeswitch.conf]("http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.conf")

into the file that's open

"" please read notes in this file "" 

In order to activate:   remove the comment signs ( ; ) that matches your device ..

 

save the file and exit gedit



 To activate the usb mode switch open up the terminal Type or Copy this  Code

[COLOR=Black]sudo usb_modeswitch[/COLOR]

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>

you should now see the device from the output list

exit and reboot

---

### Post by alexfish on 2010-01-07
[LIST]
[*]NetworkManager/Hardware/3G
[/LIST]
  This page is part of the [3GNetworkingIntrepid]("https://wiki.ubuntu.com/3GNetworkingIntrepid") effort. 
**Contents** 
Contents

[LIST=1]
[*][Data Card Info]("https://wiki.ubuntu.com/NetworkManager/Hardware/3G#Data%20Card%20Info")
[LIST=1]
[*][How to obtain device details]("https://wiki.ubuntu.com/NetworkManager/Hardware/3G#How%20to%20obtain%20device%20details")
[*][Mobile Broadband cards]("https://wiki.ubuntu.com/NetworkManager/Hardware/3G#Mobile%20Broadband%20cards")
[*][Mobile Phones]("https://wiki.ubuntu.com/NetworkManager/Hardware/3G#Mobile%20Phones")
[*][Provider info]("https://wiki.ubuntu.com/NetworkManager/Hardware/3G#Provider%20info")
[/LIST]
[/LIST]

---

### Post by pdc on 2010-01-07
the home page for usb_modeswitch is here

[http://www.draisberghof.de/usb_modeswitch/#download](http://www.draisberghof.de/usb_modeswitch/#download)

found by typing "usb_modeswitch" into google

the latest version is 1.07 I believe;

and they have a debian package at the unstable sid repository all ready to go for ubuntu users

[http://packages.debian.org/search?keywords=usb-modeswitch](http://packages.debian.org/search?keywords=usb-modeswitch)

unstable means leading-edge I understand; (as opposed to steady as a rock of granite)

the advantage of this debian package is it auto-installs and configures I understand; it is at version 1.05 but I understand it auto-configures too

it may well need additional packages downloaded: gcc and others but the debian installer should manage those things

---

### Post by asbesto on 2010-01-08
I installed from sources; now my devices switch correctly but I can't find any usbserial module in my actual kernel:

```

root@lem:~# modprobe usbserial vendor=0x1e0e product=0x9000
FATAL: Module usbserial not found.

root@lem:~# locate usbserial
/lib/modules/2.6.28-14-generic/kernel/drivers/usb/serial/usbserial.ko
/lib/modules/2.6.28-15-generic/kernel/drivers/usb/serial/usbserial.ko
/lib/modules/2.6.28-16-generic/kernel/drivers/usb/serial/usbserial.ko
/lib/modules/2.6.28-17-generic/kernel/drivers/usb/serial/usbserial.ko
root@lem:~# uname -a
Linux lem 2.6.29-1-netbook #0array1 SMP Mon Feb 23 15:02:03 MST 2009 i686 GNU/Linux
root@lem:~#

```

](*,)

---

### Post by alexfish on 2010-01-08
hi

can you provide us with a few details IE:

 / if you have any details of your modem you are trying to connect please post : also usb device or serial : means of connection  ; wvdial ; gnomeppp dial ; network manager;

:::::

lets try and find the modem first ; 

:::::::

from the terminal

Code:

dmesg | grep -e "modem" -e "tty" 


separate terminal


tail -f /var/log/syslog


and post the results

thanks in advance

alexfish

---

### Post by asbesto on 2010-01-08
...any help? :(

---

### Post by pdc on 2010-01-08
I understood that alex asked you to give him the results of two terminal commands:

so:

plug your modem into your computer

Open a terminal

paste this command in

> dmesg | grep -e "modem" -e "tty" 

copy and paste the results back to the forum

open a separate terminal

paste this command in

> tail -f /var/log/syslog

copy and paste the results back to the forum

alex suggested it would help him if he could identify your modem

---

### Post by pdc on 2010-01-08
it would seem from the vendor ID product ID 

> 1e0e product=9000

that this is a 

> Qualcomm 3G HSDPA iCON 210 USB-Surfstick

one long posting last year described successful configuration

[http://ubuntuforums.org/showthread.php?t=1210259&page=3](http://ubuntuforums.org/showthread.php?t=1210259&page=3)

go to the final post #27 and a reference to this link (in German)

[http://wiki.ubuntuusers.de/Icon_210](http://wiki.ubuntuusers.de/Icon_210)

and 

hey presto!

here is the english translation

[http://translate.google.co.nz/translate?js=y&prev=_t&hl=en&ie=UTF-8&layout=1&eotf=1&u=http://wiki.ubuntuusers.de/Icon_210&sl=de&tl=en](http://translate.google.co.nz/translate?js=y&prev=_t&hl=en&ie=UTF-8&layout=1&eotf=1&u=http://wiki.ubuntuusers.de/Icon_210&sl=de&tl=en)

I must say I do not find the wiki easy but the poster says it worked for him;

and this post also describes success

[http://eeegadgets.blogspot.com/2009/04/howto-qualcomm-3g-icon-210-and-ubuntu.html](http://eeegadgets.blogspot.com/2009/04/howto-qualcomm-3g-icon-210-and-ubuntu.html)

---

