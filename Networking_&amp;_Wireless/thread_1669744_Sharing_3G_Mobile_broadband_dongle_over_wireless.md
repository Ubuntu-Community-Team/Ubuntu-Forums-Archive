---
title: "Sharing 3G Mobile broadband dongle over wireless"
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by markturnip on 2011-01-18
Hello, I had previously been sharing my ethernet connection over wireless using Hostapd & dnsmasq on my headless server as this tutorial shows: [here]("http://ubuntuforums.org/showthread.php?t=716192") which had been working fine. 

I now wish to share my USB mobile broadband over the wireless. I using a ZTE MF112.

I was able to get the connection working using the application wvdial.

- Firstly I had to create a hard link between /dev/gsmodem & /dev/modem
- wvdial then made a new connection ppp0 which would work for internet access.

Changing the interfaces to have the br0 port like so:

```
iface br0 inet static
       address 192.168.1.1
       network 192.168.1.0
       netmask 255.255.255.0
       broadcast 192.168.1.255
       bridge-ports eth1 ppp0 wlan0 
```

Flushing the IPTables & then adding:

```
iptables -A FORWARD -i br0 -s 192.168.1.0/255.255.255.0 -j ACCEPT
iptables -A FORWARD -i ppp0 -d 192.168.1.0/255.255.255.0 -j ACCEPT
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

```

Doing so works fine, but I'm not entirely sure how to make this all automated. I could try making a script to launch, but I don't have a huge amount of experience writing scripts. 

I wonder if anyone can offer a better solution? Is wvdial the best application to use?
Keeping in mind I'm using a headless server. 

One note: I use Squeezebox server & the scrobbling didn't seem to be able to connect to last.fm. Do I need to specify which connection Squeezebox uses?

Any advice is really appreciated!

MT

---

### Post by markturnip on 2011-01-18
I guess all my script might need to be is:

```
wvdial

iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -t raw -F
iptables -t raw -X

iptables -A FORWARD -i br0 -s 192.168.1.0/255.255.255.0 -j ACCEPT
iptables -A FORWARD -i ppp0 -d 192.168.1.0/255.255.255.0 -j ACCEPT
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

echo 1 > /proc/sys/net/ipv4/ip_forward
```

Perhaps wrapping it in start & stop commands. 

My question is, how is it possible to make a script that will run as a daemon & won't quit once I stop terminal from my machine?

I have a feeling if I try the above the iptables commands will never get called as the initial wvdial command will still be feeding back results? In which case would I have to make wvdial another script daemon that gets called, wait a few seconds & then call the iptables commands?

Thanks. 

MT

---

### Post by alexfish on 2011-01-18
hi

if calling wvdial direct then probably need separate script 

to execute , possible check to see if pppd is running

a=`pidof pppd`
if [ $a > 0 ]
then
echo " ppp up "
exec <yoursript>
else
echo "ppp down"
fi

or

a=`pidof pppd`
if [ $a > 0 ]
then
echo " ppp up "
< your script bits here>  

else
echo " ppp down"
exit
fi


could possibly wrap with loop and then exit loop when pppd is up

added:

could try ppp . the call "pon myisp"  pon does  not tie up the terminal so the script can be self contained

---

