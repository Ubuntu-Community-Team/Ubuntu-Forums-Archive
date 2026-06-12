---
title: "How to configure Proxy Server with Authentication"
date: 2013-03-28
forum: Networking &amp; Wireless
---

### Post by hartz on 2013-03-28
My work proxy server requires authentication with the Microsoft domain user credentials.  Everybody knows how it works:  If you log in on a Windows workstation, your "Internet Explorer" browser based internet access requests are automatically authenticated (and identified) using your domain login credentials.

I found that Firefox can also authenticate against these proxy servers and long assumed that they "do something special".  Recently a colleague installed Linux Mint in a VM and to my surprise he was busy getting updates from the internet.

This prompted me to re-look at the proxy settings.  I run Kubuntu (with a mix of G* and K* applications, but I only use the GTK applications when I'm convinced that they are much better than anythink K*)

I do still have a copy of Windows running in a VM, mainly for Printing and for accessing internal/corporate web sites (Which both requires authentication and identification via MS domain credentials) as well as for changing my domain password every so many days.

So it would be very helpfull if I could get [some/most/all] of my Linux applications to work via the proxy server.  My most urgent needs are for Akregator and Muon to be able to work.  Other applications that may benefit are some apps that auto-update (Virtual Box Extentions) or wrap themselves around a browser (Get More Themes/Wall Papers/etc comes to mind, and the occasional use of wget)

SSH/SCP clients manage to work via the firewall without authentication.

What is the right way (tool and process) to configure this, ideally in a single location because having to maintain my password in multiple locations is a recipe for getting locked out of my account :-/

Oh, and it would be a dream come true if I could have the equivalent to the Firefox Quick Proxy proxy disable/enable utility, eg one click to enable or disable it depending on what network I'm on.  Actually thinking about it, a utility should be trainable to look at your IP address and know when you need to use the proxy!  But I digress.

Thank you,
  _Hartz

---

### Post by hartz on 2013-04-12
I am closer to a solution but not quite there yet.

I found a program called cntlm.  Installing and setting it up took only 10 minutes.

This program runs as a service and acts as an HTTP proxy, but it is configured to forward the requests to an upstream proxy.  However when it forwards the requests, it adds NT / LM authentication to the requests, and in particular it has support for NTLMv2 which is used by Microsoft ISA.

Using this program I have had partial success.

1. Muon uses APT (via apt-get) in the background.  Setting up APT to use the local cntlm proxy works fine.

2. Wget uses a .wgetrc config file, which works to make it connect through the cntlm proxy.

3. Chromium uses the KDE global settings for Proxy, which also works to allow it to connect via cntlm to the internet.

4. Akregator, Konqueror, Rekonq, the Plasma Desktop Add-on installer all aparently uses the KDE global settings but does not do so properly.  See below for details.

None of these programs even have local Proxy settings - KDE global settings appears to be the only way to configure them to use a proxy.  At least there is no way to do this in the application's GUI (Konqueror directly opens up the KDE global proxy settings)

5. VirtualBox uses a proxy for checking for updates as well as for downloading the Virtual Box Guest additions add-on.  Configuring it to point to the cntlm proxy also works fine.

6. Firefox works perfectly well by being pointed directly to the ISA proxy server, using it's own authentication mechanism.  When told to use the System proxy settings it fails.

I have not yet tested Firefox configured to use the CNTLM proxy server.  This would be ideal as I would then only need to set my password up in a single place, i.e cntlm, as opposed to also having to keep it up to date in Firefox's own password store.

I cannot thoroughly test KRDB, Torrent Clients, SSH clients or FTP clients as these work directly through the ISA server without problems.

I have not yet tested any of the instant messaging clients, dropbox or music players (connect to the internet for CDDB updates), or realy anything else besides.

The problem with the Applications mentioned in Nr 4 above is that they are affected by the KDE settings, but I can't get them to work.  In particular when I move to a direct internet connection while still having the KDE setting configured to pass through the cntlm proxy server, then they fail to connect (timeout).  If I then change the KDE setting to None, then they can connect immediately, which clearly shows they are affected by the settings there.

Of course when I am working behind the ISA proxy server, they don't work at all, regardless of the KDE proxy setting.  The cntlm log do not show any activity for any of these applications, while chromium works perfectly.

Any ideas what gives?

---

### Post by hartz on 2013-04-12
I have now confirmed that Firefox configured directly to use the cntlm proxy server does work, I will update my test results in the previous post.

---

### Post by hartz on 2013-04-12
A question about how to set the proxy configuration:

In Firefox manual proxy configuration, one uses the server name (or IP address) and port number, but in other places like the environment variables, eg http_proxy, one uses a URL format, such as "http://localhost:3128"

What format should be used in KDE's global proxy settings?  I assume that when filling in the values under "Use System proxy configuration", one uses a URL-format, while under the "Use manually specified proxy configuration" one uses a sever name or IP-address and a port number?  Does any of these (KDE) settings require a reboot or a logout/login to take effect?  

Why doesn't http_proxy (set in /etc/profile or /etc/bash.bashrc) get used (even after a reboot)

---

### Post by jferna57 on 2013-04-16
I'm a cntlm user for several years and works very well for me, but I'm unity user, not kde... 

Unity (until Ubuntu 12.10) has an option to apply the proxy settings to "system wide" (Ubuntu 13.04 don't have this option).

Regards.

---

### Post by hartz on 2013-04-16
KDE has a similar "System Wide" settings option, in fact there are two subtly different options.

I don't understand the difference between them.  The options are found under System Settings-> Network Settings-> Proxy

The choices are:
No Proxy
Detect proxy configuration automatically
Use proxy auto configuration URL
Use system proxy configuration
Use manually specified proxy configuration

I am having reasonable success with a combination of the last option and CNTLM.

But what exactly is the difference between the last two options?  I am guessing "System" is wider than KDE, and the last option is a manual configuration that applies to KDE and KDE-friendly apps only, while System would apply to KDE and everything outside of it as well.  But how to sucesfully set the system proxy configuration, and then how to dynamically change it whenever I need to, eg without reboots or log-out required.

[ATTACH=CONFIG]241437[/ATTACH]

---

