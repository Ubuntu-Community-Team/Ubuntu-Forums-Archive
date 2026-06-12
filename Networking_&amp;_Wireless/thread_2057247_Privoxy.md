---
title: "Privoxy"
date: 2012-09-13
forum: Networking &amp; Wireless
---

### Post by Falc7 on 2012-09-13
I am following [this]("http://lifehacker.com/5763170/how-to-secure-and-encrypt-your-web-browsing-on-public-networks-with-hamachi-and-privoxy") guide

And I am stuck on the privoxy part. It was starting, until I changed the following.
In the config file

```
4.1. listen-address
#  ====================
#
#  Specifies:
#
#      The address and TCP port on which Privoxy will listen for
#      client requests.
#
#  Type of value:
#
#      [IP-Address]:Port
#
#      [Hostname]:Port
#
#  Default value:
#
#      127.0.0.1:8118
#
#  Effect if unset:
#
#      Bind to 127.0.0.1 (IPv4 localhost), port 8118. This is suitable
#      and recommended for home users who run Privoxy on the same
#      machine as their browser.
#
#  Notes:
#
#      You will need to configure your browser(s) to this proxy address
#      and port.
#
#      If you already have another service running on port 8118, or
#      if you want to serve requests from other machines (e.g. on your
#      local network) as well, you will need to override the default.
#
#      You can use this statement multiple times to make Privoxy listen
#      on more ports or more IP addresses. Suitable if your operating
#      system does not support sharing IPv6 and IPv4 protocols on the
#      same socket.
#
#      If a hostname is used instead of an IP address, Privoxy will
#      try to resolve it to an IP address and if there are multiple,
#      use the first one returned.
#
#      If the address for the hostname isn't already known on the
#      system (for example because it's in /etc/hostname), this may
#      result in DNS traffic.
#
#      If the specified address isn't available on the system, or if
#      the hostname can't be resolved, Privoxy will fail to start.
#
#      IPv6 addresses containing colons have to be quoted by
#      brackets. They can only be used if Privoxy has been compiled
#      with IPv6 support. If you aren't sure if your version supports
#      it, have a look at http://config.privoxy.org/ show-status.
#
#      Some operating systems will prefer IPv6 to IPv4 addresses even if
#      the system has no IPv6 connectivity which is usually not expected
#      by the user.  Some even rely on DNS to resolve localhost which
#      mean the "localhost" address used may not actually be local.
#
#      It is therefore recommended to explicitly configure the intended
#      IP address instead of relying on the operating system, unless
#      there's a strong reason not to.
#
#      If you leave out the address, Privoxy will bind to all IPv4
#      interfaces (addresses) on your machine and may become reachable
#      from the Internet and/ or the local network. Be aware that
#      some GNU/Linux distributions modify that behaviour without
#      updating the documentation. Check for non-standard patches if
#      your Privoxyversion behaves differently.
#
#      If you configure Privoxyto be reachable from the network,
#      consider using access control lists (ACL's, see below), and/or
#      a firewall.
#
#      If you open Privoxy to untrusted users, you will also
#      want to make sure that the following actions are disabled:
#      enable-edit-actions and enable-remote-toggle
#
#      With the exception noted above, listening on multiple addresses
#      is currently not supported by Privoxy directly. It can be done
#      on most operating systems by letting a packet filter redirect
#      request for certain addresses to Privoxy, though.
#
#  Example:
#
#      Suppose you are running Privoxy on a machine which has the
#      address 192.168.0.1 on your local private network (192.168.0.0)
#      and has another outside connection with a different address. You
#      want it to serve requests from inside only:
#
#        listen-address  192.168.0.1:8118
#
#      Suppose you are running Privoxy on an IPv6-capable machine and
#      you want it to listen on the IPv6 address of the loopback device:
#
#        listen-address [::1]:8118
#
listen-address  [COLOR="Red"]5.**.**.**[/COLOR]:8118
```

I changed the red part to match the IPv4 address reported by my haguichi client. However now when I go to start privoxy, it no longer starts as reported by system monitor.

---

