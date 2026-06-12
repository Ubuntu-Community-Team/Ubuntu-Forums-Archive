---
title: "Get Wireless WPA2 working with command line only"
date: 2011-07-06
forum: Networking &amp; Wireless
---

### Post by marjiea1 on 2011-07-06
I wanted to run a little media server in my house, shared with my laptop only, so I could free up space on my laptop drive.  

I took one of my Linux boxes out of my render farm and loaded up a minimal install, command line only of Ubuntu Lucid from the mini ISO (32 bit).  I had to plug in a lan cable to install, but I wanted to move my box back out to the "farm" that doesn't have wired access to my intranet.

After much research, trial and error, this is what worked for me.  My wireless card uses an Atheros AR5001X+ chip, and it works with the desktop cd out of the box.  I found the "just works" desktop install uses the ath5k driver that is now included in Lucid, but I'm not using a desktop or window manager.  I haven't tried this on server version, if you do, let others know what you had to install to get it to work.

The things I do tell you about, I instruct you as if you are a newbie, however I have left out some things that users should know or be able to lookup easily, like if you want a static address instead of using dhcp.  You may not need all of the steps or you may have to do more research and troubleshooting.

Find your wireless card (you may need to lookup what to do if it is not recognized at all)

List all pci devices, only show network devices (-v verbose, -vv very verbose):
>>lspci &#8211;vv | grep Network

List all hardware (| less lets you pause at each page &#8211; arrow keys, page down/up to navigate, q to quit)
>>lshw | less

(If your modem is usb, learn about the lsusb command)

Check to see if network card is detected so you don't have to load a driver (where wlan0 is your card&#8217;s interface id found in previous step):
>>ifconfig wlan0

To load a driver, that is already on your system (my card was detected and the correct driver loaded from the kernel):
>>sudo modprobe drivername

If you forget to type sudo and get errors, then type:
>>sudo !!
which will execute the last command with sudo in front of it.

(you can learn about loading other drivers like broadcom bcm43xx at help.ubuntu.com)

List your wireless card&#8217;s device id:
>>iwconfig

if the command is not found (not in mini.iso) then you will need to install the wireless tools:
>> sudo apt-get install wireless-tools

If your router uses WPA or WPA2 security then install wpa supplicant:
>> sudo apt-get install wpasupplicant

(my wireless will never connect if my lan cable is plugged in, so after installing you may need to unplug your network cable too)

Scan for networks:
>>sudo iwlist scanning

If no results for your interface then enable device (and rescan):

>>sudo ip link set wlan0 up

Add your network information to wpa supplicant configuration file (where santa is the name of the network you are trying to connect to and hohohohohoho is the password for that network) (all 3 commands):
>>sudo su

root>>wpa_passphrase  santa hohohohohoho >> /etc/wpa_supplicant.conf

root>>exit

Edit the file you just created/appended:
>>sudo nano /etc/wpa_supplicant.conf
<Add to the top:>
Ctrl_interface=/var/run/wpa_supplicant

<although your wireless may work just fine now, mine kept timing out, so to make WPA2 connect faster, I added this inside network={} below ssid and above psk>
	scan_ssid=1
	proto=RSN
	key_mgmt=WPA-PSK
	pairwise=CCMP
	group=CCMP

<CTRL-O> <ENTER> to save the changes to the file
<CTRL-X> to exit the editor

If you are using WPA instead of WPA2, look up the wpa_supplicant.conf examples and find what you need (WPA instead of RSN, TKIP instead of CCMP or both, etc.)

Run wpa_supplicant:
>>sudo wpa_supplicant &#8211;D wext &#8211;i wlan0 &#8211;c/etc/wpa_supplicant.conf

Should see WPA: Key negotiation completed&#8230; CTRL-EVENT-CONNECTED
<CTRL-C> (stops the process running in the foreground of the command line/terminal)

Run wpa_supplicant in the background (up arrow, right arrow to end, add &#8211;B):
>>sudo wpa_supplicant &#8211;D wext &#8211;i wlan0 &#8211;c/etc/wpa_supplicant.conf -B

Wait a bit, then check for connection (mine wouldn't connect on the second try, I had to reboot, enable my device, then go straight to running in the background):
>>ip addr

Should see wlan0:&#8230; inet 192.168&#8230;
if so ping your router (you will need to know its ip address):
>>ping 192.168.0.1 &#8211;c 4 

Should see less than 100% packet loss

and/or ping the web:
>>ping google.com &#8211;c4

Network unreachable on internet? Do you have the correct gateway (your router number or isp gateway &#8211; all zeros indicates the default gateway)?  Any of these commands should tell you:

>>sudo netstat &#8211;nr
>>sudo route
>>/sbin/route -n

If you still can't connect to the internet, but are connected to your lan, with all zeroes for your gateway, try (192.168.0.1 should be your router IP address or your internet provider's gateway - which they would have given you if needed):
>>sudo route add default gw 192.168.0.1 wlan0

Check for connection again, ping, etc.  It should be working now.

Once you have it working, get your wireless connection to come up automatically on boot (auto brings up the interface, iface says it will get an ip assigned from the dhcp server):
>>sudo nano /etc/network/interfaces
<Add to the bottom:>

auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant &#8211;Dwext &#8211;iwlan0 &#8211;c/etc/wpa_supplicant.conf &#8211;B
post-down killall &#8211;q wpa_supplicant

<CTRL-O> <ENTER> to save the changes to the file
<CTRL-X> to exit the editor

Reboot:
>>sudo shutdown &#8211;r now

After you have logged in, check for an ip address:
>>ip addr

If you have no typos in your files, you should now have wireless internet access every time you boot up.

---

### Post by ebs16 on 2011-09-03
Thanks for the guide! I am having trouble establishing a connection to my router. First, here are the relevant specs:

Network: 802.11n WPA2 PSK TKIP (DDWRT v24-sp2)
Wifi card: 802.11g USB Ralink RT2501/RT2573
OS: Ubuntu Server 11.04 x86

I can get as far as [FONT="Courier New"]sudo wpa_supplicant –D wext –i wlan0 –c/etc/wpa_supplicant.conf -B[/FONT]. My wireless AP shows that my computer is connected, but the computer has no connectivity or IP address. Pings yield no results. [FONT="Courier New"]sudo netstat –nr[/FONT] yields no gateways. [FONT="Courier New"]sudo route add default gw 192.168.0.1 wlan0[/FONT] returns [FONT="Courier New"]SIOCADDRT: No such process[/FONT].

Any ideas as to why I can't connect?

Thanks!

---

### Post by marjiea1 on 2012-01-12
You are using the gateway ip address 192.168.0.1, this is the default for D-link routers (what I have), but other brands often use 192.168.1.1 (so make sure this is correct for your router/lan.)

---

### Post by ghis on 2013-02-12
perfect!

---

### Post by towme on 2013-09-12
First of all thanks guys, this thread helped me configure my wireless card. Only two more clarifications, which weren't straight forward for me at first.

these values:

scan_ssid=1
	proto=RSN
	key_mgmt=WPA-PSK
	pairwise=CCMP
	group=CCMP

are NOT the same for everyone.
issue 'iwlist wlan0 scan', and it should find your AP a list the above values. COPY THOSE and NOT THESE to wpa_supplicant.conf !!!
also set channel with iwconfig to right value.

if you wish to get up your wireless interface automatically without network-manager or wicd after a reboot then you have to add the following to rc.local
wpa_supplicant &#8211;D wext &#8211;i wlan0 &#8211;c/etc/wpa_supplicant.conf -B
sleep 5 #or more if your card needs more time to "wake up"
dhclient wlan0 #if your wlan0 interfaces is dynamic adressed

---

