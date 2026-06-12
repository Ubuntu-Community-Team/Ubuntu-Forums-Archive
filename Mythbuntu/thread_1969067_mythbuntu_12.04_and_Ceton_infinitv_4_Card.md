---
title: "mythbuntu 12.04 and Ceton infinitv 4 Card"
date: 2012-04-29
forum: Mythbuntu
---

### Post by supergokougt on 2012-04-29
Ok I am very frustrated at this point! I read 0.25 should [support ceton infinitv]("http://www.mythtv.org/wiki/Release_Notes_-_0.25") card right out of the box so I thought this would be my chance to make a PVR. I have tried many different install options and can not get my computer to recognize the ceton card. I am not the most experienced user, but have gotten many other things to work. 

I need help - big time. 

Should I be installing the [drivers found on this page]("http://www.mythtv.org/wiki/Ceton_InfiniTV_4") before I configure any settings? 

I have tried to install but I get error messages when I try ./configure, but im pretty sure thats because there is no configure in the unzipped pack. Note: I am very low level when it comes to installing or building from tar.gz

If i dont need those drivers. I have tried setting up the card in mythtv backend setup but no matter what I end up not getting live tv.

I have read and have searched google and forums and tried many other peoples fixes. I do think I have to get my computer to see the card before I should have tried anything from there. 

Also, I read [Ron Frazier's 3 part post]("http://mythtvblog.blogspot.com/2011/07/ceton-inifinitv-4-in-mythtv-024-part-2.html") (which was way over my head), but I didnt know how much it applied since I had a newer version. 

So I am running mythbuntu 12.04 64bit
intelcore 13 cpu540 @3.07ghz x 4
I have a ceton infinitv 4 
Using HDMI to TV (oh and not getting 5.1 sound in settings, but thats another time)
8g ram
2 hard drives 1tb and 2tb

If you can help in anyway I will really appreciate it. Links to guides or how to's, codes to get read out to help you help me, I really don't want to scrap this project and really don't want to put windows back on this just to get this working.

---

### Post by nickrout on 2012-04-29
> **supergokougt said:**
> Ok I am very frustrated at this point! I read 0.25 should [support ceton infinitv]("http://www.mythtv.org/wiki/Release_Notes_-_0.25") card right out of the box so I thought this would be my chance to make a PVR. I have tried many different install options and can not get my computer to recognize the ceton card. I am not the most experienced user, but have gotten many other things to work. 

I need help - big time. 

Should I be installing the [drivers found on this page]("http://www.mythtv.org/wiki/Ceton_InfiniTV_4") before I configure any settings? 

I have tried to install but I get error messages when I try ./configure, but im pretty sure thats because there is no configure in the unzipped pack. Note: I am very low level when it comes to installing or building from tar.gz

When you unpacked the drivers there was a file named README. Read it. ./configure is unneeded. Try 

```
sudo make install
sudo modprobe ctn91xx
```

exactly as it says in the README file.

---

### Post by supergokougt on 2012-04-30
I did try to follow the readme file, but here is my issue:

step one says to configure to your install, gcc and kernal (im at work and not at my home computer to be exact with wording)

how do I do that first step?

And in the previous installs when I was able to run modprode ctn91xx I didn't get the expected results listed in the readme.

also should the ctn91xx be changed to something more specific to me? like the xx should be my card?

now i just did a re-install of mythbuntu 12.04 and I get error message when trying to unpack the tar.gz. To fix this i am going to install ubuntu 12.04 and then add on the mythbuntu through the link on their website. I think the mythbuntu is too light and maybe not including something to unpack?

---

### Post by tgm4883 on 2012-04-30
> **supergokougt said:**
> I did try to follow the readme file, but here is my issue:

step one says to configure to your install, gcc and kernal (im at work and not at my home computer to be exact with wording)

how do I do that first step?

And in the previous installs when I was able to run modprode ctn91xx I didn't get the expected results listed in the readme.

also should the ctn91xx be changed to something more specific to me? like the xx should be my card?

now i just did a re-install of mythbuntu 12.04 and I get error message when trying to unpack the tar.gz. To fix this i am going to install ubuntu 12.04 and then add on the mythbuntu through the link on their website. I think the mythbuntu is too light and maybe not including something to unpack?

What error message? Looking at the README file it says

> *****************************************************************************
*                                  Installation
*****************************************************************************

Install make, gcc, and kernel headers for your distribution. Then run:
make
sudo make install
sudo modprobe ctn91xx

I don't see where it says to run configure. There also isn't a reason you can't open a .tar.gz file on Mythbuntu.

:EDIT:

Looking at the USB driver, it does list

> 
To build and install:
./configure --prefix=/usr
make
sudo make install


But you don't mention USB in your post, you mention a card

---

### Post by supergokougt on 2012-04-30
> **tgm4883 said:**
> What error message? Looking at the README file it says



I don't see where it says to run configure. There also isn't a reason you can't open a .tar.gz file on Mythbuntu.

:EDIT:

Looking at the USB driver, it does list



But you don't mention USB in your post, you mention a card

I have a card not the usb.

How do I do this step: Install make, gcc, and kernel headers for your distribution.?

I thought that meant running ./configure

As for error message Ill get that later tonight when I get back to the problem machine.

---

### Post by Akriss on 2012-04-30
Hello,

Heres the steps I did to configure my Ceton after a fresh install of 12.04.

All I grabed was the linux drivers from Ceton and installed like the read me suggested.

######
make

sudo make install

sudo modprobe ctn91xx
######

Then I added to the end of my " /etc/network/interfaces " file:

auto ctn0
iface ctn0 inet dhcp

rebooted and setup the Ceton card in myth backend. I just fliped through the tuners in setup till I found the Ceton card. The setup has tip on what to do. 

Hope that helps

---

### Post by nickrout on 2012-04-30
> **supergokougt said:**
> I have a card not the usb.

How do I do this step: Install make, gcc, and kernel headers for your distribution.?

I thought that meant running ./configure

As for error message Ill get that later tonight when I get back to the problem machine.

```
sudo aptitude install build-essential
sudo aptitude install linux-headers-$(uname-r)
```

---

### Post by supergokougt on 2012-04-30
> **Akriss said:**
> Hello,

Heres the steps I did to configure my Ceton after a fresh install of 12.04.

All I grabed was the linux drivers from Ceton and installed like the read me suggested.

######
make

sudo make install

sudo modprobe ctn91xx
######

Then I added to the end of my " /etc/network/interfaces " file:

auto ctn0
iface ctn0 inet dhcp

rebooted and setup the Ceton card in myth backend. I just fliped through the tuners in setup till I found the Ceton card. The setup has tip on what to do. 

Hope that helps

here is what i have in my interfaces file:

auto lo
iface lo inet loopback
auto ctn0
iface ctn0 inet dhcp

look ok?

---

### Post by supergokougt on 2012-04-30
> **nickrout said:**
> ```
sudo aptitude install build-essential
sudo aptitude install linux-headers-$(uname-r)
```

to this i get command not found

but

i was still able to do the make, make install and modprobe ctn91xx

edit:
i didnt see anyfeed back in terminal after i entered the modprobe ctn91xx command

---

### Post by supergokougt on 2012-04-30
ok so for the first time i can log onto a browser and get the ceton card website much like how you get a router. 

when i check ifconfig -a here is what i get:
ctn0      Link encap:Ethernet  HWaddr 00:22:2c:ff:ff:ff  
          inet addr:192.168.200.2  Bcast:192.168.200.255  Mask:255.255.255.0
          inet6 addr: fe80::222:2cff:feff:ffff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30058 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10719829 (10.7 MB)  TX bytes:8888 (8.8 KB)
          Interrupt:16 

the read me says the ip should not be 192.168.200.1 and it isn't. Is this because I added those lines to the interfaces file and am now using dhcp?

also can i use a static ip address to do my normal Internet connection? or will this mess with these settings?

---

### Post by nickrout on 2012-04-30
> **supergokougt said:**
> to this i get command not found

but

i was still able to do the make, make install and modprobe ctn91xx

edit:
i didnt see anyfeed back in terminal after i entered the modprobe ctn91xx command

Sorry aptitude is not installed by default in ubuntu any more, you could have used apt-get instead.

But the tools were installed anyway, so why you asked how to install them is beyond me.

---

### Post by supergokougt on 2012-04-30
> **nickrout said:**
> so why you asked how to install them is beyond me.

The readme asked me to Install make, gcc, and kernel headers for your distribution.

you suggested those commands to do that step.

---

### Post by Akriss on 2012-05-01
> **supergokougt said:**
> here is what i have in my interfaces file:

auto lo
iface lo inet loopback
auto ctn0
iface ctn0 inet dhcp

look ok?

Yes.

> **supergokougt said:**
> ok so for the first time i can log onto a browser and get the ceton card website much like how you get a router. 

 when i check ifconfig -a here is what i get:
 ctn0 Link encap:Ethernet HWaddr 00:22:2c:ff:ff:ff 
 inet addr:192.168.200.2 Bcast:192.168.200.255 Mask:255.255.255.0
 inet6 addr: fe80::222:2cff:feff:ffff/64 Scope:Link
 UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
 RX packets:30058 errors:0 dropped:0 overruns:0 frame:0
 TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqueuelen:1000 
 RX bytes:10719829 (10.7 MB) TX bytes:8888 (8.8 KB)
 Interrupt:16 

 the read me says the ip should not be 192.168.200.1 and it isn't. Is this because I added those lines to the interfaces file and am now using dhcp?

 also can i use a static ip address to do my normal Internet connection? or will this mess with these settings?

thats all good from the ifconfig.

in myth setup use 192.168.200.1 it well work . . . =)

You can set a static ip address for you network card if you like. it well not affect the Ceton's card dhcp.

---

### Post by nickrout on 2012-05-01
> **supergokougt said:**
> The readme asked me to Install make, gcc, and kernel headers for your distribution.

you suggested those commands to do that step.

yes but you had the right packages installed anyway.

---

### Post by supergokougt on 2012-05-01
Thankyou guys so much this is the farthest I got so far.

When I clicked Watch TV it actually did something this time instead of giving me a message, but I am not getting a picture.

Since I am still testing I am not using a cable card. Should I use us-bcast instead of us-cable now? I am running from my cable line and my Time Warner Box still works. Should I run my cable box then to the card?

So the machine looks like it is set up to recognize card but I can not get a picture.

---

### Post by Akriss on 2012-05-01
> **supergokougt said:**
> 
Since I am still testing I am not using a cable card. Should I use us-bcast instead of us-cable now? I am running from my cable line and my Time Warner Box still works. Should I run my cable box then to the card?

So the machine looks like it is set up to recognize card but I can not get a picture.

I never had any luck useing the Ceton card with out a cable card. Sorry I cant be much help with that.

My cable co. has maybe 10 channles(at the most) that I could use without a cable card.

---

### Post by supergokougt on 2012-05-05
so things were......were going well, and then I tried updating the firmware on the ceton card. It said the process would take at most 5 minutes but a half hour later it looked like it was bricked. 

I think the computer lost the card since it wont show up at 192.168.200.1 

The card is blinking blue and the network settings utility should be run but I cant figure out how to use the download from this link:[http://cetoncorp.com/infinitv_support/linux_drivers/](http://cetoncorp.com/infinitv_support/linux_drivers/)

Since I wiped the machine recently I tried just reinstalling the Mythbuntu, but it is still blinking blue.

What could I type into terminal to reset the network connections?

Also off topic but equal frustration. Ever since I upgraded to 12.04 my remote desktop is frozen when I access from my mac using screen sharing. My movements show up on the screen hooked to myth machine but frozen on mac. Tough when the wife is watching the one tv which is hooked up to the computer and I want to go blind trying to figure this all out. 

Any ideas or reference links?

---

### Post by Akriss on 2012-05-05
Hmmm.

If I where in that situation. I would install the Ceton card on a Windows box and see if the Windows drivers/tools have any affect. if so, Great! 
If not. At least I would have all the Diag. stuff that Ceton tech. support would need to start a RMA of the bricked card.

---

### Post by supergokougt on 2012-05-06
> **Akriss said:**
> Hmmm.

If I where in that situation. I would install the Ceton card on a Windows box and see if the Windows drivers/tools have any affect. if so, Great! 
If not. At least I would have all the Diag. stuff that Ceton tech. support would need to start a RMA of the bricked card.

I was thinking that too, but finding someone with a windows tower is proving tougher than expected.

---

### Post by supergokougt on 2012-05-07
So I have been going back and forth with linux support at ceton and it has been pretty helpful. 

I got the IP address assigned temporarily. After reboot it is gone again. 

Here is what I got from support:
Running ifconfig directly was only supposed to be temporary to get you up and running. Network Manager is supposed to assign an address, but it doesn't appear to be working in your distribution.

You will need to configure the ctn0 interface for your distribution. I think in Ubuntu the network interfaces are configured in /etc/interfaces. 

How do I configure this card in ctn0?

---

### Post by tgm4883 on 2012-05-07
> **supergokougt said:**
> So I have been going back and forth with linux support at ceton and it has been pretty helpful. 

I got the IP address assigned temporarily. After reboot it is gone again. 

Here is what I got from support:
Running ifconfig directly was only supposed to be temporary to get you up and running. Network Manager is supposed to assign an address, but it doesn't appear to be working in your distribution.

You will need to configure the ctn0 interface for your distribution. I think in Ubuntu the network interfaces are configured in /etc/interfaces. 

How do I configure this card in ctn0?

You will want to take a look at [https://help.ubuntu.com/12.04/serverguide/network-configuration.html#ip-addressing](https://help.ubuntu.com/12.04/serverguide/network-configuration.html#ip-addressing)

Specifically the section 'Static IP Address Assignment'

Just change out eth0 for ctn0

That should work

---

### Post by inypd on 2012-09-08
HI 
I have a problem.  My network  disrepair. When mythbuntu is booting up, there is a message that 
says "waiting for network configuration" so my both Ceton and network card are disable.
When I removed 

auto ctn0
iface ctn0 inet dhcp

from /etc/network/interfaces
my network card came back to life, however the ctn0 is not working

What I should do to fix that problem?

---

### Post by speed32219 on 2012-09-11
sudo nano /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto ctn0
iface ctn0 inet dhcp

#CTRL O  Keyboard Presses
#CTRL X  KeyBoard Presses


Also, post output ifconfig

---

### Post by inypd on 2012-09-12
I reset the tuners under windows which fix the problem, but  need to use bridge under windows because I have 2 more PCs in my network.
 
Do you know is there any solution to keep the bridge under windows at  the same time to be able to use the ceton card under ubuntu? 

I am still no really happy of the performens of mythtv - have some lad  or live tv is not really smooth. That is the reason why I want to keep  windows  available too, and keep testing mythbuntu.

---

### Post by nickrout on 2012-09-12
You don't need bridging in your network setup just because you have more than one computer on your lan, so what you are saying makes no sense.

---

