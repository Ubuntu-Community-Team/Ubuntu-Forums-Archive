---
title: "Frontend can't connect to Backend"
date: 2008-05-22
forum: Mythbuntu
---

### Post by BillTurnbull on 2008-05-22
I imagine this is a common question, however the volume of info is a bit big to wade through...

ver 8.04

I have a Master Backend & Fronted running nicely on one machine, can see captured tv and play my vids etc.

I used advanced install, added nfs and mysql services. Made the local backend 192.168.1.13, left the Master backend as 127.0.0.1 (and tried local backend as 127.0.0.1)


I have now installed a frontend (only) on another machine pointed its mysql server info to 192.168.1.13 checked the password etc... 

It starts up ok, but I cant watch captured tv, I get the "Could not connect to mast backend server....." error message.

The interesting part is that when I look in the video library, they are all listed, but no thumbnails and I cant play them...

Am I missing a simple step?

Thanks,

Bill

---

### Post by Unibrav on 2008-05-23
> **BillTurnbull said:**
> I imagine this is a common question, however the volume of info is a bit big to wade through...

ver 8.04

I have a Master Backend & Fronted running nicely on one machine, can see captured tv and play my vids etc.

I used advanced install, added nfs and mysql services. Made the local backend 192.168.1.13, left the Master backend as 127.0.0.1 (and tried local backend as 127.0.0.1)


I have now installed a frontend (only) on another machine pointed its mysql server info to 192.168.1.13 checked the password etc... 

It starts up ok, but I cant watch captured tv, I get the "Could not connect to mast backend server....." error message.

The interesting part is that when I look in the video library, they are all listed, but no thumbnails and I cant play them...

Am I missing a simple step?

Thanks,

Bill

Two things.

First, you need to make sure that you've NFS mounted the directory containing the recordings. It should be mounted in the same spot on the slave as it is the master. (This step is not necessary in order to watch the recordings but it is necessary to get the preview images and it will help everything to behave as you expect. If you're not sure how to do this step move on to the next one for now.)

Next, you should just need to go through 'mythtv-setup' to set the master server.

Exit the frontend. Open a terminal and type 'mythtv-setup'. On the first page of that screen leave 127.0.0.1 as the IP for the local backend and enter the IP of your master backend. Hit next > next > finish. Start the frontend again and it should be good to go.

---

