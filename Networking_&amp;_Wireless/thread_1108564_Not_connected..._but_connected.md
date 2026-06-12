---
title: "Not connected... but connected?"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by Toadinator on 2009-03-27
I'm having some problems with my internet connection recently... The network manager doesn't say I'm connected, but Pidgin, Firefox, Skype, and almost everything else that uses the internet works (some apps on wine and ftp servers wont work). I don't know whats wrong! I went to "Network Tools" in administration and there's two connections: loopback and ethernet (loopback appeared first, if thats any help). Did I do something wrong? What can I do to fix this? Thanks!

---

### Post by x33a on 2009-03-27
you are using your connection on router mode, which does not get listed. if you are using pppoe mode that'll get listed.

---

### Post by Toadinator on 2009-03-27
> **x33a said:**
> you are using your connection on router mode, which does not get listed. if you are using pppoe mode that'll get listed.

Okay then...... how do I change this?

---

### Post by x33a on 2009-03-27
well, first let me confirm if you are on router mode :)

when you switch on the computer, are you automatically connected to the net? or you do something else.

---

### Post by Toadinator on 2009-03-27
> **x33a said:**
> well, first let me confirm if you are on router mode :)

when you switch on the computer, are you automatically connected to the net? or you do something else.

auto-magic. like normal, but says its not connected :\

---

### Post by x33a on 2009-03-27
what is auto-magic? did the network manager earlier used to show the status as connected?

i would like to know if you have setup a dialer(pppoe mode) or let the modem/router do the dialing(in-built).

---

### Post by Toadinator on 2009-03-27
auto-magic meaning I do nothing, it works fine without doing anything. I don't have to do any dialing as far as I know (never have had to) but a while ago it used to say connected.

---

### Post by x33a on 2009-03-27
heh, i knew what auto-magic meant, but these days softwares have all sort of names, so was confirming.

well, you can try reinstalling network manager, and see if the problem goes away.
```
sudo apt-get --reinstall network-manager
```

---

### Post by Toadinator on 2009-03-27
> **x33a said:**
> heh, i knew what auto-magic meant, but these days softwares have all sort of names, so was confirming.

well, you can try reinstalling network manager, and see if the problem goes away.
```
sudo apt-get --reinstall network-manager
```

already tried that, no avail.

---

### Post by x33a on 2009-03-27
post the output of
```
cat /etc/network/interfaces
```

---

### Post by Toadinator on 2009-03-27
> **x33a said:**
> post the output of
```
cat /etc/network/interfaces
```

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

---

### Post by Toadinator on 2009-03-27
I'm gonna go watch a movie, so I won't be back for about two hours for the record.

---

### Post by x33a on 2009-03-27
This seems okay. did you try creating a new profile in network manager?

---

### Post by Toadinator on 2009-03-27
> **x33a said:**
> This seems okay. did you try creating a new profile in network manager?

yes, yes I did and quite a few times. I'm not sure how to set it up right though and I thought it would automatically find my connection or whatever... any help? I have absolutely no connections in the network manager.

---

### Post by x33a on 2009-03-28
i don't use network manager, and i am not even on pppoe mode, so i don't have much knowledge of network manager. 

you can try wicd
```
sudo aptitude install wicd
```

this conflicts with network manager, so uninstall it first.

---

### Post by Toadinator on 2009-03-28
> **x33a said:**
> i don't use network manager, and i am not even on pppoe mode, so i don't have much knowledge of network manager. 

you can try wicd
```
sudo aptitude install wicd
```

this conflicts with network manager, so uninstall it first.

no thanks, I'll get a new computer someday anyways.

---

