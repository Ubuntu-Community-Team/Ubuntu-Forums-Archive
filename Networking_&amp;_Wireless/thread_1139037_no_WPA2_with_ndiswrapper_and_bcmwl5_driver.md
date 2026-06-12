---
title: "no WPA2 with ndiswrapper and bcmwl5 driver"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by Guitarmaster316 on 2009-04-26
Hey all,

First of all... thanks you to all who contribute here.  I finally got my wireless card to work with ndiswrapper.  I don't know how I did it, but IT WORKS!

However; I can not get it to work on an encrypted network... namely WPA2. This DID work with the native b43Legacy driver, but it was very slow.

I have tried some suggestions from other posts, but no avail.

Network manager does not have an option for WPA2 only WEP and LEAP.  

PLease help!!  


THanks!


Matt

P.S.  Using 9.04 Jaunty

---

### Post by ittiam on 2009-04-26
Post the output of

```
pgrep wpa_supplicant
```

----------------------------------------------------------------------------------

You can try the following steps and try to get online using a secured network.

```
sudo vi /etc/wpa_supplicant.conf
```

Make sure your wpa_supplicant.conf looks exactly like the following.

```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
    ssid="your SSID here in quotes if ASCII"
    scan_ssid=1
    proto=RSN
    key_mgmt=WPA-PSK
    group=TKIP
    pairwise=TKIP
    psk="your password here in quotes if ASCII"
}
```

Try to associate with the router

```
sudo wpa_supplicant -iwlan0 -Dwext -c/etc/wpa_supplicant.conf -B
```

Above, replace wlan0 with your own wireless interface.

```
sudo dhclient <wireless_interface> like (wlan0, eth1)
```

---

### Post by Guitarmaster316 on 2009-04-26
```
matt@matt-laptop:~$ pgrep wpa_supplicant
2638
matt@matt-laptop:~$ 
```

---

### Post by ittiam on 2009-04-26
okay try this

```
pkill wpa_supplicant
```

now execute

```
pgrep wpa_supplicant
```

If the above pgrep command still throws a process id as output

post the output of the following

```
ps aux | grep NetworkManager
```

---

### Post by Guitarmaster316 on 2009-04-26
```
matt@matt-laptop:~$ pgrep wpa_supplicant
7686
matt@matt-laptop:~$ ps aux | grep NetworkManager
root      2634  0.0  0.5  16548  2544 ?        Ssl  17:44   0:01 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      2642  0.0  0.5   7048  2564 ?        S    17:44   0:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
root      7699  0.0  0.2   2276   980 ?        S    20:44   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-wlan0.pid -lf /var/lib/dhcp3/dhclient-wlan0.lease -cf /var/run/nm-dhclient-wlan0.conf wlan0
matt      7817  0.0  0.1   3340   808 pts/0    S+   20:45   0:00 grep NetworkManager
matt@matt-laptop:~$ 
```

---

### Post by Guitarmaster316 on 2009-04-26
I turned the encryption off right now.  Does it make a difference for these tests?

---

### Post by ittiam on 2009-04-26
You need to kill the NetworkManager

```
sudo kill -9 2634
```

2634 is the process id of NetworkManager I found from your previous post, if you had not restarted or something, get the correct process id of it (/usr/sbin/NetworkManager).

after this execute

```
pgrep wpa_supplicant
```

Now you should not see any process id being given as output for the above command. 

After this execute the commands I had given in my first post in this thread starting with editing of /etc/wpa_supplicant.conf

After this your wireless should work.

---

### Post by Guitarmaster316 on 2009-04-26
~```
                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
"/etc/wpa_supplicant.conf" [New File]
```



This is what my .conf file looks like.  Do I type all of what you posted here?

---

### Post by Guitarmaster316 on 2009-04-26
```
matt@matt-laptop:~$ pgrep wpa_supplicant
7686
matt@matt-laptop:~$
```


This is the output after the wpa kill command.

Is this also from the newwork manager?

```
matt@matt-laptop:~$ sudo kill -9 2634
matt@matt-laptop:~$ pgrep wpa_supplicant
7686
matt@matt-laptop:~$
```

---

### Post by ittiam on 2009-04-26
Yes you can copy the entire content into the file and just put in your ssid and your passphrase

if you do not want to put in your ascii passphrase, to generate a hex passphrase execute the following 

```
wpa_passphrase <ssid> <wpa_password>
```

then just put the generated hex passphrase in wpa_supplicant.conf against psk= without the quotes. remember if you are using ascii passphrase you need to have the quotes.

---

### Post by ittiam on 2009-04-26
Did you kill the NetworkManager using kill -9 pid_number?

After you did a kill on network manager, do a pkill on wpa_supplicant again.

Then post the output of

```
ps aux | grep NetworkManager
```

and 

```
 ps aux | grep wpa 
```
> **Guitarmaster316 said:**
> ```
matt@matt-laptop:~$ pgrep wpa_supplicant
7686
matt@matt-laptop:~$
```


This is the output after the wpa kill command.

Is this also from the newwork manager?

```
matt@matt-laptop:~$ sudo kill -9 2634
matt@matt-laptop:~$ pgrep wpa_supplicant
7686
matt@matt-laptop:~$
```

---

### Post by Guitarmaster316 on 2009-04-26
Alright, I think I screwed something up.  I have this now...

```
E325: ATTENTION
Found a swap file by the name "/var/tmp/wpa_supplicant.conf.swp"
          owned by: root   dated: Sun Apr 26 21:19:19 2009
         file name: etc/wpa_supplicant.conf
          modified: YES
         user name: root   host name: matt-laptop
        process ID: 8628
While opening file "etc/wpa_supplicant.conf"

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r etc/wpa_supplicant.conf"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/var/tmp/wpa_supplicant.conf.
swp"
    to avoid this message.

"etc/wpa_supplicant.conf" [New DIRECTORY]
Press ENTER or type command to continue
```

---

### Post by ittiam on 2009-04-26
that is nothing. i guess the file was not closed properly last time hence vi still has it opened for writing. you can do

```
sudo rm /etc/.wpa_supplicant.conf.swp
```

or

```
 sudo rm /var/tmp/wpa_supplicant.conf.swp 
```



then open it again, it will open up fine.

---

### Post by Guitarmaster316 on 2009-04-26
How do I close the file once I paste the information into it?

Sorry for the dumb newbie questions :)

---

### Post by ittiam on 2009-04-26
1. Press Esc, then :
2. then enter wq (which means save and quit)
3. Press enter

This link will help you in working with vi

[http://www.eng.hawaii.edu/Tutor/vi.html](http://www.eng.hawaii.edu/Tutor/vi.html)

---

### Post by Guitarmaster316 on 2009-04-26
For some reason, when i paste into the .conf file it cuts off the "ctrl_i" part of the ctrl interfaces line.

When I try to close it with the wq command it gives me a can't write to file error.

Can I open this file with gedit??

---

### Post by ittiam on 2009-04-26
Yes you can edit it with whatever you are comfortable with.

---

### Post by Guitarmaster316 on 2009-04-26
Thanks for all your help.

It's still not working, but I have to go to bed.

I will review all the steps you have given me and hopefully I can make it work... again, thanks!

What about using the application wpa_gui??

---

### Post by ittiam on 2009-04-27
Post the output of 

[CODE]iwlist auth[\CODE]

This command is to verify whether you have wpa2 capability. Should have done this first but sorry I just assumed it should be capable nowadays.

If you can see wpa2 in the output the following will summarize as what you might need to do 

1) Kill NetworkManager
2) kill wpa_supplicant
3) pgrep wpa_supplicant and make sure it is not running
4) Run the sequence of steps in my first post in this thread.


Let know what happens.

---

### Post by Guitarmaster316 on 2009-04-27
```
matt@matt-laptop:~$ sudo iwlist auth
[sudo] password for matt: 
lo        no authentication information.

eth0      no authentication information.

wlan0     unknown authentication information.



pan0      no authentication information.

matt@matt-laptop:~$ 
```

This could be part of the problem.

---

### Post by Guitarmaster316 on 2009-04-27
```
matt@matt-laptop:~$ dmesg | grep -e ndis -e wlan0
[   20.223951] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   20.305141] usbcore: registered new interface driver ndiswrapper
[   26.074320] usbcore: deregistering interface driver ndiswrapper
[   26.095584] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   26.216639] ndiswrapper: driver bcmwl5 (Linksys,02/12/2003, 3.10.39.7) loaded
[   26.217056] ndiswrapper 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[   26.307339] ndiswrapper: using IRQ 10
[   26.521491] wlan0: ethernet device 00:90:4b:42:d4:a8 using NDIS driver: bcmwl5, version: 0x50000, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[COLOR="Red"][   26.521638] ndiswrapper (set_ndis_auth_mode:619): setting auth mode to 3 failed (C0010015)
[   26.521643] wlan0: encryption modes supported: none[/COLOR]
[   26.523434] usbcore: registered new interface driver ndiswrapper
[   33.894063] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  117.630912] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  128.120069] wlan0: no IPv6 routers present
matt@matt-laptop:~$
```

---

### Post by ittiam on 2009-04-27
So there you go, you do not have any encryption mode supported. Sorry to have  wasted your time suggesting other things.

---

### Post by sb92075 on 2009-04-27
[http://ubuntuforums.org/showthread.php?t=202834&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=202834&highlight=AR242x)

URL above is like giving chicken soup to a dead man.
It can't hurt & just might help some.

---

### Post by ittiam on 2009-04-27
You can find what wireless card you are using and google it up to check whether it supports different encryption algorithms

```
lspci
```

should show you the type of wireless NIC you are using

---

### Post by Guitarmaster316 on 2009-04-27
I know it is supported because it works fine with Windows XP.

I am wondering why there is a failure message in the dmesg.

Is it possible that the chip needs another file that is missing?

I have both the .sys and .inf files in the same folder.

---

### Post by ittiam on 2009-04-27
Do you have wpa_supplicant correctly installed? I remember pgrep wpa_supplicant yeilding output for you.

---

### Post by Guitarmaster316 on 2009-04-27
Here is my pgrep output

```
matt@matt-laptop:~$ pgrep wpa_supplicant
2639
matt@matt-laptop:~$
```

wpa supplicant was installed as part of Jaunty.  I can see it is installed in the synaptic package manager.  Is it possible that I need to remove this and re-install using apt-get or something else?

How do I associate it with ndiswrapper.  

It is my understanding that network manager will work with ndiswrapper... is this not right?

---

### Post by Guitarmaster316 on 2009-04-27
```
matt@matt-laptop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
matt@matt-laptop:~$ 
```

Is it possible that the alternate driver is conflicting??

Thanks again for sticking with me on this!

---

### Post by ittiam on 2009-04-27
You need to blacklist the ssb module.

Open the file /etc/modprobe.d/blacklist

and add the following 2 lines to the file
 
```
blacklist ssb
blacklist b43
```

then do the following

```
modprobe -r ndiswrapper
modprobe ndiswrapper
```

then post the output of

```
iwlist auth
```

---

### Post by Guitarmaster316 on 2009-04-27
```
matt@matt-laptop:~$ iwlist auth
lo        no authentication information.

eth0      no authentication information.

pan0      no authentication information.

wlan0     unknown authentication information.



matt@matt-laptop:~$
```

I blacklisted ssb and b43

I tried blacklisting b43 legacy and lost all connections.

I also still have this:

```
matt@matt-laptop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
matt@matt-laptop:~$ 
```

---

### Post by Guitarmaster316 on 2009-04-27
Even though it says ndiswrapper is operating, it seems that the b43legacy driver is still operating as well.

Everytime I blacklist b43legacy, the network stops working and wlan0 disappears.

When I rmmod ssb it says that ssb is in use by b44.

I feel like the answer is right there, just out of reach!

---

### Post by ittiam on 2009-04-28
remove the blacklisting of ssb and add the following to /etc/modprobe.d/blacklist

```
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist b44
```

then do

```
sudo gedit /etc/modules
```

make sure ndiswrapper is there, if not add it.

then:

```
sudo gedit /etc/rc.local
```

add the following in the exact same order

```
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe ssb
```

reboot.

---

### Post by Guitarmaster316 on 2009-04-28
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contain s the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ndiswrapper
```

After doing all that, nothing worked.  wlan0 was not there.

What is the module lp?

---

### Post by ittiam on 2009-04-28
Post your /etc/rc.local

and

lsmod | grep ndiswrapper

---

### Post by Guitarmaster316 on 2009-04-28
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe ssb
exit 0
```



```
matt@matt-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           193436  0 
matt@matt-laptop:~$
```

---

### Post by ittiam on 2009-04-28
Post the output of 

```
ndiswrapper -l
```

```
iwconfig
```

---

### Post by Guitarmaster316 on 2009-04-28
```
matt@matt-laptop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
matt@matt-laptop:~$ 
```

```
matt@matt-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"WAGGNET"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:19:E3:FB:73:9C   
          Bit Rate=54 Mb/s   Tx-Power:14 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

matt@matt-laptop:~$ 
```

---

### Post by ittiam on 2009-04-28
So you are connected to your wireless router. What is the problem?

---

### Post by Guitarmaster316 on 2009-04-28
The problem is that I can't connect to encrypted networks. ndiswrapper seems to have had a problem setting auth mode (see below).

I assume that this has something to do with encryption.

It has no problem connecting to an open network.

```
matt@matt-laptop:~$ dmesg | grep -e ndis -e wlan0
[   20.428075] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   20.495521] usbcore: registered new interface driver ndiswrapper
[   29.469008] usbcore: deregistering interface driver ndiswrapper
[   29.487112] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   29.522454] ndiswrapper: driver bcmwl5 (Linksys,02/12/2003, 3.10.39.7) loaded
[   29.522880] ndiswrapper 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[   29.613401] ndiswrapper: using IRQ 10
[   29.825202] wlan0: ethernet device 00:90:4b:42:d4:a8 using NDIS driver: bcmwl5, version: 0x50000, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[COLOR="Red"][   29.825350] ndiswrapper (set_ndis_auth_mode:619): setting auth mode to 3 failed (C0010015)
[   29.825355] wlan0: encryption modes supported: none[/COLOR]
[   29.827353] usbcore: registered new interface driver ndiswrapper
[   29.873760] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   87.650980] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  103.256070] wlan0: no IPv6 routers present
matt@matt-laptop:~$
```

---

### Post by ittiam on 2009-04-28
OK you initially posted you are not even able to see the wlan0 interface and that is why I asked you to post the output of iwconfig.

Removing and installing ndiswrapper from scratch seems to be the best option now. It should not take that much time.
Make sure the all blacklisting still exists

1) Remove ndiswrapper

2) remove the files in /etc/ndiswrapper

3) Then follow steps provided in this link

[http://www.cyberciti.biz/faq/linux-ndiswrapper-wpa_supplicant-howto/](http://www.cyberciti.biz/faq/linux-ndiswrapper-wpa_supplicant-howto/)

---

### Post by Guitarmaster316 on 2009-04-28
Will do.  Is the an easy way to completely remove ndiswrapper??

---

### Post by ittiam on 2009-04-28
Yes,

```
sudo apt-get remove ndiswrapper
```

or open Synaptic Package manager and you can mark it for removal and install it again

---

### Post by Guitarmaster316 on 2009-04-28
Ok, thanks.

I'll give it a try and let you know how it goes

---

### Post by ittiam on 2009-04-29
Worked?

---

### Post by Guitarmaster316 on 2009-04-29
No.  I couldn't get rid of ndiswrapper totally.  Even removing it with snyaptic manager and I tried apt-get remove.

After I removed it, it still showed up in dmesg.

b43legacy was working after that, but at the slow speeds again.

The two seem to be working together somehow, but yet conflicting.

With b43 blacklisted the network will not work and wlan0 disappears.  dmesg says that it couldn't initialize the driver.  Or something to that effect.

It's back to doing the same thing right now, works but no encryption.

---

### Post by ittiam on 2009-04-29
Instead of WPA2 could you just try using WPA and see whether it works?

---

### Post by Guitarmaster316 on 2009-04-29
I've tried WPA and WEP  and the same response.

I am stumped and frustrated. I feel like I am so close to the answer.  It would be nice to be able to use a native driver (b43legacy) since that does work.  However;  it is VERY slow and drops the connection.

Without b43legacy working the windows driver can't initialize the card for some reason.

I appreciate all your help and if you have any further suggestions that would be great!

---

### Post by ittiam on 2009-04-30
I have tried whatever I know but couldnt solve the problem. Maybe someone else might.

---

### Post by Guitarmaster316 on 2009-04-30
Thanks for all your help!  I appreciate all your time!

I'll figure it out eventually, kind of like a puzzle. :)

---

### Post by ittiam on 2009-04-30
Okay, Enable encryption on your wireless router (WPA or WPA2, not WEP) and post the output of the following

1.
```
lspci
```

2.
```
ps aux | grep NetworkManager
```

3. 
```
ndiswrapper -l
```

4. 
```
lsmod
```

5.
```
sudo gedit /etc/modprobe.d/blacklist
```

6.
```
sudo gedit /etc/rc.local
```

7.
```
 sudo pkill wpa_supplicant 
```

After killing the wpa_supplicant make sure no other instance of wpa_supplicant is running by doing
```
 pgrep wpa_supplicant 
```

Then post the output of
```
sudo wpa_supplicant -iwlan0 -Dwext -c/etc/wpa_supplicant.conf
``` (Notice -B is not provided in this command)

---

### Post by Guitarmaster316 on 2009-04-30
Ok, will do.  

Unfortunately, I am on a trip right now and and am using the hotel's open network.  I will have to do this on Monday afternoon when I get back home and have access to my router.  

I will post the results then.

Thanks!

---

### Post by ittiam on 2009-05-01
One more thing, I just found out that for blacklisting any modules since jaunty will have to be done in the following file

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

And add the following (do not blacklist b44)

```
blacklist bcm43xx
blacklist b43
blacklist b43legacy

```

---

### Post by Guitarmaster316 on 2009-05-06
HI Ittiam,

Here we go.  When I blacklist b43legacy I have no connections to any wireless.  

```
matt@matt-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
matt@matt-laptop:~$ ps aux | grep NetworkManager
root      2833  0.0  0.6  16552  2792 ?        Ssl  09:40   0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      2839  0.0  0.7   7048  3124 ?        S    09:40   0:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
matt      3683  0.0  0.1   3340   804 pts/0    R+   09:42   0:00 grep NetworkManager

matt@matt-laptop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)

matt@matt-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
radeon                342816  2 
drm                    96296  3 radeon
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
b44                    35984  0 
ssb                    41220  1 b44
mii                    13312  1 b44
ndiswrapper           193436  0 
ipt_REJECT             11136  1 
ipt_LOG                13700  1 
xt_limit               10116  2 
xt_tcpudp              11008  7 
xt_state               10112  5 
ipt_addrtype           10496  4 
ip6table_filter        10624  1 
ip6_tables             20880  1 ip6table_filter
nf_nat_irc             10240  0 
nf_conntrack_irc       13220  1 nf_nat_irc
nf_nat_ftp             10752  0 
nf_nat                 25876  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      21388  7 nf_nat
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4
nf_conntrack_ftp       15652  1 nf_nat_ftp
nf_conntrack           72008  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         10752  1 
ip_tables              19472  1 iptable_filter
x_tables               23044  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_state,ipt_addrtype,ip6_tables,ip_tables
lp                     17156  0 
joydev                 18368  0 
snd_ali5451            27276  3 
snd_ac97_codec        112292  1 snd_ali5451
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 44748  0 
snd                    62628  16 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
psmouse                61972  0 
ati_agp                14988  1 
ppdev                  15620  0 
video                  25360  0 
snd_page_alloc         16904  1 snd_pcm
pcspkr                 10496  0 
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
serio_raw              13316  0 
i2c_ali15x3            14724  0 
i2c_ali1535            14212  0 
agpgart                42696  2 drm,ati_agp
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
output                 11008  1 video
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 40212  0 
natsemi                35552  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

matt@matt-laptop:~$ sudo wpa_supplicant -iwlan0 -Dwext -c/etc/wpa-supplicant.conf
[sudo] password for matt: 
Failed to read or parse configuration '/etc/wpa-supplicant.conf'.
matt@matt-laptop:~$ sudo gedit /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

# Troubleshooting ndiswrapper with bcmwl5
blacklist b43
blacklist b43legacy

sudo gedit /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe ssb
exit 0

```

```
matt@matt-laptop:~$ iwconfig wlan0
wlan0     No such device

matt@matt-laptop:~$ 

```

As you can see, when b43legacy is blacklisted wlan0 disappears.

When b43legacy is not blacklisted it works fine (on open networks only)and shows ndiswrapper as the driver.

Thanks again for your help!

---

### Post by Guitarmaster316 on 2009-05-06
```
matt@matt-laptop:~$ dmesg | grep -e ndis -e wlan0
[   19.974732] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   20.073072] usbcore: registered new interface driver ndiswrapper
[   27.334359] usbcore: deregistering interface driver ndiswrapper
[   27.351087] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   27.458988] ndiswrapper: driver bcmwl5 (Linksys,02/12/2003, 3.10.39.7) loaded
[   27.459403] ndiswrapper 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[   27.472088] ndiswrapper (NdisWriteErrorLogEntry:190): log: C000138D, count: 1, return_address: dcb015e2
[   27.472098] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x104
[   27.472191] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[   27.472202] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[   27.472219] ndiswrapper (mp_halt:262): device d9f00500 is not initialized - not halting
[   27.472224] ndiswrapper: device eth%d removed
[   27.472247] ndiswrapper 0000:00:09.0: PCI INT A disabled
[   27.472278] ndiswrapper: probe of 0000:00:09.0 failed with error -22
[   27.474864] usbcore: registered new interface driver ndiswrapper
matt@matt-laptop:~$
```

---

### Post by ittiam on 2009-05-07
wpa_supplicant says it failed to read the configuration file. Have you got file in correct format?

Also wlan0 may not always be the name of your wireless interface. Blacklist b43legacy and simply execute > iwconfig|. (just to make sure)]

---

### Post by Guitarmaster316 on 2009-05-07
I guess I don't know what the correct format would be.  Can you give me an example?

When I blacklist b43legacy, wlan0 disappears totally and there is no connection at all to wireless.  Also, the last time I blacklisted then took it out, it created another file with a ~ at the end.  What is this about?

---

### Post by ittiam on 2009-05-07
Once you blacklist b43legacy, reboot the system. You should atleast be able to see the wireless interface using iwconfig. With your rc.local taking care of ndiswrapper you should definitely be able to see the wireless interface. Regarding the format of wpa_supplicant.conf there are scores of links available via google, just copy paste from one of them and change your ssid and password.

Once you do that paste your wpa_supplicant.conf

---

### Post by Guitarmaster316 on 2009-05-11
Sorry for the long delay....

Blacklisting b43legacy and rebooting gets rid of wlan0 all together.  It will not show up in ifconfig.

I checked the wpa_supplicant.conf, but I don't understand what is in he file.  It is located in /etc/dbus-1/system.d  

I tried adding the configuration lines to this file, but it stopped working on open networks... don't know about WPA.  NM said "device not connected"  iwconfig showed a connection, but I couldn't get on the internet



```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe ssb

exit 0
```

wpa_supplicant.conf

```
<!DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
        <policy user="root">
                <allow own="fi.epitest.hostap.WPASupplicant"/>

                <allow send_destination="fi.epitest.hostap.WPASupplicant"/>
                <allow send_interface="fi.epitest.hostap.WPASupplicant"/>
        </policy>
        <policy group="netdev">
                <allow send_destination="fi.epitest.hostap.WPASupplicant"/>
                <allow send_interface="fi.epitest.hostap.WPASupplicant"/>
        </policy>
        <policy context="default">
                <deny own="fi.epitest.hostap.WPASupplicant"/>
                <deny send_destination="fi.epitest.hostap.WPASupplicant"/>
                <deny send_interface="fi.epitest.hostap.WPASupplicant"/>
        </policy>
</busconfig>
```

---

### Post by Guitarmaster316 on 2009-05-11
This is the output with b43legacy blacklisted.  It appears that ndiswrapper can't initialize the wireless card and wlan0 goes bye bye.



```
matt@mattz:~$ dmesg | grep -e ndis
[   21.876717] ndiswrapper version 1.54 loaded (smp=yes, preempt=no)
[   21.957782] ndiswrapper: driver bcmwl5 (Linksys,02/12/2003, 3.10.39.7) loaded
[   21.958197] ndiswrapper 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[   21.970860] ndiswrapper (NdisWriteErrorLogEntry:190): log: C000138D, count: 1, return_address: dcaa65e2
[   21.970869] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x104
[   21.970962] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[   21.970975] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[   21.970993] ndiswrapper (mp_halt:262): device d9c7c500 is not initialized - not halting
[   21.970998] ndiswrapper: device eth%d removed
[   21.971021] ndiswrapper 0000:00:09.0: PCI INT A disabled
[   21.971052] ndiswrapper: probe of 0000:00:09.0 failed with error -22
[   21.975221] usbcore: registered new interface driver ndiswrapper
[   27.276654] usbcore: deregistering interface driver ndiswrapper
[   27.276815] ndiswrapper (ntoskernel_exit:2677): object d9be4420(2) was not freed, freeing it now
[   27.294582] ndiswrapper version 1.54 loaded (smp=yes, preempt=no)
[   27.315090] ndiswrapper: driver bcmwl5 (Linksys,02/12/2003, 3.10.39.7) loaded
[   27.315539] ndiswrapper 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[   27.322399] ndiswrapper (NdisWriteErrorLogEntry:190): log: C000138D, count: 1, return_address: dcb925e2
[   27.322408] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x104
[   27.322506] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[   27.322519] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[   27.322537] ndiswrapper (mp_halt:262): device da569500 is not initialized - not halting
[   27.322541] ndiswrapper: device eth%d removed
[   27.322566] ndiswrapper 0000:00:09.0: PCI INT A disabled
[   27.322597] ndiswrapper: probe of 0000:00:09.0 failed with error -22
[   27.327067] usbcore: registered new interface driver ndiswrapper
matt@mattz:~$ 


```

---

### Post by ittiam on 2009-05-13
One thing is your wpa_supplicant.conf has all XML, the file is totally wrong. Once you blacklist b43legacy and install ndiswrapper, wireless interface should showup using iwconfig. I am out of ideas.

---

### Post by Guitarmaster316 on 2009-05-15
Thanks Ittiam, I appreciate all your help!

IT seems like b43legacy initiates the card and ndiswrapper takes over from there.

I have tried many different things with the .conf file, but nothing works.

I did notice that many others are having the same problem when blacklisting b43legacy.  Maybe it is a problem with Jaunty.

Again, thanks for all your help!

---

### Post by ittiam on 2009-05-15
If and when you make it work, please do let me know how.

---

### Post by foxy123 on 2009-06-06
I have been trying to use ndiswrapper with my bcm4306 since Gutsy. It used to work perfectly fine in Dapper (I skipped Edgy all together) but has stopped since then. I am not sure if it is ndiswrapper, Windows driver or Ubuntu problem, but it is definitely something wrong with the ability to resolve the encryption. It works fine without security enabled. 

I am moving my laptop downstairs and to get the Ethernet cable here is a hassle while the native bcm43legacy is too slow. If anyone finds a solution to this problem please post here.

---

