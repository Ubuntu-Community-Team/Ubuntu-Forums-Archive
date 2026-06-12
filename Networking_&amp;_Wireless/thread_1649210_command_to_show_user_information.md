---
title: "command to show user information"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by jabes69 on 2010-12-19
I recently installed who watch and it was able to show me a view of user activity. Specifically I want to see which machines users are logged in too on the MOTD. Since I saw whowatch display that information I can only assume its getting that info by issuing a command from a script. I wanna know what those commands are so that I can use them in a custom MOTD script.

Here's how my network works...I have users come in through a gateway machine and they are supposed to ssh to another machine in a lab. I would like to show a list of the lab machines and who is logged in to them on the MOTD through the custom script I am creating. 

To test whowatch I logged in twice. Once using my admin account in a terminal window and then again through a second terminal I logged in as a user and ssh'd as that user to another lab machine just like users are supposed to do. Switching over to my admin window I ran whowatch and it showed me both users logged in. Then using up/down I selected the regular user and pressed enter. This showed me that the regular user was logged into the gateway and had through bash ssh'd over to a lab machine showing the name of that lab machine.

Its that last part I want to grab and display in my MOTD so additional users can see what machine are available that someone else is'nt already using.

I hope I provided enough information. I am running Ubuntu Server 10.10 and have a working knowledge of update-motd and motd. Just wondering how whowatch did it so I can replicate it in an MOTD script.

Any help is greatly appreciated.

---

