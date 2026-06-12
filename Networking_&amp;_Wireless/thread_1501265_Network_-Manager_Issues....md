---
title: "Network -Manager Issues..."
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by BugBuster on 2010-06-04
I have noticed some strange behavior with Network Manager DSL connection option. 
When I use Network-manager to establish a dsl connection,which connects flawlessly, I have issues connecting to certain websites like thepiratebay.org, isohunt.com etc. Initially I thought my ISP had blocked torrent sites. But then I realized that I could login into yahoomail but on logout the connection would timeout. So I thought it was something else . I changed the dns servers to opendns ones, but it did not help either.

So I disabled Network manager completely and connected to to internet using "pon dsl-provider" method and all the issued that I have mentioned did not re-appear. So could anyone help me with configuring dsl with network-manager correctly.

Also would like to mention that I have already tried to change the MTU to 1460,1492 etc. in Network-manager dsl connection but it does not help.

---

### Post by BugBuster on 2010-06-04
Today I tried this with the Fedora 13 64-bit Live CD and the issue is present there as well. Could this be a bug in Network Manager then?

---

### Post by BugBuster on 2010-06-06
Ahhh..at last figured it out through a lot of "googling"!!

Here's how:
I assume you have setup a new DSL connection as you want and it works fine. 

Now right-click Network-Manager applet and select "Edit connections" and select the DSL connection and again click "Edit".

Then set MTU under 'Wired' tab to automatic and tick where it says "available to all users" ( This will make the DSL conection a system connection and thus will be available to others users even after you login).Then click Apply.

Then do:
```

cd /etc/NetworkManager/system-connections/

```
There you should find your DSL connection.Open that file for editing and then lookout for a "ppp" section as below
```

[ppp]
noauth=true
refuse-eap=false
refuse-pap=false
refuse-chap=false
refuse-mschap=false
refuse-mschapv2=false
nobsdcomp=false
nodeflate=false
no-vj-comp=false
require-mppe=false
require-mppe-128=false
mppe-stateful=false
crtscts=false
baud=0
mru=1492
mtu=1460
lcp-echo-failure=5
lcp-echo-interval=30

```

and change the "mtu=****" to a desired value that works for you.Now try connecting to the DSL connection again and then do
```

ifconfig |grep ppp0

```
and ensure that the MTU is what you just set.

Then verify that the sites that had issues opening before work now.

Note : I could not locate the file that has an option for changing the mtu in ppp section when the "available to all users" options is not ticked. If you find that file please post it here. I should help people out here who do not want to make the dsl connection a system connection.

---

