---
title: "Wifidog install problems"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by stevegarver on 2009-02-24
I am having trouble with installation of wifidog using ubuntu 8.
i get database connection problem
message:
trying to open Postgresql database connection:
warning pg_connect() : unable to connect to postgreSQL server:FATAL: password authenitication failed for user "wifidog" in
/var/www/wifidog-auth/wifidog/install.php on line 550

anyone have any ideas how i can fix the error?
i have tried installation 2 times with same results.

---

### Post by mtripcev on 2009-06-13
i have the same problem
please anyone help

regards

---

### Post by cariboo on 2009-06-13
I don't use postgresql, but it looks like there is a problem with your postgresql password.

---

### Post by mtripcev on 2009-06-13
can you tell me what you use and how to configure?
regards

---

### Post by t0mppa on 2009-06-14
You just have a user wifidog in the database that has a different (or no) password than the one that's set up in the auth server configs. I don't use Wifidog though, so I'm not sure where you'll find this info, maybe the wifidog.conf file that's mentioned in the installation docs?

If you're unexperienced with databases in general & SQL, you should install pgadmin3, which is a GUI that's fairly straight forward for the simple database administration tasks.

Anyway, if you dig up the info what the password should be, I can help you change it, but I still do think the easiest way out is actually asking the Wifidog staff for help, they have a mailing list and an IRC channel and will know instantly what to do in a case like this.

---

### Post by mthalis on 2009-06-17
when installation you have to create db user
   sudo su - postgres
   createuser wifidog --pwprompt 
here  you have to enter password , imagin you enter 123456

After you install auth server they wiil give
    username - wifidog
    pw       - wifidogtest

problem is two passwd not match change user password to "wifidogtest" instard of "123456"

---

### Post by iponeverything on 2009-06-17
All the account, tables, etc. are set up by the wifidog install install script.  It does not hurt to run it again. 

[http://yourmachine/wifidog-auth/wifidog/install.php](http://yourmachine/wifidog-auth/wifidog/install.php)

---

### Post by mthalis on 2009-06-17
I successfully install auth server and gateway and client can go internet also but problem is no logging window come to enter username or passwd please tell what is the wrong ?
if you have any tutorial regrading this can you sahre it? please

I used this tutorial to set up gateway, i did every thing they said.
[http://justuber.com/publicwifi%3Ainstallation_of_the_wifidog_captive_portal]("http://justuber.com/publicwifi%3Ainstallation_of_the_wifidog_captive_portal")


Thank you

---

### Post by iponeverything on 2009-06-18
No tutorial here, just brute force ;)

A couple of things to consider.

-  What is the physical layout? The wifidog machine needs sitting between the Internet and the LAN. If it is not, you need have the test environment in separate IP space.  ICMP redirects can cause the clients to go right around the wifidog box. 

- Start wifi dog process in foreground so that you can watch messages -- "wifidog -f" -- Take a look at the iptables rules that wifidog is putting in place, you should see the one to catch outgoing requests and redirect them to Auth server.

---

