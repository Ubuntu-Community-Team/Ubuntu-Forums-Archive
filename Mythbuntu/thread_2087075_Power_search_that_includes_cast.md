---
title: "Power search that includes cast?"
date: 2012-11-22
forum: Mythbuntu
---

### Post by ubnewbie2 on 2012-11-22
What do I add to a power search so that it will check for the string in the list of cast members for a movie.

As a silly example, if I wanted everything with Fred in it I tried something like

```
(program.title LIKE '%Fred%' OR
   program.subtitle LIKE '%Fred%' OR
      program.description LIKE '%Fred%')
```

What do I need to add so that it searches the names of the cast members (as I see when viewing the program details in mythweb).

---

### Post by ubnewbie2 on 2012-11-25
From what I have been able to fathom from the wiki, there is a 'credits' table that relates to the 'program' table via the unique ID of the channel ID and starttime, and that the 'person' field in the credits table can be used to look up the name via the 'people' table.  

I am not sure how to formulate the query for the power search though.

---

