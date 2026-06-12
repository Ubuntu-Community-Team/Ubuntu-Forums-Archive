---
title: "Unable to Add Applications."
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by sakthidaran on 2009-01-09
Problem: Unable to Add Applications.When I try, the system displays the following message:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to 192.168.2.202:3128 (192.168.2.202). - connect (111 Connection refused)

After reading other threads tried the following solutions suggested:

[COLOR="Blue"]sudo apt-get update

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to 192.168.2.202:3128 (192.168.2.202). - connect (111 Connection refused)

W: You may want to run apt-get update to correct these problems[/COLOR]

Tried the next solution:

apt-get update

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to 192.168.2.202:3128 (192.168.2.202). - connect (111 Connection refused)

W: You may want to run sudo apt-get update to correct these problems

The following commands were given and response is displayed below for your information.

at /etc/hostname

itadmin-desktop

cat /etc/hosts

127.0.0.1	localhost
127.0.1.1	itadmin-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

My system is connected to a proxy 192.168.2.202 I am able to browse internet. Yet, Synaptic package could not connect to the servers for downloading software or update software.

Expect your kind cooperation.

---

### Post by mikewhatever on 2009-01-09
There seems to be a problem on the local network, 192.168.2.202. Perhaps you could tell us more about that proxy setup.

---

### Post by sakthidaran on 2009-01-09
> **mikewhatever said:**
> There seems to be a problem on the local network, 192.168.2.202. Perhaps you could tell us more about that proxy setup.

I am able to access Internet with my browser. Can you be specif about setup? Will you please specify what exact information you would like to know about the proxy?

In the mean time, I will try to get the information.

---

### Post by mikewhatever on 2009-01-10
The browser and Synaptic are two separate applications, so the question is, did you setup the proxy system wide or just for the browser?

---

### Post by sakthidaran on 2009-01-15
> **mikewhatever said:**
> The browser and Synaptic are two separate applications, so the question is, did you setup the proxy system wide or just for the browser?

Thanks, your suggestion worked. Details:

I had set the proxy system wide but still I had problem. I then selected system-preferences-network proxy-preferences-set the proxy address and port number-apply system wide.

Next, system-administration-synaptic package manager-settings-preferences-network-set the proxy address and port number.

Next, Mozilla-edit-preferences-advanced-network-settings-manual proxy configuration-set the proxy address and port number.

This procedure has ensured same ip in all the packages.

---

