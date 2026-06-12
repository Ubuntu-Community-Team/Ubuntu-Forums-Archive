---
title: "have to start network each time"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by jnoreiko on 2006-06-10
I've just upgraded to Dapper with the built-in GUI upgrader. 

My network isn't working: when I boot up, and launch firefox, it says the page can't be found.
I open the Networking prefs, open the ethernet properties, disable the connection, then renable -- and then everything works again. But I have to go through these steps each time I boot up.

I'm using a router with DHCP.

---

### Post by Ixzat on 2006-06-10
Same problem here... Its kinda annoying since its a server im running, so i cant reboot the machine unless im at home with physical access to it to do these steps. Does anyone have a solution?

Heres my /etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```


Does the eth2,ath0 and wlan0 mess things up? Will it mess things up if i remove them?

---

### Post by dagr8tim on 2006-06-11
I have the same problem and would love to figure out why.  My case isn't as important because this is a secondary beater box.

The results of the /etc/network/interfaces file for me is:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
:

---

### Post by jnoreiko on 2006-06-17
Well at least it's not just me :)

Really annoying though.
I've filed a bug: [https://launchpad.net/distros/ubuntu/+bug/50099](https://launchpad.net/distros/ubuntu/+bug/50099)

---

### Post by Ixzat on 2006-06-17
Well, looks like it sorted itself out somehow... The only differance in my system is that i installed the k7 kernel instead of the default one, and then todays gnome updates. Besides from that, i havent touched anything.

---

### Post by ajifans on 2006-06-23
I still have this problem; it's not a major issue but it is really annoying.

Anyone know of any fixes yet?

---

### Post by Fedup on 2006-06-23
[QUOTE=ajifans]I still have this problem; it's not a major issue but it is really annoying.

Anyone know of any fixes yet?[/QUOTE]

Ah right, so its not **just **me who's having this problem :-k

---

### Post by ajifans on 2006-06-26
As a temporary workaround, is it possible to use something like 'cron' or similar to get eth0 to deactivate and then reactivate automatically every time I hard reboot?

---

### Post by Fedup on 2006-07-03
Bump - still not fixed :(

---

### Post by jnoreiko on 2006-08-02
I've found that if I reboot from Windows into Ubuntu, I don't have this problem.
Based on that, I've just tried switching my router on before my PC, and giving it time to connect to the internet before booting into Ubuntu -- the result is that I didn't have this problem!

So it would appear there's some problem that Ubuntu doesn't find anything on the network while the router is not ready and therefore decides not to talk to it -- either this was introduced in Dapper, or a change in the order or timing of the boot sequence has brought this to light.

---

### Post by jinx099 on 2006-08-05
I have this problem too, but I'm using this box as a headless server, so it's imperative I find a fix.  I suppose I could just make a script to do an ifup eth0, but how would I make it do that everytime on bootup?

---

### Post by evergreen on 2006-08-05
> **ajifans said:**
> I still have this problem; it's not a major issue but it is really annoying.

Anyone know of any fixes yet?

Hi I have this problem to ](*,) 

Thanks for the tip to restart eth0 though Networking saves me rebooting 10 times ;) Anybody found any new fixes?

---

### Post by drtvasudevan on 2006-08-05
> **evergreen said:**
> Hi I have this problem to ](*,) 

Thanks for the tip to restart eth0 though Networking saves me rebooting 10 times ;) Anybody found any new fixes?

](*,) 
add one more to those suffering.
have been searching this forum last 10 days, which returned umpteen results, none of them relevant.
at least i found i am not alone.
in frustration i turned to pm ing one of those in the moderator list and got politely turned away.
:-# 
will some one who knows how to report a bug please do it?

---

### Post by jnoreiko on 2006-08-05
> **drtvasudevan said:**
> ](*,) 
will some one who knows how to report a bug please do it?

There is already a bug reported
[https://launchpad.net/distros/ubuntu/+bug/50099](https://launchpad.net/distros/ubuntu/+bug/50099)

There's no point badgering the developers about it, as it will only annoy them.
However, it would be nice to have some indication that they've put it on their list of things to do :)

---

### Post by drtvasudevan on 2006-08-05
oh, thanks.
of course one does not want to bug the debuggers!
as you say, if someone had posted that this is a bug and they are at it, it would have helped so many with their frustrations.

---

### Post by jinx099 on 2006-08-05
Alright guys, I found a workaround and it works for me.

1) Open up a terminal and go to /etc/init.d

```
cd /etc/init.d/
```

2) make a new file called start-netorking as root

```
sudo vi start-networking
```

substitute vi with gedit or whatever if you wish

3) Make it a script that just starts your interfaces.  Use this as an example:

```

#!/bin/bash

ifup eth0
ifup eth1

```

I have 2 interfaces called eth0 and eth1.  You will probably only need the eth0 part if you only have 1 NIC.

4) change mode of script
```
sudo chmod 755 start-networking
```

5)  ```
cd ../rc2.d/
```

7) make a link to your script in this dir

```
sudo ln -s ../init.d/start-networking S90start-networking
```

8) reboot and see if it works!

---

### Post by peterthewolf on 2006-08-05
I have this problem too it did not happen until about 10 days ago so it is something in one of the upgrades since then

---

### Post by drtvasudevan on 2006-08-06
i too dont remember having this problem before upgrades.
did you upgrade to i686?
i did.
can the kernal cause a problem?

---

### Post by Mark Ferguson on 2006-08-06
I think I have found a solution to this problem, well it's fixed things for me.

I have posted a full explanation of how I found the fix on the launchpad site. [https://launchpad.net/distros/ubuntu/+bug/50099](https://launchpad.net/distros/ubuntu/+bug/50099)

Here is the cut down version.

I found a problem in the /etc/udev/rules.d/85-ifupdown.rules file.

FIX to /etc/udev/rules.d/85-ifupdown.rules: Remove unnecessary "--" from ifup and ifdown cmds.
 /***********************************************************************/
 SUBSYSTEM!="net", GOTO="net_end"
# Bring devices up and down only if they're marked auto.
 # Use start-stop-daemon so we don't wait on dhcp
 ACTION=="add", RUN+="/sbin/start-stop-daemon --start --background --pidfile /var/run/network/bogus --startas /sbin/ifup --allow auto $env{INTERFACE}"
 ACTION=="remove", RUN+="/sbin/start-stop-daemon --start --background --pidfile /var/run/network/bogus --startas /sbin/ifdown --allow auto $env{INTERFACE}"
LABEL="net_end"
 /*********************************************************************/

---

### Post by evergreen on 2006-08-06
> **Mark Ferguson said:**
> I think I have found a solution to this problem, well it's fixed things for me.

I have posted a full explanation of how I found the fix on the launchpad site. [https://launchpad.net/distros/ubuntu/+bug/50099](https://launchpad.net/distros/ubuntu/+bug/50099)

Here is the cut down version.

I found a problem in the /etc/udev/rules.d/85-ifupdown.rules file.

FIX to /etc/udev/rules.d/85-ifupdown.rules: Remove unnecessary "--" from ifup and ifdown cmds.
 /***********************************************************************/
 SUBSYSTEM!="net", GOTO="net_end"
# Bring devices up and down only if they're marked auto.
 # Use start-stop-daemon so we don't wait on dhcp
 ACTION=="add", RUN+="/sbin/start-stop-daemon --start --background --pidfile /var/run/network/bogus --startas /sbin/ifup --allow auto $env{INTERFACE}"
 ACTION=="remove", RUN+="/sbin/start-stop-daemon --start --background --pidfile /var/run/network/bogus --startas /sbin/ifdown --allow auto $env{INTERFACE}"
LABEL="net_end"
 /*********************************************************************/

Thanks for this I have rebooted a few times to test this fix and things look good for me. I'll report back if I find any problems. Good work:D

---

### Post by drtvasudevan on 2006-08-06
> Mark Ferguson  	I think I have found a solution to this problem, well it's fixed things for me.

I have posted a full explanation of how I found the fix on the launchpad site. [https://launchpad.net/distros/ubuntu/+bug/50099](https://launchpad.net/distros/ubuntu/+bug/50099)

Here is the cut down version.

does not seem to work for me.
the extra -- ar there.
removed them. still no go after re booting a couple of times.
:confused:

---

### Post by jinx099 on 2006-08-06
> **drtvasudevan said:**
> does not seem to work for me.
the extra -- ar there.
removed them. still no go after re booting a couple of times.
:confused:

Have you tried my way yet?

---

### Post by mrazster on 2006-08-06
> **Mark Ferguson said:**
> I think I have found a solution to this problem, well it's fixed things for me.

I have posted a full explanation of how I found the fix on the launchpad site. [https://launchpad.net/distros/ubuntu/+bug/50099](https://launchpad.net/distros/ubuntu/+bug/50099)

Here is the cut down version.

I found a problem in the /etc/udev/rules.d/85-ifupdown.rules file.

FIX to /etc/udev/rules.d/85-ifupdown.rules: Remove unnecessary "--" from ifup and ifdown cmds.
 /***********************************************************************/
 SUBSYSTEM!="net", GOTO="net_end"
# Bring devices up and down only if they're marked auto.
 # Use start-stop-daemon so we don't wait on dhcp
 ACTION=="add", RUN+="/sbin/start-stop-daemon --start --background --pidfile /var/run/network/bogus --startas /sbin/ifup --allow auto $env{INTERFACE}"
 ACTION=="remove", RUN+="/sbin/start-stop-daemon --start --background --pidfile /var/run/network/bogus --startas /sbin/ifdown --allow auto $env{INTERFACE}"
LABEL="net_end"
 /*********************************************************************/



This helped me to...with both of my networking problem.
Have them posted [HERE](http://www.ubuntuforums.org/showthread.php?t=230214)
Again...thnx a bunch Mark Ferguson for sharing this.

---

### Post by drtvasudevan on 2006-08-06
not yet.
shall do so.
hoping......

---

### Post by peterthewolf on 2006-08-07
Jinx099
Tried your way - did not work for me I use a wireless usb dongle so had to change ifups to ifup rausb0 but no joy.

Marks way works everytime but the 3 minute delay is a bit of a nuisance particularly since it makes ubuntu a LOT slower to load than XP

---

### Post by drtvasudevan on 2006-08-07
jinx099
does not work for me either.

---

### Post by Mark Ferguson on 2006-08-07
drtvasudevan

I did something similar to jinx099 before I found the problem with the udev ifupdown rule. It's just a hack but worked.

try adding the following 4 commands to the /etc/rc.local (It's one of the last boot scripts to run from /etc/rc2.d/). This will stop and start the network again during boot.

```
/etc/init.d/networking stop

# sometimes dhclient did not stop when the network was brought down, so kill it
ps -fu dhcp | grep dhclient | perl -e 'while (<>) { if ($_ =~ /^\w+\s+(\d+)\s+/) {print "kill dhclient pid: $1\n"; system("kill $1");}}'

/etc/init.d/networking start

exit 0
```


The original problem I saw before I made the udev change was ifconfig showed that the network interface was up, but no ip address was assigned. dhclient was running so theoretically an ip should have been assigned. The original 85-ifupdown-rules file appeared to be corrupting my network configuration. This was highlighted by having to kill the dhclient after stopping the network.


peterthewolf is right, the network start up time is really slow at boot with the udev ifupdown rule change. I think there are still some underlying problems with the udev/networking startup, so hopefully this gets looked at by ubuntu at some stage.

---

### Post by mrazster on 2006-08-07
> **peterthewolf said:**
> Marks way works everytime but the 3 minute delay is a bit of a nuisance particularly since it makes ubuntu a LOT slower to load than XP


Haven't noticed any extended booting time at all...if there is any it's absolutely no more than a second or 2. But I'm more than willing to go with that if my network works correctly.

Did this yestarday....and everything still works perfect.

THNX again Mark  \\:D/ =D>

---

### Post by drtvasudevan on 2006-08-07
> **Mark Ferguson said:**
> drtvasudevan

peterthewolf is right, the network start up time is really slow at boot with the udev ifupdown rule change. I think there are still some underlying problems with the udev/networking startup, so hopefully this gets looked at by ubuntu at some stage.

well. no harm trying this too i think.
do i have to undo the changes i made already?
that is remove jinx009 's solution and yours too?
how do i do that?
yours is easy. perhaps not needed at all, as i see little change in booting time.
how about the other? i need to delink the link made already.

---

### Post by Paulr-55 on 2006-08-07
I'm having same issue with Dapper and my DSL modem. When I boot up, the usual messages go by and I get:

Starting Network ... Failed
...
...
Configuring Network ... Failed

Started doing this after I ran pppoeconf when I set up my DSL connection (which is brand new today - before this I was on dial-up)

My etc/network is:

> auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

# added by pppoeconf
auto eth0

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

I have to use System/Administration/Networking GUI tool to establish internet after boot-up.

Can live with that but could be better too!

---

### Post by jinx099 on 2006-08-07
Hmm, my way didnt work for you guys, huh?  I'll undo my mod and see if the problem starts again, but so far everything has worked great for me and no apparent increase in boot time.  What kernel are you guys running?  I'm on the latest k7 kernel.

---

### Post by drtvasudevan on 2006-08-08
thanks jinx
i am on i686 kernel
i have made a profile and the settings work.
how can i make this my default profile?
that is the same problem differently put?

---

### Post by Mark Ferguson on 2006-08-08
> **drtvasudevan said:**
> well. no harm trying this too i think.
do i have to undo the changes i made already?
that is remove jinx009 's solution and yours too?
how do i do that?
yours is easy. perhaps not needed at all, as i see little change in booting time.
how about the other? i need to delink the link made already.

You may as well leave the 85-ifupdown.rules change, as it does fix syntax problems in the file.

Remove the link or comment out the script on jinx009's solution. 

Add my hack to the rc.local file. You can easily comment out these
changes and switch back to jinx009's solution too.

---

### Post by drtvasudevan on 2006-08-08
sad to report that there is no progress.

tv

---

### Post by jinx099 on 2006-08-08
Yesterday I removed the sym link to the script and was able to reproduce the problem.  So my startup script is the working solution for my machine.

drtv, when your machine is booted are you able to solve the problem just by doing a "sudo ifup eth0"?

---

### Post by drtvasudevan on 2006-08-09
will check next time when i boot.

---

### Post by drtvasudevan on 2006-08-10
> **jinx099 said:**
> 
drtv, when your machine is booted are you able to solve the problem just by doing a "sudo ifup eth0"?

it says ifup already configured
the network is not activated.
i still have to open it and change the profile.(in the location box)
then everything works.

---

### Post by jinx099 on 2006-08-10
> **drtvasudevan said:**
> it says ifup already configured
the network is not activated.
i still have to open it and change the profile.(in the location box)
then everything works.

drtv, try my script way again but use this script instead of my original one:

```
#!/bin/bash

ifdown eth0
ifup eth0

```

if that doesnt work, try simply:

```
#!/bin/bash

dhclient eth0


```

---

### Post by drtvasudevan on 2006-08-10
will try this.
meanwhile..
i have configured a location called CDL01,in which the settings are right.
the problem is i have to activate network settings and  change location each time to get on net.
can this process be run through a start up script in which case my problem is solved?

in all probability the dhcp will work. the problem with that setup is that i cant get updates through that. that is why configured the static ip settings and all sorts of problems  began.

---

### Post by elix on 2006-08-10
I install Ubuntu Server Drapper Drake and have the same problem.

When boot up the two interfaces and connect to my ISP (ASDL at eth1), I add  a few NAT rules and works fine with browsers at any windows client (DHCP sever at eth0).
But the messenger clients ( Yahoo, MSN, any ) cant connect. :( I need to restart network services and works fine. Well until yesterday, because now I start my machine and... Now I try to connect to ISP but doesnt UP eth1 ethernet card ( local network ), I replace with another ( the same chipset model ) and doesnt up and not work the DHCP daemon when boot :-(. :confused: 


Any Idea ? I m really bored with these. :sad:

---

### Post by The Shadow on 2006-08-10
I am having the same problem. I have tried all of the fixes listed here. I am now able to access the internet, but it ain't easy. I boot my computer andusing the network status tool i am able to see that eth0 hasan ip address, but it is idle. If i start my web browser it will hang up trying to locate the website. while it is doing that i can select "configure" on the network tool and suddenly the web page will load. each time i want to proceed to the next page i have to do the same thing.

has anyone located a fix yet?

---

### Post by drtvasudevan on 2006-08-11
perhaps.
after a few more shutdowns...and restarts...

---

### Post by drtvasudevan on 2006-08-11
no go.
but the problem was partlly solved by looking at this thread.
[http://www.ubuntuforums.org/showthread.php?t=233123](http://www.ubuntuforums.org/showthread.php?t=233123)
now i can go to net right away.
but there seems to be some updating problem unsolved yet.
update does not work
i need time to see if it is just that servers are down or busy now or network issues.

---

### Post by peterthewolf on 2006-08-17
Just to add a real weirdo
I bboted ubuntu and the icon at top right for software updates appeared so it must have contacted internet to know. But when I tried firefox it failed and then when I tried software update it also failed.

So maybe two ways to look at problem
1. during boot the connection is made but subsequently corrupted
2. firefox screws things up.

---

### Post by jinx099 on 2006-08-18
what does "sudo ifconfig" show right after boot, before and after starting firefox?

---

### Post by jnoreiko on 2006-09-04
I've found a way round this: use Hibernate instead of shutting down.

Only downside is that resuming from Hibernation asks for my password :(

---

### Post by lukew on 2006-09-08
Hi,

I did the removal of excess from -- of ifup and ifdown and all i get now is a long pause.  :( I am going to put it back! :)  

I normally have deactivate, activate ( 1 min pause ), deactivate and then activate to start. the later activate only take a few seconds. I have stoped dhcp and assign my own ip address which is much quicker, but still requires a down/up/down/up combo.

Has anyone else seen this? [http://www.linuxquestions.org/questions/showthread.php?t=382592](http://www.linuxquestions.org/questions/showthread.php?t=382592)

"I found a solution to this problem from Larry and Andreas. The problem is with supplicant.
Modify /etc/sysconfig/network/ifcfg-wlan-id... adding the line
PREFER_WPA_SUPPLICANT='no'"

We dont seem to have that in ubuntu, i presume it should go in /etc/network/interfaces but the = between parameter name and values contradicts the current value assignment convention in there. Any ideas?

Cheers

Luke

---

### Post by mbaker514 on 2006-09-09
Hi

Wasn't there an ifupdown upgrade released a few days ago? Could we possibly have yet another bogus update to add to the list? 

Good luck

---

### Post by Fripounet on 2006-09-11
Hello,

This is my first post on ubuntu forums :)

It seems there are a lot of people impacted by this bug. We assume that it is not a DHCP server problem (LAN or internet access) or a firewall configuration problem.
I have this problem on a clean intall of Ubuntu Dapper 6.06.1, with and without the updates.

Bug general description:
- No network at boot
Detail:
- lo and et0 are up (listed by ifconfig) but eth0 has no IP address.

Strangely, "/etc/init.d/networking restart" works fine and we can get an IP from the DHCP server. "ifdown -a" and "ifup -a" works fine too. eth0 IP configuration is only skipped at boot time.

I did not find the explanation or the solution, I just found a workaround:
- edit /etc/init.d/networking 
- add "--force" in the "ifup -a" lines
example:
- before: ifup -a
- after: ifip -a --force

eth0 IP configuration will not be skipped/ignored.

Sorry for the mistakes, english is not my native language. Do not hesitate to correct me :)

---

### Post by akkiman on 2006-09-11
Strange thing is that I see the same error.
The only difference is that I need to delete the default DNS entries in the networkign button, and add my DNS server's IP address. Then the network works fine.

After the next reboot, the DNS values change back to default. Is there to permanently make a change there ?

---

### Post by atmurray on 2007-01-05
Hi everyone, I've detailed how to fix the bug where ppp connections are not persistent due to a bug in udev here:

[http://rants.atmurray.net/2007/01/pppd-persist-not-so-persist-with-udev.html]("http://rants.atmurray.net/2007/01/pppd-persist-not-so-persist-with-udev.html")

I hope this kills this problem once and for all and we see see this bug squashed in an update soon.

---

### Post by darkborg on 2007-04-02
> **Mark Ferguson said:**
> drtvasudevan

I did something similar to jinx099 before I found the problem with the udev ifupdown rule. It's just a hack but worked.

try adding the following 4 commands to the /etc/rc.local (It's one of the last boot scripts to run from /etc/rc2.d/). This will stop and start the network again during boot.

```
/etc/init.d/networking stop

# sometimes dhclient did not stop when the network was brought down, so kill it
ps -fu dhcp | grep dhclient | perl -e 'while (<>) { if ($_ =~ /^\w+\s+(\d+)\s+/) {print "kill dhclient pid: $1\n"; system("kill $1");}}'

/etc/init.d/networking start

exit 0
```


The original problem I saw before I made the udev change was ifconfig showed that the network interface was up, but no ip address was assigned. dhclient was running so theoretically an ip should have been assigned. The original 85-ifupdown-rules file appeared to be corrupting my network configuration. This was highlighted by having to kill the dhclient after stopping the network.


peterthewolf is right, the network start up time is really slow at boot with the udev ifupdown rule change. I think there are still some underlying problems with the udev/networking startup, so hopefully this gets looked at by ubuntu at some stage.


dude your solution rocks!!!
:guitar: 

You made my day.

---

### Post by darkborg on 2007-04-02
> **Mark Ferguson said:**
> drtvasudevan

I did something similar to jinx099 before I found the problem with the udev ifupdown rule. It's just a hack but worked.

try adding the following 4 commands to the /etc/rc.local (It's one of the last boot scripts to run from /etc/rc2.d/). This will stop and start the network again during boot.

```
/etc/init.d/networking stop

# sometimes dhclient did not stop when the network was brought down, so kill it
ps -fu dhcp | grep dhclient | perl -e 'while (<>) { if ($_ =~ /^\w+\s+(\d+)\s+/) {print "kill dhclient pid: $1\n"; system("kill $1");}}'

/etc/init.d/networking start

exit 0
```


The original problem I saw before I made the udev change was ifconfig showed that the network interface was up, but no ip address was assigned. dhclient was running so theoretically an ip should have been assigned. The original 85-ifupdown-rules file appeared to be corrupting my network configuration. This was highlighted by having to kill the dhclient after stopping the network.


peterthewolf is right, the network start up time is really slow at boot with the udev ifupdown rule change. I think there are still some underlying problems with the udev/networking startup, so hopefully this gets looked at by ubuntu at some stage.


dude your solution rocks!!!
:guitar:  :KS  

You made my day.

---

