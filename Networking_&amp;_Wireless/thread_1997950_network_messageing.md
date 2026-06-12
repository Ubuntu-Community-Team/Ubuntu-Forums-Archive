---
title: "network messageing"
date: 2012-06-05
forum: Networking &amp; Wireless
---

### Post by liquid_legs on 2012-06-05
hey peoples, ive bee learning how to use zenity to which is installed on ubuntu be default to send messages across the network. some of the tutorials ive done for zenity show you how to send a message to pc your on but not to computer over the network.
ive tryed including the ip address with i the command for sending messages being

zenity [IP] [message type] [message]

but the message will only come up on the host the computer

---

### Post by Blackbird_13 on 2012-06-06
Have you tried connecting to the other pc with ssh and then using zenity?

---

### Post by liquid_legs on 2012-06-06
no i havent, but thats an idea, i shall try

---

### Post by liquid_legs on 2012-06-07
well i sshing into the pc i want to send a message to and it tells me that it cant open the display

---

### Post by Blackbird_13 on 2012-06-07
Try adding --display=:0. For example

```
zenity --info --text="Hi there" --display=:0
```

---

