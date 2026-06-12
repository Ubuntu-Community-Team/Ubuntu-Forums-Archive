---
title: "Help connecting to the Internet on Ubuntu?"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by chris9086 on 2010-12-29
I know absolutely nothing about Ubuntu. I bought a Dell Vostro 1015, not knowing it ran on Ubuntu 9.04, rather than Windows 7. I can't even figure out how to connect to my wireless router. I have the connection name and the WEP key entered, and it won't connect to it. I was able to connect to it one time, but I was just trying random things and I can't seem to connect again. Can someone please help me out?

---

### Post by PatchesTheCaveman on 2010-12-29
Sorry you're having trouble getting your Internet connection working with Ubuntu.  Dell is supposed to ensure everything works well out of the box so hopefully this will be a simple fix.

Right-click on your wireless icon and click *Edit connections*.  Switch to the Wireless tab and delete all the connections that appear.  Then click Close.

Now click on the Wireless icon again and try reconnecting to your router and re-entering your WEP key. 

If it still doesn't work, go to Applications > Accessories > Terminal and type the following and press Enter in the black box that appears:
```
sudo iwconfig
```

Copy and paste all the stuff it spits out into a post here.  Then type this and press Enter again:
```
ifconfig -a
```

Copy and paste all that too.  That will give us an idea of what might be going wrong.

---

