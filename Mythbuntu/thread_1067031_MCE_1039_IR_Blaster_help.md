---
title: "MCE 1039 IR Blaster help"
date: 2009-02-11
forum: Mythbuntu
---

### Post by Javaroaster on 2009-02-11
I'm a total newb but, I have managed to get Mythbuntu working with my MCE remote. However I cannot get the blaster to change channels on my dish 301 reciever. The PDF I downloaded from mythbuntu says that the this remote should work out of the box, but clearly there is something I'm missing. I've googled quite a bit and found out that I may need to have a channel changer script. I've attempted to follow the directions here.

[https://help.ubuntu.com/community/MythTV_External_Channel_Changer](https://help.ubuntu.com/community/MythTV_External_Channel_Changer)

but when I go into backend set up and tell it to use channel-changer-lirc.pl the frontend will not connect to the backend to view live tv.

---

### Post by Javaroaster on 2009-02-12
bump: I have followed the the directions to install change-channel-lirc.pl in /usr/local/bin. I have also edited line 5 of the script to $remote_name = "dish6"; I based this on /usr/share/lirc/transmitters/dish/general.conf and the fact that my remote has RC6 on the battery cover. I have also gone into backend setup and added change-channel-lirc.pl as an external channel change command in Input connections.

The first thing that I found was that after I added the external channel change command to the backend the frontend will not let me watch tv. I can watch recordings but not live tv. Since I cannot watch live tv I don't know if mythtv is now capable of changinging channels on my dish reciever. If I remove the external channel change command I can watch tv.

---

### Post by Javaroaster on 2009-02-13
Solved finally! When I put channel-change-lirc.pl into the backend external change command I didn't put the path /usr/local/bin/channel-change-lirc.pl. In my defense I am a linux newby, and the instructions at [https://help.ubuntu.com/community/MythTV_External_Channel_Changer](https://help.ubuntu.com/community/MythTV_External_Channel_Changer) did not say that you needed to put in the path.

---

