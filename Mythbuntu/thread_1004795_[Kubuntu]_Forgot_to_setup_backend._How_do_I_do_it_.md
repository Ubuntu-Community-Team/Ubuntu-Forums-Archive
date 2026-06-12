---
title: "[Kubuntu] Forgot to setup backend. How do I do it again?"
date: 2008-12-07
forum: Mythbuntu
---

### Post by hung0702 on 2008-12-07
I downloaded Mythtv via Adept, didn't know what I was doing, and ended up not setting up the backend (at least, that's what I THINK happened). It asked me to log out and do this stuff. I declined and didn't log out. Yes, I'm dumb. I can't setup the frontend because there is not backend. I tried uninstalling and redownloading Mythtv from Adept to see if it would bring me back to that page. It didn't. How do I configure the backend now?

More info:
TV card: MSI TV@nywhere Plus
Backend/frontend/Desktop.

---

### Post by squaregoldfish on 2008-12-07
Hi,

Running mythtv-setup will help you perform all the initial setup stuff.

If you need any help doing it, try this [tutorial]("http://parker1.co.uk/mythtv_ubuntu.php").

Steve.

---

### Post by hung0702 on 2008-12-08
> **hung0702 said:**
> [SIZE="1"]I downloaded Mythtv via Adept, didn't know what I was doing, and ended up not setting up the backend (at least, that's what I THINK happened). [/SIZE][SIZE="4"]It asked me to log out and do this stuff. I declined and didn't log out.[/SIZE] [SIZE="1"]Yes, I'm dumb. I can't setup the frontend because there is not backend. I tried uninstalling and redownloading Mythtv from Adept to see if it would bring me back to that page. It didn't. How do I configure the backend now?

More info:
TV card: MSI TV@nywhere Plus
Backend/frontend/Desktop.[/SIZE]

I can't set it up at all because my account doesn't have the permissions required. How do I completely start over again? Clean slate.

---

### Post by hung0702 on 2008-12-08
I did try mythtv-setup when I was looking through forums for a solution prior to this thread.

I enter > [FONT="Fixedsys"]mythtv-setup[/FONT] in terminal.

I get a popup that says > Mythbackend must be closed before continuing. Is it ok to close any currently running mythbackend processes?

I click yes.

I'm brought to the blue screen where I choose a language. I pick English. The next screen says > No UPnP backends foundI click ok.

Next screen is the DB configuration 1/2. It asks for the hostname, port, DB, Username, and password. I leave everything default (localhost, __, mythconverg, mythtv, mythtv) and proceed. I don't change anything on the next page (2/2), and Finish.

The next screen says > Cannot find (ping) database host on the network

Then the whole thing starts over again from (1/2)

I exit and a popup asks > Would you like to run mythfilldatabase?I oblige and it enters terminal (different from konsole).

It wouldn't let me copy and paste (exits when I press ctrl + c), so I have to type this all out. Bear with my shortcuts.

> [FONT="Fixedsys"]*date/time* Unable to read configuration file mysql.txt
*date/time* Empty LocalHostName.
*date/time* Using localhost value of Hung-PC
*date/time* New DB connection, total: 1
*date/time* Unable to connect database!
*date/time* Driver error was [1/1045]
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: *password is wrong*)
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
date/time DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QServerSocket: failes to blind or listen to the socket
date/time MCP::InitUPnP() - HttpServer Create Error
date/time Deleting UPnP client...
date/time No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [yes][/FONT]

The password is wrong. It's different from the one generated when I messed up the setup the first time. I can't access /etc/mythtv/mysql.text, even when I [QUOTE[FONT="Fixedsys"]]sudo kate /etc/mythtv/mysql.text[/FONT][/QUOTE]It still asks to check if I have read access to that file.

Regardless, I type yes and press enter.

> [FONT="Fixedsys"]Database host name: [localhost][/FONT]

A few enter presses later and it looks like > [FONT="Fixedsys"]Should I test for connectivity to this host using the ping command? [yes]
Database non-default port: [0]
Database name: [mythconverg]
Database user name: [mythtv]
Database password: [mythtv]
*unique identifier crap, default*
*Wake on LAN crap* [no]
[I]date/time says something about failure to connect
date/time closes out before I have enough time to read it.[/I][/FONT]

Now what should I do? I think it'd be easier if I could start over with a clean slate.

---

### Post by squaregoldfish on 2008-12-09
Hmm... This might be a problem where your user account has not been made a member of the mythtv group, so mythtv-setup can't do its stuff.

You can check by running id from the command prompt. If mythtv isn't among your list of groups, you'll have to add yourself:

```
sudo usermod -a -G mythtv <username>
```

Once you've done that, try doing the setup again and see if you get anywhere. At the very least you'll be able to see in the mysql.txt file to work out what the database password is.

Steve.

---

### Post by hung0702 on 2008-12-10
It says "Cannot login to database?"

It's using the right password and username (the password given to me from the initial setup and username: mythtv).

Can I just delete the mythtv folder from /etc/ and start over? Or will that not do anything?

---

### Post by squaregoldfish on 2008-12-11
I don't have experience of Adept, but if it's anything like Synaptic you should be able to do run a Complete Removal, which will delete all package files, accounts and configuration. You can then install the packages again.

---

