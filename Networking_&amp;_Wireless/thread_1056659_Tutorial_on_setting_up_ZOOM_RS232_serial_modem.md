---
title: "Tutorial on setting up ZOOM RS232 serial modem"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by vamper on 2009-02-01
I have a ZOOM rs232 serial cable modem and I guess my first question even before loacting a tutorial on it's setup is do I need a straight through or twisty 25 pin serial cable, perhaps my problem is I am using a straight through cable, there was some small discussion on this subject on a non Linux site, but it was very vauge - other than that a good read on setting up my external modem since it is damn near impossible to set up a pci modem at least for me - LOL
It is a ZOOM (non rockwell) rs232 serial cable 56k dual mode fax/modem.

---

### Post by ModelM on 2009-02-01
Connect the modem.

In a terminal type:

sudo wvdialconf

In the same terminal type:

sudo gedit /etc/wvdial.conf

This last command will bring up the wvdial config file in an editor where you can edit your username & password.

Save after editing then, in a terminal, type:

sudo wvdial

Your modem should dial & connect.

Don't worry about the cable - you have the correct one.

---

### Post by vamper on 2009-02-01
Ok thanks man will try this - and thanks for the input on the cable , some folks have said that it has to be twisty type serial cable, all I have here is straight through type for other projects - I will let you know the out come

---

### Post by vamper on 2009-02-02
Ok this is the reply I got 

[COLOR="Navy"][COLOR="DarkRed"]hell@hell-desktop:~$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<Info>: Device or resource busy
Modem Port Scan<*1>: S0   
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS3<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS3<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS3<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
hell@hell-desktop:~$[/COLOR] [/COLOR]

So I guess before a next step my question is do I use a serial cable 25 pin by 25 pin or do I need to use a db9 pin by 25 pin cable ( I do not have an instruction manual and failed to google the correct one), I know the wvdial configuration is saying it is scanning the serial ports, but I am not sure since it is my first attempt with a linux o/s, I am using a copy of Ubuntu 8.0.4.2 i386 build-32 bit version, and have learned not to use the 64 bit version for ppp connections, I figure I am on some what of a correct path here as this old modem has the light for computer sending data to the modem via the cable lights up along with the light for clear to send more data from the computer to the modem and the modem ready(powerlight) are all on. I tried to get the set serial to run but do not have all the command lines to input in the terminal window.

Thank you for your time with me here, I am very familiar with using serial and com cables for communication with other types of devices but this is my first attempt with an Linux, or this used ext.modem

---

### Post by ieee488 on 2009-02-02
The modem didn't come with it's own cable?

On newer PCs that have serial ports, the connector is a 9-pin. It has been quite some time since I have seen a PC with a 25-pin connector serial port.
I believe the cable should be a straight-through.

---

### Post by ModelM on 2009-02-02
How many serial devices do you have connected to the computer, not including the modem? If the answer is no other devices, do this:

Have a look in the directory /var/lock for a filename like this:

LCK..ttyS0


If you find one, delete it (you'll need to be root)

sudo rm /var/lock/LCK..ttyS0

and then try wvdialconf again.

I think your modem is connected to /dev/ttyS0. There is an old lock file laying around from one of your attempts, wvdialconf saw that lock file, assumed that ttyS0 was in use and skipped it.

---

### Post by vamper on 2009-02-03
> **ieee488 said:**
> The modem didn't come with it's own cable?

On newer PCs that have serial ports, the connector is a 9-pin. It has been quite some time since I have seen a PC with a 25-pin connector serial port.
I believe the cable should be a straight-through.Sorry it did not come with it's own cable, this is a newer mother board, MSI-K9VGM-V, about 3-4 years old and it has 25 and 9 pin , I have some belkin 9 pin by 25 pin cables also, that may be the solution. 
Thank you for your reply and suggestions

> **ModelM said:**
> How many serial devices do you have connected to the computer, not including the modem? If the answer is no other devices, do this:

Have a look in the directory /var/lock for a filename like this:

LCK..ttyS0


If you find one, delete it (you'll need to be root)

sudo rm /var/lock/LCK..ttyS0

and then try wvdialconf again.

I think your modem is connected to /dev/ttyS0. There is an old lock file laying around from one of your attempts, wvdialconf saw that lock file, assumed that ttyS0 was in use and skipped it. this will be the first thing I try then, I will substitute the cable and try this again.

Thank you for the reply and suggestions

---

### Post by vamper on 2009-02-03
Ok I went to the directory /var/lock and found a file named LCK..ttyS0 and deleted it.

Then I replaced the 25 pin straight trough with a 9 pin by 25 pin cable and then open up the terminal again

[COLOR="Red"]hell@hell-desktop:~$ wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

WvModem<*1>: Cannot set information for serial port.
ttyS0<*1>: ATQ0 V1 E1 -- OK
ttyS0<*1>: ATQ0 V1 E1 Z -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS0<*1>: Modem Identifier: ATI -- Zoom V.90 Serial s052099g -I Z207
ttyS0<*1>: Speed 4800: AT -- OK
ttyS0<*1>: Speed 9600: AT -- OK
ttyS0<*1>: Speed 19200: AT -- OK
ttyS0<*1>: Speed 38400: AT -- OK
ttyS0<*1>: Speed 57600: AT -- OK
ttyS0<*1>: Speed 115200: AT -- OK
ttyS0<*1>: Max speed is 115200; that should be safe.
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot set information for serial port.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot set information for serial port.
ttyS2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot set information for serial port.
ttyS3<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS3<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS3<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

Found a modem on /dev/ttyS0.
Modem configuration written to /etc/wvdial.conf.
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf.tmp6356': Permission denied
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf' ('/etc/wvdial.conf'): Bad file descriptor
ttyS0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
hell@hell-desktop:~$ 
[/COLOR]

Now as you can see I get that <warn> message can't write '/etc/wvdial.conf' : Bad File descriptor

I am not sure what that means so after a bit more reading on this subject I tried to log in as 'root', but am not sure what the pass word is for root log in I tried my own password and it didn't work, and also tried login with no password and still wrong password.
But as you can see it did pick up the modem, I restarted the computer and logged in using windows so I could get to the net, and windows xp picked up the modem immediately, I installed the win 32 software I had for it and am using it to write this message so I know it works.
If you can shed some light on the above <warn> message or perhaps how to log in as 'Root', it may help me get this modem to work on what is becoming my favorite O/S - :D

---

### Post by ModelM on 2009-02-03
Try:

sudo wvdialconf

---

### Post by vamper on 2009-02-03
[B][I][COLOR="Red"]hell@hell-desktop:~$ wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- OK
ttyS0<*1>: ATQ0 V1 E1 Z -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS0<*1>: Modem Identifier: ATI -- Zoom V.90 Serial s052099g -I Z207
ttyS0<*1>: Speed 4800: AT -- OK
ttyS0<*1>: Speed 9600: AT -- OK
ttyS0<*1>: Speed 19200: AT -- OK
ttyS0<*1>: Speed 38400: AT -- OK
ttyS0<*1>: Speed 57600: AT -- OK
ttyS0<*1>: Speed 115200: AT -- OK
ttyS0<*1>: Max speed is 115200; that should be safe.
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS3<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS3<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS3<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

Found a modem on /dev/ttyS0.
Modem configuration written to /etc/wvdial.conf.
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf.tmp6808': Permission denied
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf' ('/etc/wvdial.conf'): Bad file descriptor
ttyS0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
hell@hell-desktop:~$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- OK
ttyS0<*1>: ATQ0 V1 E1 Z -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS0<*1>: Modem Identifier: ATI -- Zoom V.90 Serial s052099g -I Z207
ttyS0<*1>: Speed 4800: AT -- OK
ttyS0<*1>: Speed 9600: AT -- OK
ttyS0<*1>: Speed 19200: AT -- OK
ttyS0<*1>: Speed 38400: AT -- OK
ttyS0<*1>: Speed 57600: AT -- OK
ttyS0<*1>: Speed 115200: AT -- OK
ttyS0<*1>: Max speed is 115200; that should be safe.
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS3<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS3<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS3<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

Found a modem on /dev/ttyS0.
Modem configuration written to /etc/wvdial.conf.
ttyS0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
hell@hell-desktop:~$ 
[/COLOR][/I][/B]
Now when I try to connect it activates the lights on the modem just for a second then they go out again and connections fails, I have the telephone number, user name and password correct,along with the modem location which is set to ttySO, I have left the prefix space blank where the telephone number and user name go  in the modem properties panel, but it just won't complete the connection.
At least it is getting closer, thanks for all the help ModelM.

---

### Post by ModelM on 2009-02-04
In my first message I outlined the three steps:

1)

  In a terminal type:

  sudo wvdialconf

2)

  In a terminal type:

  sudo gedit /etc/wvdial.conf
  
  Edit the file to add your username & password

3)

  In a terminal type

  sudo wvdial

  Your modem should dial & connect

---

### Post by vamper on 2009-02-04
OK ModelM here is my results

[COLOR="Red"]hell@hell-desktop:~$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- OK
ttyS0<*1>: ATQ0 V1 E1 Z -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS0<*1>: Modem Identifier: ATI -- Zoom V.90 Serial s052099g -I Z207
ttyS0<*1>: Speed 4800: AT -- OK
ttyS0<*1>: Speed 9600: AT -- OK
ttyS0<*1>: Speed 19200: AT -- OK
ttyS0<*1>: Speed 38400: AT -- OK
ttyS0<*1>: Speed 57600: AT -- OK
ttyS0<*1>: Speed 115200: AT -- OK
ttyS0<*1>: Max speed is 115200; that should be safe.
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS3<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS3<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS3<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

Found a modem on /dev/ttyS0.
Modem configuration written to /etc/wvdial.conf.
ttyS0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
hell@hell-desktop:~$ sudo gedit /etc/wvdial.conf[/COLOR]
 At this point I got the pop up page


[COLOR="Red"][Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
; Phone = <xxxxxxx> -  - [COLOR="Indigo"]CHANGED to X for public posting[/COLOR]
ISDN = 0
; Password = <xxxxxxx>- - [COLOR="Indigo"]CHANGED to X for public posting[/COLOR]
New PPPD = yes
; Username = <xxxxxxxxxxxxxx>- - [COLOR="Indigo"]CHANGED to X for public posting[/COLOR]
Modem = /dev/ttyS0
Baud = 115200[/COLOR]

I then save the document and close out this page, when I do I get the following




[COLOR="Red"]** (gedit:5768): WARNING **: Could not write gedit state file: Failed to create file '/root/.gnome2/gedit-2.KXHROU': No such file or directory

I/O error : No such file or directory
I/O error : No such file or directory

hell@hell-desktop:~$[/COLOR] [COLOR="Indigo"]sudo wvdial-  - I put this prompt in any way and still get the following[/COLOR]



[COLOR="Red"]--> WvDial: Internet dialer version 1.60
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
hell@hell-desktop:~$ 


[/COLOR]

[COLOR="Orange"]**Thank you for all your help and putting up with me- LOL, I am learning a little at a time **[/COLOR]

---

### Post by ModelM on 2009-02-04
Remove the semicolons as the first character of the lines containing the phone number, password, & username.

---

### Post by vamper on 2009-02-04
ModelM,

Thank you very much for working with me on this first endeavor, I removed the semicolons, and got a good response from the modem at that point but it would not stay connected, so finally remembering, something I read about the AMD 64 bit version Ubuntu 8.10, which what I was running, I installed i386 version Ubuntu 8.0.4. and re did the steps you described above - and instantly the Modem connected, and am using it right now with Ubuntu to write this message. It only connects under the v32 mode and haven't figured out how to get it to connect with the 56K mode that is also available on this model, but who cares - LOL, You have shown me how to write so command prompts, and a very good lesson learned along with that, so thank you so very much for some of my first lessons in Ubuntu and Linux operating systems

Cheers - :KS - vamper

---

