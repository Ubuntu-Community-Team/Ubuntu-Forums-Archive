---
title: "MythTV Frontend Not Starting (No Visible Screen)"
date: 2016-11-09
forum: Mythbuntu
---

### Post by mapota on 2016-11-09
OK I had Mythbuntu 14.04 and wanted to upgrade to Mythbuntu 16.04 LTS.

I downloaded the 16.04.1 ISO and installed on a fresh SSD drive. Keeping the old disk as this is a production system.

After the installation I restored the old Database (14.04 database) tot he new system. I can see in the logs that the database was upgraded and the settings all look to be correct via myth-setup.

But the local frontend does not get to the display screens. I have to hot alt-f4 and I get the this window is busy dialog do you wan t to stop it.

I have looked at the front end logs but cannot see anything 

The last log I see is about successfully reading the airplay rsa key.

The logs are available here [http://pastebin.com/KvnVSX4w](http://pastebin.com/KvnVSX4w)

I am thinking it is possibly a QT issue, ie not rendering a display correctly, but I do not know enough to diagnose. Of course I could also be well off the mark.

Any help is greatly appreciated.

---

### Post by mapota on 2016-11-09
Checking the web frontend I can see the front end status shows the backen status as online if that helps

Andrew

---

### Post by Lester_Burnham on 2016-11-10
Hi,
Looks like you've got a nVidia video card. There is/was an issue with the nVidia driver very recently, so I'm taking a stab in the dark, that it may be your issue.

[http://www.gossamer-threads.com/lists/mythtv/users/604163](http://www.gossamer-threads.com/lists/mythtv/users/604163)

Checking web frontend? I'm guessing you mean mythweb? Is that from another machine?

Lester

---

### Post by mapota on 2016-11-11
Had a look at the nvidia drivers.

The setup that works has driver 340.96. (14.04.5 with myth 0.27...)
The setup where only the frontend does not start is 367.57  (16.04.1 with myth 0.28...)


I am not convinced it is the problem. Mythtv-setup works fine, draws all the setup screens with no issues. But the frontend does not.



Andrew

---

### Post by Lester_Burnham on 2016-11-11
Hi Andrew,
I see you're posting on the mythtv mailing list also. Good chance they'll help you sort it out.

To eliminate myth music, I wonder if removing the plugin with MCC (mythbuntu control centre) and then try starting frontend again. Do you not use OpenGL or auto as the theme painter, seeing you have a nVidia card?

Lester

---

### Post by mapota on 2016-11-11
Good call Lester.

The frontend is starting now with MythMusic disabled.

Andrew

---

### Post by Lester_Burnham on 2016-11-12
Hi,
Excellent. Hope you don't use mythmusic :)

I think I came across a similar thing going from 0.25 to 0.27
Now I tend to disable any plugins I don't use at the beginning.
Lester

---

