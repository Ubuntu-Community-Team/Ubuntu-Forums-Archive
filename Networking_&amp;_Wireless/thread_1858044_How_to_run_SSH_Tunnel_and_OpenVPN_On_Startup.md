---
title: "How to run SSH Tunnel and OpenVPN On Startup?"
date: 2011-10-11
forum: Networking &amp; Wireless
---

### Post by xinapse on 2011-10-11
Hi i am in a situation where i need to tunnel openvpn through SSH for VPN to work due to port restrictions. This is all working fine , however it is tedious every boot to have to connect to SSH and openvpn everytime.

So can anyone help me with what the commands would be to put in a SH file or how i would do it?

Currently i have

ssh -L port:host:port user@host &
sudo openvpn userconf &
#sudo rm /etc/resolv.conf
#echo "nameserver 8.8.8.8" > /etc/resolv.conf

However SSH and openvpn do not run at the same time which is needed for it to work.

---

### Post by Lars Noodén on 2011-10-11
One way is to write a script for [upstart](http://manpages.ubuntu.com/manpages/natty/en/man8/initctl.8.html) for SSH and for the VPN.

---

### Post by vajorie on 2011-10-11
You could also put them in /etc/rc.local which is executed on every boot. 

because it is executed on boot, you'd have to start with a sleep command so that network interfaces have time to come up. Count how many seconds it takes for your computer to boot fully, then put that number to the begining of rc.local as such

```
sleep 100  #this is in seconds
your commands go here
```

rc.local is executed as root, so you would have to provide full paths to configuration files as well as public key location for your session in there. 

lastly, do not reboot with a new rc.local file without verifying that it works and does not hang / crash / burn. just execute your file and watch what happens, and if executes without causing problems (i.e. no output is good output), check whether it does what you want it to do

```
sudo /etc/rc.local
```

---

