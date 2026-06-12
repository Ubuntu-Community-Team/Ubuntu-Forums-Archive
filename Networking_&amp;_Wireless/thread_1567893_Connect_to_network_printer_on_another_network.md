---
title: "Connect to network printer on another network"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by Kralizec on 2010-09-04
Hello,

At school, I have a switch (school provided, so settings are unchangeable) in my apartment complex. Attached to the switch are mine and my 2 roommates' desktop computers. Also attached to the switch is our wireless router; attached to the router is a printer.

The problem is this: using Windows 7, we would like to access this printer from our desktop machines. I have set up the router to forward the printer port (9100) and can successfully telnet to the printer from in Windows. In Ubuntu, I can fully connect to the printer and print pages from the desktop. However, even after manually setting the IP and port for the printer in Windows, Windows is unable to print pages.

Can anyone shed light on our problem? Are we destined to be stuck with another Windows inadequacy?

Attached is a rudimentary network diagram of the situation. The 130.85.244.0 network is the general school network; every machine attached to the switch gets a 10.5.0.0 internal address and a 130.85.244.0 external address.

Thank you!

---

### Post by Kralizec on 2010-09-04
Shameless self-bump... :sad::neutral:

---

### Post by metalf8801 on 2010-09-04
It could be a driver problem Ubuntu (I think all GNU/Linux distros) do a great job of handling drivers.  Windows to say the least does not. Try to find the make and model of the printer and see if you can get the network drivers from the manufacturers website. 

Or 
If you have a second computer running Ubuntu you might (keyword might I really don't know enough about this part but its an idea to look into) be able to set up a print server using samba. 

good luck 
Dan 

PS have you talk to any of your schools IT people?

---

### Post by Kralizec on 2010-09-04
Thank you for your response. I'm downloading the drivers from the website now. Hopefully that resolves the issue, but I've printed to the printer from windows 7 from within the router's network before fine so I'm skeptical. Heres hoping!

Also, one of my friends works in the IT department at the school, and he thinks the setup should be working.

---

### Post by mcpc2880 on 2011-05-21
I have had problems connecting wirelessly and wired at the same time.  Don't know why your printer is connected to the wireless router. Connect directly to the switch and should have no problem.

---

### Post by Kralizec on 2011-05-21
It liiiiives! The zombie thread liiiives!

Anyway, thanks for your response. I've since gotten it working. The problem was that Windows was too stupid to realize that it actually could see the printer. After I chose to ignore Windows's warning about not being able to see it and just printed something, it worked fine.

The reason why the printer isn't on the same network as the PC is because I have a limited number of access ports to the apartment complex's switch, and they're wired only; the printer only has a wireless adapter.

---

