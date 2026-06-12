---
title: "wireless ad-hoc network and internet sharing UbuntuPC&gt;OSX"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by Bezvardis on 2006-07-02
Hello, can someone please help: I am desperately trying to do the following:
I have an Ubuntu PC desctop. That is connected to the internet via DSL cable (works fine). On that PC I have also a wireless card. I have an apple laptop. What I want to do is to
1) create a working ad-hoc network so that I can share resources between these two computers
2) share the internet connection from the desctop so that I can browse internet from my laptop (both things I can do if my desctop is running Windows)

What I managed to do so far:
I assigned both the wireless interface on Ubuntu and on my laptop static IP addresses
I changed the mode of wireless interface on Ubuntu to Ad-Hoc
I created a wireless network on the laptop and connected the wireless card on Ubuntu to the network. 
I installed Firestarter and ran the internet sharing.

Result: no internet on my Apple laptop. Yes - and for some reason at the beginning I could ping each maching back and forth, but now I cannot... Don't know the reason.

Can somebody please give me some light on this??? And show me how to work this problem out. I really like Ubuntu but this wireless connection for my laptop is essential for me since I like walking around when working. And I don't want to buy a wireless router since this system worked fine for me on Windows. Well - please save me from windows-dependancy!

---

### Post by Bezvardis on 2006-07-03
Seems that nobody has a clue as of how to resolve this issue. Meanwhile I had been searching hi and lo but with no results :cry:

---

### Post by jml on 2006-07-03
What you want to do is to set up internet connection sharing using your desktop as an "router"  I'm affraid that  I do not know how to do that, but I would like to suggest a better alternative.

I would purchase one of the readily available combination router/wireless access points.  Linksys, NetGear make them as do other companies.  They are not very expensive and offer several advantages to what you want to set up.  

For the setup.  You connect the Router/access point to the DLS modem, then plug your desktop into the router.  Set up the router to assign ip addresses via DHCP, (your router documentation will explain,) then activate and configure your desktop to connect to the router also using DHCP.  Change the administrator password on the new device as soon as you can access it from the desktop.  Keep the wireless connection unencrypted for now, and make sure ESSID broadcasting is turned on.  Then turn on your mac laptop.  If you have a Mac that utilizes OSX, the hardware should automatically detect your network and ask if you want to connect.  Once you have an unencrypted connection working, then you can add encryption, turn off the ESSID broadcast if you like and have fun.

The advantages of doing it this way are several.  You do not need to keep your Desktop computer on all the time, so its less of a target on the net.  The router acts as a basic hardware firewall presenting only its own IP address to the internet, rather than the IP addresses of your computers.  And, if you are a really causious type, you can add an additional layer of protection by configuring the router to connect to devices only by MAC addresses.  Hope that this helps.

Joe

---

### Post by Bezvardis on 2006-07-03
Thank you Joe. Probably you are right. That way it is much easier. Will keep your suggestion bookmarked and implement when I get my Linksys. I was just stubborn enough to try pushing though this idea of mine :-) Still if anybody can suggest any smart solution to it, it would be great!

---

### Post by Bezvardis on 2006-07-04
Seems that  [this thread]("http://www.live555.com/wireless/unix-base-station.html") might give an answer, but I am not sure (0-level linux/Ubuntu understanding) whether this really could work on Ubuntu and if so - how exactly. Maybe someone could comment?

---

### Post by Bezvardis on 2006-07-07
I finally resolved this problem. So what one needs to do.
 
1)find out what your network interfaces are called: system>networking. There you will see your wireless connection and ethernet connection and if they are active. My wireless is called ra0, ethernet is called eth0. If wireless says it is not active, press activate and assign a static ip address. I assigned a simple one 10.10.10.0. The network mask is assigned automatically. In "network name" write a netowrk name that you would like. I wrote "UbuNet"

2) make the wireless interface work in Ad-Hoc mode. For this open console and type:
```
sudo iwconfig ra0 mode Ad-Hoc
```
Now you can check that this did the trick by writing in console:
```
iwconfig
```
this would give me the following output:
```
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"UbuNet"
          Mode:Ad-Hoc  Frequency=2.412 GHz  Cell: 9A:8C:DA:F8:B1:D2
          Bit Rate:11 Mb/s   Tx-Power:2 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=62/100  Signal level=-64 dBm  Noise level:-193 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

3) now you have to share the internet connection. For doing that you have to perform a longer work which is described in this [thread]("http://www.ubuntuforums.org/showthread.php?t=91370&highlight=ip+forwarding") but since it needs some editorial corrections, I will copy and paste the text with my corrections here (and I write all things as it was on my computer so if any of your values differ (names of network interfaces or you choose other IP addresses, you should replace them accordingly):

1a. you need to enter the root mode. therefore type:
```
sudo -i
```

1. ( This step can be skipped because if you did the above, the static IP address 10.10.10.0 is already assigned to the wireless interface) Start by configuring the wireless internet card that interfaces to the other computers on you network:

```
ifconfig ra0 10.10.10.0
```


2. Then configure the NAT as follows:

```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

where eth0 is the network card that the Internet is coming from

```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

3. Install dnsmasq and ipmasq using apt-get:

```
apt-get install dnsmasq ipmasq
```

4. Restart dnsmasq:

```
/etc/init.d/dnsmasq restart
```

5. Reconfigure ipmasq to start after networking has been started:

```
dpkg-reconfigure ipmasq
```

6. Repeat steps 1 and 2.

7. Add the line "net.ipv4.ip_forward = 1" to /etc/sysctl.conf

```
gedit /etc/sysctl.conf
```

[this did not work like that for me, therefore you can open the file from the graphical interface. Press Alt+F2 and write in the window:

```
gksudo nautilus

```
this will open a new file browser window where you can browse as a root user and change the files. Find /etc/sysctl.conf and remove # sign (this action is called 'uncommenting' in front of the line 

net.ipv4.ip_forward = 1

To make ra0 start in Ad-Hoc mode at boot:

```
gksudo nautilus
```

Find the file /etc/network/interfaces
Open the file and find the place where it says: 

iface ra0 inet static

Change the section so that it looks like this
```
iface ra0 inet static
wireless-mode ad-hoc
address 10.10.10.0
netmask 255.0.0.0
wireless-essid UbuNet
```

8. Reboot. (Optional)

Now - this should be the end of configuration on the computer that is connected by an ethernet card to the internet directly and is sharing internet via a wireless card.

On the Macintosh that wants to connect wirelessly to the Ubunty Ad-Hoc network and wants to get internet from it:
1) Open system preferences>Network, choose Show:Airport and press tab TCP/IP
Set this to the following:
Configure IPv4: manually
IP Address: 10.10.10.1 (if you choose different static IP address for your wireless card on the first computer, the first three values of this one should co-incide, the fourth must be different)
subnet mask: 255.255.255.255 
router: 10.10.10.0 (the static IP address that was assigned to the wireless interface ra0 on the first computer)
DNS server: 10.10.10.0 (the same as above)
Search Domain: UbuNet (the one that was set at the very beginning on the first computer)

Some of these settings might not be state of the art, but this is how I got my internet shared.

That's all. Now your ra0 interface will start in ad-hoc mode every time you start your Ubuntu machine and the MacOSX machine should connect to this network automatically.

---

