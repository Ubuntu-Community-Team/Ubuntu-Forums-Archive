---
title: "Problem with permissions of folders"
date: 2009-04-13
forum: Mythbuntu
---

### Post by amar on 2009-04-13
Hi folks,

I am having trouble that sounds like the one described [in this thread]("http://ubuntuforums.org/showthread.php?t=870700")

However as far as I can tell, I have set the permissions correctly - it is driving me crazy

Symptons are the exact same as described in the previous thread, using a Freecom DVB-T card which works great with kaffine. I can setup the backend and it finds all the channels and setup looks good.

The Storage directories menu has both the Default and LiveTV directories set to '/home/amar/Videos/TV'

The permisions of the folders are set with sudo chmod 777 Videos/TV yet when I run the frontend, I can not access the screen returns to the main menu when I select Watch TV.

Any suggestions what I am doing wrong/ any other folders I should be checking out?

Any other information needed just ask.

Thanks
Alistair

EDIT: add a pastbin of my logs
[http://mythbuntu.pastebin.com/f16cb8219](http://mythbuntu.pastebin.com/f16cb8219)

---

### Post by rhpot1991 on 2009-04-13
> **amar said:**
> Hi folks,

I am having trouble that sounds like the one described [in this thread]("http://ubuntuforums.org/showthread.php?t=870700")

However as far as I can tell, I have set the permissions correctly - it is driving me crazy

Symptons are the exact same as described in the previous thread, using a Freecom DVB-T card which works great with kaffine. I can setup the backend and it finds all the channels and setup looks good.

The Storage directories menu has both the Default and LiveTV directories set to '/home/amar/Videos/TV'

The permisions of the folders are set with sudo chmod 777 Videos/TV yet when I run the frontend, I can not access the screen returns to the main menu when I select Watch TV.

Any suggestions what I am doing wrong/ any other folders I should be checking out?

Any other information needed just ask.

Thanks
Alistair

EDIT: add a pastbin of my logs
[http://mythbuntu.pastebin.com/f16cb8219](http://mythbuntu.pastebin.com/f16cb8219)

MythTV directories should follow the following:  Be owned by mythtv:mythtv, have permissions of 775, and not be inside your home directory.

---

### Post by amar on 2009-04-13
Thanks for the response:

unfortunately it did not help

I changed the directories to /media/sda5/video/TV
and then ran:
sudo chown mythtv:mythtv /media/sda5/video/TV
sudo chmod 775 /media/sda5/video/TV

made no difference, still didn't run the tv, just returned to the menu

Alistair

---

### Post by Billsputters on 2009-04-13
What I did was the same chown stuff for the 4 directories
then 

chmod a+rwx
chmod o-w

for all 4 and then a 
chmod g+s for music and recording dirs

Try importing a few MP3's and see if they import (your permissions are correct) and where it put them. 

The 4 dirs in question are also shared as well.

---

### Post by amar on 2009-04-13
Yea, did that (again) - still no difference
I am about to test whether it can record tv.

is there anyway to reset everything back to defaults?

Thanks

---

### Post by Billsputters on 2009-04-13
Can you import MP3's?

Reset -> Reinstall

Have a look at the log files in /var/logs/mythtv/

Is there a line in there where it goes to switching to live TV, can't find the channel (with a date of 1970) and then gives up flagging an error.

---

### Post by amar on 2009-04-13
Yes I get the same error to do with not finding the correct channel.

I am able to import mp3s, and am not able to record tv.

I now believe it is not a permissions problem but instead related to the problem in another thread:
[http://ubuntuforums.org/showthread.php?t=752321](http://ubuntuforums.org/showthread.php?t=752321)
which relates to the type of card.

Unfortunately the hint about changing the frequency in the mythweb interface doesn't help (or make sense to me anyway)

---

