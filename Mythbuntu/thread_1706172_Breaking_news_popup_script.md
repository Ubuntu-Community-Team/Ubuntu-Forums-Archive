---
title: "Breaking news popup script"
date: 2011-03-13
forum: Mythbuntu
---

### Post by kja999 on 2011-03-13
Hi,

Just thought some other people may like this.
I started hunting for something to put BBC breaking news alert popups on my mythbox but couldnt find anything. Some other people have asked similar questions on this forum so thought it may be worth putting here.

Basically its a bash script which I have put into cron.
I run it every 5 mins, but putting it into /etc/cron.hourly would do.

It gets breaking news from the backstage.bbc.co.uk feeds, checks to see if it has updated and uses the standard dbus notification box to show the update.

Feel free to tweak to your hearts content.....

Cheers

---

