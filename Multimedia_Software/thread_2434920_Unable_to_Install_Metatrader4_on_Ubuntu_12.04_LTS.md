---
title: "Unable to Install Metatrader4 on Ubuntu 12.04 LTS"
date: 2020-01-13
forum: Multimedia Software
---

### Post by djatkins on 2020-01-13
- My computer settings;
ubuntu 12.04 LTS
2Gb memory
intel core 2 duo@2.4GHz
32-bit


-Why 12.04?
Its an old laptop thathas shown vulnerability. I have a concern that a newer update woulddestabilize it, as it did with windows OS and the only alternativewas to switch to ubuntu.


-What is the issue
When I right click theinstallation exe to open with wine..it simply loads and thennothingness


I suspect it has to dowith wine functionality, so the following are the ways in which i tried to resolve the issue. However, if there are any other software suggestions out there that will allow me to access 
metatrader4 from ubuntu 12.04 let me know  and I will try them.


-What I have done sofar 



[LIST=1]	
[*] 	
		sudo apt-get –purge	remove wine
[/LIST]



[LIST=1]	[COLOR=#333333][FONT=Monaco, Menlo, Consolas, Courier New, monospace]sudo add-apt-repository ppa:ricotz/unstable[/FONT][/COLOR]

[COLOR=#333333][FONT=Monaco, Menlo, Consolas, Courier New, monospace]sudo apt-get update[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New, Courier, monospace]sudo apt-get install wine-stable[/FONT][/COLOR]
	
[*][COLOR=#000000][FONT=Courier New, Courier, monospace]unchecked proprietory drivers (restricted) @ software center[/FONT][/COLOR]
[/LIST]

[LIST=1]	
[*][COLOR=#000000][FONT=Courier New, Courier, monospace]Wine configuration, add application, select exe file[/FONT][/COLOR]
[/LIST]

[LIST=1]	
[*][COLOR=#000000][FONT=Courier New, Courier, monospace]sudo apt-get –purge remove wine[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New, Courier, monospace]sudo add-apt-repository ppa:ubuntu-wine/ppa[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New, Courier, monospace]sudo add-get update[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New, Courier, monospace]sude add-get install wine [/FONT][/COLOR]
[/LIST]


[COLOR=#000000][FONT=Courier New, Courier, monospace]Let me know what else I can try in order to access the installation for metatrader4[/FONT][/COLOR]

---

### Post by TheFu on 2020-01-13
Check this out: [https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)

---

