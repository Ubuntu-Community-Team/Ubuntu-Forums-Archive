---
title: "Mythweb not working"
date: 2013-10-06
forum: Mythbuntu
---

### Post by philayre on 2013-10-06
afternoon, for the life of me I cannot get mythweb to work.  I can get to the main 'homepage' but every link there just comes up with a '404 - Not Found 'The requested URL /mythweb/mythweb.php/tv/list was not found on this server.'' error

what am I doing wrong?

I'm new to web servers, normally they just work! :)

please let me know any additional info I can provide

Phil

---

### Post by harold95 on 2013-10-06
just a thought.....is the mythbackend running?

---

### Post by philayre on 2013-10-07
yes, the backend is definitely running.

my backend is installed on ubuntu 12.04.3 server, I used VNC to configure mythtv, i'm using mythtv 0.27

i have two apachie websites, one for phpvirtualbox (which works perfectly) and one for mythtv, where all the links from the homepage are dead.

Thanks for any help.

---

### Post by philayre on 2013-10-08
no thoughts?

anybody?

---

### Post by philayre on 2013-11-13
I'm still having this issue here.  

any pointers?

---

### Post by tgm4883 on 2013-11-13
> **philayre said:**
> I'm still having this issue here.  

any pointers?

I'm not at home to verify, but I'm pretty sure the link /mythweb/mythweb.php/tv/list shouldn't have mythweb.php in the middle of it. Try removing that and seeing if the link works.

---

### Post by philayre on 2013-11-13
hmm.

the error states "The requested URL /mythweb/mythweb.php/tv/list was not found on this server."

however the actual address is [http://192.168.x.x/mythweb/tv/list](http://192.168.x.x/mythweb/tv/list)

I do have a file on the server: /var/www/mythweb/mythweb.php but I cannot understand what it is doing.

one of the file-paths in that file exists:  /usr/share/mythtv/bindings/php/ (with a lot more myth .php files within it)
the other does not exist: '/usr/local/share/mythtv/bindings/php/ ('/usr/local/share/' does exist though)

I'm a bit miffed as to where the files mythweb is looking should be, and where they actually are - if they exist...

Thanks

---

### Post by philayre on 2013-11-13
I have lines like this in /var/log/apache2:

[Wed Nov 13 17:18:32 2013] [error] [client 192.168.x.x] File does not exist: /var/www/mythweb/mythweb.php/tv/recorded, referer: [http://192.168.x.x/mythweb/](http://192.168.x.x/mythweb/)

---

### Post by tgm4883 on 2013-11-14
What release of MythTV and Mythbuntu are you on? How did you install Mythweb? Do you have any other web sites on the machine?

---

### Post by philayre on 2013-11-15
> **philayre said:**
> yes, the backend is definitely running.

my backend is installed on ubuntu 12.04.3 server, I used VNC to configure mythtv, i'm using mythtv 0.27

i have two apachie websites, one for phpvirtualbox (which works perfectly) and one for mythtv, where all the links from the homepage are dead.

Thanks for any help.

as above.  cheers

---

### Post by philayre on 2013-11-15
oh, and i have installed mythweb several times, with sudo apt-get install mythweb and synaptic, and through mythbuntu-control-centre

the backend machine with mythweb installed is running ubuntu 12.04 server edition

other websites are: webmin, and phpVirtualBox

the website itself looks fine, its just anything beyond 192.168.x.x/mythweb that is broken

is it maybe worthwhile uninstalling everything and trying out an older  version of mythweb like 0.25 to see if that works?  I'm just starting  out so i don't stand to loose much.  I just thought it best to go with  the most recent version...

---

### Post by philayre on 2013-11-15
rpt post

---

### Post by philayre on 2013-11-22
still stuck.

is there anywhere better I could be posting?

Thanks

---

### Post by azmyth on 2013-11-22
Look in the /etc/apache2/sites-enabled/mythweb.conf

What does the first uncommented line say <Directory "/some/thing">

---

### Post by philayre on 2013-11-22
Hi azmyth

its <Directory "/var/www/mythweb/data">

---

### Post by azmyth on 2013-11-23
I think you need to change that to /var/www/mythweb/ and then do a sudo service restart apache2 then goto [http://your.ip/mythweb](http://your.ip/mythweb) it should work then.

---

### Post by philayre on 2013-11-23
Hmm.

I tried your suggestion and nothing changed.  Originally I followed the guide here: [https://github.com/MythTV/mythweb/blob/master/INSTALL](https://github.com/MythTV/mythweb/blob/master/INSTALL) the option you suggest is covered from line 239.

my /etc/apache2/sites-enabled/mythweb.conf file looks like this:

# CHANGE THESE PATHS TO MATCH YOUR MYTHWEB INSTALLATION DIRECTORY!  e.g.
#
#    /var/www
#    /home/www/htdocs
#    /var/www/mythweb/mythweb
#    /srv/www/htdocs/mythweb
#
    <Directory "/var/www/mythweb/data">
        Options -All +FollowSymLinks +IncludesNoExec
    </Directory>
    <Directory "/var/www/mythweb" >
    
ls /var/www/mythweb/data shows:
phil@hostserver:~$ ls /var/www/mythweb/data
cache  music  recordings  tv_icons  video  video_covers

ls /var/www/mythweb shows:
phil@hostserver:~$ ls /var/www/mythweb
classes        data      js       mythweb.conf.apache    mythweb.php  skins
configuration  includes  modules  mythweb.conf.lighttpd  mythweb.pl   tests


I really am stumped!

---

### Post by khPWXxF on 2013-11-23
There is a tick box in mythtv setup.  Is that tick necessary the way you have set up your web or is a simple frontend to it?
Phil

---

### Post by philayre on 2013-11-24
I'm sorry I don't understand your post.  I have flicked through the 'general' setup in the backend and can't see anything obviously concerned with mythweb.

i have a dedicated backend / server running mythweb, i am connecting to this from another machine on my network.

---

### Post by azmyth on 2013-11-24
[I]<Directory "/var/www/mythweb/data">
Options -All +FollowSymLinks +IncludesNoExec
</Directory>[/I]
<Directory "/var/www/mythweb" >

What I put in italics doesn't seem correct to me as I don't have any of this nor do I see this in the instructions. I would remove it.

---

### Post by philayre on 2013-11-25
Thats the first three lines in italics?

I'll comment it out, restart apachie and get back to you.

---

### Post by philayre on 2013-11-25
No change in behavior.  Apache2 crashed on restart when I commented everything out though.

what I find odd is that the homepage is fine, its just every link from here that's broken.

all the rest of the options etc. in my .conf file are just as they were when I opened it the first time.

---

### Post by philayre on 2013-11-29
any more ideas?

even a stab in the dark?

---

### Post by azmyth on 2013-11-29
You have the apache rewrite mod enabled? You should see a link in /etc/apache2/mods-enabled that says rewrite.load.

---

### Post by philayre on 2013-11-30
looks like it:

phil@hostserver:/etc/apache2/mods-enabled$ ls -al
total 8
drwxr-xr-x 2 root root 4096 Nov 13 10:42 .
drwxr-xr-x 7 root root 4096 Jul 16 06:48 ..
lrwxrwxrwx 1 root root   28 Mar 15  2013 alias.conf -> ../mods-available/alias.conf
lrwxrwxrwx 1 root root   28 Mar 15  2013 alias.load -> ../mods-available/alias.load
lrwxrwxrwx 1 root root   33 Mar 15  2013 auth_basic.load -> ../mods-available/auth_basic.load
lrwxrwxrwx 1 root root   34 Nov 13 10:42 auth_digest.load -> ../mods-available/auth_digest.load
lrwxrwxrwx 1 root root   33 Mar 15  2013 authn_file.load -> ../mods-available/authn_file.load
lrwxrwxrwx 1 root root   36 Mar 15  2013 authz_default.load -> ../mods-available/authz_default.load
lrwxrwxrwx 1 root root   38 Mar 15  2013 authz_groupfile.load -> ../mods-available/authz_groupfile.load
lrwxrwxrwx 1 root root   33 Mar 15  2013 authz_host.load -> ../mods-available/authz_host.load
lrwxrwxrwx 1 root root   33 Mar 15  2013 authz_user.load -> ../mods-available/authz_user.load
lrwxrwxrwx 1 root root   32 Mar 15  2013 autoindex.conf -> ../mods-available/autoindex.conf
lrwxrwxrwx 1 root root   32 Mar 15  2013 autoindex.load -> ../mods-available/autoindex.load
lrwxrwxrwx 1 root root   26 Mar 15  2013 cgi.load -> ../mods-available/cgi.load
lrwxrwxrwx 1 root root   30 Mar 15  2013 deflate.conf -> ../mods-available/deflate.conf
lrwxrwxrwx 1 root root   30 Mar 15  2013 deflate.load -> ../mods-available/deflate.load
lrwxrwxrwx 1 root root   26 Mar 15  2013 dir.conf -> ../mods-available/dir.conf
lrwxrwxrwx 1 root root   26 Mar 15  2013 dir.load -> ../mods-available/dir.load
lrwxrwxrwx 1 root root   26 Mar 15  2013 env.load -> ../mods-available/env.load
lrwxrwxrwx 1 root root   30 Nov 13 10:41 headers.load -> ../mods-available/headers.load
lrwxrwxrwx 1 root root   27 Mar 15  2013 mime.conf -> ../mods-available/mime.conf
lrwxrwxrwx 1 root root   27 Mar 15  2013 mime.load -> ../mods-available/mime.load
lrwxrwxrwx 1 root root   34 Mar 15  2013 negotiation.conf -> ../mods-available/negotiation.conf
lrwxrwxrwx 1 root root   34 Mar 15  2013 negotiation.load -> ../mods-available/negotiation.load
lrwxrwxrwx 1 root root   33 Mar 18  2013 php5filter.conf -> ../mods-available/php5filter.conf
lrwxrwxrwx 1 root root   33 Mar 18  2013 php5filter.load -> ../mods-available/php5filter.load
lrwxrwxrwx 1 root root   33 Mar 15  2013 reqtimeout.conf -> ../mods-available/reqtimeout.conf
lrwxrwxrwx 1 root root   33 Mar 15  2013 reqtimeout.load -> ../mods-available/reqtimeout.load
lrwxrwxrwx 1 root root   30 Nov 13 10:19 rewrite.load -> ../mods-available/rewrite.load
lrwxrwxrwx 1 root root   31 Mar 15  2013 setenvif.conf -> ../mods-available/setenvif.conf
lrwxrwxrwx 1 root root   31 Mar 15  2013 setenvif.load -> ../mods-available/setenvif.load
lrwxrwxrwx 1 root root   29 Mar 15  2013 status.conf -> ../mods-available/status.conf
lrwxrwxrwx 1 root root   29 Mar 15  2013 status.load -> ../mods-available/status.load

---

### Post by azmyth on 2013-12-01
Do you have an .htaccess file in /var/www that is causing issues? Also, I assume you edited the mythweb.conf and added your db info.

---

### Post by philayre on 2013-12-01
Hi azmyth, thanks again for your help.  The contents of my /var/www folder is:

phil@hostserver:~$ ls -al /var/www
total 16
drwxr-xr-x  3 root root 4096 Nov 13 17:08 .
drwxr-xr-x 14 root root 4096 Dec  1 15:09 ..
-rw-r--r--  1 root root  177 Mar 15  2013 index.html
lrwxrwxrwx  1 root root   25 Nov 13 01:15 mythweb -> /usr/share/mythtv/mythweb
drwxr-xr-x  9 root root 4096 Mar 15  2013 phpvirtualbox


I just noticed I have a config file in:
/var/www/mythweb/mythweb.conf.apache (which is unchanged)

and also a config file here:
/etc/apache2/sites-enabled/mythweb.conf (this is the one I have modified for my db etc.)

does that seem right? I will update the /var/www/mythweb/mythweb.conf.apache file with my information and see what happens

---

### Post by philayre on 2013-12-01
no change.  again. !

why is the mythweb.php seen in the url displayed in the error?

**Not Found**

 The requested URL /mythweb/mythweb.php/tv/list was not found on this server.
 [HR][/HR] Apache/2.2.22 (Ubuntu) Server at xxx.xxx.xxx.xxx Port 80

---

### Post by azmyth on 2013-12-01
This is the correct one to edit /etc/apache2/sites-enabled/mythweb.conf. 

I know that I changed my mythweb directory and all the files in the directory and sub-directories to my apache user which is www-data on Ubuntu. Not sure if this will help you.

---

### Post by philayre on 2013-12-02
unfortunately changing the user to www-data (keeping the group as root) didn't help either.

are there any other forums I can try?

Thanks - again! :)

---

### Post by azmyth on 2013-12-02
Could try the mythtv-users list server or IRC.

---

