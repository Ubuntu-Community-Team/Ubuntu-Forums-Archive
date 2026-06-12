---
title: "Star Ratings for recorded programs"
date: 2014-05-24
forum: Mythbuntu
---

### Post by tezcooling on 2014-05-24
So for a while I've wanted all the programs I record to be updated with star ratings. Rather than doing my dissertation I wrote a script today to do just that.

It pulls down the ratings from tvdb.com and tmdb.com and puts them into the mythtv database.

Sorry the code is a bit scrappy, its my first proper python / mythtv script and I am by no means a programmer. But thought I would share it in case anyone was looking for something similar.

```

#!/usr/bin/python
# This simply updates all the recordings in your recorded database with star ratings from tvdb.com and tmdb.com
# Written by Tez Cooling

# MySQL database login information (for mythconverg database)
DATABASEUSER="mythtv"
DATABASEPASSWORD="your password in here"


#Get the movie data
import os, sys
import MySQLdb as mdb
from sys import argv

con = mdb.connect('localhost', DATABASEUSER, DATABASEPASSWORD, 'mythconverg')

with con:
    cur = con.cursor(mdb.cursors.DictCursor)
    cur.execute("SELECT * FROM recorded")
    rows = cur.fetchall()

    for row in rows:
        if row["inetref"] > 0:
                final = ""
                final2 = ""
                ref = row["inetref"]
                sea = row["season"]
                epp = row["episode"]
                chanid = row["chanid"]
                starttime = row["starttime"]
                recording = ("/usr/share/mythtv/metadata/Movie/tmdb3.py -D ", ref)
                recording2 = ("/usr/share/mythtv/metadata/Television/ttvdb.py -D ", ref, " ", str(sea), " ", str(epp))
                final = final.join(recording)
                final2 = final2.join(recording2)
                if sea and epp > 0:
                        mystring = os.popen(final2).readlines()
                        mystring = str(mystring)
                else:
                        mystring = os.popen(final).readlines()
                        mystring = str(mystring)
                #Extract just the user rating
                loc = mystring.find("<userrating>");
                loc = loc + 12
                locend = loc + 4
                userrating = mystring[loc:locend]
                userrating = userrating.replace("<", "");
                try:
                        sqlfinal = ""
                        userrating = float(userrating) / 10
                except ValueError:
                        print row["title"], " cannot be understood star rating ", userrating, " skipped"
                else:
                        print row["title"], " will be given ", userrating, " stars"
                        sql = "update recorded set stars='", str(userrating), "' where chanid='", str(chanid), "' and starttime='", str(starttime), "'"
                        sqlfinal = sqlfinal.join(sql)
                        cur.execute(sqlfinal)
                        con.commit()


        else:
                print "no inetref"
print "complete!"
con.close

```

---

