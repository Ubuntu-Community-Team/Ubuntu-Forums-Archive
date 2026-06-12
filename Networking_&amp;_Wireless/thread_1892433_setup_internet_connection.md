---
title: "setup internet connection"
date: 2011-12-08
forum: Networking &amp; Wireless
---

### Post by Ubuntee1 on 2011-12-08
I have recently installed ubuntu 8.10 and i already have window7 os on my pc and internet is connected on that.
I heard that after installing linux it will automatically detect the intenet connection.
But in my case after installation the network is not detected.
I changed the /etc/network/interfaces by taking the addree,mask and gateway information from the windows
and also created the resolve.conf file(which was not existing before) and added the dns addresses.
and tried network restart command but i got a message saying 
unable to read /etc/network/inetrfacesfiles and failed to configure the internet.
please let me know what is the problem.
does linux/ubuntu need a separate ethernet card to internet work.because i am using on board ethernet card.

---

### Post by jaimeaux on 2011-12-08
> **Ubuntee1 said:**
> I have recently installed ubuntu 8.10 and i already have window7 os on my pc and internet is connected on that.
I heard that after installing linux it will automatically detect the intenet connection.
But in my case after installation the network is not detected.
I changed the /etc/network/interfaces by taking the addree,mask and gateway information from the windows
and also created the resolve.conf file(which was not existing before) and added the dns addresses.
and tried network restart command but i got a message saying 
unable to read /etc/network/inetrfacesfiles and failed to configure the internet.
please let me know what is the problem.
does linux/ubuntu need a separate ethernet card to internet work.because i am using on board ethernet card.
 
No, it ubuntu can use an on-board ethernet card/wireless card.
 
Questions:
 
What kind of card is it (i.e. wireless/wired)?
 
What model/brand is the card?

---

### Post by Ubuntee1 on 2011-12-08
Thanks for the quick reply.
 
 
Right now i dont have acess to my system, donot know the exact specification.
 
but that came with intel motherboard.

---

### Post by yndesai on 2011-12-08
I for ethernet LAN ubuntu never had issue. Do give specification of your ethernet card. 

If your network do not have DHCP (ie auto allocation of ip address to the client computer) then you need to provide the ip address settings manually. So you may check the ip address related settings in windows 7 and configure them in ubutnu.

BTW 8.10 is quite old if you are installing for first time better use the latest available version.

---

### Post by jaimeaux on 2011-12-08
8.10 is indeed old, is there a reason you installed it specifically? You should probably go w/ 10.04 LTS or 11.10 IMHO; However, once you get access to your computer, let us know what kind it is. I have a feeling this ought to be something simple.

---

### Post by Ubuntee1 on 2011-12-08
> **jaimeaux said:**
> 8.10 is indeed old, is there a reason you installed it specifically? You should probably go w/ 10.04 LTS or 11.10 IMHO; However, once you get access to your computer, let us know what kind it is. I have a feeling this ought to be something simple.
 
 
No special reason, i just want to implement a project on ubuntu and 8.10 is enough for that.Ayways i will upgrade the version.
 
Coming to my ethernet card info:
below is the info i got using ipconfig /all in cmdline.
actually there is a lot of info i got when i used the command.
 
 
Ethernet adapter Local Area Connection:
Connection-specific DNS Suffix . :
Description . . . . . . . . . . . : Intel(R) 82579V Gigabit Network Conection
 
Physical Address. . . . . . . . . : xx-xx-xx-xx-xx-xx
DHCP Enabled. . . . . . . . . . . : Yes
Autoconfiguration Enabled . . . . : Yes
IPv4 Address. . . . . . . . . . . : x.xx.xxx.xxx
Subnet Mask . . . . . . . . . . . : xxx.xxx.xxx.x
Lease Obtained. . . . . . . . . . : Thursday,
Lease Expires . . . . . . . . . . : Thursday,
Default Gateway . . . . . . . . . : x.xx.xxx.x
DHCP Server . . . . . . . . . . . : xxx.xxx.xx.xx
DNS Servers . . . . . . . . . . . : xxx.xxx.x.xxx
xxx.xxx.x.xx
NetBIOS over Tcpip. . . . . . . . : Enabled
 
i have used ip , subnet,and gateway as mentioned here, but when i use network restart command it cound not open the file interfaces.
 
please help.

---

### Post by jaimeaux on 2011-12-08
> **Ubuntee1 said:**
> No special reason, i just want to implement a project on ubuntu and 8.10 is enough for that.Ayways i will upgrade the version.
 
Coming to my ethernet card info:
below is the info i got using ipconfig /all in cmdline.
actually there is a lot of info i got when i used the command.
 
 
Ethernet adapter Local Area Connection:
Connection-specific DNS Suffix . :
Description . . . . . . . . . . . : Intel(R) 82579V Gigabit Network Conection
 
Physical Address. . . . . . . . . : xx-xx-xx-xx-xx-xx
DHCP Enabled. . . . . . . . . . . : Yes
Autoconfiguration Enabled . . . . : Yes
IPv4 Address. . . . . . . . . . . : x.xx.xxx.xxx
Subnet Mask . . . . . . . . . . . : xxx.xxx.xxx.x
Lease Obtained. . . . . . . . . . : Thursday,
Lease Expires . . . . . . . . . . : Thursday,
Default Gateway . . . . . . . . . : x.xx.xxx.x
DHCP Server . . . . . . . . . . . : xxx.xxx.xx.xx
DNS Servers . . . . . . . . . . . : xxx.xxx.x.xxx
xxx.xxx.x.xx
NetBIOS over Tcpip. . . . . . . . : Enabled
 
i have used ip , subnet,and gateway as mentioned here, but when i use network restart command it cound not open the file interfaces.
 
please help.

How did you use Ipconfig on a linux box?

---

### Post by Ubuntee1 on 2011-12-08
> **jaimeaux said:**
> How did you use Ipconfig on a linux box?
 
 
No i dint use ipconfig on linux box.
I  used the ipconfig /all on windows and got all the info (address,mask and gateway and dns).
 
when i use ifconfig on linux after editing interfaces in /etc/network it not showing the contents i edited.

---

### Post by jaimeaux on 2011-12-09
okay, you had me confused. boot into linux, and post the output of "lspci -vv" (just the part pertaining to your wireless card, if you can find it. If you can't, don't worry, we still have options!

---

### Post by inkrypted on 2011-12-09
First how did you edit the /etc/network/interfaces file. Perhaps something like this sudo gedit /etc/network/interfaces. And when you did were any interfaces listed such as eth0 or wlan0. Perhaps it would be easier with a good gui utility such as wicd.

---

### Post by oldtimer7777 on 2011-12-09
You are already running Windows 7 but you picked Ubuntu 8.10? You aren't going to be able to upgrade from 8.10 because that is EOL (end of life), even until the next release. It won't update either so it is junk. 

Here is a guide to correctly install Ubuntu on your system so you won't have this issue anymore.  Hopefully the driver you need has been incorprated into the kernel by now. You will know the moment you boot into the live disc or live stick of Ubuntu to install from if it does work too.

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

### Post by Ubuntee1 on 2011-12-09
> **inkrypted said:**
> First how did you edit the /etc/network/interfaces file. Perhaps something like this sudo gedit /etc/network/interfaces. And when you did were any interfaces listed such as eth0 or wlan0. Perhaps it would be easier with a good gui utility such as wicd.
 
 
i have used the below command
 
sudo vim.tiny /etc/network/inetrfaces
 
initially it dint allow me to save the files,  
i tried :wq some times ....
finally saved.
 
i dont understand what is wrong...

---

### Post by jaimeaux on 2011-12-09
> **oldtimer7777 said:**
> You are already running Windows 7 but you picked Ubuntu 8.10? You aren't going to be able to upgrade from 8.10 because that is EOL (end of life), even until the next release. It won't update either so it is junk. 

Here is a guide to correctly install Ubuntu on your system so you won't have this issue anymore.  Hopefully the driver you need has been incorprated into the kernel by now. You will know the moment you boot into the live disc or live stick of Ubuntu to install from if it does work too.

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

I gotta agree with oldtimer7777... you're running a pretty old version on a laptop that's compatible w/ Windows 7... you've kinda installed the equivalent (although miles better) version of Ubuntu95......

Y'know?

---

### Post by Ubuntee1 on 2011-12-16
> **jaimeaux said:**
> I gotta agree with oldtimer7777... you're running a pretty old version on a laptop that's compatible w/ Windows 7... you've kinda installed the equivalent (although miles better) version of Ubuntu95......

Y'know?

OK..K..K..K..K,


I have upgraded to 11.10 and now the internet is working.
i wanted to trouble shoot the problem in earlier version, but that's ok now understood the problem.

but i have another question.
11.10 look is completely changed compared to classic linux, i am not able to find out where synaptic manager is, where terminal is, and preferences so..on.

please let me know where is the setting available to change to classic look.

---

### Post by jaimeaux on 2011-12-16
At your logon screen, click the thing that looks like a little cog/gear and select a different gui. 
 
Or just login, click the Ubuntu logo, and type in "gnome-terminal"

---

