---
title: "I want to configure dual network cards: eth0 and wlan0"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by dave247 on 2010-11-14
ok I have set up Snort on my laptop. I have my wired connection eth0 hooked up to a hub which is basically just listening to the raw data coming in from my internet line. I now want to set up my wireless to use on my network to connect to my router so I can have internet like usual. 

I am wondering how I should set up my interfaces file... usually when I make changes to it nothing happens. Not sure what I should do.

any input is appreciated!

thanks

---

### Post by uncaspi on 2010-11-14
If more cards are added in interfaces than the lo device, they are not handled by the network-manager

---

### Post by dave247 on 2010-11-14
never mind. i got it working. I changed the ip of my eth0 to a static address, then told snort to listen on that. I used the gui to connect to the network with my wireless.

easy

---

### Post by Iowan on 2010-11-14
Would you consider the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

