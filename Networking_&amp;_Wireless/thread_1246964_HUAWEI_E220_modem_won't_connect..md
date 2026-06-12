---
title: "HUAWEI E220 modem won't connect."
date: 2009-08-22
forum: Networking &amp; Wireless
---

### Post by kasperelkjaer on 2009-08-22
I realize that this issue has been discussed many times before, but my problem seems different from the threads I've read so far...

My problem is this:

I have an Aspire One 150 with Mint 7 (9.04) Gnome on it, and I have an Aspire 5100 with Kubuntu (9.04).
I borrowed some Telia 3G mobile broadband from a friend which comes with the Huawei E220 modem.
When I plugged it in my One, it worked like a charm. The guide popped up and I filled in the info. It connected perfect.
But my 5100 with Kubuntu will not do the same. It didn't run really well, because on an upgrade gone bad, so I decided to reinstall the system from cd. After doing so, the wonderful guide popped up again, and I could go online! Perfect...
So I updated everything and rebooted. And what happens?
It won't connect! No matter what I do, it won't connect...
I tried installing the gnome edition too, with the same result.
It worked fine the first time I started the system, but after updating, it stops working...
I even installed the 9.10 alpha version, but it doesn't work at all...
The sim card has no PIN code on it, so that's not the problem.
And now, magically, it doesn't work on the One either! For no reason at all... I didn't do anything that would **** it up.
It works fine in windows. So now it won't work on any of my linux systems. 
I want to try to run the guide again, but don't know how to start it. Maybe that will work...

Any other ideas?

---

### Post by RabbitWho on 2009-08-22
Having similar with E160. Like that it works fine on ubuntu but not kubuntu. (If one more person says "the only difference is how they look" i'll scream) 

I can't get kubuntu to acknowledge the dongel at all, let alone use it. 

I'm using 8.10 (I swapped from 9.4 because I heard it doesn't work in that) 

What are you supposed to click to get it to connect normally? In ubuntu and icebuntu there is just a little wireless symbol.. click.. bob's your uncle you're connected, it's even far better than the software 3g actually comes with for windows and mac (which took forever to instal, and in the case of the mac we had to get 3g to send us a special cd)

---

### Post by GeorgeVita on 2009-08-22
Hi **kasperelkjaer, RabbitWho**, welcome to this forum!

I would like to express a simple idea. I think you need to learn a 'terminal method' to connect and some additional 'terminal rescue' commands that will supply internet at any time. Then you could fix or update some packages without the need of a total installation.  Later you can test and use any simpler GUI.

I am using only 3G as my internet connection, new to Ubuntu/linux environment (1+ year) but I have learned at least 5 methods to connect.

You can start using wvdial (or pppconfig) where there are a lot of posts here in ubuntuforums. Ready to help if you would like to try.

Huawei **E220** and **wvdial** read [http://forum.huawei.com/jive4/thread.jspa?threadID=322982](http://forum.huawei.com/jive4/thread.jspa?threadID=322982)
also **Ji Ruo** wrote for **Kubuntu** and **wvdial**: [http://ubuntuforums.org/showthread.php?t=1223769](http://ubuntuforums.org/showthread.php?t=1223769)

> It worked fine the first time I started the system, but after updating, it stops working...
I even installed the 9.10 alpha version, but it doesn't work at all...
The possible answer is that a 'newer' version of the 'connection program' is buggy on kubuntu. For 9.10 as it is on development we can accept anything. We could also test and report bugs but this is more difficult.

> I want to try to run the guide again, but don't know how to start it. Maybe that will work... Right click network manager icon, mobile Broadband, Edit, click on any existing provider and delete it. Reboot without modem, wait, attach it and normally the wizard will start within 1 minute. If not started check port creation with **ls /dev/ttyU***

Regards,
George

---

### Post by RabbitWho on 2009-08-22
Hi GeorgeVita! Thanks for helping us

I tried all that already but fell at the first step because when I try to execute any command involving wvdial what I get is 

cannot open dev/modem no such file or directory

---

### Post by GeorgeVita on 2009-08-22
Hi **RabbitWho**, this is because your modem is not 'placed' in the default /dev/modem. Most times system creates a directory 'place' like /dev/ttyUSB0 (huawei modems). The difficult part with 9.04 is that wvdial is not installed, so you have to use pppconfig (I find it more difficult).

If you already have wvdial installed and your modem has the serial connectivity you can just 'set' the configuration file (/etc/wvdial.conf). 

First you must check that system created the ports, so **boot without modem**, **wait** for the system to load, **attach modem**, **wait** 15 seconds, open a **terminal** window: ```
ls /dev/ttyU*
```

Then you must provide a proper configuration file. Use a text editor and create **/etc/wvdial.conf** with the contents below: ```
[Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Username = user
Password = pass
Phone = *99#
Stupid Mode =1
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 = AT+CGDCONT=1,"IP","internet"
```

You must **check APN** (Init3) and possibly user and password (most times work all).
Post country, provider name, type of connection to search (or check defaults from network manager).

To **connect**:```
sudo wvdial
```
**Disconnect** by pressing **CTRL-C** at the same terminal window you made the connection.

Regards,
George

---

### Post by RabbitWho on 2009-08-22
> **GeorgeVita said:**
> 
First you must check that system created the ports, so boot without modem, wait for the system to load, attach modem, wait 15 seconds, open a terminal window: ```
ls /dev/ttyU*
```

I did this like you said but I got the same sort of message after typing in that command, no such file or directory 

:(

What could I be doing wrong?

I have 8.10 so it should have wvdial on it already.. but when this didn't work first I tried to download and install it, could I have damaged it then?

---

### Post by GeorgeVita on 2009-08-22
All above should work directly for E220.

With E160, I am sure that works with 9.04 so you must check:

**Reboot without modem, wait for system to fully load, attach it,** wait 15 seconds and then: ```
lsusb
``` ```
dmesg | tail -n 15
```
**EDIT next post** with the output (if new one).
G

---

### Post by RabbitWho on 2009-08-22
Here we go: 

lsusb
Bus 008 Device 004: ID 0781:5151 SanDisk Corp. Cruzer Micro 256/512MB Flash Drive
Bus 008 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem/ E270 HSDPA/HSUPA Modem
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0c45:63ee Microdia
Bus 004 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
penguin@penguincounter:~$ dmesg | tail -n 15
[  385.810984] usb-storage: waiting for device to settle before scanning
[  390.808285] usb-storage: device scan complete
[  390.808838] scsi 12:0:0:0: Direct-Access     SanDisk  Cruzer Micro     8.01 PQ: 0 ANSI: 0 CCS
[  390.824062] sd 12:0:0:0: [sdd] 7862911 512-byte hardware sectors (4026 MB)
[  390.835075] sd 12:0:0:0: [sdd] Write Protect is off
[  390.835087] sd 12:0:0:0: [sdd] Mode Sense: 45 00 00 08
[  390.835092] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[  390.836580] sd 12:0:0:0: [sdd] 7862911 512-byte hardware sectors (4026 MB)
[  390.844775] sd 12:0:0:0: [sdd] Write Protect is off
[  390.844786] sd 12:0:0:0: [sdd] Mode Sense: 45 00 00 08
[  390.844791] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[  390.848506]  sdd: sdd1
[  390.850292] sd 12:0:0:0: [sdd] Attached SCSI removable disk
[  390.851728] sd 12:0:0:0: Attached scsi generic sg5 type 0
[  407.242945] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!


While i'm waiting for your next reply i'm going to try the earlier steps again, just in case i did make some simple mistake.

Edit: some different responses this time, I'm sorry I'm so hopeless at this. 

penguin@penguincounter:~$ ls /dev/ttyU*
/dev/ttyUSB0  /dev/ttyUSB1             
penguin@penguincounter:~$ sudo gedit /etc/wvdial.conf
[sudo] password for penguin:                         
                
penguin@penguincounter:~$ sudo gedit /etc/wvdial.conf
[sudo] password for penguin:                         
sudo: gedit: command not found                       
penguin@penguincounter:~$ sudo gedit /etc/wvdial.conf
sudo: gedit: command not found                       
penguin@penguincounter:~$ sudo gedit /etc/wvdial.conf
sudo: gedit: command not found                         
 penguin@penguincounter:~$ /etc/wvdial.conf
bash: /etc/wvdial.conf: Permission denied

---

### Post by GeorgeVita on 2009-08-22
Sorry I do not have kubuntu!

**gedit** is  the text editor for gnome and **sudo gedit** runs it as 'root user'

You must get '**root privileges**' and run any **text editor**
copy/paste contents of above **post#5** to /etc/wvdial.conf file!

If kubuntu text editor is geany (**example only**), run from terminal:
sudo **geany** /etc/wvdial.conf

Post here the actual command to be easier for **kasperelkjaer**

>>> I tried to dnld Kubuntu but it is a little bit BiiiG for my 3G modem!
>>> also the edit & re-edit 'messenger' is funny!

---

### Post by RabbitWho on 2009-08-22
Okay I'll give that a go now, thanks for bearing with me.

---

### Post by RabbitWho on 2009-08-22
Right, did that, this is what came up in Kate: 

[Dialer Defaults]
Phone = 
Username = 
Password = 
New PPPD = yes


And this (i don't think it's important but I don't know so up it goes anyway) is what came up in the terminal: 



penguin@penguincounter:~$ sudo kate /etc/wvdial.conf
[sudo] password for penguin:                        
Error: "/var/tmp/kdecache-penguin" is owned by uid 1000 instead of uid 0.
kate(7955): createDoc                                                    
kate(7955) KateSessionManager::KateSessionManager: LOCAL SESSION DIR:  "/home/penguin/.kde/share/apps/kate/sessions"                                            
kate(7955) KateApp::initKate: Setting KATE_PID: ' 7955 '                        
Error: "/tmp/kde-penguin" is owned by uid 1000 instead of uid 0.                
kate(7955) KateViewDocumentProxyModel::updateBackgrounds: false                 
kate(7955) KateMainWindow::KateMainWindow: **************************************************************************** 0xa0556e8                               
kate(7955) KateViewDocumentProxyModel::updateBackgrounds: false                 
kate(7955) KateViewDocumentProxyModel::updateBackgrounds: false                 
kate(7955) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "Untitled"                                                              
kate(7955) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"   
kate(7955) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "wvdial.conf"                                                           
kate(7955) KateViewDocumentProxyModel::updateBackgrounds: false                 
kate(7955) KateApp::startupKate: KateApplication::init finished successful      
Error: "/tmp/ksocket-penguin" is owned by uid 1000 instead of uid 0.            
kate(7955) KToolInvocation::klauncher: klauncher not running... launching kdeinit                                                                               
Error: "/tmp/kde-penguin" is owned by uid 1000 instead of uid 0.                
Error: "/tmp/ksocket-penguin" is owned by uid 1000 instead of uid 0.            
kdeinit4: Shutting down running client.                                         
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher                   
Error: "/tmp/ksocket-penguin" is owned by uid 1000 instead of uid 0.            
Error: "/tmp/kde-penguin" is owned by uid 1000 instead of uid 0.                
kdeinit4: preparing to launch /usr/bin/kded4                                    
Error: "/var/tmp/kdecache-penguin" is owned by uid 1000 instead of uid 0.       
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4                            
kbuildsycoca4 running...                                                        
Error: "/var/tmp/kdecache-penguin" is owned by uid 1000 instead of uid 0.       
Error: "/var/tmp/kdecache-penguin" is owned by uid 1000 instead of uid 0.       
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update                
kdeinit4: preparing to launch                                                   
kate(7955) KateViewDocumentProxyModel::updateBackgrounds: true                  
penguin@penguincounter:~$ sudo kate /etc/wvdial.conf                            
[sudo] password for penguin:                                                    
Error: "/var/tmp/kdecache-penguin" is owned by uid 1000 instead of uid 0.       
kate(7955): createDoc                                                           
kate(7955) KateSessionManager::KateSessionManager: LOCAL SESSION DIR:  "/home/penguin/.kde/share/apps/kate/sessions"
kate(7955) KateApp::initKate: Setting KATE_PID: ' 7955 '
Error: "/tmp/kde-penguin" is owned by uid 1000 instead of uid 0.
kate(7955) KateViewDocumentProxyModel::updateBackgrounds: false
kate(7955) KateMainWindow::KateMainWindow: **************************************************************************** 0xa0556e8
kate(7955) KateViewDocumentProxyModel::updateBackgrounds: false
kate(7955) KateViewDocumentProxyModel::updateBackgrounds: false
kate(7955) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "Untitled"
kate(7955) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
kate(7955) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "wvdial.conf"
kate(7955) KateViewDocumentProxyModel::updateBackgrounds: false
kate(7955) KateApp::startupKate: KateApplication::init finished successful
Error: "/tmp/ksocket-penguin" is owned by uid 1000 instead of uid 0.
kate(7955) KToolInvocation::klauncher: klauncher not running... launching kdeinit
Error: "/tmp/kde-penguin" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-penguin" is owned by uid 1000 instead of uid 0.
kdeinit4: Shutting down running client.
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher
Error: "/tmp/ksocket-penguin" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-penguin" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/bin/kded4
Error: "/var/tmp/kdecache-penguin" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-penguin" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-penguin" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update
kdeinit4: preparing to launch
kate(7955) KateViewDocumentProxyModel::updateBackgrounds: true




I was logged on as the root user alright if that's what '**root privileges**'

---

### Post by GeorgeVita on 2009-08-22
Post me also country, provider name and type of account (if more that one) to finalize /etc/wvdial.conf for you and attach it here or somewhere...

Below are the contents of /etc/wvdial.conf that may work with provider 3ie

```
[Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Username = user
Password = pass
Phone = *99#
Stupid Mode = Yes
Dial Attempts = 1

Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 = AT+CGDCONT=1,"IP","3ireland.ie"

```

---

### Post by GeorgeVita on 2009-08-22
also check from a terminal window:```
chat --help
```
```
pppd --help
```

---

### Post by RabbitWho on 2009-08-22
Ireland, 3g (sometimes just called 3, I don't know the difference but it's an international thing so you probably might) 

I'm sorry i don't know the type of account. What are the options? 
I think I have the phone number around here somewhere if you need that (a connection wizard on another system insisted on it), there's no username or password.

---

### Post by RabbitWho on 2009-08-22
> **GeorgeVita said:**
> also check from a terminal window:```
chat --help
``````
pppd --help
```


penguin@penguincounter:~$ chat --help
Usage: chat [-e] [-E] [-v] [-V] [-t timeout] [-r report-file]
     [-T phone-number] [-U phone-number2] {-f chat-file | chat-script}
penguin@penguincounter:~$ chat --help
Usage: chat [-e] [-E] [-v] [-V] [-t timeout] [-r report-file]
     [-T phone-number] [-U phone-number2] {-f chat-file | chat-script}
penguin@penguincounter:~$ pppd --help                                 
bash: /usr/sbin/pppd: Permission denied
penguin@penguincounter:~$ pppd--help
bash: pppd--help: command not found
penguin@penguincounter:~$ pppd --help
bash: /usr/sbin/pppd: Permission denied

> 
[Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Username = user
Password = pass
Phone = *99#
Stupid Mode = Yes
Dial Attempts = 1

Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 = AT+CGDCONT=1,"IP","3ireland.ie" 

What do i do with this? Do I edit the Kate file I got earlier and put this in or...?

---

### Post by GeorgeVita on 2009-08-22
> What do i do with this? Do I edit the Kate file I got earlier and put this in or...? 

Yes!

Using any existing text editor you must create the file /etc/wvdial.conf (or any abcd.txt file and save it to Desktop) and then from terminal you can 'sudo copy it' with:```
sudo cp Desktop/abcd.txt /etc/wvdial.conf
```

Finally you can check by listing the 'wanted' file: ```
sudo cat /etc/wvdial.conf
```

>>> EDIT: or get it from: [http://acomelectronics.com/GeorgeVita/various/wvdial.conf](http://acomelectronics.com/GeorgeVita/various/wvdial.conf)
>>> if sttored to Desktop, copy it with: sudo cp Desktop/wvdial.conf /etc/wvdial.conf
>>> but in case of extra 'trimming' you need the editor

P.S. possible alternative editors: nano, kate, kedit, kwrite

---

### Post by RabbitWho on 2009-08-22
Right so I think that went according to plan. But I've no understanding of what the plan was! 

penguin@penguincounter:~$ sudo cp Desktop/abcd.txt /etc/wvdial.conf
[sudo] password for penguin:                                       
penguin@penguincounter:~$ sudo cp Desktop/abcd.txt /etc/wvdial.conf
penguin@penguincounter:~$ 
penguin@penguincounter:~$ sudo cat /etc/wvdial.conf
[Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Username = user
Password = pass
Phone = *99#
Stupid Mode = Yes
Dial Attempts = 1

Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 = AT+CGDCONT=1,"IP","3ireland.ie" 
[B]
then, just for fun i typed[/B]

penguin@penguincounter:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F E1 V1 X1 &D2 &C1 S0=0
AT&F E1 V1 X1 &D2 &C1 S0=0
OK
--> Sending: AT+CGDCONT=1,"IP","3ireland.ie"
AT+CGDCONT=1,"IP","3ireland.ie"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT 3600000
--> Carrier detected.  Starting PPP immediately.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.


-------------------------------



So is this what I'm doing next:

> 
sudo wvdial hspa

(also give your password if asking for it)

After some messages including "CONNECT 7200000" comes the final "--> secondary DNS address ..."
and you are connected. Minimize the terminal window and click on the Firefox shortcut, unselect the "work off line" option from "file" menu (if selected) and Browse!

Please note that while we do not have a "real software driver" we cannot see traffic, type of connection or other parameters.

To disconnect, press CTRL-C at the terminal window which you made the connection.

As references you can read the data given via the "man wvdial" and "man wvdial.conf" commands (from a terminal window). Also take a look to that Init String that uses the E170 (or possibly E169 or E220) at the windows connection (at the log file of the modem).


Or is there something else?

---

### Post by GeorgeVita on 2009-08-22
just: **sudo wvdial**

After successful connection (you will see IP and DNS numbers) you minimize this terminal window and leave it there. Open Firefox.
**EDIT:** Firefox (before 3.5) starts offline, press **ALT-F W** to remove offline mode. When you want to disconnect, click on the terminal window you connected and press CTRL-C

> Right so I think that went according to plan. But I've no understanding of what the plan was! The problem was the differences between KDE and gnome and the 'newbity' we both have! We tried and you managed to create the configuration file for the wvdial program.

---

### Post by RabbitWho on 2009-08-22
> **GeorgeVita said:**
> just: **sudo wvdial**

After successful connection (you will see IP and DNS numbers) you minimize this terminal window and leave it there. Open Firefox.
**EDIT:** Firefox (before 3.5) starts offline, press **ALT-F W** to remove offline mode. When you want to disconnect, click on the terminal window you connected and press CTRL-C

The problem was the differences between KDE and gnome and the 'newbity' we both have! We tried and you managed to create the configuration file for the wvdial program.


Wey hey! It worked! Here I am on the Internet on kubuntu! When I woke up this morning the computer wasn't even working and now after just 12 hours I'm connected to the Internet! 

Thank you so much! If there's anything I can ever do to help you just send me a message. 

I don't think you have much newbity btw! i'm pretty flabergahsted by what we just managed. It really seemed impossible to me.

---

### Post by GeorgeVita on 2009-08-22
Fine, both tired but ... the connection done!
> **RabbitWho said:**
> ...
Thank you so much! If there's anything I can ever do to help you just send me a message.YES!
Try the following: Disconnect with CTRL-C at the terminal window and then copy paste the following commaaaaaaaaand to try connection with ONE 'hard core' instruction. (If not connected, press CTRL-C and retry).
```
sudo pppd ttyUSB0 460800 noauth nodetach defaultroute noipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','3ireland.ie'" OK "atdt*99#" CONNECT' user u password p

```Although terminal needs typing, it is a good tactic to have 'solid alternatives' when other methods are 'updating'. 

If you succeed you will have one new connection method per 6 hours (on kubuntu)!

Regards
George

---

### Post by RabbitWho on 2009-08-22
> **GeorgeVita said:**
> Fine, both tired but ... the connection done!
YES!
Try the following: Disconnect with CTRL-C at the terminal window and then copy paste the following commaaaaaaaaand to try connection with ONE 'hard core' instruction. (If not connected, press CTRL-C and retry).
```
sudo pppd ttyUSB0 460800 noauth nodetach defaultroute noipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','3ireland.ie'" OK "atdt*99#" CONNECT' user u password p

```Although terminal needs typing, it is a good tactic to have 'solid alternatives' when other methods are 'updating'. 

If you succeed you will have one new connection method per 6 hours (on kubuntu)!

Regards
George


Tried it, internet automatically disconnected and then wouldn't reconnect.. said the ty... whatever files were locked. I saved the messages to a text file before i restarted to get it working again but now I can't find that file.

edit, found some but not all of it:

> penguin@penguincounter:~$ sudo wvdial
[sudo] password for penguin:         
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: Device or resource busy
--> Cannot open /dev/ttyUSB0: Device or resource busy
--> Cannot open /dev/ttyUSB0: Device or resource busy
penguin@penguincounter:~$ sudo wvdial                
--> WvDial: Internet dialer version 1.60             
--> Cannot open /dev/ttyUSB0: Device or resource busy
--> Cannot open /dev/ttyUSB0: Device or resource busy
--> Cannot open /dev/ttyUSB0: Device or resource busy
penguin@penguincounter:~$ sudo wvdial                
--> WvDial: Internet dialer version 1.60             
--> Cannot open /dev/ttyUSB0: Device or resource busy
--> Cannot open /dev/ttyUSB0: Device or resource busy
--> Cannot open /dev/ttyUSB0: Device or resource busy
penguin@penguincounter:~$ sudo wvdial hspal
--> WvDial: Internet dialer version 1.60   
--> Warning: section [Dialer hspal] does not exist in wvdial.conf.
--> Cannot open /dev/ttyUSB0: Device or resource busy             
--> Cannot open /dev/ttyUSB0: Device or resource busy             
--> Cannot open /dev/ttyUSB0: Device or resource busy             
penguin@penguincounter:~$ sudo wvdial                             
--> WvDial: Internet dialer version 1.60                          
--> Cannot get information for serial port.                       
--> Initializing modem.                                           
--> Sending: ATZ                                                  
ATZ                                                               
OK                                                                
--> Sending: AT&F E1 V1 X1 &D2 &C1 S0=0                           
AT&F E1 V1 X1 &D2 &C1 S0=0                                        
OK                                                                
--> Sending: AT+CGDCONT=1,"IP","3ireland.ie"                      
AT+CGDCONT=1,"IP","3ireland.ie"                                   
OK                                                                
--> Modem initialized.                                            
--> Sending: ATDT*99#                                             
--> Waiting for carrier.                                          
ATDT*99#                                                          
CONNECT 3600000                                                   
--> Carrier detected.  Starting PPP immediately.                  
--> Starting pppd at Sun Aug 23 03:25:33 2009                     
--> Pid of pppd: 16767                                            
--> Using interface ppp0                                          
--> pppd: &#65533;[11]&#65533; &#65533;[07]&#65533;                                           
--> pppd: &#65533;[11]&#65533; &#65533;[07]&#65533;                                           
--> pppd: &#65533;[11]&#65533; &#65533;[07]&#65533;                                           
--> pppd: &#65533;[11]&#65533; &#65533;[07]&#65533;                                           
--> pppd: &#65533;[11]&#65533; &#65533;[07]&#65533;                                           
--> pppd: &#65533;[11]&#65533; &#65533;[07]&#65533;                                           
--> local  IP address 10.206.142.179                              
--> pppd: &#65533;[11]&#65533; &#65533;[07]&#65533;                                           
--> remote IP address 10.64.64.64                                 
--> pppd: &#65533;[11]&#65533; &#65533;[07]&#65533;                                           
--> primary   DNS address 172.31.140.69
--> pppd: &#65533;[11]&#65533; &#65533;[07]&#65533;
--> secondary DNS address 172.30.140.69
--> pppd: &#65533;[11]&#65533; &#65533;[07]&#65533;
^CCaught signal 2:  Attempting to exit gracefully...
--> Terminating on signal 15
--> pppd: &#65533;[11]&#65533; &#65533;[07]&#65533;
--> Connect time 3.9 minutes.
--> pppd: &#65533;[11]&#65533; &#65533;[07]&#65533;
--> pppd: &#65533;[11]&#65533; &#65533;[07]&#65533;
--> pppd: &#65533;[11]&#65533; &#65533;[07]&#65533;
--> Disconnecting at Sun Aug 23 03:29:26 2009
penguin@penguincounter:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: Device or resource busy
--> Cannot open /dev/ttyUSB0: Device or resource busy
--> Cannot open /dev/ttyUSB0: Device or resource busy
penguin@penguincounter:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: Device or resource busy
--> Cannot open /dev/ttyUSB0: Device or resource busy
--> Cannot open /dev/ttyUSB0: Device or resource busy
penguin@penguincounter:~$ sudo pppd ttyUSB0 460800 noauth nodetach defaultroutenoipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','3ireland.ie'" OK "atdt*99#" CONNECT' user u password p
Device ttyUSB0 is locked by pid 17249
penguin@penguincounter:~$ sudo pppd ttyUSB0 460800 noauth nodetach defaultroutenoipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','3ireland.ie'" OK "atdt*99#" CONNECT' user u password p
Device ttyUSB0 is locked by pid 17249
penguin@penguincounter:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: Device or resource busy
--> Cannot open /dev/ttyUSB0: Device or resource busy
--> Cannot open /dev/ttyUSB0: Device or resource busy
penguin@penguincounter:~$
question! at the moment I can only log on as administrator because the wvdial thing needs sudo, is there a way i can get in from the other desktops? I don't want to mess around too much on this one understandably.

---

### Post by GeorgeVita on 2009-08-23
Hi **RabbitWho**, ... let's leave 2nd try.

About wvdial: Only one program can run any time to connect (or try to connect) via /dev/ttyUSB0 port. Be sure you close (CTRL-C) the connection before trying to reconnect. In case of 'trouble' after disconnection remove ,**wait** 10 seconds, plug again your modem and retry. Reboot is the last idea.

Sharing connection is another thing. The main rule needed from wvdial (and other terminal methods) is that the user must be into 'dip' and 'dialout' groups. ```
sudo adduser USERNAME dip
``` ```
sudo adduser USERNAME dialout
``` (replace USERNAME with your 'PC username' not the provider's username).

Now you must move step by step, understanding thee progress. Possibly open a new thread regarding the 'internet sharing'.

Regards,
George

---

### Post by RabbitWho on 2009-08-23
> **GeorgeVita said:**
> Hi **RabbitWho**, ... let's leave 2nd try.

About wvdial: Only one program can run any time to connect (or try to connect) via /dev/ttyUSB0 port. Be sure you close (CTRL-C) the connection before trying to reconnect. In case of 'trouble' after disconnection remove ,**wait** 10 seconds, plug again your modem and retry. Reboot is the last idea.

Sharing connection is another thing. The main rule needed from wvdial (and other terminal methods) is that the user must be into 'dip' and 'dialout' groups. ```
sudo adduser USERNAME dip
``` ```
sudo adduser USERNAME dialout
``` (replace USERNAME with your 'PC username' not the provider's username).

Now you must move step by step, understanding thee progress. Possibly open a new thread regarding the 'internet sharing'.

Regards,
George

Cool, tell me if you figure something out and you want me to try again. I will look up "internet sharing" threads and see if there's some advice. 

Thank for all your help! 

Sorry to the person that started the thread, i know i hijacked it, but I hope something we've done here can help you!

---

