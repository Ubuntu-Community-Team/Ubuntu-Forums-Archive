---
title: "AirUWS-Lite conecting a ubuntu laptop to UWS wireless network"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by chrisbay90 on 2010-10-06
Hi all, just thought I would share my long awaited success with connecting my ubuntu laptop up to my universities (University of Western Sydney) wireless network. The rumors appeared true and they have finally implemented 802.11x authentication instead of that horrible java app netdirect im sure you've been cursing at its erratic stability.

There is no linux documentation for airUWS-Lite nor anything more imformative than there windows/mac point and click steps found at [http://www.uws.edu.au/campuses_structure/cas/services_facilities/it/helpdesk/fact_sheets](http://www.uws.edu.au/campuses_structure/cas/services_facilities/it/helpdesk/fact_sheets)

However with a few simple clicks you can have stable working connection.

When connecting make sure you have theses settings.
Security: WPA & WPA2 Enterprise
**Authentication: Protected EAP (PEAP)   #This is the settings that does not present itself correctly**
Anonymous Identity: leave blank
PEAP Version: Automatic
Inner Authentication: MSCHAPv2
Username: <YOUR 8 DIGIT STUDENT NUMBER>
Password: your regular password

Enjoy

---

### Post by La_Lata on 2011-08-17
G'day fellow UWS'er
 
I am sitting here at the Bankstown campus and have these settings on my Xubuntu 11.04 Notebook.
 
All my settings are exactly as you have stipulated but all I have access to is vUWS. 
 
Apart from that there is nothing i can load up. I've tried google.com, facebook.com and uws.edu.au. None of them load up. The browser just sits there with the loading circle working away and eventually times out.
 
Please help as IT Support is hopeless here.

---

### Post by chrisbay90 on 2012-08-30
Hello La_Lata, seems about about a year to late. But worth asking anyway. How did you go with this, still in need of help? Did you set the proxy in your browser?

EDIT: You must set your browser to use the proxy settings in the pac file [http://autoproxy.uws.edu.au/proxy.pac](http://autoproxy.uws.edu.au/proxy.pac)
So for firefox. Edit > Preferences > Advanced > Network> Settings
Automatic confuguration URL: [http://autoproxy.uws.edu.au/proxy.pac](http://autoproxy.uws.edu.au/proxy.pac)

To get apt-get or internet services on the command line to work run:
export http_proxy=http://<STUDENTID>:<PASSWORD>@proxy.uws.edu.au:3128
at the terminal

---

