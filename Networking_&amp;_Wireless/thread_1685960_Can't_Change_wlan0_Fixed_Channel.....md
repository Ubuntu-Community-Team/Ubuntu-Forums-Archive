---
title: "Can't Change wlan0 Fixed Channel...."
date: 2011-02-11
forum: Networking &amp; Wireless
---

### Post by Strageser on 2011-02-11
Hi guys,
I'm pretty new to linux but have done my best  to research this before posting.  My issue is that I am attempting to use aircrack-ng but am not getting very far because my interface (wlan0) is fixed on channel 6 when I need it on channel 11.

I tried inputting this command:

 ```
sudo iwconfig wlan0 channel 11
```
but everytime I input 

```
sudo aireplay-ng -3 -b XX:XX:XX:XX:XX:XX -h XX:XX:XX:XX:XX:XX wlan0
```i get this

```
12:03:11  Waiting for beacon frame (BSSID: XX:XX:XX:XX:XX:XX) on channel 6
12:03:11  wlan0 is on channel 6, but the AP uses channel 11
```
How can I get past this?  Any help is greatly appreciated!

---

### Post by nm_geo on 2011-02-11
No aircrack expert for sure but what determines the channel your wlan uses?  Might check your wireless access point.

---

### Post by freshmeat20 on 2011-02-11
try disconnecting from your AP first.

---

### Post by nm_geo on 2011-02-12
Interesting question..

Code

```
sudo iwlist scanning
```

You need to change the channel on your wireless access point 
Mine would be 192.168.1.1  on my wireless router and mine is operating on channel 6 too.
I accessed it through Firefox browser and changed my operating channel to 11
restarted to reconnect.
Generally you would use the channel selection to have less interference with other close residential 
wirelesses operating on the same channel

Any way you might try that .. Let us know.

---

### Post by madshaks on 2011-02-27
I had the same problem, you need to patch your drivers. the instructions as well as the links to the files are located here
[http://blog.rootshell.be/2010/08/09/backtrack4-r1-awus036nh-win/](http://blog.rootshell.be/2010/08/09/backtrack4-r1-awus036nh-win/)
hope it helps

---

### Post by underTheBridge on 2011-03-12
I had I similar problem as this.
Then I learned how to use iwconfig properly.
If you learn that then you won't need airmon-ng

Basically, for aireplay-ng to work it must be on the right channel and in monitor mode (airmon-ng is supposed to do this for you)
Unfortunately for me airmon-ng didn't work properly)
So instead i have to do this. (note that it doesn't require creating a new device)
(run as root)
```

ifconfig $IFACE down
iwconfig $IFACE mode managed
ifconfig $IFACE up
iwconfig $IFACE channel $@
ifconfig $IFACE down
iwconfig $IFACE mode monitor
ifconfig $IFACE up

```

where $IFACE would be your inferface (wlan0)
and $@ is the channel number.

run ifconfig wlan0 to check that the channel has been changed correctly
Output should look like this:

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  Mode:Monitor  Frequency:2.412 GHz  Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

Note how it is in both monitor mode and the frequency is set.
I will include the commands above as a script (since this is how i use it)
The script has in it a list of the frequencies and channels.

If you try to change the channel while in monitor mode then it will not work (not sure why)
You need to change it to managed mode first. Often it will already be in managed mode but that doesn't matter.
Also note that you cannot change the device mode when it is up (hence the ifconfig wlan0 down)
And you cannot change the channel when it is down.

Here is my script:

```

#!/bin/bash
# this script is to change the channel of the wireless card to the one specified, then puts it in monitor mode.
# make sure you uncheck enable wireless in nm-applet before continuing (this script will have no effect otherwise)
# note that if you are using airmon-ng you may want to manually remove all of the monitor devices it has created. (you don't need them)
# to do this run "airmon-ng stop mon0" and if you had more then run "airmon-ng stop mon1" etc.

# this script has undefined consequences if the commands fail (no error checking)
# it would be good idea to run each of the commands listed here separately to make sure they all work before making use of this script
# note that this is just sequence of commands which I would normally run manually on my system, they may not work on yours.
# also you need to run the script as root

#change this to the interface you wish to change
IFACE="wlan0"

ifconfig $IFACE down
iwconfig $IFACE mode managed
ifconfig $IFACE up
iwconfig $IFACE channel $@
ifconfig $IFACE down
iwconfig $IFACE mode monitor
ifconfig $IFACE up

# this will be displayed on you terminal:
iwconfig $IFACE
# if the frequency hasn't changed then the script didn't work

#here is a list of channels and frequencies so that you know if your channel is set right:
#1    2.412
#2    2.417
#3    2.422
#4    2.427
#5    2.432
#6    2.437
#7    2.442
#8    2.447
#9    2.452
#10    2.457
#11    2.462
# frequencies are in GHz
# there are 13 channels in Europe apparently, I assume that they would be:
#12    2.467
#13    2.472
# but I am reading this off an American table, so i'm not sure
# here it is:
# http://www.cisco.com/en/US/docs/wireless/technology/channel/deployment/guide/Channel.html#wp134132

```

Hope that all made sense to somebody.

---

### Post by underTheBridge on 2011-03-12
Oh yeah, i forgot. If you don't have the frequency set at all then aireplay-ng thinks it is channel -1
Output of iwconfig will look like this:

```

wlan0        IEEE 802.11abg  Mode:Monitor  Tx-Power=15 dBm   
                 Retry  long limit:7   RTS thr:off   Fragment thr:off
                 Power Management:off

```

Note the lack of the Frequency property.

This happens to me if i use airmon-ng to set it up.

---

### Post by kidsodateless on 2011-03-12
> **Strageser said:**
> 

 ```
sudo iwconfig wlan0 channel 11
```
but everytime I input 

```
sudo aireplay-ng -3 -b XX:XX:XX:XX:XX:XX -h XX:XX:XX:XX:XX:XX wlan0
```i get this

```
12:03:11  Waiting for beacon frame (BSSID: XX:XX:XX:XX:XX:XX) on channel 6
12:03:11  wlan0 is on channel 6, but the AP uses channel 11
```
How can I get past this?  Any help is greatly appreciated!


try to connect first on the ESSID that you wanted to crack.
:D

i'm trying also with dictionary attack for educational purpose only :D

---

### Post by jacortijo on 2011-03-24
madshaks could you please tell me a bit how did you do it in a ubuntu 10.10?
i tried but the directory for the patch doesnt exists...
cd /usr/src/drivers/compat-wireless-2010-07-10/net/wireless

any package to install before the patch?

thanks  a lot
jose

---

### Post by VoyezScout on 2011-12-23
> **underTheBridge said:**
> I had I similar problem as this.
Then I learned how to use iwconfig properly.
If you learn that then you won't need airmon-ng

Basically, for aireplay-ng to work it must be on the right channel and in monitor mode (airmon-ng is supposed to do this for you)
Unfortunately for me airmon-ng didn't work properly)
So instead i have to do this. (note that it doesn't require creating a new device)
(run as root)
```

ifconfig $IFACE down
iwconfig $IFACE mode managed
ifconfig $IFACE up
iwconfig $IFACE channel $@
ifconfig $IFACE down
iwconfig $IFACE mode monitor
ifconfig $IFACE up

```

where $IFACE would be your inferface (wlan0)
and $@ is the channel number.

run ifconfig wlan0 to check that the channel has been changed correctly
Output should look like this:

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  Mode:Monitor  Frequency:2.412 GHz  Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

Note how it is in both monitor mode and the frequency is set.
I will include the commands above as a script (since this is how i use it)
The script has in it a list of the frequencies and channels.

If you try to change the channel while in monitor mode then it will not work (not sure why)
You need to change it to managed mode first. Often it will already be in managed mode but that doesn't matter.
Also note that you cannot change the device mode when it is up (hence the ifconfig wlan0 down)
And you cannot change the channel when it is down.

Here is my script:

```

#!/bin/bash
# this script is to change the channel of the wireless card to the one specified, then puts it in monitor mode.
# make sure you uncheck enable wireless in nm-applet before continuing (this script will have no effect otherwise)
# note that if you are using airmon-ng you may want to manually remove all of the monitor devices it has created. (you don't need them)
# to do this run "airmon-ng stop mon0" and if you had more then run "airmon-ng stop mon1" etc.

# this script has undefined consequences if the commands fail (no error checking)
# it would be good idea to run each of the commands listed here separately to make sure they all work before making use of this script
# note that this is just sequence of commands which I would normally run manually on my system, they may not work on yours.
# also you need to run the script as root

#change this to the interface you wish to change
IFACE="wlan0"

ifconfig $IFACE down
iwconfig $IFACE mode managed
ifconfig $IFACE up
iwconfig $IFACE channel $@
ifconfig $IFACE down
iwconfig $IFACE mode monitor
ifconfig $IFACE up

# this will be displayed on you terminal:
iwconfig $IFACE
# if the frequency hasn't changed then the script didn't work

#here is a list of channels and frequencies so that you know if your channel is set right:
#1    2.412
#2    2.417
#3    2.422
#4    2.427
#5    2.432
#6    2.437
#7    2.442
#8    2.447
#9    2.452
#10    2.457
#11    2.462
# frequencies are in GHz
# there are 13 channels in Europe apparently, I assume that they would be:
#12    2.467
#13    2.472
# but I am reading this off an American table, so i'm not sure
# here it is:
# http://www.cisco.com/en/US/docs/wireless/technology/channel/deployment/guide/Channel.html#wp134132

```

Hope that all made sense to somebody.


I know that it's a bit late for this but...f%&$ing Thanks!!!!

I don't know how many times I installed that damned path over the compat-wireless package which gets overriden every time the kernel is ugraded.

Thanks man! :D

---

