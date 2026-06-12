---
title: "Asus RT- N56U wireless router"
date: 2011-04-21
forum: Networking &amp; Wireless
---

### Post by heathd666 on 2011-04-21
Afternoon to all you,
 
I hope I am not wasting any of your time as i tried searching through the forum and I am afraid i wasn't able to find the answer. I may have seen the answer but if I did I did not know it as I wont say that I know what I am doing with Linux. I am currently running 4 computers on a network through the router. 2 of the computers are windows XP pro with SP3 and the other 2 were Ubuntu 10.10 however after messing with stuff on them for the last couple of days I decided rather then try to undo whatever I had done I installed Ubuntu 11.04 on them both. Okay here is my problem.
 
I bought a Netgear WNDR3700v2 a couple of weeks ago installed it due to needing a wireless internet in the house for my kids. They all do their homework through the internet next year and I figured I would get a head start on it so I bought the router. It was supposed to be the best out there. It turned out to have lots of problems with every 10 or 15 minutes I would have to reset the router. I also lost communication between some of my computers on my home network. In particular the 2 Ubuntu machines could not see the windows network anymore. They would not access each other either. The windows machines would see the Linux machines but could not access them. 
 
I wound up taking the Netgear back and bought the Asus RT-N56U. Now I had fooled with the setting so much on the Ubuntu Machines and it had been probably 6 months to a year since I installed 10.10 on them so I installed a fresh 10.10 on them. I still could not see the windows machines. I decided after a couple more days of messiing with settings and stuff to redo it all. I decided to go ahead and Installe 11.04 Ubuntu on them. I am trying to get my network back up to where the 4 computers can see each other and everything. With 10.10 it was very easy. I ran windows network wizard on the windows machines and that was that for them. On Ubuntu I would run Samba and it joined the windows machines. Now they wont do that and I have no idea how to attempt to fix it. 
 
I did the fix from this website, [http://ubuntuforums.org/showpost.php?p=9467538&postcount=5](http://ubuntuforums.org/showpost.php?p=9467538&postcount=5) but to be honest im not sure how to determine what my DNS is so I just put what he had in it.
 
On the Ubuntu machine i did the fix from the above website I can now see the windows network it comes up with a windows network folder and when I hit it it comes back with a MSHOME folder and a WORKGROUP folder where the one I have not done the above fix on will not. However when i click on either one of them i get a "Unable to mount location" and "Failed to retrieve share list from server"
 
I am not asking you guys to tell me how to fix it just point me in the right direction. I guess if the directions were in redneck so that I can understand it would help also :) 
 
thanks in advance for any help thrown my way.

---

### Post by heathd666 on 2011-04-22
anyone? 
 
okay the instructions dont necessarily have to be in redneck just simple english

---

### Post by Steve R. on 2011-12-12
Have the same issue.  Installed the ASUS RT-N56U today and I am starting to look into this.  The home network is hardwired. Not yet using the wireless connection.

I have UBUNTU 10.10 Installed on one computer.  The Windows computers can "see" the UBUNTU computer and retrieve information from it.  The Windows computers show-up on the UBUNTU computer, but the UBUNTU computer cannot interact with them.  Get the error message:"Unable to mount location" and "Failed to retrieve share list from server".

RESOLVED: Please see: [How to: Fix Windows share browsing issues, Problem #3]("http://ubuntuforums.org/showthread.php?t=1169149").

---

