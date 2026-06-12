---
title: "Ics on ubntu wont work, please help"
date: 2009-10-11
forum: Networking &amp; Wireless
---

### Post by thingy87654321 on 2009-10-11
i was following the guide from [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) to set up ics on my ibm thinkpad t42p so i can share the internet it recives to my desktop, my wifi interface is eth1 and my ethernet interface is eth0

i want to be able to use ics using wifi (wifi to internet enabled router) to a desktop pc using ethernet, i have a router on the desktop so that way i dont need to use a crossover cable. so i was follwing the guide and i did this in two different terminal windows (half in one and half in the other) here is what i did

(and yes i had trouble figuring out the sudo -s command to gain root privilages because i havent used ubuntu in a while)

chris@chris-aouate-laptop:~$ sudo ifconfig eth1 192.168.2.10
sudo: unable to resolve host chris-aouate-laptop
[sudo] password for chris: 
chris@chris-aouate-laptop:~$ ifconfig eth1 192.168.2.10
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
chris@chris-aouate-laptop:~$ sudo
sudo: unable to resolve host chris-aouate-laptop
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
chris@chris-aouate-laptop:~$ sudo -h
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
chris@chris-aouate-laptop:~$ sudo -s
sudo: unable to resolve host chris-aouate-laptop
root@chris-aouate-laptop:~# ifconfig eth1 192.168.2.10
root@chris-aouate-laptop:~# sudo iptables -A FORWARD -i eth1 -o eth0 -s 192.168.2.11/24 -m conntrack --ctstate NEW -j ACCEPT
sudo: unable to resolve host chris-aouate-laptop
root@chris-aouate-laptop:~# sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo: unable to resolve host chris-aouate-laptop
root@chris-aouate-laptop:~# sudo iptables -A POSTROUTING -t nat -j MASQUERAD
sudo: unable to resolve host chris-aouate-laptop
iptables v1.4.1.1: Couldn't load target `MASQUERAD':/lib/xtables/libipt_MASQUERAD.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
root@chris-aouate-laptop:~# iptables -A POSTROUTING -t nat -j MASQUERADE 
root@chris-aouate-laptop:~# sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward

and i messed up on the "sudo iptables -A POSTROUTING -t nat -j MASQUERADE" line

and here is the other half of this 

chris@chris-aouate-laptop:~$ sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"sudo: unable to resolve host chris-aouate-laptop
[sudo] password for chris: 
chris@chris-aouate-laptop:~$ sudo -s
sudo: unable to resolve host chris-aouate-laptop
root@chris-aouate-laptop:~# gedit /etc/sysctl.conf
root@chris-aouate-laptop:~# cp /etc/resolv.conf /etc/resolv.conf.backup
root@chris-aouate-laptop:~# nano /etc/dhcp3/dhclient.conf
root@chris-aouate-laptop:~# sudo /etc/init.d/networking restart
sudo: unable to resolve host chris-aouate-laptop
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth1=eth1.
                                                                         [ OK ]
root@chris-aouate-laptop:~# sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT


sudo: unable to resolve host chris-aouate-laptop
root@chris-aouate-laptop:~# 
root@chris-aouate-laptop:~# 
root@chris-aouate-laptop:~# sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

sudo: unable to resolve host chris-aouate-laptop
root@chris-aouate-laptop:~# 
root@chris-aouate-laptop:~# sudo iptables -A POSTROUTING -t nat -j MASQUERADE 
sudo: unable to resolve host chris-aouate-laptop
root@chris-aouate-laptop:~# sudo /etc/init.d/networking stop
sudo: unable to resolve host chris-aouate-laptop
 * Deconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
Ignoring unknown interface eth1=eth1.
                                                                         [ OK ]
root@chris-aouate-laptop:~# sudo ifconfig eth0 192.168.0.100
sudo: unable to resolve host chris-aouate-laptop
root@chris-aouate-laptop:~# sudo /etc/init.d/networking restart
sudo: unable to resolve host chris-aouate-laptop
 * Reconfiguring network interfaces...                                   [ OK ] 
root@chris-aouate-laptop:~# 


i have tried firestarter and it didnt work well, when i plug in my ethernet cabele (connected from my laptop to the uplink port on my router (it works fine this way when i am using ics over windows)) and then ubuntu connectes to the ethernet connection and ignores the wifi connection and then i cant access internet and ics isnt working, please help

---

