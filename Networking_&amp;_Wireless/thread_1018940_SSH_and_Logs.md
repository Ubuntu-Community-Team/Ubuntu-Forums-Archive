---
title: "SSH and Logs"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by warnesey333 on 2008-12-22
Hi, 
I'm wanting to be able put the shh logs into a mysql database as I have done with my apache ones.

I've read into the syslog.conf file and how I can choose what goes to where but i've been unable to get JUST the SSHD logs to go into a seperate log file.

If anyone has done this or has any ideas - please let me know :)

Any help is greatly appreciated - thanks

---

### Post by jonobr on 2008-12-22
Hello


Just wondering what you hoping to get?
If your looking for users who tried SSH to get access to your machine they are in
/var/log/auth.log

To get them into your db, Im wondering if you could import from a file?
If so, you could grep out the lines you wanted and redirect to a file

cat /var/log/auth.log |grep sshd > sshd_outfile

You could autmate that to generate each day or so?
No being a db guru Im not sure if that helps or not

---

### Post by warnesey333 on 2008-12-22
Well i'm hoping to get:
- Any attempts made by ANY usernames - correct or not
- Any attempts at root (even though it is banned)
- Any incorrect passwords

I've used the user.log which I don't think is actually used to get most of this.

What I was thinking before was to use:

inotifywait and for it to constantly check for a change in the file ssh.logs which is simply just the auth logs.

If it found a change it would then have to find the NEW data:
- Use awk to keep a track of the PREVIOUS line number and then use this to find the new data
- Pipe the new data to a program to add to the mysql database or simply add it in this program

Would it be better for me to use a cron job or an inotifywait?

Inotifywait would be instant I believe and would stop anyone attempting to hack me there and then (after more iptables scripting ofcourse) ?

Cheers for help

---

### Post by jonobr on 2008-12-22
Hello

the greping of sshd in auth.log will show what you need and will show you the source address trying to access it.,
It will show you the user name so you will see root trying to gain access.
It will not show you the passwords is all.

I havent used inotifywait before so cant help you on that :(

---

