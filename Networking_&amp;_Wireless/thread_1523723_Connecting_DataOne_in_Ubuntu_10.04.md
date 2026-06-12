---
title: "Connecting DataOne in Ubuntu 10.04"
date: 2010-07-04
forum: Networking &amp; Wireless
---

### Post by wenkey27 on 2010-07-04
Hello.

I am using Ubuntu 10.04 inside Windows 7.

I'd like to know how to connect to the internet in Ubuntu 10.04. I have Huawei SmartAX MT 882 modem and ISP is DataOne. The instructions provided for earlier versions of Ubuntu don't seem to work.

Thanks in advance.

---

### Post by dineshs on 2010-07-05
Configure NM as follows
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection  
select ipv4 
method-manual 
click add 
address 192.168.1.100 
mask 255.255.255.0 
gateway 192.168.1.1 
then hit [COLOR="Blue"]enter[/COLOR] 
DNS 4.2.2.1
then click apply 
Now configure your modem as follows (if your ADSL-link is orange in colour you need not do the following)
Open browser (Firefox)
Type 192.168.1.1 in Address bar. click GO
Enter both Username and Password as [COLOR="Blue"]admin[/COLOR]
Click OK
Click the + sign left to home
Click WAN settings 
select PPP as WAN type
Enter  Username and Password as allotted by BSNL in the respective fields 
Select max idle time- Always on
Apply the settings
The system will ask for reboot .
Tick Yes and Click OK.
Wait till reboot complete (3 minutes).
This method gives an *always on* internet connection ie you can directly access sites via firefox

---

