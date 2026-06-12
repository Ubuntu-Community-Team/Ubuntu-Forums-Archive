---
title: "wl restricted module networkmanager problem"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by Uejji on 2009-05-21
Hello everyone.

I'm running Ubuntu 9.04 on my new Lenovo Ideapad S10e, and everything works great, although the wireless card depends on the proprietary wl driver from broadcom.  There is one issue I've been running into since I got it set up.

There is a 2wire                                               2700HG-B wireless router I connect to at times.  However, when I set it up in NetworkManager and try to connect to it, the wireless router completely reboots.  All other computers on the wireless network lose connection for a couple of minutes and it is a huge hassle for everyone.  It uses a WEP104 key, and I'm not free to modify that because it is not mine; I've only been given the WEP key to use.

In Windows 7, there is no problem of any sort.  It works great without problem.  The laptop also connects fine to all other wireless networks I have in Ubuntu without problem.

If I use iwconfig to directly set the essid and key to the wireless adapter -- ie

```
sudo iwconfig eth1 essid #####
sudo iwconfig eth1 key #####
```then run dhclient, it connects, obtains an IP address, and there are no problems.

I made myself a shell script to use when I'm over, but it's just a hassle to have to run a shell script to connect to a wireless network when networkmanager handles everything else.

I wanted to try my own wpa_supplicant.conf in an attempt to trace down the problem, but I can't seem to find a way to kill the wpa_supplicant that's always running.  Nor can I locate the configuration file where networkmanager is keeping all its networks.

Any suggestions I could have would be extremely helpful.

---

### Post by Uejji on 2009-05-22
Well, I stopped NetworkManager which allowed me to spawn my own wpa_supplicant process.

My custom wpa_supplicant network file is as follows (censored of course)

```
network={
ssid="#####"
key_mgmt=NONE
group=WEP104 WEP40
auth_alg=OPEN SHARED
wep_key0=#####
}
```By using the command *sudo wpa_supplicant -B -i eth1 -c network* I am able to authenticate with the access point perfectly without the access point crashing and restarting.

Could this possibly be a bug in NetworkManager?  Or some other weird glitch in Ubuntu's networking subsystem (which coming from a Slackware background I have little experience in)?

I'll also note that another computer running Ubuntu 9.04 connects to this network just fine using NetworkManager, so I don't know where exactly the problem could lie.

---

### Post by Uejji on 2009-07-03
Just to report back in.  This issue was resolved in the latest kernel update.

---

