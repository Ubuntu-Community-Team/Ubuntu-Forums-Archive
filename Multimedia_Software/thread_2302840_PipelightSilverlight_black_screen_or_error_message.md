---
title: "Pipelight/Silverlight black screen or error message playing Netflix in Firefox"
date: 2015-11-13
forum: Multimedia Software
---

### Post by chuckroast2 on 2015-11-13
I'm brand spanking new to Ubuntu, trying it at the recommendation of friends. It's like I'm in another country. At this point I'm just trying to get the pieces in place so that my computer does the things it does in Windows 7. Among them is to get Silverlight working. I installed it using:


sudo add-apt-repository ppa:pipelight/stable
sudo apt-get update
sudo apt-get install --install-recommends pipelight-multi
sudo pipelight-plugin --update


All seemed well with the install, but when I tried playing a video in Firefox, the browser window went black. When I clicked the refresh button, I got the following error message:


Add-ons: %7B2e1445b0-2682-11e1-bfc2-0800200c9a66%7D:2014.07.01.beta,ubufox%40ubuntu.com:3.0,online-accounts%40lists.launchpad.net:0.5,%7B972ce4c6-7e08-4474-a285-3208198ce6fd%7D:37.0,webapps-team%40lists.launchpad.net:3.0.2
BuildID: 20150328222441
CrashTime: 1447428013
EMCheckCompatibility: true
FramePoisonBase: 7ffffffff0dea000
FramePoisonSize: 4096
InstallTime: 1447341646
Notes: OpenGL: X.Org -- Gallium 0.4 on AMD OLAND -- 3.0 Mesa 10.5.9 -- texture_from_pixmap


ProductID: {ec8030f7-c20a-464f-9b0e-13a3a9e97384}
ProductName: Firefox
ReleaseChannel: release
SecondsSinceLastCrash: 2507
StartupTime: 1447426896
Theme: classic/1.0
Throttleable: 1
URL: [http://www.netflix.com/watch/70178030?trkid=14170286&tctx=6%2C0%2C41b70db9-f4ad-4ae7-b76b-9cf58e12b908-37075963](http://www.netflix.com/watch/70178030?trkid=14170286&tctx=6%2C0%2C41b70db9-f4ad-4ae7-b76b-9cf58e12b908-37075963)
Vendor: Mozilla
Version: 37.0
useragent_locale: chrome://global/locale/intl.properties


This report also contains technical information about the state of the application when it crashed.



I'm using Ubuntu 15.04, Firefox version 37, my computer is a new-ish IBuyPower so graphics hardware is not an issue. I've searched extensively, but I just can't seem to find anybody with exactly the same issues. Any help you can give would be greatly appreciated.

---

### Post by chuckroast2 on 2015-11-14
Okay, after a whole lot more research, I have uninstalled Chromium, installed the latest Chrome, and stopped using the agent override.  It works.

---

### Post by Rick St. George on 2015-11-18
There is something wrong with your command. The funny face should be a colon. But here;
> 
sudo apt-get install --install-recommends pipelight-multi

I get the following Error;
The following packages have unmet dependencies:
 pipelight-multi : Depends: mesa-utils but it is not installable
                   Depends: wine-staging
E: Unable to correct problems, you have held broken packages.

Anyone have any ideas on this?
Thanks!

---

