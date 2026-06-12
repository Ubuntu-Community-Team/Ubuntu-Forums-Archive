---
title: "How to? Change MythBuntu default storage directory"
date: 2013-06-28
forum: Mythbuntu
---

### Post by Mark_in_Hollywood on 2013-06-28
I installed MythBuntu and got it up and running today. I see by the backend infos that the storage directories are all in my / (root) partition. 

Please direct me to a URL or webpage that shows how to change the default directory schema. By the bye: I have 2 partitions on this drive one is /dev/sda3 and is the root partition. The other is /dev/sda6 and is my /home partition. I want to put recorded shows into the /sda6 or /home partition.

---

### Post by williammanda on 2013-06-29
Please refer to these urls:

[http://www.mythtv.org/wiki/Storage_Groups](http://www.mythtv.org/wiki/Storage_Groups)

[http://www.mythtv.org/wiki/MythTV-HOWTO_-_0.26#Storage_Groups](http://www.mythtv.org/wiki/MythTV-HOWTO_-_0.26#Storage_Groups)

---

### Post by Mark_in_Hollywood on 2013-06-29
williammanda

Thank you for those links. 

To Every One Else:

I have read these two links worth of info. As a non computer savvy user, I have utterly no idea of what to do. I know the theory of these storage groups, but no idea whatsoever as to How-To. 

It seems to me that these pages are written by someone who expects his reader to have roughly the same expertise as himself. And just so you don't think I'm wusssing out, I've been netsearching for MythTV and/or MythBuntu and/or Storage and/or Partitions and half a dozen other keywords and after 4 to 6 hours, I'm nowhere.

---

### Post by tgm4883 on 2013-06-29
> **Mark_in_Hollywood said:**
> williammanda

Thank you for those links. 

To Every One Else:

I have read these two links worth of info. As a non computer savvy user, I have utterly no idea of what to do. I know the theory of these storage groups, but no idea whatsoever as to How-To. 

It seems to me that these pages are written by someone who expects his reader to have roughly the same expertise as himself. And just so you don't think I'm wusssing out, I've been netsearching for MythTV and/or MythBuntu and/or Storage and/or Partitions and half a dozen other keywords and after 4 to 6 hours, I'm nowhere.

I don't have time to write a full how to for you right now, but basically you need to do 2-3 things.

1) Mount the new drive in some location. I mount all mine at /srv/mythtv (you'll need to make a /srv/mythtv directory). Do not mount it inside your /home partition.

2) Tell one of the MythTV storage groups where the mounted storage is. This is done in mythtv-setup. I've been making an installation guide, which might help you. I'd appreciate comments on any parts of it (you can make comments directly in the document without logging in).

[https://docs.google.com/document/d/19knOlqz8cV5_8VQ1tCvEd8tjEk6U50KsSOJCROR60o4/edit?usp=sharing](https://docs.google.com/document/d/19knOlqz8cV5_8VQ1tCvEd8tjEk6U50KsSOJCROR60o4/edit?usp=sharing)

3) OPTIONAL: If you don't need the old storage location anymore and you don't have any recordings on it, remove it from the mythtv storage groups (in mythtv-setup)


There is some basic computer knowledge required to use a computer. You mentioned you have a second partition for your recordings, but it's not mounted anywhere. This is assumed knowledge when reading most guides (and isn't exclusive to Linux guides).

---

### Post by Mark_in_Hollywood on 2013-06-29
> **tgm4883 said:**
> I don't have time to write a full how to for you right now, but basically you need to do 2-3 things.

1) Mount the new drive in some location. I mount all mine at /srv/mythtv (you'll need to make a /srv/mythtv directory). Do not mount it inside your /home partition.

[COLOR="#FF0000"]Sorry for the confusion. I have 1 hard drive. It is formatted: dev/sda1 and /dev/sda6. That is / and /home respectively. Both are mounted at power up or boot time.[/COLOR]

2) Tell one of the MythTV storage groups where the mounted storage is. This is done in mythtv-setup. I've been making an installation guide, which might help you. I'd appreciate comments on any parts of it (you can make comments directly in the document without logging in).

[COLOR="#FF0000"]I have done this: deleted the /var/lib/mythtv/-whatever-file-name and in their places, I have: /home/mark/myth-recordings. My username:usergroup is: mark:mark

Of small note: in order to remove the /var/lib/mythtv/-folders- I had to use the d key. (d for delete). Then use the add new directory and type in or paste the name of the new path/to/directory.[/COLOR] 

[https://docs.google.com/document/d/19knOlqz8cV5_8VQ1tCvEd8tjEk6U50KsSOJCROR60o4/edit?usp=sharing](https://docs.google.com/document/d/19knOlqz8cV5_8VQ1tCvEd8tjEk6U50KsSOJCROR60o4/edit?usp=sharing)

[COLOR="#FF0000"]I will read and respond - thank you for this unique opportunity.[/COLOR]

3) OPTIONAL: If you don't need the old storage location anymore and you don't have any recordings on it, remove it from the mythtv storage groups (in mythtv-setup)

[COLOR="#FF0000"]None and done.[/COLOR]

[COLOR="#FF0000"]Again, I apologize for the confusion. The nomenclature isn't all that simple.[/COLOR]
There is some basic computer knowledge required to use a computer. You mentioned you have a second partition for your recordings, but it's not mounted anywhere. This is assumed knowledge when reading most guides (and isn't exclusive to Linux guides).

Thank you for such a swift response.

---

