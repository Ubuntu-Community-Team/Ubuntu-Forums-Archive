---
title: "Connection with backend lost?"
date: 2009-09-19
forum: Mythbuntu
---

### Post by jccubs on 2009-09-19
The update manager came on the screen and I followed the instructions and installed all updates. This required a restart. I restarted the computer and that typically takes me to the "Watch TV" screen. I normally cannot watch tv unless I do the following: 1. Esc out of that menu (it asks if I really want to quit and I say yes). Then I go into System, Back end setup. I Esc out of that menu, then am asked to run mythfill database and I run that. Then I go to Multi-Media and start the front end. This enables the "Watch TV" function and there are no problems. Last night when I followed these stemp I got the message that connection with the back end has been lost. I could not watch tv and it said that there were no recordings to watch either. I restarted again and when I got to the "Watch TV" screen I tried to watch my recordings (without the steps mentioned above). My recordings were there and there was no problem watching them. I was still unable to watch tv. So I followed the steps above, but with the same result - connection with backend was lost. I'm only using one computer that is a combination frontend/backend machine. Very frustrated at this time. I'm at work right now and cannot try any suggestions that might be posted for a few hours. Thanks in advance for any help.

---

### Post by bsntech on 2009-09-20
You might check to ensure that your MySQL server is started.

I noticed that when I changed the IP address of mine, the MySQL server wouldn't start up by itself on startup any longer.  After I changed it back to localhost (127.0.0.1), it started up normally again.

That is what it sounds like is the issue to me - something with your database server not starting up when your computer does.

---

### Post by williammanda on 2009-09-20
> **jccubs said:**
> The update manager came on the screen and I followed the instructions and installed all updates. This required a restart. I restarted the computer and that typically takes me to the "Watch TV" screen. I normally cannot watch tv unless I do the following: 1. Esc out of that menu (it asks if I really want to quit and I say yes). Then I go into System, Back end setup. I Esc out of that menu, then am asked to run mythfill database and I run that. Then I go to Multi-Media and start the front end. This enables the "Watch TV" function and there are no problems. Last night when I followed these stemp I got the message that connection with the back end has been lost. I could not watch tv and it said that there were no recordings to watch either. I restarted again and when I got to the "Watch TV" screen I tried to watch my recordings (without the steps mentioned above). My recordings were there and there was no problem watching them. I was still unable to watch tv. So I followed the steps above, but with the same result - connection with backend was lost. I'm only using one computer that is a combination frontend/backend machine. Very frustrated at this time. I'm at work right now and cannot try any suggestions that might be posted for a few hours. Thanks in advance for any help.

Are you on a network? If so is the ip address of the master backend static? Also post your backend log located at /var/log/mythtv/mythbackend.log.

---

### Post by jccubs on 2009-09-20
I have a modem and router that I use to get my connections, but other than that I don't use this computer on a true network.  I was trying to correct this problem and made a huge mistake (I described it in a separate post).  I was going through the menu's in the backend setup and noticed that the password for mysql was not the same as my password that I selected.  Thinking this was the problem I retyped my password in.  HUGE mistake as now I cannot do anything.  If I even try to run mythfilldatabase I get errors and the screen turns blue and I m asked to select my language.  Then it goes to the page with No UPnP backends found.  The only option is OK.  The next screen is Database configuration 1/2 with the user and password there to enter.  But because I was an idiot and didn't even write down the password, I'm stuck pulling out my hair.  I can't even give you the log you asked for.  I'm relatively new to this if it wasn't too obvious.  so what do you suggest now?

---

### Post by bsntech on 2009-09-20
Hi jccubs - 

MythTV stores your username/password in the /etc/mythtv/mysql.txt file.  You might check to see if it is still in there and give that a shot in myth-backend.

Here are some other instructions to change the mythuser password using the terminal-line MySQL client by logging into root:

The problem you describe sounds like either Mythtv-backend cannot find a MySQL server - at least that is when I had a problem with my install.

You may also look here for additional help.  You might need to reconfigure the mythtv-database or mythtv-common as well.

[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting]("https://help.ubuntu.com/community/MythTV/Install/Troubleshooting")

---

### Post by jccubs on 2009-09-20
OK, I've been a windows user my whole life - trying to pick up on these things.  Do I just open a terminal and type what you listed, or do I somehow have to navigate to a location and just look at the file?  I pretty much only use this for the TV, not any other computing, so just not that familiar with it - and a bit overwhelmed.

---

### Post by bsntech on 2009-09-21
Yes, you should just open up a terminal and type in those commands.

---

### Post by jccubs on 2009-09-21
I tried typing it in and got the following No such file or directory.  Then I typed it in beginning with sudo, and  got password for jc:  i typed in the password and got command not found.  I'm going to re-install - I can't do this much more - thank you everyone for your help!

---

