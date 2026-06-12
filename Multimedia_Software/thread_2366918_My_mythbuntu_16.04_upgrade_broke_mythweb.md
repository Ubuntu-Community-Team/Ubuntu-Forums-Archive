---
title: "My mythbuntu 16.04 upgrade broke mythweb"
date: 2017-07-23
forum: Multimedia Software
---

### Post by rramesh2 on 2017-07-23
Hi,

  I upgraded my 14.04 to 16.04 today. Most of the things work. However, mythweb stopped working. I tried to disable and then enable mythweb from mythbuntu control center and that made it worse. When I connect from a browser, it comes up witth the initial screen. Selecting any of the menu entires ends up with the error message that indicates that the browser is unable to connect to the backend. It gives the IP number of port number. The IP matches backend and port number matches what is configured in to as status and control ports. So, I am not sure if the upgrade was successful or some subtle thing wend wrong. 

The upgrade did have some hickups along the way. Here are somethings that I needed to do
[LIST=1]
[*]First mythtv-backend was not installed. Mythbuntu control center did not have any reporsitory enabled. I fixed the repository and manually installed myth-tv backend
[*]Mythweb was completely broken. Browser would not connect at all. I found mythweb was not installed and manually installed that one
[*]Now the browser comes up with initial screen, but cannot proceed futher. I went through backend setup to make sure all ports and other names are correct.
[/LIST]

Now I am out of ideas and need help. I still have my 14.04 (I always make one-to-one copy before upgrade and I still have the old install disk) and can install fresh 16.04 and attemtpt to port the database alone, instead of the wholesale in place upgrade like what I did. Let me know if this is a better approach rather than fix the broken 16.04.

Ramesh

---

### Post by wildmanne39 on 2017-07-23
*Thread moved to **Multimedia Software**.*

---

### Post by Autodave on 2017-07-27
I have never had any lick upgrading from one release to the next. My advice is to save what you can to an external drive and reinstall.  Sorry.

You will get people here that disagree with my findings, but 13 machines and only one worked the last time. I don't like those3 odds and it takes less time (usually) to do a fresh install and save the headache.

---

### Post by rramesh2 on 2017-07-27
> **Autodave said:**
> I have never had any lick upgrading from one release to the next. My advice is to save what you can to an external drive and reinstall.  Sorry.

You will get people here that disagree with my findings, but 13 machines and only one worked the last time. I don't like those3 odds and it takes less time (usually) to do a fresh install and save the headache.

Thanks. I did that in my 12.04 to 14.04 upgrade. Typical problem with this approach is that you get vanilla install as opposed to tuned one I have. In the end, it may be easy to do get-selection and install the same packages on the new install. BTW, I am told mythbuntu is not supported in the future. So, we may have to install another flavor next time and it would be impossible to do upgrade in place the next time. 

Saving current install is not a problem because I always buy a new ssd each time LTS updates. So, old one is undisturbed and attached just in case I want to boot to the old system.

Ramesh

---

### Post by bilkay on 2018-03-24
I installed mythweb on a fresh install of 16.04 and it doesn't work. The only thing I could find on why it doesn't work is a post saying mythweb requires php5 and 16.04 has php7. I have been unable to find how to fix this.

[https://readlist.com/lists/mythtv.org/mythtv-users/51/259901.html](https://readlist.com/lists/mythtv.org/mythtv-users/51/259901.html)

---

### Post by mark215 on 2018-04-01
The log file for the backend will show the error and a solution which is to install some extensions. This fixed it:
sudo apt-get install php-mysql

---

