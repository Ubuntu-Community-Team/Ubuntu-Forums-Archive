---
title: "Lboro Uni Fileserver connection"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by Mr Tickle on 2010-10-05
Hi Ubuntu members,

I am sat here at my desk as a fresher for loughborough university typing up notes that I wish to backup on the Uni's file system. 
I have already established a connection on Windows 7 to the file server and am able to access it easily.

However, I don't enjoy using Windows (Also as a comp science student I need to try other systems) and am having trouble connecting to the server.
I believe I have narrowed down the problem but may be completely wrong, I have had a 'relatively' similar problem before but cannot rectify it the way I did then.

---Previous fix---

Last time I connected to a server I put its IP address (after 'pinging' its name from a terminal) in the "Connect to server..." in the windows share and boom it pops up - fantastic but also confusing - why not just work with the name :confused:

---Previous Fix---

I am stuck because when I try and ping the server (ping \\stud-fs\co-student-home\comg2 - is that what I am meant to be pinging)
it doesnt respond, I feel if I had its ip address I could connect - again not entirely sure. (Also its password protected if that makes a difference)

If I have made any mistakes in any of my assumptions/methods please be as stringent as possible so I can rectify my views on how these things work - I can learn from these forums as well as from my lectures :)

Thanks

Mr Tickle

---

### Post by kreggz on 2010-10-06
Try using the fully qualified domain name e.g fileserver.university.edu

if that works it means you aren't using the search function in /etc/resolv.conf 

search google.com

OR

you need to use WINS. you can do that by switching on Samba. 

Try these commands in a terminal on the fileserver

dig <name>

dig <fully qualified domain name>

dig -x <ip address>

---

### Post by Mr Tickle on 2010-10-06
Well how very strange.

I managed to get the connection by 'pinging' the file store \\stud-fs and grabbing its IP, shoving it into connect to server under windows share and having to login. 

Why didn't it do that yesterday though?  
Moreover why does the name of the file share \\stud-fs not work but its IP does when it comes to connecting? 

I tried that 'dig' command, what exactly is it designed to do -  I saw it looking for the server but that's all I could ascertain from it. (Every little bit of knowledge helps :)) 

Well thats strange but I'm in so I dont have to go to windows to back up files on the uni server = fantastic :)

Thanks for the help nonetheless kreggz :)

---

### Post by kreggz on 2010-10-06
Maybe they are using DFS?

E.g [http://www.microsoft.com/windowsserversystem/dfs/default.mspx](http://www.microsoft.com/windowsserversystem/dfs/default.mspx)

---

