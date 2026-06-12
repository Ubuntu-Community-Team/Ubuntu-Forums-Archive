---
title: "BCM4306 wireless adapter  doesn't work in Ubuntu, Or Xubuntu"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by hansolo4949 on 2011-01-04
Hello, This is my first post on Ubuntu forums, and I am very happy to get involved. I recently installed Ubuntu 10.04 (and eventually upgraded to 10.10) on a 6+ year old Gateway Laptop. When I booted Ubuntu up after installing it, I was rather suprised to discover that the wireless card didn't work. After extensive research, and many hours of frustration, along with several useless "fixes" I have finally decided to post my own thread on this forum, in high hopes that I will get a solution to my problem. I am almost certain that the wireless card is a Broadcom BCM4306, but I am unable to determine what revision it is, if at all. I have (some) experience with the terminal, but nothing _extremely_ techy please, although I am a geek:D, I don't want to spend _ALL_ day fixing this, if I don't completely understand what you meant :). When I look at the network connections widget, it says that the wireless card is not ready, and iwconfig (I think) says that it's disabled. It's not a problem with the laptop itself, because I was able to get a Linksys usb wireless adapter to work just fine on it, although it was SLOW (about 90 kbs, yikes).

Please note that I am trying to fix this on a _FRESH_ installation of Xubuntu 10.04 (I ditched Ubuntu, it was a little too slow on that machine), with the default packages on it, nothing more.

Now, I was able to get the wireless working ONCE on ubuntu, using fwcutter I think, but it went away upon reboot.

 One last thing, I am running the 32 bit Xubuntu 10.04 on what I think is a 64 bit machine (I think it ran x64 Ubuntu 10.04 before I ditched it), so if you could tell me how to figure out if it is 64 bit, that would be very appreciated.


 Thanks for the help!

Hansolo4949


Update: I have figured out my problem, but I will keep this thread open to help all the other distressed 4306 card users. This is the link [to the thread where the problem was solved]("http://ubuntuforums.org/showthread.php?t=1660535")
          Please keep posting on this thread, to help other 4306 card users please :)

 hansolo4949

---

### Post by PatchesTheCaveman on 2011-01-04
If you can get a working wired Ethernet connection, do so and download the *rfkill* package.  On a terminal:
```
sudo apt-get install rfkill
```

Once you've done that, run it:
```
sudo rfkill list
```

Does your wireless adapter appear hard or soft-blocked?

If it's hard-blocked, flip the wireless switch on your laptop.  This might be a physical switch, a discrete button, or a Fn key combination.  Then check *rfkill list* again.

If it's soft-blocked, run this command to unblock it:
```
sudo rfkill unblock 0
```
Replace 0 with the number reported for your wireless adapter by *rfkill list* if it's different.

In addition, you might have got bit by a bad kernel update.  To see if this bug affects you and fix it, follow the instruction I provided on this post:
[http://ubuntuforums.org/showpost.php?p=10312711&postcount=5](http://ubuntuforums.org/showpost.php?p=10312711&postcount=5)

If that doesn't fix it, let us know.  Good luck!

---

### Post by hansolo4949 on 2011-01-04
Thank you for your rapid response! I did as you said, and rfkill said that my wireless adapter was not hard blocked, OR soft blocked. I downloaded it via the afore mentioned linksys usb adapter, which shows up a wlan 1. Does that affect anything during troubleshooting? if so, I can hook it up via ethernet.:) 

  I know this is a very common problem, and I hope that this can be solved. I think that if you can help me set it up with ndiwrapper (I know there are some lines of code I need to input, but i'm not familiar with them) that would be great!


Hoping for another rapid reply :)


 hansolo4949

---

### Post by hansolo4949 on 2011-01-05
Does anyone alse have a suggestion? :)

 hansolo4949

---

### Post by hansolo4949 on 2011-01-05
Just so that you know, I started a new thread, in hopes that I could find a linux distro that's compatible with the wireless card. I then was fortunate enought to correspond with someone, who fixed the problem for me. I am not going to mark this posting as solved, because I still want input, for other people who have to same problem.

Thank you for your cooperation :)

hansolo4949

---

### Post by Bucky Ball on 2011-01-05
Post a link to the thread that is 'solved' here and then mark this one as 'solved'. You might even edit the first post in this thread and include the link to the other thread there.

This will help people. ;)

---

### Post by hansolo4949 on 2011-01-05
Okay, I will. Thank you for the helpful suggestion! This is the link to the [solved thread]("http://ubuntuforums.org/showthread.php?t=1660535"), and I am going to edit posts accordingly. Please don't take this as a queue to stop osting suggestions, as this would be very apreciated to help the other 4306 adapter haters out there :D

hansolo4949

---

### Post by hansolo4949 on 2011-02-02
Bump, and I please do keep posting on this thread, perhaps about solutions that worked for you, because I know now how much of a pain Broadcomm bcm43xx wireless cards are.

Thank you!

---

### Post by Kegusa on 2011-02-03
Interesting read. I just installed 10.10 (64bit) on a desktop I have. Using BCM4306 v.3 I performed the usual steps on the BCM43xx wiki page. I have found the card and it can see the networks in the area but I cant connect for some reason! Did you have the same error? 

AP is a D-Link DWL b/g/n setup with visible SSID and WEP encryption. 

Dmesg Output: 
> [ nnnn.nnnnnn ] wlan0: direct probe to SSID MAC timed out 

lspci -vs 02.07.0 (the 4306 ver 3 card)

> Subsystem: Broadcom Corporation Device 0418
Flags: bus master, fast devsel, latency 43, IRQ 18
Memory at fddfc000 (32-bit, non-prefecthable) [size=8K]
Kernel driver in use: b43-pci-bridge
Kernel modules: ssb

Can you post your lspci -vs on the same card just to see if that might help?

---

### Post by hansolo4949 on 2011-02-03
No, I never got that error. It just connected. Are you SURE your encryption is WEP? because ours is wep (i really need to upgrade, it's just to big of a hassle, though), and I connected just fine. Did you follow the instructions I used, and did you read my comments? I was using 32-bit, so maybe that has something to do with it.....is this a fresh install you have, or an old one?

---

### Post by Kegusa on 2011-02-03
Its a new install and 64bit. I'm the one that set up that router and have too intimate knowledge of it ;) Another test router confirmed the fault.

I begin to believe that this is a problem outside of the usual errors with the card, since the guides havent helped so far :-/
Strange thing is that wicd gives the error that it could not authenticate where nm-applet just gives up.  I havent found a thread around that specifies the exact same problem I have, but similar threads are found scattered around different forums and they all have 64bit in common with different hardware. Almost thinking of reinstalling with the 32bit version.

Made a thread with more info here regarding my own problem: [http://ubuntuforums.org/showthread.php?t=1681029](http://ubuntuforums.org/showthread.php?t=1681029)

---

### Post by hansolo4949 on 2011-02-03
Hmm....isn't the problem with just about anything always out of the ordinary problems?;)


So, you're not able to connect at all? are you using fwcutter or the sat drivers? If some of your...hrm neighbors connections are unsecured, try connecting to them (as long as you aren't going to use it for nefarious doings;)) If it can connect to the unsecured wireless, then maybe it's a problem authenticating wep....

---

### Post by ELEE on 2011-02-23
I have the same on a Pavilion zv5000 (zv5466c)  
 and  BCM4306 802.11b/ge Wirless LAN Controller (rev 03)

from the other thread you posted I went to the the Community site

[COLOR=Red]Ubuntu Documentation > Community Documentation > WifiDocsDriverbcm43xx[/COLOR]

I then read through and eventually entered as suggested (as follows) and solved.:)

[COLOR=Blue]~$  sudo apt-get install b43-fwcutter

~$ sudo modprobe -r b43 ssb

~$ sudo modprobe b43
[/COLOR]

Thanks to all who give

Long live Linux.... may I grow wise before I die.

---

### Post by hansolo4949 on 2011-02-23
Congrats in your success! I hope this thread is as much help to other bcm43xx hatred as it was for you, and me!

---

