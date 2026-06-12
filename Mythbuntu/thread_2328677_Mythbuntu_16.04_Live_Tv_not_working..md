---
title: "Mythbuntu 16.04 Live Tv not working."
date: 2016-06-23
forum: Mythbuntu
---

### Post by mccalleyt on 2016-06-23
I have done a fresh install of Mythbuntu 16.04 and I have been able to setup the backend and get the channels scanned. When I try to watch live TV it shows it is loading then it goes to the same screen I was just on. I am really new to MythTV and need ALOT of help please. 

Thanks,
Noderoamer

Edit:
I have a Hauppauge 1250

---

### Post by howefield on 2016-06-23
Thread moved to the "*Mythbuntu*" forum for a better fit.

---

### Post by mccalleyt on 2016-06-24
I have a little bit of an update. I did a fresh install of Mythbuntu 14.04.4 and everything works as it should. I am having issues that are somewhat related to the earlier problem. My Kubuntu 16.04 machine has the standard install of **mythtv-frontend** from the Kubuntu repository. It loads and shows the select language screen, when I click the save button the the window closes and it puts me right back to the same screen. It creates a crash report and restarts the program every time I hit the save button.

Thanks,
Noderoamer

---

### Post by larsolav on 2016-06-24
Are you running 0.27 or 0.28 on the Mythbuntu 14.04 box? Are you running the same version on the frontend?
Have you set up the backend to to allow for remote access in mythbuntu-control-centre? Are both computers set up to the same timezone/city?
Maybe also look at the frontend log on the frontend machine? The frontend logs to /var/log/mythtv/mythfrontend.log

---

### Post by mccalleyt on 2016-06-24
I have all machines on the same subnet and physical location. I have .28 on my Kubuntu 16.04 and .27 on my Mythbuntu 14.04.4. as far as the log.

> 011#011in mythtv-settings does not contain the proper IP address
Jun 24 00:29:59 rock-top mythfrontend.real: mythfrontend[3075]: I SendMessage mythcorecontext.cpp:436 (ConnectCommandSocket) MythCoreContext::ConnectCommandSocket(): Connecting to backend server: localhost:6543 (try 1 of 1)
Jun 24 00:29:59 rock-top mythfrontend.real: mythfrontend[3075]: E SendMessage mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 00:29:59 rock-top mythfrontend.real: mythfrontend[3075]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(7fd0f80079a0:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 00:29:59 rock-top mythfrontend.real: mythfrontend[3075]: E SendMessage mythcorecontext.cpp:506 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#

---

### Post by larsolav on 2016-06-25
In your front-end  settings you have to point the frontend to the IP address to the backend, as well as the mythconverg password (you can find the password on your backend in /etc/mythtv/mysql.txt). On your frontend settings it looks like it currently says "localhost" as the address of the backend. change that to the IP address of the backend. 
Once you have done that, I am pretty sure you will receive an error message saying your backend is not the same version as your frontend... They have to be the same version (both either 0.27 or 0.28).

---

### Post by mccalleyt on 2016-06-28
I upgraded my backend to .28 and everything works fine. Thank you for  your help. I think im going to stick with Mythbuntu 14.04 due to the  fact every machine I have upgraded to 16.04 of any of the *buntu's has  issues with hardware to software issues.

---

