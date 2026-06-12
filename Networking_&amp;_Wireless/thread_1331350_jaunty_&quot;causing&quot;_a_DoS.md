---
title: "jaunty &quot;causing&quot; a DoS"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by carolinason on 2009-11-19
my Ubuntu version == Jaunty;

I'm using a shared belkin router for a wireless internet connection and sometimes my internal ip address will be in the security logs for example

```
Wed Nov 18 15:41:43 2009 1 Blocked by DoS protection 192.168.2.8 
```

This doesn't look good for "the linux user", especially one who can't give a specific answer.

Anyway, I thought perhaps it was avahi or maybe ipv6. 

I 'K'illed avahi and my ip hasn't appeared in the logs yet, but how does one kill ipv6 in jaunty. I found this thread [http://ubuntuforums.org/showpost.php?p=7059555&postcount=24](http://ubuntuforums.org/showpost.php?p=7059555&postcount=24), but setting [COLOR="RoyalBlue"]/proc/sys/net/ipv6/disable_ipv6 to TRUE[/COLOR] makes no sense from just looking at the directory. Any input to this whole question. thanks ahead of time.

---

### Post by Iowan on 2009-11-19
The link in my sig is getting a bit dated, but you can see if it'll help. 
(I'm keeping an eye out for more recent info)

---

### Post by carolinason on 2009-11-19
That's the way it was done before ipv6 'was put' inside the kernel.

Short of recompiling my kernel, I believe it's the kernel line in grub method, but wanted further input.

Thanks

[COLOR="SeaGreen"][COLOR="Green"]I like that name Iowan[/COLOR][/COLOR]

---

### Post by carolinason on 2009-11-19
[COLOR="Red"]EDIT** None of the below resolved the issue, but the DoS entries are far fewer. [/COLOR]

it "appears" that the avahi-deamon was causing the DoS security issue with the belkin router [COLOR="Red"]//EDIT// or some of the entries.[/COLOR] 

i stopped the avahi-deamon service by using the command
```
# /etc/init.d/avahi-daemon stop
```

and disabled the avahi-deamon permanently by using the command
```

# mv /etc/rc2.d/S50avahi-daemon /etc/rc2.d/K50avahi-daemon
```

i disabled ipv6(since i'm not using it anyway) by placing ipv6.disable=1 at the end of the kernel entry in [COLOR="Green"]/boot/grub/menu.lst[/COLOR] so it looked like this
```
kernel /boot/vmlinuz-2.6.28-16-generic root=UUID=eb56537c-9763-4cfd-98a7-db353df0885b ro quiet splash ipv6.disable=1
```

[COLOR="Red"]/* note: your uuid is going to be different and i prefer to su as root for system administration and not use sudo, since i feel comfortable doing so. */[/COLOR]

i had read that the kernel needed to be updated to a kernel in the debian repositories to use ipv6.disable=1, but as you can see i am using the stock kernel at the time of this writing.  very easy, just append the line with the kernel option!

i'll mark this as solved when i've given the log some time to 'listen' to my computer.

thanks, perhaps this will help someone.

---

