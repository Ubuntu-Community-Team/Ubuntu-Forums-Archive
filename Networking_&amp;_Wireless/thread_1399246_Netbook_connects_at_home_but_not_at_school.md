---
title: "Netbook connects at home but not at school"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by mullinsn2000 on 2010-02-05
I have a HP Mini 1120NR.  I have installed Ubuntu 8.04.  I can connect wirelessly at home, but I can not at school.  The network shows up and usually shows a strong signal.  It tries to connect, but after a minute or so it stops and does not connect.  The network is non-secured so anyone within range can use it.

Any ideas on what the problem could be?

---

### Post by mullinsn2000 on 2010-02-07
Anyone??

---

### Post by crucialhoax on 2010-02-07
I had a problem similar to this. It would only connect to a network with a SSID of beta. This fixed it:

First, to find the wireless extension use:

```
ifconfig -a
```

Whatever your wireless extension was be it wlan0 eth1 eth0 insert that instead of <your wireless card> 

```
sudo iwconfig <your wireless card> ssid any
```

then apply this command:

```
sudo iwconfig <your wireless card> commit
```

---

### Post by mullinsn2000 on 2010-02-08
when I use the command "sudo iwconfig eth0 ssid any"
I get:
iwconfig: "ssid" unknown command

---

### Post by CrammitTheFrog on 2010-02-08
Try using "essid" instead of "ssid".

I had this problem a couple of times when I tried to connect to the schools network.  The problem ended up being that the required DNS addresses were different than I used at home.  I lucked out and my system changed them itself and it wasn't till I got home that I realized that the DNS addresses changed.  Now, I use a profile for at home and at school.

---

### Post by mullinsn2000 on 2010-02-08
> **CrammitTheFrog said:**
> Try using "essid" instead of "ssid".

I had this problem a couple of times when I tried to connect to the schools network.  The problem ended up being that the required DNS addresses were different than I used at home.  I lucked out and my system changed them itself and it wasn't till I got home that I realized that the DNS addresses changed.  Now, I use a profile for at home and at school.
No error message that time, thanks!

I am new to Ubuntu.  How do I set up two different profiles?  I had a doctors appointment today and I was able to connect their with only 20% signal strength.  I will find out tonight if I can connect to the school network.

---

### Post by mullinsn2000 on 2010-02-09
It still did not work.  I tried to connect lastnight and it would not connect..  It had a strong signal.

Any other suggestions???

---

### Post by CrammitTheFrog on 2010-02-11
Which version of Ubuntu are you running?  I'm currently running 8.04, which comes with a network manager.  You can download this if you would like through the synaptic.  It's ok but not perfect.

You may need to see if a special configuration for Linux users is needed to connect to the school's network.

---

### Post by mullinsn2000 on 2010-02-11
I am running 8.04.  I could not get 9.10 to work properly on the netbook.  I am going to take my wifes netbook running Windows XP and Windows 7 and see if I can connect using it.  If so I will check out the configuration on it and see what I can do with mine.

---

### Post by mullinsn2000 on 2010-02-11
I just spoke with someone from the IT department of the school.  They say that their network only works with XP and do not know why Vista, 7, or any Linux OSes will not work with it.

I have never heard of anything like this.  Anyone hear something like this?

---

### Post by CrammitTheFrog on 2010-02-15
No.  I have connected to many schools and have not had a problem.  To me, it sounds like your school is either being overly protective or just not up to date.

---

### Post by Iowan on 2010-02-15
Probably won't work, but [here]("http://ubuntuforums.org/showpost.php?p=8703594&postcount=26") is something to try...

---

### Post by ant2ne on 2010-02-15
> **mullinsn2000 said:**
> I have never heard of anything like this.  Anyone hear something like this?Yup, poorly trained, overworked and underpaid. They just don't care. wifi and dhcp protocols are OS independent. I'm going to go out on a limb and say, that they just don't care.

---

### Post by mullinsn2000 on 2010-02-24
I have not tried to use 9.10 Live CD from the USB drive yet, but trying to get this netbook connected to my school is getting to be annoying.  It is a totally unsecure network.  MAC address does not have to be given to the school to "allow" it on the network.  I connected fine with my wifes netbook, running Windows 7.

Any more suggestions???


I got rid of Network Manager and I am using WICD now, but that change did not help.  I can see the network and the signal is strong, it just will not connect at all.  Someone please help!

---

### Post by mullinsn2000 on 2010-02-27
The same problem occurs when using the Live CD of 9.10.

Someone here must know how to solve my issue, lol.  This place is filled with experts.  Someone please help, I do not want to have to go buy Windows and start using Windows on this netbook again.

---

### Post by Jekshadow on 2010-02-27
A WiFi network is a WiFi network. My school uses WPA2 Enterprise, and when I asked for the details (CA cert, whether it uses PEAP, etc.), they said, "Linux is an outdated and command line only operating system that doesn't support WiFi networking. Seeing that your computer must have come with a version of Windows, we will not help you until you reinstall the version of Windows that came with your computer." or something to that effect.

I just tried different settings until it let me connect. I then emailed them a screenshot showing I was connected and a link to Wikipedia's GNOME article, which mentions that GNOME released its first version in March 1999.

---

### Post by mullinsn2000 on 2010-02-27
> **Jekshadow said:**
> A WiFi network is a WiFi network. My school uses WPA2 Enterprise, and when I asked for the details (CA cert, whether it uses PEAP, etc.), they said, "Linux is an outdated and command line only operating system that doesn't support WiFi networking. Seeing that your computer must have come with a version of Windows, we will not help you until you reinstall the version of Windows that came with your computer." or something to that effect.

I just tried different settings until it let me connect. I then emailed them a screenshot showing I was connected and a link to Wikipedia's GNOME article, which mentions that GNOME released its first version in March 1999.
I understand that it is most likely a setting or something that needs to be done in Ubuntu. My problem is I do not know what else to do.  I am very new to Ubuntu, and Linux in general.  I have tried different ideas I have seen in other threads, but nothing so far has solved my problem.  I am just looking for some more ideas.

---

### Post by Jekshadow on 2010-02-27
> **mullinsn2000 said:**
> I understand that it is most likely a setting or something that needs to be done in Ubuntu. My problem is I do not know what else to do.  I am very new to Ubuntu, and Linux in general.  I have tried different ideas I have seen in other threads, but nothing so far has solved my problem.  I am just looking for some more ideas.

Just play with the settings and try different combinations, that worked for me. I cannot tell you what the exact settings should be without examining your school's wifi network.

---

### Post by mullinsn2000 on 2010-02-27
> **Jekshadow said:**
> Just play with the settings and try different combinations, that worked for me. I cannot tell you what the exact settings should be without examining your school's wifi network.
Ok.....What info should I ask the IT dept. from the school about their network?  I am not real familiar with what info is needed.  Thanks!

---

### Post by mullinsn2000 on 2010-03-01
Anyone.....................?  What info do I need from my school about their network.  I do not know if/what encryption they use.  There is absolutely no password that needs to be entered.  I can connect from a Windows machine with no problem whatsoever.  What settings are different between Windows 7 and Ubuntu?  Really do not want to have to go spend a lot of money on Windows because of something that is probably easily fixed.  Any help will be much appreciated.  I will try any technique as long as I do not have to be on their network to try it.  I can connect to other unsecure networks (Doctors office, McD's, etc.) without a problem.

---

### Post by mullinsn2000 on 2010-03-02
Ok.....I got it connected lastnight, but...... I could not open many webpages to test the connection because the classroom I was in (the computer lab, lol) only had a 20% signal strength.  Here is what I did:

Open terminal and typed: ping [Random IP Address out of my head]

It couldn't ping the address, but it did show my IP, so the network was assigning an IP

I opened Wicd and selected Advanced Setting on the school network

Chose Static IP and typed the IP address I was given
 
Netmask and Gateway were assigned automatically after entering my IP

I typed the Gateway as the first DNS and it connected


I will try all of this again tonight in a class where I get at least 80% signal strength and see if it works.  I am not marking this as SOLVED until I know for sure that it is.

---

### Post by Swagman on 2010-03-02
He's a good bloke is that .. Percy Verence  (perseverance)

> 
Nobody trips over mountains.  It is the small pebble that causes you to stumble.  Pass all the pebbles in your path and you will find you have crossed the mountain.  ~Author Unknown


and...
>  It's not that I'm so smart, it's just that I stay with problems longer.  ~Albert Einstein

Good work Sherlock

---

### Post by mullinsn2000 on 2010-03-02
Problem is definitely not solved.  The class I had tonight was in a room where I got 80%+ signal strength and I was still unable to go to any websites other than the schools homepage.  I am out of ideas on how to fix this issue.

Anyone have any ideas?

---

