---
title: "change login users for gnome vfs samba"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by kevmitch on 2009-02-01
I'm trying to figure out how samba authentication works for Gnome Network Places. In particular, I want to change the username with which I am logged into a given machine. 

When I first clicked on the share the while browsing "network:///" with Nautilus, it prompted me for a username and password. Now when I click on it, it automatically uses the same username and password even after I have ejected the virtual drive. While this is in general, a great feature, I would like to be able to manually override this so that I can change the user name that I'm using to log in. 

Is this possible outside of logging out and logging back in to my local machine?

---

### Post by cariboo on 2009-02-01
If you want to access your shares as a different user, create another user, and login as that user.

To create a new user, go to System-->Administration-->Users and Groups, click the unlock button and add a new user.

Remember to create a smbpassword and enable it:

```
sudo smbpasswd -L -a <username>
```

to add the user

```
sudo smbpasswd -L -e <username>
```

to enable the user.

Jim

---

### Post by kevmitch on 2009-02-10
I think what you're describing is enabling a new user to access the Ubuntu machine via samba. I'm going the other way around; accessing remote machines from Ubuntu. Does Gnome/Ubuntu provide the ability to alter the identity presented by a local user to a remote samba server? 

For instance consider the following analogy with ssh. From the Ubuntu machine homunculus, I can log into remotehost as either kevmitch of kmitchell
```

kevmitch@homunculus$ ssh kmitchell@remotehost

```
or
```

kevmitch@homunculus$ ssh kevmitch@remotehost

```

---

### Post by crouton on 2009-05-12
You could try creating a new connection, e.g. File->Connect to Server, Windows Share, and fill out the information that way.  It should prompt for password as well.

---

