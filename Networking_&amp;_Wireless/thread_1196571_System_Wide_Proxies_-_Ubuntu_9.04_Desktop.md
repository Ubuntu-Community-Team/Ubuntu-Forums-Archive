---
title: "System Wide Proxies - Ubuntu 9.04 Desktop"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by fl@ke$ on 2009-06-25
[COLOR=black][FONT=Verdana]Hi all.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I have been doing some research into how system wide proxies are configured on Ubuntu.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I have managed to achieve this task by going into the menu System -> Preferences -> Network Proxies.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I fill in all the information and all is well, so it seems. I know my proxy server requires authentication, so I enter this information as well.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Now, my problem arises when I run a simple command at the terminal:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]export[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Disturbingly, I find in a system variable, my username and password to the proxy server. Even worse IN PLAIN TEXT!![/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Now, as a student studying for a Diploma of IT, I realise that having usernames and passwords being stored in plain text is asking for trouble however my knowledge of Linux is limited.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]There are a couple of things I need to know, as these computers will be in use by technical minded folk.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[LIST]
[*][FONT=Verdana]What are the implications of this, bearing in mind that these computers are networked, and will have internet access. I mean, if this machine and others like it are compromised, will they be able to get this clearly readable information? Furthermore, if so, how?[/FONT]
[/LIST]
[LIST]
[*][FONT=Verdana]Is there another way of configuring the proxy information for the network card that does not store the usernames and passwords in plain text either in a file or RAM?[/FONT]
[/LIST][COLOR=black][FONT=Verdana]I need to have a proxy configuration included in the network card configuration because I cannot remove the proxy on the network. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thanks.[/FONT][/COLOR]

---

### Post by fl@ke$ on 2009-07-05
I could settle for all applications to ask for authentication to the proxy server, rather than relying on just one user name and password stored somewhere.

Any Ideas ?

Thanks

---

