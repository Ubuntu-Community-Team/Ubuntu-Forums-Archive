---
title: "Access www-data over Samba from Windows 7"
date: 2012-04-15
forum: Networking &amp; Wireless
---

### Post by 5circles on 2012-04-15
I want to edit files using Windows 7 tools.  I have Samba setup and working OK for my own user, but I'd like to keep the www-data user for the /var/www hierarchy to make it easier to use the LAN as a sandbox/staging to move to a public Internet server.

I tried adding a symbolic link for /home/www-data pointing to /var/www.  I wasn't able to change ownership of the link from root, so I don't know if that was a problem, but I couldn't see the share from Windows (after restarting Samba).

Then I tried adding a share with Webmin.  The share is now visible from Windows, but I can't log in - I just get errors about \\server\www-data is not accessible, you might not have permission etc.

Is there something special about the www-data account, or some steps I can follow to set this up properly?

Thanks!

---

### Post by canule on 2012-07-22
I have the same problem, I had it solved a few years ago but after re-installing the server I was unable to find the documentation of that online, and leaved it for dead, until now, and finding your question here for my solution.

However I did backup the config file what I've used then

---

### Post by canule on 2012-07-22
```
[httpd-restricted - Mediabase]
comment = Website
path = /var/www/
write list = @data
force group = root
force user = root
create mask = 0644
directory mask = 0755
wide links = No
read only = no
```

This got it working, but I doubt its a safe way to share.

---

