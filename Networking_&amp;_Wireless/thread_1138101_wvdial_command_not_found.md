---
title: "wvdial: command not found"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by HarryBhat on 2009-04-26
I use a BSNL EVDO wireless data card and have been using the 'wvdial' command in Intrepid Ibex all this while. But recently I installed Jaunty Jackalope in one of my friend's comp and when I try the command 'sudo wvdial' to connect to internet, it says 
'wvdial: command not found' (or something like that).

Could someone tell me what the new command for Jaunty to connect to internet is?

P.S.: I have added the same lines in wvdial.conf as in Intrepid. But it works perfectly OK in Intrepid.

---

### Post by GeorgeVita on 2009-04-26
Hi **HarryBhat**,

at 9.04 the wvdial program is not including as standard!

So if you have a modem (especially EVDO cards or other 3G modems) not supported by the Network Manager you must first download wvdial from the repository using Synaptic Package Manager.

Regards,
George

---

### Post by HarryBhat on 2009-04-26
Thanks a lot for the reply buddy :)
But how do I download from repositories if my only means of connecting to internet is my 3G Wireless Card which fails to connect now? :(

---

### Post by GeorgeVita on 2009-04-27
> **HarryBhat said:**
> Thanks a lot for the reply buddy :)
[SIZE="3"]But how do I download from repositories if my only means of connecting to internet is my 3G Wireless Card which fails to connect now?[/SIZE] :(
[SIZE="5"]!!![/SIZE]
So we will try to find  a solution, I thing we have to use pppd or gnome ppp or anything else (I don't know).
Start searching, I am doing the same and good luck to both of us!

Regards,
George

**EDIT: try post#6 of [http://ubuntuforums.org/showthread.php?t=1108766](http://ubuntuforums.org/showthread.php?t=1108766)**

---

### Post by GeorgeVita on 2009-04-27
Another way:

Use Synaptic Package Manager (from an internet connected pc) to download the .deb package of wvdial if not already there. In my pc i found it at:

**/var/cache/apt/archives/wvdial_1.60.1+nmu2_i386.deb**

Copy above file to the **9.04** pc (I don't know if it must be in the same directory).

Find this file (Places, Computer, Filesystem, ...) and double click it.

The **Package Installer** will start and help you get back your TOOL!

Regards,
George

---

### Post by HarryBhat on 2009-04-27
@ above,
Thanks a lot dude. Will try ur second solution soon. But concerning the link in your first solution, I didnt get this-
"6.Became root and then connected using pon ZTE"

---

### Post by anaconda on 2009-04-29
> **GeorgeVita said:**
> Another way:

Use Synaptic Package Manager (from an internet connected pc) to download the .deb package of wvdial if not already there. In my pc i found it at:

**/var/cache/apt/archives/wvdial_1.60.1+nmu2_i386.deb**

Copy above file to the **9.04** pc (I don't know if it must be in the same directory).

Find this file (Places, Computer, Filesystem, ...) and double click it.

The **Package Installer** will start and help you get back your TOOL!

Regards,
George

I dont think that would work, because wvdial has some dependencies, and you would need also those debs. (If they aren't already installed)

EDIT:
and here are the dependencies that wvdial needs: ie. dependencies that aren't pre-installed after installing ubuntu from desktop CD. (copied them from the output of 
apt-get install wvdial from an internet connected machine.

Setting up libxplc0.3.13 (0.3.13-1build1) ...
Setting up libwvstreams4.4-base (4.4.1-0.2ubuntu2) ...
Setting up libwvstreams4.4-extras (4.4.1-0.2ubuntu2) ...
Setting up libuniconf4.4 (4.4.1-0.2ubuntu2) ...
Setting up wvdial (1.60.1+nmu2) ...

---

### Post by GeorgeVita on 2009-05-09
[size=3][B]This post helps you to install wvdial in "offline mode!"[/size]
(when you do not have an internet connection)[/B]
**Last update: 27-MAY-2011**

Program wvdial is one method to connect via DIAL UP modems and some rare 3G modems.

Consider to use a newer Ubuntu version.
Take a look at **[Ubuntu Official Documentation]("https://help.ubuntu.com/")**
Search for "dialup" to get info like: **[DialupModemHowto SetUpDialer]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer")** 

[SIZE="3"]_Ubuntu 9.04_[/SIZE]
It is not easy to find the appropriate old packages for an old NON LTS version of Ubuntu (as 9.04 Jaunty). If you have your Ubuntu PC connected to internet you can update your system and install wvdial using terminal commands:
```
sudo apt-get update && sudo apt-get dist-upgrade
```
```
sudo apt-get install wvdial
```

If you have NO INTERNET CONNECTION to your Ubuntu PC you have to install wvdial in "offline mode". You need some packages which are included in my .zip file and follow the following procedure (read some [historical info here]("http://acomelectronics.com/GeorgeVita/restore_wvdial.html")):

- use a "connected" PC to download my [wvdial_904_i386.zip]("http://acomelectronics.com/GeorgeVita/wvdial_904_i386.zip") (size=1.04MB, version=32bit/i386)

- create a folder to desktop of the Ubuntu PC (ex. wvdial_packages)

- copy .zip file into that directory, right click it and choose "extract here"

- double click on all 5 packages icons (**one each time**) to install them in order:
1. libxplc0.3.13
2. libwvstreams4.4-base
3. libwvstreams4.4-extras
4. libuniconf4.4
5. wvdial
Ignore messages suggesting to use 'typical way' as you have no connection.
Note that above are all for an 32bit "i386" pc.

Now you have installed wvdial program (and its dependencies).
To use wvdial you have to setup some parameters for your modem port and your internet account (phone to dial, username and password). Some times this is also a difficult procedure which you will find help from **[DialupModemHowto SetUpDialer]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer")** and **[www.ubuntuforums.org](www.ubuntuforums.org)**. Search for "wvdial dialup modem".

Briefly you need to run from terminal:
```
sudo wvdialconf
```
Edit your configuration file (/etc/wvdial.conf) with:
```
gksudo gedit /etc/wvdial.conf
```
and try to connect:
```
sudo wvdial
```


For [SIZE="3"]_Ubuntu **9.10**_[/SIZE] (**karmic** koala) 4 files needed:
1. [http://packages.ubuntu.com/karmic/i386/libwvstreams4.6-base/download](http://packages.ubuntu.com/karmic/i386/libwvstreams4.6-base/download)
2. [http://packages.ubuntu.com/karmic/i386/libwvstreams4.6-extras/download](http://packages.ubuntu.com/karmic/i386/libwvstreams4.6-extras/download)
3. [http://packages.ubuntu.com/karmic/i386/libuniconf4.6/download](http://packages.ubuntu.com/karmic/i386/libuniconf4.6/download)
4. [http://packages.ubuntu.com/karmic/i386/wvdial/download](http://packages.ubuntu.com/karmic/i386/wvdial/download)

which can be found (**i386**) into my [**wvdial910.zip**]("http://www.acomelectronics.com/GeorgeVita/wvdial910.zip")

_**Update for Ubuntu [size=3]10.04[/size]**_
Although **wvdial** and dependencies are included into CD of **10.04** are NOT installed by default! [Bug#400573]("https://bugs.launchpad.net/bugs/400573")
You do not need to download them, just use the .iso or LiveCD or LiveUSB following the procedure below:

1. right click ubuntu-10.04-desktop-i386.iso and '**open with archive mounter**'
(or mount LiveCD/LiveUSB)
2. right click on icon created (from 1) to '**browse folder**'
3. create a folder on Desktop (ex. named 'wvdial')
4. copy into that folder all 4 .deb files that exist into .iso/LiveCD/LiveUSB
... **/pool/main/w/wvdial**
and **/pool/main/w/wvstreams**
5. use **System > Administration > Synaptic Package Manager**
and then from menu **File > Add downloaded packages** > double click Desktop and then the folder you created at point #3, click **open**, follow instructions to install

(above procedure is fully tested, other ways may work also)


_**Update for Ubuntu [size=3]10.10[/size]**_
Although **wvdial** and dependencies are included into CD of **10.10** are NOT installed by default!
You can install it simply from terminal:
```
sudo apt-get install wvdial
```

Full example shown below:
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ wvdial
The program 'wvdial' is currently not installed.  You can install it by typing:
sudo apt-get install wvdial
ubuntu@ubuntu:~$ sudo apt-get install wvdial
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libuniconf4.6 libwvstreams4.6-base libwvstreams4.6-extras
The following NEW packages will be installed:
  libuniconf4.6 libwvstreams4.6-base libwvstreams4.6-extras wvdial
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1,093kB of archives.
After this operation, 2,839kB of additional disk space will be used.
Do you want to continue [Y/n]? y 
Preconfiguring packages ...
Selecting previously deselected package libwvstreams4.6-base.
(Reading database ... 124417 files and directories currently installed.)
Unpacking libwvstreams4.6-base (from .../libwvstreams4.6-base_4.6.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package libwvstreams4.6-extras.
Unpacking libwvstreams4.6-extras (from .../libwvstreams4.6-extras_4.6.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package libuniconf4.6.
Unpacking libuniconf4.6 (from .../libuniconf4.6_4.6.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package wvdial.
Unpacking wvdial (from .../wvdial/wvdial_1.60.4_i386.deb) ...
Processing triggers for man-db ...
Setting up libwvstreams4.6-base (4.6.1-1ubuntu1) ...
Setting up libwvstreams4.6-extras (4.6.1-1ubuntu1) ...
Setting up libuniconf4.6 (4.6.1-1ubuntu1) ...
Setting up wvdial (1.60.4) ...

Sorry.  You can retry the autodetection at any time by running "wvdialconf".
   (Or you can create /etc/wvdial.conf yourself.)
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
ubuntu@ubuntu:~$ 
```


_**Update for Ubuntu [size=3]11.04[/size]**_
The same as 10.10 included but not installed. Use:
```
sudo apt-get install wvdial
```


Genaral Notice: by default wvdial uses /dev/modem as the modem port
An error 'Cannot open /dev/modem: No such file or directory" means that you have not configured file wvdial.conf (read above).

Regards,
George

P.S. thanks to **anaconda** for the helpful note!

---

### Post by prasopsuk on 2009-05-21
hi GeorgeVita
 i follow your suggestion step by step on ubuntu 9.04, but i had unlucky.
wvdialconf can't detct my PCI fax modem on my PC.
 how to solve this problem?
 thank you.

---

### Post by GeorgeVita on 2009-05-22
> **prasopsuk said:**
> hi GeorgeVita
 i follow your suggestion step by step on ubuntu 9.04, but i had unlucky.
wvdialconf can't detct my PCI fax modem on my PC.
 how to solve this problem?
 thank you.

Hi **prasopsuk**, I am not sure I can help you with a **PCI modem** but it helps (for other readers also) if you give more info:

- Full data for your modem (manufacturer, model)
- The respond of the terminal command: **lspci**

Regards,
George

---

### Post by khurtsiya on 2009-06-26
Many thanks to **GeorgeVita**!

I had exactly the same problem on my Asus Eee PC 901.

---

### Post by himanee on 2009-10-02
hello,
i am a new member here and also not quite well known to ubuntu 9.04. i have successfully installed **[COLOR=#ff0000]wvdial[/COLOR]** on ubuntu 9.04 but it is still giving **[COLOR=#ff0000]problem[/COLOR]** to connect a netconnect modem. here are the errors occurring. can somebody please help me? i have changed **[COLOR=#ff0000]wvdial[/COLOR]**.conf and usbswitch.conf appropriately. also in lsusb it detects the device with correct vendor id and product id.

himanee@himanee-laptop:~$ wvdialconf /etc/wvdial.conf
Editing `/etc/wvdial.conf'.
Scanning your serial ports for a modem.
Modem Port Scan<*1>: S0 S1 S2 S3 
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: +GMI: HUAWEI TECHNOLOGIES CO., LTD
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Max speed is 9600; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB2<*1>: ATQ0 V1 E1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB2<*1>: Modem Identifier: ATI -- Manufacturer: +GMI: HUAWEI TECHNOLOGIES CO., LTD
ttyUSB2<*1>: Speed 9600: AT -- OK
ttyUSB2<*1>: Max speed is 9600; that should be safe.
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf.tmp6501': Permission denied
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf' ('/etc/wvdial.conf'): Bad file descriptor
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB2<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"



himanee@himanee-laptop:~$ sudo [B][COLOR=#ff0000]wvdial
[/COLOR][/B][sudo] password for himanee: 
--> **[COLOR=#ff0000]WvDial[/COLOR]**: Internet dialer version 1.60
--> Warning: inherited section [Modem0] does not exist in **[COLOR=#ff0000]wvdial[/COLOR]**.conf
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
himanee@himanee-laptop:~$ sudo **[COLOR=#ff0000]wvdial[/COLOR]** netconnect
--> **[COLOR=#ff0000]WvDial[/COLOR]**: Internet dialer version 1.60
--> Warning: inherited section [Modem0] does not exist in **[COLOR=#ff0000]wvdial[/COLOR]**.conf
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Fri Oct 2 16:09:16 2009
--> Pid of pppd: 6520
--> Using interface ppp0
--> pppd: ï¿½T][08]ï¿½R][08]
--> pppd: ï¿½T][08]ï¿½R][08]
--> pppd: ï¿½T][08]ï¿½R][08]
--> pppd: ï¿½T][08]ï¿½R][08]
--> Disconnecting at Fri Oct 2 16:09:24 2009
--> The PPP daemon has died: Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password? (exit code = 19)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 19)

---

### Post by GeorgeVita on 2009-10-02
Hi **himanee**, welcome to this forum!

Usually a Huawei modem can be used with network manager, so as you have the 'real modem mode' try: right click on network manager icon, edit connections, mobile broadband, add, select country/provider.

Alternative solution: **wvdial**
Auto configuration needs root user: **sudo wvdialconf**
but you don't need it now. Just edit your /etc/wvdial.conf file:
```
gksudo gedit /etc/wvdial.conf
```Copy the following data into gedit window: ```
[Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
Baud = 460800
ISDN = 0
Phone = "#777"
Init1 = ATZ
Init2 = AT&F E0 V1 X1 &D2 &C1 S0=0
; Init3 = AT+CGDCONT=1,"IP","internet"
Stupid Mode = Yes
Username = <YourNumber>
Password = <YourPassword>

```
Replace above your username and password (for your internet provider) and ask them if they need a specific APN (if so you must remove semicolon from Init3 line and replace the word internet with the suggested one).

Connect using **sudo wvdial** and remove 'offline mode' from firefox (ALT+F W).

Post any progress to follow up.

Regards,
George

---

### Post by SanoTwo on 2009-11-08
> **GeorgeVita said:**
> 

For Ubuntu **9.10** (**karmic** koala):
[size=0]1. [http://packages.ubuntu.com/karmic/i386/libxplc0.3.13/download](http://packages.ubuntu.com/karmic/i386/libxplc0.3.13/download)
2. [http://packages.ubuntu.com/karmic/i386/libwvstreams4.4-base/download](http://packages.ubuntu.com/karmic/i386/libwvstreams4.4-base/download)
3. [http://packages.ubuntu.com/karmic/i386/libwvstreams4.4-extras/download](http://packages.ubuntu.com/karmic/i386/libwvstreams4.4-extras/download)
4. [http://packages.ubuntu.com/karmic/i386/libuniconf4.4/download](http://packages.ubuntu.com/karmic/i386/libuniconf4.4/download)
5. [http://packages.ubuntu.com/karmic/i386/wvdial/download](http://packages.ubuntu.com/karmic/i386/wvdial/download)[/size]

Regards,
George
George, link #1 and #5 are good. The others are dead.

I'm running 9.10 on a P4.

Thanks for your efforts. From another post I understand 9.04 still has wvdial in it. I'm going to downgrade I think.

---

### Post by GeorgeVita on 2009-11-08
Hi **SanoTwo**, thanks for your test & trigger on above post!

>>> to install 'offline' **wvdial** on **Ubuntu 9.10** 4 .deb packages needed:

1.  [libwvstreams4.6-base_4.6-2_i386.deb]("http://packages.ubuntu.com/karmic/i386/libwvstreams4.6-base/download")
2.  [libwvstreams4.6-extras_4.6-2_i386.deb]("http://packages.ubuntu.com/karmic/i386/libwvstreams4.6-extras/download")
3.  [libuniconf4.6_4.6-2_i386.deb]("http://packages.ubuntu.com/karmic/i386/libuniconf4.6/download")
4.  [wvdial_1.60.1+nmu2ubuntu1_i386.deb]("http://packages.ubuntu.com/karmic/i386/wvdial/download")

Which can be downloaded to desktop and double click **1st** to install. When finished continue with the 2nd, 3rd, 4th (in above series 1-2-3-4 one by one).

_Warning_: above links and my [**wvdial910.zip**]("http://www.acomelectronics.com/GeorgeVita/wvdial910.zip") file are for Ubuntu 9.10 running on **i386** architecture. For other you must find appropriate packages. 

_Note 1_: Above solution is for those that do not have other internet connection to the ubuntu PC (cannot use synaptic).

_Note 2_: although **pppd** and **pppconfig** are included into Ubuntu 9.10 release, wvdial method is more documented in a lot of Howtos.

_Note 3_: Above file links are valid as per 8-NOV-09

Regards,
George

---

### Post by SanoTwo on 2009-11-09
Thanks George. Actually I **am** running 9.04 but I have not had the time to solve the issue.

-for the thread- I was using this page, [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer) , and see that I also had a printing issue (w/ my XP machine for some reason).

Got it going now and turned on the Update Manager to make my installation "whole" I hope. 

Note: For some reason, 8.10 and 9.04 didn't like some of my hardware. Stuff that was available running the Live CD wasn't installed w/ either of the above distros on two separate machines. gparted is one that wasn't installed.  Otherwise, I'm posting now on 9.04 through a dialup ext. modem that wasn't installed when I originally loaded 9.04. Maybe that's the reason Network Manager wasn't available for me to use.

---

### Post by penguinv on 2010-01-20
Still failing after all these years?

Who is this system for?

Mark S. This is absurd. 

There must be a simpler way, or I'd be glad to use an older version of Ubuntu or figure out some other distribution in order to have working dialup.

Don't discount the lowballers, je vous en prie!

---

### Post by sillikat on 2010-02-22
[LEFT][FONT=Comic Sans MS][SIZE=4][COLOR=indigo]Many Thanks to GeorgeVita for the wvdial info to get Ubuntu 9.10 connected to the Internet.[/COLOR][/SIZE][/FONT]
[FONT=Comic Sans MS][SIZE=4][COLOR=#4b0082]Tom, USA [/COLOR][/SIZE][/FONT][/LEFT]

---

### Post by ntu on 2010-05-15
> **GeorgeVita said:**
> 
_**Update for Ubuntu [size=3]10.04[/size]**_
Although **wvdial** and dependencies are included into CD of **10.04** are NOT installed by default! [Bug#400573]("https://bugs.launchpad.net/bugs/400573")
You do not need to download them, just use the .iso or LiveCD or LiveUSB following the procedure below:

1. right click ubuntu-10.04-desktop-i386.iso and '**open with archive mounter**'
(or mount LiveCD/LiveUSB)
2. right click on icon created (from 1) to '**browse folder**'
3. create a folder on Desktop (ex. named 'wvdial')
4. copy into that folder all 4 .deb files that exist into .iso/LiveCD/LiveUSB
... **/pool/main/w/wvdial**
and **/pool/main/w/wvstreams**
5. use **System > Administration > Synaptic Package Manager**
and then from menu **File > Add downloaded packages** > double click Desktop and then the folder you created at point #3, click **open**, follow instructions to install

(above procedure is fully tested, other ways may work also)

Regards,
George

I am stuck on step 5 here. I double click on **Desktop** and the folder **Wvdial** appears that I made. I double click on this and the 4 .deb files are all shaded out or faint. Wondering what I am doing wrong here?

---

### Post by GeorgeVita on 2010-05-16
> **ntu said:**
> I am stuck on step 5 here. I double click on **Desktop** and the folder **Wvdial** appears that I made. I double click on this and the 4 .deb files are all shaded out or faint. Wondering what I am doing wrong here?

Hi **ntu**,
these files are 'shaded' but you can click on '**Open**' to continue and finally '**Apply**' to finish installation:

[IMG]http://acomelectronics.com/GeorgeVita/various/oflinewv1.jpg[/IMG]

[IMG]http://acomelectronics.com/GeorgeVita/various/offlinewv2.jpg[/IMG]

Regards,
George

---

### Post by ntu on 2010-05-16
Thank you George. I will try that.

---

### Post by MacAmb on 2010-10-09
> **GeorgeVita said:**
> Hi **ntu**,
these files are 'shaded' but you can click on '**Open**' to continue and finally '**Apply**' to finish installation:

[IMG]http://acomelectronics.com/GeorgeVita/various/oflinewv1.jpg[/IMG]

[IMG]http://acomelectronics.com/GeorgeVita/various/offlinewv2.jpg[/IMG]

Regards,
George


George i have done everything till i got that screen but i dont get it  when i click on Open nothing happen mean i dont get the second screen .hope you can help on this thanks .

---

### Post by GeorgeVita on 2010-10-10
> **MacAmb said:**
> George i have done everything till i got that screen but i dont get it  when i click on Open nothing happen mean i dont get the second screen .hope you can help on this thanks .
Hi **MacAmb**,
just tested with another set of .deb packages and worked well on Ubuntu 10.04. My procedure:

1- System > Administration > Synaptic Package Manager
2- from menu File > Add downloaded packages
3- from window 'Select directory' click to show into appropriate directory
4- all .deb files shown are in gray color, click **Open** and wait
5- the '**summary**' window appears showing '0 bytes to download', click **Apply**
6- click **Close** after installation
7- close Synaptic Package Manager and test your program

If you have any problem describe your situation for me or any other reader to follow up.

Regards,
George

---

### Post by MacAmb on 2010-10-11
yeah got it works thanks dude the problem was my wvdial.deb got corrupted  .so i got another one so it works .

---

### Post by prat22 on 2010-12-15
> **HarryBhat said:**
> I use a BSNL EVDO wireless data card and have been using the 'wvdial' command in Intrepid Ibex all this while. But recently I installed Jaunty Jackalope in one of my friend's comp and when I try the command 'sudo wvdial' to connect to internet, it says 
'wvdial: command not found' (or something like that).

Could someone tell me what the new command for Jaunty to connect to internet is?

P.S.: I have added the same lines in wvdial.conf as in Intrepid. But it works perfectly OK in Intrepid.
[B]You have to install the wvdial package.

sudo apt-get install wvdial


if you dont have internet connection available on that comp, try using Keryx.
It is a portable software that allows you to update your offline pc once you download packages connecting it to other online pc.
[/B]

---

