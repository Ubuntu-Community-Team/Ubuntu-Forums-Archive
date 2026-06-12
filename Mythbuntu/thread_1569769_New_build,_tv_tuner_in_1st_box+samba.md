---
title: "New build, tv tuner in 1st box+samba"
date: 2010-09-07
forum: Mythbuntu
---

### Post by blkbx on 2010-09-07
I have a couple of questions. First, I'm building a new backend front end system and I had thought that I guess just because
the tuner card was in the front end box and also that it was at the end tv cable.
So I was wondering if I can leave the tuners in the front box and configure them from there
Secound, I want to plug the front end box into my home lan so that I can allow others mainly window users access to the media in my backend mythtv box via samba.
thanks

---

### Post by LowSky on 2010-09-07
sorry I'm donot understand what you are trying to say?

Do you want to have a seperate frontend fomr the main backend where the frontend does the recording? That isn't really possible. What you can do is have frontend/backend and then a main backend.

Smamba can only share files to what it has access to, so if you only share the frontend, whatever is on the main backend will not be accessible if it isn't on the smaba network. 

Mythtv has UPnP server capabilities  built in and im pretty sure Windows Media Player can access those easily. which would be easier than setting up SMABA permissions.

---

### Post by blkbx on 2010-09-07
sorry for the confusion. I had trouble keeping my eyes open when I posted.
Ok so I have the frontend with a 8gig compact flash drive to hold mythbuntu and the tuner because the aerial cable only goes that far.
The backend which is 15 meters away under the stairs holds 2x1 terabyte hdd and its from these that I want to be able to share /var/lib/mythtv
I only know how to use samba when working with windows machines which is why I mentioned it.
thanks for your post

---

