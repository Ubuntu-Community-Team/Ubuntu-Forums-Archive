---
title: "sshd does not start on ifup"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by Alexander Blackbird on 2009-11-28
I have openssh-server not starting on ifup.
eth0 has static ip via /etc/nerworking/interfaces
network-manager package is removed
I figured that the problem is with /etc/network/if-up.d/openssh-server file
it exits on these lines: (I checked by putting echo befiore and after)

if [ ! -f /var/run/sshd.pid ] ||  [ "$(ps -p "$(cat /var/run/sshd.pid)" -o comm=)" != sshd ]; then
    exit 0
fi

Commenting this lines solves the problem - sshd starts after reboot and after ifdown\ifup, but it seems kinda weird.

---

### Post by nixscripter on 2009-11-28
That's checking for a PID file, or that sshd is running already. If you are sure ssh isn't running, try seeing if there is a /var/run/sshd.pid file left over from a previous run, and remove it.

Commenting out the lines may make sshd start multiple times, and is probably not a good idea.

---

### Post by Lars Noodén on 2009-11-29
> **Alexander Blackbird said:**
> sshd starts after reboot and after ifdown\ifup, but it seems kinda weird.

Another way to see if sshd is running is to check using [pgrep](http://manpages.ubuntu.com/manpages/karmic/en/man1/pgrep.1.html)

```

# if root is not running a process named sshd, 
# then (re)start sshd
pgrep -u root sshd > /dev/null || /etc/init.d/ssh restart

```

Just because there is a pid file left over does not mean that sshd is still running.

---

### Post by Alexander Blackbird on 2009-11-30
Hopefully sshd will not start twice - as this script does restart, not start
but I totally agree that commenting those lines is not a good solution.

There is no file /var/run/sshd.pid, and such problem is not on the one machine, but on quite many (I have a computer class in  university)

---

