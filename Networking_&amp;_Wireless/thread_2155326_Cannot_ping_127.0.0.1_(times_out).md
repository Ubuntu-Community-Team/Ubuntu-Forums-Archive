---
title: "Cannot ping 127.0.0.1 (times out)"
date: 2013-06-17
forum: Networking &amp; Wireless
---

### Post by malc659 on 2013-06-17
Although this question seems to pop up a lot, none of my searches solved it for me, so that is why I am posting this.

The problem for me was that "ping 127.0.0.1" was timing out and the clue is that the use of the numeric IP address eliminates any DNS issues, so you can forget about /etc/hosts, /etc/networks, /etc/nsswitch.conf, etc.

It turns out that installation of "pgl" creates a number of "iptables" rules and if you forget like me, you will probably only white-list your local network.

To fix the pgl situation in the recommended way (i.e. not issuing "iptables" commands yourself) and make the situation permanent,
edit "/etc/pgl/pglcmd.conf" and add the locahost network to WHITE_IP_IN and WHITE_IP_OUT:
            WHITE_IP_IN="192.168.254.0/24** 127.0.0.0/24**"
            WHITE_IP_OUT="192.168.254.0/24** 127.0.0.0/24**"
Then reboot, or restart the pgl service:
            sudo pglcmd restart
            sudo pglcmd show_config


Although the fix is to update the peer-guardian default white-list, listed below is a simple "iptables" save/edit/restore sequence that may assist someone with the same problem, but possibly a different cause:


_How to fix timeout of "ping 127.0.0.1" (re: "adb start-server" and "pgl"_


    Symptom:
        Tue Jun 18-11:54:25 2054$ ping -c 1 -W 3 localhost
        PING localhost (127.0.0.1) 56(84) bytes of data.
        --- localhost ping statistics ---
        1 packets transmitted, 0 received, 100% packet loss, time 0ms
    Solution:
        Check all firewalls (_do not rely on "ufw"/"gufw"_)
            1.  sudo iptables-save >iptables.txt
            2.  Edit "iptables.txt" and copy/paste/substitute "192.168.254.0/24" => "127.0.0.0/24":
                    -A pgl_fwd -s 127.0.0.0/24 -d 127.0.0.0/24 -j RETURN            **<-- Add this line**
                    -A pgl_fwd -s 192.168.254.0/24 -d 192.168.254.0/24 -j RETURN
                    ...
                    -A pgl_in -s 127.0.0.0/24 -j RETURN                             **<-- Add this line**
                    -A pgl_in -s 192.168.254.0/24 -j RETURN
                    ...
                    -A pgl_out -d 127.0.0.0/24 -j RETURN                            **<-- Add this line**
                    -A pgl_out -d 192.168.254.0/24 -j RETURN
                    ...
                    COMMIT
            3.  sudo iptables-restore <iptables.txt
        The localhost is now accessible
            Tue Jun 18-12:28:05 2074$ ping -c 1 -W 3 localhost
            PING localhost (127.0.0.1) 56(84) bytes of data.
            64 bytes from localhost (127.0.0.1): icmp_req=1 ttl=64 time=0.080 ms


            --- localhost ping statistics ---
            1 packets transmitted, 1 received, 0% packet loss, time 0ms
            rtt min/avg/max/mdev = 0.080/0.080/0.080/0.000 ms

I hope that this post is useful to others.

Basically if you cannot ping an absolute IP address, suspect firewalls and iptables.

---

