---
title: "Network not staying down after I tell it to"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by spotted zebra on 2010-08-14
When I go to coffee shops I usually change my mac address cause i am a privacy freak. I have been having a problem lately though.

I execute the command below:

```

sudo ifconfig wlan0 down

```and the wireless will go down but then automatically come back up on it's own, usually before i can execute the 'macchanger' command. 

what i have been doing recently is right clicking on the connectivity icon and disabling it that way. It is really a pain to open the terminal then have to move my cursor to do something it is much easier to just type commands, im on a netbook here so the more i can do with the keyboard the better. i also really like using the terminal. 

as a side note/problem. is there anyway to have wireless auto disabled when i boot the computer? i like to have control over what i connect to and when my computer connects to it. not just boot and connect, especially on a netbook that goes all over the place.

thanks for the help in advance.[URL="http://ubuntuforums.org/search.php"]
[/URL]

---

### Post by Iowan on 2010-08-14
Network Manager *should* have a checkbox for "Connect automatically" if you Edit Connections. Un-checking that *should* require you to initiate the connection.

---

### Post by spotted zebra on 2010-08-14
thanks man. do i have to do it for everyone of them that i don't want to auto connect to? i would assume so but i could be missing like and overall. not that big of deal really because i just don't want to connect to public 'open' networks.

to anyone else im still needing help making sure my network stays down when i tell it to.

---

### Post by Iowan on 2010-08-14
> **spotted zebra said:**
> thanks man. do i have to do it for everyone of them that i don't want to auto connect to? It's by interface - so if you disable Autoconnect for wlan0, it shouldn't connect to *anything* until you tell it to.

---

