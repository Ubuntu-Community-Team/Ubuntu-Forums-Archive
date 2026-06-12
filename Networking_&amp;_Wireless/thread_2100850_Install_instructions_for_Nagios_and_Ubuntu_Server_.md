---
title: "Install instructions for Nagios and Ubuntu Server 12.04"
date: 2013-01-03
forum: Networking &amp; Wireless
---

### Post by psyllex on 2013-01-03
**INSTRUCTIONS FOR RUNNING NAGIOS 3.4.1 ON UBUNTU SERVER 12.04 L.T.S**
Alright here's what I did in order to get Nagios up and running on a physical machine.  Should work for Virtual Machines I presume.  
I started with a blank Ubuntu 12.04 L.T.S Server that I only installed OpenSSH and Virtual Machine Hosts through the tasksel menu during installation.  

Then I followed the instructions as such (when I put a ** by something this is where I deviated a bit from Nagios installation instructions which I will include the link to; it's also a few of the comments above this one.  Maybe page 2 or something on this thread.)

**link to nagios instruction set:  [http://assets.nagios.com/downloads/nagioscore/docs/Installing_Nagios_Core_From_Source.pdf](http://assets.nagios.com/downloads/nagioscore/docs/Installing_Nagios_Core_From_Source.pdf)

[from command line]
sudo -i
**had to split up this install command as it wasnt' working the way it was written in the docs
[b][i][color=#8000BF]sudo apt-get install wget  (this is already installed but just to be careful)
(sudo isn't implicitly necessary but this is the way they wrote them so I just included it; but your running as root with the sudo -i the whole time)
sudo apt-get install build-essential
sudo apt-get install apache2 php5-gd
sudo apt-get install libgd2-xpm libgd2-xpm-dev libapache2-mod-php5[/color][/i][/b]

cd /tmp
wget [http://prdownloads.sourceforge.net/sourceforge/nagios/nagios-3.4.1.tar.gz](http://prdownloads.sourceforge.net/sourceforge/nagios/nagios-3.4.1.tar.gz)
wget [http://sourceforge.net/projects/nagiosplug/files/nagiosplug/1.4.15/nagios-plugins-1.4.15.tar.gz](http://sourceforge.net/projects/nagiosplug/files/nagiosplug/1.4.15/nagios-plugins-1.4.15.tar.gz)

useradd nagios
groupadd nagcmd
usermod -a -G nagcmd nagios

tar zxvf nagios-3.4.1.tar.gz
tar zxvf nagios-plugins-1.4.15.tar.gz

cd nagios
**I split up the following into two commands as well, not sure why it worked this way but it did.  Make sure to keep the ./configure in both.
[b][i][color=#8000FF]./configure --with-nagios-group=nagios --with-command-group=nagcmd 
./configure --with-mail=/usr/bin/sendmail[/color][/i][/b]

make all
make install
make install-init
make install-config
make install-commandmode
make install-webconf

cp -R contrib/eventhandlers/ /usr/local/nagios/libexec/
chown -R nagios:nagios /usr/local/nagios/libexec/eventhandlers
/usr/local/nagios/bin/nagios -v /usr/local/nagios/etc/nagios.cfg

**After all that you should see something similar to the following: 
[color=#FF0000][i]Nagios Core 3.4.1
Copyright (c) 2009-2011 Nagios Core Development Team and Community Contributors
Copyright (c) 1999-2009 Ethan Galstad
Last Modified: 05-11-2012
License: GPL

Website: [http://www.nagios.org](http://www.nagios.org)
Reading configuration data...
   Read main config file okay...
Processing object config file '/usr/local/nagios/etc/objects/commands.cfg'...
Processing object config file '/usr/local/nagios/etc/objects/contacts.cfg'...
Processing object config file '/usr/local/nagios/etc/objects/timeperiods.cfg'...
Processing object config file '/usr/local/nagios/etc/objects/templates.cfg'...
Processing object config file '/usr/local/nagios/etc/objects/localhost.cfg'...
   Read object config files okay...

Running pre-flight check on configuration data...

Checking services...
	Checked 8 services.
Checking hosts...
	Checked 1 hosts.
Checking host groups...
	Checked 1 host groups.
Checking service groups...
	Checked 0 service groups.
Checking contacts...
	Checked 1 contacts.
Checking contact groups...
	Checked 1 contact groups.
Checking service escalations...
	Checked 0 service escalations.
Checking service dependencies...
	Checked 0 service dependencies.
Checking host escalations...
	Checked 0 host escalations.
Checking host dependencies...
	Checked 0 host dependencies.
Checking commands...
	Checked 24 commands.
Checking time periods...
	Checked 5 time periods.
Checking for circular paths between hosts...
Checking for circular host and service dependencies...
Checking global event handlers...
Checking obsessive compulsive processor commands...
Checking misc settings...

Total Warnings: 0
Total Errors:   0

Things look okay - No serious problems were detected during the pre-flight check[/i][/color]


**So now you start up Nagios
/etc/init.d/nagios start

**Set a password...this may not work (it hiccuped for me a couple times) so follow the alternate instructions if you don't see "Set password" after you issue the command
htpasswd -c /usr/local/nagios/etc/htpasswd.users nagiosadmin
**OR
**Alternate instructions
[color=#8000BF][i][b]cd /usr/local/nagios/etc 
htpasswd -c htpasswd.users nagiosadmin[/b][/i][/color]

cd /tmp/nagios-plugins-1.4.15
./configure --with-nagios-user=nagios --with-nagios-group=nagios
make
make install

ln -s /etc/init.d/nagios /etc/rcS.d/S99nagios

**At this point you should be done and should be able to use your browser using [http://<your nagios ip>/nagios ] and everything should be running well.  But for **myself it didn't work this way.  So I did the following

[color=#8000BF][b][i]exit

sudo reboot[/i][/b][/color]

wait 5-10 mins for it to restart.

**if you try these commands to check if Nagios is running you may get a positive on the first and a definite "Config error" on the service nagios start
[b][i]ps aux | grep bin/nagios (to check if it's running)
service nagios start (will start nagios)[/i][/b]

**But here I then used my browser on my windoz machine and used the command:
http://<your.nagios.server.ip>/nagios 

**And at this point is was up and running like a charm
**You can run the ***ps aux | grep bin/nagios*** & ***service nagios start*** commands now and you will get positives on both of them.  I have no idea why it gives negative the first run before and after rebooting but this is how I got it to work on 3 servers using these exact instructions.  It may be I just didn't wait long enough.  Perhaps some of the Nagios guys can give some feedback on this.  Again thank you to[color=#00BF00] jsmurphy & sreighardt[/color] who were a great help and very patient with me throughout this process.  I will post this up in the Ubuntu forum as I saw more than a few people on there who were having trouble.  So hopefully it helps everyone out. :guitar:

---

### Post by Raafat1991 on 2013-02-02
Thanks that was useful .

---

### Post by davidvan on 2013-02-03
Cant thank you enough for this. Nagios is a wonderfull tool and I can not wait to get started on it. 

Have you managed to incorporate one of the configuration tools? i.e. Nconf, NagiosQL? 

I have tried to implement both with no success. 
I've noticed that the ubuntu rep for nagios3 has different paths then by installing the src version. 

Do you happen to have any instructions for either of those tools? Or how are you configuring your nagios with hosts services etc?

Huge thanks.
DVR

---

### Post by psyllex on 2013-02-04
> **davidvan said:**
> Cant thank you enough for this. Nagios is a wonderfull tool and I can not wait to get started on it. 

Have you managed to incorporate one of the configuration tools? i.e. Nconf, NagiosQL? 

I have tried to implement both with no success. 
I've noticed that the ubuntu rep for nagios3 has different paths then by installing the src version. 

Do you happen to have any instructions for either of those tools? Or how are you configuring your nagios with hosts services etc?

Huge thanks.
DVR
Unfortunately I haven't had any time yet.  But I'm working on a few things soon so I'll write those up when I get a chance!

---

### Post by breaker84i on 2013-05-06
this is great guide..
i follow 100% and it works..
should replace the one in nagios site - [Installing Nagios Core From Source]("http://assets.nagios.com/downloads/nagioscore/docs/Installing_Nagios_Core_From_Source.pdf")

---

