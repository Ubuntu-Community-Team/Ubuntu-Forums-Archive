---
title: "Newby installation problem"
date: 2008-08-15
forum: Mythbuntu
---

### Post by Julian15 on 2008-08-15
I am trying to install Mythbuntu 8.04 on an old Samsung laptop (while waiting for my new hardware to arrive). I am completely new to this and linux in general. I am having problems with the backend / mythfilldatabase config. I have installed a basic front end and back end I think (the installation manual does not show the same menus as the actual install software). When I run backend setup I get an error : no PnP backends found. I am then presented with the database config, which always fails (if I select the defaults or the values shown in mysql.txt). I get "Cannot log into database". I then get a prompt for mythfilldatabase which also ends in "cannot log in to database".
When I installed the system I was not connected to any network so left the DHCP config option; is this causing this database issue. What databases do I need to receive and watch TV anyway ?

---

### Post by funkydan2 on 2008-08-16
Do you have mysql installed and running?

Open up a terminal and run
```
sudo /etc/init.d/mysql status
```
and post the output here.

---

### Post by JulianE10 on 2008-08-17
> **Julian15 said:**
> I am trying to install Mythbuntu 8.04 on an old Samsung laptop (while waiting for my new hardware to arrive). I am completely new to this and linux in general. I am having problems with the backend / mythfilldatabase config. I have installed a basic front end and back end I think (the installation manual does not show the same menus as the actual install software). When I run backend setup I get an error : no PnP backends found. I am then presented with the database config, which always fails (if I select the defaults or the values shown in mysql.txt). I get "Cannot log into database". I then get a prompt for mythfilldatabase which also ends in "cannot log in to database".
When I installed the system I was not connected to any network so left the DHCP config option; is this causing this database issue. What databases do I need to receive and watch TV anyway ?
Status reply :-
Server v. 5.0.51a-3ubuntu5.1
protocol v. 10
connection localhost via UNIX socket
Unix skt /var/run/mysqld/mysqld.sock
uptime 7m28s

please excuse the abreviations, could not find a txt editor to paste the terminal o/p to. I am using a different machine to access this forum.

Many thanks, Julian.

---

### Post by vlaporte on 2008-08-19
Dear Newby,
I have installed Mythbuntu 8.04 several times, but am no expert. The database you note is used to obtain channel info and create a data base (TV Guide) of what is on each TV channel for the next 13 days. This info allows you to schedule recordings of future programs. You need to buy a membership in schedules direct to get this info off their website. 
[http://www.schedulesdirect.org](http://www.schedulesdirect.org)
You might start with a two month trial membership to see if you like MythTV. I found a book - Practical MythTV by Stewart Smith & Michael Still - very useful. Of course, they write from Australia and use TVFORMAT: PAL but we in USA use TVFORMAT: NTSC. There a few other differences but substantially accurate. 
I wonder if you need to reinstall Mythbuntu with your laptop connected to a network to setup your network properly.
Luck,
Vince

---

### Post by JulianE10 on 2008-08-20
Vince, thank you for the reply. I have since received my new hardware, a P4 3.06HT desktop. However I still have exactly the same database config issues. I did a google search and found I am not alone with this issue, it seems to be a problem with passwords but there was no proposed solution. I am confused as to why all my installation attempts (v8.04) differ from the pdf installation manual in several places (e.g. where is the standard / advanced install option ?). I have tried to find a previous v7 build but it is not available. I don't want to give up on this but am getting frustrated at what is probably simple for an expert to solve. Regarding the use of the databases for EPG I want to use the live (over the air) DVB-T EPG here in the UK rather than using web EPG data. In fact I do not want to connect the box to the internet to avoid all the hassle with virus scanning, trojans etc.

---

### Post by Alfaroid on 2008-08-20
Julian,

> **JulianE10 said:**
> .....I have tried to find a previous v7 build but it is not available. .....

You can find V7 downloads here: [http://mirror.internode.on.net/pub/mythbuntu/](http://mirror.internode.on.net/pub/mythbuntu/)

Greetings,

Alfaroid

---

### Post by ahood on 2008-08-20
> **Julian15 said:**
> When I run backend setup I get an error : no PnP backends found. I am then presented with the database config, which always fails (if I select the defaults or the values shown in mysql.txt). I get "Cannot log into database". I then get a prompt for mythfilldatabase which also ends in "cannot log in to database".
When I installed the system I was not connected to any network so left the DHCP config option; is this causing this database issue. What databases do I need to receive and watch TV anyway ?

I hope I can be of some help because I have had similar experiences. There are multiple reasons for the error message described, some of which I will try to present, and hopefully, will lead to a solution.

**(1) Myth Backend not running.**
It is possible that the error described above is due to the backend not running. This seems unlikely because the status command (sudo /etc/init.d/mysql status) indicates that the backend is running. Another way to ensure that the backend is running is to restart it and/or start it with the following commands.

Restart Myth Backend
> sudo /etc/init.d/mysql restart

Start Myth Backend
> sudo /etc/init.d/mysql stop


**(2) Myth frontend does not see the backend.**
In order for the frontend to see the backend, the front end needs to know the DBHostName, which can be either an IP address of the backend, or if the frontend is running on the same machine as the backend, then 'localhost' could work. 

Which to use? An IP address or localhost for DBHostName? The answer depends on how the backend is setup. 

_Myth Backend With IP Address:_ If the backend is setup with an IP address, then the frontend must use the IP address.  Plus, if an IP address is used for the configuration of the backend, then the machine must be connected to a local network. This is true even if the frontend exists on the same machine running the backend. 

_Myth Backend With Localhost:_ If the backend is configured with localhost, then localhost must also be used in the configuration of the frontend. This will only work if the frontend is running on the same machine as the backend.

I recommend doing the following:

First, check the backend settings by entering the following command in a terminal.

> sudo mythtv-setup

If this command does not work, then try...

> sudo /usr/bin/mythtv-setup

Then use the arrow keys on the keyboard to select **General** and verify whether the backend is using the IP address or localhost on the first screen presented.

Second, check whether DBHostName is correct in the frontend configuration screen. 

Launch the frontend by entering the following command in a terminal...

> sudo mythfrontend

Use the arrows on the keyboard to select General and the DBHostName.

It is also possible to check the frontend settings by reading the content of the mysql.txt file.

**3. Myth frontend cannot communicate with the backend.**
This could result because the database name and password in the frontend configuration does not match the backend. Repeat step 2 above to verify the the database name (usually converg) and password match in the frontend and backend.

**4. Administrator Privileges**
The last cause for the message described above is related to the administrator password that Ubuntu will ask for when performing an administrative task, such as executing mythfilldatabase. Be sure to enter the user password and not the mysql database password when executing tasks like mythfilldatabase.

I hope some of the back will lead to a solution.

Al

---

