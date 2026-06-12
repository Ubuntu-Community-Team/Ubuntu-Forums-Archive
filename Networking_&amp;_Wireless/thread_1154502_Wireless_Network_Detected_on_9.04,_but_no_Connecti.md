---
title: "Wireless Network Detected on 9.04, but no Connection..."
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by fiveacez on 2009-05-09
I just installed 9.04, but I can't connect to my router using the wireless connection.  I should be able to because my computer is dual booted with Vista, and it works fine.

What I noticed was, I will type in my encryption key, hit connect, and a window will appear a few minutes later showing a different and longer encryption key than what I put in.  It's sending the wrong encryption key.    It will be in all numbers and lowercase letters a-f (possibly a hexidecimal code?).

What can I do to fix this?  I'm new to Linux, so I'm not very familiar with how to use the terminal yet (what all the commands mean).

---

### Post by chellrose on 2009-05-09
> **fiveacez said:**
> I just installed 9.04, but I can't connect to my router using the wireless connection.  I should be able to because my computer is dual booted with Vista, and it works fine.

What I noticed was, I will type in my encryption key, hit connect, and a window will appear a few minutes later showing a different and longer encryption key than what I put in.  It's sending the wrong encryption key.    It will be in all numbers and lowercase letters a-f (possibly a hexidecimal code?).

What can I do to fix this?  I'm new to Linux, so I'm not very familiar with how to use the terminal yet (what all the commands mean).

Are you using the terminal to connect, or a GUI (such as network manager)?

---

### Post by fiveacez on 2009-05-09
GUI...I don't know how to use the terminal to do much.

---

### Post by chellrose on 2009-05-09
> **fiveacez said:**
> GUI...I don't know how to use the terminal to do much.

Do you happen to know the name of the GUI program you're using?  And do you have Gnome, or KDE?

---

### Post by fiveacez on 2009-05-09
I'm using Network Connections (System => Preferences).

How do I tell if I'm using Gnome or KDE?

---

### Post by chellrose on 2009-05-09
By what you've described, it sounds like you're using Gnome.

The two look very different.  KDE4 has (by default) a dark blue panel (something like a Windows taskbar) at the bottom, and you access your main menu by the icon that looks like an arrow inside a blue circle.  The Gnome panel, on the other hand, is smaller, grey (unless you've changed it) and has 3 menus by default, "Applications", "Places", and "System".

Unless you installed Kubuntu (with the K), you likely won't have KDE by default.

As for the wireless... I haven't gotten mine up and running completely since the upgrade, but I'll see if I can offer some helpful suggestions...

First, a few questions:

1. Do you know what kind of wireless card you have?

2. Can you post the contents of your /etc/network/interfaces file?  You'll have to do this using the terminal, but I promise that it won't be too painful.  To avoid making this post too long and confusing, I'll write a new post with instructions, and explanations.

---

### Post by chellrose on 2009-05-09
If anything is unclear, just let me know.  On the other hand, if it's too simplistic, I apologize.  But since you said you aren't too familiar with the terminal, I'm trying to be fairly detailed...

Inside the terminal:

Step 1.

```
sudo cat /etc/network/interfaces
```

* The "sudo" gives you root permissions.  Being root means you can do anything... and I mean *anything*, so you should be very careful when you're root.
It will ask you for your password.

* The "cat" means "display the contents of this file".  You might need to maximize the terminal window to see the whole thing, but it shouldn't be too long.

Step 2: Copy the output and paste here, then highlight it and click the # sign so it will get code tags around it.
*Note: The key for your network _may_ be in that file.  Don't post that. :)

Hopefully that will shed some light on the situation.  Everyone's setup seems to be a little different.

---

### Post by fiveacez on 2009-05-09
here's what outputs

```
auto lo
iface lo inet loopback
```

---

### Post by chellrose on 2009-05-09
That's all?

Hmm...

Do you have a wired connection as well?  And does that work OK?

---

### Post by fiveacez on 2009-05-09
Wired connection works great.

---

### Post by fiveacez on 2009-05-09
Here's my wireless card:

Intel WiFi Link 5100 AGN and Bluetooth

---

### Post by chellrose on 2009-05-10
Okay...
Your setup seems to be a bit different than what I'm familiar with.  (Anyone else with knowledge of this type of setup should feel free to jump in anytime! :))

EDIT:  Before you try what I've posted below the line, try this (it may be easier): Open up your network GUI, click on the "Wireless" tab, select your network, and click "Edit".  Inside that, click on the "Wireless Security" tab, and that will give you a drop-down menu listing the different kinds of encryption keys.  Try something different than whatever it's currently set to; often the different types have different lengths for the keys.

--------------------------------------------------------------------------------

Can you post the output (in the terminal) of

```
ifconfig
```and

```
cat /etc/udev/rules.d/70-persistent-net.rules
```Note: It's possible that the "70" may be different on your machine -- in which case you can figure that out by typing

```
ls /etc/udev/rules.d
```(ls = "list contents").  If at any time you get a "Permission denied" error, just stick "sudo" in front of what you're trying to do.

---

### Post by fiveacez on 2009-05-10
I made sure it was the right encryption key type, but it just changes what I enter into the encryption key after I hit apply.

For this section of code, there was something about "eth0," but I didn't think that was needed here
```


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:ea:ba:11:ba  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-EA-BA-11-BA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

``````
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1e:68:ba:58:ff", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4237 (iwlagn)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:16:ea:ba:11:ba", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```

---

### Post by chellrose on 2009-05-10
Right, "eth0" is likely your wired connection.  "wlan0" is probably your wireless.

The only other idea I have is to try connecting from the terminal.  I'm not sure why that network manager is changing your key.

Are you using dhcp to connect?  You can find out by opening up that network manager again.  Click the Wireless tab, select your network, click Edit.  Click on the IPv4 Settings tab.  What does it say next to "Method"?

---

### Post by rob1701 on 2009-05-10
Hi
I am new to ubuntu, so forgive my newbness.
I seem to have this very same problem
the password changes to a load of alpha numerics.
 
When i click on the network icon, i see my router + others
click on my router, then i get the screen for the wpa wpa2 personal password
enter the correct password, it then sits there with the icon spinning, then after a minute or so, the password reappears, with a different password with random letters and numbers.
 
I have installed onto a Medion 96625 Laptop, dual boot with Vista Home Premium
The sound also doesnt work, but i can try and sort that if i can get the wireless working.
 
Ubuntu 9.04
GUI is Gnome
and the IPv4 setting is DHCP Auto
 
Also i get same response as Fiveacez when i type
sudo cat /etc/network/interfaces
 
output is
auto lo
iface lo inet loopback
 
Wired Connection works Perfectly, internet connects as soon as i plug the cable in.
 
Other than these 2 problems, everthing installed and works very well
This is the first time i have installed, so not very clued up on terminal etc
but i want to learn )
 
Anyway thanks for reading, and hopefully will get this thing working ))

---

### Post by chellrose on 2009-05-10
rob1701,

Can you also check if you're connecting via dhcp?  Instructions on how to do so are in the post above yours.

---

### Post by fiveacez on 2009-05-10
Yeah I'm using DHCP

---

### Post by promet on 2009-05-10
Double check the file:

/etc/resolv.conf

make sure that IP(s) of your DNS server(s) are listed in that file. Connection without name resolution implies missing dns listings. 

P

---

### Post by rob1701 on 2009-05-10
> **Sissy13 said:**
> rob1701,

Can you also check if you're connecting via dhcp?  Instructions on how to do so are in the post above yours.

In The IPv4 setting, the method is Automatic (DHCP)
all other options are ghosted
address
there is nothing listed, should there be? if auto detected

DHCP Client ID is not ghosted, and nothing is there either

loading etc/resolv.conf shows this

# Generated by NetworkManager
nameserver 192.168.1.1

and thats all (

the problem seems to me is that my router is refusing connection because of the password
being scrambled, so it will not give it the DHCP info.

Any clues as to why the password is being changed?

---

### Post by fiveacez on 2009-05-10
> **promet said:**
> Double check the file:

/etc/resolv.conf

make sure that IP(s) of your DNS server(s) are listed in that file. Connection without name resolution implies missing dns listings. 

P

There are 2 IPs listed after 2 "nameserver" labels.

---

### Post by fiveacez on 2009-05-10
> **rob1701 said:**
> In The IPv4 setting, the method is Automatic (DHCP)
all other options are ghosted
address
there is nothing listed, should there be? if auto detected

DHCP Client ID is not ghosted, and nothing is there either

typing
/etc/resolv.conf

its just says 
bash: /etc/resolv.conf: Permission denied

It's easier to just go File System => etc and scroll down until you see the file. Double click to open it.

---

### Post by rob1701 on 2009-05-10
hehe
i realised that one out as i sumbmitted the post
result is in prev post )
< total newb :confused:

this dam password thing is drivin me nuts

---

### Post by chellrose on 2009-05-10
I'm not familiar with what /etc/resolv.conf is supposed to do, so I'm going to leave that to promet.

The only other idea I have is to attempt a connection through the terminal.  Reason is that you can enter your key through the terminal and it should accept it as entered.

I can walk you through that if you'd like, but of course it would be useful to get your GUI interface working properly, so maybe it would be better to wait and see if promet has any comments on the /etc/resolv.conf.  I don't use the GUI myself, so I likely don't have any more suggestions there.  But let me know if you want to try the terminal.

---

### Post by fiveacez on 2009-05-10
Sure, lets try the terminal.

---

### Post by chellrose on 2009-05-10
OK.  I can't promise this will work, but it generally works for me.  Crossing fingers. :)

(rob1701: We need to figure out what name your wireless connection goes by before you try this.  If you want to try connecting from the terminal, can you first post the output of ```
cat /etc/udev/rules.d/70-persistent-net.rules
```?  Note that the "70" may be different on your system; use ls /etc/udev/rules.d to find the correct number.)

fiveacez: here's what to do.

1. Back up your /etc/network/interfaces file:
 ```
sudo cp /etc/network/interfaces ~/interfaces.bak
``` (this copies /etc/network/interfaces to a file called interfaces.bak in your home folder)
 
 2. Open your /etc/network/interfaces file:
 ```
gksudo gedit /etc/network/interfaces
``` (The "gksudo" gets you root privileges, but with a GUI.  gedit is a text editor.  You'll likely see a popup box asking you to enter your password again.  If you have a different favorite text editor, feel free to use that.)
 
 3. Add the following lines to the end of the file:
 ```
iface wlan0 inet dhcp
wireless-essid  <name of your network (case-sensitive, and without the angle brackets)>
auto wifi0
 
```Save and close the file.

4. In the terminal again:
```
sudo -i
```(This gets you a "permanent" root access.)

```
ifdown wlan0
iwconfig wlan0 key <enter your key here, again without the angle brackets>
ifup wlan0

```You should see messages that it's trying to connect... these will include DHCPREQUEST.  If the connection is successful, you'll see "DHCPACK received from..." (and some other stuff).  If not, it will eventually say something along the lines of "No requests in database... sleeping".  (That's from memory, so may not be exactly correct, but you'll definitely see the "sleeping".)

If your wireless signal is weak, you may need to try again a few times.  For a relatively strong signal, it *should* work the first time...

6. Clear your history (this will remove the key you entered from your terminal history, which is a good security measure).  You should still be root at this point.
```

rm .bash_history
history -c

```7. Exit your root session by typing "exit" in the terminal.

If this works, you can write a script to do most of this for you every time.  If it doesn't work, you should probably restore your original /etc/network/interfaces, hence the backup in step 1.  In either case, let me know how it goes...

---

### Post by fiveacez on 2009-05-10
When I get to the line to enter in my key, it says that my encryption key is an invalid argument.  

Am I supposed to replace "key"? (if so, was I supposed to do the same for wireless-essid for part 3?)

---

### Post by fiveacez on 2009-05-10
Okay....now it's working...I  was only able to do through the first 2 lines of code for step 4, but something must have worked.  Thanks!

---

### Post by chellrose on 2009-05-10
Oh, you got it to connect?  Fantastic! :D

No, you shouldn't have to replace "key".

Is your key WEP or WPA?

According to the man page for "iwconfig", the key needs to be in hex digits, either 8-digit or 16 digits separated into groups of 4 by dashes.

If your key isn't in hex, try adding "s:" (no quotes) before your key.  That is,

```
iwconfig wlan0 key s:xxxxx
``` (where "xxxxx" is your key)

---

### Post by fiveacez on 2009-05-10
What's really weird about this though, I deleted the stuff I was doing in gedit, and it STILL works.  So...I really don't know what just happened, but it magically decided to work now.

---

### Post by chellrose on 2009-05-10
The iwconfig bit must have been sufficient to do the trick, then.

Note that the key you entered is taken to be the "current" key... You shouldn't have to do it again, as long as you keep using the same network.  But if you want to use a different network, with a different key, you'll at least have to change the wireless-essid and do the iwconfig again.

FYI, if you use multiple wireless networks and don't want to change the wireless-essid in /etc/network/interfaces all the time, you can also do ```
iwconfig essid <network name>
``` in the terminal.

---

### Post by fiveacez on 2009-05-10
I only use one network that has a router password.  Every other network has an in-browser password.  Will I have to do something for those too, or will I not have to worry about it?  I won't know until I go back to campus in the fall.

---

### Post by chellrose on 2009-05-10
I think you'll just need to change the essid, and connect normally.  Then open your browser and you should be prompted for the password there.

---

### Post by fiveacez on 2009-05-10
Ok thanks.

---

### Post by rob1701 on 2009-05-10
[quote=Sissy13;7252651]OK.  I can't promise this will work, but it generally works for me.  Crossing fingers. :)

(rob1701: We need to figure out what name your wireless connection goes by before you try this.  If you want to try connecting from the terminal, can you first post the output of ```
cat /etc/udev/rules.d/70-persistent-net.rules
```?  Note that the "70" may be different on your system; use ls /etc/udev/rules.d to find the correct number.)

ok heres the output
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:40:d0:e5:16:a0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

seems only to see the network card (eth0) and not the wireless

thanks for the assistance ) glad you got yours working fiveacez )

---

### Post by chellrose on 2009-05-10
That's odd that your wireless card isn't showing up.  But you say it's detected by the network connections applet?

Do you know what kind of wireless card you have?

Did you just recently install Ubuntu?  You say you're new to Ubuntu -- were you using a different Linux distro previously, or a different OS entirely (e.g. Windows or Mac)?

---

### Post by rob1701 on 2009-05-10
I am totally new to linux / ubuntu. i am trying it, as i am getting fed up with vista

I have it installed as a dual boot system now, with vista
I have no idea what wireless card is inside, The laptop is a medion 96625
Is there any command that will query it?

Yes, the network gui seems to see it, as it sees all the routers in my area
i also installed wifi radar, and that also sees it, but still wont connect

also
when i look under system> administartion>network tools
and hit the drop down menu for devices
it says
Loopback Interface (lo)
Ethernet Interface (eth0)
Unknown Interface (ra0)
Unknown Interface (pan0)

i think ra0 it prob the wireless, but not detected properlly, maybe driver issue?

again thanks for help )

---

### Post by chellrose on 2009-05-10
In a terminal, type

```
sudo lspci
```

(you'll need to enter your password).

That will spit out a long list of devices, one of which will hopefully be your wireless card.  Look through that and see if one of them mentions "wireless".

---

### Post by rob1701 on 2009-05-10
02:00.0 Network controller: RaLink RT2860
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

it dosnt say wireless but i think its the Ralink rt2860  .... (ra0)

---

### Post by chellrose on 2009-05-10
I think you're correct on the ra0.  At least it's getting recognized somewhere.

In the terminal, try

```

sudo -i
iwconfig ra0 essid <name of your network, case-sensitive, no angle brackets>
iwconfig ra0 key <enter your key, again with no angle brackets>
ifup ra0
rm .bash_history
history -c
exit

```

(Those last three lines clear the key from your terminal history, and log you out of your root-access session.  Very important.)

---

### Post by rob1701 on 2009-05-10
iwconfig ra0 essid <name of your network, case-sensitive, no angle brackets>
response is
iwconfig: unknown command "second word"
my essid is two words with a space in it

iwconfig ra0 key <enter your key, again with no angle brackets>
response is
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "password"

---

### Post by chellrose on 2009-05-10
Try enclosing your network name in quotes, then, i.e.

```
iwconfig ra0 essid "network name"
```

---

### Post by rob1701 on 2009-05-10
it accepts the name now
but same responce with key
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "password".

---

### Post by chellrose on 2009-05-10
Add "s:" in front of your key, e.g.

```

iwconfig ra0 key s:mykey

```

but replace "mykey" with your actual key.

---

### Post by rob1701 on 2009-05-10
yes that worked

here are responces fromlast commands

root@ubuntu:~# ifup ra0
Ignoring unknown interface ra0=ra0.
root@ubuntu:~# rm ,bash_history
rm: cannot remove `,bash_history': No such file or directory
root@ubuntu:~# history -c
root@ubuntu:~# exit
logout
rob@ubuntu:~$ 


grrr just noticed i hit comma for the rm .bash_history grrrr

its getting late

still not working ((

thank you again for the time and patience, trust me to get a laptop that dont wanna work ( lol

---

### Post by chellrose on 2009-05-10
That's a dot, not a comma, ".bash_history"

As for the ifup -- maybe check your connection again, anyway?  fiveacez seemed to be able to get it to work without the "ifup" part.

If it still doesn't work, then I'm afraid I'm out of ideas.  You might try searching the forums, and Google, for "RaLink RT2860 drivers in Ubuntu", or something similar.

---

### Post by rob1701 on 2009-05-10
yep, i noticed the error 

no problem, thank you for all your help

i will look for drivers tomorrow

---

### Post by promet on 2009-05-10
re: /etc/resolv.conf

...is where the data for your working DNS servers is stored, i.e. the computer(s) which will be doing your domain-name translations. If this file is empty, in most cases, it means you won't be able to "resolve" (thus the file name ;) ) domain names into ip addresses. 

So, you could be connected to the Internet, but when you put a domain name into your browser, i.e. [http://ubuntuforums.org](http://ubuntuforums.org), there is no DNS server available to convert (resolve) that "name" into that IP address (91.189.94.12) on the internet and retrieve the page at that address back to your browser. 

If there are two addresses in that file each after the designation "nameserver" you're probably good, assuming those two adresses are currently operating...

=D

---

### Post by sarwiz on 2009-05-11
Am also working on this same problem, and I don't even have that file in my /ect/. 9.04 found my card, and shows a list of networks to connect to, but will not connect.

---

### Post by matthewbpt on 2009-05-11
> **rob1701 said:**
> 02:00.0 Network controller: RaLink RT2860
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

it dosnt say wireless but i think its the Ralink rt2860  .... (ra0)

ra0 is indeed the wireless interface, and the reason you can't connect to the network is because there is a bug in the wireless driver for your card included in ubuntu which prevents is from connecting to WPA/WPA2 networks, details of the bug are on launchpad [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339891](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339891) . To solve the problem you basically have to install a previous version of the driver, here is a copy/paste of the instructions from another forum post.

> A solution involves downgrading the RT2860 driver to version 1.7.1.1 (the last know fully working driver). It seems to work much more reliably for me at least on 1000h.

1) Get the driver from [http://www.array.org/ubuntu/dists/intrepid/eeepc/binary-i386/rt2860-dkms_1.7.1.1_all.deb](http://www.array.org/ubuntu/dists/intrepid/eeepc/binary-i386/rt2860-dkms_1.7.1.1_all.deb)

2) Go to terminal, and move the pre-installed driver so it won't get loaded.

cd /lib/modules/2.6.28-11-generic/kernel/drivers/staging/rt2860/
sudo mv rt2860sta.ko rt2860sta.bak


3) Install rt2860-dkms_1.7.1.1_all.deb. It will also install dependencies needed to compile the driver. If it doesn't retrieve the right packages, make sure "build-essential", "linux-header-generic" and "dkms" is installed. Let it run and it should complete without a problem.

4) Restart. The new driver should work automatically.

I hope this helps, I recently had the same problem as my laptop also has this wireless card.

---

### Post by promet on 2009-05-11
No "/etc/resolv.conf"? Hmmm. Well, that is interesting...
 
I wonder...did you do a fresh install, or upgrade from an existing 8.10 or earlier? Perhaps that's got something to do with my issue, i.e. a new method of networking in 9.04 that doesn't rely on the "traditional" config files.
 
If that's so, boy, could have done with a little heads up on that...;)
 
p.s. if anyone else can confirm the lack of an "/etc/resolv.conf" file, if you happen to check, I would appreciate it. 
 
Cheers
p

---

### Post by chili555 on 2009-05-11
> if anyone else can confirm the lack of an "/etc/resolv.conf" file, if you happen to check, I would appreciate it.I am not at all certain the file exists until you connect by DHCP and are given nameservers by the DHCP server. If you connectwith a static IP, it's up to you to supply the nameservers. ("If you're smart enough to know how to use static IP's, then your smart enough to figure out DNS.")

There is nothing at all wrong with just writing your own:```
sudo gedit /etc/resolv.conf
```By the way, it's not [COLOR="Red"]/ect[/COLOR] and its not resolv[COLOR="Red"]e[/COLOR]. Add a single line:```
nameserver 192.168.1.1
```In this example, I used the IP address of the gateway, which generally works perfectly.

Proofread, save and close gedit.> a new method of networking in 9.04 that doesn't rely on the "traditional" config files.If you use Network Manager, which is installed by default, it keeps all the configuration files. I hate it and remove it immediately; however, that's not the best strategy for everybody.

---

### Post by chellrose on 2009-05-11
> **promet said:**
> 
p.s. if anyone else can confirm the lack of an "/etc/resolv.conf" file, if you happen to check, I would appreciate it. 
 
Cheers
p

I have a non-empty /etc/resolv.conf.  (I just did a fresh install because my previous upgrade didn't work correctly.  However, I also had a non-empty /etc/resolv.conf before re-installation.)

But, I do use DHCP... although, the file on my fresh install seems to have been generated by Network Manager (haven't had a chance to re-configure things yet! :) )

Hope that's at least infinitesimally helpful.

---

### Post by promet on 2009-05-11
Hmmm...the plot thickens...
 
[IMG]http://prometx.homelinux.org/images/rathbone-Sherlock-Holmes.jpg[/IMG]

---

### Post by chellrose on 2009-05-11
:mrgreen:

Well, if anyone can figure it out, Sherlock can!

---

### Post by rob1701 on 2009-05-11
> **matthewbpt said:**
> ra0 is indeed the wireless interface, and the reason you can't connect to the network is because there is a bug in the wireless driver for your card included in ubuntu which prevents is from connecting to WPA/WPA2 networks, details of the bug are on launchpad [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339891](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339891) . To solve the problem you basically have to install a previous version of the driver, here is a copy/paste of the instructions from another forum post.
 
 
 
I hope this helps, I recently had the same problem as my laptop also has this wireless card.
 
I will try this tomorrow, havn't had chance tonight (
 
and let you know the outcome, but sounds promising )

---

### Post by sarwiz on 2009-05-11
On it now as I type. Had to delete my network, then connect as if it was the first time, and it asked for the password severall times, and finally connected. Late now and have to work in the morning, but I'll poke around tomorrow night and see if I can retrieve some settings in here and post them. This is a new computer and a fresh install of 9.04. Tried 7.10 on up and this is the only one that would install. Thanks for all your help, and I'll be back on tomorrow night.

---

### Post by rob1701 on 2009-05-12
YES!!
It finally works after installing the older drivers :)

Thank you for the help all, much appriciated

Looking into sound problem now, i'm just glad this is working

Cheers

---

### Post by physeetcosmo on 2009-06-24
> **fiveacez said:**
> What I noticed was, I will type in my encryption key, hit connect, and a window will appear a few minutes later showing a different and longer encryption key than what I put in.  It's sending the wrong encryption key.    It will be in all numbers and lowercase letters a-f (possibly a hexidecimal code?).

fiveacez-

The reason that your key comes back as only numbers is that the Network Manager changes your key to HEX. Thus if you were to multiply the number of characters you originally entered by 2, you'd get the number of hex characters that are present.

What computer system are you trying to connect to your router with? Also, what encryption are you using to connect to your router, is it WEP or WPA?

I have an eeePC1000 and I am seeming to find that the RaLink wireless card doesn't support WPA through Ubuntu. The reason is that RaLink isn't opensource, same with Level 1 and thus the problems for driver development.

Good luck!:D

---

### Post by Tankerdog2002 on 2009-09-16
I had the same problem. Network detected, but no Connection.... nm keeps asking for password.... Can't keep connected....nm keeps losing password and changing key to HEX gobbley-gook. I tried everything under the sun.

In the end; The fix was so simple I smacked my forehead when I figured it out.

See this thread: Solved: Network manager scrambles WPA passkey
[http://georgia.ubuntuforums.org/showthread.php?p=7961409#post7961409](http://georgia.ubuntuforums.org/showthread.php?p=7961409#post7961409)

---

### Post by promet on 2009-09-17
Don't be confused by the hex key being in that field. I believe, confusingly, that nm automatically converts that field to the hex value for the passphrase. 

So, while you may enter "Jupiter" for your passphrase, next time you look into that particular nm text field, you will actually be seeing the hex value of "Jupiter" rather than the passphrase "Jupiter" itself. Just know that it is the hex equivalent. 

I was very confused by this myself at one point. This may not be a foolproof observation, but I believe that to be the case. So don't assume that because you see a hex value there that it is, for that reason only, incorrect; i.e. there is likely another reason for the network issue, other than the weird passphrase/hex key conversion that nm apparently does by default here. 

I wish the nm developer would change that though, cuz it's a pisser... ;) no disrespect to the valiant developer(s) themselves, just the observation of someone who spent way too much time coming to that realization...

Just a hopefully helpful tip

---

### Post by Tankerdog2002 on 2009-09-19
No confusion with the hex key .......it just pisses me off that I have to verify that it isn't actually part of the problem. You never know with this stuff so you have to check everything. 



The little tick box "available to all users"  is what actually solved the problem on all of our new notebooks at the office

---

### Post by promet on 2009-09-20
Ahhhh, "Available to all users", I hadn't encountered that issue, but that is very good to know, thanks for pointing that out. I am glad you've got things going.

Also, I am ecstatic to hear that you are using Ubuntu in an office environment, fantastic! =D>

---

### Post by caspertk on 2009-09-20
ok i tried changing the contents of the file interfaces, and it didnt work. now i cant put it back to its original contents. It tells me that i dont have the permision to do so. This is driving me nuts. Some1 please help.

Wireless card 5100 
Ubuntu/Linux 9.04
Toshiba Satelite A305

---

### Post by promet on 2009-09-20
> **caspertk said:**
> ok i tried changing the contents of the file interfaces, and it didnt work. now i cant put it back to its original contents. It tells me that i dont have the permision to do so. This is driving me nuts. Some1 please help.

Wireless card 5100 
Ubuntu/Linux 9.04
Toshiba Satelite A305

By "the file interfaces", do you mean the file "/etc/network/interfaces"?

If so, you need to edit that file as root (superuser, "su"). So you have to run whatever editor you're trying to correct that file with as the "root" (administrative) user. 

To run a process as "root" using the "sudo" command (I actually use "gksudo" for visual, "desktop" Apps, and "sudo" for command-line apps), open up a terminal window and type the following command:


```
gksudo gedit /etc/network/interfaces &
```


This will popup a window, in which you'll put your administrator ("root") password and, in turn, that window will launch a root-permission instance of the Gedit text editor, in which you can make whatever changes you think are necessary.

Also, it's not such a bad idea, to make a custom launcher on your gnome-panel with a "gksudo-ed" text editor so you can just click an icon when you need to get down and dirty with editing system files, instead of opening up terminals and typing commands, if you're less comfortable with that.

NOTE: Always make a backup before you start rewriting your config files, it not too difficult to have things get out of hand...

Cheers!
:P

---

### Post by caspertk on 2009-09-21
Many thanks. Now to back to getting my wifi to work...ugh!!!!

---

### Post by sarraceno on 2009-09-28
Ppl, I had the same issue...
My distro is: Ubuntu 9.04 Server

I found the solution...
just defining channel... dummm

interfaces:
--------------
iface wlan0 inet static
address 192.xxx.xxx.111  
gateway 192.xxx.xxx.1    
netmask 255.255.255.0   
broadcast 192.xxx.xxx.255
dns-nameservers 192.xxx.xxx.1
dns-search xxxxxx.xx

wireless-key s:xxxxxxxx
wireless-channel 8
wireless-essid "mixxxxxu"

auto wlan0
-------------------------

Nevertheless I still have the following error:
-------------------------
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
-------------------------

The not less dumm is during the battle, two days ago I did found why this error... now I do not remember... anyone knows how to? It's the only thing missing, nevertheless now my wlan0 is working.

By the way:
lspci: Network controller: RaLink RT2561/RT61 rev B 802.11g

---

### Post by hxleet on 2009-09-28
I think it might be encryption settings/key. Try without encryption, and see if it works.

I beleive the problem might be  with the file keys-ath0
by removing the file keys-ath0 and adding WEP={key}
in the file ifcfg-ath0 instead might solve the problem
Also try changing the file key-ath0 by removing the *s:*  in 
key=s:{key} to key={key} might solve problem
good luck hope this helps some

hxleet

---

### Post by physeetcosmo on 2009-10-07
> **rob1701 said:**
> I will try this tomorrow, havn't had chance tonight (
 
and let you know the outcome, but sounds promising )

Ladies and Gentlemen, I have dealt with this issue as well. I am using a RaLink rt2860 wireless card, from which the **version** of the driver is what is killing the connection for my wireless card to connect to a WPA-encrypted network.

My eeePC will connect if I change my router to ONLY use either WPA version 1 **or** version 2....NOT mixed-mode of "either" mode.

There is also a work-around where the wireless card driver can be reverted to an earlier version as well. Not sure where I saw that post, let me look for it and I'll post a link.

Maybe this will help someone as well? Couldn't hurt to change the router settings and see if that helps.

Ubuntu staff: it might be a good idea to distribute any newer distros with this earlier RT2860 driver until RaLink figures out why this newer version doesn't connect to WPA networks? Just a suggestion....

---

