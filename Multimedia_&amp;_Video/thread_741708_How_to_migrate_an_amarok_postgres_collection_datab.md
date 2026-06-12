---
title: "How to migrate an amarok postgres collection database to a new install."
date: 2008-04-01
forum: Multimedia &amp; Video
---

### Post by gkffjcs on 2008-04-01
These Instructions assume that you have configured your Amarok back end database like so:
          You have setup up the database in the way described in the first portion of this fine tutorial hosted on amarok wiki [http://amarok.kde.org/wiki/Postgresql_HowTo]("http://amarok.kde.org/wiki/Postgresql_HowTo")
and that you have given your database the name of amarokcollection. 
For this to work properly it is best that the paths to all of your music are the same on both machines. However, amarok will compensate for any differential by rescanning the collection,  the primary benefits of this process are to copy over podcast subscriptions.

Step 1: On the source computer you will dump your database into a text file like so:  

mkdir ~/Desktop/amac

chmod 777 ~/Desktop/amac

sudo su postgres
     
      pg_dump amarokcollection > /home/"your user name here"/Desktop/amac/amarokcollection

You should now have a text file in the directory amac on your desktop. The reason you made a new directory is because the command chmod 777 ~/Desktop/amac changes the permissions of the folder amac on your desktop giving all users write permissions to it and it's contents. This this could have  been a very big security problem if we ran the same command for the desktop directory itself. Therefore we minimize any risk by only doing what is needed and no more, in this case what is needed is one directory (amac) in a known location (on your desktop) with such loose permissions. 

Step 2: copy the file amarokcollection to the target computer through what ever means you have at your disposal to moving files between the computers, eg: a thumb drive, ssh, samba, or writable CD.  For simplicity sake make a directory on the target machines desktop called amac and put the file in it. 

Step 3: Once you have installed and configured postgres as per the tutorial linked to above on the target machine,  but before you configure amarok on the target machine run the following commands:

sudo su postgres
psql -d amarokcollection < /home/"your-user-name"/Desktop/amac/amarokcollection 
 
Now the final step is to connect amarok to the postgres amarokcollection database. As described in the tutorial I linked to above. You will find you collection fully imported, including podcasts and all. Also if you want to copy over the actual podcast files too you can copy the contents of ~/.kde/share/apps/amarok/podcast to the target machine.

---

