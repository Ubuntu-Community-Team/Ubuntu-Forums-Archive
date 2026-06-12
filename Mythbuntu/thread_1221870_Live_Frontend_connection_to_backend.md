---
title: "Live Frontend connection to backend"
date: 2009-07-24
forum: Mythbuntu
---

### Post by turtle02 on 2009-07-24
I have a 9.04 combo machine that runs great and i would like to connect a 9.04 live cd frontend machine from my laptop to watch videos and such. When i put in all of the info into the cd my test connection is succesfull but when i go to what tv or recordings it says no backend found. I also set the security thing to 0000 like it says to allow any frontend to connect. Not sure what the problem is and what all info you need to help. just let me know.

---

### Post by klc5555 on 2009-07-24
> **turtle02 said:**
> I have a 9.04 combo machine that runs great and i would like to connect a 9.04 live cd frontend machine from my laptop to watch videos and such. When i put in all of the info into the cd my test connection is succesfull but when i go to what tv or recordings it says no backend found. I also set the security thing to 0000 like it says to allow any frontend to connect. Not sure what the problem is and what all info you need to help. just let me know.

You'll need to enable the Mysql service on your backend's ethernet interface from MCC > System Services.

Also, for remote access, in Backend setup > General, the two instances of 127.0.0.1 (localhost) has to be changed to the actual ip address on the network. And this actual ip address will also be used for the location of the master backend when you fill in the frontend configuration data on the laptop.

---

### Post by turtle02 on 2009-07-27
Thanks that fixed my connections to the backend problem it works great. 
Now I do have another question when i had the live cd frontend connected to my server i could watch tv on the live cd end but i could not use the watch tv option on the local server monitor. Is this possible?

---

### Post by klc5555 on 2009-07-28
> **turtle02 said:**
> Thanks that fixed my connections to the backend problem it works great. 
Now I do have another question when i had the live cd frontend connected to my server i could watch tv on the live cd end but i could not use the watch tv option on the local server monitor. Is this possible?

Since the backend has been network enabled, the frontend setup on the server also has to be changed to reference the real ip address and not 127.0.0.1

---

### Post by turtle02 on 2009-07-28
Thats is the way i have it setup it has its real ip and not 127.0.0.1 or local host and that fixed my live cd frontend connection problem my new question on the same lines is.

When i have my live cd connected i can view everything just fine on it but while my live cd is connected to my backend. on my combo backend/frontend server i can no longer use the watch tv option but as soon as my live cd disconnects i can use the watch tv option again on my server? makes sense. Its a differnt issue do i need to start a new thread?

---

### Post by tgm4883 on 2009-07-28
> **turtle02 said:**
> Thats is the way i have it setup it has its real ip and not 127.0.0.1 or local host and that fixed my live cd frontend connection problem my new question on the same lines is.

When i have my live cd connected i can view everything just fine on it but while my live cd is connected to my backend. on my combo backend/frontend server i can no longer use the watch tv option but as soon as my live cd disconnects i can use the watch tv option again on my server? makes sense. Its a differnt issue do i need to start a new thread?

How many tuners do you have in your backend?

---

### Post by turtle02 on 2009-07-28
I just have one hauppauge 150 tuner

---

### Post by turtle02 on 2009-07-29
So i guess i have to have 1 tuner card per frontend connection?

---

### Post by klc5555 on 2009-07-29
> **turtle02 said:**
> So i guess i have to have 1 tuner card per frontend connection?

You need one tuner per different channel watched/recorded simultaneously on a backend. With some exceptions limited to digital signal multiplexing, which doesn't apply to a pvr 150.

But Myth records livetv the same as a scheduled recording. If you have your frontend(s) set up to list livetv in the "view recordings" menu, then other frontends may view (as a recording) the same program that one frontend is currently watching as livetv. There is no particular limit (other than network bandwidth and disk speed) on how many frontends may simultaneously watch prerecorded material from a single backend.

---

### Post by tgm4883 on 2009-07-29
You have to have 1 tuner per recording you are doing (live tv counts as a recording)

---

