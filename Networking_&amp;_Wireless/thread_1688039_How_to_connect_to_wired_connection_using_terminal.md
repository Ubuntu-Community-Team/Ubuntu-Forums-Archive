---
title: "How to connect to wired connection using terminal"
date: 2011-02-14
forum: Networking &amp; Wireless
---

### Post by lumunofloginism on 2011-02-14
how do i connect to my wired connection using the terminal?
i screwed myself over and dont have a desktop menu bar,and i need to connect
to the internet so i can get it back.

---

### Post by Pax_Harmonica on 2011-02-14
[http://www.wirelessdefence.org/Contents/LinuxWirelessCommands.htm](http://www.wirelessdefence.org/Contents/LinuxWirelessCommands.htm)

This website has some useful commands. I think it should include all that you need.

---

### Post by lumunofloginism on 2011-02-14
> **Pax_Harmonica said:**
> [http://www.wirelessdefence.org/Contents/LinuxWirelessCommands.htm](http://www.wirelessdefence.org/Contents/LinuxWirelessCommands.htm)

This website has some useful commands. I think it should include all that you need.

didnt help man, how do i know what devices are connected

---

### Post by mr_luksom on 2011-02-15
Some basics:

To see which network devices you have
```

lshw -C network

```

While you can do it completely in bash, everything else is best done in '/etc/network/interfaces', as the changes are permanent. More info here:

```

man /etc/networks/interfaces

```

---

### Post by lumunofloginism on 2011-02-16
OK guys, i figured it out.
all i had to do was set the ivp6 or whatever to "ignore"
and now it works perfectly.
if anyone wants more info on how i connected the ae1000,
send me a private message and ill post it back on the thread.

---

