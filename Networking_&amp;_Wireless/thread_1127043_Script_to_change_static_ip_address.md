---
title: "Script to change static ip address"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by KayGenz on 2009-04-16
dear all..

i usually work with several static ip address, its so boring to change my ip address manually,doing ifconfig eth0 down and up,everytime

could you help me write a (shell/bash??) script that can be use to change ip address,subnet mask,Gateway, and dns? automatically

i want that script executed with double click.

thanks for all the advice

---

### Post by celthunder on 2009-04-16
#!/bin/sh
ifconfig eth0 down;
ifconfig eth0 <ip> <subnet>;
ifconfig eth0 up
route add default gw <gatewayip>;
echo nameserver <dnsserver> > /etc/resolv.conf; 

make however many scripts you need...pretty much same as in the shell with the line added on top to call sh so you can chmod +x it and run it.

---

### Post by KayGenz on 2009-04-16
thanks for the quick response celthunder.. 

i try your scripct.. i copy paste from the forum and change it as i want like this :

#!/bin/sh
ifconfig eth0 down;
ifconfig eth0 192.168.1.229 255.255.255.0;
ifconfig eth0 up
route add default gw 192.168.1.1;
echo nameserver 192.168.1.1 > /etc/resolv.conf; 

save it as 229.sh and chmod +x to that file.. but when i double click it just flicker, and when i check the ip address with ifconfig, it still the same ip before..

when i try to excuted it using terminal with sudo, it comes with this following error

kaygenz@kaygenz-laptop:~/Documents$ sh 229.sh 
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCADDRT: Operation not permitted
229.sh: 6: cannot create /etc/resolv.conf: Permission denied
kaygenz@kaygenz-laptop:~/Documents$ sudo sh 229.sh 
[sudo] password for kaygenz: 
SIOCSIFADDR: Invalid argument



could you help me celthunder, or the other.. any feedback is appriciated :)

thanks

---

### Post by celthunder on 2009-04-16
try sudo before each line 
sudo ifconfig eth0 down  
sudo ifconfig eth0 <ip> 
etc.

---

### Post by KayGenz on 2009-04-16
Thanks you celthunder for still being with me

i change my script to like this :


#!/bin/sh
sudo ifconfig eth0 down;
sudo ifconfig eth0 192.168.1.229 24;
sudo ifconfig eth0 up
sudo route add default gw 192.168.1.1;
sudo echo nameserver 192.168.1.1 > /etc/resolv.conf; 

i try to executed again in terminal if it got some error, and the output is like this :

kaygenz@kaygenz-laptop:~/Documents$ sh 229.sh
SIOCADDRT: No such process
229.sh: 6: cannot create /etc/resolv.conf: Permission denied

when i try to use sudo to executed the file, it comes like this :

kaygenz@kaygenz-laptop:~/Documents$ sudo sh 229.sh
SIOCADDRT: No such process


and the result my ip is still the same... :(

any advice or i misconfigure something ??

---

### Post by celthunder on 2009-04-16
Well I don't see why that doesn't work but try just making multiple /etc/network/interfaces files and just copying the one you need to /etc/network/interface and then have a file like the one above with just #!/bin/sh ifdown eth0 ifup eth0

---

### Post by KayGenz on 2009-04-16
thanks for your reply celthunder, 

actually now use wicd, it look like make problem solved...

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

thanks again celthunder for your warm help :)

:popcorn:

---

