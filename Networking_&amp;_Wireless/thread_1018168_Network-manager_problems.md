---
title: "Network-manager problems"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by david-emm on 2008-12-21
Hi,
I've installed 8.10 on my Acer 2201 laptop in a dual boot configuration and I am having problems connecting to my Wifi network. The other laptops on the network (Windows XP machines) work OK as does this laptop when using XP. I have installed ndis and use the installed windows IMP2220 driver. I see all the networks in my immediate area. Network manager tries to auto connect to my network and tells me it has connected,  but will not allow data in or out. (Actually by some odd miracle I have connected twice in four days. The first time I downloaded all the 205 updates without any problem. The second was after a lot of investigation and deleting passwords in keyring).  Typically I cannot ping my gateway or any other computer on my network.

I am using WPA PSK security and have a 63 acsii char password.  This is entered via a cut and paste operation so there is no finger problem in entering. It seem that the password is saved in the keyring as something quite different (added security perhaps or is it changed to a 64 byte hex sequence?) and this is then exported back into network manager as this code. Anyway it seems that this code does not  match the code in the D-Link wireless router and communication is blocked.

Any suggestions what I should try next?

PS I have tried Wicd, see my router but this will not connect at all. Again is this a mis-match in passwords?

---

### Post by david-emm on 2008-12-22
Further to my first post.
The code input from keyring is OK. It is a WPA key generation using the SSID and the ascii key. Seems if I leave Ubuntu on for about half an hour I suddenly get connected (weird). This has happened twice today. Seems that I'm connected all the time but a bar of some sort isn't lifted to allow communication. So network manager sort of works. Maybe the next update will fix this.

---

### Post by Aearenda on 2008-12-22
It's not you - in 8.10 NM is less forgiving of slowly-associating network drivers. For me, hitting 'cancel' when it complains about the key is usually all it needs to get connected. I use WPA PSK as well, with a long passphrase.

Sometimes I find that restarting NM helps, like this: ```
sudo service NetworkManager restart
```Also, I reverted to using the Windows driver with ndiswrapper rather than the old or new atheros drivers, but your driver may be quite different.

See [this bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/272185") if you have a few hours!

---

### Post by david-emm on 2008-12-22
Thanks Aearenda for your help. I'll look at the the bug report - after Christmas. I moved to Ubuntu after using PCLOS07 on this laptop which worked (Wifi) without a problem. I didn't want to download the new distro from them as I also run a Ubuntu 8.04 server and a 8.04 desktop both of which are connected by ethernet without any problems so I got a 8.10 disk from Ubuntu.

---

### Post by Favux on 2008-12-22
Hi david-emm,

You might want to check out:

   [http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

---

### Post by Aearenda on 2008-12-23
That's a fascinating angle on the whole Intrepid N-M issue. I see some experimentation coming up. Thanks, Favux!

---

### Post by david-emm on 2008-12-25
Hi Favux,
Thanks for the lead. Have looked in  /system/networking/connections and found two supposed connections both set to auto. One is my true SSID and the other a nearby one. Don't know how this second one was made auto but it seems to me that if two networks are trying to connect at the same time there will be a conflict. I've deleted the second one. Now to find out if this helps.

---

### Post by david-emm on 2008-12-27
Following up Favux's post on [http://ubuntuforums.org/showthread.php?t=1010650](http://ubuntuforums.org/showthread.php?t=1010650) I also have changed system>networking>connections>1>802-11-wireless-security using gconf-editor.

Was
group       [wep40,wep104,tkip,ccmp]
key-mgmt    wpa-psk
name        802-11-wireless-security
pairwise    [tkip,ccmp]
proto       [wpa,rsn]

Now
group       [ccmp,tkip]
key-mgmt    wpa-psk
name        802-11-wireless-security
pairwise ccmp,tkip]
proto       [rsn,wpa]

This has improved the connection rate - I now usually connect in under a minute - but its not perfect.

---

### Post by Favux on 2008-12-27
Hi david-emm,

But progress at least.  By the way what did deleting the other auto connection do?

---

### Post by david-emm on 2008-12-28
Hi Favux,
Nothing as far a I could tell. Connection was spasmodic at best. The improvement occurred after I changed the connection data. Today it took about 45 secs to see the internet after all icons appeared. Thta's livable.

---

### Post by Favux on 2008-12-28
Hi david-emm,

Mine can be real slow to restart after laptop comes out of sleep.  What I do is just right click on NM and disable wireless.  Then I right click on it again and enable wireless.  It starts up right away then.  Give it a try.

---

### Post by david-emm on 2008-12-30
Have been doing this. Today was a real stopper. I remember that I looked at edit in the NM. This apparently resets the network connection script.  Tried to save the changed network connection script as default but this failed.  "The application "gconf-editor" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application".

---

### Post by Favux on 2008-12-30
Hi david-emm,

> I remember that I looked at edit in the NM. This apparently resets the network connection script.
Right, I warned about that.  You have to then go back and manually edit the settings again in gconf.

> Tried to save the changed network connection script as default but this failed. "The application "gconf-editor" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application".
Good, someone finally tried it.  So it gives some ominous and vaguely threatening warnings.  These sound like what happens when you don't sudo and so don't have the right permissions.  So what happened?  Did it work?  Or did the system overwrite your changes?

So now we know the changes by gconf only apply to the user after log in.  That makes sense, since if you try to sudo gconf from a terminal you don't see the gconf settings for network.  If "default" doesn't work next step is someone being brave enough to try "mandatory".  I would guess at the same results.

So then the question would be how do we, with administrator permissions, see the gconf settings so we can edit them system wide when the settings are local, only for user?  I'm stumped.

---

### Post by david-emm on 2008-12-30
HI Favux,
Logged in OK this morning. Network came up after 30 -45 secs. Tried 'Set as Mandatory'. Same result as 'Set as Default'. Some further details are available:

*No database available to save your configuration: Unable to store a value at key '/system/networking/connections/1/802-11-wireless-security/proto', as the configuration server has no writable databases. There are some common causes of this problem: 1) your configuration path file /etc/gconf/2/path doesn't contain any databases or wasn't found 2) somehow we mistakenly created two gconfd processes 3) your operating system is misconfigured so NFS file locking doesn't work in your home directory or 4) your NFS client machine crashed and didn't properly notify the server on reboot that file locks should be dropped. If you have two gconfd processes (or had two at the time the second was launched), logging out, killing all copies of gconfd, and logging back in may help. If you have stale locks, remove ~/.gconf*/*lock. Perhaps the problem is that you attempted to use GConf from two machines at once, and ORBit still has its default configuration that prevents remote CORBA connections - put "ORBIIOPIPv4=1" in /etc/orbitrc. As always, check the user.* syslog for details on problems gconfd encountered. There can only be one gconfd per home directory, and it must own a lockfile in ~/.gconfd and also lockfiles in individual storage locations such as ~/.gconf*

I can't find key '/system/networking/connections/1/802-11-wireless-security/proto*. *File /etc/gconf/path exists and belongs to root. Seems to be controlled by xml scripts. I think I have found the database files.  These are in $HOME/.gconf/sub-directories that match the gconf-editor directories. eg.

drwxr-xr-x 2 david david 4096 2008-12-31 11:34 802-11-wireless
drwxr-xr-x 2 david david 4096 2008-12-31 11:34 802-11-wireless-security
drwxr-xr-x 2 david david 4096 2008-12-31 11:34 connection
-rw-r--r-- 1 david david    0 2008-12-31 10:49 %gconf.xml
drwxr-xr-x 2 david david 4096 2008-12-31 11:34 ipv4

Each sub-directory has a %gconf.xml file in it that contains the saved data embedded in xml statements. My xml ability is poor and as yet I haven't found out how these files are managed. Probably edit in NM is associated with an xml script that resets all values to 'default' when accessed. I'll try to find this.

Looked through /log/messages today. In the start up are the following:

Dec 31 10:48:31 gemini kernel: [   18.348198] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Dec 31 10:48:31 gemini kernel: [   18.861680] ndiswrapper: driver neti2220 (LanExpress,08/16/2004,2.23.08.2004) loaded
Dec 31 10:48:31 gemini kernel: [   18.862106] ndiswrapper 0000:02:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 31 10:48:31 gemini kernel: [   19.153491] ndiswrapper: using IRQ 18
Dec 31 10:48:31 gemini kernel: [   19.352634] wlan0: ethernet device 00:0e:9b:89:90:34 using NDIS driver: neti2220, version: 0x20017, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 17FE:2220.5.conf
Dec 31 10:48:31 gemini kernel: [   19.352662] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
then later on
Dec 31 10:49:14 gemini kernel: [   73.206190] ndiswrapper (iw_set_freq:325): setting configuration failed (C0010015)
Dec 31 10:49:14 gemini kernel: [   73.207085] ndiswrapper (iw_set_ap_address:566): setting AP mac address failed (C0010015) 

Then in the daemon log a whole lot of stuff relating to wlan0. I'll send it if its of interest.

---

### Post by Favux on 2008-12-31
Hi david-emm,

I think wlan0 might be your wireless module, mine is wlan.  Maybe because you're using ndis.  I think it's just describing supported security modes.  So the daemon log may not be useful.

I noticed that in /home/user/.gconfd is saved_state with the line [ADD 2214592685 "def" "/system/networking/connections"] towards the end of the file, and then the saved settings in the line below.  Could this be part of how the .xml files are managed?

If I look in /home/user/.gconf/desktop/networking/connections/1/802-11-wireless-security/%gconf.xml I also find %gconf.xml has the stored modified key.  When I look at the .xml in browser it has ccmp deleted just like I did in gconf editor.

So I think you're right.  Somewhere there may be a master "default" file that NM is restoring from.  If we find it and can edit it for our particular setup then we'd have a stable connection no matter what we did with NM.  If instead it's generating a "default" value from other scripts on the fly we may have troubles.

---

### Post by bab1 on 2008-12-31
> So I think you're right. Somewhere there may be a master "default" file that NM is restoring from. If we find it and can edit it for our particular setup then we'd have a stable connection no matter what we did with NM. If instead it's generating a "default" value from other scripts on the fly we may have troubles.

Maybe this will shed some light on the subject:[[COLOR="blue"]**http://www.arachnoid.com/linux/NetworkManager/index.html**[/COLOR]]("http://www.arachnoid.com/linux/NetworkManager/index.html")

---

### Post by Favux on 2008-12-31
Hi bab1,

Wow!!!  So the upshot is that after Paul Lutus figured out NM's architecture and wrote his Ruby scripts (after his bug report was labeled unconfirmed) to fix his network problem, NM proceeded to ignore all the configuration information that his Ruby script was feeding it?
> It was while creating this method that I first acquired a sense that I could have any control over what NM chose to do. Until now I watched in awe as NM did whatever it pleased and blithely ignored my efforts to send it signals by way of network configuration files.

I wonder whether "ignore the user's wishes and inputs" actually represents a trend in open-source programming. I hope not.
Amazing!  While I dimly comprehend some of what he is saying and can sort of follow along I did take away:
```
gconftool-2 --recursive-list /system/networking/connections/1

```
Which shows my network settings from the gconf data base in more detail.  Again showing where I have edited out ccmp.

Well david-emm, if I'm following bab1 and Paul correctly, they are telling us we've reached a dead end.  Using gconf editor as a kludge workaround is the best we're going to do.  And be prepared to manually re-edit any time NM decides to change the keys.

I'd appreciate your take on all of this.

Edit:  Oh a key point.  As Mr. Lutus points out, and his diagram shows, NM is meant for user.  Apparently work is ongoing to make it system wide.

---

### Post by bab1 on 2008-12-31
@ Favux,

I think we should step back and look at NM from an abstract point of view.   What is the motivation of the folks at GNOME to create NM?  As Paul pointed out; for consistency across various Linux distros.  This is a good point, but  I see the use of d-bus and HAL move away from the basic UNIX/Linux "everything is a file" philosophy.  I'm not saying it is bad, but it is a major paradigm shift for Linux.  

You are correct, when we rely on NM for networking configuration there is no "file" holding the configuration.  Furthermore, when NM is running the user is allowing NM to make all of the networking configuration decisions.  The user defined configuration settings are only the variables that NM uses for it's configuration algorithm.

The NM can be initially setup to defer to a "user configured Ethernet interface" and only invoke the algorithm  when a wireless interface is in use.  This sounds like what I would want on my laptop.  I don't see a need for NM at all on a desktop.  I feel that NM should have a simple method that allows for the setup of a static IP address

The major problem from what I can tell is that NM is not very flexible.  Where does the user go if they wish to have a configuration that is a little out of the box or wishes to change the original variables used in the configuration?  These things will be worked out in the future I am sure.  For right now, welcome to the bleeding edge.  

My solution is to understand NM and use it as the developers intended (on a laptop) or remove it from the system and configure  the host manually.

**EDIT:**

> Oh a key point. As Mr. Lutus points out, and his diagram shows, NM is meant for user. Apparently work is ongoing to make it system wide.

I think what Paul is referring to is that NM is more system centric that user centric.  That is the point I make when I said NM is not very flexible.

---

### Post by Favux on 2008-12-31
Hi again bab1,

> You are correct, when we rely on NM for networking configuration there is no "file" holding the configuration. Furthermore, when NM is running the user is allowing NM to make all of the networking configuration decisions. The user defined configuration settings are only the variables that NM uses for it's configuration algorithm.
So this is why we see NM change our gconf security keys when we invoke it through it's editor, etc.

> The major problem from what I can tell is that NM is not very flexible. Where does the user go if they wish to have a configuration that is a little out of the box or wishes to change the original variables used in the configuration? These things will be worked out in the future I am sure.
I agree that it is not very flexible.  But after all it is only in version 0.70.  Hopefully as it matures it will get more flexible, as well as having a more sophisticated alogorithm.

Again the bottom line from my perspective is:  The gconf editor workaround succeeds in giving me and others wireless despite NM.  But that is all we can expect at this stage.  There is no point in looking further into NM for the reasons mentioned above and in the above posts.

---

### Post by david-emm on 2008-12-31
Hi Favux and bab1
Thanks for your help. Well, it seems that I'm just nibbling round the edges of the problem so to speak. Without all the sources and flow charts etc it's not possible to go any further.

In my case NM appears to find and start up wlan0 OK but then fails to handshake with the router. Reading through the daemon log I find that I activate OK
( <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. ),
and then get 
<info>  (wlan0): supplicant connection state change: 7 -> 4, 4  -> 5, 5 -> 6, 6 -> 7, 7 -> 4 and round and round maybe 5 or 6 times before a true connect to the router and hence internet. Could be this is a timing problem? (I don't know what the state changes refer to).
One thing I noticed yesterday was that if I start up Firefox before I got a true connect then I never get a connect. I need to reboot to clear.

---

### Post by bab1 on 2008-12-31
> ...fails to handshake with the router

@ david-emm,

I'm not sure what to say here.  I try and separate in my mind (for diagnostic purposes) the RF transceiving and the Ethernet connection.  It sounds like you may be having difficulties with the RF side.  I don't believe that NM cares about that part.  

The  FF thing might be due to cached IP addresses confusing the matter.

You might look to the DHCP configuration for the answers.

Have you looked at the dbus logs? At /var/log/dmesg

---

### Post by Favux on 2008-12-31
Hi david-emm,

In this bug report,  at the bottom, Alexander Sack (a NM developer) points you to new NM PPA's that address some driver timing issues.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/263963]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/263963")

latest NM PPA packages (0.7 final):

[https://edge.launchpad.net/~network-manager/+archive]("https://edge.launchpad.net/~network-manager/+archive")

If you decide it really is a timing problem you might want to give them a try.

---

### Post by oygle on 2008-12-31
Would be nice if the Ubuntu team put the NM 0.7 final into the Intrepid updates.  :)

---

### Post by david-emm on 2009-01-02
bab1 and Favux,
Thanks for the leads. I've just installed Alexander Sack's updated NM. Now to shut down and restart to see if there is any improvement. I'll let you know.

---

### Post by david-emm on 2009-01-02
babi and Favux,
Using the new NM from Alexander Sack. Switched on at 08:36:32. wlan0 startup at 08:37:04 and had a connection to the internet by  Jan  3 08:47:15 gemini avahi-daemon[4507]: Registering new address record for fe80::20e:9bff:fe89:9034 on wlan0.*. Not very fast but I think I had traffic before the time stamp. Will monitor over the next few days.

---

### Post by Favux on 2009-01-02
david-emm,

Good!  And you didn't need to edit the keys through Gconf?

---

### Post by bab1 on 2009-01-02
I believe David has another problem.  THe Wlan interface is running on the > gemini avahi-daemon[4507]: supplied IP address.  This would account for the slow configuration time and the reduced traffic speeds too.

it looks like you may not be getting an IP address from you routers DHCP server.

David,

post the output of ```
ipconfig -a

```

**Edit:**In other words, I feel David is still not getting a response from the router.

**Edit2:**To be more specific -- either there is no DHCP request from the host or no DHCP acknowledge from the router.  After a bit of time the AVHI daemon say use this IP address (168.254.x.x).  This has limited capacity and should not be relied upon for network connectivity.

---

### Post by david-emm on 2009-01-02
First a reply to Favux: Yes I had changed to NM rules using gconf-editor. I'll drop back to standard and see if this is still a stopper.

Now a reply to bab1: I'm using static address in my network as its small (5 machines: Ubuntu 8.04 server on ethernet - very stable; Dual boot desktop on ethernet. Win2000 and Ubuntu 8.04, two different ip addresses although I cannot use both together but useful for the MS Network - also very stable; one laptop XP home - wifes machine - do not touch; this machine dual boot XP home and Ubuntu 8.10. Again two different ip addresses for the above reason. XP connects reasonably quickly using the wireless driver built into the latop. Ubuntu uses the same wireless driver using ndis; last machine is an older laptop without built in wireless and has a USB D-Link wireless connection. Works fine on XP pro but gives a lot of trouble using any flavour of Linux. All machines use the same DNS server addresses which are part of the ISP configuration.

Tried ipconfig but this command does not exist on my machine. Did you mean iwconfig? If so this is the dump:

root@gemini:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:02:3f:08:b5:77  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3388 (3.3 KB)  TX bytes:3388 (3.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0e:9b:89:90:34  
          inet addr:192.168.0.113  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:9bff:fe89:9034/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3664 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3759 errors:0 dropped:3 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3274026 (3.2 MB)  TX bytes:647431 (647.4 KB)
          Interrupt:18 Memory:e8200000-e8200800 

 Cheers

PS Once up speed is 54Mbps

---

### Post by bab1 on 2009-01-02
Hi david-emm,

Must be too much focus on my part to the AVHI part in your previous post.  :D  The ipconfig -a is Windows command.  The command in Linux is ifconfig -a. 

New Years day I provided IT support for the press and photographers at the Rose Bowl football game.  We had many laptops with timing problems when first coming on line for the reasons I stated in the previous post.  It got sorted out but it took time.  Glad to hear that your system is working now.

---

### Post by david-emm on 2009-01-03
Favux and bab1,
I've left the NM rules modified as boot times this am were:
From power on to appearance of NM icon - 75 secs (typical).
From NM icon to Weather icom (I know I am connected to internet - 40 secs (good). 
I'm happy with this. I think we can say the new Alexander Sack NM install has helped enormously. Thanks to both of you for taking the trouble to help.

Had to look up the Rose Bowl football game on Wikipedia and found its held in Pasadena. We're now in high summer - at times over 30C and 80% humidity. Not all that pleasant. Our best times are September - November and March - May.
David-emm

---

