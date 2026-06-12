---
title: "ubuntu never detected wired ethernet"
date: 2005-12-31
forum: Networking &amp; Wireless
---

### Post by djroadrash on 2005-12-31
hi, i gave a try at installing ubuntu on a ibm thinkpad t20 650mhz pentium3
right from the begining of the install ubuntu could not find the ethernet card
i tried what one of the forums said and here is the code:



mando@ubuntumando:~$ sudo mii-tool eth0
password:
SIOCGMIIOHY on 'eth0' failed: No such device
mando@ubuntumando:~$ ifconfig eth0
eth0: error fetching interface imformation: Device not found
mando@ubuntumando:~$ lspci | grep Eth
0000:00:3.0 Ethernet controller: 3Com Corporation 3c556B CardBus [Tornado] (rev 20)
mando@ubuntumando:~$ lsmod | grep mii
mii                                   5248  1  3c59x



i have a wireless card but is my wife's and it only shows on the sistem/administration/networking and when i activated i could not  see any network. i figured i need to get the wired to work first. it seems logical. the computer can't see it on the sistem/admn/networking (is showing a light on the cable on the back of the computer), i guess its missing a driver. i am asking the forum to help me on the next step to get the wired network working, since the wireless card has to go on my wife's laptop to go to work.
thanx 
djroadrash:???: [LIST=1]
[/LIST]

---

### Post by djroadrash on 2005-12-31
am using ubuntu 5.10 for all this. 
thanx

---

### Post by Jeff12088 on 2005-12-31
Can you provide the card that you are using?
Check this: [https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards)

---

### Post by djroadrash on 2006-01-01
thanx for the quick response.
i asume that the code for this tells the making of the card:


mando@ubuntumando:~$ lspci | grep Eth
0000:00:3.0 Ethernet controller: 3Com Corporation 3c556B CardBus [Tornado] (rev 20)



i looked at the link and all i can say is that it looks like is a 3Com card model 3c556B (toronado), i saw a 3c905x (toronado-vortex) but i dont know if the same driver is true eventhought it does look like it is, now this next code tell us the driver?



mando@ubuntumando:~$ lsmod | grep mii
mii 5248 1 3c59x


i asume those last 5 digits (3c59x) is the chipset/driver i saw on the link, but this ones were not detected automatic or worked. (note: i just erased fedora core 3 form this laptop and the same conection was working, so it does work).
other than this data i dont know what else i can tell you, this card is the internal original card on the moderboard of the laptop. so i have never seen it. thanx
djroadrash

---

### Post by djroadrash on 2006-01-03
well, since the lack of someone stepping up to answer questions regarding ubuntu+thinkpad t20 (most important if the internet would work), i decided to go back to fedora core 3 as the os on this laptop, if only because i can go on line and fix and configure the machine. ubuntu never detected the original etherent card in the laptop, no idea how to make it to work. tried several things on code, read several incomplete threads about this problem on thinkpads (many people had it and i doubt they fix it ), and could not get an answer and solution:confused: . it seems it is a kernel problem since a lot of people had no problem with warty 4.10. i tried both 5.4 and 5.10 and no internet. dont get me wrong, i like ubuntu (have it on 2 more machines working fine), just this thinkpad is not working and i have no time to wait for someone to come up and help. thanx and hope to hear no more of this problems will exist on the new dapper.if i see a response that helps i might try again.
djroadrash

---

### Post by mips on 2006-01-04
Try disabling APCI & APIC during installation at bootup.

---

### Post by plamtrue on 2006-01-06
I have the exact same problem.  The ACPI (Advanced Configuration and Power Interface) was already disabled, and I'm not sure what APIC is or how to disable it.  Could it be the Advanced Programmable Interupt Controller?  Could I disable it by adding "noapic" to my grub.conf?  And why do you think that will help?

---

### Post by Zeroedout on 2006-01-06
I don't think your card is officially supported, try
sudo modprobe -l |grep 3c59     to see if the module is loaded, if not, try
sudo modprobe 3c59x . 

If it doesn't show up after that, i'de upgrade to the latest kernel you can, otherise, muck around with the module options doing everything you can manually, [http://ftp.pieskovisko.sk/linux/slackware/slackware-8.0/docs/linux-2.2.19/networking/vortex.txt]("http://ftp.pieskovisko.sk/linux/slackware/slackware-8.0/docs/linux-2.2.19/networking/vortex.txt") read through that for a list of options you can set.

---

### Post by djroadrash on 2006-01-06
hi everyone,  i took a diferent rout and installed kanotix it did a great job at detecting all my hardwaren with live cd and once i figured out their installer it was pretty easy almost as easy as ubuntu, just with all the hardware there. and so i am adopting this new distro for this laptop is nice and works, i still have ubuntu in my other two boxes running 5.4 and 5.10, thats what is all the fun of linux anyway. dont know if this thread will help anyone but sometimes thats how it has to be.
thanx for the input of all
djroadrash

---

### Post by mips on 2006-01-07
If you have a look at the kanotix setup/config you should be able to copy the parameters to (K)Ubuntu and make it work I think. Both distros are based on Debian.

---

### Post by djroadrash on 2006-01-07
a thanx!, i ll give it a try.

---

### Post by djroadrash on 2006-01-30
hi everyone, well it just took installing kubuntu and simply putting at install boot  prompt : "linux acpi=off" 
the internet configured by itself, just start firefox. enjoy
thanx for the help 
djroadrash:-D

---

