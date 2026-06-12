---
title: "setup static IP address w/ Network Manager"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by Benchrest on 2011-06-11
Setup static IP with Network Manager
to solve 2 problems and one concern

Most info I have found on this subject is several years old and doesn't apply to the current Network Manager 0.8.4 or 0.8.0


Problems 
Anytime my wireless router powers down due to power failure etc. my computers may get different IP addresses assigned. 

This causes problems with my network printer. I have to delete the printer and re-add. This itself is not to bad, but sometimes my envelopes I have saved change for a specific envelope size change to the default letter paper. Not sure why this happens.

Unison profiles to copy to a specific IP address are no longer correct.

Also I want this static IP address to only apply to my home network. If I take my laptop somewhere else I don't want these changes to cause problems


I have found write-ups to make these changes from Terminal. However, even though I have used Ubuntu since 5.04 I find terminal commands confusing because I use them so infrequently. And many times these write-ups are incomplete, assuming me, the user, should know some of the basics.  


So here is how I did it with Network Manager
I have three devices:
Desktop - Lucid Lynx w/ Network Manager 0.8.0 ethernet wired
Laptop - Natty Narwhal w/ Network Manager 0.8.4 wireless
WII - wireless
and Linksys wireless router



Wireless laptop Natty - Network Manager 0.8.4

Display connection information from top panel
wrote down info
IPV4
IP address  xxx.xxx.x.101
Broadcast Address xxx.xxx.x.xxx
Subnet mask xxx.xxx.xxx.x
Default Route (gateway) xxx.xxx.x.x
Primary DNS xx.xxx.xx.xx
Secondary DNS xx.xxx.xx.xx
Ternary DNS xx.xxx.xx.xx
IPV6
Ignored


left click wireless icon
select
Edit Connections
select wireless tab
Select wireless connection to change "mynetwork" 
click edit
select IPv4 tab
change automatic (DHCP) to Manual
click Add

click address area to highlight area to enter
enter IP address xxx.xxx.x.101

click netmask area to highlight
enter subnet mask xxx.xxx.xxx.x

click Gateway area to highlight
enter Default route xxx.xxx.x.x

in the DNS server area enter 
(primary DNS)xx.xxx.xx.xx,(Secondary DNS)xx.xxx.xx.xx,(Ternary DNS)xx.xxx.xx.xx
Three addresses are seperated by comma's



WII

IP address  xxx.xxx.x.102
Broadcast Address xxx.xxx.x.xxx
Subnet mask xxx.xxx.xxx.x
Default Route (gateway) xxx.xxx.x.x
Primary DNS xx.xxx.xx.xx
Secondary DNS xx.xxx.xx.xx



Desktop wired Lucid Lynx Network Manager 0.8.0

Display connection information from top panel
wrote down info
IPV4
IP address  xxx.xxx.x.100
Broadcast Address xxx.xxx.x.xxx
Subnet mask xxx.xxx.xxx.x
Default Route (gateway) xxx.xxx.x.x
Primary DNS xx.xxx.xx.xx
Secondary DNS xx.xxx.xx.xx
Ternary DNS xx.xxx.xx.xx
IPV6
Ignored

Only the IP address is different from the laptop and WII.

The desktop set up I found a bit tricky. Not sure if that was because it is using the older Network Manager 0.8.0 or that its a wired connection.

I could not change the existing connection to static and get it to work.
I had to rename my existing Auto eth0 connection and remove the checkbox to connect automatically. I renamed mine "Old eth0".  Be sure and remember original name and use it below to create new entry.

Then I created a new Auto eth0 with connect auto checked.

left click wired icon
select
Edit Connections
select wired tab
Select add 
add a new Auto eth0
select IPv4 tab
change automatic (DHCP) to Manual

click address area to highlight area to enter
enter IP address xxx.xxx.x.100

click netmask area to highlight
enter subnet mask xxx.xxx.xxx.x

click Gateway area to highlight
enter Default route xxx.xxx.x.x

in the DNS server area enter 
(primary DNS)xx.xxx.xx.xx,(Secondary DNS)xx.xxx.xx.xx,(Ternary DNS)xx.xxx.xx.xx   each address seperated by comma



Wireless router linksys
enter wireless router setup
Yours will be different most likely
enter router address in browser
xxx.xxx.x.x
password
change Automatic Configuration - DHCP
to
Static IP


Test

---

