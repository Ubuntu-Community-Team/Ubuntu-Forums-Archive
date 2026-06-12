---
title: "Help needed to setup frontend connection to remote backend"
date: 2009-08-09
forum: Mythbuntu
---

### Post by sperwer on 2009-08-09
Hi
I have some problems setting up a remote frontend.
I can see in the log that the frontend tries to connect to 127.0.0.1 where i need it to connect to 192.168.0.2 which I tried to setup in /settings/generel "What am i doing wrong"

I have from MCC managed to set up connection to the mythtv mysql database on the remote backend.

Flemming

THX for ur help "klc5555"

I have missed this part:
Did you also go into the Mythtv backend setup on this backend machine and in the General section change the two references there of the master database's address from 127.0.0.1 to 192.168.0.2? As described here: [http://www.mythtv.org/wiki/User_Manu...ration_Backend](http://www.mythtv.org/wiki/User_Manu...ration_Backend)

Flemming

---

### Post by klc5555 on 2009-08-09
> **sperwer said:**
> Hi
I have some problems setting up a remote frontend.
I can see in the log that the frontend tries to connect to 127.0.0.1 where i need it to connect to 192.168.0.2 which I tried to setup in /settings/generel "What am i doing wrong"

I have from MCC managed to set up connection to the mythtv mysql database on the remote backend.

Flemming

If you just run the command "mythfrontend" on the remote frontend machine, and it can't find a UPnP backend, it should dump you to the config screen, where it keeps asking for the backend's ip address, user name (i.e. "mythtv") and the MySQL password until you get it right and it can find the backend.

If this remote frontend machine has no backend with tuner(s) on it, it should not be running a mythbackend daemon with a local mythconverg database. If it is, your mythfrontend is likely trying to connect to this spurious localhost "backend" instead of finding the correct remote one.

---

### Post by sperwer on 2009-08-09
Hi

Yes this frontend have no tuners connected. In MCC i have under system roles selected no backend and selected frontend role.

During installation the backend was installed, but i believe it was uninstalled when i selected no backend role, at least the backend settings has disappeared from the system menu.

Flemming

---

### Post by klc5555 on 2009-08-09
> **sperwer said:**
> Hi

Yes this frontend have no tuners connected. In MCC i have under system roles selected no backend and selected frontend role.

During installation the backend was installed, but i believe it was uninstalled when i selected no backend role, at least the backend settings has disappeared from the system menu.

Flemming

Mythbuntu tends to install and sometimes tries to run everything, including the unnecessary backend and MySQL packages, whether you indicate the machine's a frontend-only one or not. Usually when you try to uninstall the backend and MySQL after the fact, the package manager tries to retaliate by uninstalling the desktop also. Which is the main reason I tend to install Plain-Vanilla Xubuntu on a machine I intend to use frontend-only with Mythtv, and then specifically add just the frontend packages via apt-get or Synaptic. Avoids all these sorts of Mythbuntu problems. Including the odd way that Mythbuntu partitions the hard disk during the installation process, a partitioning scheme which makes no sense on a no-backend machine that is not recording locally.

From a command prompt on a terminal on your desktop, run "top" and see if there's a backend running locally on this frontend machine. If there is, kill it with "sudo killall mythbackend". Then run "mythfrontend" from a prompt and see whether you get to the config screens that ask first for language, then for the data I indicated earlier.

Unless you have a specific other use for MySQL on a frontend-only Myth machine, it should be uninstalled from Synaptic or apt-get. Ditto for mythtvbackend. If the package managers get huffy and indicate they want to uninstall everything not nailed down including the desktop if you try this, and you don't want to deal with the hassle of trying to sort through the rubble afterward, you can disable MySQL and the backend from launching on bootup instead.

---

### Post by sperwer on 2009-08-09
Did run top, no mythbackend were running.
Started frontend in terminal, it doesn't give the opportunity to select language (however when frontend start automatic after reboot i get the option) have tried severel times to change the IP adress to backend.

Fleming

---

### Post by klc5555 on 2009-08-09
> **sperwer said:**
> Did run top, no mythbackend were running.
Started frontend in terminal, it doesn't give the opportunity to select language (however when frontend start automatic after reboot i get the option) have tried severel times to change the IP adress to backend.

Fleming

You'll also need to add the correct MySQL password for the backend. This is a randomly generated sequence of numbers and letters found on the backend in the directory /home/mythtv/.mythtv/ in the simlink "mysql.txt"

Now your first post mentioned that you had "from MCC managed to set up connection to the mythtv mysql database on the remote backend". I take it from this that you enabled the MySQL service in the "services" section of MCC on the backend. Did you also go into the Mythtv backend setup on this backend machine and in the General section change the two references there of the master database's address from 127.0.0.1 to 192.168.0.2? As described here: [http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend)

You also have to set 0000 as the PIN number in both the backend and the remote frontend's setup. Then you should be OK.

---

