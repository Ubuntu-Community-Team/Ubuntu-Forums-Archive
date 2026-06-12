---
title: "Instability on college dorm network."
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by dwnii on 2009-01-31
So I'm one of the very few students here at my university who are using ubuntu.  I had to take my laptop down to the direct connect department and get this kid to set it up to read the network, since there's no program for linux on campus. 

So he did some stuff in terminal, and now I'm connected to "auto eth0" and I can use the internet from my dorm room!

Except it's painfully slow.  Web pages time-out and youtube videos can take ten minutes to load, if at all.  I'm thinking this is some setting in Ubuntu that can be changed, since everyone on my floor using mac or pc can surf the web just fine.

So, any suggestions?

Thanks,

Dav

---

### Post by cariboo on 2009-01-31
Could you open a Applicatioons--Accessories--Terminal and type:

```
cat /etc/network/interfaces
```

and paste the output in your next post. Be sure to enclose the output using the [noparse]```

```[/noparse] tags.

Jim

---

### Post by ugm6hr on 2009-01-31
Do you have access to instructions on how to connect a Windows / Mac PC to the network.

Often, it's easiest to see those instructions to work out how the network works, and someone will probably be able to help from there.

It would also be helpful to know what was done by the direct connect "kid" in Terminal.

---

### Post by unixeducation on 2009-01-31
Sounds like you could be experiencing DNS issues. What's in your /etc/resolv.conf file? You may want to change it to reflect better DNS servers... just for testing purposes, you can try using the OpenDNS servers: 

208.67.222.222
208.67.220.220

---

### Post by MarblePanther on 2009-01-31
I agree ^^

To avoid having your settings revoked after reboots, or after periods of inactivity, do this:

    $ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
    $ sudo gedit /etc/dhcp3/dhclient.conf
    # append the following line to the document
    prepend domain-name-servers 208.67.222.222,208.67.220.220;
    # save and exit
    $ sudo ifdown eth0 && sudo ifup eth0 

You may be required to change eth0 to your own network device's name if it uses a non-standard name.

---

### Post by dwnii on 2009-01-31
```
auto lo
iface lo inet loopback
```

---

### Post by ugm6hr on 2009-02-01
> **unixeducation said:**
> Sounds like you could be experiencing DNS issues. 

Out of interest - while this sounds feasible, why would it affect only Ubuntu / Linux and not his Windows / Mac-using colleagues?

Do they have built-in alternative DNS settings that bypass your local DNS server?

---

### Post by ugm6hr on 2009-02-08
Did you get this fixed?

I have encountered a (possibly) similar situation, and have found scattered reports of routers refusing to play nice with Linux:
[http://ubuntuforums.org/showthread.php?t=1063064](http://ubuntuforums.org/showthread.php?t=1063064)

You never said what they did to get you connected in the first place either.

---

### Post by dwnii on 2009-02-08
As a matter of fact, the problem has SOMEWHAT fixed itself.  Suddenly, I was able to surf the net and watch youtube videos relatively reliably.  But it still goes in and out from time to time.  could this simply be the fact that it's a campus network that's experience a lot of traffic?

As far as what was done in the first place, as far as I know, he assigned an ip address to the laptop, and created a wired network profile called auto eth0.  

I think also that he enable DHCP (I have no idea what that is)

When he did all of that, the computer could see the network, (or vice versa?)

---

### Post by ugm6hr on 2009-02-09
DHCP is default on in Ubuntu (as it is in Windows) - so they prob did nothing on your laptop.

Perhaps the college router has MAC filtering, meaning each computer needs to be *allowed* to connect, and ip addresses are assigned by the router by MAC address.  Hence they had to *assign* an ip.

As for the intermittent issues - I would suggest trying OpenDNS:
[https://www.opendns.com/smb/start/device/ubuntu](https://www.opendns.com/smb/start/device/ubuntu) (as suggested earlier)

Of course, it may simply be that the network does not have the internet bandwidth at busy times, as you say.  No harm in using OpenDNS though.

---

