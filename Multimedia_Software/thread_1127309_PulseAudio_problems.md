---
title: "PulseAudio problems"
date: 2009-04-16
forum: Multimedia Software
---

### Post by SilverFrost on 2009-04-16
Today i installed PulseAudio but when i was about to configure it through Firestarter while looking at: [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

I gave this commands:

```
gksudo gedit /etc/firestarter/user-pre
```
and an empty file came up. Then i added this lines:


```
$IPT -A INPUT -p udp --dport 5353 -d 224.0.0.251 -j ACCEPT
$IPT -A OUTPUT -p udp --dport 5353 -d 224.0.0.251 -j ACCEPT


```

But when i was about to save the file with this two lines in it, it first said that the file was already there and asked if i wanted to replace it then i clicked on Replace. Then a rong message came up and said:

```
Could not save the file /etc/firestarter/user-pre.
You are try to save the file on a write protected disk. Look if you gave the place right and try again.
```

It doesnt work to save this file?  How do i save it?

---

### Post by SilverFrost on 2009-04-16
Or i should uninstall Firestarter?
Said: 

> If you have firestarter installed, it *WILL* stop PulseAudio from properly communicating over Zeroconf/Avahi's port 5353. 

On the PulseAudio wiki. Wich would end up in Firestarter blocking PulseAudio...

---

### Post by edvar on 2009-05-05
Run 'sudo chmod u+w /etc/firestarter/user-pre' to turn the file writable, do the changes, save the file and then run'sudo chmod u-w /etc/firestarter/user-pre' to turn the file read-only again.

---

