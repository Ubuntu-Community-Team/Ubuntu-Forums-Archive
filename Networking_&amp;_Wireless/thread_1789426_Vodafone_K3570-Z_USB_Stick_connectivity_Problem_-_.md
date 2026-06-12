---
title: "Vodafone K3570-Z USB Stick connectivity Problem - 'NO CARRIER'"
date: 2011-06-23
forum: Networking &amp; Wireless
---

### Post by chinmaya_n on 2011-06-23
Hi,

I 've problem with this usb stick to connect to Internet. I desperately tried for 6 long hours but could not resolve it! I almost tried every possible / meaningful solution but none worked!

My system detects the modem but it says NO CARRIER !
```
chinmaya@chinmaya:~$ sudo wvdial
--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
NO CARRIER

``` It clearly says "NO CARRIER" - I searched but couldn't find what this carrier is.
My /etc/wvdial.conf file
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","internet"
Password = ''
Phone = *99#
Modem Type = Analog Modem
Stupid mode = 1
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB1
ISDN = 0
Username = ''
Carrier Check = no

```

There is something interesting here... My system can detect the network as seen in the picture attached ( it says VODAFONE EDGE ).. but could not enable it with any of the connections created !

I'M currently contacting Vodafone Care. Any help would be greatly appreciated... 

Edit: My current OS: Ubuntu 11.04

ThankU.

---

### Post by chinmaya_n on 2011-06-23
bump! any help..

---

### Post by chinmaya_n on 2011-06-24
I Got this after some googleing... But I dont understand a bit except that this is a bug regarding the same problem but it was filed few months ago and it may/maynot be fixed by now!

[https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/683996](https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/683996)

Any help folks !

---

### Post by chinmaya_n on 2011-06-24
People... I went to vodafone store today and found that my balence is < 1 Rupee (India) so I had to recharge the sim to enable GPRS connectivity! -- *Those who have same problem, plz check your SIM once.*

After that it could connect.!! **It connected through default network manager not through wvdial**-- Happy for some time
But I could not figure out when it connects... It connects some times only, I guess after most of the reboots (not all)!

I observed that at some times "Mobile Connectivity" is not being enabled (we could see it when clicked on network manager applet after plugging the modem).
When ever it is enabled, modem could connect. But when it is not enabled, I had to mark it to be enabled manually, then it could not connect (weird !) It there a way to enable Mobile Connectivity by default, so that I could check this?? 

**Help People!!**

---

### Post by jamadagni on 2011-06-25
Hey man, I'm also connecting to Vodafone in India via my Nokia S60 phone with a Vodafone SIM. I am also having the same problem with erratic connectivity. I also tried to login on Windows using the Nokia Internet Connectivity software but the problem showed there also, so it's not a Linux/Ubuntu/Natty problem.

Whenever the proper connectivity is there from the network side, Natty logs in, no problem. It seems you are using GNOME. I personally use KDE and the KDE NM applet shows the signal strength. If there is a problem in connecting to the network the signal is at 0%. If you see tail /var/log/syslog you will observe errors in the cdc driver trying to connect. 

This problem is for the Vodafone guys to fix and not the Linux guys.

Anyhow, you should learn to make screenshots using the software instead of your digital camera, LOL! I don't know what app on GNOME is to be used but on KDE we have KSnapShot and hitting the PrtSc key automatically invokes it!

---

### Post by chinmaya_n on 2011-06-25
Yes I'm using gnome.. But It connects with windows seemlessly... So I expect this should be some problem with ubuntu...
(By the way I could connect with Hwaian modem easyly, I checked it at vodafone store.. They nolonger sell it- it is just a demo one)

And coming to that screenshot - we cant take a screenshot while watching network mangaer applet.

---

### Post by jamadagni on 2011-06-25
Can you post the output of tail /var/log/syslog upon connecting your modem and not receiving a connection? When the problem happens for me, I get:

```

Jun 25 13:41:15 sarvajnatma kernel: [ 9578.631579] usb 1-1.2: new high speed USB device using ehci_hcd and address 28
Jun 25 13:41:15 sarvajnatma kernel: [ 9578.737551] cdc_acm 1-1.2:1.1: ttyACM0: USB ACM device
Jun 25 13:41:15 sarvajnatma kernel: [ 9578.741891] usb 1-1.2: bad CDC descriptors
Jun 25 13:41:15 sarvajnatma kernel: [ 9578.742083] usb 1-1.2: bad CDC descriptors
Jun 25 13:41:15 sarvajnatma kernel: [ 9578.744358] cdc_phonet: probe of 1-1.2:1.12 failed with error -22

```

If you get the same kind of error, then I think you and I are in the same boat. If not, then problem your problem may still need to be investigated.

---

### Post by jamadagni on 2011-06-25
Uh oh -- I just now saw [this article](http://lwn.net/Articles/342908/). So it seems cdc phonet stuff is only for Nokia phones. Probably you will get a different error. But still, posting the output of **dmesg | tail** and **tail /var/log/syslog** would enable people to help you better.

---

### Post by chinmaya_n on 2011-06-25
Cheers !! I could connect using **Sakis3G** very well...
May be due to some reason it could not connect the earlier time ( may be that less balence thing that happend )
That script is very good :)

I have to still try with BCM (Betavine Connection Manager) - It is giving some dependency issues and 've some broken problem with Salutis Connect. So I've to resolve these issues and try BCM !
I will try that and post the result again .... 

ThankU

---

### Post by chinmaya_n on 2011-06-25
a

---

### Post by alexfish on 2011-06-25
high chinamaya_n

just received your private message requesting help

I would have recommended sakis3g, but as seen sakis3g already downloaded and working
had done a post at
[Natty, known bugs, fixes and work arounds]("http://ubuntuforums.org/showthread.php?t=1749312") 			
see post
#[**30**]("http://ubuntuforums.org/showpost.php?p=10793568&postcount=30")

regards

alexfish

---

### Post by chinmaya_n on 2011-06-25
Hi alexfish,

Thanx for your response and time.

I could now connect to internet but it is not mentioning in network-manager and how could I track my data transfers and speeds... which is the interface that is binded to it... like (eth0,ppp0 etc.,) I would like to solve this too...

Thanks and Regards.

---

### Post by alexfish on 2011-06-25
hi

have read another private private message from your self,

now saying sakis3g may or may not work , as using different distro ?

noted from previous post you were trying to install BCM and failed to dependency errors
also noted from same post now have problem with Salutis Connect, as far as I am aware in post back in 2008 salutis is no longer supported, 

can you confirm that 
1. sakis3g is installed on Ubuntu system
2. does sakis3g work , a} all the time or, b} some of the time
3. is modem manager still on the system , if not,reinstall modem manager if BCM not been used

then will take a fresh look as regards the connection and what your trying to acheive

alexfish

---

### Post by chinmaya_n on 2011-06-26
Hi 

Some how I could successfully uninstall Salutis Connect.
 
1 > Yes sakis3g is on my ubuntu 11.04
2 > Till now it has connected beautifully.. Once gave a problem with connection establishment... May be it was on network side. I xperieced a low bandwidth yesterday, thought it may be problem from sakis3g - but today it is fine (atleast I feel) Not sure about this - Does sakis3g eating away my b/w??
3 > I 've not touched this Modem-manager (default). But I could not see anytype of recognizing the modem after using sakis3g or may be after installing those packages for BCM etc., Before atleast some times it could recognize and connect through the default Mobile Broadband connection. Dont know why it has happend like dis... Any Ideas??

And when I try to run BCM it gives this error:
```
Traceback (most recent call last):
  File "/usr/bin/bcm", line 10, in <module>
    from wader.common.utils import save_file, get_file_data
ImportError: No module named wader.common.utils

```Now trying to figure this out....

---

### Post by alexfish on 2011-06-26
now know sakis3g is working

suggest try reinstall BCM from

[https://forge.betavine.net/frs/?group_id=76](https://forge.betavine.net/frs/?group_id=76)
when prompted allow the installation from the software center, or tick software center from the menu, see what happens

as said BCM will replace the default modem-manager with its own and will be limited in identifying other modems (hope it recognizes yours) but sakis3g should still work

do not install any of the modeswitch packages , not sure if these are compatible with This Ubuntu version

sakis3g does not limit bandwidth , most problems lay with the cell your connected to or if the main servers are busy, try disconnecting and reconnecting , or try use google dns option with sakis3g.

---

### Post by chinmaya_n on 2011-06-27
Ya... I'll try... 

And I'm using OpenDNS. Each time I 've to write the line into /etc/resolv.conf b'se it is being replaced after running sakis3g. :(

---

### Post by chinmaya_n on 2011-06-27
This is the installation process i followed for BCM: [ Not re installation as suggested by alexfish - Still 've to try that] 
```
root@chinmaya:~/VC# ls
bcm_2.99.12-1_all.deb
python-messaging_0.5.9-1_all.deb
usb-modeswitch-data_20100826-1betavine1_all.deb
wader-core_0.5.5-1_all.deb
root@chinmaya:~/VC# dpkg -i *.deb
(Reading database ... 142041 files and directories currently installed.)
Preparing to replace bcm 2.99.12-1 (using bcm_2.99.12-1_all.deb) ...
Unpacking replacement bcm ...
Preparing to replace python-messaging 0.5.9-1 (using python-messaging_0.5.9-1_all.deb) ...
Unpacking replacement python-messaging ...
**dpkg: warning: downgrading usb-modeswitch-data from 20110227-2 to 20100826-1betavine1.**
Preparing to replace usb-modeswitch-data 20110227-2 (using usb-modeswitch-data_20100826-1betavine1_all.deb) ...
Unpacking replacement usb-modeswitch-data ...
Preparing to replace wader-core 0.5.5-1 (using wader-core_0.5.5-1_all.deb) ...
cat: /var/run/wader.pid: No such file or directory
Unpacking replacement wader-core ...
Setting up python-messaging (0.5.9-1) ...
Setting up usb-modeswitch-data (20100826-1betavine1) ...
Processing triggers for python-central ...
Setting up wader-core (0.5.5-1) ...
Traceback (most recent call last):
  File "<string>", line 1, in <module>
ImportError: No module named wader.plugins
Setting up bcm (2.99.12-1) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
root@chinmaya:~/VC# 

```
Observe the bold text.... Does that make any problem??
I'm getting the same error when i run BCM (as in previous post)

---

### Post by chinmaya_n on 2011-06-28
Reinstalled a lot of times... But same thing repeats... 
```
Traceback (most recent call last):
  File "/usr/bin/bcm", line 10, in <module>
    from wader.common.utils import save_file, get_file_data
ImportError: No module named wader.common.utils
```

Does anybody 've any idea... (Google is not specific about it.)

---

### Post by chinmaya_n on 2011-06-28
Got BCM worked...
Went to Betavine forums and found the process:

> If you want Betavine Connection Manager on Ubuntu 11.04 (Natty) then try the following:

(1) Install BCM as described in [http://www.betavine.net/bvportal/blog/view.html?blogId=133&postId=ff8080812942915f01294cd0e6e322bc](http://www.betavine.net/bvportal/blog/view.html?blogId=133&postId=ff8080812942915f01294cd0e6e322bc)

(2) Edit /usr/local/lib/python2.6/dist-packages/wader/common/backends/nm.py and replace 'org.freedesktop.NetworkManager.Devices' with 'org.freedesktop.NetworkManager.Device'.

(3) Add the following link so that wader works with Python 2.7 as well as Python 2.6:
sudo ln -s /usr/local/lib/python2.6/dist-packages/wader /usr/local/lib/python2.7/dist-packages/wader

It worked for me. 
Source: [https://forge.betavine.net/forum/forum.php?thread_id=811&forum_id=232](https://forge.betavine.net/forum/forum.php?thread_id=811&forum_id=232)

---

### Post by chinmaya_n on 2011-07-02
BCM is not working fine.. It worked for the first time... and after then .... it never connected... :( *It will be good if our default n/w manager works*
But Sakis3G is working fine.

**Note:** Does anybody know why my network graph applet (added using add to panel option) does not work. But the processor graph applet works. My network graph applet is not recognizing the ppp0.. And it could nt find any settings to change it... Any Ideas??

---

### Post by alexfish on 2011-07-11
Hi

just done a download of BCM . the only thing That was required was to create the symlink

```
sudo ln -s /usr/local/lib/python2.6/dist-packages/wader /usr/local/lib/python2.7/dist-packages/wader
```

suggest to reverse the changes in the Dbus spec `org.freedesktop.NetworkManager`.Device back to
```

org.freedesktop.NetworkManager.Devices
```

see what happens

alexfish

---

### Post by chinmaya_n on 2011-07-12
> **alexfish said:**
> Hi

just done a download of BCM . the only thing That was required was to create the symlink

```
sudo ln -s /usr/local/lib/python2.6/dist-packages/wader /usr/local/lib/python2.7/dist-packages/wader
```

I did this.. but BCM is not launching in root account where it is launching in User account & asking to create a profile, but it is not getting created (it asks for options but is not getting saved)
> **alexfish said:**
> 
suggest to reverse the changes in the Dbus spec `org.freedesktop.NetworkManager`.Device back to
```

org.freedesktop.NetworkManager.Devices
```

see what happens

alexfish
I did nt get what are you saying...

---

### Post by alexfish on 2011-07-12
From one of your posts you followed instructions = Post""			#[**19**]("http://ubuntuforums.org/showpost.php?p=10989988&postcount=19") "" 
> (2) Edit  /usr/local/lib/python2.6/dist-packages/wader/common/backends/nm.py and  replace 'org.freedesktop.NetworkManager.Devices' with  'org.freedesktop.NetworkManager.Device'.

alexfish

---

### Post by chinmaya_n on 2011-08-12
I'm marking this thread as SOLVED. As it is going well with Sakis3G.
I tried to get things work with other but couldnt due to various reasons.

So, anyone having problems can continue posting.. :-)

---

