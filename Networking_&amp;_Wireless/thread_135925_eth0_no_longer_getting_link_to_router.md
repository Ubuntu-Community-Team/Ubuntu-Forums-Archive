---
title: "eth0 no longer getting link to router"
date: 2006-02-24
forum: Networking &amp; Wireless
---

### Post by bikeboy on 2006-02-24
I have had a server running Breezy for a few weeks now with absolutely no issues. It's not doing anything important yet and I'm just playing around to see what I can do with it. I was having a look at PCLinuxOS livecd on there yesterday (wasn't thinking of using it as a server) just to see what it's like.

I configured the network from there just fine and got onto the internet, so decided I would try ssh into it from my Breezy desktop. Managed to get openssh-server to install. I set the computer up with the same IP address as usual so when I ssh'd in it warned me that I might be part of a "man in the middle attack" (i think that's what it said) because the encryption key was different. I thought ok, I will change the IP so it's one I haven't used before. Worked.

Now to the problem, since then I haven't been able to get the network up when I boot off the HDD into Breezy. Tried many things. The /etc/network/interfaces file appears unchanged.  ipconfig comes up and shows an IP address, but no data sent or received. My router ARP table doesn't show the computer as being connected, I turned off all the firewall, MAC filtering etc. Still no good.

From the sticky I tried, "sudo mii-tool eth0" and it comes up with "Operation not supported". There is no light on the port of the router it's connected to, or on the back of the ethernet port on the mobo itself. Despite all this, PCLinuxOS gets online if I boot it and config the network again!!!!

I have no idea what has changed, I didn't even mount the HDD under the livecd. Please give me suggestions on what else I could try.

Thanks

ps. sorry for the long post, just wanted to include as much background info as possible.

---

### Post by jamesr on 2006-02-24
When you connect with PCLinuxOS do the lights come on or not?

Is the Address used on the PC the same as the one in the Ubuntu setup?

---

### Post by bikeboy on 2006-02-24
Ok, to make it shorter, can someone tell me if there is a way to get back to the original ethernet config. ie. "sudo dpkg-reconfigure xxxx"

I'm not sure what to put there.

---

### Post by bikeboy on 2006-02-24
[QUOTE=jamesr]When you connect with PCLinuxOS do the lights come on or not?

Is the Address used on the PC the same as the one in the Ubuntu setup?[/QUOTE]

Yep, lights on the router and mobo are on in PCLinuxOS by the time I reach the login screen. It's an onboard Marvell Gigabit Eth controller if that matters. But like I said, it was working before so I know it's supported.

Yes, the address I have setup when it's running Ubuntu is 192.168.1.50. So I used the same address when booting the same machine in PCLinuxOS, but had to config that address once it had finished booting.

I have tried a different address in Ubuntu since but with no difference.

---

### Post by bikeboy on 2006-02-24
Ok this is weird, it's working. The only thing I did was boot into PCLinuxOS to the point of the login screen just to check whether the lights we on. Then I rebooted.

I had rebooted numerous times before, I had also gone into PCLinuxOS again too. I don't have any explanation, but it's working so yay!!!

Thanks Jamesr, in a roundabout way I think you got it working :)

---

