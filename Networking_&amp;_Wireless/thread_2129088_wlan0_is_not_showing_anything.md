---
title: "wlan0 is not showing anything"
date: 2013-03-25
forum: Networking &amp; Wireless
---

### Post by markackerman8@gmail.com on 2013-03-25
Howdy

This is the last thing before i give this laptop back to a disgruntled windows user - and convert her to >>>Kubuntu - YEAH:popcorn:

The wireless doesn't show any SSID's - please help - 10 hours or more have found nothing - here is some info that I hope will help

lspci
&#8728; 03:00.0 Network controller: Intel Corporation Centrino Wireless-N 105 (rev c4)
&#8728; 02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)

chris@chris-Aspire-E1-531:~$ • sudo lshw -C network; sudo iwlist scan | grep 20; rfkill list
•: command not found
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

0: acer-wireless: Wireless LAN
        Soft blocked: no
        Hard blocked: no

chris@chris-Aspire-E1-531:~$ ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device


chris@chris-Aspire-E1-531:~$ lspci -nnk | grep -iA2 net 
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
        Subsystem: Acer Incorporated [ALI] Device [1025:0647]
        Kernel driver in use: tg3
--
02:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
        Subsystem: Acer Incorporated [ALI] Device [1025:0647]
        Kernel driver in use: sdhci-pci
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 105 [8086:0894] (rev c4)
        Subsystem: Intel Corporation Centrino Wireless-N 105 BGN [8086:0022]


Please >HELP a newbie ubuntuers computer

Thanks, and <>i will sure promptly answere any questions asked - <>Cheers, Mark;)

---

### Post by chili555 on 2013-03-25
>  Intel Corporation Centrino Wireless-N 105 [8086:0894]This is a relatively new device that isn't supported in older Ubuntu versions. So what version did you install?```
lsb_release -d
```

---

### Post by markackerman8@gmail.com on 2013-03-25
Thanks for the quick response,

as you asked .....
chris@chris-Aspire-E1-531:~$ lsb_release -d
Description:    Ubuntu 12.04.2 LTS

Acer E1-531-4806

Do you think an upgrade to 12.10 would solve it, and by the way it is Kubuntu though that shouldn't make a difference,

Thanks again, Mark
p.s. Upgrading to 12.10 aas we speak - do you think the newer kernel in 12.10 might make it functional ? and shoud I try to go to 13.10 if that doesn't work (though she is completely new to >>Ubuntu or <linux so <i wouold rather not)

---

### Post by chili555 on 2013-03-25
> do you think the newer kernel in 12.10 might make it functional ? Absolutely. Post back if not, but I'm very confident it will.

Reference:```
 modinfo iwlwifi | grep 0894
alias:          pci:v0000[COLOR="#FF0000"]8086[/COLOR]d0000[COLOR="#FF0000"]0894[/COLOR]sv*sd00000822bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i*
```

---

### Post by markackerman8@gmail.com on 2013-03-25
Chili,
Thanks for oyour encouragement, wow.  I should use these forums more often - with brains like you around.  Your quick responses are SOOOO appreciated.

Cheers Mark
p.s. I will of course update you with my progress
and could you explain what these lines mean, and if I should be typing some command in terminal?  I did the command in my working laptop and got the exact same result as you posted

 modinfo iwlwifi | grep 0894
alias:          pci:v00008086d00000894sv*sd00000822bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i*

on the disfuncional laptop in question - here is the terminaL RESPONSE
chris@chris-Aspire-E1-531:~/Documents$ modinfo iwlwifi | grep 0894
alias:          pci:v00008086d00000894sv*sd00000822bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000426bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000026bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i*

p.s.s   No luck after upgradiong to 12.10 and kernel 3.5...,
$ sudo ifconfig wlan0 up
[sudo] password for chris: 
wlan0: ERROR while getting interface flags: No such device

any simple troubleshooting steps you can suggest, as it seems it shouold be supported .... on [http://wireless.kernel.org/en/users/Drivers/iwlwifi](http://wireless.kernel.org/en/users/Drivers/iwlwifi), it specifically says it'ssupported since kernel 3.2 which I had already had with 12.04 now 3.6  ....hmmmmmm perhaps a firmware download or something ???????????????? at a loss - thanbs in advance,

Mark

---

### Post by markackerman8@gmail.com on 2013-03-26
please help

---

### Post by chili555 on 2013-03-26
> on the disfuncional laptop in question - here is the terminaL RESPONSE
chris@chris-Aspire-E1-531:~/Documents$ modinfo iwlwifi | grep 0894
alias: pci:v00008086d00000894sv*sd00000822bc*sc*i*
alias: pci:v00008086d00000894sv*sd00000426bc*sc*i*
alias: pci:v00008086d00000894sv*sd00000026bc*sc*i*
alias: pci:v00008086d00000894sv*sd00000422bc*sc*i*
alias: pci:v0000[COLOR="#FF0000"]8086[/COLOR]d0000[COLOR="#FF0000"]0894[/COLOR]sv*sd0000[COLOR="#FF0000"]0022[/COLOR]bc*sc*i*This means the module, aka driver, iwlwifi covers your device and is intended to work. > 03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 105 [[COLOR="#FF0000"]8086:0894[/COLOR]] (rev c4)
Subsystem: Intel Corporation Centrino Wireless-N 105 BGN [8086:[COLOR="#FF0000"]0022[/COLOR]]
If it isn't working as expected,something else is wrong. Is the module loaded?```
lsmod | grep iwl
```If not, load it and see if there are errors or warnings that point to a problem:```
sudo modprobe iwlwifi
```If it is loaded, check the message log for, again, errors or warnings:```
dmesg | grep iwl
```Last, and I include this simply for completeness, is the wireless switch on?```
rfkill list all
```

---

### Post by markackerman8@gmail.com on 2013-03-26
Chili,  sudo modprobe iwlwifi -            WORKED !           AWESOME  Chili, thanks so much
now # lsmod | grep iwl, shows

iwlwifi               386799  0 
mac80211              540032  2 iwlwifi,b43
cfg80211              206797  3 iwlwifi,b43,mac80211

and now I see the wireless networks - fantastic

I hope it works after a reboot as she (chris) is a newbie and older too so wouldn't likely want to use terminal to load it.  I wil assume it will load - and will post this right now, as I am soooo hapy for your help.  

Was "sudo modprobe iwlwifi", all I ever needed or was it the firmware I manually updated thwt did the trick?

I would hate to have gone through all of this without learning what was wrong.  And btw, is iwlwifi a new term or one that is just new to me?

thanks so much again, Chil,

Sincerely, Mark

Edit*
Ok so now it doesn't load at startup as I suspected though manually loading it as you instructed still works.  Before I edited this I thought i WOUOD GOOLGLE THE NEW PROBLEM AND MY FIRST HIT WAS A SOLVED POST THAT YOU (Chili) Solved - you are Awesome - Helping everyone.  So I though since I am with the master I would wait for your response to auto module loading - Thanks again Chili !

---

### Post by chili555 on 2013-03-26
It was probably modprobe. For some reason, unknown to me, occasionally a module fails to load once in a while. If you want it to load automagically, no matter the weather or phase of the moon, add it to /etc/modules:```
sudo su
echo iwlwifi >> /etc/modules
exit
```You should be all set, but if not, feel free to post back.

The firmware was in the default install all along but that's one of the first things people try when their wireless is not working as expected. However, generally with Intel cards, if it's not working, there is something simple and other than firmware at fault.> iwlwifi 386799 0
mac80211 540032 2 iwlwifi,b43
cfg80211 206797 3 iwlwifi,b43,mac80211
What?? Why is b43 in there? You don't have a Broadcom, do you?

---

### Post by markackerman8@gmail.com on 2013-03-26
Chili,

In my initial scrambling to get this done I had looked at the hardware and wasn't certain if it was broadcom or intel (broadcom is for the lan on her computer) and their was some lspci entry that showed a ?subsystem? of the intel 03:00 intel ... was broadcom.  I then added it to /etc/modules (b43) probably unnecessarily in my scrambling to find a solution.  I hope that helps you understand.  I just deleted it from /etc/modules and everything is working perfectly still.  P.s.  I googled the problem of autoloading while I was waiting for your responce and there was a post from 2008 with a solution that you helped someone with.  You are popping up everywhere -  helping the whole world, HAHA.  Could I by chance get yor email address - as you are a wealth of insight and so helpful.  Mine is 
[email]markackerman8@gmail.com[/email]

If not I understand - thanks again:popcorn:

Sincerely, Mark

---

### Post by markackerman8@gmail.com on 2013-03-26
------------------
                            Chili555   ROCKS ! ---------------------

---

### Post by chili555 on 2013-03-26
>  everything is working perfectly still. Awesome! Glad it's working.

---

