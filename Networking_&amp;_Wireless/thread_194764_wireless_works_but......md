---
title: "wireless works but....."
date: 2006-06-11
forum: Networking &amp; Wireless
---

### Post by bobterri on 2006-06-11
I've got a Dell 5160 Inspiron laptop with a bcm4306 wireless card up and running using nvidswrapper.  However, "System>Administration>Networking" won't work, even though it shows the card as activated.  I have to go to a terminal and use the command line to connect through the wireless tools.  That means type the whole process:

sudo iwconfig eth1 mode Managed
sudo iwconfig eth1 key open xxxxxxxxxxxxxxxxxxxxxx
sudo iwconfig eth1 essid 'xxxxxxxxx"
sudo dhclient eth1

Only then will it connect!  

Has anyone run into this problem?  If so, can you help, or perhaps someone could suggest a start up script that I can use to shorten the process of connecting to my wireless access point.

---

### Post by Zelut on 2006-06-11
I have a bcm4306 card and, since Dapper, actually stopped using ndiswapper.  I'm using the native driver and everything seems to work well.

You can try installing the 'bcm43xx-fwcutter' package and then run the included script (don't have my machine with me to know the exact path..)

This will use the native driver and should work for you.. let me know, we'll do some more digging :)

---

### Post by bobterri on 2006-06-11
The reason I went to ndiswrapper was because I read somewhere that native driver's bit rate is only 11 M/bs compared to 54 M/bs with ndiswrapper.  Waht is your bit rate when you iwconfig in terminal?

---

### Post by Zelut on 2006-06-11
Mine is 54M as far as I know.  My understanding on the 11M was that speed restriction could help in troubleshooting.  I could be wrong but mine is 54M last time I looked..

---

### Post by bobterri on 2006-06-11
Hmmm!

Interesting, but before I shutdown ndiswrapper which is obviously working for me and try the native driver, I wonder if there is anyway to set my security setting in the configuration to open instead of restricted.  

I have a feeling that when I:

sudo iwconfig eth1 key open xxxxxxxxxxxxxxxxxxxxxx

and use "open" instead of "restricted" that that is what is enabling the connection.  I have not found a way of doing that in "System>Administration>Networking"

I was running Xandros 3.02 on this same laptop and it wouldn't connect with the security setting as "restricted."  Only when I set it to "open" would it work.

---

### Post by bobterri on 2006-06-12
I tried connecting by simply:

sudo iwconfig eth1 key open xxxxxxxxxxxxxxxxxxxxxx
sudo dhclient eth1

My wep key code is entered in the "System>Administration>Networking" configuration, so I think I might be right in that my security configuration must be set to "open" instead of "restricted."  

My question again is, "Is there any way to set the security configuration in  'System>Administration>Networking" to "open" instead of "restricted?"

I don't want to try the native driver yet, because I might have the same problem if the security configuration is causing the problem.

---

### Post by bobterri on 2006-06-12
Oops, I forgot to mention that when I tried connecting with just:

sudo iwconfig eth1 key open xxxxxxxxxxxxxxxxxxxxxx
sudo dhclient eth1

It connected with just those two commands in terminal.

---

### Post by bobterri on 2006-06-12
Please, doesn't anyone know where I can find where the "System>Administration>Networking" scripts are?  I want to check whether the security settings in the script is set to "open" or "restricted."  I'm sure there's a default setting.

---

### Post by bobterri on 2006-06-12
OK, I solved the problem!  In a Ubuntu Wiki wireless troubleshooter it states that you set your security setting to "open" by adding the following to /etc/network/interfaces:

wireless-key xxxxxxxxxxxxxxxxxxxxxxxxx open

Apparently the default is "restricted."  When I edited /etc/network/interfaces and added "open" to the end of the wireless-key line, I restarted my laptop and had an instant connection.

Thanks, all who helped.

---

