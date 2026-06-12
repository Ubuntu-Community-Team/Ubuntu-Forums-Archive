---
title: "Channel files"
date: 2010-02-04
forum: Mythbuntu
---

### Post by linuxhippy on 2010-02-04
It seemed that I needed Schedules Direct to fetch channels to make my card usable.  Now that my 7 day free trial is over with them and I didn't pay for a trial (I would've if I could've found any shows) I want to backup the file where the fetch data has been saved from Schedules Direct where my tuner card stores channels.

Which file is this?

---

### Post by Calmor on 2010-02-04
I don't believe there is a file per se - it does download the files when it does the channel updating, but it then imports that data into the myth database.  

I'm not sure if you need to have the service to use Myth, you just won't get any channel data and you'll have to flip through yourself.  As it's not the fastest thing in the world to change channels, it may be irritating unless you already know what you want to watch and when.

You say you didn't find any shows?

---

### Post by linuxhippy on 2010-02-04
yup-I didn't find any shows.  I need to manually be able to tell my system where TV channels are.  My TV is unique...for instance what is recognized as 6 ABC is channel 5 for me.  So, schedules direct downloaded the information it has for channel 5 in my zip.  Unfortunately channel 5 doesn't exist in my zip and so it found nothing.

I downloaded a perl script from mythtv.org that backs up everything...did it back up the myth database where my channels are stored?

Here is the backup page I followed and I backed up everything: [http://www.mythtv.org/wiki/Database_Backup_and_Restore]("http://www.mythtv.org/wiki/Database_Backup_and_Restore")

---

### Post by nickrout on 2010-02-04
> **linuxhippy said:**
> yup-I didn't find any shows.  I need to manually be able to tell my system where TV channels are.  My TV is unique...for instance what is recognized as 6 ABC is channel 5 for me.  So, schedules direct downloaded the information it has for channel 5 in my zip.  Unfortunately channel 5 doesn't exist in my zip and so it found nothing.



What's with this zip thing? You shouldn't be putting anything down your zipper man, that's the mistake....

---

### Post by linuxhippy on 2010-02-05
> **nickrout said:**
> What's with this zip thing? You shouldn't be putting anything down your zipper man, that's the mistake....

zip code.

---

### Post by Calmor on 2010-02-05
> **linuxhippy said:**
> yup-I didn't find any shows.  I need to manually be able to tell my system where TV channels are.  

The mythbackend setup channel editor should allow you to manually create channel associations as far as telling it you have a channel 6 that's called ABC, but unfortunately it won't let you forward that information to Schedules Direct. 

SD does have a "report a lineup problem" button... so maybe you could work with them to fix the issue.

> I downloaded a perl script from mythtv.org that backs up everything...did it back up the myth database where my channels are stored?

Here is the backup page I followed and I backed up everything: [http://www.mythtv.org/wiki/Database_Backup_and_Restore]("http://www.mythtv.org/wiki/Database_Backup_and_Restore")

The channels should be in the backup if you got it before the channels left.  However, I think since they were wrong anyway, it's probably not very helpful.  Try the channel editor in mythbackend setup, let me know if that works for you.  

As I said though, you still won't have guide data, so I'd contact SD or cruise their forums and see if you can work out the problem.

---

### Post by linuxhippy on 2010-02-06
Got it to work by using the XMLTVid (5 digit # that you see when you mouse over a channel at SD) and the channel editor in mythbuntu.

---

### Post by linuxhippy on 2010-02-06
found a line up that works without editing-cable ready.

---

