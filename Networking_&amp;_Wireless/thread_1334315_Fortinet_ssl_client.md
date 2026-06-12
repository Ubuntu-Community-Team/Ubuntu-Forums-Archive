---
title: "Fortinet ssl client"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by jack frost on 2009-11-22
Sorry if this has been asked; but my work has fortinet vpn client , or the forti ssl webclient for our vpn connection.. I am trying to not have to use windows when i work from home for remote desktop. I have not been able to find a forti linux ssl client installer. I asked our network group and they said there was not one. We used to use cisco and I was able to connect in linux using vpnc and finding some solutions on the web. Any help is apprectiated. thanks.

---

### Post by petsch on 2010-01-12
You have to download the forticlientsslvn from fortinet-support, then just unpack it and start the forticlientsslvpn program. First time it asks for root-pw. 
After that you can just connect with IP and port (it suggests 10443, but probably your fortigate is configured to port 443)

[https://support.fortinet.com](https://support.fortinet.com)
left menu: Firmware-Images
then click Fortigate, then navigate to V4.00, then to SSL VPN Clients, (or) download [forticlientsslvpn_linux_4.0.2010.tar.gz]("ftp://pftpintl:F0rt1intl@support.fortinet.com/FortiGate/v4.00/4.0/4.0.0/SSL%20VPN%20Clients/forticlientsslvpn_linux_4.0.2010.tar.gz")

---

### Post by jack frost on 2010-01-12
> **petsch said:**
> You have to download the forticlientsslvn from fortinet-support, then just unpack it and start the forticlientsslvpn program. First time it asks for root-pw. 
After that you can just connect with IP and port (it suggests 10443, but probably your fortigate is configured to port 443)
 
[https://support.fortinet.com](https://support.fortinet.com)
left menu: Firmware-Images
then click Fortigate, then navigate to V4.00, then to SSL VPN Clients, (or) download [forticlientsslvpn_linux_4.0.2010.tar.gz]("ftp://pftpintl:F0rt1intl@support.fortinet.com/FortiGate/v4.00/4.0/4.0.0/SSL%20VPN%20Clients/forticlientsslvpn_linux_4.0.2010.tar.gz")
 
 
thanks!!! this is one of the last things i needed to no have to use windows.

---

### Post by jack frost on 2010-01-13
> **petsch said:**
> You have to download the forticlientsslvn from fortinet-support, then just unpack it and start the forticlientsslvpn program. First time it asks for root-pw. 
After that you can just connect with IP and port (it suggests 10443, but probably your fortigate is configured to port 443)
 
[https://support.fortinet.com](https://support.fortinet.com)
left menu: Firmware-Images
then click Fortigate, then navigate to V4.00, then to SSL VPN Clients, (or) download [forticlientsslvpn_linux_4.0.2010.tar.gz]("ftp://pftpintl:F0rt1intl@support.fortinet.com/FortiGate/v4.00/4.0/4.0.0/SSL%20VPN%20Clients/forticlientsslvpn_linux_4.0.2010.tar.gz")
 
 i also found this:
[http://portal.modeldriven.org/sites/default/files/SSL_VPN_Client_User_Guide.pdf](http://portal.modeldriven.org/sites/default/files/SSL_VPN_Client_User_Guide.pdf)
 
within the pdf it has another download link too.

---

### Post by jack frost on 2010-01-15
> **jack frost said:**
> i also found this:
[http://portal.modeldriven.org/sites/default/files/SSL_VPN_Client_User_Guide.pdf](http://portal.modeldriven.org/sites/default/files/SSL_VPN_Client_User_Guide.pdf)
 
within the pdf it has another download link too.
 
 
just wanted to report that with the guide and the download.. the vpn software works great.. i don't have to boot into my windows partition anymore unless i want to sync my zune player.  thanks again.. the ubuntu forums are the best.. everyone is always out there to help.

---

### Post by java.artisan on 2011-01-31
Did someone every heard of the Forti Client working ONLY in windows and not Linux - using the very same configuration & certificate ? Some faulty server settings ? Old server software ?

Our sysadmin gave up on me. As it works in windows I should just use that. 

Maybe somebody in here has an advise I can forward to him ? :-)

---

### Post by jack frost on 2011-02-06
> **java.artisan said:**
> Did someone every heard of the Forti Client working ONLY in windows and not Linux - using the very same configuration & certificate ? Some faulty server settings ? Old server software ?

Our sysadmin gave up on me. As it works in windows I should just use that. 

Maybe somebody in here has an advise I can forward to him ? :-)

I am using ubuntu 10.10 and it works fine.. just go to the link and download the sslvln client.. once you unpack run it as root and it will ask you to read the eula..scroll through then  say yes to accept.. the client is now on your machine.. for my company 
once I did that I just go to our vpn link and selced RDP as the protocol to connect and It launches the RDP client in linux to connect. the very fiirst time you run it to connect you have to agree to connect and I chose to always trust it. It then opened a window to select the size I wanted then my desktop at work opens.  The version in the link is 4.010; but my network dept gave me the updated one that is 4.0.2082.  I actually came back to this thread to see if  there was an updated client and saw your post.  Hope this info. helps. I think it will depend how your company has the vpn log on  page set up for your work.

---

### Post by jack frost on 2011-02-06
> **petsch said:**
> You have to download the forticlientsslvn from fortinet-support, then just unpack it and start the forticlientsslvpn program. First time it asks for root-pw. 
After that you can just connect with IP and port (it suggests 10443, but probably your fortigate is configured to port 443)

[https://support.fortinet.com](https://support.fortinet.com)
left menu: Firmware-Images
then click Fortigate, then navigate to V4.00, then to SSL VPN Clients, (or) download [forticlientsslvpn_linux_4.0.2010.tar.gz]("ftp://pftpintl:F0rt1intl@support.fortinet.com/FortiGate/v4.00/4.0/4.0.0/SSL%20VPN%20Clients/forticlientsslvpn_linux_4.0.2010.tar.gz")

do you have a log on you use to get to the downloads section.. i wanted to check for the latest client but it is requiring me to have an account etc. I tried to create one;but It was the serial number etc.  or if you can give the link to the latest version, or ftp directory. .thanks.

---

### Post by salamandro on 2011-05-09
> **petsch said:**
> You have to download the forticlientsslvn from fortinet-support, then just unpack it and start the forticlientsslvpn program. First time it asks for root-pw. 
After that you can just connect with IP and port (it suggests 10443, but probably your fortigate is configured to port 443)

[https://support.fortinet.com](https://support.fortinet.com)
left menu: Firmware-Images
then click Fortigate, then navigate to V4.00, then to SSL VPN Clients, (or) download [forticlientsslvpn_linux_4.0.2010.tar.gz]("ftp://pftpintl:F0rt1intl@support.fortinet.com/FortiGate/v4.00/4.0/4.0.0/SSL%20VPN%20Clients/forticlientsslvpn_linux_4.0.2010.tar.gz")

I was having trouble with this client version on 11.04 64bit, but there's what looks like a new version under MP3 on the ftp and the new one worked at once.  

Thanks for the id/pass.

---

### Post by java.artisan on 2011-06-28
Confirming this works for 64bit Ubuntu distro's !

The routing isn't restored after disconnection though. Can't reach the internet anymore then.

But anyway, better this than the pevious case.

Thank you !

---

### Post by melhiore on 2011-07-22
Just a quick question. I do have SSL VPN client installed. I can run tunnel but traffic is not going through the tunnel but using my LAN or WAN connection. Obviously I can not get to my company LAN addresses. I can not see packets floating via SSL VPN tunnel.

Is there any magic trick that I have to perform to force certain traffic to go via tunnel or it should go automagically???

So far I'm using not recommended by company but build in to NM PPTP client which is working fine but I would like to use SSL client...

System: Ubuntu 11.04 64bit.

---

### Post by nosebreaker on 2011-10-27
I do remember there being an (unofficial) bug with it, that a newer firmware fixed.  I think 4.0 MR3 patch 1 and newer fixed that problem where linux couldn't connect, or roll back to 4.0 MR2 patch 7 (I don't remember the exact version).

---

### Post by aerobrent on 2012-06-01
This thread may be getting old, but I came across it today when having troubles getting the latest available Fortigate SSL VPN client running on a 64 bit Ubuntu (XUbuntu 12.04 amd64) machine.

It appears the Fortigate SSL VPN clients are 32 bit applications.  Install the 32 bit compatibility libraries (ia32-libs) if you're having problems getting the client to run on a 64 bit Ubuntuish distro, and things should come right.

This solved my problem and now the client runs.

---

### Post by russki on 2012-06-11
Guys,

Have they closed access to VPN client recently? I'm trying to get to the download section of Fortinet site, but it requires login now.

---

### Post by Andre-D on 2012-11-26
anyone got fortigate forticlient to work on ubuntu 12.10 ?
- I see SSLVPN just fine, the client connects, but the SSLVPN does not recognize that there're any tunnel up, and there's no new route.

---

### Post by shuqi on 2012-12-11
> **Andre-D said:**
> anyone got fortigate forticlient to work on ubuntu 12.10 ?
- I see SSLVPN just fine, the client connects, but the SSLVPN does not recognize that there're any tunnel up, and there's no new route.
Did you manage to get it working under 12.10?
I've been trying as well, but it keeps on getting stuck during the "starting daemon" phase, whereas it runs just fine under ubuntu 11.

---

### Post by Andre-D on 2012-12-11
no, It appears to work, (the client works) but the webpage fails to notice that it's up.
also, there's no new routes.
Fortinet support next.

---

