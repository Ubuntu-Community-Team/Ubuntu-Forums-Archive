---
title: "WPA2 Static IP gives the right IP but NO internet connection"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by NertSkull on 2010-10-16
I don't know where to put this, or even what I'm looking for.

I've tried for 6 hours today to get my WPA2 wireless to work as a static IP on my laptop to no avail.  I've tried almost all the suggestions in [this]("http://ubuntuforums.org/showthread.php?t=202834") thread.

Basically I put things in correctly (at least according to that thread) but I get no interent.  When I restart I get the correct IP address but no internet pages will load.

The network monitor I have on my panel shows that it is trying to send and receive information, but I can not get my pages to load.

I'm desperately in need of help, but I really don't know how to even ask for it correctly.

But to start here is my interfaces file (one config of about 15 I've tried).

```

auto wlan0
iface wlan0 inet static
address 10.42.32.113
netmask 255.255.255.0
network 10.42.32.0
broadcast 10.42.32.255
gateway 10.42.32.1
wpa-driver wext
wpa-conf managed
wpa-ssid BDF_Net
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk c07270ac830b198dbb2161e66bffe367b1b0d7b0832c759ac32ab2c8b0afdd4c

```

I've tried CCMP TKIP together or just TKIP

I've tried WPA, WPA RSN, etc.

Nothing works for me.

My router is a linksys WRT54GS.  My wireless is set up as WPA2-Personal with the "algorithm" as TKIP+AES.

Its like it wants to connect and gives me an IP.  But I just don't get any real web data.

I've restarted and tried restarting just the network.

Anything else I can give to troubleshoot I'm happy to do.  Thanks all.

---

### Post by chili555 on 2010-10-16
Man! That's one busy, busy interfaces file. 

My router uses WPA2-PSK and AES. Here is my interfaces file, slightly disguised:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.254
wpa-ssid mylilrouter
wpa-psk uwishuknew
```I noticed this:> wpa-psk c07270ac830b198dbb2161e66bffe367b1b0d7b0832c759ac32ab2c8b0afdd4cIs that really your key, or some disguise of it; or some translation/encryption thing? The interfaces file needs the real, exact key.

If you set a static IP address, you are responsible for the DNS nameservers. Did you write /etc/resolv.conf? I suggest:```
nameserver 192.168.1.254
```Is the router pingable?

---

### Post by NertSkull on 2010-10-16
Allright well thats interesting.  Now I have two questions (a question and a problem)

Problem

I made my interfaces match more similar to yours and it now connects with the static IP.  But, its only intermittent.  It will connect, but then disconnect.  Then connect and disconnect.  I never get more then about 2 minutes of continual connection before it disconnects.  Then 4-10 minutes of no connection.  I can kind of jumpstart it (sometimes) if I manually restart the internet.

So clearly this is not going to work, I can't have the internet only work in 2 minute jumps.

Question

This is more to just understand.  Why does the thread mentioned above not use the key.  They make a big deal in the HOWTO that you need to use "wpa_passphrase <ssid> <wifi_password>" to get a HEX key and put that key in to the interfaces file.

That didn't seem to work for me.  Putting my actual WPA passphrase works (well, works for 1-2 minute bursts at this point.)  I've been reading all night, but not grasping what exactly is going on.

But mainly my first problem is where I need help. How do I keep it constantly connected?

Thanks again for the help

oh, and when its not connected.  I have no IP and the router is NOT pingable.  When its connected everything works fine.

---

### Post by NertSkull on 2010-10-16
Allright so I tried again putting the wpa-psk in as the key from the wpa_passphrase utility.

If I use that, I've had solid connection for about 20 minutes now.  So I'm assuming thats the way to go.  So I guess (for now at least, we'll see how it lasts) its fixed.

If anyone has any insights for me on what I've done to help me understand I'd appreciate it.  As is, thanks for the help chili, cause at least I have it working now.

For those interested, this is now my interfaces file

```
# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 10.42.32.112
gateway 10.42.32.1
netmask 255.255.255.0
wpa-ssid BDF_Beta
wpa-psk big_long_key_I_got_from_wpa_passphrase
```

---

### Post by chili555 on 2010-10-16
I have no idea why you get the wpa_passphrase utility encrypted passphrase to work and I can only get the actual in-the-clear passphrase to work. There might be some clues in /var/log/syslog when it won't stay connected..

I might understand if you had an /etc/wpa_supplicant.conf file that your interfaces file referred to. For example:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
pre-up wpa_supplicant -B -Dwext -i wlan0 -c /etc/wpa_supplicant.conf
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.254
post-down killall -q wpa_supplicant
```

I read about the method I use elsewhere and was frankly shocked at how easy it was and how it connects without any problems.

---

### Post by NertSkull on 2010-10-17
Yeah I don't have any idea.

Networking is not something I've ever been able to really grasp.  But your interfaces file helped.  Because something I had in mine kept it from connecting, but now all is well.  Thanks again.

I'm going to mark it as solved since it works, even though I don't know why it works.
:)

---

