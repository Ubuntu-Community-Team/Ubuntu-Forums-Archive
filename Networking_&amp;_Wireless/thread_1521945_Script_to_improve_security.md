---
title: "Script to improve security"
date: 2010-07-01
forum: Networking &amp; Wireless
---

### Post by birkopf on 2010-07-01
I will be connected to "communal" wifi network in few days and I know that some students in the building have often sleepless nights :rolleyes: 
At night their curiosity goes through the roof... 

I have enabled UFW and have taken few other steps to secure my Lucid's viriginity \\:D/  although idea poped to my mind. 

I created siple script which will be setting random MAC address to my wifi everytime system starts. Problem is - it needs root password. Is there any safe method to automate it?

Script as follows: 
#!/bin/sh
echo “Starting MAC Procedure”
sudo ifconfig wlan0 down
sudo macchanger -A wlan0
sudo ifconfig wlan0 up
echo “MAC Procedure Finished”

I plan to stick it in init.d so that it can start with boot scripts...

- How to make it automated ?

---

