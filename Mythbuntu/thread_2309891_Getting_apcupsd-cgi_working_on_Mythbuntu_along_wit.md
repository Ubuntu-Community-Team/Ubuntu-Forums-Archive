---
title: "Getting apcupsd-cgi working on Mythbuntu along with mythweb"
date: 2016-01-14
forum: Mythbuntu
---

### Post by jfaberna on 2016-01-14
I have a working Mythbuntu 14.04.3 system that includes Mythweb working as expected.

I've added a APC UPS connected via USB and have apcupsd working.  I'd like to get the web gui working for that as well so I installed apcupsd-cgi.

The installation put the .cgi files in /usr/lib/cgi-bin/apcupsd/

I can go to <mythbuntu>/mythweb and get to Mythweb.  But I can't get to <mythbuntu>/cgi-bin/apcupsd/multimon.cgi  I get errors.

I came to the conclusion that I needed some edits to /etc/apache2/apache2.conf or needed to put some .conf file in sites-available/.

I'm now to the point of when I go to<mythbuntu>/cgi-bin/apcupsd/multimon.cgi I get the multimon.cgi file downloaded to my system as a file and not executed.

Below are the changed I'm using in /etc/apache2/apache2.conf

```
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "/usr/lib/cgi-bin">
    AllowOverride None
    Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
    Require all granted
    AddHandler cgi-script .cgi
</Directory>
```

Any idea what I'm doing wrong?

---

### Post by jfaberna on 2016-01-14
I solved this by enabling CGI this way:
```
sudo a2enmod cgi
sudo service apache2 restart
```

My mods to apache2.conf remain:

```

ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "/usr/lib/cgi-bin">
    AllowOverride None
    Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
    Require all granted
    AddHandler cgi-script .cgi
</Directory>
```

---

