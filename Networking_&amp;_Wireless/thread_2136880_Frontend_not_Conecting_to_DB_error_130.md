---
title: "Frontend not Conecting to DB error 130"
date: 2013-04-18
forum: Networking &amp; Wireless
---

### Post by gga96 on 2013-04-18
Hi All,

I have bad trouble getting the backend to connect to the net.

I needed a static IP on the backend so I read [[COLOR=#dd4814]http://ubuntuforums.org/showthread.php?t=2081392[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2081392") and then followed chili555 instructions with dns-nameservers primary, secondary of the router.

The file "/etc/network/interfaces" was edited to the following:
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.3
gateway 192.168.1.1
netmask 255.255.255.0
dns-nameservers 180.181.127.3 180.181.127.4


This connected the backend. Very good, but...

But, now the frontend would not connect to the DB. Checked settings and all forum help but no joy so I have now re-installed the frontend.

Problem is now I am stuck with init setup looping with "Country", "Language" and "Database Configuration 1/2". The hostname 192.168.1.3, password etc are all correctly entered. When I try to escape the loop it restarts the setup dialog again with a message about having ERROR:130.

All I can do is turn the power off.  If I re-boot it starts the setup again.

How do I recover from the situation?
Or how do I fix the backend static IP config?

Appreciate any help from members.
Glen

---

### Post by gga96 on 2013-04-21
I am getting no where in terms of success.

Have tried changing this line "dns-nameservers 180.181.127.3 180.181.127.4" to value "8.8.8.8 192.168.1.1", but no joy.
I have no other rational ideas.

The frontend continues to loop in setup screen and "Cancel" generates error 130 when re-starting the setup loop.

I need the help of network experts like chili555 to help me solve the problem.

Knowledge is a powerful thing.
Glen

---

### Post by gga96 on 2013-04-24
The backend and local frontend work perfectly as expected.
Remote frontend will not connect to DB during setup.

Found that Alt F11 will show "Applications" panel and enable an escape from the looping setup.

Frontend history:
-"ping 192.168.1.3" from frontend, result has no errors.
-Have tested remote frontend hardware (RAM, HDD) and believe it to be ok.
-"ping 192.168.1.3" from Win 7 machine, result has no errors.
-"mysqlcheck -u root -p  --repair mythconverg" reported all ok.
-Have re-installed remote frontend to get a vanilla copy. Rebooted, set correct data in Setup Dialog. Connection failed
-Used Alt F11 to escape looping setup dialog.
-Used Mythbuntu Control Center to uncheck booting to frontend.
-Rebooted.
-Installed Firefox and gedit.
-Edited "sudo gedit /usr/bin/mythfrontend" with "exit 0" at end of loop to stop setup from looping.

I shall wait for help now, I do not want to corrupt the installation by poking around.
Being a newbie to Ubuntu I am in need of some serious help!!!

Thanks for your help.
Glen

---

### Post by gga96 on 2013-04-24
The obvious is not always obvious!
The setting of "Control Center">"Master Backend Role" had been overlooked and remained disabled.

This problem is fixed.
Thread CLOSED.

I thank all who considered the problem.
Glen

---

