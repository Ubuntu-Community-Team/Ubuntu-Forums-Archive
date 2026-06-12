---
title: "dhcp request as cron job questions"
date: 2012-12-05
forum: Networking &amp; Wireless
---

### Post by wayover13 on 2012-12-05
Hi. I've got a rather flaky wifi connection from one of my computers (highly modified ubuntu 12.04) to the gateway and am looking into ways of preventing the connection from going down. I decided that running a dhcp request from said machine every 4 hours or so might do the trick, so I implemented a quick and dirty solution: 0 0,4,8,12,16,20 * * * /sbin/dhclient eth0 as an entry in root's crontab file.

While that cron entry helps a great deal, I note that it has an undesirable effect: namely, when I run htop I can see many instances of dhclient running. Apparently the process needs to be killed, then restarted. So, might a more sensible way of doing this be to make a cron entry that looks like this: 0 0,4,8,12,16,20 * * * /sbin/dhclient -x && /sbin/dhclient eth0? From my reading of the dhclient man page that should kill, then restart dhclient.

Broadcasting for a new dhcp lease can also be done using ifup, as I know from experience. I tried entering 0 0,4,8,12,16,20 * * * /sbin/ifup --force eth0 into root's crontab file, but that has the same effect of causing multiple instances of dhclient to run. So, once again it seems something should be killed, then restarted.

Relevant to that, and as a final query in this thread, there are more sophisticated ways of doing what I'm after. To wit, a script could be created that established whether the network is up by  doing a ping test or such, then a request for an IP can be run--or not--depending on the result. I ran across a script that someone created that seems pretty close to what I need at [http://ubuntuforums.org/showthread.php?t=1101174](http://ubuntuforums.org/showthread.php?t=1101174) but I don't completely understand how that works

For my purposes, that script would actually be modified to ping the gateway at 192.168.1.1 instead of pinging some internet address, for starters. So it would need to look something like this:```
#!/bin/bash

if ! `ping -c 1 -w 1 -q 192.168.1.1 </dev/null &>/dev/null` ; then
        echo resetting eth0
        ifdown eth0
        ifup eth0
        ip route add default via ath0 table WIFI
else
        echo eth0 operational
fi
exit 0
```
Two main things I do not understand about this script. First of all, where does the result of the echo commands get recorded? In /var/log/messages? Second, and more important, why is the line "ip route add default via ath0 table WIFI" needed? When I run ifup manually on this machine, there is no need to tell it about any sort of route: the machine gets its lease renewed and I can once again browse the 'net.

Input on these issues and suggestions for accomplishing the task will be greatly appreciated.

James

---

### Post by ahallubuntu on 2012-12-05
As a side question: can we assume the reason you aren't using a static IP is that you don't have any control over the router?

---

### Post by wayover13 on 2012-12-05
> **ahallubuntu said:**
> As a side question: can we assume the reason you aren't using a static IP is that you don't have any control over the router?
I actually do have control over the router and could assign a static IP. I guess I hadn't considered that since it wasn't obvious to me that such would solve the dropped connection problem. I say that because I note that, when I loose the connection to the router/gateway and cannot therefore reach the internet from that machine, I see nonetheless that the computer still has its IP (as witnessed by ifconfig output). Despite that fact I cannot ping the router/gateway or any internet address. Successfully issuing  an IP renewal request by running dhclient restores the connection in those instances. As I mentioned, the connection is a bit flaky--owing largely to the fact that I cannot get the reception point into very close or direct relation to the broadcast point.

Thanks,
James

---

### Post by redmk2 on 2012-12-05
> **wayover13 said:**
> I actually do have control over the router and could assign a static IP. I guess I hadn't considered that since it wasn't obvious to me that such would solve the dropped connection problem. I say that because I note that, when I loose the connection to the router/gateway and cannot therefore reach the internet from that machine, I see nonetheless that the computer still has its IP (as witnessed by ifconfig output). Despite that fact I cannot ping the router/gateway or any internet address. Successfully issuing  an IP renewal request by running dhclient restores the connection in those instances. As I mentioned, the connection is a bit flaky--owing largely to the fact that I cannot get the reception point into very close or direct relation to the broadcast point.

Thanks,
James

What is the lease time on the DHCP provided IP address? I'll bet if you shorten it you can achieve the same results as your cron job.  If you have the lease set for 8 hours, the dhcp client starts requesting for renewal at 4 hours.  In other words at 1/2 the lease time the dhcp requests start.  Once again, what is the length of the DHCP lease(s)?

---

### Post by wayover13 on 2012-12-05
Thanks for your reply and suggestion, redmk2. Lease time is currently set at 1440 minutes (24 hours). What would be your suggestion for lowering the lease value? 12 hrs? 6 hrs? Looks like that's worth a try.

James

---

### Post by redmk2 on 2012-12-05
> **wayover13 said:**
> Thanks for your reply and suggestion, redmk. Lease time is currently set at 1440 minutes (24 hours). What would be your suggestion for lowering the lease value? 12 hrs? 6 hrs? Looks like that's worth a try.

James

Since you mentioned 4 hours is what you wanted your cron job to run I would start with a lease at 8 hours.  This config should start requesting a lease renewal at 4 hours.  If you wanted it less you just have to remember that the requests start at 1/2 the lease time you configure.

Idk if this will solve you underlying problem, but it's clean (no script or cron job) and it will do what you want the corn job to do.

---

### Post by wayover13 on 2012-12-05
Sounds good, redmk2. I'll give 480 minutes lease time a try. I'll try and report back here with results at some point in the future.

Thanks,
James

---

### Post by wayover13 on 2012-12-06
redmk2's approach of reducing lease time on the router did not work, perhaps because the wifi set-up is not completely straightforward. The computer in question is actually attached to a router that runs in client mode. I run a free version of dd-wrt on that router, and I suspect that version is a bit flaky since I've found that, to better stabilize the connection, I have to hard-reboot the device every 24 hours. For that I got a timer through which the router gets its power, and I set the timer to turn off and then on again after 1 minute, at 4 A.M.

I note that, after that power-off/power-on sequence this morning, the computer lost its connection to my main router (the one that governs IP lease time). So I decided to go ahead and experiment with the script I found and posted above, thinking that perhaps a combination of the two hacks will improve stability.

I commented out the "ip route add default via ath0 table WIFI" line in that script, then ran it from the command line and it seemed to work fine. Of course the output from the echo command displayed in the terminal in that case. But I'm guessing that echo stuff was put in there for testing purposes and I'll probably end up taking it out since, if this is run as a cron job, there will no place for that output to be redirected.

I've set up the cron job and will report later if this additional kludge manages to keep the connection stable.

James

---

