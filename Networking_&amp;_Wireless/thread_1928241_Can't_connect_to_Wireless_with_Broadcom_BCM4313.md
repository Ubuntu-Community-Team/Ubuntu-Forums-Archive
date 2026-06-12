---
title: "Can't connect to Wireless with Broadcom BCM4313"
date: 2012-02-19
forum: Networking &amp; Wireless
---

### Post by somaidra on 2012-02-19
I've looked through quite a few topics on this subject, but haven't exactly been able to fix my problem at all.  The drivers it gives me to download from Additional Drivers certainly doesn't work.

Yesterday, though, it seemed to magically work for a while, actually.  Then I had to close my laptop and go somewhere else.  It seems the magic went away and I can't connect again.

I tried a fresh install and it still doesn't seem to work... Tried quite a few other solutions that I read about, but they don't seem to work.

Using 11.10 Ubuntu.

---

### Post by gordintoronto on 2012-02-19
Did you read this:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_STA_drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_STA_drivers)

---

### Post by bkratz on 2012-02-20
> **somaidra said:**
> I've looked through quite a few topics on this subject, but haven't exactly been able to fix my problem at all.  The drivers it gives me to download from Additional Drivers certainly doesn't work.

Yesterday, though, it seemed to magically work for a while, actually.  Then I had to close my laptop and go somewhere else.  It seems the magic went away and I can't connect again.

I tried a fresh install and it still doesn't seem to work... Tried quite a few other solutions that I read about, but they don't seem to work.

Using 11.10 Ubuntu.

The following commands (one at a time should take care of you)

```
sudo apt-get install --reinstall bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf

```

The first makes sure that the sta driver is in place, the second and third blacklist the two drivers brcmsmac and bcma which clash with the correct sta driver. Copy/paste or make sure your typing is correct!

---

### Post by rilomuse on 2012-02-20
> **bkratz said:**
> The following commands (one at a time should take care of you)

```
sudo apt-get install --reinstall bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf

```

The first makes sure that the sta driver is in place, the second and third blacklist the two drivers brcmsmac and bcma which clash with the correct sta driver. Copy/paste or make sure your typing is correct!

Sorry, that didn't work. :( Maybe I'll try it with a fresh install.

(yes, this is a different account, I couldn't remember the password for this one earlier, so I just made a different account... Remembered it now!)

---

### Post by Bucky Ball on 2012-02-20
I wouldn't bother with a fresh install just yet. Keep digging on this problem. If it's not working now, it is 11.10 and your card (you have already re-installed and it achieved nothing). ;)

---

### Post by rilomuse on 2012-02-20
o_o I downloaded wicd network manager and I can connect through that, but not through the default network manager.

Don't understand.  Thanks, guys. :D

---

### Post by bkratz on 2012-02-20
> **rilomuse said:**
> o_o I downloaded wicd network manager and I can connect through that, but not through the default network manager.

Don't understand.  Thanks, guys. :D


Forgot to mention that a reboot would be necessary to blacklist the competing files, perhaps you did that when you installed wicd??

---

### Post by pmheideman on 2012-04-17
bkratz, your solution completely fixed my issue with the BCM4313 on my HP dm1z.  Thanks!

---

### Post by bkratz on 2012-04-17
> **pmheideman said:**
> bkratz, your solution completely fixed my issue with the BCM4313 on my HP dm1z.  Thanks!



Sure glad you got it working--congratulations!

---

### Post by llenchikk on 2012-04-27
bkratz, you resolve my issue with new notebook!
Your qick steps are awesome!
Do you know is there bug report on launchpad about it?
It is still present on fresh 12.04.

---

### Post by bkratz on 2012-04-27
> **llenchikk said:**
> bkratz, you resolve my issue with new notebook!
Your qick steps are awesome!
Do you know is there bug report on launchpad about it?
It is still present on fresh 12.04.



Glad you got it going!! Enjoy. Unfortunately I do not know it there is a current bug or not, will look and see if I can find anything.

---

### Post by Roasted on 2012-05-14
Didn't have any luck here... rebooted several times after running the commands individually. Fresh install of Ubuntu 12.04 64 bit on Dell Inspiron 1501 with Broadcom BCM4311. I ended up replacing the card with an Intel Wifi Link 1000.

---

### Post by Rambo Tribble on 2012-05-17
I have a similar problem with an HP laptop using a BCM4318 adapter. Unfortunately, the steps listed here have had no effect. The adapter had been working fine since 8.04, including 11.10. Dmesg shows no errors and lshw shows the Broadcom adapter, but Network Manager or System Settings do not. Any ideas?

---

### Post by bkratz on 2012-05-17
> **Rambo Tribble said:**
> I have a similar problem with an HP laptop using a BCM4318 adapter. Unfortunately, the steps listed here have had no effect. The adapter had been working fine since 8.04, including 11.10. Dmesg shows no errors and lshw shows the Broadcom adapter, but Network Manager or System Settings do not. Any ideas?



this thread was actually about the BCM4313 , the Bcm4318 typically uses the b43 driver. Take a look at this

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)

---

### Post by Rambo Tribble on 2012-05-17
Thanks for pointing that out. It appears that blacklisting those two conflicting drivers was all I needed, as I had already installed the b43 drivers. After purging the sta stuff and doing a precautionary reinstall of the b43, everything is working.

---

### Post by bkratz on 2012-05-18
> **Rambo Tribble said:**
> Thanks for pointing that out. It appears that blacklisting those two conflicting drivers was all I needed, as I had already installed the b43 drivers. After purging the sta stuff and doing a precautionary reinstall of the b43, everything is working.


Did you look at lsmod to see if those drivers were even loaded before blacklisting? Probably purging the sta stuff was what actually fixed your problems.  Anyway, congratulations on getting it working.

---

### Post by Rambo Tribble on 2012-05-18
Admittedly, I did not check lsmod, but the problem with wifi existed from installation, (actually, installation failed until I could get an Ethernet connection), long before the sta drivers were installed and despite the earlier installation of the b43 drivers. The difference in configuration before and after the sta drivers installation/purge is only the blacklisting of the, apparently, conflicting drivers, as the b43 drivers were up and running prior to the installation of the sta ones.

---

### Post by Bucky Ball on 2012-05-18
Could you please mark thread as 'Solved', if it is, to help others. ;)

---

### Post by Balthazar54 on 2012-07-08
> **bkratz said:**
> The following commands (one at a time should take care of you)

```
sudo apt-get install --reinstall bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf

```

The first makes sure that the sta driver is in place, the second and third blacklist the two drivers brcmsmac and bcma which clash with the correct sta driver. Copy/paste or make sure your typing is correct!

I have no idea what this does, but it fixed my wireless connection also on my Dell after doing an operating system update.

Thanx!!!

---

### Post by bkratz on 2012-07-09
[COLOR=Black]@[Balthazar54]("http://ubuntuforums.org/member.php?u=1697519")[/COLOR]

Sure glad it got you going!

---

### Post by Zenyx on 2012-07-20
> **bkratz said:**
> The following commands (one at a time should take care of you)

```
sudo apt-get install --reinstall bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf

```

The first makes sure that the sta driver is in place, the second and third blacklist the two drivers brcmsmac and bcma which clash with the correct sta driver. Copy/paste or make sure your typing is correct!
Hey bkratz, just wanted to let you know that this worked for me, so far anyways!

---

### Post by bkratz on 2012-07-21
> **Zenyx said:**
> Hey bkratz, just wanted to let you know that this worked for me, so far anyways!


Sure glad it worked for you too! Enjoy

---

### Post by FlindoJimbori on 2012-07-25
I have tried this and many more solutions, none successful. i did reboot after each one. When i  ran ubuntu in trial mode from my flash drive, it installed the braodcom drivers and wifi worked well. but now that i replaced windows and am running from my hard drive, my trial data was replaced with default settings, and the driver wont reinstall.  I have a dell mini10 netbook. please help!!!

---

### Post by FlindoJimbori on 2012-07-25
> **FlindoJimbori said:**
> I have tried this and many more solutions, none successful. i did reboot after each one. When i  ran ubuntu in trial mode from my flash drive, it installed the braodcom drivers and wifi worked well. but now that i replaced windows and am running from my hard drive, my trial data was replaced with default settings, and the driver wont reinstall.  I have a dell mini10 netbook. please help!!!
 
Sorry... it turns out that bkratz's solution worked afterall. I just had to search for the driver AFTER the reboot. Many thanks to bkratz and all others who have helped.

---

### Post by bkratz on 2012-07-25
> **FlindoJimbori said:**
> Sorry... it turns out that bkratz's solution worked afterall. I just had to search for the driver AFTER the reboot. Many thanks to bkratz and all others who have helped.




Finally just checked in and see the good news, congratulations!

---

### Post by Bucky Ball on 2012-07-25
> **bkratz said:**
> Finally just checked in and see the good news, congratulations!

Solving a few people's problems here but doesn't look like the original poster has posted since post #1. ;)

---

### Post by bkratz on 2012-07-25
> **Bucky Ball said:**
> Solving a few people's problems here but doesn't look like the original poster has posted since post #1. ;)



Just happy to help others and that is the reason for the forums, isn't it?

---

### Post by Bucky Ball on 2012-07-25
+1.

---

### Post by chinchillas on 2012-07-28
> **FlindoJimbori said:**
> Sorry... it turns out that bkratz's solution worked afterall. I just had to search for the driver AFTER the reboot. Many thanks to bkratz and all others who have helped.

How do you check it? Do you mean enable it?

---

### Post by squakie on 2012-10-27
I know this is an older thread, but does this also apply to a bcm4311?  I have that in an old dell laptop and no way to hard-wire to the router, so I need something I can download on another computer and then install on the laptop, as well as instructions on how to do any of it.  Thanks.

---

### Post by Bucky Ball on 2012-10-27
[I][B]Thread Closed

Reason:[/B][/I] Old thread.

@ squakie: Please post a new thread with a descriptive title and as much info as you can muster regarding your issues. Good luck.

---

