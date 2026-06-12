---
title: "samba nobody/nogroup"
date: 2011-06-03
forum: Networking &amp; Wireless
---

### Post by jperelli on 2011-06-03
Hello!

I create files and folders over samba (shared folder in linux with gnome/nautilus) with an anonymous user. Those files are created with user nobody, group nogroup.

I want to be able to modify this files with my linux user normally. For that, I want to know if the files created could be created with the user and group that I want (my user) even though I created them with an anonymous samba user.

Example:
 - set a samba share in linux (configure it somehow) with anonymous access +rw
 - enter the shared folder as anon from net, create a file
 - samba should create those files as a user:group through some configuration and permissions given before and once.

Can that be configured in samba?

---

### Post by mikewhatever on 2011-06-03
I think it would be a lot easier to just add yourself to the 'nogroup' group. Try that and see how it goes.

---

### Post by jperelli on 2011-06-03
I think that is a workaround, is useful, but not solved... thanks!

---

### Post by capscrew on 2011-06-04
> **jperelli said:**
> Hello!

I create files and folders over samba (shared folder in linux with gnome/nautilus) with an anonymous user. Those files are created with user nobody, group nogroup.

I want to be able to modify this files with my linux user normally. For that, I want to know if the files created could be created with the user and group that I want (my user) even though I created them with an anonymous samba user.

Example:
 - set a samba share in linux (configure it somehow) with anonymous access +rw
 - enter the shared folder as anon from net, create a file
 - samba should create those files as a user:group through some configuration and permissions given before and once.

Can that be configured in samba?

Yes it can.  In the share definition add ```
force user = user
force group = group
```

If you want to control file permissions you can use ```
force create mode
```For directory permissions you can use```
force directory mode
```

All of this is described [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html").

---

### Post by jperelli on 2011-06-04
Hello, thanks!

Does gnome/nautilus have a GUI to set those?
Or, when I create a shared folder in gnome2 with right click, where are the configuration for that share? Is not in samba.conf!

---

### Post by capscrew on 2011-06-04
> **jperelli said:**
> Hello, thanks!

Does gnome/nautilus have a GUI to set those?
Or, when I create a shared folder in gnome2 with right click, where are the configuration for that share? Is not in samba.conf!

Nautilus creates the usershares at```
/var/lib/samba/usershares
```

I don't know if you can use those parameters with Samba usershares.  Let us know if it works.  :-)

---

### Post by Morbius1 on 2011-06-04
You can't use "force user" in /var/lib/samba/usershare but you can add it to the [global] section of smb.conf itself. That's one of the downsides to usershare. All the parameters will work but only at the global level. If all your shares are guest accessible then "force user" in smb.conf will do what you want.

Just remember that unlike creating shares in Nautilus every time you modify smb.conf you need to restart samba:
```
sudo service smbd restart
```

---

### Post by jperelli on 2011-06-04
> **Morbius1 said:**
> You can't use "force user" in /var/lib/samba/usershare but you can add it to the [global] section of smb.conf itself. That's one of the downsides to usershare. All the parameters will work but only at the global level. If all your shares are guest accessible then "force user" in smb.conf will do what you want.

Just remember that unlike creating shares in Nautilus every time you modify smb.conf you need to restart samba:
```
sudo service smbd restart
```

Thank you very much! that worked!
marking as solved.

---

