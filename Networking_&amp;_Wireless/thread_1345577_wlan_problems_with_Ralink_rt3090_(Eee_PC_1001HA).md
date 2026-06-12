---
title: "wlan problems with Ralink rt3090 (Eee PC 1001HA)"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by basislinie on 2009-12-04
Hello everybody
 
I installed Ubuntu 9.10 on a netbook with Ralink Wlan device. (rt3090)
Out of the box the device was **not** recognized. 
I searched a bit and found this package for ubuntu:
[https://launchpad.net/~markus-tisoft/+archive/rt3090](https://launchpad.net/~markus-tisoft/+archive/rt3090)
I installed it, made a reboot and the device is recognized!
So i can search for hotspots with iwlist...scan and so on. 
But the problem: I can´t connect to my router (WPA2).
The network manager ask me for the key when choosing my routers SSID
and trys to connect for about 2 minutes. Then there´s coming a message like "No connection you are offline now".
 
Is there a problem with wpa and the driver?
Please can somebody helb me?
 
(console information I can give you in the evening...i´m working now...)
 
Thanks

---

### Post by Julita on 2009-12-04
This is the right topic for you: [http://ubuntuforums.org/showthread.php?t=1313132&highlight=1001ha](http://ubuntuforums.org/showthread.php?t=1313132&highlight=1001ha) everything is discussed there, and the solution is provided (namely, applying kernel patch...) well, you'll read :)

---

### Post by dave789 on 2010-01-01
i was pretty excited to find this thread, until i realized it would take me hours to figure out how to download this package.  i will spare you the details, most of you know the deal.  i love the idea of ubuntu and the ubuntu community, but there is a long way to go if they ever want to make this a feasible option for today's average computer person.  when i first heard of ubuntu a year and a half ago i was very excited about it and mentioned it to my dad.  he was apparently also excited and tried to do something with it which according to my sister who is a windows network engineer was a total disaster.  no surprise there!  after the experience i have now gained i would never even consider having my dad have a go at it.  he was an engineer and is not dumb, but he is now 74 years old and would not have a chance at all at dealing with the frustration and trying to comprehend the lingo presented in the posts that are supposed to help the new user.  afters hours... days (maybe weeks) i got my old laptop going satisfactorily last year with 8.10 and was pretty happy.  a year later, even with the first experience, i am killing myself just trying to get a wlan connection for my new netbook.  i appreciate that the nature of linux OSs require the user be more proactive, but without documentation that makes sense and the average person can work thru, windows is going to have the 90%+ of the OS market for a LONG time to come. 

i am not posting a direct question because i do not want to wait for an answer.  i will google and scream till i finally figure it out, but it will feel like always... a fight against the very people that are trying to help me.  if this post is against all of the forum rules, i must be honest and admit i did not thoroughly read them as i must spend my time elsewhere.

---

### Post by dave789 on 2010-01-01
ok, it was good to release that pressure.  i still feel what i wrote is valid, but a half hour after i wrote it i was wireless surfing.  that i did not expect.  perhaps i am getting better.  reading another post, it was revealed to me that to download the package you must double click on the deb file.  this i had seen when playing on the page.  so to be exact.

1  click on link in first post above
2  on this page click on 'view package details'   in a little blue font
3  click on the appropriate software package for your ubuntu version i.e. jaunty or karmic
4  in the expanded content list that appears you will see a deb file.  double click on it.
you should have a package installer window open up.  click OK.

the rest is self explanatory even for me.  do not forget to restart the computer to implement the package.  

i am using wifi radar to manage my wireless.  i don't know if this is a must, but if you can't get wlan to work you may want to give it a try.  

SYSTEM>ADMINISTRATION>SYNAPTIC PACKAGE MANAGER>SEARCH - wifi

you will also have to set your security settings in wifi-radar and/or network connections so that they match with your router.

this works for me, but i am only using WEP security.  basislinie in the first post apparently was having trouble with WPA2.  and lastly i would like to say that my last post was not directed at basislinie as he/she was only posting a question and not offering answers, but we all must realize that what we have figured out may be a big help to somebody else and save them a lot of frustration...  so please try to dumb it down a little for those of us who need it.

thanks and good luck.

---

### Post by dave789 on 2010-01-02
yeah, i wrote too soon. i now know my netbook can surf wireless with ubuntu because i was doing it for few hours. i forgot, however, that with ubuntu you better test it for a while before you assume any issue is solved. the next time i turned it on, my wireless card was not enabled and on top of that my lan connection was no longer recognized. it occured to me suddenly that on the Eee PC 1001ha there is a wlan switch in the keyboard combo Fn-F2 ( i have done a lot of surfing in windows and never had to mess with this switch ). unfortunately when i tried it, although my card was recognized and wifi-radar could see wireless networks, i couldn't connect to them. if anyone has suggestions, i welcome them.

---

### Post by dave789 on 2010-01-03
i am learning to supress excitement with ubuntu, but i a now seem to have both LAN and wireless and i have shut down and powered up twice and they were still there.  what did i do?  bye bye wifi radar, hello wicd.  i did it all in synaptic package manager.

---

### Post by mb36 on 2010-01-11
> **dave789 said:**
> i am learning to supress excitement with ubuntu, but i a now seem to have both LAN and wireless and i have shut down and powered up twice and they were still there.  what did i do?  bye bye wifi radar, hello wicd.  i did it all in synaptic package manager.

Thanks for the short summary list in post #4, and thanks to everyone who led you on the way! It worked just fine for me, I was up and running wlan in five minutes. I was confused by earlier forum posts about recompiling the kernel, but I suppose those solutions are obsolete in this particular case now that the driver is available from Markus Heberling's PPA.

I bought my Eee 1001HA last week at a really good price (SEK 2500) and UNR 9.10 seems to work wonderfully with it. Everything except wifi seems to work out of the box. It is (this far) a great step forward compared to my earlier Eee 900. I have got that one to work fine with Eeebuntu 3 LXDE beta, though. Gnome made it too sluggish.

Mårten

---

### Post by monarchheels on 2010-02-04
dave789, thanks for your posts. As another newbie linux user, I can relate to your frustrations. I just keep telling myself "think of how much I'm learning!" although so far, that hasn't got my Ralink rt3090 card working on a MSI U210 with UNR.
I've received some feedback on other threads that I'm about to try... crossing my fingers...

---

### Post by zibletop on 2010-02-06
Hi,
> **mb36 said:**
> I suppose those solutions are obsolete in this particular case now that the driver is available from Markus Heberling's PPA.

Yes the [ppa of Markus]("https://launchpad.net/~markus-tisoft/+archive/rt3090/+index?field.series_filter=karmic") is fast and stable on WPA (TKIP+AES) however, it does not work for me on WPA (AES/CCMP).

To install it, add this package repository:
```
deb http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu karmic main
```

Then type on a terminal:
```
sudo apt-get update
sudo apt-get install rt3090-dkms
```

---

### Post by tim1980 on 2010-03-09
I have updated to Lucid Lynx and need to get the rt3090 working on my eeepc 1001ha

I'm very annoyed that all the PPA's on launchpad don't work in Lucid, why do they only work in karmic?

Where can I get a driver for Lucid

Why in the world isnt the driver just built in by now, this is the most common netbook and Ubuntu does not work with wireless for it means lots of bad press

---

### Post by Julita on 2010-03-23
> **tim1980 said:**
> I have updated to Lucid Lynx and need to get the rt3090 working on my eeepc 1001ha

I'm very annoyed that all the PPA's on launchpad don't work in Lucid

OMG! is that truly so? I am waiting desperately for that release! It is a disaster for me because right now I have only wireless! At such moments I regret I am not a programmer mysefl :) By the way, the driver is available from ralink webpage: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) just click on the RT3090PCIe, and you will be obliged to accept their terms of use, etc.

---

### Post by Soadyheid on 2010-04-04
@Dave789
I've just got my Asus Eee PC 1001HA and found the same problem occurring with the WiFi.  I've not summoned up enough courage to blow away XP and so have run a live version of Ubuntu 9.10 from a 4Gb USB memory stick.
ifconfig shows just eth0 (Wired port) and l0 (loop back)
I followed the rt3090 link and downloaded it to another usb stick, then extracted it.  Lo and behold, it's updated the Live Ubuntu 9.10 stick and we're good to go! :)
ifconfig now shows an additional ra0 :D  Ye Ha!
Thanks again, I just need to complete the install now.  It connected to my router without problem then Infinity and beyond...

Play Bonny!

---

### Post by linbeans on 2010-04-10
Hello Soadyheid,

Can you please explain your last post a bit more, the unpacking etc..

Regards

---

### Post by Blyth on 2010-05-06
> **Soadyheid said:**
> @Dave789
I've just got my Asus Eee PC 1001HA and found the same problem occurring with the WiFi.  I've not summoned up enough courage to blow away XP and so have run a live version of Ubuntu 9.10 from a 4Gb USB memory stick.
ifconfig shows just eth0 (Wired port) and l0 (loop back)
I followed the rt3090 link and downloaded it to another usb stick, then extracted it.  Lo and behold, it's updated the Live Ubuntu 9.10 stick and we're good to go! :)
ifconfig now shows an additional ra0 :D  Ye Ha!
Thanks again, I just need to complete the install now.  It connected to my router without problem then Infinity and beyond...

Play Bonny!

Potentially the most helpfull yet the most retarded post in that you didnt leave information to help others looking to install the driver.

Have a nice day...

---

### Post by good_times on 2010-05-15
Hello dave789 and thank you so much!!! 
Despite your rantings (and to be honest, as a relative newbie myself, I feel your pain!) your step-by-step worked perfectly for me!!
I've been trying since the 10.04 upgrade to get my wireless working and I could not get it to go on my own and the strange programming language going on around the subject was way way beyond me.
I had set up a dual boot situation and all worked fine with win7, but I wanted to carry on with 10.04. So using my connection from win7, I followed your guide and downloaded the deb file. Then I unpackaged it after reboot into 10.04. Network Manager was still not having any of it so I used RutilT WLAN Manager and it worked perfect first time after a scan.
Following your advise from later posts (!) I did a reboot and this time NetMan woke up and all's good!! Hooray at last!!

Many thanks again dave789, I think sometimes people forget that there are users out there that love Ubuntu but aren't experts. Linux is for the people remember...

Roy

---

### Post by topolab on 2010-05-31
> **zibletop said:**
> Hi,

To install it, add this package repository:
```
deb http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu karmic main
``` 
hmm.. deb command didnt work for me,
so i didnt need to type this one:
> 
Then type on a terminal:
```
sudo apt-get update
sudo apt-get install rt3090-dkms
```
BUT:
Finally i just downloaded this thing
[https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb](https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb)
opened it with deb and installed all packages my asus needed so
i have my wireless working now!!!
thanks for all people

---

### Post by topolab on 2010-07-05
hm... just got all updates and my eee 1001ha doesnt recognise my wifi :~
iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

lspci:
01:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe


######
i had to modprobe

sudo modprobe rt3090sta

to make it work again like charm

---

### Post by rvr on 2010-07-07
The emergency line for me was to install pclinuxos (or mandriva) and get the drivers from synaptic. They are a little less strict on open source software.
 Then you also don`t have to install again after each kernelupdate.

---

### Post by Johnsie on 2010-08-03
I recently supplied some eeepc 1001ha machines to some friends in Honduras who work with homeless/impoverished children. I was hoping to install Ubuntu on those machines while I am here because the software is free and they can't afford to pay for software, but unfortunately the wi-fi won't work with Ubuntu. They need to be able to access wpa2 lans and this issue prevents them from doing that.

[IMG]http://i564.photobucket.com/albums/ss83/steekyjim/DSCF3394-1.jpg[/IMG]

[IMG]http://i564.photobucket.com/albums/ss83/steekyjim/2-1.jpg[/IMG]


I hope this issue can be resolved quickly and natively.

---

### Post by Johnsie on 2010-08-08
Sadly I was unable to resolve this on time. As a result I ended up installing Windows as the default OS on the machines with a Wubi Ubuntu install as the second OS. The users will mostly be using Windows because the wireless works better in Windows. Not the ideal solution, but at least they will have computers that work and that is the important thing.

---

### Post by mb36 on 2010-08-10
Good news!

Yesterday wifi stopped working on my EeePC 1001HA. Well, actually it only stopped picking up my Wireless N router, while other routers in the building were visible. I thought I might try to uninstall and reinstall Marcus H's PPA driver. Surprisingly, on reboot after uninstall wifi is still up, and what's more, it picks up my router again! This must mean that the wireless card has become supported with the latest kernel update, and that this caused a conflict with the separate PPA driver.

---

### Post by topolab on 2010-09-28
i got the new kernel again and..
no card :(

---

### Post by zebraneo on 2010-11-06
I downloaded the driver from [http://eng.ralinktech.com.tw/support.php?s=2](http://eng.ralinktech.com.tw/support.php?s=2)
put I have no idea what to do with the driver??? Do I put is somewhere or what thanks

---

### Post by chili555 on 2010-11-06
> **zebraneo said:**
> I downloaded the driver from [http://eng.ralinktech.com.tw/support.php?s=2](http://eng.ralinktech.com.tw/support.php?s=2)
put I have no idea what to do with the driver??? Do I put is somewhere or what thanksIsn't the RT3090 chipset now supported by rt2860sta? Did you try that first?```
modinfo rt2860sta
filename:       /lib/modules/2.6.35-22-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
version:        2.1.0.0
[COLOR="Red"]alias:          rt3090sta[/COLOR]
license:        GPL
description:    RT2860/[COLOR="Red"]RT3090[/COLOR] Wireless Lan Linux Driver
author:         Jett Chen <jett_chen@ralinktech.com>
firmware:       rt3090.bin
firmware:       rt2860.bin
```

---

### Post by zebraneo on 2010-11-06
where do I get rt2860sta

thanks

---

### Post by chili555 on 2010-11-06
It's built-in. Please do:```
sudo modprobe rt2860sta
lspci -nn
```Post the lines related to your wireless card.

---

### Post by Jiawen on 2011-01-29
I just upgraded my MSI U230 netbook to the latest kernel (2.6.32-28) and got this problem. In order to get on the net, I need to use an older kernel (2.6.32-27).

```
sudo modprobe rt2860sta
``` appears to work but doesn't give any messages. Doing ```
sudo modprobe rt3090sta
```gives the error
```
FATAL: Error inserting rt3090sta (/lib/modules/2.6.32-28-generic/updates/dkms/rt3090sta.ko): Invalid module format
```I've tried doing the manual compiling of drivers and whatnot, but I keep getting hung up on errors I don't know my way out of (and which none of the howtos seem to explain). I'm able to access the net by booting into the older kernel, but I'd rather not have to.

Any help would be much appreciated!

---

### Post by chili555 on 2011-01-29
> but I keep getting hung up on errors I don't know my way out ofMaybe I do. What errors are you getting? Please copy and paste from the terminal to a text document so you can post here.

---

### Post by Jiawen on 2011-02-02
Okay, I tried it again and it seems to have worked. I think I was getting confused about which files to use, and where. I've gotten a couple funky depository/update glitches since then, but it doesn't seem to be a major problem.

---

### Post by nir2000 on 2011-04-09
[https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb](https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb)

---

### Post by kWahab on 2011-04-09
I have an HP ProBook 4520s with the RT3090 wifi chipset.

On a fresh install of Ubuntu 10.10 maverick. I added this to the end of "/etc/modprobe.d/blacklist.conf":

blacklist rt2800pci

Restarted and the wifi was working normally.  

I guess the rt2800pci and rt2860sta don't play nice together.

Hope this helps.

---

### Post by bugslayr on 2011-04-09
Hello,
I can confirm kWahab's post for Natty Narwhal beta 1 on an HP ProBook 4720s.

I scaned the thread for "Bluetooth" ... nobody mentioned it ...
That's why I'd like to ask whether people who got WLAN with the rt3090 chipset working, also got Bluetooth (BT 3.0) working?
The system seems to recognize that Bluetooth is switched on, but it is not possible to detect orther Bluetooth devices.
Eager to hear about your experiences ...
Cheers!

---

### Post by Jiawen on 2011-04-30
New confusion: when I boot into kernel 2.6.32-28-generic, my wireless connection works perfectly. When I boot into any more recent kernel (2.6.32-29, -30 or -31), however, wireless doesn't work. Anyone know why that would be?

---

### Post by bugslayr on 2011-05-01
> **Jiawen said:**
> New confusion: when I boot into kernel  2.6.32-28-generic, my wireless connection works perfectly. When I boot  into any more recent kernel (2.6.32-29, -30 or -31), however, wireless  doesn't work. Anyone know why that would be?

Hi Jiawen,
did you apply the blacklist changes as described by[ kWahab]("http://ubuntuforums.org/member.php?u=231514") in posting #31? They did the trick for me on the HP ProBook.
Maybe some changes after 2.6.32-28-generic were incompatible with the WLAN adapter.
There seem to be a couple of modules, which might get loaded for this WLAN adapter. You may find out which one is currently loaded by issuing "lspci -nnk"
Could you please check which ones are loaded with the various kernels you mentioned.
If they are different, try unloading (modprobe -r) the one that does not work and load the working one.
If that is successful, blacklist the module that does not work.

This thread also mentions a ppa archive which introduces a new DKMS enabled driver from Ralink. As far as I saw, it is not the latest version ... you may get the latest one from the Ralink page ... it requires a simple one line change to compile (I currently don't have access, but let me know if I shall post the changes).

Cheers :-)

---

### Post by traffas on 2011-05-04
In case it helps anyone else...

I didn't notice any connectivity problems on an HP desktop with an RT3090 and a fresh install of Natty. 10.10 didn't work without some mod work, but 11.04 seemed to detect and connect just fine with the RT3090, so I thought it was fixed.

My problem was with Synergy. Using Ubuntu as a server and a Windows 7 as a client, the mouse on the client was very, very jerky.

Doing as kWahab suggested and adding "blacklist rt2800pci" to /etc/modprobe.d/blacklist.conf fixed the problem completely.

---

### Post by Sven6210 on 2011-05-09
You can have a look on my how-to at [http://ubuntuforums.org/showthread.p...ghlight=RT3090]("http://ubuntuforums.org/showthread.php?t=1476007&highlight=RT3090")

It also works for the RaLink RT3090, you just need to replace the "[FONT=Verdana, sans-serif]RT2860" with "RT3090".

Disadvantage of this procedure:
[/FONT]
[LIST]
[*]You need to recompile the driver each time you make a  major kernel-update. The backports I have tried so far did not work very  well
[/LIST]
Advantage of this procedure:

[LIST]
[*]On my EeeBox B202 and my friends EeePC 1015 P it works very well and reliable
[/LIST]

The manual should also work for newer releases of Ubuntu, I am still running Ubuntu 10.04 LTS on my systems.

Good luck

Sven

---

