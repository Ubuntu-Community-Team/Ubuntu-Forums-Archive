---
title: "[SOLVED] Trying to install ndiswrapper...What am I doing wrong?"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by mariane_08 on 2009-01-02
System>Administration>Hardware did not detect my Wifi (it did before so I dont know why not now but....!) Anyway its the infamous BC4318 card.

So I'm trying the ndiswrapper rout in Terminal and following the guide
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

In step 1 I'm getting the error about not finding it:
[B][COLOR=Black]
[/COLOR][COLOR=Black]mbdb@M2000:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-utils-1.9
mbdb@M2000:~$

[/COLOR][/B][COLOR=Black]Can someone tell me what I'm doing wrong here?

Thanks!
[/COLOR]

---

### Post by timcredible on 2009-01-02
to install ndiswrapper, go to system->administration->synaptic package manager and install ndisgtk.  after that, you'll have a new menu option of system->administration->windows wireless drivers.  you just point to the correct .inf file for your wireless card and reboot, done.

---

### Post by mariane_08 on 2009-01-02
> **timcredible said:**
> to install ndiswrapper, go to system->administration->synaptic package manager and install ndisgtk.  after that, you'll have a new menu option of system->administration->windows wireless drivers.  you just point to the correct .inf file for your wireless card and reboot, done.

uhm...?? where is ndisgtk? I cant see it in there anywhere!
I'm running Hardy BTW
Thanks

---

### Post by spcwingo on 2009-01-02
It's under the networking category...or you could just enter ndisgtk with the search function.

---

### Post by Ayuthia on 2009-01-02
If you don't have a working internet connection, you will need to use your liveCD to add the packages:
```
sudo apt-cdrom add
```Add the CD when asked then:
```
sudo apt-get update
sudo apt-get install ndiswraper-utils-1.9
```I think that ndisgtk is also on the CD too.

---

### Post by mariane_08 on 2009-01-02
> **spcwingo said:**
> It's under the networking category...or you could just enter ndisgtk with the search function.

Hmmm....strange? it's definately not there! I looked under "ALL" and scrolled down the list and tried search too. Could this be why I got the error in Terminal?

mbdb@M2000:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ndiswrapper-utils-1.9
mbdb@M2000:~$

In which case is there another way I can get fwcutter or ndiswrapper?

---

### Post by mariane_08 on 2009-01-02
> **Ayuthia said:**
> If you don't have a working internet connection, you will need to use your liveCD to add the packages:
```
sudo apt-cdrom add
```Add the CD when asked then:
```
sudo apt-get update
sudo apt-get install ndiswraper-utils-1.9
```I think that ndisgtk is also on the CD too.

OK Thanks! I do have a working wired connection right now as well as the CD. I'll try that. Actually since I have the ethernet cable hooked up right now that might be the best way to go

---

### Post by mariane_08 on 2009-01-02
> **Ayuthia said:**
> If you don't have a working internet connection, you will need to use your liveCD to add the packages:
```
sudo apt-cdrom add
```Add the CD when asked then:
```
sudo apt-get update
sudo apt-get install ndiswraper-utils-1.9
```I think that ndisgtk is also on the CD too.

OK that was sucessfull! :D

Maybe you could explain this to me? I installed ndiswrapper off the liveCD as you sugested. Then I rebooted. After that just out of curiousity I went to system>administration>hardwaredrivers and it had detected my bc4318 wireless card (it had not before) I clicked on enable and installed  B43 FWcuter just like that. Now the works fine. Was ndiswrapper necessary in order for it to detect my wireless card?

Thanks for your help

---

### Post by Ayuthia on 2009-01-02
> **mariane_08 said:**
> OK that was sucessfull! :D

Maybe you could explain this to me? I installed ndiswrapper off the liveCD as you sugested. Then I rebooted. After that just out of curiousity I went to system>administration>hardwaredrivers and it had detected my bc4318 wireless card (it had not before) I clicked on enable and installed  B43 FWcuter just like that. Now the works fine. Was ndiswrapper necessary in order for it to detect my wireless card?

Thanks for your help

I am not for sure if that is what fixed it, but there is a bug with Hardware Drivers where it will not initally identify your wireless card.

---

