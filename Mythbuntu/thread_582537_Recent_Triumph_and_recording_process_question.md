---
title: "Recent Triumph and recording process question"
date: 2007-10-19
forum: Mythbuntu
---

### Post by govee on 2007-10-19
Firstly I was having  problem with my Program Guide. I use Direct Tv as my source. I went through the steps of seting up and i was making the mistake of using "scan for channels" I would get 80 channels added with no names. Then later for some reason I got channels added from around 
80 on up through the XM channels but they were correctly listed by name and channel numbers. I could not get the lower channels listed.Ii found a thread that indicated I should "Fetch the Listing' vice "scan for channels" [http://g-ding.tv/?q=node/2422](http://g-ding.tv/?q=node/2422) . I went through the process of resetting up my source and the bogus lower channels were removed but not readded correctly. I went to the Schedules direct site and logged in and checked if there was something wrong there. What I found was there were 2 Direct TV listings for my area and I had used the one that Did not include the local channels on the lower end. I selected the new listing source and  now all channels  are available and correct!:guitar:

Now my question. I noticed that live tv segments are recorded and then stored. It would seem to me that would begin to eat a lot of space. Is there some setting that will erase those recordings shortly after the channel is changed or the show is over? 

I use Mythweb and set the password in Mythconfig Gui. Does that protect me from internet intrusions or is there another password that needs set?

Sorry so long winded, but I hope to help someone else struggling with the guide setup.

Thanks

---

### Post by rusty0101 on 2007-10-20
Thanks for the tip regarding the channels. I'm pretty sure that it will come in handy.

Live TV viewing is recorded because that is the way that Mythtv went for caching. By default Live TV capture files are deleted after 1 day. You can adjust this up to 365 if you would like, But, as you might expect, that's not particularly useful.

Also Live TV recordings are the first thing that will be deleted if the system needs more space. It is Auto-Expired at the highest priority. The only thing that would prevent it from being deleted is if the system thinks the show is still being watched as Live TV.

Considering that it is using php and mysql, it is possible that the system is vulnerable to a cross site scripting flaw, I would recommend regularly going into the system and doing a 'sudo apt-get upgrade' to keep the tools current. (The oft recommended 'apt-get update' is done automatically for you by the update manager.)

Whether anything else is vulnerable or not depends upon your specific configuration. As an example the default setup is for the mysql server not to be available to the network. If you are behind a firewall that is not port forwarding anything to your mythbuntu system, people pretty much can't get to it from the Internet. Yes there are a few ways around this, including poorly configured setups for other systems, but for most people the cost of doing so is not worth the effort for a linux box.

---

### Post by govee on 2007-10-20
Wow, 
I will have to reread that a few more times before it makes sense.

Thanks

---

### Post by greener on 2008-01-21
Hey govee, read your post and I am having the exact same problem, am using directtv.pl script and my myth box couldn't see some of the local stations. I went to schedule direct and found that I had selected the wrong lineup and needed to select the local one. Now my program guide can see all the stations, but when I try to record someting on a local station (any channel under 10) the direct tv box says channel not found. I ssh'd into my mythbox and tested the directv.pl script with local channel commands: i.e.

/usr/bin/directv.pl 8

/usr/bin/directv.pl 8

these commands worked fine manually, but if I schedule a recording the program guide can not change the channel to anything under ten . Any advice you have is muchly appreciated. Thanks

-Rich

---

