---
title: "Why cant I access my webserver/owncloud with the external IP from inside my LAN?"
date: 2012-08-14
forum: Networking &amp; Wireless
---

### Post by CaptainMark on 2012-08-14
This isnt an Ubuntu question at all really but I came here because I know if someone here knows the answer they will be happy to help, (yay community spirit!)

Anyway I have set up owncloud running on my raspberrypi (which I'm still a complete noob with) I set up a dyndns account to manage my dynamic ip.  If I'm on a pc outside of my LAN I can point any web browser at myhomepc.dyndns.org/owncloud and get to the owncloud interface, the same happens if I use my current dynamic ip instead of 'myhomepc.dyndns' 

However if I am on my home pc I must use the local IP of the raspberrypi so I must use the url 192.168.1.4/owncloud to log in, I cant login to it using either of the previous two urls.

This may be common knowledge to you but this was a shock to me, (get to the point Mark....) Is there no way to get logged in to owncloud using the same url no matter whether I'm in my LAN or connecting from outside.  The reason I ask is I have owncloud set up on my nexus7 tablet which means I may be on my home Wifi or anywhere outside and its frustrating that the url I have to use to connect depends on where I am when I'm connecting. If it's not possible could anyone indulge me with a noob friendly explanation as to why not?

Also if my lack of knowledge in this area has caused me to use the wrong terminology and I confused the heck out of you, I'm sorry I'm still learning, please be patient with me.

---

### Post by papibe on 2012-08-14
Hi CaptainMark.

The ability to connect to a machine from your local network using its public name, or IP, is called **NAT loopback** (read about it [here]("http://opensimulator.org/wiki/NAT_Loopback_Routers")). Unfortunately most consumer routers don't supports it.

I would start by checking the detail router's documentation in the slim case it support it.

Another solution would be to hard-code the LAN name resolution of myhomepc.dyndns.org. That would be possible in case you are using a smart router (dd-wrt), or a local caching DNS  running locally, e.g., bind or dnsmasq.

I hope that helps. Let us know how it goes.
Regards.

---

### Post by CaptainMark on 2012-08-15
Thanks for the info. I didnt really understand any of those router features so I expect that means I don't have them, I'm only running a cheap router given by my ISP so I don't expect miracles with it. I didnt know I could make my own router from a linux pc. I might make that my next project,

---

