---
title: "Run on network connection"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by cdg52 on 2009-02-03
Hey all,

I was wonder if there is a way to run a bash script or perl script on connection to a network. My main intension are to run a script when my wireless interface connects to a specific ap, but only when it connects to that ap. ...any ideas?

---

### Post by pdtpatrick on 2009-02-04
thats gonna be one hell of a script.

But it can be done. You will need a script that constantly monitors your wireless network card and filters out for a specific AP MAC address and then once that becomes true, it will then go through and run the following scripts.

But basically you will be on a loop for a while since its always searching for the appropriate parameters. Almost seem too much of wasted resources to do it :)

---

### Post by cdg52 on 2009-02-04
Darn, I was hoping there was some sort of hook somewhere that you could auto launch a script, I knew I could run a script that just runs in the background but i need those resources so thats not really an option.

Anyone know of any hooks for when a network connection goes up I can tell it to do something?

---

### Post by cdg52 on 2009-02-04
Found what I was looking for and heres how!

> 
There is also the good old-fashioned manual way to do it:

Inside /etc/network directory there are four subdirectories.
You can put .sh scripts or symbolic links in each subdirectory as follows:

if-down.d - Script that will be executed after network has been disconnected
if-post-down.d - Script that will be executed before network disconnection
if-pre-up.d - Script that will be executed before network connection
if-up.d - Script that will be executed after network has been connected

Now here is a sample script that you can put inside e.g. if-up.d directory

#!/bin/bash

ssid=`iwgetid -s`

if [ $ssid == "my_network_ssid" ]
then
#put here the command to be executed only when connected
#on network "my_network_ssid"


That Comes to you by spiros over at internettablettalk.com

---

### Post by Pertel on 2010-10-20
Hi, i'm trying to revive this old thread, because i want to use this exact script to start my synergy client whenever i log on to my home wireless network, but i cannot get it to work.

I have created a file name "synergy.sh" in the **"if-up.d"** folder which contains:

```
#!/bin/bash

ssid=`iwgetid -s`

if [ $ssid == "my_network_ssid" ]; then
synergyc -n Zepto 192.168.0.2
```

and i replaced **"my_network_ssid"** with the real ssid.

When i disconnect and reconnect the wireless, nothing happens, and i would greatly appreciate any help you might give. 

i have tried various combinations like adding the semicolon after the if statement, using **"bin/sh"** instead of **"bin/bash"**, ending the code with an **"fi"** but no luck. I have also made sure the file is "executable as a program". I tested that the **"iwgetid -s"** command returned the correct ssid, and it matches the one in the script.

As you can see i am not really competent in writing scripts, i have just tried to feel my way through it, so it might be something really obvious.

Thanks for your help in advance, i hope someone has a little spare time to help me out :)

---

### Post by Pertel on 2010-10-22
Problem solved.

I took some time to actually find out what the scripting syntax was, and found out there was a lot wrong with the script. Below is my working script for anyone interested.

```
#!/bin/bash

#get ssid from wireless network and save to ssid variable
ssid=$(iwgetid -s)
#save my home network ssid in mySsid variable
mySsid='my home ssid'

#if the network just connected to is the home network, start synergy and connect to server
if [ "$ssid" == "$mySsid" ] ; then
	/usr/bin/synergyc -n Zepto 192.168.0.2

fi
```

Just goes to show that a little googling and reading pays off. Now i know a little more about bash syntax as well :)

---

