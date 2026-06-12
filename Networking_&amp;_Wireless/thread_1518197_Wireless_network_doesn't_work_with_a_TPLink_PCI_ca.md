---
title: "Wireless network doesn't work with a TPLink PCI card"
date: 2010-06-26
forum: Networking &amp; Wireless
---

### Post by blazeag on 2010-06-26
Hi guys,

I'm trying to activate a wireless network on an ubuntu server 10.04. The machine has a TPLink PCI wireless card.
Card is well recognized, and scanning for wireless connection it finds correctly the essid of the access point in the room.

But when I try:
```

$ sudo iwconfig wlan0 essid "apoint" key s:my_key_8

```

this error is returned:
```

Error for wireless request "Set Encode" (8B2A) :
 * *SET failed on device wlan0 ; Invalid argument.

```

I looked for similar situations over many forums, and I found that it could be the card doesn't support the encryption type (My AP uses WPA with TKIP).
However if I use an ubuntu desktop live CD on the same machine, I can connect witouth any problem with NetworkManager 0.8.

Some idea? Many thanks

---

### Post by blazeag on 2010-06-26
Up

---

### Post by blazeag on 2010-06-30
up

---

