---
title: "New program for tethering(use as a modem) a Blackberry on Linux"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by tcolar on 2009-03-12
I've written a new python program (no need to compile stuff manually) whose only goal is to tether a Blackberry (Linux, FreeBSD, OSX).
It's called BBTether [http://wiki.colar.net/bbtether](http://wiki.colar.net/bbtether)

It's been tested under Linux and OSX so far.
Tested devices so far are: 8100,8120,8130,8830

If you try another device, let me know how it goes, and in case it fails please send a log file (-v option) so i can fix it !

Thanks.

---

### Post by chalewa on 2009-03-24
i am going to install this when I get home. 

There is a Win version of this same thing that just came out a few weeks ago, Tetherberry, that's $40. I was gonna buy it, but now I will just use this. 

Thanks

---

### Post by tcolar on 2009-03-25
Actually bbtether could run on windows too, i juts didn't see the point though.

On windows you can just use the standard RIM DesktopManager to do tethering, so what does that tetherberry do that is worth 40$ ?

---

### Post by steveneddy on 2009-04-11
After fighting with the not very well supported Barry - I found this little application and I can say that it works well enough that I don't think I will purchase a USB modem from my cell provider and pay extra fees just for an internet connection.

I am very mobile and this just rocks on my 8330 Curve.

I will try to post back later with updates on various states and areas of coverage.

I should see most of the lower 48 in the next six weeks.

Thank you for this app.

---

### Post by tcolar on 2009-04-12
Cool, glad it works for you.
Keep me updated on how it works when roaming around !

---

### Post by steveneddy on 2009-04-12
I like the fact that there was no set up required at all. I installed it in my /home folder, navigated to the folder and ran the app.

It connected the first time and gave no problems or issues. I used it for at least two hours.

Very impressed. How many people use this I wonder.

This is a lot easier than Barry, I can tell you that.

---

### Post by steveneddy on 2009-04-14
One problem I've noticed so far is that the python script uses up tp 100% of the CPU time heating up the laptop to almost shutdown temps.

Intel Core 2 Duo
2 Gig RAM

I would like this little bug fixed so I can continue testing.

Other than that, it seems to work real well.

I just noticed that the python script takes about 8 minutes to stop using the CPU process time, at which time everything seems to go back to normal for the rest of the session.

I am tethered to a Blackberry 8830 on Sprint network.

---

### Post by steveneddy on 2009-04-26
The python run time issue seems to have resolved itself after one of the recent updates.

This is actually all that I can attribute it to as recently I have noticed that the CPU cycles going to 100% for 8-10 minutes at a time due to a running python script have stopped occurring.

So far I have used this application from Chicago, Nebraska (don't ask), Kansas, Denver, far, far South Texas, and South Carolina.

Works perfectly no matter where you are as long as your phone has a connection.

 Very nice.

Viva the Open Sourced Community. They keep me working and making money daily no matter where is the world I am.

---

### Post by dro0g on 2009-04-26
One other recommendation for tethering - I use Blueman with my Verizon Blackberry 8330 and it works awesome over bluetooth and integrates with NetworkManager.

I will try out your app for wired tethering, thanks!

---

### Post by platinumriver on 2009-05-10
Did not work for me :(

Looking for USB devices:
	Bus 004 Device 001: ID 1d6b:0001
	Bus 002 Device 001: ID 1d6b:0002
	Bus 008 Device 001: ID 1d6b:0001
	Bus 007 Device 009: ID 0fca:0006
	Bus 007 Device 001: ID 1d6b:0001
	Bus 006 Device 001: ID 1d6b:0001
	Bus 001 Device 002: ID 05ca:18a0
	Bus 001 Device 001: ID 1d6b:0002
	Bus 005 Device 001: ID 1d6b:0001
	Bus 003 Device 001: ID 1d6b:0001
USB Device lookup finished

Found RIM device (Storage Mode)
	Manufacturer:Research In Motion
	Product:RIM Mass Storage Device
	Device:009
	VendorId: 0fca
	ProductId: 0006
	Version:01.06
	Class:0 0
	Protocol:0
	Max packet size:64
	Self Powered:0
	Max Power:200

	*Interface:0
Failed to claim interface: could not claim interface 0: Device or resource busy
Must be in use.
Will try to release it.
Trying to detach interface driver
Detaching driver returned: None
Interface is now claimed !
		Interface class:8/6
		Interface protocol:80
		EndPoint Pair:0x86L/0x7L
	-> [0x0 0x0 0x10 0x0 0x1 0xff 0x0 0x0 0xa8 0x18 0xda 0x8d 0x6c 0x2 0x0 0x0 ] [............l...]
			Not Data Pair (Read failed)
Defaulted Modem endpoints: -0x1/-0x1
Will run bbtether with args: ['verizon', '-v']
Starting Modem thread
--------------------------------
BBTether 0.3f
Thibaut Colar - 2009
More infos: [http://wiki.colar.net/bbtether](http://wiki.colar.net/bbtether)
Use '-h' flag for more informations : 'python bbtether.py -h'.
--------------------------------

Looking for USB devices:
	Bus 004 Device 001: ID 1d6b:0001
	Bus 002 Device 001: ID 1d6b:0002
	Bus 008 Device 001: ID 1d6b:0001
	Bus 007 Device 009: ID 0fca:0006
	Bus 007 Device 001: ID 1d6b:0001
	Bus 006 Device 001: ID 1d6b:0001
	Bus 001 Device 002: ID 05ca:18a0
	Bus 001 Device 001: ID 1d6b:0002
	Bus 005 Device 001: ID 1d6b:0001
	Bus 003 Device 001: ID 1d6b:0001
USB Device lookup finished

Found RIM device (Storage Mode)
	Manufacturer:Research In Motion
	Product:RIM Mass Storage Device
	Device:009
	VendorId: 0fca
	ProductId: 0006
	Version:01.06
	Class:0 0
	Protocol:0
	Max packet size:64
	Self Powered:0
	Max Power:200

	*Interface:0
		Interface class:8/6
		Interface protocol:80
		EndPoint Pair:0x86L/0x7L
	-> [0x0 0x0 0x10 0x0 0x1 0xff 0x0 0x0 0xa8 0x18 0xda 0x8d 0x6c 0x2 0x0 0x0 ] [............l...]
error: could not claim interface 0: Device or resource busy
			Not Data Pair (Write failed)
Defaulted Modem endpoints: -0x1/-0x1
BBTether Thread completed.

---

### Post by zuchini on 2009-05-15
works with a storm on verizon service...

---

### Post by exutable on 2009-06-07
Yeah I'm getting a problem with a 8830 on sprint:

Reading prefs from /home/dshea/.bbtether.conf
Looking for USB devices:
	Bus 004 Device 002: ID 044e:3003
	Bus 004 Device 001: ID 1d6b:0001
	Bus 003 Device 002: ID 0fca:0006
	Bus 003 Device 001: ID 1d6b:0001
	Bus 002 Device 001: ID 1d6b:0001
	Bus 001 Device 001: ID 1d6b:0002
	Bus 001 Device 002: ID 054c:014d
USB Device lookup finished

Found RIM device (Storage Mode)
	Manufacturer:Research In Motion
	Product:RIM Mass Storage Device
	Device:002
	VendorId: 0fca
	ProductId: 0006
	Version:01.06
	Class:0 0
	Protocol:0
	Max packet size:64
	Self Powered:0
	Max Power:200

	*Interface:0
		Interface class:8/6
		Interface protocol:80
		EndPoint Pair:0x86L/0x7L
	-> [0x0 0x0 0x10 0x0 0x1 0xff 0x0 0x0 0xa8 0x18 0xda 0x8d 0x6c 0x2 0x0 0x0 ] [............l...]
/home/dshea/Apps/bbtether/bb_usb.py:289: DeprecationWarning: BaseException.message has been deprecated as of Python 2.6
  if error.message != "No error" and not (bb_osx.is_osx() and error.errno == None):
			Not Data Pair (Read failed)
Defaulted Modem endpoints: -0x1/-0x1
Will run bbtether with args: ['sprint', '-v']
Starting Modem thread
--------------------------------
BBTether 0.3f
Thibaut Colar - 2009
More infos: [http://wiki.colar.net/bbtether](http://wiki.colar.net/bbtether)
Use '-h' flag for more informations : 'python bbtether.py -h'.
--------------------------------

Looking for USB devices:
	Bus 004 Device 002: ID 044e:3003
	Bus 004 Device 001: ID 1d6b:0001
	Bus 003 Device 002: ID 0fca:0006
	Bus 003 Device 001: ID 1d6b:0001
	Bus 002 Device 001: ID 1d6b:0001
	Bus 001 Device 001: ID 1d6b:0002
	Bus 001 Device 002: ID 054c:014d
USB Device lookup finished

Found RIM device (Storage Mode)
	Manufacturer:Research In Motion
	Product:RIM Mass Storage Device
	Device:002
	VendorId: 0fca
	ProductId: 0006
	Version:01.06
	Class:0 0
	Protocol:0
	Max packet size:64
	Self Powered:0
	Max Power:200

	*Interface:0
		Interface class:8/6
		Interface protocol:80
		EndPoint Pair:0x86L/0x7L
	-> [0x0 0x0 0x10 0x0 0x1 0xff 0x0 0x0 0xa8 0x18 0xda 0x8d 0x6c 0x2 0x0 0x0 ] [............l...]
			Not Data Pair (Read failed)
Defaulted Modem endpoints: -0x1/-0x1

No good Data Endpoint pair, bailing out !
BBTether Thread completed.
Will run bbtether with args: ['sprint', '-v']
Starting Modem thread
--------------------------------
BBTether 0.3f
Thibaut Colar - 2009
More infos: [http://wiki.colar.net/bbtether](http://wiki.colar.net/bbtether)
Use '-h' flag for more informations : 'python bbtether.py -h'.
--------------------------------

Looking for USB devices:
	Bus 004 Device 002: ID 044e:3003
	Bus 004 Device 001: ID 1d6b:0001
	Bus 003 Device 002: ID 0fca:0006
	Bus 003 Device 001: ID 1d6b:0001
	Bus 002 Device 001: ID 1d6b:0001
	Bus 001 Device 001: ID 1d6b:0002
	Bus 001 Device 002: ID 054c:014d
USB Device lookup finished

Found RIM device (Storage Mode)
	Manufacturer:Research In Motion
	Product:RIM Mass Storage Device
	Device:002
	VendorId: 0fca
	ProductId: 0006
	Version:01.06
	Class:0 0
	Protocol:0
	Max packet size:64
	Self Powered:0
	Max Power:200

	*Interface:0
		Interface class:8/6
		Interface protocol:80
		EndPoint Pair:0x86L/0x7L
	-> [0x0 0x0 0x10 0x0 0x1 0xff 0x0 0x0 0xa8 0x18 0xda 0x8d 0x6c 0x2 0x0 0x0 ] [............l...]
			Not Data Pair (Read failed)
Defaulted Modem endpoints: -0x1/-0x1

No good Data Endpoint pair, bailing out !
BBTether Thread completed.

---

### Post by exutable on 2009-06-07
Updating the blackberry software fixes the last problem, just grab the updater through ie on blackberry.com/update

Now I'm getting this error though:


--------------------------------
BBTether 0.3f
Thibaut Colar - 2009
More infos: [http://wiki.colar.net/bbtether](http://wiki.colar.net/bbtether)
Use '-h' flag for more informations : 'python bbtether.py -h'.
--------------------------------

 * Module berry_charge is loaded, this might cause problems
	 -> Will try to unload it now
	 -> OK.

Looking for USB devices:
	Bus 004 Device 002: ID 044e:3003
	Bus 004 Device 001: ID 1d6b:0001
	Bus 003 Device 004: ID 0fca:0004
	Bus 003 Device 001: ID 1d6b:0001
	Bus 002 Device 001: ID 1d6b:0001
	Bus 001 Device 001: ID 1d6b:0002
	Bus 001 Device 002: ID 054c:014d
USB Device lookup finished
Reading prefs from /home/dshea/.bbtether.conf
Using saved EP data: 0, 131, 3, 132, 4
Switching Device to data only mode

Using Data Endpoint Pair:0x83/0x3
Using Modem pair: 0x84/0x4

Claiming interface 0
Pin: 0x32c930ed
Description: RIM 8800 Series Colour CDMA Handheld
System: Linux,2.6.28-11-generic,#42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009,i686

Modem pty: /dev/pts/1
Initializing Modem
/home/dshea/Apps/bbtether/bb_usb.py:303: DeprecationWarning: BaseException.message has been deprecated as of Python 2.6
  if error.message != "No error" and not (bb_osx.is_osx() and error.errno == None):
No password requested.
session pack sent
Starting Modem thread
Modem Started
Will try to start pppd now, (/usr/sbin/pppd) with config: sprint
********************************************
Modem Ready at /dev/pts/1
 Use ^C to terminate
********************************************
Starting GPRS connect script
PPP data: BBT_OS
Starting session
PPP data: AT&F

OK
PPP data: ATZ
Connect script failed
Failed finding end of line(timeout) for: 
Error: [Errno 11] Resource temporarily unavailable
******************************************************

Shutting down
Please WAIT for shutdown to complete (up to 30s)
Otherwise you might have to reboot your BB !
******************************************************
Waiting for PPPD shutdown to complete.
PPPD finished
Stopping modem thread
Modem thread Stopped
Disconnected
Modem Disconnected
It is now safe to shutdown.
Releasing interface
bbtether completed.

---

### Post by exutable on 2009-06-08
Ok, so I found what I think is the fix to this.  Make sure you disable networking completely and then run the route command to make sure nothing comes up, then proceed to tether(I used the GUI version), and you could be answering ubuntuforums posts like me :)


THANKS TCOLAR FOR WRITING THIS!

---

### Post by new_kid on 2009-06-15
Works great on an 8310 with AT&T! Thanks for the effort! BTW I "borrowed" the config files and, with one small edit (no ~p at the end), got it to connect via bluetooth as well. Nice to have two options!

---

### Post by S0VERE1GN on 2009-06-17
ok super noob here, whats the command i type into the terminal to extract this file and install it?

---

### Post by maue80 on 2009-06-25
> **exutable said:**
> Ok, so I found what I think is the fix to this.  Make sure you disable networking completely and then run the route command to make sure nothing comes up, then proceed to tether(I used the GUI version), and you could be answering ubuntuforums posts like me :)


THANKS TCOLAR FOR WRITING THIS!

with route I'm sure to disability any network, but i cant't connect to the net, i have error 11: failed end of line...
can you help me?

---

### Post by DElliottJr on 2009-06-26
wow! this is excellent! works with the BB Storm like the Boss!! thank you so much! it is hackers like this that are making the Web a better place everyday! again beaucoup kudos!

---

### Post by RustyWyatt on 2009-07-04
Howdy,

Well here is my problem which I have posted before and have not been able to solve...

I only have my Sprint Blackberry for my home and work phone as well as my only Internet access.

I can install Ubuntu 9.04 via a CD however, I have a problem with not being able to apt-get directly for this setup because I cannot get on-line.

I also have a laptop with Window$ and that is how I am accessing the Internet for this posting.

Does anyone know how to "apt-get" on a Window$ computer and transfer it to a Ubuntu computer (via cd or network)that is not connected to the Internet?

Unfortunately this has become a deal breaker for me as I cannot get 9.04 up and running on either PC...

All info GREATLY appreciated!

Tom

---

### Post by TpyKv on 2009-08-07
If anyone has any idea how to make this work on Orange UK,

[http://ubuntuforums.org/showthread.php?t=1219142](http://ubuntuforums.org/showthread.php?t=1219142)

Please let me know!

---

### Post by fezzik on 2009-08-26
Just so I get this straight.  This is a program that allows me to subscribe to Broadband connect with Verizon and use my Blackberry as a tether, or is this something that allows me to use my blackberry as a tether without having to subscribe and just use the data plan that comes with the blackberry?

---

### Post by dro0g on 2009-08-27
> **fezzik said:**
> Just so I get this straight.  This is a program that allows me to subscribe to Broadband connect with Verizon and use my Blackberry as a tether, or is this something that allows me to use my blackberry as a tether without having to subscribe and just use the data plan that comes with the blackberry?

With Verizon you need to pay $10/month to have tethering turned on. Once the feature is turned on, it doesn't matter if you tether via a cable, Bluetooth, etc.

---

### Post by steveneddy on 2009-08-30
As far as I know - you don't need a tethering plan with this software if you have internet capabilities on your Blackberry.

A tethering plan is ONLY for Windows. It is only written for Windows users so the company can charge you more money.

Just DL berry4all and run it to see if your phone connects.

I have Sprint Simply Everything plan WITHOUT tethering and it works like a charm.

I DO have unlimited internet on my plan, but do NOT pay extra for a tethering option.

This application only accesses the phone's modem for internet access.

Welcome to the world of Linux.

:)

---

### Post by steveneddy on 2009-08-30
OK - tcolar - I still have an issue.

Running Intrepid and when I use version 0.3f I still get a high CPU usage with python. (see screenshot)

Specifically when downloading.

python 2.5

It is becoming problematic for me.

I had this issue with Hardy but it went away after an update.

Any help useful.

---

### Post by steveneddy on 2009-08-30
Double post - due to berry4all crashing.

Very annoying.

---

### Post by Lager_Monster on 2009-11-05
I just got a BB8900 tethered to a laptop running Ubuntu 9.10 and [Berry4all]("http://www.berry4all.com/home").
Location: Switzerland
Carrier: Orange CH
Edit bbtether/conf/orange-chat file to look like this:
(or create a new file)
```
TIMEOUT 10
ABORT 'BUSY'
ABORT 'NO ANSWER'
ABORT 'ERROR'
SAY 'Starting GPRS connect script\n'

'' 'BBT_OS'
'' 'ATZ'
SAY 'Setting APN\n'
OK 'AT+CGDCONT=1,"IP","internet"'
ABORT 'NO CARRIER'
SAY 'Dialing...\n'
OK 'ATD*99***1#'
CONNECT
# Without ~p it does NOT continue passed Connect !!
~p
```

Cheers,
LargerMon

---

### Post by tcolar on 2009-11-05
Sorry I forgot to check this thread in a while.
If you still have high CPU use issues please send me a full log of berry4all (verbose on) of it running with high CPU use.

Thanks for the orange script, will add to berry4all next release.

---

### Post by iamgeniusrnti on 2009-12-11
OK guys,

I'm on Sprint.

It doesn't work... I don't know what else to say--It comes up and says NO CARRIER and then shuts down.  Can someone who knows berry4all please help?

genius@K-Netbook:~/Downloads/bbtether/bbtether$ sudo ./berry4all.sh 
[sudo] password for genius:                                         
Reading prefs from /home/genius/.bbtether.conf                      
Will run bbtether with args: ['sprint']                             
Starting Modem thread                                               
--------------------------------                                    
BBTether 0.3k                                                       
Thibaut Colar - 2009                                                
More infos: [http://wiki.colar.net/bbtether](http://wiki.colar.net/bbtether)                          
Use '-h' flag for more informations : 'python bbtether.py -h'.      
--------------------------------                                    

Looking for USB devices:
        Bus 005 Device 001: ID 1d6b:0001
        Bus 001 Device 015: ID 0fca:8004
        Bus 001 Device 002: ID 0c45:62c0
        Bus 001 Device 001: ID 1d6b:0002
        Bus 003 Device 001: ID 1d6b:0001
        Bus 004 Device 001: ID 1d6b:0001
        Bus 002 Device 001: ID 1d6b:0001
USB Device lookup finished              
Using saved EP data: 0, 130, 2, 131, 3  

Using Data Endpoint Pair:0x82/0x2
Using Modem pair: 0x83/0x3       

Claiming interface 0
Pin: 0x30e543ed     
Description: RIM BlackBerry Device
System: Linux,2.6.31-16-generic-pae,#52-Ubuntu SMP Thu Dec 3 23:18:13 UTC 2009,i686

Modem pty: /dev/pts/8
Initializing Modem   
No password requested.
session pack sent     
Starting Modem thread 
Modem Started         
Will try to start pppd now, (/usr/sbin/pppd) with config: sprint
********************************************                    
Modem Ready at /dev/pts/8                                       
 Use ^C to terminate                                            
********************************************                    
Starting GPRS connect script                                    
PPP data: BBT_OS                                                
Starting session                                                

OK
PPP data: AT&F
PPP data: ATZ 
AT&F          
OKDialing...  

ATZ
PPP data: ATI
OK           
PPP data: ATDT#777
ATI
Manufacturer: Research In Motion
Model: 9630
Revision: OS Ver: 4.1.0.40  [Jun 25 2009 00:18:07]
ESN: 0x80348161
+GCAP: +CIS707-A, CIS-856, +MS, +ES, +DS, +FCLASS, CIS-856-A

OK
ATDT#777
NO CARRIER
Connect script failed
Failed finding end of line(timeout) for:
Usually means no reply from the modem
Error: [Errno 11] Resource temporarily unavailable
******************************************************

Shutting down
Please WAIT for shutdown to complete (up to 30s)
Otherwise you might have to reboot your BB !
******************************************************
Waiting for PPPD shutdown to complete.
PPPD finished
Stopping modem thread
Modem thread Stopped
Disconnected
Modem Disconnected
It is now safe to shutdown.
Releasing interface
bbtether completed.
BBTether Thread completed.


[SIZE=6]**Here is what happens when I put it in data mode:**[/SIZE]


genius@K-Netbook:~/Downloads/bbtether/bbtether$ sudo ./berry4all.sh        
Reading prefs from /home/genius/.bbtether.conf                             
genius@K-Netbook:~/Downloads/bbtether/bbtether$ sudo ./berry4all.sh        
Reading prefs from /home/genius/.bbtether.conf                             
Will run bbtether with args: ['sprint', '-v', '-m']                        
Starting Modem thread                                                      
--------------------------------                                           
BBTether 0.3k                                                              
Thibaut Colar - 2009                                                       
More infos: [http://wiki.colar.net/bbtether](http://wiki.colar.net/bbtether)                                 
Use '-h' flag for more informations : 'python bbtether.py -h'.             
--------------------------------                                           

Looking for USB devices:
        Bus 005 Device 001: ID 1d6b:0001
        Bus 001 Device 015: ID 0fca:8004
        Bus 001 Device 002: ID 0c45:62c0
        Bus 001 Device 001: ID 1d6b:0002
        Bus 003 Device 001: ID 1d6b:0001
        Bus 004 Device 001: ID 1d6b:0001
        Bus 002 Device 001: ID 1d6b:0001
USB Device lookup finished              
Using saved EP data: 0, 130, 2, 131, 3  
Switching Device to data only mode      

Using Data Endpoint Pair:0x82/0x2
Using Modem pair: 0x83/0x3       

Claiming interface 0
        -> [0x0 0x0 0xc 0x0 0x5 0xff 0x0 0x0 0x0 0x0 0x4 0x0 ] [............]
        <- [0x0 0x0 0x14 0x0 0x6 0xff 0x0 0x0 0x8 0x0 0x4 0x0 0x4 0x0 0x0 0x0 ] [................]
        <- [0xed 0x43 0xe5 0x30 ] [.C.0]                                                          
        -> [0x0 0x0 0xc 0x0 0x5 0xff 0x0 0x0 0x0 0x0 0x2 0x0 ] [............]                     
        <- [0x0 0x0 0xd0 0x1 0x6 0xff 0x0 0x0 0xc4 0x1 0x2 0x0 0x9 0x0 0x6 0x0 ] [................]
        <- [0xc4 0x1 0x0 0x0 0x13 0x0 0x6 0x5 0x4 0xd 0x0 0xd 0x52 0x49 0x4d 0x20 ] [............RIM ]
        <- [0x42 0x6c 0x61 0x63 0x6b 0x42 0x65 0x72 0x72 0x79 0x20 0x44 0x65 0x76 0x69 0x63 ] [BlackBerry Devic]
        <- [0x65 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 ] [e...............]               
        <- [0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 ] [................]                
        <- [0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x61 0x62 0x73 0x61 ] [............absa]            
        <- [0x64 0x6d 0x69 0x6e 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x4d 0x61 0x79 0x20 ] [dmin........May ]        
        <- [0x31 0x32 0x20 0x32 0x30 0x30 0x39 0x0 0x0 0x0 0x0 0x0 0x31 0x35 0x3a 0x34 ] [12 2009.....15:4]     
        <- [0x39 0x3a 0x34 0x34 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x1 0xff 0xff ] [9:44............]          
        <- [0x1 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0xb0 0x0 0x0 0x0 0xa 0x0 0x0 0x0 ] [................]               
        <- [0xc4 0x0 0x0 0x0 0x40 0x0 0x0 0x0 0x4 0x0 0x0 0x0 0x18 0xa7 0x0 0xc ] [....@...........]            
        <- [0x0 0x0 0x2 0x0 0x0 0x0 0x0 0x0 0x8 0x0 0x0 0x0 0x1 0x8 0x2 0x8d ] [................]               
        <- [0x3 0x1 0x4 0xf 0x7 0x30 0xb 0x1 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff ] [.....0..........]       
        <- [0x4a 0x56 0xbe 0x92 0x10 0x0 0x1 0x0 0x1d 0xc 0x0 0x0 0x0 0x0 0x0 0x0 ] [JV..............]          
        <- [0xd0 0x7 0x0 0x0 0x18 0xc 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 ] [................]              
        <- [0x19 0x8 0x0 0x0 0x2 0x0 0x0 0x0 0x1a 0x8 0x0 0x0 0xd 0x7 0x0 0x0 ] [................]              
        <- [0x21 0xc 0x0 0x0 0xe 0x7 0x0 0x0 0x85 0x7 0x0 0x0 0x20 0xc 0x0 0x0 ] [!........... ...]             
        <- [0x86 0x7 0x0 0x0 0xc5 0x7 0x0 0x0 0x1e 0xc 0x0 0x0 0xc6 0x7 0x0 0x0 ] [................]            
        <- [0xd0 0x7 0x0 0x0 0x9 0x8 0x0 0x0 0xd3 0x4a 0x1c 0xc 0xff 0xff 0xff 0xff ] [.........J......]        
        <- [0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff ] [................]
        <- [0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff ] [................]
        <- [0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff ] [................]
        <- [0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff ] [................]
        <- [0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff ] [................]
        <- [0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff ] [................]
        <- [0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff ] [................]
        <- [0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff ] [................]
        <- [0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff ] [................]
        <- [0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff 0xff ] [................]
Pin: 0x30e543ed                                                                                                 
Description: RIM BlackBerry Device                                                                              
System: Linux,2.6.31-16-generic-pae,#52-Ubuntu SMP Thu Dec 3 23:18:13 UTC 2009,i686                             

Modem pty: /dev/pts/8
Initializing Modem   
Writing data size: 12
        Modem -> [0x1 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x78 0x56 0x34 0x12 ] [........xV4.]
Writing data size: 12                                                                 
        Modem -> [0x1 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x78 0x56 0x34 0x12 ] [........xV4.]
Writing data size: 12                                                                 
        Modem -> [0x1 0x0 0x0 0x0 0x1 0x0 0x0 0x0 0x78 0x56 0x34 0x12 ] [........xV4.]
        Modem <- [0x4 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 ] [................]
        Modem <- [0x1 0x0 0x0 0x0 0x1c 0x0 0x0 0x0 0x78 0x56 0x34 0x12 ] [........xV4.]               
read: 28                                                                                              
No password requested.                                                                                
Writing data size: 28                                                                                 
        Modem -> [0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x3 0x0 0x0 0x0 0x0 0xc2 0x1 0x0 ] [................]
        Modem -> [0x42 0x42 0x54 0xe 0x34 0x4b 0x7b 0xc3 0x78 0x56 0x34 0x12 ] [BBT.4K{.xV4.]          
session pack sent                                                                                      
Starting Modem thread                                                                                  
Modem Started                                                                                          
Will try to start pppd now, (/usr/sbin/pppd) with config: sprint                                       
********************************************                                                           
Modem Ready at /dev/pts/8                                                                              
 Use ^C to terminate                                                                                   
********************************************                                                           
pppd options in effect:                                                                                
debug           # (from command line)                                                                  
nodetach                # (from command line)                                                          
dump            # (from command line)                                                                  
noauth          # (from /etc/ppp/options)                                                              
name wapuser            # (from conf/sprint)                                                           
user wapuser            # (from conf/sprint)                                                           
password ??????         # (from conf/sprint)                                                           
/dev/pts/8              # (from command line)                                                          
115200          # (from conf/sprint)                                                                   
lock            # (from /etc/ppp/options)                                                              
connect /usr/sbin/chat -v -V -f conf/sprint-chat                # (from conf/sprint)                   
crtscts         # (from conf/sprint)                                                                   
modem           # (from /etc/ppp/options)                                                              
noaccomp                # (from conf/sprint)                                                           
asyncmap 0              # (from /etc/ppp/options)                                                      
nomagic         # (from conf/sprint)                                                                   
nopcomp         # (from conf/sprint)                                                                   
lcp-echo-failure 999            # (from conf/sprint)                                                   
lcp-echo-interval 0             # (from conf/sprint)                                                   
lcp-restart 10          # (from conf/sprint)                                                           
hide-password           # (from /etc/ppp/options)                                                      
pap-restart 20          # (from conf/sprint)                                                           
pap-timeout 20          # (from conf/sprint)                                                           
novj            # (from conf/sprint)                                                                   
ipcp-accept-local               # (from conf/sprint)                                                   
ipcp-accept-remote              # (from conf/sprint)                                                   
noipdefault             # (from conf/sprint)                                                           
ipcp-restart 7          # (from conf/sprint)                                                           
defaultroute            # (from conf/sprint)                                                           
proxyarp                # (from /etc/ppp/options)                                                      
usepeerdns              # (from conf/sprint)                                                           
noccp           # (from conf/sprint)                                                                   
noipx           # (from /etc/ppp/options)                                                              
Starting GPRS connect script                                                                           
PPP data: BBT_OS                                                                                       
Starting session                                                                                       
Writing data size: 28                                                                                  
        Modem -> [0x0 0x0 0x0 0x0 0x23 0x0 0x0 0x0 0x3 0x0 0x0 0x0 0x0 0xc2 0x1 0x0 ] [....#...........]
        Modem -> [0x42 0x42 0x54 0xe 0x34 0x4b 0x7b 0xc3 0x78 0x56 0x34 0x12 ] [BBT.4K{.xV4.]           

PPP data: AT&F
Writing data size: 5
        Modem -> [0x41 0x54 0x26 0x46 0xd ] [AT&F.]
        Modem <- [0x41 0x54 0x26 0x46 0xd ] [AT&F.]
OK                                                 
        Modem <- [0xd 0xa 0x4f 0x4b 0xd 0xa ] [..OK..]
PPP data: ATZ                                         
Writing data size: 4                                  
        Modem -> [0x41 0x54 0x5a 0xd ] [ATZ.]         
        Modem <- [0x41 0x54 0x5a 0xd ] [ATZ.]         
        Modem <- [0xd 0xa 0x4f 0x4b 0xd 0xa ] [..OK..]
read: 21                                              
AT&F                                                  
OKDialing...                                          

ATZ
PPP data: ATI
Writing data size: 4
        Modem -> [0x41 0x54 0x49 0xd ] [ATI.]
        Modem <- [0x41 0x54 0x49 0xd ] [ATI.]
        Modem <- [0xd 0xa 0x4d 0x61 0x6e 0x75 0x66 0x61 0x63 0x74 0x75 0x72 0x65 0x72 0x3a 0x20 ] [..Manufacturer: ]
        Modem <- [0x52 0x65 0x73 0x65 0x61 0x72 0x63 0x68 0x20 0x49 0x6e 0x20 0x4d 0x6f 0x74 0x69 ] [Research In Moti]
        Modem <- [0x6f 0x6e 0xd 0xa 0x4d 0x6f 0x64 0x65 0x6c 0x3a 0x20 0x39 0x36 0x33 0x30 0xd ] [on..Model: 9630.]   
        Modem <- [0xa 0x52 0x65 0x76 0x69 0x73 0x69 0x6f 0x6e 0x3a 0x20 0x4f 0x53 0x20 0x56 0x65 ] [.Revision: OS Ve] 
        Modem <- [0x72 0x3a 0x20 0x34 0x2e 0x31 0x2e 0x30 0x2e 0x34 0x30 0x20 0x20 0x5b 0x4a 0x75 ] [r: 4.1.0.40  [Ju]
        Modem <- [0x6e 0x20 0x32 0x35 0x20 0x32 0x30 0x30 0x39 0x20 0x30 0x30 0x3a 0x31 0x38 0x3a ] [n 25 2009 00:18:]
        Modem <- [0x30 0x37 0x5d 0xd 0xa 0x45 0x53 0x4e 0x3a 0x20 0x30 0x78 0x38 0x30 0x33 0x34 ] [07]..ESN: 0x8034]  
        Modem <- [0x38 0x31 0x36 0x31 0xd 0xa 0x2b 0x47 0x43 0x41 0x50 0x3a 0x20 0x2b 0x43 0x49 ] [8161..+GCAP: +CI]  
        Modem <- [0x53 0x37 0x30 0x37 0x2d 0x41 0x2c 0x20 0x43 0x49 0x53 0x2d 0x38 0x35 0x36 0x2c ] [S707-A, CIS-856,]
        Modem <- [0x20 0x2b 0x4d 0x53 0x2c 0x20 0x2b 0x45 0x53 0x2c 0x20 0x2b 0x44 0x53 0x2c 0x20 ] [ +MS, +ES, +DS, ]
        Modem <- [0x2b 0x46 0x43 0x4c 0x41 0x53 0x53 0x2c 0x20 0x43 0x49 0x53 0x2d 0x38 0x35 0x36 ] [+FCLASS, CIS-856]
        Modem <- [0x2d 0x41 0xd 0xa 0xd 0xa 0x4f 0x4b 0xd 0xa ] [-A....OK..]                                          
OK                                                                                                                    
PPP data: ATDT#777                                                                                                    
Writing data size: 9                                                                                                  
        Modem -> [0x41 0x54 0x44 0x54 0x23 0x37 0x37 0x37 0xd ] [ATDT#777.]                                           
        Modem <- [0x41 0x54 0x44 0x54 0x23 0x37 0x37 0x37 0xd ] [ATDT#777.]                                           
read: 199                                                                                                             
ATI                                                                                                                   
Manufacturer: Research In Motion                                                                                      
Model: 9630                                                                                                           
Revision: OS Ver: 4.1.0.40  [Jun 25 2009 00:18:07]                                                                    
ESN: 0x80348161                                                                                                       
+GCAP: +CIS707-A, CIS-856, +MS, +ES, +DS, +FCLASS, CIS-856-A                                                          

OK
        Modem <- [0xd 0xa 0x4e 0x4f 0x20 0x43 0x41 0x52 0x52 0x49 0x45 0x52 0xd 0xa ] [..NO CARRIER..]
read: 14                                                                                              
ATDT#777                                                                                              
NO CARRIER                                                                                            
Script /usr/sbin/chat -v -V -f conf/sprint-chat finished (pid 13047), status = 0x3                    
Connect script failed                                                                                 
Failed finding end of line(timeout) for:                                                              
Usually means no reply from the modem                                                                 
Error: [Errno 11] Resource temporarily unavailable
******************************************************

Shutting down
Please WAIT for shutdown to complete (up to 30s)
Otherwise you might have to reboot your BB !
******************************************************
Writing data size: 4
        Modem -> [0x41 0x54 0x48 0xd ] [ATH.]
Waiting for PPPD shutdown to complete.
PPPD finished
Writing data size: 28
        Modem -> [0x0 0x0 0x0 0x0 0x23 0x0 0x0 0x0 0x3 0x0 0x0 0x0 0x0 0xc2 0x1 0x0 ] [....#...........]
        Modem -> [0x71 0x67 0x7d 0x20 0x3c 0xcd 0x74 0x7d 0x78 0x56 0x34 0x12 ] [qg} <.t}xV4.]
Writing data size: 12
        Modem -> [0x1 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x78 0x56 0x34 0x12 ] [........xV4.]
Writing data size: 28
        Modem -> [0x0 0x0 0x0 0x0 0x23 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0xc2 0x1 0x0 ] [....#...........]
        Modem -> [0x42 0x42 0x54 0xe 0x34 0x4b 0x7b 0xc3 0x78 0x56 0x34 0x12 ] [BBT.4K{.xV4.]
        Modem <- [0x41 0x54 0x48 0xd ] [ATH.]
        Modem <- [0xd 0xa 0x4f 0x4b 0xd 0xa ] [..OK..]
Stopping modem thread
read: 10
Modem thread Stopped
Disconnected
Modem Disconnected
It is now safe to shutdown.
Releasing interface
bbtether completed.
BBTether Thread completed.


[SIZE=6]Here is the conf file:[/SIZE]
 Tested by Timothy Owings
115200
noipdefault
defaultroute
#nomultilink
ipcp-restart 7
ipcp-accept-local
ipcp-accept-remote
lcp-echo-interval 0
lcp-echo-failure 999
nopcomp
noaccomp
pap-timeout 20
pap-restart 20
lcp-restart 10
#noauth
nomagic
noccp
crtscts
usepeerdns
novj
user wapuser
password wap
name wapuser
#debug debug debug
# does not exist in all pppd versions (osx)
#replacedefaultroute
connect "/usr/sbin/chat -v -V -f conf/sprint-chat"

[SIZE=6]And here is the sprint-chat file:[/SIZE]

TIMEOUT 10
ABORT 'BUSY'
ABORT 'NO ANSWER'
ABORT 'ERROR'
SAY 'Starting GPRS connect script\n'

'' 'BBT_OS'
'' 'AT&F'
OK 'ATZ'
OK 'ATI'

SAY 'Dialing...\n'
OK 'ATDT#777'
CONNECT
# Without ~p it does NOT continue passed Connect !!
~p

---

### Post by PaulReaver on 2009-12-11
could'nt this already be done with "hcitool scan" and
"rfcomm bind"?

then you can use "pppconfig" and "ppp" to create and dial the networks profile.

I'm sure ubuntu comes with bluetooth tools for pairing.

---

### Post by iamgeniusrnti on 2009-12-11
Nevermind... seems Sprint disabled PAM.  Now I gotta find a new service... ahhhhh....

---

### Post by iamgeniusrnti on 2009-12-11
> **PaulReaver said:**
> could'nt this already be done with "hcitool scan" and
"rfcomm bind"?

then you can use "pppconfig" and "ppp" to create and dial the networks profile.

I'm sure ubuntu comes with bluetooth tools for pairing.
 
I assume you are talking about pairing the phone with the computer?  I am using a USB connection--I don't even have BT on my netbook.

---

### Post by PaulReaver on 2009-12-11
yup bluetooth.

a small blue dongle is only a couple of dollars/pounds
bluetooth seems the most sensible to me on my netbook/laptop as my phone battery lasts longer than my netbooks battery. 
this way i dont need the phone hanging out of the netbook.   

never tried with usb but I assume that ppp or wvdial would work just as well through usb.

how does the berry show up on usb, is there a mass storage area to get in the way or does it show up as a  modem/cell phone.

---

### Post by iamgeniusrnti on 2009-12-11
> **PaulReaver said:**
> yup bluetooth.

a small blue dongle is only a couple of dollars/pounds
bluetooth seems the most sensible to me on my netbook/laptop as my phone battery lasts longer than my netbooks battery. 
this way i dont need the phone hanging out of the netbook.   

never tried with usb but I assume that ppp or wvdial would work just as well through usb.

how does the berry show up on usb, is there a mass storage area to get in the way or does it show up as a  modem/cell phone.


Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 017: ID 0fca:8004 Research In Motion, Ltd.
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I can do this:

genius@K-Netbook:~$ sudo killall pppob
[sudo] password for genius:
genius@K-Netbook:~$ sudo pppd call barry-sprint
Initializing
Script /usr/sbin/chat -f /etc/chatscripts/barry-sprint.chat finished (pid 13721), status = 0x5
Connect script failed
Waiting for 1 child processes...
  script /usr/sbin/pppob, pid 13719
sending SIGTERM to process 13719

But that just makes me want my 5 mins back.

---

### Post by PaulReaver on 2009-12-11
wtf? thats just vendor and product numbers.

I was thinking more of a "dmesg" rather than "lsusb"
dmesg'll tell you what module has claimed the phone storage or serial.

sorry if I'm confusing matters

---

### Post by iamgeniusrnti on 2009-12-11
> **PaulReaver said:**
> wtf? thats just vendor and product numbers.

I was thinking more of a "dmesg" rather than "lsusb"
dmesg'll tell you what module has claimed the phone storage or serial.

sorry if I'm confusing matters

Sorry new Linux user.  I ran dmesg and the output was huge.  How about this:
genius@K-Netbook:~$ dmesg | grep usb
[    0.386070] usbcore: registered new interface driver usbfs
[    0.386070] usbcore: registered new interface driver hub
[    0.386070] usbcore: registered new device driver usb
[    1.760555] usb usb1: configuration #1 chosen from 1 choice
[    1.761915] usb usb2: configuration #1 chosen from 1 choice
[    1.762874] usb usb3: configuration #1 chosen from 1 choice
[    1.763813] usb usb4: configuration #1 chosen from 1 choice
[    1.764803] usb usb5: configuration #1 chosen from 1 choice
[    2.072110] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    2.241900] usb 1-2: configuration #1 chosen from 1 choice
[   21.241479] input: WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input7
[   21.241617] usbcore: registered new interface driver uvcvideo
[   98.048181] usb 1-4: new high speed USB device using ehci_hcd and address 3
[   98.194771] usb 1-4: configuration #1 chosen from 1 choice
[   99.496127] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[   99.736578] usbcore: registered new interface driver usb-storage
[   99.736960] usb-storage: device found at 3
[   99.736968] usb-storage: waiting for device to settle before scanning
[  104.733143] usb-storage: device scan complete
[  256.557152] usb 1-4: usbfs: interface 1 claimed by usb-storage while 'bcharge' sets config #1
[  257.696114] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[  492.359152] usb 1-4: USB disconnect, address 3
[ 2337.288567] usb 1-4: new high speed USB device using ehci_hcd and address 4
[ 2337.435745] usb 1-4: configuration #1 chosen from 1 choice
[ 2337.448720] usb-storage: device found at 4
[ 2337.448727] usb-storage: waiting for device to settle before scanning
[ 2337.672952] usb 1-4: usbfs: interface 1 claimed by usb-storage while 'bcharge' sets config #1
[ 2338.784111] usb 1-4: reset high speed USB device using ehci_hcd and address 4

[SIZE=6]But if you want the whole thing, here you go[/SIZE]:

[    0.000000] Initializing cgroup subsys cpuset                                
[    0.000000] Initializing cgroup subsys cpu                                   
[    0.000000] Linux version 2.6.31-16-generic-pae (buildd@vernadsky) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #52-Ubuntu SMP Thu Dec 3 23:18:13 UTC 2009 (Ubuntu 2.6.31-16.52-generic-pae)                                                                                               
[    0.000000] KERNEL supported cpus:                                                                                                          
[    0.000000]   Intel GenuineIntel                                                                                                            
[    0.000000]   AMD AuthenticAMD                                                                                                              
[    0.000000]   NSC Geode by NSC                                                                                                              
[    0.000000]   Cyrix CyrixInstead                                                                                                            
[    0.000000]   Centaur CentaurHauls                                                                                                          
[    0.000000]   Transmeta GenuineTMx86                                                                                                        
[    0.000000]   Transmeta TransmetaCPU                                                                                                        
[    0.000000]   UMC UMC UMC UMC                                                                                                               
[    0.000000] BIOS-provided physical RAM map:                                                                                                 
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)                                                                        
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)                                                                      
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)                                                                      
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f576000 (usable)                                                                        
[    0.000000]  BIOS-e820: 000000003f576000 - 000000003f5bf000 (reserved)                                                                      
[    0.000000]  BIOS-e820: 000000003f5bf000 - 000000003f66d000 (usable)                                                                        
[    0.000000]  BIOS-e820: 000000003f66d000 - 000000003f6bf000 (ACPI NVS)                                                                      
[    0.000000]  BIOS-e820: 000000003f6bf000 - 000000003f6ef000 (usable)                                                                        
[    0.000000]  BIOS-e820: 000000003f6ef000 - 000000003f6ff000 (ACPI data)                                                                     
[    0.000000]  BIOS-e820: 000000003f6ff000 - 000000003f700000 (usable)                                                                        
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)                                                                      
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)                                                                      
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)                                                                      
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)                                                                      
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)                                                                      
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)                                                                      
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)                                                                      
[    0.000000] DMI 2.4 present.                                                                                                                
[    0.000000] last_pfn = 0x3f700 max_arch_pfn = 0x1000000                                                                                     
[    0.000000] MTRR default type: uncachable                                                                                                   
[    0.000000] MTRR fixed ranges enabled:                                                                                                      
[    0.000000]   00000-9FFFF write-back                                                                                                        
[    0.000000]   A0000-BFFFF uncachable                                                                                                        
[    0.000000]   C0000-C7FFF write-protect                                                                                                     
[    0.000000]   C8000-EFFFF uncachable                                                                                                        
[    0.000000]   F0000-FFFFF write-protect                                                                                                     
[    0.000000] MTRR variable ranges enabled:                                                                                                   
[    0.000000]   0 base 0FFF00000 mask 0FFF00000 write-protect                                                                                 
[    0.000000]   1 base 0FFFC0000 mask 0FFFE0000 uncachable                                                                                    
[    0.000000]   2 base 000000000 mask 0E0000000 write-back                                                                                    
[    0.000000]   3 base 020000000 mask 0E0000000 write-back                                                                                    
[    0.000000]   4 base 03F800000 mask 0FF800000 uncachable                                                                                    
[    0.000000]   5 base 03F700000 mask 0FFF00000 uncachable                                                                                    
[    0.000000]   6 disabled                                                                                                                    
[    0.000000]   7 base 000000000 mask 0FFFE0000 uncachable                                                                                    
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106                                                                
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)                                                  
[    0.000000] Scanning 1 areas for low memory corruption                                                                                      
[    0.000000] modified physical RAM map:                                                                                                      
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)                                                                         
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)                                                                       
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)                                                                         
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)                                                                       
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)                                                                       
[    0.000000]  modified: 0000000000100000 - 000000003f576000 (usable)                                                                         
[    0.000000]  modified: 000000003f576000 - 000000003f5bf000 (reserved)                                                                       
[    0.000000]  modified: 000000003f5bf000 - 000000003f66d000 (usable)                                                                         
[    0.000000]  modified: 000000003f66d000 - 000000003f6bf000 (ACPI NVS)                                                                       
[    0.000000]  modified: 000000003f6bf000 - 000000003f6ef000 (usable)                                                                         
[    0.000000]  modified: 000000003f6ef000 - 000000003f6ff000 (ACPI data)                                                                      
[    0.000000]  modified: 000000003f6ff000 - 000000003f700000 (usable)                                                                         
[    0.000000]  modified: 000000003f700000 - 0000000040000000 (reserved)                                                                       
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)                                                                       
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)                                                                       
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)                                                                       
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)                                                                       
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)                                                                       
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)                                                                       
[    0.000000] initial memory mapped : 0 - 00c00000                                                                                            
[    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000                                                                          
[    0.000000] Using x86 segment limits to approximate NX protection                                                                           
[    0.000000]  0000000000 - 0000200000 page 4k                                                                                                
[    0.000000]  0000200000 - 0037800000 page 2M                                                                                                
[    0.000000]  0037800000 - 00379fe000 page 4k                                                                                                
[    0.000000] kernel direct mapping tables up to 379fe000 @ 7000-d000                                                                         
[    0.000000] RAMDISK: 2f0ca000 - 2f858344                                                                                                    
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 ACER  )                                                                                          
[    0.000000] ACPI: XSDT 3f6fe120 00064 (v01 ACER   ACER     00000001      01000013)                                                          
[    0.000000] ACPI: FACP 3f6fc000 000F4 (v04 ACER   ACER     00000001 1025 01000013)                                                          
[    0.000000] ACPI: DSDT 3f6f1000 06D91 (v01 ACER   ACER     00000001 1025 01000013)                                                          
[    0.000000] ACPI: FACS 3f688000 00040                                                                                                       
[    0.000000] ACPI: SSDT 3f6fd000 004C4 (v02  PmRef    CpuPm 00003000 INTL 20051117)                                                          
[    0.000000] ACPI: HPET 3f6fb000 00038 (v01 ACER   ACER     00000001 1025 01000013)                                                          
[    0.000000] ACPI: APIC 3f6fa000 00068 (v02 ACER   ACER     00000001 1025 01000013)                                                          
[    0.000000] ACPI: MCFG 3f6f9000 0003C (v01 ACER   ACER     00000001 1025 01000013)                                                          
[    0.000000] ACPI: ASF! 3f6f8000 000A5 (v32 ACER   ACER     00000001 1025 01000013)                                                          
[    0.000000] ACPI: SLIC 3f6f0000 00180 (v01 ACER   ACER     00000001 1025 01000013)                                                          
[    0.000000] ACPI: BOOT 3f6ef000 00028 (v01 ACER   ACER     00000001 1025 01000013)                                                          
[    0.000000] ACPI: Local APIC address 0xfee00000                                                                                             
[    0.000000] 125MB HIGHMEM available.                                                                                                        
[    0.000000] 889MB LOWMEM available.                                                                                                         
[    0.000000]   mapped low ram: 0 - 379fe000                                                                                                  
[    0.000000]   low ram: 0 - 379fe000                                                                                                         
[    0.000000]   node 0 low ram: 00000000 - 379fe000                                                                                           
[    0.000000]   node 0 bootmap 00009000 - 0000ff40                                                                                            
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]                                                                    
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]                                                   
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]                                                   
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]                                                   
[    0.000000]   #3 [0000100000 - 00008ad9a0]    TEXT DATA BSS ==> [0000100000 - 00008ad9a0]                                                   
[    0.000000]   #4 [002f0ca000 - 002f858344]          RAMDISK ==> [002f0ca000 - 002f858344]                                                   
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]                                                   
[    0.000000]   #6 [00008ae000 - 00008b4178]              BRK ==> [00008ae000 - 00008b4178]                                                   
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]                                                   
[    0.000000]   #8 [0000009000 - 0000010000]          BOOTMAP ==> [0000009000 - 0000010000]                                                   
[    0.000000] Zone PFN ranges:                                                                                                                
[    0.000000]   DMA      0x00000000 -> 0x00001000                                                                                             
[    0.000000]   Normal   0x00001000 -> 0x000379fe                                                                                             
[    0.000000]   HighMem  0x000379fe -> 0x0003f700                                                                                             
[    0.000000] Movable zone start PFN for each node                                                                                            
[    0.000000] early_node_map[6] active PFN ranges                                                                                             
[    0.000000]     0: 0x00000000 -> 0x00000002                                                                                                 
[    0.000000]     0: 0x00000006 -> 0x0000009f                                                                                                 
[    0.000000]     0: 0x00000100 -> 0x0003f576                                                                                                 
[    0.000000]     0: 0x0003f5bf -> 0x0003f66d                                                                                                 
[    0.000000]     0: 0x0003f6bf -> 0x0003f6ef                                                                                                 
[    0.000000]     0: 0x0003f6ff -> 0x0003f700                                                                                                 
[    0.000000] On node 0 totalpages: 259568                                                                                                    
[    0.000000] free_area_init_node: node 0, pgdat c078bd20, node_mem_map c1000000                                                              
[    0.000000]   DMA zone: 32 pages used for memmap                                                                                            
[    0.000000]   DMA zone: 0 pages reserved                                                                                                    
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0                                                                                            
[    0.000000]   Normal zone: 1748 pages used for memmap                                                                                       
[    0.000000]   Normal zone: 221994 pages, LIFO batch:31                                                                                      
[    0.000000]   HighMem zone: 251 pages used for memmap                                                                                       
[    0.000000]   HighMem zone: 31580 pages, LIFO batch:7                                                                                       
[    0.000000] Using APIC driver default                                                                                                       
[    0.000000] ACPI: PM-Timer IO Port: 0x408                                                                                                   
[    0.000000] ACPI: Local APIC address 0xfee00000                                                                                             
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)                                                                              
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)                                                                              
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])                                                                             
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])                                                                             
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])                                                                         
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23                                                                  
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)                                                                        
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)                                                                     
[    0.000000] ACPI: IRQ0 used by override.                                                                                                    
[    0.000000] ACPI: IRQ2 used by override.                                                                                                    
[    0.000000] ACPI: IRQ9 used by override.                                                                                                    
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs                                                                                   
[    0.000000] Using ACPI (MADT) for SMP configuration information                                                                             
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000                                                                                      
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs                                                                                            
[    0.000000] nr_irqs_gsi: 24                                                                                                                 
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000                                                               
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000                                                               
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000                                                               
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000                                                               
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)                                                          
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1                                                                          
[    0.000000] PERCPU: Embedded 14 pages at c17f5000, static data 35612 bytes                                                                  
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257537                                                     
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic-pae root=UUID=d01f9679-4402-4598-909d-786313a32aec ro splash    
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)                                                                           
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)                                                                
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)                                                                  
[    0.000000] Enabling fast FPU save and restore... done.                                                                                     
[    0.000000] Enabling unmasked SIMD FPU exception support... done.                                                                           
[    0.000000] Initializing CPU#0                                                                                                              
[    0.000000] allocated 5196800 bytes of page_cgroup                                                                                          
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups                                                      
[    0.000000] Initializing HighMem for node 0 (000379fe:0003f700)                                                                             
[    0.000000] Memory: 1008056k/1039360k available (4590k kernel code, 29792k reserved, 2147k data, 544k init, 127324k highmem)                
[    0.000000] virtual kernel memory layout:                                                                                                   
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)                                                                               
[    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)                                                                               
[    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)                                                                               
[    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)                                                                               
[    0.000000]       .init : 0xc0795000 - 0xc081d000   ( 544 kB)                                                                               
[    0.000000]       .data : 0xc057b974 - 0xc07947a8   (2147 kB)                                                                               
[    0.000000]       .text : 0xc0100000 - 0xc057b974   (4590 kB)                                                                               
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.                                                     
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1                                                         
[    0.000000] NR_IRQS:2304 nr_irqs:424                                                                                                        
[    0.000000] Fast TSC calibration using PIT                                                                                                  
[    0.000000] Detected 1595.798 MHz processor.                                                                                                
[    0.001950] Console: colour VGA+ 80x25                                                                                                      
[    0.001957] console [tty0] enabled                                                                                                          
[    0.004000] hpet clockevent registered                                                                                                      
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer                                                                
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.59 BogoMIPS (lpj=6383192)                       
[    0.004000] Security Framework initialized                                                                                                  
[    0.004000] AppArmor: AppArmor initialized                                                                                                  
[    0.004000] Mount-cache hash table entries: 512                                                                                             
[    0.004000] Initializing cgroup subsys ns                                                                                                   
[    0.004000] Initializing cgroup subsys cpuacct                                                                                              
[    0.004000] Initializing cgroup subsys memory                                                                                               
[    0.004000] Initializing cgroup subsys freezer                                                                                              
[    0.004000] Initializing cgroup subsys net_cls                                                                                              
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 24K                                                                                           
[    0.004000] CPU: L2 cache: 512K                                                                                                             
[    0.004000] CPU: Physical Processor ID: 0                                                                                                   
[    0.004000] CPU: Processor Core ID: 0                                                                                                       
[    0.004000] mce: CPU supports 5 MCE banks                                                                                                   
[    0.004000] CPU0: Thermal monitoring enabled (TM2)                                                                                          
[    0.004000] using mwait in idle threads.                                                                                                    
[    0.004000] Performance Counters: Atom events, Intel PMU driver.                                                                            
[    0.004000] ... version:                 3                                                                                                  
[    0.004000] ... bit width:               40                                                                                                 
[    0.004000] ... generic counters:        2                                                                                                  
[    0.004000] ... value mask:              000000ffffffffff                                                                                   
[    0.004000] ... max period:              000000007fffffff                                                                                   
[    0.004000] ... fixed-purpose counters:  3                                                                                                  
[    0.004000] ... counter mask:            0000000700000003                                                                                   
[    0.004000] Checking 'hlt' instruction... OK.                                                                                               
[    0.020014] ACPI: Core revision 20090521                                                                                                    
[    0.044279] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1                                                                            
[    0.084043] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02                                                                        
[    0.088001] Booting processor 1 APIC 0x1 ip 0x6000                                                                                          
[    0.004000] Initializing CPU#1                                                                                                              
[    0.004000] Calibrating delay using timer specific routine.. 3191.95 BogoMIPS (lpj=6383910)                                                 
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 24K                                                                                           
[    0.004000] CPU: L2 cache: 512K                                                                                                             
[    0.004000] CPU: Physical Processor ID: 0                                                                                                   
[    0.004000] CPU: Processor Core ID: 0                                                                                                       
[    0.004000] mce: CPU supports 5 MCE banks                                                                                                   
[    0.004000] CPU1: Thermal monitoring enabled (TM2)                                                                                          
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106                                                                
[    0.176996] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02                                                                        
[    0.177709] checking TSC synchronization [CPU#0 -> CPU#1]: passed.                                                                          
[    0.180038] Brought up 2 CPUs                                                                                                               
[    0.180104] Total of 2 processors activated (6383.55 BogoMIPS).                                                                             
[    0.180234] CPU0 attaching sched-domain:                                                                                                    
[    0.180241]  domain 0: span 0-1 level SIBLING                                                                                               
[    0.180247]   groups: 0 1                                                                                                                   
[    0.180257] CPU1 attaching sched-domain:                                                                                                    
[    0.180262]  domain 0: span 0-1 level SIBLING                                                                                               
[    0.180268]   groups: 1 0                                                                                                                   
[    0.180425] Booting paravirtualized kernel on bare hardware                                                                                 
[    0.180547] regulator: core version 0.5                                                                                                     
[    0.180547] Time:  8:41:02  Date: 12/11/09                                                                                                  
[    0.180547] NET: Registered protocol family 16                                                                                              
[    0.180621] EISA bus registered                                                                                                             
[    0.180701] ACPI: bus type pci registered                                                                                                   
[    0.184059] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255                                                                
[    0.184131] PCI: MCFG area at e0000000 reserved in E820                                                                                     
[    0.184195] PCI: Using MMCONFIG for extended config space                                                                                   
[    0.184261] PCI: Using configuration type 1 for base access                                                                                 
[    0.186494] bio: create slab <bio-0> at 0                                                                                                   
[    0.188685] ACPI: EC: Look up EC in DSDT                                                                                                    
[    0.227223] ACPI: BIOS _OSI(Linux) query ignored                                                                                            
[    0.228132] ACPI: Interpreter enabled                                                                                                       
[    0.228199] ACPI: (supports S0 S3 S4 S5)                                                                                                    
[    0.228435] ACPI: Using IOAPIC for interrupt routing                                                                                        
[    0.229361] ACPI: EC: non-query interrupt received, switching to interrupt mode                                                             
[    0.362227] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function                                                              
[    0.364738] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62                                                                   
[    0.364811] ACPI: EC: driver started in interrupt mode                                                                                      
[    0.365008] ACPI: Power Resource [FN00] (on)                                                                                                
[    0.365521] ACPI: No dock devices found.                                                                                                    
[    0.366854] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS                                                   
[    0.367018] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7414a50), AE_ALREADY_EXISTS                   
[    0.367222] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error                                                      
[    0.367427] ACPI: PCI Root Bridge [PCI0] (0000:00)                                                                                          
[    0.367633] pci 0000:00:02.0: reg 10 32bit mmio: [0x56280000-0x562fffff]                                                                    
[    0.367644] pci 0000:00:02.0: reg 14 io port: [0x50f0-0x50f7]                                                                               
[    0.367654] pci 0000:00:02.0: reg 18 32bit mmio: [0x40000000-0x4fffffff]                                                                    
[    0.367663] pci 0000:00:02.0: reg 1c 32bit mmio: [0x56300000-0x5633ffff]                                                                    
[    0.367717] pci 0000:00:02.1: reg 10 32bit mmio: [0x56200000-0x5627ffff]                                                                    
[    0.367857] pci 0000:00:1b.0: reg 10 64bit mmio: [0x56340000-0x56343fff]                                                                    
[    0.367930] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold                                                                           
[    0.368012] pci 0000:00:1b.0: PME# disabled                                                                                                 
[    0.368176] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold                                                                           
[    0.368247] pci 0000:00:1c.0: PME# disabled                                                                                                 
[    0.368412] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold                                                                           
[    0.368483] pci 0000:00:1c.1: PME# disabled                                                                                                 
[    0.368646] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold                                                                           
[    0.368717] pci 0000:00:1c.2: PME# disabled                                                                                                 
[    0.368857] pci 0000:00:1d.0: reg 20 io port: [0x50a0-0x50bf]                                                                               
[    0.368937] pci 0000:00:1d.1: reg 20 io port: [0x5080-0x509f]                                                                               
[    0.369016] pci 0000:00:1d.2: reg 20 io port: [0x5060-0x507f]                                                                               
[    0.369095] pci 0000:00:1d.3: reg 20 io port: [0x5040-0x505f]                                                                               
[    0.369179] pci 0000:00:1d.7: reg 10 32bit mmio: [0x56344400-0x563447ff]                                                                    
[    0.369252] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold                                                                           
[    0.369324] pci 0000:00:1d.7: PME# disabled                                                                                                 
[    0.369582] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO                                                         
[    0.369673] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO                                                                  
[    0.369748] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at ff2c (mask 0003)                                                          
[    0.369841] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0068 (mask 0007)                                                          
[    0.369993] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]                                                                                   
[    0.370005] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]                                                                                   
[    0.370017] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]                                                                                   
[    0.370029] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]                                                                                   
[    0.370042] pci 0000:00:1f.1: reg 20 io port: [0x50c0-0x50cf]                                                                               
[    0.370124] pci 0000:00:1f.2: reg 10 io port: [0x50d8-0x50df]                                                                               
[    0.370136] pci 0000:00:1f.2: reg 14 io port: [0x50fc-0x50ff]                                                                               
[    0.370149] pci 0000:00:1f.2: reg 18 io port: [0x50d0-0x50d7]                                                                               
[    0.370161] pci 0000:00:1f.2: reg 1c io port: [0x50f8-0x50fb]                                                                               
[    0.370173] pci 0000:00:1f.2: reg 20 io port: [0x5020-0x502f]                                                                               
[    0.370186] pci 0000:00:1f.2: reg 24 32bit mmio: [0x56344000-0x563443ff]                                                                    
[    0.370231] pci 0000:00:1f.2: PME# supported from D3hot                                                                                     
[    0.370300] pci 0000:00:1f.2: PME# disabled                                                                                                 
[    0.370436] pci 0000:00:1f.3: reg 20 io port: [0x5000-0x501f]                                                                               
[    0.370561] pci 0000:01:00.0: reg 10 64bit mmio: [0x55100000-0x5510ffff]                                                                    
[    0.370663] pci 0000:01:00.0: supports D1 D2                                                                                                
[    0.370668] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold                                                                     
[    0.370741] pci 0000:01:00.0: PME# disabled                                                                                                 
[    0.370890] pci 0000:00:1c.0: bridge io port: [0x4000-0x4fff]                                                                               
[    0.370899] pci 0000:00:1c.0: bridge 32bit mmio: [0x55100000-0x561fffff]                                                                    
[    0.370912] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x50000000-0x50ffffff]                                                               
[    0.370986] pci 0000:00:1c.1: bridge io port: [0x3000-0x3fff]                                                                               
[    0.370994] pci 0000:00:1c.1: bridge 32bit mmio: [0x54100000-0x550fffff]                                                                    
[    0.371007] pci 0000:00:1c.1: bridge 64bit mmio pref: [0x51000000-0x51ffffff]                                                               
[    0.371093] pci 0000:03:00.0: reg 10 64bit mmio: [0x53000000-0x5303ffff]                                                                    
[    0.371108] pci 0000:03:00.0: reg 18 io port: [0x1000-0x107f]                                                                               
[    0.371203] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold                                                                     
[    0.371277] pci 0000:03:00.0: PME# disabled                                                                                                 
[    0.371424] pci 0000:00:1c.2: bridge io port: [0x1000-0x2fff]                                                                               
[    0.371433] pci 0000:00:1c.2: bridge 32bit mmio: [0x53000000-0x540fffff]                                                                    
[    0.371446] pci 0000:00:1c.2: bridge 64bit mmio pref: [0x52000000-0x52ffffff]                                                               
[    0.371527] pci 0000:00:1e.0: transparent bridge                                                                                            
[    0.371632] pci_bus 0000:00: on NUMA node 0                                                                                                 
[    0.371645] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]                                                                             
[    0.372075] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]                                                                        
[    0.372322] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]                                                                        
[    0.372502] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]                                                                        
[    0.372906] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS                                                   
[    0.373071] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7414a50), AE_ALREADY_EXISTS                   
[    0.380377] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)                                                                      
[    0.381015] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)                                                                      
[    0.381644] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)                                                                      
[    0.382277] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)                                                                      
[    0.382907] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.                                                         
[    0.383620] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.                                                         
[    0.384343] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.                                                         
[    0.385052] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.                                                         
[    0.385931] SCSI subsystem initialized                                                                                                      
[    0.386070] libata version 3.00 loaded.                                                                                                     
[    0.386070] usbcore: registered new interface driver usbfs                                                                                  
[    0.386070] usbcore: registered new interface driver hub                                                                                    
[    0.386070] usbcore: registered new device driver usb                                                                                       
[    0.386070] ACPI: WMI: Mapper loaded                                                                                                        
[    0.386070] PCI: Using ACPI for IRQ routing                                                                                                 
[    0.396024] Bluetooth: Core ver 2.15                                                                                                        
[    0.396129] NET: Registered protocol family 31                                                                                              
[    0.396129] Bluetooth: HCI device and connection manager initialized                                                                        
[    0.396169] Bluetooth: HCI socket layer initialized                                                                                         
[    0.396233] NetLabel: Initializing                                                                                                          
[    0.396293] NetLabel:  domain hash size = 128                                                                                               
[    0.396355] NetLabel:  protocols = UNLABELED CIPSOv4                                                                                        
[    0.396440] NetLabel:  unlabeled traffic allowed by default                                                                                 
[    0.396574] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0                                                                                         
[    0.396772] hpet0: 3 comparators, 64-bit 14.318180 MHz counter                                                                              
[    0.416030] pnp: PnP ACPI init                                                                                                              
[    0.416133] ACPI: bus type pnp registered                                                                                                   
[    0.484750] pnp 00:01: io resource (0x164e-0x164f) overlaps 0000:00:1c.2 BAR 13 (0x1000-0x2fff), disabling                                  
[    0.486439] pnp: PnP ACPI: found 9 devices                                                                                                  
[    0.486506] ACPI: ACPI bus type pnp unregistered                                                                                            
[    0.486572] PnPBIOS: Disabled by ACPI PNP                                                                                                   
[    0.486659] system 00:01: ioport range 0x200-0x20f has been reserved                                                                        
[    0.486732] system 00:01: ioport range 0x600-0x60f has been reserved                                                                        
[    0.486802] system 00:01: ioport range 0x610-0x610 has been reserved                                                                        
[    0.486872] system 00:01: ioport range 0x800-0x80f has been reserved                                                                        
[    0.486942] system 00:01: ioport range 0x400-0x47f has been reserved                                                                        
[    0.487013] system 00:01: ioport range 0x500-0x53f has been reserved                                                                        
[    0.487083] system 00:01: ioport range 0xff2c-0xff2f has been reserved                                                                      
[    0.487157] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved                                                               
[    0.487230] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved                                                               
[    0.487303] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved                                                               
[    0.487376] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved                                                               
[    0.487448] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved                                                               
[    0.487522] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved                                                           
[    0.487612] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved                                                               
[    0.501854] Switched to high resolution mode on CPU 1                                                                                       
[    0.504007] Switched to high resolution mode on CPU 0                                                                                       
[    0.522560] AppArmor: AppArmor Filesystem Enabled                                                                                           
[    0.522706] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01                                                                             
[    0.522777] pci 0000:00:1c.0:   IO window: 0x4000-0x4fff                                                                                    
[    0.522849] pci 0000:00:1c.0:   MEM window: 0x55100000-0x561fffff                                                                           
[    0.522921] pci 0000:00:1c.0:   PREFETCH window: 0x00000050000000-0x00000050ffffff                                                          
[    0.523017] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02                                                                             
[    0.523086] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff                                                                                    
[    0.523157] pci 0000:00:1c.1:   MEM window: 0x54100000-0x550fffff                                                                           
[    0.523229] pci 0000:00:1c.1:   PREFETCH window: 0x00000051000000-0x00000051ffffff                                                          
[    0.523325] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03                                                                             
[    0.523395] pci 0000:00:1c.2:   IO window: 0x1000-0x2fff                                                                                    
[    0.523466] pci 0000:00:1c.2:   MEM window: 0x53000000-0x540fffff                                                                           
[    0.523538] pci 0000:00:1c.2:   PREFETCH window: 0x00000052000000-0x00000052ffffff                                                          
[    0.523634] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04                                                                             
[    0.523701] pci 0000:00:1e.0:   IO window: disabled                                                                                         
[    0.523770] pci 0000:00:1e.0:   MEM window: disabled                                                                                        
[    0.523837] pci 0000:00:1e.0:   PREFETCH window: disabled                                                                                   
[    0.523922]   alloc irq_desc for 16 on node -1                                                                                              
[    0.523927]   alloc kstat_irqs on node -1                                                                                                   
[    0.523940] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                                    
[    0.524030] pci 0000:00:1c.0: setting latency timer to 64                                                                                   
[    0.524045] pci 0000:00:1c.1: enabling device (0000 -> 0003)                                                                                
[    0.524115]   alloc irq_desc for 17 on node -1                                                                                              
[    0.524119]   alloc kstat_irqs on node -1                                                                                                   
[    0.524128] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17                                                                    
[    0.524203] pci 0000:00:1c.1: setting latency timer to 64                                                                                   
[    0.524218]   alloc irq_desc for 18 on node -1                                                                                              
[    0.524222]   alloc kstat_irqs on node -1                                                                                                   
[    0.524230] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18                                                                    
[    0.524304] pci 0000:00:1c.2: setting latency timer to 64                                                                                   
[    0.524317] pci 0000:00:1e.0: setting latency timer to 64                                                                                   
[    0.524327] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]                                                                                  
[    0.524334] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]                                                                  
[    0.524341] pci_bus 0000:01: resource 0 io:  [0x4000-0x4fff]                                                                                
[    0.524347] pci_bus 0000:01: resource 1 mem: [0x55100000-0x561fffff]                                                                        
[    0.524354] pci_bus 0000:01: resource 2 pref mem [0x50000000-0x50ffffff]                                                                    
[    0.524360] pci_bus 0000:02: resource 0 io:  [0x3000-0x3fff]                                                                                
[    0.524366] pci_bus 0000:02: resource 1 mem: [0x54100000-0x550fffff]                                                                        
[    0.524373] pci_bus 0000:02: resource 2 pref mem [0x51000000-0x51ffffff]                                                                    
[    0.524379] pci_bus 0000:03: resource 0 io:  [0x1000-0x2fff]                                                                                
[    0.524385] pci_bus 0000:03: resource 1 mem: [0x53000000-0x540fffff]                                                                        
[    0.524392] pci_bus 0000:03: resource 2 pref mem [0x52000000-0x52ffffff]                                                                    
[    0.524398] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]                                                                                  
[    0.524405] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffffffffffff]                                                                  
[    0.524478] NET: Registered protocol family 2                                                                                               
[    0.524739] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)                                                               
[    0.525490] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)                                                            
[    0.526554] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)                                                                     
[    0.527074] TCP: Hash tables configured (established 131072 bind 65536)                                                                     
[    0.527150] TCP reno registered                                                                                                             
[    0.527422] NET: Registered protocol family 1                                                                                               
[    0.527631] Trying to unpack rootfs image as initramfs...                                                                                   
[    0.906144] Freeing initrd memory: 7736k freed                                                                                              
[    0.913641] Simple Boot Flag value 0x5 read from CMOS RAM was invalid                                                                       
[    0.913724] Simple Boot Flag at 0x44 set to 0x1                                                                                             
[    0.914194] cpufreq-nforce2: No nForce2 chipset.                                                                                            
[    0.914316] Scanning for low memory corruption every 60 seconds                                                                             
[    0.914607] audit: initializing netlink socket (disabled)                                                                                   
[    0.914699] type=2000 audit(1260520862.912:1): initialized                                                                                  
[    0.932245] highmem bounce pool size: 64 pages                                                                                              
[    0.932321] HugeTLB registered 2 MB page size, pre-allocated 0 pages                                                                        
[    0.935545] VFS: Disk quotas dquot_6.5.2                                                                                                    
[    0.935736] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)                                                                      
[    0.937102] fuse init (API version 7.12)                                                                                                    
[    0.937363] msgmni has been set to 1736                                                                                                     
[    0.937925] alg: No test for stdrng (krng)                                                                                                  
[    0.938020] io scheduler noop registered                                                                                                    
[    0.938084] io scheduler anticipatory registered                                                                                            
[    0.938148] io scheduler deadline registered                                                                                                
[    0.938316] io scheduler cfq registered (default)                                                                                           
[    0.938401] pci 0000:00:02.0: Boot video device                                                                                             
[    0.938851]   alloc irq_desc for 24 on node -1                                                                                              
[    0.938857]   alloc kstat_irqs on node -1                                                                                                   
[    0.938878] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X                                                                              
[    0.938894] pcieport-driver 0000:00:1c.0: setting latency timer to 64                                                                       
[    0.939117]   alloc irq_desc for 25 on node -1                                                                                              
[    0.939122]   alloc kstat_irqs on node -1                                                                                                   
[    0.939137] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X                                                                              
[    0.939152] pcieport-driver 0000:00:1c.1: setting latency timer to 64                                                                       
[    0.939373]   alloc irq_desc for 26 on node -1                                                                                              
[    0.939379]   alloc kstat_irqs on node -1                                                                                                   
[    0.939393] pcieport-driver 0000:00:1c.2: irq 26 for MSI/MSI-X                                                                              
[    0.939408] pcieport-driver 0000:00:1c.2: setting latency timer to 64                                                                       
[    0.939585] pci_hotplug: PCI Hot Plug PCI Core version: 0.5                                                                                 
[    0.939880] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS                                                   
[    0.940071] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7414a50), AE_ALREADY_EXISTS                   
[    0.940532] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS                                                   
[    0.941753] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7414a50), AE_ALREADY_EXISTS                   
[    0.942198] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS                                                   
[    0.942361] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7414a50), AE_ALREADY_EXISTS                   
[    0.942848] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS                                                   
[    0.943010] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7414a50), AE_ALREADY_EXISTS                   
[    0.943451] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS                                                   
[    0.943613] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7414a50), AE_ALREADY_EXISTS                   
[    0.944109] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS                                                   
[    0.944272] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7414a50), AE_ALREADY_EXISTS                   
[    0.944559] pciehp: PCI Express Hot Plug Controller Driver version: 0.4                                                                     
[    1.008148] ACPI: AC Adapter [AC] (on-line)                                                                                                 
[    1.008361] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0                                                            
[    1.008453] ACPI: Power Button [PWRF]                                                                                                       
[    1.008630] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1                                                   
[    1.008722] ACPI: Power Button [PWRB]                                                                                                       
[    1.008874] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2                                                     
[    1.009050] ACPI: Lid Switch [LID0]                                                                                                         
[    1.009209] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3                                                   
[    1.009301] ACPI: Sleep Button [SLPB]                                                                                                       
[    1.009664] fan PNP0C0B:00: registered as cooling_device0                                                                                   
[    1.009738] ACPI: Fan [FAN] (on)                                                                                                            
[    1.011155] ACPI: SSDT 3f592c90 00239 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)                                                          
[    1.012133] ACPI: SSDT 3f591e10 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)                                                          
[    1.013889] Marking TSC unstable due to TSC halts in idle                                                                                   
[    1.013985] ACPI: CPU0 (power states: C1[C1] C2[C2])                                                                                        
[    1.014186] processor LNXCPU:00: registered as cooling_device1                                                                              
[    1.014258] ACPI: Processor [CPU0] (supports 8 throttling states)                                                                           
[    1.015124] ACPI: SSDT 3f592f10 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)                                                          
[    1.015987] ACPI: SSDT 3f590f10 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)                                                          
[    1.017941] ACPI: CPU1 (power states: C1[C1] C2[C2])                                                                                        
[    1.018153] processor LNXCPU:01: registered as cooling_device2                                                                              
[    1.018224] ACPI: Processor [CPU1] (supports 8 throttling states)                                                                           
[    1.082998] thermal LNXTHERM:01: registered as thermal_zone0                                                                                
[    1.083079] ACPI: Thermal Zone [THRM] (27 C)                                                                                                
[    1.083278] isapnp: Scanning for PnP cards...                                                                                               
[    1.437549] isapnp: No Plug & Play device found                                                                                             
[    1.728213] ACPI: Battery Slot [BAT0] (battery present)                                                                                     
[    1.728577] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled                                                                         
[    1.731317] brd: module loaded                                                                                                              
[    1.732440] loop: module loaded                                                                                                             
[    1.732687] input: Macintosh mouse button emulation as /devices/virtual/input/input4                                                        
[    1.732945] ahci 0000:00:1f.2: version 3.0                                                                                                  
[    1.732976] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17                                                                   
[    1.733114]   alloc irq_desc for 27 on node -1                                                                                              
[    1.733120]   alloc kstat_irqs on node -1                                                                                                   
[    1.733139] ahci 0000:00:1f.2: irq 27 for MSI/MSI-X                                                                                         
[    1.733205] ahci: SSS flag set, parallel bus scan disabled                                                                                  
[    1.733316] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode                                                  
[    1.733409] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pio slum part                                                          
[    1.733501] ahci 0000:00:1f.2: setting latency timer to 64                                                                                  
[    1.733871] scsi0 : ahci                                                                                                                    
[    1.734168] scsi1 : ahci                                                                                                                    
[    1.734373] scsi2 : ahci                                                                                                                    
[    1.734570] scsi3 : ahci                                                                                                                    
[    1.735003] ata1: SATA max UDMA/133 abar m1024@0x56344000 port 0x56344100 irq 27                                                            
[    1.735093] ata2: DUMMY                                                                                                                     
[    1.735153] ata3: SATA max UDMA/133 abar m1024@0x56344000 port 0x56344200 irq 27                                                            
[    1.735240] ata4: DUMMY                                                                                                                     
[    1.735449] ata_piix 0000:00:1f.1: version 2.13                                                                                             
[    1.735481] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                               
[    1.735623] ata_piix 0000:00:1f.1: setting latency timer to 64                                                                              
[    1.735778] scsi4 : ata_piix                                                                                                                
[    1.735987] scsi5 : ata_piix                                                                                                                
[    1.737143] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x50c0 irq 14                                                                 
[    1.737217] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x50c8 irq 15                                                                 
[    1.737675] ata6: port disabled. ignoring.                                                                                                  
[    1.739347] Fixed MDIO Bus: probed                                                                                                          
[    1.739492] PPP generic driver version 2.4.2                                                                                                
[    1.739767] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver                                                                      
[    1.739877] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                               
[    1.739978] ehci_hcd 0000:00:1d.7: setting latency timer to 64                                                                              
[    1.739985] ehci_hcd 0000:00:1d.7: EHCI Host Controller                                                                                     
[    1.740188] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1                                                            
[    1.744207] ehci_hcd 0000:00:1d.7: debug port 1                                                                                             
[    1.744278] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported                                                                   
[    1.744309] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x56344400                                                                                
[    1.760038] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00                                                                               
[    1.760555] usb usb1: configuration #1 chosen from 1 choice                                                                                 
[    1.760684] hub 1-0:1.0: USB hub found                                                                                                      
[    1.760867] hub 1-0:1.0: 8 ports detected                                                                                                   
[    1.761078] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver                                                                          
[    1.761185] uhci_hcd: USB Universal Host Controller Interface driver                                                                        
[    1.761323] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                               
[    1.761403] uhci_hcd 0000:00:1d.0: setting latency timer to 64                                                                              
[    1.761411] uhci_hcd 0000:00:1d.0: UHCI Host Controller                                                                                     
[    1.761555] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2                                                            
[    1.761680] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000050a0                                                                               
[    1.761915] usb usb2: configuration #1 chosen from 1 choice                                                                                 
[    1.762041] hub 2-0:1.0: USB hub found                                                                                                      
[    1.762113] hub 2-0:1.0: 2 ports detected                                                                                                   
[    1.762277] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17                                                               
[    1.762356] uhci_hcd 0000:00:1d.1: setting latency timer to 64                                                                              
[    1.762364] uhci_hcd 0000:00:1d.1: UHCI Host Controller                                                                                     
[    1.762504] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3                                                            
[    1.762641] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00005080                                                                               
[    1.762874] usb usb3: configuration #1 chosen from 1 choice                                                                                 
[    1.763005] hub 3-0:1.0: USB hub found                                                                                                      
[    1.763078] hub 3-0:1.0: 2 ports detected                                                                                                   
[    1.763229] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18                                                               
[    1.763307] uhci_hcd 0000:00:1d.2: setting latency timer to 64                                                                              
[    1.763315] uhci_hcd 0000:00:1d.2: UHCI Host Controller                                                                                     
[    1.763452] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4                                                            
[    1.763582] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00005060                                                                               
[    1.763813] usb usb4: configuration #1 chosen from 1 choice                                                                                 
[    1.763942] hub 4-0:1.0: USB hub found                                                                                                      
[    1.764047] hub 4-0:1.0: 2 ports detected                                                                                                   
[    1.764200]   alloc irq_desc for 19 on node -1                                                                                              
[    1.764206]   alloc kstat_irqs on node -1                                                                                                   
[    1.764218] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19                                                               
[    1.764297] uhci_hcd 0000:00:1d.3: setting latency timer to 64                                                                              
[    1.764304] uhci_hcd 0000:00:1d.3: UHCI Host Controller                                                                                     
[    1.764434] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5                                                            
[    1.764566] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00005040                                                                               
[    1.764803] usb usb5: configuration #1 chosen from 1 choice                                                                                 
[    1.764927] hub 5-0:1.0: USB hub found                                                                                                      
[    1.765000] hub 5-0:1.0: 2 ports detected                                                                                                   
[    1.765270] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12                                                          
[    1.789784] serio: i8042 KBD port at 0x60,0x64 irq 1                                                                                        
[    1.789860] serio: i8042 AUX port at 0x60,0x64 irq 12                                                                                       
[    1.790093] mice: PS/2 mouse device common for all mice                                                                                     
[    1.790435] rtc_cmos 00:03: RTC can wake from S4                                                                                            
[    1.790577] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0                                                                           
[    1.790684] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs                                                                        
[    1.790992] device-mapper: uevent: version 1.0.3                                                                                            
[    1.791287] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]                                                
[    1.791571] device-mapper: multipath: version 1.1.0 loaded                                                                                  
[    1.791640] device-mapper: multipath round-robin: version 1.0.0 loaded                                                                      
[    1.792001] EISA: Probing bus 0 at eisa.0                                                                                                   
[    1.792097] Cannot allocate resource for EISA slot 1                                                                                        
[    1.792163] Cannot allocate resource for EISA slot 2                                                                                        
[    1.792229] Cannot allocate resource for EISA slot 3                                                                                        
[    1.792293] Cannot allocate resource for EISA slot 4                                                                                        
[    1.792358] Cannot allocate resource for EISA slot 5                                                                                        
[    1.792442] EISA: Detected 0 cards.                                                                                                         
[    1.792953] cpuidle: using governor ladder                                                                                                  
[    1.793221] cpuidle: using governor menu                                                                                                    
[    1.794406] TCP cubic registered                                                                                                            
[    1.794839] NET: Registered protocol family 10                                                                                              
[    1.795886] lo: Disabled Privacy Extensions                                                                                                 
[    1.796682] NET: Registered protocol family 17                                                                                              
[    1.796805] Bluetooth: L2CAP ver 2.13                                                                                                       
[    1.796877] Bluetooth: L2CAP socket layer initialized                                                                                       
[    1.796946] Bluetooth: SCO (Voice Link) ver 0.6                                                                                             
[    1.797013] Bluetooth: SCO socket layer initialized                                                                                         
[    1.797200] Bluetooth: RFCOMM TTY layer initialized                                                                                         
[    1.797282] Bluetooth: RFCOMM socket layer initialized                                                                                      
[    1.797357] Bluetooth: RFCOMM ver 1.11                                                                                                      
[    1.799168] Using IPI No-Shortcut mode                                                                                                      
[    1.799390] PM: Resume from disk failed.                                                                                                    
[    1.799417] registered taskstats version 1                                                                                                  
[    1.799737]   Magic number: 5:841:674                                                                                                       
[    1.799922] rtc_cmos 00:03: setting system clock to 2009-12-11 08:41:04 UTC (1260520864)                                                    
[    1.800039] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found                                                                            
[    1.800106] EDD information not available.                                                                                                  
[    1.810012] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5                                              
[    2.053105] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)                                                                          
[    2.054589] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out                                                                             
[    2.054870] ata1.00: ATA-8: Hitachi HTS543216L9A300, FB2OC40C, max UDMA/133                                                                 
[    2.054957] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)                                                                   
[    2.056668] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out                                                                             
[    2.057019] ata1.00: configured for UDMA/133                                                                                                
[    2.072110] usb 1-2: new high speed USB device using ehci_hcd and address 2                                                                 
[    2.072517] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54321 FB2O PQ: 0 ANSI: 5                                                    
[    2.072913] sd 0:0:0:0: Attached scsi generic sg0 type 0                                                                                    
[    2.073140] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)                                                           
[    2.074442] sd 0:0:0:0: [sda] Write Protect is off                                                                                          
[    2.074510] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                                                                                       
[    2.074583] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                         
[    2.075027]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 >                                                                               
[    2.152183] sd 0:0:0:0: [sda] Attached SCSI disk                                                                                            
[    2.241900] usb 1-2: configuration #1 chosen from 1 choice                                                                                  
[    2.392093] ata3: SATA link down (SStatus 0 SControl 300)                                                                                   
[    2.408379] Freeing unused kernel memory: 544k freed                                                                                        
[    2.408984] Write protecting the kernel text: 4592k                                                                                         
[    2.409249] Write protecting the kernel read-only data: 1836k                                                                               
[    2.741596] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function                                                              
[    2.742298] acpi device:1a: registered as cooling_device3                                                                                   
[    2.742770] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:16/input/input6                                            
[    2.742956] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes  post: no)                                                                 
[    2.874840] Linux agpgart interface v0.103                                                                                                  
[    2.929257] agpgart-intel 0000:00:00.0: Intel 945GME Chipset                                                                                
[    2.929726] agpgart-intel 0000:00:00.0: detected 7932K stolen memory                                                                        
[    2.932791] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000                                                                   
[    2.983140] [drm] Initialized drm 1.1.0 20060810                                                                                            
[    3.029129] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                                   
[    3.029222] i915 0000:00:02.0: setting latency timer to 64                                                                                  
[    3.260304] [drm] fb0: inteldrmfb frame buffer device                                                                                       
[    3.260386] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0                                                               
[    3.587698] [drm] LVDS-8: set mode 1024x600 e                                                                                               
[    4.006732] Console: switching to colour frame buffer device 128x37                                                                         
[    4.362383] xor: automatically using best checksumming function: pIII_sse                                                                   
[    4.380018]    pIII_sse  :  4782.000 MB/sec                                                                                                 
[    4.380026] xor: using function: pIII_sse (4782.000 MB/sec)                                                                                 
[    4.386463] device-mapper: dm-raid45: initialized v0.2594b                                                                                  
[    9.959339] EXT4-fs (sda6): barriers enabled                                                                                                
[    9.972100] kjournald2 starting: pid 428, dev sda6:8, commit interval 5 seconds                                                             
[    9.972149] EXT4-fs (sda6): delayed allocation enabled                                                                                      
[    9.972165] EXT4-fs: file extents enabled                                                                                                   
[    9.985067] EXT4-fs: mballoc enabled                                                                                                        
[    9.985100] EXT4-fs (sda6): mounted filesystem with ordered data mode                                                                       
[   10.762081] type=1505 audit(1260520873.460:2): operation="profile_load" pid=454 name=/sbin/dhclient3                                        
[   10.762666] type=1505 audit(1260520873.460:3): operation="profile_load" pid=454 name=/usr/lib/NetworkManager/nm-dhcp-client.action          
[   10.763004] type=1505 audit(1260520873.460:4): operation="profile_load" pid=454 name=/usr/lib/connman/scripts/dhclient-script               
[   10.809698] type=1505 audit(1260520873.508:5): operation="profile_load" pid=455 name=/usr/bin/evince                                        
[   10.819006] type=1505 audit(1260520873.516:6): operation="profile_load" pid=455 name=/usr/bin/evince-previewer                              
[   10.824762] type=1505 audit(1260520873.524:7): operation="profile_load" pid=455 name=/usr/bin/evince-thumbnailer                            
[   10.852003] type=1505 audit(1260520873.548:8): operation="profile_load" pid=457 name=/usr/lib/cups/backend/cups-pdf                         
[   10.852807] type=1505 audit(1260520873.552:9): operation="profile_load" pid=457 name=/usr/sbin/cupsd                                        
[   10.881447] type=1505 audit(1260520873.580:10): operation="profile_load" pid=458 name=/usr/sbin/mysqld-akonadi                              
[   10.885426] type=1505 audit(1260520873.584:11): operation="profile_load" pid=459 name=/usr/sbin/tcpdump                                     
[   20.241185] Adding 4096532k swap on /dev/sda7.  Priority:-1 extents:1 across:4096532k                                                       
[   20.264452] udev: starting version 147                                                                                                      
[   20.325062] lp: driver loaded but no devices found                                                                                          
[   20.400726] EXT4-fs (sda6): internal journal on sda6:8                                                                                      
[   20.940343] atl1c 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18                                                                  
[   20.940371] atl1c 0000:03:00.0: setting latency timer to 64                                                                                 
[   20.940477] atl1c 0000:03:00.0: PME# disabled                                                                                               
[   20.940492] atl1c 0000:03:00.0: PME# disabled                                                                                               
[   21.040087] atl1c 0000:03:00.0: version 1.0.0.1-NAPI                                                                                        
[   21.045566] cfg80211: Calling CRDA to update world regulatory domain                                                                        
[   21.045664] intel_rng: FWH not detected                                                                                                     
[   21.136227] cfg80211: World regulatory domain updated:                                                                                      
[   21.136239]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)                                                              
[   21.136250]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)                                                                   
[   21.136259]  (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)                                                                   
[   21.136268]  (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)                                                                   
[   21.136278]  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)                                                                   
[   21.136287]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)                                                                   
[   21.161428] Linux video capture interface: v2.00                                                                                            
[   21.195091] uvcvideo: Found UVC 1.00 device WebCam (0c45:62c0)                                                                              
[   21.195297] acer-wmi: Acer Laptop ACPI-WMI Extras                                                                                           
[   21.241479] input: WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input7                                                 
[   21.241617] usbcore: registered new interface driver uvcvideo                                                                               
[   21.241628] USB Video Class driver (v0.1.0)                                                                                                 
[   21.323403] ath5k 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                                  
[   21.323429] ath5k 0000:01:00.0: setting latency timer to 64                                                                                 
[   21.323519] ath5k 0000:01:00.0: registered as 'phy0'                                                                                        
[   21.426568] acer-wmi: Unable to detect available WMID devices                                                                               
[   21.612542] ath: EEPROM regdomain: 0x65                                                                                                     
[   21.612552] ath: EEPROM indicates we should expect a direct regpair map                                                                     
[   21.612563] ath: Country alpha2 being used: 00                                                                                              
[   21.612569] ath: Regpair used: 0x65                                                                                                         
[   21.680222] ip_tables: (C) 2000-2006 Netfilter Core Team                                                                                    
[   21.778088] phy0: Selected rate control algorithm 'minstrel'                                                                                
[   21.780252] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)                                                                    
[   22.013748] ADDRCONF(NETDEV_UP): wlan0: link is not ready                                                                                   
[   22.019770]   alloc irq_desc for 28 on node -1                                                                                              
[   22.019781]   alloc kstat_irqs on node -1                                                                                                   
[   22.019813] atl1c 0000:03:00.0: irq 28 for MSI/MSI-X                                                                                        
[   22.020683] ADDRCONF(NETDEV_UP): eth0: link is not ready                                                                                    
[   22.173368] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                              
[   22.173463]   alloc irq_desc for 29 on node -1                                                                                              
[   22.173470]   alloc kstat_irqs on node -1                                                                                                   
[   22.173495] HDA Intel 0000:00:1b.0: irq 29 for MSI/MSI-X                                                                                    
[   22.173555] HDA Intel 0000:00:1b.0: setting latency timer to 64                                                                             
[   22.354512] hda_codec: ALC272: BIOS auto-probing.                                                                                           
[   22.355782] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8                                                      
[   22.424203] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04771/0xa40000                                                     
[   22.529542] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9                                                
[   22.771878] type=1505 audit(1260538885.468:12): operation="profile_replace" pid=1060 name=/sbin/dhclient3                                   
[   22.772764] type=1505 audit(1260538885.472:13): operation="profile_replace" pid=1060 name=/usr/lib/NetworkManager/nm-dhcp-client.action     
[   22.773357] type=1505 audit(1260538885.472:14): operation="profile_replace" pid=1060 name=/usr/lib/connman/scripts/dhclient-script          
[   22.787259] type=1505 audit(1260538885.484:15): operation="profile_replace" pid=1062 name=/usr/bin/evince                                   
[   22.801651] type=1505 audit(1260538885.500:16): operation="profile_replace" pid=1062 name=/usr/bin/evince-previewer                         
[   22.837599] type=1505 audit(1260538885.536:17): operation="profile_replace" pid=1062 name=/usr/bin/evince-thumbnailer                       
[   22.861741] type=1505 audit(1260538885.560:18): operation="profile_replace" pid=1069 name=/usr/lib/cups/backend/cups-pdf                    
[   22.862785] type=1505 audit(1260538885.560:19): operation="profile_replace" pid=1069 name=/usr/sbin/cupsd                                   
[   22.874428] type=1505 audit(1260538885.572:20): operation="profile_replace" pid=1073 name=/usr/sbin/mysqld-akonadi                          
[   22.879210] type=1505 audit(1260538885.576:21): operation="profile_replace" pid=1077 name=/usr/sbin/tcpdump                                 
[   24.306177] ppdev: user-space parallel port driver                                                                                          
[   25.930315] CPU0 attaching NULL sched-domain.                                                                                               
[   25.930332] CPU1 attaching NULL sched-domain.                                                                                               
[   25.945280] CPU0 attaching sched-domain:                                                                                                    
[   25.945292]  domain 0: span 0-1 level SIBLING                                                                                               
[   25.945302]   groups: 0 1                                                                                                                   
[   25.945318] CPU1 attaching sched-domain:                                                                                                    
[   25.945326]  domain 0: span 0-1 level SIBLING                                                                                               
[   25.945334]   groups: 1 0                                                                                                                   
[   36.233268] CPU0 attaching NULL sched-domain.                                                                                               
[   36.233279] CPU1 attaching NULL sched-domain.                                                                                               
[   36.248219] CPU0 attaching sched-domain:                                                                                                    
[   36.248235]  domain 0: span 0-1 level SIBLING                                                                                               
[   36.248249]   groups: 0 1                                                                                                                   
[   36.248271] CPU1 attaching sched-domain:                                                                                                    
[   36.248281]  domain 0: span 0-1 level SIBLING                                                                                               
[   36.248292]   groups: 1 0                                                                                                                   
[   70.609365] wlan0: authenticate with AP 00:1e:58:27:67:43                                                                                   
[   70.611290] wlan0: authenticated                                                                                                            
[   70.611301] wlan0: associate with AP 00:1e:58:27:67:43                                                                                      
[   70.613622] wlan0: RX AssocResp from 00:1e:58:27:67:43 (capab=0x421 status=0 aid=3)                                                         
[   70.613634] wlan0: associated                                                                                                               
[   70.618659] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready                                                                              
[   81.108051] wlan0: no IPv6 routers present                                                                                                  
[   98.048181] usb 1-4: new high speed USB device using ehci_hcd and address 3                                                                 
[   98.194771] usb 1-4: configuration #1 chosen from 1 choice                                                                                  
[   99.496127] usb 1-4: reset high speed USB device using ehci_hcd and address 3                                                               
[   99.732567] Initializing USB Mass Storage driver...                                                                                         
[   99.736065] scsi6 : SCSI emulation for USB Mass Storage devices                                                                             
[   99.736578] usbcore: registered new interface driver usb-storage                                                                            
[   99.736592] USB Mass Storage support registered.                                                                                            
[   99.736960] usb-storage: device found at 3                                                                                                  
[   99.736968] usb-storage: waiting for device to settle before scanning                                                                       
[  104.733143] usb-storage: device scan complete                                                                                               
[  104.734385] scsi 6:0:0:0: Direct-Access     RIM      BlackBerry SD    0003 PQ: 0 ANSI: 4 CCS                                                
[  104.736167] sd 6:0:0:0: Attached scsi generic sg1 type 0                                                                                    
[  104.762239] sd 6:0:0:0: [sdb] Attached SCSI removable disk                                                                                  
[  105.825169] sd 6:0:0:0: [sdb] 1989632 512-byte logical blocks: (1.01 GB/971 MiB)                                                            
[  105.826369] sd 6:0:0:0: [sdb] Assuming drive cache: write through                                                                           
[  105.831132] sd 6:0:0:0: [sdb] Assuming drive cache: write through                                                                           
[  105.831152]  sdb: sdb1                                                                                                                      
[  211.975484] sd 6:0:0:0: [sdb] 1989632 512-byte logical blocks: (1.01 GB/971 MiB)                                                            
[  211.976823] sd 6:0:0:0: [sdb] Assuming drive cache: write through                                                                           
[  212.003476] sd 6:0:0:0: [sdb] Assuming drive cache: write through                                                                           
[  212.003499]  sdb: sdb1                                                                                                                      
[  256.557152] usb 1-4: usbfs: interface 1 claimed by usb-storage while 'bcharge' sets config #1                                               
[  257.696114] usb 1-4: reset high speed USB device using ehci_hcd and address 3                                                               
[  492.359152] usb 1-4: USB disconnect, address 3                                                                                              
[ 1474.876232] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled                                   
[ 1474.884494] SGI XFS Quota Management subsystem                                                                                              
[ 1475.000449] JFS: nTxBlock = 7943, nTxLock = 63547                                                                                           
[ 1475.088807] NTFS driver 2.1.29 [Flags: R/O MODULE].                                                                                         
[ 1475.184660] QNX4 filesystem 0.2.3 registered.                                                                                               
[ 1477.679967] EXT4-fs (sda3): barriers enabled                                                                                                
[ 1477.693254] kjournald2 starting: pid 3033, dev sda3:8, commit interval 5 seconds                                                            
[ 1477.693301] EXT4-fs (sda3): delayed allocation enabled                                                                                      
[ 1477.693311] EXT4-fs: file extents enabled                                                                                                   
[ 1477.707411] EXT4-fs: mballoc enabled                                                                                                        
[ 1477.707481] EXT4-fs (sda3): mounted filesystem with ordered data mode                                                                       
[ 1478.024897] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)                                                                                   
[ 1478.024908] EXT4-fs: mballoc: 0 extents scanned, 0 goal hits, 0 2^N hits, 0 breaks, 0 lost                                                  
[ 1478.024916] EXT4-fs: mballoc: 0 generated and it took 0                                                                                     
[ 1478.024921] EXT4-fs: mballoc: 0 preallocated, 0 discarded                                                                                   
[ 1479.036491] kjournald starting.  Commit interval 5 seconds                                                                                  
[ 1479.036581] EXT3-fs: mounted filesystem with writeback data mode.                                                                           
[ 1481.933231] EXT4-fs (sda3): barriers enabled                                                                                                
[ 1481.948478] kjournald2 starting: pid 3317, dev sda3:8, commit interval 5 seconds                                                            
[ 1481.948556] EXT4-fs (sda3): delayed allocation enabled                                                                                      
[ 1481.948577] EXT4-fs: file extents enabled                                                                                                   
[ 1481.970887] EXT4-fs: mballoc enabled                                                                                                        
[ 1481.970925] EXT4-fs (sda3): mounted filesystem with ordered data mode                                                                       
[ 1483.589185] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)                                                                                   
[ 1483.589194] EXT4-fs: mballoc: 0 extents scanned, 0 goal hits, 0 2^N hits, 0 breaks, 0 lost                                                  
[ 1483.589201] EXT4-fs: mballoc: 0 generated and it took 0                                                                                     
[ 1483.589205] EXT4-fs: mballoc: 0 preallocated, 0 discarded                                                                                   
[ 1486.113254] kjournald starting.  Commit interval 5 seconds                                                                                  
[ 1486.113287] EXT3-fs: mounted filesystem with writeback data mode.                                                                           
[ 1529.532084] EXT4-fs (sda3): barriers enabled                                                                                                
[ 1529.547297] kjournald2 starting: pid 4363, dev sda3:8, commit interval 5 seconds                                                            
[ 1529.547351] EXT4-fs (sda3): delayed allocation enabled                                                                                      
[ 1529.547367] EXT4-fs: file extents enabled                                                                                                   
[ 1529.556392] EXT4-fs: mballoc enabled                                                                                                        
[ 1529.556431] EXT4-fs (sda3): mounted filesystem with ordered data mode                                                                       
[ 1529.815905] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)                                                                                   
[ 1529.815916] EXT4-fs: mballoc: 0 extents scanned, 0 goal hits, 0 2^N hits, 0 breaks, 0 lost                                                  
[ 1529.815922] EXT4-fs: mballoc: 0 generated and it took 0                                                                                     
[ 1529.815926] EXT4-fs: mballoc: 0 preallocated, 0 discarded                                                                                   
[ 1530.597755] kjournald starting.  Commit interval 5 seconds                                                                                  
[ 1530.597792] EXT3-fs: mounted filesystem with writeback data mode.                                                                           
[ 1533.587463] EXT4-fs (sda3): barriers enabled                                                                                                
[ 1533.602773] kjournald2 starting: pid 4646, dev sda3:8, commit interval 5 seconds                                                            
[ 1533.602828] EXT4-fs (sda3): delayed allocation enabled                                                                                      
[ 1533.602845] EXT4-fs: file extents enabled                                                                                                   
[ 1533.618743] EXT4-fs: mballoc enabled                                                                                                        
[ 1533.618784] EXT4-fs (sda3): mounted filesystem with ordered data mode                                                                       
[ 1535.097653] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)                                                                                   
[ 1535.097663] EXT4-fs: mballoc: 0 extents scanned, 0 goal hits, 0 2^N hits, 0 breaks, 0 lost                                                  
[ 1535.097669] EXT4-fs: mballoc: 0 generated and it took 0                                                                                     
[ 1535.097674] EXT4-fs: mballoc: 0 preallocated, 0 discarded                                                                                   
[ 1536.946327] kjournald starting.  Commit interval 5 seconds                                                                                  
[ 1536.946371] EXT3-fs: mounted filesystem with writeback data mode.                                                                           
[ 1680.629222] EXT4-fs (sda3): barriers enabled                                                                                                
[ 1680.648750] kjournald2 starting: pid 9979, dev sda3:8, commit interval 5 seconds                                                            
[ 1680.648808] EXT4-fs (sda3): delayed allocation enabled                                                                                      
[ 1680.648819] EXT4-fs: file extents enabled                                                                                                   
[ 1680.658088] EXT4-fs: mballoc enabled                                                                                                        
[ 1680.658128] EXT4-fs (sda3): mounted filesystem with ordered data mode                                                                       
[ 1680.920426] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)                                                                                   
[ 1680.920436] EXT4-fs: mballoc: 0 extents scanned, 0 goal hits, 0 2^N hits, 0 breaks, 0 lost                                                  
[ 1680.920442] EXT4-fs: mballoc: 0 generated and it took 0                                                                                     
[ 1680.920447] EXT4-fs: mballoc: 0 preallocated, 0 discarded                                                                                   
[ 1681.695906] kjournald starting.  Commit interval 5 seconds                                                                                  
[ 1681.695954] EXT3-fs: mounted filesystem with writeback data mode.                                                                           
[ 1684.796156] EXT4-fs (sda3): barriers enabled                                                                                                
[ 1684.815808] kjournald2 starting: pid 10262, dev sda3:8, commit interval 5 seconds                                                           
[ 1684.815855] EXT4-fs (sda3): delayed allocation enabled                                                                                      
[ 1684.815865] EXT4-fs: file extents enabled                                                                                                   
[ 1684.826246] EXT4-fs: mballoc enabled                                                                                                        
[ 1684.826303] EXT4-fs (sda3): mounted filesystem with ordered data mode                                                                       
[ 1686.341571] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)                                                                                   
[ 1686.341580] EXT4-fs: mballoc: 0 extents scanned, 0 goal hits, 0 2^N hits, 0 breaks, 0 lost                                                  
[ 1686.341587] EXT4-fs: mballoc: 0 generated and it took 0                                                                                     
[ 1686.341591] EXT4-fs: mballoc: 0 preallocated, 0 discarded                                                                                   
[ 1689.276182] kjournald starting.  Commit interval 5 seconds                                                                                  
[ 1689.276220] EXT3-fs: mounted filesystem with writeback data mode.                                                                           
[ 1742.682309] EXT4-fs (sda3): barriers enabled                                                                                                
[ 1742.753253] kjournald2 starting: pid 15230, dev sda3:8, commit interval 5 seconds                                                           
[ 1742.753328] EXT4-fs (sda3): delayed allocation enabled                                                                                      
[ 1742.753338] EXT4-fs: file extents enabled                                                                                                   
[ 1742.762283] EXT4-fs: mballoc enabled                                                                                                        
[ 1742.762323] EXT4-fs (sda3): mounted filesystem with ordered data mode                                                                       
[ 1743.070397] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)                                                                                   
[ 1743.070407] EXT4-fs: mballoc: 0 extents scanned, 0 goal hits, 0 2^N hits, 0 breaks, 0 lost                                                  
[ 1743.070413] EXT4-fs: mballoc: 0 generated and it took 0                                                                                     
[ 1743.070418] EXT4-fs: mballoc: 0 preallocated, 0 discarded                                                                                   
[ 1743.872371] kjournald starting.  Commit interval 5 seconds                                                                                  
[ 1743.872435] EXT3-fs: mounted filesystem with writeback data mode.                                                                           
[ 1747.315494] EXT4-fs (sda3): barriers enabled                                                                                                
[ 1747.330825] kjournald2 starting: pid 15514, dev sda3:8, commit interval 5 seconds                                                           
[ 1747.330874] EXT4-fs (sda3): delayed allocation enabled                                                                                      
[ 1747.330886] EXT4-fs: file extents enabled                                                                                                   
[ 1747.343726] EXT4-fs: mballoc enabled                                                                                                        
[ 1747.343779] EXT4-fs (sda3): mounted filesystem with ordered data mode                                                                       
[ 1748.854038] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)                                                                                   
[ 1748.854048] EXT4-fs: mballoc: 0 extents scanned, 0 goal hits, 0 2^N hits, 0 breaks, 0 lost                                                  
[ 1748.854054] EXT4-fs: mballoc: 0 generated and it took 0
[ 1748.854059] EXT4-fs: mballoc: 0 preallocated, 0 discarded
[ 1751.394268] kjournald starting.  Commit interval 5 seconds
[ 1751.394323] EXT3-fs: mounted filesystem with writeback data mode.
[ 2086.477448] CPU0 attaching NULL sched-domain.
[ 2086.477468] CPU1 attaching NULL sched-domain.
[ 2086.496207] CPU0 attaching sched-domain:
[ 2086.496223]  domain 0: span 0-1 level SIBLING
[ 2086.496237]   groups: 0 1
[ 2086.496255]   domain 1: span 0-1 level MC
[ 2086.496267]    groups: 0-1 (__cpu_power = 2048)
[ 2086.496288] CPU1 attaching sched-domain:
[ 2086.496298]  domain 0: span 0-1 level SIBLING
[ 2086.496309]   groups: 1 0
[ 2086.496325]   domain 1: span 0-1 level MC
[ 2086.496336]    groups: 0-1 (__cpu_power = 2048)
[ 2240.956112] CPU0 attaching NULL sched-domain.
[ 2240.956123] CPU1 attaching NULL sched-domain.
[ 2240.969227] CPU0 attaching sched-domain:
[ 2240.969243]  domain 0: span 0-1 level SIBLING
[ 2240.969256]   groups: 0 1
[ 2240.969277] CPU1 attaching sched-domain:
[ 2240.969287]  domain 0: span 0-1 level SIBLING
[ 2240.969299]   groups: 1 0
[ 2337.288567] usb 1-4: new high speed USB device using ehci_hcd and address 4
[ 2337.435745] usb 1-4: configuration #1 chosen from 1 choice
[ 2337.448281] scsi7 : SCSI emulation for USB Mass Storage devices
[ 2337.448720] usb-storage: device found at 4
[ 2337.448727] usb-storage: waiting for device to settle before scanning
[ 2337.672952] usb 1-4: usbfs: interface 1 claimed by usb-storage while 'bcharge' sets config #1
[ 2338.784111] usb 1-4: reset high speed USB device using ehci_hcd and address 4
genius@K-Netbook:~/Downloads/bbtether/bbtether$

---

### Post by shellehs on 2009-12-11
8800 china mobile
use t-mobile 
looks fine

---

### Post by iamgeniusrnti on 2009-12-11
I think Sprint did something to stop this.  I give.

---

### Post by PaulReaver on 2009-12-11
> **iamgeniusrnti said:**
> 
[ 2337.448281] scsi7 : SCSI emulation for USB Mass Storage devices
[ 2337.448720] usb-storage: device found at 4
[ 2337.448727] usb-storage: waiting for device to settle before scanning
[ 2337.672952] usb 1-4: usbfs: interface 1 claimed by usb-storage while 'bcharge' sets config #1

have you got any usb memory sticks plugged in?
if not there is a mass storage device in the berry.  you'll need to rmmod usbstorage for the berry only

> **iamgeniusrnti said:**
>  2337.672952] usb 1-4: usbfs: interface 1 claimed by usb-storage while 'bcharge' sets config #1

easier just to buy a bluetooth dongle for newbies.

---

### Post by iamgeniusrnti on 2009-12-11
> **PaulReaver said:**
> have you got any usb memory sticks plugged in?
if not there is a mass storage device in the berry.  you'll need to rmmod usbstorage for the berry only



easier just to buy a bluetooth dongle for newbies.

I did catch that--the thing that bugs me is that it talks to the blackberry and actually takes control of it as a modem and puts it in modem mode.  I can actually watch my phone screen and see it going into modem mode.

---

### Post by PaulReaver on 2009-12-11
has anyone here had success with wvdial and wvdialconf?

---

### Post by cu_ on 2012-08-07
It is not working with "torch" under verizon-us.  Both Berry4All and barry give bulk_read time outs.  
Any ideas?

---

### Post by wildmanne39 on 2012-08-07
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

