---
title: "Can't connect to anything."
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by cchase88 on 2009-04-19
Hey everyone, I'm having a strange problem with my desktop.

Last night I was able to connect to the internet fine, but when I tried signing on today, I found I was unable to do so.

I'm at a college where in order to use the internet you have to go through an authentication process that usually involved Cisco Clean Access Agent, but since I'm running Ubuntu, and the agent only works on Windows, I instead use a web based authentication process. I thought that maybe the problem was that the server for the web based authentication was down, or was being worked on, but when I tried connecting with my laptop that runs Ubuntu, I was successfully redirected to the web authentication form, and signed on.

I've tried resetting my IP address using the commands 
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0
```

which I saw was recommended to someone in a post that I read here on the forums who was having a similar problem. After running the commands nothing happened, and the problem still persisted.

I then decided to try and boot into the ubuntu live cd to see if the default configuration that gets loaded when it boots up would work. I was disappointed again when I got the same popup telling me that the network device had been disconnected.

After all of this I'm starting to think that it may be a hardware problem, but it seems strange that over night while my computer was off something like this would happen.

Anyone have any ideas or suggestions as to what I should try next?

Thanks,
cchase88

---

### Post by cchase88 on 2009-04-19
I just went to the Network Tools option in the Administration panel, and when I loop at the network devices, I have a loopback interface as well as the Ethernet Interface (eth0), however, the interface information for eth0 is not available. This is weird because in the network connections panel, I have Auto eth0 listed, in which it says it knows the MAC address.

Anyone know what's going on with this?

---

