---
title: "Unable to connect to wireless at my university"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by Modax42 on 2009-02-12
This really ticks me off.  I USED to be able to connect to their network on Linux but they recently "upgraded" their security system somehow and now it won't work.  The only useful information I was able to get out of the IT staff was the following message:

>  It is possible to connect to UWS using Ubuntu Linux. The security certificate used is usually Thawte Premium Server CA.

The network is detected by the Network Manager, but when I enter my authentication information, it asks for a security certificate, which I do not have, then crashes.  I have attached a couple of screenshots to show this.

These are the instructions posted on their site for connecting with win XP.  There are no instructions for linux.



>  Connecting with Windows XP
Step 1 - Open Network Connections

Click on the Start button and select Run.
Type in ncpa.cpl and click OK.
Step 2 - Add a Wireless Network Connection

Right click on Wireless Network Connection and select Properties.
Click on the Wireless Networks tab and click Add....
Step 3 - Configure WPA Support

Enter UWS(all capital letters) as the Network name(known as a SSID).
Select WPA for Network Authentication
Select TKIP for Data encryption.
Step 4 - Setup Authentication

Click on the Authentication tab.
Select Protected EAP (PEAP) from the EAP type pull-down menu.
Make sure the checkboxes below are unchecked.
Click on the Properties button.
Step 5 - PEAP Properties

Select Secured password (EAP-MSCHAP v2) as the Authentication Method.
Click on the Configure... button.
Make sure that Automatically use my Windows logon name and password (and domain if any) is unchecked.
Step 6 - Accept All Settings

Click OK until you get back to the Wireless Network Connection Properties window.
If HowtoConnectToUWS is in Preferred networks, select it and click on Remove.
UWS should be in the list and HowtoConnectToUWS should not.
Click OK.
Step 7 - Enter CCID and Password

Click the balloon asking about certificates or other credentials with UWS.
In the Enter Credentials window, enter your Campus Computing ID (CCID) as the User name and your CCID password in the password field.
Leave Logon Domain blank. Click OK.
Step 8 - Process Logon Information

Another pop-up balloon from the taskbar will appear. Click on this notification.
In the Validate Server Certificate window, click on Ok.
Step 9 - Connected

You are now connected to the network!
From now on, you will automatically connect to UWS whenever your computer is in range.
You will have to sign in with your CCID and password whenever you connect.


I have followed these instructions as I can, and all of my authentication information is as it should be.  If anyone can lend a hand with this I would be eternally grateful.  I'm using 8.10.

---

