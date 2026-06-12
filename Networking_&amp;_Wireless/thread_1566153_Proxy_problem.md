---
title: "Proxy problem"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by Ghost_Mazal on 2010-09-02
Hi all ,
 
I have a problem setting my proxy info.
We access internet through a Windows ISA proxy and our proxy user details authenticate to a Windows domain.
 
Help documents say that you must add the following to /etc/bash.bashrc
 
[COLOR=black][FONT=Verdana]```
http_proxy=http://username:password@host:port[/FONT][/COLOR]
[FONT=Verdana][COLOR=black]export http_proxy[/COLOR][/FONT]
```
 

[COLOR=black][FONT=Verdana]I did this , then run source /etc/bash.bashrc to load it.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]The I run a apt-get install command. The system see the proxy but I keep getting error 407 authentication required error from the proxy.[/FONT][/COLOR]
 

[COLOR=black][FONT=Verdana]Can some one please help with the correct syntex and format that the username and password must be for Windows proxy please.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Formats I have tried :[/FONT][/COLOR]
 
 
```

[FONT=Verdana][COLOR=black][COLOR=black][FONT=Verdana]....[http://domain\username:password@proxy:port/]("http://domain/username:password@proxy:port/")[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]....[http://domain\\username:password@proxy:port/]("http://domain//username:password@proxy:port/")[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]....[http://]("http://L")username@domain:password@proxy:port/[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]....http:[//domain@username:password@proxy:port/]("http://domain@username:password@proxy:port/")[/FONT][/COLOR][/COLOR][/FONT]
```[FONT=Verdana][COLOR=black]
[/COLOR][/FONT]
 
[COLOR=black][FONT=Verdana]Can someone please help with the correct syntex please.[/FONT][/COLOR]

---

