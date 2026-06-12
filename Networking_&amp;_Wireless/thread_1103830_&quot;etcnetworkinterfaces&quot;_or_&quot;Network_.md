---
title: "&quot;/etc/network/interfaces&quot; or &quot;Network Manager&quot; ?"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by Blou_Aap on 2009-03-23
My Wireless works fine using "Network Manager" on Intrepid Ibex.
But for some reason the only way I can get my "Wired" Connection to work is through the "/etc/network/interfaces" file.

See at home I connect to a Wireless Router to get my Net Connection (Using a gateway), then I use my Laptop at Work and there I use a "Wired Connection" where I use a ppp0 dial-up for my Net Connection there.

When I first Installed 8.10 it worked fine through the "Network Manager", but after some updates I was forced* to use "/etc/network/interfaces" to get my connection to work and the dsl dial-up I have to do the old way via "sudo pon dsl-provider" to do my dial-up. 
*Forced meaning nothing else worked to get me connected again through the "Network Manager".

Now when I go to LAN events, etc, I have to always tweak my 
"/etc/network/interfaces" file to change my settings. And because I LAN quite a lot this gets annoying fast. This was never a problem before.

Can any one maybe give me some Help on how to fix this little problem, please, or is there anyone that had a similar problem and sorted it out, that can Help me please?

Will really appreciate it, thank you.

---

### Post by netztier on 2009-03-23
> **Blou_Aap said:**
> *Forced meaning nothing else worked to get me connected again through the "Network Manager".


Did you try creating an additional "Wired" connection profile in NM that has a static configuration in it's IPv4 properties? The downside is: you might have to activate that profile manually after logging in.

I never had any issues with that, works like a charm, and I can leave /etc/network/interfaces perfectly untouched.

regards

Marc

---

### Post by Blou_Aap on 2009-03-23
[QUOTE=netztier]Did you try creating an additional "Wired" connection profile in NM that has a static configuration in it's IPv4 properties? The downside is: you might have to activate that profile manually after logging in.[/QUOTE]

Yes I tried that. But it just does nothing.
Can't ping anyone, and on "ifconfig -a" my eth0 did not display the correct
information.

But my "Wireless" connection [COLOR="Red"]DOES[/COLOR] work from the "Network Manager".

---

### Post by Blou_Aap on 2009-03-23
Ok actually this was an Easier Fix than what I have thought. :p

I just completely Deleted the "/etc/network/interfaces" file.
(After making a Back-up ofc.)

Then I went and set-up a Manual Connection, and Voila, It Worked :D

Maybe some Update fixed it again.

---

### Post by netztier on 2009-03-23
> **Blou_Aap said:**
> Yes I tried that. But it just does nothing.
Can't ping anyone, and on "ifconfig -a" my eth0 did not display the correct information.

Well, what *does* it display for eth0, then? Might be a hint at what is going on.

Only try this after removing any reference to eth0 from /etc/network/interfaces, and after rebooting the machine.

Once you have a wired profile with static IP, please try to **ping your default gateway** (or another host on the subnet) and then please show the outputs of:

```
ifconfig -a
netstat -nr
arp -na

```

There wouldn't be any firestarter or other firewall/internet connection sharing tools installed that would try to manage eth0, would there?

regards

Marc

---

