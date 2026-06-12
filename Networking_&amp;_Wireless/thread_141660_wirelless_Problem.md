---
title: "wirelless Problem"
date: 2006-03-08
forum: Networking &amp; Wireless
---

### Post by lfvo on 2006-03-08
hi
i have  a problem in my wireless network. my laptop detect the ssid, but i can connect:cry: . i am try connect wireless through WPA. i have done what is saying in this post [http://www.ubuntuforums.org/showthread.php?t=90450]("http://www.ubuntuforums.org/showthread.php?t=90450"), but still no connect and have internet on my laptop. my wireless device is a intel pro 2200bg.

sorry for my bad english and i hope anyone can help me.

---

### Post by randomnote1 on 2006-03-08
whoa...never seen that solution before.  I used ndiswrapper on my girlfriend's laptop and she's never had a problem connecting to any network.

---

### Post by sdb2028 on 2006-03-09
I fought that problem for a couple of weeks, jumped through all the hoops from these threads and did major searches for help to fix it. Finally ran across a thread which explained what happens with the sysv-rc-config file and what the defaults should be. > [http://ubuntuforums.org/showthread.php?t=138760](http://ubuntuforums.org/showthread.php?t=138760)
I did a fresh install of ubuntu, so that everything would be as it was (before I made those massive changes to drivers and firmware). I then went through the sysv-rc-conf file (type "sudo sysv-rc-conf" in teminal) and set all the checks to the default as listed in the how-to thread I mentioned. I have been up and running with absolutely NO problems for over a week now. I have ipv6 ON, using the drivers and original configuration that came with ubuntu.

I found no need to make all those other changes.

---

