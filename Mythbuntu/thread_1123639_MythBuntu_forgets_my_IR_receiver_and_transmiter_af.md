---
title: "MythBuntu forgets my IR receiver and transmiter after every reboot"
date: 2009-04-12
forum: Mythbuntu
---

### Post by davidstoll on 2009-04-12
Every time I reboot, my remote stops working.  It's the newer MCE USB and it also does it with my Stream Zap, so it is not unique to the device.

Basically, to fix it, I have to go into the Myth Control Centre and change the IR transmit and IR receive device (which currently show as correct by the way) to anything else, apply that, and then change it back to what it originally was.

How can I make it stop this behavior?

---

### Post by superm1 on 2009-04-12
Is maybe the problem actually that LIRC isn't running after the reboot?  Maybe it's init script is failing for some reason or another.

Try /etc/init.d/lirc restart instead.

---

### Post by davidstoll on 2009-04-13
> **superm1 said:**
> Is maybe the problem actually that LIRC isn't running after the reboot?  Maybe it's init script is failing for some reason or another.

Try /etc/init.d/lirc restart instead.

Sorry it took me so long to get back to you.

Unfortunately, that did not help.  Any other suggestions?

---

### Post by superm1 on 2009-04-17
Well so inherently the final command called is just that command I gave you (which is why I directed you to it).  In order to call it, a complex maintainer script also gets called - /var/lib/dpkg/info/lirc.postinst

You won't be able to script the calls to lirc.postinst very well - and I wouldn't try as you can have some other not so good effects by running that at bootup.

The only other thing I can think of is the lirc udev file (/lib/udev/rules.d/85-lirc.rules in jaunty, it's somewhere in /etc in earlier).  Take it out of the picture..

---

### Post by davidstoll on 2009-04-17
> **superm1 said:**
> Well so inherently the final command called is just that command I gave you (which is why I directed you to it).  In order to call it, a complex maintainer script also gets called - /var/lib/dpkg/info/lirc.postinst

You won't be able to script the calls to lirc.postinst very well - and I wouldn't try as you can have some other not so good effects by running that at bootup.

The only other thing I can think of is the lirc udev file (/lib/udev/rules.d/85-lirc.rules in jaunty, it's somewhere in /etc in earlier).  Take it out of the picture..

So, just comment out the two lines in the file?

/etc/udev/rules.d/85-lirc.rules

```
ACTION=="add", KERNEL=="lirc[0-9]", RUN="/etc/init.d/lirc restart udev"
ACTION=="remove", KERNEL=="lirc[0-9]", RUN="/etc/init.d/lirc stop udev"
```

What would be the side effects of doing this?  If any?

---

### Post by superm1 on 2009-04-17
Changes whether lirc gets spawned on hotplug.  If there are bad complications from doing it, you can just undo the changes :)

---

### Post by davidstoll on 2009-04-17
> **superm1 said:**
> Changes whether lirc gets spawned on hotplug.  If there are bad complications from doing it, you can just undo the changes :)

Thank you superm1!  That did the trick.  After I commented out (#) those two lines, a reboot no longer causes my remote to stop working.

Now I just have to cross my fingers and hope that it doesn't have any side effects...but none so far.

my file was located at:
/etc/udev/rules.d/85-lirc.rules

Thanks again for your help.
David
:D

P.S.  I don't suppose you know how to mark a thread as solved.  I see some people have done it.  I renamed the title of my latest post as well as the first post (with other threads), but it doesn't seem to bring it up as [SOLVED] when a search is done.

---

### Post by davidstoll on 2009-04-17
Uh oh, another reboot and it stopped working again....had to go through the same steps to get it working again.... ;(

Any other ideas?

---

### Post by superm1 on 2009-04-17
Well now that's just getting bzr.  Anyway you can do your setup without the streamzap, and just use the mceusb?  maybe the combo of them is throwing things off

---

### Post by davidstoll on 2009-04-17
> **superm1 said:**
> Well now that's just getting bzr.  Anyway you can do your setup without the streamzap, and just use the mceusb?  maybe the combo of them is throwing things off

The Streamzap isn't even plugged in.  What I meant to say was that I've tried with the streamzap (only) and it does the same thing...but I like the MCE remote a little better, so that's the one that's usually plugged in.

---

### Post by jb5 on 2009-04-18
I'm seeing the same issue.

Jaunty; myth 0.21 (20403); Nova-T-500; (Both Myth & Jaunty all currently up-to-date).

Following a reboot - the remote will work for anything up to a couple of minutes, and then stop working.

Restarting lirc does NOT solve the problem.
A cold boot restores the remote to working order. 
It appears that the problem only occurs with reboots. ???

---

### Post by superm1 on 2009-04-18
jb5:
You are also using a mceusb2?

---

### Post by jb5 on 2009-04-18
Nope - using the remote with the nova-t-500, that's why I was wondering whether this was a more widespread issue.

---

### Post by davidstoll on 2009-04-19
> **jb5 said:**
> Nope - using the remote with the nova-t-500, that's why I was wondering whether this was a more widespread issue.

The same things happens for other remotes.  In other words, if I have another IR remote receiver plugged in (and only that one), it also won't work right after reboot.  I have to go through my little song and dance to get it working again.

It doesn't seem to be a problem with the devices.

---

### Post by andrewc6l on 2009-05-02
Add me to the list - I can ssh in, restart lirc, restart mythfrontend and then things are good until the next reboot. I'm using a Streamzap remote. lirc is running before then (I have a /dev/lircd and /dev/lirc0) but for some reason MythTV doesn't talk to it until I restart lirc and mythfrontend.

---

### Post by andrewc6l on 2009-07-24
I got sick of having to restart lirc every reboot, so I did the following:

1. Build an executable called restartlirc as follows:

```

#include <unistd.h>
#include <stdio.h>

int main(int argc, char* argv[]) {
	int ret;

	ret = setuid(geteuid());
	if(!ret) {
		fprintf(stderr, "error setting uid %d", ret);
	}

	ret = execl ("/bin/sh", "restartlirc", "/etc/init.d/lirc", "restart", (char*)0);

	if(!ret) {
		fprintf(stderr, "error invoking: %d", ret);
	}
}

```

2. Make restartlirc setuid and owned by root. (I put it in /usr/local/bin/.)

3. Change my /usr/bin/mythfrontend to do:
```

#!/bin/sh
# Mario Limonciello, March 2007
# partially merged with startmythtv.sh by Michael Haas, October 2007

# First, restart lirc and sleep so it has a chance to wake up
/usr/local/bin/restartlirc
/bin/sleep 1

#source our dialog functions
. /usr/share/mythtv/dialog_functions.sh

```
...

Finally, I don't need to mess about with restarting lirc manually.

---

