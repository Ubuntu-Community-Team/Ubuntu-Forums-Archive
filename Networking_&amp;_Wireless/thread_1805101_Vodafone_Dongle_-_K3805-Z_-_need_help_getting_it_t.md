---
title: "Vodafone Dongle - K3805-Z - need help getting it to work"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by moallen on 2011-07-15
Hi there,

I have a dongle that works fine with Windows, but causes me problems when trying it with Linux.  I have been reading other posts and seem to have tied myself in knots.

Here's my problem

1. I plug the dongle in
2. Select wireless icon and then select Vodafone contract
3. A window comes up saying "Enter password to unlock your login keyring - The password you use to log into your computer no longer matches that of your login keyring"
4. I have entered the root password with no success
5. Select Cancel and then get another message - "A password is required to connect to Vodafone Contract" - Once again, the oot password is rejected
6. Although I select cancel, the dongle appears to connect to Vodafone - I can ping a private address which appears to be the Vodafone gateway - 10.138.246.5 - I cannot ping anything else

Any advice would be greatly appreciated.

Thanks

Mo

---

### Post by westie457 on 2011-07-15
> **moallen said:**
> Hi there,

I have a dongle that works fine with Windows, but causes me problems when trying it with Linux.  I have been reading other posts and seem to have tied myself in knots.

Here's my problem

1. I plug the dongle in
2. Select wireless icon and then select Vodafone contract
3. A window comes up saying "Enter password to unlock your login keyring - [COLOR="Red"]The password you use to log into your computer no longer matches that of your login keyring[/COLOR]"
4. I have entered the root password with no success
5. Select Cancel and then get another message - "A password is required to connect to Vodafone Contract" - Once again, the oot password is rejected
6. Although I select cancel, the dongle appears to connect to Vodafone - I can ping a private address which appears to be the Vodafone gateway - 10.138.246.5 - I cannot ping anything else

Any advice would be greatly appreciated.

Thanks

Mo

Hello high-lighted in the quote the main issue you have and it needs to be reset.

Follow the steps in this link. [http://ubuntuforums.org/showthread.php?t=1305302](http://ubuntuforums.org/showthread.php?t=1305302)

That should get things running for you.

---

### Post by moallen on 2011-07-16
Hi there,

Thank you very much for that advice.  The password issue is now resolved.  However, the connection problem is still the same.  It appears to be connected, but I cannot ping web addresses even when I use the IP address rather than the domain name.

Just in case it is relevant, the mobile broadband settings are as follows:
Number     - *99#
Username   - web
password                 *empty*
APN        - internet
Network id              *empty*
Type any
Allow roaming if home network is not available - ticked

Thanks again for your help with this

Mo

---

### Post by moallen on 2011-07-17
Just got this working.  In case anyone else has the same problem - I found the answer at [http://betavine.mobi/bvportal/forums/index.html?threadId=ff8080812942915f0129502c4eef5736](http://betavine.mobi/bvportal/forums/index.html?threadId=ff8080812942915f0129502c4eef5736).

It comprised of my opening a terminal window and typing
sudo ifconfig usb0 -arp

There were also instructions to sort it automatically which I followed and it seems to work.  Here's the recored of what I did on terminal (using pico to create the two files I Needed)

roy@RoyLaptop:~$ cd /etc
roy@RoyLaptop:/etc$ cd udev
roy@RoyLaptop:/etc/udev$ cd rules.d/
roy@RoyLaptop:/etc/udev/rules.d$ ls
50-md300config.rules  70-persistent-cd.rules  70-persistent-net.rules  README
roy@RoyLaptop:/etc/udev/rules.d$ pico 10-vodafone-fix.rules
root@RoyLaptop:/etc/udev/rules.d# cat 10-vodafone-fix.rules
KERNEL=="usb0", RUN+="vodafone-fix.sh"
root@RoyLaptop:/etc/udev/rules.d# cd /lib/udev/
root@RoyLaptop:/lib/udev# pico vodafone-fix.sh
root@RoyLaptop:/lib/udev# cat vodafone-fix.sh
#!/bin/sh
ifconfig usb0 -arp
root@RoyLaptop:/lib/udev# chmod +x vodafone-fix.sh
root@RoyLaptop:/lib/udev#

---

