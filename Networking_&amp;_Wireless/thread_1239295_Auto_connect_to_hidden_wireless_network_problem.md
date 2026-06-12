---
title: "Auto connect to hidden wireless network problem"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by ciaopaulo on 2009-08-13
Hi all,

First off I'm a complete Ubuntu/Linux noob. I've used linux systems before at work, but we've always had sysadmins to sort stuff out. I've installed Ubuntu alongside XP (at home) and after a few teething troubles all seems to be OK... so far :)

Anyway the reoccurring issue for me is with my hidden wireless network. I want it to auto connect everytime I login. At the moment it doesn't. Naturally the automatically connect box is ticked.

And in fact manual connect method doesn't work properly either. If I go into the "Connect to hidden wireless network" section and click my prepared network settings, the "OK" button is greyed out! (This is only immediately after login)

The only way to get it to work seems to be to delete the settings completely from "network connections" and then re enter the values.

Then when I go back to "Connect to hidden wireless network" I'll be prompted to enter the hexkey again, even though the hexkey has been provided, and is starred out. Click OK and the network connects.

What a drag! Is there a workaround/fix for this? Or am I doing something wrong?

Ta!

---

### Post by pbateman on 2009-08-25
I am having the same issue with my Thinkpad....hopefully it'll get fixed soon. I was reading on the Thinkpad forums some people saying that in Karmic Koala (alpha) the issue of connecting to hidden networks appears to be solved. Anyone can confirm?

---

### Post by ciaopaulo on 2009-08-28
Anyone help with this? It's still an issue...

---

### Post by Eric Qel-Droma on 2009-08-29
I'm having some similar issues with my very old Presario 2100.  I *can* connect when I do it manually (Connect to hidden-->Enter network name [it can't be chosen from a list]).  However, I cannot create a connection to this network that stays listed, I cannot make one that auto connects.

It's not the end of the world for me, but man, it's annoying.

---

### Post by ciaopaulo on 2009-08-29
Could it be because I'm still getting prompted for the wireless key when I go to connect to the hidden network.

It should already know what this key is, and it does, it's already there but "starred" out, but for some reason it's prompting me just to click on the OK button. Hmmf.

---

### Post by pbateman on 2009-08-31
Im still dealing with this as well....yesterday I changed my connection from a hidden to one that does broadcast the SSID but the same thing happened. It just sits there trying to connect doing nothing. 
Its  gotten so annoying the fact i have to fool around with it for about 10-15 minutes everytime i boot up before it finally connects that I find myself just booting into windows cos I know it connects right away then...

---

### Post by ciaopaulo on 2009-09-02
OK I found this supposed work around.

[https://answers.launchpad.net/ubuntu/+question/20490](https://answers.launchpad.net/ubuntu/+question/20490)

> Now open a terminal and write:
gksu gedit /etc/network/interfaces


 Replace the content of the file with the following:
 # The loopback network interface
auto lo
iface lo inet loopback
 auto eth2
#iface eth2 inet dhcp
 auto ath0
#iface ath0 inet dhcp
 # WLAN
allow-hotplug wlan0
auto wlan0
iface wlan0 inet dhcp
 wireless-essid [replace this with your network name!]
 wireless-key [replace this with your wep key (hex!)]


which unfortunately doesn't work for me.

The work around I'm using now is to set my SSID to broadcast (ie no longer hidden). I'd rather I didn't have to do this though.

Also raised on this forum [here]("http://ubuntuforums.org/showthread.php?t=555641").

A similar sounding issue was fixed under Hardy 8.04 ... [here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/50214").
And the same is confirmed under Jaunty [here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/295796"). 

(it's classed as triaged, but mine is still losing blood!)

---

### Post by pbateman on 2009-09-02
That is exactly what i ended up having to do as well....set my router to broadcast the ssid. Everything is working ok now, altough again I rather not have done that.

---

### Post by Cavin on 2010-07-23
This happens to me as well on my MacBook Pro 5,1 on Ubuntu 10.04. 

ALSO this happens on Ubuntu 10.04 PowerPC on my old iBook.

My mom's computer, however, is a Dell Mini 10n, running Ubuntu Netbook Edition 10.04. I haven't heard her complain to me about anything like this happening for her. I'll ask her to be sure she just hasn't been inputing the network over and over again, but I doubt she has.

The reason my network is hidden at all is because the iBook doesn't support WPA, and my router (a Time Capsule) doesn't support WEP. So I just made it an unsecured hidden network.

---

### Post by Marctwo on 2010-07-23
I new to Ubuntu myself too so I'm no expert here... But I had a similar problem.

For me, creating a new connection from scratch didn't do it right.  I ended up setting a few things in the terminal before I could automatically create a new connection that worked.  It may work just as well (if not better) if you broadcast your SSID to connect for the first time.  This will create a new auto connection for that connection.  You can then hide your SSID again and edit the new connection as you require.

If you want your connection ready at boot, select the 'make this connection available to all users' aswell as

---

### Post by wisnoskij on 2010-11-22
Have the same issue with Ubuntu 10.10 netbook on my lenovo X61.
I had it auto connect once right at startup, and it seems to eventually auto connect but after a long time in most cases.

---

### Post by UnCola on 2010-12-31
> **Marctwo said:**
> 
If you want your connection ready at boot, select the 'make this connection available to all users' aswell as

This does not work for me.

I upgraded from 8.4 to 10.4 and the ONLY way I can get a connection is to got to > Connect to Hidden Network, then click on the network.  

No permutation of settings has ever managed to enable an automatic connection for me.  Very poor, as the automatic connection worked fine for me in all previous versions of Ubuntu, even when rebooting from Hibernate.

Now if I reboot from Hibernate it takes me a full 9 clicks to connect - I have to disable Wireless, re-enable it, then go through  the whole Connect to Hidden Network routine again.

Can this be fixed?

I have looked extensively for solutions and found none.   Wireless is one of the worst, and worst explained, features in Ubuntu - this is why I only want the LTS versions.   Before every six months when I upgraded I found a new, totally unexplained interface for the wireless and would have to spend hours of trial and error trying to establish how it worked.
How on earth can I recommend this OS to anyone else if it is so unsure that they will be able to connect?  Canonical really need to think about this and provide instructions, not offload the problems onto frustrated users.

---

### Post by #Vader# on 2011-01-21
I had this same problem for a year.  After some tinkering the last few minutes I fixed mine.  I hope the following helps.

Laptop: ACER travelmate 4010, Ubuntu 10.10

In "Network Connections", "Wireless Tab", "Edit "your profile",  uncheck "Available to all users", but keep "Connect Automaticly"

This will disable that annoying "Passwords and Encryption Key" feature that keeps popping up after you manually
select "Connect to Hidden Wireless Networks.  Which by the way, you will not have to do since now this Networked profile belongs to your profile only.

Hope this helps bud

---

### Post by harrod on 2011-06-26
I also have had this problem for about a year. On our old ThinkPad laptop, the problem mysteriously eventually went away. On our new ThinkPad laptop (Ubuntu 11.04), the problem reared its ugly head again. The previous append here by #Vader# led me to what I believe is the solution. If so, this should be sufficient information for the developers to fix the obvious code bug. 

The basic trick here seems to be: (1) be connected to the desired hidden wireless network, (2) disable networking (keep Wireless enabled), edit and save the wireless information for the hidden wireless network, (3) enable networking. This scenario appears to take a program path that properly updates the desired status variable. 

(The commands "Enable Networking," "Enable Wireless," etc. referred to below are most easily invoked by clicking the diamond shaped wireless icon that appears on the top information bar of your Ubuntu screen or workspace.) 

Step 1 (activate hidden wireless network):
---------
Enable Networking
Enable Wireless
[Observe that the system does not automatically connect to the hidden wireless network.]
Connect to hidden wireless network
[The system connects to the hidden wireless network as a result of your explicit request.]

Step 2 (change state of "Available to all users"):
---------
Disable Networking (not Wireless) [click Enable Networking to remove check mark]
Edit Connections...
Wireless tab
Select the name of the wireless network for automatic connection
Edit...
If prompted, enter your password and click Authenticate.
Available to all users [click Available all users to change its state]
Save
Enable Networking
[If the system connects automatically and you're happy with the settings, you're done. Otherwise, repeat Step 2 up to two more times.]

---

