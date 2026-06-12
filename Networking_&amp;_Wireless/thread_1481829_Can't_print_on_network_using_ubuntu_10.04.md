---
title: "Can't print on network using ubuntu 10.04"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by AryaYawe1 on 2010-05-13
Hi
I Have a Laptop running Ubuntu 10.04, and i cannot seem to find the printer on the wireless network. I am connected to the network via wireless router, and have been able to print in the past. The computer hosting the printer is an apple emac running 10.3.9, but this has not affected printing in the past. The macintosh is connected to the network as well.

Thanks

---

### Post by AryaYawe1 on 2010-05-17
bump

---

### Post by dkh503 on 2010-05-17
Same problem here. I have a Fujitsu laptop that worked flawlessly with a Brother HL2040 under the last three Ubuntu versions. It actually worked fine under Lucid until today. The printer icon is gone and it won't come back. I have researched the issue, and I have tried numerous 'fixes', including starting CUPS from a command prompt,updating CUPS, reinstalling CUPS, checking my /etc/init.d/network/interfaces file and running the "troubleshooter" which reports that it can't solve my problem and would I like to report a bug. I guess I would, but according to the bug reports I've encountered, this problem has been "solved" by one or more of the "fixes" which have all failed for me. My printer is on, the host is on (and actually logged onto), I can ping the host, and the printer shows up on the host computer as default and connected via usb. I have repeatedly gone thru the Server-Settings routine, and every time it reports that a printer cannot be found at the address, either by hostname or ip address.

---

### Post by coldbluesteel on 2010-05-17
I'm having a similar issue. CUPS is not starting when the PC is booting. I have to start it via:

sudo service cups start

every time I reboot.

It's annoying.

---

### Post by Morbius1 on 2010-05-17
If the problem is that CUPS has not started at boot then you might want to look first at the "solution" offered in the bug report:
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/500520](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/500520)

If that doesn't work you might want to add "service cups restart" to /etc/rc.local:

/etc/rc.local:
> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
[COLOR=Blue]
**service cups restart**[/COLOR]

exit 0Make sure it's before the "exit 0"

---

### Post by dkh503 on 2010-05-17
Well, I would do that, except it doesn't actually do anything. I guess I'll wait to see if 10.10 gives me wireless printing again.

---

### Post by coldbluesteel on 2010-05-17
I haven't had to reboot yet, but what I did so far is manually turn on cups at the terminal:

sudo service cups start

Then I went to:

System > Preferences > Startup Applications > Options

And clicked: Remember Currently Running Application

We shall see if that worked.

---

### Post by dkh503 on 2010-05-18
For me, this issue is reminiscent of Einstein's definition of insanity. There is nothing that seems to be returning my printing system to normal, and repeating the same steps and expecting different results is getting really old.

I just love when something that isn't broke gets 'fixed.'

---

### Post by dkh503 on 2010-05-19
Solved. Another one goes into the books as 'user error.' I was convinced, based on similar issues that others were having, that my problem was CUPS related. Then I noticed that I was suddenly having file sharing issues as well as issues with wireless printing.

I ended up reinstalling the latest versions of samba and smbfs, configuring samba as per the Ubuntu HOWTO (my samba has been so reliable over the last several years, thru all recent Ubuntu versions, I couldn't remember in detail how I even set it up), and all my problems went away, including the issues with wireless printing. 

So, if anyone is having issues with a previously working wireless printing issue under Lucid, and reloading and/or restarting CUPS isn't working for you, and you are using a samba network, you might try upgrading and/or reinstalling your samba stuff and see if that helps.

---

### Post by AugustinZ on 2010-05-26
Morbius1 thanks for your help. It really helped, actually, I've just used the command you specified to fix the problem (with sudo).

---

