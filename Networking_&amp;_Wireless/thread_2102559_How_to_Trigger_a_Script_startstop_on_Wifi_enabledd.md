---
title: "How to Trigger a Script start/stop on Wifi enabled/disabled."
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by FerroPower on 2013-01-07
I run hostapd wireless AP but I want to AUTORUN  the Hostapd   script whenever the Wireless is Enabled and stop it whenever the  Wireless is disabled. 

All I want is start the script whenever wifi is switch on and stop the script whenever wifi is off.  

I am currenty using that script at startup but want to put that in autorun mode so that it runs whenever wifi is switched on. 

I tried many different methods using upstart but no event gets triggered when a Wireless is enabled or disabled. 

Can someone please help.  

Thanks.

---

### Post by FerroPower on 2013-01-10
since nobody is bothered to reply request to MODs pls atleast close this thread. 

Thanks. ):P

---

### Post by steeldriver on 2013-01-10
how are you managing the wifi connection? if it's via network-manager then probably the right way to do it is via DBUS

---

### Post by BlinkinCat on 2013-01-10
Hi,

If you wish for the Mods to close your thread, you can ask them to do so by using the "Report abuse" button.

All the best - :)

---

### Post by Cheesehead on 2013-01-10
> **FerroPower said:**
> I run hostapd wireless AP but I want to AUTORUN  the Hostapd script whenever the Wireless is Enabled and stop it whenever the  Wireless is disabled. 

All I want is start the script whenever wifi is switch on and stop the script whenever wifi is off.


Any network interface up/down, including wireless, get signalled in three places:
- An Upstart signal is emitted by ifup
- A Dbus signal is emitted by Network Manager
- Scripts located in /etc/network/if-up.d/ and /etc/network/if-down.d/ are run.

All are effective triggers for an application.

---

### Post by FerroPower on 2013-01-10
> **steeldriver said:**
> how are you managing the wifi connection? if it's via network-manager then probably the right way to do it is via DBUS


Sorry I don't know how to use DBUS for managing scripts which should trigger on Interface enabled/disabled.



Yes I am managing wifi connection via Network-Manager, I can run run the script manually and start the Access Point but I also tried using the Upstart method & also putting the script inside /etc/network/if-up.d/ but for some reason It doesn't execute whenever the wifi is enabled. However the script gets executed when I unplug and plug my WIRED connection. I want the script to on enabling of WIFI via Network-manager. 
Nothing gets triggered off when a WIFI is disabled or Enabled. 

Thanks atleast for some reply.

---

### Post by FerroPower on 2013-01-10
> **Cheesehead said:**
> Any network interface up/down, including wireless, get signalled in three places:
- An Upstart signal is emitted by ifup
- A Dbus signal is emitted by Network Manager
- Scripts located in /etc/network/if-up.d/ and /etc/network/if-down.d/ are run.

All are effective triggers for an application.


Maybe my system is broken or something because my scripts inside /etc/network/if-up.d never run when wireless is enabled. how should I check if somethings wrong. ?

---

### Post by Hadaka on 2013-01-10
Hi, im not sure if this will do you any good for what you are doing,
i use it for a different purpose than what you do....but here is the meat of it.

a cron job is set to run every 3 minutes to run this script.

#!/bin/bash

ifconfig | grep -i broadcast > wlan_status


case `grep -i running wlan_status | awk '{print $3}'` in
  RUNNING) echo 'YOUR-PASSWORD' | sudo #RUN A SCRIPT COMMANDS;;  
  $NULL) echo 'YOUR-PASSWORD' | sudo #DON'T RUN A SCRIPT COMMANDS ;;
 esac

---

### Post by FerroPower on 2013-01-11
> **Cheesehead said:**
> Any network interface up/down, including wireless, get signalled in three places:
- An Upstart signal is emitted by ifup
- A Dbus signal is emitted by Network Manager
- Scripts located in /etc/network/if-up.d/ and /etc/network/if-down.d/ are run.

All are effective triggers for an application.

> **Hadaka said:**
> Hi, im not sure if this will do you any good for what you are doing,
i use it for a different purpose than what you do....but here is the meat of it.

a cron job is set to run every 3 minutes to run this script.

#!/bin/bash

ifconfig | grep -i broadcast > wlan_status


case `grep -i running wlan_status | awk '{print $3}'` in
  RUNNING) echo 'YOUR-PASSWORD' | sudo #RUN A SCRIPT COMMANDS;;  
  $NULL) echo 'YOUR-PASSWORD' | sudo #DON'T RUN A SCRIPT COMMANDS ;;
 esac


Sorry couldn't understand anything of your script ...


if I run[COLOR=Blue]  ifconfig | grep -i broadcast[/COLOR]  when WIFI is enabled I get the following :-        
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

But when I Disable the WIFI and run the command [COLOR=Blue]ifconfig | grep -i broadcast [COLOR=Black]I get the following :--[/COLOR]
         
         [/COLOR]UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
[COLOR=Blue]
[/COLOR]
Is something wrong here ?? ,...

---

### Post by Hadaka on 2013-01-11
Hi, no that is correct.
you are getting the running from the lo
not the wlan

---

### Post by Hadaka on 2013-01-11
hi, here is a simple version..run the complete script
and you will see that it works.

#!/bin/bash

ifconfig | grep -i broadcast > wlan_status


case `grep -i running wlan_status | awk '{print $3}'` in
  RUNNING) echo "wifi is running" ;;  
  $NULL) echo "wifi is down" ;;
 esac

#chmod +x FILENAME

#* Note you are grepping "RUNNING" from the wlan_status file NOT from ifconfig output
#* wlan_status file is created by grepping on "BROADCAST" (wlanX info) from ifconfig output

that help clear any confusion ??

---

### Post by FerroPower on 2013-01-11
> **Hadaka said:**
> hi, here is a simple version..run the complete script
and you will see that it works.

#!/bin/bash

ifconfig | grep -i broadcast > wlan_status


case `grep -i running wlan_status | awk '{print $3}'` in
  RUNNING) echo "wifi is running" ;;  
  $NULL) echo "wifi is down" ;;
 esac

#chmod +x FILENAME

#* Note you are grepping "RUNNING" from the wlan_status file NOT from ifconfig output
#* wlan_status file is created by grepping on "BROADCAST" (wlanX info) from ifconfig output

that help clear any confusion ??


Sorry to bother you again but I still get wifi is running no matter whether is enabled or disabled via Network-manager. 

By the way do I need to put your script somewhere in any directory or just run it.

---

### Post by steeldriver on 2013-01-11
I've been taking some baby steps with DBUS - here are a couple of commands you can have a play with if you would like to go down that route

```
dbus-monitor --system "type='signal',sender='org.freedesktop.NetworkManager', \
interface='org.freedesktop.NetworkManager.Device.Wireless', \
member='PropertiesChanged'"

dbus-monitor --system "type='signal',sender='org.freedesktop.NetworkManager', \
interface='org.freedesktop.NetworkManager.Connection.Active', \
member='PropertiesChanged'"
```Unfortunately the documentation seems to be next to nonexistant (plenty of API specs - no actual usage examples!). I'm not sure I'd recommend using dbus-monitor for real, it's interesting to play with but there's a python wrapper that looks more friendly for real-world applications

---

### Post by Hadaka on 2013-01-11
Hi, copy and paste the coded commands
this is exactly what the script does

```
ifconfig | grep -i broadcast > ferro.txt
grep -i running ferro.txt
cat ferro.txt 
```

         OUTPUT WHEN WIFI ENABLED
UP BROADCAST MULTICAST  MTU:1500  Metric:1
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1         "RUNNING"


```
ifconfig | grep -i broadcast > ferro.txt
grep -i running ferro.txt
cat ferro.txt 
```

    OUTPUT WHEN WIFI DISABLED 
UP BROADCAST MULTICAST  MTU:1500  Metric:1                       "NOT RUNNING"

copy the script i posted to you in your editor, give it a file name
save and close.
then in terminal
```
chmod +x FIENAME
```
to run
```
./FILENAME 
```
the script works...ive tested it several different ways.
if you are still confused..let me know.
thanks

---

### Post by FerroPower on 2013-01-11
> **Hadaka said:**
> Hi, copy and paste the coded commands
this is exactly what the script does

```
ifconfig | grep -i broadcast > ferro.txt
grep -i running ferro.txt
cat ferro.txt 
```         OUTPUT WHEN WIFI ENABLED
UP BROADCAST MULTICAST  MTU:1500  Metric:1
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1         "RUNNING"


```
ifconfig | grep -i broadcast > ferro.txt
grep -i running ferro.txt
cat ferro.txt 
```    OUTPUT WHEN WIFI DISABLED 
UP BROADCAST MULTICAST  MTU:1500  Metric:1                       "NOT RUNNING"

copy the script i posted to you in your editor, give it a file name
save and close.
then in terminal
```
chmod +x FIENAME
```to run
```
./FILENAME 
```the script works...ive tested it several different ways.
if you are still confused..let me know.
thanks


I did as you told I get the following results
_**[COLOR=Lime]WIFI Enabled[/COLOR]**_
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          UP BROADCAST MULTICAST  MTU:1500  Metric:1


_[COLOR=Red]WIFI Disabled[/COLOR]_
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1


I dont know what problem is there my output is different from yours.

Is there something wrong in my wifi driver installation or something. I am using b43 wlan driver working absolutely fine. running a custom made script using hostapd for enabling virtual wifi access point similar to Connectify in windows. 
everything works but I had to either start script manually or put it in rc.local so that the scripts loads when the PC boots, 
My problem is I only wanted to automate the process of starting the script whenever the WIFI is enabled in the machine so that a NON-ROOT user also automatically starts the script when he/she Enables WIFI.

I hope I am not sounding too much demanding ... I am still new to linux ways.... 

Thanks for helping me.

---

### Post by Hadaka on 2013-01-11
Hi, i dont think the b43 makes any difference, as that is the driver i am running.

try this, with the wifi enabled post the output of...
```
ifconfig 
```then with the wifi disabled copy the output to a file or text editor
the results of...
```
ifconfig
```there should be a huge difference between the two, please post both
thanks.

afterthought,,, with wifi enabled  ....    ifconfig > config_test
                     then with wifi disabled...     ifconfig >> config_test
and then just post the file      config_test

---

### Post by Hadaka on 2013-01-11
Hi, this should work now, the difference
between my ifconfig and yours is the bridging you have set up
for Hostapd. So here ya go. ....

```
#!/bin/bash

ifconfig | grep -i broadcast > wlan_status
case `grep -i multicast wlan_status | awk '{print $3}'` in
  MULTICAST) echo "wifi is running" ;;  
  $NULL) echo "wifi is down" ;;
 esac 
```

copy to an editor,paste, save as...a file name.
in terminal  chmod +x    "the-file-name"
terminal command ......   ./"the-file-name"

test with wifi enabeled then disabeled

---

### Post by Cheesehead on 2013-01-12
> **FerroPower said:**
> Sorry I don't know how to use DBUS for managing scripts which should trigger on Interface enabled/disabled.

Upstart listeners can be even easier.

For example, 
```
$ cat /etc/init/my-network-up.conf
description "My custom network upstart events"
start on net-device-up IFACE=wlan0
script
# Script to run as root goes here
end script

```

wlan0 is my wireless interface. You must substitute your own, of course.

> **FerroPower said:**
> I also tried using the Upstart method & also putting the script inside /etc/network/if-up.d/ but for some reason It doesn't execute whenever the wifi is enabled. However the script gets executed when I unplug and plug my WIRED connection. I want the script to on enabling of WIFI via Network-manager. 
Nothing gets triggered off when a WIFI is disabled or Enabled. 

The net-device-up and net-device down signals are emitted by the same scripts for Upstart, regardless of the interface. As you can see from the example above, the interface name *is* contained in the signal. So if it works for wired, it will certainly work for wireless...if you are using the correct interface names, and really using Network Manager to manage those interfaces instead of some workaround.

If you put your script(s) inside /etc/network/if-up.d/, look at the fundamentals: Does the script have logic to identify if the desired interface is being brought up/down? Is is properly owned by root? Is it executable?

---

### Post by Hadaka on 2013-01-12
Hi, after doing some research form this link..

[http://www.cyberciti.biz/faq/debian-ubuntu-linux-setting-wireless-access-point/](http://www.cyberciti.biz/faq/debian-ubuntu-linux-setting-wireless-access-point/)

i finally figured out you disable  eth0  not wlan0 when you uncheck enable wireless network
with the network mgr,. So as you stated early on, when you unplug your ethernet
cable your script works. Im guessing your script says wlan0, i would suggest changing
it to eth0 and then disable and enable  wireless   with network mgr. The Hostapd br0 bridging makes your eth0 basically wireless and
changes the confiuration of wlan0. While my script can be made to work, Cheesehead
is correct, its better to use something designed for exactly what you are wanting to
do. Perhaps cheesehead can take a look at the hostapd how to link and add the
one liner START / STOP commands to his Upstart scrip and get you up and running.

---

### Post by FerroPower on 2013-01-13
> **Hadaka said:**
> Hi, after doing some research form this link..

[http://www.cyberciti.biz/faq/debian-ubuntu-linux-setting-wireless-access-point/](http://www.cyberciti.biz/faq/debian-ubuntu-linux-setting-wireless-access-point/)

i finally figured out you disable  eth0  not wlan0 when you uncheck enable wireless network
with the network mgr,. So as you stated early on, when you unplug your ethernet
cable your script works. Im guessing your script says wlan0, i would suggest changing
it to eth0 and then disable and enable  wireless   with network mgr. The Hostapd br0 bridging makes your eth0 basically wireless and
changes the confiuration of wlan0. While my script can be made to work, Cheesehead
is correct, its better to use something designed for exactly what you are wanting to
do. Perhaps cheesehead can take a look at the hostapd how to link and add the
one liner START / STOP commands to his Upstart scrip and get you up and running.


Thanks for all of your help, As I have already told earlier I had already made Hostapd script which enables my Laptop to share my eth0 connection via  WPA/WPA2 based Virtual Access Point, its working 100%. All I need is trigger script which can trigger it when WIFI is enabled or disabled I tried all of the above methods to invoke my script but without any success. 

I think something is wrong with my ubuntu installation because nothing gets triggered when I enable or disable the Wireless from Network-Manager. I will try it on some other PC with Ubuntu or linux installation. 

As far I am able to start the script by unplugging and plugging back the eth0, its all right for me. and I will keep on finding solution, if any success I will definitely post it here. 

Thanks for all of your help.



P.S. I am not using bridge for connection sharing, I am getting the internet through ethernet on ppp0 and sharing it via my wlan0 as WPA/WPA2 Hotspot using hostapd.

---

### Post by Hadaka on 2013-01-13
Hi, this link...

[http://askubuntu.com/questions/41400/how-do-i-make-the-script-to-run-automatically-when-tun0-interface-up-down-events](http://askubuntu.com/questions/41400/how-do-i-make-the-script-to-run-automatically-when-tun0-interface-up-down-events)

has a simple script for testing, I played around with it and changed tun0 to wlan0
and eth0, it does indeed create a var/log file with the message. The key to getting 
it to fly is to be sure you are in root and the if-up.d directory when you chmod it.
you might give this a try to verify you can trigger.

---

### Post by FerroPower on 2013-01-14
> **Hadaka said:**
> Hi, this link...

[http://askubuntu.com/questions/41400/how-do-i-make-the-script-to-run-automatically-when-tun0-interface-up-down-events](http://askubuntu.com/questions/41400/how-do-i-make-the-script-to-run-automatically-when-tun0-interface-up-down-events)

has a simple script for testing, I played around with it and changed tun0 to wlan0
and eth0, it does indeed create a var/log file with the message. The key to getting 
it to fly is to be sure you are in root and the if-up.d directory when you chmod it.
you might give this a try to verify you can trigger.

hi buddy, thanks for your help I have already tried the above link much earlier with no success. as I said must be the problem with my installation.

---

### Post by steeldriver on 2013-01-14
out of curiosity, did you try either of the dbus-monitor commands I posted?

---

### Post by Hadaka on 2013-01-14
Hi, again. I dont know how you have your wireless ssid
connect set, ...automatic or you choose. I found that just
checking and unchecking enable wireless doesnt fire the trigger
I have to make a connection to the ssid for it to work. That was
with the script in /etc/network/if-up.d
Im curious, when you uncheck Enable Wireless..who goes away 
on the ifconfig output ??....eth0,lo,wlan0...or maybe br0
also removing the "sh" in your script might help,should be #!/bin/bash
not #!/bin/sh  or <filename>. "sh"

---

### Post by FerroPower on 2013-01-15
> **steeldriver said:**
> out of curiosity, did you try either of the dbus-monitor commands I posted?


Sorry I haven't tried the dbus commands you posted, I am not much an expert in linux, the commands looks kind of complicated to me.

---

