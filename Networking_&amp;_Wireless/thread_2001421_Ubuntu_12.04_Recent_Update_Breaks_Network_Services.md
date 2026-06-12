---
title: "Ubuntu 12.04 Recent Update Breaks Network Services"
date: 2012-06-10
forum: Networking &amp; Wireless
---

### Post by drewski22785 on 2012-06-10
All,

I recently updated ubuntu using the automatic update and it broke my network services. Luckily, after a lot of research and history I found the solution and want to post it for everyone who runs into this issue.

For starters after the upgrade when turning the computer on I got the message "Waiting for network configuration" and "waiting up to 60 more seconds for network configuration"

After it finally booted i had no network access wireless or on the lan. When i tried opening the network tool i got the error "The system network services are not compatible with this version"

FInally the fix that I came up with:

There appears to be an issue with the latest update of network manager. If you open software center, go to history, search keyword "Network" you will probably see "network-manager (0.9.4.0-0ubuntu4, 0.9.4.0-0ubuntu4.1)"

If you see this then you have the same problem as I did. The solution is to downgrade to version 3: Search in google "ubuntu network-manager package" and select the ubuntu.com link -> scroll down the page to "network-manager-dbg" select the precise (debug) ubuntu3 version.

[http://packages.ubuntu.com/precise/network-manager-dbg](http://packages.ubuntu.com/precise/network-manager-dbg)

Download the 4 related packages for your system (amd64 or i386):

network-manager (= 0.9.4.0-0ubuntu3)
    network management framework (daemon and userspace tools) 
or libnm-util2 (= 0.9.4.0-0ubuntu3)
    network management framework (shared library) 
or libnm-glib4 (= 0.9.4.0-0ubuntu3)
    network management framework (GLib shared library) 
or libnm-glib-vpn1 (= 0.9.4.0-0ubuntu3)
    network management framework (GLib VPN shared library)

install each of them using the command "sudo dpkg -i FILENAME"

restart your computer and that should fix your problem! I hope this helps some and for those of you in the know can you please report this most recent update as broken? Thanks and good luck!

---

### Post by Jukka76 on 2012-06-12
Yes I upgraded today, had same messages and network stopped working. Same error from network tool. 
I'll try your suggestion.

My hw is Gigabyte GA-E7AUM-DS2H with integrated     Realtek 8211CL chip (10/100/1000 Mbit) 

Using 12.04 32-bit.

---

### Post by Jukka76 on 2012-06-12
Worked for me also, thank you dwerski!

Downgrading these packages fixed also my broken bluetooth, logitech dinovo edge wasn't working after the upgrade.

Is there a bug reported for this issue?

How I can set not to upgrade these packages until problem is fixed?

---

### Post by Belayneh Arega on 2012-06-13
currently while trying to down grade and install network manager am facing "dependency message" which could not let me complete the installation after trying to install the four files in different sequence it seems to work(no error message appeared)but nothing changed after I install and restart the system

---

### Post by sk8 on 2012-06-13
apply the dependency package prior to install the network-manager package.

---

### Post by martinro on 2012-06-21
Thanks for this.

However as this was a desktop machine on ethernet instead of reverting to a previous version I disabled NetworkManager as per [http://www.liberiangeek.net/2012/03/disable-network-manager-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2012/03/disable-network-manager-in-ubuntu-11-10-oneiric-ocelot/) except I changed the last edit to:- 

iface eth0 inet dhcp

---

### Post by chslaxcoach on 2012-07-02
This worked for me also.

This little script might save people from a lot of annoying clicking around.

```

wget http://mirror.pnl.gov/ubuntu//pool/main/n/network-manager/network-manager_0.9.4.0-0ubuntu3_i386.deb
wget http://mirror.pnl.gov/ubuntu//pool/main/n/network-manager/libnm-util2_0.9.4.0-0ubuntu3_i386.deb
wget http://mirror.pnl.gov/ubuntu//pool/main/n/network-manager/libnm-glib-vpn1_0.9.4.0-0ubuntu3_i386.deb
wget http://mirror.pnl.gov/ubuntu//pool/main/n/network-manager/libnm-glib4_0.9.4.0-0ubuntu3_i386.deb

```

After that, I'm 99% sure installed them in this order without any dependency issues:

libnm-glib-vpn
libnm-glib4
libnm-util2
network-manager
network-manager-dbg

---

### Post by braddjwinter on 2012-07-05
Thanks!!! Since the internet wasn't working because of this, and i was on a virtual machine, i had manually download the .deb files using the host machine, create an iso image containing them (the amd64 versions) and mount it.. but then installing them in the right order (as chslaxcoach described) worked!

i have one more question...

> **Jukka76 said:**
> 
How I can set not to upgrade these packages until problem is fixed?

---

### Post by dceola on 2012-07-19
good morning,
 
I just ran into this issue this morning on my 12.04 ssytem. The system was freshly installed two days ago, and the update that broke it apparently came down to it yesterday. The thing is - my networking is working fine (ie I can browse the net fine, and I can use remote desktop to it) but I can't get the network manager gui interface to work. I tried installing the packages listed in the OP here, rebooted the system and saw no change. 
 
If it's relevant, the system is a virtual system on a vmware esxi host. Anyone have a suggestion for what I should attempt to do?
 
edit:
 
I seem to have fixed the issue, or it fixed itself; one of the two...  After attempting to install the above packages (and it not working properly) I of course kept searching google.  I found a page that said the person checked the available updates (of which there were avail updates for the networking stuff) which I allowed to install, then I rebooted (twice, actually; not sure the second time was actually necessary though). I confirmed there was no avail updates, then installed the above packages in the order that chslaxcoach mentioned, rebooted a couple more times and it started working properly.

---

### Post by jdeca57 on 2012-07-22
I... fail to see how one can google and download packages when the network is down. So, the real answer is to make a backup, install 12.04 from scratch and hope that an upgrade doesn't break the system - again? I don't know, but that doesn't feel fixed for me.

---

### Post by dceola on 2012-07-23
In my case, the network connectivity was functioning correctly, but I couldn't change any of the settings (network mgr interface wasn't working).
 
I previously stated that I performed the steps suggested in this post which fixed the issue for me, however this fix was only temporary.  I turned the system on this morning and now the networking isn't functioning again.  However this time it's quite the opposite situation of what it was for me the first time.  The network manager app is working, but my network connection is not.
 
It seems as though the system decided to install the updates again... Hopefully disabling the automatic updates installation this time will keep it from happening again.

---

### Post by bramin on 2012-08-04
> **chslaxcoach said:**
> This worked for me also.

This little script might save people from a lot of annoying clicking around.

```

wget http://mirror.pnl.gov/ubuntu//pool/main/n/network-manager/network-manager_0.9.4.0-0ubuntu3_i386.deb
wget http://mirror.pnl.gov/ubuntu//pool/main/n/network-manager/libnm-util2_0.9.4.0-0ubuntu3_i386.deb
wget http://mirror.pnl.gov/ubuntu//pool/main/n/network-manager/libnm-glib-vpn1_0.9.4.0-0ubuntu3_i386.deb
wget http://mirror.pnl.gov/ubuntu//pool/main/n/network-manager/libnm-glib4_0.9.4.0-0ubuntu3_i386.deb

```

After that, I'm 99% sure installed them in this order without any dependency issues:

libnm-glib-vpn
libnm-glib4
libnm-util2
network-manager
network-manager-dbg

Couldn't even install fist libnm-glib-vpn from usb stick. Server said "this version is outdated" in details it said "need to delete 20 objects and update 10". Since no mention of deleting anything has been mentioned I was afraid to do that to all 20 of the objects manually. Still unconnected to the internet with my server and seems others would be having trouble with this update too. Any other suggestions?

---

### Post by pztrick on 2012-08-20
> **chslaxcoach said:**
> This worked for me also.

This little script might save people from a lot of annoying clicking around.

```

wget http://mirror.pnl.gov/ubuntu//pool/main/n/network-manager/network-manager_0.9.4.0-0ubuntu3_i386.deb
wget http://mirror.pnl.gov/ubuntu//pool/main/n/network-manager/libnm-util2_0.9.4.0-0ubuntu3_i386.deb
wget http://mirror.pnl.gov/ubuntu//pool/main/n/network-manager/libnm-glib-vpn1_0.9.4.0-0ubuntu3_i386.deb
wget http://mirror.pnl.gov/ubuntu//pool/main/n/network-manager/libnm-glib4_0.9.4.0-0ubuntu3_i386.deb

```After that, I'm 99% sure installed them in this order without any dependency issues:

libnm-glib-vpn
libnm-glib4
libnm-util2
network-manager
network-manager-dbg

+1. Installing those packages in that order resolved my networking issues.

(I did have to download the amd64 packages instead of the i386.)


edit 8/22: i have also locked the packages in Synaptic Package Manager so that i don't get inadvertently update to the bad version again.

---

### Post by IndieRockSteve on 2012-08-20
> **chslaxcoach said:**
> This worked for me also.

This little script might save people from a lot of annoying clicking around.

```

wget http://mirror.pnl.gov/ubuntu//pool/main/n/network-manager/network-manager_0.9.4.0-0ubuntu3_i386.deb
wget http://mirror.pnl.gov/ubuntu//pool/main/n/network-manager/libnm-util2_0.9.4.0-0ubuntu3_i386.deb
wget http://mirror.pnl.gov/ubuntu//pool/main/n/network-manager/libnm-glib-vpn1_0.9.4.0-0ubuntu3_i386.deb
wget http://mirror.pnl.gov/ubuntu//pool/main/n/network-manager/libnm-glib4_0.9.4.0-0ubuntu3_i386.deb

```

After that, I'm 99% sure installed them in this order without any dependency issues:

libnm-glib-vpn
libnm-glib4
libnm-util2
network-manager
network-manager-dbg

you forgot 
```
wget http://mirror.pnl.gov/ubuntu//pool/main/n/network-manager/network-manager-dbg_0.9.4.0-0ubuntu3_i386.deb
```

while this works to get connected, it still seems as though all services that require a network connection fail to start.

---

### Post by brouhaha on 2012-08-24
> **drewski22785 said:**
> All,

If you see this then you have the same problem as I did. The solution is to downgrade to version 3: 

Thanks for pointing this out. I had the same problem, however a simpler solution worked for me. 

First I checked whether network manager is working at all. Just type:
```
nmcli -f all -p nm status
```

Turns out, my NetworkManager was not running. This can be fixed easily by simply typing:
```
sudo NetworkManager
```

Voila! Hellooo internet!!

---

### Post by Amine3333 on 2012-08-25
> **drewski22785 said:**
> All,

I recently updated ubuntu using the automatic update and it broke my network services. Luckily, after a lot of research and history I found the solution and want to post it for everyone who runs into this issue.

For starters after the upgrade when turning the computer on I got the message "Waiting for network configuration" and "waiting up to 60 more seconds for network configuration"



I have exactly the same problem:), however I still can connect from Ubuntu but after calling "pppoeconf" many times, it is kind of frustrating

I'm new at Ubuntu and I tried your solution but I guess I'm doing something wrong, when ever I try to install one of those packages I get the message "ldconfig deferred processing now taking place", any help on this ???

here is the output of trying to install one of the packages
```
(Reading database ... 244590 files and directories currently installed.)
Preparing to replace libnm-util2 0.9.4.0-0ubuntu3 (using libnm-util2_0.9.4.0-0ubuntu3_i386.deb) ...
Unpacking replacement libnm-util2 ...
Setting up libnm-util2 (0.9.4.0-0ubuntu3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```

---

### Post by brouhaha on 2012-08-26
Hello again,

As I said in my previous post, my NetworkManager wasn't running. So I could start it up everytime I logged in, but I still got the same messages while booting:

"Waiting for 60 more seconds... "
and
"Booting without full network configuration."

The following hack(?) worked for me:

1. Edit /etc/network/interfaces file as a root. 
2. Make sure it contains only the following two lines:
```

auto lo
iface lo inet loopback

```

Now everything works well upon startup. 

I obtained this information from [this blog post]("http://www.necopost.com/2012/06/network-manager-not-running-error-on.html").

Cheers!

---

### Post by Bucky Ball on 2012-08-26
@ [drewski22785]("http://ubuntuforums.org/member.php?u=1649844"): Please mark thread 'Solved', if it is, from Thread Tools at top right to help others. Cheers.

---

### Post by mgregrose on 2012-08-26
I am very new to all this, but when I updated to 12.04 I have this issue.  The version I had was not 9 but 8 in the items below.  It did not work, so I am still not connected.  Any suggestions?   I don't have the full 12.04 on a USB and the Dell Inspiron is using an intel chip set.  Thanks.
 
> **drewski22785 said:**
> All,
 
I recently updated ubuntu using the automatic update and it broke my network services. Luckily, after a lot of research and history I found the solution and want to post it for everyone who runs into this issue.
 
For starters after the upgrade when turning the computer on I got the message "Waiting for network configuration" and "waiting up to 60 more seconds for network configuration"
 
After it finally booted i had no network access wireless or on the lan. When i tried opening the network tool i got the error "The system network services are not compatible with this version"
 
FInally the fix that I came up with:
 
There appears to be an issue with the latest update of network manager. If you open software center, go to history, search keyword "Network" you will probably see "network-manager (0.9.4.0-0ubuntu4, 0.9.4.0-0ubuntu4.1)"
 
If you see this then you have the same problem as I did. The solution is to downgrade to version 3: Search in google "ubuntu network-manager package" and select the ubuntu.com link -> scroll down the page to "network-manager-dbg" select the precise (debug) ubuntu3 version.
 
[http://packages.ubuntu.com/precise/network-manager-dbg](http://packages.ubuntu.com/precise/network-manager-dbg)
 
Download the 4 related packages for your system (amd64 or i386):
 
network-manager (= 0.9.4.0-0ubuntu3)
network management framework (daemon and userspace tools) 
or libnm-util2 (= 0.9.4.0-0ubuntu3)
network management framework (shared library) 
or libnm-glib4 (= 0.9.4.0-0ubuntu3)
network management framework (GLib shared library) 
or libnm-glib-vpn1 (= 0.9.4.0-0ubuntu3)
network management framework (GLib VPN shared library)
 
install each of them using the command "sudo dpkg -i FILENAME"
 
restart your computer and that should fix your problem! I hope this helps some and for those of you in the know can you please report this most recent update as broken? Thanks and good luck!

---

### Post by Bucky Ball on 2012-08-26
@Mcgregrose: I suggest you start a new thread with a descriptive title rather than attempting to get help twenty posts deep on someone elses. ;) 

You will get more help that way. It gets confusing for helpers and the OP when threads get hijacked. Thanks.

BB

---

### Post by Melodie on 2012-11-18
Hello,

I am using a system built on Ubuntu 12.04 Mini. I installed all xorg and xserver-xorg packages, all drivers, authentication packages and so forth. It's my 3rd or 4th install of the kind. I use Openbox as main environment, lightdm as session manager.

I arrived here after I searched the web for a 60 seconds delay to connection problem in my Ubuntu Precise box.

I first met with this bug report:
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/881079](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/881079)

and I was frustrated because the Ubuntu version where it happens is the preceding one.

However I first had wicd-gtk installed and after I read the bug report I replaced it with network-manager. The problem was still there : 60 more seconds delay at boot and no network working once the desktop was on screen.

So I sought for the same error message on the web, but for Precise, and here I am after I found the present thread !

I have reinstalled the former packages as said in the first post of this thread.

Here are the packages I have in the Downloads directory:
> -rw-rw-r-- 1 melodie melodie   85390 avril 12  2012 libnm-glib4_0.9.4.0-0ubuntu3_i386.deb
-rw-rw-r-- 1 melodie melodie   14226 avril 12  2012 libnm-glib-vpn1_0.9.4.0-0ubuntu3_i386.deb
-rw-rw-r-- 1 melodie melodie  135104 avril 12  2012 libnm-util2_0.9.4.0-0ubuntu3_i386.deb
-rw-rw-r-- 1 melodie melodie  527750 avril 12  2012 network-manager_0.9.4.0-0ubuntu3_i386.deb
-rw-rw-r-- 1 melodie melodie 1331728 avril 12  2012 network-manager-dbg_0.9.4.0-0ubuntu3_i386.deb


Just a hint : to download them with wget, it is not necessary to add one "wget" line for each package : they can be all added one after the other, with just a space separating each URL.

Another hint : provided you have only these deb files in the Download directory, or in another directory of your choice, you don't need to worry about the order in which you will install them if you invoke this command line:
```
sudo dpkg -i *.deb
```

dpkg will manage to install them all in the right order, always.

One last hint, for who wants to block the versions of these packages:
open Synaptic, find the package names with the search field, select them (Ctrl+click or Shift+click can allow selecting several at a time) and then go to menu "Packages" then hit "Block the version". You're done, now you should see a small icon looking like a lock in front of the names of the said packages. 

After I installed the former version I rebooted and good surprise ! This time network manager was started !

But I still have a 60 seconds delay for network during boot, which I don't know why.

I connect with wired cable, on an Adsl connection, with the interface Eth1.

My Ethernet card is:
> $ lspci | grep Ethernet
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
...


I won't quote my wireless card, as I didn't try it yet. (One problem at a time... right ?)

"sudo lshw" provides the information about the driver for this card:
**e1000e**

However, lspci seems to indicate that it is NOT used (?)
```
$ lsmod | grep e1000e
e1000e                139997  0 
```

and to end with, here are a pair of additional informations:
```
$ ls -l /var/run/network
total 4
-rw-r--r-- 1 root root 6 nov.  18 15:45 ifstate
-rw-r--r-- 1 root root 0 nov.  18 15:45 ifup.eth1
-rw-r--r-- 1 root root 0 nov.  18 15:45 ifup.lo
```

and /var/log/boot.log:
[http://pastebin.com/nxzFQkJe](http://pastebin.com/nxzFQkJe)

I have looked into syslog messages too. I just installed libnss-mdns, which was missing and can help for some stuff. Since yesterday I have also added the following packages:
ifupdown-extra (0.22) (and re-installed ifupdown), gir1.2-networkmanager-1.0, (see the descriptions for each to see why I thought it could eventually help), and also installed libmtp-runtime (1.1.3-1ubuntu0.1) which was missing in my system and triggered and error message from dbus at the start of the boot (unrelated to the network problem, but any error message delaying the boot and solved is better).

I don't know if the driver e100e is used or not, and if not, what is used instead ? In the boot sequence I saw a line mentioning a virtual network : I don't know what it is about and if it is related in any way.

I will leave this post as is now, and will follow it, and seek for a related bug report on the Launchpad, if I can find one saying it happens in Pangolin Precise.

Thanks if anyone has any additional clue, links to other relevant bug reports...

---

### Post by Bucky Ball on 2012-11-18
@ drewski: I have marked this thread as 'Solved'. You can do this in future by clicking 'Thread Tools' and 'Mark this thread as solved.' ;)

---

### Post by verheek on 2012-11-20
> **brouhaha said:**
> Thanks for pointing this out. I had the same problem, however a simpler solution worked for me. 

First I checked whether network manager is working at all. Just type:
```
nmcli -f all -p nm status
```Turns out, my NetworkManager was not running. This can be fixed easily by simply typing:
```
sudo NetworkManager
```Voila! Hellooo internet!!

Excellent.  Worked for me upgrading from 10.04.4 .

I also had 4 or 5 packages fail to install due to a password:  prompt.  I guess this is another topic.

---

### Post by TRaction on 2013-06-23
> **jdeca57 said:**
> I... fail to see how one can google and download packages when the network is down. So, the real answer is to make a backup, install 12.04 from scratch and hope that an upgrade doesn't break the system - again? I don't know, but that doesn't feel fixed for me.

@jdeca57  I agree my system was not running after the update, and I recommend if your system is offline? Before you re-install, try manually starting network manager. On my system, after the inital error of "waiting for network configuration" I waited, and it came up and I logged in. Open a terminal window from the task bar. Next in the terminal window type "sudo start network-manager"

the terminal replied: "network-manager start/running, process 3907"

[IMG]http://ubuntuforums.org/image/png;base64,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[/IMG]

For me, this got my internet up and enabled me to begin sorting out the downgrade as described above.

I had trouble installing the packages with synaptic because the later version was installed, and my attempt so far to remove them has failed due to lack of command-line knowledge  (so painful the learning curve). Hope this helps

PS (Sorry, had to edit because I tried pasting a screen cap of the terminal window, and that didn't work)

---

### Post by zhongyijun on 2013-06-26
> **brouhaha said:**
> Hello again,

As I said in my previous post, my NetworkManager wasn't running. So I could start it up everytime I logged in, but I still got the same messages while booting:

"Waiting for 60 more seconds... "
and
"Booting without full network configuration."

The following hack(?) worked for me:

1. Edit /etc/network/interfaces file as a root. 
2. Make sure it contains only the following two lines:
```

auto lo
iface lo inet loopback

```

Now everything works well upon startup. 

I obtained this information from [this blog post]("http://www.necopost.com/2012/06/network-manager-not-running-error-on.html").

Cheers!


Great!This helps me.

---

### Post by Keith_Beef on 2013-08-27
I had a few error messages while upgrading to 12.04, but they seem to be because I had run out of space in /boot so there was no space to install the new kernel. When the computer rebooted after the end of the upgrade, I also was left with no network; I got the message "a network cable is unplugged".

I checked /etc/network/interfaces as described below.

> **brouhaha said:**
> 
The following hack(?) worked for me:

1. Edit /etc/network/interfaces file as a root. 
2. Make sure it contains only the following two lines:
```

auto lo
iface lo inet loopback

```



But the file was exactly as brouhaha described… so I deleted a few old, old files in /boot (freeing up a couple of hundred MB), rebooted and as if by magic networking was fixed. :/

---

### Post by keshara_Dorakumbura on 2013-09-21
It worked. Many thanks !!!!!

for all stuck with this issue, just do what this post say... you are go.

Again, thanks man for your effort.. have a good day.

---

### Post by dqc on 2014-04-19
Hey Drewski22785,

I don't know if you still check this forum, but I have almost the same issue as what you've written above. I'm having difficulty downloading and installing the 4 network manager links. Firstly, I'm operating with an HP Chromebook 14 that has Ubuntu 12.04 installed. I was able to connect online just fine, without any issues. I logged out for awhile and switched to my Chrome OS for awhile. When I switched back to Ubuntu, I could no longer connect to the server (using the same laptop). When I tried opening the network tool, I got the message, [COLOR=#000000]"The system network services are not compatible with this version."

[/COLOR]Still being new to using Ubuntu, I'm not sure how to follow the steps to downloading and installing each of those links you noted. Can you advise any help on this matter? Thanks.

---

### Post by lightman2 on 2015-01-10
#sorry i commented on a wrong post

---

