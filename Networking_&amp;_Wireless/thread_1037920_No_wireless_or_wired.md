---
title: "No wireless or wired"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by stoopid_noob on 2009-01-12
Hello,

I just did the updates before bed last night and now I am not able to get wireless or wired connections to work. After I completed the updates I know that the wireless was working. 

I am faced with two issues. First, it looks like that wireless is not turned on, so I tried using the wireless switch in the front as I have before but still no go. It bothers me there is no way to tell whether or not it is even actually turned on with the LEDs!!! 

I tried using the command:

"sudo ifconfig wlan0 up" 

But it returns:

"SIOCSIFFLAGS: Resource temporarily unavailable" 

What is going on here??? HELP!

---

### Post by ecujak on 2009-01-12
No wired web. Torrents work though. Funny.

8.10


Network manager GUI is different now to. 

Could this be a DNS issue?


Funny how I am posting from the same network on my windows machine that I hate but seems to be the only thing that really, "Just WORKS."

---

### Post by ecujak on 2009-01-12
Must point out that everything was working for years until an update last night that seemed to require a reboot. After the reboot my web connections no longer work.

I can still connect to all of my torrents, at an unbelievable high speed, but no web.

---

### Post by stinkybear on 2009-01-12
Same problem here. Was working last night. Web is not working today. After reading your post I tried torrents and all works there. Why is it just the web? 

My machine is dual boot with windows and the windows boot can surf the net just fine. This sucks. I was really feeling the love from Ubuntu, but a busted network is worse than a girlfriend cheating with your best friend.

I hope someone can find a fix. I don't know what update it was that F'ed up my system, but there weren't that many up there last night. It did require a reboot and then.... no go.

---

### Post by superprash2003 on 2009-01-12
does [http://209.85.171.100](http://209.85.171.100) open?? if so, then its definetly a dns issue.. try changing dns servers to opendns - 208.67.222.222 and 208.67.220.220 .. [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by stinkybear on 2009-01-12
> **superprash2003 said:**
> does [http://209.85.171.100](http://209.85.171.100) open?? if so, then its definetly a dns issue.. try changing dns servers to opendns - 208.67.222.222 and 208.67.220.220 .. [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

Yes the static ip did open.

I manually undated the /etc/dhcp3/dhclient.conf
and added the open dns to the bottom. Still no go, even after a reboot.

I will post some more info...

---

### Post by stinkybear on 2009-01-12
@kubuntu:~$ more /etc/dhcp3/dhclient.conf
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope, interface-mtu;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
#
prepend domain-name-servers 208.67.222.222,208.67.220.220;

---

### Post by stinkybear on 2009-01-12
kubuntu:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:00:2f:a5:00:00  
          inet addr:192.168.1.48  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fea5:2028/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:437029 errors:0 dropped:0 overruns:0 frame:0
          TX packets:429558 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:111621465 (111.6 MB)  TX bytes:64658010 (64.6 MB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35308 (35.3 KB)  TX bytes:35308 (35.3 KB)

---

### Post by stinkybear on 2009-01-12
as posted above, I too notice a new network connection manager that I have never noticed before. 

System-> Preferences-> Network Configuration

---

### Post by stoopid_noob on 2009-01-12
Ok, I went into my Network Configuration and deleted all connections under all and then restarted. I entered my network information again for wireless and it worked. Try that if all else fails. I know it is simplistic ... but it worked for me. :guitar:

---

### Post by stinkybear on 2009-01-12
no go here. "Network Configuration" won't even let me add a new connection. It asks for my password, then after I enter my password nothing is added. 

I wish I knew the command to run this "Network Configuration" in sudo because it obviously thinks I don't have rights.

I wish I could disable this and use my old network tools and settings. 

I really just want my internet to work.

---

### Post by stinkybear on 2009-01-12
Please someone help me. This is very frustrating. I have been working on this for 6 hours now.

---

### Post by stinkybear on 2009-01-12
this is what I get when trying to add a connection with nm NetworkManager

sudo nm-connection-editor

(nm-connection-editor:7587): GLib-CRITICAL **: g_hash_table_foreach: assertion `hash_table != NULL' failed
** Message: nm_connection_list_new: failed to load VPN plugins: Couldn't read VPN .name files directory /etc/NetworkManager/VPN.

** (nm-connection-editor:7587): WARNING **: No connections defined

(nm-connection-editor:7587): GLib-CRITICAL **: g_hash_table_lookup: assertion `hash_table != NULL' failed

** (nm-connection-editor:7587): WARNING **: Unknown setting '802-3-ethernet'

** (nm-connection-editor:7587): WARNING **: create_new_connection_for_type: unhandled connection type '(null)'

** (nm-connection-editor:7587): WARNING **: Can't add new connection of type '802-3-ethernet'

(nm-connection-editor:7587): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

** (nm-connection-editor:7587): WARNING **: Invalid setting 802.1x Security: Invalid 802.1x security

** (nm-connection-editor:7587): WARNING **: Invalid setting IPv4 Settings: addresses

** (nm-connection-editor:7587): WARNING **: ui_to_setting: IPv4 address '<none>' missing or invalid!

** (nm-connection-editor:7587): WARNING **: Invalid setting IPv4 Settings

** (nm-connection-editor:7587): WARNING **: ui_to_setting: IPv4 prefix '<none>' missing!

** (nm-connection-editor:7587): WARNING **: Invalid setting IPv4 Settings
[WARN  7587] polkit-action.c:211:polkit_action_set_action_id(): polkit_action_validate_id (action_id)
 Not built with -rdynamic so unable to print a backtrace
:confused:

as you see, it is not letting me add a connection.

---

### Post by stinkybear on 2009-01-12
now I get this:

Updating connection failed: nm-ifupdown-connection.c.82 - connection update not supported (read-only)..

---

### Post by stoopid_noob on 2009-01-13
Make sure that you are not being blocked by some keyring. Go into your "Home" folder, View hidden files and select .gnome2 > keyrings. Now delete any files you see in there, usually it is "default.keyring" and "default." 

Restart the computer and then try to connect to a wireless connection or create one. It will prompt you at this time to create a new keyring. I made it the same as my login password to make it easy. 

There is a way to bypass the keyring thing too, I can't remember what I did. I will get back to you.

---

### Post by stoopid_noob on 2009-01-13
Found it:

[http://ubuntuforums.org/showthread.php?t=431893&highlight=libpam-keyring](http://ubuntuforums.org/showthread.php?t=431893&highlight=libpam-keyring)

---

### Post by stinkybear on 2009-01-13
Network Manager Patching bug resolved. 


Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf.

sudo vim /etc/resolv.conf



Once your preferred editor opens the file you want to enter the following information (changing your addresses where necessary):



    # Generated by NetworkManager

    nameserver 208.67.220.220
    nameserver 208.67.222.222

 sudo /etc/init.d/networking restart






    *Reconfiguring network interfaces. [OK]







I hope this helps someone.... I guess any help to another will be more help than any given to me. I guess I am just not cool enough for you  guys to lend a hand yet.

I still don't know why the updates killed my dns. Or how NetworkManager was enabled....


:popcorn:

---

### Post by stinkybear on 2009-01-13
Thanks SNoob... you don't seem like too much of a noob.

---

### Post by superprash2003 on 2009-01-14
so did that work?? well it looked like a DNS issue.. please mark thread as SOLVED under thread tools..

---

### Post by normanp on 2009-01-21
As in another thread I fixed this (8.10) by:
sudo nano /etc/network/interfaces
Comment out all the lines under the heading Primary Network Interface using #
Ctrl-x to exit, y to save, enter
Reboot machine, go back to Network Connections and put in settings as required.

---

