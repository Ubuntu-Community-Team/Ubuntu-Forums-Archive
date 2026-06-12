---
title: "networking doesnt work on boot, please help"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by kylegio on 2009-11-12
ongoing problem have not been able to find a solution for several weeks, no one seems to have much useful input this is a last cry for help. 


on boot if i log in (using a keyboard and monitor, ssh does not work) and give an ifconfig command there is absolutely no output. no interfaces, nothing.

(ps this is ubuntu 9.10)
if i give either /etc/init.d/networking restart  or service networking restart
then do a networking restart it works perfectly. i can not for the life of me figure out why on boot it does not properly start networking, is there a way to just fully re-install networking from scratch. the problem is that many of my services depend on networking to be running (apache2, some p2p stuff, etc.) these all have to be manually stopped and re-started after every reboot because they do not start properly without networking. for example in apache i have multiple domains / virtual domains, if they can not be reached at the time apache is started then they do not work.
it is an absolute pain having to 1) have a keyboard and mouse attached to my server because i cant ssh into it on restart until i reset the networking 2) have to be at the physical location of my server to do so... sometimes i'm not near it for weeks and then i wont be able to get it back up 3) having to go and restart a whole slew of services after booting. 

i am not looking for a work-around like putting /etc/init.d/networking restart in a init script, because then i still have to restart everything else and its just a mess. i just want networking to work properly. i am willing to put the server down for a couple hours on some of the less traffic times and do whatever i have to to get it working properly again.

can ANYONE think of a way to fix this/why it is not working/can the entire networking package be re-installed?/ should i re-install my entire server?/go back to 9.04?


i appreciate any help!
thanks,
kyle

---

### Post by Iowan on 2009-11-12
Is your networking configured via */etc/networking/interfaces* or does the machine have a desktop with Network Manager? 
(Post */etc/networking/interfaces*)

---

### Post by kylegio on 2009-11-12
/etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0
iface lo inet loopback

# The primary network interface
iface eth0 inet dhcp

```

i do not think it is a problem here because forcing a restart of networking makes it work just fine, if this had a problem wouldn't the networking not work at all? before doing a restart of networking service after booting ifconfig doesn't even show the loopback interface, 
its just blank:
```

$sudo ifconfig
$

```

then after restart of networking it shows all interfaces/loopback etc gets DHCP address.

---

### Post by Iowan on 2009-11-13
> **kylegio said:**
> i do not think it is a problem here I'm inclined to agree - The "auto" line is present.  I wonder how networking is enabled/disabled on boot.  Older versions would have had it in rcX.d directories.  Dunno how the "service" thing works...

---

### Post by kylegio on 2009-11-13
> **Iowan said:**
> I'm inclined to agree - The "auto" line is present.  I wonder how networking is enabled/disabled on boot.  Older versions would have had it in rcX.d directories.  Dunno how the "service" thing works...

i think it has something to do with this "service" thing, it worked before upgrade to 9.10, after that it worked for awhile i think:S but then one day i just couldnt connect to it, and discovered it was no longer working. i have no idea where to check to see if it is configured to start on boot anymore, i mean when its booting it says "starting network" or something along those lines, and its not start that i have to tell it to get it to work; its restart. its like its "starting" but not running the interfaces script, then it does that when i restart.

---

### Post by Iowan on 2009-11-13
Does it provide any interesting "error messages" if you try a "start" instead of "restart" for networking?

---

### Post by kylegio on 2009-11-13
> **Iowan said:**
> Does it provide any interesting "error messages" if you try a "start" instead of "restart" for networking?

i do get a couple weird errors ive never seen before when i first boot
ill just paraphrase them because im lazy 
```
render error detected, EIR:0x00000010
*ERROR* EIR stuck 0x00000010
render error detected, EIR:0x00000010
```
then it says
```
 setting up preliminary keymap
preparint restricted drivers
cleaning up isupdown
starting apparmor profiles
**setting up networking  **
setting up console font and keymap
starting openBSD secure shell server sshd
starting mysql
checking for corrupt, not cleanly closed and upgrade needint gables
starting webserver apache2
Ubuntu 9.10 server tty1
server login:$|
```

i then log in check networking with ifconfig, yup still empty

```
$sudo /etc/init.d/networking start
Rather then invoking init scripts through /etc/init.d use the service(8) utility, e.g service networking start

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start(8) utility, eg start networking
start: Unknown job:networking
$
```

ok well lets try that then 
```
$sudo service networking start
rather then invoking init....etc same message
```

lets try the other one
```
$sudo start networking
Start:unknown job:networking

```

annnd what i can actually do to make it work
```
$sude /etc/init.d/networking restart
*reconfiguring network interfaces....etc gets DHCP addresses yadda yadda
```

so im thinking that the problem lies in the fact that it is an "Upstart" job whatever that means now and using the service utility to start it with "start" doesnt work, so its probably failing there in boot.

EDIT:

heres my thoughts on why it doesnt work with start but does with restart. checking the /etc/init.d/networking file  i see under the start case 
```

start)
      /lib/init/upstart-job networking start
      ;;

stop)...etc

```

however the restart case makes no reference to upstart-job,
calling /lib/init/upstart-job networking start manually returns (obviously) the error that Unknown job: networking. 

pretty sure thats my reason right there, testing out the hypothesis on my ubuntu desktop, i do not get the unknown job error when calling the /lib/init/upstart-job networking start. it spews some bs about using the service utility.

---

### Post by kylegio on 2009-11-13
sorry for double posting, 

after even more narrowing down i compared my "initctl list" from my desktop which works to my server which does not. smack in the middle of the initctl list for my desktop i see
```

network-interface lo start/running
network-interface eth0 start/running
network-interface eth1 start/running
...
networking stop/waiting

```

i do not see any occurrence of the word "network" in the initctl list for my server

yet another edit:
i have found that the files /etc/init/network-interface.conf and networking.conf to not exist on my server, i have copied them from my desktop, now 

sudo initctl lists 
network-interface start/running (it does not give a device name)
networking stop/waiting 

also /lib/init/upstart-job networking start now works, however no still no networking on boot. ifconfig still empty after restart, however after /lib/init/upstart-job networking start the ifconfig shows the interfaces. and works properly.



would it be useful to close this thread and make another one specifying in the title that the problem is upstart related so maybe i could get some more specific help, i think very few people are going to read tot he bottom of the thread to realize what the actual problem is

---

### Post by Iowan on 2009-11-14
Looks like you're zeroing in on it. Check **man service**. **service** is new to Karmic. Upstart sounds familiar, bud dunno if it's different than the other startup methods.
New thread? Kinda your choice. It may end up merged back with this one, but the troubleshooting direction has certainly changed, and a different title might elicit better response. You could still link to this one for background info.

---

