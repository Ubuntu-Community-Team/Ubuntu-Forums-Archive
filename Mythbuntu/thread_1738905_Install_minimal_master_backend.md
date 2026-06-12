---
title: "Install minimal master backend"
date: 2011-04-25
forum: Mythbuntu
---

### Post by natomb on 2011-04-25
Hello,

I have the following situation:

an Ubuntu server (actually, a virtual machine) running 24x7 to provide file services etc.

a PC in the living room.

I want to use the Ubuntu server as Myth master backend, but _without_:

[LIST]
[*]video cards
[*]mysql server (is running in another virtual machine for other purposes)
[/LIST]
The PC in the living room would host the video cards (2x DVB-S) and thus would be a secondary backend and the frontend.


Could you please advice me how to install the mythbuntu with just a master backend role (no mysql server, no graphical frontend [ssh is fine], etc.)? What package I have to select in apt?


Kindest regards
  Bjoern

---

### Post by superm1 on 2011-04-25
> **natomb said:**
> Hello,

I have the following situation:

an Ubuntu server (actually, a virtual machine) running 24x7 to provide file services etc.

a PC in the living room.

I want to use the Ubuntu server as Myth master backend, but _without_:

[LIST]
[*]video cards
[*]mysql server (is running in another virtual machine for other purposes)
[/LIST]
The PC in the living room would host the video cards (2x DVB-S) and thus would be a secondary backend and the frontend.


Could you please advice me how to install the mythbuntu with just a master backend role (no mysql server, no graphical frontend [ssh is fine], etc.)? What package I have to select in apt?


Kindest regards
  Bjoern

Install using the "slave" backend role, and then create your mysql database in the other VM. 

You can turn off the gdm upstart job if you won't ever need to use graphics.

---

### Post by natomb on 2011-04-26
Hi,


thank you for the quick response. I tried to setup but failed in the following cases:

running mythfilldatabase will try to connect to the master backend, which fails.
In the mythbuntu control center I cannot test the connection to the master backend (register "MySQL configuration", Test connection button).


Could you please advice me where to install / configure what? Currently, I have the following setup:

Host: mysql
Role: provider of mysql Server

Host: myth-backend
Role: (primary?) backend for mythtv

Host: living-room
Role: frontend and secondary backend (here the TV tuners are built in)

Host (in 2012 / 2013): myth-recorder
Role: secondary backend (here, all TV tuners will move into, as soon as my kids demand their own TV set :) )


Thank you very much
  Bjoern

---

