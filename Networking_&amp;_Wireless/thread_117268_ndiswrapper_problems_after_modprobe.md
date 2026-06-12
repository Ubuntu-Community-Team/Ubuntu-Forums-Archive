---
title: "ndiswrapper problems after modprobe"
date: 2006-01-14
forum: Networking &amp; Wireless
---

### Post by kasemodz on 2006-01-14
Alright, I'm trying to install my pci wireless card on my desktop. After I installed the necessary driver, I went and did modprobe ndiswrapper. Then I said ndiswrapper -m. It said
> Adding alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper

Then I went to iwconfig but it said
> lo      no wireless extensions
eht0      no wireless extensions
sit0       no wireless extensions

Then I did dmesg and it said in the end
> [4295681.891000] <3>ndiswrapper _wrapper_init:173): loadndiswrapper fialed (11); check system log for messages from 'loadndisdriver'

What should I do now?

---

### Post by kasemodz on 2006-01-14
Then I went to /var/log/syslog and here is the full log
Keep in mind to open this log in wordpad or word. Don't use notepad in windows.

---

### Post by healychan on 2006-01-14
Please post
more /etc/network/interfaces

and 

ls /etc/modprobe.d/

also

more /etc/modules

please

---

### Post by healychan on 2006-01-14
May I ask what PCI card you are using, are you sure you installed the correct driver with ndiswrapper ???

---

### Post by kasemodz on 2006-01-14
alright here is /etc/network/interfaces

There are a lot of sutff in modprobe.d.  One of them is ndiswrapper. I have attached that file as well.

However there is no /etc/modules/

I am using a realtek 8185 chipset pci card. It is a 54g pci card. I used the driver that they provided which was net8185.inf.

---

### Post by trubblemaker on 2006-01-14
Just a hunch run ```
demod -a
```, then try  ```
moprobe ndiswrapper
```

---

### Post by healychan on 2006-01-14
Because the information you provided are fragmented, let me just confirm the whole installation process with you step by step.

1. Identify the chipset id of your card. Model name is useless since same model may use different chipset.

2. Check to see if your card is supported by ndiswrapper, if yes, then find out which driver should you use.

3. When you install the driver, make sure the .sys and .inf files are in the same directory, because some driver need the sys and inf to work together.

4. Do "sudo ndiswrapper -m", "sudo modprobe ndiswrapper", also add the word "ndiswrapper" into the end of the /etc/modules file.

5. After that, do some checking such as "ndiswrapper -l", "more /etc/modprobe.d".....etc to confirm that the driver is being installed correctly.

Find out more no this wiki trouble shooting guide [https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29]("https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29")

---

### Post by trubblemaker on 2006-01-14
is your kernel Dapper or Breezy?

---

### Post by kasemodz on 2006-01-14
my kernel is 2.6.12-9-386, I don't know what name that is. I think its breezy.
Healychan- the chipset is rtl8185. The sourceforge rtl8180 project supports this card. Many people have been able to use this card via ndiswrapper. I have installed ndiswrapper many times. I have checked and seen that the modules were in modprobe.d

---

### Post by trubblemaker on 2006-01-14
first 
```
cp "/etc/network/interfaces" "/etc/network/interfaces.old"
```
then edit "/etc/network/interfaces"
remove any devices that you don't see when you do ifconfig and 
DO NOT remove anything to do with "lo" or "eth0" they are supposed to be there, we're more looking for eth1 entries...(if you tried to install the driver natively b4 ndiswrapper there may be some garbage in there.) post it if you don't want to guess, but if something does go wrong, then you have a back up  and just "restore" it.

---

### Post by blu.gecko on 2006-01-14
just asking but I know you said you did " sudo modprobe ndiswrapper"
but did you sudo ndiswrapper -m and then activate the wlan0 ?

I could never get mine to work right until I did it in that order.....

If its a onboard laptop wifi card, get away from ndiswrapper, lookup wireless chipsets, I know ubuntu has the cisco drivers, I had 5.10 on a IBM t40, working great...that chipset is like 20 dollars...I think malabs.com carries it

---

### Post by healychan on 2006-01-14
[QUOTE=kasemodz]my kernel is 2.6.12-9-386, I don't know what name that is. I think its breezy.
Healychan- the chipset is rtl8185. The sourceforge rtl8180 project supports this card. Many people have been able to use this card via ndiswrapper. I have installed ndiswrapper many times. I have checked and seen that the modules were in modprobe.d[/QUOTE]

Do```
ndiswrapper -l
```if you are able to see the phrase [COLOR="Red"]"hardware present"[/COLOR], add following lines to the end of /etc/network/interfaces file.

```
iface wlan0 inet dhcp
auto wlan0
```and remove```
auto eth0
```then restart the computer.

---

### Post by healychan on 2006-01-14
May be you can read this thread to find some hint.

[http://www.ubuntuforums.org/showthread.php?t=117013]("http://www.ubuntuforums.org/showthread.php?t=117013")

---

### Post by Jeezis on 2006-01-15
i'm having similar problems. i am attempting to set up an inprocomm minipci wireless card. i got the .sys and .inf files and ndiswrapper seems to have worked perfectly. when i run ndiswrapper -l it says "driver detected, hardware detected". the problem is when i run "modprobe ndiswrapper" it says the module is not found. i've checked in /etc/modprobe.d and there is an ndiswrapper file. in /lib/modules/2.6.12-9-386 there is a module.ndiswrapper file. deeper in the /lib/modules/ file structure i found several ndiswrapper folders but they are empty. 

in the /etc/ndiswrapper folder there are several .conf files and the .inf and .sys files. it seems like everything is where it's supposed to be except there is no ndiswrapper.ko or neti2220.ko file for modprobe to load.

i'm dualbooting with windoze at the moment, so it's a bit difficult to try and find a solution and work on the problem on the same machine but i'll see what i can do :-p

thanks for your time and i look forward to any help you can offer

---

### Post by healychan on 2006-01-15
[QUOTE=Jeezis]the problem is when i run "modprobe ndiswrapper" it says the module is not found.[/QUOTE]
What about "iwconfig", can you see your interface ???

I am not sure adding a "sudo" before "modprobe ndiswrapper" will help or not, but I suggest you do "sudo modprobe ndiswrapper" first. You should see something like "Adding alias wlan0........"

---

### Post by Jeezis on 2006-01-15
iwconfig does not see the interface and sudo modprobe ndiswrapper gave me the same output. it is quite confusing to me

-EDIT-

when i run ndiswrapper -m it says the alias has already been added. then "sudo modprobe ndiswrapper" says "module ndiswrapper not found" or something like that.

---

### Post by kasemodz on 2006-01-15
alright guys i installed linus driver 2.6.12-10-k7 and then I was able to successfully install it. Modprobe ndiswrapper went fine. I went to /lib/modules/kernel-2.6.12.10-k7/driver/net/ndiswrapper and ndiswrapper.ko was there. However, when I did dmesg in the end it said no ip-v6 routers found for eth0. Then I added ndiswrapper to /etc/modules and rebooted. Well it hanged on loading modules. I rebooted and used another linux distro and deleted ndiswrapper from modules file. Then I went back to booting and it said > the file system is not clean. Reiserfs. trans...blah blah I waited for 10 minutes nothing happened so I'm reinstalling ubuntu. Ah guys, I don't know if this happens to you'll but in linux I'm jinxed or something. Whenever I'm close to fixing something, something else pops up.

---

### Post by Jeezis on 2006-01-15
i believe my problem is with ndiswrapper, it seems to have created all the files needed except the actual module. one thing that i just remembered is this: i installed kubuntu fresh and didn't configure then network because i only have wireless. i don't know but could this be causing some of the problems?

i also tried downloading the most recent stable release of ndiswrapper but it failed to compile. i think that if i had wired internet access in order to experiment this would be much easier but that isn't an option at the moment .](*,)

thanks for your guys patience and help, i hope i can get this figured out soon, kubuntu 5.10 is so awesome and i can't wait to see all it can do!

---

### Post by kasemodz on 2006-01-15
alright everyone, I got my wireless card workingish. The good news is linux identifies the wireless device. I can go to administration---networking and wireless is there. Bad news is that somehow I can't sync with the router. But thanks everyone. I installed a fresh version of ubuntu, then I upgraded my linux kernel from 2.6.12-9-386 to 2.6.12-10-k7 since i have an athlon processor. After that I didn't go with the latest build but went with 1.1. I got ndiswrapper-utils 1.1 from synaptic, installed it and bam. I'm happy now, finally I'm making some progress.

---

### Post by healychan on 2006-01-16
If you are able to see your interface from "iwconfig". You are very close.:p 

Welcome to post again if you have problems accessing the Internet.

---

### Post by kasemodz on 2006-01-16
well healychan, bad news, I cannot for some reason get the ip fro my router. I don't have encrytption. My wireless card can scan the access points just not join em for some reason. I can force the wireles card to join an ssid but I don't get any ip. When i dhclient wlan0, it tries to get ip but it just can't. In dmesg, it says no ipv6 routers found. I don't know but that could be the problem. Anybody know how to disable that?

---

### Post by Jeezis on 2006-01-16
anyone have any blinding flashes of brilliance for my ndiswrapper problem? does kubuntu have a working version of ndiswrapper or just ndiswrapper-utils?

---

### Post by healychan on 2006-01-17
[QUOTE=kasemodz]well healychan, bad news, I cannot for some reason get the ip fro my router. I don't have encrytption. My wireless card can scan the access points just not join em for some reason. I can force the wireles card to join an ssid but I don't get any ip. When i dhclient wlan0, it tries to get ip but it just can't. In dmesg, it says no ipv6 routers found. I don't know but that could be the problem. Anybody know how to disable that?[/QUOTE]
If you can see your wireless interface via "iwconfig", you can try```
sudo iwconfig wlan0 essid "xxx"
sudo ifup wlan0
```
this should brings your interface up and gain an IP from your DHCP server.

Since your adapter can scan the access point, it should be working properly.

---

