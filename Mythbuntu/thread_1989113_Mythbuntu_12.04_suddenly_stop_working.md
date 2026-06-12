---
title: "Mythbuntu 12.04 suddenly stop working"
date: 2012-05-28
forum: Mythbuntu
---

### Post by amitshay on 2012-05-28
Hello,
I have mythbuntu for a few months now and upgraded to 12.04 as it came out.
Today after I Restarted my pc instead of mythtv frontend start i got a setup screen of the country & language and then a message that "mythtv could not connect to the database . please verify your database settings below. from reading other's threads I understand there is a problem with mysql but I dont know exactly what is it.
I am a newbie with linux.
Please Help me.

Thank you

---

### Post by nhtrader on 2012-05-29
I have also experienced this problem.

1. If you are stuck in a loop; can't get away from the Country & Language Page, press ALT+F11. Now you should see the menubar.
 Then select Applications|System|Mythbuntu Control Centre
 Now find on right side, Startup Behavior and select it.
 Disable "Automatically start MythTV Frontend"
 Now turn off computer and reboot. Then you can enter terminal mode to diagnose problem.


2. If you set the Local Backend IP address to something other than 127.0.0.1 or localhost, and your lost your network connection this can cause this problem.

3. If you made changes such as to your computer name; MythTV's database user name or password, these changes don't get propagated thoroughly. And the path of least resistance is to remove all copies of the mysql.txt on the system.

sudo find / -name "mysql.txt" -exec rm '{}' \; 

And start over...

mythtv-setup

---

### Post by amitshay on 2012-05-29
thanks for your reply.
I got error message : find:missing argument to -exec. anyway i tried to remove mysql.txt from /.myth folder in home but nothing changed.
I did not changed any of the settings before it happend.

---

### Post by anonymousdog on 2012-05-30
Assuming your BackEnd is on the same PC as your FrontEnd, you can point a browser at [http://localhost:6544](http://localhost:6544) to at least see what the backend status is.  That's a decent starting place.

---

