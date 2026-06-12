---
title: "Where has inetd.conf gone?"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by s_raiguel on 2010-11-29
Whatever happened to good old inetd.conf or xinetd.conf? Back in the day, lines in these files were handy ways of insuring that apps like smb and telnetd would (or would not) be automatically started at boot. Since neither of these configuration files exists in /etc anymore, I can only assume their function has been taken over by some other script or process to be run at startup. With earlier versions of Ubuntu, one could even turn Samba startup on or off using the "startup applications" applet under the system->preference menu, but this, too, has disappeared. So where has this control gone? What determines whether such applications get started? The "Ubuntu Documentation", as is often the case, is less than helpful at providing any enlightenment regarding the actual workings of the system or documenting arbitrary changes made to it from version to version. 

So my questions are - (1)what has now taken over the function of inetd.conf or xinetd.conf;  (2)how can networks services such as telnetd be added or removed from the startup and (3)if one these files is created and put into /etc will its contents still be read and executed?

---

### Post by SeijiSensei on 2010-11-29
Many services that used to have a single consolidated configuration file now use separate files for each service.  This enables package installers to place the file for a specific service in the configuration directory.  In the case of xinetd, the configuration files are stored in /etc/xinetd.d/.

"sudo apt-get install xinetd" will install the binary and create the /etc/xinetd.d/ directory. You'll also get an /etc/xinetd.conf file that essentially tells xinetd to traverse the xinetd.d directory.

The original inetd has been largely deprecated in favor of the more powerful xinetd.

More and more server daemons are designed to run securely as standalone programs rather than being invoked by xinetd.  I still use it to run a few specific services for which I need to control access via hosts.allow and hosts.deny.  But the major servers -- SSH, Apache, MySQL/PostgreSQL, sendmail/Postfix, etc. -- all run as standalone daemons these days.

---

### Post by ajgreeny on 2010-11-29
Are you sure you do not mean **/etc/init.d** which is where a lot of shell scripts to start various services are located.

---

### Post by SeijiSensei on 2010-11-29
> **ajgreeny said:**
> Are you sure you do not mean **/etc/init.d** which is where a lot of shell scripts to start various services are located.

No, we're talking about xinetd, the Internet "superserver," not the init startup process that reads scripts from /etc/init.d.  xinetd listens on ports and invokes a program in response to connections.  By "wrapping" a service in xinetd you can allow or reject connections based on the contents of /etc/hosts.allow and /etc/hosts.deny and control many other features of the connection as well.  See "man xinetd" and "man hosts.allow" for more details.

---

### Post by s_raiguel on 2010-11-30
That was most helpful. Thanks for taking the time to reply.

---

