---
title: "How to configure the interfaces for wireless and WUSB54GC"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by marianlibrarian on 2010-05-10
Hi,

So far I have been able to get a computer using Ubuntu 10.04 and WUSB54GC Wireless adapter to connect to our network.

I have a network manager located on our Vista laptop. It shows this computer in our network list of computers. However, it says that it is off line.

This computer will not access the internet.

This is what I have investigated so far:
I black listed in the blacklist.conf
rt2800usb and rt2870usb 
--when I added the rt2870usb, the computer was listed in our network.

Then I looked at my /etc/network/interfaces 
The following is all that is in that file:
auto lo
iface lo inet loopback

In the Devices - Network Tools, the Network device: Wireless Interface (wlan0) is listed. I am not able to PING or lookup any other computers from there. 

I believe that my problem is an incomplete interfaces configuration. I clicked on help in the Devices menu but all that is there is an introduction. So I came here. 

Any help will be appreciated.

P.S. I really am a librarian in a very small very rural library. All of our public access computers and two of our staff computers are running some form of Ubuntu since 2007. I feel like I am so close to figuring this out. Thank you in advance for your help.

---

### Post by marianlibrarian on 2010-05-10
Perhaps I am in the wrong place / forum to ask my question? Is there still an "Absolute Beginner" Forum? I have been reading and searching through these forums for two days and I thought I had found the right place since I am finding many people having wireless problems of many kinds. 

Could someone please direct me to the proper forum?

---

### Post by bkratz on 2010-05-10
> **marianlibrarian said:**
> Perhaps I am in the wrong place / forum to ask my question? Is there still an "Absolute Beginner" Forum? I have been reading and searching through these forums for two days and I thought I had found the right place since I am finding many people having wireless problems of many kinds. 

Could someone please direct me to the proper forum?

Well, you are in the right place, but 1 and 3/4 hour is a pretty short fuse!  Anyway, see if your answer is here ( I hope).

[http://ubuntuforums.org/showthread.php?p=9274010#post9274010](http://ubuntuforums.org/showthread.php?p=9274010#post9274010)

Nevermind-- I see you were there already!

---

### Post by marianlibrarian on 2010-05-10
I'll keep trying and searching...

Where do I get ndiswrappers for 10.04?

my screen says that this is not installed. I can get it by sudo apt-get but.... that requires internet access.

lsusb tells me:
Bus 001 Device 002: ID13bl: Linksys WUSB54GC 802.11g Adapter [ralink rt73]

Should I blacklist rt73?

I blacklisted it and restarted but it made no difference. Still looking.

---

### Post by marianlibrarian on 2010-05-10
Without an Internet connection, you can still install ndiswrapper-utils from the Desktop CD. If you installed from that, the repository in which ndiswrapper-utils is found is on the CD, but not within the live session. You need to boot into your new Ubuntu installation and then reinsert _online resume writer_ the Desktop CD. You will be asked if you want to add the packages on the CD to your list of repositories.

What in the world does a resume writer have to do with installing ndiswrapper??????

[http://cvresumewriters.com/onlineresume.php](http://cvresumewriters.com/onlineresume.php)

This problem is getting worse by the moment. If I don't find a solution soon, I may be OUT OF A JOB and need that resume writer!

---

### Post by marianlibrarian on 2010-05-10
Hi Bkratz, thanks for looking. I have been floating in here for a couple of days. Well, Friday and Monday. I don't have internet access at home - so all research is done during business hours. :)

The thread you found is the first one I found on Friday. It seems to have worked when I added rt2870 to my blacklist. At least the message at the top says "Wireless network connection 'genevapubliclibrary' active: genevapubliclibrary (100%) 

that is a good thing. but still no internet access. 

So I found this:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

But there is nothing there for 10.04

I even did a search for ndiswrapper 10.04 and this is what I got:
Sorry - no matches. Please try some different terms.

Perhaps it was a mistake to install the "latest" version of ubuntu. I still have the 9.10 cd. Should I start over / downgrade to 9.10?

So around and around and around I go.

---

### Post by chili555 on 2010-05-10
STOP!

Nobody has given you a clue as to what to do, yet you are making random changes based on...what? I don't understand why you would determine that your device uses an RT73 chipset and then blacklist it. Is your objective to make sure that it never works, ever?

The driver module rt73usb is what your device requires to work. rt2870sta and rt2800usb have nothing to do with it. It won't hurt that you blacklisted them, but it won't change anything.

I am not at all sure I understand your question, actually. You say:> So far I have been able to get a computer using Ubuntu 10.04 and WUSB54GC Wireless adapter to connect to our network.But then you say:> I have a network manager located on our Vista laptop. It shows this computer in our network list of computers. However, it says that it is off line.Are you really trying to set up file sharing between Ubuntu and Windows?

---

### Post by chili555 on 2010-05-10
> the message at the top says "Wireless network connection 'genevapubliclibrary' active: genevapubliclibrary (100%)That would indicate that you are connected. What happens when you open Firefox? Open a terminal and post:```
ping -c3 74.125.157.99
cat /etc/resolv.conf
```

---

### Post by marianlibrarian on 2010-05-10
> STOP!

Nobody has given you a clue as to what to do, yet you are making random changes based on...what? I don't understand why you would determine that your device uses an RT73 chipset and then blacklist it. Is your objective to make sure that it never works, ever?

one clue from here:
[http://ubuntuforums.org/showthread.php?p=9274010#post9274010](http://ubuntuforums.org/showthread.php?p=9274010#post9274010)

i apologize for offending.

---

### Post by marianlibrarian on 2010-05-10
ping -c3 74.125.157.99
connect: Network is unreachable

cat /etc/resolv.conf
#Generated by NetworkManager

i apologize for the confusion when i mentioned vista. i have a vista laptop that has Cisco Network Manager installed. i use it to monitor our public library network. this includes public access computers and all staff computers. the computer that i just installed 10.04 is showing up on Cisco Network Manger list but it says that it is off line or now powered on.

---

### Post by chili555 on 2010-05-10
> **marianlibrarian said:**
> one clue from here:
[http://ubuntuforums.org/showthread.php?p=9274010#post9274010](http://ubuntuforums.org/showthread.php?p=9274010#post9274010)

i apologize for offending.You are not offending, however, it's very difficult to help when you are making changes faster than I can reply and have two threads going! Are you connected now? Can you connect again if you remove rt73usb from blacklist and do:```
sudo modprobe rt73usb
```

Please check private messages.

---

### Post by marianlibrarian on 2010-05-10
thanks. i thought i was helping by reading and researching for myself and not being a technomoocher.

anyway, sudo modprobe rt73usb does not return anything.

p.s. i am not going to many any changes at all until you respond back. just so you know. even if it isn't until tomorrow or something like that. also i need to let you know that i am the only library person here. we close in at 17:30 central standard time. some kids just trashed the children's room so i am cleaning up here. thank you for your patience.

---

### Post by chili555 on 2010-05-10
After you loaded rt73usb, did you have any evidence you are connected?```
iwconfig
ifconfig
```Thanks.

---

### Post by marianlibrarian on 2010-05-10
iwconfig

lo no wireless extensions.

eth0 no wireless extensions.

wlan0 
IEEE 802.11bg ESSID:"genevapubliclibrary"
Mode:Ad-Hoc Frequency:2.412 GHz Cell: A6:33:6F:91:1B:90
Tx-Power=18 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:on

copy pasted using flashdrive
ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1a:4d:68:1c:35  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:796 errors:0 dropped:0 overruns:0 frame:0
          TX packets:796 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63248 (63.2 KB)  TX bytes:63248 (63.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:bf:73:32:16  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::214:bfff:fe73:3216/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3675 (3.6 KB)

---

### Post by chili555 on 2010-05-10
> wlan0
IEEE 802.11bg ESSID:"genevapubliclibrary"
Mode:[COLOR="Red"]Ad-Hoc[/COLOR] Ah, haaaa! It's trying to make an ad-hoc connection; that is, computer to computer. We want computer to access point. Please do:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed
sudo ifconfig wlan0 up
```Now can you click the Network Manager icon and connect to ye olde interwebs?

---

### Post by marianlibrarian on 2010-05-10
i followed your instructions. 

iwconfig now says

> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=18 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

However, still now internet access. using flash drive between laptop and ubuntu desktop - and i am slow.

---

### Post by chili555 on 2010-05-10
When you click the Network manager icon at the top right, do you see your network? Does it try to connect?

---

### Post by marianlibrarian on 2010-05-10
sorry for the delay. closing library. everyone gone but me.

the only icon i see is the wireless network connection which says active: genevapubliclibrary (100%)

i don't know where the network manager icon is.

edit:
if that is the network manager icon, there is a drop down menu that has the following items:
Wired Network 
disconnected

Wireless Networks
Disconnect
Available
genevapubliclibrary
genevapubliclibrary
VPN Connections
Connect to Hidden Wireless Network
Create New Wireless Network

---

### Post by chili555 on 2010-05-10
Well, I think you are connected. What does this tell us?```
ifconfig
```Does it show a 10.42.x.x address or some other? What does this say?```
ping -c3 74.125.157.147
```No need to thumb drive the results. just tell me if you get ping returns.

---

### Post by marianlibrarian on 2010-05-10
connection information
ip address: 10.42.43.1
broadcast address: 10.42.43.255

None of the other computers have ip addresses like that. They are supposed to assigned by DHCP and have ip addresses that begin with 192.168.1.#

the ping command says
Network is unreachable

---

### Post by chili555 on 2010-05-10
> ip address: 10.42.43.1
broadcast address: 10.42.43.255That's typical of an ad-hoc connection. Please right-click the Network Manager icon:> edit:
if that is the network manager icon, there is a drop down menu that has the following items:
Wired Network
disconnected

Wireless Networks
Disconnect
Available
genevapubliclibrary
genevapubliclibrary
VPN Connections
Connect to Hidden Wireless Network
Create New Wireless Network Yep, that one...select Edit Connections, select Wireless and delete both of the genevapubliclibrary items. Reboot and see if you can now connect to a proper managed, not ad-hoc connection.

---

### Post by marianlibrarian on 2010-05-10
deleted both instances of genevapubliclibrary connections

restarted

when the computer came back up, there is no connection in the network manager.

i opened a terminal window and did:
iwconfig

lo and eth0 both say no wireless extensions.

wlan0 
IEEE 802.11bg ESSID:off/any
Mode;Managed Access Point: Not-Associated Tx-Power=18 dBm
---and the other stuff

Mode is Managed but no connections

---

### Post by chili555 on 2010-05-10
And when you click the icon, what do you see?> Wired Network
disconnected

Wireless Networks
Disconnect
Available
[B]anyone?
anything?[/B]
VPN Connections
Connect to Hidden Wireless Network
Create New Wireless Network 

---

### Post by marianlibrarian on 2010-05-10
Found something!!

i added new connection and now wireless connection is up and active, however, now when i do the iwconfig...

Mode is Ad-Hoc

i can right click on the network icon and edit connection is in the menu. i select that and the genevapubliclibrary is there. However, Mode only has two options: Ad-hoc and Infrastructure.

---

### Post by chili555 on 2010-05-10
Select Infrastructure. Now when you run *ifconfig*, do you see a 192.168.x.x address?

---

### Post by marianlibrarian on 2010-05-10
i selected infrastructure and the mode with iwconfig is still Ad-Hoc.

Dear Chili555, i will need to go home soon. my daughter is here with me and we have homework and supper and bathtime and read book time and then bed time. 

i so appreciate your help here. i learn something new every time i come here. someday - someday i will be able to contribute instead of always being the needy one.

i will get here early in the morning - as soon as my daughter gets on the school bus - around 7 in the morning.

i promise promise not to touch or mess with anything until i read your post. thank you so much - i will wait a few minutes - i have to do backup here - to see if you will be here tomorrow.

---

### Post by chili555 on 2010-05-10
I'll be here. Take good care of that daughter and we'll meet tomorrow.

---

### Post by marianlibrarian on 2010-05-10
thank you and good night and see you tomorrow!

---

### Post by chili555 on 2010-05-11
Good morning!

I suggest you do:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed
sudo ifconfig wlan0 up
```Now right-click the Network Manager icon and select Edit Connections. Select Wireless, highlight Auto genevapubliclibrary and click Edit. Make sure the SSID says genevapubliclibrary, the mode is Infrastucture and click Apply. Close Network Connections and see if you are connected with a 192.168.x.x address with:```
ifconfig
```Please let me know your result.

---

### Post by marianlibrarian on 2010-05-11
good morning!

i followed your instructions. it now seems to be stuck in a "authentication required" cycle. 

ifconfig does not show any ip addresses.

it cycled through the authentication required and finally quit.

ifconfig does not show any ip addresses.

---

### Post by chili555 on 2010-05-11
Can you put the authentication in Edit Connections and check Connect Automatically? If the password and method (WPA vs. WEP vs. WPA2 etc.) is correct, it won't ask; it will simply connect.

---

### Post by marianlibrarian on 2010-05-11
hi chili555

i opened the connection name in edit, and the connect automatically is check marked. our router uses wep authentication and i double checked to make sure that the correct key is displayed. the mode remains "infrastructure".

something i noticed yesterday... the contents of my etc/network/interfaces file has only two lines. 

auto lo
iface lo inet loopback

i have never seen this file have so little information. do you think this might be part of my problem? also, if it is, i did not mess with this file. :)

---

### Post by chili555 on 2010-05-11
> something i noticed yesterday... the contents of my etc/network/interfaces file has only two lines.

auto lo
iface lo inet loopback

i have never seen this file have so little information. When Network Manager is handling your connection, it handles all those details. That configuration is correct.

I am a bad person to ask. I think NM is useless in a fixed, desktop setting; I think it's better to set up your details in /etc/network/interfaces, remove NM and be done with it forever. My wife runs Ubuntu and has never seen or dealt with NM. It gets the ax in any install here.

The Ubuntu world at large doesn't agree; NM is installed by default. I suppose it's easier than trying to figure out at installation if the computer moves or stands still.

How many characters in the key? After you put that key in the correct box, does it try to connect?

---

### Post by marianlibrarian on 2010-05-11
> I think NM is useless in a fixed, desktop setting; I think it's better to set up your details in /etc/network/interfaces, remove NM and be done with it forever. My wife runs Ubuntu and has never seen or dealt with NM. It gets the ax in any install here. Things that make you go hmmmm...

there are 26 characters in my key. when i click on the name in the network manager menu, it attempts to connect for several minutes, then stops.

i noticed something else, since it is controlled by the network manager - that sounds so windows - anyway, in the nm-system-settings.conf there is the following information:
> [main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

does that look alright to you?

---

### Post by chili555 on 2010-05-11
> [ifupdown]
managed=false You get a lot of conflict here; some systems work well with false and some with true. Please edit it to true and reboot. Let us know if it connects.

I have an appointment in Big City in about an hour, so we have to fix this soon!

---

### Post by marianlibrarian on 2010-05-11
that did not make any difference. it continues to cycle through the wireless network authentication required. however, right after i restarted, the connection was made. i checked the ifconfig and wlan0 mode is managed. then connection was lost and now it continues to cycle through the authentication over and over.

we may have to put this away until tomorrow. i have a library board meeting to prepare for this evening. 

i really really appreciate your help. i have all confidence that this problem will be resolved. -- thank you so much =)

Edit: before i put this away, i unplugged the usb wireless from the back of the computer and plugged it into one of the front places. it stays connected at 40%. however, ifconfig shows the inet addr:10.42.43.1 while the iwconfig shows mode:managed. 

hmmm.... anyway, have a safe trip into big town. i will tackle this perhaps tomorrow. i have a children's reading hour tomorrow at 1:30 so may only be able to work on this for a little while tomorrow afternoon. :)

---

### Post by marianlibrarian on 2010-05-11
I FOUND IT!!!!!!!!!!!!!!!!!!!!!!!!!!

happy happy joy joy

i used nm-tool in the terminal window. it showed that the IPv4 settings with address 10.42.43.1

i right clicked on the network icon and selected edit connections.

i selected the wireless tab and selected my connection name and edited the IPv4 settings from something called Shared ??? to DHCP


and that worked!!!!!

i am typing this on the offending computer because now it is on line!!!

i have to get to work now - my board meeting will be this evening. wow thank you chili555

have a superfantastical day

---

### Post by chili555 on 2010-05-11
I am very glad it's working! Have a great meeting and a great day. Call on us any time.

---

