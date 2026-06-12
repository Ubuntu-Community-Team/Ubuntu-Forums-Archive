---
title: "mythbuntu updates restore settings that dont work with my setup"
date: 2008-10-03
forum: Mythbuntu
---

### Post by oobe-feisty on 2008-10-03
I dont know how to post or where to post an official bug report so im posting it here over the last couple of days i have been setting up a remote frontend and after installing updates tonight it could not connect to database even though i could connect to mysql on the backend from the frontend all test's passed i was very puzzled making a dump file of mythfrontend running from the remote frontend i noticed 

2008-10-04 00:38:32.963 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-10-04 00:38:32.963 Connection timed out.
                        You probably should modify the Master Server
                        settings in the setup program and set the


so i ran mythtv setup and noticed that my ip address had reverted to the loopback address instead of NAT.


not only this but the first thing i discovered was that i had enabled myqsl over ethernet in mythbuntu-control-centre but after the update this had reverted back to disabled both of these settings are necesary to run a remote FE. 


im considering disableing mythtv updates until this is resolved does anyone know if this is a bug or is there i way i can work around this with out having to restore settings after each update

---

### Post by hempar on 2008-10-03
does MTD works after updates? I just posted MTD problem that i have after updates.It is little different but same situation.

---

### Post by oobe-feisty on 2008-10-03
> **hempar said:**
> does MTD works after updates? I just posted MTD problem that i have after updates.It is little different but same situation.

sorry i dont use MTD

---

### Post by laga on 2008-10-03
What updates did you install?

---

### Post by oobe-feisty on 2008-10-03
I use the mythbuntu 21 svn fixes repo however i just disabled it after this

---

### Post by laga on 2008-10-03
That's *very* odd.

Can you post the output of ```
echo "get mythtv/public_bind" | debconf-communicate
``` and your ~/.mythtv/mysql.txt file? Of course, make sure to remove the password.

---

### Post by oobe-feisty on 2008-10-03
> **laga said:**
> That's *very* odd.

Can you post the output of ```
echo "get mythtv/public_bind" | debconf-communicate
``` and your ~/.mythtv/mysql.txt file? Of course, make sure to remove the password.

echo "get mythtv/public_bind" | debconf-communicate 

password for oobe: debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied


this is the mysql.txt from the frontend 

DBHostName=192.168.0.10

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
#DBHostPing=no

DBUserName=mythtv
DBPassword=fakepasswords
DBName=mythconverg
DBType=QMYSQL3

# Set the following if you want to use something other than this
# machine's real hostname for identifying settings in the database.
# This is useful if your hostname changes often, as otherwise you
# will need to reconfigure mythtv (or futz with the DB) every time.
# TWO HOSTS MUST NOT USE THE SAME VALUE
#
#LocalHostName=my-unique-identifier-goes-here

# If you want your frontend to be able to wake your MySQL server
# using WakeOnLan, have a look at the following settings:
#
#
# The time the frontend waits (in seconds) between reconnect tries.
# This should be the rough time your MySQL server needs for startup
#
#WOLsqlReconnectWaitTime=0
#
#
# This is the number of retries to wake the MySQL server
# until the frontend gives up
#
#WOLsqlConnectRetry=5
#
#
# This is the command executed to wake your MySQL server.
#
#WOLsqlCommand=echo 'WOLsqlServerCommand not set'

---

### Post by oobe-feisty on 2008-10-14
just letting you know it happened again both in mythtv-setup and mythbuntu-control-centre but i was ready for it

---

### Post by laga on 2008-10-15
When exactly does this problem happen? Every time you get new MythTV packages?

---

### Post by oobe-feisty on 2008-10-18
yeah the last few but i only setup a remote frontend between now and the last few so it could of been like that the whole time however i just removed weekly builds packages and reinstalled the main packages so we will see what happens in future

---

### Post by loser28 on 2008-10-18
buntu2  [http://www.free-prepaid.com/?id=75351748](http://www.free-prepaid.com/?id=75351748)  :lolflag:

---

### Post by oobe-feisty on 2008-11-10
what i did was restore my sources back to the main repo then i uninstalled myth binaries then i reninstalled them then i added the weekly builds repo and now it wont revert my settings.

i think the problem was i had no remote frontend when i setup weekly builds and thats why it was not saving my changes on updates so when i did the above process it now recognises the settings and does not revert

---

