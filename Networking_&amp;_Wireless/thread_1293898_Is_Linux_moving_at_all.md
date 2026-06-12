---
title: "Is Linux moving at all?"
date: 2009-10-17
forum: Networking &amp; Wireless
---

### Post by Thulemanden on 2009-10-17
When drivers for the Intel wireless have been available since 2007 on [http://intellinuxwireless.org/?n=Downloads](http://intellinuxwireless.org/?n=Downloads) I find it a bit crappy it's not built into the kernel in fall 2009.

I'm talking about the 3945 ABG.

Also I find it ridiculous you can't add a driver except building a new kernel as the support answers on this form advise.

---

### Post by chili555 on 2009-10-17
What, exactly, is wrong with *iwl3945* which I am using at the moment and which, for me, works perfectly? Now, you may not be connecting because Network Manager is being lazy today, or you are too far from the router or your encryption key is faulty, but the driver is there by default.

---

### Post by oboedad55 on 2009-10-17
Ditto, it's working here as well, same adapter.

---

### Post by Thulemanden on 2009-10-17
Very Strange. I just downloaded Ubuntu in the latest version 9.0.4 and the driver is not there.

I'm running it in demo live mode from a cdrom.

I have used Linux in some years in nearly all distros but gave up after about 3 years of hard work with it so I'm not a total newbie, and if the driver was there, I'm sure it would have emerged by now. Screenshots attached.

I don't get this at all. Why does it still have to be so difficult to make use of?

---

### Post by chili555 on 2009-10-17
It's not proprietary and it's not in a Synaptic package named iw-sumthin. Simply open a terminal and do:```
sudo modprobe iwl3945
```Check both it's presence and version with:```
modinfo iwl3945
```If modprobe doesn't kick your wireless to life, I'd check the wireless switch.

---

### Post by Thulemanden on 2009-10-17
Thank you.

I guess the attached image is good news?

Then, do I need to reboot or what?

No change in the network connections interface

---

### Post by chili555 on 2009-10-17
Reboot? I only reboot when I go on vacation. Confirm that you have a wireless interface with:```
iwconfig
```Does *wlan0* appear? When you click the Network Manager icon (looks like two little monitors at the upper right), do you see networks to connect to? Can you connect?

---

### Post by Thulemanden on 2009-10-17
Hi Chili

After iwconfig I get a disappointing


ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"VJ"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ubuntu@ubuntu:~$ 


Needless to say, the wireless works great with my Vista and at a distance of 40 Cm can hardly get closer as suggested.

As my attached images already showed there is no wireless connection information in Netwoork connections, as you asked about. Perhaps you would want to look at the attached documentation above.

A guy had the same problem and it disappeared when he installed PCLinuxOS.

I do find it strange Ubuntu doesn't find and connect the wireless when the driver is included as you proved. How come Ubuntu doesn't do that automatically yet?

---

### Post by chili555 on 2009-10-17
> wlan0 IEEE 802.11abg ESSID:"VJ"
Mode:Managed Frequency:2.462 GHz Access Point: Not-Associated
Tx-Power=15 dBm
Retry min limit:7 RTS thrff Fragment thr=2352 B
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
How is this disappointing? You have a perfectly good *wlan0* ready to be commanded to connect. When you left-click the Network Manager icon, do you see networks, VJ, perhaps? If not, please post:```
sudo iwlist wlan0 scan
```It make take a few moments; please be patient.

---

### Post by Thulemanden on 2009-10-17
It's working now!     :guitar:

I took notes from the Vista connection on the access data and added them to a new Network Connection (SSID, MAC, Security mode and DHCP mode (Automatic).

I also looked through the routers config in Vista.

Only when I used the password for the Router configuration did it start to work. I used the password I had entered in Vista for quite a while without success. I couldn't guess I needed the Router config password.

By accident I now also clicked the left mouse button on the wireless icon and now I saw a row of available networks, some secured but also the unsecured VJ from a neighbour. Had I seen it before I would probably had tried it and discovered the access worked so the driver and hardware was OK, and it would have been my aceess information to my router that was at fault and I would have added a network connection manually.

But I can't figure out how you could identify the network VJ as it was not posted in the documentation? Sherlock? :P  How did you do that?  :confused:

Anyways, thank you very much for bearing so patient over with me.

Now to the permanent installation.  Should I choose and 'In Windows' or a 'Select OS' at boot?

Guess I make best use of memory by booting directly into Ubuntu?

---

### Post by Thulemanden on 2009-10-17
Well, I just booted the live PCLinuxOS and all I had to do was entering the router config password. All the rest was gathered automatically in a few seconds as I originally expected. It uses drakroam  for that  it looks.

Drakroam is the wireless utility used in Mandriva Linux 

Well thank you again for the assistance.

---

### Post by chili555 on 2009-10-17
> But I can't figure out how you could identify the network VJ as it was not posted in the documentation? Sherlock?  How did you do that?I'd love to take credit, but...> wlan0 IEEE 802.11abg ESSID:"[COLOR="Red"]VJ[/COLOR]"
Mode:Managed Frequency:2.462 GHz Access Point: Not-Associated
Tx-Power=15 dBm
Retry min limit:7 RTS thrff Fragment thr=2352 B
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0 Glad it's working for you.

---

