---
title: "Move Database to a different server other than the master backend"
date: 2013-04-03
forum: Mythbuntu
---

### Post by TheFuzz4 on 2013-04-03
Hey Everyone,

So in my network topology I have a MySql server running on a different server.  I would like to move my MythTV DB to this server instead of running it off of the backend for various reasons.  I have adjusted the two files located within the /etc/mythtv on the backend.  Then I shutdown the backend, shutdown the local MySql Server and start the backend back up.  However it never attempts to connect to the remote MySql server.  Yes I do have remote connections enabled on the MySql Server.  I'm also not sure if there are some files that I need to change for MythWeb as well in order to get it to go pull stats from the remote MySql server, or if I need to just install mythweb on the remote MySql server (although I think that would be a little counter productive as I wish to keep my MySql box as a remote connections server only and not run a webserver on it.  Thank you all in advance for your assistance with this.  I can't imagine that this is not possible but I must just be missing a setting somewhere in order to complete this migration.

---

### Post by flecki on 2013-04-04
I have read somewhere that the mysql.txt and config.xml files can be in several locations and should be the same everywhere - search for duplicates and change them all

---

### Post by TheFuzz4 on 2013-04-04
You are 100% correct.  I also had to update the config file located within /usr/share/mythtv.  

Then after doing that the backend connected to the Database but failed because I didn't have the Timezone data loaded.  Followed the guide here [http://www.mythtv.org/wiki/MySQL_Time_Zone_Tables]("http://www.mythtv.org/wiki/MySQL_Time_Zone_Tables") to load the data in to the database for the timezone stuff.  Once I did that I started the backend back up one more time and it connected right away with no issues.  

Once I was done with that I then had to get mythweb working.  In order to do that I had to edit the mythweb apache conf file located in /etc/apache2/sites-enabled and changed the database location there.  Once I was done with that mythweb made its connection to the database and I was back in business.  Now to go update my frontends with the new location as well.  Thank you for your help.

---

