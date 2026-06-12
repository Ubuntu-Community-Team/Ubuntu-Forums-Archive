---
title: "grive error usage with google drive, permission denied"
date: 2012-11-25
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2012-11-25
> scott@scott-P5QC:/tmp$ grive
Reading local directories
exception: boost::filesystem::directory_iterator::construct: Permission denied: "./pulse-PKdhtXMmr18n"


so what to do now?
I installed grive and got the authentication code by running 
grive -a

then your supposed to run grive.
enticing info here
[http://www.geek.com/articles/news/grive-a-free-open-source-google-drive-client-has-arrived-on-linux-20120524/](http://www.geek.com/articles/news/grive-a-free-open-source-google-drive-client-has-arrived-on-linux-20120524/)

binary source here
[http://www.ubuntuupdates.org/ppa/webupd8?dist=precise](http://www.ubuntuupdates.org/ppa/webupd8?dist=precise)

---

### Post by sdowney717 on 2012-11-25
Did not have enough info, now it is running

[http://followthegeeks.com/how-to-sync-google-drive-with-linux-without-using-google-docs-fs/](http://followthegeeks.com/how-to-sync-google-drive-with-linux-without-using-google-docs-fs/)

anyone use grive?

---

### Post by sdowney717 on 2012-11-25
what it doing now is taking all my google drive files and copying them to a directory called GoogleDrive which I dont know If I like that.

They are some picture files I uploaded to google drive on the web as a test. This means I will have duplicate copies on my local PC, some in Pictures folder, and some in GoogleDrive folder.

It will be interesting to see how it syncs. Ideally you should discard your duplicates in the Pictures folder, etc...

---

### Post by sdowney717 on 2012-11-25
example here
```
sync "./97047.pdf" created in remote. creating local
sync "./p43.pdf" created in remote. creating local
sync "./techup08_web.pdf" created in remote. creating local
sync "./ClassicBoatVarnishTestMarch2008.pdf" created in remote. creating local
Finished!

this is where I added a new folder and put in a file
then reran grive which then resyncs to match the changes.
It wont sync until you run grive

scott@scott-P5QC:~/GoogleDrive$ grive 
Reading local directories
Synchronizing folders
Reading remote server file list
Detecting changes from last sync
Synchronizing files
sync "./grivetest" doesn't exist in server, uploading
sync "./grivetest/SS850463.JPG" doesn't exist in server, uploading
Finished!
scott@scott-P5QC:~/GoogleDrive$ 

```

---

