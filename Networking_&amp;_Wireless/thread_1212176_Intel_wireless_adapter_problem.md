---
title: "Intel wireless adapter problem"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by xenex79 on 2009-07-13
Hi folks,

I'm new to linux and just started the cross over from Vista last week,

Specs:
Samsung R560 (laptop/notebook)
Intel core2Duo
GeForce 9600m GS
4GB RAM
Marvell Gigabit Ethernet
Intel Wlan (ver.12.1.2.1)

OS:
Ubuntu Studio x64



I've only tried a few distros thus far and i think i would like to settle with Ubuntu Studio as this machines primary use will be for multimedia content creation (until I can build a decent new Desktop for the purpose) but i'm open to any other suggestions on the distro front ;)

I first used plain Ubuntu Jaunty 9.04 which worked fine and there were no configurations needed for the wifi and since Ubuntu Studio is based on this it has been puzzeling me as to why i can no longer connect using this interface when switching to Studio, I can however connect using ethernet but its a wee bit restricting to drag a cable around the place so any instructions or pointers would be fab.

Here is some info:

from 'lspci'
```

02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
06:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)

```from 'iwconfig'
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"BTHomeHub-C3P0"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


```As i have said i'm really new to linux so explain it to me.... like i'm a 6 year old, if you need more info to help me let me know.

Regards,

Steve

---

### Post by xenex79 on 2009-07-15
No? nobody willing to take a guess at this one? I know the wifi is compatible because it works under plain ubuntu 9.04 right out the box after install with no fiddling or tweaking necessary, i'm just not sure whats missing from ubuntu studio.

Ubuntu studio is based on Jaunty 9.04 right? so why is this simple task made so difficult for mainstream hardware on modern linux OS's? Microsoft may be accused of a lot of things but at least because of its automated procedures my stuff just works without needing a criptologist to decipher how to install something that is expected to just work, whatever happened to simple naming conventions and to the point descriptive texts? geez the linux world doesn't half make things difficult for the new user does it, this is no doubt why my machine came with Vista and not a Linux distro in the first place.

In the past i have had to do stuff like compile software and design web pages so i'm not particularly afraid to get my hands dirty when it comes to code my aptitude is there for these things but the main problem i have found with Linux is that its just plain messy! there is no clear cut route to follow for info on something and when there is info its expected that you know all about Linux in the first place! again i am new to linux so any help on this one would reeaaally! be appreaciated.

---

### Post by martinbaselier on 2009-07-15
Picking on linux does not help you much, None of the users has much influence on the whole development, which is rather separated since it's split into a whole lot of different packages. 

If all hardware manufacturers would either create drivers themselves or provide the all the necessary technical information, there would be very little problems. The reality is however quite different.

Try installing xp on a sata HDD on a system without a floppy drive and then we'll speak again. My personal experience is that under windows I had to find out which hardware was in it, download a program to do so, find the drivers install them, reboot 20 times and have a working system with all necessary drivers and all updates. In linux all my hardware worked out of the box, I downloaded all updates rebooted once and I had a working system. 

**About the problem.**
Did you have the 32-bit version before or also the 64-bit? 
I presume it's the 32-bit, since ubuntustudio is just ubuntu with some extra packages installed. You could have installed ubuntustudio from ubuntu, it's a meta-package which installs all the extra packages.


You output show the wireless card is working, it's just not connected. 

I presume you use networkmanager, a graphical interface, to connect. 

Do you have encryption enabled? If so, is it WEP/WPA/WPA2 ?

Have you checked the settings in networkmanager? (it's in the settings section, or you can access it by right clicking on the network icon on your task bar)

Edit: the problem might also be related to the realtime kernel. You could try and start synaptic (from the settings section), click on a random package in the list and type linux=image, then choose linux-image-2.6.28.13-ge (ge stands for general), install it, reboot, enter the bootmenu (you might need to press Esc to do so) and choose the general kernel instead of the realtime one.

---

### Post by xenex79 on 2009-07-15
As much as i appreciate that the development on Linux distros is fragmented because developed is done by many people often in their spare time voluntarily and at times development can be slow i assure you it is not my intension to be "picking on" Linux i am merely stating the obvious of an alternative OS of which i have made the decision to switch to, i have no preference to brands just how they work... still the core of most distros lack the simple plug and play detection that most modern OS's should have by now in this day and age.

As for the hardware manufacturers not releasing technical info or releasing their own Linux drivers i fully understand the problem this presents but as i stated before this is not the case with my problem as the wireless worked with the original Ubuntu 9.04 x64 distro it is something not quite setup on the Ubuntu Studio x64 distro that is the problem and like all things on Linux so far its like pulling teeth to find out about what to do to get things to tick because everything is written like the user should know what Linux is all about and is often never explained for noob's like myself who are accustom to wizards and more plug and play "friendly" environments such as Windows.

> **martinbaselier said:**
> Try installing xp on a sata HDD on a system without a floppy drive and then we'll speak again

I actually did this very thing on a RAID system i build a couple of years back on a system designed for x64 when it was relatively unheard of in the home user market at the time and my experience was quite pleasant even without the floppy drive (which i have not used in a system since CD media became universally available) i received a CD with the needed SATA drivers and as i always did back then i integrated these drivers into my custom XP CD but then again i'm more familiar with Windows than Linux and this is my main point with the info not being easy to figure out on Linux.

> **martinbaselier said:**
> **About the problem.**
Did you have the 32-bit version before or also the 64-bit? 
I presume it's the 32-bit, since ubuntustudio is just ubuntu with some extra packages installed. You could have installed ubuntustudio from ubuntu, it's a meta-package which installs all the extra packages.

I have the 64-bit version of Ubuntu Studio currently installed with no wifi, when i was using just Ubuntu 9.04 "Jaunty" i also had the 64-bit version installed and had no problem with the wireless at all.


> **martinbaselier said:**
> You output show the wireless card is working, it's just not connected. 

I presume you use networkmanager, a graphical interface, to connect. 

Do you have encryption enabled? If so, is it WEP/WPA/WPA2 ?

Have you checked the settings in networkmanager? (it's in the settings section, or you can access it by right clicking on the network icon on your task bar)

Yes i use the networkmanager and it detects wlan0, i have filled in all relevant settings but in Ubuntu Studio i have no icon in the task bar and i may be wrong but i think it is a different networkmanager used than in the normal Ubuntu 9.04 "Juanty".

My router uses WEP encryption by default which i leave it on but can use WPA/WPA2.

I have a sneaky suspicion that the problem may be certain modules Ubuntu Studio does not install for my hardware but as i cannot figure out which ones specifically i am not having an easy time learning what to look for as info is limited or cryptic, don't get me wrong i Like the ideas and principles of Linux and its distros (else i would not put it on my machine) but by heck its not for the uninitiated.

Thanks for the relpy its appreciated that the community does help out NOOBZ :p


Edit: Sure the kernel may very well be the issue i will follow up on that one.

---

### Post by xenex79 on 2009-07-16
Well after much reading and head scratching I've decided that Ubuntu Studio is probably not going to benefit my machine anymore than Ubuntu probably will so i have opted to reinstall Ubuntu as at least my wireless works with that, if anyone can tell me what the major difference between the two are and if there is indeed any performance gains from using Ubuntu Studio rather than plain old Ubuntu or whether it is just cosmetics and specific packages for multimedia content that would be good.

I'm still interested if anyone wants to try and help diagnose my original problem but at this point since its my first time using Linux i want to just spend my time using it as apposed to diagnosing it :p

Regards,

Steve.

---

### Post by martinbaselier on 2009-07-17
You can transform your ubuntu-install into ubuntu-studio.
Open a terminal and type:
**sudo apt-get install ubuntustudio-desktop**

To see which packages will be installed, you can do a simulation by:
**sudo apt-get install ubuntustudio-desktop -s**

About the sata driver thing: I got it working in the end too, but it took a lot of reading and I wouldn't call it user friendly. It's always a hassle if some particular piece of hardware is not working. It's of course a lot easier if you know the operating system.

About ubuntu-studio: I've tried it in the past and removed it again. I prefer to install individual programs that I need and use, rather than installing a whole lot of them of which I only use a small part. I find it easier to just install one (or a few) application(s) at a time and test if I like it and if not, remove it. 

What are you planning to do on it?

Music or video? 

If it's music, I could give some advice. It would be nice to know a bit more, do you want to record music or create your own music, what genre would it be?

It would be better to create a new topic for it (something like good programs for creating ...) 
[wikipedia is great starting point too](http://en.wikipedia.org/wiki/Linux_audio_software)

---

### Post by xenex79 on 2009-07-17
Thanks again for your input on this.

> **martinbaselier said:**
> You can transform your ubuntu-install into ubuntu-studio.
Open a terminal and type:
**sudo apt-get install ubuntustudio-desktop**

To see which packages will be installed, you can do a simulation by:
**sudo apt-get install ubuntustudio-desktop -s**

Great tip, i was unaware that Ubuntu Studio was installable from Ubuntu, does this mean that Ubuntu Studio is no more effective than Ubuntu performance wise?

> **martinbaselier said:**
> About the sata driver thing: I got it working in the end too, but it took a lot of reading and I wouldn't call it user friendly. It's always a hassle if some particular piece of hardware is not working. It's of course a lot easier if you know the operating system.

Yes indeed everything is easy once we have the information, experience and can understand it but i feel that there are some points that should be covered by Linux distros like my issue with the wireless card though it is obviously compatible it may just as well not have been for all the confusion it caused and i feel these issues should be dealt with first and made more simplified than focusing on getting desktop eye candy and the likes into the distros.

Of course there will always be compatibility issues in all OS's when it comes to hardware detection but despite all Microsoft's faults in certain areas (yes i have had my fair share of problems with MS too) I have taken for granted the work that Microsoft does in its OS's specifically to automate hardware detection and setup, i feel in this day and age this should be first priority to consider for the end users sanity, I do however sympathize with Linux users who rely on open source alternatives when manufacturers should have the common decency to develop for as many alternative OS's as possible.

> **martinbaselier said:**
> About ubuntu-studio: I've tried it in the past and removed it again. I prefer to install individual programs that I need and use, rather than installing a whole lot of them of which I only use a small part. I find it easier to just install one (or a few) application(s) at a time and test if I like it and if not, remove it.

As i'm still getting used to Linux and how the package/module based thing all works i'm still at the bottom level of knowing what is better to use in order to setup my machine for maximum multimedia performance.

> **martinbaselier said:**
> What are you planning to do on it?

Music or video? 

If it's music, I could give some advice. It would be nice to know a bit more, do you want to record music or create your own music, what genre would it be?

It would be better to create a new topic for it (something like good programs for creating ...) 
[wikipedia is great starting point too]("http://en.wikipedia.org/wiki/Linux_audio_software")

There will most likely be need for both Audio and Video editing/creation but i would say that the bulk usage will be 3D graphics including real-time graphics, while i was still a Vista user i made the switch from 3D Studio Max to Blender 3D and it was this along with various other factors that nudged me to become an open source fanatic :P using Linux is just another step down this road as i like the amount of control given to the user.

Best regards,

Steve.

---

### Post by linuxnola on 2009-07-24
I have the same problem.  I just installed Ubuntu Studio.  Wireless worked on the LiveCD but do not have the network icon on the taskbar.

lspci yielded:

00:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

iwconfig yielded:

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by linuxnola on 2009-07-24
forgive me the happy face was supposed to be "=o"

---

### Post by xenex79 on 2009-07-26
Hi Linuxnola,
 
Sorry for the late reply i have not had the chance to check my emails for the past few days and therefore missed your post alert.
 
Try this and see how you get along,
 
First install networkmanager from Synaptics, just do a search for it and make sure the 'all' category is chosen and you should find it no problem.
 
after you have it installed restart your machine and then you should see it in your taskbar then either right click on the icon to configure or continue to menu System>Administration>Network and check/review that all settings are correct.
 
If you are still having troubles let me know and i'll try and help out some more as i had some problems getting wireless to work to begin with but i have it working with Ubuntu Studio now.
 
Edit: Oh by the way if you want you can put any output between BB code braces ["code]YOUR TEXT HERE[/code"] just take away the ""'s when doing it for real, that way you wont end up with the smillies ;)
 
Like this:
 
```
lspci yielded:
 
00:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
 
iwconfig yielded:
 
lo no wireless extensions.
 
eth0 no wireless extensions.
 
wifi0 no wireless extensions.
 
ath0 IEEE 802.11b ESSID:"" Nickname:""
Mode:Managed Channel:0 Access Point: Not-Associated 
Bit Rate:0 kb/s Tx-Power:0 dBm Sensitivity=1/1 
Retry:eek:ff RTS thr:eek:ff Fragment thr:eek:ff
Power Management:eek:ff
Link Quality=0/70 Signal level=0 dBm Noise level=0 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
 
pan0 no wireless extensions.

```
 
Regards,
 
Steve.

---

### Post by chavafloresv on 2009-12-03
Hi Xenex79,

Ok i'm also new to Linux stuff, i had the 8.04 ubuntu and i remember i had a lot of work to get my wireless work, but i did it. (also a BIG problem to see the GRUB).

I now installed the whole UbuntuStudio, which is based on Ubuntu 9.10 the newest.

So, i saw you were asking what special features offered the ubuntustudio other than just adding a lot of applications, well maybe you know by now, but i think the main advantage is the real time kernel, i think its great!
I'm a musician and believe in this ideology of the GNU, thats why I'm willed to get this to work...

So, I'm just missing my wireless connection ...

I have tried several things, I installed something called wcid but didn't help, the I did what you suggest, but it still isn't working.

Is that all you have done to get your wireless work?

---

### Post by xenex79 on 2009-12-03
Wow I only just barely remember this thread lol.
 
Yes the instructions I gave in a previous post was how I managed to get my wireless working. Perhapse if that method isn't working for you its possible you may need to try another, there are other threads relating to wireless problems and some are manufacturer and model specific, try searching the forums for the make and model of your wireless device.
 
There is also a chance that your wireless device is not supported at all! have you had your wireless working on any other Ubuntu distro's?
 
My particular problem was just installing the specific modules needed if I remember correctly, it was a pain at the time and had taken several attempts to finally get it to work.
 
If you have any specific questions just let me know and i'll try and help you out more.
 
Good luck on getting your wireless up and running.
 
Steve

---

### Post by chavafloresv on 2009-12-04
Yes, I had my wireless card working fine with Ubuntu 8.04 before, and with windows XP, its the same card.

I have to research a little more, yes, thanks

---

### Post by uncaspi on 2009-12-04
Try to remove all lines except auto lo and iface lo inet loopback in /etc/network/interfaces and then reboot.

---

