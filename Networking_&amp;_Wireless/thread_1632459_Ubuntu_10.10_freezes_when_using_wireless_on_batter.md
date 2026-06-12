---
title: "Ubuntu 10.10 freezes when using wireless on battery"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by tiredofguessingusernames on 2010-11-28
Hi All

Unlike a lot of others, I have had no problems getting the wireless on my Dell Studio 1558 working with the STA driver. As long, as I am not on battery, that is. Within minutes of switching to battery and disconnecting from the LAN, my system freezes: I cannot move the mouse, the keyboard is useless (I can't even Ctrl-Alt to a terminal) and my only option is a hard boot.

I currently have the 2.6.35-23 kernel and I have tried the following driver options for the wireless (all the below were tried with 2.6.35-22):

- the Broadcom STA driver in the repos
- the latest STA dirver from Broadcom
- the new broadcom driver, not yet available in ubuntu repos (brcm80211)
- ndiswrapper ( I can only get win 7 drivers for my laptop, so this does not even enable the driver)

My Wifi card uses the BCM43224 chipset.

After a freeze, I have pored over the logs and I cannot find any obvious error messages preceding the event - so I am a little at wit's end ito resolving this. Can anybody give me any clues as to where I should start looking to resolve this issue?

---

### Post by grahammechanical on 2010-11-29
Are you switching to battery without shutting down? What do you mean by "disconnecting from the LAN?" Are you physically changing the configuration of the system without warning the OS first? 

Things freeze, as you put it, when the OS gets locked into repeat operations that use up all the processing power and/or memory. The OS is trying to accomplish a more important task than re-drawing the screen to reflect mouse movements or key presses.

Regards.

---

### Post by tiredofguessingusernames on 2010-11-29
So - the steps are more or less like this:

1) I am at my desk, I have both a wifi connection the network as well as a Wifi connection.
2) I unplug the AC power lead (so the laptop is now running off battery) and I disconnect the Ethernet cable so that I only have the Wifi connection. In other words, I am using the laptop pretty much the way it was intended.
3) Within a few minutes, the laptop freezes and does not accept input from keyboard or mouse.

Given that I have a Core i5, and that this happens repeatedly regardless of how many windows I have open or what tasks I perform, I would really like to know what the OS thinks is so important - so that I can correct it!

I am not sure exactly how I am supposed to warn the OS that I am going to move the laptop (it freezes whether I physically move the laptop or not) - but I have two other laptops both running Ubuntu, that handle the same behaviour just fine.

---

### Post by jagadish7 on 2010-11-30
I have a similar issue with my Ubuntu 10.10 running on MacBook. I have no issues what so ever running 10.04 with the older version of the kernel(now i have 2.6.35-23).

Issue details:
The system freezes and goes to a blank screen when i remove the power and the laptop turns to Battery power. All i can do is do a force restart. I could find no information about the crash in the log files and have no clue on how to fix the issue.


Jax

---

### Post by cdillard-hsp on 2010-12-01
Same problem here.  It's random though and not easily duplicated (i.e. doesn't happen every time I go from power plugged in to unplugged and running on battery).  I have an HP Elitebook 8530w with an Intel wireless card, Ubuntu 10.10 x86_64 with the 2.6.35-23 kernel and this notebook has an Nvidia Quadro FX card.

This morning I repeatedly unplugged and plugged in the power supply with no freeze.  I do see that EXT-4 is re-mounted ro in /var/log/messages every time power is swapped and though this might be normal, it could be a clue.

---

### Post by tiredofguessingusernames on 2010-12-02
Hi

I found this post that contained the solution to my problem: 
[http://ubuntuforums.org/showpost.php?p=10185265&postcount=12](http://ubuntuforums.org/showpost.php?p=10185265&postcount=12) 

Since rolling back to an older version of pmi-utils, I have had no problems with battery power at all!

I have marked the thread as solved - jagadish, cdillard - hope the above link helps you guys out as well!

---

### Post by AgentZ86 on 2010-12-02
I also suspect something in the power management.

Let me as when you turn on the computer on battery power first then plugin the power does this create the same symptom ? 

And then unplugging it again after being first booted to battery power only.

Does this create the same symptom again ?

Perhaps turn off power management features first in ubuntu and see if this has any effect.

And try turning off power management features in the bios to see if this has any effect.

See if doing any of this can pinpoint which power management setting may be the problem.

I don't know if any of this will help, but worth a try.

---

### Post by david111 on 2010-12-07
i have a problem as well. only when i unplug my cord the screen freezes and the caps lock light on the keyboard blinks. i have a toshiba satalite l505d-s5983

---

### Post by cdillard-hsp on 2010-12-07
I went through the process of downgrading pm-utils as one poster suggested but this had no effect.  I still suffer from the freeze.  I've just added acpi=off in the kernel options but this is not a good long-term solution and I've not played with the power yet to see if it will still freeze up on me.

Sure do wish Ubuntu folks would fix this.

I've submitted a bug on this so please do go and add your comments so that this gets some attention.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/684164](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/684164)

Thanks,
Clay

---

### Post by david111 on 2010-12-07
thanks for your help. ubuntu needs to fix this, i know its ubuntu because i installed fedora 14 and tested the unplug and stand by and it worked flawlessly but i couldnt get the wifi working so i switched back to ubuntu

---

### Post by choongii on 2010-12-29
Try `touch /etc/pm/power.d/wireless`. This will prevent pm-powersave from putting your wlan0 card into powersaving mode when running on battery power. Solved the issue for me.

---

### Post by psychydyl on 2010-12-30
> **choongii said:**
> Try `touch /etc/pm/power.d/wireless`. This will prevent pm-powersave from putting your wlan0 card into powersaving mode when running on battery power. Solved the issue for me.

It worked for 30 mins, then back to freezing it went!

---

### Post by PatchesTheCaveman on 2010-12-30
Try
```
sudo iwconfig wlan0 power off
```

Replace wlan0 with your wireless interface if it's different. Run *sudo iwconfig* to check.

If that fixes your problem, make the change permanent by running:
```
sudo bash -c "echo iwconfig wlan0 power off >> /etc/rc.local"
```

Again, replace wlan0 with your wireless network interface if its different.

---

### Post by spantch101 on 2011-01-05
this worked for me on asus k50id 
"aspera wrote on 2010-11-26: 	#37

I'm sorry, but I was a little bit to fast. After I attached Linux Mint Julia to wlan and USB-Memory, it crashed after the Filetransfer began immediately also.

But I found finally a workaround, which I have tested the last 2 days:

I deinstalled the pm-utils 1.4 with synaptic. Download the package pm-utils 1.3.0-1ubuntu1_all_deb from

"http://packages.ubuntu.com/de/lucid/all/pm-utils/download"

and installed it.

Now it workes fine and all functions remain in the best way.

In my opinion the error lies in the current pm-utils package. But I am only a completely normal user and not a programmer!

Would anybody test it too and write a coment?

Thanks

aspera
"

---

### Post by springnuts on 2011-01-07
> **PatchesTheCaveman said:**
> Try
```
sudo iwconfig wlan0 power off
```


Thanks Patches - that works for me as a one off, however after applying the  

> **PatchesTheCaveman said:**
> sudo bash -c "echo iwconfig wlan0 power off >> /etc/rc.local"

command the crash still happened when starting wireless.  I checked the file "rc.local": it now had the text "iwconfig wlan0 power off" as its final element after the line "exit 0".  Should this have been "sudo iwconfig ..." ?

Have restored rc.local and will use the one off solution until new pm utils comes out I think.

Problem happened on an Advent 7211.

Springnuts

---

### Post by PatchesTheCaveman on 2011-01-07
You need to put that line before the *exit 0* line.  Sorry, I forgot they had that in there.

*sudo* is not necessary because startup scripts are executed with root privileges.

---

### Post by Morgoth1299 on 2011-01-10
> **jagadish7 said:**
> I have a similar issue with my Ubuntu 10.10 running on MacBook. I have no issues what so ever running 10.04 with the older version of the kernel(now i have 2.6.35-23).

Issue details:
The system freezes and goes to a blank screen when i remove the power and the laptop turns to Battery power. All i can do is do a force restart. I could find no information about the crash in the log files and have no clue on how to fix the issue.


Jax
  

I have almost the same problem!  As well as some others w/Ubuntu 10.10.  I would be happy to switch back to an older kernal if I could, I have seen that that fixed a lot of peoples problems, eg unable to reume after sleep and freezing up.  Could someone help?

---

### Post by Morgoth1299 on 2011-01-10
> **david111 said:**
> i have a problem as well. only when i unplug my cord the screen freezes and the caps lock light on the keyboard blinks. i have a toshiba satalite l505d-s5983


Exact same thing happens to me!!!  Toshiba T115D-S1125 4G RAM 

Help anyone?

---

### Post by zeating on 2011-01-22
> **spantch101 said:**
> this worked for me on asus k50id 
"aspera wrote on 2010-11-26: 	#37

I'm sorry, but I was a little bit to fast. After I attached Linux Mint Julia to wlan and USB-Memory, it crashed after the Filetransfer began immediately also.

But I found finally a workaround, which I have tested the last 2 days:

I deinstalled the pm-utils 1.4 with synaptic. Download the package pm-utils 1.3.0-1ubuntu1_all_deb from

"http://packages.ubuntu.com/de/lucid/all/pm-utils/download"

and installed it.

Now it workes fine and all functions remain in the best way.

In my opinion the error lies in the current pm-utils package. But I am only a completely normal user and not a programmer!

Would anybody test it too and write a coment?

Thanks

aspera
"
worked for me, same model K50ID thanks!!!

---

### Post by bongey on 2011-03-06
There is an on going bug report for this problem [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656745](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656745)  , seems one kernel module is acting up.

---

### Post by carlp101 on 2011-08-23
Hi,

I have been having problems with my Dell Studio 15 freezing intermittently when on battery for months. I have read many, many posts on this topic and tried many different tweaks to no avail. Reverting to an earlier version of pm_utils worked, but I lost the ability to put my laptop on standby, so that was no good. I decided it was time for me to do some analysis and try a few tweaks of my own. Well, it looks like I have come up with a successful work around that should work for any type of wireless card.

I run Mint 10 and have the latest version of pm-utils installed - 1.4.1. tailing /var/log/pm-powersave.log reveals that /usr/lib/pm-utils/power.d/wireless is called to put the wireless card into powersave mode when the power cord is removed. I found the specific section of code that makes that change is at the end of the script:

case $1 in
    true) wireless_powersave on;;
    false) wireless_powersave off ;;
    *) exit $NA ;;
esac

I simply changed it to:

case $1 in
    true) wireless_powersave off;;
    false) wireless_powersave off ;;
    *) exit $NA ;;
esac

This results in the card never being put into powersave mode and has stopped the freezing. This change does not appear to affect the power consumption either. So, all is well and I have said goodbye a very frustrating problem. I hope it works for you too.

FYI, my wireless card is a Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

---

### Post by batman01 on 2011-09-27
In case this didn't work for others as it didn't form me, I found that I had to comment out the whole section -

#case $1 in
#true) wireless_powersave off;;
#false) wireless_powersave off ;;
#*) exit $NA ;;
#esac

I can only assume that its the setting the powersave mode at all that is the issue, not just turning it on.

My Dell Studio works fine now.

---

### Post by Bill Gates Foundation on 2012-03-07
toshiba tecra a-9
nvidia 300 on xserver (nvidia never works right)
12.04

  removed nouveau firmware in syn app and now switching power sources works great:P

---

