---
title: "Wireless USB"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by Ruff Paws on 2011-05-16
Hey guys, i've researched via the forums and havent found anything that has helped, I've done everything I can, so now I look to you folks for help...
 
I am new to anything linux.
 
Anyways, the network thing shows that it is reading the usb wireless adapter, also I've researched and it is one that should work... When I click the network tab, it says for wireless that firmware is missing, how do I go abouts fixing this? 
 
Thanks to any and all who help, btw I will be checking this post quite often so can do whatever is needed.... Except one thing, I am on a laptop now, and ubuntu is on my desktop, running 11.04...
 
Thanks,
Eric

---

### Post by Ruff Paws on 2011-05-26
No one can help????

---

### Post by fractalman on 2011-05-26
Ok, i'm still a newbie but i'll offer what help i can

If there is no firmware then that basically means you need to find the driver and install it, so

What sort usb adapter is it?  then look here for the driver

[http://wireless.kernel.org/en/users/Devices/USB](http://wireless.kernel.org/en/users/Devices/USB)

you should find instillation instructions on the same page as the driver download

---

### Post by chili555 on 2011-05-26
Please open a terminal and run and post:```
lsusb
```We'll guide you through the process.

---

### Post by Ruff Paws on 2011-05-26
> **chili555 said:**
> Please open a terminal and run and post:```
lsusb
```We'll guide you through the process.
 
Thanks, I appreciate the help... When I type that in, I got a bunch of stuff, but for the wireless USB adapter it says 
 
 
BUS 001 DEVICE 003: ID 1737:0079 Linksys WUSB600N Wireless-N USB Network Adapter with Dual-Band ver. 2

---

### Post by Ruff Paws on 2011-05-26
> **fractalman said:**
> Ok, i'm still a newbie but i'll offer what help i can
 
If there is no firmware then that basically means you need to find the driver and install it, so
 
What sort usb adapter is it? then look here for the driver
 
[http://wireless.kernel.org/en/users/Devices/USB](http://wireless.kernel.org/en/users/Devices/USB)
 
you should find instillation instructions on the same page as the driver download
 
Thanks, but didnt find it in there... I saw it somewhere else though..

---

### Post by jawilljr on 2011-05-26
> **Ruff Paws said:**
> Thanks, but didnt find it in there... I saw it somewhere else though..

Do you want you wifi to work? I can fix it for you.  Just answer back.

Jerry

---

### Post by Ruff Paws on 2011-05-26
> **jawilljr said:**
> Do you want you wifi to work? I can fix it for you. Just answer back.
 
Jerry
 
Yes I do, that would be great!!!

---

### Post by chili555 on 2011-05-26
This gives you the procedure. You will also need to install build-essential and linux-headers-generic. Both of these are complex packages of other packages. This is not easy to do with no internet connection. Do you have any possibility of a temporary ethernet connection?

[https://help.ubuntu.com/community/WifiDocs/Device/Linksys%20WUSB600N](https://help.ubuntu.com/community/WifiDocs/Device/Linksys%20WUSB600N)> in a terminal window. If you get a line like

```
Bus 001 Device 009: ID 1737:0079 Linksys

```
you have a WUSB600Nv2, and these instructions should apply to it.This procedure is a bit complex with an internet connection and maddening without!

I have built the module on my system so I know it can be done. I will be glad to help you.

---

### Post by josephmills on 2011-05-26
please go to post number 85 you answer is there lets us know if you get hung up or get and error on the make   [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165)
sorry chili did not see you there

---

### Post by chili555 on 2011-05-26
> **jawilljr said:**
> Do you want you wifi to work? I can fix it for you.  Just answer back.

JerryI will watch and learn.

---

### Post by Ruff Paws on 2011-05-26
> **chili555 said:**
> This gives you the procedure. You will also need to install build-essential and linux-headers-generic. Both of these are complex packages of other packages. This is not easy to do with no internet connection. Do you have any possibility of a temporary ethernet connection?
 
[https://help.ubuntu.com/community/WifiDocs/Device/Linksys%20WUSB600N](https://help.ubuntu.com/community/WifiDocs/Device/Linksys%20WUSB600N)This procedure is a bit complex with an internet connection and maddening without!
 
I have built the module on my system so I know it can be done. I will be glad to help you.
 
Yes I can take tower downstairs and plug in

---

### Post by chili555 on 2011-05-26
> **Ruff Paws said:**
> Yes I can take tower downstairs and plug inWho do you trust? Three guys claim to have the answer. I have nothing to offer except it works on my Natty system; yes, I do have a rt3572sta device. Your choice.

---

### Post by josephmills on 2011-05-26
I say go with chili and I would love to learn from this

---

### Post by jawilljr on 2011-05-26
To let you I am going tpo have you download the latest compat-wireless drivers for your chipset.

First things first download the latest firmware. They are located [Here](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=tree;h=ae524638c277301a83daf126aaaf880738e2474b;hb=ae524638c277301a83daf126aaaf880738e2474b). Here is the [Direct link](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob_plain;f=rt2870.bin;hb=ae524638c277301a83daf126aaaf880738e2474b)

Download it to your Downloads directory. then do this:

```
cp ~/Downloads/rt2870.bin /lib/firmware
```

Now download [	compat-wireless-2011-05-24-p](http://www.orbit-lab.org/kernel/compat-wireless-2.6/2011/05/compat-wireless-2011-05-24-p.tar.bz2)

Again download it to your Downloads directory.

Now it is time to compile and install:

```
cd ~/downloads
tar jxzf compat-wireless-2011-05-24-p.tar.bz2
cd 	compat-wireless-2011-05-24-p
make
sudo make install
sudo reboot
```

---

### Post by Ruff Paws on 2011-05-26
> **chili555 said:**
> Who do you trust? Three guys claim to have the answer. I have nothing to offer except it works on my Natty system; yes, I do have a rt3572sta device. Your choice.
 
K, I'll go with you!!! lol so what do I do? I appreciate your help so much!!!

---

### Post by Ruff Paws on 2011-05-26
> **jawilljr said:**
> To let you I am going tpo have you download the latest compat-wireless drivers for your chipset.
 
First things first download the latest firmware. They are located [Here]("http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=tree;h=ae524638c277301a83daf126aaaf880738e2474b;hb=ae524638c277301a83daf126aaaf880738e2474b"). Here is the [Direct link]("http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob_plain;f=rt2870.bin;hb=ae524638c277301a83daf126aaaf880738e2474b")
 
Download it to your Downloads directory. then do this:
 
```
cp ~/Downloads/rt2870.bin /lib/firmware
```
 
Now download [    compat-wireless-2011-05-24-p]("http://www.orbit-lab.org/kernel/compat-wireless-2.6/2011/05/compat-wireless-2011-05-24-p.tar.bz2")
 
Again download it to your Downloads directory.
 
Now it is time to compile and install:
 
```
cd ~/downloads
tar jxzf compat-wireless-2011-05-24-p.tar.bz2
cd     compat-wireless-2011-05-24-p
make
sudo make install
sudo reboot
```
 
I mean no disrespect all at, but since someone else told me to try chili's I will, if it doesnt work/pan out, I'll do this....

---

### Post by Ruff Paws on 2011-05-26
oh... Ok, I'll follow those instructions chili, i'll let you know how it turns out.... So I need to go plug directly into internet?

---

### Post by jawilljr on 2011-05-26
> **Ruff Paws said:**
> I mean no disrespect all at, but since someone else told me to try chili's I will, if it doesnt work/pan out, I'll do this....

No disrespect at all...just that you will not get wireless N or 5ghz.

Here is my iwconfig

```
jawilljr@jawilljr:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"KJAWJR"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: C0:C1:C0:38:4F:32   
          Bit Rate=130 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:60   Missed beacon:0
```

And my uname -a

```
Linux jawilljr 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

Jerry

And also just to let everyone know that the ralink staging drivers will be removed from the 2.6.40 kernel... so you will have to use rt2800usb.

Have a [Look at this](http://www.h-online.com/open/features/Kernel-Log-Coming-in-2-6-39-Part-1-Network-drivers-and-infrastructure-1227053.html?page=2)

Use whatever you want.

Jerry

---

### Post by josephmills on 2011-05-26
> **Ruff Paws said:**
> oh... Ok, I'll follow those instructions chili, i'll let you know how it turns out.... So I need to go plug directly into internet?

yes to download things from the net you need to be on the internet.

---

### Post by chili555 on 2011-05-26
Get thee to an internet connection, open Applications > Accessories > Terminal and do:```
sudo apt-get install build-essential linux-headers-generic
```Now, I'd like to email you the package with all the needed changes made. It's too big to attach to my reply here. Can you please click my user name and send me a private message with your email address? Can you get a 1.9MB attachment? 

When you get it, drag and drop it to your desktop. Right-click it and select Extract Here. Then go back to the terminal and do:```
cd Desktop/2010
```Press Tab and the remainder will fill in. Now do:```
sudo su
make
make install
echo rt3572sta >> /etc/modules
modprobe rt3572sta
exit
```Is your wireless device blinking and connecting?

If you get errors, stop and ask. Warnings are OK. If there is anything you don't understand, please ask.

---

### Post by Ruff Paws on 2011-05-26
> **jawilljr said:**
> No disrespect at all...just that you will not get wireless N or 5ghz.
 
Here is my iwconfig
 
```
jawilljr@jawilljr:~$ iwconfig
lo        no wireless extensions.
 
eth0      no wireless extensions.
 
wlan0     IEEE 802.11abgn  ESSID:"KJAWJR"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: C0:C1:C0:38:4F:32   
          Bit Rate=130 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:60   Missed beacon:0
```
 
And my uname -a
 
```
Linux jawilljr 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```
 
Jerry
 
And also just to let everyone know that the ralink staging drivers will be removed from the 2.6.40 kernel... so you will have to use rt2800usb.
 
Have a [Look at this]("http://www.h-online.com/open/features/Kernel-Log-Coming-in-2-6-39-Part-1-Network-drivers-and-infrastructure-1227053.html?page=2")
 
Use whatever you want.
 
Jerry
 
That's fine with the "N" really, I dont even have a router capable of wireless "N"

---

### Post by Ruff Paws on 2011-05-26
Well Chili, that didnt work, and now that i've tried it, I know i've tried before and didnt work :(

---

### Post by chili555 on 2011-05-26
> **jawilljr said:**
> No disrespect at all...just that you will not get wireless N or 5ghz.

Here is my iwconfig

```
jawilljr@jawilljr:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"KJAWJR"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: C0:C1:C0:38:4F:32   
          Bit Rate=130 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:60   Missed beacon:0
```

And my uname -a

```
Linux jawilljr 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

Jerry

And also just to let everyone know that the ralink staging drivers will be removed from the 2.6.40 kernel... so you will have to use rt2800usb.

Have a [Look at this](http://www.h-online.com/open/features/Kernel-Log-Coming-in-2-6-39-Part-1-Network-drivers-and-infrastructure-1227053.html?page=2)

Use whatever you want.

JerryDo you have the same device?> 1737:0079 Linksys WUSB600N Wireless-N USB Network AdapterWhat driver are you using; rt2800usb?```
$ modinfo  /home/chili/Desktop/Forum/compat/compat-wireless-2011-05-24-p/drivers/net/wireless/rt2x00/rt2800usb.ko | grep 0079
$ 

```rt2800usb doesn't claim his device.

???

---

### Post by chili555 on 2011-05-26
> **Ruff Paws said:**
> Well Chili, that didnt work, and now that i've tried it, I know i've tried before and didnt work :(What didn't work? Did you download the package elsewhere? Where did it fail?

---

### Post by Ruff Paws on 2011-05-26
> **chili555 said:**
> What didn't work? Did you download the package elsewhere? Where did it fail?
 
 
Right away when I tried sudo.... Got an error 2.... Give me a sec, found something on forums that might make that go away.... Sec :)

---

### Post by jawilljr on 2011-05-26
> **chili555 said:**
> Do you have the same device?What driver are you using; rt2800usb?```
$ modinfo  /home/chili/Desktop/Forum/compat/compat-wireless-2011-05-24-p/drivers/net/wireless/rt2x00/rt2800usb.ko | grep 0079
$ 

```rt2800usb doesn't claim his device.

???

I am using the driver I posted:

```
jawilljr@jawilljr:~$ modinfo rt2800usb | grep 0079
alias:          usb:v1737p0079d*dc*dsc*dp*ic*isc*ip*
```

It was added [in this patch](http://git.kernel.org/?p=linux/kernel/git/ivd/rt2x00.git;a=commit;h=ce2919c9fffe2aa52f9c3e327176d03764dbf9b5)

Jerry

---

### Post by Ruff Paws on 2011-05-26
Well damn, whatever Jerry had me do sucks, now it's not even showing I have the USB stick plugged in... How do I remove all that, I'm going to try the second thing Chili wanted me to do

---

### Post by chili555 on 2011-05-26
Sorry, folks, tornado warning. Mrs. Chili and I are heading for cover.

---

### Post by Ruff Paws on 2011-05-26
> **chili555 said:**
> Sorry, folks, tornado warning. Mrs. Chili and I are heading for cover.
 
 
Hey man, you guys be careful, and be safe!!!!!!

---

### Post by josephmills on 2011-05-26
hi there could you bring us up to speed what you have done and what is going on right now what are the errors that you are getting when running sudo su ? thanks

---

### Post by Ruff Paws on 2011-05-26
> **josephmills said:**
> hi there could you bring us up to speed what you have done and what is going on right now what are the errors that you are getting when running sudo su ? thanks
 
 
I'm thinking of just caning this, it's kind of a B.S. process.... What do you mean with sudo su, nothing came up, just now says [EMAIL="root@ruffpaws"]root@ruffpaws[/EMAIL] instead of ruffpaws... 
 
I did everything that the one guy had me do, I was going to try what chili said to do, but now it's not even reading my wireless usb....

---

### Post by josephmills on 2011-05-26
> **Ruff Paws said:**
> I'm thinking of just caning this, it's kind of a B.S. process.... What do you mean with sudo su, nothing came up, just now says [EMAIL="root@ruffpaws"]root@ruffpaws[/EMAIL] instead of ruffpaws... 
 
I did everything that the one guy had me do, I was going to try what chili said to do, but now it's not even reading my wireless usb....

just go back to post #21 and do that did you get the doc from him?

---

### Post by jawilljr on 2011-05-26
> **Ruff Paws said:**
> Well damn, whatever Jerry had me do sucks, now it's not even showing I have the USB stick plugged in... How do I remove all that, I'm going to try the second thing Chili wanted me to do

Of course you did not give any error messages.

To remove it just got to the compat-wireless directory and type this:

```
sudo make uninstall
sudo make clean
sudo reboot
```

Then follow chili's instructions...after the tornado warnings.

Me I look at this as a positive development. Why? because as I have said, the Ralink staging drivers will be removed from the future versions of the kernel. And if people don't start using rt2800(usb)(pci) the rt2x00 devs won't be able to find bugs.

Also what is nice about Natty is you can go back and forth from the staging driver to rt2800usb real easy. I do it all the time.

The best place to send bug reports is [rt2x00's mailing list](http://rt2x00.serialmonkey.com/mailman/listinfo/users_rt2x00.serialmonkey.com)

Jerry

---

### Post by Ruff Paws on 2011-05-26
> **jawilljr said:**
> Of course you did not give any error messages.
 
To remove it just got to the compat-wireless directory and type this:
 
```
sudo make uninstall
sudo make clean
sudo reboot
```
 
Then follow chili's instructions...after the tornado warnings.
 
Me I look at this as a positive development. Why? because as I have said, the Ralink staging drivers will be removed from the future versions of the kernel. And if people don't start using rt2800(usb)(pci) the rt2x00 devs won't be able to find bugs.
 
Also what is nice about Natty is you can go back and forth from the staging driver from the staging drivers to rt2800usb real easy. I do it all the time.
 
The best place to send bug reports is [rt2x00's mailing list]("http://rt2x00.serialmonkey.com/mailman/listinfo/users_rt2x00.serialmonkey.com")
 
Jerry
 
Jerry,
 
There were no error messages, everything went though, however now it doesnt even read my wireless adapter..... I followed what you said to do to the "T" and nothing, not even wireless adapter now

---

### Post by Ruff Paws on 2011-05-26
Oh, and yes, I have the doc from him

---

### Post by josephmills on 2011-05-26
> **Ruff Paws said:**
> Oh, and yes, I have the doc from him

then go back to that post please and try it if you get and errors or warning you can just drop a line *

---

### Post by jawilljr on 2011-05-26
> **Ruff Paws said:**
> Jerry,
 
There were no error messages, everything went though, however now it doesnt even read my wireless adapter..... I followed what you said to do to the "T" and nothing, not even wireless adapter now

do this:

```
cat /etc/modprobe.d/blacklist.conf
```

and:

```
lsmod | grep rt
```

Jerry

---

### Post by Ruff Paws on 2011-05-27
Just an update, I followed what Chili said and had zero problems getting it to work! Thanks again Chili

---

### Post by chili555 on 2011-05-27
Woo hoo! Glad it's working! Have fun!

I was starting to be a bit worried. I guess some of you out there actually work and have families...poor guys.

---

