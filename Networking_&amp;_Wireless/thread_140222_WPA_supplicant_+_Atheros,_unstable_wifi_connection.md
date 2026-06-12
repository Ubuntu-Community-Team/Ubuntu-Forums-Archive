---
title: "WPA_supplicant + Atheros, unstable wifi connection?"
date: 2006-03-05
forum: Networking &amp; Wireless
---

### Post by ssalman on 2006-03-05
I have posted this problem before, but got no answers, so I went back did more research and I'm posting again in hope someone will be able to help me out. :)

I have a Netgear WG511T PCMCIA wifi card with an Atheros chipset. The card works great with Ubuntu on unsecured connections, even with WPA_supplicant I get some kind of a connection. The problem is that the connection I get with WPA is not stable, it alternates between connected (for about 15 sec) and disconnected (for about 3 sec). This really affect the over all speed of my internet connection even when I'm just browsing. not to mention how annoying this has become! :(

I have another laptop with an Intel/ipw wifi chipset/driver, and it is not having any issues with the same AP. here are my wpa_cli output and configuration files. Thanks in advance. :)


this is what I get just by typing "sudo wpa_cli" and nothing more inside wpa_cli!!! (i've replaced the AP and SSID with x's)

```
<2>CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
<2>Trying to associate with xx:xx:xx:xx:xx:xx (SSID='xxxxxxxx' freq=2452 MHz)
<2>Associated with xx:xx:xx:xx:xx:xx
<2>WPA: Key negotiation completed with xx:xx:xx:xx:xx:xx [PTK=TKIP GTK=TKIP]
<2>CTRL-EVENT-CONNECTED - Connection to xx:xx:xx:xx:xx:xx completed (reauth)
<2>CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
<2>Trying to associate with xx:xx:xx:xx:xx:xx (SSID='xxxxxxxx' freq=2452 MHz)
<2>Associated with xx:xx:xx:xx:xx:xx
<2>WPA: Key negotiation completed with xx:xx:xx:xx:xx:xx [PTK=TKIP GTK=TKIP]
<2>CTRL-EVENT-CONNECTED - Connection to xx:xx:xx:xx:xx:xx completed (reauth)
<2>CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
<2>Trying to associate with xx:xx:xx:xx:xx:xx (SSID='xxxxxxxx' freq=2452 MHz)
<2>Associated with xx:xx:xx:xx:xx:xx
<2>WPA: Key negotiation completed with xx:xx:xx:xx:xx:xx [PTK=TKIP GTK=TKIP]
<2>CTRL-EVENT-CONNECTED - Connection to xx:xx:xx:xx:xx:xx completed (reauth)

``` 
The above behavior does not happen at all at my Intel laptop. Below is my "/etc/default/wpasupplicant" setup for the Atheros, with the Intel setup commented out.

```
ENABLED=1
OPTIONS="-D madwifi -i ath0 -c /etc/wpa_supplicant.conf"
#OPTIONS="-D ipw -i eth1 -c /etc/wpa_supplicant.conf"

``` 
below is my "/etc/wpa_supplicant.conf" setup for Atheros, Intel's setup is the same but does not contain the line with "scan_ssid=1" as it worked with my hidden AP ssid without it, the Atheros setup needed this line to figure out the hidden ssid.

```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

ap_scan=1
fast_reauth=1

network={
    key_mgmt=WPA-PSK
    scan_ssid=1
        ssid="xxxxxxxx"
    psk=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
}


```

---

### Post by firecat53 on 2006-03-06
First, try adding "proto=WPA" to your wpa_supplicant.conf file inside the "network=" section.  Then try removing the scan_ssid line, and all the lines before the "network=" line if that doesn't work.

Good luck!

Scott

---

### Post by Skye on 2006-03-06
I have the exact same setup- a netgear WG511T, and the exact same problem- wireless maintains connection for 7 seconds (I timed it) every time, and then disconnects.  I recently (today) switched to Dapper, and everything works great, save for the wireless.

I'm currently using wpa_supplicant 0.5.1 and the most recent madwifi drivers.

Things I've done so far:
-Screwed around with the /etc/wpa_supplicant.conf file, which currently looks like this:
```

network={
        ssid="Neonet"
#     scan_ssid=1
        proto=WPA
#     key_mgmt=WPA-PSK
        psk=my psk, in hex
}

```

-Compiled wpa_supplicant from source, both verion 0.4.8 and version 0.5.1.
-Changed the wpa_supplicant .config file around (currently, it looks like this:
```

CONFIG_DRIVER_MADWIFI=y
CFLAGS += -I /usr/src/madwifi-ng
CONFIG_CTRL_IFACE=y

```

-Tried various different snapshots of the madwifi driver, with no luck (the latest, some recent ones, and then all the way back to when they stopped loading cleanly on my system.

I'm now out of ideas.  Anyone else have any?

---

### Post by ssalman on 2006-03-06
[FONT=Arial]Similar to what Skye did, I have tried many combinations of the wpa_supplicant.conf parameters and nothing would work. But I didn't go as far into trying different driver snapshots, or wpa_supplicant versions. But now that I know what Skye have tried it disturbs me. 

  Is that a madwifi driver issue, so we can post a bug report, as I hear they are make constant progress all the time.

[/FONT]           [FONT=Arial]Or is it a Netgear issue, so I can vote with my money and return it back?[/FONT]

---

### Post by Skye on 2006-03-06
I don't think it's a hardware issue-  I know the card works (it does in windows) and I know it *can* work in linux- it did before I upgraded to Dapper. That being said, I've re-created everything I had in Breezy again in Dapper, and i still have this problem.

Having said that, I don't know where the problem lies- either in wpa_supplicant, or the different driver versions... changing both doesn't seem to affect the problem.

I think what we're looking for is something that's common between all versions of wpa_supplicant and madwifi-ng... some other software thing that is broken, and can be fixed.  But, for the life of me, I can't think of anything else to change.

What other software components effect a wireless link?

---

### Post by ssalman on 2006-03-06
Okay, That seems a little odd, I'm having the problem in Breezy, and you are saying it used to work in Breezy, but not in Dapper?? could it be my dependencies[FONT=&quot]?[/FONT]

---

### Post by firecat53 on 2006-03-06
I'm running breezy with a self-compiled 2.6.15 kernel, and I've had the best luck using the CVS version of madwifi-old, and the latest wpa_supplicant version (.5 something from CVS). This combination has worked reliably with both the original 2.6.12.x kernels, 2.6.14 and 2.6.15.  Again, I'm using a DWL-G630, so different card, but same Atheros chipset. 

I also had some trouble with the madwifi-ng driver, but as I recall it was mostly because of a long time (>30sec) to initially get a connection and issues with suspend/resume correctly on my laptop.  Honestly, I haven't gone back and had another go at it in a few months now. 

My wpa_supplicant.conf file is something like (I'm not at my laptop right now):
```
network={
        ssid="homenetworkid"
        proto=WPA
        key_mgmt=WPA-PSK
        psk="my psk in hex"
}
```

Good luck!
Scott

---

### Post by ssalman on 2006-03-06
What madwifi driver version do we get with the repository&#8217;s restricted kernel? Is it madwifi-ng?

---

### Post by Skye on 2006-03-06
Im not sure which driver we get with the restricted modules, but I have some good news, I think everything is working for me now!

Here's what I did:

1- Wiped my install.  You probably won't have to go that far, but since mine was almost new anyway, I didn't lose anything from wiping it.

2- Removed the restricted-modules package from my computer, (in synatic, use the "Remove Completely" option) and got rid of anything pertaining to previous versions of madwifi or wpa_supplicant.  Reboot after that's all done

3-  Did the following commands in the following order:

Install the latest Madwifi-ng driver:
```

cd /usr/src
sudo wget http://snapshots.madwifi.org/madwifi-ng-current.tar.gz
sudo tar -xvzf madwifi-ng-current.tar.gz
sudo mv madwifi-ng-r1460-20060304 madwifi-ng
cd madwifi-ng
sudo make clean
sudo make
sudo make install
sudo modprobe ath_pci

```

Install wpa_supplicant
```

cd ~/
wget http://hostap.epitest.fi/releases/wpa_supplicant-0.5.1.tar.gz
tar -xvzf wpa_supplicant-0.5.1.tar.gz
cd wpa_supplicant-0.5.1

```
Next, insert the .config file into that directory- mine is attached at the end of this post, it should work for you.

```

sudo make
sudo make wpa_gui 

```
This gui requires alot of different qt/ qt development libs- I don't remember which ones, but anything with qt3 or qt4 and "dev" in it should help- do a search in synaptic.  This is by no means a required step, but a gui is a nice thing.

Next, copy over the executables to /usr/sbin, where the system will know to find them.
```

sudo cp wpa_cli wpa_passphrase wpa_supplicant ./wpa_gui/wpa_gui /usr/bin
sudo gedit /etc/wpa_supplicant.conf

```

My wpa_supplicant.conf file is attached at the end of this post alongside the .config file.

Finally, bring up the network for testing:
```

sudo wpa_supplicant -dd -i ath0 -c/etc/wpa_supplicant.conf -D madwifi -w

```

This should display alot of junk, but end up with a connected network, with "CONNECTED" being displayed.  If you want to cut down on the log verbosity, remove the "-dd" from the command- that asks for extra verbosity.

Hopefully, all this works, so you can edit your /etc/network/interfaces file so that the portion pertaining to ath0 looks like this::

```

auto ath0
iface ath0 inet dhcp
 pre-up wpa_supplicant -i ath0 -c/etc/wpa_supplicant.conf -D madwifi -w && dhclient
 pre-down wpa_cli terminate

```

This last portion brings up ath0 on boot, and assumes you will be in range of your AP when your computer starts.  You can cancel it at boot if you're not in range by pressing ctrl + C.

I hope this helps you!

The attachments function seems not to be working, so here are the relevant files:

.config (for wpa_supplicant)
```

CONFIG_DRIVER_MADWIFI=y
CFLAGS += -I/usr/src/madwifi-ng
CONFIG_CTRL_IFACE=y

```

/etc/wpa_suppliant.conf
```

##Obtain the network block for your specific setup by running:
## sudo wpa_passphrase SSID_OF_YOUR_NETWORK PSK_IN_PLAINTEXT 

ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="Neonet"
        psk=your PSK
}

```

3/6/2006: Edited to include a dhcp request in the networking config.

---

### Post by ssalman on 2006-03-06
THANKS Skye!!!

That was some detailed instructions, I will give it a try and see if it will work for me. I will post my results.

---

### Post by Skye on 2006-03-07
One thing to note, I've had to run ```
sudo dhclient ath0
``` to get a dhcp address assigned to my computer... i'm sure there's some way to include this in /etc/network/interfaces (as I tried to do) but it doesn't work for me.  The connection itself is fine, though

---

### Post by ssalman on 2006-03-07
Skye, I'm having trouble installing the driver, I tried to install the kernel headers, but I'm now stuck with the following error, could you please help me out.

```
root@x20:/usr/src/madwifi-ng# make clean
/bin/sh: cc: command not found
for i in ./ath_hal ./net80211 ath_rate/sample ./ath; do \
        make -C $i clean; \
done
/bin/sh: cc: command not found
make[1]: Entering directory `/usr/src/madwifi-ng/ath_hal'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
rm -f ah_osdep.c opt_ah.h hal.o
make[1]: Leaving directory `/usr/src/madwifi-ng/ath_hal'
/bin/sh: cc: command not found
make[1]: Entering directory `/usr/src/madwifi-ng/net80211'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[1]: Leaving directory `/usr/src/madwifi-ng/net80211'
/bin/sh: cc: command not found
make[1]: Entering directory `/usr/src/madwifi-ng/ath_rate/sample'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[1]: Leaving directory `/usr/src/madwifi-ng/ath_rate/sample'
/bin/sh: cc: command not found
make[1]: Entering directory `/usr/src/madwifi-ng/ath'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[1]: Leaving directory `/usr/src/madwifi-ng/ath'
make -C ./tools  clean
make[1]: Entering directory `/usr/src/madwifi-ng/tools'
rm -f athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig core a.out
make[1]: Leaving directory `/usr/src/madwifi-ng/tools'
rm -rf ./symbols
rm -f svnversion.h
root@x20:/usr/src/madwifi-ng# make
/bin/sh: cc: command not found
Checking requirements... ok.
Checking kernel configuration... FAILED
Only kernel versions 2.4.x and above are supported.
You have .
make: *** [configcheck] Error 1
root@x20:/usr/src/madwifi-ng#

```

and are we recompiling the kernel or just the madwifi-nd driver? I'm kind of new to the whole thing.

---

### Post by Skye on 2006-03-07
We're just compiling the madwifi-ng kernel driver-  they need to be compiled specifically to reflect your kernel version.

It looks like you're lacking either the compilation tools, or kernel headers, or maybe both.  Run the following at a command prompt:
```

sudo apt-get install build-essential linux-headers-$(uname -r)

```
and once that's done, retry making the madwifi-ng drivers.  If you have problems, post back here and we'll figure it out.

---

### Post by ssalman on 2006-03-08
Skye,
 Thanks for your help with this. I'm now stuck a little further in the make process and I think I'm still missing some package, please check my attached make output (or what I could get out of it). Thanks again Skye.

---

### Post by Skye on 2006-03-08
I'm glad I can help, I understand how frustrating this can be.  I'm not really sure what is causing this problem, but I do have a guess and a plan of action.

Do the following: (these commands add library I forgot to mention, and also removes the specific copy of the driver package on your machine.  Both could possibly fix your problem.)
```

sudo apt-get install sharutils
cd /usr/src
sudo rm -rf madwifi-ng*

```
Then pick up the howto I wrote earlier in the thread at the beginning, and go from there.  Good luck (!), and tell me how it turns out.

---

### Post by ssalman on 2006-03-08
I did what you suggested, but it found that I do have that package, but I continued anyway, and it is still stuck at the same place, I'm trying to direct all it's output to a file so I can show you the whole output, but it is not letting me. I'm using "sudo make > ~\Desktop\out.txt". is there a way to get all the make output directed to a  file? and what else could be stoping thee make process?

Thanks again for your help.

---

### Post by Skye on 2006-03-08
Hrm.  I agree that it seems as if you're missing some sort of essential package.  This might be easier if we could talk in real-time, do you have AIM?  (I'm TotaLackOfSanity)

As to redirecting the file, try ```
sudo make > /home/USERNAME/Desktop/output.txt
```  Remember that in linux, the slashes go the opposite was as in Windows.

---

### Post by ssalman on 2006-03-08
Well I was able to increase my terminal scroll buffer and now I have the full output attached. Thanks Skye

---

### Post by Skye on 2006-03-08
Oh!  I know what's wrong now.  

First off, do 
```

sudo apt-get install subversion

```

Then, to quote from another HOWTO:
[quote=http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=804955]
There is an error that comes up if you don't follow this step first.

Open Makefile.inc

```

sudo gedit Makefile.inc

```

towards the bottom is a line line that needs to be modified.

COPTS+= -Werror

change this line and remove the -Werror part so line now looks like this.

COPTS+=

This will not affect driver in anyway, it's just something in the way ubuntu built the kernel for breezy which will prevent installing the driver.
[/quote]

Once that's done, try again, it should work.

---

### Post by ssalman on 2006-03-10
Thanks Skye for your help.

I was able to compile and follow your instructions without much trouble, I had to get few QT dependences and install gcc-3.4 but after I figured how the process works it was a matter of time. Now I got the latest madwifi driver and wpa_supplicant on my system, it looks like it is up and running with my AP associated all the time, I still have a problem connecting to the internet, but I believe it's a parameters setup thing, and I will work on it this weekend. I will post my results once everything is up and running.

Again thanks for your help Skye.

---

### Post by Skye on 2006-03-10
I think i encountered this problem as well.  When your link is up, run 
[/code] sudo dhclient ath0[/code]

And try to access the web, it should work.

---

### Post by ssalman on 2006-03-10
The thing is that I have a static IP not a dynamic IP, so I'll have to figure out why my connection is not working. I'm still guessing it's the WPA parameters as I also have a hidden ESSID.

---

### Post by Skye on 2006-03-11
If you have a hidden essid, add the following to your /etc/wpa_supplicant.conf file, inside the network block for your network:
```

network={
        **scan_ssid=1**
        ssid="YourSSID"
        psk=your PSK
}

```
(The thing to add is in bold)

Now run 
```

sudo wpa_supplicant -dd -i ath0 -c/etc/wpa_supplicant.conf -D madwifi -w 

```

And see if it connects to your network.  The above command won't stop on its own, after awhile, press ctrl + c in the terminal window to stop it.  Good Luck!

If that fails, paste some of the output here.

---

### Post by ssalman on 2006-03-11
Well I'm still having trouble :( here is what I have done so far...
  
When I boot it got stuck in the network part, and I know it is the wpa_supplicant, so I press ctrl-c and move on, from the command line when I run wpa_supplicant it connects right away after few sec of scanning (but with no internet yet) so I added -B to my pre-up line in the /etc/network/interface file, and now it boots without stopping at the network part, and when I get to Gnome I see that my panel network indicator is up, I check wpa_cli using the "status" command, and I have the following:
  
  ```

  bssid=xx:xx:xx:xx:xx:xx
  ssid=MY_SSID
  pairwise_cipher=TKIP
  group_cipher=TKIP
  key_mgmt=WPA-PSK
  wpa_state=COMPLETED
  
```   
and I don't have the problem I used to have at the begining of this thread of connecting and disconnecting... So I think I have a solid connection with my router...
  
  But, when I ping my router it does not respond. This could be also tied to another problem I was having at [this]("http://www.ubuntuforums.org/showthread.php?t=140225") thread. but any way I'll post my configuration files below... I hope you can help me... and Thanks for all your time Skye. 
 

```
 root@x20:~# cat /etc/wpa_supplicant.conf
##Obtain the network block for your specific setup by running:
## sudo wpa_passphrase SSID_OF_YOUR_NETWORK PSK_IN_PLAINTEXT

ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="MY_SSID"
        key_mgmt=WPA-PSK
        scan_ssid=1
        psk=MY_PSK_KEY
}

``` 
```

root@x20:~# cat /etc/default/wpasupplicant
# /etc/default/wpasupplicant

# WARNING! Make sure you have a configuration file!

ENABLED=1

# Useful flags:
#  -D <driver>          Wireless drive, typically optional.
#  -i <ifname>          Interface
#  -c <config file>     Configuration file
#  -d                   Debugging (-dd for more)
#  -w                   Wait for interface to come up

# See the manual page wpa_supplicant(1) for more options and information.

OPTIONS="-i ath0 -D madwifi -c /etc/wpa_supplicant.conf -w"

# EXAMPLES:

# OPTIONS="-i wlan0 -D hostap -c /etc/wpa_supplicant.conf"
# OPTIONS="-i ath0 -D madwifi -c /etc/wpa_supplicant.conf"

``` ```
root@x20:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface ath0 inet static
wireless-essid MY_SSID
address 192.168.2.4
netmask 255.255.255.0
gateway 192.168.2.1
dns-nameservers 192.168.2.1
#dns-search ip3networks.com

#pre-up wpa_supplicant -i ath0 -c/etc/wpa_supplicant.conf -D madwifi -w && dhclient
#pre-up wpa_supplicant -i ath0 -c/etc/wpa_supplicant.conf -D madwifi -w -B
pre-up wpa_supplicant -i ath0 -c/etc/wpa_supplicant.conf -D madwifi -B
pre-down wpa_cli terminate
auto ath0

```

---

### Post by ssalman on 2006-03-13
Okay, I have tried one more thing...

I commented-out all the pre-up and pre-down lines in the interface file and booted, of course I didn’t have wireless connection so I started wpa_supplicant:
   
```
wpa_supplicant -i ath0 -c/etc/wpa_supplicant.conf -D madwifi -w
```  

and when I had a CONNECTED message, I verified with the “wpa_cli status” command and for sure I had a solid connection. I then pinged my router with “ping 192.168.2.1” but it did not respond. I then enabled DHCP on my router and used “dhclient ath0” to get IP address and it worked and I hade my Internet connection working, I could “ping [www.google.com]("http://www.google.com/")” successfully :)
   
  So it seams that my new driver/wpa_supplicant combination is working perfectly, but my problem lies in the static IP and DNS setup, any idea how would I go about fixing this… I tried to add it to the interface file but it didn’t work (see previous post).
   
  Thanks for your help.

---

### Post by Skye on 2006-03-13
Hey-

I'm at school right now but I have a script at home that I found online that should do the trick.  I'll edit this post tonight with the text of the script and a how-to on how to use it.

EDIT:

It's great that you got DHCP working- it makes fixing this so much easier.

First thing, create a file in /etc called wireless.sh

```

sudo gedit /etc/wireless.sh

```

Paste the following into the file, (NOTE: spacing and line breaks are important- make sure they are exactly as they appear here)
```

#!/bin/sh

# wifi: wpa_supplicant init
echo " * [Wifi]: Enabling WPA supplicant..."
wpa_cli terminate
if [ -x /usr/sbin/wpa_supplicant ]; then
 /usr/sbin/wpa_supplicant -i ath0 -c /etc/wpa_supplicant.conf -D madwifi -w &
fi

sleep 2

#use dhcp to request a network address
echo " * [Wifi]: Requesting DHCP address..."
dhclient ath0

exit 0

```
(Also note: This code is NOT my work.  I found it while looking around on the web for help with setting up wireless at boot, and have since edited it slightly, but I have lost the original page.  If this is your code, please notify me and i'll credit you.)

Once that's in the file, save it, and close gedit.  You have to make sure it's executable, so run:
```

sudo chmod +x /etc/wireless.sh

```

Last thing to do is to make the script run at startup.  To do that, do:
```

cd /etc/rcS.d
sudo ln -s S40wifi /etc/wireless.sh

```

The "S40" part is the important here, because that combination means that the script will be run in place 40, which is after the hardware devices (AKA the wireless card) are given power and recognized, but before network-dependent tasks like nfs and samba shares are mounted.  The addition of "wifi" to the end only signifies its purpose.

Reboot, and wireless *should* start at boot.  Good Luck!

---

### Post by ssalman on 2006-03-14
Thanks Skye,

I followed your steps with the following changes:

replaced
```
sudo ln -s S40wifi /etc/wireless.sh
```   with
```
sudo ln -s /etc/wireless.sh S40wifi
```   
and replaced
```
/usr/sbin/wpa_supplicant
``` with
```
/usr/bin/wpa_supplicant
``` 
and at boot it seamed to work, it took quite a while to boot (about 90 Sec. more) but it got an IP from dhcp. But when I finally got to Gnome and tried to ping the router it didn't respond, the panel network indicator showed connected and so did the wpa_cli status.

I opened a terminal window and typed the following and it worked:

```

sudo ifdown ath0
sudo ifup ath0
ping 192.168.2.1

``` 

The ifup command started the dhcp call and got a new ip and the router ping worked. (Note: I have changed the interfaces file to be dhcp instead of static for ath0)

This tells me that I have a configuration file that overrides my settings after the S40wpa file, as in boot I do get an ip but lose that when I get to Gnome, trying to do dhclient didn't help either, so it looks like the ath0 interface gets messedup after we configured it and before we get to the Gnome desktop.... and only a ifdown + ifup will fix it!

Any ideas!! ??? :)

Thanks.

---

### Post by ssalman on 2006-03-14
UPDATE: So far the WPA/MadWifi combination works great, but I'm having trouble with the IP/DHCP setup... I think I found a work around... I will edit this post tonight with the details. Thanks for all your help and time Skye.

---

### Post by ssalman on 2006-03-15
The Ubuntu Forum was down for maintinance last night so I couldn't post my new setup.... Anyway... here we go.

The new setup uses the interface configuration file and the post-up command. I have deleted the wireless.sh script and removed it's link from the the rcS.d directory as it is not needed in this setup. I also disabled the time synchronization at boot (by adding a "exit 0" at the begining of the configuration file) as it won't work with this setup.

In this setup, Ubuntu boots and starts the WPA_supplicant but don't wait on it to associate, and continue to setup networking using static ip. Just seconds before the Gnome desktop appears, my card makes the association (two leds blinking together) and when the desktop is up, I see that I have solid connection with the router, wpa_cli status confirms that too. My static ip setup is still not working, so I have to use "sudo dhclient ath0" to get ip setup. once that is done I can ping my router and can surf the internet.

I think the only thing I have to fix now is the static IP setup. the advantage it has over DHCP is that I don't need to wait for wpa_supplicant to associate with the router before I get successfull dchp answer, which will increase my boot time with about 45 seconds.

here are my configuration files:

```
$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface ath0 inet static
wireless-essid SinanNet
address 192.168.2.4
netmask 255.255.255.0
gateway 192.168.2.1
dns-search SinanNet
dns-nameservers 192.168.2.1
post-up wpa_supplicant -i ath0 -c/etc/wpa_supplicant.conf -D madwifi -w -B
pre-down wpa_cli terminate
auto ath0


``` 
and when I boot I don't get a valid IP
```
$ ifconfig ath0
ath0      Link encap:Ethernet  HWaddr 00:0F:B5:64:03:5C
          inet6 addr: fe80::20f:b5ff:fe64:35c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:813 (813.0 b)  TX bytes:476 (476.0 b)

``` so I use dhclient
```
$ sudo dhclient ath0
Password:
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ath0/00:0f:b5:64:03:5c
Sending on   LPF/ath0/00:0f:b5:64:03:5c
Sending on   Socket/fallback
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.11 -- renewal in 1005088681 seconds.

``` and now I have a valid IP setup
```
$ ifconfig ath0
ath0      Link encap:Ethernet  HWaddr 00:0F:B5:64:03:5C
          inet addr:192.168.2.11  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fe64:35c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1403 (1.3 KiB)  TX bytes:818 (818.0 b)

``` and valid DNS
```
$ cat /etc/resolv.conf
search SinanNet
nameserver 192.168.2.1

``` 
at the end I want to thank Skye for all the help and time, I wouldn't got it to work without your help Skye... Thanks.

---

### Post by Skye on 2006-03-15
It's great that you got everything working, and I'm glad I could help!

---

### Post by onioneater36 on 2006-10-03
MEGAbump.  I have had similar problems and will be reading thru this entire thread, but I am short on time tonight.  I will post my problems and add info if anything in this thread cured them.

Thanks a ton!!!

---

### Post by Skye on 2006-10-03
As of Dapper, I'm pretty sure WPA with Atheros is pretty straightfoward.  Just make sure you've installed the restricted-modules package for your kernel, as well as the **network-manager-gnome** package (assuming you're running gnome.)  Reboot, and you should be all set.

Good Luck!

---

