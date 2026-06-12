---
title: "[SOLVED] Logging Network Usage / Bandwidth Monitoring"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by bobman on 2009-03-07
I was trying to get something similar to BitMeter that would record my usage since I'm on restricted bandwidth (Verizonwireless - 5gig limit)

Here is what I did that worked:
To install vnstat, in Terminal:

sudo apt-get install vnstat
sudo vnstat -u -i <interface>

for <interface>, mine was eth1

Then, create a script in /etc/init.d called netlog.sh
sudo gedit /etc/init.d/netlog.sh

insert code: 
#!/bin/bash
vnstat -u -i eth1

Next, in Terminal (this adds it to the shutdown script since generally vnstat only updates every 5 mins):

sudo chmod a+x /etc/init.d/netlog.sh
sudo update-rc.d netlog.sh defaults

That's it! Now, whenever you want to check your usage use vnstat from the terminal:
vnstat

If you want to see you current usage (graphical) just right click the panel and select "Add to Panel..." then choose System Monitor
After adding it, right click the graph and choose "Properties"
Then choose the option that says "Network" and deselect "CPU", that should be all for that. Now you have realtime viewing and long-term logging. This is my first post, sorry if anything is unclear. Good luck.

As an aside: If you want to see the results of vnstat quickly without opening the terminal do this:
Right Click, Choose "Create Launcher", Type whatever you want for name, but for command type in the following line of code:
gnome-terminal -x bash -c "vnstat -u -i eth1;vnstat;read -n1"

This will open the terminal, let you see the output, and continue showing the information until you click a button. Much better than the manual way if you ask me.

---

### Post by chandru155 on 2009-09-04
Thanks. I was looking for this only. I am newbie(Advanced user in windows).

Can u explain me those two line code

sudo chmod a+x..........
sudo update -rc..........

Please explain me clearly

And alos 

gnome-terminal -x.........

I created a launcher and using that launcher. Thanks

---

### Post by shredder12 on 2009-09-04
> **chandru155 said:**
> Thanks. I was looking for this only. I am newbie(Advanced user in windows).


Welcome to the world of linux.. :)
> 
Can u explain me those two line code

sudo chmod a+x..........
sudo update -rc..........

gnome-terminal -x.........


If you want to know what a command does then you should always check the man page for that command..
eg. try ```
man chmod
```

anyways, chmod is used to change the file permissions a+x means add executable permissions to the file.. "x" means executable

try reading man page of update-rc.d for details but in brief it is used  to install or remove init script links.. these are the scripts that are executed at system start up ( they are mostly used to control daemons)

gnome-terminal -x opens a terminal with a command executed , in this case it is bash -c .
bash is kind of shell and -c means to execute a command from the string, in our case the string is "vnstat -u ...."

And once again, for more details u should always refer to the man page..
Hope that helps

---

### Post by chandru155 on 2009-09-04
Thanks.

---

