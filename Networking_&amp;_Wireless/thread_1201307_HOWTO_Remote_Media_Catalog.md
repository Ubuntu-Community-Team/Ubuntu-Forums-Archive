---
title: "HOWTO: Remote Media Catalog"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by ronaldprettyman on 2009-07-01
This howto will explain how to access your system remotely for several different reasons. Including but not limited to.
[LIST]
Filesharing
Remote administration
Webhosting
Media Streaming[/LIST]
The first step is to setup your ssh server.
Before doing this make sure you have a strong password, especially for all users with sudoer permissions.
```
sudo apt-get install ssh
```
Next your want to forward port 22 from your router or modem.
I can't explain howto do this, but you should be able to figure it out. Your want your internal IP address first.
```
ifconfig eth0|grep inet|grep -v inet6

```
replacing eth0 with the network card you use to access the web. Note I don't recommend setting up a computer that access's the web wireless to be your server.
Now write down that address. Your want to make sure its a static address, but that is beyound this guide. You can find that information with google or in the forums.

Now with that address goto your router or modem, more then likely by replacing the last digit of your ip address with a one
So for example if your ip address is
192.168.100.2
Your router is probably 192.168.100.1
or if your address is
10.0.1.23 router would be 10.0.1.1
192.168.1.12 router 192.168.1.1
Now in the table your want to forward TCP traffic on port 22 to your ip address(some router this might show a drop menu with host name, in which case select your hostname).
Your also want to forward port 80 for your webserver.
Next your want to setup your database.
```
sudo apt-get install mysql-server
```
Write down the password you created
restart mysql server
```
sudo /etc/init.d/mysql restart
```

now were install the webserver
```
sudo apt-get install apache2 php5 libapache2-mod-php5 
```
Restart apache
```
sudo /etc/init.d/apache2 restart
```
test that the webserver works
```
sudo vi /var/www/index.php
```
put in the code
[PHP]<?php
phpinfo()
?>[/PHP]
save and in your browser goto
[http://localhost/index.php]("http://localhost/index.php")
you should see the php info page.
Now goto [http://www.dyndns.com/]("http://www.dyndns.com/")
Setup an account.
(This is for dealing with the fact that home internet connection usually have a dynamic ip that changes on a regular interval based on the ISP's DHCP server)
Once your account is setup your want to 
Add New Hostname
All the defaults work, pick your hostname and everything and select
Use auto detected IP address ###.###.###.###
Add to cart check out.
THIS IS FREE, IF IT ASK FOR MONEY YOUR NOT DOING IT RIGHT!!!
Defeats the whole purpose if you pay anything.
Once that is done.
Goto Support>DNS Tools>Update Client Configurator
Select the check box next to your hostname
and the dot box next to 
inadyn
Click generate
now copy and save that to a your favorite text edit and set it aside. Call it inadyn.conf save it on the Desktop

Now you need to install inadyn
```
sudo apt-get install inadyn
```
your want that file you just created and saved to the desktop as inadyn.conf
```
sudo cp ~/Desktop/inadyn.conf /etc/inadyn.conf
```
Now edit the file
```
vi /etc/inadyn.conf
```
Replace ##YOUR PASSWORD## with your password
For security purposes lets make sure no one but root can read the file.
```
sudo chmod g-r /etc/inadyn.conf
sudo chmod o-r /etc/inadyn.conf
```
now by default, well I don't really like the way inadyn handles it self and I find that it doesn't update as readily as I would like and striving for a higher uptime when remote is always key.
So were write two scripts. One to run the command at boot, and one to kill then rerun the command every 2 hours(every hour and your be black listed)
```
sudo vi /etc/init.d/inadyn
```
Insert this
```
#!/bin/bash
#Check to see if its running and add the pid to the variable $IS_IT_RUNNING
IS_IT_RUNING=`ps -A|grep inadyn|grep -v grep|awk '{print$1}'`
echo $IS_IT_RUNING
case $1 in
	start)
		#if its not running start it
		if [ $IS_IT_RUNING ]; then
			echo It is already running			
		else
			echo Starting
			/usr/sbin/inadyn &
		fi
	;;
	stop)
		if [ $IS_IT_RUNING ]; then
			kill $IS_IT_RUNING
		else
			echo It is not running
		fi
	;;
	restart)
		if [ $IS_IT_RUNING ]; then
			echo Stopping
			kill $IS_IT_RUNING
		fi
		echo Starting
		/usr/sbin/inadyn &
	;;
	force-stop)
		killall inadyn || true
		sleep 2
		killall -9 inadyn || true
		;;
	*)
		echo "Usage: /etc/init.d/inadyn {start|stop|restart|force-stop}"
		exit 1
	;;
esac
```
Save the script
Give it executable permissions
```
sudo chmod +x /etc/init.d/inadyn
```
Add it to the startup script
```
sudo update-rc.d inadyn defaults
```
Now where write another script to be run every two hours. To check if its already running, stop and then restart it.
```
sudo vi /usr/local/bin/inadyn.sh
```
Add this code to it
```
#!/bin/bash
#Check to see if its running and add the pid to the variable $IS_IT_RUNNING
#Replace GOOGLE.COM with your hostname from the dyndns.org
########################
DDNSHostName=GOOGLE.COM
########################
#Replace this with the location of the log file
########################
DDNSLogFile=/var/log/ddnds.log
########################
IS_IT_RUNING=`ps -A|grep inadyn|grep -v grep|grep -v .sh|awk '{print$1}'`
if [ $IS_IT_RUNING ]; then
	kill $IS_IT_RUNING
fi
/usr/sbin/inadyn &
#Determine Size of log file
DDNSSizOLF=`wc -l $DDNSLogFile|awk '{print$1}'`
#Maximum Size of Log File
MaxDNSLSize=100
if [ $DDNSSizOLF > $MaxDNSLSize ]; then
	mv $DDNSLogFile $DDNSLogFile.0
fi
#Appends a time stamp followed by the IP address of your hostname to the log file
##########################
date >> $DDNSLogFile
dig DDNSHostName|grep IN|awk '{print$5}' >> $DDNSLogFile
#########################

```
make it executable
```
sudo chmod +x /usr/local/bin/inadyn.sh
```
now add it to cron
```
sudo vi /etc/crontab
```
add the line
```
15 */2    * * *   root    /usr/local/bin/inadyn.sh
```
Change the 15 to something between 1 and 60 so were all not hitting dyndns at the same time and your update every two hours on that minute so if it was 12 then 2:12, 4:12 etc...
save that file and restart cron
```
sudo /etc/init.d/cron restart

```
Now you should be good to go with your hostname that your use to access your machine remotely.
At this point you have ssh, LAMP(linux apache, mysql, and php) and your hostname setup.
You can access your machine from anywhere. Just make sure your server has port 22 open if your using a firewall, by default ubuntu does not have this port blocked so you should be fine.
Note that you can also do file transfers with ssh though a client such as filezilla, on a quick connect just put port 22 or when setting up a host select secure file transfer ssh 22.

Now for your media. Your want to consolidate your media files if possible, Their is software to handle this but I won't go into that.
For the point of this HOWTO, lets assume all your music is located in two location.
Your linux collection is here
/home/YOURUSERNAME/Music
Your old files from Windows are here
/media/disk/Music

Your want to download ampache
First prepare your system
```
sudo apt-get install eyed3 gettext intltool-debian javascript-common libgd2-xpm libjs-prototype libmail-sendmail-perl libmcrypt4 libsys-hostname-long-perl libt1-5 php5-cli php5-gd php5-mcrypt php5-mysql phpmyadmin po-debconf python-eyed3 wwwconfig-common
```
If asked choose "apache2"
[http://ampache.org/download.php]("http://ampache.org/download.php")
Save it.
By default firefox saves to the desktop and I'll assume you downloaded 3.5.1 change if applicable
Move the archive to your /var/www folder
```
sudo mv ~/Desktop/stable.tar.gz /var/www
```
Extract the file
```
sudo tar -zxvf stable.tar.gz
```
Create a more userfriendly directory
```
sudo mv ampache-3.5/ ampache
```
now in your browser goto here
sudo mv ampache-3.5/ ampache
[http://localhost/ampache/install.php]("http://localhost/ampache/install.php")
Choose Start Configuration

Now remember the database information from earlier
follow the directions
On step two when you click write config and download box will pop up click save
then move to the config location
```
sudo mv ~/ampache.cfg.php /var/www/ampache/config/
```1359
Check for config, should get two Ok's
Continue to Step 3
Create your ampache account
Go to the admin section>Add Catalog
Call your first catalog Linux
Path /home/YOURUSERNAME/Music
Add Catalog
Then add another Catalog Windows
Path /media/disk/Music

You should now have everything setup. Note that you won't be able to access your remote hostname from your local area network. Theirs an easy fix for this. Just add a line to your /etc/hosts file
```
sudo vi /etc/hosts
```
at the bottom before the #The following lines..... add
```
127.0.0.1 YOURHOSTMAN.WHATEVER.COM
```
so if your host name was ubuntu.homelinux.com then you'd add that to the end line.
Now when you type in your browser [http://yourhostname.whatever.com/ampache](http://yourhostname.whatever.com/ampache) it will take you to the site.
You can go a step further and add a virtualhost to your apache2 configuration that defaults yourhostname to /var/www/ampache
Any questions or comments post them below

To test that everything is working, go through a proxy and try to reach your website though your hostname, ampache probably won't play music, but you should be able to see it, if this works it will work when you try to access it out side of your LAN as long as your net connection is up your computer is running and your ip has changed in the last two hours your be able to log in and stream music anywhere.

---

