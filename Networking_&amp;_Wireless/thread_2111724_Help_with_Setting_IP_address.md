---
title: "Help with Setting IP address"
date: 2013-02-02
forum: Networking &amp; Wireless
---

### Post by studio7 on 2013-02-02
Hello: I am hoping this forum can help me out. My IT person has gone on a months vacation and he updated my server/storage device as he was leaving as it had froze. It was set so that all computers mapped to it on an IP address of 192.168.2.100, but now it has automatically set it's IP to 192.168.2.12 and when I go into the System Admin for networking I can change things, but don't want to mess the whole thing up.

I have research online how to change it but everyone tells me to go to a command line and our is a icon based. We are using Unbuntu 8.10

I am not a networking person, but I can find my way around.

Your help would be greatly appreciated.

---

### Post by gerowen on 2013-02-02
I created this video to demonstrate how to assign static DNS servers, but the IP address is in the same place, and even though I'm using Unity in the video, the steps are the same for Gnome since they both use the Gnome Network Manager.

[http://youtu.be/xIOpfBooCvw](http://youtu.be/xIOpfBooCvw)

---

### Post by Bucky Ball on 2013-02-02
*Thread moved to **Networking & Wireless**.*

> **studio7 said:**
>  We are using Unbuntu 8.10



Welcome to the forums.

!!! 8.10??? If these machines are online you are vulnerable and are running a security risk. 8.10 reached end of life ages ago and hasn't had updates, most importantly security updates, since April 2010! Unsafe. If they're whirring away on a company LAN and not connecting with the outside world that is another story, but honestly, 8.10 is ancient (in techno time, that is) and the apps and everything else are old and well out of date.

Think it's time for a complete overhaul, but perhaps someone (sys admin?) has been putting off, and putting off, a consistent upgrade of all your production machines. As production machines, they should be running an LTS release anyway, which is exactly what the LTS releases are designed for; production machines and servers.

Anyway, on the local machine, right click the network icon> choose the connection you want to edit> IPv4 tab> change the gateway address to the router's new one; 192.168.2.12. That should at least get you out. If you're not the IT person, I wouldn't start changing things around on the main server/system/router. You may be digging yourself a deeper hole ...

As inferred, I would get those machines offline (WAN) ASAP personally.

---

### Post by SeijiSensei on 2013-02-02
I'm going to walk you through some steps that will require the terminal.  Don't worry, you can do it.  You'll need to log in with the username that your admin typically uses.

1)  From the main menu open the Terminal program.  You'll get a screen with a line ending in a dollar sign.  That is the "prompt".  You'll type commands after it.

2)  At the prompt, type this
```

cd /etc/network
sudo nano interfaces

```
You'll be asked for a password.  Enter the same password you used when you logged in.  If that doesn't work, post a message to that effect, and I'll give you some more help.

3)  This will open the "nano" text editor.  We'll use this to modify the file.  You'll notice that nano provides some useful help lines at the bottom.  When you see something like "^S" that means to hold down the Ctrl key and type "s".  Those keys are case-insensitive, so don't worry if it says "S".  You can type small "s", too.

4)  The top two lines should read:
```

auto lo
iface lo inet loopback

```
Leave those alone.  What we're going to modify is the "stanza"  that should begin with "auth eth0".  On Linux, "eth0" represents the primary "Ethernet" adapter, the one this is most likely connected to the rest of your network.  Delete any lines that immediately follow that (Ctrl-Y will delete a line), but if you see any other code that starts with "auto eth1" leave that and anything below it alone.  Also if you see a line in the eth0 stanza that starts with "gateway", leave that intact as well.

5)  Now use nano to add the following after "auto eth0":
```

iface eth0 inet static
address 192.168.2.100
netmask 255.255.255.0

```

If there was a "gateway" line, probably "gateway 192.168.2.1" then that line should follow the netmask entry above.  If the gateway entry has a different address like 192.168.1.254, use that instead.  When you are done it should look like this:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.100
netmask 255.255.255.0
gateway 192.168.2.1

[any other stuff that you left alone like "auto eth1".]

```

6) Now hold down Ctrl and type "X".  You'll be asked if you want to save the file before exiting.  Answer yes.

7) OK, acid test time.  Run these commands to reset the network:
```

sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start

```

Then type the command "ifconfig".  You'll see the address assigned to eth0.  Is it back to 192.168.2.100?  Now try "ping 192.168.2.1" or whatever address is assigned as the gateway?  Do you get a reply?  Finally try "ping 8.8.8.8" to see if you can contact a host on the Internet, in the case the Google DNS servers.

Don't be shy about asking for more help.  Being abandoned by an admin with a malfunctioning server is a lonely feeling.  Personally, I'd start looking for a new networking consultant for the reasons Bucky mentions.  Your admin should have upgraded your systems to a more recent release with long-term support months, even years ago.  The current version of Ubuntu with long term support is 12.04, which means it was released in April of 2012.  That's the release you should be running. It will be [supported]("https://wiki.ubuntu.com/Releases") through April of 2017.

---

### Post by studio7 on 2013-02-02
thanks for all your help! I should have mentioned it is not a "Server" just a stand alone computer he has configured to work as a Network storage device for our small office.

I appreciate the help. I will ask him about updating to the newest version as suggested.

Thanks!

---

### Post by studio7 on 2013-02-02
If I only have the first two stanzas #4 in your help
how do I get to auth eth0?

I tried the "next page" but nothing happened.

---

### Post by ahallubuntu on 2013-02-02
~

---

### Post by Bucky Ball on 2013-02-02
> **ahallubuntu said:**
> The helpful instructions above may unfortunately conflict with how your IT guy set up the server on your network and it could actually make things worse if it is setup differently.

+1. My sentiments exactly. Mr/Ms IT may arrive back to a dog's breakfast (as we say in Australia) and have some work getting things back to the way they want them.

---

### Post by steeldriver on 2013-02-02
It sounds like your `server` is using a (very early!) version of network-manager

I didn`t use that back in the day, but if it is similar to the current version you can go to ``Edit Connections`` and then select the active connection and edit the IPv4 settings to use a manual (static) address

[FWIW it appears there was a bug in that version which caused the connection to revert from static to DHCP on reboot - that may be what happened here]

Alternatively if you know your office's router login / password you may be able to fix it by setting a DHCP address reservation

---

### Post by SeijiSensei on 2013-02-03
> **studio7 said:**
> If I only have the first two stanzas #4 in your help
how do I get to auth eth0?

Then the address was not set originally in /etc/network/interfaces.  Just edit that file so it reads:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.100
netmask 255.255.255.0
gateway 192.168.2.1

```

Put a blank line between these sections.

The reason I thought you were talking about a server is because you wrote 
> It was set so that all computers mapped to it on an IP address of 192.168.2.100, but now it has automatically set it's IP to 192.168.2.12.

Even if you think of it as just another workstation, the fact that you all expect to connect to it over the network means it is providing some "server" functions as well.  (My guess is that it runs samba.)  Best practice would be to have dedicated server machines distinct from workstations, but best practice and actual practice are often not the same.  Also it is possible to configure samba so you wouldn't need to know the machine's IP address, just its name.  It can register itself via [WINS]("http://www.samba.org/samba/docs/using_samba/ch07.html") or by joining an Active Directory [domain]("http://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-samba-servers.html").  You might take that up with your IT person as well.

---

