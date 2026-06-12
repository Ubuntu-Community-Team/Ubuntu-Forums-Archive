---
title: "Channel Present on HD HomeRun and Antenna but not in MythBuntu"
date: 2014-08-03
forum: Mythbuntu
---

### Post by johnvic on 2014-08-03
I am running a mythbuntu backend with an HD Homerun Dual for OTA TV. It is mythbuntu ver 14.04, mythtv ver. 27. The HD Homerun is on the latest firmware.

If I use the HD Homerun diagnostic program to look at the channels I see real channel 30, which is virtual channel 68. There are 3 subchannels, 68.1, 68.2 & 68.3. I am interested in 68.3 and I can watch it fine using the diagnostic program which launches VLC. I have done this from the mythtv backend PC. If I connect the antenna directly to my tv then I see channels 68.1, 68.2 & 68.3.

When I do a scan on mythtv it says that there are 3 possible channels for real channel 30. But when I look at my channel listing I only see 68.1 & 68.2. I scanned it using Schedules Direct and EIT. Any suggestions on where to look to solve this? The system is working fine other than this missing channel. I have tried several scans.

[IMG]https://forum.mythtv.org/images/flags/US.png[/IMG][johnvic]("https://forum.mythtv.org/memberlist.php?mode=viewprofile&u=498")Newcomer Posts: 2Joined: Thu Jul 31, 2014 7:41 pm
[LIST]
[*]
[/LIST]
[RIGHT][/RIGHT]

---

### Post by khPWXxF on 2014-08-05
[COLOR=#444444][FONT=Calibri]You’ve not had any replies for what is probably a popular setup in US so I’ll now chip in with a whacky theory.  I’m in UK and use DVB-T receivers so my setup is totally different, but I have observed that Mythtv does have a habit of using stale information in its database and not refreshing it on a channel rescan.  Is it possible that your symptoms have the same underlying cause?[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]I’ve documented it here:[/FONT][/COLOR]
[http://www.mythtv.org/wiki/DVB-T_Reception_Problems#Loss_of_a_whole_multiplex](http://www.mythtv.org/wiki/DVB-T_Reception_Problems#Loss_of_a_whole_multiplex)
hth
Phil

---

### Post by johnvic on 2014-08-05
Thanks for the answer. I have deleted and rescanned before but I decided to do it one more time and I did something different this time. As a test I rescanned just real channels 29 thru 31 but I set it to "Test Decryptability". That found the missing channel! It shows no directory data but the show is there.

---

### Post by johnvic on 2014-08-16
The problem is solved. I scanned but set the option for "Test Decryptability". I was able to get the channel. I then contacted schedules direct and they included the channel guide. Great service on their part!

---

