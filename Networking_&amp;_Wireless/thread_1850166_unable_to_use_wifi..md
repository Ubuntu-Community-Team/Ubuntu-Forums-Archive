---
title: "unable to use wifi."
date: 2011-09-25
forum: Networking &amp; Wireless
---

### Post by rishi_singh on 2011-09-25
This is my first post here. I am an "intermediate computer user". I have installed ubuntu 10.04 beside windows 7 on my laptop. I am unable to use the wifi inside ubuntu because i dont see any connections. It works in windows though.

What i tried (unsuccessfully) - installed that ndis wrapper and the other 2 files from ubuntu site. Downloaded the driver file and copied the .inf file for what i think was related to my wifi adapter. It appears in ndis. Then, i put my wifi settings (not so sure if all are correct). Still, i dont see any wifi connections.
I am still unable to connect to the internet.

Please help me to solve this problem. Will installing ubuntu 11 help in any way ?

PS :
RANT - Why is everything so complicated in linux ? Do they really think that the regular user would like to go through so much trouble for the "smallest" tasks ? To be comfortable with linux i would need BS,MS, 3 Phd in computer science, certifications in networking, security and more... :(.
There is one more problem which i will post in another sub forum. 
I feel  that linux will remain only in labs, nerds computers and never become mainstream with this kind of stuff. Not every body enjoys typing 10-20 commands for a problem - I would like to be proved wrong though. 

All those folk who criticize windows and praise linux too much should produce an os as easy to setup and use. Then, the praise and windows bashing will seem plausible.

---

### Post by mörgæs on 2011-09-26
It would be easier to help you if you started with a complete hardware description including the wirefree card.

Yes, installing 11.04 using wired internet access is a good beginning. Post again if you still don't get a connection after that.

---

### Post by rishi_singh on 2011-09-26
> **mörgæs said:**
> It would be easier to help you if you started with a complete hardware description including the wirefree card.

Yes, installing 11.04 using wired internet access is a good beginning. Post again if you still don't get a connection after that.

hardware :
1x1 11b/g/n Wireless LAN PCI Express Half Mini Card Adapter
Adapter Type  :  IEEE 802.11 wireless
NetBIOS over TCP/IP  :  Enabled via DHCP
NETBIOS Node Type  :  Hybrid node


Operating System
    MS Windows 7 Home Premium 64-bit SP1


If anymore info is needed, please let me know.

---

### Post by Brandel Valico on 2011-09-26
Have you tried connecting it via ethernet and downloading the additional drivers. Your wifi card may have a driver available for it. You would find the additional drivers by clicking the System tab and and mousing to Administrator then mouse down to additional drivers. 

If one is available it should offer you the option to activate it. 

You also may just need to install the updates will hooked up with a cable.

---

### Post by rishi_singh on 2011-09-26
> **Brandel Valico said:**
> Have you tried connecting it via ethernet and downloading the additional drivers. Your wifi card may have a driver available for it. You would find the additional drivers by clicking the System tab and and mousing to Administrator then mouse down to additional drivers. 

If one is available it should offer you the option to activate it. 

You also may just need to install the updates will hooked up with a cable.

Sorry, but i have no ethernet cable and my all my connections are wireless. 
Any other way to get my wifi running inside linux. I am desperate.

---

### Post by kiwibrit on 2011-09-26
Does your wirelss router have an ethernet port?  If so you could run a cable to your computer from that.

Good luck.  FWIW, I'm having trouble getting a Linux driver for my WLAN, too - see [this thread](http://ubuntuforums.org/showthread.php?t=1850244).  I like the speed of Ubuntu compared to Windows - but it does seem there is a lack of driver support in some areas.

---

### Post by Denver Dave on 2011-09-26
I also did the ethernet port option until I managed to get connected.

Have you taken your laptop to an area where you are sure that there are broadcast wireless connections?

Also helps to have a 2nd laptop from a friend where there connections work, to compare settings.

I had a different, pleasant experience with ubuntu and connecting to my hidden wireless connection - much easier than with windows 7
[http://ubuntuforums.org/showthread.php?p=11287528](http://ubuntuforums.org/showthread.php?p=11287528)

---

### Post by rishi_singh on 2011-09-26
> **kiwibrit said:**
> Does your wirelss router have an ethernet port?  If so you could run a cable to your computer from that.


The router is high up on a wall. It has no ethernet port.

---

### Post by mörgæs on 2011-09-26
According to 
[http://ubuntuforums.org/showthread.php?t=1850446](http://ubuntuforums.org/showthread.php?t=1850446)
it seems like you are trying 11.04. This is good, but it would have been a VERY friendly gesture if you had posted this information here. There might be someone right now wasting their time trying to find you a solution based on 10.04.

When you open a thread, you have the responsibility for it until closed.

---

### Post by rishi_singh on 2011-09-26
> **mörgæs said:**
> According to 
[http://ubuntuforums.org/showthread.php?t=1850446](http://ubuntuforums.org/showthread.php?t=1850446)
it seems like you are trying 11.04. This is good, but it would have been a VERY friendly gesture if you had posted this information here. There might be someone right now wasting their time trying to find you a solution based on 10.04.

When you open a thread, you have the responsibility for it until closed.

I am keeping all options open. I have not uninstalled 10.04 yet. Tried 11.04 liveCD and had the same problem. Now I am wondering if i should delete 10.04 and put 11.04.

---

### Post by chili555 on 2011-09-26
> To be comfortable with linux i would need BS,MS, 3 Phd in computer science, certifications in networking, security and more... .This will be a big surprise to my wife who uses Linux every day and couldn't be happier. She is none of those; she is a retired and a grandmother. However, she doesn't need wireless and she does have a bit of help.

Just give me a bit more information. Open a terminal and type in:```
lspci -nn | grep 0280
```Press Enter. Post the result. I am confident we can get you going easily.

COUNTER_RANT: Getting wireless going is a bit of a hurdle. In many cases, it 'just works.' In a few, it's a bit harder. Once that's done, it's all smooth sailing, as Mrs. Chili can confirm.

---

### Post by sammiev on 2011-09-26
Have you tried burning a few copies of different versions of ubuntu like 11.04 and 11.10 to see it your wireless is supported without having to use a ethernet connection? After today I do not have any problems suggesting people to start using 11.10. The 11.10 final release is only 2 or 3 weeks away now. :)

---

### Post by rishi_singh on 2011-09-27
> **sammiev said:**
> Have you tried burning a few copies of different versions of ubuntu like 11.04 and 11.10 to see it your wireless is supported without having to use a ethernet connection? After today I do not have any problems suggesting people to start using 11.10. The 11.10 final release is only 2 or 3 weeks away now. :)
Deleted 10.04. Did stuff to make its partition visible and usable in win 7. But now i cant instal 11.04 in that partition. It throws up options i cant understand. Besides, the wifi did not work with live cd for 11.04. :(

---

### Post by alexan on 2011-09-27
> **rishi_singh said:**
> RANT - Why is everything so complicated in linux ? Do they really think that the regular user would like to go through so much trouble for the "smallest" tasks ? To be comfortable with linux i would need BS,MS, 3 Phd in computer science, certifications in networking, security and more... :(.
There is one more problem which i will post in another sub forum. 
I feel  that linux will remain only in labs, nerds computers and never become mainstream with this kind of stuff. Not every body enjoys typing 10-20 commands for a problem - I would like to be proved wrong though. 

All those folk who criticize windows and praise linux too much should produce an os as easy to setup and use. Then, the praise and windows bashing will seem plausible.
A usb wifi dongle cost about ~13$

Before buy check on Google if it's fully compatible with Linux or [is listed there](http://linuxhcl.com/browse/search?offset=0&category=25&manufacturer=&rating=5&os=&order-by=&keywords=)
Can I have my *BS,MS, 3 Phd in computer science, certifications in networking, security* now?

---

### Post by rishi_singh on 2011-09-27
[SIZE=4][B]update : 
I now use ubuntu 11.04. But the original problem still remains. Please help me to solve it.
I dont want to buy a wifi dongle for it. So that option is out.
[/B][/SIZE]

---

### Post by rishi_singh on 2011-09-27
> **alexan said:**
> A usb wifi dongle cost about ~13$

Sorry, i dont want to consider that option. I want the drivers.

I'd rather go to a massage parlour and get a head massage for $13+ to relieve the headache that linux has and continues to give me.

---

### Post by chili555 on 2011-09-27
> I want the drivers.Please provide the information I requested above. It is needed in order to see what driver you need.

---

### Post by rishi_singh on 2011-09-27
> **chili555 said:**
> Please provide the information I requested above. It is needed in order to see what driver you need.
Realtek semicondutor corps : rtl8192ce wireless card.
1x1 11b/g/n Wireless LAN PCI Express Half Mini Card Adapter
Adapter Type  :  IEEE 802.11 wireless

---

### Post by chili555 on 2011-09-28
> **rishi_singh said:**
> Realtek semicondutor corps : rtl8192ce wireless card.
1x1 11b/g/n Wireless LAN PCI Express Half Mini Card Adapter
Adapter Type  :  IEEE 802.11 wirelessThat's not the information I requested. The full data including the vendor and device ID are needed. If it is indeed a Realtek that uses the 8192CE chipset, you'll need to compile the driver from source code. Another alternative is to install Ubuntu 11.04 where rtl8192ce is included by default. Which do you prefer?

---

### Post by rishi_singh on 2011-09-28
> **chili555 said:**
> That's not the information I requested. The full data including the vendor and device ID are needed. If it is indeed a Realtek that uses the 8192CE chipset, you'll need to compile the driver from source code. Another alternative is to install Ubuntu 11.04 where rtl8192ce is included by default. Which do you prefer?

I installed 11.04 already. But no networks are detected. how to get these things "the vendor and device ID" and source code of the driver ?

---

### Post by chili555 on 2011-09-28
If you've upgraded to 11.04, we must change our strategy a bit. Please open a terminal and run and post these commands, one at a time:```
lsmod | grep 819
iwconfig
sudo iwlist wlan0 scan
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Thanks.

---

### Post by rishi_singh on 2011-09-28
> **chili555 said:**
> If you've upgraded to 11.04, we must change our strategy a bit. Please open a terminal and run and post these commands, one at a time:```
lsmod | grep 819
iwconfig
sudo iwlist wlan0 scan
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Thanks.

How do i copy the results of the commands and put them into a txt file so that i dont have to type them ?

[SIZE=4]**NOTE : In windows, i use an application to authenticate/login into my organization's internet.**[/SIZE] I hope it has nothing to do with this.

**lsmod | grep 819 **
rtl819ce   some number 0
rtlwifi   some number 1  rtl819ce
mac<some number> some number 3  rtl819ce, rtlwifi

**iwconfig**
lo no wireless extension
eth0 no wireless extension
wlan0 IEE 802.11 bgn ESSID : off/any
<some more wierd stuff by linux here> <EDITED>

**sudo iwlist wlan0 scan**
wlan 0   Interface doesnt support scanning : Network is down.

As for the pipe symbol, we window$ users are not so handicapped :)


[SIZE=4]**PS : Did you folks see the movie "Independence  day " or any such movie which has hackers ? They should not upload viruses. Just upload linux and the system will become useless.  **[/SIZE][SIZE=3]**Linux is the most sophisticated "hacking toolkit". **[/SIZE]

---

### Post by Denver Dave on 2011-09-28
I'm not sure about how to do the script file, but that would be nice to know.

For the terminal, for some unknown reason the paste part of the cut and paste is different - do ctl+shift+v  (not just ctl+v)

Hope this helps.

---

### Post by tcb2185 on 2011-09-28
Glad im not the only one having this prob.. But i got one of these coming that will be here tomorrow so hopefully that will take care of my issues.[Link Here]("http://www.amazon.com/External-Antenna-Wireless-802-11G-Network/dp/B0037G2BMY/ref=sr_1_5?ie=UTF8&qid=1317257259&sr=8-5")

:popcorn:

---

### Post by rishi_singh on 2011-09-29
> **tcb2185 said:**
> Glad im not the only one having this prob.. But i got one of these coming that will be here tomorrow so hopefully that will take care of my issues.[Link Here]("http://www.amazon.com/External-Antenna-Wireless-802-11G-Network/dp/B0037G2BMY/ref=sr_1_5?ie=UTF8&qid=1317257259&sr=8-5")

:popcorn:
I want to avoid that approach. Too many usb devices on hand. Dont want the clutter. BTW, did you choose your device because it has a big external antenna ? There is one that looks like a pen drive, but dont know if its antenna will be "good."

---

### Post by chili555 on 2011-09-29
> How do i copy the results of the commands and put them into a txt file so that i dont have to type them ?The easiest way is to merely transfer it into a text document right from the command line. Let's practice with the next set of diagnostics that I need. Please do:```
dmesg | grep 819 > singh.txt
rfkill list all >> singh.txt
iwconfig wlan0 >> singh.txt
```> iwconfig
lo no wireless extension
eth0 no wireless extension
wlan0 IEE 802.11 bgn ESSID : off/any
<some more bull-s-hit by linux here>Some of the data that followed is informative. I will appreciate not being edited. Furthermore, I hope we can keep the forum family-friendly.

You will find a text file in your user directory called singh.txt. You can either copy and paste it into the reply or directly attach it to your reply using the paperclip tool at the top of the reply box.

You have a wireless driver rtl8192ce and an interface wlan0. I suspect either firmware or the wireless key combination is preventing correct operation.> 

---

### Post by rishi_singh on 2011-09-29
Results of the commands :

[    1.658819] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[   14.532330] rtl8192ce 0000:08:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   14.532344] rtl8192ce 0000:08:00.0: setting latency timer to 64
[  218.961007] JFS: nTxBlock = 8192, nTxLock = 65536
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off

---

### Post by chili555 on 2011-09-29
> Tx-Power=off > 1: acer-wireless: Wireless LAN
Soft blocked: yesAnd now we see the real problem! Please do:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
```If your wireless comes to life, we'll blacklist acer-wmi so it doesn't interfer again.```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```Please post back so the searchers will learn from your experience.

---

### Post by rishi_singh on 2011-09-29
> **chili555 said:**
> And now we see the real problem! Please do:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
```

Thank you very much. Next time i am stuck,i will shine a light in the sky for you :) 
Wifi works with those commands. It works all right, but i have no idea of what i was doing. 
Thats what i dislike about linux. 

I dont know why, but it sometimes disconncets for a few microseconds and reconnected. 
Signal strength is fine, but speed seems slower than windows.

> **chili555 said:**
> ]If your wireless comes to life, we'll  blacklist acer-wmi so it doesn't interfer again.```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```Please post back so the searchers will learn from your experience.
That gives an error - bash : no such file or directory.



Yes, I did spew some hateful comments about linux. Just venting my  frustration. Dont know why folks accused me of trolling. Trolls dont  mark threads solved, do they ?

PS : Why do i still have firefox 4.0 when my win 7 has firefox 7 ? I dont see any update buttons in ubuntu firefox.

---

### Post by tcb2185 on 2011-09-29
Cool Glad you got it working. I Also got mine working. Just in Time too. my Windows 7 HDD Crashed and Now im running Ubuntu Linux setup. and :guitar:im DIGGIN it!

---

### Post by rishi_singh on 2011-09-30
> **tcb2185 said:**
> Cool Glad you got it working. I Also got mine working. Just in Time too. my Windows 7 HDD Crashed and Now im running Ubuntu Linux setup. and :guitar:im DIGGIN it!

Well, not exactly. I have to always type in the following commands after boot :
sudo rmmod -f acer-wmi
sudo rfkill unblock all

I am looking for that last step to make the wireless connection "always on". Glad to hear that things are working for you too.

---

### Post by bkratz on 2011-09-30
> **rishi_singh said:**
> Well, not exactly. I have to always type in the following commands after boot :
sudo rmmod -f acer-wmi
sudo rfkill unblock all

I am looking for that last step to make the wireless connection "always on". Glad to hear that things are working for you too.

This should do it for you:

The first thing I would do is add acer-wmi module to the blacklist file


```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```Next to make the others happen 

```
gksudo gedit /etc/rc.local

```Add a line above exit 0:

```
rfkill unblock all
```At reboot it should all happen for you!

---

### Post by rishi_singh on 2011-09-30
> **bkratz said:**
> This should do it for you:

The first thing I would do is add acer-wmi module to the blacklist file


```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```Next to make the others happen 

```
gksudo gedit /etc/rc.local

```Add a line above exit 0:

```
rfkill unblock all
```At reboot it should all happen for you!

Thanks ! It works now. However, the speed of wifi on ubuntu (painfully slow) is not as good as win 7, probably due to drivers. Will post that as a separate issue.:)

---

