---
title: "easytether one click connect"
date: 2011-03-07
forum: Networking &amp; Wireless
---

### Post by nelio2k on 2011-03-07
Hi all,

I have written a short bash script utilizing zenity to make it easy to call easytether and also DHCP. It makes connecting to the internet a lot easier. 

[LIST=1]
[*]Make sure you have zenity (sudo apt-get install zenity)
[*]Download the script to a location (i.e. ~/scripts/easytetherHelper.sh)
[*]Create a Nautilus menu item.
[*]Type: **Application**
[*]Name: **EasyTetherHelper**
[*]Command: **bash "/home/[username]/scripts/easytetherHelper.sh"** (change your path accordingly)
[*]Enter any comments if you'd like.
[/LIST]

You can now launch it from the menu or create a panel with a button to it, or even put it on your desktop. It'll make connecting to the internet a lot easier. 

Click it once to connect. Click it once more and it will ask if you want to disconnect.

If at any point easytether quits, it will notify you. 

Note: You will be prompted to enter your password due to the script calling gksudo. It's quite simple and not malicious, but it's needed for the process.

Note: You may want to right click on "network manager" and uncheck "enable network" to get empathy/evolution/firefox" to avoid those programs getting stuck due to network manager telling them that there is no network connection.

---

### Post by TeTeT on 2011-03-15
Thanks for your script, it's a nice helper application! It motivated me to do some research and integrate the easytether commands via udev. While not interactive and resilient as your code, it might be useful for those that want automatism:

```

$ more /etc/udev/rules.d/easytether.rules 
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="22b8", ATTR{idProduct}=="41da" , RUN+="/usr/local/bin/easytether"

```

```

$ cat /usr/local/bin/easytether 
#!/bin/sh 

logger "Easytether script"
/usr/bin/easytether connect &

/sbin/dhclient easytether0

logger "End Easytether script"

```

---

