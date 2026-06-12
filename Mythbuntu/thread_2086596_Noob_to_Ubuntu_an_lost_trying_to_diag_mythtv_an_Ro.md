---
title: "Noob to Ubuntu an lost trying to diag mythtv an Roku"
date: 2012-11-21
forum: Mythbuntu
---

### Post by johnfm3 on 2012-11-21
NOOB in need of assistance with this setup....

I have fought MythTV for a few years an never was able to set it up. I have made a new attempt an found MythBuntu which took care of all the magic of builing a dedicated mythtv box. My linux distro of choice is OpenSuSE/SLES, an have very little knowege as too how to navigate around Ubuntu as SuSE has Yast for all the administrative needs.

That being said, when trying to setup an trouble shoot the MythRoku add on, I am having troubles. Needless to say, I dont know the passwords for the mythtv account. Not even sure if that account exist. Root password seems to be set to something which is unknown (unclear if logins are just disabled). I know that there is NO apache account, unsure what account is running apache.

Some of the trouble shooting steps on the Mythroku page include making sure that the correct account has permissions on the mythroku folder.  The suggestion was to chown -R apache.apache <folder>.  When I did that, I got a respose that the account didnt exist.  Other trouble shooting steps include issues involving SQL an whether mthtv account has access via PHP to the SQL Server.  I am assuming a mythtv account exist, an assuming its password is mythtv.  Unable to verify.
 
When it comes to account, all I know is there a graphical interface which only shows my account that I am logged on with (which was created at install).
 
What does Ubuntu offer for account administration????  How do I know what system accounts I have an what accounts are disabled from log on?

I know my thread is going all over the place, using ubuntu I feel like a fish out of water.

Could really use some assistance in clearing up what I have an getting it working.


John

---

### Post by nickrout on 2012-11-21
> **johnfm3 said:**
> NOOB in need of assistance with this setup....

I have fought MythTV for a few years an never was able to set it up. I have made a new attempt an found MythBuntu which took care of all the magic of builing a dedicated mythtv box. My linux distro of choice is OpenSuSE/SLES, an have very little knowege as too how to navigate around Ubuntu as SuSE has Yast for all the administrative needs.

That being said, when trying to setup an trouble shoot the MythRoku add on, I am having troubles. Needless to say, I dont know the passwords for the mythtv account. Not even sure if that account exist. Root password seems to be set to something which is unknown (unclear if logins are just disabled). I know that there is NO apache account, unsure what account is running apache.

Some of the trouble shooting steps on the Mythroku page include making sure that the correct account has permissions on the mythroku folder.  The suggestion was to chown -R apache.apache <folder>.  When I did that, I got a respose that the account didnt exist.  Other trouble shooting steps include issues involving SQL an whether mthtv account has access via PHP to the SQL Server.  I am assuming a mythtv account exist, an assuming its password is mythtv.  Unable to verify.
 
When it comes to account, all I know is there a graphical interface which only shows my account that I am logged on with (which was created at install).
 
What does Ubuntu offer for account administration????  How do I know what system accounts I have an what accounts are disabled from log on?

I know my thread is going all over the place, using ubuntu I feel like a fish out of water.

Could really use some assistance in clearing up what I have an getting it working.


John
user accounts are listed in /etc/passwd and group ownership in /etc/group. 

There is a user settings in the admin menu.

apache appears to run as user www-data on my backend,  which I discovered by the simple expedient of ```
ps aux|grep apache
```.

The mythtv user is created by the ubuntu mythtv packages, so it will be there. The mythtv user's database password is found in ~mythtv/.mythtv/mysql.txt and should be in the same place for the user you created on mythbuntu installation.

Do you have mythtv up and running? Do that first.

---

### Post by johnfm3 on 2012-11-21
> **nickrout said:**
> user accounts are listed in /etc/passwd and group ownership in /etc/group. 
 
There is a user settings in the admin menu.
 
apache appears to run as user www-data on my backend, which I discovered by the simple expedient of ```
ps aux|grep apache
```.
 
The mythtv user's database password is found in ~mythtv/.mythtv/mysql.txt 
 
Do you have mythtv up and running? Do that first.
 
MythTV came up with no issues after install an completing mythtv-setup.  Currently the machine is built as a Pri Backend/Frontend machine.  An the front end can see an play the 4 movies I copied via smb share.
 
Please explain where I find the admin menu.
 
ps auk | grep apache????  Can you please explain what ps auk does?  I have used grep an understand grep comfortably.
 
Assuming shadow is where the users are located.
mysql:!:15570:0:99999:7:::
Does the ! in the second field mean the account login is disabled?  Root has a ! as well.  Does that mean root login is disabled?
 
Much thanks for your reply.  Ubuntu is forcing me to learn more linux admin skills.
 
John

---

### Post by johnfm3 on 2012-11-21
Ok, so I found the following in a mysql.txt file in my home dir
 
DBUserName=mythtv
DBPassword=uq5HVM2m
DBName=mythconverg
DBType=QMYSQL

So does this mean the mythtv user password for the system is "uq5HVM2m"?  Or is that the password for mythtv to access SQL?  Does SQL use the system user credientials?
 
John

---

### Post by nickrout on 2012-11-21
> **johnfm3 said:**
> MythTV came up with no issues after install an completing mythtv-setup.  Currently the machine is built as a Pri Backend/Frontend machine.  An the front end can see an play the 4 movies I copied via smb share.
 
Please explain where I find the admin menu.exit out of mythtv frontend and there are menus at the top left of the desktop. There is also an accessories menu that contains terminal, where you can type commands.> 
 
ps auk | grep apache????  Can you please explain what ps auk does?  I have used grep an understand grep comfortably. its ps aux not ps auk, but in brief:

ps shows the running processes
aux are options - they mean show all processes (a) and their users (u) and I can't recall exactly what x does. 
| pipes the output to the next command which is grep. 
grep searches through the output of the first command (ps aux) and looks for the string apache. So you get a list of apache processes and the users who are running them, viz:

```
nick@media:~$ ps aux|grep apache
root      2194  0.0  0.0  67100   848 ?        Ss   Nov16   0:17 /usr/sbin/apache2 -k start
www-data 14961  0.0  0.0  68352   716 ?        S    Nov18   0:00 /usr/sbin/apache2 -k start
www-data 14962  0.0  0.0  67476   540 ?        S    Nov18   0:00 /usr/sbin/apache2 -k start
www-data 14963  0.0  0.0  67100   480 ?        S    Nov18   0:00 /usr/sbin/apache2 -k start
www-data 14964  0.0  0.0  67100   476 ?        S    Nov18   0:00 /usr/sbin/apache2 -k start
www-data 14965  0.0  0.0  67100   472 ?        S    Nov18   0:00 /usr/sbin/apache2 -k start
nick     15070  0.0  0.0   6952   764 pts/4    S+   Nov18   0:00 mc /etc/apache2/sites-available/
www-data 15157  0.0  0.0  67100   472 ?        S    Nov18   0:00 /usr/sbin/apache2 -k start
nick     22134  0.0  0.0   3324   888 pts/11   S+   11:21   0:00 grep --color=auto apache
www-data 30379  0.0  0.0  68384   664 ?        S    Nov18   0:00 /usr/sbin/apache2 -k start
www-data 30380  0.0  0.0  70952   732 ?        S    Nov18   0:00 /usr/sbin/apache2 -k start
www-data 30382  0.0  0.0  67868   712 ?        S    Nov18   0:00 /usr/sbin/apache2 -k start
www-data 30383  0.0  0.0  67628   532 ?        S    Nov18   0:00 /usr/sbin/apache2 -k start

```> 
 
Assuming shadow is where the users are located.
mysql:!:15570:0:99999:7:::I told you where account details were located, namely /etc/passwd> 
Does the ! in the second field mean the account login is disabled?  Root has a ! as well.  Does that mean root login is disabled?root login is disallowed in ubuntu and it's derivatives. I doubt that login as user mysql is allowed either, why would you want to? In fact a check shows that it's shell is /bin/false, so no logins allowed.```
nick@media:~$ grep mysql /etc/passwd
mysql:x:102:105:MySQL Server,,,:/var/lib/mysql:/bin/false
```

If you want to do something as root in ubuntu use sudo, eg ```
sudo service mysql start
```
 > 
Much thanks for your reply.  Ubuntu is forcing me to learn more linux admin skills.
 
John

---

### Post by nickrout on 2012-11-21
> **johnfm3 said:**
> Ok, so I found the following in a mysql.txt file in my home dir
 
DBUserName=mythtv
DBPassword=uq5HVM2m
DBName=mythconverg
DBType=QMYSQL

So does this mean the mythtv user password for the system is "uq5HVM2m"?  Or is that the password for mythtv to access SQL?  Does SQL use the system user credientials?
 
JohnMySQL uses it's own internal authentication mechanism. uq5HVM2m the password for the mythtv user to log into the mythconverg database in MySQL. It is higghly likely that what mythroku wants is the username mythtv and the password uq5HVM2m. However I am not familiar with mythroku and cannot find the instruction page on the web to see what exactly they want. Perhaps you could point me to it so I can assist further (I admit I haven't looked particularly hard).

The other problem you may face is that both mysql and mythtv-backend need to be listening on your network address, not localhost. If you give us the output of ```
sudo netstat -tanp|grep 3306 
```it will tell you if mysql is listening on 127.0.0.1 or 0.0.0.0. Similarly ```
sudo netstat -tanp|6543|grep LISTEN
``` will give you an idea what addresses mythbackend is listening on.

Hope that all helps.

---

### Post by johnfm3 on 2012-11-21
While I am getting ready to run your code request an re read your post, I am providing you the link to the MythRokuPlayer

[https://github.com/zane131/MythRokuPlayer/tree/dev](https://github.com/zane131/MythRokuPlayer/tree/dev)

There is a readme which I am following.  I also have threads on roku forums trying to piece this all together.

Thanks,
John

---

### Post by johnfm3 on 2012-11-21
jmoore@mythtv:/usr/share/mythtv/mythweb/mythroku$ sudo netstat -tanp|grep 3306
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      813/mysqld      


jmoore@mythtv:/usr/share/mythtv/mythweb/mythroku$ sudo netstat -tanp|grep 6543|grep LISTEN
tcp        0      0 127.0.0.1:6543          0.0.0.0:*               LISTEN      2702/mythbackend



I understand the reason for using sudo, even though I break that rule all the time when I use su an provide the root password.  It more about understanding how this system works.  It looks as if when the ! is in the shadow file, the account is disabled.  An I also see that mythtv account is not disabled.

So after I got home, I rebuilt the system completely fresh mythbuntu install.  Moved 2 movies over an tested from the front end that MythTV is working the way its suppose too.  Now I am just fighting Mythroku.

John

---

### Post by nickrout on 2012-11-21
From looking at the mythroku stuf it appears that it diesn't need database access anyway, as it seems to interact with mythweb.

I am not sure that I could be bothered with a roku if it means transcoding everything to h.264 in an mp4 container.

---

### Post by nickrout on 2012-11-21
However Roku does perhaps seem well placed to be a client for the new (in 0.25) HTTP Live Streaming API in mythtv.

[http://sdkdocs.roku.com/display/RokuSDKv43/Encoding+Guide#EncodingGuide-40HLSHTTPLiveStreaming](http://sdkdocs.roku.com/display/RokuSDKv43/Encoding+Guide#EncodingGuide-40HLSHTTPLiveStreaming)

---

### Post by johnfm3 on 2012-11-21
I have 5 kids an a large movie collection.  The roku is something I dont mind them touching.  An if they act up, I can simply stop network traffic or a service while at work an there is no more tv (since cable isnt hooked up).

My long term goal is for the kids to be able to watch live tv thru Roku.

John

---

### Post by johnfm3 on 2012-11-21
So I am 1 step closer.  I can now browse files thru the Roku, each file is a white block with now image.  An my apache2 error.log is saying the following...

[Wed Nov 21 18:22:06 2012] [error] [client 192.168.2.8] Directory index forbidden by Options directive: /var/www/mythweb/data/recordings/
[Wed Nov 21 18:22:06 2012] [error] [client 192.168.2.21] PHP Warning:  getimagesize([http://192.168.2.8/mythweb/data/recordings/):]("http://192.168.2.8/mythweb/data/recordings/%29:") failed to open stream: HTTP request failed! HTTP/1.1 403 Forbidden\r\n in /usr/share/mythtv/mythweb/mythroku/resizeimage.php on line 10
[Wed Nov 21 18:22:06 2012] [error] [client 192.168.2.21] PHP Fatal error:  Call to undefined function imagesx() in /usr/share/mythtv/mythweb/mythroku/resizeimage.php on line 60
[Wed Nov 21 18:22:06 2012] [error] [client 192.168.2.8] Directory index forbidden by Options directive: /var/www/mythweb/data/video_covers/
[Wed Nov 21 18:22:06 2012] [error] [client 192.168.2.21] PHP Warning:  getimagesize([http://192.168.2.8/mythweb/data/video_covers/):]("http://192.168.2.8/mythweb/data/video_covers/%29:") failed to open stream: HTTP request failed! HTTP/1.1 403 Forbidden\r\n in /usr/share/mythtv/mythweb/mythroku/resizeimage.php on line 10
[Wed Nov 21 18:22:06 2012] [error] [client 192.168.2.8] File does not exist: /var/www/mythweb/data/video_screenshots
[Wed Nov 21 18:22:06 2012] [error] [client 192.168.2.21] PHP Warning:  getimagesize([http://192.168.2.8/mythweb/data/video_screenshots/):]("http://192.168.2.8/mythweb/data/video_screenshots/%29:") failed to open stream: HTTP request failed! HTTP/1.1 404 Not Found\r\n in /usr/share/mythtv/mythweb/mythroku/resizeimage.php on line 10

Looking at permissions now.  Looks like the /var/www location shown above is a symlink to /usr/share/mythtv/<subfolder>.  An the permissions are different.  The permissions for the symlinks are root.root with 777, an the real destination folders are mythtv.mythtv all with I think 600.

John

---

### Post by nickrout on 2012-11-21
I have no idea what all that means, nor how roku works. Woever may I suggest if you can put a URL into Roku, you try [http://backendaddress:6544](http://backendaddress:6544) and get to API then examples then http live streaming.

If that doesn't work straight off then join the mailing list mythtv-users. Chris Pinkham wrote the http live streaming code and from my research has used it with his Roku and will be able to give some tips.

---

### Post by johnfm3 on 2012-11-22
> **nickrout said:**
> I have no idea what all that means, nor how roku works. Woever may I suggest if you can put a URL into Roku, you try [http://backendaddress:6544](http://backendaddress:6544) and get to API then examples then http live streaming.

If that doesn't work straight off then join the mailing list mythtv-users. Chris Pinkham wrote the http live streaming code and from my research has used it with his Roku and will be able to give some tips.

The way I understand the mythruku code, it interacts via PHP thru the Mythweb interface.  The dev's wrote a test php which is too be used from a browser to test against the backend in the same manor the roku would.  The errors I showed were my attempts to test with a web browser.

Should that address be browsable???  I tried via firefox an had no connection.  Looking at my nmap output, I dont see any port higher 3306.

BTW:  Thanks for your assistance.  An really thanks for the crash course on linux administration with out GUI.

John

---

