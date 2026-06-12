---
title: "Cannot connect HTC Android phone via Internet Pass through"
date: 2010-11-12
forum: Networking &amp; Wireless
---

### Post by kavoura on 2010-11-12
I have just bought a HTC Desire Z mobile phone, running Android 2.2.

It has a feature to allow, via the USB cable, use of the Internet connection on a PC so that the phone can connect via that, rather than use the 3G or wi fi when those are not available or not wanting to use them. I want to download lots of applications without draining my 3G data allowance.

I have searched via Google, and some people have said that it just worked for them. They plugged in the phone to their Ubuntu PC and they could use the Internet on the phone.

But I cannot get it to work. I am new to Android, and still figuring out the phone. In the Settings/Wireless & Networks, there is an option for Internet Pass-through, which is trying to connect but never does. Then it comes up with a message saying:
"Unable to connect to PC" and asks me to install HTC Sync software (which is Windows only).

Is there something I need to install in Ubuntu to get it to work?

---

### Post by ahmetalpbalkan on 2010-12-18
Same problem here. Interestingly it doesnt work. Many people do it automatically... :-/

---

### Post by madjoe on 2011-01-06
Same here. I use Ubuntu Karmic on my laptop and Android Froyo on my HTC Desire Z, but I can't use Pass-throgh feature to connect my HTC on the Internet by using a wired ADSL connection from my Ubuntu. It warns me that my firewall could cause the issue, but it's the same even if I disable the firewall (sudo ufw disable) on my Ubuntu Karmic. Is there any solution for this?

---

### Post by kavoura on 2011-01-07
I ended up buying a Wireless Access Point to connect to my router and use the wi-fi on the mobile phone. It works, and is easier than setting up the Internet pass through, although I am not a big fan of using too much wireless technology.

---

### Post by ctiebs on 2011-01-19
:KSBUUUUUMP! Any new info anyone? :)

---

### Post by ttanev on 2011-01-20
> **kavoura said:**
> I ended up buying a Wireless Access Point to connect to my router and use the wi-fi on the mobile phone. It works, and is easier than setting up the Internet pass through, although I am not a big fan of using too much wireless technology.
Same for me too - the cable is the best choice for using at home and after I installed dd-wrt on my router to use the WPS button for radio on/off this is the second thing I will have to figure out - the usb internet pass trough. 
When I try to connect it with this option enabled an Auto USB Connection appears in Network Manager Applet and I guess that is the same in all your cases. Well the thing that caught my attention was that the IP that was in use was with different third component xxx.xxx.YYY.xxx and there was no gateway. 
[[IMG]http://img26.imageshack.us/img26/2304/screenshotogg.th.png[/IMG]]("http://goo.gl/bZhZc")


My network is with 192.168.**[SIZE=2]1[/SIZE]**.xxx

After about minute the connection goes down and the phone tells that it was unable to connect to the PC. 

Have to dig a little more about that rndis_host driver.

Edit: Found something, but I'm not quite sure that it will be a success :)
[http://blog.mycila.com/2010/06/reverse-usb-tethering-with-android-22.html](http://blog.mycila.com/2010/06/reverse-usb-tethering-with-android-22.html)

I tried to bridge the interfaces of eth0 and usb0 and to set the default address of my dd-wrt to be in the same x.x.99.x segment of the network, but still no go. I think that it's the HTC Sync it depends on and tried it too but within a virtual machine with no success too. I'll try with windows later, maybe I'm missing something.

---

### Post by ttanev on 2011-02-06
Wrote to HTC support, but their only directions were to try to search for an app in the store and if there is nothing useful to try google :) Maybe they have no plans for HTC Sync for Linux.

---

### Post by lars-i on 2011-03-05
hello,

i had the same problem mentioned above.
in the htc internet was working, when connecting it to my ubuntu 10.10 via usb ubuntu could not connect to the internet via the htc. i had a look into the network configuration in the htc and i found that there was set as the apn "wap.eplus.de". i changed it to "internet.eplus.de" and also set the user name ("eplus") and password ("gprs"). i replugged the usb cable and afterwards ubuntu could connect to the internet via the htc.

so my suggestion: check the network connection in the htc. i hope that information will help you.

---

### Post by ngh007 on 2011-06-08
Hi, Im a newbie to the forum.
I have a new HTC Desire Z - and I cant connect to internet through laptop either - not even first time.
What should my new APN settings be? Ive tried to find them online, but all I can find is APN settings for mobile service providers - [http://hdmp4.com/APN](http://hdmp4.com/APN)
Where do I find the APN settings for my laptop?


> **lars-i said:**
> hello,

i had the same problem mentioned above.
in the htc internet was working, when connecting it to my ubuntu 10.10 via usb ubuntu could not connect to the internet via the htc. i had a look into the network configuration in the htc and i found that there was set as the apn "wap.eplus.de". i changed it to "internet.eplus.de" and also set the user name ("eplus") and password ("gprs"). i replugged the usb cable and afterwards ubuntu could connect to the internet via the htc.

so my suggestion: check the network connection in the htc. i hope that information will help you.

---

### Post by ttanev on 2011-06-09
I think we are talking about different things here. 
My device is DesireHD and have installed the native Android 2.3 via OTA update from the last month. When connected with USB there's some options like "Charge only", "HTC Sync", "Disk Drive", "USB tethering" and "Internet Pass-through". "Disk drive" and "USB Tethering" are working flawlessly in any distro /with network-manager installed/. This thread is about "Internet pass-through" which is to use the PC's internet connection in the phone. As I understood the only way to use it is to install the non-existing HTC sync application in Linux. 
To lars-i: If you want to use the 3G/HSDPA or Wi-Fi internet of your HTC in your Ubuntu, just set the USB connection type to "USB Tethering" mode and everything should be fine in Ubuntu 9.10-11.04 /checked/. 
To ngh007: If you have internet on your phone when disconnected from your PC, then you shouldn't re-set your APN settings. What OS/distribution do you use ?

---

### Post by forevertheuni on 2011-06-10
We need to make masquerading probably with IPtables in the ubuntu machine. Probably the preferred setting will be to have a dhcp server as well(or fixed ips).
I'll look into it soon. (I used to use my linux machines for this so...)

---

### Post by Anal on 2011-07-27
Hello buds, does anybody had any success with this?

Thanks.

---

### Post by ivajloip on 2011-08-19
Hello!

I had some success, but quite partial. I managed to start the internet on my android powered device, however after a minute or so it said - could not connect to PC... 

Anyway, here is what I did. First of all I installed bind9 (DNS server, that's right). Then I did some iptables (using SNAT). I executed ```
echo 1 > /proc/sys/net/ipv4/ip_forward
```. After that I pluged-in the usb and it found the device. Then I started the bind9 service (only told it to bind to all interfaces and to forward any request to my dns server - 8.8.8.8 ). I could use my internet connection (at least with the default browser).

My problem was that although there was in fact internet connection on the android device, the program wouldn't notice it, so after a shourt while it turned down the usb0 device. As a consequence some of my applications would say - there is no internet connection - we can not work now (even before the usb0 was down). They wouldn't check :/

If someone knows how to explain to the andoid that there is in fact internet connection, I will be very happy to hear how to do it :)

P.S: If someone needs more information on something that I did, please let me know :)

---

### Post by aoniumo on 2011-09-14
Has anyone been able to solve this?  Just wondering since I got my HTC two weeks ago and I didn't want to start a new thread when there's this one that doesn't seem to have been solved.

---

### Post by haqking on 2011-09-14
> **aoniumo said:**
> Has anyone been able to solve this?  Just wondering since I got my HTC two weeks ago and I didn't want to start a new thread when there's this one that doesn't seem to have been solved.


You mean reverse tethering ?  I thought on the HTC it came as an option as soon as you plug it in via USB.

anyways see here if not [http://blog.mycila.com/2010/06/reverse-usb-tethering-with-android-22.html](http://blog.mycila.com/2010/06/reverse-usb-tethering-with-android-22.html)

---

### Post by aoniumo on 2011-09-14
> **haqking said:**
> You mean reverse tethering ?  I thought on the HTC it came as an option as soon as you plug it in via USB.

anyways see here if not [http://blog.mycila.com/2010/06/reverse-usb-tethering-with-android-22.html](http://blog.mycila.com/2010/06/reverse-usb-tethering-with-android-22.html)

  I don't why I can't just plug it in and enable "Internet Pass-Through" on the android phone like when it's connected to windows.

---

### Post by haqking on 2011-09-14
> **aoniumo said:**
> I don't why I can't just plug it in and enable "Internet Pass-Through" on the android phone like when it's connected to windows.


yeah i think i remember reading that was only supported under windows 9the android dves kind of slipped up there ;-)

anyways have you tried the bridging method in the link i posted ?

---

### Post by haqking on 2011-09-14
> **aoniumo said:**
> I don't why I can't just plug it in and enable "Internet Pass-Through" on the android phone like when it's connected to windows.


You could always use a Virtual machine with Windows in it. connect your phone and it should use the internet connection just fine

---

### Post by bluegray on 2011-10-10
I also have some success with NAT and installing a DNS server - browser works, but applications don't see that there is a connection. It only works until the phone gives up and disconnects pass-through.

It works fine when connecting through windows in virtualbox - I don't see why it can't work directly in Linux... :mad:

---

### Post by ivajloip on 2011-10-15
[SIZE=2]I searched the API trying to find if any application could actually detect that there is a connection with internet pass-through. And I couldn't see any way to do so as for API v10. In API v13 in [/SIZE][SIZE=1][SIZE=2]ConnectivityManager which should provide information about available networks, there is connection type ethernet. So I don't have any idea how this thing work on windows, however my (wild) guess is that it's some sort of hack. Something fooling the phone that it's connected through wifi... I will try to study the code and if I have some progress (for example creating some application), I will let you know :)[/SIZE]
[/SIZE]

---

### Post by saadia choudhry on 2012-02-09
will some buddy guide me how to use Internet pass through via my htc wildfireS????

---

### Post by hazelnut on 2012-06-22
On htc phones, when you plug the usb and select internet passthrough, it annoyingly waits for htc sync and gives up. It is listening on port 6000, so you only need to fake htc sync with netcat. Try this at the command line:

phoneip=$(arp -n | grep usb | awk '{print $1}')
echo -n -e "\x00\x02\x00\x00" | nc $phoneip 6000 > /dev/null

the hex value of 00 02 00 00 is all the stupid thing is looking for.

Have phun!  ):P

---

### Post by Gryllida on 2012-09-14
> **hazelnut said:**
> On htc phones, when you plug the usb and select internet passthrough, it annoyingly waits for htc sync and gives up. It is listening on port 6000, so you only need to fake htc sync with netcat. Try this at the command line:

phoneip=$(arp -n | grep usb | awk '{print $1}')
echo -n -e "\x00\x02\x00\x00" | nc $phoneip 6000 > /dev/null

the hex value of 00 02 00 00 is all the stupid thing is looking for.

Have phun!  ):P

```

~$ phoneip=$(arp -n | grep usb | awk '{print $1}')
~$ echo -n -e "\x00\x02\x00\x00" | nc $phoneip 6000 > /dev/null
This is nc from the netcat-openbsd package. An alternative nc is available
in the netcat-traditional package.
usage: nc [-46DdhklnrStUuvzC] [-i interval] [-P proxy_username] [-p source_port]
	  [-s source_ip_address] [-T ToS] [-w timeout] [-X proxy_protocol]
	  [-x proxy_address[:port]] [hostname] [port[s]]
~$

```

---

### Post by v4169sgr on 2013-01-11
Hello!

Sorry for the late reply, but I saw this & have a HTC One S & want to download a valid available system update without network charges. I have chosen not to have any wireless at home, and am running 12.04 stock with LTSP.

```
phoneip=$(arp -n | grep usb | awk '{print $1}')
echo -n -e "\x00\x02\x00\x00" | nc $phoneip 6000 > /dev/null
```
works for me - I can convince the phone I am now connected. But of course networking isn't working.

My machine's IP is 10.0.0.1, gateway 10.0.0.138. I have been using Network Manager to manually set the phone's IP [to e.g. 10.0.0.20] and can verify this address through e.g. ping. I've tried a lot of options for gateway, routes etc but I have not stumbled on the right solution.

I don't want to fiddle with IP tables, or change my LTSP DHCP [don't think I have to].

Anyone any ideas for getting reverse tethering working now that I have got this far?

Thanks!

---

### Post by v4169sgr on 2013-01-12
Any thoughts will be appreciated - thanks :)

---

### Post by oliverthered on 2013-06-11
> **v4169sgr said:**
> Any thoughts will be appreciated - thanks :)

worked for me after doing
iptables -A POSTROUTING -t nat -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward

installing
apt-get bind9

plugging device in until
ifconfig
said it had an ipv4 address
then doing the nc command in a previous post to fake HTC sync.

(also works as a wifi hotspot too), that's what I wanted it for, using the phone as a wifi router via the pc's wired cable internet connection.


There should be a simpler solution as not least DNS can just be any dns server, e.g. the one the PC already has... so bind9 isn't really required... I'll see if I can strip the solution down to the bare minimun and as much basic GPU config as possible (that may enable skipping the iptables etc... parts)

---

### Post by oliverthered on 2013-06-26
Here's my updated version:

```

cd ~
echo '!/bin/bash
apt-get install bind9
iptables -A POSTROUTING -t nat -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward' > setup_bind9_nat.sh

chmod +x setup_bind9_nat.sh
sudo ./setup_bind9_nat.sh
```

now plug in you're phone and select 'internet pass through'

wait for the device to appear in: 

```
ifconfig 
```

check it is also in: 

```
arp
```

I found I had to unplug the device then plug it in again for it to appear in arp, things don't work properly if arp doesn't show the device.

The device will then sit waiting for HTC Sync to send it a message so you have to mock HTC Syncs message:
```


#change this line to be more specific if you have more than one usb network device
phone_usb_device="usb"
get_ip ()
{
    arp -n | grep $phone_usb_device | awk '{print $1}'
}

#TODO: This needs a timeout and loop needs cleaning up, but works fine and borrowed from another post.
echo "waiting for IP on computer usb"
while [[ `get_ip` < 192 ]];do sleep 2; done
phoneip=`get_ip`
echo "IP adress is $phoneip "

echo -n -e "\x00\x02\x00\x00" | nc -q 2 $phoneip 6000 > /dev/null
```


The latter part could be turned into a D-Bus script

---

### Post by alexsmith on 2014-01-31
This worked perfectly for me. Thanks a lot!

---

