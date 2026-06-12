---
title: "NetworkManager taking the scenic route"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by yandman on 2010-05-06
Hi all,

On a very old laptop, I've just switched from xub to lub, and I must say it's a lot lot faster. There's just one really annoying problem (I have no idea if this is in any way related to LXDE or if it's just due to 10.04):

Network Manager only starts about a minute after the rest of the desktop. So my system boots up, I log in, see the applet, but it is greyed out (it tells me "Network Manager is disabled" or something similar). After a minute (approx), it suddenly comes to life and connects me.

Now, I *think *this only happens when I have:

A) set the wireless connection to "all users"
B) given an empty password for the keyring

But when I cancel either of the two above, it doesn't stop it from happening. I've tried updating etc.. to no avail. I've also tried wicd, but for some reason installing wicd from synaptic doesn't remove Network Manager? Very strange..

Anyway, has anyone seen behaviour like this? Any suggestions for first steps to take to see where it's blocking?

Cheers,
y.

---

### Post by phillw on 2010-05-06
Hmm, I've not come accross this one before.

Can you give the specifications of said laptop? (Processor, RAM, Hard Drive)

could you also paste the the top 5 lines from issuing ```
top
```

(press q to stop **top** running, you can then left click and hold it down, using your mouse to highlight those lines, once they are highlighted Shift + Ctrl + C will copy them, allowing you to use Ctrl + V to paste them here)

I'll subscribe to this thread & will do a bit of asking for you. We may be putting on a boot monitor programme, but I'll go through doing that if it is suggested that report will be of help.

Regards,

Phill.

---

### Post by yandman on 2010-05-07
Thanks Phill! It's one of the first Vaios, Pentium M (Centrino) 1.2Ghz-ish and 256mb RAM, ipw2100. Not sure about the hard drive. I'm running Lubuntu 10.04 Lucid.

I investigated a bit more last night, and the issue is more general than what I previously believed:

On accessing the desktop, there is a delay of about 2 minutes before I can do anything that needs "authentification". So I **can **run chromium, leafpad, abiword etc... I **can't** run NetworkManager, Synaptic GUI etc...

The most blatant way to show this behaviour is by launching a terminal as soon as I boot to desktop - I can tap away happily, but if I ever call sudo .... It freezes until the 2-minutes (very approx) have gone past, upon which it asks me for my password, and everything starts working again (at the same time networkmanager starts running, synaptic can be opened again).

I'll try running a "top" during and after this strange behaviour this lunchtime. I'll post the results as soon as I get them.

Again,
Thanks for helping me out here, it's slightly aggravating to have an OS that boots in 40s, and then to have to wait 2 minutes to be able to connect to wifi...

Y.

---

### Post by yandman on 2010-05-07
I've attached the results of two startups, before and after the "unlock" (which seems to be at 4 minutes?). The first is with the default ordering, the second with CPU time (L) ordering.

---

### Post by phillw on 2010-05-07
Hi, can you post the result of ```
 cat /var/log/auth.log |tail -n20
```

Regards,

Phill.

---

### Post by yandman on 2010-05-07
Every time the computer is booted, I get exactly the same first 7 lines. Here is an example where I type sudo su as soon as the desktop starts. You can see that the sudo line in auth.log only registers 3 minutes later!

May  6 20:31:08 y-laptop lxdm-binary: PAM unable to dlopen(/lib/security/pam_gnome_keyring.so): /lib/security/pam_gnome_keyring.so: cannot open shared object file: No such file or directory
May  6 20:31:08 y-laptop lxdm-binary: PAM adding faulty module: /lib/security/pam_gnome_keyring.so
May  6 20:31:08 y-laptop lxdm-binary: pam_succeed_if(lxdm:auth): requirement "user ingroup nopasswdlogin" not met by user "y"
May  6 20:31:08 y-laptop lxdm-binary: pam_unix(lxdm:session): session opened for user y by (uid=0)
May  6 20:31:12 y-laptop gnome-keyring-daemon[852]: couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files
May  6 20:31:12 y-laptop gnome-keyring-daemon[852]: couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files
May  6 20:31:14 y-laptop polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session1 (system bus name :1.8 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
May  6 20:34:55 y-laptop sudo:        y : TTY=unknown ; PWD=/home/y ; USER=root ; COMMAND=/usr/sbin/synaptic


What is strange is that there don't seem to be any traces at the 3/4-minute mark indicating something has started working?

---

### Post by phillw on 2010-05-07
hi, back again :-)
can you post the output of ```
 sudo -l
``` (That's a little L not the number one)

Regards,

Phill.

---

### Post by yandman on 2010-05-07
Already? :p

As I said earlier, sudo locks up until the 3-minute mark (before asking for the password). Once it finishes it gives:

------------------

y@y-laptop:~$ sudo -l
[sudo] password for y: 
Matching Defaults entries for y on this host:
    env_reset

User y may run the following commands on this host:
    (ALL) ALL

-----------------

Cheers,
Y

---

### Post by phillw on 2010-05-07
Hi, I'm struggling here. It's been recommended that you pop onto live help on the IRC

[http://webchat.freenode.net/?channels=ubuntu-beginners](http://webchat.freenode.net/?channels=ubuntu-beginners)

The above link will take you to the ubuntu-beginners channel, where they can ask to look at various parts of your system.

Regards,

Phill.

---

### Post by yandman on 2010-05-07
Thanks Phill, I'll see what they can do for me

---

### Post by yandman on 2010-05-08
I've noticed that you can either do the waiting before logging in or after, or half-and-half. All that matters is that you wait 4-ish minutes after booting. Very strange...

---

### Post by phillw on 2010-05-08
Hi,

it's a new day, so let's start with a quick check, to put my mind at ease. Did you run the checkCD option on the installation CD and did it report back that everything was okay?

As it is weekend you should be able to catch a couple of the lubuntu people in

[http://webchat.freenode.net/?channels=lubuntu](http://webchat.freenode.net/?channels=lubuntu)

It is a small team, so it may be a case of logging on and hanging around for a while (I'll be in there anyway), I can then see if one of the guys who was helping with your issue yesterday has some free time today.

Regards,

Phill.

---

### Post by yandman on 2010-05-08
Hi Phill,

I checked the iso (md5) and then the CD when burning it (bit by bit), but I didn't run the "verify CD" in the CD boot options, because I have heard that it generates incorrect errors for lubuntu. I'll go where you suggest, maybe someone there can illuminate us... 

Y

---

### Post by yandman on 2010-05-08
Good catch! It gives one error. A bit strange though, because the Nero check didn't give any errors. Have you tried running this on your CD/DVD? Can you confirm it should give 0 errors? If so, I'll go and buy some CD-Rs :)

Cheers,
Y.

---

### Post by ibuclaw on 2010-05-08
If you haven't reinstalled yet, I'd suggest you try looking at your /etc/hosts file.

```
cat /etc/hosts
```

You should see something along the lines of:
> 
127.0.0.1	localhost
127.0.1.1	y-laptop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


And if you don't correct it accordingly.

The problem is most likely a corrupt hosts file, as it will result in DNS lookup failing on your hostname. Which is what sudo, and many other network aware applications do whenever they start. ;)

---

### Post by yandman on 2010-05-08
**Bingo!**

Phill, I apologise for having led you on a wild goose chase, I'm an idiot for having forgotten this...

I use a PCMCIA card to get wifi with the laptop. Sounds normal so far. But wait a second: Didn't he say something about a Centrino? Indeed, but the internal wifi chip broke about 4 years ago. So since then I've been using an external adapter.

Ibu, when you pointed out that the state of the network devices could influence something as basic as "sudo", it all fell into place... I blacklisted ipw2100 (the centrino, not the external card), and Robert is now my uncle.

Guys, is there any way of tagging this thread as solved, and maybe adding some keywords in case it can help someone in the future? Ubuntu 10.04 Broken Centrino Blacklist ipw2100

Anyway, thanks a lot, I really appreciate the help the community has given me these last two days. I can now go back to using the fastest 1GHz laptop I have ever owned.

Cheers,
Y.

---

