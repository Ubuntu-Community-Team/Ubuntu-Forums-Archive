---
title: "INstalling adobe.air apps"
date: 2016-06-06
forum: Multimedia Software
---

### Post by Hamburgian on 2016-06-06
I've managed to install adobe air [http://www.noobslab.com/2015/05/adobeair-is-now-available-for-ubuntu.html]("http://www.noobslab.com/2015/05/adobeair-is-now-available-for-ubuntu.html")
Now I'm trying to install from a CD with an .air archive

Here's what I get in my install log file when running from the installation CD
```
[Adobe AIR Application Installer:9909][INFO] Application Installer begin with version 2.6.0.19170 on Linux x86
[Adobe AIR Application Installer:9909][INFO] Commandline is: 
[Adobe AIR Application Installer:9909][INFO] Installed runtime (2.6.0.19170) located at /opt/Adobe AIR
[Adobe AIR Application Installer:9909][INFO] Unpackaging file:///media/mark/GlobaleWBInt/Install_Win/Global_Intermediate.air to /tmp/FlashTmp.wGKFwF
[Adobe AIR Application Installer:9909][INFO] Application signature verified
[Adobe AIR Application Installer:9909][INFO] Unpackaging/validation complete
[Adobe AIR Application Installer:9909][INFO] No app located for appID 'Global-Intermediate' and pubID 'F58001C6A320BE09FB6D7E092A4A96AA9BF1591A.1'
[Adobe AIR Application Installer:9909][INFO] Converting unpackaged application to a native installation package in /tmp/FlashTmp.wZIlST
[Adobe AIR Application Installer:9909][INFO] Native installation package creation succeeded
[Adobe AIR Application Installer:9909][INFO] Starting app installation to /opt/Macmillan/Global eWorkbook. Installing app Global-Intermediate.F58001C6A320BE09FB6D7E092A4A96AA9BF1591A.1 version v1 using the source file at file:///media/mark/GlobaleWBInt/Install_Win/Global_Intermediate.air
[Adobe AIR Application Installer:9909][ERR] Error occurred during rpm install operation; beginning rollback: [ErrorEvent type="error" bubbles=false cancelable=false eventPhase=2 text="Unhandled exception Error: Only root can install the application" errorID=0]
[Adobe AIR Application Installer:9909][INFO] Rollback complete
[Adobe AIR Application Installer:9909][ERR] Got an unexpected fatal error while in stateInstalling: [ErrorEvent type="error" bubbles=false cancelable=false eventPhase=2 text="Unhandled exception Error: Only root can install the application" errorID=0]
[Adobe AIR Application Installer:9909][INFO] Launching subprocess with commandline /opt/Adobe AIR/Versions/1.0/Adobe AIR Application Installer -runtime /opt -silent -logToStdout -url -location "/opt/Macmillan/Global eWorkbook" -desktopShortcut -programMenu file:///media/mark/GlobaleWBInt/Install_Win/Global_Intermediate.air
[Adobe AIR Application Installer:9909][INFO] Relaunching with elevation
[Adobe AIR Application Installer:9909][ERR] Elevated install failed: error 1  error: dpkg: error processing archive /tmp/FlashTmp.HWhqzE/setup.deb (--install):; parsing file '/var/lib/dpkg/tmp.ci/control' near line 2 package 'globalintermediate.f58001c6a320be09fb6d7e092a4a96aa9bf1591a.1':; error in 'Version' field string 'v1': version number does not start with digit;Errors were encountered while processing:; /tmp/FlashTmp.HWhqzE/setup.deb
[Adobe AIR Application Installer:9909][ERR] Application Installer end with exit code 7
```

and a similar report if I try after copying the CD to my hard drive and running the air installer from there
```
[Adobe AIR Application Installer:3274][INFO] Application Installer begin with version 2.6.0.19170 on Linux x86
[Adobe AIR Application Installer:3274][INFO] Commandline is: /media/WORK/mark/Macmillan/Global_Intermediate.air
[Adobe AIR Application Installer:3274][INFO] Installed runtime (2.6.0.19170) located at /opt/Adobe AIR
[Adobe AIR Application Installer:3274][INFO] Unpackaging file:///media/WORK/mark/Macmillan/Global_Intermediate.air to /tmp/FlashTmp.daesaZ
[Adobe AIR Application Installer:3274][INFO] Application signature verified
[Adobe AIR Application Installer:3274][INFO] Unpackaging/validation complete
[Adobe AIR Application Installer:3274][INFO] No app located for appID 'Global-Intermediate' and pubID 'F58001C6A320BE09FB6D7E092A4A96AA9BF1591A.1'
[Adobe AIR Application Installer:3274][INFO] Converting unpackaged application to a native installation package in /tmp/FlashTmp.LFVH5K
[Adobe AIR Application Installer:3274][INFO] Native installation package creation succeeded
[Adobe AIR Application Installer:3274][INFO] Starting app installation to /media/WORK/mark/Macmillan/Global eWorkbook. Installing app Global-Intermediate.F58001C6A320BE09FB6D7E092A4A96AA9BF1591A.1 version v1 using the source file at file:///media/WORK/mark/Macmillan/Global_Intermediate.air
[Adobe AIR Application Installer:3274][ERR] Error occurred during rpm install operation; beginning rollback: [ErrorEvent type="error" bubbles=false cancelable=false eventPhase=2 text="Unhandled exception Error: Only root can install the application" errorID=0]
[Adobe AIR Application Installer:3274][INFO] Rollback complete
[Adobe AIR Application Installer:3274][ERR] Got an unexpected fatal error while in stateInstalling: [ErrorEvent type="error" bubbles=false cancelable=false eventPhase=2 text="Unhandled exception Error: Only root can install the application" errorID=0]
[Adobe AIR Application Installer:3274][INFO] Launching subprocess with commandline /opt/Adobe AIR/Versions/1.0/Adobe AIR Application Installer -runtime /opt -silent -logToStdout -url -location "/media/WORK/mark/Macmillan/Global eWorkbook" -desktopShortcut -programMenu file:///media/WORK/mark/Macmillan/Global_Intermediate.air
[Adobe AIR Application Installer:3274][INFO] Relaunching with elevation
[Adobe AIR Application Installer:3274][ERR] Elevated install failed: error 1  error: dpkg: error processing archive /tmp/FlashTmp.byKHVg/setup.deb (--install):; parsing file '/var/lib/dpkg/tmp.ci/control' near line 2 package 'globalintermediate.f58001c6a320be09fb6d7e092a4a96aa9bf1591a.1':; error in 'Version' field string 'v1': version number does not start with digit;Errors were encountered while processing:; /tmp/FlashTmp.byKHVg/setup.deb
[Adobe AIR Application Installer:3274][ERR] Application Installer end with exit code 7
```

Adobe's site suggests installing Flash 10.1...which I have as the alternative version, but I installed the original anyway using this method
 [http://milindapro.blogspot.de/2011/08/how-to-install-adobe-flash-player.html]("http://milindapro.blogspot.de/2011/08/how-to-install-adobe-flash-player.html")

From the error message I would assume that it's telling me that I need to be root to do this...but I'm asked for my password and it's accepted before beginning the installation process.
Any ideas? Is there a way I can run this process from a terminal? Would that help?

---

