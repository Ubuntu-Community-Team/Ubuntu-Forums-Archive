---
title: "Public files/network sharing not working"
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by Antarctica32 on 2011-03-21
So I want to put some of my folders on my network. I open up nautilus and go to my home folder and right click -> properties-> share and then selected share this folder, made it so that others could modify stuff on it and have guest access (which is what I want), and changed the share name to "home". Then I clicked create share. I then went to Places->Network->******'s public files on [the name of my computer]. But then some stupid error message popped up saying: 

"DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)"

 whatever that means. Here is a screenshot of it. All help of any kind is greatly appreciated. Thanks in advance.

---

### Post by Antarctica32 on 2011-03-22
*bump* anybody.....?

---

### Post by Antarctica32 on 2011-03-24
still unable to fix it...

---

### Post by Antarctica32 on 2011-03-27
any ideas? please

---

### Post by gordintoronto on 2011-03-27
What happens when you try to access the Share from another computer on your network? What version of Ubuntu are you using?

I would never share my home folder, which exposes all my files and settings. Instead, I share a folder which is in Home. It's always worked for me.

---

### Post by Morbius1 on 2011-03-27
I do believe you are talking about two entirely different protocols.
> I open up nautilus and go to my home folder and right click ->  properties-> share and then selected share this folder, made it so  that others could modify stuff on it and have guest access (which is  what I want), and changed the share name to "home". Then I clicked create share.That's Samba. Specifically Samba Usershares. You would access the share by: Nautilus > Network > Windows Network > Workgroup > Name of the Box > home
> I then went to Places->Network->******'s public files on [the name of my computer]. That's not Samba. That's gnome-user-share a.k.a. "Personal File Sharing". It can only create a share of one folder: /home/username/Public. It shows up under "Network" at the same level as "Windows Network" and has the form:
> user-name's public files on host-nameTo create one of these shares you would go to "Personal File Sharing" in the Preferences part of the menu I believe. 

I don't use Personal File Sharing because it's too flaky as you are finding out.

See if your Samba share at "home" is alive and well.

---

### Post by Antarctica32 on 2011-03-27
> **gordintoronto said:**
> What happens when you try to access the Share from another computer on your network? What version of Ubuntu are you using?

I would never share my home folder, which exposes all my files and settings. Instead, I share a folder which is in Home. It's always worked for me.

When I attempt at access the share on a different ubuntu computer it gives the same results as when I do it on mine, when I attempt to access it on a windows computer it doesn't even show up as if the share didn't exist. I am aware of the risks involved with sharing but it doesn't really matter as all the nodes on the network are owned by me.

---

### Post by Morbius1 on 2011-03-28
> **Antarctica32 said:**
> When I attempt at access the share on a different ubuntu computer it gives the same results as when I do it on mine, when I attempt to access it on a windows computer it doesn't even show up as if the share didn't exist. 
If you're still talking about the "******'s public files on [the name of my computer]" part of this then it's unlikely Windows will ever see it. "Personal File Sharing" set's up a baby Apache File Server that broadcasts it's presence using avahi. You would have to install avahi on Windows ( called bonjour on Windows ) for that to work and based on my experiences it just doesn't work. It doesn't even work very well with an OSX client and Apple invented bonjour.

From your own machine run the following command and see if you can access your own share:
```
nautilus smb://192.168.0.100/home
```*[COLOR=Blue]Changing 192.168.0.100 to the ip address of your own machine.[/COLOR]*[COLOR=Black]

That will tell you if your samba share is functioning.
[/COLOR]

---

