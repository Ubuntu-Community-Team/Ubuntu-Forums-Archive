---
title: "How to configure bridge when use  KVM vitual machine management on Unbuntu 11"
date: 2012-05-08
forum: Networking &amp; Wireless
---

### Post by camit on 2012-05-08
Hello every one.
Now, I want to deploy a Routing Lab on Ubuntu.
                    [COLOR=White]....................[/COLOR]-------------------------------------------------------------------------
                    [COLOR=White]..................... [/COLOR]|   Ubuntu 11[COLOR=White] ................................................................. [/COLOR][COLOR=White].........[/COLOR]                                                                |
                   [COLOR=White].....................[/COLOR]|[COLOR=White]..........[/COLOR]               -----------------[COLOR=White]....................[/COLOR]          ------------------[COLOR=White]................[/COLOR]       |
                   [COLOR=White].....................[/COLOR]|[COLOR=White]..........[/COLOR]               | [COLOR=White]....................[/COLOR]                        | [COLOR=White]...................[/COLOR]|                           [COLOR=White]....................[/COLOR]| [COLOR=White]................[/COLOR]      |
Internet-----|               |                         [COLOR=White]..........[/COLOR]|[COLOR=White]....................[/COLOR][COLOR=White]..[/COLOR]|[COLOR=White]...................[/COLOR]                           |[COLOR=White]....................[/COLOR]       |[COLOR=White]....................|[/COLOR]
                    [COLOR=White].....................[/COLOR]|              [COLOR=White]..........[/COLOR]|Ubuntu 11 [COLOR=White].....[/COLOR]|---------------|Ubuntu 11[COLOR=White].....[/COLOR]| [COLOR=White]................[/COLOR]     |
                   [COLOR=White].....................[/COLOR]|[COLOR=White]..........[/COLOR]               |  VM1[COLOR=White]............[/COLOR]                | [COLOR=White]...................[/COLOR]        |    VM2[COLOR=White].............[/COLOR]|[COLOR=White].................[/COLOR]      |
                   [COLOR=White].....................[/COLOR]|[COLOR=White]..........[/COLOR]               ------------------ [COLOR=White]..................[/COLOR][COLOR=White]..[/COLOR]----------------[COLOR=White]....................[/COLOR]|
                   [COLOR=White].....................[/COLOR]-------------------------------------------------------------------------

This topology, I have a Physical Machine, it is installed Ubuntu 11.
On this host, I install KVM, then create two virtual machines (VM1 and VM2).
I want VM2 connect to Internet via VM1.
I have a problem when I configure the bridge br0 to VM1 connect to Internet.

Please help me to solved this problem.
Thank you so much.

---

### Post by houstonbofh on 2012-06-13
You will need an additional nic for this.  It will not need to be connected to the LAN, but it will need to be seen as "Up."  You can then set up a second bridge br1, and it will be your internal network.  VM1 will need interfaces on br0 and br1 while vm2 will only need br1.  You may also be able to do this with the vibr interface, or create a virtual br1 without a nic...  I just know it works with a nic because I did it that way.

---

