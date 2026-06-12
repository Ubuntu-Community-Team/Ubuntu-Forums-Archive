---
title: "problem connecting to VPN through firefox using Juniper"
date: 2012-03-12
forum: Networking &amp; Wireless
---

### Post by tuathan on 2012-03-12
I'm using Ubuntu with Mozilla Firefox 3.6.17 (Ubuntu) to try and connect to my work VPN. 
When i go to the remote access webpage it attempts to install Juniper Networks Inc. Host Checker but it fails and i get the following message:

 >   Loading Components...
    Please wait. This may take several minutes.
    	• 	
    Host Checker
    	
    If an error prevents a component from loading properly, you can click here to continue. Not all functionality may be available.
    Your browser does not support either ActiveX controls or Java applets. Please contact your administrator.

Any ideas why? thanks

---

### Post by tuathan on 2012-03-12
The Java plugin wasnt properly installed with Firefox. I created a symbolic link to the java plugin in the firefox directory. Now i am getting:

>     Loading Components...
    Please wait. This may take several minutes.

    	• Host Checker
    	
    If an error prevents a component from loading properly, you can click here to continue. Not all functionality may be available.



Juniper Host Checker is still not installed...

---

