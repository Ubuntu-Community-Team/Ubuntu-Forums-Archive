---
title: "Waiting for network configuration."
date: 2012-03-19
forum: Networking &amp; Wireless
---

### Post by snippyv on 2012-03-19
Hello.

I've tried 12.04 on a live USB and everything was fine...but when I have installed it I have wifi problems.

On boot I get...

1) Waiting for network configuration.
2) waiting up to 60 more seconds for network configuration.
3) Booting system without full network configuration.
4) I then log on.
5) The system shows my wifi router.
6) I click on it to log on.....and I get the message "Disconnected-you are now offline".

Can anyone offer any suggestions???

Why would the wifi work on the live usb and not the install? 

ps...I am using 12.04 instead of 11.10 as I had that black screen bug at log on when I tried 11.10.

Thanks.

---

### Post by snippyv on 2012-03-19
Just found this, but as Im a n00b it seems a little advanced for me! 

<><><><><><><><><><><><><><><><><><><><><><><><><>


@daemonrebel:

The following worked for me (borrowed from post #9):

You need to
(i) create directories /run and /run/lock,
(ii) move contents of /var/run into /run and /var/lock into /run/lock,
(iii) delete directories /var/run and /var/lock
(iv) create replacement simlinks; e.g. 'ln -s /run /var/run' and 'ln -s /run/lock /var/lock'

If you've never messed too much with Linux, it will be a little tricky. I booted w/o recovery console (it gets stuck in read only mode for me sometimes). Once you get to point where it's hanging and failing to boot further, hit ctrl-alt-F1. This will bring you to a virtual terminal. Log in as root or as a sudoer (you should be one). Attempt to move all the contents of the folders as described, like:

mkdir /run
mv /var/run/* /run]

etc.

If there is anything in these folders you cannot move or delete, it's possible it is a special mount point file. If rm <file> fails, try umount -fl <file> then attempt rm <file> again. After you move all of the contents, create the symlinks, reboot, and you should be okay.

---

### Post by snippyv on 2012-03-19
Just found this.....

[http://techspear.com/2011/10/solved-waiting-for-network-configuration-11-10-upgrade/](http://techspear.com/2011/10/solved-waiting-for-network-configuration-11-10-upgrade/)

I will have a go later and report back.

---

### Post by krishnamohan on 2012-06-30
[http://techspear.com/2011/10/solved-...11-10-upgrade/](http://techspear.com/2011/10/solved-...11-10-upgrade/)
 did not work for me..

I had the above problem as well as the problem of Network Manager not starting on startup after upgrade to 12.04...

What worked for me was the following (also see [http://www.codewhirl.com/2011/10/ubuntu-11-10-waiting-up-to-60-more-seconds-for-network-configuration/](http://www.codewhirl.com/2011/10/ubuntu-11-10-waiting-up-to-60-more-seconds-for-network-configuration/) )

Commenting out the following lines in /etc/network/interfaces fixed both problems for me..

```
auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet dhcp
```

---

### Post by brouhaha on 2012-08-26
> **krishnamohan said:**
> 
Commenting out the following lines in /etc/network/interfaces fixed both problems for me..


It seems different users have different code in /etc/network/interfaces file. It confused me a bit when I read similar posts that said, comment out XYZ, and I didn't have any XYZ in my file. 

So I'll simplify krishnamohan's comment. Just make sure that /etc/network/interfaces file contains only the following two lines:

```

auto lo
iface lo inet loopback

```

This worked for me, and I guess this is the net effect of krishnamohan's suggestion too.

Cheers!

---

