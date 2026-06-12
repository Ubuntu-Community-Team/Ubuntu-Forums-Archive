---
title: "How to install WUSB54G for Dapper Drake"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by g3r41d on 2006-06-08
Okie after fiddling for a long time I finally get the thing to work. (Finally..) Btw mine is version 4 so i might not know whether the rest willl work the same. 

First you'll see that in the admin -> network there is a rausb0 wireless. However that does not work with the native drivers provided (think they used rt2570)

**Step 1**

So you need to blacklist it first in a file situated in etc/modprobe.d/

```
$sudo gedit /etc/modprobe.d/blacklist
```

add the following line in the blacklist file 

blacklist rt2570

save and restart. Check that after restart your wireless rausb0 disappears leaving only the modem in admin -> network.

**Step 2**

Now install ndiswrapper 1.8. I'm not sure whether the default ndiswrapper provided in the cd works. I think it should. You can give it a try. Here's the link for ndiswrapper 1.8

[http://prdownloads.sourceforge.net/ndiswrapper/ndiswrapper-1.8.tar.gz?download](http://prdownloads.sourceforge.net/ndiswrapper/ndiswrapper-1.8.tar.gz?download)

Then extract the archive files

```
$tar zxvf ndiswrapper-version.tar.gz
```

Go to the directory created and type the following

```
$sudo make uninstall

$sudo make

$sudo make install
```

If you encounter problem with make command not recognised. It means that development tools are not installed properly. Pop in your cd and install

- build-essentials
- kernel headers

via synaptic. This should enable make.

Now ndiswrapper is installed

**step 3**

Installing the drivers is next. Pop in your WUSB54G installation cd. And find the drivers. For me it is version 4. So i copied the version 4 directory which is WUSB54Gv4. Copied the folder to my user directory.

```
/home/username/WUSB54Gv4
```

First check any drivers in ndiswrapper.
```

$sudo ndiswrapper -l
```

if there are any drivers installed uninstall it by

```
$sudo ndiswrapper -e drivername
```

follow by installing from the directory the inf file

```
$sudo ndiswrapper -i drivername 
```

please remember the inf extension. In my case the drivername is rt2500usb.inf

So now restart and wireless should work. Configure your wireless connection in admin -> network

^^

---

### Post by Quiet Revolution on 2006-06-11
Thank you very much for this quick and easy guide.  Other posts and places I've gone to try and find a solution to this have never even mentioned blacklisting the rt2570.

---

### Post by SlugO on 2006-06-12
I guess I have a slightly different WIFI device, Buffalo WLI-U2-KG54, but it's close enough that it probably would work with your instructions.

I did all the steps in you tutorial, except that I installed netu2g54 which seems to be the correct driver for me. After I've done that sudo ndiswrapper -l says:```
Installed ndis drivers:
netu2g54          driver present, hardware present
```However I can't find the device in the network manager after restart. It did show up there before blacklisting anything. Any idea what's wrong? :confused:

Using Xubuntu btw...

---

### Post by Relic2K on 2006-06-12
Will this also work with the X64 version of Ubuntu as well ? I have the exact USB wireless adapter you have. I made the mistake of installing Suse 10.1 X64 due to it's native Wireless support only to have everything messed big time and could not get anything to work properly anymore. Can anyone verify they have this working in the X64 version for me before I go to download the Distro, thanks in advance :)

---

### Post by hothamp on 2006-06-29
Ok I have the exact same adapter as you do (V4).  The installation went flawlessly with the instructions you gave.  My original wireless adapter (the wrong one) disappeared after rebooting.  I got no errors when installing the adapater as instructed.  But when I rebooted its only showing eth0 my onboard ethernet card.  Everything on the system is stock no modifications until installing this.  Any idea what I did wrong?  the wireless card doesn't even show up.  I'm using the x86_64 version.

---

### Post by moitio on 2006-06-29
[QUOTE=SlugO]After I've done that sudo ndiswrapper -l says:```
Installed ndis drivers:
netu2g54          driver present, hardware present
```However I can't find the device in the network manager after restart. It did show up there before blacklisting anything. Any idea what's wrong? :confused:

Using Xubuntu btw...[/QUOTE]

Make sure that after you do all the steps in the tutorial, do:

sudo depmod
sudo modprobe ndiswrapper

---

### Post by mattoman on 2006-07-01
Alrighty Thanks it works great. 

I have to run those two last commands:
sudo depmod
sudo modprobe ndiswrapper

The only problem is I have to run them everytime i restart, any way to resolve this? Thanks!

Matt

---

### Post by vest1 on 2006-07-07
Edit: Problem solved.

Seems that the ndiswrapper package on the cd is not enough, the link provided by the OP worked.

---

### Post by kewldude606 on 2006-07-07
> **mattoman said:**
> Alrighty Thanks it works great. 

I have to run those two last commands:
sudo depmod
sudo modprobe ndiswrapper

The only problem is I have to run them everytime i restart, any way to resolve this? Thanks!

Matt

Try sudo ndiswrapper -m.

---

### Post by Linuturk on 2006-07-08
I have the same exact adapter: WUSB54G v4

I've playing with this for the last two days. Funny thing is, my adapter works ok with the native drivers if the device IS NOT PLUGGED IN DURING THE UBUNTU INSTALL OR STARTUP. If you plug it in after, and activate it, it works. I'm about to try your method, b/c occasionally it will freeze up my system completely, and I have to hard reboot.

______________________________________________

This fixed all the problems I was having. It recognizes all the networks around me now, and it doesn't freeze up! Thanks so much!

Don't forget that sudo ndiswrapper -m

---

### Post by ndookie on 2006-07-09
Now , all of this has worked , and wlan0 is active and all.. all the configuration files are correct but still it doesnt work..

the deafult gateway device.. this never sets , i put wlan0 as it , and i click ok , when i check back , its not set..is this necessary for it to work ? Is there any other program that can be used to diagnose these errors and figure out whats going wrong with the wireles... If anyone is willing to help i would be very greatful.

Thank You,
Nigel

---

### Post by Linuturk on 2006-07-10
Ok, it seems things work fine after a modprobe ndiswrapper, using the driver from the cd. But over time, the performance of my adapter seems to degrade and it disconnects from any wireless network. I have to unplug the adapter, restart (if it doesn't freeze up my system) and plug it back in after the machine boots. After a modprobe ndiswrapper, it works great again; But it repeats that process.

---

### Post by sparhawk on 2006-07-10
OK so I followed the directions and the card is up and running... the only problems are it tells me that the signal is 100% which it should only be about 25% but no big deal. The real issue is that the system locks up and I have to reboot every 5 minutes... any suggestions? I have tried 3 different cards now and I am about to throw this box out the window. If anyone has any suggetions about wireless cards that actually work please let me know. Either that or why this system keeps freezing up would help. Thanks.

---

### Post by Linuturk on 2006-07-13
With the drivers included on the CD, you run into a serious problem.

If you have multiple access points around you with the same SSID, the WUSB54G will drop it's connection after a short time. Go download the latest drivers for your adapter at Linksys. I installed it using this driver, and I haven't had my connection drop yet.

---

### Post by lmp on 2006-07-15
I have a WUSB54Gv4. I had no problem at all with the native ubuntu 6.06 LTS. I did NOT need ndiswrapper for my desktop. Also my laptop had no problems with it. Only advise: first configure, then save and restart, than activate (otherwise it won't work).
I have the same issue with my laptop that after x minutes the wifi is not working anymore. I read in a windows magazine that this might be caused by the power settings of the wifi.The wifi wakes up not as fast as the computer, so it losses contact. However, were can i find this powersetting in XUBUNTU or UBUNTU??. I have an old laptop toshiba 2180 cdt. I already changed the hardware setting (bios), but this doesn't seem to help.

---

### Post by beemer on 2006-07-21
Linuturk -

I had the same issue with getting my wireless to work right - in that I had to leave it unplugged until after boot, plug it in, configure and it was ok.

Here's what I found:

$ lsmod | grep islsm

this showed several devices, one of which was "islsm_usb"

It was interferring with ndiswrapper at boot - so basically both drivers were fighting for the adapter.

in /etc/modprobe.d/blacklist I added:

blacklist islsm_usb 

to the end of the file and rebooted.  That prevented the islsm (prism54) driver from starting and ndiswrapper was able to do it's job. :)

One note: It seems that I (and others) are having issues with the system locking up (hard) after a bit of internet use using the 686 based kernels.  Under a 386 kernel - no issues what so ever.

Beemer

---

### Post by saz on 2006-07-25
I did everything as it were in the tutorial. My device is a WUSB54Gv4 too... the problem is that i installed the driver (rt2500usb) with ndiswrapper, all went very well, but after restarting ubuntu, the wireless rausb0 wasn't there... anyone can help?

---

### Post by bionnaki on 2006-07-27
will this work with a **wmp54g** with the rt2500 driver?

---

### Post by Area51mafia on 2006-07-29
> **ndookie said:**
> Now , all of this has worked , and wlan0 is active and all.. all the configuration files are correct but still it doesnt work..

the deafult gateway device.. this never sets , i put wlan0 as it , and i click ok , when i check back , its not set..is this necessary for it to work ? Is there any other program that can be used to diagnose these errors and figure out whats going wrong with the wireles... If anyone is willing to help i would be very greatful.

Thank You,
Nigel

I've just guided a friend of mine through this thread getting his WUSB54Gv4 installed correctly and we ran into this problem aswell.

Atfirst I thought it was because it wasn't loading on boot, so we did:

> 
ndiswrapper -m

and

> sudo gedit /etc/modules

and added **ndiswrapper** to the bottom.

(didn't fix it, but hey, it's good for some people here to know)

Then he suddenly told me that he had WEP enabled on his network. (..yes...he's an idiot) We put in the right Key, and it let it be set as the Default Gateway. So you could look into that, if you haven't already.

Cheers.

---

### Post by StrifeX on 2006-08-02
I've been playing around with this for 2 days and in the GNOME terminal it tell's me that the device is present and so is the driver, but it won't show up in the networking list. Can this be caused by the fact that I used the ndiswrapper drivers off of the CD instead of downloading the newest version and installing it (because I don't have internet on my Ubuntu computer)?

I've tried sudo ndiswrapper -m, etc and still it doesn't work. Any ideas?

---

### Post by StrifeX on 2006-08-03
*bump*

How to do I "login as root" in terminal? I need to do that in order to run the make install command in running the ndiswrapper install.

Please help, StrifeX

---

### Post by bionnaki on 2006-08-03
sudo <command>

---

### Post by StrifeX on 2006-08-03
Well, I've gotten my internet working because of this post, thanks alot. :)

---

### Post by alenm88 on 2006-08-04
it helped a lot

<a href="http://weegly.com">Weegly</a>

---

### Post by goonies on 2006-08-04
well getting this adapter to work was a nightmare, i spent 7 hours on it and it was all due to one little error and i guess not following instructions closely, i wasnt copying over the whole drivers folder, i was just copying over rt2500usb.inf which lead to a invalid driver error.... thanks for the great instructions =),,, 

TIP: read the instructions very carefully and follow them religously

ive notice i seem to disconnect every now and then, i have the latest linksys and ndiswrapper installed =\ what have u guys done to get a more stable connection?

---

### Post by astrobit on 2006-08-06
Hello... i dont know why do i get dis error.
-------------------------------------------------------------

leo@nava:~$ sudo ndiswrapper -l
Installed ndis drivers:
rt2500usb               driver present, hardware present
leo@nava:~$ sudo depmod
leo@nava:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
leo@nava:~$

-------------------------------------------------------------

Could somebody help me?

---

### Post by StrifeX on 2006-08-06
Did you install the newest version of ndiswrapper from the site? Installing the package from Synaptic doesn't work 100%.

Also try  "sudo gedit /etc/modules"

and add ndiswrapper to the bottom.

---

### Post by IrishMLK on 2006-08-07
> **lmp said:**
> Only advise: first configure, then save and restart, than activate (otherwise it won't work).

Thanks lmp!

I did this and have no problems now on my old Compaq Presario 1700 laptop. Even after I rebooted, my WUSB54G v.4 was linked before the login screen for Xubuntu popped up.  All without ndiswrapper and much headache.

---

### Post by rsd-17 on 2006-08-09
> **beemer said:**
> Linuturk -

I had the same issue with getting my wireless to work right - in that I had to leave it unplugged until after boot, plug it in, configure and it was ok.

--snip--

in /etc/modprobe.d/blacklist I added:

blacklist islsm_usb 

to the end of the file and rebooted.  That prevented the islsm (prism54) driver from starting and ndiswrapper was able to do it's job. :)

Beemer

Brilliant...that just saved me more time and frustration than you can imagine ](*,)  

Using a WUSB54G (no version number...initial release of the hardware I guess) on a Sony VAIO Desktop! 

..John R

---

### Post by Carmel on 2006-08-12
Hi guys.

I have done all thats said, and I can see my card in the admin> network place.

However, I have no internet access. And I do not know if I am connected to the network.

when I do iwconfig, I get something like this.

* wlan0      IEEE 802.11g  ESSID:"2WIRE995"
          Mode- Auto  '''Frequency- 2.437 GHz'''  '''Access Point- Not-Associated'''
          Bit Rate-11 Mb/s   Tx-Power-20 dBm   Sensitivity=- 121 dBm
          RTS thr:2347 B   Security mode:restricted
          Power Management off
          Link Quality=0  Signal level=-0 dBm  Noise level=-0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I have a 2Wire router, and its called 2WIRE995, the key is also correct.

Edit: Oh yea, it's a b/g router, and can go up to 54mb.

Can anyone advise? Quite sad I can't get internet. Thanks lots

---

### Post by SpyderMS on 2006-08-14
I'm trying to get my WUSBF54G to work using the driver provided [here]("http://zd1211.ath.cx/wiki/UntestedWithRewrite"). Unfortunately when I go to compile it, I get the following error.

```
spyder@LINK:~/zd1211$ sudo make
make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  LD      /home/spyder/zd1211/built-in.o
  CC [M]  /home/spyder/zd1211/zd_netdev.o
In file included from /home/spyder/zd1211/zd_mac.h:26,
                 from /home/spyder/zd1211/zd_netdev.c:28:
/home/spyder/zd1211/zd_chip.h:663: error: field &#8216;mutex&#8217; has incomplete type
/home/spyder/zd1211/zd_netdev.c:214: error: &#8216;ieee80211softmac_wx_set_mlme&#8217; undeclared here (not in a function)
make[2]: *** [/home/spyder/zd1211/zd_netdev.o] Error 1
make[1]: *** [_module_/home/spyder/zd1211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make: *** [build] Error 2

```

Does anyone know why it's not compiling?

---

### Post by Jeff2006 on 2006-08-21
> **g3r41d said:**
> Okie after fiddling for a long time I finally get the thing to work. (Finally..) Btw mine is version 4 so i might not know whether the rest willl work the same. 

First you'll see that in the admin -> network there is a rausb0 wireless. However that does not work with the native drivers provided (think they used rt2570)

**Step 1**

So you need to blacklist it first in a file situated in etc/modprobe.d/

```
$sudo gedit /etc/modprobe.d/blacklist
```

add the following line in the blacklist file 

blacklist rt2570

save and restart. Check that after restart your wireless rausb0 disappears leaving only the modem in admin -> network.

**Step 2**

Now install ndiswrapper 1.8. I'm not sure whether the default ndiswrapper provided in the cd works. I think it should. You can give it a try. Here's the link for ndiswrapper 1.8

[http://prdownloads.sourceforge.net/ndiswrapper/ndiswrapper-1.8.tar.gz?download](http://prdownloads.sourceforge.net/ndiswrapper/ndiswrapper-1.8.tar.gz?download)

Then extract the archive files

```
$tar zxvf ndiswrapper-version.tar.gz
```

Go to the directory created and type the following

```
$sudo make uninstall

$sudo make

$sudo make install
```

If you encounter problem with make command not recognised. It means that development tools are not installed properly. Pop in your cd and install

- build-essentials
- kernel headers

via synaptic. This should enable make.

Now ndiswrapper is installed

**step 3**

Installing the drivers is next. Pop in your WUSB54G installation cd. And find the drivers. For me it is version 4. So i copied the version 4 directory which is WUSB54Gv4. Copied the folder to my user directory.

```
/home/username/WUSB54Gv4
```

First check any drivers in ndiswrapper.
```

$sudo ndiswrapper -l
```

if there are any drivers installed uninstall it by

```
$sudo ndiswrapper -e drivername
```

follow by installing from the directory the inf file

```
$sudo ndiswrapper -i drivername 
```

please remember the inf extension. In my case the drivername is rt2500usb.inf

So now restart and wireless should work. Configure your wireless connection in admin -> network

^^
Thank you G3r41d for your clear step by step explanation.
There are 2 points which I need:
1. How do I get ver no of my Linksys wireless adapter?
2. I went to Add/Remove software and could not find Build-essentials and kernel headers.
Once again thank you very much

---

### Post by Jerk on 2006-08-21
> **Jeff2006 said:**
> 
1. How do I get ver no of my Linksys wireless adapter?


Jeff, I'm having trouble with the WUSB54G myself... but I believe the answer to your question is that it will be on the underside of the adapter. There is a piece that will slide out and reveal a decal that looks like this.

[IMG]http://www.linksys.co.jp/support/download/alart/images/wusb54g-v4.jpg[/IMG]

There's a red box around the area in that image. I hope that image is helpful.

Now, as far as my own personal problem. I'm running Xubuntu 6.06 on an older laptop. I have a WUSB54G that is detected when plugged in but it hard freezes the system when activated. So, I've tried following the instructions here and I run into trouble when installing ndiswrapper.

I download the file from SourceForge, and it craps out on the make command. So, I go through the install for build-essentials and kernel headers... but they have different names. I believe this is due to using the cd as a repository since I have no way of connecting to the internet on this laptop. After installing from the cd, I try to make ndiswrapper again and this time it gives a message about not being able to find the path to the kernel headers?

I'm sorry, I don't have the machine with me right now.

I have other computers that are connected to the internet, is it possible to download the files from the repositories on a mac?

Should the instructions be slightly adapted for Xubuntu?

Thanks for your help.

---

### Post by Jerk on 2006-08-22
**Update:**

So, I ran through the guide found here: [vuul's guide]("http://ubuntuforums.org/showthread.php?t=177836&highlight=xubuntu+wusb54g")

I thought that since my problem with the guide in this thread happened somewhere in the "[FONT="Courier New"]make[/FONT]" realm, that I'd use that guide which uses dpkg. So... I get all the way through and it seems to have gone swimmingly, except for the area where I'm to edit the "[FONT="Courier New"]/etc/network/interfaces[/FONT]"

I just don't understand how to add my device, as in where in the file. My device is called rausb0 by [FONT="Courier New"]iwconfig[/FONT]. I've read the man file for interfaces but it's a bit cryptic.

If I try and activate the card through Network-admin my system freezes.

Thanks in advance for any advice you could give me.

---

### Post by lupine_nickt on 2006-08-24
You need to add something like this:-

```

auto rausb0
iface rausb0 inet dhcp

```

That'll get it to automatically configure on startup. You can also add any commands that you would give to iwconfig, as you need to - for instance, setting the ESSID would look like this:-
```
    wireless-essid MyESSID
```
You can do the same with wep key (-key), etc.

By the way, the WUSB54G**v4** *does* work with the rt2570 native kernel driver... meaning that you don't need to use ndiswrapper! 

xF,

...Nick

---

### Post by Golgoth on 2006-08-24
I know the wusb54g v4 works with the rt2750 driver: when I connect it and after a lsmod|grep rt25, I can see that the rt2750 is loaded.

I can see the rausb0 in the network settings but when I try to activate it, my computer freezes...

Any idea?

THX

---

### Post by Jerk on 2006-08-24
Golgoth, I have the same exact issue. I'm going to try editing [FONT="Courier New"]/etc/network/interfaces[/FONT] again.

I'll let you know if it works.

---

### Post by lupine_nickt on 2006-08-27
The native drivers are minimally dodgy (it is beta software, after all).

Make sure you're using the latest CVS build, and do your best not to unplug or otherwise ask the USB dongle to stop. Also, try to use the 'rutilt' program to configure it (that's in the repo as well; or you can compile your own ;) ). Make sure that the line 'auto rausb0' is in the /etc/network/interfaces file - that could help.

xF,

...Nick

---

### Post by windquest on 2006-08-30
I had really hoped not to have to write...but. I am a real nubie b ut do know my way around "the other" program. Followed your instructions with good results right up to the point of installing the driver. Uswing ndiswrapper v1.8 the driver fails in line 135. Thinking this might be a ndiswrapper problem, I downloaded and installed v1.23. This time it fails in line 145. The driver is the rt2500usb.inf I don't know what the problem is or what to do next to get my WSUB54Gv4 installed and working...Thanks in advance](*,)

---

### Post by windquest on 2006-09-01
Well I found out the problem. For those that have this happen...the solution was to completely remove ndiswrapper. Follow the instructions at the web site. Once removed, then follow the installation instructions given here and all should be well. I now have: driver found, hardware found. I am still not connecting but that maybe another issue.

---

### Post by menzies on 2006-09-02
n00b using Dapper.  My computer freezes up about three minutes after I plug in my WUSB54Gv1 to my USB 2.0 ports (IOGear PCI card, GIC220U).  The wireless works fine when it's plugged into my usb 1.0 ports. I have not been able to reproduce the freezing using other devices on the USB card.  Used ndiswrapper v1.8, followed the directions in thread.  Before freezing, the wireless works great.

My questions: 1) Is it the wireless that is messed up, or is it the usb card driver?  2) If it is the usb driver, is there a way for me to install the windows drivers (available from mfg.) over the usb drivers in the linux kernel?

P.S. the computer also freezes if I plug in my WUSB54G -> USB 1.1 keyboard/hub -> USB 2.0 card.

Any ideas?

---

### Post by ajare on 2006-09-04
I have just reinstalled 6.06 from scratch. One of the posts earlier helped, I got the WUSB54G to work by using WEP 128 specifying the key as Hex pairs and logging out before activating. I didn't test trying to activate it first, couldn't be bothered (and I call myself a scientist!).
Anyway it works fine.

AMD Athlon 64 3500, Ati Sapphire X800, Belkin 54G router & WUSB54G.

Cheers

---

### Post by wallstreetp on 2006-09-05
does this also work for a WUSB11 ? i have been trying for days to get on my network with this. i installed edubuntu on an old computer to set up for my son. ihave installed the linux-wlan-ng package and now admin>networking recognizes a wireless port and device manager recognizes that it is an 802.11 device, but it won't recognize the specifics of the device and it will not connect to the network. i have configured the eth1 wireless link with my network name (i don't require a WEP) and it is set for DCHP, although i have also tried a static ip. any thoughts? please? help!

---

### Post by Golgoth on 2006-09-09
> **Jerk said:**
> Golgoth, I have the same exact issue. I'm going to try editing [FONT="Courier New"]/etc/network/interfaces[/FONT] again.

I'll let you know if it works.

Just to say, my wusb54g v4 works with Edgy using the rt2750 provided by the kernel (2.6.17) in edgy.

---

### Post by tmtim on 2006-09-10
Is there a way to use the rt2570 kernel driver that you talk about in Dapper Drake instead of having to get Edgy?. I'm using ndiswrapper 1.8 in Dapper drake and am having problems with my connection dropping randomly and then never being able to get it back to working again without rebooting the whole computer.  

I just LOVE using ubuntu/linux but my only connection available to my room is  wireless network. I always end up back in windows because i have no reliable connection in linux :( If there isn't a native driver i could use in dapper drake like there is in edgy(assuming native = more reliable). Is there another card one could recommend for use in linux? USB or PCI is fine..


Thanks!
-tmTim

---

### Post by tmtim on 2006-09-10
Oh btw i've already tried the newer driver from linksys as well as the one on the CD with no difference. thought i'd add that in there before I got any replies.

-tmTim

---

### Post by lupine_nickt on 2006-09-12
The rt2570 driver can be compiled for Dapper - or alternatively, I've done all the hard work for you :). [http://www.ubuntuforums.org/showthread.php?t=240669](http://www.ubuntuforums.org/showthread.php?t=240669)

Regarding Edgy, it currently has the following ralink drivers (this is kernel 2.6.17-7-386):-

rt2x00-legacy: rt2400 - CVS 2005/07/11
rt2x00-legacy: rt2500 - CVS 2005/7/10
rt2x00-legacy: rt25780 - Beta 1 (2005/7/31)

rt2x00: rt61pci
rt2x00: rt73usb

Both of the new (rt2x00) drivers have no version on them - all I can see is that they're CVS. rt2400, rt2500 and rt2570 drivers for the new rt2x00 aren't in there right now.

What this basically means is that they're still out of date ;). However, more cards "should" work out of the box (including mine - although the rt2570 driver has made leaps and bounds in terms of stability over the last year). 

The firmware for the rt61 is also included in the linux kernel package... however, the rutilt package is still nowhere to be seen.

Once edgy is released, I think I'll update the repository with the rt2x00 drivers, and update the legacy drivers as well. 

xF,

...Nick

---

### Post by windquest on 2006-09-12
I thought I would update my other posts with this short version.If anyone wants more infor, just ask. Out of frustration, I took one of the comments to try the native drivers. Here are the steps I used for success.

Fresh install of Ubuntu from scratch (Note: do not attach any USB device or any adapter)

Reboot

After the Reboot, plug in the WUSB54Gv4 and go to System> Network 
You should find your adapter as RUSB0. Confugure the card. (It should see the local SSID's available)

Click OK and exit WITHOUT Activating 

shutdown > disconnect the adapter

Startup

Connect the adapter and go again to Networking....activate the adapter

You should be on the internet!!!!!

Notes: Remember to disconnect the card for each boot. After booting you can disconnect and reconnect the card at will BUT you must reboot anytime you change the configuration and then re-activate as above. I hope this helps someone.
Henry

---

### Post by Protonz on 2006-09-20
@windquest: I tried everything in this thread but your solution actually worked :)

I don't even have to disconnect the adapter after each boot.

---

### Post by kpictjl on 2006-09-30
Step 1 says to download and install ndiswrapper.  Here do I download the file to?  My home directory? Desktop or where?  I'm just used to windows so I don't understand the "my downloads" or "program files" equivalent in linux.

---

### Post by boz on 2006-10-21
> **windquest said:**
> I thought I would update my other posts with this short version.If anyone wants more infor, just ask. Out of frustration, I took one of the comments to try the native drivers. Here are the steps I used for success.

Fresh install of Ubuntu from scratch (Note: do not attach any USB device or any adapter)

Reboot

After the Reboot, plug in the WUSB54Gv4 and go to System> Network 
You should find your adapter as RUSB0. Confugure the card. (It should see the local SSID's available)

Click OK and exit WITHOUT Activating 

shutdown > disconnect the adapter

Startup

Connect the adapter and go again to Networking....activate the adapter

You should be on the internet!!!!!

Notes: Remember to disconnect the card for each boot. After booting you can disconnect and reconnect the card at will BUT you must reboot anytime you change the configuration and then re-activate as above. I hope this helps someone.
Henry

This worked for me.  Perhaps the orginal author of this thread could append his advice to the original message?

---

### Post by jerrallan on 2006-10-22
I followed the directions and the hardware and driver for the WUSB54G was successfully installed.  But I still cannot get an internet connection.  I ve followed the advice given me and the troubleshoot networks on this site.
I do iwconfig, dhclient and I know that the wireless device is recognizing the access point but cannot get a lease.

I think this is barking up the wrong tree, but one commenter on this thread
said that he successfully installed this driver using rausb and the 2570 driver.

I wonder how he went about doing that?  When I tried to configure using rausb the screen froze up.
Thanks

---

### Post by jerrallan on 2006-10-22
Okay, it looks like I succeeded in connecting to the internet.
I went back and uninstalled ndiswrapper. I commented out the line to blacklist rt2570.

If I go to System>Administration>Networking it tells me that rausb is not configured. If i configure it the screen freezes up and I have to reboot.

I can configure rausb through sudo iwconfig rausb0 essid <xxxxxx>
then sudo iwconfig rausb0 encryption on, then sudo iwconfig rausb0 encryption 
<xxxx-xxxx-xx>.
Then it works.

I found out later if I rebooted, that I lost my internet connection and had to go through the above procedure again.  Also, I added this line to "pump" for a connection: sudo dhclient rausb0

I  added all of this to a script to semi-automate reconnecting to the internet.  Any suggestions for a more permanent fix?
Jerry

---

### Post by acorn22 on 2006-10-24
I have a WUSB54G version 4 and it says invalid driver!

I tried the version 1 and 2 as well.

I am using KDE, Dapper

**EDIT**

I had to make sure the sys and cab files where in the same directory as the inf file. 

So I uninstalled everything from ndis and re-installed and inf file which i put in a folder with the other files I needed. Hope that helps somebody else.

---

### Post by bionnaki on 2006-10-25
here's how to install a **wmp54g**: [http://ubuntuforums.org/showthread.php?t=241565](http://ubuntuforums.org/showthread.php?t=241565)

perhaps it'll help this thread or others looking for tips.

---

### Post by Erik. on 2006-10-25
I am looking for a topic for the WMP54G pci v2

---

### Post by bionnaki on 2006-10-25
do you use the rt2500 driver?

---

### Post by Yourname on 2006-10-30
Same instructions for EDGY connecting to a WPA2 (AES) network?

---

### Post by thewatts on 2006-11-05
WUSB54Gv4 Issues:

ive blacklisted rt2570, ive installed the newest version of ndiswrapper, and installed the rt2500usb.inf file from my cd using ndiswrapper --- and when i type in the code:

ndiswrapper -l


i get:

"rt2500usb   invalid driver!"

any suggestions?

i have a new .exe file from the linksys website - - but i dont know how to unzip it to get to the latest .inf file. 

thanks :D


PS - it also says that my hardware isnt present in the ndiswrapper interface... but its definately plugged in and works with my windows partition..

---

### Post by chris.olsen on 2006-11-10
Little problem here.

when I try to do the sudo make uninstall I get the error:
----------
chris@chris-ubuntu:~/Desktop/ndiswrapper-1.8$ sudo make
make -C driver
make[1]: Entering directory `/home/chris/Desktop/ndiswrapper-1.8/driver'
Can't find kernel sources in /lib/modules/2.6.17-10-386/build;
  give the path to kernel sources with KSRC=<path>             argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/chris/Desktop/ndiswrapper-1.8/driver'
make: *** [all] Error 2
----------

I am not sure what to do to fix this.  Any help would be appreciated.

---

### Post by Mediciman on 2006-11-11
Any Things like that for Edgy?
With the same Router and everything?

---

### Post by mysticrider92 on 2006-11-18
](*,) OK.  I have attempted to install a V1 card and now I can't even see the card.  I blacklisted islsm_usb, uninstalled ndiswrapper and then reinstalled.  So far, nothing.   Has anyone been able to make a V1 usb card work?

[edit] Finally got it working after a good bit of playing with it.

---

### Post by Wienerbatzi on 2006-12-07
> **bionnaki said:**
> sudo <command>

For some reason I keep getting line errors, when typing sudo <command> into the terminal window.

---

### Post by DirtDawg on 2006-12-12
> **chris.olsen said:**
> Little problem here.

when I try to do the sudo make uninstall I get the error:
----------
chris@chris-ubuntu:~/Desktop/ndiswrapper-1.8$ sudo make
make -C driver
make[1]: Entering directory `/home/chris/Desktop/ndiswrapper-1.8/driver'
Can't find kernel sources in /lib/modules/2.6.17-10-386/build;
  give the path to kernel sources with KSRC=<path>             argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/chris/Desktop/ndiswrapper-1.8/driver'
make: *** [all] Error 2
----------

I am not sure what to do to fix this.  Any help would be appreciated.

Cmon somebody, what is the problem here because I get the same error. I've spent the last two damn days trying to get ANY of my 3 wireless cards working and I'm at wits end. I'm about to say "Screwbuntu!"

Any ideas at all?'

---

### Post by DirtDawg on 2006-12-12
EDIT: I decided a quick "how I fixed this" is better than a crazy, frustrated rant. After I calmed down, I tried once more with a fresh install. After that, I followed the instructions listed in the O.P. again except I installed the ndiswrapper that came with the Live CD and executed these three commands before rebooting(as suggested a few posts later):
```
sudo depmod
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```
It should also be noted that when I reinstalled, I had only the usb wireless plugged in where before I had both the usb and another wireless card plugged in. I'm not sure that makes a difference.

---

### Post by haiku99 on 2006-12-19
> **IrishMLK said:**
> Thanks lmp!

I did this and have no problems now on my old Compaq Presario 1700 laptop. Even after I rebooted, my WUSB54G v.4 was linked before the login screen for Xubuntu popped up.  All without ndiswrapper and much headache.

yep, me too...configuring WITHOUT activating, rebooting and THEN activating was the key, this also w/ a v4 card, built in Dapper drivers and no ndiswrapper.  THis is great, as I also have a built in wifi card that must use ndiswrapper, so I can still use either, AFAIK ndiswrapper can only run one card on a given machine.  FWIW I usually use my internal card, but need to use an external card with a wifi wok to reliably use the local freenet in my town.....
signal strength graphic and wifi radar are not working w/ the usb card, but I can live w/ that

edit---   after reading a few other posts I learned that cofiguration lockups can be avoided by manually editing the configuration file
  (i.e. sudo gedit /etc/network/interfaces)  when changing ESSID's, WEP keys, etc.....the networking GUI tool does NOT like this adapter

edit2-  changed from Dapper to Edgy (clean install), was able to get the card working w/ the builtin drives again

---

### Post by BNoohi on 2006-12-27
Hi there, quick question. I've managed to make ndiswrapper before but for some reason I can't now. I'm trying to make version 1.32. After the untar process, I go to the directory, type make and get this:

make -C driver
make[1]: Entering directory `/home/bardia/Desktop/Help files/ndiswrapper-1.32/driver'
make -C /lib/modules/2.6.18-1.2798.fc6/build SUBDIRS=/home/bardia/Desktop/Help files/ndiswrapper-1.32/driver
make[2]: Entering directory `/usr/src/kernels/2.6.18-1.2798.fc6-i586'
make[2]: *** No rule to make target `files/ndiswrapper-1.32/driver'.  Stop.
make[2]: Leaving directory `/usr/src/kernels/2.6.18-1.2798.fc6-i586'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/bardia/Desktop/Help files/ndiswrapper-1.32/driver'
make: *** [all] Error 2

Any ideas?

p.s. I've already done "make uninstall" before using the make command.

---

### Post by nighthawke on 2007-01-01
The procedures work in Edgy with a WUSB54G  Ver.4. Used the synaptic version of NDISwrapper for the process and it is stable.

---

### Post by thammer on 2007-01-03
I have tried some of the same fixes. Every time I try to add rt2570 to the blacklist it says its a read only.

---

### Post by Awperator on 2007-01-12
> **thammer said:**
> I have tried some of the same fixes. Every time I try to add rt2570 to the blacklist it says its a read only.

Make sure you're using Sudo when you edit. Maybe you don't have admin privileges.

---

### Post by mudflapz on 2007-01-24
I noticed that this tutorial says that most people with the bcm4318 driver can't use this tutorial.  Can anyone point me to a tutorial that is for the bcm4318?

---

### Post by deusknight on 2007-01-26
Does this all work for the WUSB54GC?  I see alot of ppl using v4.....

---

### Post by robinsingh on 2007-01-27
> **mattoman said:**
> Alrighty Thanks it works great. 

I have to run those two last commands:
sudo depmod
sudo modprobe ndiswrapper

The only problem is I have to run them everytime i restart, any way to resolve this? Thanks!

Matt

Thanks for the instructions, I temporarily :-(  got them working for W54USB v4 
on Ubuntu 6.10 Edgy. My problem started happening after running the command
ndiswrapper -m ( on a perfectly running setup)..
Initially, when I got it working after following the original instructions(from user-g3r41d).

Admin > network was showing the wireless connection , i provided the details and enabled it. It showed the message, activating the network interface. 
Then I went to the Network MAnager applet (in the system tray) , right clicked and I saw two options - wired connection and wireless connection . I clicked on wireless connection and provided my network name etc. And it showed excellent connection and i could browse the web without any issues. 

But then I was having to run the above mentioned commands everytime.

so i read the next message (from the user-kewldude606)  in this post and did 
ndiswrapper -m
hoping that this will fix the issue of having to run the above two commands after every system restart.

My problem started happening then onwards.
I ran the command and restarted the machine. 
Now even though my Admin > networking does show the Wireless connection listed for rt2500usb device. I can enable it after providing the details and it even says activating the network interface....

but the taskbar icon(double-computer icon a.k.a Network Manager applet) does not show the option of wireless connection when i right click on it.  It only shows wired connection option. 

I dont know how running the command ndiswrapper -m could screw the whole thing.

I tried running the two commands
sudo depmod
and
sudo modprobe ndiswrapper   (didnt help)

I even tried adding ndiswrapper at the bottom of /etc/modules. and restarting (didnt help)

After that I even tried removing and re-installing the rtusb2500.inf  by
sudo ndiswrapper -e rt2500usb
and then 
sudo ndiswrapper -i rt2500usb

even though 
sudo ndiswrapper -l   output shows 
rt2500usb  driver present, hardware present  ( didnt help)

Same issue, admin >network shows the wireless connection and lets me activate it.
But the network manager applet does not show the option of wireless connection so that i can click on it and connect to the network.''


PLEASE HELP ....  :confused:

---

### Post by robinsingh on 2007-01-27
nvm i found that its just a stupid issue with network manager applet itself. 
I can access internet through the wireless adapter on system restarts (*without runnning any commands)

its just network manager applet still does not show the wireless connection option available. it just shows wired connection available. 

Any idea, how can i make the network manager show the wireless connection option. 
since i might want to change the security settings for my network tomorrow and then might need network manager to let enter the password etc. 

what do you guys think ?

robin

---

### Post by M$LOL on 2007-02-11
I'm using Edgy AMD64, and I keep getting

```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/misc/ndiswrapper.ko): invalid argument
```

whenever I try sudo modprobe ndiswrapper. What's going on?

---

### Post by rtonyb on 2007-02-21
I have been trying this with my WUSB54Gv4, but on the last line (trying to run 'sudo ndiswrapper -i ~/WUSB54Gv4/rt2500usb.inf') I get the following error:

unable to execute /usr/sbin/ndiswrapper: no such file or directory

I can see the file there, but it's 'grey' not sure what that means...can anybody help me?
Thanks!

---

### Post by gradedcheese on 2007-02-21
> 
I can see the file there, but it's 'grey' not sure what that means...can anybody help me?


```

sudo chmod +x /usr/sbin/ndiswrapper

```

---

### Post by rtonyb on 2007-02-22
Thank you.  I will try this tonight and report back!

---

### Post by rtonyb on 2007-02-22
> **gradedcheese said:**
> ```

sudo chmod +x /usr/sbin/ndiswrapper

```

I tried this, nothing really is displayed afterwords but I do think it changed the permissions.  Then I retried the last step in the ndiswrapper install and still the same error message that it is 'unable to execute /usr/sbin/ndiswrapper: No such file or directory'

Any other ideas?
Thanks in advance.

---

### Post by gradedcheese on 2007-02-22
hmm... run this to check the permissions, post them here:

```

ls -l /usr/sbin/ndiswrapper

```

(that's "LS minus L")

---

### Post by rtonyb on 2007-02-23
> **gradedcheese said:**
> hmm... run this to check the permissions, post them here:

```

ls -l /usr/sbin/ndiswrapper

```

(that's "LS minus L")

OK, here's the output from running: ls -l /usr/sbin/ndiswrapper
-rwxr-xr-x 1 root root 21431 2007-02-22 21:15 /usr/sbin/ndiswrapper  (/usr/sbin/ndiswrapper is in green)

-Thanks

---

### Post by gradedcheese on 2007-02-23
that's odd, it should run then.  Try running it manually (just run "/usr/sbin/ndiswrapper" literally)

---

### Post by rtonyb on 2007-02-23
Figured it out...had to also install the ndiswrapper tools package in synaptic.
Thanks for all your help.

---

### Post by 720iD on 2007-02-24
some people have been asking how to install wusb11 i have linksys wusb11v4 myself which i have struggled to get working for sometime until now. after reading this thread, i have got mine working very simply but being newb i had not known how or where to go. here is what i did.

installed ndiswrapper using synaptic and using the repositories that come as dvd iso. this installed ndiswrapper1.8 

i used the gui version of ndiswrapper which was located in system menu.
browse to the folder where the driver wusb11v4 was located. [i had extracted the .exe file under windows] then selected the driver with ndiswrapper.

i got a message driver installed and hardware present.

there is a menu in ndiswrapper to configure device

configure network [name of network essid and network key if using one]

set enable this connection [wireless connection will now be in network settings window]

ok

reboot the system. connected to internet straight away.

---

### Post by Lapsi on 2007-02-25
Has anybody managed to get the WUSB54G v.1 to work with the latest Xubuntu? I have tried all the methods posted here but none of them seem to work. And how do I edit the blacklist file if the command in the first method did not work?

---

### Post by rslynch on 2007-02-25
i just took the plunge and switched from linux to windows yesterday.  your tutorial worked great.  thanks for the help!!

---

### Post by rslynch on 2007-02-25
> **rslynch said:**
> i just took the plunge and switched from linux to windows yesterday.  your tutorial worked great.  thanks for the help!!

i mean from windows to linux of course:)

---

### Post by Lapsi on 2007-02-26
Ok. After two hard-working days I managed to get the WUSB54G v.1 work with Xubuntu.

I had to install the build-essentials, wlan-package and kernel-headers.

Then I blacklisted rt2570 and islsm_usb to get the w-lan disappear.

Then I read the 
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation) 
to get the 

ln -s /usr/src/linux-<kernel-version> /lib/modules/VERSION/build 

command (which was kind of tricky to a newbie like me), because without it I couldn't install the ndiswrapper I got from this thread. After that I just followed the sections written by G3r41d and I was careful to first configure and then boot and then activate the device.

Thank you guys for all your help!

---

### Post by Yellohead on 2007-03-01
Ongoing problems getting my WUSB54G (no version number) up and running on My 
AMD64 version of 6.10.

no problems with step 1, and with installing ndiswrapper 1.8, which i found on my ubuntu installation cd.  

I have the latest driver for my device from the linksys website (wusb54gv2), which is in my user directory.

When I input the command "sudo ndiswrapper -i wusb54gv2.inf", I get the following:

installing wusb54gv2
couldn't copy wusb54gv2 at /usr/sbin/ndiswrapper- 1.8 line 144

What does this mean?  What should I try next?

I am visiting this forum through the dark side of my dual boot system, and eager to get the light side up and running!

---

### Post by Zacharius on 2007-03-02
Ok, I am completely new to Ubuntu but I followed this guide and managed to get everything to work but once I completed it, I rebooted and went to system>admin>netoworking and wireless isn't there to choose from.

Could someone please help I have been up since 10am yesterday.

edit: I started over from scratch and now everything seems to be fine.

---

### Post by Yellohead on 2007-03-03
> **Yellohead said:**
> Ongoing problems getting my WUSB54G (no version number) up and running on My 
AMD64 version of 6.10.

no problems with step 1, and with installing ndiswrapper 1.8, which i found on my ubuntu installation cd.  

I have the latest driver for my device from the linksys website (wusb54gv2), which is in my user directory.

When I input the command "sudo ndiswrapper -i wusb54gv2.inf", I get the following:

installing wusb54gv2
couldn't copy wusb54gv2 at /usr/sbin/ndiswrapper- 1.8 line 144

What does this mean?  What should I try next?

I am visiting this forum through the dark side of my dual boot system, and eager to get the light side up and running!

Just got rid of the 64 bit version, installed the 32 bit version.  Now, no wireless device icon shows up in the network display.

I followed the steps, and I am still getting the same error:

couldn't copy wusb54gv2 at /usr/sbin/ndiswrapper- 1.8 line 144

What should I try next?

---

### Post by RealG187 on 2007-03-14
It's wierd I have this card and have no issues [it's ironic how I have the one mentioned here!].

I had no troulbe, I just typed in my WEP and it worked, but then again I was in Edgy, so I guess Edgy works with this card while Drake doesnt...

---

### Post by Yellohead on 2007-03-20
> **RealG187 said:**
> It's wierd I have this card and have no issues [it's ironic how I have the one mentioned here!].

I had no troulbe, I just typed in my WEP and it worked, but then again I was in Edgy, so I guess Edgy works with this card while Drake doesnt...

Would that be WUSB54G without a version number?  If so, what driver are you using?  Did you use ndiswrapper?

---

### Post by RealG187 on 2007-03-21
I wasnt using Ndiswrapper {i have it but not installed}.

I was using Edgy Eft w/ Firefox, I tried a torrent and it didn't work, but that might just be the torent....

---

### Post by Tunica Intima on 2007-03-24
I did all of the steps in the tutorial but i keep getting an invalid driver messge

---

### Post by benutne on 2007-03-26
I finally got the v1 adapter working after installing the Gnome frontend for ndiswrapper and using that.  Seems only WEP works for now though.  It doesn't seem to hold a connection after a reboot though.  I have to remove the device and add it again to get it to work.

---

### Post by dawv on 2007-03-26
is there any way i can do something similar to this to get my Airlink101 AWLH3026T to work... my system dosen't detect it AT ALL.. and im new to linux, so i don't know where to begin....

---

### Post by RealG187 on 2007-03-26
Do I need to do this if I am in Edgy? Or is this only for Dapper Drake?

---

### Post by influensi on 2007-04-25
Ok, so thanks to this thread I have internet access with my WUSB54G (no version number, so I assume v1). However, after about 30 minutes to an hour, the signal abruptly drops to zero and I cannot reconnect unless I restart my computer. Even disabling/re-enabling the adaptor doesn't work. I've tried ifdown/ifup, and if I'm even using it correctly, it doesn't work either. I've seen this bug mentioned in a few other places but with no responses on how to fix it. Any ideas?

---

### Post by RealG187 on 2007-04-26
I think it works w/ Edgy as it! Not even Windoze does that!! U need the driver, but in Edgy u dont!

I feel sorry for dapper users!

---

### Post by gwhitener on 2007-04-29
I recently upgraded to Feisty, hoping that would solve the issue, but it didn't.

Here is what did:

[http://ubuntuforums.org/showthread.php?p=2557642#post2557642](http://ubuntuforums.org/showthread.php?p=2557642#post2557642)

Cheers

---

### Post by RealG187 on 2007-04-29
> **gwhitener said:**
> I recently upgraded to Feisty, hoping that would solve the issue, but it didn't.

Here is what did:

[http://ubuntuforums.org/showthread.php?p=2557642#post2557642](http://ubuntuforums.org/showthread.php?p=2557642#post2557642)

Cheers

hold up!

is urs a card? is this thread  about a pci card? mine is a usb thing....

---

### Post by gwhitener on 2007-04-30
No, it's a USB based adapter.  I was considering moving to a PCI card, but now no need.  I can't see other networks (or even mine, which is WEP encrypted, but publicly visible), or the strength of my signal, but I consistently get 200+kbps download speeds, so I am not complaining.

Have you tried this out, did it work for you?

---

### Post by zmigliozzi on 2007-05-09
> **moitio said:**
> Make sure that after you do all the steps in the tutorial, do:

sudo depmod
sudo modprobe ndiswrapper

that did it. thanks for the help as well.

---

### Post by RealG187 on 2007-05-09
Just to clear things up:

The WUSB54G works with Edgy and Fiest right? For me it worked in Edgy, so it should work in Edgy too, like if the new version supported less ahrdware it wouldnt be as good and that defeats the purpose of updating!

Also, my Laptops built in Wireless worked in Edgy, I think it was either Ubuntu or Xubuntu, if my laptop works in Edgy will that work in Fiesty? I wanna use it with Kubuntu 7.04 [got my CDs today!], so should it work in Kubuntu 7.04 if it works w/ 6.10 [K*]ubuntu

* I put the K in brackets cuz I cant remember if it was Normal ubuntu [Gubuntu] or Kubuntu..

---

### Post by tatoogoo on 2007-06-05
HI,
I'm new to Ububtu although I played with Linux about 10 years ago and so have some basic idea. I'm trying to install a Safecom SWLUS-1100 USB WLAN and am having no luck at all. I read every reference I can about ndiswrapper but don't seem to be able to get it installed on my machine. When I try to install it I get a message saying that DPKG-DEV is needed - I install that and get a message that the same version is already installed however, modprobe tells me it isn't there. When I persist in trying to install ndiswrapper again, I get a message saying that DPKG-DEV cannot be installed - I'm stumped! The wlan is the only way I can get the linux machine to talk to the internet as its permanently hooked up to a milling machine (the linux distro I'm trying to install is the Dapper Drake raltime version with EMC2 integrated into it), and so, to install new packages at the moment I have to try to find suitable packages using a Windows machine and transfer them to the linux machine via a USB memory stick - all very long winded and boring when linux keeps deciding that it needs extra little packages before it will install new apps and each new package requires a trip up and down stairs between the computers - hence the great desire to get the linux machine talking to the internet as quickly as possible. Any help will be gratefully recieved - please assume I am totally ignorant as I seem to have been missing something very fundamental up to now!! Thanks..

---

### Post by NfF on 2007-06-13
hemmm...ive got a question...

im using 7.04 ubuntu feisty fawn now...so are the installion different,or same?
my adapter is ver4 too.





REPLY ME IN PRIVATE MSG.
TY

---

### Post by douradinhos on 2007-06-14
thanks, works fine with Feisty and WUSB54G ver4 :KS

---

### Post by mick99 on 2007-06-18
> **douradinhos said:**
> thanks, works fine with Feisty and WUSB54G ver4 :KS
So, just to clarify, would these instructionl work with a WUSB54G Ver.4 on 7.04 Xubuntu?  I tried the command in step one and it wasn't recognized at all.  is there any really obvious first step that I'm missing?

---

### Post by kranky on 2007-06-27
i thought this was the appropriate place for general WUSB54G problems, but apologies if it isn't...

i'm using the WUSB54G, version 4 adapter with and AMD64 version of feisty fawn.  my internet seems to work for the most part. however, i also have the intermittent connection dropping that other people have mentioned, and my wireless menu shows 0% signal strength for all networks!  i'm pretty sure that this is wrong because using a borrowed adapter on the same computer i see good signal strengths across the board.

does anyone know what could be wrong?  any help would be appreciated.  thanks in advance.

---

### Post by uuow on 2007-07-04
were can i download WUSB54G:p:popcorn::KS

---

### Post by vehorenkamp on 2007-07-10
This post looked promising until I tried it.  When I went to admin_.networking, I showed a wireless connection (eth1), a wired connection (eth0, I think) and a modem connection.  I did not find rausb0 wireless.  When I look in device manager, I don't see any error indicators, but I do see that my WUSB54G is completely unrecognized.  I'm running Dapper Drake (6.06) on the same physical machine as Vista Business.  I switch hard drives in the setup menu.  I know that the adapter works and that Vista recognizes it immediately.  Any ideas?  It seems like everybody and their brother is having problems getting this adapter to work.  I can't get any adapter cards to work either.  

Thanks.

Vince Horenkamp

---

### Post by be4truth on 2007-07-11
I connected a Linksys WUSB54G Ver.4 to my xeron laptop and installed Ubuntu Mint. After the installation it worked out of the box. Haven't checked with encryption but otherwise works fine.

---

### Post by be4truth on 2007-07-11
1 character

---

### Post by soluphobe on 2007-08-03
I'm using 7.04 Ubuntu, trying to install a WUSB54G**SC** adapter.  I ran through the processes in the sticky, but some things don't fit.

First, I never saw a rausb0 wireless.  I blacklisted the rt2570 driver anyway, figuring that it couldn't hurt (Yeah, I know, I unblacklisted it later).  I had some problems installing ndiswrapper, but I installed some packages from the CD and now ndiswrapper works fine (using 1.47).

So, here's my issue.  The adapter is simply not recognized by my system.  When I plug it in (after the install and login) the light comes on, though I know there are no wireless networks for it to pick up (it works fine on my XP partition...I think).  

When I fiddle around with ndiswrapper from the terminal (with the adapter plugged in), I get the following:
```
root@SG:~# sudo ndiswrapper -l
wusb54gsc : invalid driver!  /*   this is what I'm worried about   */
root@SG:~# sudo ndiswrapper -m
module configuration already contains alias directive

root@SG:~# $lsmod | grep islsm
/*  nothing   */
root@SG:~# iwconfig
lo		no wireless extensions

eth0		no wireless extensions

root@SG:~# sudo depmod
/*  long pause   */
root@SG:~# sudo modprobe ndiswrapper
/*  short pause - nothing changes   */
/*  here I repeat everything - no changes   */
root@SG:~# exit
```

So *nothing* shows up when I do lsmod | grep islm (or the $ variation).  I looked through lsmod, but nothing really caught my eye (except that ndiswrapper was running).  

As an experiment, I tried unblacklisting the native drivers (I suspect I'm blacklisting the wrong ones anyway).  Nothing happened.  In Network Tools, I still got just three entries:  Loopback, eth0, and eth0:avahi.  So I re-blacklisted stuff, this time the entries from Vuul's guide.  Nothing.  I've edited the modules file and added ndiswrapper, but I can't see any obvious differences.

I'm using the driver from the CD (I've uninstalled/reinstalled it repeatedly through ndiswrapper -e/i , with no errors) and the latest ndiswrapper - what am I doing wrong?  Do I need to get a different driver?

Thanks in advance!

---

### Post by xjgnsdof on 2007-08-19
After inputting sudo make install in the extracted ndiswrapper folder, I get this:

```
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.200-16-generic/kernel/ubuntu/misc/ndiswrapper/bin/rm: cannot remove /lib/modules/2.6.200-16-generic/kernel/ubuntu/misc/ndiswrapper/': Is a directory
make:  *** [uninstall] Error 1'
```

What's going on?

---

### Post by wieman01 on 2007-08-20
> **elgilicious said:**
> After inputting sudo make install in the extracted ndiswrapper folder, I get this:

```
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.200-16-generic/kernel/ubuntu/misc/ndiswrapper/bin/rm: cannot remove /lib/modules/2.6.200-16-generic/kernel/ubuntu/misc/ndiswrapper/': Is a directory
make:  *** [uninstall] Error 1'
```

What's going on?
I would install "ndiswrapper" from the repositories. This guide is a bit outdated... the latest version in the repositories should do.
> sudo apt-get install ndiswrapper-utils-1.9

---

### Post by l337_G33K on 2007-08-21
---
(Wrong Place)

---

### Post by soluphobe on 2007-08-27
Just found this out.

If you keep getting an 'invalid drivers' error from ndiswrapper, what you need to do is get ahold of the files **usb8023.sys** and **rndismp.sys** from a windows partition (WINDOWS/system32/drivers), then copy them into etc/ndiswrapper/<driver name> .  Ndiswrapper will now recognize your driver!

(My internet doesn't work yet, but I'll find a way...)

EDIT:  I think I got it working!  Now all I have to do is test it on some network somewhere...

---

### Post by jrmink on 2007-09-18
I want a simple answer to the following question.  Will this guide work for ubuntu fiesty 7.0.4 and if not what changes must I do to get my linksys WUSB54g wireless adapter working?

---

### Post by wieman01 on 2007-09-18
> **jrmink said:**
> I want a simple answer to the following question.  Will this guide work for ubuntu fiesty 7.0.4 and if not what changes must I do to get my linksys WUSB54g wireless adapter working?
Yes, it should. If not post here, we will help you out.

---

### Post by CoriolisSTORM on 2007-09-20
I have yet to get mine working on Feisty with this guide, I blacklist the driver that is preloaded for it (no WPA support) and do everything with ndiswrapper that is recommended and then when I reboot nothing shows up. Using preindtalled ndiswrapper also with newest drivers for the card, the device is present and so is the driver but nothing else happens.

---

### Post by jrmink on 2007-09-22
Seriously...

Its time some ubuntu staff or experts give guides on how to get all versions of the linksys wusb54g usb adapter to work.  Ive been trying to get my ver1 wusb54g to work for days and its still not working.

---

### Post by soluphobe on 2007-09-30
> **CoriolisSTORM said:**
> I have yet to get mine working on Feisty with this guide, I blacklist the driver that is preloaded for it (no WPA support) and do everything with ndiswrapper that is recommended and then when I reboot nothing shows up. Using preindtalled ndiswrapper also with newest drivers for the card, the device is present and so is the driver but nothing else happens.

I think that may be the same sort of thing I'm experiencing.  I've got the driver and device recognized, but I'm not getting any wireless extensions with iwconfig.  What driver did you blacklist?  I couldn't find the default one that comes with the adapter (just using the official one from the CD).

---

### Post by wieman01 on 2007-09-30
> **soluphobe said:**
> I think that may be the same sort of thing I'm experiencing.  I've got the driver and device recognized, but I'm not getting any wireless extensions with iwconfig.  What driver did you blacklist?  I couldn't find the default one that comes with the adapter (just using the official one from the CD).
You could blacklist all drivers listed in the tutorial. It does not do any harm at all.

What chipset have you got? Do you have a PCI or USB device?

---

### Post by rightmind on 2007-12-10
I am new Ubuntu linux. I follewed the instructions, and after I inserted the cd I installed the build essentials, but there was no "kernel headers". How can I get these headers, or update my kernal. That is the only thing preventing me for doing the make install. Below is some info that might help.



chris@chris-desktop:/lib/modules/2.6.15-26-386$ ls
initrd      modules.alias        modules.inputmap   modules.seriomap
kernel      modules.ccwmap       modules.isapnpmap  modules.symbols
madwifi     modules.dep          modules.ofmap      modules.usbmap
madwifi-ng  modules.ieee1394map  modules.pcimap     volatile
chris@chris-desktop:/lib/modules/2.6.15-26-386$
chris@chris-desktop:/lib/modules/2.6.15-26-386$ cd kernel
chris@chris-desktop:/lib/modules/2.6.15-26-386/kernel$ ls
arch  crypto  drivers  fs  lib  net  security  sound
chris@chris-desktop:/lib/modules/2.6.15-26-386/kernel$ cd drivers
chris@chris-desktop:/lib/modules/2.6.15-26-386/kernel/drivers$ ls
acpi       char       hwmon       input    misc     pci        usb
atm        connector  i2c         isdn     mmc      pcmcia     video
block      cpufreq    ide         md       mtd      scsi       w1
bluetooth  crypto     ieee1394    media    net      serial
cdrom      firmware   infiniband  message  parport  telephony
chris@chris-desktop:/lib/modules/2.6.15-26-386/kernel/drivers$ pwd
/lib/modules/2.6.15-26-386/kernel/drivers

Thank you for your help!

---

### Post by rightmind on 2007-12-14
I got it to work! I followed everything you all said. YOU MUST (least in my case) add the sudo ndiswrapper -m at the end. My wireless driver would not show other wise.

ALSO:I used synaptic to install the ndiswrapper for me. ALOT easier! I also used it to install kernel headers (linux-headers 2.6.15-25). Therefore I didn't have to deal with the make commands.

Synaptic (In Ubuntu Dapper Drake is found in System>Adminstration>Synaptic Package Handler. I needed to hook up to the internet via hard line for the updates to download.

Again, thanks all. Because fo your collective input I am posting this from my WUSB54Gv4 wireless adapter.
;)

---

### Post by 720iD on 2007-12-15
i managed to get this device working with edgy eft but struggling again with gutsy, has any body managed to get this going with gutsy?

---

### Post by Scott-271 on 2007-12-15
I've been struggling with this adapter for far too long on a T22 thinkpad. I started off with Xubuntu 7.10, then Ubuntu 7.10, Xubuntu 7.04. Ubuntu 7.04, Zenwalk 4.8 & 4.4, Vector 5.8, DSL and a few versions of Puppy, then back to Xubuntu 7.04 again,(if my cd burner didn't crap out on Slack 12 - disc 1, that would have had a chance as well)...I'm to the point, that I've seen enough people post that everything worked fine with Dapper - that's what is currently installed on the Thinkpad! Dapper-Xubuntu, of course. ;)

If it was possible to find a way to get a Windows/Xfce combo......right about now I might go for it....(please, nobody tell that there is..).

Anyhoo, now that I have Dapper installed and updated, I will try this out tomorrow, as well as checking out this [thread]("http://ubuntuforums.org/showthread.php?t=177836&highlight=xubuntu+wusb54g") too. So far I will say, after some tinkering around; I was able to get online for about a minute or so. I'm struggling between having to shut down FF and restart it to get back online; and having the whole comp freeze up, making me do a hard reset.

For the record, this whole process has cost a fortune in beer!

Scott

---

### Post by 720iD on 2007-12-16
okay now i am having real problems with this. i have installed ndiswrapper with gui from the latest repositories. i opened up ndiswrapper and selected what looked like the most approriate .inf file [wusb11v4.inf]. ndiswrapper says this is an invalid driver i uninstall that driver  and try the only other two inf files. none of these other drivers do anything. ndiswrapper is blank, nothing, zero. so i try take out my adapter and plug back in reboot to reinstall wusb11.inf, ndiswrapper is blank. nothing. i want to swear and blaspheme praising windows, for at least it works.

---

### Post by wieman01 on 2007-12-16
Guys, you could try the Ralink tutorial that you see in my signature. I has worked for some people. Post there if you have problems.

Pay attention to one thing though... if you happened to have installed the 64-bit version of Ubuntu, then you also need the 64-bit version of the Windows driver, otherwise it won't work. Just in case...

---

### Post by 720iD on 2007-12-16
> **wieman01 said:**
> Guys, you could try the Ralink tutorial that you see in my signature. I has worked for some people. Post there if you have problems.

Pay attention to one thing though... if you happened to have installed the 64-bit version of Ubuntu, then you also need the 64-bit version of the Windows driver, otherwise it won't work. Just in case...

your thread really helped. i just dont know the basics thats my biggest obstacle with ubuntu. following your thread i just copied what you wrote into my konsole, until i got to ! unzip <your_driver>.exe ! i have no idea how to do this kind of thing navigate directory and move copy files from terminal. 

so! i went back to the gui ndiswrapper thinking i may work now i managed to blacklist the other drivers and it did, it worked!  thank you!

---

### Post by wieman01 on 2007-12-16
> **720iD said:**
> your thread really helped. i just dont know the basics thats my biggest obstacle with ubuntu. following your thread i just copied what you wrote into my konsole, until i got to ! unzip <your_driver>.exe ! i have no idea how to do this kind of thing navigate directory and move copy files from terminal. 

so! i went back to the gui ndiswrapper thinking i may work now i managed to blacklist the other drivers and it did, it worked!  thank you!
Cool. Yes, the unzip section is a bit confusing I guess. Need to rewrite it perhaps. Thanks for the suggestion. :-)

---

### Post by Scott-271 on 2007-12-16
Hey Weiman01,

Yes, I've tried your tutorial, as well as kevdogs, and AlexMonos. I've tried every possible combination of distros/drivers/ndiswrapper. I've reformatted this laptop so many times, I can do a text-based installer in my sleep.

Everything short of (re)building the kernel has been tried. I will give this a shot on Dapper; if it doesn't work, the guys in the forums over at Mint Linux say this adapter works out of the box with Mint........I'll give that a try.

The worst part is, all I need this laptop for is so my wife can surf the net, and order things online; and all that's holding my back is this adapter.  ](*,)   The windows option is still there....she doesn't really care what's on the computer as long as Amazon.com ***is***.

---

### Post by wieman01 on 2007-12-16
> **Scott-271 said:**
> Hey Weiman01,

Yes, I've tried your tutorial, as well as kevdogs, and AlexMonos. I've tried every possible combination of distros/drivers/ndiswrapper. I've reformatted this laptop so many times, I can do a text-based installer in my sleep.

Everything short of (re)building the kernel has been tried. I will give this a shot on Dapper; if it doesn't work, the guys in the forums over at Mint Linux say this adapter works out of the box with Mint........I'll give that a try.

The worst part is, all I need this laptop for is so my wife can surf the net, and order things online; and all that's holding my back is this adapter.  ](*,)   The windows option is still there....she doesn't really care what's on the computer as long as Amazon.com ***is***.
All I can offer is that I guide you through every single step. There must be a solution, you have probably missed something... or you are simply unlucky.

To begin with, what system are you on right now? 32-bit or 64-bit? What exact wireless adapter have you got (version number, etc.) and where have you got the driver from?

Let's give it another try. :-)

---

### Post by Scott-271 on 2007-12-16
Ok, here's what I've got:

IBM T22 Thinkpad
PIII-900Mhz, 128 RAM
12G hdd - no dual boot, strictly one OS
WUSB54G**v4** USB adapter
WRT54Gv6 wireless router with DD-WRT firmware

I've gotten the drivers from: CD that came with adapter-had drivers for v.1, 2, & 4, downloaded from Linsys site, built rt2500 & rt2570 from serialmonkey, you name it, I've tried it.

I currently have alternate install discs for 6.06, 7.04, & 7.10 - all Xubuntu, with 6.06 installed now. I'm willing to reformat it again to whichever one would be the easiest to get working.

I'll give anything a try, but I'd really like to get it to work with Xubuntu. I'm really starting to get into this distro.

Thanks for your help weiman01,
Scott

EDIT: yes, I think that I am simply unlucky.......    >.<

---

### Post by wieman01 on 2007-12-16
Have you done every single step given in my tutorial? 

Please post:
> sudo iwlist scan
> sudo ndiswrapper -l
> sudo ifdown -v wlan0
> sudo ifup -v wlan0
> sudo cat /etc/network/interfaces

---

### Post by Scott-271 on 2007-12-16
I've just reformatted again.......this time with Xubuntu-Gutsy, and I'm just finishing up the updating.

I've installed nothing "extra", just a basic install/upgrade; and will be starting your tutorial fresh in a little while. Any/all problems/errors, I'll stop and post.

Should I continue this over in your tutorial thread?

Thanks again,
Scott

---

### Post by Scott-271 on 2007-12-16
Ok, problem........everything was going fine, I blacklisted rt2500usb, tried to install rt2500usb.inf.....no such file.blah,blah....I opened up the inf file, as well as moving .cat, .sys, and .inf to just my /home folder - not all in the "driver" folder in /home...came back and said "driver rt2500usb is already installed"..........ndiswrapper -l gives me "rt2500usb   : invalid driver!"

:S

---

### Post by 720iD on 2007-12-16
this device definitely works with gutsy stick with it. i was so frustrated at first. it was the same when i tried to install this with edgy when that came out. one thing to point out dont plug the adapter in until after you have the driver installed correctly then power off plug in device reboot and configure network.

---

### Post by rightmind on 2007-12-16
It works with Dapper Too.

---

### Post by wieman01 on 2007-12-18
> **Scott-271 said:**
> Ok, problem........everything was going fine, I blacklisted rt2500usb, tried to install rt2500usb.inf.....no such file.blah,blah....I opened up the inf file, as well as moving .cat, .sys, and .inf to just my /home folder - not all in the "driver" folder in /home...came back and said "driver rt2500usb is already installed"..........ndiswrapper -l gives me "rt2500usb   : invalid driver!"

:S
Have you followed my guide to the letter? 

Second thing is... Are you on Gutsy 64-bit or 32-bit? Where have you got the driver from?

---

### Post by 720iD on 2007-12-18
use the wusb11v4.inf driver from linksys website.

---

### Post by wieman01 on 2007-12-18
> **720iD said:**
> use the wusb11v4.inf driver from linksys website.
"wusb54v4.inf", is it not?

---

### Post by 720iD on 2007-12-18
@wieman01

oh yes! sorry

---

### Post by Scott-271 on 2007-12-18
I followed it exactly as it is written, double checking everything before hitting enter.

I have the 32bit - Xubuntu Gutsy, and the drivers from the cd that came with it.

I did do some tinkering around. I removed rt2500usb from the blacklist, installed the Ndiswrapper GUI from Synaptic, it listed the driver and I removed it. Rebooted. Opened up the GUI, and installed the driver from the disc, then blacklisted it again. Rebooted. Opened up N-M, and deactivated the wired connection and filled in the info for the wireless. Rebooted. Opened up N-M, and activated the wireless connection. Rebooted. Opened up Firefox, and got "Problem loading page", but **ndiswrapper -l** now lists the driver is installed and the device is present.

After that I tried everything, from when I plug the adapter in to how long I wait to open up FF. Currently, when the adapter is plugged in it slows the computer to a crawl, and after issuing commands in terminal, the whole thing freezes after about a few minutes; and the new thing is I lose use of the keyboard. I had a whole great big post with terminal outputs and everything ready to go.....and couldn't do anything after I copied and pasted it.

I'm getting ready to paint a target on the damn thing and get a really big hammer out. ](*,) 

I'm wondering if I should try the rt2570 from serialmonkey again? I have had this working with DSL 3.4.4 and Puppy, without any drivers installed on my part; but it would only last for about a minute. The other thing is, I have never wiped my /home, even with all the reformatting. I do have stuff from previous attempts still in there (like the rt2570 stuff), do I need to try this from a completely clean install?

Thanks so much,
Scott

---

### Post by wieman01 on 2007-12-19
@Scott-271:

Hang on, Scott. I think you are closer than you think. Please post the results of:
> sudo iwlist scan
> sudo ndiswrapper -l
> sudo lshw -C network

---

### Post by Scott-271 on 2007-12-19
Hey weiman01, here goes,

Ok, first of, having issues: 

 When I boot up **with** the adapter plugged in, Ndiswrapper says it's not present, and N-M does not list a wireless connection.

When I boot up **without** it plugged in, and then plug in at or after login window, it's present in both.

After I run those commands with the adapter (and only the adapter) plugged in, I get all the info. Once I unplug it, and plug in my ethernet cable; N-M won't open up and I lose all use of the keyboard.

So, with that being said, bear with me as I'm typing all this in on another computer, while looking at the laptop.

```

lynnette@myfrigginlaptop:~$ sudo iwlist scan
[sudo] password for lynnette:
lo         interface doesn't support scanning

eth0     interface doesn't support scanning

irda0    interface doesn't support scanning

wlan0   No scan results

lynnette@myfrigginlaptop:~$ sudo ndiswrapper -l
rt2500usb  :  driver installed
              device  (13B1:000D) present  (alternate driver:  rt2500usb)
lynnette@myfrigginlaptop:~$ sudo lshw -C network
   *network
          description:  Ethernet interface
          product:  82557/8/9 Ethernet Pro 100
          vendor: Intel Corporation
          physical:  id: 3
          bus info:  pci@0000:00:03.0
          logical name:  eth0
          version:  0c
          serial:  00:03:47:74:7e:f6
          size:  10MB/s
          capacity:  100MB/s
          width:  32 bits
          clock:  33MHz
          capabilities:  pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
           configuration:  autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=half firmware-N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *network
         description:  Wireless interface
         physical id:  1
         logical name:   wlan0
         serial:  00:12:17:76:98:ac
         capabilities:  ethernet physical wireless
         configuration:  broadcast=yes driver=ndiswrapper+rt2500usb driverversion=1.45+Linksys,04/13/2005, 2.00.02 link=no multicast=yes wireless=IEEE 802.11g
lynnette@myfrigginlaptop
```

A few more things:
I tried the adapter with dhcp and static, made no difference; but the adapter lights were going crazy when I opened FF. It also slows the computer to a crawl.

 I have the adapter placed about 3 feet from my router, which has no security settings engaged yet. I tackle that once this is working.

I really have nothing in /home except for my FF and desktop settings, so wiping it clean and starting from scratch is not a problem. I've also noticed that when I restart, it'll list all the processes being shutdown but will hang/freeze when it gets to "* Will now restart". I have to do a hard reset to get it to move past there.

I don't know if all these problems are due to trying to install this or not, but if starting from a completely clean slate is going to help...I'll do it. With a recommendation of which version to use that has the best success rate.

Thanks,
Scott

---

### Post by wieman01 on 2007-12-19
**@Scott:**

You know what... I think I experienced the same problem when I still had Dapper on my PC. I think your version of "ndiswrapper" is defective, so what I did back then was to compile the latest CVS version of "ndiswrapper" which worked fine.

The scan results do not look promising, your computer slowing to a crawl also suggests that "ndiswrapper" is not doing it's job. Would you consider compiling it from source? I think it might help,

---

### Post by Scott-271 on 2007-12-19
I've done it a few times before using kevdog's guide, which I'll use again. The though of wiping the comp clean and starting fresh is tempting though.

---

### Post by wieman01 on 2007-12-20
> **Scott-271 said:**
> I've done it a few times before using kevdog's guide, which I'll use again. The though of wiping the comp clean and starting fresh is tempting though.
Don't reinstall just yet. Try to recompile "ndiswrapper" first and post your results here. This is really, really odd.

---

### Post by Scott-271 on 2007-12-21
Well, it didn't go as well as it has before. It totally froze/crashed everything on reboot.

So, here's what I'm planning on doing.
[LIST]
[*]Reinstall Xubuntu 7.10, and upgrade
[*]Download Ndiswrapper from sourceforge, then install according to kevdog's guide, without installing the drivers
[*]download both rt2500 and rt2570 from rt2x00 (and build according to AlexMono94's guide) and start with rt2500usb after ndiswrapper is installed
[*]install rt2500usb according your guide
[/LIST]

It's going to be a little while until it's installed and upgraded, so if there's any changes to my plan that need to be made, let me know.

I'll post any/all errors/issues/successes.

I really appreciate all the help!

Thanks,
Scott

---

### Post by wieman01 on 2007-12-22
After upgrading, please check if the card works out of the box first. There is a little chance that it does...

---

### Post by Scott-271 on 2007-12-22
Hey Weiman01,

I reinstalled and upgraded, which went a little funny but worked overall. Update-manager updated everything as soon as I logged in after install, as usual; then said I still needed to update right after the update. So I just did it all through Synaptic.

Anyhoo, I built the latest version (1.51) of Ndiswrapper, following kevdog's guide. I did every step verbatim, except the installing of the drivers. I blacklisted every driver as per your guide. At this point, I called it a night and had a beer. ;)

I will try to use the .inf file from the cd that came with the adapter first, then move on the the serialmonkey rt2500 and rt2570, respectively.

Before I do anything, I wil run the usual network commands, and save them. just so I have a before and after.

Scott

---

### Post by wieman01 on 2007-12-22
> **Scott-271 said:**
> At this point, I called it a night and had a beer. ;)
Smart idea, man. :-)

Let me know how you go. Before you install "ndiswrapper" please post your scan results... just curious:
> sudo iwlist scan
And:
> sudo lshw -C network

---

### Post by Scott-271 on 2007-12-26
Hey Weiman,
Ok, after the madness of Christmas(I currently have a 3 yr old little girl in Dora the Explorer overload :o), I've come back to working on this.

Here's the "before" as requested:
```
lynnette@myfrigginlaptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

lynnette@myfrigginlaptop:~$ sudo lshw-C network
sudo: lshw-C: command not found
lynnette@myfrigginlaptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82557/8/9 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 0c
       serial: 00:03:47:74:7e:f6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A ip=192.168.1.116 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
lynnette@myfrigginlaptop:~$ 


```

Here's the after with strictly following kevdog's guide for installing ndiswrapper - including the .inf:
```

lynnette@myfrigginlaptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:9A:0B:F1
                    ESSID:"linksys"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:12/100  Signal level:-88 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:0C:41:3D:86:54
                    ESSID:"linksys"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:10/100  Signal level:-89 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

lynnette@myfrigginlaptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82557/8/9 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 0c
       serial: 00:03:47:74:7e:f6
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:17:76:98:ac
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2500usb driverversion=1.51+Linksys,04/13/2005, 2.00.02 ip=192.168.1.103 link=yes multicast=yes wireless=IEEE 802.11g
lynnette@myfrigginlaptop:~$ ndiswrapper -l
rt2500usb : driver installed
        device (13B1:000D) present (alternate driver: rt2570)
lynnette@myfrigginlaptop:~$ lsusb
Bus 001 Device 002: ID 13b1:000d Linksys 
Bus 001 Device 001: ID 0000:0000  
lynnette@myfrigginlaptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:9A:0B:F1   
          Bit Rate=11 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:40/100  Signal level:-70 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lynnette@myfrigginlaptop:~$ 

```

Now at this point I have N-M picking up a "linksys" network, which is my router - as well as my neighbor's; at about 24% with roaming enabled. I open FF try to go to Google and it takes forever to get a "Problem Loading Page" error.

Everything was showing up as it should, all the lights were blinking - just no internet. So I started messing with N-M settings: tried "any" network, dhcp, then static id. I followed your guide from blacklisting all drivers to the end. All the while rebooting between any/all changes, and trying to get to Google every time.

Then it hit me. I'm using a Linksys wireless router with DD-WRT firmware on it. I disabled roaming, typed in dd-wrt as the network, and set it for dhcp. Rebooted. I'm now wireless!!!!!!!!!

I don't think that was the problem all along, because at other stages of trying this, I had set it to dd-wrt as the network. 

I want to thank you very much for all the help you've given to me with this.

Scott

---

### Post by Scott-271 on 2007-12-27
Well there's good news and bad news......

After I got this thing wireless, I went to update some things and add stuff from Synaptic. Seems I had run out of space on my root partition. I ran GParted Live CD to see the state of things and hoped maybe I could resize. No luck, / was full, and resizing wasn't possible.

So, onto reformat #???. Did the reformat this morning, updated, and started working on the wireless .......again. I am happy to say, it is working. I pretty much did a much more organized version of what I said in the above post. I also C&P'd terminals at every step. 

Weiman, if you'd like I can send you copies of that, as well as anyone else who might find it helpful.

One thing I did find funny, and I remembered it too late, was that I never checked to see if ndiswrapper was already loaded or not. Turns out that it wasn't, and I used ver.1.51 from sourceforge, but when I ran "ndiswrapper -v" it came back with ver.1.45. Regardless, it works!

Thanks again,
Scott

---

### Post by wieman01 on 2007-12-28
> **Scott-271 said:**
> I pretty much did a much more organized version of what I said in the above post. I also C&P'd terminals at every step.
Excellent, glad you got it working, buddy.

Yes, it'd be interesting to see what you have got. So could you post your steps here? I will help other less knowledgeable users in future, I am pretty sure.

You might want to disable IPV6 if browsing is continuously slow. Let me know if that is a problem.

---

### Post by Scott-271 on 2007-12-31
Sorry that it's taken so long to get this posted - it's been a very hectic holiday season, for my 3 yr. old daughter and more so for me!

Here goes:

First I started with a fresh install and update. Downloaded the latest Ndiswrapper (v. 1.51) from sourceforge, and rt2570 from serialmonkey, then blacklisted **all** rt drivers by your guide. Install rt2500usb .inf, .sys, and .cat files to ~/driver. ~/driver must be created.

After that, it's a mix and match of terminal commands and GUI commands - some were just easier for me to do with GUI. I'll post the whole terminal process, and you can see what what done only in terminal, otherwise it was done GUI. 

Install **build-essential** and **linux-headers- `uname -r`**

Build rt2570 per AlexMono's guide, I did every step but blacklisting it. That was already done when all rt drivers were blacklisted. I don't know if building this driver was absolutely neccessary, but figured it couldn't hurt. Also, at one point I saw the rt2500usb as the loaded driver, and rt2570 as the alternate.

Build Ndiswrapper, per kevdog's guide. The only thing I did different here was to download Ndiswrapper directly from sourceforge with Firefox, not through the terminal commands given. Created ~/ndiswrapper, and extracted all the files to there. The current version of Ndiswrapper is 1.51, which is different from the example given by kevdog - which must be taken into consideration.

Reboot. Add info to Network-Manager, disabling roaming. I set it dhcp, and entered my network name. This was the critical point. I am running a Linksys WRT54Gv.6 wireless router with DD-WRT firmware, not the Linksys firmware; and my neighbor is also running a Linksys wireless router. I had to enter the network name as **DD-WRT**, otherwise it didn't work. N-M showed a "Linksys" network at 18% and "any" at 100%; I could not get a connection with either one. Do not check the box to enable "wireless" at this point. 

Reboot. Now, I unplugged the wired connection and plugged in the wireless adapter as it was shutting down. When it rebooted, the wireless connection was enabled. Had it not been, which I was expecting, I would have enabled it and rebooted. Also, at no point in the entire process is the wireless adapter plugged in until this time.

Now, terminal ouputs:
```

lynnette@myfrigginlaptop:~$ sudo mousepad /etc/modprobe.d/blacklist
[sudo] password for lynnette:
lynnette@myfrigginlaptop:~$ sudo aptitude install build-essential linux-headers-`uname -r`
[sudo] password for lynnette:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following NEW packages will be automatically installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev patch 
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev 
  linux-libc-dev patch 
0 packages upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 7935kB of archives. After unpacking 31.9MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://us.archive.ubuntu.com gutsy-updates/main linux-libc-dev 2.6.22-14.47 [653kB]
Get:2 http://us.archive.ubuntu.com gutsy-updates/main libc6-dev 2.6.1-1ubuntu10 [3287kB]
Get:3 http://us.archive.ubuntu.com gutsy/main libstdc++6-4.1-dev 4.1.2-16ubuntu2 [1129kB]
Get:4 http://us.archive.ubuntu.com gutsy/main g++-4.1 4.1.2-16ubuntu2 [2600kB]  
Get:5 http://us.archive.ubuntu.com gutsy/main g++ 4:4.1.2-9ubuntu2 [1440B]      
Get:6 http://us.archive.ubuntu.com gutsy/main patch 2.5.9-4 [95.6kB]            
Get:7 http://us.archive.ubuntu.com gutsy/main dpkg-dev 1.14.5ubuntu16 [162kB]   
Get:8 http://us.archive.ubuntu.com gutsy/main build-essential 11.3ubuntu1 [7066B]
Fetched 7935kB in 1m47s (73.6kB/s)                                              
Selecting previously deselected package linux-libc-dev.
(Reading database ... 88018 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.22-14.47_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.6.1-1ubuntu10_i386.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.2-16ubuntu2_i386.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.2-16ubuntu2_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.1.2-9ubuntu2_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-4_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.5ubuntu16_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_i386.deb) ...
Setting up linux-libc-dev (2.6.22-14.47) ...
Setting up libc6-dev (2.6.1-1ubuntu10) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.5ubuntu16) ...
Setting up libstdc++6-4.1-dev (4.1.2-16ubuntu2) ...
Setting up g++-4.1 (4.1.2-16ubuntu2) ...
Setting up g++ (4:4.1.2-9ubuntu2) ...

Setting up build-essential (11.3ubuntu1) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
lynnette@myfrigginlaptop:~$ cd rt2570-cvs-2007122712
lynnette@myfrigginlaptop:~/rt2570-cvs-2007122712$ cd Module
lynnette@myfrigginlaptop:~/rt2570-cvs-2007122712/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/lynnette/rt2570-cvs-2007122712/Module/rtusb_main.o
  CC [M]  /home/lynnette/rt2570-cvs-2007122712/Module/mlme.o
  CC [M]  /home/lynnette/rt2570-cvs-2007122712/Module/rtusb_bulk.o
  CC [M]  /home/lynnette/rt2570-cvs-2007122712/Module/connect.o
  CC [M]  /home/lynnette/rt2570-cvs-2007122712/Module/sync.o
  CC [M]  /home/lynnette/rt2570-cvs-2007122712/Module/rtusb_init.o
  CC [M]  /home/lynnette/rt2570-cvs-2007122712/Module/rtmp_tkip.o
  CC [M]  /home/lynnette/rt2570-cvs-2007122712/Module/wpa.o
  CC [M]  /home/lynnette/rt2570-cvs-2007122712/Module/rtmp_wep.o
  CC [M]  /home/lynnette/rt2570-cvs-2007122712/Module/rtusb_info.o
  CC [M]  /home/lynnette/rt2570-cvs-2007122712/Module/assoc.o
  CC [M]  /home/lynnette/rt2570-cvs-2007122712/Module/auth.o
  CC [M]  /home/lynnette/rt2570-cvs-2007122712/Module/auth_rsp.o
  CC [M]  /home/lynnette/rt2570-cvs-2007122712/Module/md5.o
  CC [M]  /home/lynnette/rt2570-cvs-2007122712/Module/rtusb_io.o
  CC [M]  /home/lynnette/rt2570-cvs-2007122712/Module/sanity.o
  CC [M]  /home/lynnette/rt2570-cvs-2007122712/Module/rtusb_data.o
  CC [M]  /home/lynnette/rt2570-cvs-2007122712/Module/rt2x00debug.o
  LD [M]  /home/lynnette/rt2570-cvs-2007122712/Module/rt2570.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/lynnette/rt2570-cvs-2007122712/Module/rt2570.mod.o
  LD [M]  /home/lynnette/rt2570-cvs-2007122712/Module/rt2570.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
lynnette@myfrigginlaptop:~/rt2570-cvs-2007122712/Module$ sudo make install
[sudo] password for lynnette:
2.6 module install
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/lynnette/rt2570-cvs-2007122712/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  INSTALL /home/lynnette/rt2570-cvs-2007122712/Module/rt2570.ko
  DEPMOD  2.6.22-14-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
/sbin/depmod -a
*** Update /etc/modprobe.d/ralink alias for rausb0
lynnette@myfrigginlaptop:~/rt2570-cvs-2007122712/Module$ cd
lynnette@myfrigginlaptop:~$ cd ~
lynnette@myfrigginlaptop:~$ mkdir ndiswrapper
lynnette@myfrigginlaptop:~$ cd ndiswrapper-1.51
bash: cd: ndiswrapper-1.51: No such file or directory
lynnette@myfrigginlaptop:~$ cd ndiswrapper
lynnette@myfrigginlaptop:~/ndiswrapper$ cd ndiswrapper-1.51
lynnette@myfrigginlaptop:~/ndiswrapper/ndiswrapper-1.51$ make distclean
make -C driver clean
make[1]: Entering directory `/home/lynnette/ndiswrapper/ndiswrapper-1.51/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
make[1]: Leaving directory `/home/lynnette/ndiswrapper/ndiswrapper-1.51/driver'
make -C utils clean
make[1]: Entering directory `/home/lynnette/ndiswrapper/ndiswrapper-1.51/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/lynnette/ndiswrapper/ndiswrapper-1.51/utils'
rm -f *~
rm -fr ndiswrapper-1.51 ndiswrapper-1.51.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/lynnette/ndiswrapper/ndiswrapper-1.51/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm -f *_exports.h .\#* win2lin_stubs.h built-in.o
make[1]: Leaving directory `/home/lynnette/ndiswrapper/ndiswrapper-1.51/driver'
make -C utils distclean
make[1]: Entering directory `/home/lynnette/ndiswrapper/ndiswrapper-1.51/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/home/lynnette/ndiswrapper/ndiswrapper-1.51/utils'
rm -f .\#*
lynnette@myfrigginlaptop:~/ndiswrapper/ndiswrapper-1.51$ make
make -C driver
make[1]: Entering directory `/home/lynnette/ndiswrapper/ndiswrapper-1.51/driver'
make -C /usr/src/linux-headers-2.6.22-14-generic SUBDIRS=/home/lynnette/ndiswrapper/ndiswrapper-1.51/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  LD      /home/lynnette/ndiswrapper/ndiswrapper-1.51/driver/built-in.o
  CC [M]  /home/lynnette/ndiswrapper/ndiswrapper-1.51/driver/crt.o
  CC [M]  /home/lynnette/ndiswrapper/ndiswrapper-1.51/driver/hal.o
  CC [M]  /home/lynnette/ndiswrapper/ndiswrapper-1.51/driver/iw_ndis.o
  CC [M]  /home/lynnette/ndiswrapper/ndiswrapper-1.51/driver/loader.o
  CC [M]  /home/lynnette/ndiswrapper/ndiswrapper-1.51/driver/ndis.o
  CC [M]  /home/lynnette/ndiswrapper/ndiswrapper-1.51/driver/ntoskernel.o
  CC [M]  /home/lynnette/ndiswrapper/ndiswrapper-1.51/driver/ntoskernel_io.o
  CC [M]  /home/lynnette/ndiswrapper/ndiswrapper-1.51/driver/pe_linker.o
  CC [M]  /home/lynnette/ndiswrapper/ndiswrapper-1.51/driver/pnp.o
  CC [M]  /home/lynnette/ndiswrapper/ndiswrapper-1.51/driver/proc.o
  CC [M]  /home/lynnette/ndiswrapper/ndiswrapper-1.51/driver/rtl.o
  CC [M]  /home/lynnette/ndiswrapper/ndiswrapper-1.51/driver/wrapmem.o
  CC [M]  /home/lynnette/ndiswrapper/ndiswrapper-1.51/driver/wrapndis.o
  CC [M]  /home/lynnette/ndiswrapper/ndiswrapper-1.51/driver/wrapper.o
  CC [M]  /home/lynnette/ndiswrapper/ndiswrapper-1.51/driver/usb.o
  CC [M]  /home/lynnette/ndiswrapper/ndiswrapper-1.51/driver/divdi3.o
  LD [M]  /home/lynnette/ndiswrapper/ndiswrapper-1.51/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/lynnette/ndiswrapper/ndiswrapper-1.51/driver/ndiswrapper.mod.o
  LD [M]  /home/lynnette/ndiswrapper/ndiswrapper-1.51/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: Leaving directory `/home/lynnette/ndiswrapper/ndiswrapper-1.51/driver'
make -C utils
make[1]: Entering directory `/home/lynnette/ndiswrapper/ndiswrapper-1.51/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
make[1]: Leaving directory `/home/lynnette/ndiswrapper/ndiswrapper-1.51/utils'
lynnette@myfrigginlaptop:~/ndiswrapper/ndiswrapper-1.51$ sudo make install
make -C driver install
make[1]: Entering directory `/home/lynnette/ndiswrapper/ndiswrapper-1.51/driver'
make -C /usr/src/linux-headers-2.6.22-14-generic SUBDIRS=/home/lynnette/ndiswrapper/ndiswrapper-1.51/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
echo /lib/modules/2.6.22-14-generic/misc
/lib/modules/2.6.22-14-generic/misc
mkdir -p /lib/modules/2.6.22-14-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.22-14-generic/misc
/sbin/depmod -a 2.6.22-14-generic -b /
make[1]: Leaving directory `/home/lynnette/ndiswrapper/ndiswrapper-1.51/driver'
make -C utils install
make[1]: Entering directory `/home/lynnette/ndiswrapper/ndiswrapper-1.51/utils'
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo

NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
make[1]: Leaving directory `/home/lynnette/ndiswrapper/ndiswrapper-1.51/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
lynnette@myfrigginlaptop:~/ndiswrapper/ndiswrapper-1.51$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.45
vermagic:       2.6.22-14-generic SMP mod_unload 586 
lynnette@myfrigginlaptop:~/ndiswrapper/ndiswrapper-1.51$ cd ~
lynnette@myfrigginlaptop:~$ mkdir driver
lynnette@myfrigginlaptop:~$ cd driver
lynnette@myfrigginlaptop:~/driver$ sudo ndiswrapper -i rt2500usb.inf
installing rt2500usb ...
lynnette@myfrigginlaptop:~/driver$ ndiswrapper -l
rt2500usb : driver installed
lynnette@myfrigginlaptop:~/driver$ ndiswrapper -l
rt2500usb : driver installed
        device (13B1:000D) present (alternate driver: rt2500usb)
lynnette@myfrigginlaptop:~/driver$ sudo depmod -a
lynnette@myfrigginlaptop:~/driver$ sudo modprobe ndiswrapper
lynnette@myfrigginlaptop:~/driver$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000007fe0000 (usable)
[    0.000000]  BIOS-e820: 0000000007fe0000 - 0000000007feec00 (ACPI data)
[    0.000000]  BIOS-e820: 0000000007feec00 - 0000000007ff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000007ff0000 - 0000000007ff4000 (reserved)
[    0.000000]  BIOS-e820: 0000000007ff4000 - 0000000008000000 (usable)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 128MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 32768) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    32768
[    0.000000]   HighMem     32768 ->    32768
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    32768
[    0.000000] On node 0 totalpages: 32768
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 224 pages used for memmap
[    0.000000]   Normal zone: 28448 pages, LIFO batch:7
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6EB0 checksum 0
[    0.000000] ACPI: RSDP 000F6EB0, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 07FE4B71, 002C (r1 PTLTD    RSDT    6041110  LTP        0)
[    0.000000] ACPI: FACP 07FEEB65, 0074 (r1 IBM    TP-16     6041110             0)
[    0.000000] ACPI: DSDT 07FE4B9D, 9FC8 (r1 IBM    TP-16     6041110 MSFT  100000C)
[    0.000000] ACPI: FACS 07FEF000, 0040
[    0.000000] ACPI: BOOT 07FEEBD9, 0027 (r1 PTLTD  $SBFTBL$  6041110  LTP        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 08000000:f7f80000)
[    0.000000] Built 1 zonelists.  Total pages: 32512
[    0.000000] Kernel command line: root=UUID=e3f69227-3190-4dbb-ab41-12d1a205f269 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0110b000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 512 (order: 9, 2048 bytes)
[    0.000000] Detected 896.160 MHz processor.
[    7.435843] Console: colour VGA+ 80x25
[    7.436043] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
[    7.436201] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
[    7.448608] Memory: 118396k/131072k available (2015k kernel code, 12060k reserved, 916k data, 364k init, 0k highmem)
[    7.448633] virtual kernel memory layout:
[    7.448635]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    7.448639]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    7.448642]     vmalloc : 0xc8800000 - 0xff7fe000   ( 879 MB)
[    7.448645]     lowmem  : 0xc0000000 - 0xc8000000   ( 128 MB)
[    7.448649]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    7.448652]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[    7.448655]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[    7.448663] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    7.448752] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    7.528736] Calibrating delay using timer specific routine.. 1793.61 BogoMIPS (lpj=3587238)
[    7.528797] Security Framework v1.0.0 initialized
[    7.528816] SELinux:  Disabled at boot.
[    7.528851] Mount-cache hash table entries: 512
[    7.529128] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[    7.529153] CPU: L1 I cache: 16K, L1 D cache: 16K
[    7.529160] CPU: L2 cache: 256K
[    7.529167] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[    7.529191] Compat vDSO mapped to ffffe000.
[    7.529223] Checking 'hlt' instruction... OK.
[    7.544940] SMP alternatives: switching to UP code
[    7.545290] Freeing SMP alternatives: 11k freed
[    7.545929] Early unpacking initramfs... done
[    8.300021] ACPI: Core revision 20070126
[    8.300558] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    8.308635] ACPI: setting ELCR to 0200 (from 0800)
[    8.343676] CPU0: Intel Pentium III (Coppermine) stepping 06
[    8.343690] SMP motherboard not detected.
[    8.343696] Local APIC not detected. Using dummy APIC emulation.
[    8.343793] Brought up 1 CPUs
[    8.344079] Booting paravirtualized kernel on bare hardware
[    8.344209] Time: 17:29:32  Date: 11/27/107
[    8.344301] NET: Registered protocol family 16
[    8.344567] EISA bus registered
[    8.344592] ACPI: bus type pci registered
[    8.345071] PCI: PCI BIOS revision 2.10 entry at 0xfd94f, last bus=7
[    8.345077] PCI: Using configuration type 1
[    8.345081] Setting up standard PCI resources
[    8.350506] ACPI: EC: Look up EC in DSDT
[    8.590242] ACPI: EC: GPE=0x09, ports=0x66, 0x62
[    8.740767] ACPI: Interpreter enabled
[    8.740778] ACPI: (supports S0 S1 S3 S4 S5)
[    8.740823] ACPI: Using PIC for interrupt routing
[    8.960020] ACPI: EC: GPE=0x09, ports=0x66, 0x62
[    8.960130] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.960146] PCI: Probing PCI hardware (bus 00)
[    8.960397] PCI: Firmware left 0000:00:03.0 e100 interrupts enabled, disabling
[    8.960738] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
[    8.960746] PCI quirk: region 1040-104f claimed by PIIX4 SMB
[    8.960757] PIIX4 devres C PIO at 15e8-15ef
[    8.960763] PIIX4 devres I PIO at 03f0-03f7
[    8.960769] PIIX4 devres J PIO at 002e-002f
[    8.961151] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.961303] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    8.971984] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    8.972415] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    8.972836] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    8.973257] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    8.973665] ACPI: Power Resource [PSER] (off)
[    8.973771] ACPI: Power Resource [PSIO] (on)
[    8.973798] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.973838] pnp: PnP ACPI init
[    8.973865] ACPI: bus type pnp registered
[    9.084414] pnp: PnP ACPI: found 15 devices
[    9.084423] ACPI: ACPI bus type pnp unregistered
[    9.084432] PnPBIOS: Disabled by ACPI PNP
[    9.084589] PCI: Using ACPI for IRQ routing
[    9.084597] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.090480] NET: Registered protocol family 8
[    9.090485] NET: Registered protocol family 20
[    9.090687] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[    9.090696] pnp: 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    9.090703] pnp: 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    9.090710] pnp: 00:00: iomem range 0xc8000-0xcbfff could not be reserved
[    9.090726] pnp: 00:02: ioport range 0x1000-0x103f has been reserved
[    9.090733] pnp: 00:02: ioport range 0x1040-0x104f has been reserved
[    9.090739] pnp: 00:02: ioport range 0xfe00-0xfe0f has been reserved
[    9.090762] pnp: 00:09: ioport range 0x15e0-0x15ef has been reserved
[    9.091839] Time: tsc clocksource has been installed.
[    9.121513] PCI: Bridge: 0000:00:01.0
[    9.121517]   IO window: disabled.
[    9.121527]   MEM window: f0000000-f7ffffff
[    9.121534]   PREFETCH window: 20000000-200fffff
[    9.121542] PCI: Bus 2, cardbus bridge: 0000:00:02.0
[    9.121548]   IO window: 00001400-000014ff
[    9.121555]   IO window: 00001c00-00001cff
[    9.121562]   PREFETCH window: 10000000-13ffffff
[    9.121569]   MEM window: 14000000-17ffffff
[    9.121576] PCI: Bus 6, cardbus bridge: 0000:00:02.1
[    9.121581]   IO window: 00002000-000020ff
[    9.121588]   IO window: 00002400-000024ff
[    9.121595]   PREFETCH window: 18000000-1bffffff
[    9.121602]   MEM window: 1c000000-1fffffff
[    9.122583] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    9.122591] PCI: setting IRQ 11 as level-triggered
[    9.122598] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    9.123388] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    9.123394] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[    9.123432] NET: Registered protocol family 2
[    9.159924] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
[    9.160023] TCP established hash table entries: 4096 (order: 3, 49152 bytes)
[    9.160161] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[    9.160248] TCP: Hash tables configured (established 4096 bind 4096)
[    9.160254] TCP reno registered
[    9.172091] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[    9.803786]  it is
[   10.598833] Freeing initrd memory: 7059k freed
[   10.599190] Simple Boot Flag at 0x35 set to 0x1
[   10.599742] audit: initializing netlink socket (disabled)
[   10.599775] audit(1198776574.120:1): initialized
[   10.605329] VFS: Disk quotas dquot_6.5.1
[   10.605504] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.605781] io scheduler noop registered
[   10.605789] io scheduler anticipatory registered
[   10.605794] io scheduler deadline registered
[   10.605849] io scheduler cfq registered (default)
[   10.605875] Limiting direct PCI/PCI transfers.
[   10.605923] Boot video device is 0000:01:00.0
[   10.606314] isapnp: Scanning for PnP cards...
[   10.959168] isapnp: No Plug & Play device found
[   11.041279] Real Time Clock Driver v1.12ac
[   11.041495] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   11.044234] pnp: Device 00:0c activated.
[   11.044561] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   11.045984] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   11.045993] ACPI: PCI Interrupt 0000:00:03.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   11.048039] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   11.048565] input: Macintosh mouse button emulation as /class/input/input0
[   11.048780] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[   11.065705] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.065720] serio: i8042 AUX port at 0x60,0x64 irq 12
[   11.066194] mice: PS/2 mouse device common for all mice
[   11.066470] EISA: Probing bus 0 at eisa.0
[   11.066485] Cannot allocate resource for EISA slot 1
[   11.066492] Cannot allocate resource for EISA slot 2
[   11.066517] EISA: Detected 0 cards.
[   11.066780] TCP cubic registered
[   11.066820] NET: Registered protocol family 1
[   11.066884] Using IPI No-Shortcut mode
[   11.067277]   Magic number: 3:795:492
[   11.068765] Freeing unused kernel memory: 364k freed
[   11.094667] input: AT Translated Set 2 keyboard as /class/input/input1
[   12.537412] AppArmor: AppArmor initialized<5>audit(1198776575.620:2):  type=1505 info="AppArmor initialized" pid=1125
[   12.559986] fuse init (API version 7.8)
[   12.572698] Failure registering capabilities with primary security module.
[   12.607296] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   12.607310] ACPI: Processor [CPU] (supports 8 throttling states)
[   12.611157] ACPI: Thermal Zone [THM0] (52 C)
[   14.018342] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[   14.018352] e100: Copyright(c) 1999-2006 Intel Corporation
[   14.018438] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   14.105061] e100: eth0: e100_probe: addr 0xe8120000, irq 11, MAC addr 00:03:47:74:7E:F6
[   14.270798] SCSI subsystem initialized
[   14.302699] libata version 2.21 loaded.
[   14.309245] ata_piix 0000:00:07.1: version 2.11
[   14.309624] scsi0 : ata_piix
[   14.309731] scsi1 : ata_piix
[   14.381764] usbcore: registered new interface driver usbfs
[   14.381821] usbcore: registered new interface driver hub
[   14.381875] usbcore: registered new device driver usb
[   14.385354] USB Universal Host Controller Interface driver v3.0
[   14.624855] Floppy drive(s): fd0 is 1.44M
[   14.708081] FDC 0 is a National Semiconductor PC87306
[    7.400000] Marking TSC unstable due to: possible TSC halt in C2.
[    7.404000] Time: acpi_pm clocksource has been installed.
[    7.440000] ata1: PATA max UDMA/33 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011850 irq 14
[    7.440000] ata2: PATA max UDMA/33 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011858 irq 15
[    7.620000] ata1.00: ATA-5: IBM-DJSA-220, JSGIAC1A, max UDMA/66
[    7.620000] ata1.00: 23572080 sectors, multi 16: LBA 
[    7.648000] Clocksource tsc unstable (delta = -854786193 ns)
[    7.680000] ata1.00: configured for UDMA/33
[    8.172000] ata2.00: ATAPI: HITACHI DVD-ROM GD-S200, 0034, max UDMA/33
[    8.360000] ata2.00: configured for UDMA/33
[    8.360000] scsi 0:0:0:0: Direct-Access     ATA      IBM-DJSA-220     JSGI PQ: 0 ANSI: 5
[    8.364000] scsi 1:0:0:0: CD-ROM            HITACHI  DVD-ROM GD-S200  0034 PQ: 0 ANSI: 5
[    8.376000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    8.376000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    8.376000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[    8.380000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[    8.380000] uhci_hcd 0000:00:07.2: irq 11, io base 0x00001860
[    8.380000] usb usb1: configuration #1 chosen from 1 choice
[    8.380000] hub 1-0:1.0: USB hub found
[    8.380000] hub 1-0:1.0: 2 ports detected
[    8.424000] sd 0:0:0:0: [sda] 23572080 512-byte hardware sectors (12069 MB)
[    8.424000] sd 0:0:0:0: [sda] Write Protect is off
[    8.424000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.424000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.424000] sd 0:0:0:0: [sda] 23572080 512-byte hardware sectors (12069 MB)
[    8.424000] sd 0:0:0:0: [sda] Write Protect is off
[    8.424000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.424000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.424000]  sda: sda1 sda2 sda3
[    8.480000] sd 0:0:0:0: [sda] Attached SCSI disk
[    8.508000] sr0: scsi3-mmc drive: 10x/24x cd/rw xa/form2 cdda tray
[    8.508000] Uniform CD-ROM driver Revision: 3.20
[    8.508000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    8.520000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    8.520000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    8.916000] Attempting manual resume
[    8.916000] swsusp: Resume From Partition 8:3
[    8.916000] PM: Checking swsusp image.
[    8.916000] PM: Resume from disk failed.
[    8.968000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    8.968000] EXT3-fs: write access will be enabled during recovery.
[   16.540000] kjournald starting.  Commit interval 5 seconds
[   16.540000] EXT3-fs: sda1: orphan cleanup on readonly fs
[   16.540000] ext3_orphan_cleanup: deleting unreferenced inode 49303
[   16.652000] ext3_orphan_cleanup: deleting unreferenced inode 49168
[   16.668000] EXT3-fs: sda1: 2 orphan inodes deleted
[   16.668000] EXT3-fs: recovery complete.
[   16.672000] EXT3-fs: mounted filesystem with ordered data mode.
[   30.776000] Linux agpgart interface v0.102 (c) Dave Jones
[   30.868000] Yenta: CardBus bridge found at 0000:00:02.0 [1014:0130]
[   30.868000] Yenta: Using INTVAL to route CSC interrupts to PCI
[   30.868000] Yenta: Routing CardBus interrupts to PCI
[   30.868000] Yenta TI: socket 0000:00:02.0, mfunc 0x00001000, devctl 0x66
[   30.868000] spurious 8259A interrupt: IRQ7.
[   30.912000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.100000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   31.100000] Socket status: 30000006
[   31.100000] Yenta: CardBus bridge found at 0000:00:02.1 [1014:0130]
[   31.100000] Yenta: Using INTVAL to route CSC interrupts to PCI
[   31.100000] Yenta: Routing CardBus interrupts to PCI
[   31.100000] Yenta TI: socket 0000:00:02.1, mfunc 0x00001000, devctl 0x66
[   31.332000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   31.332000] Socket status: 30000006
[   31.332000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.332000] agpgart: Detected an Intel 440BX Chipset.
[   31.336000] agpgart: AGP aperture is 64M @ 0xf8000000
[   32.528000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   32.528000] piix4_smbus 0000:00:07.3: IBM system detected; this module may corrupt your serial eeprom! Refusing to load module!
[   32.528000] piix4_smbus: probe of 0000:00:07.3 failed with error -1
[   32.548000] input: PC Speaker as /class/input/input2
[   33.476000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   33.512000] input: TPPS/2 IBM TrackPoint as /class/input/input3
[   34.200000] parport_pc 00:0d: reported by Plug and Play ACPI
[   34.200000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   34.392000] cs: IO port probe 0x100-0x3af: clean.
[   34.392000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   34.392000] cs: IO port probe 0x820-0x8ff: clean.
[   34.392000] cs: IO port probe 0xc00-0xcf7: clean.
[   34.396000] cs: IO port probe 0xa00-0xaff: clean.
[   34.396000] cs: IO port probe 0x100-0x3af: clean.
[   34.396000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   34.396000] cs: IO port probe 0x820-0x8ff: clean.
[   34.396000] cs: IO port probe 0xc00-0xcf7: clean.
[   34.396000] cs: IO port probe 0xa00-0xaff: clean.
[   34.440000] irda_init()
[   34.440000] NET: Registered protocol family 23
[   34.488000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   34.528000] pnp: Device 00:0e activated.
[   34.528000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   34.528000] nsc-ircc, chip->init
[   34.528000] nsc-ircc, Found chip at base=0x02e
[   34.528000] nsc-ircc, driver loaded (Dag Brattli)
[   34.528000] IrDA: Registered device irda0
[   34.528000] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   34.652000] cs46xx: failure waiting for FIFO command to complete
[   35.056000] gameport: CS46xx Gameport is pci0000:00:05.0/gameport0, speed 1807kHz
[   35.960000] loop: module loaded
[   36.028000] lp0: using parport0 (interrupt-driven).
[   36.240000] Adding 522104k swap on /dev/sda3.  Priority:-1 extents:1 across:522104k
[   36.612000] EXT3 FS on sda1, internal journal
[   37.704000] kjournald starting.  Commit interval 5 seconds
[   37.704000] EXT3 FS on sda2, internal journal
[   37.704000] EXT3-fs: mounted filesystem with ordered data mode.
[   40.044000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   40.088000] ACPI: ACPI Dock Station Driver 
[   40.096000] ACPI: \_SB_.PCI0.IDE0.SCND.MSTR: found ejectable bay
[   40.096000] ACPI: \_SB_.PCI0.IDE0.SCND.MSTR: Adding notify handler
[   40.096000] ACPI: Error installing bay notify handler
[   40.096000] ACPI: Bay [\_SB_.PCI0.IDE0.SCND.MSTR] Added
[   40.288000] input: Power Button (FF) as /class/input/input4
[   40.288000] ACPI: Power Button (FF) [PWRF]
[   40.328000] input: Lid Switch as /class/input/input5
[   40.328000] ACPI: Lid Switch [LID]
[   40.348000] input: Sleep Button (CM) as /class/input/input6
[   40.348000] ACPI: Sleep Button (CM) [SLPB]
[   40.764000] ACPI: Battery Slot [BAT0] (battery present)
[   40.856000] ACPI: AC Adapter [AC] (on-line)
[   44.244000] ppdev: user-space parallel port driver
[   45.796000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   46.532000] audit(1198776618.677:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4476 profile="/usr/sbin/cupsd"
[   46.952000] IBM machine detected. Enabling interrupts during APM calls.
[   46.952000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   46.952000] apm: overridden by ACPI.
[   47.436000] thinkpad_acpi: ThinkPad ACPI Extras v0.14
[   47.436000] thinkpad_acpi: http://ibm-acpi.sf.net/
[   47.544000] thinkpad_acpi: another device driver is already handling bay events
[   47.544000] thinkpad_acpi: disabling subdriver bay
[   47.652000] Non-volatile memory driver v1.2
[   47.672000] input: /usr/sbin/thinkpad-keys as /class/input/input7
[   48.148000] Failure registering capabilities with primary security module.
[   53.712000] [drm] Initialized drm 1.1.0 20060810
[   53.768000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   53.768000] [drm] Initialized savage 2.4.1 20050313 on minor 0
[   53.768000] mtrr: base(0xf2000000) is not aligned on a size(0x5000000) boundary
[   53.772000] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
[   53.772000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[   53.772000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[   54.588000] NET: Registered protocol family 17
[   57.532000] NET: Registered protocol family 10
[   57.532000] lo: Disabled Privacy Extensions
[   67.628000] eth0: no IPv6 routers present
[ 3290.044000] UDF-fs: No VRS found
[ 3290.068000] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 3290.116000] ISOFS: changing to secondary root
[ 8264.320000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[ 8264.664000] usb 1-1: configuration #1 chosen from 1 choice
[ 8372.040000] ndiswrapper version 1.45 loaded (smp=yes)
[ 8372.332000] usb 1-1: reset full speed USB device using uhci_hcd and address 2
[ 8372.756000] ndiswrapper: driver rt2500usb (Linksys,04/13/2005, 2.00.02.0000) loaded
[ 8373.392000] wlan0: ethernet device 00:12:17:76:98:ac using NDIS driver: rt2500usb, version: 0x20000, NDIS version: 0x500, vendor: 'Ralink Technology Inc.', 13B1:000D.F.conf
[ 8373.396000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 8373.400000] usbcore: registered new interface driver ndiswrapper
[ 8375.056000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8387.268000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
lynnette@myfrigginlaptop:~/driver$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
lynnette@myfrigginlaptop:~/driver$ echo "ndiswrapper" | sudo tee -a /etc/modules
ndiswrapper
lynnette@myfrigginlaptop:~/driver$ 

```

After everything was done, and I made sure I was connected, I ran the usual commands. Here's the output of that:
```

lynnette@myfrigginlaptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:47:74:7E:F6  
          inet addr:192.168.1.116  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:47ff:fe74:7ef6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:921 (921.0 b)  TX bytes:5627 (5.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:76:98:AC  
          inet6 addr: fe80::212:17ff:fe76:98ac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:199 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20538 (20.0 KB)  TX bytes:468 (468.0 b)

lynnette@myfrigginlaptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:9A:0B:F1   
          Bit Rate=5.5 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lynnette@myfrigginlaptop:~$ sudo iwlist scan
[sudo] password for lynnette:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:9A:0B:F1
                    ESSID:"linksys"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:18:F8:E7:E7:30
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:93/100  Signal level:-36 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:0C:41:3D:86:54
                    ESSID:"linksys"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

lynnette@myfrigginlaptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82557/8/9 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 0c
       serial: 00:03:47:74:7e:f6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A ip=192.168.1.116 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:17:76:98:ac
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2500usb driverversion=1.45+Linksys,04/13/2005, 2.00.02 multicast=yes wireless=IEEE 802.11g
lynnette@myfrigginlaptop:~$ ndiswrapper -l
rt2500usb : driver installed
        device (13B1:000D) present (alternate driver: rt2500usb)
lynnette@myfrigginlaptop:~$ lsusb
Bus 001 Device 002: ID 13b1:000d Linksys 
Bus 001 Device 001: ID 0000:0000  
lynnette@myfrigginlaptop:~$ 

```

There are a few things I don't get though. The version for Ndiswrapper comes up as 1.45 when it should be 1.51; and iwlist scan shows it as "linksys" when I know it should be dd-wrt. Other than just finding out why those things are incorrect, I am happy I finally got this figured out - almost as happy as my wife, who this is for. I really think it had a lot to do with the order of the steps done. I had tried this eight ways from Sunday to no avail, and until I sat down and had everything kinda organized I was at a loss.

Weiman01, I can't thank you enough for your patience and assistance. If it hadn't been for you I probably just would have put XP on----I had the disk in my hand at several points during this entire process! Thank You!!!!!

Scott


------------------

That was written last night. I was able to get a connection, but by the time I was ready to post it I had lost the wireless connection. I haven't been able to get it back yet. At one point, I also had no wireless connection, but I have solved that. So basically, I was wireless for a few days.

Here's some outputs:

```

lynnette@myfrigginlaptop:~$ ndiswrapper -l
rt2500usb : driver installed
lynnette@myfrigginlaptop:~$ ndiswrapper -v
modinfo: could not open ndiswrapper: No such device
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not open ndiswrapper: No such device

You may need to upgrade driver and/or utils to latest versions available at
http://ndiswrapper.sourceforge.net
lynnette@myfrigginlaptop:~$ sudo iwlist scan
[sudo] password for lynnette:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

lynnette@myfrigginlaptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

lynnette@myfrigginlaptop:~$ lsusb
Bus 001 Device 001: ID 0000:0000  
lynnette@myfrigginlaptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82557/8/9 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 0c
       serial: 00:03:47:74:7e:f6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.1.116 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
lynnette@myfrigginlaptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:03.0 Ethernet controller: Intel Corporation 82557/8/9 Ethernet Pro 100 (rev 0c)
00:03.1 Serial controller: Agere Systems LT WinModem (rev 01)
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)
lynnette@myfrigginlaptop:~$ 

```

When I open N-M, it doesn't even list a wireless connection option, just wired and modem. The adapter just flashes the power light when I plug it in, and then goes blank; if it doesn't go blank, it freezes the computer right up. I'm at a loss with this, but knowing it can work, I refuse to give up. I'm going to conitnue to tinker with different things (and keep a record of said things); but, any/all help or insight is appreciated.

Scott

---

### Post by Scott-271 on 2007-12-31
Sorry to double post, but......

As much as I want this to work in Xubuntu, I have had nothing but trouble trying to get it to work or fix it. Currently, the adapter won't even stay powered up. It just seems that most of these  things tend to work better in Ubuntu - my wife really doesn't care what OS is on it as long as it's working - so, I'll be reformatting again, and changing to Ubuntu.

I'll post the progress of this attempt, and any problems that come with it.

Scott

P.S. I almost feel like I need to start a blog about this....."Thinkpad + WUSB54Gv4 + Linux = ](*,)"

---

