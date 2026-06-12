---
title: "Mythbuntu 10.10 v0.23 (32bit) Error Messages"
date: 2011-01-26
forum: Mythbuntu
---

### Post by nhtrader on 2011-01-26
I'm a newbie and just completed an installation of Mythbuntu 10.10 v0.23 (32bit) yesterday. It took me 5 days to hash through a number of error messages with the generous help of those within these forums. Thanks to all that helped me to solve these problems.

I thought it would of interest to all to start a thread that consolidates error messages to make it easier for future newbies to find them. If you encounter an error message using this version of Mythbuntu please add it to the list. If you're using a different version, please create another topic/thread.

Here were a few that I encountered...

Error Messages

Frontend Database Configuration Page
Error Msg: Myth could not connect to Database. Please verify your database settings below.

Solution: need to synchronize 4 or 6 files, then using mysql commands reset database
enter terminal mode and use text editor either: pico or nano
These three contents should match...
sudo pico /etc/mythtv/config.xml
sudo pico /home/mythtv/.mythtv/config.xml
sudo pico /home/your_username/.mythtv/config.xml

These three contents should match...
sudo pico /etc/mythtv/mysql.txt
sudo pico /home/mythtv/.mythtv/mysql.txt
sudo pico /home/your_username/.mythtv/mysql.txt


mysql commands:

mysql -uroot -p

mysql>GRANT ALL PRIVILEGES ON mythconverg.* TO 'mythtv'@"localhost" identified $
mysql>GRANT ALL PRIVILEGES ON mythconverg.* TO 'mythtv'@"%" identified by "pass$
mysql>use mysql;
mysql>UPDATE user SET Password=PASSWORD('password here') WHERE user='mythtv';
mysql>FLUSH PRIVILEGES;
mysql>exit


Backend Setup program section 2. Capture Cards
If you have a device listed as [V4L : ] and you select it to view its properties and it shows...
card type: Analog V4L capture card
probed info: failed to open

Solution: You probably don't have an analog capture card. Delete this entry using "Delete capture devices on your_computername".
Then create a new capture device. Use the dropdown box to highlight the option DVB DTV and proceed.



Error Msg: MythTV is using all inputs, but there are no active recordings?
Solution: Need to complete setup within backend setup program. Specifically complete sections: 3. Video Sources & 4. Input Connections
It is likely that no video source was created.



Error Msg: found in frontend | watchTV = Failed to reinitialize video output.

Frontend program | Utilities/Setup | Setup |TV Settings | Playback
(Hit Enter three times to go to the third screen titled "Playback Profiles (3/ 8")

Change Property: "Current Video Playback Profile: to "High Quality" (select from drop down box)

---

