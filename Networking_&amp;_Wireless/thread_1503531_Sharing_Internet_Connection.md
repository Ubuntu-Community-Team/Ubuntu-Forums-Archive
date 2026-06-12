---
title: "Sharing Internet Connection"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by kire98 on 2010-06-06
Hello all.  I am happy to report that I am very satisfied with Ubuntu.  This has been the best distro I have tried.

Now for my tricky question.  I want my Ubuntu box to share its Internet connection with the rest of my home computers.  I basically want this box to sit on the WAN side of my Linksys router while my other network devices sit on the 4 port LAN side.  I am sure you can all sympathize with why I do not want Windoze sitting directly on the Internet with only the Windoze Firewall between myself and the rest of the world.  LOL  So basically I want to use my Linksys Firewall along with my Linux box acting as a gateway.  I don't want to get into the specifics of firewall settings just yet (unless you feel we need to).  I just want enable connection sharing on the Ubuntu box, plug it into the Wan port of my Linksys and have my 2 computers and the family Wii share the connection.  Now the thing that might cause the biggest problem is my connection to the Internet is a Verizon Wireless UM175 Modem.  I don't not have access to any other broadband services so thats all I can use.  I have successfully set that connection up on my Ubuntu box using Network Manager.  In fact I am using it right now.  So I know the connection works.  I just don't know how to allow traffic from my router, through my Ubuntu Box's NIC, and out the USB Modem connection.  I feel comfortable that my router settings are correct.  I just know there is something I need to do on the Ubuntu box to make this happen.  I just don't know what that is.  Any help would be greatly appreciated.

---

### Post by Iowan on 2010-06-07
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is an ICS help page. It contains some other links - in case you need wireless...

---

### Post by kire98 on 2010-06-08
Thanks Iowan.  I will look that over.  Sorry I haven't responded until now.  I was expecting an email letting me know when someone replied.  I must not have set that option or something.  I will let you know if I have any more issues after reading that.  Thank you very much.

---

### Post by kire98 on 2010-06-08
OK I followed the guide and its still not working.  I am sure you are all shocked.  LOL

Below is what I entered and I will note the changes I made and so on.  FYI as we proceed my "internal interface" is eth0 and my external interface is the USB UM175 from Verizon Wireless which is interface ttyACM0 according to the Connection Information screen.

sudo ifconfig eth0 192.168.0.1 [COLOR=Red]##Skipped this step. I already had an IP Address of 192.168.0.2 assigned to this adapter via Network Manager.  192.168.0.1 is the IP of my Linksys Wan Interface[/COLOR]

sudo iptables -A FORWARD -i ttyACM0 -o eth0 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT [COLOR=Red]##Changed interface info to match my setup[/COLOR]
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT [COLOR=Red]##Completed as is[/COLOR]
sudo iptables -A POSTROUTING -t nat -j MASQUERADE [COLOR=Red]##Completed as is[/COLOR]

sudo iptables-save | sudo tee /etc/iptables.sav [COLOR=Red]##Completed as is[/COLOR]

*Edit rc.local
iptables-restore < /etc/iptables.sav [COLOR=Red]##Completed as is[/COLOR]

sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward" [COLOR=Red]##Completed as is[/COLOR]

*Edit /etc/sysctl.conf [COLOR=Red]##Added the following lines to the end of the file.[/COLOR] [COLOR=Red]Directions don't say where to add those two lines
[COLOR=Black]net.ipv4.conf.default.forwarding=1[/COLOR] ##Completed as is[/COLOR]
net.ipv4.conf.all.forwarding=1 [COLOR=Red]##Completed as is[/COLOR]
[COLOR=Black]
I still have a question.  What should be the gateway of my internal interface?  The instructions never say.  Should I enable "Share this connection" on that interface?  If I do that it greys out the IP settings.

Please help.  I would much appreciate it.
[/COLOR]

---

### Post by kire98 on 2010-06-16
OK.  Well it has been a while, but I found an older thread that suggested using Firestarter which worked like a dream.  Thanks all.

---

