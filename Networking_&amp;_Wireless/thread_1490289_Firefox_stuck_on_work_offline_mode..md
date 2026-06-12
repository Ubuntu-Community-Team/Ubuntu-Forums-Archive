---
title: "Firefox stuck on work offline mode."
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by Linuxqueen on 2010-05-22
Hi,
I've got a Compaq Presario V2000 laptop with Ubuntu 10.04 LTS installed. Wired connection.
When I start firefox it comes up with the welcome to Ubutnu..........and when I search in google it comes up with "Offline mode. Firefox is currently in offline mode and can't browse the web.
"*Uncheck "Work offline" in the file menu, then try again."
I Uncheck it and press try again but it comes up with "server not found............"
There is a icon in the top panel and when I hover over it, it says "No network connection."
I have rung up my internet server and asked what the prob was but he said it was my computer.
I've got two other computers connected to the same modem and they all work.
It was working until a couple of days ago, and I can't remember changing anything.
The computer won't connect to the internet so I can't check Thunderbird or install anything.

Thanks to anyone that can help.

Groove on:guitar:

---

### Post by djchandler on 2010-05-22
We need more information about your internet connection.

Are you connecting through your ethernet (wired ore wireless) to a broadband device, either DSL (ADSL) or cable?
If so, do you share this connection through a router?
Or are you actually using a real modem with an analog phone line connected through the serial port?

And watch this thread if your connection is through your network adapter.

[http://ubuntuforums.org/showthread.php?t=1488013](http://ubuntuforums.org/showthread.php?t=1488013)

---

### Post by kibbles2 on 2010-09-13
I am now having the same problem.  System worked fine and then I shut down.
 
I shut down differently this time.  I logged out and then chose HIBERNATE as opposed to SHUT DOWN like I normally do.
 
When I fired up the system again, the screen did not come up and I held the power button down (10.04 bug I thougt I had fixed) to shut down and reboot.  I did this as I had no video and couldn't see a mouse cursor or menu.  Not sure what choice I had.
 
The system seemed to come up normally when I hit the power button again but when I fired up Firefox it says:  Off line and then when I check on line, Server not found.
 
I am hoping this is an easy fix but I am a bit of a noob at Ubuntu.  Great when it works.
 
I guess I could reinstall but then I lose all my files and updates.  
 
Anyone have a better update on this issue?
 
Thanks

---

### Post by BkkBonanza on 2010-09-13
Click the NetworkManager icon (menu bar top right) and check if it says you have a connection. Try to manually connect. If you still cannot get a connection then open a terminal (Application, Accessories, Terminal) and type **ifconfig** <enter> and post result here.

---

### Post by gotchanisa on 2010-09-18
Hi,

I'm facing a similar problem. I tried a few steps ([http://ubuntuforums.org/showpost.php?p=9859817&postcount=12)and](http://ubuntuforums.org/showpost.php?p=9859817&postcount=12)and) it now connects for the first time, but the second page onwards it goes into an offline mode. I use a wired connection that is connected to a router. The other computers are windows and connect with no issues to the net. Initially I was able to ping any website but now I am not.
The ifconfig gives me the following

etho0 Link encap:Ethernet HWaddr 00:14:c5:47:6b
      inet6 addr: fe80::214ff:fec5:476b/64 Scope:Link
      UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
      RX packets:451 errors:2 dropped:0 overruns:0 frame:15
      TX packets:404 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000
      RX bytes:324116 (324.1 KB) TX bytes:55282 (55.2KB)
      Interrupt:16

lo    Link encap:Local Loopback
      inet addr:127.0.0.1 Mask.255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING MTU:16436 Metric:1
      RX packets:648 errors:0 dropped:0 overruns:0 frame:0
      TX packets:648 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0
RX bytes:49648 (49.6 KB) TX bytes:49648 (49.6)

Whew....! That was some typing I had to do. Please bear with me, I'm new to Ubuntu (10.04). Help! 
I was able to install all the updates required. Just not able to browse now. I also get an error when I try to use the synaptic package manager. Some message about not being able to fetch some address.

---

### Post by BkkBonanza on 2010-09-18
That indicates that eth0 doesn't have a valid ipv4 address (which it does need). I hope you didn't type that all in by hand...

In terminal mark text with mouse, then Ctrl-Shift-C. Back in forum window Ctrl-V to paste. The normal Ctrl-C, Ctrl-V doesn't work in the terminal because it needs to handle the more traditional control codes (why? I don't know).

As for why you have no address assigned to eth0 - not sure yet. Normally Network Manager would handle setting up the connection for you using DHCP with your router. So you would need to check each part of that. Start with cable and make sure it's still correctly connected. Then make sure that dhclient is running with a command like this,

ps ax |grep dhclient

which should list a line showing that it is running. This program will talk with your router to assign an address to your system. Network Manager may be having some problem and if "disconnecting" and "connecting" again from the menu icon doesn't work then you could try a manual method.

sudo ifconfig eth0 down

sudo ifconfig eth0 up

If none of that helps then post output of,

cat /etc/network/interfaces

in case something is wrong with the config.

---

### Post by gotchanisa on 2010-09-18
Thanks for the reply!

Since I get only intermittent connection on the laptop (on which I have loaded 10.04) I am accessing this forum on the windows desktop. Thus I have to type out the entire message :(

I tried both steps and was connected for a while. But I'm back to offline mode again. The strange thing is that the Network connection has a red exclamation mark that says No network connection! I haven't made any changes to the cable. The same cable if used with another laptop (windows) works fine. Strange!

I just restarted the system and now there is no exclamation mark or message. I even installed a Beta of Skype.

Anyway the response to cat /etc/network/interfaces
is 

auto lo
iface lo inet loopback

Now that you mention IPv4.... what is the default setting when we edit connections, go to wired and click IPv4 Settings? I remember following another thread that instructed me to add a DNS server to it. Can't find the thread now.

So the final story as of now - seems like I am connected. I'll update this thread in case I face the same issue again.

Thanks for your help and for bearing with my 'rants':)

---

### Post by BkkBonanza on 2010-09-19
Your /etc/network/interfaces looks normal. IPv4 setting is usually handled by dhclient and so there would be an IP address. If for some reason dhclient cannot negotiate the DHCP request with your router then the IP would be left unset, and the connection not useable.

Hopefully it was a temporary problem and will continue to work.

---

