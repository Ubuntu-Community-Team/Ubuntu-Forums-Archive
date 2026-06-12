---
title: "Trendnet TEW-421PCMCIA Card Working"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by LenL on 2009-07-13
I have tried a number of things to get my Trendnet TEW-421PCMCIA card with the realtek RTL8185 chip to work with a LINUX distro.  I tried both Debian and Fedora distros first and the card was not recognized.  This is for an IBM thinkpad 600X laptop.
 

 Then I installed Ubuntu 9.04 and the card was recognized and the network.   I was even able to download and install updates to the initial Ubuntu CD install.  But after I rebooted I was having trouble getting into the network.  So I tried all kinds of things.  Change settings for the card, the keyring, including attempting to bypass the keyring.  I even tried reinstalling Unbuntu 3 or 4 times as the card seemed to work before updates were installed.  
 

 Finally I installed Ubunto and the updates and changed the keyring password to agree with the Network PASSPHRASS password and not my login PW which I don't key in anyway as I set the system up to bypass login sign in.  Suprise surprise based on what I did the system will boot up right to displaying all the networks it can find including mine and even log me on to the network withtout my having to enter any passwords including the keyring password.  So I think I have proven that this particular PCMCIA card and chipset will work with Linux and specifically UBUNTU.  I don't know if I exactly remember all the things I did to get this to work the way it does but it was not by installing anything special.
 

 That is the good news.  The bad news is that sometimes it boots up fine into the network and other times I have to restart the laptop 2 or 3 times to get it to boot up and get me into the network.  It seems to always see my network but hangs trying to get my laptop signed in. Like I said if that happens and I simply restart UBUNTU 2 or 3 times I get right in without doing any sign in.
 

 There may still be a quirk of somesort with UBUNTU, the keyring processing or the card that causes this issue.  However that fact that the Laptop can simply be restarted and I get right into my network without doing anything is very interesting.  Especially after reading all of the hints and special things suggested for people to do to get this card to work and or avoid entering the keyring PW everytime.

---

