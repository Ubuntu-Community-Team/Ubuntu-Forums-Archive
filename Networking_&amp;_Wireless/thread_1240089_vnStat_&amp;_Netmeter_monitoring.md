---
title: "vnStat &amp; Netmeter monitoring"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by The Thug on 2009-08-14
I'm currently running Ubuntu 9.04 on my laptop.

At home I connect to the net with a 3G card and for obvious reasons want to monitor my traffic.

Under Win XP I used Netmeter which I found was extremely accurate.

After installing Ubuntu, I installed Netmeter under WINE and also installed vnStat. 

2 problems I have:

a. Unless I start Netmeter prior to connecting to the net, it doesn't record the usage (although I'm pretty good at starting it), and
b. The usage as recorded by vnStat does not agree to anything

If I compare MTD usage figures, I get the following:

Netmeter: 250 Mb
vnStat: 178 Mb
ISP: 261 Mb (per account info)

So as you can see, I'm not too bad with starting Netmeter BUT I don't want to have to rely on having to start an app.

Can anyone lead me to what the problem with vnStat might be ?

---

### Post by The Thug on 2009-08-15
So no-one has a clue ? :confused:

---

### Post by Vergo on 2009-08-18
> **The Thug said:**
> Can anyone lead me to what the problem with vnStat might be ?
I assume that you use a ppp connection with the 3G card? Is your connection always enabled or do you connect several times everyday?

The old version of vnStat that's in Ubuntu 9.04 has some limitation when used with interfaces that are often disabled. The reason is that it's not possible to get any traffic information from the interface after it gets disabled. With the default settings of vnStat in Ubuntu 9.04 it's possible to "miss" around 5 minutes of traffic at most every time you disable the interface. That's because the interface is polled only every 5 minutes. The poll interval can be changed by editing the cron entry in /etc/cron.d/vnstat but 1 minute is the shortest period cron supports. I can only assume that Netmeter polls much more often or Wine does some wrapping on how interfaces are visible to programs.

---

### Post by The Thug on 2009-08-18
Correct, I'm using PPP with a 3G card to connect which I might do once or twice a day.

I've upgraded to the latest vnStat (1.7) and have the following added in my crontab file

* * * * * root    if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi

---

### Post by Vergo on 2009-08-18
Version 1.8 is actually the latest. I'd also suggest using the daemon instead of the cron especially if you have your laptop set to spin down the hd when not used. That "once every minute" cron will keep the disk spinning all the time where as the daemon can be configured to save the database much less often (SaveInterval in /etc/vnstat.conf). Check also that MaxBandwidth has been set according to your connection speed in the config.

Note that if you choose to use the daemon then make sure to remove all vnstat cron related files from /etc. Something like "find /etc -name vnstat*" should give you a list of vnstat related files and only /etc/vnstat.conf and /etc/init.d/vnstat are needed for the daemon.

---

### Post by The Thug on 2009-08-18
Thanks, will download 1.8 and try out the daemon.

---

### Post by dsf54y on 2011-11-04
I know this is an old thread, but there is a lot of old info about vnstat around. Spent quite some time trying to figure out why cron is not created automatically. It seems that latest version (1.10) is using daemon by default.
For up to date instructions check here [www.mysysadmintips.com]("http://www.mysysadmintips.com/index.php/servers-lin/161-install-network-traffic-monitoring-utility-vnstat-on-ubuntu-server")

---

