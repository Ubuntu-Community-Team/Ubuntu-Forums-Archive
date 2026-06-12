---
title: "unstable internet connection"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by mastablasta on 2010-08-11
Hello i have probably a bit different question.
 
My internet connection is acting strange. unstable. sometimes pages would load only basic HTML other times connection to server is not there...
 
According to ISP the problem is somewhere in my network (so on my side). i have dynamic IP on a broadband connection. i think static IP handles this better but they say it makes no difference.
 
Anyway i am experiencing this on XP and well as Ubuntu. so i want to check this claim. what programmes do you suggest? also if you have any suggestion for XP i would appreciate.
 
I used to have a program in Win98 that was tracking conneciton and time and wrote down all servers i connect to enroute. can't remember the name though. thought about a malware on XP but antivirus as well as firewall don't show any unusual activity.

---

### Post by mprokolo on 2010-08-11
1st static ip will make no difference at all 

2nd it doesnt seem that you have a virus or malware

this "usually" happends if you max out your connection with downloading and/or uploading for example torrents or large files if you are sure that this is not the case check your router logs to see is there is somebody else connected to your network

---

### Post by mastablasta on 2010-08-11
bingo. i've seen this before... however i haven't used torrent and also i have them limited on my connection.
 
i have a wireless dongle on the modem, but the light is not on (as i am not using it). Also it is secured & encrypted under password. my modem is configured as router. It also provides signal for phone and video/TV (FTTH connection) 
 
do you think someone can still be accessing my modem? any diagnostic tool (linux or win)?
 
hmm large files... so if i directly downloaded large files i could max out connections as well? even so i didn't do any big download now that i think of it. and also the download i did do (filezilla for win) wasn't really so fast. then again i might have still maxed out the connections, huh?

---

### Post by varunendra on 2010-08-11
As for a monitoring tool, you may try [PRTG network monitor]("http://www.paessler.com/prtg/"). It is free for upto 10 sensors and looks promising.

I installed it once but couldn't get time to thoroughly test it. (I got sonicwall right then :))

---

### Post by mprokolo on 2010-08-11
I doubt that another person is using your internet 
large files tend to max out the bandwith 
torrents tend to make too many connections 
if you have adsl torrents can easily max out the upload bandwith and that causes general "slowness"
if these are not the case it could be that the site was "down" or had too many connections so this is not your problem

finally,when you are experiencing unstable internet connection stop all programms that are down/uploading and do a speed test (speedtest.net if i remember correctly) if it gives you the speed that you are paying for then the problem is not you nor your isp but the site's server

---

### Post by varunendra on 2010-08-11
> **mprokolo said:**
> if these are not the case it could be that the site was "down" or had too many connections so this is not your problem

finally,when you are experiencing unstable internet connection stop all programms that are down/uploading and do a speed test (speedtest.net if i remember correctly) if it gives you the speed that you are paying for then the problem is not you nor your isp but the site's server
Can it be possible due to slower response time of DNS servers?

How about trying open DNS servers that have a quicker response time?

---

### Post by mastablasta on 2010-08-12
I don't know... i am thinking maybe it was windows updates that were loading suspiciously long in background.
 
torrents connection are quite limited. you see before i had 256kB D/56kB U, so i limited it all in torrents to fit that connection. 
 
now i moved and got FTTH (optic fiber), so now i have 20Mbit/20Mbit. speed test was the first thing i did. strangely again i could not connect at certain times or connecion was showed to be 13 Mbit. then i tried some different servers and connection went up to 20 again.
 
its just very annoying getting that message and can mess it all up if you are filling out some forms. i mean as soon as i click reload (or "try again") page pops up. or sometimes it would just not load the whole website... strange. like only basic HTML is loaded. no pictures, no menues (just links).
 
TV (and phone) is also via modem and is using separate conneciton. it is not using any of that 20Mbit. and yet it also suffers stutters every now and then. yesterday it was once in 3 hours that i watched it... that is why i was suspecting that conneciton from server to me is not ok. but hard to tell...
 
So i was thinking torrent, but i wasn't running it (before).
 
Since i have dynamic IP i was thinking that maybe someone else with that IP was running it and then i got his IP. is it possible i would still get the connections?
 
i think once before when i was on ADSL with dynamic IP i had this similar problem.
 
Oh and the modem doesn't seem to be logging anything. and yes you are correct - no one else seems to be on my network.

---

### Post by raven2099 on 2012-12-01
i get this too. i'll visit say youtube or crackle go to watch something and the page will time out and i'll have to reload it 5 to 6 times

even my blog wit be unreachable and i'll have to reload several times to bring it up
 wifi or wired makes no difference

---

### Post by varunendra on 2012-12-01
> **raven2099 said:**
> i get this too. i'll visit say youtube or crackle go to watch something and the page will time out and i'll have to reload it 5 to 6 times

even my blog wit be unreachable and i'll have to reload several times to bring it up
 wifi or wired makes no difference
raven2099,
Network problems are very versatile and their cause as well as solutions can be much different for different people, even though the symptoms and effects may look same. Besides, the last post above yours is more than two year old.

As such, I'd recommend to start a new thread of your own, and if you are using wireless, post the result of wireless_script in it as suggested in this post : [http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)

---

### Post by howefield on 2012-12-01
Old thread back to sleep.

---

