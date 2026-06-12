---
title: "wifi disabled?"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by vividia on 2009-03-26
I run Intrepid and for some reason my wireless card is disabled.  It was working and then one day, it stopped.

I ran a lshw -C network

this is what i got.


WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:06:09.0
       logical name: wmaster0
       version: 20
       serial: 00:c0:a8:ed:6e:03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 module=rtl8180 multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 42:2b:b2:fc:fb:9a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

Its says the network is disabled.  Beyond the fact that I did not want it disabled in the first place, how do I enable it?

---

### Post by BkkBonanza on 2009-03-26
Have you tried to bring the interface up again?
Try,

sudo ifconfig eth1 up

but put your device name in if not correct, maybe rt0, wlan0
If not then post results from,

ifconfig
iwconfig

---

### Post by vividia on 2009-03-26
I tried running the interlace command.  Nothing seemed to work.  I say seemed because all I got was a shiny new prompt.  I did run ifconfig and got:

eth0      Link encap:Ethernet  HWaddr 00:03:25:48:38:f1  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe48:38f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3732282 errors:2 dropped:0 overruns:0 frame:2
          TX packets:4382405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2771863837 (2.7 GB)  TX bytes:1556935150 (1.5 GB)
          Interrupt:21 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2886 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2886 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:233084 (233.0 KB)  TX bytes:233084 (233.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:ed:6e:03  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-ED-6E-03-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Then I ran iwconfig and got this:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

Hope thats what you're looking for.

---

### Post by BkkBonanza on 2009-03-26
Ya, the command I gave you would come back with no output but it should have brought the interface up. The output you gave me seems to indicate that your interface is up and running fine. Your wifi interface is wlan0 and from that output it appears normal. So your problem is likely in network config not hardware config. 

How are you trying to use it? Like to connect to your wifi router in the same room or in some other way. 

You can try the command, 

sudo iwlist wlan0 scan

to show if the wifi interface can see any other wifi access points nearby.

---

### Post by vividia on 2009-03-26
> **BkkBonaza said:**
> Ya, the command I gave you would come back with no output but it should have brought the interface up. The output you gave me seems to indicate that your interface is up and running fine. Your wifi interface is wlan0 and from that output it appears normal. So your problem is likely in network config not hardware config. 

How are you trying to use it? Like to connect to your wifi router in the same room or in some other way. 

You can try the command, 

sudo iwlist wlan0 scan

to show if the wifi interface can see any other wifi access points nearby.

I got 

wlan0        No Scan Results

---

### Post by plague.immortal on 2009-03-26
Seems like we have a similar problem.

[http://ubuntuforums.org/showthread.php?t=1106353](http://ubuntuforums.org/showthread.php?t=1106353)

I need help to.

I thought that the problem is in the router itself by blocking access to the new MAC add.
Take a look at your Wi-Fi access point if theres any security enabled that could block your network interface from connecting to the router and to the net from there.

---

### Post by vividia on 2009-03-26
> **plague.immortal said:**
> Seems like we have a similar problem.

[http://ubuntuforums.org/showthread.php?t=1106353](http://ubuntuforums.org/showthread.php?t=1106353)

I need help to.

I thought that the problem is in the router itself by blocking access to the new MAC add.
Take a look at your Wi-Fi access point if theres any security enabled that could block your network interface from connecting to the router and to the net from there.

Not trying to be crabby but that's a pointless thing to tell me.  I do not use wireless at home, just at school.  I have 0 control on the wireless network here.  I go to school at the University of Minnesota.  They have a massive wifi network and I see lots of people using it with no problems.

Again, cannot check router. access points or anything else like that.  Only thing I can do anything to is my laptop.

Edit: I realized the post stating that this was a non-home environment issue.  My apologies.  But still, don't assume its someone's home network setup. I actually refuse to put wifi in my home since I live in an apartment.  Too many leechers.

---

### Post by plague.immortal on 2009-03-26
Did you read the Cheesehead's post? He put in some commands that are worth trying.

And btw could you get some info about using wireless from the people who use it? They might tell you how to get it going. Perhaps theres a university's policy that not everyone is able to use the wireless. They could have MAC filtering setup and you may have to ask for a permission or something.. Just a guess though. Have no idea how universities work I am from high school in Slovenia (Europe, next to Italy).

---

### Post by vividia on 2009-03-26
> **plague.immortal said:**
> Did you read the Cheesehead's post? He put in some commands that are worth trying.

I replied to you first.  Now I'm reading the post.

---

### Post by vividia on 2009-03-26
The first two steps I've already done with no scan results for the second step.  That right there puts me out of the running so to speak.  I don't think I can continue with his steps if I can't get past step 2.

See my previous posts.

---

### Post by damis648 on 2009-03-26
What if you try good ol
```
sudo /etc/init.d/networking restart
```
or maybe
```
sudo ifdown wlan0
sudo ifup wlan0
```
or even
```
sudo rmmod module_name_that_runs_wireless_card
sudo modprobe module_name
```

---

### Post by plague.immortal on 2009-03-26
Well I hope someone will be able to help us.
I can't get pass the step 2 as well.

---

### Post by vividia on 2009-03-26
> **plague.immortal said:**
> Did you read the Cheesehead's post? He put in some commands that are worth trying.

And btw could you get some info about using wireless from the people who use it? They might tell you how to get it going. Perhaps theres a university's policy that not everyone is able to use the wireless. They could have MAC filtering setup and you may have to ask for a permission or something.. Just a guess though. Have no idea how universities work I am from high school in Slovenia (Europe, next to Italy).

LOL  not all Americans are ignorant of the rest of the world.  

I should have been more clear.  I have used this before at this school.  There is a security protocol of ID/password AFTER making a connection with the network.  Basically, it lets you connect locally then after you sign in, you can surf.

I've used it before.  I've even used it at my friend's house before but I can't even get the network manager to show any available networks.  I'm at school now in the library, a hot zone among the larger hot zone.  i got zip.

---

### Post by vividia on 2009-03-26
> **damis648 said:**
> What if you try good ol
```
sudo /etc/init.d/networking restart
```
or maybe
```
sudo ifdown wlan0
sudo ifup wlan0
```
or even
```
sudo rmmod module_name_that_runs_wireless_card
sudo modprobe module_name
```

I did the first suggestion... but I'm not sure what I'm supposed to get.

---

### Post by vividia on 2009-03-26
> **damis648 said:**
> What if you try good ol
```
sudo /etc/init.d/networking restart
```
or maybe
```
sudo ifdown wlan0
sudo ifup wlan0
```
or even
```
sudo rmmod module_name_that_runs_wireless_card
sudo modprobe module_name
```

I did sudo ifdown wlan0 and got 
interface wlan0 not configured

FUN!

---

### Post by plague.immortal on 2009-03-26
Interesting I got the same things. That restart thingy just printed out "recounfiguring network devices...        [OK]"

But the scan command insists on "Network is down".

---

### Post by vividia on 2009-03-26
Yeah I got the reconfiguring devices messages and then a new prompt.

so discouraging

---

### Post by plague.immortal on 2009-03-26
Can you describe what caused your wireless to stop working?

I had mine running for like 40 seconds under windows and then decided I need Ubuntu. So I know for sure that the device can work propperly. I am in doubt that the drivers are there..But for the moment I don't see where to get them or how to get them up on the Ubuntu server machine.

---

### Post by vividia on 2009-03-26
I don't know when it stopped working per se.  I had been able to use the wifi here through beginning of the semester up until March 3 or 4th.  I noticed it but I had bigger things going: mid terms.  

btw, I don't dual boot.  strictly ubuntu on this machine.

---

### Post by plague.immortal on 2009-03-26
I am running Ubuntu Server on the troubled PC as well, not a dual boot. Had windows server trial on to see what it looks like and I hated it after 40 seconds..

It is weird that the device just stops working. Did you do any major upgrades to the system lately? Perhaps played around with delicate settings? Or did it just simply stop workining?

I know that this things can't be the reason for my wi-fi not working since I didnt change anything at all.
Maybe I need to somehow enable the wireless in some config file or something.. I dont know.

---

### Post by dnairb on 2009-03-26
The ouput from iwconfig suggests that the wireless interface is working OK, but that it can't find a network.

Maybe the network no longer broadcastst its SSID (i.e. it is a hidden netrwork). Try this: click the network icon-thingy (if it is on a panel) and select "Connect to hidden wireless network" - this only works if you know the network's SSID and security setting.

---

### Post by vividia on 2009-03-26
> **dnairb said:**
> The ouput from iwconfig suggests that the wireless interface is working OK, but that it can't find a network.

Maybe the network no longer broadcastst its SSID (i.e. it is a hidden netrwork). Try this: click the network icon-thingy (if it is on a panel) and select "Connect to hidden wireless network" - this only works if you know the network's SSID and security setting.

Ok, well, I'll have to head to the computer help people.  that might take me some time.

---

### Post by plague.immortal on 2009-03-26
I think the better option is to go to someone who is using wireless and ask for information. If they are connected they know the SSID.

---

### Post by vividia on 2009-03-26
> **plague.immortal said:**
> I think the better option is to go to someone who is using wireless and ask for information. If they are connected they know the SSID.

In a university like this?  I have the computer help staff in the next building.  No, its the better option. 

That and its rude since most people won't actually know it.  Lot of people here know how to turn the PC on, get e-mail and IM.  thats about it.

I have yet to go but I will shortly.  I had to finish up some stuff here in the library.  Then i'll go see.  I will also have to see about getting back on a computer.

---

### Post by vividia on 2009-03-26
Seems like this is prolly some bug in Intrepid.  Just as annoying as the "Do you know how much hard drive space is left?  cuz i don't!" bug.

---

### Post by plague.immortal on 2009-03-26
Is that what the computer staff told you?

---

### Post by pastalavista on 2009-03-26
don't want to insult your intelligence or anything but does your notebook have a physical switch on it anywhere that may be switched off? happened to me once. tore the jumble of configs apart and my stupid wifi switch was turned off. I never turned it off...

---

### Post by vividia on 2009-03-26
> **pastalavista said:**
> don't want to insult your intelligence or anything but does your notebook have a physical switch on it anywhere that may be switched off? happened to me once. tore the jumble of configs apart and my stupid wifi switch was turned off. I never turned it off...

Beyond all the places I've checked I don't know where that would be.  Are you talking about a physical switch?  If that is the case, I don't have one.

As for the SSID, I didn't make it to the PC help office before they closed.  But it really shouldn't make a difference since it happens everywhere, not just one place.

---

### Post by pastalavista on 2009-03-26
ah well, good luck. you might also check in the bios for an enable/disable.. the bios is full of 'em

---

### Post by BkkBonanza on 2009-03-27
No. If the wireless wass disabled or turned off then I'm pretty sure the interface wouldn't be UP and have a config showing in iwconfig.

When you did the iwlist command are you sure you did it with sudo? I have noticed that not being run as root it will usually show no results, but as root it does.

The fact that you get seemingly reasonable results from these various commands seems to point to everything working but no access point withing range (or not strong enough, or hidden). 

I don't have any further ideas now. Maybe you need a real life Linux techie. Maybe your internal antenna has come loose and so no signal is getting picked up.

---

### Post by vividia on 2009-03-27
> **BkkBonaza said:**
> No. If the wireless wass disabled or turned off then I'm pretty sure the interface wouldn't be UP and have a config showing in iwconfig.

When you did the iwlist command are you sure you did it with sudo? I have noticed that not being run as root it will usually show no results, but as root it does.

The fact that you get seemingly reasonable results from these various commands seems to point to everything working but no access point withing range (or not strong enough, or hidden). 

I don't have any further ideas now. Maybe you need a real life Linux techie. Maybe your internal antenna has come loose and so no signal is getting picked up.

Noob query: How do I run as root?

I had given thought to my wireless card just dying.  I wonder if i might just do re-install and take everything back to square one and see what happens.  I keep all files backed up so its not a problem at all.  if it still doesn't work, then I am pretty sure my card has died (I'll bury it with a 21 swear salute)

---

### Post by tdawg on 2009-03-29
I think this describes Linux perfectly

[IMG]http://i14.photobucket.com/albums/a331/madhatterdisease/screenshot-2.jpg[/IMG]

---

### Post by plague.immortal on 2009-03-29
You run as root by using the command "sudo" infront.

sudo something

---

### Post by vividia on 2009-03-31
> **plague.immortal said:**
> You run as root by using the command "sudo" infront.

sudo something

oh duh

---

### Post by vividia on 2009-03-31
> **BkkBonaza said:**
> No. If the wireless wass disabled or turned off then I'm pretty sure the interface wouldn't be UP and have a config showing in iwconfig.

When you did the iwlist command are you sure you did it with sudo? I have noticed that not being run as root it will usually show no results, but as root it does.

The fact that you get seemingly reasonable results from these various commands seems to point to everything working but no access point withing range (or not strong enough, or hidden). 

I don't have any further ideas now. Maybe you need a real life Linux techie. Maybe your internal antenna has come loose and so no signal is getting picked up.
Ran it as root and this is the output

Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation

---

### Post by BkkBonanza on 2009-03-31
you need to also use the command and interface like,

sudo iwlist wlan0 scan

that will give a list of any nearby access points that your wifi interface can see. If you get something then it means your card is functioning and it's software config that is messed up. Try to be sure you are close / in range of an access point when you do it. Ideally look around and see the access point and then go sit close to it.

---

### Post by vividia on 2009-04-01
> **BkkBonaza said:**
> you need to also use the command and interface like,

sudo iwlist wlan0 scan

that will give a list of any nearby access points that your wifi interface can see. If you get something then it means your card is functioning and it's software config that is messed up. Try to be sure you are close / in range of an access point when you do it. Ideally look around and see the access point and then go sit close to it.
Ok... did it that way.

wlan0     No scan results

---

### Post by BkkBonanza on 2009-04-02
Hmmm. Well it's been over several days and no doubt reboots. So I would suggest backtracking and checking each step. 

The command, 

ifconfig

should list any interfaces that are "UP".
If wlan0 isn't listed then you need to bring it up with,

sudo ifconfig wlan0 up

Once wlan0 is up, then you should have output from,

iwconfig wlan0

that shows the mode and various details. Mode should be "Managed" for normal use.

If that is up then using,

sudo iwlist wlan0 scan

should show any AP it can "see".

This is not even worrying about higher level controls like network manager or wicd. You should still be able to get this series of steps. It seems like you have normal results except no AP are seen by the interface. I'm not sure why that would be but probably someone with more experience needs some hands on time to poke at various things there.

If your drivers and modules were not in order I don't think you would get any results at all from ifconfig for wlan0.

---

### Post by vividia on 2009-06-16
Sorry for not keeping up on this.  I was in the hospital for most of April and May.  God i missed computers!!!

The problem has disappeared.  It picks up wireless signals now.  Not really sure what happened.  I won't tag this as solved because technically it isn't.  And if it stops working again, I'll just pick up where I left off.

Thanks for the advice.

---

### Post by Aszasz on 2009-06-18
> **damis648 said:**
> What if you try good ol
```
sudo /etc/init.d/networking restart
```
or maybe
```
sudo ifdown wlan0
sudo ifup wlan0
```
or even
```
sudo rmmod module_name_that_runs_wireless_card
sudo modprobe module_name
```


I ran the first command and after a reboot wifi came back and is running great now:D (really have to try understanding my computer in the end the solution was quite obvious... so at least i can call it solved. thanks damis648!   
Good luck with your wifi, vividia

---

