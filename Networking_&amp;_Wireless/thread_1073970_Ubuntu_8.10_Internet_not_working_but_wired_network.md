---
title: "Ubuntu 8.10 Internet not working but wired network is connected"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by mohsinhussain on 2009-02-18
Internet Working fine on Win XP but not on Ubuntu 8.10 at the same time.
I have installed Ubuntu desktop 8.10,from 2 days its working fine and internet also working fine,but suddenly today internet stop working.
It is showing Wired internet connected and its auto-detect eth0 but internet not working,a day before it detect auto eth0 and internet was working fine but not now,everything is showing fine its showing mac address,my system ip and DNS,dhcp Ip's all of them correct but still internet not working.

I am having Windows XP and Ubuntu 8.10 with Dual-boot and internet working fine on my windows XP machine but it is not working on Ubuntu.

run ifconfig cmd==>and it shows correct ip and mac there.

I try Many things search through google 
(((
Add lines to
/etc/network/interfaces
auto eth0
iface eth0 inet dhcp
)))

(((
try
sudo ifdown eth0
sudo ifup eth0
)))


I was also facing shutdown and Restart problem with Internet problem.it hang when i try to shutdown or restart ubuntu then i use this command and this commands work fine.but dont know that is it create any harm to my wired internet connection.
((((
"Open the file /etc/init.d/alsa-utils with the following command:
sudo gedit /etc/init.d/alsa-utils
The file opens in Gedit and around the line 353 you'll find the instruction "stop)". Below this instruction you should add these two instructions:
ifconfig wlan0 down
ifconfig eth0 down
So, the file should be this way:
stop)
ifconfig wlan0 down
ifconfig eth0 down
EXITSTATUS=0
After doing this, save the file, close it and restart or shutdown Ubuntu and verify if the problem continues."
))))

Please do help me to solve my problem ....and one more thing i like to tell that it is my 2nd time that i am installing ubuntu at my 1st install also net work for 2 or 3 days then face the same problem that show wired network connected and ifconfig etc commands work fine but net not working.
takecare All

---

### Post by whoop on 2009-02-18
Are you using a router? can you ping the router. can you ping any other ip outside of your lan. If you can you dns server settings are wrong or outdated.

---

### Post by mohsinhussain on 2009-02-19
I am On Lan Network,I can ping my ip which is locally 10.100.78.88 and server ip which is 10.100.50.11 and i can also ping 127.0.0.1 but if i try to ping [www.gooogle.com](www.gooogle.com) then it give an error host not found,my firefox also not working now,few days back internet was working fine firefox too....do reply guyz...tc

---

### Post by superprash2003 on 2009-02-19
in windows do you require a dialer to connect to the internet??

---

### Post by mohsinhussain on 2009-02-19
No..its direct connected...I just login to windows and start surf website msn etc .......I was same in ubuntu before this problem,login to ubunty and start surfing internet but not now.may be ubuntu 8.10 having some network bugs in it...or i read some where on internet that network manager 0.7 having some problem with it.Yes I have install vmware server 2 on it but i dont think so it create any problem to my wired connection.

---

### Post by hobo on 2009-02-19
Try pinging 75.125.67.100  (google.com)

---

### Post by superprash2003 on 2009-02-20
is your server a windows/linux machine running ICS?? or a router?

---

### Post by suyashpandit on 2010-10-28
Having same problem on Ubuntu 10 LTS

I found this thread on search engine, but cant find solution, I am still finding solution.

---

