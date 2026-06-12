---
title: "MythTV wont connect to backend."
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by vonda on 2007-10-29
Hi all, as a new Linux and Ubuntu user I hope you will forgive me for any stupid questions or inept Linux knowledge I display!

I have recently installed Ubuntu 7.10 and am getting on well with it. Its the 64bit version as im running on an AMD64 platform.

When i try and run MythTV front-end i get an error saying it cant connect to the backend. The terminal displays 

2007-10-30 20:25:19.856 New DB connection, total: 2
2007-10-30 20:25:19.856 Connected to database 'mythconverg' at host: 127.0.0.1
2007-10-30 20:25:19.875 Connecting to backend server: 192.168.1.4:6543 (try 1 of 5)
2007-10-30 20:25:19.875 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.

I have edited both /home/'username'/.mythtv/mysql.txt and /etc/mythtv/mysql.txt to both point to 127.0.0.1 and alsy have the front end looking for 127.0.0.1.

Both the frontend and backend are on the same box, my ip is 192.168.1.4 which i must have set at some point.

I cant figure out where the IP address is set other than in the program but also why would it not connect on the that IP as it is my box's IP?

Anyone got any ideas?

Oh and thanks to all Ubuntu contributers for a great OS!

---

