---
title: "[SOLVED] tv_grab_eu_epgdata doesnt save the PIN"
date: 2008-05-15
forum: Mythbuntu
---

### Post by nanofuzzy1 on 2008-05-15
Hi,

I installed the tv_grab_eu_epgdata succesfully with my PIN some days ago without problem and got all the data.

Now, mythfilldatabase shows:

2008-05-15 21:01:50.650 Connected to database 'mythconverg' at host: localhost
Sorry, your PIN is not defined. Run tv_grab_eu_epgdata --configure to fix this. at /usr/bin/tv_grab_eu_epgdata line 195.
2008-05-15 21:01:51.305 FAILED: xmltv returned error code 65280.
2008-05-15 21:01:51.306 Error in 1:1: unexpected end of file

I did it several times without succes. I even changed the permissions of the file (tv_grab_eu_epgdata) so that everybody can write. No change in the result. Could it be a problem in the mysql database?

What can I do?

Thanks for your help!

patrick

---

### Post by laga on 2008-05-15
Hi,

how are you running mythfilldatabase? You probably ran mythtv-setup as a different user.

---

### Post by nanofuzzy1 on 2008-05-15
I have a ubuntu desktop with frontend and backend - no myhtbuntu.

It worked some days ago and now it doesnt. AFAIK I didnt change anything concerning users but how could I find it out?

patrick

---

### Post by laga on 2008-05-15
What do the following two commands return:

```

ls -al ~/.mythtv/*xmltv
ls -al /home/mythtv/*xmltv

```

You should execute them in a shell as your normal user.

---

### Post by nanofuzzy1 on 2008-05-15
patrick@mythtv:~$ ls -al ~/.mythtv/*xmltv
-rw-r--r-- 1 patrick patrick 0 2008-05-08 21:29 /home/patrick/.mythtv/analog.xmltv
patrick@mythtv:~$ ls -al /home/mythtv/*xmltv
ls: Zugriff auf /home/mythtv/*xmltv nicht möglich: No such file or directory

---

### Post by laga on 2008-05-16
And how are you trying to run mythfilldatabase? It should work as your normal user. Does /home/patrick/.mythtv/analog.xmltv contain your PIN?

---

### Post by Titus A Duxass on 2008-05-16
When I run mythfilldatabase --manual in a terminal (as a normal user) I enter the pin (and what a pin it is!) but you don't get any confirmation that it is accepted, is that similar to your problem.

As an aside, when you ran it successfully did you get the encrpyted channels as well (i.e. BBC Prime, Nat.Geo., TCM) or just the free channels.

---

### Post by nanofuzzy1 on 2008-05-16
ad laga: the file exists but it is empty. So the answer is no:

-rw-r--r--  1 patrick patrick    0 2008-05-08 21:29 analog.xmltv
drwxr-xr-x  2 patrick patrick 4096 2008-04-30 20:34 channels
-rw-r--r--  1 patrick patrick  422 2008-05-16 09:21 config.xml
-rw-r--r--  1 patrick patrick 1122 2008-04-28 20:13 mysql.txt

EPGdata told me, they get a request from the grabber with my PIN, but he seems not to be able to download the data. They guess it is a problem with my firewall. I dont think so.

What about reinstalling the grabber? How can I do this?


ad titus:

The problem is that the grabber doesnt get the infos and the reason is - in his opinion - that the PIN is not configured.

Yes, I get also data for encrypted channels. But which channels are encrypted depends on the provider. EPGdata is just a tv journal.

---

### Post by nanofuzzy1 on 2008-05-16
Solved: In the backend I switched to another grabber and instantly back to tv_grab_eu_epgdata. Then, I had to insert the PIN and the other data again. This time it worked. I have an actual EPG now. No idea, why it worked, but the problem is solved.

Thank you for your help.

---

