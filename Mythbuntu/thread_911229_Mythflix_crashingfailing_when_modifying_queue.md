---
title: "Mythflix crashing/failing when modifying queue"
date: 2008-09-05
forum: Mythbuntu
---

### Post by extension on 2008-09-05
My RSS feeds correctly show but when I try to modify my queue either nothing happens or x restarts.

When I ran netflix.pl the response was "Status Code: 200".

The only problem I could possibly imagine is that when inserting the MySql I may have used the wrong value for '[YOUR QUEUE NAME]' but I am not sure that even has any impact on the updating process.

Is there any way for me to get information on what is failing when I try to modify my queue so I can understand what the possible fix is?

---

### Post by jdeslip on 2008-11-22
I have the exact same problem - did you ever solve this??

---

### Post by fenian on 2008-11-23
You have to run the following command TWICE (username=your netflix account name password=your netflix account password)...

/usr/share/mythtv/mythflix/scripts/netflix.pl -L <username> <password>

It should return the status code 200,
I don'tknow why you have to enter the command twice but I was not able to edit the queue in Mythtv until I did.

---

