---
title: "webdav not mounted"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by Bietje on 2010-04-22
Hi,

I've set up (compiled) a webserver (apache with webdav mods) and everything works fine, but the the webdav... When i connect to the webdav folder everything goes fine, I can create and remove file and directory's. Where does it go wrong then? Here: when I try to rename a file. When I try to I get the following error:

[IMG]http://i42.tinypic.com/15n6kix.png[/IMG]
The error is in dutch it says:
"The item could not be renamed!
test2 could not be renamed to test:
The given location is not mounted"

(And if i click refresh the name is changed anyway)

Interesting part of conf.httpd
------------------
DocumentRoot "/opt/PCmichelweb/apache/htdocs"
DavLockDB "/opt/PCmichelweb/apache/dav-conf/DavLock"
alias /webdav /opt/PCmichelweb/apache/htdocs/webdav
<Directory "/opt/PCmichelweb/apache/htdocs/webdav">
    DAV On

    Order Allow,Deny
    Allow from all

    AuthType Digest
    AuthName DAV-upload

    # You can use the htdigest program to create the password database:
    #   htdigest -c "/opt/PCmichelweb/apache/dav-conf/davusers.passwd" DAV-upload admin
    AuthUserFile "/opt/PCmichelweb/apache/dav-conf/davusers.passwd"
    AuthDigestProvider file

    # Allow universal read-access, but writes are restricted
    # to the admin user.
    <LimitExcept GET OPTIONS>
        require user admin
    </LimitExcept>
</Directory>
------------------------

When I change my documentroot to /opt/PCmichelweb/apache/htdocs/webdav the entire problem is solved.. but then my normal site doesn't work anymore. How can i solve this?

Thanks in advance! Greets

---

### Post by Bietje on 2010-04-22
Hi,

I've set up (compiled) a webserver (apache with webdav mods) and everything works fine, but the the webdav... When i connect to the webdav folder everything goes fine, I can create and remove file and directory's. Where does it go wrong then? Here: when I try to rename a file. When I try to I get the following error:

[click]http://i42.tinypic.com/15n6kix.png[/click] large image
The error is in dutch it says:
"The item could not be renamed!
test2 could not be renamed to test:
The given location is not mounted"

(And if i click refresh the name is changed anyway)

Interesting part of conf.httpd
------------------
DocumentRoot "/opt/PCmichelweb/apache/htdocs"
DavLockDB "/opt/PCmichelweb/apache/dav-conf/DavLock"
alias /webdav /opt/PCmichelweb/apache/htdocs/webdav
<Directory "/opt/PCmichelweb/apache/htdocs/webdav">
    DAV On

    Order Allow,Deny
    Allow from all

    AuthType Digest
    AuthName DAV-upload

    # You can use the htdigest program to create the password database:
    #   htdigest -c "/opt/PCmichelweb/apache/dav-conf/davusers.passwd" DAV-upload admin
    AuthUserFile "/opt/PCmichelweb/apache/dav-conf/davusers.passwd"
    AuthDigestProvider file

    # Allow universal read-access, but writes are restricted
    # to the admin user.
    <LimitExcept GET OPTIONS>
        require user admin
    </LimitExcept>
</Directory>
------------------------

When I change my documentroot to /opt/PCmichelweb/apache/htdocs/webdav the entire problem is solved.. but then my normal site doesn't work anymore. How can i solve this?

Thanks in advance! Greets

---

### Post by Bietje on 2010-04-22
Hi,

I've set up (compiled) a webserver (apache with webdav mods) and everything works fine, but the the webdav... When i connect to the webdav folder everything goes fine, I can create and remove file and directory's. Where does it go wrong then? Here: when I try to rename a file. When I try to I get the following error:

[click][http://i42.tinypic.com/15n6kix.png]("http://i42.tinypic.com/15n6kix.png")[/click] (large image)
The error is in dutch it says:
"The item could not be renamed!
test2 could not be renamed to test:
The given location is not mounted"

(And if i click refresh the name is changed anyway)

Interesting part of conf.httpd
------------------
DocumentRoot "/opt/PCmichelweb/apache/htdocs"
DavLockDB "/opt/PCmichelweb/apache/dav-conf/DavLock"
alias /webdav /opt/PCmichelweb/apache/htdocs/webdav
<Directory "/opt/PCmichelweb/apache/htdocs/webdav">
    DAV On

    Order Allow,Deny
    Allow from all

    AuthType Digest
    AuthName DAV-upload

    # You can use the htdigest program to create the password database:
    #   htdigest -c "/opt/PCmichelweb/apache/dav-conf/davusers.passwd" DAV-upload admin
    AuthUserFile "/opt/PCmichelweb/apache/dav-conf/davusers.passwd"
    AuthDigestProvider file

    # Allow universal read-access, but writes are restricted
    # to the admin user.
    <LimitExcept GET OPTIONS>
        require user admin
    </LimitExcept>
</Directory>
------------------------

When I change my documentroot to /opt/PCmichelweb/apache/htdocs/webdav the entire problem is solved.. but then my normal site doesn't work anymore. How can i solve this?

Thanks in advance! Greets

Edit.. For some unknown reason is the tread posted trice?

---

### Post by lisati on 2010-04-22
Threads merged.

---

### Post by Bietje on 2010-04-22
thanks for that

---

