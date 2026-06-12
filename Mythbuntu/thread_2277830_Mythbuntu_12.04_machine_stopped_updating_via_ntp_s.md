---
title: "Mythbuntu 12.04 machine stopped updating via ntp servers??"
date: 2015-05-11
forum: Mythbuntu
---

### Post by neutron68 on 2015-05-11
I'm pretty sure my Mythbuntu 12.04 machine has been updating the time daily since I installed it, 2 years ago.
Following a power failure Sunday night, the clock was off by about 15 minutes, and ntp didn't correct it!

Are the ubuntu ntp servers down?

When I try and manually invoke the ntpdate script, I get an error that the ntp servers can't be used.

```
$ sudo ntpdate {0,1,2,3}.ubuntu.pool.ntp.org && date
11 May 19:26:55 ntpdate[4860]: no server suitable for synchronization found
```

```
$ sudo ntpdate
11 May 19:36:22 ntpdate[4881]: no servers can be used, exiting
```

The /etc/ntp.conf file has the default servers listed:
```
# Specify one or more NTP servers.

# Use servers from the NTP Pool Project. Approved by Ubuntu Technical Board
# on 2011-02-08 (LP: #104525). See http://www.pool.ntp.org/join.html for
# more information.
server 0.ubuntu.pool.ntp.org
```

---

### Post by ian-weisser on 2015-05-12
Those servers are up for me.
Can you ping the NTP servers?

---

### Post by neutron68 on 2015-05-12
Yes, I tried pinging the 0.ubuntu.pool.ntp.org server and got responses.

Maybe it's the current ntpdate application that's broken?

---

### Post by ian-weisser on 2015-05-12
The current ntpdate application in 15.04 works fine for me.
Is your connection, by chance, through a proxy or VPN?

---

### Post by neutron68 on 2015-05-12
> **ian-weisser said:**
> The current ntpdate application in 15.04 works fine for me.
Is your connection, by chance, through a proxy or VPN?
The Mythbuntu box is connected to the Net via a Linksys router running in NAT mode - no proxy or VPN connection.

In previous versions of Mythtv (0.21, 0.22) I used to have a cron.daily job that would call a script once per day which contained the line "ntpdate -u pool.ntp.org".  That worked great for keeping the time sync'ed up.
In the same system, I was able to invoke the ntpdate command from a command line and see successful time setting results.

I just found this page on ntp setting:
[http://askubuntu.com/questions/254826/how-to-force-a-clock-update-using-ntp](http://askubuntu.com/questions/254826/how-to-force-a-clock-update-using-ntp)

Respondants said you need to stop the ntp service before you manually invoke ntpdate from a command line.
I don't recall needing to do that in the past.

I just tried that and got the same error message from ntpdate:
```
eric@Mythbuntu:~$ sudo service ntp stop
 * Stopping NTP server ntpd                                                                                                          [ OK ]
eric@Mythbuntu:~$ sudo ntpdate 0.ubuntu.pool.ntp.org
12 May 11:24:03 ntpdate[6357]: no server suitable for synchronization found
```

Can you tell why ntpdate is giving an error?
Wrong default permissions with the /etc/ntp.conf file?
As is:  ```
-rw-r--r-- 1 root root 1974 May 11 20:44 ntp.conf
```

---

### Post by ian-weisser on 2015-05-12
> **neutron68 said:**
> Respondants said you need to stop the ntp service before you manually invoke ntpdate from a command line.
I don't recall needing to do that in the past.

They use the same port, so only one can be running at a time. If blocked, ntpdate will fail with exactly that 'no server suitable for synchronization found' error.
See [http://ubuntuforums.org/showthread.php?t=2193509](http://ubuntuforums.org/showthread.php?t=2193509) for a similar problem with that cause.

> **neutron68 said:**
> Can you tell why ntpdate is giving an error?
Unfortunately no. There are few possibilities: Bad .conf file, proxy or other network problem, something else using that port, corrupted application
You seem to have checked all of them.

> **neutron68 said:**
>  Wrong default permissions with the /etc/ntp.conf file?
-rw-r--r-- 1 root root 1974 May 11 20:44 ntp.conf
Hmm. That looks right, and matches mine.

---

### Post by neutron68 on 2015-05-12
From that askubuntu link I referenced above, I see there is an sntp command.

That command works on my system, so it's just the ntpdate command that is screwed up.

```
eric@Mythbuntu:/var/log$ sudo service ntp stop
 * Stopping NTP server ntpd        
eric@Mythbuntu:/var/log$ sudo sntp 0.ubuntu.pool.ntp.org
12 May 18:02:28 sntp[7026]: Started sntp
2015-05-12 18:02:29.392078 (+0600) -0.840145 +/- 0.073654 secs
2015-05-12 18:02:29.427015 (+0600) -0.846103 +/- 0.037491 secs
2015-05-12 18:02:29.502957 (+0600) -0.842505 +/- 0.032776 secs
2015-05-12 18:02:29.552343 (+0600) -0.840799 +/- 0.027481 secs
```

---

