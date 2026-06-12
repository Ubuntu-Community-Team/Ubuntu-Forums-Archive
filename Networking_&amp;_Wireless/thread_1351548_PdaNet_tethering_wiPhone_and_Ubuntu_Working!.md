---
title: "PdaNet tethering w/iPhone and Ubuntu Working!"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by FuManShu on 2009-12-10
After countless hours of trying many routes to get true tethering to work between my iPhone and my Laptop I finally found a working fix.  To do this you will need:

* A Jailbroken iPhone (tested on 3g OS3.0 but am not sure as to others)
* PdaNet (available via Cydia)
* usbmuxd ([https://launchpad.net/~jonabeck/+archive/ppa](https://launchpad.net/~jonabeck/+archive/ppa))
* python-twisted
* umux2007 ([http://xzrq.net/umux2007/umux2007-0.0.1.tar.gz](http://xzrq.net/umux2007/umux2007-0.0.1.tar.gz))

Step 1: Dependencies
install usbmuxd via the .debs or add the repository:
sudo apt-get install usbmuxd

To get python-twisted, simply:
sudo apt-get install python-twisted

Step 2: Install umux
download the .tar file and extract the folder.  In a terminal, "cd" to the umux directory and run:

sudo ./install

To test the installation, plug your iPhone to USB, change PdaNet to USB mode, and run in a terminal umux2007.py and you should see:
2009-12-02 11:26:55-0800 [-] Log opened.
2009-12-02 11:26:56-0800 [-] usbmux connected (fd 7, pid 1934)
161t?~

Ctrl+C to end the process and then on to the final step.

Step 3: Illumination!

From the terminal run "sudo pon umux2007" without the quotes and that should activate a connection between PdaNet and your laptop. Congratulations! You now have True USB tethering!

To shut down the connection type in terminal "poff" without the quotes and it will terminate.

Many thanks to Hector Martin for providing usbmuxd and also the developer of umux2007, Pavel Pergamenshchik.

I hope many find this as useful as I have and pardon my verbose tutorial.

*NOTE!: Your Network icon will NOT show that your are connected to a network, but don't mind that.

---

### Post by cymrujmc on 2009-12-24
Wow, I can't believe nobody has thanked you for this yet!  This is exactly what I've been needing since jailbreaking and finally found this!  Thanks!  Now maybe I can get my money's worth out of AT&T's data charges.  Instructions were easy to follow and it works perfectly so far.

---

### Post by FuManShu on 2009-12-28
Can I ask which iPhone Firmware and Model your iPhone is?  Or can anybody else confirm that this is working on different setups besides mine?

---

### Post by keyrunner on 2010-01-05
Has anyone tried this great solution with an Android phone, like the G-1, and PdaNet for Android?  I would love to tether my ubuntu and jolicloud netbooks.

---

### Post by FuManShu on 2010-01-07
This will not work for Android based phones, sadly, because it utilizes "usbmuxd" which is a recreation of the normal iTunes USB multiplexor to communicate with the iPhone.  I do, however, think that WiFi tethering is possible on Android devices.

---

### Post by j-d33zy on 2010-01-17
hi, great tutorial, but im having a problem, i installed the dependencies, and installed umux, but when i try to run it this is the output i get:

xxxx@xxxxxxx:~/Desktop/Downloads/umux2007-0.0.1$ umux2007.py
2010-01-16 20:56:04-0800 [-] Log opened.
2010-01-16 20:56:05-0800 [-] No devices found
2010-01-16 20:56:05-0800 [-] Traceback (most recent call last):
2010-01-16 20:56:05-0800 [-]   File "/usr/local/bin/umux2007.py", line 89, in <module>
2010-01-16 20:56:05-0800 [-]     connect_to_stdio(fd)
2010-01-16 20:56:05-0800 [-]   File "/usr/local/bin/umux2007.py", line 74, in connect_to_stdio
2010-01-16 20:56:05-0800 [-]     skt = socket.fromfd(fd, socket.AF_UNIX, socket.SOCK_STREAM)
2010-01-16 20:56:05-0800 [-] TypeError: an integer is required
 

any help in this matter would be greatly appriciated.

Thanks.

---

### Post by FuManShu on 2010-01-17
Double check that PdaNet is on and is set to "USB Mode".  You will need PdaNet >= v1.40.

---

### Post by j-d33zy on 2010-01-21
cool! got it working thanks. for some reason ubuntu wasn't mounting my iphone correctly, rebooted and it works fine. awesome guide!

---

### Post by balente84 on 2010-01-24
Coooooooooooooooooooool!!!!!!!!!!!!!
At the very first, the internet speed was so fast so I couldn't believe my eyes
but that was because of the wifi lol 

Anyways it works perfect for me
I'm using iPhone 3g 3.1.2 with Ubuntu Karmic Koala 9.10
Thank you thank you!!!!

---

### Post by FuManShu on 2010-01-24
If the speed isn't up to snuff then disable ipv6 and it will blaze.  Since PdaNet does not get along with ipv6, it will cause a long timeout before the page actually loads.  If you are using Firefox just type about:config in the address bar and then find "network.dns.disable.ipv6" and set it to true.  If you are using Chrome than you have to disable ipv6 throughout the OS, which is a little more of a hassle.  Glad people are appreciating this great trick!

---

### Post by RedPenguin on 2010-01-26
Thank you so much, I'm thinking that I had to do a huge iTunes + PdaNet Desktop install inside wine, but now it's just two simple commands.

I love this, because often in college I'm having class in a room disconnected from Internet, and the computers have no hard drive.

So what I do now is, I run Ubuntu off USB, then simply hooked up my iPhone, so now using two USB devices, I have a complete OS + Internet.

Also, I have no phone service on my iPhone, so it's just using the school's WiFi.

EDIT: Also, thanks again for your Firefox Disable IPv6 tip, because at first, it was going slower than dial-up, but once I did that, it went nice and fast, like broadband, so to speak.

Actually, even though the OS + Internet are both USB in my case, it seems to go faster, than Windows on a normal hard drive + PdaNet. I guess Linux will always be faster, LoL.

---

### Post by puzzler995 on 2010-01-30
This is Awesome!!! The only bad thing is that after the trial ends PdaNet will only connect to http:// not https:// so this doesn't work with Facebook or Gmail.

---

### Post by rewolfgz on 2010-02-08
It's working now! Fantastic.

This is exactly what I am looking for!

---

### Post by poisson37 on 2010-02-23
Just simply amazing! 

Thank you _very_ much, you made my year!

---

### Post by iomz on 2010-03-07
Wow what a smart tweek! Thanks a lot now I can be online anytime anywhere without losing extra battery life!:)

---

### Post by hkyork2064 on 2010-04-04
when i type umux2007.py, i get this:

york@york-laptop:~$ umux2007.py
2010-04-04 14:53:52+0800 [-] Log opened.
2010-04-04 14:53:52+0800 [-] Traceback (most recent call last):
2010-04-04 14:53:52+0800 [-]   File "/usr/local/bin/umux2007.py", line 88, in <module>
2010-04-04 14:53:52+0800 [-]     fd = connect_to_usbmux(2007)
2010-04-04 14:53:52+0800 [-]   File "/usr/local/bin/umux2007.py", line 55, in connect_to_usbmux
2010-04-04 14:53:52+0800 [-]     lmux = CDLL('libusbmuxd.so.1')
2010-04-04 14:53:52+0800 [-]   File "/usr/lib/python2.6/ctypes/__init__.py", line 353, in __init__
2010-04-04 14:53:52+0800 [-]     self._handle = _dlopen(self._name, mode)
2010-04-04 14:53:52+0800 [-] OSError: libusbmuxd.so.1: cannot open shared object file: No such file or directory
york@york-laptop:~$ 

any idea?

---

### Post by Shutter4U on 2010-04-04
You guys know you can use internet tethering via the USB cable, right?

I got it to work on my (non-jailbroken) iPhone 3g by doing this:

1) go into System->Preferences->Network Connections in Ubuntu
2) in the "Wired" tab, click "Add"
3) Give the new connection a friendly name
4) enter the MAC address of your iPhone in the field that asks for it

 - you can get this address from your iPhone:
 - goto Settings->General->About and and scroll down to "Wi-Fi Address"
 - the "Wi-Fi Address" is the MAC address

5) click checkboxes for "connect automatically" and "available to all users"
6) click "Apply" then "Close"
7) connect your iPhone and it should automatically connect. make sure "internet tethering" is enabled on your iPhone first, of course ;)

---

### Post by FuManShu on 2010-04-11
The problem with that solution is that in the US, we don't have the option of enabling tethering on firmware versions above 3.0.1. Even at 3.0.x, you have to use a custom mobileconfig file to get an option to allow tethering. That's why I started this thread is so that those stuck in the US with AT&T as their carrier can continue to use PDAnet to tether their phones to their Linux systems.

---

### Post by Lonoki on 2010-04-16
Hi,

everything is working just fine, i'm able to connect my iPhone, in PDANet app it shows computer connected, the *umux2007.py *command does what it should...
But i'm not  able to transfer a single byte.... In PDANet it says:
  USB Connection
  Bytes 0/0
  DNS Lookups: 0
  Connections: 0
  .
  .
  .


i have internet tethering and also 3G turned on and i was able to connect via wi-fi but it was pretty unstable so i'm trying this. I have iPhone 3GS 3.1.2, PDANet 1.61 registred and Ubuntu 9.04.... any clues?

---

### Post by FuManShu on 2010-04-16
You're almost there. You are just using the wrong command.  Instead of "umux2007.py", use "sudo pon umux2007" (without the quotes and note that there isn't a .py extension on the last part.). That should get you going.

---

### Post by Lonoki on 2010-04-17
no no no... you don't understand... in the first post, you said that i should test install with *umux2007.py *and it should give back:
2009-12-02 11:26:55-0800 [-] Log opened.
2009-12-02 11:26:56-0800 [-] usbmux connected (fd 7, pid 1934)


and it did... however when i do *sudo pon umux2007* it connects the iPhone, starts PDANet session but its not transfering data... its just 0/0 bytes all the time (i left it turned on for 30mins...)

i think the mistake's somewhere in my ubuntu config... any clues where....

---

### Post by FuManShu on 2010-04-17
Alright. So first off, make sure you ctrl+c out of umux2007.py before you issue sudo pon umux2007. Secondly, I had a very similar issue on kernel 2.6.31-14 and it was corrected by upgrading to 2.6.31-16 and all appropriate modules. Which kernel are you using?

I can't say for sure what is causing this conflict but if everything seems in order than there is a new program called MyWi available via Cydia that will allow you to tether via Diego giagio's ipheth module.

---

### Post by Lonoki on 2010-04-18
Hmmm.... its clear now.. Im still using 9.04 with newest kernel 2.6.28-18... so i need to ugrade to 9.10.

:( i hoped so much that everything would work on 9.04 :P

Okey... as soon as I get on KarmicK i'll post some reply over here...


Thx for help.

---

### Post by Lonoki on 2010-04-19
Hi... guess what type of internet connection am i using :) 

So i upgraded to 9.10 kernel 2.6.31-20
everything works fine, exept i had to uncheck "enable wireless" in NetworkManagerApplet...

thanks for the simplest and best working guide for iPhone tethering..


P.S now i can take full advantage of the BIO lessons :P

---

### Post by FuManShu on 2010-04-20
Great.  Strange though that you had to disable wireless networking.  I know that, while I cannot run both a wireless connection and tether, I do not need to disable it.  Wonder if your wireless card was trying to connect to some (possibly dummy) wireless network.  I'll keep that caveat in mind in case it comes up again.

---

### Post by dudewiththeface on 2010-04-21
i think i know the answer to this but ill ask anyways, can i use this guide on a HTC Touch Diamound or am i just up the creek without a paddle

---

### Post by FuManShu on 2010-04-22
You cannot, as Umux makes heavy use of libusbmuxd, which is an essential port of the normal apple multiplexor. It wouldn't work with a device that's not an Apple.

---

### Post by compostme on 2010-05-05
hey FuManShu,

thanks a ton for your simple tutorial to get this thing working...it works like a charm! it was very slow at first, but after disabling ipv6 in firefox, its blazing!

YAY, and thanks a ton :-)

---

### Post by Legionz on 2010-05-17
thank you so much it works very well :)

I tested on Ubuntu 9.10 => Ok
I tested on Ubuntu 10.04=>Ok

_EDIT : on Ubuntu 10.04 I succeed to make it works , but not very normallly :_

First I verified all the packages needed : everything OK
After I do this : *umux2007.py*  to test the connection with iDevice : iDevice Ok
So the tethering should work if I do : *sudo pon umux2007* , but no....

In the PdaNet app on the iPhone I see 236 packets sent , but 0 received. No connection with Firefox.

_BUT if I ping for exemple google , the sent and received packets are incresasing ! _that's very crazy don't you think .?! :p

AND still no connection with Firefox :/

_So , now is the solution_ :** if I plug a wifi usb key to my computer, and than i unplug it just after  , it works !! **
(I don't connect  to any  wireless network)

I don't kow what's wrong with this , it works , but this is very strange... :/

On Ubuntu 9.10 no problem like this ...

_What do you think about that ? have you tested on Ubuntu 10.04 ?_

---

### Post by tincup on 2010-05-31
Similar Problems here.

I tried to use PdaNet in Kubuntu 10.04 with my old 2G.
Setup and connection works perfect but then... no data seems to arrive.

Pinging and even trying to open pages generates some traffic in the PdaNet status bar, and from time to time I see a single ping with huge latency arriving.

Cannot try this WiFi key in and out thing, since I do not own one ;-)

Any ideas?

---

### Post by lecelte on 2010-06-10
THANKS

Works fine with iPhone 3Gs 3.1.2 + Ubuntu 10.4

But ... Firefox 3.6.3 doesn't seem to like this king of network : doesnt work at startup, need to unckeck 'off line mode' and then it's works, but very very slow ...

Chromium works fine.

PS : Don't forget to change your UserAgent ;)

---

### Post by mparic on 2010-06-25
I can confirm that this works on 10.04 (Firefox 3.6.3, Chrome 5.0.375) using iOS 4 (jailbroken with redsn0w) on an iPhone 3G. Brilliant!

---

### Post by Legionz on 2010-07-20
OK.

I found the solution  : I installed Chromium and it roxx :popcorn:
So , the problem is Firefox.

youhou ! ;)

---

### Post by grad_student on 2010-08-15
This will sound dumb but how do I "cd" into umux2007?

---

### Post by ThatBum on 2010-10-11
I thought I'd make a script for this:

```
#!/usr/bin/env bash
# This script connects to PDAnet on iPhone via USB.

set +x
check_root() {
uid=$(/usr/bin/id -u) && [ "$uid" = "0" ] ||
{ echo "You are not root, go away."; exit 3; }
}
start() {
    ifconfig | grep ppp >/dev/null
    STATUS=$?
if [ $STATUS -eq 0 ] ; then
    zenity --info --text "PDAnet already running; doing nothing."
else
    echo "Connecting..."
    pon umux2007 > /dev/null
    sleep 3
    ifconfig | grep ppp > /dev/null
    STATUS=$?
if [ $STATUS -eq 1 ] ; then
    zenity --error --text "No PDAnet device detected. Is is plugged in and in USB mode?"
    exit 2
fi
    dig @8.8.8.8 www.google.com +time=1> /dev/null
    DNS=$?
if [ $DNS -eq 0 ] ; then
    zenity --info --text "PDAnet connected!"
else
    zenity --warning --text "PDAnet is connected, but DNS didn't resolve. Are you in an area with cell coverage?"
fi
fi
}
stop() {
    ifconfig | grep ppp > /dev/null
    STATUS=$?
if [ $STATUS -eq 0 ] ; then
    echo "Disconnecting..."
    poff umux2007 > /dev/null
    zenity --info --text "PDAnet disconnected."
else
    zenity --info --text "PDAnet not running; doing nothing."
    exit 3
fi
}
restart() {
    ifconfig | grep ppp > /dev/null
    STATUS=$?
if [ $STATUS -eq 0 ] ; then
    echo "Disconnecting..."
    poff umux2007 > /dev/null
    sleep 3
    start
else
    zenity --info --text "PDAnet not running; doing nothing."
    exit 4
fi
}
status() {
ifconfig | grep ppp >/dev/null
STATUS=$?
if [ $STATUS -eq 0 ] ; then
    echo "PDAnet is on"
else 
    echo "PDAnet is off"
fi
}

case "$1" in
    start|stop|restart) check_root ; $1 ;;
    status) $1;;
*)
    echo "Usage: /etc/init.d/pdanetusb {start|stop|restart|status}"
    exit 1
    ;;
esac
exit 0
```This is provided it's all installed first, of course...

EDIT: Made it a little better with zenity notifications and such.

---

### Post by Zuloo on 2011-03-21
Hello guys I am trying to run a tethered internet from my iphone 3g3 (4.2.1) with PDA Net on Ubuntu 10.10 and I was trying the method in this thread but then I run into a hitch,

When I "CD" to my [ ~/UMUX2007-0.0.1$ ]
then run: Sudo ./install
It just takes me right back to my [  ~/UMUX2007-0.0.1$ ]
No confirmation or no failed message, Any Ideas?

---

### Post by tomaszekp5 on 2011-07-08
Thank you man! You are awesome for posting that! It fully worked for me :]!

---

### Post by RedPenguin on 2011-09-11
Anyone know how to use this method for 11.04?

I have been using this method perfectly on 10.04 LiveUSB.

Now I have created a 11.04 LiveUSB and it appears that new packages namely ipheth appears to be totally conflicting.

The minute I plugin the iPhone it shows "eth3" and ppp errors out:

/usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem'

I tried looking how to tether using the eth3 that shows up, but it says I need to "Enable Tethering" on the iPhone but neither my iPhone 2G 3.1.3 or iPhone 3G 4.2.1 show "Tethering" at all. Even trying the "tethering profile" from [http://help.benm.at/](http://help.benm.at/) do not work for me either. NOTE: My iPhones are totally dead of cell service, I use them basically as iPod Touches, WiFI only.

---

### Post by chrisinpants on 2012-08-24
Isn't it great when it all works out. Thanks fumanshu

---

### Post by darkrelik on 2013-06-25
I'm having the same problem as hkyork... I have Ubuntu 13.04, python-twisted, usbmuxd and I installed umux2007, however when I type "umux2007.py" (without the quotes) into the terminal, it returns this:

2013-06-25 12:07:16-0700 [-] Log opened.
2013-06-25 12:07:16-0700 [-] Traceback (most recent call last):
2013-06-25 12:07:16-0700 [-]   File "/usr/local/bin/umux2007.py", line 88, in <module>
2013-06-25 12:07:16-0700 [-]     fd = connect_to_usbmux(2007)
2013-06-25 12:07:16-0700 [-]   File "/usr/local/bin/umux2007.py", line 55, in connect_to_usbmux
2013-06-25 12:07:16-0700 [-]     lmux = CDLL('libusbmuxd.so.1')
2013-06-25 12:07:16-0700 [-]   File "/usr/lib/python2.7/ctypes/__init__.py", line 365, in __init__
2013-06-25 12:07:16-0700 [-]     self._handle = _dlopen(self._name, mode)
2013-06-25 12:07:16-0700 [-] OSError: libusbmuxd.so.1: cannot open shared object file: No such file or directory

Is anyone else having this problem? Is umux2007 no longer compatible with the newer versions of Ubuntu? I used to use this tool in 10.10, so I'm a bit confused...

---

### Post by darkrelik on 2013-06-25
Never mind, I fixed it! I've seen a few other people were having this same problem and it took a while for me to spot it. But now, it runs beautifully!

For those of you who are having this problem, I fixed it by opening umux2007.py with the text editor, found where it was looking for "libusbmuxd.so.1" and changed it to "libusbmuxd.so.1.0.8" which is the version of usbmuxd I am currently running. You can do this before/after installing umux2007.

I had been searching this problem for a couple of days now with no results, so I figured it'd be a good idea to post my findings on here for all to see.

Thanks for the program, FuManShu! I shall enjoy it yet again!!!

---

### Post by boazbrak on 2013-08-07
> **darkrelik said:**
> Never mind, I fixed it! I've seen a few other people were having this same problem and it took a while for me to spot it. But now, it runs beautifully!

For those of you who are having this problem, I fixed it by opening umux2007.py with the text editor, found where it was looking for "libusbmuxd.so.1" and changed it to "libusbmuxd.so.1.0.8" which is the version of usbmuxd I am currently running. You can do this before/after installing umux2007.

I had been searching this problem for a couple of days now with no results, so I figured it'd be a good idea to post my findings on here for all to see.

Thanks for the program, FuManShu! I shall enjoy it yet again!!!
thanks to you I can finally enjoy internet on my own computer! First I thought it was never going to work because im not realy used to working with a terminal , but after trying a few times it finally worked!

---

### Post by Cloud4Twenty on 2013-09-11
Not sure if I'm just late to the party or what, but for some reason every time i try to download the umux2007 thing it downloads a 1.3kb file that won't do anything. I go to the downloaded file and get an error trying to extract of 
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Exiting with failure status due to previous errors
Can anyone tell me what I can do to get this thing working for me?

---

### Post by rhuisking on 2014-03-09
> **darkrelik said:**
> Never mind, I fixed it! I've seen a few other people were having this same problem and it took a while for me to spot it. But now, it runs beautifully!

For those of you who are having this problem, I fixed it by opening umux2007.py with the text editor, found where it was looking for "libusbmuxd.so.1" and changed it to "libusbmuxd.so.1.0.8" which is the version of usbmuxd I am currently running. You can do this before/after installing umux2007.

I had been searching this problem for a couple of days now with no results, so I figured it'd be a good idea to post my findings on here for all to see.

Thanks for the program, FuManShu! I shall enjoy it yet again!!!

I have recently bought a iPhone 5S and jailbroke it using evasion, which was a great decision, and I followed the steps above and it works decent. One thing I have noticed is the phone spams "Do you trust this computer" and the only way to stop this is to say no, but everything else works. Thanks

---

