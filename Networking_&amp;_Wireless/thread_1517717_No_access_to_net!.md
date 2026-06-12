---
title: "No access to net!"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by Martin Sullivan on 2010-06-25
On a spare PC I have 2 hard drives. On the larger one I have Win xp Home edition. On the smaller drive I have Win XP, PLUS Ubuntu, side by side. I have a Linksys wireless N router and a Linksys USB adapter and can access the Internet using XP but cannot access it using Ubuntu. Since most of the help with ubuntu is accessible mainly thru the net this creates a problem.
Can anyone help???

---

### Post by OxentroT on 2010-06-25
Have you tried to set up NDIS wrapper?
You will need to make sure you find and save the windows drivers for your adapter somewhere easy to find as you will soon need them. Disable or disconnect your adapter and open up a terminal to enter these commands.


```
sudo apt-get install ndisgtk
```

when finished, enter this command to wrap the win drivers

```
sudo ndisgtk
```

A window will open asking you for your windows drivers. Did you download them to somewhere easy to find? (e.g. documents)
Click the install new driver button and a selector window will pop up for you to then tell the wrapper where your drivers are. When done it will bring you back to the original window to show you that your drivers are now listed within it.

Now you want to configure your adapter
 run this to see if your adapter was picked up by ndis wrapper

```
dmesg
```

If you see your adapter listed, that is a good sign.

Now you want to run 

```
iwconfig wlan0
```

Hopefully this will get it working. If not recognized at least.

---

### Post by Martin Sullivan on 2010-06-25
Thank you, thank you Cleveland!

---

