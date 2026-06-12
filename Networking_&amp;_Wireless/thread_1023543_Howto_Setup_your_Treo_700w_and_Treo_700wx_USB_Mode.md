---
title: "Howto: Setup your Treo 700w and Treo 700wx USB Modem"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by lachild on 2008-12-28
Hello everyone.  I thought I'd write up another how to for people attempting to use there Treo 700w or 700wx as a tethered modem in Ubuntu.  

The original guide written by elephant007 [Found Here]("http://ubuntuforums.org/showthread.php?t=550133") needed a couple of modifications to work under Hardy and the post is too old to respond to it.  With that said all credit for this post as well as my thanks go to elephant007 for all the hard work.

Below is Elephant007 original guide with the modifications needed to work under Hardy.

-----------------------------------------------------------------------------

I'll just give you what I did to get it going, after all, that's what a howto is for!

On your 700wx, Activate the Modem Link program and plug it into your USB cable attached to the comptuer, then


```
lsusb
```

look for your 700wx, mine listed as

```
Bus 003 Device 004:  ID 045e:0079 Microsoft Corp.
```

Write down the vendor id which is the first set of numbers and then the product id which is the last set of numbers, Stop the Modem Link program and disconnect Treo from the USB cable.
Run

```
sudo gedit /etc/rc.local
```

Add these lines above "exit 0" use the vendor and product numbers your wrote down, make sure you start each number with 0x

```
/sbin/modprobe ipaq vendor=0x045e product=0x0079
touch /var/lock/subsys/local
```

save and close and then run

```
sudo /etc/rc.local start
```


Start Modem Link on the Treo and reconnect it to the USB cable. 

Check to make sure the modem driver loaded correctly

```
dmesg | tail
```

You should see the following message

```
usb 3-1: new full speed USB device using uhci_hcd and address 5
usb 3-1: configuration #1 chosen from 1 choice
ipaq 3-1:1.0: PocketPC PDA converter detected
usb 3-1: PocketPC PDA converter now attached to ttyUSB0

```

If you didn't see the above output, Craig suggests a restart at this time
If you did see an output similar to the above, write down the information of where the PocketPC PDA converter is attached to.


Next we need to make a change to the PPPD config file to keep us connected once the connection is made.  With out this change pppd will exit with a status 15 shortly after your connected.

Run the following

```
sudo gedit /etc/ppp/options
```

Change the following two lines

```
lcp-echo-interval 30
lcp-echo-failure 5
```

To this

```
lcp-echo-interval 0
lcp-echo-failure 0
```


(the rest of this howto is provided by the Sprint Broadband Setup Guide)
**Make sure you're connected to the internet to download appropriate packages**
Download KPPP and KPPLogview
click on APPLICATIONS>ADD/REMOVE
Select ALL
Search for ppp
Select KPPP and KPPPLongview
Click APPLY
After it's done downloading and in stalling, close ADD/REMOVE
Now let's configure the KPPP to use the modem we configured previously
Click APPLICATIONS>INTERNET>KPPP
Click CONFIGURE>>NEW>MANUAL SETUP
Name the connection whatever you desire
Click ADD
enter #777 for the phone number, click OK>OK
this will take you back to KPPP Configuration
click the MODEM tab click NEW
name the modem whatever you desire
click the down arrow on the MODEM DEVICE and change it to the location that corresponds to the where your PocketPC PDA is attached to (mine is /dev/ttyUSB0) Click OK>OK, this will exit your out of KPPP CONFIGURATION
click CONNECT and watch your Treo connect you to the internet!

I rebooted my laptop several times, the only error I received once was that KPPP couldn't detect a carrier. I disconnected my Treo from the USB cable and waited a few seconds, then plugged it back in and this resolved the problem.

Good luck!!!

---

