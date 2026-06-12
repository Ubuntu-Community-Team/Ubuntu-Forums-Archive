---
title: "How do I get my Mythtv frontend to play a video or mp3 file from my server?"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by Scorpuk on 2007-06-03
I have set up Mythtv on my HTPC as a frontend / backend configuration. Server currently sits in the living room.

I am now trying to add another frontend to my bedroom.


The bit I am having difficulty in is setting up the new frontend to play any of the video files or mp3's I have sitting on the backend.

I get the full list as it sees it in the database, but it cannot locate the files.



Any help would be most appreciated.

---

### Post by wjston on 2007-06-03
> **Scorpuk said:**
> I have set up Mythtv on my HTPC as a frontend / backend configuration. Server currently sits in the living room.

I am now trying to add another frontend to my bedroom.


The bit I am having difficulty in is setting up the new frontend to play any of the video files or mp3's I have sitting on the backend.

I get the full list as it sees it in the database, but it cannot locate the files.



Any help would be most appreciated.

Are you trying to access the files through MythTV or through MythWeb?

---

### Post by wjston on 2007-06-03
> **Scorpuk said:**
> I have set up Mythtv on my HTPC as a frontend / backend configuration. Server currently sits in the living room.

I am now trying to add another frontend to my bedroom.


The bit I am having difficulty in is setting up the new frontend to play any of the video files or mp3's I have sitting on the backend.

I get the full list as it sees it in the database, but it cannot locate the files.



Any help would be most appreciated.

The information here might be of some help if your having connectivity problems. It is from the - " How To - Introduction to MythTV" by Andrew McNabb.

Configuring a Second Frontend

By default the MySQL server on the backend won't let you connect as the "mythtv" user from anywhere other than localhost. Go in and add a new "mythtv" user for the second frontend host, for a subnet wildcard host, or for the % host if you're firewalled off. Remember to "flush privileges." Test that you can connect as the mysql user by running "mysql -u mythtv -h [backend-server] -p" from the new host(s). If none of that made sense, read the MySQL documentation, particularly the MySQL Privileges section, until it does (it's really good documentation). [http://dev.mysql.com/doc/refman/5.0/en/index.html](http://dev.mysql.com/doc/refman/5.0/en/index.html)

Finally, modify the /usr/share/mythtv/mysql.txt file on the frontend computer to have the correct DBHostName, DBUserName, DBPassword, etc. Then mythfrontend should magically work, and you're off to client configuration, as described for the first frontend.

---

### Post by Scorpuk on 2007-06-04
Tnx for your replies.


I probably wasnt clear enough on my first post, but I have gone through the configuration of mysql etc.

Where I got up to on the second front end was:


Able to watch Live TV.
Able to watch Recorded Programs


Unable to listen to Music
Unable to watch Video Files (stored DVD's)


If I goto the video manager setup it says the files arent there and do I want to remove them from the database.



**[COLOR="Red"][SIZE="5"]BUT.[/SIZE][/COLOR]**

The one thing I havent done yet is :

> Finally, modify the /usr/share/mythtv/mysql.txt file on the frontend computer to have the correct DBHostName, DBUserName, DBPassword, etc. Then mythfrontend should magically work, and you're off to client configuration, as described for the first frontend.


I will try this out next time I'm home. ;)

---

### Post by Baka no Kami on 2007-06-06
I don't know if this is the best solution, but it's worked for me. I've got a backend only on my server and I'm running the frontend on my desktop.  My videos & music are on a USB drive connected to the server.  I shared the folder on the network, and mounted it locally.  In the video setup options I listed the local folder for the video directory. I still have to rebuild my tablet due to a dying HDD, so I haven't tested using the same setup on a 2nd frontend.

---

### Post by barney_1 on 2007-06-07
I would be inclined to mount the network shares as a local directory and use that location in mythvideo and mythmusic.  I should work just fine if you are using a unique identifier for each frontend so the directory settings for the new box don't effect those for your other boxes.

---

### Post by Scorpuk on 2007-06-12
I mounted the appropriate folders with the exact same folder path as the server and this looks to be working ok.

---

