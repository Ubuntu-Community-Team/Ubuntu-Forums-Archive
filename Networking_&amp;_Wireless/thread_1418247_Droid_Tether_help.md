---
title: "Droid Tether help"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by iamgeniusrnti on 2010-02-28
Guys, I need help, I know this should be simple, I am sure I am missing something silly.

I followed this: [http://www.humans-enabled.com/2009/12/how-to-tether-your-verizon-droid-as.html](http://www.humans-enabled.com/2009/12/how-to-tether-your-verizon-droid-as.html)

In the last step I run the azi on the Droid and it works.

I run teh script, and it works.  Droid sense Ubuntu and Ubuntu sees the Droid.  My Droid is rooted.

Here is the output of the script:


genius@k-laptop:~/Downloads/azilink$ sudo start_modem
sudo: start_modem: command not found
genius@k-laptop:~/Downloads/azilink$ sudo ./start_modem
Sun Feb 28 10:51:48 2010 OpenVPN 2.1_rc19 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Oct 13 2009
Sun Feb 28 10:51:48 2010 WARNING: --ping should normally be used with --ping-restart or --ping-exit
Sun Feb 28 10:51:48 2010 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Sun Feb 28 10:51:48 2010 ******* WARNING *******: all encryption and authentication features disabled -- all data will be tunnelled as cleartext
Sun Feb 28 10:51:48 2010 TUN/TAP device tun0 opened
Sun Feb 28 10:51:48 2010 /sbin/ifconfig tun0 192.168.56.2 pointopoint 192.168.56.1 mtu 1500
Sun Feb 28 10:51:48 2010 Attempting to establish TCP connection with 127.0.0.1:41927 [nonblock]
Sun Feb 28 10:51:48 2010 TCP connection established with 127.0.0.1:41927
Sun Feb 28 10:51:48 2010 TCPv4_CLIENT link local: [undef]
Sun Feb 28 10:51:48 2010 TCPv4_CLIENT link remote: 127.0.0.1:41927
Sun Feb 28 10:51:49 2010 Peer Connection Initiated with 127.0.0.1:41927
Sun Feb 28 10:51:50 2010 Initialization Sequence Completed

To me it seems to work but when I go to firefox, it can't find anything... what am I missing?  Do I need to build a connection in the connection manager?

---

### Post by iamgeniusrnti on 2010-03-06
Bump?  Surely I'm not the only Ubuntu user who owns a Droid and thought about connecting the two together?

---

### Post by meatball on 2010-03-12
I'll refer you to this thread...

[http://ubuntuforums.org/showthread.php?t=1179894&highlight=azilink](http://ubuntuforums.org/showthread.php?t=1179894&highlight=azilink)

I followed shawn c's directions with my unrooted Verizon HTC Droid Eris and it works well. Good Luck.

---

### Post by iamgeniusrnti on 2010-03-12
> **meatball said:**
> I'll refer you to this thread...

[http://ubuntuforums.org/showthread.php?t=1179894&highlight=azilink](http://ubuntuforums.org/showthread.php?t=1179894&highlight=azilink)

I followed shawn c's directions with my unrooted Verizon HTC Droid Eris and it works well. Good Luck.

Yea... that's the instructions I used to get to where I was.  

But tonight I played with it some more and figured it out.  My Droid was attached to my home wifi network!  I realized it was probably misdirecting traffic.  As soon as I turned off the wi-fi and switched it to 3G, the script started working!

In fact, I am using it now!!!!  WAHOO!!!

---

### Post by Knsierraa on 2010-06-12
try this if your having problems...easy as its going to get


Tether an Android Phone Using Proxoid  
Written by Dmitri Popov 
edited and dumbed down by Rob
Meet Proxoid, a proxy server application that lets you use your phone as a modem without hacking its system. Making Proxoid work does require a few steps, but the entire process is simple enough even for uninitiated users. Here is how to make Proxoid work with an Ubuntu-based system. 
Start with installing the Proxoid application on your Android phone from the Android Market. On your phone, navigate to Settings - > Application -> Development and enable the USB debugging feature. On your Ubuntu machine, create the 90-android.rules file: (applications then accessories then terminal...select)   copy and paste the following:

gksudo gedit /etc/udev/rules.d/90-android.rules       (Press enter)
Add the following line to it:      copy and paste the following:

SUBSYSTEM=="usb", ATTRS{idVendor}=="0bb4", MODE="0666"     (press enter)
Save the file and quit the text editor. Download and unpack the latest release of Android SDK. Connect the phone to the Ubuntu machine via USB and start the Proxoid application. Open the Terminal, navigate to the tools directory in the Android SDK folder and run the following command: 
 
Example:  robert@robert-office:~$ cd '/home/robert/Desktop/android-sdk-linux_86/tools'       (press enter)
(where robert@robert-office:~$   will be specific to your setup and “robert/desktop” will be replaced with your user name and destination folder...that is wherever you downloaded the android sdk file...usually...     Downloads)
add the folloing line to it:  copy and paste the following
./adb forward tcp:8080 tcp:8080       (press enter)


The proxy server should now be running, but to be able to use it with Firefox, you have to modify the browser's proxy settings. In Firefox, choose Edit -> Preferences and switch to the Advanced -> Network section. Press the Settings button in the Configure how Firefox connects to the Internet group. Select the Manual proxy configuration option, then enter localhost in the HTTP Proxy field and 8080 in the Port field. Press OK to save the settings and close the window. Now you can browse the Web using the created connection.

---

### Post by w1ski on 2010-06-13
Proxoid works very well with Firefox.  Does anyone know or have it working with Thunderbird and gmail without going through or using the web browser?  In other words, thunderbird direct to gmail (doesn't like the port 8080, and does not work using gmail port 995?).  I am using ubuntu 10.04, proxoid, and the motorola droid.  Also, works very well with virtualbox, windows XP and PDAnet - but prefer ubuntu direct.  Any ideas on the "forward tcp:8080" for thunderbird would be appreciated.  Thanks.

---

### Post by Carl Hamlin on 2010-08-29
> **w1ski said:**
> Proxoid works very well with Firefox.  Does anyone know or have it working with Thunderbird and gmail without going through or using the web browser?  In other words, thunderbird direct to gmail (doesn't like the port 8080, and does not work using gmail port 995?).  I am using ubuntu 10.04, proxoid, and the motorola droid.  Also, works very well with virtualbox, windows XP and PDAnet - but prefer ubuntu direct.  Any ideas on the "forward tcp:8080" for thunderbird would be appreciated.  Thanks.

I'm having the same problem. Currently posting from the airport using my tethered Droid, but can't get Thunderbird to use the proxy, even though I've set it to use the same settings as Firefox for all protocols.

Has anyone gotten Thunderbird working with Proxoid?

---

### Post by iamgeniusrnti on 2010-08-29
> **Carl Hamlin said:**
> I'm having the same problem. Currently posting from the airport using my tethered Droid, but can't get Thunderbird to use the proxy, even though I've set it to use the same settings as Firefox for all protocols.

Has anyone gotten Thunderbird working with Proxoid?

Never tried, sorry.  Probably not applicable, but some carriers have been known to block certain ports.  But if you can acces the same ports directly off your phone, taht wouldn't be the case here... sorry, I don't know.

---

