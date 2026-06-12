---
title: "mythbuntu 12.04 - ceton card no IPV$"
date: 2012-07-07
forum: Mythbuntu
---

### Post by inypd on 2012-07-07
Hi,
 I have issue when I trying  to use mythbuntu 12.04. when I install the drivers for Ceton card
I have only IPV6(inet6 addr: fe80::222:2cff:feff:ffff/64), IPV4 is not  available. Do you have any suggestions how to fix that issue. In addition, if I disable IPV6, still IPV4 does not appear.

---

### Post by Akriss on 2012-07-07
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

 rebooted and setup the Ceton card in myth backend. I just fliped through the tuners in setup till I found the Ceton card. The setup has tips on what to do. 

 Hope that helps.


p.s. more info in this post may help.[http://ubuntuforums.org/showthread.php?t=1969067&highlight=ceton]("http://ubuntuforums.org/showthread.php?t=1969067&highlight=ceton")

---

### Post by inypd on 2012-09-08
HI 
that work for a while, however, there is another problem. My network disrepair. When mythbuntu is booting up, there is a message that 
says "waiting for network configuration" so my both Ceton and network card are disable.
When I removed 

auto ctn0
iface ctn0 inet dhcp

from /etc/network/interfaces
my network card came back to life, however the ctn0 is not working

What I should do to fix that problem?

---

### Post by Akriss on 2012-09-08
Hi,

Do you know when there is a kernel update from update manager, you well need to rebuild the Ceton drivers again? Right?


;)

---

### Post by inypd on 2012-09-09
HI,
 
probably there was an update because everything was working good and last week stopped.
how can I check that?

I try to do to install ceton drivers with 
######
 make

 sudo make install

 sudo modprobe ctn91xx
 ######

still nothing 

any suggestions?

---

### Post by Akriss on 2012-09-10
> **inypd said:**
> HI,
 
probably there was an update because everything was working good and last week stopped.
how can I check that?


Quoted from [HTML]http://www.cyberciti.biz/faq/how-do-i-update-ubuntu-linux-softwares/[/HTML]
"Using Ubuntu Update Manager tool

This is GUI tool. It works like Microsoft /Red Hat update manager i.e. you will see a little icon in the kicker bar/taskbar when there are updates. It will only appear when new upgrades are available. All you have to do is click on it and follow the online instructions.

You can also star GUI tool by Clicking System > Administration > Update Manager"


Is your Ceton card networked bridged?

---

### Post by inypd on 2012-09-10
HI
Actually I believe when I update to 3.0.29 the I lost my networking.

I don't thing is bridged.
how can a check that?

In /etc/network/interfaces I have only 

auto lo
iface lo inet loopback
auto ctn0
iface ctn0 inet dhcp

Do I have to have anything else?
Yesterday, I installed the new 12.4.1 mythbuntu, with fresh install of the ceton linux driver, and still nothing.
If I remove 
auto ctn0
iface ctn0 inet dhcp

the network is back, and ceton is disable.
when I put it back.
message with wait network configuration appears again on booting screen.
and network is down again.

---

### Post by Akriss on 2012-09-10
I would try and reset the Ceton card. Ceton has a reset utility available for linux at [http://cetoncorp.com/infinitv_support/linux_drivers/](http://cetoncorp.com/infinitv_support/linux_drivers/) .

 However I have found that reseting the card in a windows computer much more easy. and the windows driver package has good diagnostic tools for the card.


The linux reset utility is a python script. if you know how to run a python script you can try it. But again. The windows driver package is easy.

---

### Post by inypd on 2012-09-11
I forgot to mention that I have windows installed too. Everything is working under windows, however, under Ubuntu have that problem

---

### Post by Akriss on 2012-09-11
Good reset the card then.

The windows driver package most likely set the card in bridged mode. which is not needed for a stand alone installation.

---

### Post by inypd on 2012-09-12
that fix the problem, but  need to use bridge under windows because I have 2 more PCs in my network.
 
Do you know is there any solution to keep the bridge under windows at the same time to be able to use the ceton card under ubuntu? 

I am still no really happy of the performens of mythtv - have some lad or live tv is not really smooth. That is the reason why I want to keep windows  available too, and keep testong mythbuntu.

---

### Post by Akriss on 2012-09-12
> **inypd said:**
> that fix the problem, but  need to use bridge under windows because I have 2 more PCs in my network.
 
Do you know is there any solution to keep the bridge under windows at the same time to be able to use the ceton card under ubuntu? 


Great glad to hear that the reset work.

Sorry I can help with the Windows side of it.

I run Mythtv/Mythbuntu exclusively.

---

### Post by nickrout on 2012-09-12
> **inypd said:**
> that fix the problem, but  need to use bridge under windows because I have 2 more PCs in my network.
 
Do you know is there any solution to keep the bridge under windows at the same time to be able to use the ceton card under ubuntu? 

I am still no really happy of the performens of mythtv - have some lad or live tv is not really smooth. That is the reason why I want to keep windows  available too, and keep testong mythbuntu.

It is very confusing if you keep posting identical messages to two different threads, and if your posts are full of spelling mistakes.

---

### Post by inypd on 2012-09-13
My apologies for that posting.

It looks like you are really smart, but under WMC, 3 PC cannot work without bridging the ceton card on the server because tuners have to assigned to each PC in order to watch TV.

---

### Post by inypd on 2012-09-13
[Akriss]("http://ubuntuforums.org/member.php?u=406480"), 
do you have any problems with the quality of the picture under mythbuntu?

when I compare the qualities of WMC and mythbuntu, mythtv looks really poor.
I have some lag, freezing or jumping between the frames.
 
Do you thing that could be some configuration issue?
I have

Asus F1A75-m PRO/CSM
AMD A8 3870k  cpu+GPU 
8GB DDR 3 ram  G.Skill
Kingston 120 SSD hyper X

Any ideas what could causing these problems with the picture?

---

### Post by Akriss on 2012-09-13
> **inypd said:**
> 

Any ideas what could causing these problems with the picture?


Yes I do.

From looking at your computer specs. you are using an AMD GPU (or CPU/GPU combo).

Although the drivers can/should work. It is still kind of complicated to setup correctly ATM.

For a great picture, easy setup and compatibility (out of the box) Nvidia video cards are the way to go. All my frontends have them.

P.S. A little lite reading for you from the Mythtv Wiki about video cards [[COLOR="Red"]HERE[/COLOR]]("http://www.mythtv.org/wiki/User_Manual:Setting_Up#Graphics_cards")

---

### Post by nickrout on 2012-09-13
> **inypd said:**
> My apologies for that posting.

It looks like you are really smart, but under WMC, 3 PC cannot work without bridging the ceton card on the server because tuners have to assigned to each PC in order to watch TV.

OK so you are trying to bridge the ceton ip address to the host's lan ip address so that other computers on your lan can access the ceton card?

That is NOT how mythtv works. Myth needs exclusive access to the ceton card. If other computers want to access the ceton card then they should run mythfrontend connected to the mythbackend which is running on the host with the ceton card in it.

---

### Post by inypd on 2012-09-14
nickrout,
I don't want to be rude. 
 
I never said that i am bridging ceton card and network card under ubuntu with mythTV. I said under Windows Media center (WMC) i had to do that, which in my case was actually causing the problem when tried to boot mythbuntu. 

To solve the problem I had to reset my ceton card configuration.
 Thank you  any way for your help.

---

### Post by inypd on 2012-09-14
I will buy one Geforce GT 430 card these days, and will see is there any improvement.
Thank you

---

