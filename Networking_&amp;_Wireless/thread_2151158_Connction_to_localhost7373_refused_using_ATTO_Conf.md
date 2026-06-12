---
title: "Connction to localhost:7373 refused using ATTO ConfigTool v4.1"
date: 2013-06-03
forum: Networking &amp; Wireless
---

### Post by sweinberger on 2013-06-03
I am battling a connection refused to localhost for a few days.

I installed ATTO ConfigTool (used with their RAID controllers) v4.1 on the latest Ubunto. I ran all the updates. The ATTO Config Tool works great when connecting to other computers on the network, but refuses to connect to local host.

If I say Networking | Find Host, and enter "localhost" (or 127.0.0.1) and use port 7373 (the default that ATTO places in the Agent Port textbox field and press the find button, then I get:

*The connection to ':7373'' refused. Please make sure the agent is running on that port, and that the port is not being blocked by the remove machine's firewall.*

Everything is on the local machine and I just have the default installation of Ubunto with all the updates, the ATTO R608 driver, and the ATTO Configuration Tool v4.1 installed, nothing else, and everything default settings.

The service is fine and the driver installed nicely, so the problem is something to do with Ubunto Linux:

Thoughts?

---

### Post by sweinberger on 2013-06-05
I tried a promising route yesterday, namely to use the method outlined in

 [http://www.upubuntu.com/2012/01/how-to-open-specific-port-under-ubuntu.html](http://www.upubuntu.com/2012/01/how-to-open-specific-port-under-ubuntu.html)

to no avail. The suggestion was to:

Open the terminal (Ctrl+Alt+T) and run this command (root privileges is required):
[B]sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport [COLOR=#CC0000]8289 [/COLOR]-j ACCEPT
[/B]
That did not work. 

I finally heard back from ATTO technical support. We had gone back and forth a few rounds over the past however many days. They finally said that there is a problem and recommended the command line options as a workaround, but did not say exactly what the problem is with the GUI and why it cannot connect. I asked that specific question in my reply, so we shall see what they say.

Here is ATTO's response:

There "is a known issue with Ubuntu and our ATTO Config Tool.

We do however have a work around. When you were installing the Config Tool there should have been some questions about where you would like to install the CLI. The CLI is our command line interface used for all of our ATTO card. Normally this can be found in the /usr/local/sbin folder and a program called atraidcli.

From here you can do the same features that you would if you were using the GUI."

---

