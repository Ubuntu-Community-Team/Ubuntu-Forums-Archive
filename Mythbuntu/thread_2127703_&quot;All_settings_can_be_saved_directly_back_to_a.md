---
title: "&quot;All settings can be saved directly back to a flash drive for easy portabilit&quot;?"
date: 2013-03-20
forum: Mythbuntu
---

### Post by gga96 on 2013-03-20
[FONT=Verdana][COLOR=#222222][FONT=Verdana][COLOR=#222222]The Title quote = [/COLOR][/FONT][[FONT=Verdana]http://www.mythbuntu.org/[/FONT]]("http://www.mythbuntu.org/")[FONT=Verdana][COLOR=#222222] front page, para 4 "Live Frontend".

The full context of the quote is:
"Live Frontend
A Mythbuntu CD can also be used as a live frontend. This is great if you want to 
turn a laptop or desktop into a quick frontend or quickly test hardware 
compatibility. The live frontend provides a GUI to mount network shares, 
configure a remote, hostname, location of your master backend and a place to 
save settings. All settings can be saved directly back to a flash drive for easy 
portability."

[/COLOR][/FONT][FONT=Verdana][COLOR=#222222]I realize it refers to a live frontend but ...
[/COLOR][/FONT][FONT=Verdana][COLOR=#222222]I have already installed and configured the back & front ends on my PC and all work well.
I now want to propagate the installed front end configuration to network stand alone front end 
installations on Asrock ion2 3d units.

I thought a frontend .conf file might exist for the current frontend installation, but I cannot find such a beast.

[B]How do I save the frontend config data to a file or flash drive so I can use it to configure the next to be installed network frontend as per the MythBuntu installation disk.?
[/B]
[/COLOR][/FONT][FONT=Verdana][COLOR=#222222]Some minor edits my be required but the look and feel of all frontends 

[FONT=Arial][SIZE=2][COLOR=#000000]Any ideas will be appreciated.[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=#000000]
Glen[/COLOR][/SIZE][/FONT] 
[/COLOR]
[/FONT]

[/COLOR][/FONT]

---

### Post by tgm4883 on 2013-03-21
It's talking about the config.xml file (~/.mythtv/config.xml). All mythtv settings are kept in the database, so that config.xml file will have the information to connect to the database. In previous versions it was mysql.txt, but 0.26 no longer users mysql.txt

---

### Post by gga96 on 2013-03-21
Thank you tmg4883 for your reply.

I still have the need to propagate the installed front end configuration to other network stand alone frontends to maintain a consistent look and feel.

Clearly the data needs to be extracted from the database.

Can you sugest a script that does the job or is almost applicable but can be edited to do the job?

Thank you
Glen

---

