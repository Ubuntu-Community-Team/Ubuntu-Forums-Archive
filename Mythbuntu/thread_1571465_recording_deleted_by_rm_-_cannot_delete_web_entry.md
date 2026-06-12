---
title: "recording deleted by rm - cannot delete web entry"
date: 2010-09-09
forum: Mythbuntu
---

### Post by panash on 2010-09-09
Did a silly thing, removed a recording by the rm *.mpg in the recordings directory - now I cannot delete it in the mythweb interface.
 
(I did this after a reinstallation to remove old recordings that did not appear in the webmyth interface)
 
Help
 
Thnx
 
PN

---

### Post by ian dobson on 2010-09-09
Hi,

Delete the screwed recordings from the MythFrontend. Mythweb first tries to delete the file from the fs then when that worked it cleans up the database.

Another solution would be just to create a file with the correct name (the recording name) and then delete it through mythweb.

Regards
Ian Dobson

---

### Post by panash on 2010-09-10
Thnx for the reply,

Just a couple of snags, I'm using Mythbuntu in backend only - I use a windows based MPEG editor (Videoredo) to pull recordings from the Mythbuntu m/c & then deleting using the mythweb i/f.

And the second snag is how do I reconstitute the original file name?

PN

---

### Post by DemonBob on 2010-09-10
First try to delete the file from mythweb again, then check /var/log/mythtv/mythbackend.log on the backend server you have. You should see errors towards the bottom of the log file mentioning the recording name. Usually it will be something like this 1053_0304099494.mpg


Then cd to the directory where your recordings are stored. By default they are stored in /var/lib/mythtv/recordings But you may have changed that on your install. 

Once you are in the recordings directory. 

```
sudo touch FILE_NAME_FROM_LOG
```

You may have to change the owner to the mythtv user, once you create the file. 

Do an ls -la command to see what the owner and group is on the other recordings, by default this is user mythtv group mythtv

Sample output of ls -la, where it says mythtv mythtv that is the owner and group you need to use in the next command 

```
-rw-r--r--  1 mythtv   mythtv 2333433792 2010-09-09 11:00 1028_20100909100000.mpg
-rw-rw-rw-  1 mythtv   mythtv      89621 2010-09-09 11:25 1028_20100909100000.mpg.png
-rw-r--r--  1 mythtv   mythtv 2340052928 2010-09-09 14:00 1028_20100909130000.mpg
-rw-rw-rw-  1 mythtv   mythtv     115738 2010-09-09 14:26 1028_20100909130000.mpg.png
-rw-r--r--  1 mythtv   mythtv 2336698304 2010-09-10 10:00 1028_20100910090000.mpg
-rw-rw-rw-  1 mythtv   mythtv     113058 2010-09-10 10:52 1028_20100910090000.mpg.png
-rw-r--r--  1 mythtv   mythtv 2333226944 2010-09-10 11:00 1028_20100910100000.mpg
-rw-rw-rw-  1 mythtv   mythtv     122066 2010-09-10 11:51 1028_20100910100000.mpg.png

```

Then run this command. 

```
sudo chown YOU_OWNER:YOUR_GROUP FILE_NAME_FROM_LOG
```

Proceed to mythweb and try to delete the file.

---

### Post by panash on 2010-09-11
nailed the SOaB! Whose the daddy now! Thnx guys.

It was a needle in a haystak to find the exact string I needed (it started a couple of minutes after 9pm so there was a 2102 end to the string.

How do I trim this huge file? I think its grown to a huge file because I live in a fringe area (Freeview predictor tells us that there should be no reception where we live) .

PN

---

### Post by ian dobson on 2010-09-12
> **panash said:**
> nailed the SOaB! Whose the daddy now! Thnx guys.

It was a needle in a haystak to find the exact string I needed (it started a couple of minutes after 9pm so there was a 2102 end to the string.

How do I trim this huge file? 


echo > FILENAME

regards
Ian Dobson

---

### Post by winewood on 2011-04-20
Greetings,
 
I deleted a few MONTHS of data from my directory after rebuilding my system.  I had to find a way to do a few hundred shows.  Just wanted to share my method.
 
 
mysql -u root mythconverg -p
mysql> use mythconverg 
mysql> select basename from recorded where progend like  "2011-01-%" ;

I copied all the names from the output into a file called deletelist.
Edit the file to remove the | in it.  (yes, I didn't know an efficient way to do that)
 
run the following as root, you can substitute the /opt/livetv with your recordings directory:
 
for x in `cat deletelist`
do
echo > /opt/livetv/$x
chmod 777 /opt/livetv/$x
done

Then in mythweb you can delete away anything from January.
 
Why did I not simply delete from the database with that command??  I couldn't be sure when deleting recorded (delete from recorded where progend like "2011-01-%") would have left other linked records orphaned, and I knew the webpage would remove it completely.
 
Others, feel free to correct where I could have made this more simple.  Can you simple delete the recorded rows and be fine?

---

### Post by ian dobson on 2011-04-20
Hi,

No you also need to delete the entries from the seek table.

Have a look on my webpage, I have written a small perl script that checks the mythtv database.

Regards
Ian Dobson

---

### Post by nickrout on 2011-04-20
The script provided in the wiki ```
find_orphans.py 
```works well. It can be downloaded via ```
mythwikiscripts
```

---

### Post by winewood on 2011-04-20
I love you guys.. many thanks!

---

