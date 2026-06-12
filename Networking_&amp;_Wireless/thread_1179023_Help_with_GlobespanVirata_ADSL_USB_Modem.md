---
title: "Help with GlobespanVirata ADSL USB Modem"
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by hesabb on 2009-06-05
**Help with GlobespanVirata ADSL USB Modem**             
                                                                Hi Guys

I Have a GlobespanVirata USB ADSL Modem (Corecess Model 3112UG chipset
GS7470), and have Surfed through the Net ALL Day Long to find out how to
make Kubuntu 9.04 (2.6.28-11 Generic Kernel) use the Modem so I can
connect to the Internet and start My first days in Linux (after Switching
From Windows XP) but I'm Stuck in Installing the Modem although I have had
some progress…

First I downloaded the .deb file from:
[http://eciadsl.flashtux.org/download.php](http://eciadsl.flashtux.org/download.php)
I've also downloaded some synch .bin file from the mentioned URL that
didn't work for me (so I had to create my own .bin file which was a long
story to tell)

I Used "eciadsl-text-config" command to configure my modem configuration
files and also to test all those bin files to see which one let the Modem
LED to stop blinking and become fully ON

I then used eciadsl-start command to start my modem (a 5-step process
after which my modem LED became fully ON)

I also used ifconfig to find out then I had a tap0 Ethernet device
created, and the command pppoeconf tap0 to configure some more settings
(which I used the recommended settings for all except Username and
Password for my Connection)

I was told by the tutorials I've read so far to use the command pon
dsl-provider in the end to see that I'm connected to the Internet. But I
WAS NOT…
I tried different options, different combination and… but still no Luck.

I am very new to Linux and I don’t know the meaning of any of those
commands I've mentioned and I'll probably fail in beating my Windows
Habits without Internet connection.

I don’t really have any idea where could the problem be? I have no clue. I
don’t know where to start?… is it a problem with modem configuration or
now that it's ON the problem is in some Network settings?

Please help me

Thanks in advance

---

