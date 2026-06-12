---
title: "Mythtv Database problem"
date: 2009-07-02
forum: Mythbuntu
---

### Post by z3ro-kam on 2009-07-02
I have two mythtv systems they have been working great for over a year now. I very rarely watch tv on the backend a few weeks ago I went to watch tv on the backend and nothing showed up in my recordings. I log into my front end and all of my recordings show up there is there a separate database for the frontend and if so how can I copy it to my backend so I can watch my recordings. I just find it weird all of my recordings are stored on my backend but I cant watch them from there.

---

### Post by Das Hammer on 2009-07-02
Perhaps it is not looking at it's own database.

When you are running the frontend on your backend machine, can you see guide data? This would tell you if that machine is looking in the right place for the database.

Utilities/Setup - Setup - General - 1st screen is where you'll find the settings to tell the frontend program to look for the database.

---

### Post by z3ro-kam on 2009-07-06
Yes I do see the gide data. it is set to the ip address of my backend server for the database

---

### Post by crez79 on 2009-07-06
Check the recording filter. Assuming you haven't changed the default key assignments, hit 'm' and make sure the filter is such that you can see what you want. Somehow mine got changed to deleted one time and all I could see were the shows I swear I had watched and deleted already...

---

### Post by z3ro-kam on 2009-07-06
Thank you crez79 that fixed the problem now I can see all the shows

---

