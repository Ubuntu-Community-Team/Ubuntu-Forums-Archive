---
title: "Jackd problem, cannot start"
date: 2011-12-11
forum: Multimedia Software
---

### Post by soyodi on 2011-12-11
Ever since i installed Ubuntu 11.10 i havn't been able to get jackd to run. I even completely removed pulseaudio but the problem persists exactly as it did before. The main reason I want to use linux is for audio production purposes so any help to get this running  would be greatly appreciated! 

This is what I get when I open QjackCtl :

 p, li { white-space: pre-wrap; }  [COLOR=#999999]18:36:59.310 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]18:36:59.316 Statistics reset.[/COLOR]
 [COLOR=#cccc99]18:36:59.320 ALSA connection change.[/COLOR]
 [COLOR=#999999]18:36:59.363 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 JackSocketClientChannel read fail
 Cannot open qjackctl client
 [COLOR=#66cc99]18:37:04.411 ALSA connection graph change.[/COLOR]
 Sun Dec 11 18:37:04 2011: [1m[31mERROR: JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
 Sun Dec 11 18:37:04 2011: [1m[31mERROR: Driver is not running[0m
 Sun Dec 11 18:37:04 2011: [1m[31mERROR: Cannot create new client[0m


..and if I click the start button this is the message I get:


 p, li { white-space: pre-wrap; }  [COLOR=#ff0000]18:41:51.487 D-BUS: JACK server could not be started. Sorry[/COLOR]
 [COLOR=#999999]JackSocketClientChannel read fail[/COLOR]
 [COLOR=#999999]Cannot open qjackctl client[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: [1m[31mERROR: JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: [1m[31mERROR: Driver is not running[0m[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: [1m[31mERROR: Cannot create new client[0m[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: driver "alsa" selected[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Saving settings to "/home/martin/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: Starting jack server...[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: [1m[31mERROR: `default' server already active[0m[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:41:51 2011: [1m[31mERROR: Failed to open server[0m[/COLOR]
 [COLOR=#ff0000]18:42:01.094 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 [COLOR=#999999]JackSocketClientChannel read fail[/COLOR]
 [COLOR=#999999]Cannot open qjackctl client[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:42:01 2011: [1m[31mERROR: JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:42:01 2011: [1m[31mERROR: Driver is not running[0m[/COLOR]
 [COLOR=#999999]Sun Dec 11 18:42:01 2011: [1m[31mERROR: Cannot create new client[0m[/COLOR]

---

