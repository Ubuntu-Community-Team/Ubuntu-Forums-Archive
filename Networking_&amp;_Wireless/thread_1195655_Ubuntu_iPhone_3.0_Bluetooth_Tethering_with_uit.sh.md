---
title: "Ubuntu iPhone 3.0 Bluetooth Tethering with uit.sh"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by cooperlees on 2009-06-24
If you would like to use your iPhone 3.0 with your bluetooth capable Ubuntu 9.04 PC then uit.sh (Ubuntu Iphone Thethering) is for you. This script installs all required conf, allows you to enable and disable your iphone tethering and even uninstall the conf if you no longer need it. I do expect NetworkManager to eventually support this out of the box.

Thanks to [http://xn--9bi.net/2009/06/17/tethering-iphone-3-0-to-ubuntu-9-04/](http://xn--9bi.net/2009/06/17/tethering-iphone-3-0-to-ubuntu-9-04/) blog post which assisted me in knowning what configuration was needed.

**Usage:**
-- Ubuntu iPhone Tethering (uit) Version 0.1 - Cooper Lees <me@cooperlees.com> --
Usage: ./uit.sh options
- This script will install, uninstall, enable and disable iPhone tethering with iPhone 3.0 Software.
- It has been tested on a upto date (patched) box as of 20090623.
- !! Be careful, this script will ask for your password to get root privledges to your system!

OPTIONS:
    -h    Show this message
    -i    Install required configuration
    -u    Uninstall required configuration
    -c    Connect Tethering
    -d    Disconnect Tethering
    -m []    Set iPhone's MAC Address (to /home/USERNAME/.uitrc)
    -v    Verbose

**Install Guide:**
Avaliable from: [http://us.cooperlees.com/download.php?F=uit.sh.gz](http://us.cooperlees.com/download.php?F=uit.sh.gz)

- Inital installation requires an active Internet Connection to get required dependancies through apt-get. Current dependancies = 'bluez-compat'
- Only the install requires you to sudo the script, other areas apropriately sudo where required.

*Install Process:*

[LIST=1]
[*]Open terminal
[*]wget [http://us.cooperlees.com/download.php?F=uit.sh.gz](http://us.cooperlees.com/download.php?F=uit.sh.gz)
[*]gunzip uit.sh.gz
[*]chmod 755 uit.sh
[*][OPTIONAL] Move the script into your sbin - 'sudo mv uit.sh /usr/sbin' (This will allow it to be in your PATH)
[*]Run 'sudo uit.sh -i' (You will need to have your iphone in discoverable mode with [COLOR=Blue]Bluetooth[/COLOR] on)
[*]You will be notified if it all sucessfully installs.
[/LIST]
*Connect Process:*
- Ensure Bluetooth is on and paired with your system (use the GNOME Bluetooth tool to pair). Also make sure Internet Tethering is on.

[LIST=1]
[*]uit.sh -c
[/LIST]
- Once connected you will see the iPhone come up with a blue bar stating 'Internet Tethering' is activated.

*Disconnect Process:*
One command will disconnect from the iphone tethering - You should see the blue notification text dissapear.

[LIST=1]
[*]uit.sh -d
[/LIST]
*Uninstall Process:*

[LIST=1]
[*]uit.sh -u
[/LIST]
- This will remove conf from files and also make backup of files modified.

Hope you enjoy it as much as I am. Finding the bluetooth a little slow. But still very handy and good. Thanks Apple.

---

### Post by Mr. Frog on 2009-06-26
I wasn't able to make that working with my bluetooth interface.
For those that might need help, see this thread:

[http://ubuntuforums.org/showthread.php?p=7363690](http://ubuntuforums.org/showthread.php?p=7363690)

---

### Post by imatt.au on 2009-06-30
To stop Network Manager interfering with the connection I added "sudo /etc/init.d/NetworkManager stop" to your connect function and "sudo /etc/init.d/NetworkManager start" to the disconnect function to bring it back up when you're finished. 

Other then that a great little script. 

Thanks.

---

### Post by dannyboy79 on 2009-07-01
i am using hardy heron and bluez-compat isn't in the ppa repository. All I have is whats in the picture:
[[IMG]http://img139.imageshack.us/img139/3734/screenshot1q.th.png[/IMG]](http://img139.imageshack.us/i/screenshot1q.png/)
can I still get this working somehow with the packages that are available to mE? I did try to connect to my 2G 3.0 iPhone and this is the message I get:

[[IMG]http://img356.imageshack.us/img356/6776/screenshot2.th.png[/IMG]](http://img356.imageshack.us/i/screenshot2.png/)
any help please?

---

### Post by imatt.au on 2009-07-02
Have you tried running the script yet? Or just tried pairing through gnome?

---

### Post by dannyboy79 on 2009-07-02
i haven't tried running the script because Hardy Heron does not have the required dependencies being bluez-compat. I suppose I can give it a shot anyway and see what happens. I did end up getting Blueman GUI working but the problem is that I don't have a wireless adapter on my Ubuntu Desktop. I was hoping to be able to use the iphone as a dialup modem and I didn't realize I needed a wireless adapter on the Ubuntu machine in order to do this.

---

### Post by imatt.au on 2009-07-02
This script allows you to use the Bluetooth tethering feature of your iphone; using the internet allowance provide from your telco. The Bluez-compat package is for the newer versions of Ubuntu because I think  they change the bluetooth stack a bit. By the looks of it you have the original bluez packages already installed. Just run the script as per the instructions and you should be right.

---

### Post by steveneddy on 2009-07-02
> **dannyboy79 said:**
>  I was hoping to be able to use the iphone as a dialup modem and I didn't realize I needed a wireless adapter on the Ubuntu machine in order to do this.

Not a wireless adapter but a Bluetooth adapter.

Maybe if your machine doesn't have Bluetooth, go out and purchase a USB Bluetooth adapter for this to work for you.

---

### Post by cooperlees on 2009-07-05
Hey all ..

Glad to hear people are liking the script. Due to the feedback I have made a few changes:

Added
sudo /etc/init.d/NetworkManager stop
to the connect function 

and

Added 
sudo /etc/init.d/NetworkManager start
to the disconnect function

Enjoy ...

---

### Post by dannyboy79 on 2009-07-06
i can't get this to work because I have a 8gb 2G iphone running OS 3.0. When I install the AT&T USA mobileconfig I never get the tethering option within network settings. Guess MMS and tethering will never make it to teh 2G iphone.

---

### Post by digitalb0y on 2009-07-06
I could not download
[http://us.cooperlees.com/download.php?F=uit.sh.gz](http://us.cooperlees.com/download.php?F=uit.sh.gz)
*Firefox can't establish a connection to the server at us.cooperlees.com.*

Although I can access your website [http://cooperlees.com/blog/](http://cooperlees.com/blog/)

if it's just a shell script files can you please post it.

Thanks.

---

### Post by robllewellyn on 2009-07-06
Is the script not available any longer guys?

Edited. Yes it is! Worked for me, thank you.

I am not well versed in Linux. I was wondering if it is possible to create an icon on my desktop to run the connect and disconnect script without opening terminal.

Can anyone help me?

---

### Post by dannyboy79 on 2009-07-07
this doesn't appear to work for the 2G Edge iphones. I've tried everything from adding the USA AT&T mobileconfigs to everything else I have found on the internet and nothing will allow it to work. I can't get MMS to work on the 2G either.

---

### Post by cooperlees on 2009-07-07
I would dare say that is because AT&T don't allow teathering ... I am sure it's support on the old EDGE phones? 
 
Can anyone confirm here?

---

### Post by griffin30007 on 2009-07-13
hey guys.  Having some major issues getting this script to go.  Heres what I get:

[INDENT]gg@gg-laptop:~$ sudo uit.sh -c
 * Stopping network connection manager NetworkManager                    [ OK ] 
pand[7959]: Bluetooth PAN daemon version 4.39
pand[7959]: Connecting to 00:21:e9:81:5d:97
pand[7959]: Connect to 00:21:e9:81:5d:97 failed. Connection refused(111)
/etc/network/interfaces:5: duplicate interface
ifup: couldn't read interfaces file "/etc/network/interfaces"
!-> ERROR: Unable to bring up the interface bnep0 ...[/INDENT]

Heres my /etc/network/interfaces file:
[INDENT]
auto lo
iface lo inet loopback

iface bnep0 inet dhcp
iface bnep0 inet dhcp[/INDENT]

the interfaces file doesn't look quite right.  Going to try reinstalling Ubuntu 9.04 tonight.  If I can get this to work I'll have everything I need to fully switch my laptop to Ubuntu.  Running Ubuntu 9.04 through wubi atm.
Thanks

---

### Post by Willberto on 2009-07-14
I'm getting the following error and cannot seem to get it to connect

* Stopping network connection manager NetworkManager                    [ OK ] 
pand[7316]: Bluetooth PAN daemon version 4.39
pand[7316]: Connecting to 00:....
pand[7316]: Connect to 00:....x failed. Connection refused(111)

I have tried adding sleep 1 to /etc/init.d/bluetooth and restarting as described in the following link to no effect:  [https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/121915](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/121915)

---

### Post by nasha on 2009-07-18
Hi Guys,
Im also getting the connection refused error. Can anyone shed some light on this situation? Would be greatly appreciated :)

Regards,
Nasha
```

nasha@eeeBuntu:~$ uit.sh -c
 * Stopping network connection manager NetworkManager                    [ OK ] 
pand[4561]: Bluetooth PAN daemon version 4.39
pand[4561]: Connecting to 00:24:36:0B:A5:17
pand[4561]: Connect to 00:24:36:0B:A5:17 failed. Connection refused(111)
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
bnep0: ERROR while getting interface flags: No such device
bnep0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up bnep0.

```

---

### Post by Cbcom0 on 2009-07-26
> **nasha said:**
> Hi Guys,
Im also getting the connection refused error. Can anyone shed some light on this situation? Would be greatly appreciated :)

Regards,
Nasha
```

nasha@eeeBuntu:~$ uit.sh -c
 * Stopping network connection manager NetworkManager                    [ OK ] 
pand[4561]: Bluetooth PAN daemon version 4.39
pand[4561]: Connecting to 00:24:36:0B:A5:17
pand[4561]: Connect to 00:24:36:0B:A5:17 failed. Connection refused(111)
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
bnep0: ERROR while getting interface flags: No such device
bnep0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up bnep0.

```

I am also getting this error, could somebody please post a solution to this problem, as I have no clue of how to resolve the problem. 

Thanks

---

### Post by nasha on 2009-07-26
I have since solved the connection refused issue. It turns out your iPhone and Ubuntu need to be paired each time prior to attempting to connect. This means deleting the saved entries on BOTH your iPhone and Ubuntu box, and re pairing using bluetooth-applet, then connecting from the iPhone via bluetooth.

Once this is done you can connect to your device simply by:
```
sudo pand -c xx:xx:xx:xx:xx:xx -n
```
where xx is your iPhone BT MAC address.
Or simply stick with uit.sh. I myself don't use it anymore, but theres no reason it shouldnt work after that

Best of luck,
Nasha

---

### Post by dbqpdb on 2009-07-31
Hi There,
I'm so incredibly close to making this work.  Maybe somebody could give me some advice.  I'm running Ubuntu intrepid on a Thinkpad T60, have a iPhone 3G running os 3.0 .  I have internet tethering enable on the iPhone, and can successfully pair my machine to the phone.  The script given then runs fine, and the iPhone then goes into tethering mode with hte blue bar on top and everything.  But my machine still can't seem to contact the outside world.  I think I can ping my iPhone, but I'm guessing I'm not making it past there for some reason.  Here's the output of the script:

* Stopping NetworkManager...                                            
[ OK ] 
pand[7385]: Bluetooth PAN daemon version 4.12
pand[7385]: Connecting to 00:25:00:78:A9:97
pand[7385]: bnep0 connected
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/bnep0/00:19:7d:ec:0a:c4
Sending on   LPF/bnep0/00:19:7d:ec:0a:c4
Sending on   Socket/fallback
DHCPDISCOVER on bnep0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on bnep0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.20.2 from 192.168.20.1
DHCPREQUEST of 192.168.20.2 on bnep0 to 255.255.255.255 port 67
DHCPACK of 192.168.20.2 from 192.168.20.1
bound to 192.168.20.2 -- renewal in 1492 seconds

And here is the output of netstat -rn

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt 
Iface
192.168.20.0    0.0.0.0         255.255.255.0   U         0 0      0  bnep0
172.16.220.0    0.0.0.0         255.255.255.0   U         0 0      0  vmnet1
172.16.207.0    0.0.0.0         255.255.255.0   U         0 0      0  vmnet8
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0        0  bnep0
0.0.0.0         192.168.20.1    0.0.0.0         UG        0 0         0  bnep0

Anybody have any ideas?  Could you use any more information?  Any help at all would be appreciated.

---

### Post by CyberCr33p_ on 2009-09-03
I have the same problem as @dbqpdb.

---

### Post by dave_blob on 2009-09-11
If anyone else is getting this error:
```

pand[5575]: Connect to 00:FF:AA:AA:AA:A failed. Connection refused(111)
```

Try the following:

[LIST=1]
[*]Right click on your bluetooth-manager and choose properties, and delete the pairing with your iphone.
[*]Go into the bluetooth settings in your iphone and delete the pairing with your PC(click the arrow then 'forget about this')
[*]restart your iphone (hold the menu button and power for 3 sec)
[*]Re-pair your PC with your phone using gnome bluetooth icon
[*]Re-pair your iphone with you pc using the iphone bluetooth screen
[/LIST]

Thats all I had to do to resolve the 'Connection refused' with my iphone 3gs - i believe it was the restart that did it!

---

### Post by bluepowder7 on 2009-09-12
does this also work for 8.04 LTS or is there a different script i should use?  i've got the iPhone 3GS with firmware 3.0.1 (7A400)

---

### Post by nasha on 2009-09-12
Instructions should work under 8.04 provided you have a blueooth adapter of course.
Dave blobs instructions are perfect

---

### Post by UCAP on 2009-09-19
I only get "pand [...] permission denied(13)" error messages. Could it have anything to do with the new iPhone firmware 3.1?

---

### Post by d0b33 on 2009-09-25
Thanks for this :)

Took a few install and uninstalls to get this working but as they say 3rd time lucky ;) 3rd time the process went smoothly.

Thanks again ;)

---

### Post by Saidear on 2009-10-13
> **dave_blob said:**
> If anyone else is getting this error:
```

pand[5575]: Connect to 00:FF:AA:AA:AA:A failed. Connection refused(111)
```Try the following:

[LIST=1]
[*]Right click on your bluetooth-manager and choose properties, and delete the pairing with your iphone.
[*]Go into the bluetooth settings in your iphone and delete the pairing with your PC(click the arrow then 'forget about this')
[*]restart your iphone (hold the menu button and power for 3 sec)
[*]Re-pair your PC with your phone using gnome bluetooth icon
[*]Re-pair your iphone with you pc using the iphone bluetooth screen
[/LIST]

Thats all I had to do to resolve the 'Connection refused' with my iphone 3gs - i believe it was the restart that did it!

I tried this, and still received the same error as before: ```
 * Stopping network connection manager NetworkManager                                           [ OK ] 
pand[5149]: Bluetooth PAN daemon version 4.39
pand[5149]: Connecting to 00:26:08:7D:6A:B4
pand[5149]: Connect to 00:26:08:7D:6A:B4 failed. Connection refused(111)
/etc/network/interfaces:4: duplicate interface
ifup: couldn't read interfaces file "/etc/network/interfaces"
!-> ERROR: Unable to bring up the interface bnep0 ...

```

If I remove the duplicate entry on bnep0, I get:

```
 * Stopping network connection manager NetworkManager                                           [ OK ] 
pand[5345]: Bluetooth PAN daemon version 4.39
pand[5345]: Connecting to 00:26:08:7D:6A:B4
pand[5345]: Connect to 00:26:08:7D:6A:B4 failed. Connection refused(111)
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
bnep0: ERROR while getting interface flags: No such device
bnep0: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up bnep0.
```

This is running a jailbroken iPhone 3GS running 3.0 firmware.

---

### Post by drdom on 2009-10-15
> **dave_blob said:**
> If anyone else is getting this error:
```

pand[5575]: Connect to 00:FF:AA:AA:AA:A failed. Connection refused(111)
```

Try the following:

[LIST=1]
[*]Right click on your bluetooth-manager and choose properties, and delete the pairing with your iphone.
[*]Go into the bluetooth settings in your iphone and delete the pairing with your PC(click the arrow then 'forget about this')
[*]restart your iphone (hold the menu button and power for 3 sec)
[*]Re-pair your PC with your phone using gnome bluetooth icon
[*]Re-pair your iphone with you pc using the iphone bluetooth screen
[/LIST]

Thats all I had to do to resolve the 'Connection refused' with my iphone 3gs - i believe it was the restart that did it!

This procedure solved the problem for me with Ubuntu 9.04 and iPhone 3GS fw 3.1.

Thanks all!

---

### Post by Mevos on 2009-11-09
I get the following error message when trying to connect using the script:

```

pand[8234]: Bluetooth PAN daemon version 4.57
pand[8234]: Connecting to 00:xx:xx:xx:xx:xx
pand[8234]: bnep0 connected
/etc/network/interfaces:5: duplicate interface
ifup: couldn't read interfaces file "/etc/network/interfaces"
!-> ERROR: Unable to bring up the interface bnep0 ...

```

When i look at the line "Unable to bring up the interface bnep0", it reminds me that I'm using a Bluetooth dongle so that might be the reason why. It looks like that would be only a part of the problem thought.

Edit: 

I found why that message comes up. If my iphone is not paired, it refuses to pair to my laptop but if i pair from the iphone b4 running the script, it still says the same error but since im already paired, the iphone starts saying its tethering the internet.

But... its not doing it...

Anyone know how to fix this? I'm using ubuntu 9.10

---

### Post by Mevos on 2009-11-09
Ahh i found out why it wasn't working...

There was a duplicate entry of the line "iface bnep0 inet dhcp" in the file "/etc/network/interfaces".

---

### Post by sorbic on 2009-12-12
> **dbqpdb said:**
> Hi There,
I'm so incredibly close to making this work.  Maybe somebody could give me some advice.  I'm running Ubuntu intrepid on a Thinkpad T60, have a iPhone 3G running os 3.0 .  I have internet tethering enable on the iPhone, and can successfully pair my machine to the phone.  The script given then runs fine, and the iPhone then goes into tethering mode with hte blue bar on top and everything.  But my machine still can't seem to contact the outside world.  I think I can ping my iPhone, but I'm guessing I'm not making it past there for some reason.  Here's the output of the script:

* Stopping NetworkManager...                                            
[ OK ] 
pand[7385]: Bluetooth PAN daemon version 4.12
pand[7385]: Connecting to 00:25:00:78:A9:97
pand[7385]: bnep0 connected
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/bnep0/00:19:7d:ec:0a:c4
Sending on   LPF/bnep0/00:19:7d:ec:0a:c4
Sending on   Socket/fallback
DHCPDISCOVER on bnep0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on bnep0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.20.2 from 192.168.20.1
DHCPREQUEST of 192.168.20.2 on bnep0 to 255.255.255.255 port 67
DHCPACK of 192.168.20.2 from 192.168.20.1
bound to 192.168.20.2 -- renewal in 1492 seconds

And here is the output of netstat -rn

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt 
Iface
192.168.20.0    0.0.0.0         255.255.255.0   U         0 0      0  bnep0
172.16.220.0    0.0.0.0         255.255.255.0   U         0 0      0  vmnet1
172.16.207.0    0.0.0.0         255.255.255.0   U         0 0      0  vmnet8
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0        0  bnep0
0.0.0.0         192.168.20.1    0.0.0.0         UG        0 0         0  bnep0

Anybody have any ideas?  Could you use any more information?  Any help at all would be appreciated.
I had the same problem... managed to get it working by going into firefox:
edit->preferences->advanced->network->"configure how firefox connects to the internet"
then go "Auto-detect proxy settings for this network"... should work :)

---

### Post by kevpatts on 2010-05-11
Before I try this, has anyone tried it with Lucid?

---

### Post by lxiaob on 2010-08-19
Can anybody here post the uit.sh.gz again? The download link is not available right now.

---

### Post by kevpatts on 2010-08-20
just do this: [http://www.ubuntugeek.com/iphone-tethering-on-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/iphone-tethering-on-ubuntu-9-10-karmic.html)

It works perfectly.

---

