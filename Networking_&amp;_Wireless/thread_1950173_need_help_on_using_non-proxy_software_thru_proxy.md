---
title: "need help on using non-proxy software thru proxy"
date: 2012-03-31
forum: Networking &amp; Wireless
---

### Post by naira on 2012-03-31
[FONT=Times New Roman]Hi guys,[/FONT]
 
[FONT=Times New Roman]I need help with using 2 online trading software (trading platforms), from behind a firewall.[/FONT]
 
[FONT=Times New Roman]To start with, I access the internet from my company’s LAN, which has a restrictive firewall, so I cannot request the admin to open any ports manually for me. Hence I use a software called your-freedom, available at [http://www.your-freedom.net/ems-dist/freedom-20120328-01.exe](http://www.your-freedom.net/ems-dist/freedom-20120328-01.exe). This proxy software supports both http as well as socks 4 and 5 proxy (by entering the proxy IP 127.0.0.1 (localhost) and Port 8080 for http proxy OR 1080 for Socks Proxy), and I have successfully been using web browsers and some other softwares that support proxy/ allow proxy info to be entered to login/ connect to the internet. Your-Freedom also supports port forwarding.[/FONT]
 
[FONT=Times New Roman]However, the softwares I intend to use do not have any options to enter proxy methods or proxy ports (as far as I have noticed). I have tried to proxify these 2 softwares using softwares such as SocksCap and Free Cap, but either they don’t work, or my settings in proxifying are not correct. I believe I will have to do port forwarding or proxify the softwares, but have been unable to do so in the correct manner. Can you please guide me **_(with screenshots)_** about which settings to be done in the your-freedom client or please tell me if I can make any manual changes to any config file for the softwares on my system.[/FONT]
 
[FONT=Times New Roman]Following is the info on the 2 softwares:[/FONT]
 
[FONT=Times New Roman]**_1. NOW Trading terminal:_**[/FONT]
[FONT=Times New Roman]Normally when I start the NOW or Zerodha software, the software starts and I get a login screen, but under firewall conditions, I get the initial Splash screen but then the software stops with the error: **_NOW Initialisation failed for Interactive Engine << os error>>._** Software is available for downloading and trial [http://www.zerodha.com/download/Setup/NOW_V.1.7.1.0_SETUP.zip](http://www.zerodha.com/download/Setup/NOW_V.1.7.1.0_SETUP.zip)[/FONT]
[FONT=Times New Roman]http://www.zerodha.com/download/Setup/Zerodha_Trader_Setup_V.3.10.57.96.1.exe [/FONT]
[FONT=Times New Roman]_**2. PowerIndia Bulls:**_[/FONT]
[FONT=Times New Roman]The software is written in Java and starts with a batch file (PowerIndiabulls.bat) located in C:\Users\DEFAULT_USERNAME\AppData\Roaming\Indiabulls Securities Ltd\Power Indiabulls\PowerIndiabulls.bat. I converted this batch file to .exe (with battoexe software) and then ran it through a proxifying software. The .exe start properly without proxifying software but not under proxifying environment. Basically the software needs to connect to the internet using Port 443. I am also expected to keep ports 443, 41599 and 59598 open. Help about the software's requirement is available at [http://www.indiabulls.com/securities/customercare/technical_faq.htm#](http://www.indiabulls.com/securities/customercare/technical_faq.htm#) (item no. 5).[/FONT]
[FONT=Times New Roman]To confirm, while the software is **_unable_** to connect through port 443, you will get an error message: "Connection to Login Server could not be established" when you try to login with any random Username and Password.[/FONT]
[FONT=Times New Roman]To know that the software is able to _**connect properly**_, you will get an error: "This User ID is not enabled to be used with this product".[/FONT]
 
[FONT=Times New Roman]Please help me in connecting these 2 softwares from behind firewall using your-freedom.net[/FONT]

---

