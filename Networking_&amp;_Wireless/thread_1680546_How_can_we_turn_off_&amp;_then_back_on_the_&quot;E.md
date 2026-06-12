---
title: "How can we turn off &amp; then back on the &quot;Enable Networking&quot; via terminal commands?"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by rocksockdoc on 2011-02-02
[SIZE=3]**How can one uncheck & recheck "Enable Networking" from the command line?**[/SIZE]

Here's how I change the Ubuntu 10.04 laptop MAC address today (see photo below):
- MANUALLY I right click on the "Wireless Connection" icon in the default Ubuntu desktop
- MANUALLY I uncheck the box for "Enable Networking"
- In a TERMINAL window, I type:
```

ifconfig -a | grep HWaddr
sudo ifconfig wlan0 down hw ether DE:AD:BE:EF:CA:FE
sudo ifconfig wlan0 up
!ifconfig

```
- MANUALLY I again right click on the "Wireless Connection" icon & re-check "Enable Networking".

This method works (to change the MAC address); but it requires manual checking and unchecking of the "Enable Networking" switch.

The approach will fail if I don't uncheck and then recheck the Enable Networking box; and the approach of changing the MAC does not work from the /etc/network/interfaces file (as far as we can tell [from this related thread]("http://ubuntuforums.org/showthread.php?t=1581148")). We can't find any other method (yet); so the simplest (which is what I've shown above) is generally the best (when nobody else can do it any other way).

It's working - but it could be just a tad more efficient if we could script it.

To that end ... 

[SIZE=3]**Do you know how to uncheck & recheck "Enable Networking" from the command line?**[/SIZE]


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=182582&stc=1&d=1296683540[/IMG]

---

### Post by thefasterblueone on 2011-02-02
Have a look here:

[https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses]("https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses")

---

### Post by rocksockdoc on 2011-02-02
> **thefasterblueone said:**
> Have a look here:
[https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses](https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses)

My mistake.

I should have mentioned that the suggested method "macchanger" does not work.

I noted the utter & complete failure of macchanger to work on Ubuntu 10.04 on September 24th, 2010 [in the very first post of this thread]("http://ubuntuforums.org/showthread.php?t=1581148") (which I had already referenced but I add it again for convenience).

Macchanger does nothing on reboot in Ubuntu 10.04. Unless there is something else that triggers macchanger, the entire approach can be considered worthless.

At the moment, we can easily randomize the MAC address using:
```

echo $RANDOM$RANDOM | md5sum | sed -r 's/(..)/\1:/g; s/^(.{17}).*$/\1/;'

```

What we need to do is programatically uncheck the "Enable Networking" and then programatically recheck "Enable Networking".

**[SIZE=3]Does anyone know how to turn Enable Networking on and off from the terminal window?[/SIZE]**

---

### Post by rocksockdoc on 2011-02-02
For the record, here is the log file of the most recent macchanger attempt today.

If you know of any mistakes, please let me know.

Otherwise, I must conclude, as I did in September of last year, that Macchanger does not change the MAC address of my Ubuntu 10.04 PC upon reboot given the instructions referenced prior and shown below.

```

----------------------------------------------------------------------------
user@ubuntu:~$ **ifconfig | grep wlan0**
*wlan0     Link encap:Ethernet  HWaddr 00:aa:00:c4:a5:12*
----------------------------------------------------------------------------
root@ubuntu:~# **apt-get install network-manager**
[I]Reading package lists... 0%Reading package lists... 100%Reading package lists... Done
Building dependency tree... 0%Building dependency tree... 0%Building dependency tree... 50%Building dependency tree... 50%Building dependency tree
Reading state information... 0%Reading state information... 0%Reading state information... Done
network-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 42 not upgraded.[/I]
----------------------------------------------------------------------------
root@ubuntu:~# **apt-get install macchanger**
[I]Reading package lists... 0%Reading package lists... 100%Reading package lists... Done
Building dependency tree... 0%Building dependency tree... 0%Building dependency tree... 50%Building dependency tree... 50%Building dependency tree
Reading state information... 0%Reading state information... 0%Reading state information... Done
macchanger is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 42 not upgraded.[/I]
----------------------------------------------------------------------------
root@ubuntu:~# **ls -l /etc/network/if-pre-up.d/macchanger**
*ls: cannot access /etc/network/if-pre-up.d/macchanger: No such file or directory*
----------------------------------------------------------------------------
root@ubuntu:~# **cat > !$ << EOF**
cat > /etc/network/if-pre-up.d/macchanger << EOF
[FONT=Courier New]> #!/bin/sh
> # Randomize the mac address for the given interface
> # as per https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses
> # Each time any managed interface is activated, the network MAC address will
> # be randomized under the VENDOR id as it passes through the pre-up phase.
> # If you desire a completely random MAC address change the -e in the
> # macchanger script to -r.
>
> /usr/bin/macchanger -e \$IFACE[/FONT]
> **EOF**
----------------------------------------------------------------------------
root@ubuntu:~# **cat /etc/network/if-pre-up.d/macchanger**
[I]#!/bin/sh
# Randomize the mac address for the given interface
# as per https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses
# Each time any managed interface is activated, the network MAC address will
# be randomized under the VENDOR id as it passes through the pre-up phase.
# If you desire a completely random MAC address change the -e in the
# macchanger script to -r.

/usr/bin/macchanger -e $IFACE[/I]
----------------------------------------------------------------------------
root@ubuntu:~# **which macchanger**
*/usr/bin/macchanger*
----------------------------------------------------------------------------
root@ubuntu:~# **reboot**
----------------------------------------------------------------------------
user@ubuntu:~$ **ifconfig | grep wlan0**
*wlan0     Link encap:Ethernet  HWaddr 00:aa:00:c4:a5:12*
----------------------------------------------------------------------------
root@ubuntu:~# **reboot**
----------------------------------------------------------------------------
user@ubuntu:~$ **ifconfig | grep wlan0**
*wlan0     Link encap:Ethernet  HWaddr 00:aa:00:c4:a5:12*
----------------------------------------------------------------------------
root@ubuntu:~# **reboot**
----------------------------------------------------------------------------
user@ubuntu:~$** ifconfig | grep wlan0**
*wlan0     Link encap:Ethernet  HWaddr 00:aa:00:c4:a5:12*
----------------------------------------------------------------------------

```

**[SIZE=3]Does anyone know how to turn Enable Networking on and off from the terminal window?[/SIZE]**

---

### Post by thefasterblueone on 2011-02-03
Here is a link that might help you.

[http://www.cyberciti.biz/faq/ubuntu-network-restart/]("http://www.cyberciti.biz/faq/ubuntu-network-restart/")

---

### Post by rocksockdoc on 2011-02-03
> **thefasterblueone said:**
>  [http://www.cyberciti.biz/faq/ubuntu-network-restart/](http://www.cyberciti.biz/faq/ubuntu-network-restart/)

[SIZE=3]Very interesting! And clever![/SIZE]

That ubuntu-network-restart procedure did not get us the last step of the way; but it did get is half a step closer perhaps (depending on your interpretation)!

[LIST=1]
[*]**Progress**: The "initd networking stop" & "start" allowed the MAC to change
[LIST]
[*][SIZE=1](w/o having to uncheck & recheck "Enable Networking" even while connected)![/SIZE] :)
[/LIST]
 
[*]**Failure**: However, it also prevented re-connection to the wireless network
[LIST]
[*][SIZE=1](until I manually unchecked & rechecked "Enable Networking)![/SIZE] :(
[/LIST]
 
[/LIST]
 Here's a more detailed summary:
*Note: The goal is a random MAC upon reboot; but first I have to get a random MAC script to work!*

[LIST]
[*]Always, on Ubuntu 10.04, whenever I was unconnected from any wireless network, I could easily change the wlan0 MAC address simply by running commands in the terminal window (i.e., "ifconfig  wlan0 down hw ether DE:AD:BE:EF:CA:FE" and "ifconfig wlan0 up".
[*]Prior to the suggested ubuntu-network-restart procedure, I could NOT change the MAC if I was already connected to the network using those same ifconfig commands (i.e., "ifconfig  wlan0 down hw ether DE:AD:BE:EF:CA:FE" and "ifconfig wlan0 up") and then  manually re-checked "Enable Networking". This mix of terminal and  manual procedures automatically re-connected to the wireless network  with the newly assigned wlan0 MAC address.
[*]Prior to the suggested ubuntu-network-restart procedure, if I was already connected to the wireless network, I could only change the MAC address if I first manually unchecked the "Enable Networking" GUI (and then re-checked it after running the ifconfig commands listed above).
[*]```
login@ubuntu:~$ sudo -i
-> [sudo] password for login:
root@ubuntu:~# ifconfig wlan0 down hw ether AA:AA:AA:AA:AA:AA
root@ubuntu:~# ifconfig wlan0 up
root@ubuntu:~# ifconfig | grep HWaddr
-> eth0      Link encap:Ethernet  HWaddr 00:16:d3:3e:83:04
-> wlan0     Link encap:Ethernet  HWaddr aa:aa:aa:aa:aa:aa
root@ubuntu:~# ping www.google.com
-> PING www.l.google.com (74.125.224.52) 56(84) bytes of data.
-> ... blah blah blah ...
root@ubuntu:~# ifconfig wlan0 down hw ether BB:BB:BB:BB:BB:BB
-> SIOCSIFHWADDR: Cannot assign requested address

```
[/LIST]

[LIST]
[*]With this newly suggested ubuntu-network-restart procedure  (see log file below), whether connected to the wireless network  initially or not, I was now able to change the MAC address (as evidenced by  "ifconfig -a | grep HWaddr") WITHOUT having to manually un-check and  re-check "Enable Networking"!
[*]This is progress (of sorts) ...
[*]However ... after running the suggested ubuntu-network-restart  commands ... while I was already connected to the wireless network ... and with  "Enable Networking" checked prior ... I could NOT subsequently connect  to the wireless network - the icon just spun and spun and spun (until it  gave up).
[*]Much to my dismay ... even if I manually tried to connect and disconnect  from the wireless network, the networking icon still just spun and spun until it  gave up trying to connect.
[*]However ... as always, simply manually un-checking and  re-checking "Enable Networking" did allow me to connect to the wireless  network (with the new MAC address).
[/LIST]
So, we didn't actually gain anything because I still need to manually check and uncheck "Enable Networking" to connect back to the existing wireless network with the new MAC address.

So, the good news (sort of) of using the ubuntu-network-restart procedure is that the wlan0 MAC address actually changed without me having to manually uncheck and recheck "Enable Networking"; however, the bad news is that we still need to manually uncheck & recheck "Enable Networking" in order to re-connect to the wireless network with the newly assigned MAC address. :(

So, while very interesting ... we actually got nowhere with the ubuntu-network-restart procedure (because it only succeeded in adding a step without changing the end result).

However, I do believe we're closer now. All we need to do is figure out how to disable whatever "Enable Networking" does ... and then re-enable it.

Here's the log for more complete details:
```

login@ubuntu:~$ **script /tmp/mac_change.log**
-> *Script started on Thu 03 Feb 2011 11:51:26 AM PST*
login@ubuntu:~$ **date**
-> *Thu Feb  3 11:50:28 PST 2011*
login@ubuntu:~$ **ifconfig -a | grep HWaddr**
-> *eth0      Link encap:Ethernet  HWaddr 00:a1:03:43:5a:af*
-> *wlan0     Link encap:Ethernet  HWaddr 00:aa:00:c4:a5:12*
login@ubuntu:~$ **sudo /etc/init.d/networking stop**
-> [sudo] *password for user:*
[I]-> * Deconfiguring network interfaces...
-> [80G Ignoring unknown interface wlan0=wlan0.
-> [ OK ][/I]
login@ubuntu:~$ **sudo ifconfig wlan0 down hw ether DE:AD:BE:EF:CA:FE**
login@ubuntu:~$** sudo ifconfig wlan0 up**
login@ubuntu:~$ **ifconfig -a | grep HWaddr**
[I]-> eth0      Link encap:Ethernet  HWaddr 00:a1:03:43:5a:af
-> wlan0     Link encap:Ethernet  HWaddr de:ad:be:ef:ca:fe[/I]
login@ubuntu:~$ **sudo /etc/init.d/networking start**
[I]-> Rather than invoking init scripts through /etc/init.d, use the service(8)
-> utility, e.g. service networking start
->
-> Since the script you are attempting to invoke has been converted to an
-> Upstart job, you may also use the start(8) utility, e.g. start networking
-> networking stop/waiting[/I]
login@ubuntu:~$ **exit**
-> *exit*
-> *Script done on Thu 03 Feb 2011 11:53:24 AM PST*

```[B][SIZE=3]Is there a way to programitically do whatever unchecking & rechecking "Enable Networking" does on Ubuntu 10.04?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=182645&stc=1&d=1296764824[/IMG]
[/SIZE][/B]

---

### Post by rocksockdoc on 2011-02-24
Still unsolved ... but at least it's working manually! 

In a nutshell, whenever I need change my radio NIC MAC address & PC hostname:
- I uncheck "Enable networking"
- I run the commands to change the hostname and the MAC address
- I re-check "Enable networking"
- I connect to the wifi hotspot

That way, a bogus MAC address is divulged in the radio NIC authentication frame.

Now the next privacy problem to (manually) resolve is the Ubuntu privacy bug that causes the last-connected SSID to be constantly revealed in the radio NIC association request (allowing cookie-crumb attacks if your SSID is at all unambiguous).

---

### Post by rocksockdoc on 2011-03-02
Still unsolved. But working manually. 

I am surprised I'm the only one here who changes his radio NIC MAC address.

---

### Post by matt_symes on 2011-03-03
Hi

This is a real shot in the dark (as you are right in that i don't change my mac address) but i was wondering if forcing a reload of network manager might also reload its setting and the new MAC address.

```
sudo /etc/init.d/network-manager reload
```

or even

```
sudo /etc/init.d/network-manager restart
```

If not can you send it a dbus message ?

Kind regards

---

### Post by Csirkefogo on 2011-03-04
> **rocksockdoc said:**
> Still unsolved. But working manually. 

I am surprised I'm the only one here who changes his radio NIC MAC address.

Hi,

I have to change my MAC every time I reboot because my WISP only accepts the MAC of the client router which broke down recently and I use my laptop to share the net. I was thinking of writing a startup script to do it always for me but I encountered the same problem as you.

After a while of head-scratching I found a solution that works for me:

To uncheck the wifi in the NetworkManager and be able to edit the MAC:
```
sudo rfkill block wifi
```
To enable the wifi again:
```
sudo rfkill unblock wifi
```

Sorry for the bad English.
Hope it helps :)

---

### Post by rocksockdoc on 2011-03-07
Just for the record, I found a nice way to dynamically change the hostname on the fly (non persistent);
```

sudo -i
echo "foo" > /etc/hostname
hostname --file /etc/hostname

```

---

