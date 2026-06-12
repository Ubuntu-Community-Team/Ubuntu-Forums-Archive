---
title: "Google, Gaim, Xchat do not load + WPA ing"
date: 2005-12-31
forum: Networking &amp; Wireless
---

### Post by deadly_paddooo on 2005-12-31
I have actually two main questions

Lemme explain my position, I m a newbie and I like terminal (stuff)

1) Well, I finally connected Ubuntu to internet via wireless using WEP. Actually I have been trying for days to connect it to my original WPA however, all i tried and did not work. Some sites I went to

\[https://wiki.ubuntu.com/WPAHowto\](https://wiki.ubuntu.com/WPAHowto\)
\[http://www.fmepnet.org/debian_wpa.html\](http://www.fmepnet.org/debian_wpa.html\)
[http://ubuntuforums.org/showthread.php?t=90450](http://ubuntuforums.org/showthread.php?t=90450)

Googled it plenty of times! no success

if it makes not sense i basically get this
ioctlSIOCSIWPMKSA: No such device
ioctlSIOCSIWENCODEEXT No such device
ioctlSIOCSIWENCODEEXT No such device
ioctlSIOCSIWENCODEEXT No such device
ioctlSIOCSIWENCODEEXT No such device
Trying to associate with xx xx xx xx xx xx (SSID='zzzzz' freq=1234 MHz)
Associated with xx xx xx xx xx xx
WPA: Key negotiation completed with xx xx xx xx xx xx PTK=TKIP GTK=TKIP
CTRL-EVENT-CONNECTED - Connection to xx xx xx xx xx xx completed (auth)

taken from [http://ubuntuforums.org/showthread.php?t=99845&highlight=wireless+wpa](http://ubuntuforums.org/showthread.php?t=99845&highlight=wireless+wpa)


From the first site, i get the following from terminal on doing this

See Attached txt file, this forum was considering "[]" tags as img tags so indicating i have 45 images attached!!!

Hope that it is still readable, Darn Notepad took all the breaks out when i transfered it to windows. I also changed some code to 000/0 (shuld been 00) or xx or yy.

Then I go to firefox and open google.com fails.
where could the problem be here?

2) Then I decided to go for WEP as the System-Networking had something similar there. So I got connected to internet, downloaded wifi radar from apt-get GUI, worked fine.
On firefox opened ubuntu.com, mozilla.com worked fine, great.
But google.com stucks at "Connecting to the server..." and then timed out. 
Also GAIM, XChat cannot connect to the internet. 
My router shows the Ubuntu system on the Active user list (w/ user unknown). 
Do we have to do some additional steps to open sites after we get connected?

3) I have to do "$ sudo modprobe ndiswrapper" to start it each time. How can  i get it to start at booting? Also In general how can we get something to startup at booting?

Thanx

Whoa!!! It took me about one hour to post this thread, I had 20 images (whoa!!!!!!) It'as not until after one hour of messin' i realized the script was takin' a mac address of type xx_xx_xx_xx_xx_xx (fill in blanks w/ a colon) as similies, cheez, hence i had to remove all those from the attached output from terminal and also to attach a txt file!

---

### Post by firecat53 on 2005-12-31
Try adding the -w flag to your wpa_supplicant command.

Also, search for some of my other posts regarding wpa_supplicant. I've put my /etc/network/interfaces and wpa_supplicant.conf in them, so just check and make sure they're similar. 

Also make sure (ps -e) that you don't have any other instances of wpa_supplicant running before you start it up.

Good luck!

Scott

---

### Post by deadly_paddooo on 2005-12-31
Certainly, I will be trying that.

---

### Post by deadly_paddooo on 2006-01-01
Tried all of that
Still not working
Changed the /etc/network/interfaces rebooted

I have followed exactly the steps by different post, none worked
And your posts too.

What is (ps -e)?

EDIT: Oh! kinda similar to jobs cmd (read in a book about red hat) Dun worry about that
EDIT: I tried ipwconfig (just for fun) and it tells me its kinda like connected to my router w/ a bit rate of 36 mb/s.
I have the feelin' that wpasupplicant connects to the router, however the other softwares (like firefox) still see it as no connection. Can it go like that?

---

### Post by Lambert on 2006-01-01
Don't use or know that much about wpa but if it seems your connected can you post output of these commands?

arp -a
iwconfig
ifconfig
route -n


static or dhcp network wetup?

can you ping router?
ping ______________ 
if yes try to ping site with ip
ping 82.211.81.130
if yes the ping via host name
ping [www.ubuntulinux.com](www.ubuntulinux.com)

---

### Post by deadly_paddooo on 2006-01-01
I am giving my wpasupplicant and wpa_supplicant.conf files!
# /etc/default/wpasupplicant<br><br>


# WARNING! Make sure you have a configuration file!<br><br>

ENABLED=1<br><br>

# Useful flags:<br>
#  -D <driver>		Wireless drive, typically optional.<br>
#  -i <ifname>		Interface<br>
#  -c <config file>	Configuration file<br>
#  -d 			Debugging (-dd for more)<br>
#  -w			Wait for interface to come up<br>
<br>
# See the manual page wpa_supplicant(1) for more options and information.<br>
#OPTIONS="-D ndiswrapper -i wlan0 -c /etc/wpa_supplicant.conf -w"<br>
<br>
OPTIONS="-i wlan0 -D ndiswrapper -c /etc/wpa_supplicant.conf -w"<br>
<br>
# EXAMPLES:<br>
<br>
# OPTIONS="-i wlan0 -D hostap -c /etc/wpa_supplicant.conf"<br>
# OPTIONS="-i ath0 -D madwifi -c /etc/wpa_supplicant.conf"<br>
<br>

#END WPASUPPLICANT FILE @ /ETC/DEFAULT/WPASUPPLICANT



#START WPASUPPLICANT CONFIG FILE @ /ETC/WPA_SUPPLICANT.CONF
# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see <
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete<
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
#network={
#        ssid=""
#        key_mgmt=NONE
#}

network={
        ssid="NetworkSSID"
	#scan_ssid=1
        proto=WPA
	key_mgmt=WPA-PSK
        psk=0004404059f0898b0808c88888e80808098908
}
#END WPASUPPLICANT CONFIG FILE @ /ETC/WPA_SUPPLICANT.CONF

OUTPUT DONE WHEN WPA_CLI
> status
bssid=00:00:00:00:00:00
ssid=NetworkSSID
pairwise_cipher=TKIP
group_cipher=TKIP
key_mgmt=WPA-PSK
wpa_state=COMPLETED
Supplicant PAE state=AUTHENTICATED
suppPortStatus=Authorized
EAP state=SUCCESS

COMMAND 
paramsingh@paddooo:~$ arp -a -dd
arp: need host name

paramsingh@paddooo:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"NetworkSSID"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:36 Mb/s   Sensitivity=-200 dBm
          RTS thr:2346 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-77 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:1273   Missed beacon:0

paramsingh@paddooo:~$
paramsingh@paddooo:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15773 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15773 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1040251 (1015.8 KiB)  TX bytes:1040251 (1015.8 KiB)

wlan0    Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          inet6 addr: fe80::240:f4ff:fed3:7e78/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:18131 (17.7 KiB)  TX bytes:2549 (2.4 KiB)
          Memory:42200000-4220ffff

paramsingh@paddooo:~$
paramsingh@paddooo:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref   
Use Iface
paramsingh@paddooo:~$

*****************END
P.S. I changed SSID, Network key, and Mac addresses, hope they don't cause any problems! andn don't worry about <br> tags I added them b'coz i transfered file from linux gedit to win notepad and no breaks remain, so i tagged them.

With all this, I think it might be apparent that I am kinda connected but really disconnected (from the errors in TX packets etc).
Therefore, I could not ping my router or any other host.
Also I have dhcp Network setup.

Where is the problem?

---

### Post by Lambert on 2006-01-01
>  wlan0     IEEE 802.11b  ESSID:"NetworkSSID"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:00:00:00:00:00

this tells me you're not connected/associated to your router. If you were you'd have the mac address of the router after Access Point:

Just briefly looking at what links you posted I'd suggest starting over from scratch setting up wpa. Look at these links as these are specific to ndiswrapper.

[https://wiki.ubuntu.com/forum/hardware/ndiswrapperWithWPA](https://wiki.ubuntu.com/forum/hardware/ndiswrapperWithWPA)

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/WPA](http://ndiswrapper.sourceforge.net/mediawiki/index.php/WPA)

---

### Post by deadly_paddooo on 2006-01-01
[QUOTE=Lambert]this tells me you're not connected/associated to your router. If you were you'd have the mac address of the router after Access Point:

[/QUOTE]

Sorry, I had the mac address of the router, i made all mac addresses to 00,
I did not know if it is not connccted mac address is 00:00...

do ya want the original address?

If that's the issue, then 00 mac address could be potential bug b'coz if one is not connected there should be no mac address, just say not connected. Kinda like arrays!

EDIT: Certainly, I will be checking out the links provided! Thanks

---

### Post by Lambert on 2006-01-01
No, mac address is not neccessary and now I see in your post where you say you changed them.

1. have you tried to *sudo dhclient wlan0 *after associating?

2. You can also try to set a static ip just to see if you can ping

 ```
sudo ifconfig wlan0 192.168.0.254 wlan0
```
```
sudo route add default gw 192.168.0.1 wlan0
```

change 192.168.0.1 to the ip of your router if different then what I wrote.

then try to ping

ping -c 4 127.0.0.1
ping -c 4 192.168.0.254
ping -c 4 192.168.0.1
ping -c 4 82.211.81.130

any results?

as posted previously, not that knowledgeable with wpa so hopefully somebody else can see what's wrong and help.

And you can find help in other areas that are specific to ndiswrapper if you don't find it here.

[http://ndiswrapper.sourceforge.net/support.html](http://ndiswrapper.sourceforge.net/support.html)

---

### Post by deadly_paddooo on 2006-01-02
[QUOTE=Lambert]No, mac address is not neccessary and now I see in your post where you say you changed them.

1. have you tried to *sudo dhclient wlan0 *after associating?
[/QUOTE]

Thanks, that was it!
I did not had to do anything, it just gave configured me an ip address, nice!

However, I am still not able to open some sites such as [http://mail.yahoo.com](http://mail.yahoo.com), or [http://www.google.com](http://www.google.com), However It opened centralops.net where i took google and yahoo's ip and pinged them. Ping was a success!
Firefox's returns with time out. Also it easily opened ubuntuforums.org. Neither of Xchat nor Gaim log on, or I dunno how to configure them?

EDIT: I might know the issue, it could be ipv6. I had similar problems on windows until i uninstalled ipv6. Probably, my router is not configured for ipv6. So I might try searching for thread concerning ipv6.


Thank you for your help, its great with WPA, that was why I installed Ubuntu b'coz i could not configure wpa on windows.
Happy New Year
:)

---

### Post by Lambert on 2006-01-02
[http://www.ubuntuforums.org/showthread.php?t=87798&highlight=ipv6](http://www.ubuntuforums.org/showthread.php?t=87798&highlight=ipv6)

Should automatically start dhcp when interface is brought up. You can post your /etc/network/interfaces file and someone could verify there's something not missing there so you don't have to run the dhclient wlan0 command.

---

### Post by deadly_paddooo on 2006-01-03
I have to do following to start my wireless,

first to start the ndiswrapper, ```
 sudo modprobe ndiswrapper 
```
Then I restart the network  ```
 sudo invoke-rc.d networking restart 
```
Then I have to do dhclient ```
 sudo dhclient wlan0 
```

After all this I am on the network
How can i make this automated? OR
I basically followed the HOW TO: on WPA to set up WPA [http://www.ubuntuforums.org/showthread.php?t=90450&highlight=wpa](http://www.ubuntuforums.org/showthread.php?t=90450&highlight=wpa)


What changes in my /etc/network/interfaces file which is here?

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
auto wlan0
iface wlan0 inet dhcp
wireless-essid WAHEGURU
pre-up /usr/local/sbin/wpa_supplicant -wB -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -p wpa_supplicant

#End of file

EDIT: GUESS WHAT?
I think I can guide you on the problem, so what i found out?
Well, i shuld say how can i bring ```
 sudo modprobe ndiswrapper 
``` to start on the boot?
B'coz, as this code has not been run yet, there's no wlan0, so if there's no wlan0 there is no way one can get dhclient wlan0 and thus I have to run it manually!
Also this modprobe one shuld be before run before dhclient is run from interfaces file i guess!
And I don't have to restart my networking too!

---

### Post by Lambert on 2006-01-03
type this command

```
sudo ndiswrapper -m
```

This adds the module to the /etc/modprobe file which loads the ndiswrapper module automatically at boot. This should solve your problem.

---

