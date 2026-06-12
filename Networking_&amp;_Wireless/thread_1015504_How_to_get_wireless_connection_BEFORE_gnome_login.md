---
title: "How to get wireless connection BEFORE gnome login"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by scohar70 on 2008-12-18
[SIZE="4"][COLOR="Red"]THE PROBLEM:[/COLOR][/SIZE]

Greetings. 

I have searched the forums for this, but can't find any help.  Hopefully someone will know how to do this.

Here's what I'm trying to do:

I have several computers in my home (hostnames are cobra, raptor, rabbit and jaguar).  All are connected via a wireless network.  Wireless network is working fine.  

Jaguar serves as a file server for the whole house.  I have successfully mounted all my family members' home directories from jaguar, so that if they change files on any computer, it will update their main home directory on the main fileserver.  This way, they can use any computer and have consistent files and login settings.

I'm running Hardy 8.04 and Intrepid 8.10 on the various computers.  No problems with either OS.

My /etc/fstab looks a little like this:

```

# Home Dir Shares
#
# Purposefully not mounting scott home dir because main one is on my laptop
# and will need to roam if laptop goes on the road.  Cannot be server bound.
#
# Note, other logins will not work if laptop is taken on the road.
#
192.168.1.180:/home/share /home/share nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.1.180:/home/becky /home/becky nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.1.180:/home/luke  /home/luke nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.1.180:/home/eddie /home/eddie nfs rsize=8192,wsize=8192,timeo=14,intr
```

So all that works just fine.  My drives are mounting with NFS just great, and all the logins work as expected.  The home directories are nicely being served over the network via NFS.

Except not my laptop!  On the laptop, it does not establish the wireless connection until a user has first logged in and the pam-keyring stuff has happened and the network manager stuff has happened.  Only after this does the mount of the directories occur.

So the effect is that for users becky, eddie or luke, they have empty home dirs each time they log in.  If I log in first with my privileged account, it will of course establish wireless and mount everything, and their logins will be fine.  But I don't want to have to log in first each time the laptop is turned on.

So the simple question is:  **Can I force a wireless connection BEFORE anybody logs in through gnome?  If so, how?**

[SIZE="4"][COLOR="Red"]SOLUTION:[/COLOR][/SIZE]

The flakiness of Network Manager is why I was looking for a way to bypass Network Manager for a manual connection with wireless. NM works fine for me on a wire, but with wireless, it was a little trickier.

The most important line to make this work BEFORE login was the pre-up sleep 20 in the /etc/network/interfaces file. Apparently, the timing of the various daemons is such that the wireless stuff isn't ready right away, but this doesn't seem to slow down my boot-up or login process at all.

To make this work, you need to set NM to manual configuration and then edit your /etc/network/interfaces file for the network device you're trying to install.

Here is a snipet the /etc/network/interfaces file that worked for me:

Code:

```
# ath0 is my wireless card, yours may vary.
auto ath0
iface ath0 inet dhcp
pre-up sleep 20
wpa-passphrase *YOUR*PASSWORD*HERE*
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid *YOUR*SSID*HERE*

```
After you do this, you will have wireless up before any logins occur.

---

### Post by scohar70 on 2008-12-23
So, I figured out how to get this working, for anybody who cares.

You have to establish a manual configuration and then you have to put the network information in your /etc/network/interfaces file along with the statement pre-up sleep 20 at the top of the settings for your interface.

If anybody cares, I will post the file.

---

### Post by tbj61898 on 2009-01-08
Hello scohar70,
if you still remember what you did... well I CARE about that solution!

Thank you in advance!

Andrè :KS

---

### Post by scohar70 on 2009-01-08
I will post the files tonight when I get home.

---

### Post by netztier on 2009-01-08
> **scohar70 said:**
> 
So the simple question is:  **Can I force a wireless connection BEFORE anybody logs in through gnome?  If so, how?**

Configure the Wireless connection in NM normally. Then from NM-applet's right-button-menu, go to "Edit Connections", pick the one of interest and "edit" it. 

You'll find a checkbox "**System setting**". Activate this one, and it should get you going. 

At least in my case, it works perfectly with a wired connection that is only defined in NM, *not* in /etc/network/interfaces, and *with* NFS-mounted shares.

NM doesn't always play well with manual interventions in /etc/network/interfaces - the NM mailing list is full of discussion threads about it.


regards

Marc


On a side note: using boot-time mounted NFS shares is not what I'd do with a laptop. What if that laptop is away from it's home network? It'll constantly try to reconnect to your NFS server, at the office, at school, at <put-your-favourite-public-WiFi-Hotspot-here>. I for one don't see any need to waist system ressources for that. Rather use the on-demand features of "connect to server" in the places menu for that, and have it create a bookmark you can just click when you need it.

---

### Post by scohar70 on 2009-01-08
The flakiness of Network Manager is why I was looking for a way to bypass Network Manager for a manual connection with wireless.  NM works fine for me too on a wire, but with wireless, it was a little trickier.  

The most important line to make this work BEFORE login was the pre-up sleep 20.  Apparently, the timing of the various daemons is such that the wireless stuff isn't ready right away, but this doesn't seem to slow down my boot-up or login process at all.

To make this work, you need to set NM to manual configuration and then edit your /etc/network/interfaces file for the network device you're trying to install.

Here is a snipet the /etc/network/interfaces file that worked for me:

```

# ath0 is my wireless card, yours may vary.
auto ath0
iface ath0 inet dhcp
pre-up sleep 20
wpa-passphrase *YOUR*PASSWORD*HERE*
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid *YOUR*SSID*HERE*

```

After you do this, you will have wireless up before any logins occur.

---

### Post by tbj61898 on 2009-01-08
Thank you for your reply Scohar, You helped me a lot figuring it out. 

As usually happens my configuration ended up to be different from yours.

> **scohar70 said:**
> The flakiness of Network Manager is why I was looking for a way to bypass Network Manager for a manual connection with wireless.  NM works fine for me too on a wire, but with wireless, it was a little trickier.  

I definitely confirm that. NM do its wireless configuration job AFTER a user login.

I got a zd1211rw compatible wireless device and I just installed ubuntu 8.10. Here's what I did (with your help and a bit of googling).

- created /etc/wpa_supplicant.conf
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
network={
        ssid="MY SSID"
        proto=WPA
        pairwise=TKIP
        psk="MY PASSPHRASE"
        priority=1
}


-edited /etc/network/interfaces
auto wlan0
iface wlan0 inet dhcp
wpa-conf /etc/wpa_supplicant.conf

After these modifications I did a reboot and everything was just fine, wireless went up just after bootstrap, without requiring me to login anywhere. NM told me he had nothing to manage.

Next Steps, optional: 
- remove NM (because I don't use wired connections)
- encode passphrase in wpa_supplicant.conf (using wpa_passphrase)
- enable XCMDP (plenty of howtos online)

Speaking of that (but I'm not an expert), I suggest to You to encode your password too. Clear-passwords ain't good.

Hope this helps,
Andrè :popcorn:

---

### Post by wererogue on 2009-09-11
I've been looking for a way to do this for a while - I'll give it a try tonight.  Thanks for the writeup!

---

### Post by cjfarley on 2009-11-11
Thanks to everyone who contributed, this is great!  

I have a very specialized situation that I'm wondering if you can help with.  I work at a boarding school that is starting a Laptop program for all high school.  We are using Ubuntu 9.04.  The students will be using wireless 99.9% of the time.  We map drives, so I need the wireless up at boot, but I also need to kids to be able to take their laptop home (summers) and be able to use network manager (or a variant) to connect to other wireless without changing the default connection to the schools wireless.  To make is slightly more complicated the school's wireless uses Radius authentication.  

I have been able to setup the wireless in the way that your describing, but it seems to disable NM completely.  Any ideas or help would be greatly appreciated.

---

### Post by Czar on 2009-12-01
Thanks for the post.  I need wifi to load without nm/gnome so that xbmc-standalone connects.  Here's what worked for me

vi /etc/network/interfaces 

```

auto eth1
iface eth1 inet dhcp
pre-up sleep 20
wpa-passphrase *YOUR*PASSWORD*HERE*
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid *YOUR*SSID*HERE*

```

---

### Post by Hero of Time on 2009-12-21
You can also install WICD (replaces NM). It is a more user friendly tool for wpa_supplicant, it can  handle wireless just fine as well as wired. It starts it's daemon on boot, you have network on CLI too and it has a curses client in case you need to switch or change settings without a GUI. Of course, it has a GUI too. All written in python and quite fast. It has per SSID settings too, so if you have a laptop, you can set static for one SSID, while keeping DHCP for another. It can even run scripts upon connecting and disconnecting (mount and unmount NFS shares for example).

It's best to grab it from their own repo at [www.wicd.net](www.wicd.net), the one in the Ubuntu repo isn't updated that often.

---

