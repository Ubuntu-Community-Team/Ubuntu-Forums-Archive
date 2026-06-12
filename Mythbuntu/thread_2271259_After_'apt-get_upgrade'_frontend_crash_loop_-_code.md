---
title: "After 'apt-get upgrade' frontend crash loop - code 130 - Backend/Frontend combo"
date: 2015-03-28
forum: Mythbuntu
---

### Post by MrBackhand on 2015-03-28
Last weekend I did a successful upgrade from Mythbuntu 12.04 to Mythbuntu 14.04.2.  I had a few problems but I was able to restore the database backup and get everything working again. The 14.04 sources were working and I had performed an 'apt-get upgrade' earlier in a week successfully with the default Ubuntu 14.04 Sources.  The MythTV sources were not in the sources.list. Today, I stopped the frontend, ran the Mythbuntu Control Center and added the .27 sources as that was the version of the MythTV software and database.  I ran the 'apt-get update', then 'apt-get upgrade', and was presented with MythTV updates.  The updates downloaded and installed without a problem, but then I was presented with a new screen and a question:

"Will any other Mythfrontend be connecting to the database?"  No other frontend was going to connect other than the one on the local machine, so I selected no.  It went back to the console screen and I saw installs, and changes.  It was after that the frontend would not launch.  The mythfrontend.log says it cannot connect to the database on port 6543.  Is there any way I can run that question again and change it to yes, or edit the mythfrontend settings and change the backend to the IP address of the machine? I am thinking it might solve the problems.  Wifey isn't happy.  :)

```
Mar 28 16:48:20 mythtv mythfrontend.real: mythfrontend[8746]: E SendMessage mythcorecontext.cpp:305 (SetupCommandSocket) MythCoreContext: Problem connecting server socket to master backend
Mar 28 16:48:20 mythtv mythfrontend.real: mythfrontend[8746]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Mar 28 16:48:20 mythtv mythfrontend.real: mythfrontend[8746]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: localhost:6543 (try 1 of 1)
Mar 28 16:48:20 mythtv mythfrontend.real: mythfrontend[8746]: E SendMessage mythcorecontext.cpp:959 (GetBackendServerIP) No address defined for host: localhost
Mar 28 16:48:20 mythtv mythfrontend.real: mythfrontend[8746]: E SendMessage mythcorecontext.cpp:305 (SetupCommandSocket) MythCoreContext: Problem connecting server socket to master backend
Mar 28 16:48:20 mythtv mythfrontend.real: mythfrontend[8746]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Mar 28 16:48:20 mythtv mythfrontend.real: mythfrontend[8746]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: localhost:6543 (try 1 of 1)
Mar 28 16:48:20 mythtv mythfrontend.real: mythfrontend[8746]: E SendMessage mythcorecontext.cpp:959 (GetBackendServerIP) No address defined for host: localhost
Mar 28 16:48:20 mythtv mythfrontend.real: mythfrontend[8746]: E SendMessage mythcorecontext.cpp:305 (SetupCommandSocket) MythCoreContext: Problem connecting server socket to master backend



```


Thanks!

---

### Post by MrBackhand on 2015-03-28
I would like to point out that the mythbackend is starting up fine and I am able to connect to it through mythweb.  I can get the backend status, set recordings, delete files, all without a problem from the mythweb.  Only mythfrontend seems to be having the problem connecting to the database.

---

### Post by Lester_Burnham on 2015-03-28
You can change IP address in mythtv-setup (backend config). Maybe also check the contents of ~/.mythtv/config.xml & /etc/config.xml and make sure the passwords match the backend. If it's only a standalone system, you can use 127.0.0.1 for local ip and machine ip for master ip.

---

### Post by MrBackhand on 2015-03-29
Hi, thank you for responding.

I tried setting the IPv4 address and Master Backend address to 127.0.0.1, then made sure the config.xml files had the same. I also checked that the myth database password was correct and I still received the same mythfrontend error.  I also tried changing all of the IPs to the machine's static 192.* address and still had the same problem. I changed the bind address in /etc/mysql/conf.d/mythtv.cnf from 0.0.0.0 to 127 and 192. and no dice.  i feel like it's something simple i've missed.

---

### Post by Lester_Burnham on 2015-03-29
Hi,
So the frontend is not upgrading MySQL then crashing is it? There was an issue ages ago when upgrading from 0.25, where you needed to remove mythmusic for it to proceed. But looking at the log you pasted, it does look like connection problem.

---

### Post by MrBackhand on 2015-03-29
I think you are on the right track!  I did a quick check with apt-get and this was the message:

"The following packages have been kept back:  mythgallery mythmusic mythtv-common mythtv-frontend mythweb"

I then tried 'apt-get install myth-frontend' and received the error:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 mythtv-frontend : Depends: udisks
E: Unable to correct problems, you have held broken packages.

I am thinking I should do an "apt-get remove" then try "apt-get install udisks myth-frontend" but I am worried about making my MythTV situation worse.  I also checked the MythTV Control Center to make sure i selected the correct version of .27, and that was correct.  Below that option is a check box to "Activate Mythbuntu Updates Repository" but I am unclear if that includes MythMusic, etc, since there is a different window for that.  I do not remember if I had that selected before.   



What'cha think?

---

### Post by MrBackhand on 2015-03-29
Problem fixed.

I think when I selected the .27 branch in the MythbuntuTV Control Center I did not click the 'Refresh Available Repositories" button, though I am not sure. Anyway, what I had was two different versions of MythTV .27 between the front and backend. I followed the steps outlined here [http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa](http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa) uninstalling mythtv, and all of the dependencies, including apache2, php, and mysql. I refreshed all of the sources, then reinstalled mythtv* with apt-get which downloaded and installed everything back. The backend started up immediately after installation without error and I was able to connect with MythWeb. I ran MythFrontend and I was back in business, no data loss.  Wifey happy! :D 

Thanks!

---

### Post by Lester_Burnham on 2015-03-29
Glad you got it fixed. No one can live with un-happy wifey :)
In MCC I normally have the updates turned on, which I think updates all mythtv components. The other area you see myth music is where you can add or remove plugins.

---

