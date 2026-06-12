---
title: "Issues starting Mythweb"
date: 2014-05-26
forum: Mythbuntu
---

### Post by nainsurvolte on 2014-05-26
Just managed to get my Mythbackend to work... to find myself in trouble with Mythweb.

I manage to realign my users as I was getting a cannot access database error in the **error.log** file in** /var/log/apache2** folder. Now that the mythtv user is all set up and the backend up and running this is what I get as an error message

```
error] [client 192.168.1.110] PHP Fatal error:  Call to a member function query_col() on a non-object in /usr/share/mythtv/mythweb/includes/utils.php on line 59
```

This gets created the minute I try to access Mythweb (192.168.1.110 being the address of the PC I am working one to troubleshhot).

Someone has any idea what could be the issue? I never even played in that folder "**/usr/share/mythtv/mythweb/includes/**"

BTW, here is what is at line 59 in the utils.php file.

```
  $cache[$h][$field] = $db->query_col('SELECT data FROM settings WHERE value=? AND hostname IS NULL', $field);
```

Thanks,

---

### Post by nainsurvolte on 2014-05-26
Ok, following a thread where people seemed to have solve the issue by simply uninstalling and reinstalling mythweb, I decided to give it a try. 

I now have a new error message....

```
[error] [client 192.168.1.110] PHP Fatal error:  require(): Failed opening required 'modules/_shared/tmpl/tmpl/footer.php' (include_path='/usr/local/share/mythtv/bindings/php/:/usr/share/mythtv/bindings/php/:.:/usr/share/php:/usr/share/pear') in /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/fatal.php on line 43
[error] [client 192.168.1.110] PHP Warning:  require(modules/_shared/tmpl/tmpl/footer.php): failed to open stream: No such file or directory in /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/fatal.php on line 43
```

:confused:

I am baffled....

---

### Post by blm-ubunet on 2014-05-26
missing packages:
libapache2-mod-php5
php5-mysql

php not enabled for apache
```
ls -al /etc/apache2/mods-enabled/ph*
```

man a2ensite

there is some readme file in the mythweb folder (might have to look at git repo)

---

### Post by nainsurvolte on 2014-05-26
Both packages are installed.

If I ls your command line....

```
lrwxrwxrwx 1 root root 27 Feb  8  2012 /etc/apache2/mods-enabled/php5.conf -> ../mods-available/php5.conf
lrwxrwxrwx 1 root root 27 Feb  8  2012 /etc/apache2/mods-enabled/php5.load -> ../mods-available/php5.load
```

Not too sure exactly what I should be doing with a2ensite....

I think I may have messed up the config, hosts and all that...

Just to put things straight
My server name is TV-Server and on the network it is @ 192.168.1.111

Now, in the config.xml file
-What is LocalHostName?
-What is Host?

Not too sure if I have to put Localhost, 127.0.0.1, 192.168.1.111 or even has I saw on a thread, 127.0.1.1 (for apache2 apparently)

Now in my hosts file, here is what I got

```
127.0.0.1    localhost    localhost.localdomain
192.168.1.111    TV-server    localhost.localdomain
```

It has to do with the setup of the config.xml as mythweb was working fine before the upgrade with those host settings.

Thanks

---

### Post by blm-ubunet on 2014-05-26
Mythweb does not use config.xml or the backend..AFAIK it just directly operates on database & recordings through server side code php.
dBase credentials, including hostname, are found in appropriate apache conf files

```
ls -al /etc/apache2/sites-enabled/
```
look for files like
mythweb.conf.apache
or mythweb-ssl.conf

a2ensite would be required to get conf file from available to enabled.

Light reading:
[https://github.com/MythTV/mythweb/blob/cc3c3aeceff85c44803129c5eaa70b766f98d10a/INSTALL](https://github.com/MythTV/mythweb/blob/cc3c3aeceff85c44803129c5eaa70b766f98d10a/INSTALL)

Try:
[http://TV-server:6544/](http://TV-server:6544/)
Do NOT open this port to the web.

---

### Post by nainsurvolte on 2014-05-26
:roll:

Oh... boy. How many conf file are they ?!

Is there a way to delete some and converge on the one? Anyway, so there was one other "**mythweb.conf**" under "**/etc/apache2/sites-available**" and that was the one messing everything up.

Thanks again.

---

### Post by blm-ubunet on 2014-05-26
You can converge the config.xml files with symlinks..

The apache config should be separated.
MythWeb is server side app (LAMP server) very independent of BEs & FEs.
It is a good thing there is a layer of separation (& SSL) if you expose mythweb to the outside world.

MythWeb is not a backend server but there is one in development. Protecting it (proxy?) will be another configuration problem.

---

