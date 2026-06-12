---
title: "Maxon BP3 connects, not software tho..."
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by Slowjoe on 2009-11-11
Hopefully this is an easy one for you.  Thanks for reading.  Have just defected (like many others it seems), so dumbed-down explanations are required please.  I'm using Jaunty, kernal 2.26.1.

So far... I have followed instructions in another thread to set up and connect my Maxon BP3 Bigpond modem.  It connects because I can ping [www.google.com.au]("http://www.google.com.au").  However, when I try to connect via NetworkManager it appears to connect for a second then gives me the disconnected notification.  I suspect something is interfering because another message sometimes appears asking for a password (not for root access).  Firefox won't recognise the connection either.

My settings in NetworkManager are:
Mobile Broadband tab:
    Add -> [in wizard] Telstra (UMTS/HSDPA) -> 
    Edit -> [in mobile broadband tab, Basic] Number: *99#
    Username: ________ (as per account, and 100% correct)
    Password: ________ (as per account, and 100% correct too)
    [Advanced] APN: telstra.bigpond
    [In all other sections of NetworkManager] Default

Here are the instructions I followed to get connected from the other thread.  I am not even convinced everything went to plan because I can't find an entry for Sierra in Synaptics.  (It's possible I'm not looking in the right place too... ) 

From a post by Frans81 on 22 Sept 2007...

.....................................................................................................[INDENT]                                     **Re: bigpond next g wireless broadband**             
      I got one of these units working today. it was a blue BP3-USB with a bigpond sticker.
there are a few ways to get this working. this is the way that i got it working first.

**Step 1.**
have your user name and password ready. [COLOR=Red]THEY ARE CASE SENSITIVE[/COLOR].
go to [https://www.bigpond.com/mybigpond/default.asp](https://www.bigpond.com/mybigpond/default.asp)    and enter your [EMAIL="username@bigpond.com"]username@bigpond.com[/EMAIL] and password in the login box on the left.

if the username and password is correct you will be able to see info on your plan.
doing this saves a lot of piss farting around if you have the password wrong (remember it is case sensitive). Trust me, I found out the hard way.

Write you user name and password down in exact case.

**Step 2.**
Plug the modem into to a USB port.
when the Blue LED has stopped flashing and is on solid Blue, then you have enough signal to make a connection. if the blue LED is blinking, then you don't have enough signal strength. the purveyor of the BP3USB [Maxon Australia]("http://maxon.com.au/") sells [external antennas for the device in there online store]("http://maxon.com.au/shop/index.php?cPath=22")
The LED will turn green when when a point to point link has been established (ie you are connected to the internet)

**Step 3.**
open a terminal
     Code:
     ls /dev/ttyUSB* 
if you can see 3 ttyUSB devices then you are in luck. otherwise you may have to open a terminal and type
     Code:
     sudo insmod /lib/modules/`uname -r`/kernel/\drivers/usb/serial/usbserial.ko \vendor=0x16d8 product=0x6280 
this binds you modem to a tty device.

**Step 4.**
First download these files to your desktop.
[ppp.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=37181&d=1183447467")
[sierra.v.1.0.6.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=37181&d=1183447467") 

Then Extract the archives downloaded by [Right click] [Extract Here]

**Step 5.**
The files in the ppp.tar.gz archive that you should now have extracted should be moved to 
/etc/ppp/peers/

the easiest way to do this is open a terminal and then 
     Code:
     sudo nautilus 
 then enter your password. this will give the file manager root access.

1) navigate to /home/[COLOR=Red]Your Username[/COLOR]/Desktop/ppp/
2) select all of the files and copy.
3) navigate to /etc/ppp/peers/
4) paste the files that you copied.

**Step 6.**
open the file gsm with a text editor. (/etc/ppp/peers/gsm) you will need root access if you don't already have it.
on line 3, make sure that it says /dev/ttyUSB1
on line 21, change [EMAIL="username@bigpond.com"]username@bigpond.com[/EMAIL] to your [EMAIL="username@bigpond.com"]username@bigpond.com[/EMAIL]
on line 22, change [COLOR=Red]your password[/COLOR] to your password (remember it is case sensitive)
Save the file and close it.

**Step 7.**
open a terminal
TIP - you can press TAB to complete a path after typing a few characters

     Code:
     sudo su [enter password]
cd /home/[COLOR=Red]Your Username[/COLOR]/Desktop/sierra.v.1.0.6/ 
make
make install 
**Step 8.**
you should be ready for testing now.

to dial type
     Code:
     pon gsm 
to hang up open a terminal and type
     Code:
     poff gsm 
if you connect successfully, in the terminal window it should tell you what IP address you have been assigned. sorry i don't have a terminal output of a successful connection as i was setting this up for someone else and i don't have the modem any more. 
if after about 30 seconds, if it has not said hanging up then chances are that it has connected.

to test it
     Code:
     ping [www.google.com]("http://www.google.com") 
if you get a response then it is all working.
   *                                              Last edited by Frans81; September 22nd, 2007 at 02:52 AM..*
  [/INDENT][I].................................................................................................................

NetworkManager has been acting a bit strangly sometimes too.  Like minimising, then not restoring (always after I've connected via terminal)
I suspect it's something really easy to fix... haha.   Thanks for your time.

Slowjoe.[/I]

---

### Post by Slowjoe on 2009-11-12
Reply to my own thread...  Apparently I had a permissions issue because I checked the "Make connection available to all"  checkbox, and Bob was (actually is), my uncle.  In other words my software will now let me connect.

I've only been on-line for 5 minutes so I should probably not speak too soon.

Joe.

---

