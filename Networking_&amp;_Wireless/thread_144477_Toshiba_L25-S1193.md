---
title: "Toshiba L25-S1193"
date: 2006-03-14
forum: Networking &amp; Wireless
---

### Post by deja2004 on 2006-03-14
I was able to grab one of those "Black Friday" laptops on the cheap at Circuit City last year. It's a decent computer (although not amazing) and it gets my work done.

However, when I tried setting up Kubuntu 5.10 on it, everything (after some working with the video drivers) worked fine except for the Atheros AR5005G wireless card. I have no idea how to get this card to work. :(

Any suggestions would be greatly appreciated!

---

### Post by djroadrash on 2006-03-15
hello deja2004
maybe its a problem with acpi, i had this problem on a few thinkpads.
try booting a livecd and put this parameters at boot
```
linux acpi=off dma=off
```
try that on livecd and see if it works, if it does just reinstall ubuntu or kubuntu and after it has detected all, then u can turn on acpi and dma.
try that and let us know what happened.
u can also do this in a terminal
```
$lspci
```
```
$dmesg
```
this will tell u what hardware u have and help see if it is being detected.
let us know

---

### Post by deja2004 on 2006-03-15
I used a Knoppix 3.9 Boot CD that I had laying around with those parameters, and it still didn't give me wireless connectivity. Within Knoppix, lspci yielding this result:

0000:09:04.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)

I noticed that when I did a "dmesg" in Kubuntu, towards the end I have several lines of errors referring to "ACPI-0508" and "ACPI-0362". Maybe that's what I'm looking for? (Sorry to sound like a n00b... I am)

---

### Post by djroadrash on 2006-03-16
i have been using linux for a year, so im a newbe as well, but since i have a hobby for laptop and desktop fixing i have a lot of machines to play with. and a lot of problems to solve sometimes. but i know that 5.10 has support for some atheros chips, i could not find yours but i might be missing something, check this page for your card: 
[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards")
you will have to do a little research for madwifi stuff as i never have used it. but it seems your card should be supported by breezy out of the box with madwifi.

---

### Post by djroadrash on 2006-03-16
maybe this will help 
[http://www.ubuntuforums.org/showthread.php?p=701804#post701804]("http://www.ubuntuforums.org/showthread.php?p=701804#post701804")
try the stuff i told the person in this thread and if no luck then his solution wont work since is a diferent chip. so i guess more work will have to be done.

---

### Post by deja2004 on 2006-03-18
Thanks for the info... I'm going to give Ubuntu a break and try out SUSE. I'll let you know if I have any luck there. Thanks for all your time though, I appreciate it! :-D

---

### Post by cwmccabe on 2006-04-16
I hate to post the dumb reply, but did you make sure to push the on/off button for the wireless device on the front of the laptop?  A number of Toshiba laptops have these buttons and sometimes people aren't aware of them.  I have an L25-S119 and the button is down on the front edge, near where the palm of my right hand falls when I'm using the touchpad.

---

### Post by deja2004 on 2006-05-15
Actually I did, just to follow up. Sorry for the way late reply, I forgot about this post :-P

---

### Post by deja2004 on 2006-05-15
And, I'm happy to admit, I've gone back to Ubuntu. Dapper seems to have resolved all of my issues. I'm SO excited about this release!:KS

---

