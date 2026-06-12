---
title: "initramfs ip network overrides /etc/network settings"
date: 2012-11-17
forum: Networking &amp; Wireless
---

### Post by nrohluap on 2012-11-17
Question on networking and initramfs interaction.

Installing Ubuntu 12.10 Server, 64 bit, on some new hardware. Working on using dropbear / ssh to remotely unlock LUKS volumes at boot.

The install is very basic at this point: an SSH server, apt-get update/upgrade complete, and a static IP address set for eth0 in /etc/network/interfaces.

After installing dropbear, initramfs starts networking on bootup. By default, it uses DHCP. It is also possible to set a static IP. That much I have working, and can remotely ssh in when the server starts and is waiting for the luks passphrase.

What I can't figure out, and haven't found a post anywhere that addresses this, is that once this process completes and the server continues to boot, the network remains somehow under "control" of initramfs. Boot process stops for several minutes "waiting for network configuration." Once it finally starts, any settings in /etc/network/interfaces are ignored. 

[LIST]
[*]service networking restart changes nothing.

[*]"ifdown eth0" says that eth0 is not configured.

[*]"ifup eth0" reports RTNETLINK answers: File exists. Failed to bring up eth0.

[*]/run/network has only the loopback entries. There are no longer entries for eth0 or the static network directory.
[/LIST]

Am I missing a script in the /scripts/init-bottom or local-bottom where dropbear shuts down? Or is this expected when initramfs uses the network at boot?

---

### Post by tdussa on 2012-11-17
Hi,

it should be sufficient to add a script to local-bottom or init-bottom that takes down the network.  However, adding ```
pre-up ip adr flush dev eth0
``` to the proper stanza in **/etc/network/interfaces** is a neat workaround and does the trick.  The **ip** utility is not available in the initramfs without doing some magic, and I have not come around to try whether calling ```
ipconfig eth0 down
``` would also do the trick.  It well might.

BTW, I do think this is a regression in Ubuntu. I have been doing stuff very similar to what you are trying to do for some years now (since 10.04), and this problem has started bugging me after the upgrade to precise.

 HTH.

 Cheers, Toby.

---

### Post by nrohluap on 2012-11-19
I had the same thought on disabling eth0 directly using ifconfig.

It's not very generic (it is "assuming" that eth0 is the interface) but inserting that on a particular host should work.

I ran into a related issue today implementing this on a physical Dell server (so far I had been using virtual machines). Ubuntu 12.10 is doing something similar to what RHEL/Fedora 15+ does, in that it wants to rename eth0 to em1, p132p3 and similar "consistent" names. When udev tries to do that, it reports that "unable to rename, eth0 is busy" and leaves the interface eth0, meaning my interfaces file referencing em1 no longer works. Since udev is not processing /etc/networking/interfaces file yet, the "flush" directive has no effect. That leaves disabling/downing the interface on exit of the dropbear shell as a requirement.

There is no "down" equivalent of the configure_network utility in /usr/share/initramfs-tools/scripts/functions, but I think a script to find devices via /run/net-*.conf could be used to bring down any configured devices.

 - Paul

---

### Post by nrohluap on 2012-11-20
> **nrohluap said:**
> 
There is no "down" equivalent of the configure_network utility in /usr/share/initramfs-tools/scripts/functions, but I think a script to find devices via /run/net-*.conf could be used to bring down any configured devices.

Something akin to this:
```

log_begin_msg "Shutting down network"
for device_conf in `ls /run/*.conf`
do
  filename=$(basename "$device_conf" .conf)
  device=${filename#net-}
  _log_msg "   downing  $device ..."
  ifconfig $device down
done

```

However, having tested simply ```
ifconfig eth0 down
``` while it does down the connection (the unlock ssh session terminates), it still leaves the device "busy" and udev fails to rename and the "pre-up flush" statement is still required.

---

### Post by wiz561 on 2012-12-29
I'm running into this same problem and trying to find the solution.  Would you be kind enough to explain where the location of these files should exist?

Thanks!

---

### Post by sam73 on 2013-05-20
hi all i am using this script and i've added       #     IFACES=\$(ip a|egrep "^[0-9]*: "|egrep -v "^[0-9]*: lo:"|awk '{print \$2}'|sed 's/:$//g')     for IFACE in \$IFACES; do        ip a flush \$IFACE     done     #  to solve this network issue  cat /etc/initramfs-tools/hooks/unlockroot  #!/bin/sh  PREREQ="dropbear"  prereqs() {     echo "$PREREQ" }  case "$1" in     prereqs)         prereqs         exit 0     ;; esac  . "$CONFDIR/initramfs.conf" #. /usr/share/initramfs-tools/hook-functions  if [ "$DROPBEAR" != "n" ] && [ -r "/etc/crypttab" ] ; then     # fix for dropbear in Ubuntu 12.04 x86_64     [ -d /lib/x86_64-linux-gnu ] && \cp -a /lib/x86_64-linux-gnu/libnss_* "$DESTDIR/lib/"      mkdir -m 755 -p "$DESTDIR/lib/unlock"  ##### /bin/unlock cat > "${DESTDIR}/bin/unlock"

---

