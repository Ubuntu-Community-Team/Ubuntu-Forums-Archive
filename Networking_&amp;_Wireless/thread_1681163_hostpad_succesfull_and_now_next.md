---
title: "hostpad succesfull and now next ?"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by phoenixpb on 2011-02-03
what i want to do is 

client <--> wlan0 <--> computer <--> eth0 <--> rooter <--> internet 

i have 2 network connections
eth0 wired connected to internet
wlan0 wireless (work fine)

i have installed hostapd with madwifi and so on
oki

when i run hostapd the clients see the hot spot oki
clients connect with wpa oki

network manager run at demand not automatic (keep it for Internet help)
now I'm a bit lost [IMG]http://forums.fedoraforum.org//forum/images/smilies/smile.gif[/IMG]

what do i need is wlan0 give to  the client an ip (optional i can set a static ip in the android phone)
forward the traffic of wlan0 to eth0

and can someone point me to the good direction
create a bridge between wlan0 and eth0 ?
 masquerade?

as i have said hostapd work (was the big thing to start) i see the hotspot in my android phone

if someone can give the right direction with some steps
perhaps using something else than hostapd ?

thanks

Edit :
phoenix@styx:/etc/hostapd$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Master  Frequency:2.437 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          
mon.wlan0  IEEE 802.11bg  Mode:Monitor  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off

---

### Post by AlexQM on 2011-02-04
You'll need to use bridge-utils
```
sudo apt-get install bridge-utils
```
Can you show me your example of your hostapd config file? I'm trying to do the same as you but haven't got that part right! The bridging part I've got!

Alex

---

### Post by phoenixpb on 2011-02-04
hostapd.conf

interface=wlan0
bridge=br0
driver=nl80211
logger_stdout=-1
logger_stdout_level=2
ssid=phoenix
hw_mode=g
channel=6
auth_algs=3
max_num_sta=5
wpa=2
wpa_passphrase=what_you_want
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
rsn_pairwise=CCMP

i have installed bridge-utils already

---

### Post by AlexQM on 2011-02-04
Thanks for that, I should be able to configure mine in a similar way. To use bridge-utils:
```
brctl addbr br0
brctl addif br0 X
brctl addif br0 eth0
ifconfig br0 <IP> up
echo 1 > /proc/sys/net/ipv4/ip_forward

```

Replace X with your wifi interface, eg wlan0 or ath0 depending on what driver/chipset you're using. Have you got you're wifi interface into Managed mode or Access Point mode?


Alex

---

### Post by phoenixpb on 2011-02-05
in master mode with the correct drivers
in which files do you put these commands ? (i knew these commands) to have your bridge at boot ?

how do you resolve that you loose internet on the server ?

---

### Post by AlexQM on 2011-02-05
I haven't got these commands in a .conf file as I don't want them to run at every boot so I'll put the whole lot of these steps in a script that I can run as and when I need it (for use when I'm at my studio). 
I haven't been able to get the AP to bridge correctly to my router to obtain an IP address from it. I'm going to be setting up hostapd now. I'll post back when I've got it set up

Alex

---

### Post by AlexQM on 2011-02-05
```
    iwconfig ath0 essid "MY-WIRELESS"
    iwpriv ath0 mode 3
    brctl addbr br0
    brctl addif br0 eth0
    brctl addif br0 ath0
    brctl setfd br0 1
    ifconfig ath0 up
    ifconfig eth0 up
    ifconfig br0 192.168.0.2 up
    hostapd -dd /etc/hostapd.conf 
```

That should do what you need it to do, there are plenty of pages I've seen that will show you how to have this ready at boot up.

You'll need to replace "MY-WIRELESS" with whatever you have in your hostapd.conf file.
The IP address that you give br0 will be the IP address that your eth0 has before you start this process.
I have successfully used the code above and have got it working!

Alex

---

