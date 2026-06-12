---
title: "connected...not really"
date: 2006-02-28
forum: Networking &amp; Wireless
---

### Post by aosmith on 2006-02-28
so im connected to my router via wifi (both sending and reciving packets), but cant get an ip via dhclient.  i know router is setup as dhcp any thoughts? TIA

---

### Post by joshuapurcell on 2006-03-01
Have you been to get a DHCP address while using a cable? Does **network-admin** show that your card is setup for DHCP?

---

### Post by aosmith on 2006-03-01
yes x 2

---

### Post by claes on 2006-03-01
Are you connected to the access point?

Check the output of iwconfig. 
claes@tdselt0136:~$ iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11b  ESSID:"Elektrosmog"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:12:17:B7:52:D9  <-- This is the intresting part.
          Bit Rate=11 Mb/s   Tx-Power:off
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=97/100  Signal level=-61 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:0   Missed beacon:0

---

### Post by aosmith on 2006-03-01
yup...

---

### Post by jamesr on 2006-03-01
can you ping the router, and post output.

---

### Post by aosmith on 2006-03-01
no i cant when i try i get <connect: Network is unreachable>

---

### Post by jamesr on 2006-03-01
please post the outputs of 

```
sudo iwconfig 
sudo ifconfig -a
```

---

### Post by claes on 2006-03-02
You could try and set the machine with static ip just to see that it works. Easier to see if it's the wireless that have problem or if it's something else.

Claes

---

### Post by aosmith on 2006-03-02
i tried static ip as well (along with reconfiguring my router)...

---

### Post by aosmith on 2006-03-02
here are the outputs:


<sudo iwconfig>

lo        no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"linksys"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:12:17:00:C1:A2
          Bit Rate:11 Mb/s
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-58 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


<sudo iwconfig -a>

-a        No such device

---

### Post by aosmith on 2006-03-02
i read something about run levels with the airgo chipset anyone?

---

### Post by claes on 2006-03-03
[QUOTE=aosmith]here are the outputs:


<sudo iwconfig>

lo        no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"linksys"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:12:17:00:C1:A2
          Bit Rate:11 Mb/s
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-58 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


<sudo iwconfig -a>

-a        No such device[/QUOTE]


This looks fine. Could you please test to use a static ip address an see if it works with that?

sudo ifconfig wlan0 [ipaddress] netmask [subnetmask]
ex.

sudo ifconfig wlan0 192.168.0.2 netmask 255.255.255.0

If I remember correctly this is usualy the default net on linksys.
And see if you can ping the linksys router?

Claes

---

### Post by aosmith on 2006-03-03
yup ill give it a try

---

### Post by sdb2028 on 2006-03-03
I was having pretty much the sme problems as you are. I tryd any of the suggestions in the forums, none seemed to work. I finnaly found where someone had posted the configuration in sysv-rc-conf. He showeed what he uses plus the defaults. I checked my configuration(which was different that the defaults) try'd some of his changes (which didn't work on my system) then went through and set all the check boxes to the defalts as listed. I have been up and running with no problems ever since (been 3 days now). Check the thread [http://ubuntuforums.org/showthread.php?t=138760](http://ubuntuforums.org/showthread.php?t=138760) 
I put in images of my configuration which you can use as a guide.
To get to the configuration window:
type sudo "sysv-rc-conf" (without quotes) in your terminal.
good luck, hope it helps.

---

### Post by sdb2028 on 2006-03-03
if you wnt to check out the thread about sysv-rc-conf:
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)
it explains everything.

---

### Post by aosmith on 2006-03-05
i looked through my synaptic package manager, found sysv-rc and installed with my cd in so i wouldnt need an internet connection.  whenever i run the command <sudo sysv-rc> or <sysv-rc-conf> i an error stating that this is an invalid command.  What do you guys think?

---

### Post by aosmith on 2006-03-05
[QUOTE=claes]This looks fine. Could you please test to use a static ip address an see if it works with that?

sudo ifconfig wlan0 [ipaddress] netmask [subnetmask]
ex.

sudo ifconfig wlan0 192.168.0.2 netmask 255.255.255.0

If I remember correctly this is usualy the default net on linksys.
And see if you can ping the linksys router?

Claes[/QUOTE]

nope still cant ping the router...

---

### Post by sdb2028 on 2006-03-05
try to get to 
> sudo sysv-rc-conf
you need to use "sudo" or it won't work.
I had internet issues for a long time, I finally did a fresh install so that everything would be at "default", then went through the sysv-rc-conf and set all the check marks to the defaults listed in the thread I sent earlier. I have now had NO connection problem for almost a week. I did not change the drivers, using the ones which came with the install. Didn't change the firmware either. I am using a IPW2200 built-in Centrino wireless with a linksys broadband wirelees G with speed boost router.
All isworking good.
Not sure why you can't get to the file, suggest try again-- make sure syntax is correct: sudo sysv-rc-conf
should let you in.
good luck, hope this helps.

---

### Post by aosmith on 2006-03-05
yea theres something funky with my install...maybe ill just do a fresh install again tongiht... and i know you have to have admin privlages to edit those folders...

---

