---
title: "Keeps asking for wireless password and doesn't connect!"
date: 2011-01-23
forum: Networking &amp; Wireless
---

### Post by chaozuper on 2011-01-23
Hi. I'm trying to get connected to the internet wirelessly using a Belkin F5D8053 wireless adapter. I used ndisgtk to install the driver (which i got straight off the disc that came with the adapter). I plugged in the adapter and ndisgtk recognised the hardware. Problem is, when i tried to connect to the internet, ubuntu tried to connect for about a minute then asked for my password again. It keeps on asking for my password every few minutes and doesn't connect! my password and encryption type are definitely correct. i'm using ubuntu 10.10.

Please help, i've been spending about 3 days trying to get on the internet and it's getting really frustrating! thanks.

---

### Post by bkratz on 2011-01-23
What type of encryption are you using?  Other people (including me) have had problems with having the wireless access point in combination mode ie. 
WPA and WPA2.  Try one or the other, but not the both setting on the AP.

---

### Post by chaozuper on 2011-01-23
> **bkratz said:**
> What type of encryption are you using?  Other people (including me) have had problems with having the wireless access point in combination mode ie. 
WPA and WPA2.  Try one or the other, but not the both setting on the AP.

Thanks for the reply. i'm using WEP encryption.

---

### Post by chaozuper on 2011-01-24
bump

---

### Post by oj0kksn5 on 2011-01-24
well first off try removing all security and connect make sure there isnt anything else stopping it from connecting. if you can connect with no security try adding your security back in but make sure you know the password and the encryptions

---

### Post by chaozuper on 2011-01-24
> **sephedo said:**
> well first off try removing all security and connect make sure there isnt anything else stopping it from connecting. if you can connect with no security try adding your security back in but make sure you know the password and the encryptions

i removed security on my network and i was able to connect! unfortunately, i couldn't when i put wep back on. i've looked around for help with this, and someone suggested installing wicd, which i tried, but it couldn't find my wireless network. also, i tried editing /etc/network/interfaces and i'm pretty sure i screwed it up! will this affect my connection? (i didn't really know what i was doing :S)

---

### Post by oj0kksn5 on 2011-01-24
okay so you are best going back to how you were before when you where connected to your router without your security, you should be able to access the routers web interface and just add it back in then connect again with new password

---

### Post by Beetlemma on 2011-01-24
I'm having the same problem
I bought a  Dlink wireless usb adapter DWA 130
I uploaded the drivers and got the thing flashing but same thing, it keeps asking for my password and doesn't connect even though it can see the network and there's a good connection. 
This was the first thing I was trying to do after a clean install
I'm also using 10.10
:mad:

---

### Post by chaozuper on 2011-01-24
> **sephedo said:**
> okay so you are best going back to how you were before when you where connected to your router without your security, you should be able to access the routers web interface and just add it back in then connect again with new password

i tried that but i just get disconnected when i change the encryption back to wep. if i try and connect again, ubuntu asks for a password, tries to connect, fails to connects and then asks me for my password again... and that keeps on happening.

---

### Post by oj0kksn5 on 2011-01-24
have you tried removing the security to see if it connects?

---

### Post by oj0kksn5 on 2011-01-24
what encryption are you using WEP still? or another version of WEP? also do you know what wireless network card you are using?

---

### Post by grahammechanical on 2011-01-24
Hi guys

Forgive me if I am stating the obvious but, it is just a machine and it is a stupid machine at that. If the password is incorrect then it cannot connect.

When the operating system asks for authentication it sometimes needs your login password that you choose when the OS was first installed. This is often the case but when the OS asks for authentication of a wireless network connection it needs the wireless key also called WPA-PSK key or even the network security key or pass-phrase. 

This is an easy mistake to make. It is a mistake that I myself have made. This is why I point it out now.

Regards.

---

### Post by chipppy on 2011-01-24
Good Morning

I am also having a heap of issues with wireless and hopefully the following will help someone out there in guru land help me fix this problem.
I seems to be more then a simple computer to wireless security problem.  this is long get a cuppa and a cumfy seat and yes this did take me the better part of 1/2 a day to complete all this testing

I have the following computers
Mythbuntu 10.10 (custom built with 1 wirelss adapter)
Main desktop Ubuntu 10.10 (custom built with different wireless adapter)
Emachines netbook ubuntu netbook respin 10.10(different wireless adapter again)
compac laptop window 7 (yet another different wireless adapter)

setup wireless router to no encryption and all 4 machines connect and surf perfectly.  great

change wireless router to WAP2 with simple password (1234567890)
Window works great
3 X linux machines dont connect and keep asking for passowrd

Change router to WEP with simple password (1234567890) required 8-32 characgter password in wireless router.
Windows works great
3 X linux machines dont connect and keep asking for passowrd

Played around with letting linux autowlan connection and then type in passkey.  also tried editing connections and entering passkey in there and then try and connect.  Everytime I tried to connect a linux machine i disconnected and reconnect windows to prove that it was linux machine problem only and not something else.

Tried silly things like putting my keyring password and sudo password in where it asked for passkey instead of the passkey (just in case it was something that simple)  Still no luck.

To me it looks like something more then an individual adapter or computer or wireless router brand/model issue.
Reading through the various forums through the web searchs that I have done, it looks like wireless security is a little hit and miss still on linux.

I volentier my various machines and time to try and fault find the issue on all machines to help the developers to fix this problem on mine and I can document everything.  Hopefully this will help someone fix wireless security on Linux once and for all.

Just tell me what to do and i will do it.
Also do you want me to start a new thread as I dont want to highjack this one.

Cheers
chipppy

---

### Post by woodrow667 on 2011-01-24
chippy,

i'm right there with you. got the same issue. will be following you're thread very close.

Woody

---

### Post by chaozuper on 2011-01-25
chipppy, 

just use this thread, it basically is my question anyway. i look forward to hearing your results so we can finally get encryption going on ubuntu!

---

### Post by chipppy on 2011-01-25
Good Afternoon

I haven't had any luck fixing this one yet.  
I have cross  posted in the Security Forums 
([http://ubuntuforums.org/showthread.php?t=1675191]("http://ubuntuforums.org/showthread.php?t=1675191")), 
as I think that this is more security/encryption issue then wireless networking as we have proven that without the security/encryption function the wireless networks work.

Cheers
chipppy

---

### Post by dark fader on 2011-01-25
My issue is similar but tot exactly the same. I can connect to secure networks - unless they're hidden or ad-hoc. The result is the same - I am repeatedly asked for my password.

---

### Post by oj0kksn5 on 2011-01-25
Have any of you looked in the log files? if not could you post up the system (general) log file

[http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/) <- how to do this

---

### Post by thefasterblueone on 2011-01-25
> **bkratz said:**
> What type of encryption are you using?  Other people (including me) have had problems with having the wireless access point in combination mode ie. 
WPA and WPA2.  Try one or the other, but not the both setting on the AP.

> **chaozuper said:**
> Thanks for the reply. i'm using WEP encryption.

bkratz has good advice, use WPA2. I had the same problem when I was using WPA and WPA2 mixed mode. I kept getting disconnected and kept telling me "Bad Password".

I tried WEP and could not connect at all.

check your /etc/network/interfaces file, the only thing that should be there is
 ```
auto lo
iface lo inet loopback
```

Also WICD Network Manager is the best one to use.

goodluck :popcorn:

---

### Post by walt.smith1960 on 2011-01-25
I use WPA/WPA2 on desktop 10.10 and so far so good (crosses fingers and hopes not to jinx self) I did have an issue trying to connect to a WEP network with Windows a few years ago. There were two types of WEP passwords-hex and alpha numeric.  The access point & adapter had to be using the same type.  

The few times I've run into being repeatedly asked for my network password, it was usually after resuming from suspend and restarting fixed the problem. I haven't seen this for a couple months at least.

---

### Post by chaozuper on 2011-01-25
> **thefasterblueone said:**
> bkratz has good advice, use WPA2. I had the same problem when I was using WPA and WPA2 mixed mode. I kept getting disconnected and kept telling me "Bad Password".

Unfortunately, i can't use wpa2 because i have to use wep for my nintendo ds ;)

---

### Post by Beetlemma on 2011-01-25
bump 4 help

---

### Post by chaozuper on 2011-01-26
bump

---

### Post by chaozuper on 2011-01-27
c'mon please give something to shine light on this  situation. i've been stuck for almost a week now :(

---

### Post by chipppy on 2011-02-01
Good Evening

Sorry for the delay guys and girls.  I had a personal day at the beach that ended in 2nd degree sunburn and have been suffering since.  Enough of excusses

> 
check your /etc/network/interfaces file, the only thing that should be there is
Code:

auto lo
iface lo inet loopback

Checked this and all is as quoted

> I use WPA/WPA2 on desktop 10.10 and so far so good (crosses fingers and hopes not to jinx self) I did have an issue trying to connect to a WEP network with Windows a few years ago. There were two types of WEP passwords-hex and alpha numeric. The access point & adapter had to be using the same type. 
Good point I didnt know this.
How do I check this to confirm is they are set the same or different.
Ubuntu 10.10 OS
Billion BiPac 7401VGP R3 wireless router

> Have any of you looked in the log files? if not could you post up the system (general) log file

First I want to confirm the passwords as both the same type and if the problem still exists I will rerun all the testing after marking the log releavant log files and then paste all log file sections in here.

Cheers
chipppy

---

### Post by brianthefolksinger on 2011-02-02
same problem
able to connect through LAN though doesn't show on networkmanager but wireless won't work, WEP authentication window just keeps popping up
can't access router (Verizon FIOS) to alter anything so have to use WEP

note: open System>Administration>Log file viewer
look for daemon.log and todays date, keep it open and you can see what is happening and errors or what changes though I don;t understand 90% of it, sometimes it makes sense, and can copy relevant bits to post here

note: I know nothing, just quesswork and trial and error, over many years with computers under the hood
ok
got wireless to work by:
WEP authentication code is 128 bit key (not password), key is on a sticker on the router, BUT it is only 10 digits and 24 are required so enter it twice plus the first 4 digits, check box to see it so you know it is right.
now you may have a key or a password. only way I figured was trial and error. BUT have to make network manager and authentication window match, so openned system>preferences>network connections, chose wireless tab, identified my router ID (also on sticker) and selected it, opened it with edit, and chose (in my case) WEP 128 bit key and entered 24 digits as indicated above, then did the same in authentication window.
(also tried wep as password with 24 digits, 10 digits etc)
for me the above combo worked.. whatever, must match and do both

now wireless came on! yes, but internet stopped, on both wireless and LAN
(huh?)
ok, open firestarter firewall utility
  system>administration>firestarter
disabled firewall, always first possibility and yes, now wireless works, internet access, because the firewall has decided to block all traffic, including LAN that worked before when wireless didn't. whoopie
with firewall disabled and firestarter open you can click at bottom of window to view details and see ip address of router and port being used and note it down, may be handy later
so I personally dislike firestarter, have had problems with it before, configuring samba in LANs so axed it
start system>administration>synaptic package manager
search for firestarter and mark it for removal
then search for ufw, this is a firewall utility should already be installed, I mark gufw, the graphic interface for it for installation to replace firestarter
then make sure to disable firewall with firestarter then close firestarter than click to apply changes in synaptic , firestarter is removed and using ufw.
remeber to renable firewall at this point.. won't be able to tell if I fix it otherwise
still have the problem but assume I'll use gufw to identify router traffic and allow it, but decided to post this much at least since this may not be everyones problem, but I am at least making progress

back a few minutes later.. it worked, opened gufw (though you could probably just do this using firestarter still
system>administration>firewall configuration or firestarter

remember the ip address I got from firestarter for the router when the firewall was disabled and I looked at the details of traffic.. or you can get it from your router info pamphlet because it is the address used to access the router using the browser I think
using gufw, not sure how in firestarter but use same principle
anyway selected the rules box, clicked ADD, used the "simple" tab to create a rull to allow IN  - BOTH (tcp and Udp) from the Ip address of the router replacing the last digit with a 0/24 to indicate a range of addresses(ie 100.100.1.0/24) to cover both router and internet interfaces it labels in pc
it worked!. though oddly, connection is slower now then when it all didn't and the LAN cable was forcing a connection, that was real fast. 

of course, I may have opened a gaping security hole in my firewall but well can't have everything, as I said I know nothing but can swing a hammer and knock a hole in a wall. ma needs to access her email and nothing important on this computer. better working insecurely than not working. Might be nice to have someone who knows what they are doing indicate a more elegant solution.
peace to all, my hopes for the people of Egypt


note: in log file I was getting a lot of endless couplets
Joining mDNS multicast group on interface eth1.IPv4 with address (IP address)
IP_ADD_MEMBERSHIP failed: no buffer space available
seems to do it again every 2 seconds
that went away
good luck all

final note
I'm still having network problem, no persistent connection, I get 10 seconds of internet then it shuts down, have to switch back to the forced connect over a unmanaged LAN cable to download updates
I can use system monitor
System>administration>system monitor 
to watch the network, it bumps a few bytes every ten seconds exact for a couple minutes then bursts again for ten seconds. Even now the connection times out half the time trying to get to any website and everything is dead slow. As I recall I've had this problem with linux all along and it is network manager.. which is why I wonder it is still here, thought they had discontinued it. I should echo suggesting replacing it with wicd as I recall that as being a solution, but have never tried it, I always managed to make NM work each time but will have to look in my notes to recall how.. I think I had to enter in all the manual information into network manager like nameservers and static ips and hardware id numbers all of which can be seen in the daemon log file for your particular configuration. Maybe I'll try moving to wicd if there is a gui for it.
This seems to be a persistent weakness..maybe it is network manager or the driver for the pro1000/pro2100 wireless card (as I recall) or both. MAybe I need to refind and install that driver. remember it being a pain when I set up hardy and before with whatever it was.

good luck..maybe there should be an x40 specific thread/manual somewhere since we should have the same problems and solutions hmmm maybe there was one in wiki or somewhere. can't remember.

---

### Post by chiocken on 2011-02-19
I'm having a similar problem. The wireless icon cycles endlessly and I'm asking to enter my WPA/WPA2 password periodically. No internet access at all.

The strangest part is that it was working fine one minute, then wouldn't connect the next. I'm using another computer with the same OS on the same network and it works fine.

What should I be looking for?

---

### Post by meddyuk on 2011-02-27
Hiya Guys,

Thought i would add my 2 penneth! I've just literally gone out this morning and bought the Belkin N300 Dual Band USB for my Deskstation running Maverick Meerkat. At first i put the stick in and nothing happened. So i went to System>admin>Windows wireless drivers and clicked on there. I put the CD in the drive that came with the dongle and found the drivers folder on the disk. I then installed the .inf file in the XP folder. It connected straight away as easy as that.

I do have a slight problem in that every now and again, it loses conectivity and then asks me for my WAP password on connection, but then doesn't seem to connect. I unplug the dongle and then hit connect again and it connects. The signal strength isn't that great and im only 100m from the wireless modem in the other room.

im loathed to mess round with the settings as it works, albeit intermittently. I'll just wait and read the various replies.

meddy.

---

### Post by Cosworth32 on 2011-06-20
Same problem here. wifi has been running fine for 6 months and suddenly it fails to connect to both AP's in range (WEP & WPA2). reboot, wifi toggle etc doesn't help at all. The only way to connect is to run the laptop on batteries while connecting to the wifi!?!? Then it works for a day or two until it suddenly fails again.

---

