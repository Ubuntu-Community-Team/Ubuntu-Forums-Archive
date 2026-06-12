---
title: "Use ubuntuserver as router?"
date: 2013-04-28
forum: Networking &amp; Wireless
---

### Post by malaTG on 2013-04-28
Hi everyone,

I have bought a apple tv 2 which I world like to stream content to from my ubuntu server (10.04). I have set it up wireless through my router but soon realised that I will nerver get the throughput that I need to make it work.

Now the apple tv and the server are not that far way from each other so my idea was to connect the apple tv to the ubuntu server via ethernet so that when streaming content from my server it will be smart enough to just take the content directly from the server without going through the router and if I access the internet from my apple tv 2 then it goes through the server to the router. So a couple of questions

1. Do you think this is the smartest way to solve the problem?

2. How do I do it? :-)

Thank you in advance!

Marcus

---

### Post by SirWeazel on 2013-04-28
Hey,

[COLOR=#000000]1. Do you think this is the smartest way to solve the problem?
- no.
[/COLOR]
Why do you think you don't have enough throughput? What kind of router do you have? You could always just hard wire to the router. I'm able to stream wifi without a problem to multiple devices. But my server is wired directly to my router. Is your server hard wired (my recommendation) or connected wirelessly to your router.  Even if wireless, i would think with a strong signal and a decent router then you should still be fine.

For future expansion (adding more devices and ect...) i would route everything through the router, and if it isn't too much trouble then even try to hard wire what you can.

---

### Post by 2F4U on 2013-04-28
> I have set it up wireless through my router but soon realised that I will nerver get the throughput that I need to make it work.


I guess the problem why you are getting not enough througput is the wireless setup. If possible, connect both Apple TV and Ubuntu server through a wired connection to the router. If you don't want to use cables there are alternatives such as homeplug/power line ([http://en.wikipedia.org/wiki/HomePlug](http://en.wikipedia.org/wiki/HomePlug)).

---

### Post by malaTG on 2013-04-28
> **SirWeazel said:**
> Hey,

[COLOR=#000000]1. Do you think this is the smartest way to solve the problem?
- no.
[/COLOR]
Why do you think you don't have enough throughput? What kind of router do you have? You could always just hard wire to the router. I'm able to stream wifi without a problem to multiple devices. But my server is wired directly to my router. Is your server hard wired (my recommendation) or connected wirelessly to your router.  Even if wireless, i would think with a strong signal and a decent router then you should still be fine.

For future expansion (adding more devices and ect...) i would route everything through the router, and if it isn't too much trouble then even try to hard wire what you can.

Hi,

Thank you for the input!

The router is far away from the server and I can't hardwire it. Regading the wireless I have big files to stream which I tried to stream yesterday and I wasn't even close. I mean is it that hard to just do it via cable?

Best regards

Marcus

---

### Post by malaTG on 2013-04-28
> **2F4U said:**
> I guess the problem why you are getting not enough througput is the wireless setup. If possible, connect both Apple TV and Ubuntu server through a wired connection to the router. If you don't want to use cables there are alternatives such as homeplug/power line ([http://en.wikipedia.org/wiki/HomePlug](http://en.wikipedia.org/wiki/HomePlug)).

Hi,

Yes you are totalt correct however because of physical constraints even for homeplugs :( (and also my wallet) I figured I might solve it in a cheaper and good enough way, something like.

Router
IP adress: 192.168.2.5

Apple tv
IP adress: 192.168.2.8
Gateway: 192.168.2.5 (ubuntu server ip adress)

Ubuntu server
IP adress: 192.168.2.5
Gateway: 192.168.2.1

Logic on ubuntu-server: If end adress equals "192.168.2.5" then "stop" here and do what is requested else send to "192.168.2.1" and the reverse if I want to access the apple tv 2 from any other device. Is this possible?

---

### Post by nachwaal3ab on 2013-04-28
[COLOR=#000000]Hi,[/COLOR]

[COLOR=#000000]Thank you for the input![/COLOR]

[COLOR=#000000]The router is far away from the server and I can't hardwire it. Regading the wireless I have big files to stream which I tried to stream yesterday and I wasn't even close. I mean is it that hard to just do it via cable?[/COLOR]

[COLOR=#000000]Best regards[/COLOR]

[COLOR=#000000]Marcus[/COLOR]

---

### Post by SeijiSensei on 2013-04-28
The best method would be to install another Ethernet card on the Linux box and connect the TV to that.  Give them both static IP addresses in a different subnet than the router's 192.168.2.0/24. Make sure the TV's default gateway is the Linux box. Now connections between the TV and the server will take place over the wire.  

If the TV needs to access other machines on your network, or access the Internet, you have to make a change in /etc/sysctl.conf (as root with sudo) to enable the kernel parameter "net.ipv4.ip_forward".  Set that to one as the file describes, then reboot.  You should now be able to ping both the server and the outside Internet from the TV.

However I'll just point out that I routinely stream video material from a server in my home using wifi.  I have no trouble with H.264 encodes at 720p or 1080p.  I'm using 802.11g (54 Ghz) by the way, too, not draft-N.

---

### Post by malaTG on 2013-05-04
Hi,

Thank you for the help!

Now it works perfect however I agree with you that the wireless should work so I will also give that another shot!

/Marcus

---

