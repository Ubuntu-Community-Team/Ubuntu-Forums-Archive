---
title: "No UPnP Backend found"
date: 2008-08-08
forum: Mythbuntu
---

### Post by legswilly on 2008-08-08
Hi I tried to install three times and cant configure the front or backend. It tells me that it cant find the backend. It looks like as if the database is being installed. It asked me to configure the backend? in a command line interface . One of the outputs says "No error type from QSqlError? Strange ...". I was installing this from Add/Remove under Applications in 8.04 twice and from a download from Mythtv once. Neither was successful. 
I wanted to stick we my current Ubuntu install. Would it be better to install from scratch with Mythbuntu and can I add the same applications as with 8.04?
Any help is appreciated.
Werner

---

### Post by SniperKIng on 2008-08-08
Hey 

With mythbuntu only taking like 10 minutes to install for me anyway, i would say its your best option unless someone else here can help. As mythbuntu is just ubuntu with mythtv installed i see no reason why you cant use the same programs, i have never had a problem with them. You may want to change the desktop environmet if the default doesnt suit you,this can be done from within System>Mythtv control centre and then click the top tab.

Hope this helps

SniperKIng

---

### Post by dannyboy79 on 2008-08-08
> **legswilly said:**
> Hi I tried to install three times and cant configure the front or backend. It tells me that it cant find the backend. It looks like as if the database is being installed. It asked me to configure the backend? in a command line interface . One of the outputs says "No error type from QSqlError? Strange ...". I was installing this from Add/Remove under Applications in 8.04 twice and from a download from Mythtv once. Neither was successful. 
I wanted to stick we my current Ubuntu install. Would it be better to install from scratch with Mythbuntu and can I add the same applications as with 8.04?
Any help is appreciated.
Werner
this thread resolved the same issue possibly. 
[http://ubuntuforums.org/showthread.php?t=881876](http://ubuntuforums.org/showthread.php?t=881876)
It has to do with the mythconverg database not being created etc etc. good luck.

+1 for mythbuntu also.

---

### Post by Thacker on 2008-09-02
Tried Mythbuntu same result if anything even more confusing

---

### Post by davidryder on 2008-09-25
I just uninstalled it. This should not be in the default repositories at all. I don't know anything about mysql nor should I have to. 

I was able to connect as root, but not mythtv and I couldn't figure the problem out. Oh well - that's what Vista is for.

---

### Post by SoFingFrustrated on 2008-09-30
> **davidryder said:**
> I just uninstalled it. This should not be in the default repositories at all. I don't know anything about mysql nor should I have to. 

I was able to connect as root, but not mythtv and I couldn't figure the problem out. Oh well - that's what Vista is for.


Agreed...I'm giving up as well...I feel like Im bothering too many people and talked down to as I've been a windows user for all my life.  I think Myth Tv IS a Myth....wasted sooo much time reading forums sudo this sudo that...i copied a guys machine exactly  ubuntu is fine on it, Myth tv...i go to 'watch tv' i get a black screen for 1 second and thats it.....nothing happends

---

### Post by DemonBob on 2008-09-30
> **SoFingFrustrated said:**
> Agreed...I'm giving up as well...I feel like Im bothering too many people and talked down to as I've been a windows user for all my life.  I think Myth Tv IS a Myth....wasted sooo much time reading forums sudo this sudo that...i copied a guys machine exactly  ubuntu is fine on it, Myth tv...i go to 'watch tv' i get a black screen for 1 second and thats it.....nothing happends

What video card? What tv tuner? What CPU? What play back profile selected? Start your own post listing the issues you are having, and i'll try to help.

---

### Post by Eric Boring on 2008-09-30
> **davidryder said:**
> I just uninstalled it. This should not be in the default repositories at all. I don't know anything about mysql nor should I have to. 

I was able to connect as root, but not mythtv and I couldn't figure the problem out. Oh well - that's what Vista is for.

I had this problem with mythbuntu 8.04 on one install. Try removing the backend and reinstalling it. The easiest way is to go open the synaptic package manager (I can't remember where it is in Mythbuntu, should be something with system tools). When you have synaptic opened, search for mythbuntu, right click on the backend package name, mark for removal. THen click apply. Then right click it again and mark for installation. Click Apply again. See if that helps.

Don't give up the dream! If I can get this thing working, I _guarantee_ you that you can. ;)

-josh

---

### Post by davidryder on 2008-09-30
Thanks Eric. I would have an easier time if I knew more about MySQL. It's not really a big deal it was just something I was tinkering with on my office PC. I have an HTPC in my living room with Vista dedicated to media.

---

### Post by ReddogOne on 2008-10-02
"No UPnP Backend found" as far as I can remember... ignore this. Don't think the MythTV Backend is actually UPnP. Wikipedia has plenty of what UPnP is so I won't repeat.

Try going to [http://parker1.co.uk/mythtv_ubuntu.php]("http://parker1.co.uk/mythtv_ubuntu.php") as the MythTV help is just wwwwwwwaaaaaaaaaaaaaaayyyyyyyyyyyyy to complicated (as most Linux instructions seem to be for the average user)!

If your front end is on a different machine. You need to fill in the computer name, database and password on the frontend.

---

### Post by SiHa on 2008-10-02
> No UPnP Backend found" as far as I can remember... ignore this.

You can ignore it if you like, but it's telling you something quite important - the frontend can't see the backend. Have you configured your IP addresses properly?

In the backend setup, the IP address for the master backend server defaults to 127.0.0.0. This is fine if the frontend is on the same machine, but if it's on a different machine you'll need to set it to that machine's IP address.

Also, if the frontend is on a different machine, you have to do an 'Advanced Install'

IMHO, the easiest route by far is a fresh install of Mythbuntu, all the extra bits are pre-installed,and you can always add the 'Ubuntu' bits later.

---

