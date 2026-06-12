---
title: "Trouble with making bigpond cable work"
date: 2006-01-16
forum: Networking &amp; Wireless
---

### Post by mikemain on 2006-01-16
I have a motorolla SB4200 surfboard cable modem.  All is working fine through windows but in Ubuntu it only works sometimes and never for long.  It seems to only work when I connect through windows, then restart the computer and go to Ubuntu but it always drops out.  This is wierd because the connection terminates when I restart.

I know about the heartbeat thing and have installed bpalogin but it doesn't seem to have made a difference.  Can't figure out if I've installed bpalogin correctly. :???:

---

### Post by mips on 2006-01-17
Fom windows do a  ipconfig /all and post here.

Are you using ethernet ?

Do a search for bigpond on this forum, someone has probably had this problem before.

---

### Post by mikemain on 2006-01-17
Yes, I am using ethernet. It's most likely my inept setting up of bpalogin.  I assume the username and password it asks for are the ones for my bigpond account.  There are so many IP addresses or things that look like IP addresses that I don't know what goes where.

Ta.

Windows IP Configuration

        Host Name . . . . . . . . . . . . : test-75i6fapdv9
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : vic.bigpond.net.au

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : vic.bigpond.net.au
        Description . . . . . . . . . . . : ADMtek AN983 10/100 PCI Adapter
        Physical Address. . . . . . . . . : 00-0A-CD-01-7F-5E
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 203.45.56.183
        Subnet Mask . . . . . . . . . . . : 255.255.252.0
        Default Gateway . . . . . . . . . : 203.45.56.1
        DHCP Server . . . . . . . . . . . : 172.18.17.80
        DNS Servers . . . . . . . . . . . : 144.140.71.16
                                            144.140.70.15
                                            144.140.71.29
        Lease Obtained. . . . . . . . . . : Wednesday, 18 January 2006 2:10:54 P
M
        Lease Expires . . . . . . . . . . : Wednesday, 18 January 2006 8:10:54 P
M

---

### Post by mips on 2006-01-18
I assume you installed the bplogin 2.0.2-4 client via **synaptic** ?

I dunno what the username format is, contact bigbond for that. With adsl the username is usually   [email]username@domain.com.au[/email]  type format. From the bigpond website it looks like you only need a plain username & password.

This is a very nice aussie resource, [http://forums.whirlpool.net.au/](http://forums.whirlpool.net.au/)
More on bpalogin here, [http://bpalogin.sourceforge.net/index.php?page=index](http://bpalogin.sourceforge.net/index.php?page=index)

---

### Post by mikemain on 2006-01-19
I only learnt about synaptic after working out how to install it using command lines!!!!!!!!  That is a serious learning curve for me.

Thanks for your help, I got it working.  It wanted a different version of the username from the windows one (without the @bigpond.net.au as a suffix).  So simple it's hard.

---

### Post by mips on 2006-01-19
lol. Glad to hear you got it working.

---

