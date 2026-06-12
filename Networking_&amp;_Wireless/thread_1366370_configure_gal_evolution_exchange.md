---
title: "configure gal evolution exchange"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by luca219 on 2009-12-28
Hello, I use ubuntu with karmic evolution 2.28.1.
I want to connect to my company serves rexchange.
For receiving and sending everything works well connected at https: / / owa.myexchange.it / exchange Riech not to operate the global address catalog (gal) netbios name is "mail".
What should I write?
https: / / owa.myexchange.it /?
mail.myexchange.it?
Port 443? 3268?
:confused:
please help

---

### Post by rehdwolfe on 2010-01-02
I found on another page how to determine your global catalog. Assuming you have access to an outlook client that is presently working:

[http://seer.entsupport.symantec.com/docs/293154.htm](http://seer.entsupport.symantec.com/docs/293154.htm)


To determine if the authentication logon server is also being used as the Closest Global Catalog (GC) server check the properties of Outlook.

1. Open Outlook
2. Create a New mail message and press To
3. Change the Show Names from the: selection to All Address Lists
4. Right-click All Address Lists and click Properties

The name of the GC is listed in The current server is: field.

The authentication server can be found using the command Set and search for the field LOGONSERVER

The Outlook GC can be changed to match the LOGONSERVERDetails:
To determine if the authentication logon server is also being used as the Closest Global Catalog (GC) server check the properties of Outlook.

1. Open Outlook
2. Create a New mail message and press To
3. Change the Show Names from the: selection to All Address Lists
4. Right-click All Address Lists and click Properties

The name of the GC is listed in The current server is: field.

The authentication server can be found using the command Set and search for the field LOGONSERVER

---

