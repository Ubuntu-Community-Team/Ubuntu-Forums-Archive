---
title: "Change the default dhcp client"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by Michel Boaventura on 2011-06-01
Hello,

I want to use dhcpcd instead of dhclient on Ubuntu. The 'interfaces' man page say:

"The dhcp Method
This  method  may  be  used to obtain an address via DHCP with  any of the tools: dhclient, pump, udhcpc, dhcpcd. (They have been listed  in their order of precedence.)"

I can't find where to change this default order. I can uninstall dhcp3-client, but this will also remove ubuntu-minimal, which is not a good solution.

---

### Post by gmargo on 2011-06-02
The "precedence order" of dhcp clients is hard coded in the **/sbin/ifup** binary (from the **ifupdown** package), so the only convenient way to use **dhcpcd** is to remove all of the higher precedence choices.

Just go ahead and install the **dhcpcd** package.  The remove the **dhcp3-client** and **dhcp3-common** packages.  That will also remove the **ubuntu-minimal** package, but that's ok; it's just a "meta-package".

Then reboot.  Network should come up hopefully.  Run "ps" to see that dhcpcd-bin is running.  (I tested this on a Maverick virtual machine.)

Possible alternative: Instead of removing the **dhcp3-client** package, you could rename or change permissions on the /sbin/dhclient* binaries.

Update: Another alternative: Instead of using /etc/network/interfaces, let the NetworkManager take over.  It's configuration file allows a "dhcp=" option to specify either dhclient or dhcpcd.

---

### Post by Michel Boaventura on 2011-06-04
I've tried to use the "dhcp=" option on the networkmanager configuration, but it doesn't work. Seems like networkmanager doesn't works with dhcpcd version 3, the one present on ubuntu's repository: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=607956](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=607956)

I find out that the version 5 works, but you have to install the package dhcpcd5, which is not avaible on 10.04 (the one used on my work).

So I have to upgrade ubuntu to 10.10 at least in order to use it. It's a shame that I need to have all this work just to change a default dhcp cliend, isn't?

But, anyway, thank you for the reply!

---

