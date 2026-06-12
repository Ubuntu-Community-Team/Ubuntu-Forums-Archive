---
title: "Stuck configuring backend with DVB-S (TBS 6984)"
date: 2012-09-18
forum: Mythbuntu
---

### Post by Erik-NA on 2012-09-18
I have configured my sat card, TBS 6984. 

I can watch TV by using szap and mplayer.

Now I am stuck when configuring MythTV-backend.

[LIST]
[*]I have configured the capture devices, I have four of them
[*]I have created a Video source, using tv.swedb.se
[*]I have setup input connections for all my capture devices. I have used "scan for channels" to import my channels.conf file created with the scan-command
[*]I cannot see any channels in the channel editor. However, using phpmyadmin, there are imported channels in the database
[/LIST]

When I am exiting MythTV-backend I am getting the message: "Card 1 (Type DVBInput) is set to start on Channel. Please add, which does not exist."

What am I doing wrong?

---

### Post by nickrout on 2012-09-18
> **Erik-NA said:**
> I have configured my sat card, TBS 6984. 

I can watch TV by using szap and mplayer.

Now I am stuck when configuring MythTV-backend.

[LIST]
[*]I have configured the capture devices, I have four of them
[*]I have created a Video source, using tv.swedb.se
[*]I have setup input connections for all my capture devices. I have used "scan for channels" to import my channels.conf file created with the scan-command
[*]I cannot see any channels in the channel editor. However, using phpmyadmin, there are imported channels in the database
[/LIST]

When I am exiting MythTV-backend I am getting the message: "Card 1 (Type DVBInput) is set to start on Channel. Please add, which does not exist."

What am I doing wrong?Have you set up your LNB?

---

