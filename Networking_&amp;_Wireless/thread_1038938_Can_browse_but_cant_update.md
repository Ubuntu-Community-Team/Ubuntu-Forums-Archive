---
title: "Can browse but cant update"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by nmvictor on 2009-01-14
[FONT="Arial"]Hi everyone,I have a problem with my systems Internet connection.I have a hp desktop and uses wireless connection to access the Internet.My web browser,Mozilla obediently connects me to the Internet with proxy server settings.However,my update manager as well as my gmail-notifier can't connect to the Internet.This is stressing me out:(.what could be the problem?I have tried to locate network settings to try and configure but I can only see Network proxy,Network configuration (in the **Systems>Preference> **tab) and Network tools in the **System>Administration>**tab.)I urgently need to update my system.is anyone out their with the right information on what I can do about this?Please help.Thanks in advance...[/FONT]

---

### Post by HunterThomson on 2009-01-14
> **nmvictor said:**
> [FONT="Arial"]Hi everyone,I have a problem with my systems Internet connection.I have a hp desktop and uses wireless connection to access the Internet.My web browser,Mozilla obediently connects me to the Internet with proxy server settings.However,my update manager as well as my gmail-notifier can't connect to the Internet.This is stressing me out:(.what could be the problem?I have tried to locate network settings to try and configure but I can only see Network proxy,Network configuration (in the **Systems>Preference> **tab) and Network tools in the **System>Administration>**tab.)I urgently need to update my system.is anyone out their with the right information on what I can do about this?Please help.Thanks in advance...[/FONT]

Do you have to connect to the internet through that Proxy ?

Have you tried a wired connection ?

Try to run this in the shell and report back any errors...

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by nmvictor on 2009-02-07
> **HunterThomson said:**
> Do you have to connect to the internet through that Proxy ?

Have you tried a wired connection ?

Try to run this in the shell and report back any errors...

```
sudo apt-get update && sudo apt-get upgrade
```
Thanks Thompson for you suggestion concerning my post "Can browse but Cant update" which I posted three weeks ago.Im sorry it has taken me quite so long to respond but the thing still does'nt work.When i run the command you asked me to at the terminal,it echos that t is connecting to te proxy server but the university proxy I am using is uses athentication and so it fails having not reolved the authentication.Its quite hard for me to configure the username and password with system services search as update manager or the terminal.I have manage to do this with firefox,the browser I am using so I need help on how I can apply this authentication system-wide so that when the update manager tries to fetch for updates from the internet,it askes for the proxy authentication just like the browser does.It would be great if you helped me out on this .Thanks again.

---

