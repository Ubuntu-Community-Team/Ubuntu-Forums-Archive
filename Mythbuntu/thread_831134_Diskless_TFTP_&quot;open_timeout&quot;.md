---
title: "Diskless: TFTP &quot;open timeout&quot;"
date: 2008-06-16
forum: Mythbuntu
---

### Post by SilkBC on 2008-06-16
Hi There.

i am attempting to test out the diskless-server features of Mythbuntu, and have installed the "Diskless Server" and "DHCP Server" options in the Mythbuntu Control Center.

I have built the image and run dpkg-reconfigure on mythbuntu-diskless-server to make sure the appropriate directory is exported via NFS.  I see the i386.img file in '/opt/ltsp/images'.

I copied the dhcpd.conf file from '/usr/share/doc/ltsp-server/examples' and placed in '/etc/dhcp3'.  I also created a directory called "ltsp" and made a symlink to '/etc/dhcp3/dhcpd.conf' in there (I wasn't sure it was really needed, but I did it anyway; didn't see any harm)

Anyway, I am testing with my laptop, and it gets an IP address and such from my Mythbuntu server.  It then tries to boot via TFTP but eventually fails with 'PXE-E32 TFTP open timeout'.

The only change I made to the dhcpd.conf file was to tailor it to my network.  Here it is, in its entirety:

```

#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 10.215.1.0 netmask 255.255.255.0 {
    range 10.215.1.100 10.215.1.199;
    option domain-name "murrell-van.local";
    option domain-name-servers 10.215.1.1,10.215.1.254;
    option broadcast-address 10.215.1.255;
    option subnet-mask 255.255.255.0;
    option routers 10.215.1.254;
    #next-server 192.168.0.1;
    #get-lease-hostnames true;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}

```

Here is the relevent entry from my '/etc/inetd.conf' file:

```

2000               stream  tcp            nowait  nobody /usr/sbin/tcpd /usr/sbin/nbdrootd /opt/ltsp/images/i386.img

```

Is there a step I am missing?  Any light you might be able to shed on this would be appreciated.

Other than a DHCP acknowledgement between the Mythbuntu server and my laptop, there is nothing in my logs that I can see (I checked 'syslog' and 'messages')

Thanks, in advance.

-Alan

---

### Post by laga on 2008-06-16
Interesting.
What does ```
grep tftp /etc/inetd.conf
``` return?

---

### Post by SilkBC on 2008-06-17
> **laga said:**
> Interesting.
What does ```
grep tftp /etc/inetd.conf
``` return?

It returns:

```

tftp  dgram  udp  wait  root  /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /var/lib/tftpboot

```

---

### Post by SilkBC on 2008-06-17
I had to reboot my Mythbuntu server for a couple changes I made, and thought I would try this again.  I seem t be getting a different error now:

```

TFTP
PXE-T01: File not found
PXE-E3B: TFTP Error - File Not found
PXE-M0F: Exiting Intel PXE ROM

```

I am suspecting the first error I got may have been due to inetd not having been restarted after the tftp daemon got installed, but this one is a little more decriptive.  I had recalled from playing around with LTSP a long time ago that sometimes it wasn't looking for the files in '/var/lib/tftpboot' but rather in 'tftpboot', so I made a symlink from '/var/lib/tftpboot' to '/tftpboot', but that still gave me the same error.

I am still not getting anything in my logs ('syslog' and 'messages')

Ah, interestingly, when I actually look inside /tftpboot/ltsp there are no files!  There's the problem.  Any idea why no files got installed to there?  Where would I find them, or what package did not get installed?

-Alan

---

### Post by laga on 2008-06-17
How did you build the image? Using MCC?

---

### Post by SilkBC on 2008-06-17
> **laga said:**
> How did you build the image? Using MCC?

That is correct.  I waited until it finished, and assumed all was good.  Should I try building a new image?

-Alan

---

### Post by laga on 2008-06-17
There have been some bug fixes regarding image generation the latest MCC in hardy-proposed: [https://bugs.launchpad.net/ubuntu/+source/mythbuntu-control-centre/+bug/221921](https://bugs.launchpad.net/ubuntu/+source/mythbuntu-control-centre/+bug/221921)

Please grab the .deb from hardy-proposed and try again :) It's vital that there are files in /opt/ltsp/images/ and /var/lib/tftpboot/ltsp/

---

### Post by SilkBC on 2008-06-17
> **laga said:**
> There have been some bug fixes regarding image generation the latest MCC in hardy-proposed: [https://bugs.launchpad.net/ubuntu/+source/mythbuntu-control-centre/+bug/221921](https://bugs.launchpad.net/ubuntu/+source/mythbuntu-control-centre/+bug/221921)

Please grab the .deb from hardy-proposed and try again :) It's vital that there are files in /opt/ltsp/images/ and /var/lib/tftpboot/ltsp/

Thanks, I will try that when the "Launchpad" site comes back up (the page said it was down for maintenance)

In the meantime, I did delete the exostong image an create a new one, and the image itself gets created but nothing in '/var/lib/tftpboot/ltsp'.

I will let you know how I get on with the .deb from Hardy-proposed.

-Alan M.

---

### Post by SilkBC on 2008-06-19
OK, so I downloaded and installed the ~hardy2 version of MCC which I got form another thread, since I couldn't find any hardy-proposed repositories that had actual packages in them.

I rebuilt the i386 image and it still built find, but ther eis *still no pxelinux.0 file and the like in '/var/lib/tftpboot/ltsp/i386' (the directory is completely blank)

Any ideas why that directory is not getting populated at all?

Please advise.  Thanks! :-)

-Alan

---

### Post by laga on 2008-06-19
That's interesting. You don't have a kernel and friends in /var/lib/tftpboot/ltsp/ but the image in /opt/ltsp/images/ is there?

How big is the image? It should be around 400-500MB. Does /var/lib/tftpboot/ get populated if you run ```
sudo ltsp-update-kernels
```?

---

