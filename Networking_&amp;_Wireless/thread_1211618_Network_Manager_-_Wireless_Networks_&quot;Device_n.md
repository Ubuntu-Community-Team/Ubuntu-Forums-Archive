---
title: "Network Manager - Wireless Networks &quot;Device not managed&quot;"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by iEthan on 2009-07-12
When I left-click on the Network Manager, it says, under Wireless Networks, "device not managed". It recognizes the driver, but it won't manage it. Is there a workaround?

---

### Post by RedSingularity on 2009-07-12
Are you sure the driver is activated?  Is there anything under System>Admin>Hardware drivers?

---

### Post by Iowan on 2009-07-12
Do you have configuration information in */etc/network/interfaces* - other than "lo"?

---

### Post by superprash2003 on 2009-07-13
hope this helps [http://www.prash-babu.com/2009/05/how-to-fix-ubuntu-network-manager-error.html](http://www.prash-babu.com/2009/05/how-to-fix-ubuntu-network-manager-error.html)

---

### Post by iEthan on 2009-07-13
I resolved it on my own :)

Thanks for your input.

---

### Post by neo_ritz on 2009-07-13
Well I have the same prob, how did you resolve it?

---

### Post by neo_ritz on 2009-07-13
Okkaiy..........
Got the solution,

Step 1 : Go to the Terminal ( Applications->Accessories->Terminal ) and type sudo gedit /etc/NetworkManager/nm-system-settings.conf
Step 2 : A window would now popup displaying the contents of the nm-system-settings.conf file
Step 3 : Now Change "managed=false" to "managed=true"
Step 4 : Save the file and close the window
Step 5 : Now back in the terminal type sudo killall nm-system-settings
Step 6 : Thats it, your network interface should now be detected and it should attempt to connect to a network.

---

### Post by vskoric on 2009-07-23
Thanks for solution,

I just do not understand why Network Manager needs me to every while change that managed=something config line.

I had managed=disabled working for a while and than it suddenly stopped working, now I am ok with managed=true.


:confused:

---

### Post by JlyGrnMigt on 2010-02-27
> **neo_ritz said:**
> Okkaiy..........
Got the solution,

Step 1 : Go to the Terminal ( Applications->Accessories->Terminal ) and type sudo gedit /etc/NetworkManager/nm-system-settings.conf
Step 2 : A window would now popup displaying the contents of the nm-system-settings.conf file
Step 3 : Now Change "managed=false" to "managed=true"
Step 4 : Save the file and close the window
Step 5 : Now back in the terminal type sudo killall nm-system-settings
Step 6 : Thats it, your network interface should now be detected and it should attempt to connect to a network.

This worked for me, though I had to reboot to get everything to work.  Thanks!

---

### Post by Cygni on 2010-07-06
> **neo_ritz said:**
> Okkaiy..........
Got the solution,

Step 1 : Go to the Terminal ( Applications->Accessories->Terminal ) and type sudo gedit /etc/NetworkManager/nm-system-settings.conf
Step 2 : A window would now popup displaying the contents of the nm-system-settings.conf file
Step 3 : Now Change "managed=false" to "managed=true"
Step 4 : Save the file and close the window
Step 5 : Now back in the terminal type sudo killall nm-system-settings
Step 6 : Thats it, your network interface should now be detected and it should attempt to connect to a network.
Thank you! This excellent information worked for my backup comp, a Pismo that I just installed 10.04 on and could not get the network working after updating. ---> Happy face! :D

---

### Post by eb3ha4el on 2011-05-09
> **neo_ritz said:**
> Okkaiy..........
Got the solution,

Step 1 : Go to the Terminal ( Applications->Accessories->Terminal ) and type sudo gedit /etc/NetworkManager/nm-system-settings.conf
Step 2 : A window would now popup displaying the contents of the nm-system-settings.conf file
Step 3 : Now Change "managed=false" to "managed=true"
Step 4 : Save the file and close the window
Step 5 : Now back in the terminal type sudo killall nm-system-settings
Step 6 : Thats it, your network interface should now be detected and it should attempt to connect to a network.




I'm a newbie, so dont know what's difference however,
for me this did not work.

instead, I used this, which is very similar but different. and it worked. 
[http://www.accretionlogistics.com/2011/04/ubuntu-11-04-fix-the-wireless-device-not-managed/](http://www.accretionlogistics.com/2011/04/ubuntu-11-04-fix-the-wireless-device-not-managed/)

---

### Post by malapradej on 2011-06-20
> **neo_ritz said:**
> Okkaiy..........
Got the solution,

Step 1 : Go to the Terminal ( Applications->Accessories->Terminal ) and type sudo gedit /etc/NetworkManager/nm-system-settings.conf
Step 2 : A window would now popup displaying the contents of the nm-system-settings.conf file
Step 3 : Now Change "managed=false" to "managed=true"
Step 4 : Save the file and close the window
Step 5 : Now back in the terminal type sudo killall nm-system-settings
Step 6 : Thats it, your network interface should now be detected and it should attempt to connect to a network.

I'd just like to comment for those who are using Natty Narwhal replace "/nm-system-settings.conf" with "NetworkManager.conf" both for file names, and the kill command (less the .conf).

---

