---
title: "How to install Subsonic as a non-root user on Ubuntu 10.04"
date: 2011-01-02
forum: Multimedia Software
---

### Post by OM NOM NOM on 2011-01-02
NOTE:These instructions were compiled from  several sources and tweaked/updated  by me where needed. Thanks to  Zachary Lund from Lundscape.com, Baaldemon and Sean P. Keown from the  Subsonic forums, The Apache Tomcat FAQ and of course Andre for doing the  actual heavy lifting [IMG]http://www.activeobjects.no/subsonic/forum/images/smiles/icon_smile.gif[/IMG] 
From Zachary Lund from [http://blog.lundscape.com/2009/05/install-subsonic-on-ubuntu-server/comment-page-1/#comment-11745](http://blog.lundscape.com/2009/05/install-subsonic-on-ubuntu-server/comment-page-1/#comment-11745) 
 
Since I'm somewhat of a novice, I used the Ubuntu Desktop edition and  set it up as a server.  I installed Nomachine's NX Server to get remote  access to the GUI when I needed it. [Http://www.nomcahine.com]("http://www.nomcahine.com/") . You'll need to also install openSSH from the repositories to get NX to work. 
 
 
Why would I want to go through the trouble of doing this when I can just download and install the .deb file from Subsonic?  
 
Because by default the .deb file will install as root, which is a  significant security risk if you are going to enable external access to  the server.  Using this method will install Apache/Subsonic as an  unprivileged user, limiting the ability of an attacker to compromise  your system. It is also recommended to use port-forwarding on your  router from a non-standard port to port 8080 (or whatever port you set  up, default is 8080) internally on your Tomcat/Subsonic server.  
 
What's the advantage of using the Apache Tomcat version in the Ubuntu  repositories rather than downloading and installing it directly from  Apache.org? 
 
Security and convenience. Since you can install it from the repositories  in Synaptic the initial setup is much easier. But most importantly it  creates a user called tomcat6 and runs under that rather than root,  which makes things a lot more secure. However if you are experienced  Tomcat user and would rather use the traditional install that'll  certainly work too.  
 
What is Apache's Tomcat anyway? 
Tomcat is a free, open source web server specifically designed to run Java-based applications like Subsonic.  
More info can be found at: 
[http://tomcat.apache.org/](http://tomcat.apache.org/) 
 
1. Install the necessary Java packages, Tomcat, and Lame: 
 
apt-get install java-common sun-java6-bin sun-java6-jdk sun-java6-jre 
apt-get install tomcat6 
apt-get install lame 
 
2. Stop Tomcat before changing the Tomcat configuration and installing the Subsonic web application. 
 
/etc/init.d/tomcat6 stop 
 
NOTE: in the Ubuntu repo version of tomcat6 this should be turned off by  default, making this next step unnecessary. You may just want to check  /etc/init.d/tomcat6 to make sure. If not, the steps below should correct  it. 
 
cd /etc/init.d/ 
mv tomcat6 tomcat6.bak 
sed "s/TOMCAT6_SECURITY=yes/TOMCAT6_SECURITY=no/" tomcat6.bak > tomcat6 
chmod +x tomcat6 
rm tomcat6.bak 
 
3. Download and extract the Subsonic 4.2 WAR file: 
 
[http://sourceforge.net/projects/subsonic/files/subsonic/4.2/subsonic-4.2-war.zip/download](http://sourceforge.net/projects/subsonic/files/subsonic/4.2/subsonic-4.2-war.zip/download) 
 
4. Go to the directory where you downloaded the file. (in this case my Firefox Downloads folder): 
 
cd /home/user/Downloads 
 
5. Unzip and move subsonic.war into the webapps directory: 
 
unzip subsonic-4.2-war.zip -d subsonic 
mv subsonic/subsonic.war /var/lib/tomcat6/webapps/ 
 
6. Subsonic expects certain directories to exist. The following creates those directories and sets the permissions. 
 
mkdir /var/subsonic 
mkdir /var/subsonic/playlists 
mkdir /var/subsonic/transcode 
chown -R tomcat6:nogroup /var/subsonic 
 
7. Subsonic uses Lame to transcode/compress mp3s for streaming. The next two lines make Lame available to Subsonic: 
 
cd /var/subsonic/transcode 
ln -s /usr/bin/lame lame 
 
8. Now start Tomcat again: 
/etc/init.d/tomcat6 start 
 
Subsonic should now be running and available at [http://localhost:8080/subsonic/.]("http://localhost:8080/subsonic/")  The port might vary depending on the installation of Tomcat. Log in.  You can change the password by clicking on “Settings” and then “Users”  and then selecting the admin account. 
 
How do I override the default home page loaded by Tomcat? 
 
If you are using port forwarding for external access to your Subsonic  server, you'll want your Subsonic login page to come up as the default  “index” page rather than a subdirectory from the root URL in order for  forwarding to work properly. Here's how. 
 
From: 
[http://wiki.apache.org/tomcat/HowTo#How_do_I_override_the_default_home_page_loaded_by_Tomcat.3F](http://wiki.apache.org/tomcat/HowTo#How_do_I_override_the_default_home_page_loaded_by_Tomcat.3F) 
 
After successfully installing Tomcat, you usually test it by loading [http://localhost:8080]("http://localhost:8080/")  . The contents of that page are compiled into the index_jsp servlet.  The page even warns against modifying the index.jsp files for this  reason. Luckily, it is quite easy to override that page. Inside  $TOMCAT_HOME/conf/web.xml there is a section called  <welcome-file-list> and it looks like this:  
    <welcome-file-list> 
        <welcome-file>index.html</welcome-file> 
        <welcome-file>index.htm</welcome-file> 
        <welcome-file>index.jsp</welcome-file> 
    </welcome-file-list> 
The default servlet attempts to load the index.* files in the order  listed. You may easily override the index.jsp file by creating an  index.html file at $TOMCAT_HOME/webapps/ROOT. It's somewhat common for  that file to contain a new static home page or a redirect to a servlet's  main page. A redirect would look like:  
<html> 
 
<head> 
<meta http-equiv="refresh" content="0;URL=http://mydomain.com/some/path/to/servlet/homepage/"> 
</head> 
 
<body> 
</body> 
 
</html> 
This change takes effect immediately and does not require a restart of Tomcat.

---

### Post by MReptile on 2012-04-10
You made my day, mate

Do you know furthermore how to make subsonic work with my own SSL Certificate, that I bought recently?

Greetings 

MReptile

---

