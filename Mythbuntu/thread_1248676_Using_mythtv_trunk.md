---
title: "Using mythtv trunk?"
date: 2009-08-24
forum: Mythbuntu
---

### Post by raptorjr on 2009-08-24
Sorry if this have been covered before, since english is not my native language i didn't really know what to search for.

I wonder if it is possible to install mythbuntu and then use mythtv trunk in a nice way? So if i do something wrong i just have to reinstall the regular mythbuntu mythtv weekly trunk package and be up and running again? I would like to be able to apply patches to mythtv trunk and test new things, but still want all the goodies that i get from mythbuntu. Making it so much easier to use mythtv. I dont want to break anything that makes mythbuntu so nice.

If i use mythbuntu weekly mythtv trunk builds i guess i cant apply mythtv trunk patches and compile? So is there some kind of script and/or howto to help me to get mythtv trunk working, compiling the source, and still have the mythbuntu as a fallback? If this is even possible.

---

### Post by xinix on 2009-08-24
[S]The .22 (trunk) version of MythTV uses a different database schema.  So, if you try going from .22 to .21 you would not be able to continue using the same database.  You would have to start with a new one.[/S]

I need to read all words in a question.

---

### Post by tgm4883 on 2009-08-24
> **xinix said:**
> The .22 (trunk) version of MythTV uses a different database schema.  So, if you try going from .22 to .21 you would not be able to continue using the same database.  You would have to start with a new one.

I don't think that is what the OP is doing. OP says they would be building Trunk or using the Mythbuntu trunk PPA. Both of those are .22

---

### Post by raptorjr on 2009-08-25
> **tgm4883 said:**
> I don't think that is what the OP is doing. OP says they would be building Trunk or using the Mythbuntu trunk PPA. Both of those are .22

Yes exactly. 

So i wonder if there are a nice way to do this that would be helpful? Like i know that in mythbuntu the mythfrontend file is called mythfrontend.real and other files like that. But when compiling my own i get mythfrontend, and i wouldnt want to overwrite the mythbuntu files.

So is there a script or something that would help me running mythtv from source and still be compatible with a mythbuntu system?

---

### Post by tgm4883 on 2009-08-25
> **raptorjr said:**
> Yes exactly. 

So i wonder if there are a nice way to do this that would be helpful? Like i know that in mythbuntu the mythfrontend file is called mythfrontend.real and other files like that. But when compiling my own i get mythfrontend, and i wouldnt want to overwrite the mythbuntu files.

So is there a script or something that would help me running mythtv from source and still be compatible with a mythbuntu system?

You might just try an 'apt-get source' and then put it on your own PPA and try sticking the patches in there and building. 

That may be the easiest way.

---

