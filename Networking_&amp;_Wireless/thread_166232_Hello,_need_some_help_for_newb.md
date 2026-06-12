---
title: "Hello, need some help for newb"
date: 2006-04-26
forum: Networking &amp; Wireless
---

### Post by penywise on 2006-04-26
First of all I would like to say hi, it's my first post here, so it should be kind of official ;)

I am a proud member of the Linux community since... last night:mrgreen: 
So far I have using Windows only... and my knowledge of Linux is at really low level.

I got an Ubuntu installed, never mind I am a total noob, it is what was reccomended to me, after several discussions on Damn Small Linux, etc...

I had a problem with the installation on the part with Detecting Network (or sth like that). Then it asked me to configure my internet manually (IP, etc...) but they were all written in a file on my Windows, so I didn't stop the installation, thinking that when it's complete I would finish that with no troubles as well.

Frankly I slept for a few hours and did... nothing. I "Googled", took notes and rebooted every time to try everything to get my internet running on the Linux as well... No success.

I have internet directly through my LAN card. The motherboard is EPOX 8RDA+, and the LAN card is onboard there.

I HAVA A STATIC IP ADDRESS

So, I looked at the Device Manager (in Linux), but what I saw there was just info, that could not be modified in any way - no double click, no right button... My AUDIO card is onboard as well, and Ubuntu doesn't have problems detecting it (well, I have 5.1 speakers that are not set up... but first things first...)

Opening the Terminal and writing down
"network-admin"
got me into the Network Setup
I continued to "Google" and look for possible solutions, found a couple of things, even with image explanations...

I have only two types of "choises" in my Network Setup. One is "Modem", the other one is "Ethernet". No wireless, NOT a SINGLE other option to do there - just "Activate, Deactivate & Configurate". NOTHING else (the images and things to do I found were with option for wireless network (not that I need it..))

So I dropped the Modem "way" of getting internet...

I tried setting it by Ethernet (the ONLY other option).
So I chose the DHCP - no internet started.
I tried to setup the connection manually writting my IP, Subnet Mast and Gateway. Initialized it again - no effect...](*,) 

As for the Device Manager - it's all like "unknown", "unknown" (for CPU info, etc)... 
Yet it finds my Video, finds my HDD, finds my Audio...

I would like to apologize for that long first post of mine.

I am a complete noob, leading the noobs, but I would, and I will advance never mind how long it takes. I have the will and believe it would be a pleasure to "do" it.
(as long as I get at least my internet running);) 

Thank you in advance... never mind the answer is somewhere... here

---

### Post by deadgobby on 2006-04-26
Just a simple way. Try Booting with you modem on. Try it an see if that works.
Gobby

---

### Post by penywise on 2006-04-26
[QUOTE=deadgobby]Just a simple way. Try Booting with you modem on. Try it an see if that works.
Gobby[/QUOTE]

Thank you for you quick reply.

I don't have a modem.

I have internet from a "switch" (on the roof of the building), then it is connected directly to my onboard LAN card via LAN cable.

And... the LAN card is always on ;)

---

### Post by Phasmagon on 2006-04-26
If you do not have a DHCP server you should configure all the settings yourself. This means either by System-->Administration-->Networking, where you have to add your IP, Subnet and Default gateway, plus your DNS preffered servers.

You can do this also from command line:

# sudo ifconfig eth1 xxx.xxx.xxx.xxx netmask 255.255.yyy.yyy up
# sudo route add default gw zzz.zzz.zzz.zzz
# sudo echo nameserver [www.www.www.www](www.www.www.www) > /etc/resolv.conf

I assume eth1 is the name of your ethernet card
xxx.xxx.xxx.xxx is your static IP
255.255.yyy.yyy is your subnetmask
zzz.zzz.zzz.zzz is your default gateway
[www.www.www.www](www.www.www.www) is your providers preffered DNS server.

Hope this helps you.

---

### Post by penywise on 2006-04-26
Yep, I did it all. I know I wrote down the exact IP, Subnet mast & Gateway. I took them from the netw. conn. in the Windows (I run both the OS, just cut 2 partitions for the Linux, one of them SWAP)

As for the DNS server -> (as I said - I'm more noob, then newb;)) -> how would I know what to write there? I tried several things there, but afterwards when I ran the:
"network-admin" -> it gave me several lines of some error in the Terminal...

When I delete the DNS (leave it empty) - and run that command again - no errors occure.

**So, how do I understand the prefered DNS server(s)?**

*# sudo echo nameserver [www.www.www.www](www.www.www.www) > /etc/resolv.conf*
--> what would that mean?

[COLOR="Red"]EDIT:[/COLOR]

I had a chat with some guys that told me several commands... To check "/etc/conf.d"
Then to initialize something like  "/etc/conf.d/network start"

I browsed My Computer, the "etc" directory... and found nothing like that, could open such files from the File Browse either.
I found some "networking"... etc, but when I tried to open them (the guys told me that the settings of the connection are held in that "/etc/conf.d" file) -> they were all .xml files, and I didn't see any place to add or modify the IP, Subnet, etc...

[COLOR="Red"]EDIT 2:[/COLOR]

I installed Ubuntu 5.04

---

### Post by penywise on 2006-04-26
Oh sh*t, I'm such a dumb *ss!

I just remembered that my onboard LAN stopped working, so I got "some" PCI LAN card from the ISP's office and set everything again...

But it was so long, that I just thought of it and remembered...

Not that it does any matter, but...

So, how do I write the "preffered DNS"
(I believe that is what prevents the start of the whole thing...)

[COLOR="Red"]EDIT:[/COLOR]

I looked for some info and got into:

"look in /etc/resolve.conf "
my DNS should be there...

---

### Post by penywise on 2006-04-26
GR8, I contacted my ISP, he told me... uh the same setting I tried with last night...

As my IP is not static - my DNS server is the same as my Gateway...

I... think I did the same setting last night, but... yet nothing happened](*,)

---

### Post by mips on 2006-04-26
[http://www.ubuntuforums.org/showthread.php?t=87643](http://www.ubuntuforums.org/showthread.php?t=87643)

At what point do you get stuck with the above guide ?

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please copy **entire** output of windows **ipconfig /all** command here
7. Who is your ISP and provide a web link.

---

### Post by penywise on 2006-04-26
Thank you, I will read and write down carefully everything writen there.
I can get the setting you requested as soon as I get back home...

The main thing would be where the whole process crashes...

As for the ISP:
[http://powerone-bg.net/index.html](http://powerone-bg.net/index.html)

Hope that would help...

---

### Post by penywise on 2006-04-26
Well I got it running, as I read all day and collected info, contacted my ISP - he told me the DNS, I set it up - now I have internet...

Now comes the real stuff...

Thank you all, we will surely keep in touch (all day):mrgreen:

---

