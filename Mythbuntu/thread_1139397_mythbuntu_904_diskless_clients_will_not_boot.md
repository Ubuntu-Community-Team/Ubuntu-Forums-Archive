---
title: "mythbuntu 904 diskless clients will not boot"
date: 2009-04-27
forum: Mythbuntu
---

### Post by map7 on 2009-04-27
I just installed mythbuntu 904 and went through the mythbuntu-control-center to install the diskless options.

I built my image, then tried to boot a PXE machine.  I've tried two PXE machines which I know worked with mythbuntu 810.

Here is the error I'm getting:

```
nbd0: Attempted send on closed socket
end request: I/O error, dev nbd0, sector 0
SQUASHFS error: sb_bread failed:Invalid argument
mount: Mounting /dev/nbd0 on /rofs failed: Invalid argument
```

How can I fix this? What am I doing wrong?

Here is my dhcpd.conf setup

```

# For MythTV Terminals
authoritative;
option domain-name-servers 192.168.200.1;
option broadcast-address 192.168.200.255;
option routers 192.168.200.1;
option root-path "/opt/ltsp/i386";

next-server 192.168.200.9;
if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
} else {
        filename "/ltsp/i386/nbi.img";
}

```

---

### Post by walterdf00 on 2009-05-25
Not sure if this will help you or not.  (I've been using this long weekend to stumble through the same issues.)

Here is the section of my dhcpd.conf for ltsp.  I am using i386.img instead of nbi.img.
```
next-server 192.168.123.100;
if substring( option vendor-class-identifier, 0, 9) = "PXEClient" {
  filename "/ltsp/i386/pxelinux.0";
} else {
  filename "/ltsp/i386/i386.img";
}
```If I look in /opt/ltsp/images I can see i386.img there.  I think that is what gets sent to the client.

Take this with a grain of salt, though.  I am having trouble getting the MCC for the client (that is running on the host, launched from the host's MCC) to actually make changes.

---

### Post by mal on 2009-05-27
A couple of comments that might help:

- I had trouble setting up the diskless server using MCC.  I found I had to manually install mythbuntu-diskless-server-standalone to get dhcp loaded.  In the end, I gave up using MCC and instead used the command line approach as per [ this thread]("https://help.ubuntu.com/community/MythTV/Install/Hardy/Diskless") (ignore the bit about downloading an updated version of the mythbuntu-diskless LTSP plugin).

- The reference to "/ltsp/i386/nbi.img" in /etc/ltsp/dhcpd.conf is relative to the location /var/lib/tftpboot/.  You won't find nbi.img in /opt/ltsp/i386/.  

- There is a bug that prevents the Jaunty diskless frontends from shutting down properly.  This is discussed [ this thread]("http://ubuntuforums.org/showthread.php?t=1157560").

Mal

---

